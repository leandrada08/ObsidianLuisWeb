  
## **Índice Combinado Revisado para Ambos PDFs**

  

1. **Introducción**

- Motivación para el uso de sensores ToF de baja resolución.

- Desafíos y objetivos del sistema.

- Beneficios del uso de Machine Learning (ML) junto con sensores ToF en computación perimetral.

2. **Sensores ToF y Contexto de Clasificación de Objetos**

- Uso de sensores ToF y su importancia en la detección de profundidad.

- Aplicaciones típicas y ventajas sobre otras tecnologías.

- Limitaciones de los sensores ToF en tareas de visión por computadora.

3. **Metodología para la Clasificación de Objetos usando Sensores ToF**

- **3.1 Preparación del Conjunto de Datos**

- Adaptación del conjunto de datos a la resolución ToF.

- Proceso de simulación de datos de baja resolución.

- **3.2 Arquitectura del Modelo CNN**

- Diseño del modelo para datos de baja resolución.

- Capas convolucionales y su rol en la extracción de características.

- **3.3 Entrenamiento del Modelo**

- Estrategia de entrenamiento y ajuste fino.

- Cuantificación de pesos para optimización de hardware.

4. **Implementación de Hardware y Optimización**

- **4.1 Arquitectura de Hardware para Computación Perimetral**

- Implementación en FPGA y microcontroladores STM32.

- Descripción del núcleo de procesamiento y recursos utilizados.

- **4.2 Optimización de Consumo Energético y Desempeño**

- Evaluación del rendimiento en términos de eficiencia energética y tiempo de inferencia.

- Comparación con soluciones existentes.

5. **Resultados de la Clasificación**

- **5.1 Evaluación de Precisión del Modelo**

- Evaluación del desempeño con distintas clases.

- Comparación con otros sistemas de clasificación con ToF.

- **5.2 Eficiencia Energética y Resultados de Hardware**

- Resultados de consumo energético.

- Implementación y validación de tiempos de inferencia.

6. **Beneficios y Limitaciones del Sistema**

- **6.1 Beneficios de Usar Sensores ToF para Clasificación**

- Compactación y reducción de consumo.

- Viabilidad para aplicaciones en dispositivos de borde.

- **6.2 Limitaciones y Desafíos del Sistema**

- Limitaciones de resolución y precisión.

- Problemas al escalar el sistema a más clases y entornos complejos.

7. **Conclusiones y Futuras Perspectivas**

- Resumen de logros.

- Propuestas para futuros desarrollos, como generalización a secuencias de video y mejoras en la eficiencia del hardware.

  

## **1. Introducción**

El sistema de clasificación de objetos propuesto se centra en el uso de sensores **Time-of-Flight (ToF)** de **ultra-baja resolución** (8x8 píxeles), combinados con **modelos de Machine Learning (ML)**, específicamente **redes neuronales convolucionales (CNN)**. El enfoque principal de este sistema es demostrar que un sensor ToF de tan baja resolución puede ser suficiente para identificar y clasificar objetos, a pesar de sus limitaciones, siempre y cuando el procesamiento se realice de manera adecuada y eficiente.

  

### **Motivación para el Uso de Sensores ToF de Baja Resolución**
- **Información de Profundidad Útil**: Los sensores ToF proporcionan información crítica sobre la **profundidad de los objetos en la escena**. A diferencia de las cámaras RGB, los ToF permiten medir directamente la distancia de cada píxel al sensor, proporcionando una visión tridimensional esencial para tareas como la **navegación autónoma**, la **detección de gestos**, y la **clasificación de objetos** en aplicaciones de bajo consumo de energía.

- **Bajo Consumo y Compactación**: El sensor **VL53L8CX** utilizado en este estudio tiene solo 8x8 píxeles, lo cual representa una gran **reducción en la cantidad de datos a procesar** en comparación con sensores de mayor resolución o cámaras RGB. Esto hace que el sistema sea ideal para **dispositivos compactos** y de bajo consumo de energía, como los wearables o los sistemas de asistencia personal.

- **Viabilidad en Computación Perimetral**: Los dispositivos de computación perimetral (Edge Computing) requieren sistemas que puedan procesar los datos localmente, sin depender de servidores remotos. Los sensores ToF de baja resolución, junto con modelos CNN optimizados, permiten la integración directa en **microcontroladores y FPGA**, manteniendo un bajo costo y un consumo energético reducido.

