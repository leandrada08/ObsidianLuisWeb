# Repaso
## ![[Descripcion funcional de un microcontrolador#Registros]]


## Saltos, completar

## ![[Descripcion funcional de un microcontrolador#Memoria]]

## ![[Manejo de Memoria#Pila]]

## ![[Subrutina#Subrutina]]
# Interrupciones
## Proceso de una interrupcion
1. Se esta ejecutando una tarea
2. Pedido de interrupcion
3. Consulta de prioridades
4. Guarda el estado de la tarea actual
5. Sirve a la interrupcion
6. Estado de su tarea
7. Continua la tarea original
![[Pasted image 20230607144109.png]]
![[Pasted image 20230607144245.png]]

### Caracteristicas de las interrupciones
- Son causadas opr eventos externo
- Asincronas con la ejecucion del programa
- Reclaman un servicio, ISR
Son transparente al programa principal
- No tiene forma de saber cuando llega
- No puede prepararse para ello

### Preguntas importantes
*Que diferencias hay entre interrupciones y subrutina?*
1. Las interrupciones son ASINCRONICAS
2. Son por hardware
3. Reclaman servicio
*Como sabe en donde esta la rutina de interrupcion?*
Con una tabla, mediante el num d eINT accede a una tabla de direcciones llamada vector de interrupciones

### Excepciones
#### Traps
Un trap se activa cuando ocurre algo inusual o fuera de lo esperado durante la ejecución del programa en el microcontrolador. Esto puede incluir eventos como desbordamiento de temporizadores, divisiones por cero, acceso a direcciones de memoria no permitidas, intentos de ejecución de instrucciones no reconocidas, entre otros.
- Causados por eventos internos
- Condiciones excepcionales o de error
- Son sincronicas con la ejecucion del programa
- El programa debe ser remediado por un supervisor
- Si no se puede, se aborta el programa
#### Interrupciones

### Simultaneas
Son simultaneas las que ocurren en el intervalo de una instruccion, tambien son simultaneas las que quedaron sin atender de una ronda previa. Se resulve por prioridades, este sistema debe ser equitativo

### Anidamiento
Cuando tengo 1 interrupcion mientras estoy tratando a otra.
‣ Define el Diseñador.
	‣ Usar solo en caso necesario, es complejo.
	‣ En general se las puede enmascarar.
‣ Si Admite, entonces
	‣ El Hw permite solo con mayor prioridad.


### NVIC: gestor de excepciones
- Hasta 255 excepciones
	- 240 interrupciones
	- 16 excepciones
- Cada excepcion se indentifica con un numero
- Hay vector con la direccion de inicio de cada rutina de serivico
- Se busca en la entrada correspondiente al numero de excepcion


## Condicion de interrupcion - I
Deben cumplirse cuatro condiciones necesarios simultaneamente
- *Habilitado en el CPU:* I=0 in PRIMASK
- *Habilitado en el dispositivo:* el bit del Hw=1
- *Nivel Prioridad:* Nivel de IRQ "menor" que BASEPRI (Diferencia con la primera condicion?)
- *Pedido:* Una accion externa de HW setea la bandera de pedido.

## Procesamiento de la INT - ISR
### Procesamiento de la INT
1. Esperar el fin de la instruccion actual
2. Suspender ejecucion y push de 8 registros en stack(R0, R2, R12, LR, PC, PSR)
3. LR=0XFFFFFF9
4. Escribir en PSR el numeo de instruccion
5. PC <- Direccion inicial de la rutina de servicion
### Procesamiento de ISR
1. Pone a cero el flag que disparo la interrupcion
2. Salva registros no guardados automaticamente si los usa, en Stack
3. Servicio a la interrupcion
4. Restaura registro del punto (2)
5. Se retorna al prog principal con BX LR

### EJ: Cambio de contexto
![[Pasted image 20230607151504.png]]

## Excepciones del Nucleo(Traps)
Tres prioridades fijas, el resto configurables:
- Reset=-3
- NMI= -2
- Hard Fauld= -1
Faults- ademas de hard fault:
- MPU: Violacion de proteccion de M
- Bus Fault: Falla en el bus
- Usage Fault: Falla en programa
No son fauld:
- SVCALL: Pedidos del programa al SO
- SysTick Interrupt: Pedida por un timer interno del nucleo del ARM.

## Modos: Usuario / Supervisor
Nivel de Privilegio: Supervisor/Usuario.
- En modo supervisor:
	- Todas las intrucciones permitidas
	- Todas los dispositivos y areas de M
- En modo Usuario
	- No se permite acceder a los dispositivos
	- No se permite acceder a algunas areas
	- Para segurar que un usuario no provoque problemas

## Modos: Thread/Handler
*Modo Thread:* Cuando un programa esta corriendo
*Modo Handler:* Cuando una interrupcion se ejecuta.
![[Pasted image 20230607152803.png]]
