## Introducción a los Semiconductores

Los semiconductores son materiales que presentan una conductividad eléctrica intermedia entre los conductores y los aislantes. 
- Esta propiedad única los hace extremadamente valiosos en una variedad de aplicaciones electrónicas.
- La estructura electrónica de los semiconductores incluye una banda de conducción y una banda de valencia separadas por una banda prohibida. 
- Algunos semiconductores conocidos incluyen el silicio (Si), el germanio (Ge) y el arseniuro de galio (GaAs), cada uno con su respectiva banda prohibida.
**Papel de la temperatura:**
- La temperatura juega un papel crucial en el comportamiento de los semiconductores. 
- A *bajas temperaturas*, los semiconductores se comportan como *aislantes*, con la banda de valencia llena y la banda de conducción vacía.
- A medida que *aumenta la temperatura*, algunos electrones adquieren suficiente energía térmica para saltar a la banda de conducción, convirtiéndose en portadores de carga libres.
- A temperatura ambiente son malos conductores y malos aislantes y su $10^{-3}<\rho<10^5\ohm\cdot cm$  
## Disposición Atómica y Estructura Cristalina

La disposición atómica de un semiconductor puede ser amorfa, policristalina o cristalina:

- Sólido Amorfo: Sin orden a largo alcance en la disposición atómica.
- Sólido Policristalino: Formado por subsecciones cristalinas no homogéneas.
- Sólido Cristalino: Átomos ordenados en un patrón tridimensional definido.

La estructura cristalina influye en el comportamiento eléctrico de los semiconductores.
![[Pasted image 20240515170337.png]]