### **Desafíos y Objetivos del Sistema**
- **Baja Resolución y Poca Información de Contexto**: La **resolución de 8x8 píxeles** presenta un desafío significativo porque limita la cantidad de información disponible sobre la forma y detalles de los objetos. Esto dificulta la diferenciación entre objetos similares que podrían tener características distintivas solo en un entorno de alta resolución.

- **Integración de Machine Learning**: A pesar de la limitación en la cantidad de datos, el uso de **redes neuronales convolucionales (CNN)** optimizadas permite aprender patrones en los datos de profundidad, lo que hace posible clasificar objetos con una alta precisión incluso con imágenes de tan baja resolución. Este enfoque demuestra cómo el ML puede ser usado para mejorar las capacidades de sensores limitados.

  

### **Beneficios del Uso de Machine Learning con Sensores ToF en Computación Perimetral**
- **Optimización del Rendimiento**: Los modelos CNN, en combinación con el ToF, están diseñados para ser **pequeños y eficientes**, tanto en términos de memoria como de consumo energético. Las técnicas de **cuantificación** y **ajuste fino** permiten adaptar estos modelos a entornos de hardware muy limitados, como los microcontroladores.

- **Reducción de la Complejidad del Sistema**: Al trabajar solo con el sensor ToF, se reduce la necesidad de manejar imágenes RGB de alta resolución. Esto simplifica la arquitectura del hardware y minimiza la carga de procesamiento, permitiendo a los sistemas embebidos realizar tareas de clasificación con pocos recursos.

## **Sensores ToF y Contexto de Clasificación de Objetos**
El **sensor Time-of-Flight (ToF)** es un dispositivo que mide la **distancia** entre el sensor y los objetos en una escena utilizando pulsos de luz infrarroja. El sensor emite un pulso, que se refleja en los objetos y regresa al sensor, donde se mide el **tiempo que tarda** el pulso en regresar. Este tiempo es proporcional a la **distancia** entre el sensor y el objeto, lo cual permite construir un **mapa de profundidad** de la escena.

- **Datos de Profundidad para Contexto Tridimensional**: A diferencia de las cámaras RGB que capturan **color y textura**, los sensores ToF proporcionan información tridimensional directa. Esto es útil en aplicaciones donde la **posición espacial** de los objetos es crucial, como en la **detección de obstáculos** o la navegación autónoma.

- **Resolución Limitada, Ventaja para Computación Local**: La resolución de 8x8 píxeles es extremadamente baja, pero también tiene ventajas: **menor cantidad de datos** significa menor **necesidad de ancho de banda y almacenamiento**, lo cual es fundamental en sistemas que deben ser pequeños, portátiles y tener un bajo consumo de energía.

### **Aplicaciones Típicas y Ventajas sobre Otras Tecnologías**
- **Navegación Autónoma**: Los sensores ToF se utilizan en la navegación de robots pequeños para evitar obstáculos y detectar rutas. La información de profundidad permite a los robots entender la distancia a objetos cercanos y tomar decisiones en tiempo real.

- **Detección de Gestos y Asistencia Personal**: Los sensores ToF también se utilizan en sistemas de **interacción humana**, como gafas inteligentes, donde los gestos del usuario pueden ser detectados y utilizados para dar instrucciones. En estos casos, la información de profundidad permite detectar la forma y el movimiento de la mano del usuario.

### **Limitaciones de los Sensores ToF en Tareas de Visión por Computadora**
- **Capacidad Limitada para Detectar Detalles Finos**: La resolución de **8x8 píxeles** proporciona un nivel muy básico de información. Esto significa que no se pueden detectar detalles complejos de los objetos, lo cual limita el rango de aplicaciones donde se puede utilizar este sistema.

- **Dificultad en Diferenciar Objetos Similares**: Con una resolución tan baja, los objetos que tengan formas similares pueden ser difíciles de distinguir entre sí. Esto es particularmente problemático si se requieren altos niveles de precisión o si los objetos a clasificar son muy parecidos.

  
## **Metodología para la Clasificación de Objetos usando Sensores ToF**
La metodología del sistema de clasificación de objetos utilizando sensores ToF se centra en tres aspectos fundamentales: la preparación del conjunto de datos, el diseño del modelo de red neuronal convolucional (CNN) adaptado a los datos de baja resolución, y el entrenamiento del modelo para maximizar su eficiencia y precisión.

