
## [[TensorFlow#TensorFlow Lite]] [[TensorFlow#TensorFlow Lite Micro]]




## [[TensorFlow#Opciones de Despliegue de Modelos]]



## Introducción a la Optimización de Modelos

La optimización de modelos es crucial para ejecutar aprendizaje automático en dispositivos con recursos limitados. Los modelos entrenados en TensorFlow suelen ser demasiado grandes o consumir demasiados recursos para ser desplegados eficientemente en dispositivos móviles o sistemas embebidos. Por lo tanto, es esencial aplicar técnicas de optimización para reducir el tamaño y mejorar la eficiencia de los modelos sin comprometer significativamente la precisión.

![[Captura de pantalla 2024-10-14 a las 2.24.41 p. m..png]]

## Proceso de Conversión y Optimización de Modelos

Para ejecutar modelos en dispositivos con recursos limitados, es necesario convertir y optimizar los modelos entrenados en TensorFlow al formato de **TensorFlow Lite**, diseñado para ser ligero y eficiente.

### Pasos del Proceso:

1. **Entrenamiento del Modelo en TensorFlow:**

   Se entrena el modelo utilizando TensorFlow estándar, ajustando los hiperparámetros y alcanzando la precisión deseada.

2. **Guardado del Modelo:**

   El modelo entrenado se guarda utilizando `tf.saved_model.save`, creando un directorio con los archivos y metadatos necesarios.

   ```python
   export_dir = 'saved_model/1'
   tf.saved_model.save(model, export_dir)
   ```

3. **Conversión a TensorFlow Lite:**

   El modelo guardado se convierte al formato TensorFlow Lite mediante `TFLiteConverter`, reduciendo su tamaño y optimizándolo para dispositivos con recursos limitados.

   ```python
   converter = tf.lite.TFLiteConverter.from_saved_model(export_dir)
   tflite_model = converter.convert()
   ```

4. **Guardado del Modelo Convertido:**

   El modelo convertido se guarda en un archivo `.tflite`.

   ```python
   import pathlib
   tflite_model_file = pathlib.Path('model.tflite')
   tflite_model_file.write_bytes(tflite_model)
   ```

5. **Optimización del Modelo:**

   Durante la conversión, se pueden aplicar técnicas de optimización adicionales, como la cuantificación, para mejorar aún más la eficiencia del modelo.

---

## Optimización durante la Conversión

La optimización durante la conversión permite reducir el tamaño y mejorar la eficiencia del modelo. TensorFlow Lite ofrece varias opciones de optimización que se pueden aplicar a través del convertidor.
![[Captura de pantalla 2024-10-16 a las 12.25.38 p. m..png]]
### Uso de `converter.optimizations`:

Se pueden especificar optimizaciones que se aplicarán durante la conversión del modelo.

```python
converter.optimizations = [tf.lite.Optimize.DEFAULT]
tflite_model_quant = converter.convert()
```

Las opciones de optimización incluyen:

- `tf.lite.Optimize.DEFAULT`: Optimiza automáticamente para reducir el tamaño y la latencia.
- `tf.lite.Optimize.OPTIMIZE_FOR_SIZE`: Enfocado en reducir al máximo el tamaño del modelo.
- `tf.lite.Optimize.OPTIMIZE_FOR_LATENCY`: Enfocado en reducir el tiempo de inferencia.

### Resultados de la Optimización:

- **Reducción del Tamaño del Modelo:** El tamaño del modelo puede reducirse significativamente. Por ejemplo, un modelo de 9 MB puede reducirse a 2.3 MB.
- **Mejora de la Velocidad de Inferencia:** Las pruebas muestran mejoras de dos a tres veces en la velocidad.
- **Impacto en la Precisión:** Puede haber una pequeña pérdida de precisión. Es importante evaluar si esta pérdida es aceptable para la aplicación específica.

---

## Cuantificación Mediante Datos Representativos

La **cuantificación** es una técnica de optimización que reduce la precisión de los pesos y activaciones del modelo, generalmente de float32 a int8, lo que reduce significativamente el tamaño del modelo y mejora la eficiencia computacional.

### Cuantificación de Pesos y Activaciones:

- **Pesos:** Valores que representan las conexiones entre neuronas en la red.
- **Activaciones:** Salidas de las neuronas después de aplicar la función de activación.

### Proceso de Cuantificación con Datos Representativos:

1. **Preparación de un Conjunto de Datos Representativo:**

   Se utiliza un conjunto de datos que representa el tipo de datos que el modelo verá durante la inferencia. Esto es crucial para calibrar correctamente los rangos de cuantificación.

   ```python
   def representative_dataset():
       for data in tf.data.Dataset.from_tensor_slices(train_images).batch(1).take(100):
           yield [data]
   ```

