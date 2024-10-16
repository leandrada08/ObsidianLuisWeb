
##  Entrenamiento de ConvNets en Práctica

### Divisiones del Dataset: Entrenamiento, Validación y Test
El entrenamiento de ConvNets requiere dividir el dataset disponible en diferentes subconjuntos para asegurar un entrenamiento adecuado y evitar problemas como el sobreajuste. Estas divisiones permiten medir el rendimiento del modelo y verificar si está generalizando correctamente.

- **Conjunto de Entrenamiento (Training Set)**:
  - Este conjunto se utiliza para ajustar los pesos de la red.
  - Representa la mayor parte de los datos disponibles, generalmente entre un 70% y un 80% del total, dependiendo del tamaño del dataset.

- **Conjunto de Validación (Validation Set)**:
  - Se utiliza para **evaluar el rendimiento** del modelo durante el proceso de entrenamiento, sin ajustar los pesos directamente.
  - Se usa para el **ajuste de hiperparámetros**, como la tasa de aprendizaje, el tamaño del batch, y el uso de técnicas de regularización.
  - Sirve para aplicar técnicas como **Early Stopping**, ya que ayuda a determinar cuándo el modelo ha dejado de mejorar.

- **Conjunto de Prueba (Test Set)**:
  - Este conjunto se usa para evaluar el rendimiento del modelo después de que haya sido completamente entrenado y ajustado.
  - Refleja la capacidad de **generalización** del modelo a datos no vistos, proporcionando una medida objetiva de su efectividad.

### Batch Size y su Impacto en el Entrenamiento
El **batch size** es el número de muestras que la red procesa antes de actualizar sus parámetros. Es un hiperparámetro importante que tiene un impacto significativo en el entrenamiento de las ConvNets.

- **Batch Size Grande**:
  - **Ventajas**: Proporciona estimaciones más estables de los gradientes, lo cual puede hacer que el proceso de optimización sea más suave.
  - **Limitaciones**: Requiere más memoria de GPU y puede resultar en tiempos de entrenamiento más lentos por actualización, pero a veces más rápidos por epoch.
  - **Uso en GPUs**: El entrenamiento con batch sizes grandes aprovecha mejor la paralelización de GPUs, pero no siempre permite capturar la variabilidad en los datos de forma efectiva.

- **Batch Size Pequeño**:
  - **Ventajas**: Permite una actualización más frecuente de los parámetros, lo cual puede llevar a un proceso de entrenamiento más dinámico y propenso a escapar de mínimos locales.
  - **Limitaciones**: Las estimaciones de gradiente tienden a ser más ruidosas, lo cual puede dificultar la convergencia a la solución óptima.

- **Mini-Batch Gradient Descent**:
  - La mayoría de los entrenamientos en la práctica usan un tamaño de batch que permite un compromiso adecuado entre estabilidad y eficiencia computacional.
  - Los tamaños de batch típicos van de **16 a 256**, dependiendo de los recursos disponibles.

### Entrenamiento Distribuido y Paralelización
Las **ConvNets profundas**, especialmente en grandes conjuntos de datos, requieren una gran cantidad de recursos computacionales. Para hacer frente a estas necesidades, se utilizan técnicas de entrenamiento distribuido y hardware especializado.

#### Uso de GPUs/TPUs
- **GPUs (Graphics Processing Units)**:
  - Las GPUs son capaces de realizar cálculos paralelos masivos, lo cual es ideal para operaciones matriciales intensivas que se requieren durante la propagación hacia adelante y hacia atrás de las ConvNets.
  - Utilizar **GPUs** permite reducir significativamente el tiempo de entrenamiento de modelos profundos, especialmente al manejar grandes cantidades de datos.

- **TPUs (Tensor Processing Units)**:
  - Las **TPUs**, desarrolladas por Google, son procesadores específicos optimizados para operaciones de tensor (multiplicaciones y adiciones en matrices), especialmente eficaces para entrenar modelos de redes neuronales.
  - Proporcionan una alternativa más rápida en ciertos casos, como el uso de plataformas en la nube para proyectos de gran escala.

#### Estrategias de Entrenamiento Distribuido
Cuando los modelos o los datos son demasiado grandes para ser manejados por una sola GPU o TPU, se emplean técnicas de **entrenamiento distribuido**:

- **Data Parallelism** (Paralelización de Datos):
  - **Descripción**: El dataset se divide entre diferentes dispositivos (como varias GPUs), cada uno de los cuales entrena una copia del modelo con una parte diferente del batch.
  - **Actualización de Parámetros**: Tras la propagación hacia atrás, los gradientes se combinan y se aplican para actualizar los pesos de forma sincronizada.
  - **Ventajas**: Es la forma más común de paralelización, ya que permite entrenar con lotes más grandes dividiéndolos entre varias GPUs.

- **Model Parallelism** (Paralelización de Modelo):
  - **Descripción**: El modelo se divide en varias partes, y cada parte se asigna a un dispositivo diferente.
  - **Ventajas**: Es útil cuando el modelo es demasiado grande para caber en la memoria de una sola GPU, como en redes extremadamente profundas o complejas.
  
- **Híbridos de Data y Model Parallelism**:
  - En algunos casos, se utiliza una combinación de paralelización de datos y de modelo para aprovechar al máximo los recursos computacionales disponibles, lo cual es particularmente útil en la investigación de arquitecturas muy profundas.