### **Preparación del Conjunto de Datos**
La **preparación del conjunto de datos** fue un paso crucial para poder entrenar el modelo CNN utilizando imágenes de **8x8 píxeles**, que es la resolución ofrecida por el sensor ToF utilizado.

  

**Adaptación del Conjunto de Datos a la Resolución ToF**

  

- **Origen de los Datos**: Durante la fase de entrenamiento, se utilizó un **conjunto de datos público** de alta resolución, originalmente con imágenes en RGB de **640x480 píxeles**. Este dataset incluía diferentes clases de objetos con imágenes detalladas que contaban con información de color y profundidad.

- **Recorte y Escalado**: Como el sensor ToF VL53L8CX tiene una **resolución de 8x8 píxeles**, las imágenes del dataset original fueron **recortadas y escaladas** para simular lo que el sensor capturaría. Este proceso de reducción implica disminuir las imágenes de alta resolución a una versión mucho más simple que encaja con las capacidades del sensor ToF. Específicamente, las imágenes se redujeron a un tamaño de 8x8 píxeles para mantener la consistencia con los datos reales que el sensor generaría durante la inferencia.

- **Simulación de Datos Reales**: La razón para usar un dataset de alta resolución como punto de partida fue **simular escenarios reales** donde los objetos están a diferentes distancias y ángulos respecto al sensor. Al recortar las imágenes y adaptar los datos a la matriz de 8x8 píxeles, se creó un conjunto de datos que imita la información que se generaría durante el uso real del dispositivo, pero con una variedad más amplia de ejemplos para entrenar el modelo de manera más efectiva.

  

**Proceso de Simulación de Datos de Baja Resolución**

  

- **Creación de Variaciones**: Se crearon **distintas versiones de los objetos** variando la posición, rotación y el ángulo respecto al sensor, generando así diferentes mapas de profundidad. Esto fue crucial para que el modelo pudiera aprender a identificar objetos desde diferentes perspectivas y bajo diferentes condiciones.

- **Clases Seleccionadas**: Se seleccionaron inicialmente **cuatro clases**: manzana, calculadora, botella de agua y caja de comida, por ser objetos fácilmente diferenciables en términos de forma y volumen, incluso en baja resolución. Luego, se expandió a **diez clases** añadiendo otros objetos como una batería, un durazno y una taza de café, lo cual incrementó la dificultad del problema y mejoró la capacidad del modelo para generalizar.

  

**3.2 Arquitectura del Modelo CNN**

  

El diseño del modelo de **red neuronal convolucional (CNN)** fue adaptado específicamente para operar con la **baja resolución** de los datos proporcionados por el sensor ToF. Este enfoque tuvo que equilibrar la capacidad de extraer características útiles y la eficiencia en términos de memoria y consumo energético.

  

**Diseño del Modelo para Datos de Baja Resolución**

  

- **Entrada de Baja Resolución**: La entrada al modelo es una imagen de **8x8 píxeles** que contiene los valores de profundidad de la escena capturada por el sensor ToF. Cada píxel representa la distancia entre el sensor y un punto en la escena, generando un **mapa de profundidad**.

- **Primera Capa Convolucional**: El modelo comienza con una **capa convolucional con tres filtros de 3x3**. Estos filtros se utilizan para extraer características locales, como variaciones rápidas en la profundidad, lo cual puede representar el borde de un objeto o una diferencia de nivel en la escena.

- **Tres Filtros (Canales)**: Estos tres filtros generan tres mapas de características a partir de la imagen original de 8x8. Cada filtro es capaz de identificar diferentes aspectos de la imagen, como patrones de profundidad o contornos. Al tener múltiples filtros, se amplía la capacidad del modelo para captar una variedad más rica de características.

  

**Capas Convolucionales y su Rol en la Extracción de Características**

  

- **Segunda Capa Convolucional**: Después de la primera capa, los datos pasan por una **segunda capa convolucional** con **cuatro filtros adicionales**. Estos filtros son responsables de extraer características de mayor nivel a partir de los mapas de características generados en la capa anterior.

- **Capa Totalmente Conectada (Fully Connected)**: Finalmente, el modelo incluye una **capa completamente conectada** que se encarga de tomar todas las características extraídas y tomar una decisión sobre cuál es la clase del objeto. La capa de salida aplica una **función softmax** para asignar probabilidades a cada clase y determinar la clasificación final.

