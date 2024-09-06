
## Conceptos preliminares
#### Funcion compleja seccionalmente continua
Una funcion $f:R-->C$, $f(t)=u(t)+i.v(t)$, es seccionalmente continua en $(-\infty,\infty)$ si en todo intervalo finito las funciones u y v son seccionalmente continuas.



#### Funcion compleja absolutamente integrable 
Una funcion $f:R-->C$ es absolutamente integrable si $\int_{-\infty}^{\infty}|f(t)|dt<\infty$ 





## Fourier



#### Definicion Transformada de Fourier 
Sea f una funcion compleja con dominio en $(-\infty,\infty)$ o sea $f:R-->C$. Se define la transformada de Fourier de f como la funcion $F:R-->C$ dada por $$F(w)=\int_{-\infty}^{\infty}f(t).e^{-iwt}dt ;w\in R$$




#### Condicion suficientes para la existencia de la transformada de Fourier 
Si la funcion $f:R-->C$ es seccionalmente continua en $(-\infty,\infty)$ y absolutamente integrable entonces, la transformada de Fourier de f existe para todo w en R.



### Integral de fourier de una funcion 
Sea la funcion $f:R-->C$ seccionalmente continua en $(-\infty,\infty)$ y absolutamente integrable. Se define a la integral de Fourier de f como $$\frac{1}{2.\pi}\int_{-\infty}^{\infty}F(w)e^{iwt}dw$$





#### Teorema de convergencia de la integral de fourier 
Si las funciones f y f' son seccionalmente continua en $(-\infty,\infty)$ y f absolutamente integrable entonces, la integral de Fourier converge para todo $t \in (-\infty,\infty)$ al valor $\frac{f(t+)+f(t-)}{2}$





#### Forma trigonometrica de la integral de Fourier 
Cuando la funcion f es real $f:R-->R$ ,entonces, la integral de fourier toma la forma $$f(t)=\frac{1}{\pi}.\int_{0}^{\infty}[A(w)cos(wt)+B(w).sen(wt)]dw$$
Llamada forma trigonometrica de Fourier
- Los coeficientes an y bn de la serie trigonometrica de fourier son los analogos de A(w) y B(w)





### Definicion de transformada inversaa de Fourier 
Dada una funcion compleja F definida para todo w real, se define la transformada inversa de Fourier de F a la funcion $f:R-->C$ dada por $$f(t)=\frac{1}{2.\pi}\int_{-\infty}^{\infty}F(w).e^{iwt}dw$$ Con $t \in R$




## Propiedades de Fourier


#### Propiedades de Fourier Linealidad, demuestre 
Sean f y g funciones complejas y a, b constantes complejas. Si existen $F[f(t)]$ y $F[g(t)]$ entonces, $$F[a.f(t)+b.g(t)]=a.F(f(t))+b.F[g(t)]$$ Con $a,b \in C$







#### Propiedades de Fourier Desplazamiento en el tiempo, demuestre 
Sean f una funcion compleja y to un numero real fijo. Si $F[f(t)]=F(w)$ entonces, $$F[f(t-to)]=e^{-i.w.to}F(w)$$







#### Propiedades de Fourier Desplazamiento en la frecuencia, demuestre 
Sea f una funcion compleja y wo un numero real fijo. Si $F[f(t)]=F(w)$ entonces, $$F[e^{i.wo.t}.f(t)]=F(w-wo)$$







#### Propiedades de Fourier Cambio de escala, demuestre 
Sea f una funcion compleja y a un numero real fijo no nulo. Si $F[f(t)]=F(w)$ entonces,$$F[f(at)]=\frac{1}{|a|}.F(\frac{w}{a})$$







#### Propiedades de Fourier Simetria 
Sea f una funcion compleja. Si $F[f(t)]=F(w)$ entonces, $$F[F(t)]=2.\pi.f(-w)$$






#### Propiedades de Fourier Transformada de derivadas 
Supongamos que las funciones $f,f',...,f^{(n-1)}$ son continua en $(-\infty,\infty)$ y que $f,f',...,f^{(n)}$ admiten transformdas de Fourier. Supongamos ademas que $$\lim_{t-->\infty}f^{(k)}(t)=\lim_{t-->-\infty}f^{(k)}(t)=0$$ Para k=0,1,2..,n-1.
Entonces $$F[f^{(n)}(t)]=(i.w)^{n}.F(w)$$







#### Propiedades de Fourier Transformada de una integral 
Sea f una funcion compleja. Si $F[f(t)]=F(w)$ y $\int_{-\infty}^{\infty}f(t).dt=0$ entonces, $$F[\int_{-\infty}^{t}f(u)du]=\frac{F(w)}{i.w}$$Para $w \neq 0$ 







#### Propiedades de Fourier Derivada de una transformada 
Sean f una funcion complena y n un numero natural. Si f es seccionalmente continua en $(-\infty,\infty)$ y la funcion $t^n.f(t)$ es absolutamente integrable entonces, $$F[t^n.f(t)]=i^n.\frac{d^nF(w)}{dw^n}$$







#### Referencia 
- [[Series de Fourier]]