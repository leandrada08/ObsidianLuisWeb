
## Introducción

Los metales conductores exhiben una característica única en su estructura de bandas de energía: la Banda de Conducción. En esta banda, los electrones pueden moverse libremente, similar a su movimiento dentro del metal. Sin embargo, están restringidos a permanecer dentro del metal para mantener la neutralidad eléctrica.

## Densidad de estados y Funcion de Fermi-Dirac

### Densidad de estados
Aplicando la mecánica cuántica a la Banda de Conducción, las ondas de De Broglie asociadas a los electrones deben cumplir una condición similar a la de los orbitales atómicos: debe caber un número entero de longitudes de onda en la dimensión del metal. La ecuación de Schrödinger, que describe el comportamiento energético de los electrones, se aplica a este modelo para optener la densidad de estados N(E) (numero de estados por electron volt y por metro cubico). $N(E)=\frac{4\pi}{3}(2m)^{3/2}(1,6.10^{-19})^{3/2}E^{1/2}=\gamma E^{1/2}$ 
![[Pasted image 20240515154902.png]]
La pregunta clave es: ¿cómo se ocupan estos estados con electrones?

### Funcion Fermi-Dirac
La respuesta se encuentra en la mecánica estadística, específicamente en la función de Fermi-Dirac, F(E). Esta función proporciona la probabilidad de que un estado cuántico de energía "E" esté ocupado por un electrón. $$f(E)=\frac{1}{e^{\frac{E-E_F}{kT}}+1}$$![[Pasted image 20240515155809.png]]
### Funcion densidad de estados
Número de estados cuánticos disponibles por unidad de energía para los electrones en el material. En otras palabras, es una medida de cuántos estados cuánticos hay disponibles en un rango particular de energías. $\rho(E)=N(E)f(E)$
![[Pasted image 20240515155841.png]]

Para calcular el número de electrones libres por metro cúbico en el metal, es el area bajo la curva ($\rho(E)$) $$n=\int_0^E\rho(E)dE=\frac{2}{3}\gamma E_f^{3/2}$$

## Nivel de Energía de Fermi

Conociendo la densidad y el numero de electrones libre por atomo se puede calcula el nivel de fermi$E_f$: $E_f=(\frac{3n}{2\gamma})^{3/2}$
Este nivel de energía representa la energía máxima que puede tener un electrón a temperatura absoluta cero. A temperaturas más altas, algunos electrones pueden adquirir energías por encima de Ef.

## Función Trabajo

La función trabajo, Ew, es la energía necesaria para extraer un electrón del metal. Está relacionada con el nivel de energía de Fermi y proporciona información sobre la facilidad con que los electrones pueden ser liberados del metal.


# Mecanismo de Conducción Eléctrica en Metales

## Ley de Ohm Macroscópica y Microscópica

La Ley de Ohm, una ley fundamental en la física eléctrica, se puede expresar tanto en términos macroscópicos como microscópicos. La ley macroscópica establece que la corriente (I) es directamente proporcional a la tensión (V) aplicada: I = V/R, donde R es la resistencia.

La ley microscópica, por otro lado, se enfoca en la densidad de corriente (J) y su relación con el campo eléctrico (E): J = σE, donde σ es la conductividad. Aquí, estamos considerando la densidad de corriente en lugar de la corriente total, y el campo eléctrico en lugar de la tensión.

## Mecanismo de Conducción

La conductividad eléctrica de un material depende de su composición. Los metales conductores, como el cobre, la plata y el aluminio, tienen diferentes valores de conductividad. Es importante destacar que la resistividad de estos metales aumenta con la temperatura, lo que se conoce como coeficiente de temperatura positivo (PTC).

## Modelo de Movimiento de Electrones

Los electrones en un metal pueden representarse como una nube en movimiento aleatorio dentro de la estructura cristalina fija de iones positivos. Los electrones chocan contra la red cristalina y recorren un camino promedio llamado camino libre medio (λ). La velocidad promedio entre choques se denomina velocidad de deriva (vd).

La velocidad de deriva se calcula como la distancia promedio recorrida (λ) dividida por el tiempo promedio entre choques (τ): vd = λ/τ.

Cuando se aplica una tensión, se crea un campo eléctrico, lo que genera una fuerza sobre los electrones (F = qE), donde q es la carga del electrón. Esto resulta en un desplazamiento neto en la dirección del campo, opuesto a la fuerza aplicada.

## Movilidad y Linealidad de la Ley de Ohm

La movilidad de los electrones se define como la velocidad de deriva dividida por el campo eléctrico: v = vd/E. La movilidad puede variar con la temperatura y la estructura cristalina del metal.

La linealidad de la Ley de Ohm se refiere a la relación directa entre la tensión aplicada y la corriente resultante. Esta linealidad es una característica fundamental de los metales conductores y es esencial para su uso en circuitos eléctricos y electrónicos.


# Instalaciones
## Conductores

### Cables
Un conductor no es otra cosa que una resistencia de bajo valor, en la realidad los conductores estan constituidos del aislante y del metal
El aislante puede ser:
	PVC
	XLPE
Los conductores pueden ser:
	Cobre(Cu)
	Aluminio(Al)
La resistencia de estos conductores esta dada por la ecuacion: $R=\rho.(l/s)$
Donde l es la longitud, s la seccion transversal y $\rho$ la resistividad del material

|Cobre|Aluminio|
|-------|---------|
|Mayor peso|Menor Peso|
|Menor resistencia|Mayor Resistencia|
Para que tengan la misma resistencias $Sal=1,6.Scu$

|PVC|XLPE|
|-----|-----|
|Tservicio 70C|Tservicio 90C|
|Tcc 160C|Tcc 250C|
|Barato|Caro|