- **Uso de Funciones de Activación ReLU**: Todas las capas convolucionales utilizan la función de activación **Rectified Linear Unit (ReLU)**, que permite introducir no linealidad y mejorar la capacidad del modelo para aprender representaciones complejas de los datos.

  

## **Entrenamiento del Modelo**

  

El entrenamiento del modelo CNN fue diseñado para **maximizar la eficiencia y la capacidad de generalización** del sistema, a pesar de la limitación en la resolución de entrada.

  

**Estrategia de Entrenamiento y Ajuste Fino**

  

- **División del Conjunto de Datos**: El conjunto de datos fue dividido en un **70% para entrenamiento**, **15% para validación**, y **15% para pruebas**. Esto aseguró que el modelo pudiera aprender de la mayoría de los ejemplos disponibles, mientras se evaluaba su capacidad de generalizar a datos nuevos.

- **Optimizador SGD y Ajuste Fino**: Para el entrenamiento se utilizó el **optimizador Stochastic Gradient Descent (SGD)** con una tasa de aprendizaje que se ajustaba progresivamente. Se aplicó una técnica de **ajuste fino** (fine-tuning) para mejorar la precisión del modelo después de un primer entrenamiento general. Esta técnica permite realizar pequeñas modificaciones a los pesos del modelo previamente entrenado, mejorando su capacidad de generalización.

- **Dropout para Evitar Sobreentrenamiento**: Se aplicó un **dropout del 25%** después de cada capa convolucional para evitar el **sobreentrenamiento** del modelo. Esto se hizo desconectando aleatoriamente algunas neuronas durante el entrenamiento, lo cual forzó al modelo a aprender características más robustas y a no depender de ciertas combinaciones específicas de neuronas.

  

**Cuantificación de Pesos para Optimización de Hardware**

  

- **Cuantificación Posterior al Entrenamiento**: Una vez completado el entrenamiento, se aplicó una **cuantificación de 8 bits** tanto a los pesos como a las activaciones del modelo. Esta cuantificación redujo el tamaño del modelo y disminuyó significativamente el **consumo energético** y la **ocupación de memoria**, haciendo viable la implementación en dispositivos de bajo costo y con recursos limitados.

- **Impacto de la Cuantificación**: A pesar de reducir la precisión numérica de los pesos del modelo (de 32 bits flotantes a 8 bits enteros), el impacto sobre la precisión final fue **mínimo**, con una reducción de menos del **0.4%** en la precisión del modelo. Esta pequeña pérdida de precisión es aceptable dada la gran mejora en la eficiencia y el tamaño del modelo, lo cual fue crucial para que pudiera ser implementado en un microcontrolador o FPGA.

  

## **Implementación de Hardware y Optimización**

  

Una vez que el modelo CNN fue diseñado y entrenado, el siguiente paso fue implementarlo en hardware adecuado para garantizar su funcionamiento eficiente en tiempo real y su viabilidad en entornos de bajo consumo.

  

**4.1 Arquitectura de Hardware para Computación Perimetral**

  

El objetivo principal era implementar el modelo en un hardware que pudiera ser utilizado en dispositivos **embebidos** y de **computación en el borde (Edge Computing)**, donde los recursos de hardware son limitados y el consumo de energía debe ser muy bajo.

  

**Implementación en FPGA y Microcontroladores STM32**

  

- **FPGA AMD Xilinx Artix-7**: El modelo fue implementado en una **FPGA AMD Xilinx Artix-7**, la cual permitió realizar pruebas de la eficiencia de hardware y verificar la viabilidad del sistema. La FPGA fue elegida porque permite un alto grado de **paralelismo**, lo cual es ideal para redes neuronales convolucionales que requieren realizar múltiples operaciones en paralelo.

- **Microcontroladores STM32**: También se probó la implementación en **microcontroladores STM32** de bajo costo. Los microcontroladores fueron seleccionados debido a su capacidad de operar en entornos con **restricciones energéticas**, haciendo que el sistema resultara viable para dispositivos portátiles o wearables.

  

**Descripción del Núcleo de Procesamiento y Recursos Utilizados**

  

- **Componentes de Hardware Utilizados**: El núcleo de procesamiento incluía tres componentes principales: las capas **con1** y **conv2** correspondientes a las convoluciones, y una capa completamente conectada (**fc**) para la clasificación. También se utilizaron memorias de entrada y de características (**feature memory**) para almacenar los datos intermedios durante el procesamiento.

