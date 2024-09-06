

## Sucesion numerica compleja
#### Definicion
Una sucesion nuemrica compleja es una funcion z:N-->C que asigna a cada n perteneciende a los naturales el valor z=z(n) perteneciente a los complejos

#### Convergencia
Se dice que la sucesion compleja{zn} es convergente si existe un numero finito l(l perteneciente a los complejos) tal que: $$\lim_{z->infinito}zn=l$$
- Se puede analizar la convergencia separando la sucesion compleja en 2 sucesiones reales y convergera al valor de estas


## Serie numerica compleja
#### Definicion
Sea una sucesion de numeros complejos {zn}. La suma infinita que denotamos $$\sum_{n=1}^{infinito}zn=z1+z2+z3+...$$
se llama serie de numeros complejos
#### Convergencia
La serie compleja $\sum_{n=1}^{infinito}zn$ Se dice convergente si la sucesion de sumas parciales {Sk} converge, donde Sk=z1+z2+...+zk. Mas precisamente,
Si Sk-->L  cuando K--->infinito, entonces $\sum_{n=1}^{infinito}zn=L$

#### Condicion necesaria de la convergencia de una serie
Si la serie compleja $\sum_{n=1}^{infinito}zn$ converge, entonces $\lim_{z->infinito}zn=0$
Tambien vale el opuesto del complementario

## Sucesion de funciones complejas
#### Definicion
Son funciones complejas que para todo n perteneciente a los naturales, fn: D-->C. A este conjunto de funciones {fn} le llamamos sucesion de funiones

#### Convergencia
La sucesion de funcinoes {fn} converge en el punto zo perteneciante a D si la sucesion numerica {fn(zo)} converge.
- Si queremos analizar la convergencia en un conjunto de puntos hay que usar la definicion con cada punto de ese conjunto

## Serie de funciones complejas
#### Definicion
Sea {fn} una sucesion de funciones complejas(en D). La suma infinita $\sum_{n=1}^{infinito}fn$ se denomina serie de funciones complejas
#### Convergencia  
La serie de funciones $\sum_{n=1}^{infinito}fn(z)$ converge(a una funcion f) en el conjunto D0 contenido en D si la sucesione de funciones {Sn} con $Sn=\sum_{k=1}^{n}fn$ converge en D0.
La sucesion de funcinoes {Sn} se denomina sucesion de sumas parciales


# Series de potencia
#### Definicion
Una serie de funciones de la forma
$$\sum_{n=1}^{infinito}an(z-zo)^n=a0+a1.(z-zo)+a2.(z-zo)^2+...$$
donde a0,a1,... son constantes complejas, sellama serie de potencia de (z-zo).
- La serie de potencias dada por la ecuacion recien vista se dice que esta centada en zo(zo se conoce como el centro de la serie).
#### Circulo de convergencia
El circulo de convergencia de la serie dada por (1.7) es el conjunto de todos los puntos dentro de cierto circulo centrado en z0 y de radio R>0 donde dicha serie es convergente. A R se lo denomina radio de convergencia
$$R=1/L$$
$$L=\lim_{n->infinito}|\frac{\mbox{a}_{n+1}}{\mbox{a}_n}|$$

#### Teorema Continuidad
Una serie de potencias $\sum_{n=1}^{infinito}an(z-zo)^n$ convergente en |z-zo|<R< con R>0 representa una funcion continua dentro de su circulo de convergencia
- Esta se puede derivar dentro del circulo de convergencia dando el resultado $\sum_{n=1}^{infinito}an.n(z-zo)^{n-1}$ 

---
### Obs importante
**Como consecuencia de la formula integral de Cauchy se menciono que una funcion analitica en un punto zo siemre se puede desarrollar en una serie de potencias centrada en ese punto. Esto se logra mediante una particular serie centrada en zo denominada serie de Taylor**

#### Teorema de Taylor
Sea f una funcion compleja de variable compleja, analitica en un dominio D. Entonces, la funcion f tiene la representacion en serie de potencias de la forma
$$f(z)=\sum_{n=1}^{infinito}\frac{f^{(n)}(z)}{n!}(z-zo)^n$$ para |z-zo|<R< contenido en D
Donde zo pertenece a D fijo y R es el radio de convergencia

---
#### Definicion de series de potencia negativas
Una serie de potencias negativas de (z-zo) es de la forma $$\sum_{n=-1}^{-infinito}\mbox{a}_n (z-zo)^n=\frac{\mbox{a}_{-1}}{(z-zo)}+\frac{\mbox{a}_{-2}}{(z-zo)^2}+...$$
Los terminos de esta serie son funciones analiticas en el plano complejo ampliado excepto en z=zo.
La convergencia de este tipo de serie sera en |z-zo|>R(R>0). El numero R se denomina radio de convergencia.
- El radio de convergencia para las series de potencias negativas se calcula de la misma manera que para las series de potencias positivas

