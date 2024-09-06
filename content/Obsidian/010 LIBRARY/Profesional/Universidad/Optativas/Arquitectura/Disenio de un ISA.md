# Disenio de un ISA
## Decisiones de disenio para un ISA
- Tipo de ISA
- Instrucciones y modos de direccionamiento a incluir
- Formato de instruccion fijo o variable
- Manejo de constantes
- Tipos de datos a soportar
- Evaluacion de condiciones e instrucciones de salto
- 32 vs 64 bits

## Caracteristicas requeridas de un ISA
- Debe ser completo
    - Se probo que con una sola isntruccion alcanza
- Debe ser eficiente
	- Instrucciones mas usadas deben ser rapidas
- Debe ser regular
	- Operaciones y modos de direccionamiento esperados
	- Formatos uniformes, fijos de ser posible.
	- *Simplicidad favorece la regularidad*
- Debe hacer un buen uso de la memoria
	- Que pueda manejar bien cualquier tipo de dato(grande y chico)
		- Haremos que pueda manejar datos de 1 bit


## Comparacion de distintos ISAs
### Tipos
#### ISA con operandos en memoria
$ADD$ $A,B,C$    $M(A)<-M(B)+M(C)$
- Muchos accesos a memoria
	- En la ecuacion de arriba son *4 accesos a memoria(por el acceso a memoria a buscar la instruccion)*
- Generan un cuello de botella en el acceso a memoria
- Instrucciones muy largas
#### ISA con operando en registros y memoria
$ADD$ $r1,C$    $R(r1)<-R(r1)+M(C)$
- Facil de codificar, menor longitud de programa.
- Uno de los operandos fuente se sobreescribe
- Instrucciones de longitud y duracion diferente, segun el operando
#### ISA con operando en registros
$ADD$ $r1,r2,r3$    $R(r1)<-R(r2)+R(r3)$
-  Condificacion simple. Facilida disenio de Hardware
- Necesita mas instrucciones para un mismo programa
### Comparacion
- *Los ISAs basados en registros se impone*
	- Principalmente, porque son mas rapdios que memoria
	- Ademas, porque son mas faciles de optimizar por el compilador.
**Principio de disenio: cuanto mas pequenio, mas rapido**
- **Arquitectura dominante:tipo Load-Store**
	- Unicamente las instrucciones de tipo *Load y de tipo Store* pueden acceder a memoria.
	- Ideal para implemetnar en un Pipeline.
#### Importante
En el fondo es una cuestion tecnologica. Ya que hoy en dia tenemos registros mas rapidos que memoria, en un futuro puede cambiar esto.

## Que elijo para mi ISA
### Que instrucciones incluir en el ISA
1. Si es lenta y obliga a que las demas sean lentas --> *No incluirla*
2. Si es lenta pero es muy necesaria para que el set sea completo --> *Hago una pseudoinstruccion que la remplace* y que el ensamblador la expanda a esta.
#### 3. Las mas usadas
Lo mejor es medir en varios programas, cuales son las que realmente mas se usan. siempre considerando la frecuencia dinamica.
![[Pasted image 20230403084849.png|500]]

### Que modo de direccionamiento elegir?
Midieron y obtuvieron:
![[Pasted image 20230403085257.png|500]]
- 88% de las veces se usan los 3 primeros modos


### Que tipo de formato elegir?
Los formatos de instrucciones peuden ser de longitud fija o variable.
- Ventajas formato de longitud fija:
	- En general, mejor performance
	- Mayor simplicidad
	- Mayor regularidad
- Desventaja foramto de longitud fija:
	- Menor densidad de codigo: se necesitan mas instrucciones para la misma tarea
	- Menor posibilidad de ampliacion: en algun momento, se acaban los bits.
- Actualmente, estan de moda formatos con dos longitudes fijas.
	- Instrucciones de 32 y 16 bits unicamente.
	- Obtiene las ventajas de fijas y variables

### Que tamanio de constantes
- Para desplazamiento el 99% de los casos es menor a 16bits
- Para constantes el 80% entra en 16 bits
**Usamos constantes de 16 bits**
Y si la constante es mas grande?
- La remplazo con 2 instrucciones
La constante 0 es *MUY* usada
- La dejamos siempre en un registro, para ganar eficiencia, aunque pierdamos un registro.


### Que tipos de datos soportar?
- Manipulacion de bits.
- Enteros y caracteres:
	- 8-bit, 16-bit, 32-bit, 64-bit
	- Los numeros simpre en complemento a 2
	- 75% de las veces se usan datos de 32 bits.
- Punto flotante:
	- Precision simple(float, 32-bit), doble(double, 64-bit) y quadruple(quadword, 128-bit).
	- 70% de las veces se usan precision doble.


### Como se evaluan las condiciones?
2 casos
- Mediante codigos de condiciones(CC, basicamente las banderas)
	- Instrucciones aritmeticas setean los CC, las instrucciones de salto los evaluan.
	- Suele requerir menos instrucciones
	- No todas las instrucciones cambian todos los CC.
	- *Dificulta la implementacion en pipeline*
		- Porque los CC se leen y se escriben en distintos momentos.
- Sin codigos de condicion
	- Se comparan registros, y sobre ellos se guardan los resultados.
#### Consideraciones sobre los saltos.
- La mayoria de los destinos de los saltos son muy cercanos a la propia instruccion.
- Por ello, es muy utilizado el modo de direccionamiento relativo a PC
	- Es un modo que utiliza PC como registro base
		- Con al menos 8 bits para desplazamiento.
			- Nos permite saltar 128 espacios hacia adelante o hacia atras.
- El programas de enteros, el salto condicional por igual/distinto es por lejos el mas usado.
	- Hacer que se ejecute mas rapido.

## Dimensiones del ISA
- Los ISAs mas comunes son de 32-bits
	- Este es el tamanio de los operandos enteros, de las instrucciones, de las direcciones a memoria y de los registros.
- Tambien hay ISAs mas pequenios(Thumb) de 16-bits y tambien combinaciones de 16-bits y 32-bits
- Tambien hay ISAs de 64 bits, mas "recientes".
	- Esto se debe a que aumentaron los tamanios de las memorias.
		- *Solamente hay un error que se puede cometer en disenio de computadoras que es dificil de reponerse: no tener suficientes bits para el manejo y direccionamiento de la memoria*


## Metricas para comprar ISAS
Es importante medir para saber bien nuestros objetivos de disenio: *No se puede mejorar lo que no se puede medir*
- Distintos tipos de procesadores para distintas areas tiene distintos requerimiento de PPP.
### Metricas a analizar
- Tamanio del programa en memoria
- Cantidad de instrucciones que se ejecutan
- Cantidad de accesos/transferencias a memoria.
- Cantidad de ciclos promedio por instruccion.
- *Tiempo de ejecuccion(t=CI.CPI.T)*


## Principios de disenio
- *La cimplicidad favoredce la regularidad*
- *Hacer mas rapido el caso mas comun*
- *Cuanto mas pequenio, mas rapido*
- *No perjudicar a la mayoria por casos de las minorias*
- *Un buen disenio requeride compromisos*