2. **Configuración del Convertidor para Cuantificación:**

   Se especifica que se desea realizar cuantificación plena a int8.

   ```python
   converter.optimizations = [tf.lite.Optimize.DEFAULT]
   converter.representative_dataset = representative_dataset
   converter.target_spec.supported_ops = [tf.lite.OpsSet.TFLITE_BUILTINS_INT8]
   converter.inference_input_type = tf.uint8
   converter.inference_output_type = tf.uint8
   tflite_quant_model = converter.convert()
   ```

### Ventajas de la Cuantificación con Datos Representativos:

- **Reducción Significativa del Tamaño del Modelo:** Puede reducir el tamaño del modelo hasta en un 75%.
- **Mejora de la Latencia:** Los cálculos con enteros de 8 bits son más rápidos que con float32.
- **Mantenimiento de la Precisión:** Al calibrar con datos representativos, la pérdida de precisión es mínima.

### Consideraciones:

- Es importante que el conjunto de datos representativo sea similar a los datos reales que el modelo procesará en producción.
- La cuantificación es especialmente beneficiosa en hardware que soporta operaciones int8 de forma eficiente.

---

## Cuantificación durante el Entrenamiento

La **cuantificación durante el entrenamiento** (Quantization Aware Training, QAT) ajusta el modelo para que use pesos y activaciones cuantizados durante el entrenamiento. Esto permite que el modelo aprenda a ser robusto a los efectos de la cuantificación, mejorando la precisión en comparación con la cuantificación posterior al entrenamiento.

### Implementación de QAT:

1. **Importar el Model Optimization Toolkit:**

   ```python
   import tensorflow_model_optimization as tfmot
   ```

2. **Aplicar Cuantificación al Modelo:**

   Se envuelve el modelo original con las capas de cuantificación.

   ```python
   quantize_model = tfmot.quantization.keras.quantize_model(model)
   ```

3. **Compilar y Entrenar el Modelo Cuantizado:**

   ```python
   quantize_model.compile(optimizer='adam',
                          loss='sparse_categorical_crossentropy',
                          metrics=['accuracy'])
   quantize_model.fit(train_images, train_labels, epochs=5)
   ```

### Ventajas de QAT:

- **Mejor Mantenimiento de la Precisión:** El modelo aprende a compensar los errores introducidos por la cuantificación.
- **Optimización desde el Inicio:** No es necesario un conjunto de datos representativo después del entrenamiento.
- **Resultados Equivalentes o Mejores que el Modelo Original:** En algunos casos, la precisión puede incluso superar a la del modelo float32.

### Consideraciones:

- Requiere más tiempo de entrenamiento.
- Es más complejo de implementar que la cuantificación posterior al entrenamiento.

---

## Tipos de Cuantificación

Existen dos enfoques principales para cuantificar modelos:

1. **Cuantificación Posterior al Entrenamiento (PTQ):**

   - Se aplica después de que el modelo ha sido entrenado.
   - Fácil de implementar.
   - Puede resultar en una pequeña pérdida de precisión.
   - No requiere modificar el proceso de entrenamiento.

2. **Cuantificación Consciente del Entrenamiento (QAT):**

   - Se aplica durante el entrenamiento del modelo.
   - El modelo aprende a ser robusto a la cuantificación.
   - Mantiene una precisión más alta que PTQ.
   - Requiere modificar el proceso de entrenamiento.

---

## Beneficios de la Cuantificación a 8 Bits

La cuantificación a 8 bits es una técnica poderosa para mejorar la eficiencia de los modelos durante la inferencia, especialmente en dispositivos con recursos limitados.

### Beneficios Clave:

1. **Reducción del Tamaño del Modelo:**

   - Disminuye el tamaño del modelo hasta en un 75%.
   - Permite desplegar modelos complejos en dispositivos con poca memoria.

2. **Mejora de la Latencia:**

   - Los cálculos con enteros de 8 bits son significativamente más rápidos que con float32.
   - Aprovecha la capacidad de procesamiento paralelo (SIMD) en hardware moderno.

3. **Menor Consumo de Energía:**

   - Las operaciones int8 consumen menos energía que las operaciones float32.
   - Ideal para dispositivos alimentados por batería.

4. **Aceleración por Hardware:**

   - Muchos dispositivos embebidos y DSPs están optimizados para operaciones int8.
   - Mejora el rendimiento y eficiencia energética al aprovechar aceleradores de hardware específicos.

### Por Qué Funciona la Cuantificación:

