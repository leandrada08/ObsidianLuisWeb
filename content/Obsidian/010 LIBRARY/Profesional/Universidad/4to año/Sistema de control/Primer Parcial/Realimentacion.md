# La Realimentacion


## Cuando hay realimentacion?
Se dice que un sistema esta realimentado cuando existe una secuencia cerrada de relaciones causa-efecto entre as variables de un sistema


## Conceptos basicos
Sistema de control realimentado elemental sin camino de fuga![[Pasted image 20220906110133.png]]
Se definen los siguientes elementos:
-  P: planta o proceso
-  A: Sistema actuador
-  B: sistema de medición + red acondicionadora de señal
-  C: controlador
Se definen las siguientes variables en el lazo:
-  R: señal consigna o referencia
-  Y: salida o variable controlada
-  E: error o señal que se aplica al controlador (E=R-BY)
-  U: señal de entrada a la Planta
-  O: señal entregada por el controlador
-  BY: señal realimentada o señal de retorno
#### Funciones definidas en un diagrama de bloque de sistema de control ki 
-  TCD: transmitancia del camino directo (TCD= CAP)
-  T: Transmitancia del Lazo, función de transferencia del lazo, razón de retorno o simplemente **ganancia de lazo** (T=CAPB)
	- La ganancia de lazo es la ganancia que tenemos a lo largo del lazo si no tenemos senial en la entrada
-  F: diferencia de retorno (F=1+T)
	- La diferencia de retorno es la diferencia entre lo aplicado y lo que me devuelve el lazo
-  Y/R: función de transferencia de lazo cerrado ( Y/R=Tcd/(1+T)=CAP/(1+CAPB))=Geq
-  |F|: realimentación (|1+T|)


## Realimentacion positiva y negativa
### Analisis con diagrama de bloque para realimentacion ki 
![[Pasted image 20220906111603.png]]
Si $\alpha$ tiene el *mismo* signo que $\alpha$" se dice que tenemos **Realimentacion positiva** y si tienen *distinto* signo es **Realimentacion Negativa**
En la práctica, para conocer el signo de una realimentación en continua, bastará que en la expresión matemática de la función de transferencia del lazo T:
1. se eliminen si hubiera, las expresiones de “s” debidas a los polos o ceros en el origen,
2. se verifique el signo resultante para s = 0.
#### observaciones
1. Si el signo de T es positivo, la realimentación es negativa. En este caso, F=1+T, resultará un número positivo y mayor que uno.
2. T=0, se interpreta que no existe realimentación
3. El signo de T es negativo en el rango -1<T<0, la realimentación es positiva. En este caso F=1+T resultará mayor que cero pero menor que uno.
4. T= -1, es realimentación positiva. Se interpreta como de inestabilidad.
5. El valor de T <-1, la realimentación es positiva. Esta situación no tiene una interpretación física en el terreno de la teoría lineal para los sistemas reales. Se considera que el sistema resulta inestable pues se interpreta como que la señal de retorno en el extremo α’’ del lazo de realimentación aumenta indefinidamente en el tiempo, con respecto a la de origen α.  


### Analisis con la diferencia de retorno ki 
Sea la funcion de transferencia $Y/R=\frac{Geq(s)}{1+Geq(s)}$ donde el denominador se llama diferencia de retorno "F", entonces:
1. Si el modulo de la diferencia de retorno es *menor a 1* tenemos **realimentacion positiva**.
	- Si este es *mucho mayor a 1 decimos que tenemos una realimetacion fuerte* 
2. Si el modulo de la diferencia de retorno es *mayor a 1* tenemos **realimentacion negativa**. 
#### Observaciones
- Un teorema de bode dice que el area de realimentacion negativa es igual al area de realimentacion positiva, por eso no es muy bueno buscar valores muy grandes de realimentacion negativa ya que tendremos mucha realimentacion positiva que puede afectar a mucho ruido.
- La realimentacion depende de la frecuencia en la que estemos trabajando, por ellos si tenemos una realimentacion negativa muy fuerte en frecuencias bajar, tendremos una realimentacion positiva muy grande en alguna frecuencia para cumplir el teorema de bode
- Esto hace que el ruido tenga mucho efecto en nuestro sistema
- Es por ellos que analizamos el valor de $\zeta$  , si este es muy pequenio significa que tenemos una realimentacion negativa muy fuerte, es por ello que a valores mas pequenios de este factor nos aparece un pico en la frecuencia de corte, ya que en esta frecuencia se da la mayor realimentacion positiva



