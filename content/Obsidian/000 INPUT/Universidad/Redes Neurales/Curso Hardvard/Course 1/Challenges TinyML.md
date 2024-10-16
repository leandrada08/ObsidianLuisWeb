
## Hardware
### [[Estructura de las computadoras]]
### [[Introduccion sistemas embebidos]]
#### Diferencias entre microprocesadores y microcontroladores
1. **Microprocesador**:
   - Se utiliza en **computadoras generales** como laptops y servidores.
   - Es solo una parte del sistema y necesita otros componentes externos como memoria y almacenamiento.
   - Es más flexible y permite configurar sus características (como la memoria en laptops).
   
2. **Microcontrolador**:
   - Está diseñado para **sistemas embebidos** y tiene todos los componentes (procesador, memoria y almacenamiento) integrados en un solo bloque.
   - Tiene **funciones específicas**, como controlar una cafetera o gestionar llamadas telefónicas.
   - **Tamaño pequeño**: Se enfoca en la reducción de tamaño y bajo consumo energético.

#### Diferencias en rendimiento y capacidad
- **Microprocesadores**:
   - Frecuencia: Entre **1 y 4 GHz**.
   - Memoria: De **megabytes a gigabytes**.
   - Almacenamiento: De **gigabytes a terabytes**.
   - Consumo energético: En el rango de **decenas de vatios**.
   
- **Microcontroladores**:
   - Frecuencia: Entre **1 y 4 Hz**.
   - Memoria: De **kilobytes a algunos megabytes**.
   - Almacenamiento: De **kilobytes a megabytes**.
   - Consumo energético: De **microvatios a milivatios**.

#### Implicaciones de las limitaciones del microcontrolador
- **Tareas específicas**: Las aplicaciones para microcontroladores deben ajustarse a tareas **menos complejas** debido a sus limitaciones de procesamiento, memoria y energía.
- **Selección del microcontrolador adecuado**:
   - La elección del microcontrolador depende de la complejidad de la tarea y de los **requerimientos de memoria y potencia**.
   - Es importante considerar si la tarea necesita **procesamiento en tiempo real** o si puede ejecutarse de forma intermitente para ahorrar energía.



## Software

El software en sistemas embebidos tiene una estructura diferente a la de los sistemas generales. Generalmente, se compone de tres niveles:
1. **Aplicaciones de alto nivel**: Son las que interactúan directamente con el usuario o con los datos.
2. **Bibliotecas**: Proveen soporte a las aplicaciones, permitiendo que se ejecuten de manera eficiente.
3. **Sistema operativo (OS)**: Gestiona el hardware y ofrece una base para las bibliotecas y aplicaciones.
![[Captura de pantalla 2024-10-09 a las 12.33.03 p. m..png]]
#### Sistemas operativos en sistemas embebidos
- En sistemas generales como **laptops o smartphones**, los sistemas operativos comunes son **Windows**, **MacOS**, **Linux**, **iOS** o **Android**.
- Estos OS permiten una gran **flexibilidad** y **portabilidad** en las aplicaciones, con múltiples capas de abstracción que facilitan la programación y el desarrollo.
![[Captura de pantalla 2024-10-09 a las 12.34.19 p. m..png|500]]
- En **sistemas embebidos**, sin embargo, los sistemas operativos son mínimos o a veces inexistentes. Ejemplos como **FreeRTOS** y **ARM Mbed OS** son comunes, pero su uso es limitado ya que ocupan **memoria** y **ciclos de procesamiento** que el sistema embebido podría necesitar para otras tareas más críticas.
![[Captura de pantalla 2024-10-09 a las 12.35.48 p. m..png|500]]
#### Bibliotecas:Problemas de portabilidad en sistemas embebidos
- En sistemas generales, bibliotecas como **NumPy** permiten que el código sea **portátil**, es decir, que pueda ejecutarse en cualquier sistema sin necesidad de modificaciones.
- En sistemas embebidos, la portabilidad es un reto. Cada sistema puede tener diferentes capacidades, lo que genera problemas cuando se implementan **bibliotecas especializadas** que dependen de hardware específico.
![[Captura de pantalla 2024-10-09 a las 12.39.20 p. m..png]]
#### Resumen
1. **Limitaciones de hardware**: Los microcontroladores tienen **poca memoria, capacidad de procesamiento** y **bajo consumo de energía**, lo que dificulta la implementación de software complejo como los sistemas operativos comunes.
2. **Portabilidad limitada**: A diferencia de los sistemas generales, el software en sistemas embebidos no es universalmente portable debido a la **especialización** del hardware.
3. **Flexibilidad reducida**: Mientras que los sistemas generales pueden ejecutar múltiples aplicaciones, los sistemas embebidos tienden a estar diseñados para tareas específicas, lo que reduce la flexibilidad.

