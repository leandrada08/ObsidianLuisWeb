# Respuesta en el tiempo

## Introduccion
### Seniales de prueba
Para analizar las respuesta en el tiempo de los sistema emplearemos distintas seniales para probarlo, el beneficio de hacer esto es que estas seniales son muy simples en el tiempo y en la frecuencia, al igual que nos permite analizar todos los sistemas en base a las mismas seniales, estas son: Impulso, rampa, escalon, etc.
### Respuesta transitoria y respuesta en estado estacionario
#### Respuesta transitoria
Va desde un estado inicial a un estado final
#### Respuesta en estado estacionario
Respuesta del sistema cuando t tiende a infinito

### Especificaciones a la respuesta transitoria
1. Tiempo de retardo(td): Tiempo para que alcance por 1ra vez el valor final
2. Tiempo de subida(tr):Tiempo en pasar del 10% al 90% o 5% a 95% o del 0 al 100%
3. Tiempo de pico(tp):Tiempo en alcanzar la sobreelongacion mazima
4. Sobreenlogacion maxima(Mp): diferencia entre el valor de equilibrio y el valor maximo de la senial
5. Tiempo de asentamiento(ts): Tiempo para que se mantenga entre el 2% o 5%

![[Pasted image 20221010102910.png]]

### Polo dominantes
Si el cociente de las partes reales son mayores a 5 y no hay ceros cerca, los polos en lazo cerrado mas cercanos al eje jw dominaran el comportamiento de la respuesta transitoria. Con mucha frecuencia, los polos dominantes en lazo cerrado aparecen en forma de un apr complejo conjugado. Los polos dominantes en lazo cerrado son los mas importantes entre todos los polos en lazo cerrado
Con frecuencia pasa que la ganancia de un sistema de orden superior se ajusta para que exita un par de polos dominantes complejos conjugados en lazo cerrado. La presencia de tales polos en un sistema estable reduce el efecto de la no linealidades, tales como la zona muerta, el huelgo y la friccion de Coulomb  


## Respuesta transitorias a sistema de segundo orden
Forma estandar de sistema de segundo orden $\frac{C(s)}{R(s)}=\frac{\omega n^{2}}{s^{2}+2.\zeta . \omega n .s + \omega n^{2}}$ 
Grafica de la respuesta transitoria de una sistema de segundo orden a un excitacion de un escalon
![[Pasted image 20221010100230.png]]
Analizaremos los dintintos casos para una exitacion de escalon unitario
### Caso subamortiguado $(0<\zeta<1)$
$$c(t)=1-\frac{e^{\zeta .\omega n . t}.sen(\omega d .t + tg^{-1}(\frac{\sqrt{1-\zeta^{2}} }{\zeta}))}{\sqrt{1-\zeta^{2}}}$$
En este caso obtenemos una respuesta que oscila en un inicio(oscila a una frecuencia transitoria wn) pero luego tiende al valor de la excitacion
### No amortiguado $(\zeta = 0)$
$$c(t)=1-cos(\omega n . t)$$
En este caso la respuesta oscila permanentemente en la frecuencia de oscilacion transitoria
### Amortiguamiento critico$(\zeta =1)$
$$c(t)=1-e^{-\omega n .t}.(1+\omega n .t)$$

### Sobreamortiguado$(\zeta >1)$
$$c(t)=1-e^{-(\zeta -(\sqrt{\zeta ^2 -1})).\omega n .t}$$
En estos 2 ultimos casos, la respuesta se amortigua sin oscilar


### Parametros para un sistema de segundo orden
#### Sobrepico SP
$$SP=e^{\frac{-\pi.\zeta}{\sqrt{1-(\zeta)^2}}}.100$$
#### Tiempo de establecimiento ts
$$ts=\frac{4}{\zeta.wn}$$

#### OBs
Para una respuesta transitorio conveniente de un sistema de segundo orden, el factor de amortiguamiento relativo debe estar entre 0,4 y 0,8. Valores pequenios de $\zeta$ ($\zeta <0.4$ )producen un valor de la sobreelongacion excesivo en la respuesta transitoria, y un sistema con un valor grande de $\zeta(\zeta >0.8)$ responde con lentitud

