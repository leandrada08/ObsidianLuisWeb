
 Este curso se centra en los aspectos prácticos de **TinyML**, donde aprenderás cómo crear un sistema de aprendizaje automático de extremo a extremo para aplicaciones reales. Además, trabajarás con **tres tipos de sensores** diferentes: **sensores acústicos, sensores de imagen y sensores de movimiento**. Estos sensores serán la entrada para los modelos de ML y aprenderás cómo manejar cada tipo de señal.
- Aprenderás a tomar los datos de entrada de los sensores y convertirlos en un **modelo de aprendizaje automático**. Cada sensor proporciona datos únicos y el **modelo de red neuronal** debe adaptarse a estos diferentes tipos de entrada.
- La precisión del modelo es importante, pero también se debe considerar cómo el modelo se desempeña en el mundo real. En este curso, el objetivo es que puedas diseñar una aplicación TinyML de extremo a extremo, no solo enfocarte en la red neuronal sino en toda la tubería de procesamiento y cómo se relacionan los sensores, el modelo y la implementación.
- Una de las principales enseñanzas del curso es cómo aplicar TinyML de manera efectiva, lo cual incluye entender cómo los modelos de aprendizaje automático se construyen dentro de las limitaciones del hardware integrado. Para esto, se explorarán diferentes tipos de redes y métodos de entrenamiento, así como las compensaciones necesarias para ajustar los modelos a los dispositivos embebidos.


### **Ingeniería de Características y Prevención del Sobreajuste**
La ingeniería de características es el proceso de extraer rasgos relevantes de los datos para entrenar la red. Cada sensor tiene características específicas que requieren diferentes enfoques de ingeniería. Se profundizará en esta práctica para preparar adecuadamente los datos provenientes de diferentes tipos de sensores.

#### **Preprocesamiento de Datos**
El preprocesamiento de datos es crucial para el rendimiento del modelo. Este proceso varía según el tipo de sensor y afecta directamente la calidad de las predicciones de la red.

### **Optimización de Modelos para TinyML**
A medida que los modelos se vuelven más grandes y complejos (como VGG-16), surge la necesidad de reducir su tamaño para poder desplegarlos en dispositivos con recursos limitados, como los microcontroladores. En [[Course Applications of TinyML]] se introdujo la idea de la **poda de redes** (pruning), que consiste en eliminar sinapsis o neuronas para reducir la complejidad computacional del modelo. Además, se habló sobre la **cuantización** (quantization), una técnica para reducir la cantidad de memoria requerida representando valores con menor precisión, como pasar de *float32* a *int8*, logrando así una reducción significativa en el tamaño del modelo, aunque con posibles pérdidas de precisión.

La implementación de modelos TinyML no consiste solo en entrenar una red neuronal en un entorno como Google Colab y luego desplegarla en un microcontrolador. Existen varios pasos adicionales para convertir el modelo al formato adecuado para su despliegue en hardware con recursos limitados. Estos procesos incluyen la **cuantización**, que permite reducir el tamaño del modelo para que pueda ser almacenado y ejecutado en dispositivos con memoria limitada.

Otra consideración importante es la robustez del modelo ante variaciones del entorno, como diferencias de iluminación en el caso de sensores de imagen o variaciones en la pronunciación de palabras clave para sensores acústicos. Asegurarse de que los modelos sean generales y no presenten sesgos es esencial para una implementación exitosa en el mundo real.


### **Frameworks para Despliegue en Dispositivos de Recursos Limitados**
TensorFlow se utiliza comúnmente para el entrenamiento de modelos, pero para desplegar estos modelos en dispositivos pequeños, como microcontroladores, se necesita usar frameworks como **TensorFlow Lite**. En este curso, se profundizará en las diferencias entre TensorFlow y TensorFlow Lite, y en cómo adaptar los modelos para que funcionen eficientemente en dispositivos de recursos limitados.





### **Casos de Uso y Aplicaciones de TinyML**
Se analizarán tres aplicaciones distintas en profundidad para entender cómo se ajustan los sistemas embebidos y TinyML a diferentes escenarios. El objetivo es comprender cómo los sensores, el aprendizaje automático y el hardware embebido interactúan y cuál es la mejor manera de optimizar los modelos para cada caso.

En este curso no se implementará físicamente en hardware aún; se centrará en aprender y aplicar los fundamentos del aprendizaje automático en el espacio de las aplicaciones.

![[Captura de pantalla 2024-10-14 a las 12.49.19 p. m..png|300]]


