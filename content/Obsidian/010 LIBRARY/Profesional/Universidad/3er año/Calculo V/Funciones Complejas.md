

Sea el conjunto de salida A, el conjunto de llegada B y w=f(z) que relaciona ambos conjuntos
- Si A es complejo y B es complejo ---> Funcion compleja de variable compleja
- Si A es complejo y B es real ---> Funcion real de variable compleja
- Si A es real y B es compleja ---> Funcion compleja de variable real

## Funciones complejas elementales
#### Polinomio
Se define igual que la real solo que los coeficientes pueden ser complejos y la variable es la Z
#### Racional
Se define igual que la real solo que ahora los polinomios son complejos
#### Funcion exponencial
$$e^{z}=e^x.(cos(y)+isen(y))$$
#### Funiones trigonometricas
$$sen(z)=\frac{e^{iz}-e^{-iz}}{2i}$$
$$cos(z)=\frac{e^{iz}+e^{-iz}}{2}$$
#### Funciones hiperbolicas
Igual que las hiperbolicas reales solo que ahora la variable es Z


## Limite,Continuidad y Derivada
### Limite
La definicion y los teorema de limite de las funciones reales con variables se mantienen praa funciones complejas de variable compleja, solo se agrega un teorema
#### Teorema Limite Complejo
Sea f un funcion compleja de variable compleja y $z=x+iy$, donde $f=u(x,y)+iv(x,y)$ , ademas sean zo y wo perteneciente a los complejos de la forma $zo=xo+iyo$ y $wo=uo+ivo$
entonces si $\lim_{z->zo}f(z)=wo$ entonces $\lim_{(x,y)->(xo,yo)}{u(x,y)}=uo$ y $\lim_{(x,y)->(xo,yo)}{v(x,y)}=vo$ 
### Continuidad
La definicion y los teorema de continuidad de las funciones reales con variables se mantienen praa funciones complejas de variable compleja, solo se agrega un teorema
#### Teorema Continuidad Compleja
$f(z)=u(x,y)+iv(x,y)$ es continua en $zo=xo+ixo$ si y solamente si $u(x,y)$ y $v(x,y)$ son continua en (xo,yo)
### Derivada
La definicion y los teorema de derivada de las funciones reales con variables se mantienen para funciones complejas de variable compleja, solo se agrega un teorema


## Fuciones analiticas y armonicas
### Funcion analitica

#### Definicion Funcion Analitica 
Sea f funcion compleja de variable compleja, definida en un dominio D y sea el punto zo perteneciente a D,  Se dice que f es analitica en el punto zo si es derivable en todo punto de algun entorno de zo.
Se dice que una funcion es analitica en un conjunto S si es analitica en cada punto de S



#### Condiciones Necesaria para la Analiticidad 
Si una funcion $f(z)=u(x,y)+iv(x,y)$ donde $z=x+iy$ es analitica en un dominio D, entonces, para todo z perteneciente a D se cumplen las ecuaciones de Cauchy-Riemann
$$ux(x,y)=vy(x,y)$$ $$uy(x,y)=-vx(x,y)$$




#### Condiciones suficiente para la analiticidad 
Una funcion compleja de variable copleja $f(z)=u(x,y)+iv(x,y)$ es analitica en un conjunto D, si $u,ux,uy,v,vx,vy$ son continuas en D y para punto del conjunto se cumple las condiciones de Cauchy-Riemann



### Funcion Armonica

#### Definicion funcion armonica 
Sea la funcion h real de variable real, se dice que h es una funcion armonica en $D$C$R^2$ si las funciones h,hx,hxx,hy,hyy son continuas en D y ademas se cumple la condicion de Laplace para todo punto del conjunto D
$$hxx+hyy=0$$
DELETE 
<!--ID: 1671055560917-->


#### Teorema relacion funciones armonicas con analiticas 
Si una funcion $f(z)=u(x,y)+iv(x,y)$ donde $z=x+iy$ es analitica en un dominio D, entonces, la funciones u(x,y) y v(x,y) son armonicas en D
DELETE 
<!--ID: 1671055560924-->



#### Definicion funciones armonicas conjugada 
Sean las funciones reales de variables reales armonicas H(x,y) y Q(x,y) en un dominio D, se dice que la funcion Q(x,y) es armonica conjugada de H(x,y) en D si la funcion F(z)=H(x,y)+iQ(x,y) es analitica en D
DELETE 
<!--ID: 1671055560933-->


## Ceros, Singularidad y Polos

#### Punto regular
Se dice que zo es un punto regular de la funcion f si zo es un punto en el cual la funcion f(z) es analitica

#### Definicion de cero 
Sea f una funcion analitica en zo, zo perteneciente a D(D dominio de f). Diremos que zo es un cero de orden n de f si en un entorno de zo se puede escribir:$f(z)=(z-zo)^{n}.\phi(z)$ 
Donde $\phi(z)$ es analitica en zo y $\phi(zo) \neq 0$ 
DELETE 
<!--ID: 1671060652889-->



#### Definicion de Singularidad 
Sea zo un punto donde la funcion f no es analitica. Se dice que zo es una singularidad de f si en todo entorno reducido de zo la funcion f es analitica
DELETE 
<!--ID: 1671060652899-->



#### Definicion de Singularidad aislada 
Sea zo un punto donde la funcion f no es analitica. Se dice que zo es una singularidad aislada de f si existe algun entorno reducido de zo donde zo es la unica singularidad
DELETE 
<!--ID: 1671060652906-->



#### Clasificaciones de singularidades aisladas 
Sea zo una singularidad aislada de la funcion f, se dice zo es una singularidad:
- Evitable si $\lim_{z->zo}f(z)\neq infinito$
- Polar si $\lim_{z->zo}f(z)= infinito$
- Esencial si no existe $\lim_{z->zo}f(z)$
DELETE 
<!--ID: 1671060652911-->



#### Definicion de polo 
Sea la funcion f analitica en un entorno reducido de zo. Se dice que f posee un polo de orden p(p natural) en zo si en un entorno reducido de zo se peude escribir: $f(z)=\frac{\phi(z)}{(z-zo)^{p}}$
Donde $\phi(z)$ es analitica en zo y $\phi(zo) \neq 0$ 
DELETE 
<!--ID: 1671060652918-->



#### Teorema relacion entre polos y ceros 
La funcion f compleja de variable compleja posee en zo un polo de orden p, si y solo si, la funcion 1/f posee un cero de orden p en zo.
DELETE 
<!--ID: 1671060652924-->

##### Demuestre teorema que relaciona polos y ceros de una funcion 
asdfgasdg
adsgaga
dAGADSG
DELETE 
<!--ID: 1676333676613-->
