

## Función Real de Variable Vectorial Diferenciable
Una función $f: \mathbb{R}^n \to \mathbb{R}$ es **diferenciable** en un punto $\mathbf{p_0} \in \mathbb{R}^n$ si puede aproximarse localmente por un plano que pasa por el punto. En términos más formales, se dice que $f$ es diferenciable en $\mathbf{p_0}$ si existe una **aproximación lineal** para el incremento de la función, es decir:

$$
f(\mathbf{p_0} + \mathbf{h}) = f(\mathbf{p_0}) + \nabla f(\mathbf{p_0}) \cdot \mathbf{h} + o(\|\mathbf{h}\|)
$$

donde $\nabla f(\mathbf{p_0})$ es el **gradiente** de $f$ en $\mathbf{p_0}$ y el término $o(\|\mathbf{h}\|)$ representa los términos de orden superior que son insignificantes cuando $\|\mathbf{h}\| \to 0$.

### Propiedades de la Diferenciabilidad (con demostración)

1. **Continuidad de Función Diferenciable**:
   Si $f$ es diferenciable en $\mathbf{p_0}$, entonces $f$ es **continua** en $\mathbf{p_0}$. Esto se deduce directamente de la definición de diferenciabilidad, ya que la aproximación lineal implica que:

   $$
   \lim_{\mathbf{h} \to 0} f(\mathbf{p_0} + \mathbf{h}) = f(\mathbf{p_0})
   $$

2. **Unicidad del Plano Tangente**:
   Si $f$ es diferenciable en $\mathbf{p_0}$, existe un único plano tangente que aproxima la función en ese punto. Esto se debe a que la existencia de derivadas parciales continuas implica un comportamiento suave de la superficie.

### Condición Suficiente para la Diferenciabilidad
Una condición suficiente para que una función $f: \mathbb{R}^n \to \mathbb{R}$ sea diferenciable en un punto es que todas sus **derivadas parciales** existan y sean **continuas** en una vecindad de ese punto. Esta condición garantiza la existencia del plano tangente y la continuidad de la derivada.

## Propiedad Geométrica: Plano Tangente a una Superficie $z = f(x, y)$
Para una función de dos variables $z = f(x, y)$, si la función es diferenciable en un punto $(x_0, y_0)$, el **plano tangente** a la superficie en el punto $(x_0, y_0, z_0)$ se puede describir por:

$$
z - z_0 = f_x(x_0, y_0) (x - x_0) + f_y(x_0, y_0) (y - y_0)
$$

donde $f_x$ y $f_y$ son las derivadas parciales con respecto a $x$ e $y$, respectivamente.

## Teorema del Valor Medio del Cálculo Diferencial (Sin Demostración)
El **teorema del valor medio** para funciones de varias variables establece que, bajo ciertas condiciones de continuidad y diferenciabilidad, existe un punto en el cual la derivada direccional coincide con una variación promedio en la función. Geométricamente, esto puede interpretarse como la existencia de un plano tangente paralelo a un incremento promedio.

## Diferencial Total
El **diferencial total** de una función $f(x_1, x_2, \ldots, x_n)$ se define como:

$$
df = \frac{\partial f}{\partial x_1} dx_1 + \frac{\partial f}{\partial x_2} dx_2 + \cdots + \frac{\partial f}{\partial x_n} dx_n
$$

Este diferencial total representa una aproximación lineal de cómo cambia la función en función de los pequeños cambios en cada variable.

## Función Vectorial de Variable Vectorial Diferenciable
Para una función vectorial $\mathbf{f}: \mathbb{R}^n \to \mathbb{R}^m$, se dice que es **diferenciable** si cada una de sus componentes es diferenciable. 

### Matriz Jacobiana
La **Matriz Jacobiana** de $\mathbf{f}$ en el punto $\mathbf{p_0}$ se define como:

