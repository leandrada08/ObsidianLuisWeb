
## Clase 1

Cuando trabajaste con **MNIST** o **Fashion MNIST**, fue muy fácil porque:
1. Solo tenías que cargar los datos con dos líneas de código.
2. Ya venían listos para usarse, preprocesados y con sus etiquetas (números que representan las clases).
Esto es muy cómodo, pero no es la realidad para la mayoría de los proyectos del mundo real. En el mundo real, los datos no vienen tan ordenados ni fáciles de usar. En lugar de datasets simples como MNIST, normalmente tienes que:
1. **Descargar y organizar imágenes manualmente** (por ejemplo, si trabajas con imágenes de perros y gatos, tendrías que poner las fotos de cada categoría en su propia carpeta).
2. **Preprocesarlas** (normalizarlas, ajustar tamaños, etc.).
3. **Etiquetarlas** (las etiquetas no suelen venir listas; muchas veces tienes que generar las etiquetas basándote en nombres de archivos o carpetas).

Aquí es donde entran las herramientas como **ImageDataGenerator** y **TensorFlow Datasets (TFDS)**, que te ayudan a organizar y preparar los datos de manera eficiente.

### API de Splits y Funciones de Mapeo
TFDS tiene dos conceptos importantes que debes aprender:

1. **API de Splits**: Te permite dividir el conjunto de datos en subconjuntos (entrenamiento, prueba, validación). Por ejemplo:
   ```python
   data = tfds.load('horses_or_humans', split='train', as_supervised=True)
   ```
   Aquí estamos cargando el conjunto de datos "horses_or_humans" y solicitamos el subconjunto de entrenamiento.

2. **Funciones de Mapeo (Mapping Functions)**: Estas funciones te permiten aplicar transformaciones a las imágenes, como la **Augmentación de Imágenes** (aumentar el tamaño de los datos mediante transformaciones como voltear imágenes). Si ya no estás usando generadores de imágenes, puedes usar la función `map()` de TFDS para hacerlo fácilmente.


Por ejemplo, si deseas cargar **Fashion MNIST** usando TFDS, el código sería así:

```python
import tensorflow as tf
import tensorflow_datasets as tfds

# Cargar el dataset de Fashion MNIST
mnist_data = tfds.load("fashion_mnist")

# Explorar el dataset
for item in mnist_data:
    print(item)
```

- Beneficios de TFDS
	- **Acceso simplificado a múltiples tipos de datos**: Imágenes, texto, audio, etc.
	- **Preprocesamiento automático**: TFDS se encarga de preparar los datos para el entrenamiento, lo que ahorra tiempo y esfuerzo.
	- **Splits flexibles**: Puedes dividir los datos fácilmente en subconjuntos como entrenamiento, validación y prueba.
	- **Augmentación**: Permite aplicar transformaciones a los datos para mejorar el rendimiento del modelo.


### Preparación de los datos
A diferencia de MNIST, que estaba fácilmente disponible en TensorFlow, ahora trabajaremos con un conjunto de datos almacenado en directorios. Cada directorio contendrá imágenes etiquetadas en carpetas según su clase (caballos o humanos). La estructura de las carpetas será algo así:
```
/train/horses
/train/humans
/validation/horses
/validation/humans
```
![[Captura de pantalla 2024-10-10 a las 5.38.05 p. m..png]]






- **Codigo de ejemplo:** https://colab.research.google.com/github/tinyMLx/colabs/blob/master/2-4-3-HorsesOrHumans.ipynb



## Clase 2

Lo que Laurence Moroney te está explicando en esta clase es un concepto clave en Machine Learning: **overfitting** o **sobreajuste**. Aquí te lo explico en términos sencillos:

### **¿Qué es el overfitting?**
El **overfitting** ocurre cuando tu modelo se ajusta demasiado bien a los datos de entrenamiento, al punto de que se vuelve "especialista" en esos datos y no generaliza bien en datos nuevos. Es como si aprendiera de memoria los ejemplos, pero no entendiera realmente el concepto.

Imagina que estás entrenando a un modelo para reconocer zapatos. Si solo le enseñas botas de montaña, el modelo podría aprender a identificar solo ese tipo de zapatos. Luego, cuando le muestras otro tipo de zapatos, como zapatillas, no sabe reconocerlos porque ha "sobreaprendido" a identificar botas de montaña específicamente. Esto es lo que pasa cuando hay **overfitting**.