## Efectos de la realimentacion
1. Reduccion de *sensibilidad para la variacion de los parametros* de planta
2. Reduccion de *sensibilidad a pertubaciones*
3. Controla la *ganancia global*
4. Controla el *ancho de banda* del sistema
5. *Estabiliza* un sistema inestable
6. Controla la *respuesta transitoria* del sistema
7. Modifica la *ubicacion de los polos*
8. Modificacion de la *funcion de transferencia de lazo cerrado*

### Efectos sobre la ubicacion polos y ceros
Si a un sistema simple le colocamos una realimentacion la funcion de transferencia se modifica de la siguiente manera![[Pasted image 20221011221032.png]]![[Pasted image 20221011221034.png]]
De estas ecuaciones podemos sacar las siguientes conclusiones:
- Ajustando el valor k podemos modificar la ubicacion de los polos
	- Entonces podemos modificar el comportamiento del sistema
	- El metodo para hacer esto es [[Lugar geometrico de las raices]]
- La realimentacion no modifica la ubicacion de los ceros
- El sistema realimentado tendra orden dado por el maximo producto de numeradores o denominadores  
- Si B=1, se ajusta la posicion de los polos sin modificar el orden

### Modificaion de la funcion de transferecia de lazo cerrado 
Sabemos que la funcion de transferencia de lazo cerrado para el sistema definido al principio de esta seccion es $$M=\frac{CAP}{1+CAPB}$$
De aqui podemos ver que si tenemos una realimentacion fuerte, CAPB>>>1 por lo que podriamos reducir la ecuacion a $\frac{CAP}{CAPB}$ y simplificando obtendriamos que $M=\frac{1}{B}$ 
#### Conclusiones
- Cuando la realimentacion negativa es fuerte, la funcion de transferencia de lazo cerrado depende exclusivamente del camino de realimentacion B el cual generalmente se puede construir con componentes precisos
- Dicho de otra manera *Una fuerte realimentacion negativa tiene un efecto invariabilizante de la funcino de transferencia de lazo cerrado*
#### Utilizadades
- Si necesitamos un sistema de seguimiento, colocando una fuerte realimentacion negativa y B=1 se consigue el efecto deseado

### Efecto de la realimentacion en la ganancia total
Cuando un sistema esta realimentado, la funcion de transferencia de este circuito paso a ser $\frac{Y(s)}{X(s)}=\frac{G}{1+G.H}$ donde G esta la ganancia anterior y H la realimentacion, se puede ver que si G.H<1 la ganancia del sistema aumentara, en este caso tendremos realimentacion positiva, y cuando G.H>1 la ganancia del sistema deisminuira, en este caso tendremos realimentacion negativa, no olvidemos que estos paramentros dependen de la frecuencia, por lo que se podria cumplir ambas condiciones en distinta frecuencia, entonces, la realimentacion puede incrementar la ganancia del sistema en un intervalo de frecuencia pero reducirlo en otro.

### Efectos sobre la estabilidad
Viendo la funcion de transferencia descrita en el apartado anterior, si G.H=0, la salida del sistema seria infinita para cualquier entrada, por lo tanto el sistema es inestable, esto demuestra que la realimentacion puede volver inestable un sistema estable, por lo tanto la realimentacion es un arma de doble filo, hay mas condiciones para la estabilidad que G.H=0, la veremos luego, pero como puede volver un sistema inestable tambien puede volver un sistema estable, en el ejemplo anterior, en el caso de aplicar una realimentacion a todo ese sistema, se podria hacer que el divisor sea distinto de 0, volviendo estable es sistema.


