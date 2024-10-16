

# SUCESIONES

## Definición de una Sucesión
Una **sucesión** es una función definida sobre el conjunto de los números naturales $\mathbb{N}$. Matemáticamente, una sucesión puede escribirse como:

$$
a_n = f(n), \quad n \in \mathbb{N}
$$

Esto significa que una sucesión es una lista ordenada de números: $a_1, a_2, a_3, \ldots$.

### Ejemplo
La sucesión $a_n = \frac{1}{n}$ es una función que toma valores de $n$ en $\mathbb{N}$ y genera la lista:

$$
1, \frac{1}{2}, \frac{1}{3}, \frac{1}{4}, \ldots
$$

## Sucesiones Convergentes y Divergentes
- Una **sucesión convergente** es aquella cuyo término general se aproxima a un número finito $L$ cuando $n \to \infty$. Esto se expresa como:

$$
\lim_{n \to \infty} a_n = L
$$

- Una **sucesión divergente** es aquella que no se aproxima a ningún valor finito cuando $n$ tiende a infinito, o tiende a infinito positivo o negativo.

### Ejemplo
La sucesión $a_n = \frac{1}{n}$ **converge** a $0$ cuando $n \to \infty$. Por otro lado, la sucesión $a_n = n$ **diverge** hacia infinito.

## Sucesiones Monótonas
- Una sucesión es **monótona creciente** si $a_{n+1} \geq a_n$ para todo $n \in \mathbb{N}$.
- Es **monótona decreciente** si $a_{n+1} \leq a_n$ para todo $n \in \mathbb{N}$.

### Ejemplo
La sucesión $a_n = 2^n$ es monótona creciente, ya que sus términos aumentan indefinidamente.

## Sucesiones Acotadas
- Una sucesión está **acotada superiormente** si existe un número $M$ tal que $a_n \leq M$ para todo $n$.
- Está **acotada inferiormente** si existe un número $m$ tal que $a_n \geq m$ para todo $n$.
- Una sucesión se dice **acotada** si está acotada tanto superior como inferiormente.

### Ejemplo
La sucesión $a_n = \sin(n)$ está acotada, ya que todos sus términos están entre -1 y 1.

## Criterios de Convergencia para Sucesiones Monótonas y Acotadas
Una **sucesión monótona y acotada** es siempre **convergente**. Es decir, si una sucesión es monótona creciente y acotada superiormente, o monótona decreciente y acotada inferiormente, entonces la sucesión tiene un límite finito.

### Ejemplo
La sucesión $a_n = 1 - \frac{1}{n}$ es monótona creciente y está acotada por 1, por lo que es convergente hacia 1.

# SERIES DE NÚMEROS REALES Y DE POTENCIAS

## Definición de Serie
Una **serie** es la suma de los términos de una sucesión. Dada una sucesión $\{a_n\}$, se define la serie como:

$$
\sum_{n=1}^{\infty} a_n = a_1 + a_2 + a_3 + \cdots
$$

### Convergencia y Divergencia de una Serie
- Una serie **converge** si la secuencia de las **sumas parciales** tiene un límite finito. La **n-ésima suma parcial** se define como:

$$
S_n = \sum_{k=1}^n a_k
$$

Si $\lim_{n \to \infty} S_n = S$, entonces la serie converge y su suma es $S$.
- Una serie **diverge** si el límite no existe o es infinito.

### Condición Necesaria para la Convergencia
Para que una serie $\sum a_n$ **converja**, es necesario que:

$$
\lim_{n \to \infty} a_n = 0
$$

Si $\lim_{n \to \infty} a_n \neq 0$, la serie **diverge**.

## Serie Geométrica
Una **serie geométrica** tiene la forma:

$$
\sum_{n=0}^\infty ar^n = a + ar + ar^2 + ar^3 + \cdots
$$

- La serie converge si $|r| < 1$ y su suma es:

$$
S = \frac{a}{1-r}
$$

- Si $|r| \geq 1$, la serie diverge.