### **¿Cómo evitar el overfitting?**
Para evitar que el modelo se sobreajuste, se utilizan técnicas de **data augmentation** (aumento de datos), que permiten "aumentar" el tamaño del dataset sin necesidad de agregar más imágenes. Se crean nuevas variaciones de las imágenes originales para que el modelo vea más diversidad. Algunas técnicas incluyen:

1. **Rotación**: Girar las imágenes aleatoriamente (hasta cierto ángulo). Esto ayuda al modelo a reconocer los objetos aunque estén inclinados.
   
2. **Desplazamiento**: Mover las imágenes hacia arriba, abajo, izquierda o derecha. Esto evita que el modelo aprenda que los objetos siempre están en el centro.
   
3. **Zoom**: Ampliar o reducir las imágenes para que el modelo no dependa del tamaño exacto del objeto.
   
4. **Shearing (Sesgado)**: Cambiar el ángulo de los objetos para simular que están "inclinados" hacia un lado.
   
5. **Volteo horizontal**: Voltear las imágenes horizontalmente. Esto es útil, por ejemplo, si entrenas con personas levantando la mano derecha, pero también necesitas que el modelo reconozca cuando levanten la mano izquierda.

### **¿Cómo se hace esto en código?**
Todo esto lo puedes hacer automáticamente usando una herramienta llamada **ImageDataGenerator**, que crea esas variaciones de las imágenes mientras entrena el modelo. Aquí algunos ejemplos de los parámetros que podrías usar:

- **rotation_range**: Gira la imagen aleatoriamente hasta un máximo de grados.
- **width_shift_range y height_shift_range**: Desplaza la imagen a lo largo del ancho y alto.
- **zoom_range**: Aplica zoom aleatoriamente a las imágenes.
- **horizontal_flip**: Voltea la imagen de manera horizontal.
- **shear_range**: Sesga la imagen.

### **¿Por qué esto es importante en la vida real?**
En el mundo real, las imágenes no siempre están bien centradas o perfectamente orientadas, por lo que es crucial que tu modelo sea capaz de reconocer patrones en diferentes situaciones. Si solo entrenas con imágenes "perfectas", cuando el modelo se enfrente a una imagen ligeramente diferente (un poco inclinada o con partes faltantes), podría fallar.

En esta clase se introdujo el concepto de **dropout regularization** como una técnica para combatir el **sobreajuste** (overfitting) en las redes neuronales. Aquí te lo explico de forma más simple:

### **¿Qué es el sobreajuste (overfitting)?**
El sobreajuste ocurre cuando una red neuronal se vuelve demasiado "experta" en los datos de entrenamiento, pero no generaliza bien cuando se enfrenta a datos nuevos o diferentes. Es como aprenderse de memoria las respuestas para un examen sin entender el tema.

### **¿Qué es el Dropout y cómo ayuda?**
El **dropout** es una técnica para evitar que la red se vuelva demasiado especializada en los datos de entrenamiento. Consiste en **apagar** (temporalmente) un porcentaje aleatorio de neuronas durante el entrenamiento, lo que obliga a la red a no depender tanto de las neuronas individuales. De esta manera, la red se vuelve más generalizable y menos propensa a sobreajustarse.

### **¿Cómo funciona el Dropout en la red neuronal?**
1. **Normal**: En una red densa normal, cada neurona se conecta con todas las neuronas de la siguiente capa, lo que puede llevar a que algunas neuronas se vuelvan demasiado importantes.
   
   Imagina que en una red neuronal tienes muchas conexiones entre neuronas. Algunas neuronas pueden volverse "demasiado poderosas", y esto puede afectar a las neuronas de las capas siguientes, generando un sobreajuste.

2. **Con Dropout**: Con el **dropout**, se apagan al azar algunas de esas neuronas y sus conexiones durante el entrenamiento. Esto ayuda a que las neuronas restantes hagan el trabajo de aprender los patrones, lo que impide que algunas se vuelvan demasiado especializadas.

   Cuando se activan solo algunas neuronas, el modelo aprende de manera más equilibrada, ayudando a que sea más robusto frente a diferentes entradas de datos.

### **Implementación en código**
En Keras (la API de TensorFlow), es muy sencillo implementar el dropout. Solo tienes que agregar una capa `Dropout()` a tu modelo. Por ejemplo, para apagar el 20% de las neuronas en una capa, se usa:

