# Propiedades de la red de Petri
La fortaleza del modelado de la PN radica en sus propiedades, las propiedades dependiendo del marcado inicial son llamas _propiedades dinámicas_ y las propiedades independientes del marcado son llamas _estructurales_
## Propiedades Dinámicas o del comportamiento
Estas propiedades dependen del marcador inicial
### Propiedades
#### Alcanzabilidad
Consiste en que cada disparo transición modifica la distribución de los marcadores dentro de la red. Por lo que una secuencia de disparo generara una secuencia de marcadores.

Se dice que un marcador Mn es alcanzable desde el marcador M0 si y solo si existe una secuencia de disparo que transforme M0 en Mn.
La secuencia de disparo se denota con $\sigma$ $$\sigma=M0.t1.M1.t2.M2.t3.M3.....tn.Mn$$
- El conjunto de todos los marcadores posibles a partir de M0 es denotado como R(N,M0)
- El conjunto de todos los disparos desde M0 se denota como L(N,M0) 
- Si Mn es alcanzable desde M0 se denota como$M0[\sigma>Mn$ 

#### Limitada o Acotada
Se dice que una red de Petri esta k-limitada si para todo marcado alcanzable se tiene que ningún lugar tiene un numero de marcas mayor que K.
#### Vivacidad
Se dice que una red es viva si no importa cual marcado haya sido alcanzado, siempre será posible una nueva secuencia de disparos y llegar a un nuevo marcado. Que una red sea libre nos asegura una red libre de bloqueos
#### Reversibilidad y estado inicial
Se dice que es reversible si desde cada marcado Mn existente en R(N,M0), Mo es alcanzable desde Mn
#### Cobertura
Se dice que el marcado M es un marcado _cubierto_ si existe un marcado M' dentro de R(N,M0) tal que $M'(p)>=M(p)$ para cada lugar p dentro de la red.
#### Persistencia
Es persistente si para cualquiera de dos transiciones habilitadas, el disparo de una transición no deshabilitara a la otra transición.
#### Distancia sincrónica
Es una métrica asociada al grado de dependencia mutua entre dos eventos en un sistema condición/evento..
![[Pasted image 20230131182802.png]]

### Método de análisis de propiedades dinámicas

Hay 3 métodos para analizar las propiedades dinámicas

#### 1) El árbol de cobertura

Representación grafica de los estados del sistema. Dada una red de Petri, se puede obtener tantos marcadores nuevos como transiciones habilitadas disparadas. Este proceso resulta en la obtención de un árbol de marcados infinitos para una red de Petri no acotada. Para redes acotadas, el árbol de cobertura es llamado árbol de alcanzabilidad

#### 2) Matriz de incidencia

Es una matriz $A^T$ cuya dimensión es n x m, donde n es equivalente al número total de plazas, mientras que m es igual al número de transiciones. La matriz está compuesta por Aij elementos. Cada uno de estos elementos Aij se los calcula como$$Aij=Aij^+-Aij^-$$
Donde $Aij^+$ es igual al peso del arco que entra a la plaza i desde la transición j. En caso de no existir el arco, el valor es 0 y $Aij^-$ es igual al peso del arco que sale de la plaza i y llega a la transición j.

Nosotros armaremos una matriz con los componentes $Aij^+$ y otra con los componentes $Aij^-$ y restamos ambas matrices.

Un estado para una Red Petri representa un cambio en la distribución de los Tokens (ubicados en plazas) como resultado de un disparo o corrida (firing) de una transición. La ecuación general se define como:$$Md=M0+A^T.\sum_{k=1}^{d} Uk$$ para d=1,2,...
Donde :
- Mk equivale al estado que se desea conocer
- M0 estado inicial del sistema
- $A^T$ es la matriz de incidencia
- Uk es un vector que indica las transiciones que permitirán los desplazamientos de Tokens A esta sumatoria de Uk la llamaremos X. Ahora, si igualamos el termino de $A^T.X = 0$ estaremos buscando los vectores X que hacen que nuestro estado sea igual a la inicial, a este X lo llamaremos invariantes T (transiciones que hacen invariantes al estado). De manera análoga podemos conseguir el vector invariante P. Los invariante T y P son útiles para determinar propiedades estructurales de una PN en forma analítica

### 3) Reglas de reducción

Las reglas de reducción permiten convertir sistemas complejos en sistema más simples conservando sus propiedades originales
a)  Fusión de lugares en serie
b)  Fusión de transiciones en serie
c)   Fusión de transiciones paralelas
d)  Fusión de lugares en paralelos
e)  Eliminación de auto bucles en lugares
![[Pasted image 20230131190732.png]]


## Propiedades Estáticas

Las propiedades estáticas que se platean a continuación solo aplican a PN ordinarias y puras. Estas propiedades dependen de las estructuras de la red de Petri

#### Vivacidad Estructural

Es estructuralmente viva si tiene un marcador inicial para N

#### Controlabilidad

Se dice que es completamente controlable si cualquier marcado es alcanzable desde cualquier otro marcado. Para que esto suceda se debe cumplir que: $Rango(A)=m$

Donde m es la cantidad de lugares de la red

#### Limitación o acotado estructural

Es limitada o acotada estructural si para cualquier conjunto de marcados iniciales M0 es limitada

#### Conservabilidad

Es conservativa si existe un entero positivo y(p), para cada lugar p tal que la sumatoria de marca sea constante para cada $M\in R(N,M0)$

#### Repetibilidad

Una PN es repetible si existe un marcado M0 y una secuencia de disparos $\sigma$ desde M0 tal que las transiciones se disparan infinitamente en la secuencia definida por $\sigma$

#### Consistencia

Una PN es consistente si existe un marcado M0 y una secuencia de disparos reversibles $\sigma$ desde M0 hacia M0 tal que cada transición haya sido disparada al menos una vez en $\sigma$