- **Robustez de las Redes Neuronales:** Las redes neuronales pueden tolerar la reducción de precisión debido a su capacidad para manejar ruido e imprecisiones.
- **Rango de Valores Limitado:** Los pesos y activaciones suelen estar dentro de rangos que pueden ser representados adecuadamente con 8 bits.

---

## Cuantificación Consciente del Entrenamiento (QAT)

La cuantificación consciente del entrenamiento introduce la cuantificación en el proceso de entrenamiento, permitiendo que el modelo ajuste sus pesos y activaciones para compensar los errores introducidos por la cuantificación.

### Características de QAT:

- **Entrenamiento con Simulación de Cuantificación:**

  - Durante el entrenamiento, se simula la cuantificación en los cálculos hacia adelante.
  - La retropropagación utiliza los valores en float32 para actualizar los pesos.

- **Beneficios en la Precisión:**

  - Mejora la precisión en comparación con PTQ.
  - En algunos casos, puede superar la precisión del modelo original en float32.

### Implementación Detallada:

1. **Preparación del Modelo Cuantizado:**

   - Se aplica `tfmot.quantization.keras.quantize_model` al modelo base.
   - Se añaden capas de cuantización que simulan los efectos de la cuantificación.

2. **Compilación y Entrenamiento:**

   - Se compila el modelo cuantizado con los mismos parámetros que el modelo original.
   - Se entrena el modelo, permitiendo que ajuste sus pesos para compensar la cuantificación.

3. **Conversión a TensorFlow Lite:**

   - Una vez entrenado, el modelo se convierte a TensorFlow Lite.
   - El modelo resultante está optimizado y mantiene una alta precisión.

### Consideraciones:

- **Complejidad Adicional:** Requiere más recursos computacionales durante el entrenamiento.
- **Tiempo de Entrenamiento Mayor:** El proceso de entrenamiento puede ser más lento.

---

## Detalles Adicionales sobre Cuantificación

### Funcionamiento de la Cuantificación:

- **Mapeo Lineal de Valores:** Los valores float32 se mapean linealmente a int8 dentro de un rango específico.
- **Ejemplo de Mapeo:**

  - Rango float32: -3.0 a 6.0
  - Mapeo a int8: -128 a 127
  - Valores float32 específicos se asignan a enteros correspondientes.

### Impacto en la Memoria y Ancho de Banda:

- **Reducción de Ancho de Banda:** Los valores int8 requieren menos memoria y ancho de banda, mejorando la eficiencia de la caché.
- **Operaciones SIMD:** Las operaciones con int8 pueden aprovechar instrucciones SIMD para paralelizar cálculos.

### Compromisos de la Cuantificación:

- **Pérdida de Precisión:** Puede haber una disminución en la precisión, aunque generalmente es mínima.
- **Necesidad de Evaluación:** Es importante evaluar si la pérdida de precisión es aceptable para la aplicación específica.

---

## Conclusiones

La optimización y cuantificación de modelos son técnicas esenciales para desplegar aprendizaje automático en dispositivos con recursos limitados. Al aplicar cuantificación, ya sea posterior al entrenamiento o consciente del entrenamiento, se logran los siguientes beneficios:

- **Reducción Significativa del Tamaño del Modelo:** Permite que modelos complejos se ejecuten en dispositivos con memoria limitada.
- **Mejora de la Latencia y Eficiencia Energética:** Los cálculos con int8 son más rápidos y consumen menos energía.
- **Mantenimiento de la Precisión:** Con técnicas como QAT, es posible mantener una alta precisión en las predicciones.
- **Aprovechamiento de Aceleradores de Hardware:** Los modelos cuantificados pueden aprovechar hardware optimizado para operaciones int8.

Estas técnicas son fundamentales en el campo de **TinyML**, permitiendo llevar el aprendizaje automático a dispositivos embebidos y móviles, y ampliando el alcance de las aplicaciones de inteligencia artificial.

---

**Nota Final:** Es recomendable experimentar con las técnicas de cuantificación y optimización en proyectos reales, evaluando el impacto en la precisión y rendimiento, y ajustando según las necesidades específicas de cada aplicación.




# Essential Code

### 1. **Carga y preprocesamiento de datos**

Este bloque es esencial en cualquier proyecto de *machine learning*, ya que la calidad de los datos afecta directamente el rendimiento del modelo. Se repite en varios de los códigos.

```python
import tensorflow as tf
import tensorflow_datasets as tfds

def format_image(image, label):
    image = tf.image.resize(image, (224, 224)) / 255.0
    return image, label

(raw_train, raw_validation, raw_test), metadata = tfds.load(
    'cats_vs_dogs',
    split=['train[:80%]', 'train[80%:90%]', 'train[90%:]'],
    with_info=True,
    as_supervised=True,
)
```

