### Introduccion
El algoritmo CORDIC (Coordinate Rotation Digital Computer) es un método iterativo para realizar operaciones trigonométricas y de rotación de vectores en coordenadas polares. Este algoritmo se utiliza comúnmente en hardware para calcular funciones trigonométricas de manera eficiente.

La aproximación rotacional en el algoritmo CORDIC se utiliza para realizar rotaciones de un vector en el plano xy. El objetivo es lograr que el vector de entrada rote hacia el eje x (la rotación sea cero) mediante la aplicación de una secuencia de rotaciones finitas.

La idea principal detrás del algoritmo CORDIC es realizar rotaciones sucesivas, cada una de las cuales reduce la componente y del vector de entrada. Estas rotaciones se realizan de manera iterativa, y la suma acumulativa de todas las rotaciones da como resultado la rotación total deseada.


### Matematica
El valor anterior (x,y) y el valor nuevo (x’,y’) estan dando por la siguiente ecuacion
$x'=x.cos(\phi)-y.seno(\phi)$
$y'=y.cos(\phi)+x.sin(\phi)$
Trabajando algebraicamente llegamos a 
$x'=cos(\phi)[x-y.tg(\phi)]$(1)
$x'=cos(\phi)[y+x.tg(\phi)]$(2)

- Donde$\phi$es el angulo de rotacion entre los 2 valores
- Hay que tener en cuenta que$tg(\alpha_i)=2^i$
- Si el angulo$\phi$es entre -100 y 100 grados, se puede aproximar$\phi$a una sumatorias de$\alpha_i$
Este ultimo enuncia nos permite reescribir las ecuaciones 1 y 2 de la siguiente manera
$x_{i+1}=K_i[x_i-y_i.d_i.2^{-1}]$(3)
$y_{i+1}=K_i[y_i-x_i.d_i.2^{-1}]$(4)
Donde:
$K_i=cos(\alpha_i)=cos(tag^{-1}(2^{-i}))$
$d_i=\pm1$
Reescribiendo estas ecuaciones llegamos a 
$x_{i+1}=cos(\alpha_i).[cos(\alpha_{i-1})(x_{i-1}-y_{i-1}d_{i-1}2^{-i+1})]$
$y_{i+1}=cos(\alpha_i).[cos(\alpha_{i-1})(y_{i-1}+x_{i-1}d_{i-1}2^{-i+1})]$
Reescribiendo esto
$x_{i+1}=cos(\alpha_i)cos(\alpha_{i-1})[...]$
$y_{i+1}=cos(\alpha_i)cos(\alpha_{i-1})[...]$

Donde se puede separar el valor de adelante que es constante con lo de … que es lo que depende de las muestras anterior, entonces ons queda la ecuacion 3 y 4
- Luego se define la variable z, esta se refiere al ángulo de rotación total o acumulado a través de las iteraciones del algoritmo CORDIC. Puedes pensar en z como la suma de todos los αi​ a lo largo de las iteraciones, y se utiliza para calcular las coordenadas rotadas en cada paso del algoritmo

### Vectoring mode
El modo vectorial (vectoring mode) en el algoritmo CORDIC se utiliza para encontrar el ángulo de rotación y la magnitud de un vector en coordenadas cartesianas. Mientras que en el modo de rotación calculamos las coordenadas rotadas de un punto, en el modo vectorial calculamos el ángulo y la magnitud del vector original.

En el modo vectorial, tenemos un vector de entrada \((x, y)\) y queremos encontrar el ángulo \(\theta\) y la magnitud \(r\) del vector. La iteración del algoritmo en el modo vectorial se ve así:

$x_{i+1} = x_i - d_i \cdot y_i \cdot 2^{-i}$
$y_{i+1} = y_i + d_i \cdot x_i \cdot 2^{-i}$
$z_{i+1} = z_i - d_i \cdot \arctan(2^{-i})$

Donde:
- $(x_i, y_i)$ son las coordenadas en la \(i\)-ésima iteración.
- $d_i$ es el bit de dirección que indica si la rotación es en sentido horario o antihorario.
- $z_i$ es el ángulo acumulado hasta la \(i\)-ésima iteración.

En el modo vectorial, el algoritmo CORDIC se ejecuta hasta que $y_n$ se acerca a cero, y en ese punto, $z_n$ se convierte en una buena aproximación del ángulo \(\theta\), y $x_n$ y $y_n$ dan la magnitud $r$ del vector.

Este modo es útil para aplicaciones que requieren conocer tanto la magnitud como la dirección de un vector en coordenadas cartesianas.


### Generalizacion del algoritmo

### Implementacion en nuestro diseño