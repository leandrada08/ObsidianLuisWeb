## Sistema Operativo FreeRTOS
- Es un sistema operativo comercial con licencia para ser utilizado sin costo en aplicaciones comerciales.
- Es un sistema operativo dinamico: las tareas son creadas en tiempo de ejecucion, antes o despues de iniciar el planificador.
- El manejo de memoria puede ser estatico o dinamico, evitando los problemas de la memoria dinamica.
- Implementa un planificador mixto que permite realizar un round-robin entre todas las tareas de igual prioridad.
![[Pasted image 20230614150959.png]]
1. Ready (Listas): La tarea está creada y lista para ejecutarse, pero aún no se le ha asignado el tiempo de CPU para su ejecución. Se encuentra en la lista de tareas listas para ser seleccionada por el planificador y ejecutada.
2. Running (Ejecutando): La tarea se encuentra actualmente en ejecución, es decir, está utilizando el tiempo de CPU asignado y realizando su trabajo.
3. Blocked (Bloqueadas): La tarea está bloqueada y no puede ejecutarse debido a alguna condición o evento. Puede ser bloqueada por una espera de tiempo, una espera de semáforo, una espera de evento, una espera de cola, entre otras situaciones. La tarea bloqueada no se incluirá en la selección del planificador hasta que se cumpla la condición de desbloqueo.
4. Suspended (Suspendida): La tarea ha sido suspendida explícitamente y no participa en la planificación. Esto significa que no se seleccionará para ejecutarse hasta que sea reanudada.

Además de estos estados principales, FreeRTOS también proporciona algunos estados adicionales específicos para ciertas características o condiciones:
- Deleted (Eliminada): La tarea ha sido eliminada y sus recursos se han liberado. Después de ser eliminada, ya no existe en el sistema y no se considera para la planificación.
- Dormant (Inactiva): La tarea se encuentra en un estado inactivo y no está en ninguna de las otras categorías de estados. Puede ser utilizada para tareas que no se ejecutan de forma periódica o que están esperando activarse por alguna condición específica.

## Politica del planificador FIFO
![[Pasted image 20230614151105.png]]

## Tarea en FreeRTOS
- Se definen como funciones que reciben un puntero como par´ametro.
- Normalmente estas funciones tienen la misma estructura de una funci´on main(): estan formadas por un bloque secuencial seguido de un lazo infinito.
	- En este lazo infinito debe haber una funcion bloqueante
- La ejecucion del programa no debe alcanzar nunca la llave de cierre de la funcion: si una tarea quiere terminar debe llamar a una funcion del sistema operativo.
	- Debo destruirla antes de llegar al final

### Gestion de las tareas
- xTaskCreate\[Static\](): Crea una nueva tarea y le asigna los recursos necesarios.
- vTaskDelete(): Elimina una tarea del sistema operativo.
- vTaskSuspend(): Suspende la ejecucion de una tarea colocandola en el estado blocked.
- xTaskResume\[FromISR\](): Reanuda la ejecucion de una tarea suspendida.
- vTaskPrioritySet(): Cambia la prioridad de una tarea.


### Tarea como parametros
- Las funciones que implementan tareas en FreeRTOS reciben un puntero como par´ametro de entrada.
- Este puntero se asigna cuando se crea la tarea llamando a las primitivas del sistema operativo.
- Para poder usar esta funcionalidad el codigo de la tarea debe ser reentrante, es decir que debe soportar volver a empezar antes de terminar la instancia anterior.
- Esto implica no utilizar variables globales (o estaticas) en este tipo de funciones.

``` C
/** @brief Estructura con los parametros de la tarea blinking */
typedef struct {
	uint 8_t led ; /** < Led que debe parpadear la tarea */
	uint 16_t delay ; /** < Demora entre cada encendido */
} blinking_t ;
/** @brief Funcion que implementa la tarea blinking */
void Blinking ( void * parametros ) {
	blinking_t * valores = parametros ;
	while (1) {
		Led_Toggle ( valores ->led );
		vTaskDelay ( valores -> delay / portTICK_PERIOD_MS );
	}
}
```

``` C
int main ( void ) {
/* Variable con los parametros de las tareas */
	static const blinking_t valores [] = {
		{ . led = RED_LED , . delay = 500 },
		{ . led = RGB_B_LED , . delay = 300 }
	};

	/* Creacion de las tareas */
	xTaskCreate ( Blinking , " Rojo ", configMINIMAL_STACK_SIZE ,
		( void *) & valores [0], tskIDLE_PRIORITY + 1, NULL );
	xTaskCreate ( Blinking , " Azul ", configMINIMAL_STACK_SIZE ,
		( void *) & valores [1], tskIDLE_PRIORITY + 2, NULL );

}
```


## Temporizacion en FreeRTOS
- Para el manejo de espera de tiempos FreeRTOS ofrece dos recursos: Esperas y Temporizadores.
- Las esperas son servicios del sistema operativo que ponen bloquean tarea durante un cierto tiempo.
- Los temporizadores son cuentas regresivas de una vez o repetitivas que llaman a funciones de callback al expirar.
- Los temporizadores son cuentas regresivas de una vez o repetitivas.
- Al expirar la cuenta programada se ejecuta una funcion de callback.
- La implementacion de los temporizadores utiliza una tarea interna de FreeRTOS llamada TimerTask.
- La tarea del usuario se comunica con la tarea del sistema operativo utilizando una cola de mensajes que no puede ser accedida en forma directa.
- Para enviar mensajes a la TimerTask se deben utilizar las funciones de la API de temporizadores.
- La función de callback se ejecuta en el contexto de la tarea TimerTask.
- Agregar el archivo `timers.c` al proyecto.

- Configurar las siguientes constantes en `FreeRTOSConfig.h`:

- `configUSE_TIMERS`: Se debe poner en 1 para habilitar la funcionalidad de temporizadores, lo que implica la creación automática de la tarea `TimerTask`.

- Configurar las siguientes constantes en `FreeRTOSConfig.h`:

- `configTIMER_TASK_PRIORITY`: Prioridad de la tarea `TimerTask`. Tiene impacto en una posible latencia en la ejecución de la función de callback.
- `configTIMER_QUEUE_LENGTH`: Cantidad de entradas en la cola de pedidos de servicio.
- `configTIMER_TASK_STACK_DEPTH`: Cantidad de palabras reservadas para el stack de la tarea `TimerTask`.
- `xTimerCreate[Static]()`: Crea un nuevo temporizador y la función de callback, el valor de la cuenta y si es repetitiva.
- `xTimerStart[FromISR]()`: Inicia la cuenta regresiva de un temporizador.
- `xTimerReset[FromISR]()`: Reinicia una cuenta regresiva activa.
- `xTimerStop[FromISR]()`: Detiene una cuenta regresiva activa.
- `xTimerChangePeriod[FromISR]()`: Cambia el valor de la cuenta.
- `xTimerIsTimerActive()`: Retorna si una cuenta regresiva está activa.


### Manejo de esperas
- vTaskDelay(): Suspende la ejecucion de una tarea por un determinado tiempo. Es opcional y solo puede ser llamada por la tarea que desea esperar.
- vTaskDelayUntil(): Suspende la ejecucion hasta que el temporizador del sistema alcance un valor determinado.
- xTaskAbortDelay(): Cancela la espera de una tarea y la coloca inmediatamente en estado ready.



