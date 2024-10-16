

## Definición
Una **función real de $n$ variables reales** es una función que asigna un número real a cada $n$-tupla de números reales. Formalmente, una función $f: \mathbb{R}^n \to \mathbb{R}$ está definida como:

$$
f(x_1, x_2, \ldots, x_n)
$$

donde $(x_1, x_2, \ldots, x_n) \in \mathbb{R}^n$.

## Representación Gráfica
Para funciones con más de una variable:
- **$n = 1$**: La representación es una **curva** en el plano.
- **$n = 2$**: La representación es una **superficie** en el espacio tridimensional.
- **$n \geq 3$**: La representación gráfica no es fácil de visualizar, pero se utilizan **curvas de nivel** y **superficies de nivel** para comprender la estructura de la función.

## Curvas de Nivel y Superficies de Nivel
- **Curvas de Nivel**: Para una función de dos variables, una curva de nivel es el conjunto de puntos para los cuales la función tiene un valor constante. Matemáticamente:

  $$
  f(x, y) = c
  $$

  representa una curva en el plano $xy$, donde $c$ es una constante.

- **Superficies de Nivel**: Para una función de tres variables, una **superficie de nivel** es un conjunto de puntos en el espacio tridimensional donde la función toma un valor constante:

  $$
  f(x, y, z) = c
  $$

  Esto representa una superficie en el espacio $\mathbb{R}^3$.

## Conceptos Topológicos
- **Conjunto Abierto**: Un conjunto $U \subseteq \mathbb{R}^n$ es **abierto** si para cada punto $x \in U$, existe una esfera abierta centrada en $x$ que está contenida en $U$.
- **Bola**: En $\mathbb{R}^n$, una **bola abierta** de radio $r$ y centro en $x_0$ es el conjunto de puntos cuya distancia al centro es menor que $r$.

## Límite y Continuidad
- **Límite**: Se dice que el límite de una función $f(x_1, x_2, \ldots, x_n)$ es $L$ cuando $(x_1, x_2, \ldots, x_n)$ tiende a un punto $(a_1, a_2, \ldots, a_n)$:

  $$
  \lim_{(x_1, x_2, \ldots, x_n) \to (a_1, a_2, \ldots, a_n)} f(x_1, x_2, \ldots, x_n) = L
  $$

- **Continuidad**: La función $f$ es **continua** en un punto $(a_1, a_2, \ldots, a_n)$ si:

  $$
  \lim_{(x_1, x_2, \ldots, x_n) \to (a_1, a_2, \ldots, a_n)} f(x_1, x_2, \ldots, x_n) = f(a_1, a_2, \ldots, a_n)
  $$

## Derivadas Parciales
La **derivada parcial** de $f$ con respecto a la variable $x_i$ se define como el límite:

$$
\frac{\partial f}{\partial x_i} = \lim_{h \to 0} \frac{f(x_1, \ldots, x_i + h, \ldots, x_n) - f(x_1, x_2, \ldots, x_n)}{h}
$$

### Interpretación Geométrica
La derivada parcial con respecto a una variable representa la **pendiente** de la función en la dirección de esa variable, manteniendo las demás variables constantes.

### Derivadas Parciales Sucesivas
Las **derivadas parciales sucesivas** se obtienen derivando parcialmente varias veces:

$$
\frac{\partial^2 f}{\partial x_i \partial x_j}
$$

Estas derivadas se utilizan para construir el **hessiano**, una matriz importante en el análisis de máximos y mínimos.

## Derivada Direccional
La **derivada direccional** de $f$ en la dirección de un vector unitario $\mathbf{u} = (u_1, u_2, \ldots, u_n)$ se define como:

$$
D_{\mathbf{u}} f = \lim_{h \to 0} \frac{f(\mathbf{x} + h \mathbf{u}) - f(\mathbf{x})}{h}
$$

Esto puede calcularse usando la relación:

$$
D_{\mathbf{u}} f = \nabla f \cdot \mathbf{u}
$$

donde $\nabla f$ es el **gradiente** de $f$, que contiene todas las derivadas parciales.




