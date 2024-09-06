
## Introduccion
### Concepto de color
- Si yo puedo distinguir el color significa que puedo ver la lungueza de onda
	- Entonces, el rayo no es del color que lo que vemos, lo que verdaderamente sucede es que el color que vemos es una interpretacion de nuestro cerebro de la lungueza de onda
	- Entonces: Nuestro cerebro ve la longitud de onda → La interpreta como color

### Optica geometrica
La optica geometrica es una simplificacion de la ecuaciones de maxwell que siempre deben resolverse in problemas de electromagnetismo, pero no siempre son resolubles.
- Entonces la optica geometrica es una aproximacion usada para resolver la ecuacion de Maxwell que lleva a consideraciones geometrica y nos permite trazar el campo electromagnetico como rayos
- Comumente usamos la onda plana para resolver, pero esto es un aproximaxion

### Rayo optico
- La frecuencia de las ondas visibles son muy pequeñas($10^{-6}-10^{-7}$m)
	- Entonces podemos suponerla como 0 respecto a los objetos donde queremos resolver la ecuaciones de Maxwell. Por ejemplo, la longitud de onda es mucho mas pequeña que que el diametro de una fibra optica
		- Esto nos sirve para hacer un analizis vectoriales y geometrico mas sencillo
- Un rayo optico, es una curva orientada en el espacio, que tralada cierta cantidad de energia electromagnetica a travez de un campo
	- La porpagacion del campo si reduce al estudio de la energia electromagnetica trasmitica en la trayectoria del rayo
	- La propagacion vectorial, se traduciria en una propagacion escalar
- Las ecuaciones que describen la trayectoria del rayo pueden ser obtenidas de las ecuaciones de Maxwell
- De este rayo nos preocuparemos solo del modulo pero no de la fase. Despues de un cierto camino vedremo directamente como es hecho el modulo y la fase 

### Ecuaciones de maxwell
![[Pasted image 20240307095656.png]]


## Optica geometrica
Medio:
- *Lineal:* Cualquier combinacion de causa correponde a una combinacion lineal de efecto con los mismo coeficientes
- *Isotropico:* Presenta propiedades iguales en todas las direcciones respeto a un determinado fenomeno fisico
- *Homogeneo:* Medio donde sus propiedades(electricas, fisicas, quimica, etc) no varian de punto a punto
- *Libre de perdidas:* Es un medio(electromagnetico) es sin perdida cuando la magnitud de interes(campo electromagnetico) no se atenua a lo largo de los caminos del medio

### En condiciones ideales
- Si planteamos las ecuaciones de Maxwell en un medio lineal, isotropico, omogeneo, sin perdida y con parametro $e=n^2e_0$ y $\mu_0$ constantes($e$ depende del indice de refraccion del medio) , la solucion a este problema nos dara una onda plana uniforme: $$E(r)=E_0e^{-iK.r}$$
	- $E_0$ es un vector constante
	- K es un vector real llamado “vector de propagacion”. En un medio isotropico el vector K indica la direccion de las superficies en equilibrio y como fluye la potencia

### Medio no homogeneo
- Ahora si este medio es no homogeneo, nuestro indice de refraccion sera dependiente de la posicion $e(r)=n^2(r)k_0$
	- Al modificar de esta manera nuestras condiciones, no encontramos solucion a la ecuacion de maxwell
	- En la realidad el medio no es homogeneo. Entonces, como hacemos?
*Solucion:*
- En los casos de nuestro interes practico:
	- El medio cambia pero es un cambio muy lento
	- Y el cambio es muy pequeño
	- Los cambios se producen en escalas de longitud mucho mayores que la longitud de onda λ.
