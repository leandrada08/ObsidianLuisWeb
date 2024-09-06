*RTN:* Notacion de transferencia de registros
La "Register Transfer Notation" (RTN) es una notación utilizada para describir el comportamiento de los circuitos digitales y los microprocesadores. En términos generales, la RTN describe cómo los datos se transfieren entre los registros de un microprocesador y los circuitos que los procesan.
En la RTN, se utiliza un conjunto de símbolos para representar las operaciones que se realizan en el circuito digital. Por ejemplo, un símbolo de flecha hacia la derecha indica una transferencia de datos de un registro a otro, mientras que un símbolo de suma representa una operación de suma.
Al utilizar la RTN para describir el comportamiento de un microprocesador, es posible crear un modelo abstracto que muestra cómo los datos se mueven a través del sistema. Esto es útil para diseñar y depurar circuitos digitales, ya que permite identificar posibles problemas y optimizar el rendimiento del sistema.
## Descripcion abstracta(RTN Abstracta)
Dice que se hace pero no como se implementa
- Hay una unica descripcion abstracta
- Estas descripciones son parte del ISA
![[Pasted image 20230323174835.png]]
### Notacion
*La imagen muestra la descripcion abstracta de todo el ISA*(todo el comportamiento de la maquina)
- *Los puntos y coma(;)* marcan ciclos
- *Los 2 puntos(:)* marcan paralelo
- Si esta entre parentesis con punto y coma al final significa que se repite permanentemente ese ciclo
- *La flecha(<-)* indica asignacion
- *Los dos puntos con igual(:=)* significa que la funcion se le asigna una serie de opciones que se ejecutan todas simultaneamente, o la opcion que este a continuacion, si esta precede a una igualdad, es una condicion para que se realice la asignacion
- $R[]$ significa registro
- $M[]$ significa memoria
- *16@IR(15)#* Esto significa 16 veces el bit 15 de IR concatenado con...
### Analisis de la imagen
En la image:
- La parte de $IR<=M[PC]: PC<=PC+4$ es el fetch en el ciclo de intruccion
- El decode de hace automaticamente(no se ve en las transferencias)
- $Instruction_execution$ es la parte de ejecutar
#### Observaciones
- No leer de izquierda a derecha, todo se asigna en paralelo, si doy vuelta las cosas deberia ser lo mismo
- Registro base y desplazamiento
## Descripcion concreta(RTN Concreta)
Dice como se implementa
- En la descripcion concreta rompemos la abstracta en varias secuencias, que esta dice como se implementa en el camino de datos.
- Puede tener distintas implementaciones
	- Osea, multiples descripciones concretas
- Esta descripcion no es parte del ISA y siempre cambia
- En esta descripcion vemos como se implementa cada instruccion en la arquitectura que tenemos
### Notacion
Es la misma que en RTN abstracto, los simbolos significan lo mismo
## RTN Concreto y abstracto de ADD
### Abstracto
``` 
Abstract RTN:(
	IR<-M[PC]: PC<-PC+4;
	add(:=op=12) -> R[ra]<-R[rb]+R[rc]:
)
```
### Concreto
Para la concreta necesito la arquitectura
![[Pasted image 20230323192503.png|500]]
```
T0:MAR<=PC: C<=PC+4;
T1:MDR<=M[MAR]: PC<=C;
T2:IR<=MDR;
T3:A<=R[rb];
T4:C<=A+R[rc];
T5:R[ra]<=C;
```
Implementacion del RTN abstracto en Concreto:
- Linea 2 de abstracto se implementa en las lineas 1,2 y 3 en el concreto
	- *Estas lineas son iguales en todas las instrucciones*
	- A esto lo llamamos IF
		- Se refiere a la busqueda de la instrucciones(instruction fetch)
- La linea 4 de abstracto se implmenta en las siguientes lineas
	- A esto lo llamos IEx
	- Es la *ejecucion de la instrucciones*