### **Puntos Críticos del Curso**
En este curso de TinyML, se profundiza en la integración de sensores, modelos de redes neuronales y la evaluación de métricas para desarrollar aplicaciones eficientes. Este curso se enfoca en el análisis de tres tipos específicos de sensores: acústicos, de imagen y de movimiento, así como en cómo sus diferencias afectan el procesamiento de datos y el diseño de modelos.

#### Metricas
Las métricas utilizadas para evaluar el rendimiento de las redes neuronales pueden variar según el tipo de sensor y el tipo de datos. Se analizará si existe una métrica única que se pueda aplicar a todos los sensores, o si cada uno necesita métricas específicas para evaluar la efectividad del modelo.

Además, se evaluarán las métricas en el contexto de las limitaciones de los dispositivos embebidos. Esto implica que los modelos deben ser entrenados para adaptarse a las restricciones de memoria y consumo de energía de los dispositivos, manteniendo un equilibrio entre el rendimiento y la eficiencia.
#### **Tipos de Sensores y Aplicaciones**

##### **Sensores Acústicos: Detección de Palabras Clave**  
- Los sensores acústicos se usan principalmente en aplicaciones como la detección de palabras clave, también llamada detección de palabras de activación. Esto se observa en dispositivos como Alexa o Siri, que responden a frases como "Hola Siri" o "OK Google". El proceso implica capturar el audio desde un micrófono, preprocesarlo y luego hacer que una red neuronal determine si la palabra dicha coincide con la configurada para activar el dispositivo.
- Un aspecto importante en la detección de palabras clave es la diversidad en los datos de entrenamiento. Por ejemplo, distintas personas pueden decir "OK Google" de diferentes maneras, lo cual presenta el reto de asegurarse que la red sea lo suficientemente robusta para reconocer esas variaciones sin introducir sesgos.
- Este proceso de preprocesamiento es específico y diferente al de otros tipos de datos, ya que consiste en una red particular que permita extraer información relevante del audio.
##### **Sensores de Imagen: Detección en Entornos de Oficina**  
- Los sensores de imagen, como las cámaras, se utilizan para aplicaciones como la detección de ocupación en oficinas. Esto permite, por ejemplo, apagar las luces cuando no hay nadie en la habitación, ahorrando energía. En este tipo de aplicaciones, los datos de la cámara se procesan mediante redes neuronales convolucionales que detectan la presencia de personas.
- En este curso se introduce el concepto de **aprendizaje por transferencia**, que permite acelerar el tiempo de entrenamiento de las redes. Esto es crucial para aplicaciones TinyML, donde se necesita una respuesta rápida y eficiente.


##### **Sensores de Movimiento: Mantenimiento Predictivo en Entornos Industriales**  
- Los sensores de movimiento, como acelerómetros y giroscopios, se utilizan para monitorear el rendimiento de máquinas en aplicaciones industriales. El objetivo es detectar anomalías en el comportamiento de una máquina que puedan indicar fallas futuras, permitiendo realizar mantenimiento predictivo y evitar tiempos de inactividad costosos.
- Este tipo de aplicación utiliza datos de series temporales, y se emplea un enfoque diferente al de los sensores anteriores: **autoencoders** para detectar comportamientos anómalos sin necesidad de aprendizaje supervisado. Esto es útil porque, en muchos casos, no se tiene un conjunto de datos claro con ejemplos de fallos, por lo que la red debe aprender a identificar anormalidades por sí misma.



### **El Papel de los Sensores en Aplicaciones TinyML**

Los sensores desempeñan un papel fundamental en las aplicaciones de aprendizaje automático al conectar los recursos algorítmicos con el entorno físico. Actualmente, existe un impulso continuo hacia sensores de bajo costo y alto rendimiento para aplicaciones como el monitoreo de la calidad del aire y el mantenimiento predictivo. Los sensores se pueden categorizar en dos tipos principales: **in situ** y **sensores remotos**.

Los **sensores in situ** vienen en diversas formas, cada uno con su propio mecanismo de detección, que puede involucrar reacciones químicas, luz o cambios de voltaje debido al estrés del material. Estos sensores miden atributos locales en el lugar del elemento de detección y suelen caracterizarse como sensores físicos. Los **sensores remotos**, por otro lado, operan a distancia y son generalmente técnicas ópticas. Por ejemplo, la temperatura se puede medir mediante un termómetro infrarrojo y las concentraciones de gases atmosféricos se pueden detectar mediante mediciones satelitales. Aunque los sensores in situ pueden utilizar mecanismos ópticos, se diferencian porque solo capturan datos locales.