- **Interfaz SPI para Comunicación**: Se utilizó una interfaz **SPI (Serial Peripheral Interface)** para la comunicación entre el sensor ToF y el núcleo de procesamiento, lo cual permitió recibir los datos de profundidad del sensor y realizar la inferencia en tiempo real.

  

**4.2 Optimización de Consumo Energético y Desempeño**

  

El diseño del sistema fue optimizado para maximizar la eficiencia energética y garantizar que pudiera ser implementado en dispositivos de borde sin necesidad de una fuente de energía constante.

  

**Evaluación del Rendimiento en Términos de Eficiencia Energética y Tiempo de Inferencia**

  

- **Consumo Energético**: La implementación en la FPGA mostró un consumo de **65.6 nJ por inferencia**, con un consumo de energía dinámico de **1.095 μW**. Estos valores representan una gran reducción en comparación con los métodos tradicionales de clasificación de objetos utilizando cámaras RGB, que requieren procesadores más complejos y un consumo de energía mucho mayor.

- **Tiempo de Inferencia**: El tiempo de inferencia del modelo cuantificado fue **inferior a 1 ms**, lo cual fue significativamente menor que el **Output Data Rate (ODR)** del sensor ToF (una muestra cada 66.67 ms). Esto permitió que el sistema pudiera realizar las inferencias en tiempo real, procesando cada imagen antes de que el sensor adquiriera la siguiente.

  

**Comparación con Soluciones Existentes**

  

- **Reducción en la Ocupación de Memoria y Hardware Utilizado**: En comparación con otros sistemas de clasificación de objetos, el modelo presentado fue capaz de operar con una ocupación de **2.65 kB de memoria** en el microcontrolador STM32, y sin el uso de DSPs (Digital Signal Processors) en la FPGA. Esto muestra la **compactación** del sistema y la eficiencia en el uso de hardware, haciéndolo mucho más adecuado para aplicaciones en dispositivos de borde.

  



Continuemos con el desarrollo del **punto 5: Resultados de la Clasificación** y el **punto 6: Beneficios y Limitaciones del Sistema**, para proporcionar una visión completa de los logros y desafíos del sistema basado únicamente en sensores ToF de baja resolución.

  

**5. Resultados de la Clasificación**

  

En esta sección se presentan los resultados obtenidos a partir del entrenamiento e implementación del modelo CNN con datos de **8x8 píxeles** provenientes del sensor ToF. Estos resultados incluyen la evaluación de la **precisión del modelo**, así como la **eficiencia energética** y el desempeño al ser implementado en hardware de bajo consumo.

  

**5.1 Evaluación de Precisión del Modelo**

  

**Evaluación del Desempeño con Distintas Clases**

  

- **Clasificación con Cuatro Clases Iniciales**: En la primera fase del proyecto, el modelo fue entrenado para clasificar cuatro clases de objetos: **manzana, calculadora, botella de agua y caja de comida**. Estos objetos fueron seleccionados debido a su diferencia significativa en términos de forma y volumen. La precisión alcanzada por el modelo en este escenario fue del **93.6%**, lo cual demuestra que, a pesar de la baja resolución de 8x8 píxeles, el sensor ToF y la red CNN fueron capaces de aprender y generalizar bien las características de estos objetos.

- **Ampliación a Diez Clases**: Posteriormente, se aumentó el número de clases a **diez**, incluyendo objetos adicionales como una **batería, barra de pegamento, durazno, taza de café y plato**. Este incremento en la cantidad de clases trajo consigo un desafío mayor para el modelo, que debía diferenciar objetos que en algunos casos eran más similares en términos de profundidad o forma. A pesar del aumento en la complejidad, el modelo logró mantener una **precisión del 90.21%**, lo cual sigue siendo un resultado considerablemente alto dado el tipo de sensor utilizado.

  

**Comparación con Otros Sistemas de Clasificación con ToF**

  

- **Sistemas Tradicionales y Competitivos**: En comparación con otros sistemas que utilizan sensores ToF o tecnologías similares para la clasificación de objetos, el rendimiento del modelo basado en el sensor **VL53L8CX** se mostró competitivo. Otros sistemas ToF que utilizan resoluciones más altas y sensores de mayor calidad alcanzan precisiones que varían entre el **86% y el 91%**, pero a costa de un mayor consumo energético y complejidad de hardware.

