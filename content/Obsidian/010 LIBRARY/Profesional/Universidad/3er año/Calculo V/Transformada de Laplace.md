

La tranformada de Laplace, que es la herramienta matematica objeto de estudio en esta unidad, es un operador integral. Tiene diversar aplicaciones, siendo una de las mas importantes la resolucion de ecuaciones diferenciales con coeficientes constante transformandolas en ecuaciones algebraicas. Ademas es especialmente util en problemas con terminos no homogeneos de naturaleza discontinua



## Conceptos preliminares

#### Definicion de funcion seccionadamente continua 
Se dice que una funcion real f:$[a,b]-->R$ es seleccionadamente continua en un intervalor $[a,b]$ si:
- f es continua en $[a,b]$ salvo en un numero finito de puntos de $[a,b]$
- Los limites laterales $$f(xo+)=\lim_{h->0+}{f(x0+h)}$$$$f(xo-)=\lim_{h->0+}{f(x0-h)}$$
Existen en cada punto x0 en $[a,b]$





*Resultados importantes:*
- Si f es seccionalmente continua en $[a,b]$ entonces la integral de a a b de f(x) existe y es independiente de los valores que toma f en los puntos de discontinuidad
- Si 2 funciones con identicas salvo en sus disontinuidades, sus integrales son iguales
- El producto de 2 funciones seccionadamente continua tambien es seccionadamente continua
- Toda funcion continua en seccionadamente continua

## Laplace

### Definicion de transformada de Laplace 
Sea f una funcion real de variable real t, cuyo dominio D esta incluido en $[0,\infty)$. La transformada de Laplace de f se define como $$L[f(t)]=\int_{0}^{\infty}f(t).e^{-st}dt$$
Con $s \in C$
Siempre que la integral impropia exista




### Existencia de la transformada de Laplace


#### Funcion de orden exponencial 
Sea f una funcion con dominio D incluido en $[0,\infty)$ . Se dice que f es de orden expoencial $\alpha$ si existe $M>0;T>0$ y $\alpha \in R$ tales que: $$|f(t)|\leq M.e^{\alpha.t}$$ Para todo $t>T$ con $t\in domf$ 





#### Teorema de existencia de la transformada de Laplace 
Sea f una funcion real de valores reales, seccionadamente continua en $[0,\infty)$ y de orden exponencial $\alpha$ , enttonces: $L[f(t)]$ existe para $Re(s)>\alpha$





#### Definicion de transformada inversa de Laplace 
Dada una funcion $F:C->C$, Si existe una funcion continua $f:[0,\infty)-->R$ de manera que sastifaga $L[f(t)]=F(s)$ entonces, decimos que f(t) es la transformada inversa de Laplace de F(s) y se denota $L^{-1}[F(s)]$. De modo que:$$f(t)=L^{-1}[F(s)]<->L[f(t)]=F(s)$$



## Propiedades de Laplace 


#### Propiedades de Laplace Linealidad,, demuestre 
Sean f y g funciones tales que $L[f(t)]=F(s)$ para $Re(s)>\alpha1$ y $L[g(t)]=G(s)$ para $Re(s)=\alpha2$ cons $\alpha1,\alpha2$ contantes. Entonces $$L[a.f(t)+b.g(t)]=a.F(s)+b.G(s)$$
Para $Re(s)>max(\alpha1,\alpha2)$ . Con a,b contantes reales





#### Propiedades de Laplace Cambio escala, demuestre 
Sea f funcion tal que $L[f(t)]=F(s)$ para $Re(s)>\alpha$ y a un numero real tal que a>0 entonces:$$L[f(at)]=\frac{1}{a}.F(\frac{s}{a})$$Para $Re(s)>a.\alpha$






#### Propiedades de Laplace Traslacion en s , demuestre 
Sea f funcion tal que $L[f(t)]=F(s)$ para $Re(s)>\alpha$ y a un numero real entonces $$L[e^{a.t}f(t)]=F(s-a)$$Para $Re(s)>a+\alpha$ 






#### Propiedades de Laplace Traslacion en t, demuestre 
Sea f funcion tal que $L[f(t)]=F(s)$ para $Re(s)>\alpha$ y a un numero real no negativo, entonces: $$L[u(t-a).f(t-a)]=e^{-a.s}.F(s)$$ Para $Re(s)>\alpha$






#### Propiedades de Laplace Transformada de la derivada 
Sea f una funcion continua en $[0,\infty)$ y de orden exponencial $\alpha$ y sea f' seccionadamente continua en $[0,\infty)$ y de orden exponencial $\alpha$ . Entonces $$L[f'(t)]=s.F(s)-f(0)$$ para $Re(s)>\alpha$ . Con $L[f(t)]=F(s)$ para $Re(s)>\alpha$ 







#### Propiedades de Laplace Transformada de la integral 
Sea f una funcion seccionadamente continua en $[0,\infty)$ y de orden exponencial $\alpha$ de manera que $L[f(t)]=F(s)$ para $Re(s)>\alpha$ entonces, $$L[\int_{0}^{t}f(u)du]=\frac{F(s)}{s}$$ Para $Re(s)>max(0,\alpha)$ 







#### Propiedades de Laplace Derivada de una transformada 
Si f es seccionadamente continua en $[0,\infty)$ y de orden exponencial $\alpha$, de manera que $L[f(t)]=F(s)$ para $Re(s)>\alpha$ entonces, $$L[t.f(t)]=-F'(s)$$ para $Re(s)>\alpha$ 






#### Propiedades de Laplace Integral de una transformada 
Si f es seccionalmente continua en $[0,\infty)$ y de orden exponencial $\alpha$ de manera que $L[f(t)]=F(s)$ para $Re(s)>\alpha$ y existe $\lim_{t->0+}\frac{f(t)}{t}$ entonces, $$L[\frac{f(t)}{t}]=\int_{s}^{\infty}F(u)du$$ para $Re(s)>\alpha$