## Obtencion de funcion en el tiempo

### Metodo de descomposicion en fracciones parciales
Metodo para encontrar una respuesta temporal de un sistema de orden n
1. Separo la expresion en N fracciones, donde n es el numero de polos
2. Cada una de estas fracciones tendra un polinomio de orden del polo que tenga en el numerador menos 1
3. Para calcular los coeficiente de estos polinomios hay varios metodos
#### Calculo con limite
$$Rpn=\lim_{s\rightarrow pn}Y(s).(s-pn)$$

#### Igualando polinomios
Igualamos ambos denominadores analizando cada parte del polinomio


#### Metodo grafico para calcular los residuos
Modulo del residuo $|Rs|=\frac{k.\prod distZ}{\prod distP}$
Angulo del residuo $arg(Rs)=\sum arg(distZ) - \sum arg(distP)$ 

**Calcular el residuo de los complejos conjugados**
La solucion de un sistema con polos complejos conjugados es $$x(t)=\frac{M.e^{-\sigma t}}{w} sen(wt+\phi)$$
Donde:
- M: Modulo de la distancia de todos los otros polos y cero menos entre ellos de los complejos conjugados
- $\phi$ : Angulo de la distancia de todos los otros polos y cero menos entre ellos de los complejos conjugados
- $\sigma$ : Valor absoluto de la parte real de los complejos conjugados
- $\omega$ : Valor imaginario de los polos complejos conjugados

En el caso de tener un K $\neq$ 1 este multiplicaria a la solucion
*Observacion*: Calcular el M poniendo las distancia en forma binomial y despues la convertimos
#### Calcular la respuesta de una excitacion senoidal
Supongamos que tenemos una entrada x(t)=7sin(7t+30) un sistema con un K=19, M=4 y $\phi$=45 dado al polo conjugado de la exitacion, entonces la respuesta a la exitacion x(t) sera $$y(t)=7.19.\frac{4}{7}sin(7t+30+45)$$

## Teorema del valor incial y final
### TVI
$$\lim_{t\rightarrow 0}y(t)=\lim_{s\rightarrow infinito}Y(s).s$$
### TVF
$$\lim_{t\rightarrow infinito}y(t)=\lim_{s\rightarrow 0}Y(s).s$$



## Condiciones iniciales
Supongamos un circuito RC, donde la salida del sistema esta conectado a C, por lo que la funcion de transferencia nos quedaria $$Vc(s)=\frac{Vi(s)}{SCR+1}$$
Ahora supongamos que el capacitor estaba cargado antes de la excitacion, esto haria que tengamos que colocar una fuente de valor $vc(0-)/s$ por lo que la nueva funcion de transferecia nos quedaria $$(i)Vc(s)=\frac{Vi(s)}{SCR+1}+\frac{SCR.vc(s)}{(SCR+1).S}$$
- Tener en cuenta que si tenemos una ecuacion diferencia, esta tambien se ve modificada por las condiciones iniciales
- Podemos ver de manera clara como se modifica la respuesta del sistema


## Analizando un sistema constante en un tiempo distinto de 0
En este caso, supongamos que el sistema vale Vcd siempre, y nosotros la analizamos con la transformada de laplace con la ecuacion (i) por lo tanto $$Vc(s)=\frac{Vcd}{s(SCR+1)}+\frac{Vcd.SCR}{s.(SCR+1)}=\frac{Vcd(1+SCR)}{s.(SCR+1)}=Vcd/s$$
Lo cual es logico ya que si tenemosn una respuesta permanentes y la analizamos no nos deberia aparecer un transitorio
- Tambien lo podemos ver como que la exponencial que generara la condiciones iniciales se cancela con la exponencial del transitorio del sistema unilateral

## Analizando un sistema que viene con una tension de continua y se le agrega a ese sistema una tension VCD
$$Vc(s)=\frac{Vcd}{s(SCR+1)}+\frac{vc(0-).SCR}{s.(SCR+1)}=\frac{Vcd}{s(SCR+1)}+\frac{vc(0-).SCR+1}{s.(SCR+1)}-\frac{vc(0-)}{s(SCR+1)}=\frac{Vcd-vc(0)}{s(SCR+1)}+\frac{vc(0)}{s}$$