- **Ventajas del Uso de Baja Resolución**: El sistema propuesto mostró que es posible alcanzar precisiones similares con una resolución de **8x8 píxeles**, gracias al diseño eficiente del modelo y al enfoque específico para la extracción de características de profundidad. Esto es particularmente relevante para aplicaciones de **bajo costo** y **computación perimetral**, donde el objetivo es realizar tareas de clasificación con recursos muy limitados.

  

**5.2 Eficiencia Energética y Resultados de Hardware**

  

**Resultados de Consumo Energético**

  

- **Implementación en FPGA**: La implementación del modelo cuantificado en la **FPGA AMD Xilinx Artix-7** demostró un consumo energético notablemente bajo, con **65.6 nJ por inferencia**. Este resultado resalta la eficiencia del sistema para aplicaciones que requieren procesamiento continuo en tiempo real, como en dispositivos de detección de gestos y asistencia robótica.

- **Implementación en STM32**: En el caso del **microcontrolador STM32**, la implementación del modelo mostró un **consumo de energía de 32 µJ por inferencia**, con un tiempo de procesamiento de **1 ms**. Esto permite que el sistema realice la clasificación antes de que el sensor ToF adquiera la siguiente imagen, lo cual es crucial para garantizar el rendimiento en aplicaciones de tiempo real.

  

**Implementación y Validación de Tiempos de Inferencia**

  

- **Capacidad de Inferencia en Tiempo Real**: El **tiempo de inferencia** logrado fue de menos de **1 ms**, lo cual es considerablemente menor que el tiempo requerido para la adquisición de cada nueva muestra por parte del sensor ToF (66.67 ms). Esto significa que el sistema tiene suficiente tiempo para procesar los datos de profundidad y clasificar el objeto antes de que el sensor vuelva a capturar datos, garantizando la capacidad de operar en **tiempo real**.

  

**Conclusión sobre la Eficiencia del Modelo**

  

Los resultados obtenidos durante la implementación del modelo en hardware muestran que el sistema es **altamente eficiente** y **adecuado** para aplicaciones de bajo consumo energético. El hecho de que la precisión del modelo permanezca alta a pesar de la cuantificación de los pesos y activaciones, demuestra que el enfoque adoptado es sólido y viable para los objetivos planteados en escenarios de computación perimetral.

  

**6. Beneficios y Limitaciones del Sistema**

  

En esta sección se discuten los beneficios clave y las limitaciones que presenta el sistema propuesto, considerando su implementación en hardware y su capacidad para clasificar objetos utilizando solo un sensor ToF de **ultra-baja resolución**.

  

**6.1 Beneficios de Usar Sensores ToF para Clasificación**

  

**Compactación y Reducción de Consumo Energético**

  

- **Eficiencia Energética**: Uno de los principales beneficios de este sistema es su **bajo consumo energético**, lo cual es esencial para aplicaciones en dispositivos portátiles y sistemas embebidos. La cuantificación a 8 bits permitió reducir el tamaño del modelo, optimizando el consumo energético tanto en la FPGA como en los microcontroladores.

- **Compactación del Hardware**: La implementación de la CNN en una FPGA o microcontrolador con recursos limitados es una prueba del potencial de **compactación** del sistema. Utilizar un sensor de baja resolución permite reducir la complejidad del hardware, disminuyendo tanto el **costo** como el **espacio físico** necesario para el sistema.

  

**Viabilidad para Aplicaciones en Dispositivos de Borde**

  

- **Computación Perimetral (Edge Computing)**: El sistema está diseñado para **computación perimetral**, lo que significa que el procesamiento se realiza directamente en el dispositivo, sin depender de la nube o de servidores externos. Esto reduce la **latencia** y mejora la **seguridad** de los datos, ya que toda la información se procesa localmente.

- **Aplicaciones Versátiles**: Este tipo de clasificación es útil en diversas aplicaciones, como **detección de gestos** para sistemas de interacción hombre-máquina, **navegación autónoma** para robots pequeños, y sistemas **portátiles** para asistencia visual. El sensor ToF de baja resolución proporciona una visión suficiente para entender la disposición espacial básica, que es todo lo que muchos de estos sistemas requieren.

  

**Robustez en Escenarios Limitados**

  

- **Capacidad de Operación en Entornos de Baja Iluminación**: A diferencia de los sensores RGB que dependen en gran medida de la iluminación del entorno, el sensor ToF funciona mediante pulsos de luz infrarroja, lo cual le permite operar de manera efectiva incluso en **condiciones de poca luz**. Esto hace que el sistema sea útil para aplicaciones en interiores o en situaciones donde la iluminación es inestable.

  

