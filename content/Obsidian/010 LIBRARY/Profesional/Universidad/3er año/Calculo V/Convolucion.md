

#### Definicion de convolucion 
Sean f y g funciones seccionadamente continua en un dominio D incluido en $[0,\infty)$. La convolucion de f y g se define como $$(fxg)(t)=\int_{0}^{t}f(x).g(t-x)dx$$





#### Definicion de producto de convolucion 
Sea f y g funciones definidas en $(-\infty,\infty)$ . Se denomina producto de convolucion de f y g a una nueva funcion definida por $$(f*g)(t)=\int_{-\infty}^{\infty}f(u).g(t-u)du$$Para los valores de $t \in R$ donde existe la integral.






## Teoremas de convolucion

#### Teorema de convolucion Laplace 
Sean f y g funciones seccionadamente continuas en $[0,\infty)$ y de orden exponencial $\alpha$ tales que $L[f(t)]=F(s)$ y $L[g(t)]=G(s)$. Entonces: $$L[(gxf)(t)]=F(s).G(s)$$
En terminos de transformada inversa: $L^{-1}[F(s).G(s)]=(fxg)(t)$




#### Teorema de convolucion en el tiempo Fourier 
Si $F[f(t)]=F(w)$ y $F[g(t)]=G(w)$ entonces, $$F[(f*g)(t)]=F(w).G(w)$$




#### Teorema de convolucion en frecuencia Fourier 
Si $F[f(t)]=F(w)$ y $F[g(t)]=G(w)$ entonces, $$F[f(t).g(t)]=\frac{1}{2.\pi}(F*G)(w)$$





## Consulta 
Diferencia entre las definiciones de producto de convolucion

#### Referencia
- [[Transformada de Laplace]]
- [[Transformada de Fourier]]