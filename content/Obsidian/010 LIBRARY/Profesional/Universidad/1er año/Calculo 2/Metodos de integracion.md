# METODOS INTEGRACIÓN

## Métodos de Integración

### 1. Método de Sustitución
El **método de sustitución** se utiliza para simplificar una integral transformándola en una forma más fácil de resolver. Consiste en hacer un cambio de variable.

Ejemplo:

$$
\int (2x) \cos(x^2) \, dx
$$

Sustituimos $u = x^2$, entonces $du = 2x \, dx$:

$$
\int (2x) \cos(x^2) \, dx = \int \cos(u) \, du = \sin(u) + C = \sin(x^2) + C
$$

### 2. Integración por Partes
La **integración por partes** se usa para integrar productos de funciones. Se basa en la regla del producto para derivación y se formula como:

$$
\int u \, dv = u v - \int v \, du
$$

Ejemplo:

$$
\int x e^x \, dx
$$

Seleccionamos $u = x$ y $dv = e^x \, dx$. Entonces $du = dx$ y $v = e^x$:

$$
\int x e^x \, dx = x e^x - \int e^x \, dx = x e^x - e^x + C = e^x (x - 1) + C
$$

### 3. Integrales que Dan como Resultado Funciones Trigonométricas Inversas e Hiperbólicas Inversas
Para algunas integrales específicas, el resultado puede ser una **función trigonométrica inversa** o **hiperbólica inversa**.

Ejemplo:

$$
\int \frac{1}{\sqrt{1-x^2}} \, dx = \sin^{-1}(x) + C
$$

$$
\int \frac{1}{x^2 + 1} \, dx = \tan^{-1}(x) + C
$$

### 4. Integración de Potencias de Funciones Trigonométricas e Hiperbólicas
Este método se aplica para resolver integrales de la forma $\sin^n(x)$, $\cos^n(x)$, etc.

Ejemplo:

$$
\int \sin^2(x) \, dx = \int \frac{1 - \cos(2x)}{2} \, dx = \frac{x}{2} - \frac{\sin(2x)}{4} + C
$$

### 5. Sustituciones Trigonométricas e Hiperbólicas
Las **sustituciones trigonométricas** se utilizan cuando se enfrentan integrales con expresiones del tipo $\sqrt{a^2 - x^2}$, $\sqrt{x^2 - a^2}$, etc.

Ejemplo: Para integrar $\int \frac{1}{\sqrt{a^2 - x^2}} \, dx$, podemos usar la sustitución $x = a \sin(\theta)$.

Para **sustituciones hiperbólicas**, se usan funciones como $x = a \cosh(t)$ para resolver integrales de expresiones de tipo $\sqrt{x^2 + a^2}$.

### 6. Sustitución por Fracciones Simples
Este método se utiliza para descomponer funciones racionales en una suma de fracciones más simples. Por ejemplo:

$$
\int \frac{1}{x^2 - 1} \, dx
$$

Podemos descomponer:

$$
\frac{1}{x^2 - 1} = \frac{1}{2} \left( \frac{1}{x-1} - \frac{1}{x+1} \right)
$$

Y luego integrar cada fracción por separado.

### 7. Integración Numérica
A veces no es posible encontrar una antiderivada exacta, por lo que se utilizan métodos **numéricos** para calcular el valor de la integral.

#### Regla de los Trapecios
La **Regla de los Trapecios** aproxima el área bajo una curva dividiendo la región en trapecios.

$$
\int_a^b f(x) \, dx \approx \frac{b-a}{2} [f(a) + f(b)]
$$

#### Regla de Simpson
La **Regla de Simpson** utiliza parabolas para aproximar el área bajo la curva y es más precisa que la regla de los trapecios.

$$
\int_a^b f(x) \, dx \approx \frac{b-a}{6} [f(a) + 4f\left( \frac{a+b}{2} \right) + f(b)]
$$

### Estimación de Error
La **estimación del error** es importante para conocer la precisión de las aproximaciones numéricas. Tanto la Regla del Trapecio como la de Simpson tienen fórmulas específicas para calcular el error en función de la derivada de orden superior de la función que se está integrando.