**6.2 Limitaciones y Desafíos del Sistema**

  

**Limitaciones de Resolución y Precisión**

  

- **Baja Resolución Limita la Capacidad de Diferenciar Objetos Similares**: La resolución de **8x8 píxeles** presenta una limitación significativa en términos de los **detalles finos** que se pueden captar. Esto significa que la capacidad de diferenciar objetos que son similares en forma y tamaño es limitada. Por ejemplo, una **manzana** y un **durazno** podrían ser difíciles de distinguir si tienen tamaños similares y formas redondeadas.

- **Detalle Espacial Restringido**: La baja resolución significa que cada píxel representa una porción considerable del espacio frente al sensor, lo cual lleva a una **pérdida de detalles** en el objeto. Esta restricción es adecuada para clasificar objetos grandes y bien diferenciados, pero puede ser insuficiente para objetos que requieren un análisis más detallado o que presentan **características complejas**.

  

**Problemas al Escalar el Sistema a Más Clases y Entornos Complejos**

  

- **Escalabilidad Limitada**: A medida que se aumenta el número de clases, el sistema debe ser capaz de capturar diferencias cada vez más sutiles entre los objetos, lo cual no siempre es posible con la información de profundidad de **8x8 píxeles**. Escalar el sistema para clasificar un número mayor de clases, o para operar en **entornos más complejos**, presenta un desafío debido a las limitaciones inherentes del sensor.

- **Entornos Complejos y Oclusión**: En escenas con **múltiples objetos** o donde los objetos están parcialmente cubiertos, el sensor ToF puede no proporcionar suficiente información para hacer una clasificación precisa. La baja resolución hace que los **bordes** y las **oclusiones** sean difíciles de detectar, lo cual puede llevar a errores de clasificación.

  

**Requerimientos de Alineación Física del Sensor**

  

- **Dependencia de la Posición del Sensor**: Dado que la resolución es tan baja, la **posición relativa** del sensor respecto al objeto tiene un impacto significativo en la calidad de los datos capturados. Un mal posicionamiento puede hacer que la información capturada sea insuficiente o ambigua, lo cual puede reducir la precisión del sistema.

  

**6.3 Posibilidades de Mejora y Trabajo Futuro**

  

- **Generalización a Secuencias de Video**: Un posible camino para mejorar el sistema sería extender su capacidad para procesar **secuencias de video**, en lugar de imágenes individuales. Esto permitiría al sistema **rastrear objetos en movimiento** y mejorar la precisión de clasificación mediante la integración de datos temporales.

- **Integración con Sensores Adicionales**: Otra posible mejora sería combinar el sensor ToF con otros sensores como cámaras RGB o sensores de proximidad, lo cual podría aumentar la **capacidad de discriminación** del sistema y resolver algunas de las limitaciones impuestas por la baja resolución.

- **Optimización de Hardware**: También se podría desarrollar una **arquitectura de hardware específica (ASIC)** que integre el sensor ToF con el núcleo de procesamiento de la CNN. Esto permitiría optimizar aún más el consumo de energía y mejorar el rendimiento general del sistema.

  

**Conclusiones y Futuras Perspectivas (Punto 7)**

  

En resumen, el sistema de clasificación de objetos utilizando sensores ToF de baja resolución demuestra que es posible implementar una solución de **computación perimetral** eficiente para la clasificación de objetos. Aunque el sistema tiene ciertas limitaciones relacionadas con la baja resolución, las técnicas de **Machine Learning** y la **implementación eficiente en hardware** lo hacen viable para aplicaciones de bajo consumo de energía y en escenarios donde la información de profundidad es suficiente.

  

Las futuras mejoras se centran en aumentar la capacidad del sistema para operar en entornos más complejos, así como en explorar formas de combinar datos de diferentes sensores para aumentar la robustez y la precisión del sistema. Además, la posibilidad de integrar directamente el sensor ToF con el procesamiento mediante hardware específico podría mejorar aún más la eficiencia y abrir nuevas oportunidades en el campo de los dispositivos embebidos y de borde.

  

Este desarrollo permite a los dispositivos compactos realizar tareas de clasificación y detección con recursos limitados, lo cual tiene un gran potencial en la **industria del Internet de las Cosas (IoT)** y en aplicaciones de **asistencia personal** y **navegación autónoma**.