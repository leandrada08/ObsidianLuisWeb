## Introducción
El **aprendizaje automático** consiste en diseñar **modelos estadísticos** que pueden identificar patrones en los datos y utilizar esos patrones para realizar predicciones o tomar decisiones. En lugar de programar manualmente reglas explícitas para resolver un problema, el objetivo de ML es que el sistema **aprenda** cómo resolver el problema directamente de los datos.
La idea central es que el sistema se **entrena** con un conjunto de datos y luego puede generalizar sus conocimientos a nuevos ejemplos que no ha visto antes. Esto hace que ML sea útil en una amplia variedad de aplicaciones como el reconocimiento de voz, la visión por computadora, la detección de fraudes y más.
- **Aplicaciones cotidianas** de ML: Mejora de imágenes en smartphones, reconocimiento de voz ("OK Google", "Alexa"), recomendaciones en redes sociales, entre otras. Todo esto demuestra que ML está presente en nuestras vidas diarias.
![[Captura de pantalla 2024-10-09 a las 11.40.42 a. m..png|500]]
### Subclases de ML en aplicaciones
1. **Clasificación de imágenes**: Identificar si una imagen contiene un gato o un perro. Este tipo de ML es estadístico, por lo que no siempre es preciso.
2. **Detección de objetos**: Localizar con precisión elementos en una imagen, como diferenciar entre naranjas y manzanas.
3. **Segmentación de imágenes**: Usada en coches autónomos para identificar humanos, carriles y bordes de carreteras mediante el coloreado de píxeles.
4. **Traducción automática**: Ejemplo aplicado a gafas inteligentes, donde la traducción de voz en tiempo real es procesada por un modelo de ML.
5. **Sistemas de recomendación**: Basado en interacciones como "me gusta" o "no me gusta", sistemas como redes sociales usan ML para ofrecer contenido personalizado.




### **Componentes Fundamentales del Machine Learning**
Un sistema de **aprendizaje automático** típicamente involucra los siguientes elementos:
- **Datos de entrenamiento**: Estos son los datos que se utilizan para **entrenar** el modelo. Deben ser representativos del problema que se quiere resolver.
- **Algoritmo de aprendizaje**: Es el método que se utiliza para construir el modelo a partir de los datos. Existen diferentes tipos de algoritmos, dependiendo de la tarea y el tipo de datos.
- **Función objetivo (o función de costo)**: Es una función que el algoritmo busca **minimizar o maximizar**. En un problema de regresión, podría ser el **error cuadrático medio**, mientras que en clasificación podría ser una **función de entropía cruzada** o **accuracy**.
- **Modelo**: Después de entrenar, el algoritmo produce un modelo que puede usarse para hacer predicciones o tomar decisiones basadas en nuevos datos.
- **Generalización**: La capacidad del modelo para **performar bien en nuevos datos** que no ha visto antes, lo que es clave en ML.



## Tipos de Sistemas de Aprendizaje Automático

Los sistemas de aprendizaje automático pueden ser clasificados según varios criterios, entre ellos el tipo de supervisión, la capacidad de aprendizaje continuo y el enfoque de modelado:

1. **Supervisado vs No Supervisado**
   - **Aprendizaje Supervisado**: Los algoritmos supervisados se entrenan usando datos etiquetados, es decir, ejemplos con entradas y sus respectivas salidas correctas. Un ejemplo es un sistema que aprende a clasificar correos electrónicos como spam o no spam. Entre los algoritmos más comunes se encuentran la regresión lineal, la regresión logística, y las máquinas de soporte vectorial (SVM).
   - ![[Captura de pantalla 2024-10-04 a las 12.03.03 p. m..png]]
   - **Aprendizaje No Supervisado**: Los algoritmos no supervisados trabajan con datos que no tienen etiquetas. El objetivo es encontrar patrones subyacentes en los datos, como en el caso del clustering. Ejemplos de algoritmos no supervisados incluyen K-Means y PCA (Análisis de Componentes Principales).
   ![[Captura de pantalla 2024-10-04 a las 12.03.58 p. m..png]]
   - **Aprendizaje Semi-Supervisado**: En este tipo, el algoritmo se entrena con una combinación de datos etiquetados y no etiquetados. Esto es útil cuando etiquetar todos los datos es costoso y laborioso.
   - ![[Captura de pantalla 2024-10-04 a las 12.04.22 p. m..png]]
   - **Aprendizaje por Refuerzo**: Este es un paradigma distinto en el que un agente interactúa con el entorno, tomando acciones para maximizar una recompensa. Es útil para problemas donde el resultado depende de una serie de decisiones, como en los videojuegos o robótica.
   - ![[Captura de pantalla 2024-10-04 a las 12.05.17 p. m..png]]

2. **Enfoques de Aprendizaje Basados en Instancias vs Modelos**
   - **Aprendizaje Basado en Instancias**: Estos algoritmos memorizan los ejemplos del entrenamiento y generalizan al comparar nuevos ejemplos con los almacenados, como el algoritmo K-Nearest Neighbors.
   - ![[Captura de pantalla 2024-10-04 a las 12.07.51 p. m..png]]
   - **Aprendizaje Basado en Modelos**: Estos algoritmos crean un modelo general a partir de los datos de entrenamiento. Utilizan los datos para ajustar los parámetros del modelo con el objetivo de minimizar una función de error. Ejemplos incluyen la regresión lineal y las redes neuronales.
   - ![[Captura de pantalla 2024-10-04 a las 12.08.05 p. m..png]]

