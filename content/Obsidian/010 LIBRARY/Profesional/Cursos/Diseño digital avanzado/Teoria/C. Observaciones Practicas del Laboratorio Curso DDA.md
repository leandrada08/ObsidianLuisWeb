
## VIO e ILA
### VIO
**Virtual Imput-Output**
Permite controlar y manejar las entradas y salidas del diseño, por ende:
- La VIO es una instancia que te permite monitorear y controlar señales dentro de tu diseño de Verilog mientras está en funcionamiento en la FPGA.
- Puedes configurar la VIO para que actúe como un generador de señales o como un observador, lo que te permite simular entradas o capturar salidas mientras tu diseño está en ejecución en la FPGA.
- Es útil para verificar el comportamiento de las señales en tiempo real y depurar posibles problemas de funcionamiento.
- Las salidas del proyectos seran entradas del VIO
- Las entradas del proyecto seran salidas del VIO
**Observacion:** Tenes realizar un multiplexor para las entradas, ya que si no lo haces te saldra error
``` verilog
   // Reverse Reset
   assign sw_w      = (selMux) ? sw_from_VIO : i_sw;
   assign reset     = (selMux) ? ~reset_from_VIO : ~i_reset;
```


### ILA
**Integrated logic analizer**
Permite analizar estados logicos obtenidos en el circuito
- Solo tiene entradas
- Hay 2 maneras de visualizarlas, cuando configuramos el bloque debemos elegir
	- La primera es la que esta por defecto de vivado
	- la segunda es de xilinx
- La ILA es una herramienta de depuración más avanzada que permite capturar y analizar señales dentro de tu diseño en tiempo real.
- Permite establecer puntos de control y capturar datos de señales específicas en momentos específicos durante la ejecución del diseño en la FPGA.
- Puedes visualizar los datos capturados en una interfaz gráfica que te permite analizar el comportamiento de las señales y detectar problemas de funcionamiento o errores de diseño.



## Analizando los caminos críticos
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


## Ambientes de trabajo
- Se puede crear ambientes de trabajo para hacer analisis de distintas sintesis o implementaciones sin perder la anterior
	1. Ir a Desing runs → Apretar el boton *+*
	2. Definir si se requiere implementacion, sintesis o ambas
	3. Elegir el constrain y el tipo de estrategia de vivado a usar
	- Luego se genera otro entorno de trabajo y se debe seleccionar cual activar aprentando click derecho y activando
![[Pasted image 20240502104929.png]]


- Implementacion generica vs implementacion especifica → Analisis para proyecto
	- En la implementacin generica se usara muchisimo mas componentes que en las especificas
	- Esto se debe a que la herramienta no podra sintentizar el diseño en base a valores usados, por lo cual debera usar todos los componentes necesarios
	- Por ejemplo si tenemos un filtro con la mitad de los valors 0 y la mitad 1(que es muy probable por entropia), el resultado sera un filtro de la mitad de recursos que uno que tiene todos 1, que seria aproximadamente el que se deberia implementar en un filtro generico