- **`tfds.load`:** Esta función carga conjuntos de datos populares directamente desde la API de TensorFlow Datasets. En este caso, se usa el dataset `cats_vs_dogs`, pero puede cambiarse a otros como `MNIST`.  
  - **`split`**: Divide el conjunto en entrenamiento, validación y prueba.
  - **`with_info=True`**: Proporciona información adicional sobre el dataset, como el número de ejemplos o clases (gatos y perros en este caso).
  - **`as_supervised=True`**: Devuelve los datos en forma `(imagen, etiqueta)`.

- **`format_image`**: Redimensiona las imágenes a un tamaño fijo, en este caso `224x224`, y normaliza los valores de los píxeles dividiéndolos por 255.0. Esto asegura que los datos de entrada estén en un formato adecuado para el modelo.

### 2. **División de datos y creación de lotes**

Crear lotes (batches) es un patrón común en proyectos de ML, y se usa para optimizar la carga de datos y el entrenamiento.

```python
BATCH_SIZE = 32
train_batches = raw_train.shuffle(num_examples // 4).map(format_image).batch(BATCH_SIZE).prefetch(1)
validation_batches = raw_validation.map(format_image).batch(BATCH_SIZE).prefetch(1)
test_batches = raw_test.map(format_image).batch(1)
```

- **`BATCH_SIZE`**: Define el tamaño de los lotes con los que se entrenará el modelo. Un valor típico para proyectos tinyML es 32 o menor, dependiendo de la capacidad del dispositivo.
- **`shuffle()`**: Baraja los datos de entrenamiento para evitar que el modelo aprenda patrones no deseados del orden de los datos.
- **`map()`**: Aplica la función de preprocesamiento `format_image` a cada imagen.
- **`batch()`**: Agrupa las imágenes en lotes del tamaño definido.
- **`prefetch(1)`**: Optimiza el proceso de carga de datos, cargando en paralelo el siguiente lote mientras el modelo está entrenando con el lote actual.

### 3. **Definición del modelo**

Ya sea usando un modelo preentrenado o un modelo simple, la arquitectura es una parte fundamental. Aquí se muestra la definición de un modelo secuencial típico.

```python
from tensorflow.keras import Sequential
from tensorflow.keras.layers import Dense

model = Sequential([
    Dense(units=1, input_shape=[1]),
])
```

- **`Sequential`**: Un tipo de modelo donde las capas se apilan una tras otra.
- **`Dense`**: Capa densa donde cada neurona está conectada a todas las neuronas de la capa anterior. Aquí se define una sola neurona con una entrada de un solo valor.

Este es el patrón básico de un modelo en TensorFlow o Keras, pero puede variar con capas adicionales, como convoluciones en modelos de imágenes o capas recurrentes para secuencias.

### 4. **Compilación y Entrenamiento del Modelo**

Este paso convierte la definición del modelo en algo que puede ser entrenado y optimizado.

```python
model.compile(optimizer='adam', loss='sparse_categorical_crossentropy', metrics=['accuracy'])
model.fit(train_batches, epochs=5, validation_data=validation_batches)
```

- **`compile()`**: Prepara el modelo para el entrenamiento. Los componentes clave son:
  - **`optimizer`**: Adam es un optimizador popular y eficiente.
  - **`loss`**: La función de pérdida `sparse_categorical_crossentropy` se utiliza cuando las etiquetas son enteros y no *one-hot encoded*.
  - **`metrics`**: `accuracy` evalúa el porcentaje de predicciones correctas.
  
- **`fit()`**: Inicia el entrenamiento del modelo durante 5 épocas (`epochs=5`), utilizando los lotes de datos de entrenamiento y validación.

### 5. **Guardado y Conversión del Modelo a TensorFlow Lite**

Después del entrenamiento, para usar el modelo en un dispositivo tinyML, es necesario convertirlo a un formato más eficiente: TensorFlow Lite.

```python
import tensorflow as tf

export_dir = 'saved_model/1'
tf.saved_model.save(model, export_dir)

converter = tf.lite.TFLiteConverter.from_saved_model(export_dir)
tflite_model = converter.convert()

import pathlib
tflite_model_file = pathlib.Path('model.tflite')
tflite_model_file.write_bytes(tflite_model)
```