## Algorithm for TinyML
El campo del **machine learning** ha crecido exponencialmente en los últimos años. Los modelos han aumentado en **complejidad** y requieren **mayor capacidad de procesamiento**. Un ejemplo claro es **GPT-3**, que es significativamente más grande que modelos anteriores, lo que ilustra el crecimiento acelerado de la complejidad.
![[Captura de pantalla 2024-10-09 a las 1.26.40 p. m..png|500]]
Desde 2012, con la introducción de **AlexNet**, la capacidad de procesamiento requerida ha aumentado aproximadamente **300,000 veces**, lo que ha impulsado el desarrollo de procesadores especializados como las **TPU** (Tensor Processing Units) de Google.

Si bien los grandes centros de datos permiten manejar modelos complejos, estos solo procesan una pequeña parte de los datos disponibles. El desafío en **TinyML** es llevar esos modelos grandes y adaptarlos a dispositivos pequeños, con **restricciones de recursos**.

### Evolución de los modelos de Machine Learning
![[Captura de pantalla 2024-10-09 a las 1.28.41 p. m..png]]
1. **AlexNet (2012)**: 
   - **Tamaño del modelo**: 61 MB.
   - **Precisión**: 57.1%.
   
2. **VGGNet (2014)**:
   - **Tamaño del modelo**: 528 MB (casi 10 veces más grande).
   - **Precisión**: 71.5%.
   
3. **ResNet (2015)**:
   - Mejoró la **precisión** al 75.8%, con una reducción en el tamaño del modelo.
   
4. **MobileNet (2017)**:
   - Diseñado para dispositivos móviles, priorizó el **tamaño pequeño** (16.9 MB), aunque comprometiendo algo de precisión.
   
#### Desafíos de TinyML
Aunque los modelos como **MobileNet** han reducido el tamaño, los **microcontroladores** en los que se implementa TinyML solo tienen unos **kilobytes de memoria**, lo que representa un **gran desafío** en comparación con los modelos actuales que aún son relativamente grandes (megabytes).
![[Captura de pantalla 2024-10-09 a las 1.29.45 p. m..png|500]]
#### Técnicas para habilitar TinyML
Durante el curso, se explorarán técnicas para **comprimir** estos modelos y hacerlos más eficientes. El objetivo es lograr que los modelos de machine learning se ajusten a las limitaciones de los dispositivos embebidos, sin sacrificar demasiada precisión o funcionalidad.



## Reducir el tamaño del modelo

El reto principal en TinyML es **reducir el tamaño** de los modelos de machine learning sin perder la capacidad de identificar patrones en los datos. A continuación, se presentan técnicas para comprimir y optimizar modelos.

### **1. Pruning:**
- **Descripción:** Consiste en eliminar conexiones o neuronas de una red neuronal que tienen poca relevancia en el resultado final.
- **Objetivo:** Reducir el tamaño del modelo y la demanda computacional sin sacrificar precisión.
- **Beneficio:** Permite ejecutar el modelo en dispositivos pequeños y con poca capacidad de cómputo.
![[Captura de pantalla 2024-10-09 a las 1.36.03 p. m..png|500]]