### Definicion Series de potencias positivas y negativas  (La parte de parte analitica y principal)
Una serie de potencias positivas y negativas de (z-zo) tiene la forma $$\sum_{n=-\infty}^{\infty}\mbox{a}_n(z-zo)^n$$
Donde la parte de potencias *positiva es la parte analitica* y la parte de potencias *negativas es la parte principal*.$$\sum_{n=-\infty}^{\infty}\mbox{a}_n(z-zo)^n=\sum_{n=0}^{\infty}\mbox{a}_n(z-zo)^n+\sum_{n=-1}^{-\infty}\mbox{a}_n(z-zo)^n$$
Este tipo de serie converge si y solo si las partes analiticas y principal convergen
#### Convergencia de una serie de potencias positivas y negativas
Estas series convergen en un conjunto de punto denominado anillo de convergencia y fiene la forma$$R2<|z-zo|<R1$$
Donde R1 y R2 son los raidos de convergencia de las series positivas t negativas respectivamente. Si la parte analitica converve a f1 y la parte principal a f2 entonecs la serie positiva y negativa converge a f1+f2 en el radio de convergencia.


### Obs importante
*Muchas de las funciones que se utilizan habitualmente no se pueden desarrollar en serie de potencias positivas en las proximidades de determinados puntos, debito a que en esos puntos presentan singularidades. Pero, aun si una funcion no es analitica en un punto puede desarrollarse en serie de potencias. Esto se logra mediante la serie de Laurent, que es un caso particular de series de potencias positivas y negativas*


## Series de Laurent
#### Definicion
Sea una funcion f analitica en un dominio D definido por R2<|z-zo|< R1, (R2< R1). Entonces f tiene la representacion.$$\sum_{n=-\infty}^{\infty}\mbox{A}_n(z-zo)^n(1.12)$$valida para R2< |z-zo| < R1.
Los coeficientes An estan dados por $$An=\frac{1}{2.\pi.i}\int_\gamma \frac{f(z)}{(z-zo)^{n+1}}dz$$
con n=0,+-1,+-2,...
Donde $\gamma$ es cualquier contorno cerrado incluido en el anillo tal que zo pertenece a su interior.



### Metodo de cancelacion del polo  
Sea f una funcion compleja de variable compleja en un dominio D. Sean zo un polo de orden p de f y R la distancia de zo a la singularidad mas proxima. Entonces, la correspondiente serie de Laurent de f alrededor de zo tiene la forma.$$\sum_{n=-\infty}^{\infty}\mbox{b}_n(z-zo)^{n-p}$$
valida para 0< |z-zo| < R
Donde para todo n: $$bn=\frac{1}{n!}\lim_{z->zo}\frac{d^{(n)}}{dz^{(n)}}[(z-zo)^pf(z)]$$





#### Clasificacion de singularidades usando la serie de Laurent
- zo es una singularidad evitable <-> An=0 para n=-1,-2,...
- zo es un polo de orden p <-> $\mbox{A}_{-p}\neq 0$ y $\mbox{A}_{-p-1}=\mbox{A}_{-p-2}=...=0$
- zo es una singularidad esencial <-> $\mbox{A}_{-n}\neq 0$ para infinitos n>0



### Residuos


#### Definicion de Residuo  
Sea f una funcion compleja de variable compleja definida en un dominio de la forma 0<|z-zo|< R y zo una singularidad aislada de f de manera que: $$f(z)=\sum_{n=-\infty}^{\infty}\mbox{A}_n(z-zo)^n=...+\frac{\mbox{A}_{-1}}{(z-zo)}+\mbox{A}_0+\mbox{A}_1.(z-zo)+...$$
Para 0<|z-zo|< R 
Entonces el coeficiente $\mbox{A}_{-1}$ se denomina residuo de la funcion f(z) alrededor del punto zo y se denota $Res[f,zo]$. Esto es, $Res[f,zo]=\mbox{A}_{-1}$ 




#### Usos del residuo  
Se puede utilizar el residuo para calcular la integral de una funcion f analitica dentro y sobre un contorno $\gamma$ salvo tal vez en un numero finito de singularidades aisladas en el interior del contorno
##### Teorema de los residuos
Sea f una funcion analitica dentro y sobre un contorno cerrado $\gamma$ salvo quizas en un numero finitos de singularidades aisladas z1,z2,..,zk interiores a $\gamma$, entonces$$\int_\gamma f(z)dz=2.\pi.i\sum_{k=1}^{n}Res[f,zk]$$
- Osea, la integral de contorno de una funcion analitica con singularidades aisladas, es igual a la suma de los residuos de las singularidades







### Comportamiento en el infinito
Sea f una funcion compleja de variable compleja. Se dice que f tiene una singularidad en $z=\infty$ cuando la funcion F(s)=f(1/s) tiene una singularidad en s=0.

#### Desarrolo en serie alrededor del infinito
Para determinar el desarrollo de una funcion f alrededor de $z=\infty$, entonctraremos el desarrollo de la funcion F(s)=f(1/s) en s=0. Esto es, si $$F(s)=\sum_{n=-\infty}^{\infty}\mbox{A}_ns^n$$ Para R2<|s|< R1
entonces $$f(z)=F(1/z)=\sum_{n=-\infty}^{\infty}\mbox{A}_n(1/z)^n$$
Para 1/R1<|z|<1/R2