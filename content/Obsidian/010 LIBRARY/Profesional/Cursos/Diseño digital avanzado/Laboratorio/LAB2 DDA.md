# Explicacion video
## Introduccion al lab
El laboratorio de filtros FIR y recursivos tiene como objetivos:

- Analizar y modelar filtros.
- Trabajar con herramientas de punto fijo.
- Explorar metodologías de escritura de filtros.

### Python lab
Se desarrolla una herramienta para evaluar los efectos de cuantización en filtros y señales, experimentando con cambios en la cantidad de bits en la señal de entrada y coeficientes, y evaluando el comportamiento de los polos y ceros al modificar la resolución de los coeficientes. 

Los recursos proporcionados incluyen una guía práctica y laboratorio para desarrollar de forma independiente, ejemplos de Verilog y scripts en Python, y un tutorial de Python para aquellos sin experiencia previa en el lenguaje.

La cuantización de coeficientes de filtro FIR implica definir los bits a utilizar tanto para los coeficientes como para las muestras de entrada, ajustando la cantidad de bits afecta la calidad de la señal de salida, y modificarla permite observar cómo afecta la calidad del filtro y la señal resultante, tanto en el dominio del tiempo como en el de la frecuencia.

## Filtro en verilog

### Observaciones importantes
- **USAR mas la herramienta teros hdl**
	- ![[Pasted image 20240201092817.png]]
	- Es el segundo boton

---

- Se detalla la implementación de filtros FIR en Verilog, destacando la estructura del código, la manipulación de matrices para representar coeficientes y la importancia de comprender la implementación a nivel de hardware.
	- Cuando le declaras que una matriz es signada, la herramienta le coloca automaticamente un bit de signado
		- Por lo cual no hace falta que estemos pensando que el primer bit es signado ya que la herramienta lo hace
	- Cuando se define una matriz lo primero que se coloca es el ancho y luego la cantidad de filas.
		- Cuando se trabaja la matriz es al reves, primero pongo la fila y despues el ancho
	- Se define una matriz que va de 3 a 1 para el Shift register para el fir ya que el valor 0, de la ecuacion, no se almacena, es directamente la entrada, entonces para usar siempre los mismo valores de numeros, se define de esta manera.
- Explora métodos para la implementación del árbol de suma en el filtro, discutiendo la eficiencia y la representación en diferentes herramientas de diseño.
	- Tambien se puede hacer un shift register y el producto con for para simplificar el codigo
	- Tambien se puede usar generate con assign para que sea de manera generica y extendibles.
	- Tambien un generate con always y asignacion no bloqueante, pero esto agregaria latencia, para no agregar always tenemos que realizar asignacion bloqueantes
	- Si no usamos generate y queremos colocar solo always, no podemos expandirlos.
	- Tambien se puede hacer directamente con arbol de suma, de manera bruta o con always,  hay que usar un codigo especifico para que se realiza en arbol de suma
- Analiza la saturación y el truncado en la representación de números, proporcionando ejemplos detallados y estrategias para la detección de palabras positivas y negativas.
	- En la suma se agrega que $log_2(N)$. Esto es mas facil verlo cuando lo paralelizamos
	- Para hacer el redondeo, concatenacio, saturacion y truncado, hay que tener en cuenta que:
		- Como los coeficientes son entre 0 y 1, la salida tambien tiene que tener el mismo rango de valor que la entrada, ya que nunca se agregaran bits
		- Entonces hace falta agregar un bloque de redondeo y concatenacion
	- Para saber si podemos representar o no la magnitud tenemos que analizar si en algun valor mas significativo que nuestro proximo valor signo, hay un bit, distinto que nuestro signo, este valor no se puede representar. Por lo cual solo tenemos que analizar estos valores para saber si es necesario hacer saturacion.
	- Entonces si el bit es positivo tengo que ver que ningun bit a sacar sea distinto de 0 y si es negativo tengo que que lo mismo pero con 1.
		- En caso de que esto se cumpla solo saco los valores,
		- En caso de que no se cumpla, tengo que analizar el bit de signo para ver para donde satura(positivo o negativo)


## Testbech
- Las variables de entrada son reg y las de salida son wire
- Se puede usar la funcion $sin para generar una seno
	- Esta funcion es real
	- Para asignar a una variable reg, la herramienta la convierte en entero de manera automatica, por lo cual redondea al entero
		- Para evitar este error, se multiplica por la parte fraccional, basicamente se convierte el real a un valor que cuando se redondee, tenga el valor deseado fraccional
			- Esto se realiza multiplicado por $2^{NBF}$ donde NBF son los bits fraccionales.
			- Hace falta que si el valor es mayor al maximo a representar, se lo lleve al valor maximo manualmente y no dejar que la herramienta redondee porque nos generara un valor negativo
	- Hay que generar una muestra de esta seno cada 1 clock para evitar perder informacion


El artículo aborda la implementación y simulación de filtros FIR:

- Se describe la implementación de un filtro FIR y su testeo mediante un test bench, incluyendo el modelado del filtro con operaciones de suma y producto, y consideraciones sobre la representación de datos reales.
- Explora la conversión de números reales a punto fijo, abordando problemas de redondeo y manejo de valores límite, así como técnicas para garantizar la alineación de muestras con el flanco de reloj en simulaciones.
- Detalla el modelado de señales y filtros en simulación, explicando la generación de muestras de señales, consideraciones sobre el periodo de espera en el filtro, y demostrando la simulación y visualización de resultados en forma de onda.


## Filtro IIR
### Python
- Introduce el modelado de filtros IIR en Python, enfocándose en filtros recursivos y proporcionando ejemplos de representación gráfica de polos y ceros, así como análisis de la respuesta en frecuencia.
- Describe la sección de configuración del filtro en cascada, dividiendo la primera etapa en tres subfiltros y explicando cómo cada sección se aplica sucesivamente a la señal de entrada.


- La calidad de tu filtro esta limitada por la quantizacion de las muestras de entradas
	- Se aplica cuantización a las muestras de entrada y a los coeficientes del filtro. La cuantizacion de las muestras de entrada fija cual es el limite
	  - Se analiza el error generado al cambiar la resolución de la cuantización.
	  - La relación señal-error depende de la cantidad de bits utilizados en el sistema.
	  - Se presenta una curva que relaciona la relación señal-error con la cantidad de bits utilizados.
	  - El desempeño del filtro no mejora significativamente al aumentar la cantidad de bits más allá de cierto punto.
	  - Se recomienda mantener la cantidad de bits en un rango óptimo para maximizar el rendimiento y minimizar el uso de recursos.

**2 horas y 1 minutos**
![[Pasted image 20240201172649.png]]
> En esta imagen podemos ver que si tenemos 18 bits en la quantizacion de nuestros coeficientes o 31, la relacion señal ruido es igual, y con 15 no diminuye mucho, por lo cual nos deja elegir con un buen criterio nuestros bits. 


### IIR Verilog 1
El artículo profundiza en aspectos específicos del diseño de filtros recursivos:

- Se discute la alineación de muestras en simulación, presentando dos opciones y destacando las ventajas de tener ambos escenarios para jugar con la metodología.
- Examina la estructura del filtro recursivo, enfatizando la manipulación de coeficientes, la modularidad del diseño y el proceso de cuantización y truncado, incluyendo la gestión de la resolución.
- Explora cómo se realizan las operaciones de suma y producto en las muestras, junto con la aplicación de saturación y truncado.



### IIR Verilog 2
- En este modelo se tiene un top level, un filtro generico y 3 archivos que son los coeficientes de cada filtro de las cascadas, de esta manera si queremos modificar los coeficientes, solo tenemos que cambiar estos archivos.
  - Se detalla la configuración del test bench para analizar el comportamiento del filtro, incluyendo la aplicación de señales de impulso y escalón.
	- Con lo cual, con un mismo test bench podemos analizar todos los comportamientos: senoidal, al inpulso y al escalon
	- Cuando queremos relanzar el tb, hay que apretar en el ultimo boton del panel superio(un circulo con una flecha como de reiniciar)

  - Se destaca la importancia de las verificaciones funcionales utilizando diferentes estrategias, no solo limitadas a simuladores.
  - Se ofrece una visión sobre cómo integrar el filtro en el proyecto, simplificando la inclusión de archivos necesarios y evitando errores de inclusión duplicada.



# A realizar por nosotros

>Lo que nosostros tenemos que hacer esta dentro del zip LAB

**Consigna 1**
Implementar en FPGA el filtro FIR según los siguientes archivos
- top_design.v
- signal_generator.v
- filtro_fir.
- SarTruncFP.v
Agregar los IPs VIO e ILA para controlar en forma remota el diseño
- Nuestra tarea basicamente aqui es analizar los codigos dados e implementar el vio y el ila


**Consigna 2**
Considerar un sistema de transmisión compuesto por una señal senoidal y un filtro pasa bajo con las siguientes características:
- Señal senoidal compuesta por dos frecuencias f1 = 17kHz (A = 0:5) y f2 = 1:5kHz (A = 1:0)
- Frecuencia de muestreo fs = 48kHz
- Filtro pasa bajo con frecuencia de corte fcut = 8khz


**Consigna 3**
Desarrollo del modelo
1. Utilizando el scripts de Python coeff.ipynb, determinar los coeficientes del filtro para una frecuencia de corte de fcut = 8khz. El filtro debe tener una longitud de 15 coeficientes.
2. Realizar el diagrama en bloques del filtro.
3. Generar un proyecto con los archivos entregador por la cátedra con la herramienta Vivado.
4. Configurar el archivo mem.hex con las señales senoidales especificadas previamente utilizando el script genmem.py.
5. Generar los coeficientes del filtro utilizando el script coeff.ipynb para los siguientes valores de frecuencias de corte fcut = 0:5khz;8khz;18khz.
6. Configurar el filtro en verilog con los valores de los coeficientes cuantizados (sintetizar cada filtro por separado).
7. Implementar en FPGA y graficar las señales senoidales pre y pos filtradas.