![[Captura de pantalla 2024-10-09 a las 1.36.19 p. m..png|500]]
### **2. Quantization:**
- **Descripción:** Reducción de la precisión numérica de los valores que el modelo maneja. Por ejemplo, pasar de valores de punto flotante (32 bits) a enteros de 8 bits (int8).
- **Objetivo:** Disminuir el tamaño del modelo y reducir el consumo de memoria.
- **Beneficio:** Reducción de 4x en el tamaño del modelo y mejoras en la velocidad de cómputo, ya que los enteros son más fáciles de procesar en sistemas embebidos.



### **3. Knowledge Distillation:**
- **Descripción:** Un modelo grande (maestro) entrena a un modelo más pequeño (estudiante) para que aprenda a realizar la tarea de manera más eficiente.
- **Objetivo:** Transferir el conocimiento de un modelo complejo a uno más pequeño sin sacrificar demasiado la precisión.
- **Beneficio:** Permite mantener un alto nivel de rendimiento con un modelo más pequeño, ideal para TinyML.

![[Captura de pantalla 2024-10-09 a las 1.39.28 p. m..png]]


## Runtime
### **Desafíos en el nivel de runtime:**

**4. TensorFlow Lite vs TensorFlow:**
- **TensorFlow:** Framework usado para entrenar grandes modelos en servidores o centros de datos con múltiples GPU/TPU.
- **TensorFlow Lite:** Adaptado para dispositivos móviles, optimizando el uso de memoria y consumo de energía para **inferencia**, no para entrenamiento.
- **TensorFlow Lite Converter:** Herramienta que convierte los grandes modelos de TensorFlow en versiones más ligeras (.tflite) para que se puedan ejecutar en dispositivos móviles o embebidos.

![[Captura de pantalla 2024-10-09 a las 1.44.46 p. m..png|300]]![[Captura de pantalla 2024-10-09 a las 1.46.10 p. m..png|500]]





### **Why the Future of Machine Learning is Tiny and Bright**

El futuro de TinyML es brillante y su potencial es vasto, impulsado por los microcontroladores (MCUs) ubicuos, de bajo costo y de muy bajo consumo energético. Se estima que existen más de 250 mil millones de microcontroladores en uso en todo el mundo y se espera que este año se vendan más de 50 mil millones. Estos MCUs están presentes en dispositivos de consumo, médicos, automotrices e industriales. Aunque generalmente pasan desapercibidos, son esenciales para habilitar aplicaciones de TinyML, que permiten que estos pequeños dispositivos ejecuten algoritmos inteligentes.
![[Captura de pantalla 2024-10-09 a las 3.45.05 p. m..png]]
Los MCUs son baratos, cuestan menos de 1 USD en promedio, y están diseñados para realizar tareas específicas de manera eficiente, a menudo utilizando solo una fracción de la energía que consumen los procesadores tradicionales. Este bajo consumo de energía los hace ideales para ser integrados en dispositivos autónomos que operan durante largos periodos sin mantenimiento.

TinyML está emergiendo como una solución viable para ejecutar algoritmos de aprendizaje automático en estos microcontroladores, permitiendo que dispositivos como cepillos de dientes inteligentes, sensores biomédicos y sistemas de seguridad automotriz funcionen de manera autónoma y eficiente. TinyML también promete transformar la agricultura y la conservación ambiental con sensores que monitorean cultivos y fauna.

El procesamiento de datos a nivel local en estos dispositivos, en lugar de enviar toda la información a la nube, no solo ahorra energía, sino que también desbloquea nuevas aplicaciones. Por ejemplo, dispositivos con reconocimiento de voz o visión podrán operar con interfaces de bajo costo que funcionen con baterías pequeñas durante largos periodos de tiempo.

El futuro de TinyML es prometedor, y sus aplicaciones potenciales son casi infinitas. Con la tecnología adecuada, pronto veremos una explosión de nuevas soluciones impulsadas por TinyML en todos los sectores de la vida cotidiana.



## Potencial y Responsabilidad

