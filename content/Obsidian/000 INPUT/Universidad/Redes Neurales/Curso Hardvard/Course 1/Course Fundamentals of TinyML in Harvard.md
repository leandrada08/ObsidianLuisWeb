## Informacion del curso

### Instructores
- **Laurence Moroney** (Google): Introducirá los fundamentos del machine learning en los cursos 1 y 2.
- **Pete Warden** (Google): Desarrollador de TensorFlow Lite Micro, participará en los cursos 2 y 3.
### Público objetivo
- **TinyML es accesible para todos**, sin importar edad, ubicación o nivel de conocimiento. El objetivo es empoderar a cualquier persona con acceso a educación de vanguardia.
- Este curso es útil para:
  - **Estudiantes**: Desde estudiantes de secundaria hasta universitarios o aprendices de por vida que deseen profundizar en ML.
  - **Practicantes**: Aquellos interesados en desarrollar aplicaciones o productos basados en TinyML, aprendiendo sobre el diseño a través de las capas de aplicaciones, tiempos de ejecución y hardware.
  - **Ingenieros**: Pueden ser ingenieros de ML que buscan implementar TinyML en nuevo hardware o ingenieros de hardware que quieran aprender sobre ML y los desafíos del diseño de sistemas TinyML.

### Estructura del curso
![[Captura de pantalla 2024-10-09 a las 10.28.57 a. m..png]]
1. **Curso 1: Fundamentos de TinyML**:
   - Introducción al lenguaje de machine learning: Se centrará en el **lenguaje del aprendizaje automático** (ML) con un enfoque en el rendimiento y limitaciones de tiempo.
   - Se enseñarán los conceptos básicos, sin suponer conocimientos previos sobre ML o sistemas embebidos.
   - **Habilidades requeridas**: Programación básica en Python, nada avanzado, se puede aprender sobre la marcha.
   
2. **Curso 2: Aplicaciones de TinyML**:
   - Aplicaciones de TinyML, incluyendo el uso de sensores: Exploraremos aplicaciones como la **detección de palabras clave** ("Alexa", "Ok Google") y otras aplicaciones interesantes que se beneficiarán del ML.
   - Uso de Python en **Google Colab** para desarrollar aplicaciones.
   - Google Colab será utilizado como entorno de programación para la creación de proyectos en Python.

3. **Curso 3: Implementación en microcontroladores**:
   - Despliegue de modelos ML en dispositivos embebidos: Se implementarán modelos en **microcontroladores**, considerando sus limitaciones de potencia y capacidad de procesamiento.
   - Se necesitarán conocimientos básicos de programación en **C y C++**.
   - Programación física de un microcontrolador mediante un **IDE** (Entorno de Desarrollo Interactivo).
   - Se proporcionará el IDE necesario para programar los dispositivos.


### Metodología del curso
- **Aprendizaje práctico**:
  - El curso tiene una fuerte base práctica con tareas programando en **TensorFlow** y sus variantes adaptadas para dispositivos pequeños, como **TensorFlow Lite Micro**.
  - Los estudiantes programarán en un **IDE web** (Google Colab) y eventualmente implementarán sus modelos en hardware físico.
#### Software utilizado
- Tensor flow para machine learning
- Google colab 
#### Hardware utilizado
- Se proporcionará un **microcontrolador Arm Cortex-M4** equipado con varios sensores como:
  - **Sensor de color, proximidad y brillo**
  - **Micrófono digital**
  - **Sensor de movimiento, vibración y orientación**
  - **Sensor de temperatura, humedad y presión**

#### Componentes del curso
1. **Videos**:
   - Proporcionan los fundamentos teóricos y la introducción a nuevos conceptos y temas relacionados con TinyML.
2. **Materiales de lectura**:
   - Complementan los videos ofreciendo una visión más profunda y ejemplos adicionales sobre los temas tratados.
3. **Foros de discusión**:
   - Espacios interactivos donde los estudiantes pueden intercambiar ideas y fomentar debates sobre temas clave, como la IA responsable.
4. **Google Colab**:
   - Plataforma utilizada para la parte práctica del curso. Los estudiantes programarán en Google Colab para resolver desafíos prácticos de TinyML.
   - Se usa principalmente en los **Cursos 1 y 2**.
5. **Asignaciones**:
   - Desafíos prácticos que ayudan a aplicar las habilidades aprendidas en Google Colab.
   - En el **Curso 3**, los estudiantes implementarán lo aprendido en un **dispositivo físico**.

