- En el TB de los sumadores tenemos instanciados los 3 sumadores para compararlos
- En el multiplicador, se compara el booth contra el tradicional. En el de booth se genera con tareas
- Tengo que armar un proyecto para sumadores, otro para multiplicadores y otro para FIR
- Debemos arman un archivo top level para cada bloque y instanciar todos los bloques de estos con if
- Para comparar que hciismos bien el top, tenemos que comparar el bloque top con cada bloque seleccionado
	- En el tb tenemos comparadores a la salida entre los bloques
	- Nosotros tenemos que hacer 3 comparadores ahora para comparar el top con cada componente y se tiene que habilitar cada comparador con cada bloque
![[Pasted image 20240219214200.png]]














## Resumen HARPA

- [00:46](https://www.youtube.com/watch?v=6e_r3Ia1vcs&t=46s) 📝 Objetivo del trabajo de análisis de complejidad en circuitos:

  - Analizar la complejidad de sumadores, multiplicadores y filtros.
  - Comparar diferentes arquitecturas y determinar su complejidad y velocidad.
  - Utilizar códigos proporcionados para implementar y comparar distintas estructuras.

- [03:58](https://www.youtube.com/watch?v=6e_r3Ia1vcs&t=238s) 🛠️ Estructura de archivos y funciones de los módulos:

  - Archivos disponibles para sumadores, multiplicadores y filtros.
  - Funciones de los archivos de construcción, simulación y pruebas de los módulos.
  - Uso de registros de entrada y salida para focalizar el análisis de la herramienta.

- [10:39](https://www.youtube.com/watch?v=6e_r3Ia1vcs&t=639s) 🧩 Configuración de proyectos y selección de módulos:

  - Generación de proyectos para cada escenario de prueba (sumadores, multiplicadores, filtros).
  - Inclusión de archivos proporcionados por la cátedra en los proyectos.
  - Configuración de los Define para seleccionar el tipo de estructura a sintetizar en cada proyecto.

- [16:36](https://www.youtube.com/watch?v=6e_r3Ia1vcs&t=996s) 🔄 Simplificación del proceso de síntesis y verificación:

  - Creación de un solo archivo Top Level con Define para seleccionar la estructura a sintetizar.
  - Verificación del diseño utilizando el Top Level en el test bench y comparando las salidas con los módulos individuales.
  - Uso de condicionales de síntesis para simplificar la configuración del proyecto.



- [30:23](https://youtu.be/6e_r3Ia1vcs?t=1823s) 🖥️ Práctica de código y manejo de Define en jerarquías:
  - El objetivo es practicar la escritura del código, manejar los Define en distintas jerarquías y entender su uso a nivel de instancias.

- [31:47](https://youtu.be/6e_r3Ia1vcs?t=1907s) 📊 Obtención de parámetros y reportes:
  - Se busca obtener reportes de celdas, instancias, timing y complejidad del diseño.
  - Los reportes incluyen información sobre la utilización de la arquitectura sintetizada.
















- [34:26](https://youtu.be/6e_r3Ia1vcs?t=2066s) 📅 Sobre fechas de entrega y asistencia:
  - Se hace hincapié en la importancia de justificar retrasos en la entrega de tareas o en la asistencia a clases.
  - Se solicita comunicación sobre ausencias o retrasos para mantener un registro claro.

- [37:03](https://youtu.be/6e_r3Ia1vcs?t=2223s) 🛠️ Interpretación de esquemáticos a nivel conceptual:
  - Se analiza la interpretación literal de los esquemáticos generados, que representan el diseño lógico conceptual.
  - Se distingue entre la interpretación conceptual y la implementación física del diseño.

- [40:00](https://youtu.be/6e_r3Ia1vcs?t=2400s) 📈 Análisis de complejidad y timing:
  - Se explica la generación de esquemáticos para analizar la complejidad y el timing del diseño.
  - Se detalla el proceso de obtención de información para diferentes frecuencias de funcionamiento.

- [43:02](https://youtu.be/6e_r3Ia1vcs?t=2582s) 📑 Informe de resultados y comparativas:
  - Se instruye sobre la elaboración de informes que comparen la complejidad y la capacidad de funcionamiento a distintas frecuencias.
  - Se espera un análisis detallado basado en los resultados obtenidos en el laboratorio.

- [44:33](https://youtu.be/6e_r3Ia1vcs?t=2673s) 📊 Resultados esperados y cierre del laboratorio:
  - Se establece un plazo estimado para la finalización del laboratorio, resaltando la importancia del análisis de los resultados.
  - Se alienta a los estudiantes a comprender la complejidad del sistema y a comparar diferentes técnicas de implementación.



- [54:44](https://www.youtube.com/watch?v=6e_r3Ia1vcs&t=3284s) 🧠 Análisis de resultados de laboratorio y comparación de estructuras de diseño.

  - El laboratorio se centra en entender y comparar los resultados de la síntesis de diferentes estructuras de diseño.
  - Se analizan ventajas y desventajas de utilizar distintas estructuras, como DCP y filtros transpuestos.
  - La optimización del diseño se evalúa en función de la complejidad, velocidad y recursos utilizados.

- [01:00:01](https://www.youtube.com/watch?v=6e_r3Ia1vcs&t=3601s) 🔄 Impacto del uso del riple carry en la velocidad de operación.

  - El uso del riple carry en la implementación de arquitecturas en FPGA incrementa significativamente la velocidad de operación.
  - Se comparan frecuencias de trabajo obtenidas con diferentes arquitecturas, destacando la superioridad del riple carry en términos de velocidad.
  - La implementación con riple carry reduce la complejidad y aumenta la velocidad, haciendo que sea la opción preferida en muchas aplicaciones.

- [01:12:03](https://www.youtube.com/watch?v=6e_r3Ia1vcs&t=4323s) 💡 Consideraciones sobre el diseño de filtros y multiplicadores en FPGA.

  - Se discute cómo la elección de arquitecturas de filtros y multiplicadores afecta el rendimiento y los recursos utilizados en FPGA.
  - Se analizan las estrategias de diseño para optimizar la velocidad y el área ocupada en la implementación.
  - Se enfatiza la importancia de entender la teoría detrás de las decisiones de diseño y de ser críticos al interpretar los resultados obtenidos.



