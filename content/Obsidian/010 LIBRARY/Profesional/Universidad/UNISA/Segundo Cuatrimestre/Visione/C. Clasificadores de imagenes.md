
En lugar de decirle a la computadora exactamente cómo se ve un "gato" o un "perro", lo que hacemos es darle muchos ejemplos de cada categoría. Así, la computadora aprende por sí misma a identificar las características de cada clase basándose en esos ejemplos. Este método se llama **aprendizaje basado en datos**.

**¿Cómo funciona la clasificación?**  
Para clasificar imágenes, seguimos estos pasos:

1. **Entrenamiento**: Le damos a la computadora un conjunto de imágenes con etiquetas para que aprenda cómo se ve cada categoría.
2. **Aprender**: La computadora usa estas imágenes para entender las características de cada categoría.
3. **Evaluación**: Luego se le dan nuevas imágenes (que no ha visto antes) y se le pide que adivine la etiqueta. Comparamos sus respuestas con las correctas para ver qué tan bien está funcionando.

## Clasificador de Vecinos Más Cercanos (kNN)
Imagina que tienes una nueva imagen de prueba y necesitas etiquetarla. El clasificador kNN lo que hace es comparar esa imagen con todas las imágenes de entrenamiento que tiene almacenadas, buscando las más similares. La etiqueta de la imagen más parecida se usa como predicción.
Podemos usar diferentes formas de medir qué tan parecidas son las imágenes. Por ejemplo:
- **Distancia L1**: Calcula las diferencias absolutas entre todos los píxeles y las suma. $$d_1(I_1,I_2)=\sum_p|I_1^p-I_2^p|$$![[Captura de pantalla 2024-09-30 a las 4.42.56 p. m..png]]
- **Distancia L2**: Similar a L1, pero las diferencias se elevan al cuadrado y luego se toma la raíz cuadrada, lo cual da más peso a diferencias grandes. $$d_2(I_1,I_2)=\sqrt{\sum_p(I_1^p-I_2^p)^2}$$

## **k-Vecinos Más Cercanos**  
En lugar de considerar solo la imagen más cercana, también podemos considerar los "k" vecinos más cercanos y hacer que todos "voten" para decidir la etiqueta. Esto ayuda a que el clasificador sea más resistente si algunas imágenes tienen ruido o son difíciles de identificar. Ajustar el valor de "k" es un proceso importante para que el clasificador sea más preciso. Por ejemplo, si estás clasificando gatos y perros y la mayoría de los vecinos de la imagen son perros, la imagen se clasifica como un perro.
![[Captura de pantalla 2024-09-30 a las 5.02.08 p. m..png]]

### **Ajuste de Hiperparámetros y Validación**  

Los **hiperparámetros** son configuraciones que se establecen antes de que el modelo empiece a aprender, y no se ajustan automáticamente durante el proceso de entrenamiento. Son como los "controles" del modelo, y tú decides qué valores usar. Algunos ejemplos de hiperparámetros en el kNN serían:

- **k**: El número de vecinos que se considerarán al hacer la clasificación (¿uno solo o varios?).
- **Tipo de distancia**: Cómo se mide la similitud entre las imágenes, usando la distancia L1, L2, u otra.

#### Ajuste de Hiperparámetros: ¿Cómo encontramos los mejores valores?
El problema con los hiperparámetros es que no sabemos cuál es el mejor valor hasta que vemos cómo afecta el rendimiento del modelo. Aquí es donde entra el **ajuste de hiperparámetros**: básicamente probamos con varios valores diferentes para ver cuál funciona mejor.

Por ejemplo, imaginemos que queremos saber si es mejor usar **k = 3** o **k = 5** en el kNN. Para eso necesitamos evaluar el rendimiento del modelo con cada valor y comparar los resultados.

#### Validacion
Una cosa importante es que **nunca usamos el conjunto de pruebas para ajustar los hiperparámetros**. Esto se debe a que el conjunto de pruebas está reservado para ver cómo el modelo se comporta con datos que no ha visto antes, simulando su rendimiento en el "mundo real". Si ajustáramos los hiperparámetros directamente en el conjunto de pruebas, podríamos hacer que el modelo se adapte demasiado a esos datos en particular, lo cual es engañoso porque queremos que el modelo funcione bien con cualquier dato, no solo con los datos de prueba específicos.

Para saber qué valores de hiperparámetros funcionan mejor, usamos una parte de nuestros datos llamada **conjunto de validación**. 

- Primero, dividimos nuestros datos en tres conjuntos:
  1. **Conjunto de entrenamiento**: Se usa para enseñar al modelo.
  2. **Conjunto de validación**: Se usa para probar distintos valores de hiperparámetros y ver cuál da mejores resultados. 
  3. **Conjunto de pruebas (test)**: Se usa al final para verificar qué tan bien funciona el modelo.