### Efecto sobre la sensibilidad
Definimos la sensibilidad como la variacion porcentual de alguna cantidad o funcion especifica de Z del sistema con respecto a la variacion de un parametro $\alpha$ 
En los sistemas de control definimos la sensibilidad donde este Z es la funcion de transferencia de lazo cerrado M y $\alpha$ es la ganancia o planta$$Smg=\frac{\delta M/M}{\delta G/G}$$
Usando la funcion de transferencia del sistema realimentado llegamos a que: $$Smg=\frac{1}{1+G.H}=\frac{1}{1+T}=\frac{1}{F}$$
Por lo tanto aqui vemos como la realimetacion puede favorecer a la sensibilidad como tambien daniar esta
#### Observaciones importantes
- Si se desea evaluar la sensibilidad de la funcion de transferencia de lazo cerrado en funcion de otro parametro de camino directo, obtendremos el mismo resultado
- La realimentacion tambien modifico la ganancia entrada-salida
- *La realimentacion transfirio la sensibilidad del camino directo al camino de realimentacion*
- Si tenemos una funcion $M=\frac{N}{D}$,entonces Sm=Sn-Sd
#### Funcion sensibilidad
Todas las sensibilidades que se calculan dependen de la frecuencia, por lo que recibe el nombre de **Funcion Sensibilidad** y se denota simplemente como: $$S(s)=\frac{1}{1+T(s)}$$

### Efecto sobre el ruido
Para este analisis suponemos el diagrama: 
![[Pasted image 20221009225920.png|750]]
En este caso, suponiendo una entrada nula, la salida por causa del ruido si no tendriamos realimentacion seria: $Y=G2.n$
Y si agregamos la realimentacion la salida se convertiria en: $Y=\frac{G2}{1+G1.G2.H}.n$


### Efectos sobre la velocidad
En el dominio del tiempo la velocidad esta determinada por parametros de la respuesta transitoria(tiempos comunmente) y en frecuencia esta esta caracterizada por el ancho de banda
#### Modificacion del ancho de banda
Llamemos ABsr al ancho de banda antes de agregar la realimentacion y ABcr al ancho de banda con realimentacion:$$ABcr=ABsr.(1+B)$$
Donde B es el bloque de realimentacion
*Conclusion:* 
- La realimentacion incrementa el ancho de banda
- El costo de hacer esto es que reducimos la ganancia del sistema
**Distintos tipos de frecuencia para caracterizar la velocidad**
- Frecuencia de corte de modulo(fc):  Donde T=1 o 0bd 
- Ancho de banda de lazo cerrado(fb): Su frecuencia de corte es donde la funcion de lazo cerrado es $1/\sqrt{2}$ de su maximo valor
	- Comunmente fb=1,3fc a 1,7fc
- Frecuencia de corte de sensibilidad(fcs): Modulo de la funcion sensibilidad igual a 1
	- fcs>fc>fb

#### Exactitud
Se puede medir la exactitud de un sistema analizando el error, este depende de la ubicacion de los polos del sistema, por lo cual tambien podriamos modificarla con realimentacion
- 
- 
# Cancelar polos con ceros  
Si analizamos funciones adentro del lazo no podemos cancelar ceros con polos, que significa, que las inestabilidades internas no se las puede solucionar cancelando con un cero en el mismo lugar, en este caso nos da la razon **Nunca cancelar polos y cero si son internos del sistema, osea, estan adentro del lazo**, si la cancelacion se hace de una funcion transferencia afuera de lazo, osea externa al sistema, si se puede cancelar los polos y ceros


# Parametros de un sistema realimentado
### Velocidad
Se la puede definir de manera cualitativa con tiempos de la curva
#### Tiempos de la curva
Cuando graficamos la respuesta al escalon unitario de un sistema con cierta funcion de transferencia, defimos distintos tiempos
*Completar tiempos*




#### Referencia: 
- [[Sistema de control]]
- [[Diagrama de bloque]]
- [[Funcion de transferencia]]
- [[Lugar geometrico de las raices]]