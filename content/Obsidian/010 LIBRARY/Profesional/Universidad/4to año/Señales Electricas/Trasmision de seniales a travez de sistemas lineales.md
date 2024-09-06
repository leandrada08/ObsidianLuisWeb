# Trasmisión de señales a través de sistemas lineales
## Teoremas de Convolucion en el tiempo y en la frecuencia
La convolucion en el tiempo es igual al producto de las respuestas en la frecuencia y viceversa
## Que es un sistema lineal
Es un sistema que respeta el principio de superposición, en estos sistemas se puede representar la señal como una suma de impulsos y este sistema realizara una convolución a la señal que ingresa
## Como es la respuesta de un sistema lineal invariante en el tiempo
un sistema variante en el tiempo produce una convolución entre la respuesta natural del sistema  y la respuesta del estimulo
## Formas gráficas de ver la Convolución (deltas o área)
Se puede ver como infinitas respuestas a la deltas, que estas tardarían en atenuarse al 100, que se suman y ese resultado da el valor de la convolución en ese punto, o como el área entre la intersección de las 2 figuras
## Que dice el teorema de muestreo
Si la señal contiene una frecuencia máxima finita, entonces, estará determinada por valores en intervalos menores a 1/fm2, este teorema nos permite convertir una señal continua en sus muestras y luego recuperarla, ya que al tomar muestras que respeten el criterio de nyquiz, el espectro de frecuencia de la señal se repetira.
## Cual es el valor máximo en el eje x en la función convolución
Es la suma de los periodos de las señales a las cuales se les hace la convolución
## Que dice el criterio de Paley-Wiener
Básicamente nos da un criterio para saber si nuestro sistema es realizable o no, ya que muchas veces para lograr sistemas ideales necesitamos sistemas que no sean causales, lo cual no es real
## Como se relaciona el ancho de banda con el tiempo de subida
El ancho de banda de nuestro filtro nos dará el máximo tiempo de subida que podríamos tener, la relacion entre este tiempo y la frecuencia de corte es inversamente proporcional
## Energía y potencia normalizada
Son la energía producida o la potencia disipada por una señal cuando la resistencia del medio es 1 Ohm
## Que es el espectro de densidad de energía
Es una relacion de la energía de una señal respecto a sus frecuencias, se lo puede ver como la energía por ancho de banda unitario
## Espectro de densidad energía de la entrada y la respuesta
Esta dado por el espectro de densidad de energía de la entrada multiplicado por el cuadrado de la respuesta natural del sistemas(Si el sistema es lineal)
## Espectro de densidad de potencia
Nos da la relacion de potencia por ancho de banda unitario,  cuando la señal no es periódica, se lo calculara con un limite que es el espectro densidad de energía divido en el periodo, con este tendiendo a infinito, cuando es periódica, se lo calcula como la sumatoria de los espectro de densidad de energía de cada pulso de Dirac en las frecuencias de la señal y la potencia la calculamos como 1/2pi por el area bajo la curva del espectro de densidad de potencia
## Como seria un filtro ideal y porque este no se puede dar en la realidad
Seria un pulso rectangular en la frecuencia y no se lo puede aplicar porque la respuesta seria no casual
## Que debe cumplir un filtro para que se pueda realizar
Energia finita y ceros finitos
## Si tengo 20,40 o 60 decibeles menos, cuanto varia mi potencia y mi amplitud
la potenia varia 100 a la n y la amplitud 10 a la n donde n es 20 por n
## Que define el tiempo maximo de subida
En ancho de banda
## Que es el ancho de banda equivalente
Es el ancho de banda que contiene básicamente toda la potencia de la señal que pasa por el filtro(95% de la energia)
## Cuando se dice que un sistema es lineal
Cuando cumple el ppio de superposición, osea, la salida y la entrada están relacionadas por una ecuación lineal 
## Que debe suceder para que decir que un sistema no genera distorsión
La fase de la señal de salida debe varias de manera lineal negativa o neutro respecto a la entrada y la amplitud de la señal de salida debe ser constante respecto a la entrada
## Que produce el corrimiento de fase lineal negativo en la salida respecto a la entrada
Esto produce un retardo de grupo, lo cual no afecta en la legitimidad de la señal, si el corrimiento no fuera lineal, el retardo seria distinto para cada frecuencia por lo que afectaría a la lectura de la señal
## Que produce la distorsión no lineal y cuando la señal ya no es recuperable
Produce un número infinito de componentes(un polinomio de Taylor) dónde, si tenemos componentes de 3er orden o mayor, la señal no se puede recuperar
## Ecuación de una señal con distorsión no lineal, y como queda en el dominio de las frecuencias
La señal se representa con un polinomio de Taylor y en la frecuencia se hace una convolución
## Que es el producto de intermodulación
Son los productos de orden superior de la señal consigo misma cuando tenemos una distorsión no lineal, en especial cuando tenemos una señal de múltiples frecuencia
## Que es la distorsión por intermodulacion
Es la distorsion generada por los productos de intermodulacion
## Que son los puntos IP2 e IP3 y como los calcularíamos
Son los puntos donde las potencias de 2do orden y 3er orden respectivamente alcanzan la lineal y se los calcula con una señal de 2 bandas, que al producirse los productos de intermodulación, la frecuencia central aparece acompañada de 2 bandas laterales, y con la relacion con estas se calcula 
## Que es el punto de compensación
Es el punto donde la señal real se separa 1dB de la ideal
## Relacion entre P3 y P2 con P1
Se relacionan en base a IP2 e IP3


#### Referncia
- [[Seniales en el dominio de la frecuencia]]