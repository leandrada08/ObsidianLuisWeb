
# INTEGRALES IMPROPIAS Y APLICACIONES DE LA INTEGRAL DEFINIDA

## Integrales Impropias

### 1. Límites Infinitos de Integración
Una **integral impropia** ocurre cuando al menos uno de los límites de integración es infinito. Se define usando un límite:

$$
\int_a^\infty f(x) \, dx = \lim_{b \to \infty} \int_a^b f(x) \, dx
$$

Ejemplo:

$$
\int_1^\infty \frac{1}{x^2} \, dx = \lim_{b \to \infty} \int_1^b \frac{1}{x^2} \, dx = \lim_{b \to \infty} \left[ -\frac{1}{x} \right]_1^b = 1
$$

### 2. Discontinuidades Infinitas
Si la función tiene una **discontinuidad infinita** dentro del intervalo de integración, también se considera una integral impropia.

Ejemplo:

$$
\int_0^1 \frac{1}{\sqrt{x}} \, dx = \lim_{\epsilon \to 0^+} \int_\epsilon^1 \frac{1}{\sqrt{x}} \, dx = 2
$$

## Aplicaciones de la Integral Definida

### 1. Áreas de Regiones en el Plano
El **área** de una región en el plano delimitada por la curva $y = f(x)$, el eje $x$, y las líneas $x = a$ y $x = b$ se calcula como:

$$
A = \int_a^b f(x) \, dx
$$

### 2. Volúmenes de Sólidos de Revolución
Para hallar el **volumen** de un sólido generado por la revolución de una curva $y = f(x)$ alrededor del eje $x$:

$$
V = \pi \int_a^b [f(x)]^2 \, dx
$$

#### Ejemplo del Método de los Discos
Si se rota la región entre $f(x)$ y el eje $x$ de $x = a$ a $x = b$, el volumen es:

$$
V = \pi \int_a^b [f(x)]^2 \, dx
$$

### 3. Área de Superficie de Revolución
El **área de superficie** de un sólido generado por la revolución de una curva se calcula como:

$$
A = 2\pi \int_a^b f(x) \sqrt{1 + (f'(x))^2} \, dx
$$

Esta fórmula se aplica en problemas como calcular el área de un depósito o la superficie de un objeto tridimensional.

### 4. Longitud de un Arco de Curva
La **longitud del arco** de una curva $y = f(x)$ en el intervalo \([a, b]\) se calcula mediante:

$$
L = \int_a^b \sqrt{1 + (f'(x))^2} \, dx
$$

Este cálculo es útil en ingeniería para determinar la longitud de estructuras como puentes o cables.

#### Ejemplo
Para la curva $f(x) = x^2$ de $x = 0$ a $x = 1$:

$$
f'(x) = 2x, \quad L = \int_0^1 \sqrt{1 + (2x)^2} \, dx
$$

Este tipo de integral es frecuente en el diseño de trayectorias y análisis estructural.
