
## Compensadores
Se puede colocar compensadores en serie o en paralelo a la planta, los llamados en paralalo basicamente realimentan la planta. Los compensadores en serie son mas sencillos que los en paralelo pero tienen mas componentes fisicas
- Si aplicamos una entrada sinusoidal a la entrada de la red y a la salida tiene un adelanto de fase, se denomina *Red de adelanto*
- En el caso que esta salida tenga un retardo de fase, se denomina *Red de retardo*
- Hay redes que son de *Adelanto-Retardo*, estas producen un retardo a bajas frecuencias y un adelanto a altas frecuencias
#### Efectos de la adicion de polos
La adicion de un polo a lla funcion de transferencia en lazo abierto tiene el efecto de desplazar el lugar geometrico a la derecha, lo cual tiende a disminuir la estabilidad relativa del sistema y el tiempo de asentamiento de la respuesta
#### Efectos de la adicion de ceros
La adicion de un cero a la funcion de transferencia en lazo abierto tiene el efecto de desplazar el lugar hacia la izquierda, lo cual tiende a hacer el sistema mas estable y se acelera el tiempo de asentamiento de la respuesta
![[Pasted image 20221122112612.png]]

Se presentara el disenio por 2 metodos:
- Mediante Bode
- Mediante lugar geometrico de las raices
En cada metodo hay que volcar en distintas variables las especificaciones, en bode deberiamos volcarlo en especificaciones de frecuencias.


# Disenio con lugar geometrico de las raices

El disenio mendiante el lugar geometrico de las raices se basa en aniadir polos y ceros a la funcion de transferencia en lazo abierto del sistema y hacer que el lugar de la raices pase por los polos en lazo cerrado deseados en el plano s. Cuando se disenia un sistema de control si se requiere un ajuste de la ganancia, o de cualquier parametro, se debe modificar los lugar de las raices originales, introduciendo un compensador adecuado

## Compesacion de adelanto
Son redes con caracteristicas de una red de adelanto.
El principal problema a la hora de hacer una compensacion de adelanto, se convierte en hacer una elecccion juiciosa de los polos y ceros del compensador Gc(s) para tener los polos en lazo cerrado dominantes en la posiciones deseadas en el plano s de forma que se cumplan las especificaciones de comportamiento
#### Procedimiento para diseniar un compensador de adelanto
1. Localizacion deseada para los polos dominantes en lazo cerrado.
2. Compruebo si el ajuste de la ganancia puede o no por si solo proporcionar los polos en lazo cerrado adecuados
3. Si no basta con la ganancia, se calcula la deficiencia del angulo $\phi$. Este angulo debe ser la contribucion del compensador de adelanto si el nuevo lugar de las raices va a psar por las localizaciones deseadas para los polos dominantes en lazo cerrado.
4. Supongo Gc(s) $$Gc(s)=Kc.\alpha.\frac{Ts+1}{\alpha.Ts+1}$$
	- $\alpha$ y T Se determinan a partir de la deficiencia del angulo
	- Kc se determina a partir del requisito de ganancia en lazo abierto
5. Determino la localizacion del polo y cero del compansador para cumplir las especificaciones dadas
6. Si no tengo un error dado, hago $\alpha$ lo mas grande posible
7. Determino Kc a partir de los requisitos de magnitud
Si se requiere una constante de error estatico grande, se debe introducir en cascada una red de retardo o convertir el compensador de adelanto en un compensador de retardo-adelanto
## Compensacion de retardo
Usamos el compensador de atraso cuando tenemos un sistema con una respuesta transitoria deseada pero una respuesta en estado estacionario insastifactoria. En este caso la compensacion consiste en incrementar la ganancia en lazo cerrado sin modificar de forma notable las caracteristicas de la respuesta transitoria. Para lograr ello necesitamos que *La contribucion de angulo de la red de retardo debe tener un valor pequenio*, para asegurar esto, se situan el polo y el cero de la red de retardo relativamente cerca uno del otro y cerca del origen del plano s.
- *Comunmente la ganancia del compensador sera aproximadamente 1*
- La compensacion de retardo nos permite modificar el valor del error estatico de velocidad casi de manera lineal ya que: $$Kv'=\lim s.Gc(s).G(s)=Kc.\beta.Kv$$
	- Podemos ver que incrementa en un factor de $Kc.\beta$ donde Kc=1
