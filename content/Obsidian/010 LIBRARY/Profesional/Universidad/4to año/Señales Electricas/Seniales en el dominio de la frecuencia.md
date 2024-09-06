# Señales en el dominio de la frecuencia
### Explicar la analogía entre vectores y señales→
Para generar un campo y poner definir cualquier vector en este, necesitamos que estos vectores sean ortogonales, lo mismo pasa con las señales, necesitamos que para poder aproximar de la mejor manera estas, las señales de la base tienen que ser ortogonales
#### Que es la ortogonalidad entre vectores y entre señales y porque es tan importante analizarla
Para poder generar una base de un espacio vectorial necesitamos que los vectores sean ortogonales, lo mismo pasa con una señal, necesitamos para definir cualquier señal un conjunto completo de señales(que estas sean ortogonales)
#### Como analizo ortogonalidad y error

### Teorema de Parseval
La potencia es igual a la suma al cuadrado de sus componentes en la serie exponencial de Fourier. ![](local://C:/Users/leand/remnote/remnote-625df90fa52b4e0035e5ab57/files/PGdcMnut1qc1S53aihkxI2N33W31Fbe8Obop41BqIULNJT5jgjvtRGUvcL6W5a9_7cs3s3MZzw5jYS_1RpZBVuciaidMxD65she8WhgheXvJpFATsHpnYqp0JB2_PV_m.png)
#### Como llevar este teorema a la serie trigonométrica
dividiendo cada componente en raíz de 2  
#### Teorema de Raleigh
Como Parceval pero para transformada, dice que la energía es igual a la integral desde menos infinito hasta infinito del cuadrado de la transformada de la función.    
#### ![](local://C:/Users/leand/remnote/remnote-625df90fa52b4e0035e5ab57/files/biOPW3xcFKEw9IZsgeTjy_Gyxwvpq8wKVVUoTXDaUktUJfA5F_tu3YBb0U-xg3zrPTZHwiUqtplG3uk-UQyoINYrgg4nrxy9O6WeVNbHx1awNXmHVP0ZFLziQa-CrPOU.png) 
#### Diferencia entre señales de energía y de potencia
Las de energía tienen potencia 0 y una energía finita y las de potencia tienen una potencia finita y energía infinita
### Formas de analizar una señal en el dominio de las frecuencia→Serie trigonométrica de Fourier, serie exponencial de Fourier y transformada de Fourier
#### Similitudes y diferencia entre estas
La exponencial tiene el espectro de la trigonométrica dividido en 2 y la transformada tiene la forma del espectro exponencial pero continua cuando las series tienen espectro discreto
#### Como obtener las componentes de la serie exponencial con la transformada de Fourier 
 Cada componente de la serie exponencial seria Cn.DeltaDirac(f-nfo) ademas Cn=(1/To)F(nfo)
#### Como convertir cualquier espectro continuo en uno discreto y como se haría con el modulo del espectro continuo
Haciendo periódica la señal
### Definicion de la funcion pulso de dirac
La definición del pulso rectangular aparece en la falencia para analizar señales en los valores limites, por ejemplo, si quisiéramos analizar la señal escalón unitario en 0(que es cuando esta cambia)  no tiene derivadas en este punto, ahora hay un inconveniente y es que estamos idealizando la función, en la realidad no cambiaria de 0 a 1 en un instante 0 de tiempo, por lo tanto cuando analizamos la derivada de esta función en ese punto mientras hacemos tender el tiempo de cambio de esta función a 0, obtenemos la función pulso de Dirac
#### Con que otras funciones se puede definir esta
Pulso de gauss, pulso triangular, pulso exponencial y funcion de muestreo
#### Que funciones usan la pulso de Dirac en su transformada
Las periódicas, las trigonométricas, la escalón unitario y la constante 
### Propiedades importante de la transformada de Fourier y como pensarlas
Traslación en el tiempo(solo cambia la fase de la transformada),translación en frecuencia(la multiplica por la exponencial), derivada e integral en el tiempo(der. e int. de la exponencial) y derivada e integral en la frecuencia
### Transformada de funciones periódicas
Tiene la misma forma que la transformada de fourier, pero esta "discretizada", sus valores se dividen en T y solo tienen valores en nfo
### Correlación y autocorrelación
La correlación nos da un valor dependiendo de la similitud entre ambas funciones, mientras mas similares sean, este valor es mas grande mientras que la autocorrelación nos da una relacion con ella misma cuando se desplaza en el tiempo
### Para que nos sirve hacer la correlación con una señal seno
Para ver si una señal tiene componentes de esa frecuencia?
### En la transformada discreta de Fourier, cual es la mayor componente de Fourier
El maximo valor de componentes que tenemos es N, luego de esto se repiten, y el maximo valor de frecuencia es 1/fm donde fm es la frecuencia 1/N