- Entonces podemos suponer que nuestra solucion sigue siendo una onda plana uniforme, pero cambia poco.
	- Tambien se elimina la hipotesis de la existencia de planos equifasicos. Pero si los planos aun deben aprecerse a los de las ondas planas, y si la intensidad del campo electromagnetico tambien depende de la posicion “r”, entonces es razonable suponer que la solucion a este problema siempre sea siga siendo una onda plana pero la expresion que la define es diferente.
	- Entonces: $$E(r)=E_0(r)e^{-ik_0L(r)}$$
		- $E_0(r)$ : Vector en funcion del espacio
		- $L(r)$ : Funcion iconica, esta es real, por lo tanto, es un medio sin perdidas
	- Tambien podemos obetener la ecuacion del campo magnetico como:$$H(r)=H_0(r)e^{-ik_0L(r)}$$


#### Verificacion de la solucion con las ecuaciones de maxwell
- Si la expresion obtenida es correcta, debe satisfacer las ecuaciones de Maxwell

**Verificando la primera ecuacion:**
![[Pasted image 20240306180101.png]]

- Podemos ver que la ecuacion obtenida es muy similar a al primera ecuacion de Maxwell solo que tenemos un termino agregado
	- Este termino tiene la funcion iconica L(r), por lo que si el medio seria homogeneo, este termino desapareceria quedando como la original


**Verificando la segunda ecuacion:**
![[Pasted image 20240306180133.png]]
- Podemos ver que la ecuacion obtenida es muy similar a al segunda ecuacion de Maxwell solo que tenemos un termino agregado
	- Este termino tiene la funcion iconica L(r), por lo que si el medio seria homogeneo, este termino desapareceria quedando como la original


**Verificando la tercera ecuacion:**
![[Pasted image 20240306180253.png]]
- En este caso tenemos 2 terminos nuevos, uno que es directamente proporcional a la funcion iconica L(r) y otro que es directamente proporcional a la variacion de la permitividad electrica en el medio, la cual, si tenemos un medio homogeneo, tambien es igual a 0 quedando la ecuacion original


**Verificando la quarta ecuacion:**
![[Pasted image 20240306180406.png]]
- En este caso el termino agregado tambien depende del vecctor iconico


**Ecuaciones de Maxwell e iconicas**
![[Pasted image 20240306180811.png]]
- Donde
	- $k_0=w\cdot\sqrt{\epsilon_0}\cdot\sqrt{\mu_0}$ 
	- $\zeta_0=\frac{\sqrt{\mu_0}}{\sqrt{\epsilon_0}}$   

#### Ecuaciones par longitud de onda pequeña
Vimos que la base de la optica geometrica es la hipotesis que la longitud de onda es mucho mas pequeña que la estructura donde le campo electromagnetico se propaga. Entonces: $\lambda$ → 0
- Por definicion de $k$, si $\lambda$ →0 entonces $k_0$ → +$\infty$    
- Con estas hipotesis, optenemos la siguiente simplificaciones que las ecuaciones de Maxwell-iconicas:
![[Pasted image 20240307120235.png]]
- Para que esto se cumpla se deben cumplir las condiciones de:
	- Variaciones espaciales *finitas* de la magnitud de los campos
	- Varaiciones espaciales *lentas* de las caracteristicas del medio
---
*Mario*
Hemos supuesto que los medios son "lentamente variables" y, por lo tanto, los campos también son "lentamente variables", es decir, no puede haber cambios bruscos en el medio que conduzcan a cambios bruscos en la intensidad de los campos. Por lo tanto, los vectores Eo y Ho son cantidades finitas y, como tales, el rotor y la divergencia de los campos también serán cantidades finitas que dividen una cantidad que tiende a infinito. Por esta razón, los segundos términos de las ecuaciones para longitudes de onda pequeñas son nulos. Se debe prestar atención a la tercera ecuación en la que aparece el gradiente de ε. Pero hemos dicho que el medio cambia sus propiedades lentamente, no presenta cambios bruscos como un delta, por lo que incluso el gradiente de ε (o el índice de refracción) es una cantidad finita que divide k0, que tiende a infinito. Por lo tanto, el segundo término de la tercera ecuación también es nulo.

---
De las ecuaciones obtenidas de Maxwell podemos ver que el vector iconico L es perpendicular a el campo magnetico y al campo magnetico, por lo tanto este vector es el vector propagacion ya conocido(o tiene esta direccion), osea, este vector indica la direccion en la que se propaga la onda plana


