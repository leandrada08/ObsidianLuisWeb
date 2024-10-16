# Redes de Petri coloreadas

Introducido por Jensen en el año A986. En el modelado mediante redes de Petri regulares, a menudo es necesario tener varios subconjuntos idénticos. Esto se debe a que plegarse en una sola subred destruiría la posibilidad de distinguir diferentes procesos. Por lo tanto, el tamaño de PN se vuelve grande al modelar esos sistemas prácticos. Para superar este problema, los colores se introducen en la PN normal y la PN normal se amplía a la PN coloreada. La PN coloreada es ampliamente utilizada en modelado, análisis, simulación y control. este capítulo presenta CPN y algunos métodos de análisis de CPN.

Básicamente la CPN sirve para modelar procesos en donde hay varias partes o varias máquinas que hacen el mismo trabajo, procesando el mismo o diferente material. Ejemplo: Imaginemos que tenemos 2 plantas(m1,m2) que procesan 2 tipos de materiales(j1,j2). La red de Petri de este sistema seria la siguiente.![[Pasted image 20230202094901.png]]

Ahora, si lo hacemos con redes de Petri coloreada se simplificaría a lo siguiente.

![[Pasted image 20230202094931.png]]

Pero en este caso, para trabajar con redes de Petri debemos definir colores, donde p1 indica que hay una un trabajo en espera, p2 que se está procesando un trabajo en la máquina y p3 indica que hay una maquina disponible. La transición t1 indica que la maquina inicia su proceso de trabajo y t2 que finaliza. Hay 2 tipos de productos posibles en p1, entonces hay que definir 2 colores para esta, lo mismo pasa en p3 donde hay 2 tipos de máquinas, en p2 es más complicado el asunto, ya que tenemos 4 casos, el de cada máquina con cada producto, por lo tanto, son 4 colores y esto mismo ocurre en las transiciones donde es necesario 4 tipos de colores para distinguir cada transición.

## Definición formal de CPN

Un CPN es una six-cupla $$CPN=(P,T,I,O,C,M0)$$

Donde:

- P={p1,p2,...,pm},m>0, es un conjunto finito de lugares

- T={t1,t2,...,tn},n>0, es un conjunto finito de transiciones tales que $PUT\neq \phi$ y $P\bigcap T=\phi$

- C(p) y C(t) son los colores asociados a los lugares p $\in$ P y a la transiciones t $\in$ T$$C(pi)={ai1,ai2,...,aiu}$$$$C(ti)={bj1,bj2,...,bjv}$$

- $I(p,t):C(p)XC(t)=>N$ es la función de entrada donde N={0,1,2,3,...} es el conjunto de enteros no negativos

- $O(p,t):C(p)XC(t)=>N$ es la función de salida

- $M:P=>N$ Es una marca que representa el número de tokens en los lugares

### Reglas de activación y habilitación de transiciones

Se dice que la transición tj $\in$ T está habilitada respecto al color bjk en la marca M si y solo si $$M(pi,aih)>I(pi,tj)(aih,bjk)$$ Para todo $pi \in p$ y $aih \in C(pi)$ 

Cuando una transición está habilitada puede dispararse. Disparar una transición habilitada tj con respecto al color bjk en la M cambia la marca de M a M' de acuerdo con la siguiente ecuación: $$M'(pi,aih)=M(pi,aih)-I(pi,tj)(aih,bjk)+O(pi,tj)(aih,bjk)$$ Para todo $pi \in p$ y $aih \in C(pi)$


## Referencia
- [[Bases de Redes de Petri]]
- [[Clasificaciones de PN]]
- [[Propiedades de la Red de Petri]]