- El efecto negativo de la compensacion de retardo es que al aniadir un polo cerca del origen, obtenemos una respuesta transitoria mas larga
#### Procedimiento para diseniar un comperador de retardo
1. Dibujo lugar geometrico sin compensador
2. Supongo: $$Gc(s)=Kc.\beta.\frac{Ts+1}{\beta.Ts+1}$$
3. Calculo el error estatico especificado en el problema
4. Determino el incremento necesario de la constante de error para sastifacer las especificaciones
5. Determino el polo y el cero del compensador de retardo que producen el incremento necesario e n la constante de error estatico sin modificar apreciablemente los lugares de las raices originales
6. Dibujo el viejo y el nuevo lugar geometrico de las raices y localizo los polos dominantes que necesito
7. Ajusto la ganancia de Kc a partir de la condicion de magnitud, para que los polos dominantes en lazo cerrado se encuentren en la localizacion deseada


# Disenio por el metodo de la respuesta en frecuencia
#### Espeficifaciones en frecuencia
**Error:** Pendiente en baja frecuencia y la constante de bode Kb.
**Velocidad:** Corte de ganancia unitaria wcg. Esta guarda una relacion con el tiempo de subida(tr.wcg=2,1)
**Estabilidad:** Margen de fase y margen de ganancia
Despues del disenio con la respues en frecuencia hay que calcular los polos y ceros de lazo cerrado y ver si verifica el transitorio requerido. El diagrama de frecuencia indica claramente la forma en la que debe modificarse el sistema, aunque no sea posible hacer una prediccion cuantitatia exacta de estas. Una ventaja de usar este metodo es cuando tenemos ruido de alta frecuencia. 
Hay 2 disenios con frecuencia, con bode o con diagrama polar. El segundo es muy complicado y lleva mas trabajo, por lo que usaremos el primero. Para este enfoque comunmente se varia primero la ganancia de lazo abiero, si con esto no sastifacemos las especificaciones de margen de fase y margen de ganancia, se determina un compensador adecuado.
#### Observaciones 
- La region de *bajas frecuencia* indica el comportamiento en *estado estacionario* de lazo cerrado
- La region de *frecuencia medias*(cerca a -1+0j) muestran la *estabilidad relativa*
- Y la regiones de *alta frecuencia*, informa sobre la *complejidad* del sistema
#### Requisitos sobre la respuesta en frecuencia en lazo abierto
Para obtener un valor alto de la constante de error de velocidad, y todavia tener una estabilidad relativa sastifactoria, es necesario volver a dar forma a la curva de respues en frecuencia en lazo abierto. La ganancia en la region de bajas frecuencia debe ser suficientemente grande, y, cerca de la frecuencia de cruce de ganancia unitario, la pendiente de la curva de magnitud logaritmica en el frigama de bode debe ser de -20dB/decada. Para la region de altas frecuencia, la ganancia debe atenuarse lo mas rapido posible a fin de reducir los efectos del ruido.
#### Caracteristicas basicas de la compensacion de adelanto y retado
La compensacion de adelanto produce, esencialmente, una mejora apreciable en la respuesta transitoria y un cambio pequenio en la precision en estado estacionario. Puede incrementar los efectos del fuido de alta frecuencia. La compensacion de retardo, produce una mejora notable de la precision a costa de aumentar el tiempo de respuesta transitoria. Suprime los efectos de las seniales de ruido de alta frecuencia
## Compensacion de adelanto
Se lo usa cuando tenemos problema en la velocida y estabilidad del sistema
Suponemos un compensador de la forma:$$Gc(s)=Kc.\alpha.\frac{Ts+1}{\alpha.Ts+1}$$
Tiene cero en $s=-1/T$ y polo en $s=-1/\alpha.T$. El valor minimo de alfa esta limitado por la contruccion fisica del compensador de adelanto, normalmente el minomo es alrededor de 0,05. La fase maxima que puede producir el compensador de adelanto es de 65 grados.![[Pasted image 20221128190501.png|350]]
- El compensador de adelanto se comporta como un filtro pasa alto.
- La funcion principal del compensador de adelanto es proporcinoar un angulo de adelanto de fase suficiente para compensar el excesivo retardo de fase asociado con las componentes del sistema fijo.
- *La efectividad de la accion compensadora se produce debido a su atraso y no a su ganancia*
#### Procedimiento de disenio
1. Supongo un compensador como dijimos mas arriba y definimos $K=Kc.\alpha$ y $G1(s)=K.G(s)$ , entonces la funcion de transferencia de lazo abierto del sistema con compensador queda como:$$Gc(s).G(s)=\frac{T.s+1}{\alpha.T.s+1}.G1(s)$$
2. Dibujo el bode de G1(s) y calculo su margen de fase, y, en base a este diagrama calculo el adelanto de fase necesario que se aniada al sistema, al calculado le sumo 5 a 12 grados.
3. Determino $\alpha$ con la ecuacion $$sen(\phi max)=\frac{1-\alpha}{1+\alpha}$$ Determino la frecuencia a la cual G1(s) es igual a $-20log(1/\sqrt{\alpha})$ , esta sera la nueva frecuencia de cruce de ganancia unitaria $wn=1/(\sqrt{\alpha}.T)$ y en esta frecuencia ocurre el cambio de fase maximo
4. Frecuencia del polo y cero : $wp=1/\alpha.T$ y $wz=1/T$
5. Calculo Kc como $Kc=K/\alpha$
6. Verifico el margen de ganancia 

