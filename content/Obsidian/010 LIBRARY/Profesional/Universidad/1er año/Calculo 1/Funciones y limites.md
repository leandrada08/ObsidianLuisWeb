

# Funciones
## Definición de Función
Una **función** es una relación entre dos conjuntos, donde a cada elemento del conjunto de partida (denominado **dominio**) se le asigna un único elemento del conjunto de llegada (**codominio**). Matemáticamente se denota como:

$$
f: A \to B
$$

donde $f(x)$ es la imagen de $x \in A$ en el conjunto $B$.

## Representaciones Gráficas
Las funciones pueden representarse de diversas formas: **algebraicamente** mediante ecuaciones, **gráficamente** mediante curvas en el plano cartesiano, o **tabularmente** mediante listas de pares ordenados.

Ejemplo: $f(x) = x^2$ se representa gráficamente como una parábola.

## Clasificación de Funciones
### 1. Funciones Polinomiales
Las **funciones polinomiales** se expresan en la forma:

$$
f(x) = a_n x^n + a_{n-1} x^{n-1} + \cdots + a_1 x + a_0
$$

donde los coeficientes $a_i$ son números reales y $n$ es un número natural. Ejemplo: $f(x) = 3x^3 + 2x - 5$.

### 2. Funciones Racionales
Una **función racional** es el cociente de dos polinomios:

$$
f(x) = \frac{P(x)}{Q(x)}
$$

con $Q(x) \neq 0$. Ejemplo: $f(x) = \frac{x^2 + 1}{x - 3}$.

### 3. Funciones Trascendentes
Las **funciones trascendentes** no son algebraicas y no pueden expresarse como raíces de polinomios. Ejemplos comunes incluyen las **exponenciales** ($e^x$), **logarítmicas** ($\ln(x)$), y **trigonométricas** ($\sin(x), \cos(x)$, etc.).

## Funciones Trigonométricas
Las funciones trigonométricas están definidas a partir de las relaciones entre los lados de un triángulo rectángulo. Las más comunes son:

- **Seno**: $\sin(x)$
- **Coseno**: $\cos(x)$
- **Tangente**: $\tan(x) = \frac{\sin(x)}{\cos(x)}$

Estas funciones tienen aplicaciones directas en problemas de ingeniería, como el análisis de ondas o el estudio de fenómenos periódicos.

## Álgebra de las Funciones
Se pueden realizar operaciones con funciones de forma similar a los números:

- **Suma**: $(f + g)(x) = f(x) + g(x)$
- **Resta**: $(f - g)(x) = f(x) - g(x)$
- **Multiplicación**: $(f \cdot g)(x) = f(x) \cdot g(x)$
- **Cociente**: $\left( \frac{f}{g} \right)(x) = \frac{f(x)}{g(x)}$, con $g(x) \neq 0$

## Composición de Funciones
La **composición de funciones** implica aplicar una función dentro de otra:

$$
(f \circ g)(x) = f(g(x))
$$

Esto se usa frecuentemente para modelar procesos en cadena en ingeniería, como transformaciones sucesivas de señales.

## Función Inversa
Una función $f$ tiene una **función inversa** $f^{-1}$ si cada valor del rango tiene exactamente un valor del dominio asociado. Se cumple:

$$
f(f^{-1}(x)) = x
$$

Ejemplo: La función exponencial $f(x) = e^x$ tiene como inversa el logaritmo natural $f^{-1}(x) = \ln(x)$.

## Funciones Trigonométricas Inversas
Las funciones trigonométricas también tienen inversas definidas para valores restringidos:

- **Arcoseno**: $\sin^{-1}(x)$
- **Arcocoseno**: $\cos^{-1}(x)$
- **Arcotangente**: $\tan^{-1}(x)$

Estas funciones son útiles para resolver ecuaciones trigonométricas y aparecen en problemas relacionados con ángulos y distancias.



# LÍMITES Y CONTINUIDAD

## Límite de una Función
El **límite** de una función describe el comportamiento de la función cuando el valor de la variable independiente se acerca a un punto determinado.

### Noción Intuitiva de Límite
Se dice que:

$$
\lim_{x \to a} f(x) = L
$$

si al acercarse $x$ a $a$, los valores de $f(x)$ se acercan a $L$.

### Definición Formal de Límite
Para todo número $\epsilon > 0$, existe un número $\delta > 0$ tal que si $0 < |x - a| < \delta$, entonces $|f(x) - L| < \epsilon$. Esta definición formal permite precisar el comportamiento cercano a un punto.

## Teoremas sobre Límites
Algunos teoremas importantes son:

1. **Límite de la Suma**: \(\lim_{x \to a} [f(x) + g(x)] = \lim_{x \to a} f(x) + \lim_{x \to a} g(x)\)
2. **Límite del Producto**: \(\lim_{x \to a} [f(x) \cdot g(x)] = \lim_{x \to a} f(x) \cdot \lim_{x \to a} g(x)\)
3. **Límite del Cociente**: \(\lim_{x \to a} \frac{f(x)}{g(x)} = \frac{\lim_{x \to a} f(x)}{\lim_{x \to a} g(x)}, g(a) \neq 0\)

## Límites Laterales
Los **límites laterales** nos indican el comportamiento de la función al acercarse a un punto $a$ desde la izquierda ($x \to a^-$) o desde la derecha ($x \to a^+$). Si ambos límites laterales son iguales, el límite existe y es ese valor.

## Límites de Funciones Trigonométricas
Las funciones trigonométricas tienen límites importantes, como el **límite fundamental trigonométrico**:

$$
\lim_{x \to 0} \frac{\sin(x)}{x} = 1
$$

Este límite es clave en el análisis de series y la aproximación de funciones en ingeniería.

## Funciones Continuas
Una función $f$ es **continua** en un punto $a$ si:

1. $f(a)$ está definida.
2. $\lim_{x \to a} f(x)$ existe.
3. $\lim_{x \to a} f(x) = f(a)$

### Propiedades de las Funciones Continuas
Las funciones continuas tienen propiedades importantes, como el **Teorema del Valor Intermedio**, que garantiza que si $f$ es continua en un intervalo \([a, b]\), entonces toma todos los valores entre $f(a)$ y $f(b)$.

## Discontinuidades
Una función puede tener distintos tipos de **discontinuidades**:

1. **Evitable**: Si se puede redefinir la función para que sea continua.
2. **De Salto**: Cuando los límites laterales existen, pero son diferentes.
3. **Infinita**: Cuando la función tiende a infinito en un punto.

## Asíntotas
### 1. Asíntotas Verticales
Las **asíntotas verticales** ocurren cuando la función crece sin límite al acercarse a un valor del dominio:

$$
\lim_{x \to a} f(x) = \pm \infty
$$

### 2. Asíntotas Horizontales
Una **asíntota horizontal** se presenta cuando el valor de la función se aproxima a una constante al extender el dominio hacia infinito:

$$
\lim_{x \to \infty} f(x) = L
$$