$$
J_f(\mathbf{p_0}) = \begin{bmatrix}
\frac{\partial f_1}{\partial x_1} & \frac{\partial f_1}{\partial x_2} & \cdots & \frac{\partial f_1}{\partial x_n} \\
\frac{\partial f_2}{\partial x_1} & \frac{\partial f_2}{\partial x_2} & \cdots & \frac{\partial f_2}{\partial x_n} \\
\vdots & \vdots & \ddots & \vdots \\
\frac{\partial f_m}{\partial x_1} & \frac{\partial f_m}{\partial x_2} & \cdots & \frac{\partial f_m}{\partial x_n}
\end{bmatrix}
$$

La **Jacobiana** contiene toda la información acerca de las derivadas parciales de la función.

## Funciones Compuestas y Regla de la Cadena
Si $z = f(u_1, u_2, \ldots, u_m)$ y $u_i = g_i(x_1, x_2, \ldots, x_n)$, entonces la derivada de la función compuesta se puede calcular mediante la **Regla de la Cadena**:

$$
\frac{\partial z}{\partial x_j} = \sum_{i=1}^m \frac{\partial f}{\partial u_i} \frac{\partial u_i}{\partial x_j}
$$

## Funciones Implícitas y Teorema de la Función Implícita
Para una ecuación de la forma $F(x, y) = 0$:
- Existe una función implícita $y = g(x)$ si $\frac{\partial F}{\partial y} \neq 0$ en un punto dado.

Para $F(x, y, z) = 0$, la superficie se puede representar localmente como $z = g(x, y)$ si $\frac{\partial F}{\partial z} \neq 0$.

### Plano Tangente a una Superficie Definida Implícitamente
Si la superficie está definida implícitamente por $F(x, y, z) = 0$, el plano tangente en un punto $(x_0, y_0, z_0)$ está dado por:

$$
F_x (x - x_0) + F_y (y - y_0) + F_z (z - z_0) = 0
$$

donde $F_x, F_y, F_z$ son las derivadas parciales de $F$.





## Máximos y Mínimos de Funciones Reales de Varias Variables
Una función $f(x_1, x_2, \ldots, x_n)$ puede tener **máximos y mínimos locales** (relativos) o **máximos y mínimos globales** (absolutos).

- **Máximo Relativo**: Un punto $\mathbf{p_0}$ es un máximo relativo si existe una vecindad en la que $f(\mathbf{p_0}) \geq f(\mathbf{p})$ para todos los puntos $\mathbf{p}$ en esa vecindad.
- **Mínimo Relativo**: De forma similar, un punto es un mínimo relativo si $f(\mathbf{p_0}) \leq f(\mathbf{p})$.

## Puntos Críticos
Los **puntos críticos** de una función son aquellos puntos donde todas las derivadas parciales son cero, es decir:

$$
\nabla f = (f_x, f_y, \ldots, f_n) = \mathbf{0}
$$

Estos puntos son candidatos para ser máximos, mínimos o puntos de silla.

## Condición Necesaria para la Existencia de Extremos Relativos
Si $f$ tiene un extremo relativo en un punto $\mathbf{p_0}$ y las derivadas parciales existen en $\mathbf{p_0}$, entonces $\mathbf{p_0}$ es un punto crítico, es decir:

$$
f_x(\mathbf{p_0}) = f_y(\mathbf{p_0}) = \cdots = f_n(\mathbf{p_0}) = 0
$$

## Condición Suficiente para la Existencia de Extremos Relativos
Para determinar si un punto crítico es un **máximo**, **mínimo** o un **punto de silla**, se utiliza la **matriz Hessiana**:

$$
H(f) = \begin{bmatrix}
f_{xx} & f_{xy} & \cdots & f_{xn} \\
f_{yx} & f_{yy} & \cdots & f_{yn} \\
\vdots & \vdots & \ddots & \vdots \\
f_{nx} & f_{ny} & \cdots & f_{nn}
\end{bmatrix}
$$

- **Máximo Relativo**: Si la Hessiana es **definida negativa**.
- **Mínimo Relativo**: Si la Hessiana es **definida positiva**.
- **Punto de Silla**: Si la Hessiana no es definida positiva ni definida negativa.