### Ecuacion iconica
![[Pasted image 20240307121850.png]]
![[Pasted image 20240307121913.png]]
- En la hipotesis que la lonigtud de onda es mucha mas pequeña que la dimension geometrica analizada, *es necesario que la funcion real L(r) cumpla la ecuacion iconica*
- Tambien $E_0(r)$ y $H_0(r)$ deven sastifacer la ecuacion de transporte

### Ecuacion de trasporte
![[Pasted image 20240307122745.png]]

### Onda plana localmente
- Las ecuaciones de transporte e inconica son obtenida si:
	- $\lambda$→0:Longitud de onda tiende a 0 respecto a nuestro objeto de analisis
	- $\frac{\nabla \epsilon}{\epsilon}$→0  La permitividad electrica del campo varia muy lentamente(esta condicion luego vemos que no es necesaria)
	- Los vectores $E_0(r),H_0(r)$ y $\epsilon(r)$ son lentamente variable
- Entonces, vimos que las ecuaciones dadas inicialmente $E(r)=E_0(r)e^{-ik_0L(r)}$ y $H(r)=H_0(r)e^{-ik_0L(r)}$ son soluciones de la ecuacion y son llamadas **Onda localmente plana**

En resumen, en el caso en que λ sea mucho más pequeña que el sistema bajo análisis, para variaciones lentas del índice de refracción del medio y, por lo tanto, para variaciones lentas de la amplitud de los campos, los campos eléctrico y magnético son campos descritos por ondas localmente planas. Además, el vector de onda k0 que aparecía en las ecuaciones de Maxwell llevaba la información de la dirección de propagación. Ahora esta información es llevada por el gradiente de la función icónica L(r). La terna compuesta por el campo eléctrico, magnético y el gradiente de la función icónica forman una terna de vectores ortogonales entre sí.


### Ecuaciones de Helmholtz
Se puede demostrar que en el caso de la optica geometrica, valen la ecuacion de Helmboltz
![[Pasted image 20240307124819.png]]

![[Pasted image 20240307124803.png]]
### Vector de poityng e iconico
![[Pasted image 20240307125102.png]]
Queda demostrado que el vector de poyting tiene la misma direccion que $\nabla L$, ya que aparece el mismo operador de direccion s. Osea el vector de poyting es paralelo a $\nabla L$ 
Tambien nos queda la solucion para el vector de poyting en la optica geometrica, de donde obtenemos la intensidad de un rayo optico
![[Pasted image 20240307125454.png]]
#### Conservacion de la energia
![[Pasted image 20240307125620.png]]
Es decir, en el supuesto de validez de la óptica geométrica, la potencia se conserva completamente dentro del rayo. No hay fenómenos radiativos. Este fenómeno se conoce como "principio de conservación de la energía para la óptica geométrica".


#### Vector de poynting, iconale y rayo
- El vector $\nabla L$ es perpendicular la superficio $L=cost$.
- El rayo optico son las curva orientadas en el espacio tangente a en cada punto al vector $\nabla L$ y entonces al vector de Poynting S. 
Hemos dicho que las ondas planas son perpendiculares a las superficies equifásicas. Esta consideración también vale para el estudio realizado en el caso de la óptica geométrica. De hecho, en la óptica geométrica, los rayos son aquel conjunto de puntos perpendiculares siempre a las superficies equifásicas. Los rayos ópticos serán, por lo tanto, curvas orientadas en el espacio paralelas al gradiente de la función icónica y, por lo tanto, también al vector de Poynting. En - estos rayos fluye la energía y, como se ha demostrado, sin fenómenos radiativos.
### Rayo y frente de onda
- Para determinar como es hecha la curva en el espacio, es decir como es hecho el rayo, se usa la ecuacion llamada *ecuacion del rayo*
$$\frac{d}{ds}(n\frac{dr}{ds})=\nabla n$$
- En caso de un medio homogeneo($\nabla n=0$) la ecuacion del rayo puede ser facilmente resuelta y mostrar que la trayecyorio del rayo es recta
	- Donde A y B son vectores constantes arbitrarios
