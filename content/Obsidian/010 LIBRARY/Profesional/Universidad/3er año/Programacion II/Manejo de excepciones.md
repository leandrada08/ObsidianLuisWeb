Manejo de Excepciones:

- Introducción al Manejo de Excepciones:
  - Las excepciones son eventos que ocurren durante la ejecución de un programa y que interrumpen el flujo normal de ejecución.
  - El manejo de excepciones es el proceso de capturar y controlar estas situaciones excepcionales para evitar que el programa se detenga abruptamente.

- Bloques Try-Catch:
  - Los bloques try-catch son utilizados para capturar y manejar excepciones en Java.
  - El bloque try contiene el código que puede generar una excepción.
  - El bloque catch se utiliza para capturar y manejar la excepción generada en el bloque try.
  - Pueden existir múltiples bloques catch para manejar diferentes tipos de excepciones.

- Tipos de Excepciones:
  - Java proporciona una variedad de clases de excepciones predefinidas que cubren diferentes situaciones excepcionales.
  - Existen excepciones de tiempo de ejecución (RuntimeException) y excepciones comprobadas (Checked Exceptions).
  - Las excepciones de tiempo de ejecución son aquellas que pueden ocurrir durante la ejecución normal del programa y no requieren una declaración explícita en el código.
  - Las excepciones comprobadas son aquellas que deben ser declaradas en el código utilizando la cláusula throws o manejadas en un bloque catch.

- Cláusula Finally:
  - La cláusula finally se utiliza para definir un bloque de código que se ejecutará siempre, independientemente de si se produce una excepción o no.
  - Es útil para realizar tareas de limpieza o liberación de recursos, garantizando que se realicen incluso en caso de excepción.

- Lanzamiento de Excepciones:
  - Además de capturar excepciones, también es posible lanzar manualmente excepciones en Java.
  - Esto se logra utilizando la palabra clave throw, seguida de una instancia de una clase de excepción.
  - Lanzar una excepción permite indicar que se ha producido una situación excepcional y proporcionar información sobre el problema.

- Excepciones Personalizadas:
  - Además de las excepciones predefinidas en Java, es posible crear excepciones personalizadas mediante la creación de clases de excepción personalizadas.
  - Esto permite lanzar y manejar excepciones específicas para situaciones particulares en el programa.
  - Las excepciones personalizadas deben heredar de la clase Exception o de sus subclases.

El manejo de excepciones es una parte fundamental de la programación en Java. Permite detectar y controlar situaciones excepcionales, evitando que el programa se detenga de manera abrupta y permitiendo una mejor administración de errores. El uso de bloques try-catch permite capturar y manejar las excepciones, mientras que la cláusula finally garantiza la ejecución de un bloque de código específico. Además, es posible lanzar excepciones manualmente para indicar situaciones excepcionales y personalizar las excepciones para adaptarse a las necesidades del programa.