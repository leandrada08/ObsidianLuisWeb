## Declaraciones secuenciales
Permiten describir el comportamiento de un circuito como una secuencia de eventos relacionados.
- Pueden ser usado para modelar, simular o sintetizar
	- Sistemas combinacionales
	- Sistemas secuenciales
- Son usados en 
	- Procesos
	- Funciones
	- Precedimientos
**El orden de la secuencia de las declaraciones secuenciales es muy importante.**
## Procesos
Un proceso en VHDL es una unidad de ejecución que describe el comportamiento de un circuito digital. *Es una declaracion concurrente, es la principal forma de hacer declaraciones secuenciales.* 
- Se ejecuta en un tiempo delta
- Desde el punto de vista de la programacion tradicional es un lazo infinito
- Multiples procesos se ejecutan en paralelo.
### Anatomia de un proceso
Tiene dos estados: *Ejecucion y espera.*
![[Pasted image 20230427090501.png|350]]
Una vez ejecutado debe esperar hasta que la siguiente condiciones se cumpla.
### Sintaxis de un proceso
*Sintaxis 1:*
Con lista de sensibilidad
- Se activa cuando se modifica algun valor de la lista
``` VHDL
Nombre_Proceso: PROCESS(Lista_de_sensibilidad)
	Declaraciones de variables;
BEGIN
	Descripcion del comportamiento;
END PROCESS Nombre_Proceso;
```
*Sintaxis 2:*
Sentencia "wait"
- Siempre se activa hasta encontrar un wait
- Cuidado que aveces no son soportados por algunas herramientas de sintesis
``` VHDL
PROCESS
	Declaracion de variables;
BEGIN
	Descripcion del comportamiento;
	wait on Lista_de_sensibilidad;
END PROCESS;
```
### Partes de un proceso
*Lista de sensibilidad:* Lista de seniales que habilitan el disparo del proceso y que permiten el monitero de eventos en las herramientas de simulacion
*Declaraciones:* Parte declarativa, incluye declaraciones de tipos, funciones, procedimientos y variables. Tiene alcance local.
*Declaraciones secuenciales:* Se ejecutan cada vez que el proceso se activa.

#### Seniales en procesos
Las asignaciones de seniales dentro de un proceso ocurren cuando el proceso finaliza o es suspendido(wait). Mientras el se ejecuta el proceso son consideradas constante.
Las seniales son interfaz entre procesos o entre el dominio concurrente y secuencial dentro de un proceso.

#### Variables en procesos.
Todas las variables en un proceso se actualizan inmediatamente en la declaracion de la asignacion de variable.


*Completar todo lo que esta a continuacion*
## Procesos sincronizados.
- Todas las seniales asignadas dentro de un procesos terminan en un flip-flop.
- Si una variable es leida en un proceso sincronizado antes de la asignacion de valor tambien termina en un flip-flop(Mala practica!)
- Toda logica originada por una asignacion de seniales puede resultar en un circuito combinacional ubicado antes de la entrada del flip-flop.

## Procesos combinacionales
- Todas las seniales de entrada y las seniales que se leen deber setar contenidos en la lsita de sensibilidad.
- Si una senial se omite en la lista de sensibilidad, la simulacion VHDL y el hardware sintetizado se comportaran de manera diferente.
- Todas las seniales de salida del proceso se las sebe asignar un valor cada vez que se ejecuta el proceso. Si esta condicion no se cumple, la seniales mantendra su valor(latch). Basicamente hay que asignar todos loas valores de las seniales de salida para todos los casos.

### Observaciones
- Si hay lista de sensibilidad no podemos poner wait on, en caso de querer hacer una sintesis(como en tb no queremos sintetizar, lo hacemos)
- Permite modelar el comportamiento de un sistema
- Contiene un conjunto de sentencia secuenciales que se ejecuentan secuencialmente
- Un proceso en si mismo es una sentencia concurrente

