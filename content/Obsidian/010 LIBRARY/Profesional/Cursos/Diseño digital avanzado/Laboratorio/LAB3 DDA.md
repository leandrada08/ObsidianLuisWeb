**Enfoque del laboratorio:**
 - Utilización de herramientas y obtención de información de timing.
 - Lectura de reportes de timing y complejidad. 
 - Análisis detallado de un ejemplo prediseñado para comprender el proceso. 
### Arquitectura del laboratorio
 - La arquitectura consiste en:
	- Un solo reloj que se distribuye a todos los módulos.
	- Un bloque de control que genera las señales de Valid.
	- Dos generadores de PRBS9.
	- Dos filtros SRRC - OverSample: 8.
	- Memorias BRAM para guardar las salidas de los filtros.
	- El modelo se sintetizó a las frecuencias de reloj 50MHz, 100MHz y 200MHz con el objetivo de analizar el efecto que causa sobre los caminos críticos el aumento de la frecuencia de trabajo.

![[Pasted image 20240206210726.png]]
- El objetivo es analizar los reportes de timing y la respuesta frente a diferentes frecuencias. 
- Los estudiantes replicarán este diseño en sus propios proyectos. 
- El filtro polifásico (SRRC I) es una alternativa para eliminar productos por cero en la convolución. 
	- Divide el filtro en subconjuntos más pequeños para actuar sobre un mismo set de muestras. 
	- Permite una implementación eficiente de la convolución en diseños físicos. ️ 
![[Pasted image 20240206211107.png]] 
- Arquitecturas polifásicas en filtros digitales 
    - Se comparan dos enfoques de implementación de filtros polifásicos. 
	- Uno es realizando los 3 productos y seleccionando cual usare y el otro(en el abajo) es solo seleccionando los parametros para realizar 1 producto que usare
	- Al ser la entrada solo de 0,1,-1 *se puede aplicar el producto con un multiplexor*


### Simulacion
- Se debe configurar como establece el pdf
- Primer paso es ajustar las rutas
- Luego debemos configurar la forma de onda de la simulacion




### Sintesis
1. Comentar y descomentar codigo necesario(seguir pdf)
2. Instanciar VIO e ILA
3. Generar Bitstream

![[Pasted image 20240207174801.png]]
- Aqui podemos ver que fue incluido de manera exitosa en nuestro diseño los epi cores previamente agregados

Luego hacemos un analisis de la sintesis de la herramienta
![[Pasted image 20240207175435.png]]
- La herramienta primero analiza el diseño general
- Luego va a los puertos particulares
- En la etapa de síntesis vamos a poder observar las diferentes optimizaciones del diseño que la herramienta va generando a medida que procesa el código Verilog.
- Genera una primera versión de la complejidad mostrando que componentes utiliza.
- En la ventana Log vamos a encontrar el detalle de cada paso de la síntesis.
- Es importante poder observar que se hayan generado las jerarquías y utilizado los componentes que mejor reducción de complejidad brinde al diseño.
- Tambien podemos observar las LUT ocupadas, los bloques DSP, las ROMS,etc.
- Tambien identifica Shift register
- Tambien los bloques que incluyo(vio e ila)
- Tambien vemos las celdas
	- Estas celdas son elementos o componentes de cualquier tamaño basicamente
- Tambien se puede encontrar un archivo plano con toda esta informacion dentro de la carpeta del proyecto


Reporte de utilizacion
- Debemos ir al apartado de sintesis a la izquierda y luego a reporte de utilizacion
![[Pasted image 20240208202243.png]]
- Ahi nos saldra una tabla como la siguiente
![[Pasted image 20240208202303.png]]
Donde cada columna son los recursos utilzados de la FPGA
- En el mismo cuadro donde esta el nombre de cada recurso, aparece el numero de total de este recurso
- Luego cada fila es cada bloque dentro de nuestro diseño y se puede ver cuanto utiliza de cada recurso



