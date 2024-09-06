

## Definiciones de curva y contornos en plano complejo
#### Curva
Una curva C en el plano complejo es el conjunto de los $z=x+iy$ donde x=x(t) e y=y(t) para a<t<b< son funciones continuas de la vairbale real t
- **Curva simple:** Curva que no se intersecta a si misma
- **Curva suave:** $z'(t)\neq0$ y $z'(t)$ continua
- **Curva suave a trozo:** Conjunto de un numero finiot de curva suave

#### Contorno
Un curva es contorno si y solo si es una curva suave y simple
## Integral de una funcion compleja de variable real
Sea f la funcion compleja de variable real f:D C R --> complejos 
$$f(t)=u(t)+iv(t)$$ t perteneciente a D, u(t) y v(t) funciones reales
#### Integral sobre un intervalo real
Se define la integral de la funcion f en [a,b] mediante
$$\int_{a}^{b}f(t)dt=\int_{a}^{b}u(t)dt+i\int_{a}^{b}v(t)dt$$

## Integral de una funcion compleja de variable compleja
#### Integral de contorno
Sea un contorno $\gamma$ : z=z(t). La integral de la *funcion compleja de variable compleja* f sobre $\gamma$ es
$$\int_{\gamma}f(t)dt=\int_{a}^{b}f(z(t)).z'(t)dt$$


### Teorema de Cauchy
Sea f una funcion compleja de variable compleja. Si f es analitica en un conjunto simplemente conexo D , entonces, para cualquier contorno cerrado $\gamma$ en D se cumple que:$$\int_\gamma f(z)dz=0 $$



#### Demuestre teorema de Cauchy
aosdngaldsjkva
afedadsfa









### Teorema de Cauchy en condiciones debiles
Sea f una funcion compleja de variabale compleje y $\gamma$ una curva lisa a tramos cerrada. Si f es analitica en todo el interior de $\gamma$ salvo en un numero finito de puntos zk del interior de $\gamma$ , con k=1,2,3,...,n. Si ademas $\lim_{z->zk}(z-zk).f(z)=0$ y f es continua en $\gamma$ y en el interior de $\gamma$ entonces:$$\int_\gamma f(z)dz=0 $$


#### Teorema de cauchy conjuntos multiplemente conexos
En estos casos, la integral de contorno de $\gamma$ sera igual a la suma de las integrales de contorno se los conjuntos cerrados que no pertenecen a conjunto

#### Observaciones importantes
- La integral en una superficie simplemente conexa, no depende de depende del camino, solo del valor inicial y final
- En la funciones complejas de variable compleja tambien existen las primitivas y se las calculo como en C2
- En las funcinoes complejas de variables complejas tambien es valida la regla de barrow


### Formula integral de Cauchy
Si f es una funcion compleja de variable compleja analitica en un conjunto D simplemente conexo y $\gamma$ es una curva cerrada en D, para cuarquiel punto zo del interior de $\gamma$ vale que:$$\frac{f^{(n)}.2.\pi.i}{n!}=\int_\gamma \frac{f(z)}{(z-zo)^{n+1}}$$
#### Colorarios de la formula integral de Cauchy
Si f es analitica en D simplemente conexo y zo pertenece a D, entonces:
- f posee infinitas derivadas en zo
- sus derivadas tambien son analiticas en zo
- las funciones u(x,y) y v(x,y) tambien poseen infinitas derivadas y estas son continuas en Zo

### Teorema de morera
si f es una funcion compleja de variable compleja continua en un conjunto simplemente conexo D y $\int_\gamma f(z)dz=0$ para todo $\gamma$ en D entonces, f es analitica en D



## Consultar  
- No entiendo la relaciones entre integrales de funciones complejas de variable real con las integrales de funciones compleja de variable compleja