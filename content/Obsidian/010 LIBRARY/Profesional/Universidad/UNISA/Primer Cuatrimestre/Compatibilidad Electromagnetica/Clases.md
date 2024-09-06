

## Observaciones de clase
Es fundamental diferenciar entre la "compatibilidad" y la "suscetibilidad". La compatibilidad se refiere a la capacidad de un dispositivo para no generar interferencia que afecte negativamente a otros dispositivos. Por otro lado, la susceptibilidad se relaciona con la resistencia de un dispositivo a las interferencias generadas por otros.
- Antes, para evaluar la CEM, se solían producir prototipos de dispositivos y realizar pruebas de compatibilidad y susceptibilidad en el mundo real. Hoy en día, se utilizan sofisticados software de simulación para analizar y prevenir problemas de CEM de manera más eficiente.
- El dispositivo recargable puede generar armonicos en la fuente de alimentacion, ya que el cable puede funcionar como linea de transmision o antena
- La duracion de una distorcion suele ser inversamente proporcional a su intensidad
- Se suele estudiar intervalos de medicion muy amplios, todas las mediciones e informan en dB
	- dB no es una unidad de medida sino una forma de represntacion
	- Las ganacias de V y de A suelen ser distintas a las de P
		- Son igual cuando la resistencia de entrada es igual a la de carga
			- Por esto es importante tener una linea adaptada.


*Clase 4*
- Para mediciones de compatibilidad se debe tener un detectos de cuasi pico y las bandas de frecuencias marcadas por la norma.
	- Se requerie un ancho de banda menor a 140kHz
	- Todos los analizadores tienen un detectos de picos y de cuasi pico.
	- En la pantalla del analizador de espectro tenemos curvas que depende de los estadares marcador, estas curvas son los limites para las perturbaciones
		- Hay una curva clase A(limites industriales) y clase B(aplicaciones industriales)
			- La clase A es mayor a la clase B generalmente
![[Pasted image 20231014190401.png|500]]
- Medidiones de interferencias conducidas
	- Para EEUU y para europa el limite superior es 30MHz
		- Si hay pocos armonicos conducidos, entonces hay poca radiacion
	- Cuando conecto mi dispositivos a la red mi dispositivo recibe interferencia de los otros dispositivos.
		- Todo lo que este conectado a la red con frecuencias entre 150KHz y 30MHz es visto por el dispositivo como una carga
			- Esto tambien depende del enchufe al cual lo conectamos
		- Para evitar este problema se utiliza el Line Impedance Stabilization Network (LISN), que es un estabilizador de impedancia.
			- Si ponemos el LISN en la toma de corriente y se activa el interruptor diferencial porque sé que hay ruido, pero todavía quiero que 50Hz pase para alimentar el dispositivo.
				- Para hacer esto, simplemente debo usar un paralelo, de modo que 1/ωC sea aproximadamente un corto (por ejemplo, 10Ω). Dado que las perturbaciones entre la fase y la tierra pueden ser diferentes, se debe utilizar esta capacidad entre la fase y la tierra y una capacidad entre neutral y la tierra.
				- Aunque estas perturbaciones tendrán una amplitud pequeña, son numerosas y pueden provocar que la corriente absorbida por estos condensadores y que pasa por el neutro sea tan grande (un poco más de 3 mA aproximadamente) que provoque el disparo del interruptor diferencial.
					- Por este motivo, se utiliza un transformador de acoplamiento adecuado para realizar la medición.
			- En la entrada del DUT hay una sonda de corriente. La sonda de corriente es un dispositivo en el que se inserta un cable en el que pasa la corriente y el sensor se comporta como un transformador reductor (TA). Al salir del sensor tenemos 2 cables a los cuales tenemos una tensión que es proporcional a la corriente que pasa en el cable.
				- La sonda de corriente de un electricista está calibrada para 50Hz, mientras que nuestras sondas deben medir en el rango definido por las normas (150kHz o 450kHz, hasta 30MHz).
					- El principio de funcionamiento de la sonda de corriente está relacionado con la primera y segunda ecuación de Maxwell.
					- El fabricante proporcionará la impedancia de transferencia que NO es un número, sino una tabla o un gráfico:
						- $Zt=\frac{Vout}{If}$
						- Donde Vout es la tension de salida e If la corriente del cable
					- Cuando usamos un sensor para una corriente pequeña es bueno utilizar una bobina con alta permeabilidad
![[Pasted image 20231014192557.png|400]]
Como hay dependencia de ω, el fabricante proporciona una Z de transferencia en forma de tabla o gráfico. Existen también sondas de tensión, pero son menos precisas que las de corriente. El LISN es una solución más precisa que la sonda de corriente. De hecho, LISN también utiliza inductores (calibrados siempre en la frecuencia más pequeña indicada por el estándar)
En la compra de las LISN se indica también la corriente máxima soportable (aproximadamente 300-400A). Además de ciertas corrientes se utiliza la sonda de corriente. Las perturbaciones también pueden provenir del tipo de corriente que fluye en el cable, donde por tipo de corriente indicamos las corrientes de modo común y diferencial. Las corrientes de modo diferencial producen un campo con mayor intensidad que las corrientes de modo común.
- El campo producto del dipolo electrico elemental en coordenadas esfericas es: 
![[Pasted image 20231014193128.png|200]]

Nota: la medición del campo irradiado se realiza a 3 metros, por lo que en las cuentas usamos 3 metros como distancia entre el centro del sistema y el punto de observación. De la cuenta observamos que la corriente de modo común que conduce a un campo máximo por debajo del límite de las normas es de aproximadamente 8μA. La cuenta corriente de modo diferencial es idéntica, a diferencia de solo el signo y que conduce a una corriente de modo diferencial de aproximadamente 12mA. Esta aplicación es relevante en el caso de los cables de cinta en los que podemos tener precisamente corrientes de modo diferencial o común.

# Legislacion de la contaminacion electromagnetica
- Clase 2
Por contaminacion nos referimos a los niveles de campos electromagneticos que estamos imersos, en la vida cotidiana.
- Solo analizaremos la radiacion no ionizante

*Cual es el instrumento normativo que utiliza el legislador para fijar los limites?*
- La ley especifica el campo EM limite a soportar que sera le mismo para toda la nacion
- Tambien especifica que el plan de antenas sera una accion a nivel municipal
	- Por lo tanto es el municipio quien decide donde se intalaran la antenas.
	- Si el municipio no ha adoptado un plan, el instalador tiene mas libertad
	- Se debe presentar un plano de antenas hecho por un ingeniero electronico, con detalles del suelo
	- Si se coloca la antena en suelo estatal se le debe pagar un alquiler al estado
	- Si es en terreno privado, se le paga al dueño


*Cuales son los limites de campos electromagneticos?*
Se fijaron los limites con dos decretos del primer ministro de 2003, uno para bajas frecuencias y el otro para altas.
- En estos decretos se fijan limites de exposicion y los valores de precausion
- Por limite de exposicion nos referimos a los valores a los que la poblacion nunca debe estar expuesta, por ninguna cantidad de tiempo.
- Valores de atencion son los valores a los cuales la poblacion puede estar expuerta pero por poco tiempo(4 horas al dia)
- Los valores impuertos tambien deben tener en cuenta los campos preexistentes






