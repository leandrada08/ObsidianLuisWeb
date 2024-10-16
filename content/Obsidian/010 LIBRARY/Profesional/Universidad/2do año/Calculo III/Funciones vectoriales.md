

## Funciones Vectoriales
Una **función vectorial** es una función que asigna un vector a cada punto de su dominio. Por ejemplo, una función $\mathbf{F}: \mathbb{R} \to \mathbb{R}^3$ se puede escribir como:

$$
\mathbf{F}(t) = (f_1(t), f_2(t), f_3(t))
$$

donde $t \in \mathbb{R}$ y $f_1, f_2, f_3$ son funciones reales de una variable real.

### Límite y Continuidad de Funciones Vectoriales
- **Límite**: Se define como el límite componente a componente:

  $$
  \lim_{t \to t_0} \mathbf{F}(t) = \left( \lim_{t \to t_0} f_1(t), \lim_{t \to t_0} f_2(t), \lim_{t \to t_0} f_3(t) \right)
  $$

- **Continuidad**: Una función vectorial $\mathbf{F}(t)$ es continua en $t = t_0$ si:

  $$
  \lim_{t \to t_0} \mathbf{F}(t) = \mathbf{F}(t_0)
  $$

## Derivada de Funciones Vectoriales
La **derivada** de una función vectorial $\mathbf{F}(t)$ se define tomando la derivada componente a componente:

$$
\mathbf{F}'(t) = (f_1'(t), f_2'(t), f_3'(t))
$$

### Interpretación Geométrica
La derivada de una función vectorial representa la **tasa de cambio** del vector con respecto a la variable independiente, lo cual se puede interpretar como la **velocidad** si $\mathbf{F}(t)$ describe la posición de una partícula en el espacio.

## Curva Parametrizada y Recta Tangente
Una **curva parametrizada** en $\mathbb{R}^n$ se representa mediante una función vectorial:

$$
\mathbf{r}(t) = (x(t), y(t), z(t))
$$

La **recta tangente** a la curva en un punto se obtiene derivando la función vectorial y evaluándola en el valor del parámetro correspondiente:

$$
\mathbf{r}'(t_0) = (x'(t_0), y'(t_0), z'(t_0))
$$

La ecuación de la recta tangente se puede escribir como:

$$
\mathbf{T}(t) = \mathbf{r}(t_0) + t \mathbf{r}'(t_0)
$$

donde $\mathbf{r}(t_0)$ es el punto en la curva y $\mathbf{r}'(t_0)$ es el vector tangente.

## Campos Vectoriales
Un **campo vectorial** es una función que asigna un vector a cada punto del espacio. En $\mathbb{R}^2$ o $\mathbb{R}^3$, un campo vectorial se denota como:

$$
\mathbf{F}(x, y, z) = (P(x, y, z), Q(x, y, z), R(x, y, z))
$$

donde $P, Q, R$ son funciones reales.

### Ejemplos Comunes de Campos Vectoriales
- **Campo Gravitacional**: Describe la fuerza gravitacional que actúa en un punto en el espacio.
- **Campo Eléctrico**: Describe la fuerza eléctrica que experimenta una carga en un punto en el espacio.