## Compensacion de retardo
Se lo usa cuando tenemos problemas con la *exactitud*
Supongo $$Gc(s)=Kc.\beta.\frac{Ts+1}{\beta.Ts+1}$$
Tiene cero en $s=-1/T$ y polos en $s=-1/\beta.T$, las frecuencias esquinas del compensador de retardo son $w=1/T$ y $w=1/(\beta.T)$ 
- El compensador de retardo es esencialmente un filtro pasa bajo
- La funcion principal de este es atenuar en el rango de alta frecuencia a fin de aportar un margen de fase suficiente al sistema
- Se lo debe ubicar en baja frecuencia donde el atraso no complique la estabilidad del sistema a lazo cerrado
- *La efectividad de su accion esta amrcada por la atenuacion que introduce ya que el atraso comunmente es perjudicial*
#### Procedimiento del disenio
1. Se define K y G1 al igual que en el compensador de adelanto, en este caso determinador el K que sastifaga los requesitos sobre la conste de error estatico de velocidad
2. Encuentro la frecuencia a la cual el angulo de fase de la funcion de transferencia en lazo abierto sea igual a -180 + margen de fase requerido(Margen especificado + 5 a 12 grados) y seleccionador esta frecuencia como la nueva frecuencia de cruce de ganancia unitaria.
3. Seleccione la frecuencia de esquina $w=1/T$ entre una octava y una decada por debajo de la nueva frecuencia de cruce de ganancia unitaria. De esta manera el retarod de fase ocurre en la region de bajas frecuencias de manera que no afecta al margen de fase.
4. Determine la atenuacion necesaria para llevar la curva de magnitud a 0dB en la nueva frecuencia de cruce de ganancia unitaria
5. Calculo Kc como $Kc=K/\beta$ 

![[Pasted image 20221130210230.png]]

#### Referencia
- [[Lugar geometrico de las raices]]
- [[Diagrama polares]]
- [[Estabilidad]]