### Ejemplo
La serie $\sum_{n=0}^\infty \frac{1}{2^n}$ es geométrica con $a = 1$ y $r = \frac{1}{2}$. Converge y su suma es:

$$
S = \frac{1}{1 - \frac{1}{2}} = 2
$$

## La Serie p
La **serie p** se define como:

$$
\sum_{n=1}^\infty \frac{1}{n^p}
$$

- Converge si $p > 1$.
- Diverge si $p \leq 1$.

### Ejemplo
La serie $\sum_{n=1}^\infty \frac{1}{n^2}$ converge, mientras que la serie $\sum_{n=1}^\infty \frac{1}{n}$ (serie armónica) diverge.

## Criterios de Convergencia para Series de Términos Positivos
### 1. Criterio de Comparación
Si $0 \leq a_n \leq b_n$ para todo $n$ y $\sum b_n$ converge, entonces $\sum a_n$ también converge.

### 2. Criterio del Cociente
Para una serie $\sum a_n$, si existe un $L = \lim_{n \to \infty} \left| \frac{a_{n+1}}{a_n} \right|$:

- Si $L < 1$, la serie converge.
- Si $L > 1$, la serie diverge.
- Si $L = 1$, el criterio no es concluyente.

### 3. Criterio de la Raíz
Para una serie $\sum a_n$, si $L = \lim_{n \to \infty} \sqrt[n]{|a_n|}$:

- Si $L < 1$, la serie converge.
- Si $L > 1$, la serie diverge.
- Si $L = 1$, el criterio no es concluyente.

## Series Alternadas
Una **serie alternada** es aquella cuyos términos cambian de signo.

Ejemplo: La **serie alternada armónica**:

$$
\sum_{n=1}^\infty \frac{(-1)^{n+1}}{n} = 1 - \frac{1}{2} + \frac{1}{3} - \frac{1}{4} + \cdots
$$

El **criterio de Leibniz** establece que si los términos de una serie alternada decrecen en valor absoluto y tienden a cero, la serie converge.

## Convergencia Absoluta y Condicional
- Una serie **converge absolutamente** si la serie de los valores absolutos converge:

$$
\sum |a_n| \quad \text{converge}
$$

- Si una serie converge, pero no converge absolutamente, se dice que **converge condicionalmente**.

## Serie de Potencias
Una **serie de potencias** es de la forma:

$$
\sum_{n=0}^\infty c_n (x - a)^n
$$

Tiene un **radio de convergencia** $R$, que determina el intervalo en el cual la serie converge.

### Ejemplo
La serie $\sum_{n=0}^\infty \frac{x^n}{n!}$ tiene radio de convergencia infinito, lo que significa que converge para todos los valores de $x$.

## Series de Taylor y McLaurin
Una **Serie de Taylor** de una función $f$ en torno a un punto $a$ se define como:

$$
f(x) = \sum_{n=0}^\infty \frac{f^{(n)}(a)}{n!} (x-a)^n
$$

Si $a = 0$, se denomina **Serie de McLaurin**:

$$
f(x) = \sum_{n=0}^\infty \frac{f^{(n)}(0)}{n!} x^n
$$

### Ejemplo: Serie de McLaurin para $e^x$
$$
e^x = \sum_{n=0}^\infty \frac{x^n}{n!} = 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \cdots
$$

Estas series son útiles en ingeniería para aproximar funciones complicadas mediante polinomios, lo que facilita cálculos numéricos y analíticos.
```

Estos apuntes abarcan de manera detallada las propiedades y conceptos fundamentales de las **sucesiones** y las **series**, incluyendo los criterios de convergencia, tipos de series, y aplicaciones importantes como las **series de Taylor** y **McLaurin**. Estos conceptos son fundamentales para análisis y aplicaciones en ingeniería, especialmente en áreas como señales y sistemas, análisis de circuitos, y modelado numérico.

¿Te gustaría que desarrolle algún concepto adicional o que agregue ejemplos específicos de aplicaciones en ingeniería?