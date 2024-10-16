
# DERIVADA

## Definición de Recta Tangente
La **recta tangente** a una curva en un punto $P(a, f(a))$ es una recta que toca la curva únicamente en ese punto sin cruzarla. La pendiente de la recta tangente se corresponde con la **derivada** de la función en ese punto.

### Ecuación de la Recta Tangente
La ecuación de la recta tangente a la curva $y = f(x)$ en el punto $(a, f(a))$ es:

$$
y - f(a) = f'(a) (x - a)
$$

donde $f'(a)$ representa la derivada de la función en $x = a$.

## Derivada de una Función
La **derivada** de una función $f(x)$ en un punto $a$ es el límite del cociente incremental:

$$
f'(a) = \lim_{h \to 0} \frac{f(a+h) - f(a)}{h}
$$

Esto se interpreta como la pendiente de la recta tangente a la curva en el punto $(a, f(a))$.

### Interpretación Geométrica y Física
- **Geométrica**: La derivada $f'(x)$ en un punto da la pendiente de la curva en ese punto.
- **Física**: Si $f(x)$ representa la posición de un objeto en función del tiempo, entonces $f'(x)$ representa la **velocidad** del objeto.

## Derivadas Laterales
Las **derivadas laterales** se refieren a las pendientes obtenidas al acercarse al punto desde la izquierda ($f'_-(a)$) o desde la derecha ($f'_+(a)$). La derivada existe si ambos límites laterales son iguales.

## Derivabilidad y Continuidad
- Si una función es **derivable** en un punto, necesariamente es **continua** en ese punto.
- Sin embargo, una función continua no siempre es derivable (por ejemplo, en puntos angulosos).

## Reglas de Derivación
### 1. Derivada de una Constante
$$
f(x) = c \implies f'(x) = 0
$$

### 2. Regla de Potencia
$$
f(x) = x^n \implies f'(x) = n x^{n-1}
$$

### 3. Regla del Producto
$$
(f \cdot g)' = f' \cdot g + f \cdot g'
$$

### 4. Regla del Cociente
$$
\left( \frac{f}{g} \right)' = \frac{f' \cdot g - f \cdot g'}{g^2}, \quad g(x) \neq 0
$$

### 5. Derivada de una Función Compuesta (Regla de la Cadena)
Si $y = f(g(x))$, entonces:

$$
f'(x) = f'(g(x)) \cdot g'(x)
$$

## Derivadas de Funciones Trigonométricas
- **Seno**: \(\frac{d}{dx} \sin(x) = \cos(x)\)
- **Coseno**: \(\frac{d}{dx} \cos(x) = -\sin(x)\)
- **Tangente**: \(\frac{d}{dx} \tan(x) = \sec^2(x)\)

## Derivadas de Orden Superior
Las **derivadas de orden superior** son derivadas sucesivas de una función. La segunda derivada, denotada como $f''(x)$, describe la **concavidad** de la función.

## Derivada de la Función Inversa
Si $f(x)$ tiene una función inversa $f^{-1}(x)$, entonces la derivada de la inversa se calcula como:

$$
\frac{d}{dx} f^{-1}(x) = \frac{1}{f'(f^{-1}(x))}
$$

## Derivada de las Funciones Trigonométricas Inversas
- **Arcoseno**: \(\frac{d}{dx} \sin^{-1}(x) = \frac{1}{\sqrt{1-x^2}}\)
- **Arcocoseno**: \(\frac{d}{dx} \cos^{-1}(x) = -\frac{1}{\sqrt{1-x^2}}\)

## Derivación Implícita
Se utiliza para derivar funciones que no están explícitamente despejadas en términos de $y$:

Ejemplo: Si $x^2 + y^2 = 1$, la derivada implícita es:

$$
2x + 2y \frac{dy}{dx} = 0 \implies \frac{dy}{dx} = -\frac{x}{y}
$$

## Razón de Cambio
La **razón de cambio** mide cómo cambia una cantidad con respecto a otra. En física, la velocidad es la razón de cambio de la posición respecto al tiempo.

## Diferencial
El **diferencial** de una función $f$ se denota como $dy = f'(x) dx$. Se usa en aproximaciones lineales.

## Método de Newton para Aproximación de Ceros
El **método de Newton** es un procedimiento iterativo para encontrar aproximaciones de las raíces de una función $f(x)$:

$$
x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}
$$

# TEOREMAS DEL CÁLCULO DIFERENCIAL

## Teorema de Rolle
Si una función $f$ es continua en el intervalo \([a, b]\), derivable en \((a, b)\), y $f(a) = f(b)$, entonces existe un punto $c \in (a, b)$ tal que:

$$
f'(c) = 0
$$

## Teorema del Valor Medio
Para una función continua en \([a, b]\) y derivable en \((a, b)\), existe un punto $c \in (a, b)$ tal que:

$$
f'(c) = \frac{f(b) - f(a)}{b - a}
$$

Este teorema es útil en ingeniería para demostrar la existencia de un valor instantáneo igual al promedio en ciertos procesos.

## Funciones Crecientes y Decrecientes
- Una función es **creciente** si $f'(x) > 0$ en un intervalo.
- Es **decreciente** si $f'(x) < 0$.

## Formas Indeterminadas y Regla de L’Hôpital
Cuando una expresión tiene forma indeterminada como $\frac{0}{0}$ o $\frac{\infty}{\infty}$, se aplica la **Regla de L’Hôpital**:

$$
\lim_{x \to a} \frac{f(x)}{g(x)} = \lim_{x \to a} \frac{f'(x)}{g'(x)}
$$


# APLICACIONES DE LA DERIVADA

## Valores Máximos y Mínimos
### Condición Necesaria para Extremos Relativos
Si $f$ tiene un máximo o mínimo relativo en un punto $c$, entonces:

$$
f'(c) = 0
$$

### Condiciones Suficientes
- **Criterio de la Primera Derivada**: Si $f'$ cambia de signo de positivo a negativo en $c$, $f(c)$ es un **máximo**. Si cambia de negativo a positivo, es un **mínimo**.
- **Criterio de la Segunda Derivada**: Si $f''(c) > 0$, entonces $f(c)$ es un **mínimo**. Si $f''(c) < 0$, es un **máximo**.

## Problemas de Optimización
Se utilizan derivadas para encontrar máximos y mínimos de funciones en problemas prácticos, como minimizar costos o maximizar eficiencia.

## Concavidad y Puntos de Inflexión
- La función es **cóncava hacia arriba** si $f''(x) > 0$.
- **Cóncava hacia abajo** si $f''(x) < 0$.
- Un **punto de inflexión** ocurre donde la concavidad cambia, es decir, cuando $f''(x) = 0$ y cambia de signo.

## Aplicación en el Trazado de Curvas
La derivada permite identificar las propiedades fundamentales de una curva, como intervalos de crecimiento, máximos, mínimos, concavidad, y puntos de inflexión, para realizar un análisis detallado del comportamiento de la función.