6. **Cuestionarios**:
   - Pruebas formativas diseñadas para ayudar a los estudiantes a reflexionar sobre los conceptos clave vistos en los videos y materiales de lectura.
   - Actúan como una pausa para revisar y consolidar los conocimientos adquiridos.

7. **Exámenes**:
   - Evaluaciones formales, disponibles para aquellos que estén inscritos en el programa de certificación.
   - Los exámenes cubren todo el contenido del curso: videos, Colabs, lecturas, cuestionarios, tareas y discusiones.
#### Metodología de aprendizaje
- El curso está diseñado para adaptarse a diferentes estilos de aprendizaje:
   - **Videos** para los estudiantes que prefieren aprender de forma visual.
   - **Lecturas** para quienes prefieren profundizar en el contenido a través de la lectura.
   - **Prácticas en Google Colab** para aquellos que aprenden mejor haciendo.

## Introduccion

#### Definición y Concepto
- **TinyML (Tiny Machine Learning)** es la intersección entre machine learning y sistemas embebidos, caracterizado por la capacidad de ejecutar análisis de datos en dispositivos pequeños y de bajo consumo energético (en el orden de milivatios). Estos dispositivos pueden operar durante largos períodos con una batería pequeña, como una pila de botón.

- **Machine Learning (ML)** es una subdisciplina de la inteligencia artificial que, mediante el uso de grandes volúmenes de datos, infiere patrones y hace predicciones sobre datos nuevos.

#### Ejemplo práctico
- **Keyword spotting o hotword detection**: "Ok Google", "Hey Siri", o "Alexa" son ejemplos de reconocimiento de palabras clave que hacen que los dispositivos se activen. Estos dispositivos, a pesar de usar tecnología similar, dependen de estar conectados a una fuente de energía. TinyML se diferencia en que busca implementar ML en procesadores pequeños que operan sin estar conectados a la red eléctrica, usando solo una batería.
- **ElephantEdge**: Ejemplo de aplicación de TinyML para monitorear y proteger a elefantes mediante collares inteligentes con sensores.
- **Gafas inteligentes**: Aplicaciones como la traducción de voz en tiempo real que requiere tiempos de respuesta instantáneos para que la conversación sea fluida.
- La intersección de las **necesidades de la aplicación** (como la forma del dispositivo) y las **limitaciones del hardware** es clave para habilitar TinyML.
#### Aplicaciones futuras de TinyML
- **Drones autónomos**: Usados para vigilancia y monitoreo de áreas peligrosas o inaccesibles, como la selva amazónica, donde se usan para reforestar.
- **Robots móviles**: En el sector servicios, pueden asistir en el cuidado de personas mayores, requiriendo múltiples sensores para moverse y operar eficientemente con batería.
- **Gafas inteligentes**: Podrían implementar reconocimiento contextual para mejorar la audición o realizar traducción en tiempo real.
- **Dispositivos médicos**: Pacemaker como el Micra de Medtronic, que al incorporar ML podría monitorear la salud del corazón de forma más eficiente.
- **Chips cerebrales**: Proyectos como el de Elon Musk buscan interpretar señales neuronales para tratar condiciones como depresión o insomnio.

#### Impacto presente y futuro
TinyML puede transformar múltiples sectores, desde el cuidado de la fauna (ej. collares inteligentes para elefantes que monitorean el riesgo de caza furtiva) hasta la conservación del medio ambiente. Estas aplicaciones permiten tomar decisiones en tiempo real, directamente en el lugar donde se generan los datos, sin necesidad de enviar la información a grandes servidores.







## Final del curso
En esta clase, **Vijay Janapa Reddi** cierra el Curso 1 y da una introducción a lo que vendrá en los siguientes cursos. Aquí te dejo un resumen clave de los puntos tratados:

### 1. **TinyML y su relevancia**
   - TinyML es una extensión de la IA que se lleva a los dispositivos más cercanos a las personas, como teléfonos inteligentes y dispositivos inteligentes (por ejemplo, Google Assistant).
   - Aunque la IA comenzó en grandes centros de datos, está migrando hacia dispositivos más pequeños para ofrecer aplicaciones en tiempo real con menor latencia.
   - La clave no es solo la capacidad de estos dispositivos, sino **los datos** que generan. Los dispositivos modernos, como teléfonos, contienen numerosos sensores (acelerómetro, giroscopio, magnetómetro, etc.) que generan datos valiosos que no se están aprovechando completamente.