- La estructura cristalina puede tener diversas fomas(cristobalite, tridimite, quarzo, …)
### Configuración Electrónica y Enlaces Covalentes
![[Uniones quimicas#Enlace Covalente en el Silicio]]

# Semiconductores Intrínsecos
## Introduccion
- En los semiconductores intrínsecos, la estructura cristalina y los enlaces covalentes juegan un papel fundamental. 
- A medida que aumenta la temperatura, se rompen algunos enlaces covalentes, creando electrones libres y huecos.
- La concentración de electrones libres es igual a la concentración de huecos, y este proceso se conoce como generación térmica.
- La concentración intrínseca de portadores de carga depende de la temperatura y la banda prohibida del semiconductor ya que la energia termica kT necesaria para romper un enlance covalente, ha de ser > Eg banda prohibida
![[Pasted image 20240516112316.png]]

### Huecos
Es la vacante dejada en el enlance covalente cuando el electron queda libre
- Esta vacante dejada en el enlace covalente se comporta como si fuese una nueva partícula libre de carga positiva +q (q =1,6 E-19 C) y masa comparable a la del e-.
- Esta partícula aparente recibe el nombre de “hueco” h+ .
- El numero de huecos que aparecen es igual al numero de electrones, pues por cada enlace covalente que se rompe aparece un electrón libre y un hueco. Es decir la concentración de electrones por unidad de volumen es igual a la concentración de huecos por unidad de volumen. $$n=p$$
- Esto es lo que se llama *generacion termica* y genera una *concentracion intriseca* $$n_i=n=p$$

### Recombinación de Electrones y Huecos
- Los electrones libres y los huecos también pueden recombinarse, reduciendo la cantidad de portadores de carga.
- En equilibrio termodinámico, la tasa de generación de pares electrón-hueco es igual a la tasa de recombinación. La concentración intrínseca en función de la temperatura y la banda prohibida se puede expresar mediante una ecuación.

### Generacion de portadores
- Los procesos de generacion termica de pares eletron hueco y de recombinacion de los mismo coexisten. En la situacion de equilibrio termodinamico el numero de generaciones es igual al de recombinaciones.$$n_i^2=A_0T^3e^{-E_{G0}/kT}$$
	- $A_0$ es una constante
	- $n_i$ es la concentracion intrinseca
	- $T$ es la temperatura en grados Kelvin
	- $E_g$ es el ancho de la banda prohibida
	- $k$ es la constante de Boltzman
![[Pasted image 20240516170439.png]]


## Propiedades electronicas de los semiconductores intrisecos
### Banda de energia
![[Pasted image 20240516171008.png]]
### Densidad de estados, funcion de Fermi, energia de Fermi, etc.
**Densidad de estados permitidos en banda de conduccion:**$$N(E)=\gamma(E-E_C)^{1/2}$$
- Con $E>E_C$

**Funcion de Fermi:**$$f(E)=\frac{1}{1+e^{\frac{E-E_F}{kT}}}$$
- Con $E>E_C$

**Concentracion de electrones en la banda de conduccion:**$$n=N_CE^{-\frac{E_C-E_F}{kT}}$$
- Donde $N_C=2(\frac{2\pi m_nkT}{h^2})^{3/2}$ 
- Donde $m_n$ es la masa efectiva

**Concentracion de huecos en la banda de Valencia:**$$p=N_VE^{-\frac{E_F-E_V}{kT}}$$
- Donde $N_C=2(\frac{2\pi m_pkT}{h^2})^{3/2}$ 
- Donde $m_p$ es la masa efectiva
#### Concentracion Intrinseca
1. Como el cristal es electronicamente neutro → $n_i=p_i$
2. Suponemos que las masas efectivas de electrones y huecos son las mismas → $N_C=N_V$ → $E_F=\frac{E_C-E_V}{2}$
3. La concentracion Intrisica es $$np=N_CN_Ve^{-\frac{E_G}{kT}}$$
- Para materiales intrisecos y extrinsecos vale la **LEY DE ACCION DE MASAS:**$$np=n_i^2$$
#### Energia de la Banda Prohibida
- La energia de la Banda prohibida decrece linealmente con la temperatura:$$E_G=E_{G0}-\beta T$$
![[Pasted image 20240516173001.png]]


## Corriente Eléctrica y Conductividad en Semiconductores 
La conducción eléctrica en semiconductores como el silicio y el germanio se debe al movimiento de electrones y huecos. Estos últimos son posiciones vacantes en la banda de valencia donde deberían haber electrones. Ambos, electrones y huecos, contribuyen a la conducción eléctrica dentro del cristal semiconductor. La corriente eléctrica en un semiconductor es el resultado de la influencia de un campo eléctrico aplicado sobre estos portadores de carga. La corriente total es la suma de las contribuciones individuales de electrones y huecos, las cuales dependen de su concentración y movilidad. La conductividad eléctrica está directamente relacionada con estas propiedades.

La principal diferencia con la conducción en un conductor tradicional radica en la densidad de portadores de carga y la influencia de la energía térmica. En un conductor, los electrones abundan y contribuyen significativamente a la corriente. En cambio, en un semiconductor, la densidad de portadores es menor, y la energía térmica juega un papel crucial en su generación. Además, el nivel de conducción en un semiconductor se puede manipular ajustando la concentración de portadores a través del dopado o aplicando un campo eléctrico.

Los huecos, a pesar de ser vacantes, pueden moverse dentro del cristal bajo la influencia de un campo eléctrico. Cuando un electrón deja su posición, creando un hueco, este puede desplazarse a través del cristal. Tanto los electrones como los huecos transportan carga eléctrica, contribuyendo a la conductividad del material. Cuando se aplica un campo eléctrico externo, los huecos, al tener una carga positiva, se mueven en dirección opuesta al campo, siendo atraídos hacia el polo negativo. De esta manera, tanto electrones como huecos responden al campo eléctrico aplicado y contribuyen a la corriente eléctrica, pero en direcciones opuestas."
![[Pasted image 20240516173601.png]]

### Contribucion de electrones a la corriente
**Corriente de electrones:** $$J_N=\frac{Nqv}{lA}$$
- $v:$ velocidad de deriva

### Contribucion de huecos a la corriente
**Corriente de electrones:** $$J_p=pqv=\sigma_pE$$
- $v:$ velocidad de deriva
- p: concentracion de huecos

### Corriente total

**Relaciones importantes:**
- $v=\mu_pE$
**Conductividad:** $$\sigma=n\cdot q \cdot\mu_n$$ 
**Movilidad de electones:** $$\mu=\frac{v}{E}$$
**Corriente total:**
$$J_T=J_N+J_P=qn_i(\mu_n+\mu_p)E=\sigma\cdot E$$

# Semiconductores Extrínsecos

## Introduccion
Los semiconductores extrínsecos, también conocidos como dopados, son materiales modificados para mejorar su flexibilidad y adaptarlos a diversas aplicaciones prácticas. La principal diferencia con los semiconductores intrínsecos es la introducción controlada de átomos de impurezas, lo que resulta en un aumento significativo del número de portadores de carga.

### Dopaje tipo N

En un semiconductor tipo N, se sustituye uno de los átomos de la red cristalina (por ejemplo, silicio) por un átomo con cinco electrones de valencia. Este átomo donador cede uno de sus electrones, que se libera fácilmente a temperatura ambiente, dejando una vacante que puede ser ocupada por otro electrón vecino. Así, se crea un portador adicional y no se genera un hueco, por lo que hay más electrones que huecos. A estos elementos donadores se les llama impurezas donadoras, y hacen que el semiconductor sea de tipo N.
![[Pasted image 20240516181459.png]]
### Dopaje tipo P
En un semiconductor tipo P, se introduce un átomo con tres electrones de valencia. Este átomo aceptor no completa la estructura de enlaces, dejando una vacante que puede ser ocupada por un electrón ligado de un átomo vecino. Esto resulta en la creación de un hueco y un ion positivo fijo. A estos elementos aceptores se les llama impurezas aceptadoras, y hacen que el semiconductor sea de tipo P, ya que conduce principalmente a través de los huecos.
![[Pasted image 20240516181524.png]]


Es importante destacar que, para mantener la neutralidad eléctrica del cristal, debe haber el mismo número de cargas positivas y negativas. Los iones fijos creados por el dopaje no contribuyen a la conducción de corriente eléctrica.

## Propiedades electronicas en semiconductores extrinsecos
### Densidad de carga
Finalmente, es de señalar que cuando el átomo donador o aceptador, cede o admite e-respectivamente queda cargado positiva / negativamente. 
- Sin embargo, el ion correspondiente tiene su estructura de enlaces completa. Es una carga fija que no puede contribuir a la conducción de corriente eléctrica.
- Por otra parte, el cristal es eléctricamente neutro, es decir, debe haber el mismo número de cargas positivas y negativas. $N_{ACEPTADORES}^-+n=N_{DONADORES}^+ + p$ 
- Para un semiconductor tipo n → $n \approx N_D$ → $p=\frac{n_i^2}{N_D}$ 
- Para un semiconductor tipo p → $p\approx N_A$ → $n=\frac{n_i^2}{N_A}$

### Nivel de Fermi
- Para un tipo n →$E_F=E_C - kTln(\frac{N_C}{N_D})$
- Para un tipo p →$E_F=E_V - kTln(\frac{N_V}{N_A})$


### Temperatura intriseca
![[Pasted image 20240516183222.png]]


## Modulación de la Conductividad en Semiconductores

La conductividad de un semiconductor puede ser variada mediante dos métodos principales: modificando la temperatura o irradiando (iluminando) el material. Los termistores son sensores de temperatura semiconductores intrínsecos que funcionan aprovechando la disminución de su resistividad con el aumento de la temperatura, lo que resulta en un coeficiente de temperatura negativo (NTC). Por otro lado, los PTC (coeficiente de temperatura positivo) son semiconductores extrínsecos cuya resistencia aumenta con la temperatura debido a la disminución de la movilidad de los portadores.
### Efecto Hall

El efecto Hall es un fenómeno observado en bloques conductores por los que circula una corriente eléctrica y se aplica un campo magnético. Las cargas en movimiento experimentan una fuerza magnética perpendicular a su velocidad y al campo magnético, creando una separación de cargas y una diferencia de potencial conocida como tensión Hall. Este efecto se utiliza en dispositivos prácticos para medir campos magnéticos y corrientes.

### Fotoconductores

Los fotoconductores son dispositivos que modulan su conductividad mediante la irradiación de luz. El espectro visible ocupa una pequeña porción del espectro electromagnético, generalmente desde 380-400 nm hasta 760-780 nm. La radiación incidente en el semiconductor genera pares electrón-hueco, aumentando la concentración de portadores y, por lo tanto, la conductividad.

### Dependencia de la resistividad con la Temperatura
![[Pasted image 20240516183515.png]]
## Ecuaciones de Variación Temporal y Espacial de la Carga

La variación temporal de la carga en un semiconductor se describe mediante la ecuación:

[dp/dt = g - p/\tau]

donde _g_ es la tasa de generación de huecos por segundo debido a la generación térmica, y _\tau_ es el tiempo de vida medio de los portadores.

La densidad de portadores inyectados o excedentes (_p'_) se define como el exceso de concentración de portadores minoritarios sobre el valor de equilibrio. La velocidad de cambio de esta concentración es proporcional a su valor, y el signo indica si se trata de una disminución (recombinación) o un aumento (recuperación de una disminución temporal).

## Difusión

Cuando existe un gradiente de concentración de portadores en un semiconductor, aparece un movimiento de partículas en sentido contrario al gradiente. Como estas partículas son cargas, se genera una corriente eléctrica. Las constantes de difusión (_D<sub>n</sub>_ y _D<sub>p</sub>_) relacionan el gradiente de concentración con la corriente de difusión. Estas constantes están relacionadas con las movilidades de los portadores a través de la relación de Einstein:

[D = \frac{\mu V_T^2}{q}]

donde _V<sub>T</sub>_ es la velocidad térmica.

## Ecuación de Continuidad

La ecuación de continuidad describe la variación temporal y espacial de la carga en un volumen dado del semiconductor, incluyendo la corriente por campo eléctrico:

$$\frac{\partial \rho}{\partial t} + \nabla \cdot \vec{J} = 0$$

donde _\rho_ es la densidad de carga y _\vec{J}_ es la densidad de corriente.





# Dispositivos semiconductores
### Semiconductores de germanio
- Primer transitor 1947
- El primer transitor era de germanio
	- Este tenia una Eg pequeña(0,66)
		- Esto genera gran corriente inversa
		- Para poder usarlo con buena sensibilidad hace falta que lo usemoa a baja temperatura(<100grados)
	- No es idone para la tecnologia plana(tecnologia planare)
	- La ventaja es que puede ser fabricado con temperatura baja(<1000grados)

### Semiconductores silicio
- Eg mas elevata
- Menor corriente inversa
- Temperatura maxima de operacion mas alta(150 grados)
- Permite tecnologia plana
- Abundacia de materia prima(25,7% della crosta terreste)
	- Es 10 veces mas barato que el germanio
- Actualmente se usa en el 95% del mercado electronico
- Es duro pero tambien es muy fragil
- Es silicio no es naturalmente cristalino, nosotros lo hacemos cristalino para mejorar la movilidad
- Tiene una impureza muy baja, tiene una impureza del 14% aproximadamente
	- Esto no se puede mejorar mas ya que es imposible debido al proceso de fabricacion
		- No se puede generar un vacio absoluto al fabricar
		- Ademas cuando tenemos preciones muy baja debido al vacio, se evapora el metal y genera impuresas
			- Esto se debe que el metal no tiene fuerzas que los mantengan unidos
		- El factor importante es el vacio dentro de la estructura
- Quien produce las fetas de silicio no son los que implementan el circuito
	- Las empresas que hacen los procesador y circuitos compran las fetas
	- Ya que no se pueden permitir frenar el proceso por una mala fabricacion
		- Es por esto que tambien cada empresa de implementacion tiene varias empresas que le dan los lingotes
			- Cuando reciben estos lingotes, analizan caracteristicas como la resistividad longitudinal y transversal para ver si cumple con los requisitos, ya que necesitamos que sea lo mas uniforme posible
- Producir estas fetas, es carisimo
- Las empresas que producen estas fetas tienen su propio sistema de alimentacion para evitar desconexiones y variaciones en esta energia
	- Estas empresas tambien suelen vender 

### Oxido de silicio
**Caracteristicas principales:**
- Optimo “isolante electrico”(banda prohibida “pari a 8eV”)
- Ottimo “passivante nei confronti del silicio”
- Barriera contro le impuritá
- Processi di realizzazione ad elevata controllabilitá
- Los iones presentes de distintos tipos compuesto dentro del oxido, generan que este tenga un histeresis dependiendo de la tension aplicada anteriormente
Tenemos *2 tipos de oxidos*, uno que solo se usa para la fabricacion y no nos sirve para mas que para la implantacion(oxido sacrificado) y otro que se usa de manera funcional
- El *oxido sacrificado*, es un oxido que se usa para la fabricacion para el proceso de la implantacion y no para el funcionamiento, se usa para cascara para la implatancion
	- Que expesor debe tener este oxido? Depende de muchas cosas, por ejemplo durante la implantacion cuando bombadeamos para drogar nuestra placa, esto se puede hacer de varias maneras y tampoco es de intensidad constante  y maxima intensidad sobre la placa
	- Luego de usar este oxido par la implantacion se lo descarta, por eso se llama safricado
	- Esto se hace con un acido super fuerte que se llama BHF que se almacena en una botella de platico
		- El problema de este acido es que ataca a otros compuestos como el silicio
		- El acido es importante cuando es selectivo, para evitar que coma silicio y otros de los compuestos de la placa
	- Por todo lo dicho se usa un ataque de implantacion no tan fuerte para poner un oxido sacrificado no tan grueso
- El *oxido funcional* viene hecho con un proceso llamada oxidacion termica o con CVD
	- Esta tecnica aumenta la oxidacion con la temperatura
	- El CVD se fase con una fase de vapor
		- Con esta tecnica se hace entrar el gas en semiconductor para la oxidacion


### GaAs
- Es muy costoso
	- La materia prima
	- El proceso de fabricacion
- Pero tiene muchas ventajas sobre le silicio
	- Tiene una movilidad mas alta
	- Tiene una concentracion intriseca baja
- Se lo usa principalmente para optoelectronica
- Se usa para aplicaciones de comunicaciones y extratrerestre
- *El factor mas importante de un semiconductor es la movilidad*, porque nos da la corriente y otras caracteristicas muy importantes, por esto, es muy usado este semiconductore

