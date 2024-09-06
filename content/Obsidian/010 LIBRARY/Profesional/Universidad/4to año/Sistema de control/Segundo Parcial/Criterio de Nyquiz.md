# Criterio de Nyquiz
Este criterio, obtenido por H. Nyquiz, es util en la ingenieria de control, debido a que permite determinar graficamente la estabilidad absoluta del sistema en lazo cerrado a partir de las curvas de respuesta en frecuencia en lazo abierto, sin que sea necesario determinar los polos en lazo cerrado. Este criterio de estabilidad se basa en un teorema de la variable compleja
### Contorno cerrado del semi plano derecho
Como dijimos el criterio de Nyquist se basa en un teorema de variables complejas, este teorema es una integral de contorno, en principio, nuestra zona de estudio es el spd, por lo analizaremos un contorno que contenga todo el semiplano derecho, este mismo ira desde jw=-infinito hasta jw=+infinito y hara un semicirculo de radio infinito, este teorema que usamos para llegar a este criterio, nos dice que no debe haber un polo en el contorno elegido, por lo cual, se hara un rodeo alrededor del polo que encontremos a los largo del contorno, como se ve en la figura.
![[Pasted image 20221126225641.png|300]]
![[Pasted image 20221126225644.png|300]]
### Expresion matematica del criterio
El criterio para que un sistema sea estable es: $$Z=N+P=0$$
Por lo tanto el sistema sera estable cuando P=N=0 o cuando N=-P, ahora analicemos esta ecuacion con un poco mas de detenimiento 
#### Z
Z corresponde al factor de numero de ceros de 1+G(s).H(s) en el semiplano derecho, por lo tanto estos ceros se convertirian en polos de la funcion a lazo cerrado, es po ellos que siempre tiene que ser 0
#### P
P corresponde al numero de polos de G(s).H(s) en el semiplano derecho del plano s, basicamente en nuestro teorema serian los polos adentro del contorno elegido
#### N
N es el numero de rodeos en el sentido de las aguajs del reloj del punto -1+j0 del diagrama polar de G(s).H(s), para realizar este diagrama tenemos que ver el contorno que elegimos y las condiciones que nos da este, esto quedara mas claro mas adelante cuando analicemos el paso a paso del criterio
### Aplicar el criterio de nyquiz
1. Se grafica el diagrama polar de G(jw) desde w=0+ hasta w=infinito
2. Se agrega la imagen especular con respecto al eje real  para completar desde w=0- hasta w=-infinito
3. Se analiza el giro de radio infinito remplazando $s=R.e^{j\theta}$ , donde R es infinito y $\theta$ varia desde 90 hasta -90
4. Si hay polos o ceros sobre el eje imaginario se agrega los rodes correspondientes de modo que se unan las curvas antes y despues del rodeo correspondiente, para esto $s=r.e^{j\alpha}$ donde r tiende a cero y $\alpha$ varia desde -90 hasta +90
5. Se analiza la expresion matematica del criterio respecto al diagrama polar formado


#### Observacion
Basicamente cada polo en el eje imaginario agrega caminos para analizar

#### Referencia
- [[Estabilidad]]