- **`tf.saved_model.save()`**: Guarda el modelo completo (estructura, pesos y gráfico) en el directorio especificado.
- **`TFLiteConverter.from_saved_model()`**: Crea un convertidor para transformar el modelo en formato TFLite, que es mucho más ligero.
- **`convert()`**: Convierte el modelo a un archivo `.tflite`, optimizado para su uso en dispositivos móviles y embebidos.
- **`write_bytes()`**: Guarda el archivo `.tflite` en el sistema de archivos.

### 6. **Optimización del Modelo TFLite**

La optimización es clave para obtener modelos más pequeños y rápidos en dispositivos limitados.

```python
converter.optimizations = [tf.lite.Optimize.DEFAULT]
quantized_tflite_model = converter.convert()
```

- **`converter.optimizations`**: Se aplica una optimización predeterminada que busca reducir el tamaño del modelo y mejorar el rendimiento.
- **`quantized_tflite_model`**: El modelo cuantizado resultante tiene pesos en formato `int8` en lugar de `float32`, lo que reduce significativamente el tamaño.

### 7. **Evaluación del Modelo TFLite**

Para verificar que el modelo convertido funciona correctamente, se utiliza el intérprete de TensorFlow Lite.

```python
interpreter = tf.lite.Interpreter(model_path='model.tflite')
interpreter.allocate_tensors()

input_index = interpreter.get_input_details()[0]["index"]
output_index = interpreter.get_output_details()[0]["index"]

interpreter.set_tensor(input_index, test_image)
interpreter.invoke()
tflite_results = interpreter.get_tensor(output_index)
```

- **`Interpreter()`**: Carga el modelo TFLite para ser usado en inferencias.
- **`allocate_tensors()`**: Asigna los tensores que se usarán durante la inferencia.
- **`get_input_details()` y `get_output_details()`**: Proporcionan información sobre las formas y tipos de los tensores de entrada y salida del modelo.
- **`set_tensor()`**: Establece los valores de entrada para el modelo.
- **`invoke()`**: Realiza la inferencia.
- **`get_tensor()`**: Recupera los resultados de la inferencia.

### 8. **Cuantización Consciente de Entrenamiento (QAT)**

El entrenamiento consciente de cuantización es una técnica avanzada para hacer que los modelos sean más eficientes.

```python
import tensorflow_model_optimization as tfmot
quantize_model = tfmot.quantization.keras.quantize_model

q_aware_model = quantize_model(model)
q_aware_model.compile(optimizer='adam', loss='sparse_categorical_crossentropy', metrics=['accuracy'])
```

- **`tfmot.quantization.keras.quantize_model()`**: Transforma el modelo en uno compatible con el *entrenamiento consciente de cuantización*. Esto asegura que el modelo tenga en cuenta la cuantización mientras se entrena, sin perder precisión.

### 9. Post Training Quantization
El concepto de **Post-Training Quantization (PTQ)** es una técnica clave en _TinyML_ para optimizar modelos ya entrenados, reduciendo su tamaño y mejorando su eficiencia para ser ejecutados en dispositivos con recursos limitados, como teléfonos móviles o microcontroladores. Esta técnica se aplica **después de que el modelo ha sido entrenado**, a diferencia de la cuantización consciente durante el entrenamiento (_Quantization Aware Training_), que ajusta el modelo durante el proceso de entrenamiento.

#### **¿Dónde se realiza la Post-Training Quantization (PTQ)?**

En el código que me proporcionaste, la PTQ ocurre en las siguientes líneas clave:

```Python
converter = tf.lite.TFLiteConverter.from_keras_model(model)

# Aquí se aplica la optimización por cuantización.
converter.optimizations = [tf.lite.Optimize.DEFAULT]

tflite_quant_model = converter.convert()

tflite_model_quant_file = tflite_models_dir / "mnist_model_quant.tflite"
tflite_model_quant_file.write_bytes(tflite_quant_model)

```
### **Resumen General de Bloques Clave en tinyML:**
- **Carga y Preprocesamiento de Datos:** Redimensionar imágenes, normalización.
- **Creación de Lotes:** Uso de `batch()`, `shuffle()`, y `prefetch()`.
- **Definición de Modelos:** Usar `Sequential` y `Dense` o capas especializadas como `Conv2D`.
- **Compilación y Entrenamiento:** Uso de `compile()` y `fit()`.
- **Conversión a TensorFlow Lite:** Guardar y convertir modelos con `TFLiteConverter`.
- **Optimización del Modelo:** Cuantización mediante `converter.optimizations`.
- **Inferencia en TensorFlow Lite:** Uso de `Interpreter()` y `invoke()` para ejecutar modelos en dispositivos tinyML.

Estos bloques clave son fundamentales para desarrollar modelos tinyML eficientes y fáciles de desplegar en dispositivos de bajo rendimiento.


