

Las ecuaciones de diferencias son analogas discretas a las ecuaciones diferencias, estas estudian cambios a taza regulares de tiempo
En las ecuaciones de diferencias la incognita que buscamos deja de ser una funcion continua y empieza a ser una sucesiones
*Notacion:* Denotaremos con $R^{\infty}$ Al conjunto de todas las sucesiones de numeros reales
#### Definicion de ecuacion de diferencias
Unas ecuacion de diferencias(edd) es una expresion de la forma $$F(n,y(n),y(n+1),...,y(n+k))=0$$
Para todo n perteneciente a los naturales
Donde la incognita $y$ es tal que $y \in R^{\infty}$ es decir, $y$ es una sucesion de numeros reales
#### Orden de una ecuacion de diferencias
Sea una ecuacion de diferencias donde N1 y N2 son los valores maximos y minimos de n respectivamente, entonces, el orden de la ecuacion de diferencias es N1-N2


### Definicion de ecuacion de diferencias lineal 
Una ecuacion de diferencias lineal de orden k es una edd de la forma $$\mbox{y}_{n+k}+an.\mbox{y}_{n+k-1}+bn.\mbox{y}_{n+k-2}+...+cn.\mbox{y}_{n+1}+dn.\mbox{y}_{n}=hn$$
Donde an,bn,...,cn,dn y hn son sucesiones dadas con $dn\neq 0$ Para todo $n \in N$ .
- Si an,bn,...,cn,dn son sucesiones constante decimos que la ecuacion tiene coeficiente constantes
- Si $hn=0$ decimos que la ecuacion de diferencais es homognea, de lo contratio es una ecuacion de diferencias inhomogenea




#### Teorema de unicidad
Si tenemos un problemas de valor inicial existe una unica solucion que verifica el problema


### Definicion de ecuacion de diferencias lineales de 1er orden 
Una ecuacion de diferencias lineal de 1er orden tiene la forma $$\mbox{y}_{n+1}=an.\mbox{y}_{n}+hn$$
donde la sucesion an es tal que $an \neq 0$ para todo $n \in C$(C=N o C contenido en N)


#### Encuentre la solucion de una ecuacion de diferencia lineal inhomogenea de primer orden con coeficientes variables. 
adsfasdga
gafdsgaf




### Definicion de ecuacion de diferencias lineal de 2do orden 
Una ecuacion de diferencias lineal de 2do orden tiene la forma $$\mbox{y}_{n+2}+an.\mbox{y}_{n+1}+bn.\mbox{y}_{n}=hn$$
Donde la sucesion bn es tal que $bn \neq 0$ para todo $n \in C$ 




### Definicion de casotariano 
Sean $x,z \in R^{\infty}$ . Si las sucesiones x y z son solucion de la ecuacion de diferencias homogena asociada, entonces, el casotariano de x y z denotado por $\mbox{C}_{n}(x,z)$ esta dado por $$\mbox{C}_{n}(x,z)=|\left(
\begin{array}{ll}
x(n) & z(n) \\
x(n+1)   & z(n+1)
\end{array}
\right)|=x(n).z(n+1)-z(n).x(n+1)$$ 



#### Formula del casotariano 
Sean x,z soluciones de la ecuacion de diferencia homogenea de 2do oden $$\mbox{y}_{n+2}+an.\mbox{y}_{n+1}+bn.\mbox{y}_{n}=0$$
Donde la sucesion bn es tal que $bn \neq 0$ para todo $n \in C$ . Entonces el casotariano es: $$\mbox{C}_{n}(x,z)=co.\prod_{k=0}^{n-1}bk$$
Con $co \in R$ 


##### Demuestre la formula del casotariano 
asdgasdg
asdgasg






### Forma de ecuacion de diferencias de 2do orden homogenea con coeficientes constantes y su solucion 
Sea la ecuacion de diferencia de 2do orden homogenea con coeficientes constantes $$\mbox{y}_{n+2}+a.\mbox{y}_{n+1}+b.\mbox{y}_{n}=0$$
Donde a,b son constante reales con $b \neq 0$
#### Solucion
Proponemos una solucion de la forma $yn=\lambda^n$ . Remplazando en la ecuacion de diferencias encontramos la ecuacion caracteristica asociada $$\lambda^2+a.\lambda+b=0$$
Resolviendo esta ecuacion caracteristica con baskara nos encontramos con 3 casos:
1. Raices reales y distintos
En este caso la solucion dentra la forma $\mbox{y}_{g}=c1.\lambda1^n + c2.\lambda2^n$ con c1 y c2 constantes arbitrarias
2. Raices reales y repetidas
En este caso la solucion dentra la forma $\mbox{y}_{g}=c1.\lambda1^n+c2.n.\lambda1^n$ con c1 y c2 constantes arbitratias
3. Raices complejas
En este caso la solucion dentra la forma $\mbox{y}_{g}=c1.r^n.cos(n.\phi)+c2.r^n.sen(n.\phi)$ 