### 2. **Aplicaciones de TinyML**
   - TinyML puede impactar muchas áreas, desde la robótica y los drones hasta la conservación del medio ambiente.
   - Un ejemplo dado fue el proyecto **ElephantEdge**, que utiliza TinyML para monitorear elefantes y proteger la fauna.
   - En resumen, **la capacidad de TinyML está en su poder para capturar y procesar datos en tiempo real**, abriendo nuevas posibilidades para el desarrollo de aplicaciones innovadoras.

### 3. **Desafíos éticos**
   - La IA es una tecnología disruptiva, lo que implica que puede cambiar significativamente muchos aspectos de la vida diaria y de los negocios.
   - **El uso responsable de la IA** es crucial. Como mencionó el Dr. Kennedy en clases anteriores, **el diseño responsable de IA** implica tener en cuenta los impactos potenciales desde la fase de diseño hasta el desarrollo y la implementación.
   - Aunque la IA tiene un gran potencial, también presenta riesgos y desafíos éticos. **Empresas y consorcios están colaborando** para garantizar que los ingenieros del futuro (como tú) diseñen tecnologías responsables.

### 4. **Importancia de la confianza del usuario**
   - Muchas personas desconfían de los dispositivos que procesan datos, y esto afecta la adopción de la tecnología.
   - **El diseño responsable de IA** busca generar confianza, asegurando que las personas se sientan cómodas con el uso de la tecnología y que comprendan cómo se manejan sus datos.
   - El costo de los errores en el despliegue de IA es grande y afecta no solo a productos individuales, sino a compañías completas.

### 5. **Curso 2 y Curso 3**
   - En los próximos cursos, se profundizará en cómo se desarrollan los algoritmos de IA y cómo se despliegan en dispositivos.
   - **El concepto de IA responsable** seguirá siendo un eje clave, y se conectará con cómo se implementa TinyML de manera segura y ética.

En resumen, esta lección refuerza la importancia de **entender la IA no solo desde el punto de vista técnico**, sino también desde el lado **ético y responsable**, para que las futuras aplicaciones de TinyML sean útiles y confiables para todos.


En este video, **Vijay Janapa Reddi** hace un resumen de los puntos clave que cubriste en el Curso 1 y proporciona una vista previa de lo que está por venir en los próximos cursos. Aquí te dejo un resumen simplificado de los conceptos importantes que menciona:

### 1. **Fundamentos de Machine Learning y Deep Learning**
   - **Machine Learning (ML)** es un subcampo de la inteligencia artificial (IA), y el curso se enfocó en **Deep Learning** (aprendizaje profundo), que utiliza redes neuronales para aprender patrones a partir de grandes cantidades de datos.
   - Estas redes neuronales aprenden a hacer predicciones basadas en patrones de los datos que han visto antes. Si se enfrentan a datos nuevos y no conocidos, pueden cometer errores, lo cual es parte de la limitación de este enfoque.

### 2. **El proceso de entrenamiento**
   - El **proceso de entrenamiento** de una red neuronal sigue un ciclo de hacer una predicción, medir su precisión (¿el modelo predijo correctamente?) y optimizar la predicción para mejorarla.
   - En este proceso, usamos **descenso de gradiente estocástico** para minimizar el error del modelo y ajustar los pesos de las conexiones neuronales.
   - Este ciclo de predicción y corrección se repite hasta que el modelo alcanza una alta precisión o un bajo error.

### 3. **Importancia de la topología de la red**
   - La **topología** de una red neuronal, es decir, la cantidad de neuronas y cómo están conectadas, depende del desarrollador. A través de este proceso, ajustamos los pesos de las conexiones para reducir el error en las predicciones.
   - Las redes densas o conectadas completamente (MLPs) son un ejemplo simple pero poderoso de cómo podemos entrenar redes para clasificar imágenes, como en el caso del conjunto de datos **MNIST**, donde se clasificaban dígitos escritos a mano.

### 4. **Transformaciones de datos y aumento de datos**
   - Durante el entrenamiento, aprendiste sobre **transformaciones de datos** (como aplanar imágenes para prepararlas para una red) y **aumento de datos**, que implica aplicar técnicas como rotaciones o cambios de tamaño a las imágenes para aumentar el conjunto de datos de forma artificial.
   - El aumento de datos es esencial para mejorar la capacidad de generalización de las redes neuronales.