En TinyML, los datos de los sensores generalmente vienen en forma de imágenes o series temporales, lo que permite realizar análisis espaciales o temporales mediante modelos de aprendizaje automático. Los sensores permiten la retroalimentación y el monitoreo en tiempo real del entorno local, ya sea en el punto de detección o de forma remota. Por ejemplo, una red de sensores de gas in situ puede monitorear la contaminación en un campus o instalación industrial, mientras que una cámara remota puede rastrear las condiciones meteorológicas mediante el análisis de formaciones de nubes en ubicaciones con acceso limitado a internet.

En el caso de los sensores que producen datos en serie temporal, las mediciones individuales pueden servir como características en un modelo de aprendizaje automático. Un segmento de la serie temporal también puede utilizarse para propósitos de clasificación o detección de anomalías. En métodos basados en imágenes, cada píxel del mapa de bits puede aplanarse y utilizarse como una característica en una red neuronal.

Los sensores se pueden utilizar de forma individual o combinada para producir efectos sinérgicos, mejorando sus capacidades, especialmente cuando se combinan con el aprendizaje automático en línea. Un ejemplo común es la combinación de un **acelerómetro** y un **giroscopio**, a menudo presentes en smartphones y dispositivos integrados, que juntos pueden diferenciar movimientos complejos en 6 ejes. Esto permite que los teléfonos inteligentes detecten cuando se levantan o cuando el usuario sufre una caída. También se utilizan en drones para estimar la velocidad y dirección del viento. Los **sensores de vibración** son otro tipo de sensor común en entornos industriales que permiten el mantenimiento predictivo, ayudando a mejorar la disponibilidad de la maquinaria al detectar vibraciones anómalas antes de que ocurra una falla catastrófica.

El uso de sensores para el aprendizaje automático integrado también presenta desafíos. Primero, los sensores tienen una vida útil limitada, lo cual debe tenerse en cuenta durante el desarrollo. Un sistema complejo no debería volverse inutilizable si un sensor falla, y el sistema debería tener una acción predeterminada en caso de fallo. Los sensores también pueden mostrar ruido y deriva, que a menudo son difíciles de modelar estadísticamente. Los sistemas TinyML deben ser lo suficientemente robustos como para no verse afectados por el ruido o la deriva durante las operaciones regulares. Además, los sensores mal aislados pueden interferir con otras mediciones, y aumentar el número de sensores puede hacer que un sistema sea más complejo y consuma más energía. Ser competente en TinyML implica no solo comprender el aprendizaje automático y los sistemas integrados, sino también gestionar las limitaciones impuestas por los desafíos de ingeniería eléctrica y mecánica.

Para abordar estos desafíos, considera las siguientes recomendaciones:

1. **Recolecta Datos Ricos**: En el aprendizaje automático, los datos son fundamentales. Recopilar una gran cantidad de datos ayuda a que los modelos TinyML aproximen eficazmente la distribución de los datos. Más datos siempre son beneficiosos.

2. **Evita el Sobre-Ingeniería**: Aunque pueda ser tentador agregar muchos sensores a un sistema, es recomendable seguir la navaja de Occam: mantén el diseño simple. Seleccionar los sensores de manera inteligente y mínima reduce las complicaciones de hardware.

3. **Cubre las Fuentes de Variación**: Asegúrate de que los datos recopilados cubran una amplia variedad de escenarios sin complicar en exceso el sistema. Esto puede involucrar la recopilación de datos que incluyan casos extremos y agregar sensores que proporcionen poder explicativo adicional.

4. **Utiliza la Tasa de Muestreo Más Alta Posible**: Aunque transmitir y almacenar datos de alta frecuencia puede ser costoso, los sistemas TinyML mitigan este problema ya que las inferencias se realizan en el dispositivo. Es más fácil reducir la resolución de los datos que aumentarla, por lo que se recomienda recolectar datos a la mayor resolución posible para mantener la flexibilidad en los procesos de ingeniería de datos.

Independientemente del tipo de datos del sensor—sonidos, imágenes, vibraciones o señales eléctricas—estos insumos se pueden combinar para entrenar modelos de aprendizaje automático que clasifiquen, modelen o predigan eventos en tiempo real usando microcontroladores de bajo costo, lo que hace de TinyML una herramienta extremadamente poderosa.


