## Algebra booleana
Estructura algebraica que esquematiza las operaciones logicas
- Solo se les permite tener 2 valores posibles: 0 y 1
- La entrada determina la salida
- Solo hay 3 operaciones *OR,AND y NOT* que llamaremos operacion logicas
#### Tabla de verdad
- Describe la salida en funcion de los niveles logico de las entradas
- El numero de combinaciones de entrada sera $2^N$ para N entradas

### Compuertas
#### OR(SUMA)
- Salida en alto(1) si cualquiera de sus entradas esta en alto(1)
- Se expresa como $X=A|B=AorB=AvB$
![[Pasted image 20230225192302.png]]
#### AND(PRODUCTO)
- Salida en bajo(0) si cualquiera de sus entradas en bajo(0)
- Se expresa como $X=A.B=AB$ 
![[Pasted image 20230225192617.png]]
#### NOT(INVERSION)
- Su nivel logico a la salida es opuesto a su nivel logico en la entrada
- Se expresa como $X=A'$
![[Pasted image 20230225192732.png]]
#### NOR
- Se invierte el resultado de una OR
- $(A+B)'$
![[Pasted image 20230225193202.png]]
#### NAND
- Se invierte el resultado de una AND 
- $(A.B)'$
![[Pasted image 20230225193230.png]]

### Teoremas boleanos
![[Pasted image 20230225193604.png]]


## Circuitos logicos
- Todo circuito logico puede escribirse mediante el uso de las 3 operacion booleanas basicas
	- Es posible implementar cualquier expresion logica utilizando solo compuertas NAND o NOR
#### Regla
- La operacion AND precede a OR
1. Primero se realiza las inversiones individuales
2. Luego parentesis
3. Si uuna expresion tiene barra de inversion, primero se realiza la expresion y luego la barra
- Se puede resolver con el uso de tablas de verdad

#### Principio de dualidad
- Una igualdad sigue siendo valida si se intercambia todas los 1 por 0 y los AND por 


### Observaciones importantes
- Si se agrega una burbuja en una entrada o salida, es equivalente a colocar un inversor en este lugar
	- Una linea se dice que esta activo en alto cuando no tiene burbuja 
	- Una linea se dice que esta activo en bajo cuando tiene una burbuja


