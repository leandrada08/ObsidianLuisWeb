
# INTEGRAL INDEFINIDA

## Antiderivada
La **antiderivada** de una función$f(x)$es una función$F(x)$tal que:

$$
F'(x) = f(x)
$$

El proceso de encontrar una antiderivada se denomina **antidiferenciación** o **integración indefinida**.

## Definición de Integral Indefinida
La **integral indefinida** de una función$f(x)$es el conjunto de todas sus antiderivadas, denotado como:

$$
\int f(x) \, dx = F(x) + C
$$

donde$C$es la **constante de integración**. La constante es necesaria ya que la derivada de cualquier constante es cero, y las antiderivadas difieren por una constante.

## Propiedades de la Integral Indefinida
Las **propiedades** básicas de la integral indefinida incluyen:

1. **Linealidad**: 
  $$
   \int [a f(x) + b g(x)] \, dx = a \int f(x) \, dx + b \int g(x) \, dx
  $$
   donde$a$y$b$son constantes.

2. **Constante multiplicativa**:
  $$
   \int k f(x) \, dx = k \int f(x) \, dx
  $$

Estas propiedades son útiles para simplificar la integración de funciones complejas, permitiendo la separación en términos manejables.

## Regla de la Cadena para la Antidiferenciación
Para integrar una **composición de funciones**, se aplica la **regla de la cadena inversa** o el **método de sustitución**. Dada una función de la forma$f(g(x))g'(x)$, la integral se calcula como:

$$
\int f(g(x)) g'(x) \, dx = \int f(u) \, du, \quad \text{con } u = g(x)
$$

Este método permite simplificar integrales en las que la función tiene una estructura compuesta, siendo muy común en problemas de ingeniería donde se necesita revertir operaciones de derivación compuestas.

# INTEGRAL DEFINIDA

## Suma de Riemann y la Integral Definida
La **suma de Riemann** es una aproximación de la **integral definida** de una función$f$sobre un intervalo$[a, b]$. Se define como:

$$
\int_a^b f(x) \, dx = \lim_{n \to \infty} \sum_{i=1}^n f(x_i^*) \Delta x
$$

donde$\Delta x = \frac{b-a}{n}$es el ancho de los subintervalos, y$x_i^*$es un punto dentro del i-ésimo subintervalo. En el límite, la suma de Riemann se convierte en la **integral definida**, proporcionando una medida exacta del área bajo la curva de$f(x)$desde$a$hasta$b$.

## Área de una Región Plana Situada Debajo de una Curva
La **integral definida** también se interpreta como el área de la región situada bajo la curva de$f(x)$y sobre el eje$x$entre los límites$a$y$b$, siempre y cuando$f(x) \geq 0$.

$$
A = \int_a^b f(x) \, dx
$$

Esta interpretación geométrica es fundamental para resolver problemas de áreas y volúmenes en ingeniería.

## Propiedades de la Integral Definida
1. **Aditividad del Intervalo**: 
  $$
   \int_a^b f(x) \, dx + \int_b^c f(x) \, dx = \int_a^c f(x) \, dx
  $$
2. **Cambio de Límites de Integración**:
  $$
   \int_a^b f(x) \, dx = -\int_b^a f(x) \, dx
  $$
3. **Constante por Integral**:
  $$
   \int_a^b k f(x) \, dx = k \int_a^b f(x) \, dx
  $$

## Teorema del Valor Medio para Integrales
El **Teorema del Valor Medio para Integrales** establece que si$f$es continua en el intervalo$[a, b]$, entonces existe un punto$c \in [a, b]$tal que:

$$
\int_a^b f(x) \, dx = f(c) (b - a)
$$

Este teorema se usa para demostrar que existe un valor promedio de la función que representa el área bajo la curva.

## Teorema Fundamental del Cálculo
El **Teorema Fundamental del Cálculo** vincula la derivación y la integración:

1. **Primera Parte**: Si$F$es una antiderivada de$f$en$[a, b]$, entonces:

  $$
   \int_a^b f(x) \, dx = F(b) - F(a)
  $$

2. **Segunda Parte**: Si$f$es continua en$[a, b]$, entonces la función:

  $$
   F(x) = \int_a^x f(t) \, dt
  $$

   es derivable y su derivada es$f(x)$.

Este teorema proporciona el fundamento para calcular áreas y resolver problemas que implican acumulación de cambios.

