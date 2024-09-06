## Familias logicas
- TTL
	- Mas exitoso
- [[CMOS]]
	- Mas lenta que TTL
	- Bajo consumo
	- Altos niveles de integracion
### Logica [[CMOS]]

### Fan-In
*El fan- in d euna familia logica es el numero de entradas que una compuerta puede tener en una familia logica particular*
- Una compuerta de n entradas tiene en su construccion n transistores en serie y n en paralelo
	- Comunmente el fan-in de NOR es de 4 y de NAND es 6
- Si queremos ams entradas hay que modificar el circuito

### Compuertas AND-OR-INVERT
- Se realizan 2 operacion logicas con un solo nivel de transistor
![[Pasted image 20230225213259.png]]
- Tambien existe *OR-AND-INVERT*
![[Pasted image 20230225213323.png]]

### Compuertas de transmision
Se une un transistor N y uno P para formar una llave controlada por logica.
![[Pasted image 20230225213953.png]]
Cuando en EN' hay un nivel logico opuesto a EN, se conectan A y B
#### Multiplexor 2 canales
![[Pasted image 20230225214115.png]]

### Entrada Schmitt-Trigger
Es un circuito que utiliza realimentacion interna para desplazar el umbral de conmutacion.
Se logra una histeresis para poder tener mayor inmundiad al ruido.![[Pasted image 20230225214635.png]]