### 5. **Convoluciones y extracción de características**
   - Aprendiste sobre las **convoluciones**, un proceso clave en la visión por computadora, donde los filtros extraen características específicas de una imagen (como bordes, patrones, etc.). Esto ayuda a simplificar y destacar las partes más importantes de la imagen.
   - Estos filtros permiten a la red identificar patrones críticos en los datos, haciendo que el proceso de clasificación sea más preciso.

### 6. **Arquitectura de redes convolucionales**
   - Las redes convolucionales (CNNs) se utilizan ampliamente para problemas de visión por computadora. Estas redes aplican convoluciones, seguidas de un proceso de **max pooling** (para reducir la cantidad de datos manteniendo las características importantes).
   - Después de aplicar varias convoluciones y filtros, las características más importantes se pasan a una capa densa que finalmente hace la predicción.

### 7. **Hardware y recursos limitados**
   - También se discutió cómo estos modelos de aprendizaje profundo se entrenan en hardware especializado, como **TPUs** (Tensor Processing Units), para acelerar el proceso de entrenamiento.
   - Sin embargo, para el campo de **TinyML**, estamos interesados en cómo implementar modelos de machine learning en dispositivos pequeños y con recursos limitados, como microcontroladores, que tienen mucha menos capacidad (por ejemplo, 256 KB de memoria en comparación con los 17 MB de un modelo de MobileNet).
   - Esto crea grandes desafíos, pero también oportunidades emocionantes para desplegar machine learning en dispositivos pequeños y ubicuos.

### 8. **Desafíos y oportunidades futuras**
   - A medida que pasamos de entrenar modelos en grandes centros de datos a implementarlos en dispositivos más pequeños (microcontroladores), hay muchos desafíos, como la necesidad de hacer los modelos más pequeños sin perder precisión.
   - En los próximos cursos, aprenderás cómo hacer los modelos más eficientes y cómo optimizar el uso del hardware limitado de los dispositivos TinyML.

¡Claro! Vamos a desglosar las dos últimas clases impartidas por **Vijay Janapa Reddi** de una manera sencilla para que puedas comprender mejor los conceptos clave.

---

### **Clase 1: Resumen del Curso 1 y Introducción al Curso 2**

**Objetivos del Curso 1:**
1. **Introducción a TinyML:** Entender qué es TinyML y por qué es importante.
2. **Fundamentos de Machine Learning (ML):** Asegurarse de que todos tengan una base sólida en los conceptos básicos de ML.

**¿Qué es TinyML?**
- **TinyML** se refiere a la implementación de modelos de aprendizaje automático en dispositivos pequeños y con recursos limitados, como microcontroladores.
- A diferencia de los centros de datos grandes y potentes donde se entrenan y ejecutan modelos de ML tradicionales, TinyML lleva la inteligencia directamente a los dispositivos que usamos en nuestra vida diaria (smartphones, asistentes de voz, sensores, etc.).

**Por Qué TinyML es Importante:**
- **Interactividad en Tiempo Real:** Al ejecutar ML directamente en el dispositivo, se reduce la latencia (tiempo de respuesta), lo que permite aplicaciones más rápidas y responsivas.
- **Eficiencia Energética:** Los dispositivos pequeños consumen menos energía, lo que es crucial para baterías de larga duración.
- **Privacidad y Seguridad:** Los datos no necesitan ser enviados a la nube, lo que mejora la privacidad del usuario.

**Desafíos de TinyML:**
- **Recursos Limitados:** Menor capacidad de memoria y procesamiento en comparación con los centros de datos.
- **Optimización de Modelos:** Necesidad de reducir el tamaño de los modelos sin perder precisión.
- **Fragmentación de Hardware:** Diferentes dispositivos pueden tener distintas capacidades y requerimientos.

**Próximos Pasos en el Curso 2:**
- **Construcción de Aplicaciones TinyML:** Aplicar los fundamentos aprendidos para crear aplicaciones reales.
- **Optimización de Modelos:** Técnicas como **pruning** (eliminar partes innecesarias del modelo), **quantization** (reducir la precisión de los números usados en el modelo) y **knowledge distillation** (transferir conocimientos de un modelo grande a uno más pequeño).
- **Despliegue en Hardware:** Convertir modelos de TensorFlow a TensorFlow Lite y optimizarlos para que funcionen en microcontroladores con recursos limitados.

---

### **Clase 2: Fundamentos de Deep Learning y Preparación para TinyML**

