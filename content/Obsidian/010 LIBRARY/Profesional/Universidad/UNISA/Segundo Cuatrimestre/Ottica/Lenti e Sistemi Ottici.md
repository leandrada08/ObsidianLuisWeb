
### Introduccion
Las siguientes consideraciones permiten el estudio de las superficies ópticas. 
- En un medio homogéneo, los rayos tienen trayectoria rectilínea.
- Al acercarse a una discontinuidad entre dos medios homogéneos, se genera un rayo reflejado y un rayo refractado o transmitido.
- Las direcciones a lo largo de las cuales se propagan el rayo reflejado y el rayo transmitido están determinadas por las leyes de Snell. 


### Superficie optica
Una superficie óptica es una superficie refringente que separa dos medios homogéneos diferentes. La superficie refringente más común es la esférica (dioptría esférica).

![[Pasted image 20240313170857.png]]

- Las superficies ópticas son superficies de separación entre un medio con un índice de refracción $n$ y otro medio con un índice $n'$. 
- Dicha superficie es refringente, es decir, es capaz de refractar las radiaciones electromagnéticas. Solo nos preocupamos por los rayos transmitidos de un rayo que incide en esta superficie.
- En la práctica, una superficie óptica modifica la forma de las superficies de igual fase de la onda incidente al variar su velocidad de propagación $c/n$. Por ejemplo, la superficie óptica en la figura transforma frentes de onda esféricos divergentes en frentes de onda esféricos convergentes al disminuir la velocidad de propagación en la región central $(c/n’' < c/n)$.

![[Pasted image 20240313171012.png]]

- Se tenemos una fuente puntual, cuando las superficies de igual fase encuentran la superficie óptica, la concavidad del frente cambia de cóncavo a convexo. Como hay un índice de refracción diferente, también cambia la velocidad de fase. En particular, la onda electromagnética se ralentiza porque tenemos un índice mayor después de la superficie óptica.
	- Nota: Es importante recordar que las superficies de igual fase son aquellas en las que las ondas electromagnéticas que estamos modelando como rayos tienen todas la misma fase. Por lo tanto, si los rayos cambian de dirección, las superficies de igual fase también deben deformarse para mantener esta característica en la fase de las ondas electromagnéticas.


### Diottro sferico
![[Pasted image 20240313171358.png]]
- C: Centro de curvatura
- D:Apertuda
- R:Radio
- V:Vertice
- C’: Asse ottico(retta passante per i punti C e V)

- Una superficie piana pui considerarsi una supeficie sferica con raggio di curvatura $R=\infty$ 
### Raggi indicenti su una superficie
- Raggi meriadiani: Tiene una trayectorio en un plano que contiene al asse ottico
- Raggi obliqui: Tienen trayectoria en plano no diametrales
- Raggi parassiali: Son rayos meridiani o obliqui con trayectorio muy proxima al asse ottico
	- Los rayos parassiali tienen angulo muy pequeño e inciden in punto muy cercanos al vertice de la superficie optica
	- En la hipostesis de parassialita $cos(\theta)\approx 1$ , $sin(\theta) \approx \theta$ , $tan(\theta) \approx \theta$
- Basicamente todos los rayos estan divididos en parassiali y no parassiali
![[Pasted image 20240313172117.png]]

### Convenciones de la optica geometrica

![[Pasted image 20240313172502.png]]
- Si consideran rayos que se propagan de izquierda a derecha
- En relación al eje óptico, un punto de la superficie tiene una altura positiva si está por encima del eje y negativa en caso contrario.
- El sentido positivo para medir el ángulo que el rayo forma con el eje óptico es en sentido antihorario. 




![[Pasted image 20240313172514.png]]
- El radio de curvatura de la superficie óptica es positivo si el centro de curvatura está a la derecha del vértice (superficie convexa) y negativo en caso contrario (superficie cóncava).
- Al medio desde el cual proviene el rayo se le asigna un índice de refracción n, mientras que al medio en el cual el rayo es refractado se le asigna un índice n’ 
- n > 0 si el rayo viaja de izquierda a derecha.







![[Pasted image 20240313172612.png]]
- En un punto genérico de la trayectoria de un rayo se define la pareja de parámetros  $y$(Distancia del rayo al eje optico) e  $n \cdot \theta$. 
- Las coordenadas del rayo se organizan en un vector columna llamado vector de coordenadas del rayo.
- Identificamos las relaciones que relacionan los vectores de coordenadas del rayo entrante y del rayo saliente adyacentes a la superficie. 

### Refraccion para distintos diottro esferico

#### Convexo
**Desarrollo matematico:**
![[Pasted image 20240314094112.png]]
- Supongamos rayos incidente parassiali y transmitidos con coordenadas $(y,n\theta);(y',n'\theta')$
	- $y=y'$

- Aplicando ley de snell con los angulos $\alpha$ y $\alpha'$ y sabiendo que se cumplen relaciones de seno y coseno de parassialita llegamos a: $$n\cdot\alpha=n'\cdot\alpha'$$
- Tambien se cumple la relacion $\alpha=\theta+\gamma$ ; $\alpha'=\theta'+\gamma$ 
	- Esto es cierto para α porque tenemos dos rectas paralelas cortadas por una transversal (las rectas son el eje óptico y su proyección superior) y γ está presente en α. Sin embargo, para α' siempre tenemos dos rectas paralelas cortadas por una transversal pero γ es un ángulo alterno.
- En base a esta relacion podemos calcular $n'\cdot\theta$ que es el valor de nuestros interes, ya que el otro valor de coordenada($y’$) ya lo tenemos: $$n'\cdot\theta'=n\cdot\theta-(n'-n)\cdot\gamma$$

- Tambien notamos por trigonometria basica que $R\cdot sin(\gamma)=y$ y que $sen(\gamma)=y/R$ y a su vez por parassialita $sen(\gamma)=\gamma$ 
	- Entonces, podemos reescribir la anterior ecuacion como: $$n'\cdot\theta'=n\cdot\theta-(\frac{n'-n}{R})y$$

- En base a esta ecuacion definimos k como $k=\frac{n'-n}{R}$ potenza ottica del diottro($l^{-1}$)
- Si el radio de curvatura de la superficie esférica se expresa en metros, la potencia óptica se expresa en dioptrías($m^{-1}$)

**Matriz de refraccion:** 
- En base a los resultados obtenidos, armamos un sistema de ecuacion y podemos obtener la matriz de refraccion
![[Pasted image 20240313173745.png]]
#### Concavo
- Para el concavo, hacemos el mismo analisis con un par de diferencias
	- Radio de curvatura R<0
- Aplicando ley de snell con los angulos $\alpha$ y $\alpha'$, sabiendo que se cumplen relaciones de seno y coseno de parassialita, aplicando la relacion entre los angulos $\gamma,\theta,\alpha$ y realizando el mismo analisis que para convexo llegamos a :$$n'\cdot\theta'=n\cdot\theta+(n'-n)\cdot\gamma$$
- De la cual tambien aplicando trigonometria y parassialita podemos llegar a $$n'\cdot\theta'=n\cdot\theta+\frac{(n'-n)}{R}\cdot y$$
- Como R es negativo, podemos usar su valor absoluto y la ecuacion quedaria igual a la de convexo
	- *Por lo tanto tendriamos la misma matriz de refraccion*

#### Plano
![[Pasted image 20240313173956.png]]
- Queremos analizar el caso en el que el dioptrio esférico es una superficie plana. 
- Este caso es una aproximación bastante simple ya que una superficie no es más que un dioptrio esférico con un radio de curvatura que tiende a infinito. Recordando la definición de la matriz de refracción, podemos obtener la matriz de refracción para este caso particular:

![[Pasted image 20240313174004.png]]
- En todos los casos, todos los dioptrios esféricos tienen matrices con determinante unitario, por lo que la matriz es transparente para las potencias, es decir, toda la potencia que tenemos antes de la superficie la encontramos igual después de la superficie.


### Matriz de trasmision
![[Pasted image 20240314103427.png]]
- En este caso estudiaremo como se propaga un rayo en un medio homogeneo constante, por lo tanto:
	- $n=n'$
	- $\theta'=\theta$ 
	- Entonces: $n'\theta'=n\theta$ 
- Calculamos la nueva coordenada $y'$ con trigonometria
	- $y'=y+d\cdot tg(\theta)$ 
		- Aplicando parassialita
	- $y'=y+d\cdot\theta$

**Matriz de trasmision**
- Aplicando un sistema de ecuacion con la obtencion de ambas coordenada llegamos a la matriz de transmision:
 ![[Pasted image 20240314103125.png|200]]
 
La matriz 2x2 obtenida es la matriz para el caso particular en el cual analizamos la trasmision del rayo en un medio homogeno entre 2 puntos distantas, con una distancia d. Es por esto que toma el nombre de matriz de trasmision $T$

### Reflexion

- *Convenio*
	- El índice de refracción es positivo si el rayo viaja de izquierda a derecha. 
	- El índice de refracción es negativo si el rayo viaja de derecha a izquierda. 

- Por lo tanto, la reflexión se estudia como la refracción en un medio con un índice negativo $n' = -n$. 
- Además, el rayo reflejado viaja de derecha a izquierda, por lo que las distancias recorridas por el rayo son negativas. 

*Explicacion simple*
- Dado que, por convenio, los rayos se propagan en la dirección positiva de izquierda a derecha, entonces a un rayo reflejado que se propaga de derecha a izquierda se le asocia un índice de refracción negativo. 
- Por lo tanto, la reflexión no es más que el estudio de una refracción pero con un índice de refracción negativo. Dado que el medio en el que tenemos el rayo reflejado es el mismo medio en el que también tenemos el incidente, entonces en módulo los dos índices de refracción son idénticos porque es el mismo medio.

#### Concavo y convexo
![[Pasted image 20240313181615.png]]
- Si el espejo es convexo, la matriz de reflexión no cambia si se toma la convección habitual en el signo del radio de curvatura
- Dado que el rayo reflejado no es más que un rayo refractado pero con un índice de refracción igual al del medio en el que tenemos el rayo incidente pero cambiado de signo, entonces la matriz que obtenemos (es decir, una matriz de reflexión) es la misma pero se debe cumplir la condición $n' = -n$
.


#### Plano
![[Pasted image 20240313181750.png]]
- En el caso de que la superficie reflectante sea un plano, entonces tendremos una reflexión en un dioptrio esférico de radio infinito y la matriz de reflexión se convierte
- Todas estas matrices de reflexión siempre tienen un determinante unitario. Hemos analizado el caso de un espejo cóncavo, pero si el espejo fuera convexo, la matriz no cambiaría si se asume la convención habitual sobre el signo del radio de curvatura


## Sistema optico complejos
### Definicion sistema optico complejo
- Un sistema optico complejo es un sistema con distintos tipos de superficies en el medio
![[Pasted image 20240313181918.png]]
- Un sistema óptico (centrado) es una sucesión de superficies refringentes y/o reflectantes constituidas por porciones de esferas cuyos centros yacen en una línea recta (eje óptico del sistema).
- Según la convención de la óptica geométrica, el sistema óptico se analiza de izquierda a derecha. Dado que cada dioptrio tiene su propia matriz de refracción y las lentes están separadas por un medio con un índice de refracción constante, la transmisión del rayo puede estudiarse mediante una matriz de transmisión, lo que implica que todo el sistema puede ser estudiado simplemente mediante productos entre matrices. Al final, el sistema completo nos dará el par $(y', n' \cdot \theta')$ simplemente multiplicando el par $(y, n \cdot \theta)$ por la matriz total del sistema.


#### Definiciones importantes
*Punto objeto real:* es el punto $S$ del cual parte un haz de rayos.
*Punto imagen real:* es el punto $S'$ en el cual convergen todos los rayos que parten del punto objeto real $S$ después de atravesar el sistema.

- Cuando todos los rayos que parten del punto objeto real $S$ convergen en el punto imagen real $S'$, entonces los puntos $S$ y $S'$ se definen como *conjugados*.
- Además, un sistema óptico se define como *simétrico* si es posible intercambiar el punto $S'$ con el punto $S$, es decir, si es posible hacer que un haz de rayos parta del punto $S'$ y estos, después de atravesar el sistema, converjan todos en $S$.


![[Pasted image 20240313182033.png]]


*Punto imagen virtual:* El punto $S’$ en el que convergen las prolongaciones de los rayos en caso de divergencia al salir del sistema
![[Pasted image 20240313182204.png]]
#### Sistema optico estigmatico
- Se a cada punto $S$ del espacio se le puede asociar un punto conjugado $S'$, entonces el sistema se llama *estigmático*.
- Un sistema estigmático produce una imagen bien definida del objeto, que está compuesta por todos los puntos imagen asociados a los puntos objeto que componen el objeto.
- En la hipótesis de parassialidad es suficiente que la coincidencia $S$ → $S'$ exista para todos los puntos de una región limitada concentrada alrededor del eje óptico del sistema (objetos fuente de tamaño limitado).

**Obtencion de ecuacion**
![[Pasted image 20240314105734.png]]
- Sea $C'$ y $C$ las matrices con coordenadas desde el medio de izquierda a derecha respecticamente.
- Sea $R_1,R_2,R_3$ las matrices de refraccion de cada lente y $T_{12},T_{23}$ las matrices de trasmision entre los medios 1 y 2 e 2 y 3 respectivamente


- Iniciamos calculando las cordenadas del rayo despues de cruzar la primer lente
$C'=R_1\cdot C$
- Luego, a este mismo rayo hay que calcular su trasmision en el medio 1→2
$C''=T_{12}\cdot C'=T_{12}\cdot R_1\cdot C$
- Ahora repetimos este proceso con las siguientes refracciones y espejos, obteniendo
![[Pasted image 20240314110652.png]]

- Como podemos notar, hemos obtenido un total de 5 matrices($2xN_{Lentes}-1$).
- Además, la sucesión de las matrices es inversa a la convención de la óptica geométrica, es decir, para escribir rápidamente la ecuación matricial, se escriben las matrices de refracción o transmisión a partir de la derecha yendo hacia la izquierda.

**Constantes de Gauss**
Como todas las metrices de trasmision y refraccion son de determinante unitario, la matriz $S_0$ es 2x2 y tendra determinante unitario, se puede escribir como :
![[Pasted image 20240314114632.png|300]]


## Lentes
Una lente es una sistema optico centrado simple, es generalmente de vidrio y tiene superficies efericas concavas o convexa(una tambien puede ser plana)
Las 6 lentes fundamentales son:
- Lente bi-convexa
- Lente plana-convexa
- Lente menisco-convexo
	- Esta se caracteriza ya que ambas lentes son del mismo tipo pero con distinto rayo
	- R2>R1
- Lente bi-concavo
- Lente plano-concavo
- Lente menisco-concavo
	-  Esta se caracteriza ya que ambas lentes son del mismo tipo pero con distinto rayo
	- R1>R2
Estas tambien se pueden llemar al reves dependiendo de la biografia, como la bi convexa en algunos libros la llaman bi concava

![[Pasted image 20240314115035.png]]
- Estas se utilizan para hacer una estimación aproximada del sistema óptico deseado, pero posteriormente se utilizan software para perfeccionar el sistema.
- El fenomeno que regula el comportamiento de estas lentes es la refraccion optica(lente refractante)

### Tipos de lentes
#### Lente positiva o convergente
![[Pasted image 20240314115756.png]]
Una lente es *positiva o convergente* si un haz de rayos paralelos que la atraviesan convergen en un punto
- La lente transforma un frente de onda plano en un frente de onda esferico convergente en un punto sobre el eje
	- Nota: El punto en el que convergen los rayos se encuentra en el eje óptico.

#### Lentes negativo o divergente
![[Pasted image 20240314120034.png]]
La lente es negativa o divergente si un haz de rayos paralelos que lo atraviesan diversen
- Este tipo de lentes transforma un frente de onda plano en un frente de onda divergente desde un punto sobre el ojo
	- Nota: El punto (en este caso virtual) desde el que salen los rayos se encuentra en el eje óptico.


### Matriz ingreso-salida de la lente
- Para estudiar la propagación de un haz a través de una lente desde su superficie de entrada a la superficie de salida, el enlace secuencial entre las coordenadas de entrada y salida en cada superficie atravesada
- Esta matriz se obtiene sel producto de la matrices de refraccion de los 2 superficies y de la matriz de transferencia del interior de la lente
![[Pasted image 20240314120453.png]]

- Para la imagen dada, si llamamos $T_{12}$ a la matriz de trasmision del interior del lente y $R_1$ y $R_2$ a las matrices de reflexion de las superficie 1 y 2 respectivqmente, nuestra matriz de ingreso-salida $S_0$ es:$$S_0=R_2\cdot T_{12}\cdot R_1$$
- Haciendo el producto de estas matrices y definiendo $k_2=\frac{n2-n}{R2}$ y $k_1=\frac{n-n1}{R1}$ nos queda el resultado: 
![[Pasted image 20240315094743.png]]
- Como $S_0$ es producto de matrices 2x2 con determinantes igual a 1, entonces $S_0$ tambien tiene determinante igual a 1, por lo cual:

$$AD-BC=1$$
![[Pasted image 20240314120612.png]]
- Se considera en las ecuacion n’ el de la lente y n el del medio externo
- Como estamos en condiciones de paralelismo(parasialita) podemos considerar que los rayos entrantes son paralelos al eje
### Matriz de transformacion
- Esta nos sirve para calcula las cordenadas general en el punto $P'$ sobre el plano $\pi'$ del rayo que sale del punto $P$ del punto $\pi$   
- Suponiendo que el haz optico es orientado de derecha a izquierdas, entonces tambien calculamos las distintas $d,d1,d2$
![[Pasted image 20240314121915.png]]

- Definimos la matriz $Q$ como la matriz de transformación que transforma las coordenadas de partida en las coordenadas de llegada. 
	- Esta matriz está compuesta por el producto entre matrices de transferencia derivadas de las distancias entre los planos y la lente y la matriz $S_0$ de la lente
	- Nota: Normalmente, el segundo componente del vector que identifica las coordenadas del radio es el producto entre el ángulo entre el radio y el eje de la lente y el coeficiente de refracción del medio. Aquí el coeficiente no está escrito simplemente porque el medio de partida es aire, es decir, una tarifa unitaria. Así que está implícito.
![[Pasted image 20240315095205.png]]


### Aumento trasversale M
El aumento transversal se define como la relación entre y' e y, es decir, la relación entre la distancia desde el eje óptico del punto en el plano π' es la distancia desde el eje óptico del punto en el plano π:
$$M=\frac{y'}{y}$$
- Si recalculamos estos parametros usando los ultimos resultados, tenemos:
![[Pasted image 20240315095356.png]]
- Como podemos ver, la altura final del radio también depende del ángulo θ de partida, por lo que si varios radios comienzan desde el punto P en el plano π cada uno con un ángulo θ de partida diferente, entonces en el plano π tenemos varias réplicas del mismo punto.


### Imagen
La imagen es aquella transformación mediante la cual
1. Todos los rayos que parten del punto $P$ en el plano $\pi$ deben converger en el mismo punto $P'$ en el plano $\pi'$ independientemente del ángulo de partida $\theta$, 
2. Esta transformación debe aplicarse de la misma manera para todos los rayos independientemente de la altura de partida, es decir, el aumento transversal $M$ debe ser igual para todos los rayos.
![[Pasted image 20240314175355.png]]

### Sistema ortoscopico
Un sistema óptico que garantiza la transformación de imagen para todos los puntos del plano objeto se llama ortoscópico.
- Este sistema transforma figuras planas en el plano objeto en figuras planas en el plano imagen. *En este caso, los dos planos se llaman conjugados*.

**Condicion de ortoscopia**
- Para que un sistema óptico sea ortoscópico, la matriz $Q$ debe cumplir ciertas condiciones. 
- Queremos determinar la condición sobre la matriz $Q$ para que el sistema sea ortoscópico, es decir, las condiciones bajo las cuales el sistema tenga planos conjugados y garantice la transformación de imagen.

Para que esto ocurra necesitamos que $M=\frac{y'}{y}=const$ $\forall \theta$  
- Usando la ecuacion ya obtenida anteriormente para el aumento:$$y'=y(A+C\cdot d_2)+\theta[B+A\cdot d_1 + d_2(D+C\cdot d_1)]$$
- Por lo tanto necesitamos que el segundo termino que depende de $\theta$ sea igual a cero:$$B+A\cdot d_1 + d_2(D+C\cdot d_1)=0$$
- Por lo tanto:$$M=A+C\cdot d_2$$
- Remplazando los resultados obtenidos en la matriz de transformacion ya obtenida anteriormente $Q$, nos queda que:
![[Pasted image 20240315102855.png]]
![[Pasted image 20240315102904.png]]
- Haciendo aplicar la condicion del determinante igual a 1, leggamos a que $D+C\cdot d_1=\frac{1}{M}$
- Por lo cual la matriz de transformacion Q, para que el sistema se ortoscopico es:
![[Pasted image 20240315103049.png]]

### Elementos “cardinali” de una lente
En una lente se identifican planos y puntos particulares caracterizados por propiedades específicas:
- Planos y puntos principales.
- Planos y puntos focales.

Estos planos y puntos son notables porque poseen propiedades importantes específicas.

#### Principales
##### Planos principales de una lente
![[Pasted image 20240314180554.png]]
Los planos principales de una lente son la pareja de planos objeto-imagen entre los cuales existe un *coeficiente de transformación transversal unitario*.
##### Puntos principales de una lente
![[Pasted image 20240314180718.png]]
Los puntos principales de la lente son las intersecciones de los planos principales con el eje óptico de la lente.


#### Foco posterior
![[Pasted image 20240314180902.png]]
Es el punto $F'$ en el eje óptico donde *convergen los rayos de un haz con eje paralelo* al eje óptico incidente en la superficie anterior del sistema. 
- Dado que el punto $F'$ yace en el eje óptico, el factor de aumento transversal es nulo.

##### Plano focal posterior
El plano focal posterior es el plano perpendicular al eje óptico y que pasa por el punto focal posterior $F'$.

##### Longitud focal posterior
Se definen:
- $l_f'$: Longitud focal posterio → es la distancia focal posterior y corresponde a la distancia entre el plano imagen principal y el plano focal posterior.
- $f'$: Longitud focal efectiva posterior → es la distancia entre el plano focal posterior y el plano tangente al borde de la lente posteriormente.

La lente es recíproca porque al colocar rayos divergentes desde $F'$, obtenemos rayos paralelos en la región anterior a la lente.


##### Distancia focal posterior efectiva
La "focale efectiva posterior" es la transformación de los rayos que convergen en $F'$ caracterizada por un aumento transversal nulo ($y' = 0$). Dado que en $F'$ tenemos $y' = 0$, entonces también el factor de aumento transversal $M$ es nulo, de donde podemos deducir la distancia $d_2$, es decir, la longitud focal efectiva posterior.

![[Pasted image 20240314181344.png]]

$$f'=x_F'-x_2=-\frac{A}{C}$$

El signo de $f'$ depende del signo de los coeficientes $A$ y $C$:
- $f' > 0$: $F'$ está a la derecha de la superficie posterior de la lente (lente positiva o convergente).
- $f' < 0$: $F'$ está a la izquierda de la superficie posterior de la lente (lente negativa o divergente).

Entonces, el punto $F'$ puede estar fuera o dentro de la lente. Su posición depende del valor de los coeficientes de Gauss $A$ y $C$ de la lente.
![[Pasted image 20240314181525.png]]


#### Foco anterior
Se define como "foco anterior" al punto $F$ en el eje óptico donde *convergen los rayos paralelos* de un haz con eje paralelo al eje óptico *incidente en la superficie posterior* del sistema óptico.


![[Pasted image 20240314181722.png]]


#### Plano focal anterior
El plano focal anterior es el plano perpendicular al eje que pasa por el foco anterior $F$.

#### Longitudes focales anteriores
- $l_f'$: distancia focal anterior -> distancia del plano focal desde el plano principal objeto
- $f$: longitud focal efectiva anterior

La lente es recíproca porque los rayos divergentes desde $F$ salen de la lente como rayos paralelos.

#### Foco efectivo anterior
![[Pasted image 20240314182108.png]]
La "focale efectiva anterior" es la transformación de los rayos que convergen en $F$ caracterizada por un aumento transversal infinito ($y = 0$). Dado que en $F$ tenemos $y = 0$, entonces el factor de aumento transversal $M$ es infinito, de donde podemos deducir la distancia $d_1$, es decir, la longitud focal efectiva anterior.

El signo de $f$ depende del signo de los coeficientes $C$ y $D$:
- $f > 0$: $F$ está a la izquierda de la superficie anterior de la lente (lente positiva o convergente).
- $f < 0$: $F$ está a la derecha de la superficie anterior de la lente (lente negativa o divergente).

Entonces, el punto $F$ puede estar fuera o dentro de la lente. Su posición depende del valor de los coeficientes de Gauss $D$ y $C$ de la lente.

![[Pasted image 20240314182257.png]]


## Ejercicio(Hacer)
![[Pasted image 20240314182339.png]]
![[Pasted image 20240314182350.png]]
![[Pasted image 20240314182358.png]]
![[Pasted image 20240314182406.png]]







## Conceptos adicionales
### Definición de objetivo:
![[Pasted image 20240322102134.png]]
- El objetivo de una cámara fotográfica, o "óptica", tiene la función de *proyectar la imagen* que se está fotografiando en el plano focal, donde se encuentra el film en la fotografía analógica y el sensor en la fotografía digital. 
- El objetivo fotográfico está compuesto por una o más lentes y/o espejos.
- Los objetivos de lentes pueden concentrar la luz en el plano focal, reduciendo las deformaciones de una imagen dada. 

### Distancia focal
- Si consideramos los objetivos fotográficos como una lente normal, podemos definir la distancia focal como la medida, generalmente expresada en milímetros, que separa la lente del plano focal.
- Los objetivos fotográficos están compuestos por múltiples grupos de lentes, por lo que esta distancia se puede medir en varios puntos. 
- Una medida típica es desde el centro óptico del objetivo, que suele coincidir con el diafragma.


### Luminosidad
- La longitud focal está relacionada con la "luminosidad" de un objetivo fotográfico. La luminosidad depende de dos factores: 
	- El diámetro de la lente frontal
	- La longitud focal.

**La luminosidad es la relación entre la longitud focal y el diámetro del objetivo.**

El paso de la luz depende del diámetro del "agujero" a través del cual pasa la luz y la longitud del "tubo" a través del cual debe pasar la luz.

Por ejemplo, si usamos dos tubos de 100 milímetros de diámetro con diferentes longitudes, uno de 100 mm y otro de 200 mm, el primero dejará pasar el doble de luz que el segundo.

## Lente delgada
![[Pasted image 20240322103221.png]]
Se define como lente delgada cuando la distancia entre la lenti y el borde es insignificante.
- En estos casos el foco y el foco efectivo coinciden

### Matriz ingreso salida de una lenta delgada
- Se analiza el caso de la matriz comun $S_0$ pero con un limite en el infinito
	- Con este analisis matematico podemos demostrar que longitud focal y la focal efectiva coinciden
![[Pasted image 20240322103305.png]]

- En base a la definicion del factor de Gauss C tambien podesmos poner
![[Pasted image 20240322103624.png]]

### Lente delgada positiva y negativa
Dado que los índices de refracción "n" son siempre mayores que 0, son los valores de los radios de curvatura los que determinan si la distancia focal efectiva es mayor o menor que 0.
En particular:
- Si $f > 0$, entonces la lente se define como positiva;
- Si $f < 0$, entonces la lente se define como negativa.

### Formacion de la imagen en una lente delgada
Ahora queremos determinar mediante un procedimiento gráfico cómo un objeto atraviesa el sistema óptico y cómo su imagen resulta agrandada o reducida. *El método implica el uso solo del trazado de líneas y puntos*. Utilizando el plano anterior de la lente como origen del sistema, se distinguen 3 casos:

1. El punto $Q$ donde se encuentra el objeto está a una distancia $s_0$ tal que: $0 < s_0 < f$;
2. El punto $Q$ donde se encuentra el objeto está a una distancia $s_0$ tal que: $f < s_0 < 2f$;
3. El punto $Q$ donde se encuentra el objeto está a una distancia $s_0$ tal que: $s_0 > 2f$;


Nota: Estamos utilizando la definición de "foco" de la lente (aplicable tanto al foco anterior como al posterior), es decir, estamos utilizando un rayo paralelo al eje óptico que, tan pronto como alcanza el punto A' de la lente delgada, se "curva" hacia el punto focal posterior F'. La construcción del punto A sigue el mismo razonamiento, pero como si el rayo partiera de F para convertirse en un rayo paralelo al eje óptico después de atravesar el sistema óptico.

#### So < f
![[Pasted image 20240322110221.png]]
Desde la cima T del objeto, trazamos dos rayos:
- Uno paralelo al eje óptico.
- Uno que pasa por el foco posterior de la lente.
Luego, identificamos las intersecciones con el plano de la lente A y A’
![[Pasted image 20240322110354.png]]

Para el punto A, trazamos una línea paralela al eje óptico.
Luego, trazamos la línea que pasa por los puntos A' y F'.
La intersección de estas dos líneas proporciona la imagen T' de la cima del objeto.
La imagen del pie del objeto se encontrará en el eje óptico en correspondencia con T'.
Por lo tanto $M=\frac{y'}{y}>1$
**La imagen virtual es agrandada**


#### f<S0<2f
![[Pasted image 20240322110602.png]]
- Aplicando el metodo nos datmos cuenta que la imagen es real, invertida e agrandada

![[Pasted image 20240322110744.png]]

#### S0=2f
![[Pasted image 20240322110813.png]]

#### S0>2f
![[Pasted image 20240322110941.png]]

### Obtencion de la ecuacion de la lente delgada con geometrica
1. ![[Pasted image 20240322111244.png]]

2. ![[Pasted image 20240322111300.png]]

3. ![[Pasted image 20240322111406.png]]
#### Ecuacion de Newton
- De la segunda parte de ambas escuacion de puede obtener
![[Pasted image 20240322111501.png]]
- Lo que nos da la *ecuacion de la lenta delgada en forma de Newton*
$$z_0z_i=f^2$$

#### Ecuacion de Gauss
- Ahora de la primera parte de ambas ecuacion se puede obtener
![[Pasted image 20240322111643.png]]
- Sabiendo que $z_i=s_i-f$  podemos llegar a la *ecuacion de la lente delgada en forma de Gauss*
$$\frac{1}{s_0}+\frac{1}{s_i}=\frac{1}{f}$$


### Sistema generico de lentes
Dado un sistema genérico de lentes, cada lente tendrá su propia matriz $S_0$ (en este caso, $S_1$ y $S_2$), y a cada intervalo espacial se le asociará una matriz de transmisión $T$ (en este caso, de medio 1 a medio 2, por lo tanto, $T_{12}$). Realizando los productos apropiados, obtenemos la matriz total del sistema óptico. Dado que cada lente tiene su distancia focal, en las matrices aparece el factor f1 (y f2), que es el recíproco del factor de Gauss C.

## Ejercicio(Hacer)
![[Pasted image 20240322112257.png]]
![[Pasted image 20240322112305.png]]
![[Pasted image 20240322112316.png]]

## Otros parametros que caracterizan un sistema optico
### Apertura numeri NA
El primer parámetro es la apertura numérica. Está relacionado con la cantidad de luz que el sistema óptico puede aceptar. Es un parámetro adimensional relacionado con el ángulo máximo (llamado ángulo de aceptación) en el cual un rayo de luz llega al foco. Otro parámetro es el número f o "relación focal". Es la relación entre la distancia focal y el diámetro de la lente. Solo los rayos que cumplen muy bien las condiciones de paraxialidad serán aceptados. La luminosidad del sistema puede ser alta o baja y podemos entenderlo rápidamente por el número f.

### Diafragma
Para regular la luz que puede ser aceptada por el sistema óptico, se utiliza un diafragma. El diafragma es un objeto colocado frente a la primera lente y es ajustable en apertura. Es un sistema que deriva del ojo humano.

### Profundidad de campo
Veamos la "profundidad de campo". En fotografía, debemos representar objetos que no son unidimensionales. En la realidad, los objetos están distribuidos, por lo que solo una parte de ellos se encuentra en el plano focal, el resto está fuera del plano focal, es decir, "fuera de foco" o simplemente "desenfocado". La profundidad de campo representa el área alrededor del foco en la cual el objeto se considera "en foco" o, en una palabra, "nítido". Esta descripción no es completamente científica. Depende de persona a persona. Aproximadamente, para la mayoría de las personas, se puede considerar buena. La profundidad de campo es una estimación máxima de dónde debe estar un objeto para considerarse en gran parte enfocado. Es la experiencia del fotógrafo la que hace que toda la imagen parezca lo más nítida posible. La transición de la nitidez al desenfoque no es brusca sino gradual.

La profundidad de campo depende de cómo se enfoque el objeto distribuido. Cuanto más grande sea la lente, más rayos se pueden usar para reconstruir el objeto. Entonces, ¿cómo podemos cambiar la nitidez? Cambiando la relación focal. Esto se hace cambiando la cantidad de luz que entra en la lente, es decir, aumentando el número f mediante un diafragma. Al disminuir el diámetro de la lente, aumentamos la relación focal y, por lo tanto, aumenta la profundidad de campo. Sin embargo, al disminuir el diámetro, también disminuye la luminosidad.

¿Cuál es la solución entonces? En general, la solución está en el medio, por lo que se debe buscar el equilibrio adecuado. Sin embargo, hay un límite en la aplicación del diafragma. En particular, el diafragma limita la cantidad de luz que entra en el sistema. Cuando el diámetro del diafragma es de alrededor de 1 mm, comienzan a ser evidentes los fenómenos de difracción que gradúan las imágenes.
### Aberraciones opticas
Las aberraciones ópticas son manifestaciones que ocurren cuando el sistema no es perfectamente ortoscópico, es decir, la imagen no tiene una correspondencia unívoca con el objeto fuente. Las aberraciones son: Cromáticas; Esféricas; Coma; Curvatura del plano focal; Distorsión; Los rayos que salen de un punto en el espacio objeto ya no convergen en un solo punto del plano imagen.
#### Cromatica
![[Pasted image 20240410200217.png]]
La aberración más común es la cromática. Como el vidrio es un medio dispersivo de cualquier manera (incluso ligeramente), si tomamos un haz de rayos paralelos provenientes desde la izquierda hacia el sistema, al atravesar la lente, por delgada que sea, aún habrá un fenómeno de dispersión de la luz. Las componentes de la luz se descompondrán en rayos con diferentes inclinaciones y dependientes de la ley de Snell. Todas las componentes que componen el espectro luminoso tendrán cada una un punto de convergencia (un foco) diferente. El foco siempre está en el eje óptico, pero a una distancia diferente entre sí.

¿Cómo se compensa? Se introduce una segunda lente que pueda compensar este efecto. Es una lente divergente primero cóncava y luego plana. Se llama lente Crown. Son muy utilizadas en lentes ópticas. Su composición también incluye calcio y sílice. Tiene un índice de refracción de aproximadamente 1.52.

Las lentes Flint son una corona pero con un dopante. El dopante utilizado depende del propósito de la lente.

#### Esferica
![[Pasted image 20240410200243.png]]
Vamos a ver ahora la aberración esférica. Esta aberración ocurre en lentes curvas. Los rayos que inciden más cerca del centro de la lente intersectan el eje en puntos más alejados de la superficie posterior (aberración esférica negativa). Los rayos marginales, por otro lado, inciden en puntos más cercanos a la superficie posterior (aberración esférica positiva).
La aberración esférica se puede minimizar:
- Utilizando superficies asféricas (proceso costoso)
- Utilizando sistemas de lentes esféricas con aberración de signo opuesto
- Aumentando la relación focal con un diafragma (es decir, disminuyendo el diámetro útil de la lente)
Para reducir este efecto, una solución inicial es reducir el diafragma. Otra solución es usar "lentes asféricas", es decir, lentes en las que el radio de curvatura es variable. Estas lentes están diseñadas para que todos los rayos converjan en un solo punto, conjugado con respecto al punto antes de la lente.
El problema de esta última solución es que es más costosa.

#### Coma
![[Pasted image 20240410200300.png]]
El coma se presenta cuando un haz de rayos paralelos incide en la superficie frontal de la lente con el eje no alineado al de la lente (tilt angular). La aberración de coma se debe a los rayos que inciden tan oblicuamente que ya no se puede considerar válida la condición de parassialità y, por lo tanto, el sistema ya no es ortoscópico.

Con una gran apertura numérica (un sistema muy luminoso porque acepta muchos rayos), los rayos laterales intervienen como un haz de rayos paralelos y oblicuos con un ángulo θ respecto al eje óptico y dan origen a un fenómeno de "coma" en el que la imagen se distribuye en el plano focal en lugar de en un único punto. En particular, los rayos laterales serán más periféricos y, por lo tanto, más cercanos al foco del sistema porque compensan la inclinación de los rayos incidentes, mientras que aquellos que inciden más centralmente lo hacen más "en línea recta" y, por lo tanto, estarán más lejos del foco de la lente. Por lo tanto, se obtiene una distribución de la imagen que ya no es distinguible.

El coma es una aberración muy difícil de limitar. Por lo general, se limitan los rayos periféricos que intervienen en la luminosidad del sistema óptico.

#### Curvatura
![[Pasted image 20240410200310.png]]
Cuando el haz incidente tiene una gran apertura angular, el lugar geométrico de los puntos de convergencia de los rayos salientes de la lente es una superficie esférica. En la aberración de curvatura del plano focal, consideramos una apertura angular elevada. Los puntos de convergencia de los rayos salientes de la lente forman una superficie esférica. Tenemos focos, pero distribuidos en un arco de circunferencia.


### Distorsion
![[Pasted image 20240410200317.png]]
Los rayos que inciden en diferentes puntos de la lente son transformados con diferentes ratios de magnificación \( M \). Las imágenes resultantes están distorsionadas de varias maneras:

- En forma de barril (botte).
- En forma de cojín (cuscino).
- Con aberración en forma de bigote (baffo).

Para resolver este problema, se utiliza un diafragma que pueda reducir al máximo dicha aberración.

# Completar de pagina 239 a 257 de mario
# Cosas a memorizar
- Que es un sistema optoico estigmatico
- Que es un sistema ortoscopico
	- Obtencion de condicion de ortoscopia
- Que es la imagen
- Cuando un punto es conjugado
- Cuando un plano es conjugado
- Que es un superficie optica
- Raggi parassiali
- Obtencion de la matriz de refraccion para las distintas superficies
- Obtencion de la matriz de trasmision
- Estudio matriz de reflexion