TinyML abre un abanico de posibilidades tanto a nivel de hardware como de software. Sin embargo, junto con su potencial, surgen desafíos importantes, como las limitaciones de los sistemas integrados y los algoritmos de aprendizaje automático. La tecnología es poderosa y, aunque puede traer cambios positivos, también puede generar riesgos que deben ser abordados con responsabilidad.

### **IA Responsable y Privacidad**

#### **El poder de la IA en dispositivos pequeños**
La IA puede identificar aspectos únicos de las personas, como su forma de caminar, a través de datos de dispositivos cotidianos. Esto demuestra que aunque la tecnología tiene capacidades sorprendentes, también plantea serias preocupaciones sobre la invasión de la privacidad y la seguridad de los datos personales.

#### **Desafíos éticos en la implementación de IA**
No es suficiente desplegar IA sin prever sus riesgos. Empresas como Amazon, Google y Microsoft están uniendo fuerzas para abordar los riesgos y fomentar la creación de productos seguros. La IA debe implementarse de manera que los usuarios se sientan seguros, ya que esto puede aumentar la confianza y la adopción del producto.

---

### **Casos de Uso de TinyML**

#### **TinyML en la Industria**
**Beneficios:**  
TinyML puede reducir el tiempo de inactividad en la industria mediante el monitoreo de fallos en tiempo real, detectando patrones de vibración o sonido que indican problemas en las máquinas antes de que fallen. Esto permite reparaciones proactivas, mejora la productividad y reduce costos.

**Desafíos:**  
Hay que tener cuidado con la exactitud de las predicciones, especialmente en sectores críticos como la aviación. Además, el mantenimiento predictivo puede impactar negativamente en el empleo, lo que plantea preguntas sobre el equilibrio entre eficiencia y el impacto en la fuerza laboral.

#### **TinyML en el Medio Ambiente**
**Beneficios:**  
En el campo medioambiental, TinyML puede monitorear animales en peligro de extinción, como los elefantes, mediante dispositivos portátiles que recopilan datos en tiempo real. Esto permite obtener información precisa sin arriesgar a los humanos en terrenos peligrosos y reduce los costos de investigación.

**Desafíos:**  
La seguridad de los datos es una preocupación clave. Si los datos cayeran en manos equivocadas, como cazadores furtivos, podrían empeorar la situación. Además, los datos generados por TinyML no siempre son confiables, y la calidad de los mismos es crítica.

#### **TinyML y la Interacción Humana**
**Beneficios:**  
TinyML mejora la accesibilidad para personas con discapacidades, permitiendo interacciones sin necesidad de dispositivos físicos. Esto simplifica el diseño de interfaces y hace la tecnología más intuitiva para todos.

**Desafíos:**  
Es necesario asegurar que los modelos de aprendizaje automático no estén sesgados y que respeten la diversidad cultural y geográfica. Además, la privacidad del usuario se ve amenazada si los dispositivos TinyML están siempre encendidos, lo que podría capturar información sin consentimiento.

---

### **Diseño, Desarrollo e Implementación de TinyML**

#### **Diseño Proactivo y Ética**
Es vital considerar el diseño, desarrollo e implementación de estos sistemas de manera proactiva. El diseño debe tener en cuenta a quién está dirigido el producto y qué sucede si falla. El desarrollo debe preocuparse por los sesgos en los datos y su equidad, mientras que la implementación debe garantizar la seguridad y privacidad de los usuarios.

#### **Importancia de la Ética en el Desarrollo de IA**
Susan Kennedy, experta en ética aplicada y sistemas de aprendizaje automático, nos guiará en el curso sobre los impactos éticos, sociales y políticos de tecnologías como TinyML. Es crucial que, como ingenieros y científicos, integremos valores humanos en todas las etapas de desarrollo de la IA.

---

### **Conclusión**
La creación y despliegue de TinyML debe realizarse de manera responsable. Necesitamos considerar cuidadosamente las implicaciones de esta tecnología, asegurando que esté alineada con los valores humanos y que sea segura para la sociedad. TinyML tiene el potencial de mejorar nuestra vida diaria, pero solo si se desarrolla e implementa de forma ética y responsable.
