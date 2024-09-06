## Interrupciones
- Mecanismo implementado que permite suspender la tarea en curso y ejecutar una rutina específica para atender una situación especial.
- Son utilizadas para atender dispositivos sin la sobrecarga de tener que revisar periódicamente el estado del mismo.
- El dispositivo procesa una tarea y cuando termina genera un pedido de interrupción al procesador utilizando una línea de hardware específica.
- El procesador identifica el pedido y decide aceptarlo en función de las prioridades de la tarea actual y del pedido de interrupción.
- Si el procesador acepta la interrupción, entonces ubica la rutina de servicio correspondiente, guarda el estado de la tarea actual y comienza a ejecutar la rutina de servicio con una prioridad igual a la de la interrupción.
### Interrupciones en FreeRTOS
- El vector de interrupciones es gestionado por el proyecto C, como en BareMetal.
- Para el Cortex-M4, se deben dirigir tres excepciones a rutinas del sistema operativo:
  - La interrupción de SysTick que se utiliza para gestionar las esperas y el round robin.
  - La excepción SVC Handler que se utiliza para pedir servicios al sistema operativo.
  - La excepción PendSV Handler que se utiliza para pedir servicios del sistema operativo en forma diferida.
### Interrupciones cortas
- Por muy alta que sea la prioridad asignada a una tarea, la atención de las interrupciones suspende la ejecución de las tareas.
- Por lo tanto, las rutinas de servicio de las interrupciones modifican los tiempos de respuesta del sistema.
- Si no se permite el anidamiento de las interrupciones, entonces también hay una interferencia en los tiempos de respuesta con otras interrupciones.
- Si se permite el anidamiento de interrupciones, entonces aumenta la posibilidad de anidamiento y, por lo tanto, la complejidad para predecir el comportamiento del sistema.

### Excepciones
- También pueden llamarse interrupciones por software o System Traps.
- Tienen el mismo comportamiento que las interrupciones, pero son causadas por eventos internos, normalmente condiciones de error.
- En general, son sincrónicas con el programa, mientras que las interrupciones son asincrónicas.
- También se utilizan para pedir servicios al sistema operativo en forma similar a la ejecución de una subrutina.
- Normalmente, se asigna un número y un nombre a cada interrupción o excepción del sistema.

### Vector de interrupciones
- Es una tabla en memoria que contiene las direcciones de las rutinas de servicio de las interrupciones y excepciones.
- En el caso del Cortex-M4, las primeras 16 entradas de la tabla corresponden a excepciones y son las mismas para cualquier fabricante.
- El resto de las entradas son para interrupciones y depende del fabricante cuales se utilizan y a qué dispositivos corresponden.
- Existe un registro especial en el procesador que apunta a la dirección de inicio del vector de interrupciones.
- Este registro normalmente está cargado con el valor cero, pero puede cambiarse el valor del mismo y, por lo tanto, cambiar totalmente el vector de interrupciones durante la ejecución.

### Procesamiento diferido
- Es una técnica muy utilizada para mantener las rutinas de servicio cortas:
- La rutina registra la causa de la interrupción y la borra.
- La rutina desbloquea a una tarea auxiliar que será la responsable de procesar la información.
- Esta tarea auxiliar se vuelve a bloquear esperando la señal de una nueva interrupción.
- Si la tarea que procesa la información es la de mayor prioridad, el procesamiento se produce inmediatamente.

![[Pasted image 20230628092447.png]]


### Implementacion con semaforo
- La tarea que procesa la información pide un semáforo binario que se inicia vacío y se bloquea.
- La rutina de servicio recibe los datos y otorga el semáforo, lo que desbloquea a la tarea de procesamiento.
- La tarea procesa la información recibida por la rutina de servicio y repite el lazo infinito, por lo que pide nuevamente el semáforo y vuelve a bloquearse.
- Si en el transcurso del procesamiento hubiese habido una nueva interrupción, entonces se repite el procesamiento de forma inmediata.
- Si ocurriese un tercer evento antes de terminar el primero, entonces se pierde.
- Utilizar semáforos contadores resuelve el problema de perder eventos.


### Implementacion con cola
- Las colas son una forma muy cómoda de comunicación entre las rutinas de servicio y las tareas de procesamiento.
- Al definir una cola, se especifica la cantidad de elementos a ingresar y su tamaño, y se realiza la asignación de memoria correspondiente.
- Cuando se ingresan o se retiran elementos de la cola, estos se copian desde las variables a la memoria asignada a la cola y viceversa.
- Por esta razón, no son un método eficiente si los datos llegan con mucha frecuencia o son muy voluminosos.