**Validación** significa que probamos diferentes configuraciones del modelo (por ejemplo, diferentes valores de k) usando el conjunto de validación, para ver cuál es la mejor configuración antes de probar el modelo en el conjunto de pruebas final. De esta manera, nos aseguramos de que estamos usando los mejores valores de hiperparámetros para obtener la mayor precisión posible.


##### Validación Cruzada
A veces, el conjunto de datos es muy pequeño, y dividirlo podría dejarnos con pocos datos para entrenar y validar. En esos casos, usamos una técnica llamada **validación cruzada**. 

En la **validación cruzada**, dividimos los datos de entrenamiento en varias partes (llamadas "pliegues") y usamos cada parte como conjunto de validación mientras el resto se usa para entrenar. Repetimos esto varias veces y luego promediamos los resultados para obtener una buena estimación del rendimiento del modelo con cada valor de hiperparámetro. Esto ayuda a que los resultados sean más confiables y menos dependientes de cómo hayamos dividido los datos.

- En la practica, si se tiene un numero suficientemente grande de datos, se suele evitar la validacion cruzada por su coste computacional.
	- Se suele tomar entre el 50% y el 90% para el entrenamiento y el restante para la valdiacion
- Si se tiene un conjunto de datos muy pequeños, se suele hacer validacion cruzada de 3,5 o 10 pliegues
![[Captura de pantalla 2024-09-30 a las 5.48.20 p. m..png]]
#### **Pros y Contras del kNN**  
El kNN tiene algunas ventajas, como que es muy fácil de entender e implementar. Sin embargo, tiene dos grandes problemas:

- **Almacenamiento**: kNN necesita almacenar todas las imágenes de entrenamiento, lo cual requiere mucho espacio.
- **Lento**: Comparar una imagen de prueba con todas las imágenes de entrenamiento puede ser muy costoso en términos de tiempo.

Para superar estas limitaciones, usamos el **clasificador lineal**, que es más eficiente y directo. En este método, en lugar de almacenar todas las imágenes, aprendemos unos **parámetros** (o "pesos") que nos permiten predecir la clase de una imagen con una operación matemática simple.




## Linear Classification
La **clasificación lineal** es un enfoque fundamental, su objetivo es encontrar una relación lineal que separe los datos de entrada (en este caso, imágenes) en diferentes clases. Este tipo de clasificador tiene una forma relativamente simple y sirve como base conceptual para modelos más avanzados.

En la clasificación de imágenes, se representa la imagen como un vector de características y se calcula una combinación lineal de esas características para determinar la clase. Esta combinación lineal tiene la forma:

$$
f(x) = W x + b
$$

Donde:
- $W$(tamaño \[K x D]) es una matriz de pesos que mapea el vector de características al espacio de las clases.
- $x$(tamaño \[D x 1]) es el vector de características de la imagen.
- $b$(tamaño \[K x 1]) es el vector de sesgos que desplaza la predicción.
- El resultado de esta operación son **puntuaciones de clase**, que luego se interpretan para determinar cuál es la clase de la imagen.

- Lo parametros en W a menudo se llaman pesos y B se llama vector de sesgo porque influye en las puntuaciones de salida, pero sin interactuar con los datos reales X
![[Captura de pantalla 2024-09-30 a las 5.57.48 p. m..png]]
### 2. Parameterized Mapping from Images to Label Scores
La operación de **mapping parametrizado** de imágenes a puntajes de clases implica ajustar los pesos $W$ y los sesgos $b$ para que el clasificador pueda hacer predicciones precisas. En el contexto de clasificación de imágenes, este mapeo significa aprender una combinación de características que permita discriminar entre distintas clases.

Para entrenar el clasificador, los parámetros $W$ y $b$ se ajustan mediante un proceso de optimización que minimiza una **función de pérdida** (o loss function), que mide qué tan bien se están clasificando las imágenes.

### 3. Interpreting a Linear Classifier
Un **clasificador lineal** asigna una puntuación a cada clase basándose en una combinación lineal de características. Si estamos trabajando, por ejemplo, con una clasificación de tres clases (gato, perro y conejo), los valores $W$ y $b$ se ajustan de tal forma que la puntuación más alta indique la clase más probable.

Cada fila de la matriz de pesos $W$ representa una clase, y cada columna corresponde a un valor de la característica. Así, la interpretación de un clasificador lineal es que cada clase tiene una “plantilla” específica que describe cómo deberían combinarse las características de entrada para predecir esa clase. Si consideramos los pesos como filtros, podemos imaginar que cada clase tiene una "mirada" distinta hacia el vector de características.

### 4. Loss Function
La **función de pérdida** mide qué tan bien el modelo está prediciendo las clases correctas. En el contexto de clasificación lineal, el objetivo es minimizar esta pérdida para mejorar la precisión de las predicciones.

