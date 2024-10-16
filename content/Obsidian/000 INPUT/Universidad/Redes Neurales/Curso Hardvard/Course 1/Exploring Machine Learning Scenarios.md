

## Tipos de capas neuronales

### **Red Neuronal Densa** **(DNN)**
Cuando múltiples neuronas se agrupan en **capas**, pueden descubrir relaciones más complejas. En una red neuronal, las capas se conectan entre sí densamente, formando lo que se conoce como una **capa densa (Dense layer)**. Si hay múltiples capas entre la entrada y la salida, tienes una **red neuronal profunda (Deep Neural Network)**, que es la base de lo que llamamos **Deep Learning**.
### **Capas Recurrentes (RNN)**
Otro tipo de capa son las **capas recurrentes (Recurrent Neural Networks, RNNs)**. Estas capas son capaces de aprender secuencias de datos. En una capa recurrente, los valores se pasan de una neurona a la siguiente dentro de la misma capa, permitiendo que la información fluya a lo largo de la secuencia.
Un ejemplo potente de este tipo de red es el **Long Short Term Memory (LSTM)**, que es capaz de mantener un **estado de memoria** (Cell State) que puede influir en el aprendizaje no solo de las neuronas cercanas, sino también de neuronas más alejadas en la secuencia. Esto es especialmente útil para tareas de secuencias largas, como la predicción de series temporales o el procesamiento de texto.
![[Captura de pantalla 2024-10-10 a las 1.06.20 p. m..png]]


![[Captura de pantalla 2024-10-10 a las 1.07.01 p. m..png]]
### **Capas Convolucionales (CNN)**
Además de las capas recurrentes, hay **capas convolucionales (Convolutional Neural Networks, CNNs)**, que son especialmente útiles para trabajar con datos de imágenes. En lugar de aprender parámetros simples como **w** y **b**, las CNNs utilizan **filtros** que transforman los datos de entrada (imágenes) y permiten que el modelo reconozca patrones como bordes, texturas o formas.




## **Recapitulación**
- **Neuronas simples**: Al principio, una sola neurona puede aprender la relación lineal entre **x** e **y** en la ecuación **y = wx + b**.
- **Capas densas**: Varias neuronas en capas densas pueden aprender relaciones complejas y clasificar imágenes simples, como dígitos escritos a mano.
- **Problemas con imágenes complejas**: Cuando las imágenes se vuelven más complejas, como fotos de personas o caballos, las capas densas no son suficientes para capturar detalles como el fondo, la ubicación, y otros detalles intrincados. Aquí es donde las convoluciones son útiles.

### **Filtros y Convoluciones**
- Un **filtro** es una matriz que se pasa sobre la imagen para analizar las relaciones entre píxeles. 
- Al aplicar el filtro a una imagen, se multiplican los valores de los píxeles por los valores del filtro y se suman para producir un nuevo valor de píxel.
- Esto permite detectar características importantes como **líneas verticales u horizontales**.

Por ejemplo, en una imagen de un botín, se pueden usar filtros para detectar líneas verticales u horizontales en los bordes del objeto. Estas características se denominan **extracción de características** (feature extraction).

### **Pooling**
- El **pooling** es una técnica que reduce el tamaño de los datos conservando las características más importantes.
- Se toma un conjunto de píxeles (como un bloque 2x2), y se selecciona el valor máximo, eliminando los demás. Esto ayuda a reducir la cantidad de datos, lo que mejora la eficiencia de la red sin perder información crucial.

### **Uso de Filtros para Reconocer Imágenes**
- Los filtros no solo detectan características básicas como líneas, sino que también pueden aprender a identificar elementos más complejos como **manos, rostros** o **piernas**.
- A través del entrenamiento, la red neuronal puede asociar ciertas características extraídas con clases específicas de imágenes. Por ejemplo, si los filtros identifican consistentemente **piernas, manos y rostros** en imágenes etiquetadas como "humano", la red aprenderá a asociar esas características con la clase "humano".

### **Entrenamiento de Filtros**
- Al igual que los pesos y sesgos en las neuronas, los valores de los filtros se inicializan de manera aleatoria y luego se ajustan durante el entrenamiento.
- El proceso de entrenamiento optimiza los valores del filtro a través de la minimización de la **pérdida** (loss), de forma similar a cómo se ajustan los pesos en una capa densa.

### **Aplicaciones y Ejemplos**
- Un ejemplo interesante de la utilización de filtros en redes profundas es **DeepDream**, donde las características extraídas de una imagen se superponen en ella, creando efectos visuales similares a sueños.

- **Ejemplo de Red Neuronal Convolucionales:** https://colab.research.google.com/github/tinyMLx/colabs/blob/master/2-3-3-ExploringConvolutions.ipynb



## **Recapitulación del modelo DNN**
- El modelo básico que hemos usado hasta ahora tiene capas densas (fully connected) y utiliza **MNIST** o **Fashion MNIST**. En el caso de Fashion MNIST, el modelo DNN obtiene una precisión del 89.53% y una precisión de validación del 86.77% tras 20 épocas.
- Aunque estos resultados son buenos, podemos mejorarlos al introducir **convoluciones** para extraer mejor las características de las imágenes.

