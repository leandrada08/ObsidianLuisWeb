## Lineamientos de Sintesis
### Logica de encolado(Glue Logic)
- Mientras que el diseñador esta dividiendo el diseño de forma jerarquica en una seria de modulos, debe evitar la logica encolado que conecta dos modulos
- Esto puede suceder despues de corregir un desajuste de interfac o agregar alguna funcionalidad que falta al depurar el diseño
- Cualquier logica de este tipo deberia formar parte de la logica combinacion de uno de los modulos constituyentes
- *La logica de encolado peude causar problemas en sintesis ya que los modulos individuales pueden satisfacer restricciones de tiempo, mientras que el modulo de nivel superior puede que no*
![[Pasted image 20231008115147.png]]

### Modulos con objetivos comunes de diseño
- El diseñador debe evitar colocar en el mismo módulo una lógica crítica y no crítica en tiempo.
- El módulo con lógica de tiempo crítico debe ser sintetizado para mejorar la sincronización, mientras que el módulo con lógica no crítica en el tiempo se optimiza para el mejor área.
- Ponerlos en el mismo módulo producirá un diseño sub-óptimo.
- La lógica debe ser dividida y colocada en dos módulos separados.
![[Pasted image 20231008115421.png]]



## Sistema Realimentado
- Cualquier circuito realimentado que sea solamente combinacional no será sintetizado ni simulado correctamente por la herramienta.
	- Se los suele llamar loops combinacionales y deben ser evitados.
- Un sistema realimentado, como por ejemplo un acumulador, debe incluir registros en algún punto del camino realimentado.
	- Importante: Utilizar una señal de inicialización (reset) en estos registros. Esto es porque cualquier valor previo almacenado en los registros corromperá todos los cálculos futuros. Desde el punto de vista de simulación, se asume una x en los registros hasta su inicialización, la cual puede propagarse por el circuito realimentado si no se aplica una señal de reset adecuadamente.
- El reset puede ser síncrono o asíncrono y, en ambos casos, activo por alto o bajo.
- Se realiza una realimentacion con un registro para que la salida dependa de salidas anteriores, para esto debemos defenir una señal intermedia, no podemos hacerlo directamente con la señal de salida.

![[Pasted image 20231012124519.png|500]]

## Latch
- Un diseñador debe evitar cualquier sintaxis de RTL que infiera latches.
- Un latch es un dispositivo de almacenamiento que almacena un valor sin el uso de un reloj.
- Su implementación suele ser específica de la tecnología y suelen generar problemas de routeo y timing, o derivar en loops combinacionales, por lo que deben evitarse en diseños síncronos.
- Para evitarlos, el diseñador debe cumplir con ciertas pautas de codificación al definir lógica combinacional en bloques procedurales.
	- En sentencias if 
		- Siempre *incluir* la instrucción *else* 
		- Para cada condición se deben *asignar valores a todas las variables*, o bien se deben asignar valores predeterminados a todas las variables fuera del bloque condicional.
	- En sentencias case
		- Se deben *especificar todas las condiciones posibles* de la variable de selección
		- *Para cada condición se deben asignar valores a todas las variables*. De no ser así, se debe incluir la condición default y asignar valores predeterminados a todas las variables fuera del bloque condicional.
*Cual es la diferencia entre un latch y un flip flop?*
- Diferencia entre el latch y el flip flop es que el primero cambio cuando el reloj es 1 y el segundo solo con los flancos positivos.
### Ejemplos
![[Pasted image 20231012185907.png|400]]

