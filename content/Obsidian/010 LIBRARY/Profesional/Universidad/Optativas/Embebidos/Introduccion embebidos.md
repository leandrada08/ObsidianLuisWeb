## Sistemas embebidos
- Sistemas basados en computadoras diseniadas para una funcion especifica
- En este curso veremos pocas unidades de baja y mediana complejidad
- Estos sistemas son:
	- Reactivos:Permanece pasivo hasta un cambio de entorno
	- De tiempo real:Tiempos de respuestas acotado, basicamente tiene que responder en ventanas de tiempo definidas, no necesariamente rapidos
	- Sistemas criticos
### Especializacion
- Especializados a solucionar un problema puntual
## Tipos de sistemas embebido

### Microprocesador
Procesador integrado en una unica pastilla, esta pastilla contiene:
- Registros
- Unidad aritmetico-logica
- Sistema de control

### Microntrolador
Integra las siguientes componentes en una sola pastilla
- Microprocesadores
- Memoria RAM y ROM
- Interfaces I/O
- 
### SOC(System-on-chip)
Integra:
- Microcontrolador
- Dispositivos perefericos


## Interfaces de entrada y salida
*GPI:* Entradas y salidas digitales de propositos digitales
Se utilizan registros para alimentar la logica combinacional y para almacenar los resultados. Cada registro ocupa una direccion y tiene un proposito definido, esta informacion esta en el manual de usuario.

## Varias funciones para un terminal
El costo de un chip depende mucho del area del silicio y de la cantidad de terminales. Habitualmente los terminales pueden tener varias funciones, de esta manera podemos facilitar el ruteo

## Biblioteca del fabricante
- Encapsulan las operaciones sobre los dispositivos de entrada/salida
- Permiten desarrollar el software sin conocer el funcionamiento del hardware

## HAL
Es una capa de abstraccion de hardware, esto nos sirve para cambiar de microprocesadores sin necesidad de cambiar el software, lo cual es lo mas caro.
### El software marca la diferencia
Hoy en dia es habitual que varias productos tengan las mismas especificaciones. La diferencia en el exito comercial suele estar determinado en mayor parte por el software


## Software
Es muchisimo mas que el codigo, es las introducciones que se ejecutan, la estructura de datos que permite que los programas manipulen adecuadamente la informacion y la informacion descriptiva sobre el disenio. Es este el que define, en general, las prestaciones que diferencian un producto de otros con caracteristicas similares
![[Pasted image 20230317104450.png|400]]
### Detalles del software
- El principal costo del desarrollo de software es la ingenieria
- La mayoria del software se desarrolla a medida
- La calidad del resultado depende de un buen disenio
- No responde a la economia de escala
	- Es todo lo contrario, mientras mas grande es, es mas costoso