## Implementacion
### Analizando los caminos críticos
- En la última etapa es importante identificar los problemas de timing que puedan aparecer en el diseño.
- También es de interés conocer hasta cuanto podemos aumentar la frecuencia de trabajo según un análisis de todos los caminos críticos.
- La herramienta nos brinda un detalle de cada path especificando todos los componentes que utilizó entre un punto de origen y destino.
- *Se pude utilizar como referencia el documento UG906 de Xilinx*.
	- Muy interesante
- El reporte de timing se obtiene ejecutando la siguiente opción de la barra de herramientas: Reports - Timing - Report Timing Summary.


- Las secciones de análisis son
	- *Source Clock Path:* Es el camino seguido por el reloj de la fuente desde su punto de origen (típicamente un puerto de entrada) hasta el pin del reloj del primer registro. Para una ruta de tiempo que comienza en un puerto de entrada, no hay un camino de fuente de reloj.
	- *Data Path:* Es la sección del camino de tiempo en la que se propagan los datos, entre el punto de inicio del camino y el punto final del mismo. Se aplican las siguientes definiciones: (1) El punto de inicio del camino(Start Point) es un pin de reloj de un registro o un puerto de entrada de datos; y (2) El punto final(End point) del trayecto es un pin de entrada de datos de un registro o un puerto de salida de datos.
	- *Destination Clock Path*: La ruta del reloj de destino es el camino seguido por el reloj de destino desde su punto de origen, típicamente un puerto de entrada, hasta el pin del reloj del registro de destino. Para una ruta de tiempo que termina en un puerto de salida, no hay una ruta de reloj de destino.
	- *OutPut Delay*: Este analisis es desde el ultimo registro hasta la salida.

![[Pasted image 20240207180404.png]]
![[Pasted image 20240207180406.png]]


![[Pasted image 20240208205143.png]]
- Encontramos los timing de setup, de hold y de pulse width
- La herramienta nos entrega un reporte como este
	- Nos muestra el peor slack negativo(en este caso positivo)
	- Tambien nos muestra el tiempo total de slack negativo y el tiempo que acumulan estos fallos.
		- En este caso no tenemos ya que ninguno falla
	- Si tocamos sobre el peor tiempo podemos ver los path que los generan
		- Si sobre un path apretamos boton dereche+ schematic podemos ver el path desde el inicio hasta el fin y todos los componentes por los cual pasa
		- Esto nos sirve para ver que bloques tenemos que mejorar o donde tenemos que colocar registros
	- El slack es el tiempo de source clock path+ data path - destination clock path
		- Este valor nos indica cuanto tiempo tenemos de sobre respecto al periodo
			- Entonces nos dice cuando podemos o tenemos que aumenta o disminuir el periodo
	- Los StartPoint estan puesto en el pin de clock del primer registro
	- Los EndPoint en el pin de dato del registro.
	- Tambien jugando con las configuraciones podemos ver dentro de la placa el puerto. **1 hora 50 minutos**
		- Aqui tambien podemos ver como calculo cada tiempo para ese path





- Otra forma de facilitar el analisis del timing es utilizando histogramas.
- Los histogramas de timing se pueden obtener una vez implementado el diseño.
- Para ejecutar el análisis el reporte de timing usando histogramas debemos ir a Reports - Timing - Create Slack Histogram.
- Este analisis nos sirve para ver como estan distribuidos los endpoint para saber cuantos tengo en cada slack de tiempo
	- Este es de gran utilidad para saber cuando deberias mejorar para mejorar en cierta cantidad la velocidad
- Hay que analizar porque muchas veces tenemos muchos caminos en un valor pero cuando aumentamos la frecuencia la herramienta es capaz de solucionar muchos
	- Esto tambien depende de la syntesis elegida
	- La herramienta tambien lo puede solucionar, o lo podemos hacer nosotros tambien de manera manual de tecnicas que veremos mas adelante

