# Lugar geometrico de las raices (LR)
Es un metodo grafico para estudiar las posiciones de las raices de un polinomio cuando cambia algun parametro del mismo

## Ejemplo practico:
Sea la funcion de transferencia $T(s)=\frac{P(s)^m}{Q(s)^n}$ , para que la funcion sea sintetizable necesitamos que n>=m
Descomponiendo en fracciones parciales nos queda $T(s)=\frac{Rp1}{s-p1}+\frac{Rp2}{s-p2}+...+\frac{Rpn}{s-pn}$, donde Rpn son los residuos y pn los polos
Ahora, supongamos que la salida tiene la forma $h(t)=h1(t)+...+hn(t)$
Entonces:$h(t)=L^{-1}(\frac{Rp1}{s-p1})+...+L^{-1}(\frac{Rpn}{s-pn})$  
Si agregamos una funcion x(t) distinta del impulso en la entrada, los polos de la funcion T(s) no cambian, solo se agregan la cantidad de polos del orden de la entrada X(s), a estos primeros polos, que se mantienen sin importar la entrada, constituiran la respues transitoria del sistema y los polos que son agregados por x(t), constituiran la respues forzada del sistema
### Polos de ecuacion de 2do orden
Supongamos una ecuacion de 2do orden con 2 variables $x^2+7x+\epsilon=0$ 

|$\epsilon$|ceros|
|---|------|
|1|0;-7|
|5|-0,145;-6,85|
|10|-2;-5|
|12,25|-3,5|
|15|-3,5+-j1,55|
|21,25|-3,5+-j3|
Si lo graficamos podemos ver que se nos forma una cruz, primero los polos se acercan por el eje real y cuando llegan al valor intermedio, se comienzan a separar en complejos conjugados. Mientras estas raices son reales, su respuesta temporal son solo 2 exponenciales y cuando las raices se convierten en complejas, esta respuesta se convierte en una cosenoidal
- Si analizamos para $\epsilon>0$ se llama *Lugar de las raices*
- Si analizamos para $\epsilon<0$ se llama *Lugar de las raices complementario*
- Si analizamos para $-infinito<\epsilon<infinito$ se llama *Lugar de las raices completo*
### Lugar geometricos
Puntos del plano que cumplen una condicion dada
- En el ejemplo anterior, la grafica con forma de cruz forman con la condicion que son ceros del polinomio de segundo orden para algun valor de $\epsilon$,



## Idea de Evans
La gran idea de evans es evitar hacer esta tabla para cada valor de $\epsilon$ , para lograr esto, separo la igualdad de segundo orden en igual de modulo e igualdad de argumento, se dio cuenta que la igualdad del argumento no depende de $\epsilon$, entonces, podemos encontrar la grafica de los ceros con la igualdad del argumento y luego encontramos la raiz que nos interese con la igualdad de modulo, esta idea la generamos a partir del ejemplo dado, lo que verdaderamente describio Evans fue lo siguiente
Dada la siguiente ecuacion $$\epsilon.\frac{1}{(s-0)(s+b)}=-1$$
En esta ecuacion nos quedaria igual la igualdad de argumento que en el ejemplo: $arg(s-0)+arg(s+b)=180$, entonces la grafica nos quedara de la misma manera
Generalizando la idea: $$\epsilon . Pm(s)+Qn(s)=\epsilon . \frac{Pm(s)}{Qn(s)}+1=0$$ Escrito de otra manera $\epsilon . \frac{Pm(s)}{Qn(s)}=-1$ , donde esta razon tambien cumpliria la **Condicion de argumento** : $arg(Pm(s))-arg(Qn(s))=180$
Esto visto es muy importante ya que cuando tenemos un diagrama de bloque, $\epsilon$Pm(s) es G(s) y Qn(s) es 1+G(s)H(s), donde 1+G(s)H(s) es el polinomio caracteristico

## Reglas para la construccion del lugar geometrico de las raices
*Ramas*:Moviemientos de los ceros, hay 1 por cada polo que tengamos
*Exceso polo-cero*: La resta de polos del sistema menos los ceros (P-Z)
7. Si el exceso polo-cero es ≥ 2, la suma de la posición de los polos de lazo cerrado para todo valor de $\epsilon$ es una constante igual a la suma de las posiciones de los polos de G(s). **Consular**

#### 1.Ramas
- Tenemos tanta ramas como el numero maximo de polo o de cero
- Estas ramas nacen en los polos(donde el parametro variable vale 0)
- Mueren en los ceros(parametro variable mas menos infinito)
	- Si hay mas polos que ceros, las ramas mueren en el infinito
	- Si hay mas ceros que polos, las ramas nacen en el infinito
#### 2.Eje Real
- Si estamos a la izquierda de un numero par de polos y ceros de F(s), estos puntos pertenecen al lugar geometrico de las raices
#### 3.Asintotas
Las ramas que tienen o vienen del infinito siguen ciertas asintotas
- Todas las asintotas se cruzan en el centroide $OA=\frac{\sum{Polos} - \sum{Ceros}}{p-z}$
	- En este punto tambien nacen las asintotas, osea el origen de las asintotas
	- **Es lo mismo hacer la sumatoria de polos menos la sumatoria de ceros que hacer la sumatoria de la ubicacion de polos menos la sumatoria de la ubicacion de los ceros**
- Las asintotas se distribuyen de manera uniforme, cada una con un angulo  $\phi=\frac{180+k360}{p-z}$ con k=0,1,..,p-z
#### 4.Cruces con el eje imaginario
- Usamos en criterio de routh
- Si las ramas del lugar cruzan el eje imaginario, lo hacen en puntos donde se cumple la condición de ángulo.Tambien podemos encontrar estos valores analiticamennte igualando la ecuacion a 0 y particularizando en wj 
#### 5. Puntos de ruptura y puntos de entrada
- En estos puntos se encuentra un maximo o un minimo de la funcion $\epsilon(s)=\frac{-1}{F(s)}$
	-  Punto de salida: $\epsilon$(s) maximo
	- Punto de entrada: $\epsilon$(s) minimo
	- Estos valores se determinar como $\frac{d\epsilon}{ds}=0$ 
		- El angulo con el que salen o entran es $\theta=180/a$ donde a son las ramas que emergen de ese punto
#### 6. Angulos de salidas de polos y ceros conjugados
- Se lo grafica haciendo la sumatoria de angulos en un punto infinitesimalmente cercado
	- Explicacion: Se hace un zoom y se hace una sumatoria de los angulos igual a 180, en el caso de los polos esos angulos son negativos y en el caso de los ceros esos angulos son positivo
#### 7. Simetria
-  Las ramas son simetricas respecto al eje real

## Uso de LR para sistemas de control
Con el lugar geometrico de las raices podemos ver como se mueven los polos de nuestro funcion de transferencia de lazo cerrado en funcion de como variamos un parametro, conmunmente en nuestro sistema modificaremos la ganancia, tener muy en cuenta que cuando graficamos el LR, estamos graficando los ceros y polos de la ecuacion caracteristica no de nuestra funcion de transferencia de lazo cerrado, esta distincion es muy importante ya que en el LR solo vemos los polos y para un analisis completo necesitariamos completarlo con los ceros de nuestra funcion de transferencia







#### Referencia:
- [[Funcion de transferencia]]