```python
tf.keras.layers.Dropout(0.2),
```

Esto significa que durante el entrenamiento, el 20% de las neuronas en esa capa serán desactivadas al azar.

### **Ejemplo con Fashion MNIST**
Si tomas una red más grande, con varias capas densas (como el siguiente ejemplo), puedes ver signos de sobreajuste. La red tiene muchas capas densas que pueden sobreespecializarse.

```python
model = tf.keras.models.Sequential([
    tf.keras.layers.Flatten(input_shape=(28,28)),
    tf.keras.layers.Dense(256, activation=tf.nn.relu),
    tf.keras.layers.Dense(128, activation=tf.nn.relu),
    tf.keras.layers.Dense(64, activation=tf.nn.relu),
    tf.keras.layers.Dense(10, activation=tf.nn.softmax)
])
```

Al entrenarla, el modelo puede lograr una precisión del **94% en el conjunto de entrenamiento**, pero solo **88.5% en el conjunto de validación**. Esta diferencia indica que podría haber sobreajuste.

Ahora, al agregar **dropout** después de cada capa densa, se fuerza al modelo a "trabajar más" para aprender patrones sin depender tanto de neuronas individuales.

```python
model = tf.keras.models.Sequential([
    tf.keras.layers.Flatten(input_shape=(28,28)),
    tf.keras.layers.Dense(256, activation=tf.nn.relu),
    tf.keras.layers.Dropout(0.2),
    tf.keras.layers.Dense(128, activation=tf.nn.relu),
    tf.keras.layers.Dropout(0.2),
    tf.keras.layers.Dense(64, activation=tf.nn.relu),
    tf.keras.layers.Dropout(0.2),
    tf.keras.layers.Dense(10, activation=tf.nn.softmax)
])
```

Con dropout, la precisión en el conjunto de entrenamiento baja un poco (**89.5%**), pero la precisión en el conjunto de validación se mantiene casi igual (**88.3%**). Esto muestra que la red ahora está menos sobreajustada y es mejor para generalizar con datos nuevos.

Aquí tienes el texto reescrito:

---

**Explorando funciones de pérdida y optimizadores**

Hasta este punto, te han guiado a través de diferentes funciones de pérdida y optimizadores que puedes usar al entrenar una red.

Es bueno explorarlos por ti mismo, así como entender cómo declararlos en TensorFlow, ¡especialmente aquellos que pueden aceptar parámetros!

Ten en cuenta que generalmente hay dos formas en que puedes declarar estas funciones: por nombre, usando un string literal, o por objeto, definiendo el nombre de la clase de la función que deseas usar.

Aquí tienes un ejemplo de cómo hacerlo por nombre:

```python
optimizer = 'adam'
```

Y uno usando la sintaxis funcional:

```python
from tensorflow.keras.optimizers import Adam
opt = Adam(learning_rate=0.001)

optimizer = opt
```

Usar el primer método es obviamente más rápido y fácil, y no necesitas importar nada, lo cual es fácil de olvidar, en particular si estás copiando y pegando código de otro lado. ¡Usar el segundo método tiene la ventaja de permitirte ajustar hiperparámetros internos, como la tasa de aprendizaje, dándote un control más detallado sobre cómo aprende tu red!

Puedes aprender más sobre la suite de **optimizadores** en TensorFlow en [este enlace](https://www.tensorflow.org/api_docs/python/tf/keras/optimizers) — hasta este punto has visto SGD, RMSProp y Adam, y te recomendaría que investigues lo que hacen. Después de eso, considera leer sobre algunos de los otros, en particular las mejoras al algoritmo Adam que están disponibles.

De manera similar, puedes aprender sobre las **funciones de pérdida** en TensorFlow en [este enlace](https://www.tensorflow.org/api_docs/python/tf/keras/losses), y hasta ahora has visto Mean Squared Error, Binary CrossEntropy y Categorical CrossEntropy. Léelos para ver cómo funcionan, y también investiga algunos otros que son mejoras de estos.

Cuando termines, vuelve a algunos de los ejercicios o notebooks que has hecho, y experimenta con diferentes funciones de pérdida u optimizadores. En particular, intenta modificar cosas como la tasa de aprendizaje u otros parámetros para ver si puedes mejorar tus modelos.

---

Espero que esto te sea útil. ¿Te gustaría ahondar en algún tema?
# No sirve?















