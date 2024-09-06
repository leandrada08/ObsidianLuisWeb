# Analisis de la estabilidad relativa
Podemos extrapolar lo visto en el criterio de nyquist, para ello primero vamos a acotar nuestro analisis a sistemas sin polos ni ceros en el semiplano derecho en ningun bloque, por el criterio de nyquist sabemos que al no tener polos en el semiplano derecho, necesitamos que nuestro diagrama polar no de ninguna vuelta al punto -1+0j, por lo tanto mientras mas cerca este nuestro sistema de este punto, mas inestable sera, cuando nuestro sistema pasa por el punto tendriamos un oscilador, por lo tanto en base a lo antes mencionamos podriamos definir variables que nos indiquen la cercania a este punto, estas variables se llama **Margen de ganancia y margen de fase.** 
### Margen de fase
El margen de fase es la cantidad de retardos de fase adicional en la frecuencia de cruce de ganancia unitaria para llevar al sistema al brode de la inestabilidad.
Se lo calculo como $$\gamma=180+\phi$$
Donde $\phi$ es el angulo de la funcion de transferencia en lazo abierto en la frecuencia de ganancia unitaria
### Margen de ganancia
El margen de ganancia es el reciproco de la magnitud |G(jw)| en la frecuencia a la cual el angulo fase es -180 $$Kg=\frac{1}{|G(jw)|}$$
![[Pasted image 20221127103316.png|500]]
#### Criterio para el analisis
- Para que el sistema se estable, ambos margenes deben ser positivos
- A mayor valor de ambos, mayor estabilidad relativa tendra el sistema
#### Observaciones
- Los margenes de fase y de ganancia de un sistema son en conjunto una medida de estabilidad relativa de un sistema, por si solo no aportan un indicio suficiente sobre la misma. 
- Se los puede utilzar como criterio de disenio
- Si el sistema es de fase minima(ceros y polos en el SPD) los margenes de fase y de ganancia deber ser positivos con el fin de que el sistema sea estable

## Margen de ganancia y margen de fase Formigli

![[Pasted image 20221110104800.png|300]]![[Pasted image 20221110111017.png|300]]
Si particularizamos $G.H(s=jw)$ estamos obteniendo la relacion en frecuencia de esta funcion, si al trabajar con la frecuencia, se cumple modulo igual a 1 y fase igual a -180 significa que estamos trabajando con un K que nos posiciona los polos sobre los ejes imaginarios, por lo tanto generaria una oscilacion sin atenuacion, entonces, usaremos este criterio para saber cuando podemos aumentar la ganancia sin generar esta oscilacion permanente, por lo tanto, cuando trabajemos con bode, marcamos el punto de fase -180 y de ganancia 0dB, la diferencia entre la frecuencia de -180(frecuencia de cruce de fase) y de 0 db(frecuencia de cruce de ganancia) lo llamamos *margen de ganancia* y a la diferencia de fase en la frecuencia de cruce de ganancia y -180 le llamamos *margen de fase*






#### Referencia
- [[Estabilidad]]
- [[Criterio de Nyquiz]]