![[Pasted image 20240307141414.png]]


- En caso de medio no homogeneo, la trayectoria del rayo es curvilinea y dirije su concavidad hacia las regiones con indice de refraccion mas elevado

### Camino Optico
Se define camino optico como la intergal del indice de refraccion entre 2 puntos del razo: $$[co]_{s0,s1}=\int_{S0}^{S1}n\cdot ds$$
- Reacomodando la ecuacion podemos ver que el camino optico es el producto de la velocidad de la luz en el vacio por el tiempo usado por la luz para cubrir la distancia entre 2 puntos S0 y S1(tiempo de transito). $$[co]_{s0,s1}=c\int_{t0}^{t1}dt$$
- Tambien, desarrolando mantematicamente esta ecuacion, se puede llegar a que el camino optico entre dos frentes de onda es contante(frentes opticamente paralelos).$$[co]_{s0,s1}=\int_{s0}^{s1}dL=L1-L0$$
	- Esto nos dice que la diferencia de la funcion iconale calculada en 2 puntos distintos del camino optico de un rayo es contante.

- De este desarrollo nos podemos dar cuenta que:
	- Los frentes de onda en el medio no homogéneneneo permanecen siempre perpendiculares a los radios mismos, pero dado que los rayos no siguen una trayectoria rectilínea sino curvilínea, entonces las superficies equifase se deforman para permanecer perpendiculares a los rayos, Pero la distancia entre las dos ondas es constante. 
		- Debido a la deformación, los frentes de onda ya no son paralelos entre sí, sino que solo lo son para los rayos, es decir, son "ópticamente paralelos".
	- En un medio homogéneneneo, en cambio, los frentes de onda son efectivamente paralelos entre sí, así como perpendiculares a los rayos.
		- En particular, los rayos se curvan hacia las zonas de índice de refracción mayor. Cuanto mayor es la variación del índice de refracción, más curvan los rayos.s
![[Pasted image 20240312082317.png]]

#### Variacion de la fase del campo a lo largo de un rayo
Sea el vector de campo electro:$E=E_0e^{i\phi}$ con $\phi=-k_0L$ .
- Por lo tanto, entre 2 puntos s1,s0 del rayo la diferencia de fase de la onda asociada es:$$\Delta\phi=-k_0[co]_{s0,s1}$$
- Se define el vector de onda local K, que a diferencia del vector de propagacion k, el primero, indica, localmente, la direccion de propagacion de la onda.$$K=k_0\cdot n \cdot s_{versor}=k_0\nabla L$$



### Ley de la intensidad de la optica geometrica
**Obtencion**
- Si consideramos 2 frente de onda L0 y L1
- Si prendemos 2 secciones $d\Sigma_0$ y $d\Sigma_1$
- Si consideramos el tubo de flujo de rayos que van de la superficie $d\Sigma_0$ a la superficie $d\Sigma_1$ y elegimos las normales saliente p
![[Pasted image 20240307131956.png]]
![[Pasted image 20240307132448.png]]
![[Pasted image 20240307132459.png]]
![[Pasted image 20240307132521.png]]

### Transicion brusca de un medio a otro
- El principio de Fermat es el principio que dice que la luz, o mas generalmente, a radiacion electromagnetica, sigue para alcanza de un punto a otro, un *camino optico estacionario(minimo*)
- El principio de Fermat mostra que tambien en presencia de discontinuidad brusca del indice de refraccion, se verifican las leyes di Snell

#### Ley de snell de reflexion
Las caústicas son puntos donde la óptica geométrica falla. ¿Cómo analizar entonces un punto como este según las hipótesis hechas para la óptica geométrica? Se utiliza un principio, el principio de Fermat, según el cual la luz (o cualquier radiación electromagnética) sigue un camino óptico estacionario (es decir, un mínimo). El principio de Fermat se aplica para obtener las leyes de Snell. Por ejemplo, consideremos un medio homogéneo con una superficie sobre la cual incide un rayo: 
![[Pasted image 20240307134110.png]]
- Observamos en este punto:
![[Pasted image 20240307134112.png]]

