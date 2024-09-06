## Dispositivos de entrada/salida
Basicamente se manejan con registros, en los cuales escribimos los que queremos enviar, leemos lo que queremos recibir y con estos registros analizamos los estamos de estos.
### GPIO(Entradas y salidas digitales)
- Conjunto de termianles que pueden ser entradas y salidas digitales.
- Tienen 2 registros:1 de control y 1 de dato.
### Funciones de fabricantes
- Las funciones provistas por el fabricante solo tiene como objetivo facilitar el uso del procesador
- Los prototipos de las funciones cambian por cada fabricante
	- Como soluciono esto?*Hago mi propia capa de abstraccion*
### Construyendo nuestra propia abstraccion
Sera una biblioteca que concentrar todas las funciones para la gestion de los dispositivos de entrada/salida.
Se puede desarrollar:
- A medida del proyecto(*BSP*)
- Reutilizable entre otro proyecto(*HAL*)
![[Pasted image 20230414120759.png]]
