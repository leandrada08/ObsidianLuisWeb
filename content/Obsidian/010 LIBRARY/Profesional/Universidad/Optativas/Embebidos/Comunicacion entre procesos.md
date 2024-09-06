## Comunicacion entre procesos
- La forma más simple de comunicación entre procesos es la utilización de variables compartidas.
- El uso de variables compartidas genera problemas de sección crítica y de espera activa.
- Los sistemas operativos ofrecen mecanismos que permiten la comunicación entre procesos.
- Estos mecanismos resuelven o evitan los problemas de sección crítica, por esta razón muchas veces se habla de comunicación y sincronización como el mismo problema.

### Evento
- El mensaje más simple que se puede enviar entre dos tareas es un valor lógico verdadero/falso que indica que ocurre una condición previamente pactada entre ambas tareas.
- En general, todos los sistemas operativos implementan un sistema de eventos que permite este tipo de comunicación.
- Muchas veces, los eventos se agrupan en conjuntos afines, de forma tal que una tarea puede esperar por más de un evento.
- Como el mecanismo de eventos es controlado por el sistema operativo, la espera de un evento es pasiva, ya que se implementa sacando a la tarea del estado de Ready hasta que se produzca el evento esperado.

#### Eventos en FreeRTOS
- `xEventGroupCreate[Static]()`: Crea un grupo de eventos.
- `xEventGroupDelete()`: Borra un grupo de eventos.
- `xEventGroupSetBits[FromISR]()`: Activa determinados bits de eventos en un grupo.
- `xEventGroupClearBits[FromISR]()`: Limpia determinados bits de eventos en un grupo.
- `xEventGroupGetBits[FromISR]()`: Devuelve el estado de los eventos de un grupo.
- `xEventGroupWaitBits()`: Espera que determinados eventos se activen. Puede esperar por uno cualquiera o por todos especificados en una máscara y limpiar los eventos recibidos automáticamente.
- `xEventGroupSyncBits()`: Fija uno o más eventos y espera por otros eventos del mismo grupo en forma atómica. Se utiliza para la sincronización de procesos.


### Semaforos
- Son un mecanismo de comunicación y sincronización universal.
- Son una variable numérica con un valor inicial que solo puede ser accedida por dos operaciones.
- `p()` o `wait()`: espera que la variable tenga un valor mayor que cero y la decrementa.
- `v()` o `signal()`: incrementa la variable.
- Ambas operaciones son atómicas.
#### Semaforo en FreeRTOS
- `xSemaphoreCreateCounting[Static]()`: Crea un nuevo semáforo numérico.
- `xSemaphoreTake[FromISR]()`: Solicita acceso al "testigo" del semáforo o del mutex.
- `xSemaphoreGive[FromISR]()`: Devuelve el "testigo" del semáforo o del mutex.
- `vSemaphoreDelete()`: Elimina un semáforo.


### Implementacion de una cola
Consideremos el caso de una cola con capacidad para almacenar n datos.
- Dos procesos interactúan a través de esta cola, uno produce datos y otro los consume.
- La comunicación se puede resolver utilizando tres semáforos:
  - `mutex` inicia en 1 y protege la sección crítica.
  - `lleno` inicia en n y espera un lugar en la cola.
  - `vacio` inicia en 0 y espera un dato en la cola.


### Colas o Buzones
- Muchos sistemas operativos implementan colas como un servicio nativo.
- Estas colas resuelven el problema de sección crítica y espera activa.
- En general, almacenan punteros, lo que permite el envío de cualquier tipo de información.
- FreeRTOS dispone de un servicio de colas.
#### Colas en FreeRTOS
- `xQueueCreate[Static]()`: Crea una cola.
- `xQueuePeek[FromISR]()`: Lee el primer elemento de la cola sin retirarlo.
- `xQueueReceive[FromISR]()`: Recupera el primer elemento de la cola.
- `xQueueSend[FromISR]()`: Agrega un elemento al final de la cola.
- `xQueueSendToFront[FromISR]()`: Agrega un elemento al inicio de la cola.
- `xQueueReset()`: Reinicia la cola como vacía.
