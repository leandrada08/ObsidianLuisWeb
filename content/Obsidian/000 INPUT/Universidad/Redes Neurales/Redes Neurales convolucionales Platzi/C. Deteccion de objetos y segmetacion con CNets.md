
## Detección de Objetos
La **detección de objetos** consiste en identificar y localizar múltiples objetos dentro de una imagen. Este proceso es mucho más complejo que simplemente clasificar una imagen, ya que implica determinar tanto la clase del objeto como su ubicación en la imagen mediante **cuadros delimitadores (bounding boxes)**. Algunos de los enfoques más importantes mencionados en el capítulo incluyen:
![[Captura de pantalla 2024-10-07 a las 11.39.41 a. m..png]]
1. **Deslizamiento de la CNN a través de la imagen**:
   - **Método Tradicional**: Una técnica clásica para la detección de objetos era deslizar una CNN entrenada para clasificar un solo objeto a través de diferentes secciones de la imagen (dividida en una cuadrícula). Esta técnica implicaba aplicar la red repetidamente a todas las posibles sub-regiones de la imagen, lo cual resultaba en una alta complejidad computacional y detecciones redundantes del mismo objeto. Para reducir el número de detecciones redundantes, se utiliza una técnica conocida como **supresión no máxima (non-max suppression)**【53:0†source】.

2. **YOLO (You Only Look Once)**:
   - **YOLOv3** es una arquitectura extremadamente rápida y precisa para la detección de objetos. A diferencia de otros métodos que requieren ejecutar una red sobre múltiples sub-regiones de la imagen, YOLO procesa toda la imagen en una sola pasada, lo cual lo hace ideal para aplicaciones en tiempo real.
   - **Características de YOLOv3**:
     - **Salida de Múltiples Cuadros Delimitadores**: YOLOv3 genera cinco cuadros delimitadores para cada celda de la cuadrícula de la imagen, cada uno con un puntaje de objetividad que indica la probabilidad de que exista un objeto en el cuadro.
     - **Escalabilidad**: Durante el entrenamiento, YOLOv3 utiliza imágenes de diferentes tamaños para que pueda detectar objetos de diferentes escalas, lo que también le permite ofrecer un equilibrio entre precisión y velocidad según el tamaño de la imagen utilizada【53:5†source】【53:9†source】.

3. **SSD (Single Shot Multibox Detector)** y **Faster R-CNN**:
   - **SSD** también es un modelo de detección en una sola pasada, similar a YOLO, que se enfoca en la rapidez.
   - **Faster R-CNN** es un método más complejo en el cual la imagen se procesa primero a través de una CNN para extraer características, luego se usa una **Red de Propuestas de Regiones (Region Proposal Network, RPN)** para generar cuadros delimitadores probables, y finalmente se clasifica cada cuadro mediante una segunda etapa. Aunque es más lento que YOLO o SSD, suele ser más preciso, especialmente para problemas que requieren alta precisión【53:8†source】.

4. **Métricas de Evaluación: Mean Average Precision (mAP)**:
   - La métrica **mAP** es comúnmente usada para evaluar el rendimiento de los sistemas de detección de objetos. Se calcula tomando la precisión máxima para distintos niveles de **recall** y luego promediando estos valores. En algunos desafíos como el **PASCAL VOC**, se utiliza un umbral de **Intersection over Union (IoU)** de 0.5 para definir si una detección es correcta【53:14†source】.

## Segmentación Semántica
La **segmentación semántica** es el proceso de asignar una clase a cada píxel de la imagen. A diferencia de la detección de objetos, que simplemente coloca cuadros alrededor de los objetos, la segmentación semántica clasifica cada píxel para proporcionar una comprensión detallada de la escena. Algunos de los puntos destacados en el capítulo incluyen:
![[Captura de pantalla 2024-10-07 a las 11.41.27 a. m..png]]
1. **Problemas de Pérdida de Resolución**:
   - Cuando las imágenes pasan por una CNN convencional, estas suelen perder resolución espacial debido a las capas de **pooling** y convoluciones con **strides mayores que 1**. Por ejemplo, una red puede saber que hay una persona en la parte inferior izquierda de la imagen, pero no puede ser más precisa en cuanto a la localización exacta del objeto【53:3†source】.

2. **Redes Totalmente Convolucionales (Fully Convolutional Networks, FCN)**:
   - En 2015, Jonathan Long y sus colegas propusieron convertir una CNN preentrenada en una **red completamente convolucional (FCN)**. En lugar de usar capas densas al final de la red, se reemplazan por capas convolucionales que producen mapas de características del mismo tamaño que la entrada.
   - La técnica consiste en aplicar una capa de **upsampling** para aumentar la resolución de los mapas de características hasta alcanzar la resolución original de la imagen. Esto permite obtener una segmentación más detallada. Además, se utilizan **convoluciones transpuestas** para realizar el upsampling, lo que permite a la red aprender cómo recuperar detalles espaciales más precisos【53:3†source】【53:6†source】.

3. **Mask R-CNN para Segmentación de Instancias**:
   - **Mask R-CNN** extiende la arquitectura **Faster R-CNN** al agregar una máscara de píxeles para cada cuadro delimitador, permitiendo no solo clasificar y localizar los objetos, sino también identificar los píxeles exactos que pertenecen al objeto. Esto es particularmente útil en aplicaciones como el análisis médico o la visión de robots, donde se necesita una segmentación precisa a nivel de píxeles【53:1†source】.