- **Función de Pérdida Hinge**: En el caso de las **Máquinas de Soporte Vectorial** (SVM), se utiliza una función de pérdida llamada **Hinge Loss**. Esta función busca maximizar el margen entre clases, penalizando ejemplos incorrectamente clasificados y aquellos que se encuentran demasiado cerca del margen.

- **Entropía Cruzada (Cross-Entropy)**: Es otra pérdida utilizada con el **clasificador Softmax**, que mide la discrepancia entre las distribuciones de probabilidad predicha y la real. Penaliza fuertemente cuando el modelo da alta probabilidad a la clase incorrecta.

### 5. Multiclass Support Vector Machine (SVM) Loss
La **pérdida de SVM para múltiples clases** o **Multiclass SVM loss** es una extensión de la SVM binaria, utilizada para problemas donde se tienen más de dos clases. La fórmula general para la pérdida de SVM está dada por:

$$
L = \sum_{i \neq y} \max(0, s_i - s_y + \Delta)
$$

Donde:
- $s_i$ es la puntuación de la clase $i$.
- $s_y$ es la puntuación de la clase correcta.
- $\Delta$ es un margen fijo, que se utiliza para asegurar que la diferencia entre la puntuación correcta y las demás sea suficientemente grande.

La pérdida SVM busca que la puntuación de la clase correcta sea superior a la de cualquier otra clase por al menos un margen \(\Delta\). De lo contrario, hay una penalización proporcional a la diferencia.

### 6. Practical Considerations
En la práctica, hay varios aspectos a tener en cuenta al entrenar un clasificador lineal:
- **Regularización**: Para evitar el sobreajuste, es importante regularizar los pesos del modelo. Esto se hace comúnmente añadiendo un término a la función de pérdida, como la **regularización L2** (\(\lambda ||W||^2\)), que penaliza grandes valores de los parámetros.
  
- **Optimizadores**: Los parámetros del clasificador (pesos y sesgos) se ajustan usando **métodos de optimización** como el **Descenso de Gradiente Estocástico** (SGD). Para problemas de clasificación lineal con grandes conjuntos de datos, usar mini-batches y técnicas avanzadas de optimización (como Adam o RMSprop) puede acelerar el proceso.

### 7. Softmax Classifier
El **clasificador Softmax** es otro tipo de clasificador lineal pero con una diferencia clave: en lugar de asignar puntajes sin normalizar, utiliza la **función Softmax** para convertir estos puntajes en probabilidades que suman 1 para todas las clases:

$$
P(y = k | x) = \frac{e^{s_k}}{\sum_{j} e^{s_j}}
$$

Donde:
- $s_k$ es la puntuación de la clase $k$.
  
La pérdida asociada al clasificador Softmax es la **entropía cruzada**. A diferencia de SVM, el objetivo es que la probabilidad de la clase correcta sea lo más cercana posible a 1.

### 8. SVM vs. Softmax
- **SVM**: Tiende a maximizar el margen entre clases. En problemas donde las clases son bien separables, SVM puede ser más robusto.
  
- **Softmax**: Utiliza la entropía cruzada para ajustar las probabilidades y puede ser más efectivo en casos donde las clases no son claramente separables o cuando se requiere interpretar las predicciones en términos de probabilidades.

Ambos métodos se basan en una combinación lineal de las características, pero su enfoque sobre cómo tratar los ejemplos incorrectamente clasificados es diferente, lo cual lleva a distintos comportamientos en escenarios reales.

### 9. Interactive Web Demo
Es común encontrar **demos interactivas** que permiten visualizar cómo se ajusta un clasificador lineal. Estas demos suelen ofrecer un conjunto de datos bidimensional y permiten ajustar los parámetros y ver cómo cambia la frontera de decisión. Estos tipos de herramientas son útiles para comprender la intuición detrás de los clasificadores lineales.

### 10. Summary
- Los **clasificadores lineales** son modelos relativamente simples que se basan en una combinación lineal de características para separar las clases.
- Los métodos como **SVM** y **Softmax** ofrecen diferentes enfoques para definir y optimizar la separación de clases.
- Los aspectos prácticos incluyen la regularización, la selección de hiperparámetros, y el uso de funciones de pérdida adecuadas para cada situación.

### 11. Further Reading
Para entender más sobre los clasificadores lineales y cómo se aplican en el contexto de redes neuronales, recomendaría explorar temas como:
- **Descenso de Gradiente y Optimizadores**.
- **Teoría de márgenes en SVM**.
- **Aplicación del Softmax en arquitecturas neuronales profundas**.

Con esto hemos cubierto los conceptos básicos de clasificación lineal, sus variantes, y los puntos prácticos a tener en cuenta. ¿Qué dudas tienes sobre esta sección antes de pasar a la siguiente?