En un medio homogéneo, si un rayo incide en una superficie, el ángulo entre el rayo incidente y la superficie es igual al ángulo entre el rayo reflejado y la superficie. Nota: el mismo razonamiento es aplicable con los ángulos entre el rayo incidente y la perpendicular a la superficie y entre el rayo reflejado y la perpendicular a la superficie. La única diferencia es que tendremos la función seno en lugar de la función coseno.


#### Ley de snell de refaccion
Si consideramos 2 medio N1 y N2
![[Pasted image 20240307134521.png]]
- Observamos en este punto:
![[Pasted image 20240307134540.png]]
Entonces, en dos medios con índices de refracción n1 y n2, si un rayo incide en una superficie, el ángulo entre el rayo incidente y la superficie es diferente del ángulo entre el rayo transmitido y la superficie. Lo que este último resultado nos dice es que al variar el ángulo de incidencia en el medio con índice de refracción n2, podemos variar el ángulo de transmisión. Además, existe un ángulo, llamado "ángulo crítico", para el cual no hay rayo transmitido.
Nota: el mismo razonamiento es aplicable con los ángulos entre el rayo incidente y la perpendicular a la superficie y entre el rayo reflejado y la perpendicular a la superficie. La única diferencia es que tendremos la función seno en lugar de la función coseno. 


#### Observaciones
- Hemos entendido entonces que en presencia de una discontinuidad del medio, los rayos no tienen comportamientos extraños, sino que simplemente presentan rayos reflejados o transmitidos. Ahora queremos aplicar la óptica geométrica al caso de las superficies ópticas.
- Tenemos que tener en cuenta que para poder usar la leyes de snell necesitamos que la discontinuidad sea brusca


### Casos donde no se puede utilizar la optica geometrica
#### I fouchi
- Un fuochi es un punto donde la superficie $\Sigma$ tiende a 0
- En este caso no se cumple la optica geometricca ya que tenemos que poder cumplir la ley de la intesidad y si una superficie $\Sigma$ es 0, la intensidad tiene que ser $\infty$ para cumplir esta ley

#### Le caustiche
- Si partimos de la ecuacion de transporte, sacando factor comun el laplaciano del iconico 
- Aqui nos damos cuenta que cuando el lapaciano del iconico es infinito, el campo diverge o es nullo, por lo tanto no puede tomar este valor
	- Pensariamos que esto nunca pasa con las hipotesis de la optica geometrica, pero es incorrecto, esto pasa en las cuspides por ejemplo 
- Esta superficie en la que existe cuspide, se llaman superficie caustica
![[Pasted image 20240307140520.png|200]]
#### Riflexion total
Cuando hay reflexión total en el segundo medio hay una onda plana evanescente (onda no uniforme) con vector de atenuación $alpha_t$ ortogonal a la superficie de separación entre los dos medios y vector de propagación $B$  paralelo a esa

##### Demostracion
![[Pasted image 20240313165351.png]]
- Estas ecuaciones demuestran que la amplitud de la onda reflejada es la misma de la onda incidente
	- La reflexion total de la onda incidente es independiente de la polarizacion
	- La fase del coeficiente de reflexion indica un brusco desfase entre la onda incidente y reflejada
	- **Entonces la Optica geometrica pierde validez**
- Porque la dijimos que la onda es tan pequeña que no deberiamos ver la variacion de fase y en este caso si lo estamos haciendo

##### Efecto Goos-Hánchen
$$r_s=e^{i\sigma_{perpendicular}}$$
$$r_p=-e^{i\sigma_{paralelo}}$$
El desfase puede atribuirse a una traslación lateral del haz reflejado respecto a la del haz incidente.
Es como si la reflexión no se realizara en la interfaz de separación entre los dos medios sino dentro del segundo.
![[Pasted image 20240313170153.png]]