### Aprendizaje en Lote vs En Línea

1. **Aprendizaje en Lote (Batch Learning)**
   - **Descripción**: Los sistemas que aprenden en lote son incapaces de aprender de manera continua. Primero, el sistema es entrenado utilizando todos los datos disponibles, y posteriormente se despliega y no aprende más. Este enfoque se llama "aprendizaje fuera de línea" ya que se requiere detener el sistema para actualizar el modelo con datos nuevos.
   - **Ventajas y Desventajas**: El aprendizaje en lote suele ser muy eficiente cuando se tiene acceso a grandes cantidades de datos y se dispone de recursos de cómputo suficientes para el procesamiento inicial. Sin embargo, requiere volver a entrenar el sistema cada vez que hay datos nuevos, lo cual puede ser costoso y poco flexible para entornos dinámicos.

2. **Aprendizaje en Línea (Online Learning)**
   - **Descripción**: Los sistemas de aprendizaje en línea entrenan de forma continua, procesando los datos a medida que llegan. Esto es útil en situaciones donde los datos se generan constantemente, como en la monitorización de redes de sensores.
   - **Ventajas y Desventajas**: Este enfoque es más adecuado para aplicaciones donde los datos cambian rápidamente o donde es impráctico almacenar todos los datos para el entrenamiento en lote. Sin embargo, los sistemas de aprendizaje en línea deben ser diseñados para gestionar cambios bruscos y evitar el "olvido catastrófico", donde el sistema pierde conocimiento previo debido a una adaptación excesiva a datos recientes.

### Desafíos Principales del Aprendizaje Automático

1. **Cantidad Insuficiente de Datos de Entrenamiento**
   - **Problema**: La mayoría de los algoritmos de aprendizaje automático necesitan una gran cantidad de datos para funcionar correctamente. Sin suficientes ejemplos, el modelo tendrá problemas para generalizar correctamente a nuevos datos.
   - **Solución**: Utilizar técnicas como el aumento de datos, recopilar más datos si es posible, o utilizar métodos de aprendizaje que requieran menos datos.
![[Captura de pantalla 2024-10-04 a las 12.11.48 p. m..png]]
2. **Datos No Representativos**
   - **Problema**: Si los datos de entrenamiento no representan bien el problema a resolver, el modelo aprenderá sesgos que afectarán negativamente a su rendimiento. Un modelo basado en datos sesgados tendrá dificultades para generalizar.
   - **Solución**: Asegurarse de que los datos de entrenamiento sean lo más variados y completos posible para cubrir las posibles situaciones del entorno.![[Captura de pantalla 2024-10-04 a las 12.11.23 p. m..png]]

3. **Datos de Mala Calidad**
   - **Problema**: Datos con ruido, errores, o características irrelevantes pueden llevar al modelo a aprender patrones incorrectos. La calidad del modelo depende directamente de la calidad de los datos.
   - **Solución**: Realizar una limpieza cuidadosa de los datos, eliminar errores y, si es necesario, corregir valores atípicos.

4. **Características Irrelevantes o Mal Elegidas**
   - **Problema**: Elegir las características adecuadas es fundamental para un buen rendimiento del modelo. Características irrelevantes pueden dificultar el proceso de aprendizaje.
   - **Solución**: Aplicar técnicas de selección de características y transformar las características (ingeniería de características) para asegurar que el modelo trabaje con la información más útil.

5. **Sobreajuste (Overfitting)**
   - **Problema**: Ocurre cuando el modelo aprende "demasiado bien" los detalles y el ruido del conjunto de entrenamiento, perdiendo la capacidad de generalizar. Esto lleva a un modelo que funciona muy bien con datos de entrenamiento, pero mal con datos nuevos.
   - **Solución**: Utilizar más datos, aplicar regularización al modelo o utilizar técnicas como el ensamble para mejorar la robustez.
![[Captura de pantalla 2024-10-04 a las 12.12.48 p. m..png]]
6. **Subajuste (Underfitting)**
   - **Problema**: Sucede cuando el modelo es demasiado simple para capturar los patrones subyacentes de los datos. El modelo no aprende lo suficiente, ni siquiera los patrones más evidentes.
   - **Solución**: Utilizar un modelo más complejo o entrenarlo durante más tiempo para que pueda aprender mejor las relaciones entre los datos.

7. **Desajuste de Datos (Data Mismatch)**
   - **Problema**: Puede existir una diferencia significativa entre la distribución de los datos de entrenamiento y los datos de producción, lo cual resulta en un mal rendimiento del modelo.
   - **Solución**: Intentar replicar lo mejor posible las condiciones del entorno de producción durante el entrenamiento o ajustar el modelo periódicamente con nuevos datos.




## [[Introduction TinyML|Introduction TinyML]]