### **Modelo CNN (Red Neuronal Convolucional)**
El nuevo modelo incluye capas convolucionales que permiten identificar características más complejas en imágenes, como bordes y texturas, mediante el uso de filtros.

1. **Input Shape**: 
   - En las capas convolucionales, se especifica el tamaño de la entrada como **28x28x1** para imágenes monocromáticas (28x28 píxeles con 1 canal de color). Para imágenes en color, sería algo como **28x28x3**.
   
2. **Capas Convolucionales (Conv2D)**:
   - Se define la primera capa convolucional usando **Conv2D**. El primer parámetro, **64**, indica el número de **filtros** que se aplicarán a la imagen. Estos filtros serán aprendidos durante el entrenamiento.
   - El tamaño del filtro es especificado con **3x3**, lo que significa que se aplicará a cada píxel y sus vecinos inmediatos. Los tamaños de filtros son generalmente impares (3x3, 5x5, etc.) para poder abarcar un centro y sus alrededores.

3. **Pooling**:
   - Se aplica una capa de **max pooling** (agrupar píxeles y seleccionar el valor máximo) después de cada convolución. En este ejemplo, el tamaño del pool es **2x2**, lo que reduce el tamaño de la imagen al seleccionar un píxel de cada cuatro. Esto ayuda a reducir la cantidad de datos y, a la vez, resalta las características más importantes.

4. **Flatten y capas densas**:
   - Una vez que las capas convolucionales y de pooling han extraído y reducido la información de la imagen, los datos son **flattened** (aplanados) antes de ser pasados a capas densas, que funcionan como en el modelo original.

### **Impacto de los parámetros de la capa convolucional**
- **Número de filtros**: En este ejemplo se usaron 64 filtros. Esto significa que, tras aplicar estos filtros, se generarán 64 copias modificadas de la imagen original, cada una destacando diferentes características.
- **Tamaño del filtro (3x3)**: Controla cuántos píxeles vecinos se consideran al aplicar el filtro.
- **Pooling**: Reduce el tamaño de la imagen después de cada convolución para minimizar los datos sin perder características importantes.

### **Beneficios de las CNN**
Las capas convolucionales permiten que el modelo aprenda patrones más complejos en imágenes, lo que resulta en una mayor precisión en tareas de clasificación visual. Al reducir los datos a través del pooling, el modelo puede enfocarse en los aspectos esenciales sin procesar innecesariamente demasiada información.

- **Ejemplo:** https://colab.research.google.com/github/tinyMLx/colabs/blob/master/2-3-5-FashionMNISTConvolutions.ipynb




## **Filtros en Convoluciones**
Los **filtros** son patrones que se aplican sobre una imagen para identificar ciertas características o patrones consistentes. En el ejemplo:

1. **Filtro de piernas humanas**: Extrae siempre características parecidas a cilindros que podrían corresponder a piernas cuando la imagen está etiquetada como **humano**.
   
2. **Filtro de manos humanas**: Extrae formas similares a manos en imágenes etiquetadas como **humano**.

3. **Filtro de rostros humanos**: Identifica características como ojos y boca que se encuentran en imágenes etiquetadas como **humanos**.

Cuando un modelo está entrenado correctamente, aprende que cuando estos tres filtros (u otros) detectan características específicas, la imagen probablemente pertenece a la clase **humano**. Por lo tanto, combina la información de los filtros y concluye "es un humano". Si los filtros no detectan nada significativo para esa clase, el modelo pasa a analizar otros filtros para otras clases, como **caballos**.
![[Captura de pantalla 2024-10-10 a las 1.14.32 p. m..png]]
![[Captura de pantalla 2024-10-10 a las 1.14.41 p. m..png]]
### **Interpretabilidad**

El concepto clave aquí es que la red no necesita detectar patrones que nosotros como humanos reconocemos fácilmente, como piernas o rostros. Podría encontrar patrones que no son tan evidentes para nosotros, pero que son constantes en imágenes etiquetadas de una clase específica, haciendo que el modelo sea más eficiente y preciso para la tarea de clasificación. Este proceso es la base de cómo las redes convolucionales aprenden a interpretar imágenes complejas.

### **Visualización de Convoluciones**
Es fascinante cómo los estudios de **visualización de convoluciones** pueden revelar qué características específicas están aprendiendo las redes. A veces, los patrones no son tan evidentes para los humanos, pero el modelo los utiliza para tomar decisiones precisas. Esto demuestra que, mientras un humano puede identificar objetos a partir de características tangibles, los modelos de machine learning pueden detectar patrones más sutiles y, a veces, más efectivos.

Así, la capacidad de las redes convolucionales de aprender a "ver" imágenes va más allá de lo que un ojo humano podría hacer, lo que las hace especialmente útiles en tareas como la visión por computadora.


- **Ejemplo:** Red neuronal terminada por mi https://colab.research.google.com/github/tinyMLx/colabs/blob/master/2-3-9-AssignmentQuestion.ipynb#scrollTo=P1L6kq5wJquF