**Repaso de Conceptos Básicos de Machine Learning:**
- **Deep Learning:** Subcampo de ML que utiliza redes neuronales profundas para aprender patrones complejos en grandes conjuntos de datos.
- **Redes Neuronales:** Compuestas por capas de neuronas que procesan información. La topología (número de capas, número de neuronas por capa) es elegida por el desarrollador.

**Proceso de Entrenamiento de una Red Neuronal:**
1. **Hacer una Predicción:** La red intenta predecir una salida basada en una entrada.
2. **Medir la Precisión:** Se compara la predicción con la respuesta correcta utilizando métricas como **precisión (precision)** y **recall**.
3. **Optimizar:** Si la predicción es incorrecta, se ajustan los pesos de las conexiones neuronales para mejorar futuras predicciones.
4. **Repetir (Epochs):** Este ciclo se repite muchas veces (épocas) hasta que el modelo alcanza una precisión aceptable.

**Minimización del Error:**
- **Stochastic Gradient Descent (SGD):** Técnica para ajustar los pesos de la red minimizando el error.
- **Función de Pérdida (Loss Function):** Mide cuánto se está equivocando el modelo. El objetivo es minimizar esta función.

**Importancia de la Topología de la Red:**
- **Elección de Neuronas y Conexiones:** Determina cómo el modelo aprende y qué tan bien puede generalizar a nuevos datos.
- **Redes Densas (MLPs):** Cada neurona en una capa está conectada a todas las neuronas de la siguiente capa. Son buenas para tareas simples pero pueden sobreajustarse en datos complejos.

**Transformaciones y Aumento de Datos:**
- **Transformación de Datos:** Convertir datos crudos (como imágenes) en un formato adecuado para la red neuronal (por ejemplo, aplanar una imagen 28x28 en un tensor de 784 elementos).
- **Aumento de Datos (Data Augmentation):** Crear variaciones de los datos originales (rotaciones, cambios de tamaño, etc.) para aumentar la diversidad del conjunto de datos y mejorar la capacidad de generalización del modelo.

**Extracción de Características con Convoluciones:**
- **Filtros (Convolutions):** Detectan características específicas en las imágenes (bordes, texturas). Ayudan a simplificar y resaltar la información importante.
- **Max Pooling:** Reduce la cantidad de datos manteniendo las características más importantes, lo que ayuda a disminuir la complejidad del modelo y evitar el sobreajuste.

**Desafíos del Entrenamiento y Recursos:**
- **Hardware Especializado:** Entrenar modelos grandes requiere GPUs o TPUs que son costosas y consumen mucha energía.
- **TinyML en Dispositivos Pequeños:** Requiere optimizar los modelos para que sean lo suficientemente pequeños y eficientes para funcionar en microcontroladores con muy poca memoria y potencia de procesamiento.

**Futuro y Continuación del Aprendizaje:**
- **Curso 2 y 3:** Se enfocarán en construir aplicaciones reales de TinyML, optimizar modelos para dispositivos pequeños y desplegarlos en hardware específico.
- **Interacción entre Capas:** Entender cómo las diferentes capas de un modelo interactúan y cómo optimizarlas para mejorar el rendimiento y reducir el tamaño del modelo.

---

### **Resumen Final: Claves para Avanzar en TinyML**

1. **Comprender los Fundamentos:** Tener una base sólida en machine learning y deep learning es crucial para avanzar en TinyML.
2. **Optimización de Modelos:** Técnicas como pruning, quantization y knowledge distillation son esenciales para reducir el tamaño de los modelos sin perder precisión.
3. **Conversión a TFLite:** Convertir modelos de TensorFlow a TensorFlow Lite es un paso necesario para desplegar modelos en dispositivos pequeños.
4. **Desafíos de Hardware:** Adaptar modelos para que funcionen en microcontroladores requiere comprender las limitaciones de estos dispositivos y cómo superar esos desafíos.
5. **Aplicaciones Prácticas:** El siguiente curso se enfocará en aplicar estos conocimientos para crear aplicaciones reales en áreas como el habla, visión y sensores.

**Consejo Final:**
Mantente entusiasmado y abierto a aprender. TinyML es un campo en rápido crecimiento con muchas oportunidades para innovar y crear soluciones que impacten positivamente en la vida diaria y en el medio ambiente.

¡Buena suerte en tu viaje hacia TinyML y en los próximos cursos!
