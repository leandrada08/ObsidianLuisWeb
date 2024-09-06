## Sincronizacion en FreeRTOS
- FreeRTOS provee varios mecanismos para sincronización de tareas el ma ́s simple es el semáforo binario.
- Una alternativa es el Mutex que incluye un mecanismo de herencia de prioridad para minimizar los efectos de la inversión de prioridades.
- Cuando una tarea de alta prioridad espera un mutex quien lo ocupa sube temporalmente la prioridad al nivel de la que está esperando.

### Funciones
- xSemaphoreCreateBinary\[Static\]\(\): Crea un nuevo sema ́foro binario.
- xSemaphoreCreateMutex\[Static\]\(\): Crea un nuevo mutex.
- xSemaphoreTake\[FromISR\]\(\): Solicita acceso al semaforo binario o al mutex.
- xSemaphoreGive\[FromISR\]\(\): Libera el acceso del semaforo binario o del mutex.
- vSemaphoreDelete(): Elimina un sema ́foro o un mutex.
