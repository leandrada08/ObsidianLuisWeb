

## Integrales Paramétricas y Regla de Leibniz

### Integrales Paramétricas
Las **integrales paramétricas** se utilizan para evaluar integrales donde los límites de integración dependen de un parámetro. Si la integral tiene la forma:

$$
I(\alpha) = \int_{a(\alpha)}^{b(\alpha)} f(x, \alpha) \, dx
$$

### Regla de Leibniz
La **Regla de Leibniz** permite derivar una integral respecto a un parámetro:

$$
\frac{d}{d\alpha} \left( \int_{a(\alpha)}^{b(\alpha)} f(x, \alpha) \, dx \right) = f(b(\alpha), \alpha) b'(\alpha) - f(a(\alpha), \alpha) a'(\alpha) + \int_{a(\alpha)}^{b(\alpha)} \frac{\partial f}{\partial \alpha} \, dx
$$

## Integrales Dobles
Las **integrales dobles** se utilizan para calcular el volumen bajo una superficie definida por una función de dos variables. Para una función $f(x, y)$:

$$
\int \int_R f(x, y) \, dA
$$

donde $R$ es la región en el plano $xy$.

### Teorema del Valor Medio del Cálculo Integral
El **teorema del valor medio para integrales** establece que si $f$ es continua sobre una región $R$, entonces existe un punto $(x_0, y_0) \in R$ tal que:

$$
\int \int_R f(x, y) \, dA = f(x_0, y_0) A(R)
$$

donde $A(R)$ es el área de la región $R$.

## Teorema de Cambio de Variables: Aplicación en Coordenadas Polares
El **teorema de cambio de variables** permite evaluar integrales dobles en coordenadas más convenientes, como las **coordenadas polares**. En polares, los elementos de área se expresan como:

$$
dA = r \, dr \, d\theta
$$

Para una función $f(r, \theta)$:

$$
\int \int_R f(x, y) \, dA = \int_{\theta_1}^{\theta_2} \int_{r_1}^{r_2} f(r \cos\theta, r \sin\theta) \, r \, dr \, d\theta
$$

## Integrales Triples
Las **integrales triples** se utilizan para calcular el volumen dentro de un sólido definido por una función de tres variables. Para una función $f(x, y, z)$:

$$
\int \int \int_V f(x, y, z) \, dV
$$

### Teorema de Cambio de Variables: Coordenadas Cilíndricas y Esféricas

#### Coordenadas Cilíndricas
En **coordenadas cilíndricas** ($r, \theta, z$):

$$
dV = r \, dr \, d\theta \, dz
$$

#### Coordenadas Esféricas
En **coordenadas esféricas** ($\rho, \phi, \theta$):

$$
dV = \rho^2 \sin\phi \, d\rho \, d\phi \, d\theta
$$

## Aplicaciones de las Integrales Múltiples
- **Área de una Región Plana**: Utilizando una integral doble para calcular el área bajo una curva.
- **Volumen de un Sólido**: Utilizando integrales triples.
- **Cálculo de Masa**: Si una densidad $\rho(x, y, z)$ está definida, la masa se obtiene mediante:

  $$
  M = \int \int \int_V \rho(x, y, z) \, dV
  $$

- **Centro de Masa**: Utilizando las coordenadas del centroide:

  $$
  \bar{x} = \frac{1}{M} \int \int \int_V x \rho(x, y, z) \, dV
  $$

- **Momento de Inercia**: Se define respecto a un eje específico, por ejemplo:

  $$
  I_z = \int \int \int_V (x^2 + y^2) \rho(x, y, z) \, dV
  $$



## Curvas Regulares y Longitud de Arco
Una **curva regular** se define mediante una función vectorial diferenciable $\mathbf{r}(t)$ tal que $\mathbf{r}'(t) \neq \mathbf{0}$. La **longitud de arco** de una curva $C$ parametrizada por $t \in [a, b]$ es:

$$
L = \int_a^b \|\mathbf{r}'(t)\| \, dt
$$

## Integrales Curvilíneas de Funciones Reales
Para una función real $f(x, y)$ definida sobre una curva $C$, la **integral curvilínea** de $f$ a lo largo de $C$ es:

$$
\int_C f(x, y) \, ds
$$

donde $ds = \|\mathbf{r}'(t)\| \, dt$ es el elemento de longitud de arco.

## Integrales Curvilíneas de Campos Vectoriales
Para un campo vectorial $\mathbf{F} = (P, Q)$ y una curva $C$ parametrizada por $\mathbf{r}(t)$:

$$
\int_C \mathbf{F} \cdot d\mathbf{r} = \int_a^b (P(x(t), y(t)) x'(t) + Q(x(t), y(t)) y'(t)) \, dt
$$

### Aplicaciones de las Integrales Curvilíneas
- **Masa de un Alambre**: Si el alambre tiene una densidad lineal $\rho(s)$:

  $$
  M = \int_C \rho(s) \, ds
  $$

- **Trabajo de una Fuerza**: Si una fuerza $\mathbf{F}$ actúa a lo largo de una trayectoria $C$:

  $$
  W = \int_C \mathbf{F} \cdot d\mathbf{r}
  $$

## Teorema de Gauss-Green (Enunciado)
El **Teorema de Green** relaciona una integral de línea alrededor de una curva cerrada $C$ con una integral doble sobre la región $D$ que limita $C$:

$$
\oint_C (P dx + Q dy) = \int \int_D \left( \frac{\partial Q}{\partial x} - \frac{\partial P}{\partial y} \right) \, dA
$$



## Superficies Regulares y Área de Superficie
Una **superficie regular** en $\mathbb{R}^3$ puede parametrizarse mediante una función vectorial $\mathbf{r}(u, v)$. El **área de una superficie** parametrizada por $(u, v) \in D$ se calcula como:

$$
A = \int \int_D \|\mathbf{r}_u \times \mathbf{r}_v\| \, dudv
$$

donde $\mathbf{r}_u$ y $\mathbf{r}_v$ son las derivadas parciales de la parametrización con respecto a $u$ y $v$.

## Integrales de Superficie de Funciones Reales
Para una función $f(x, y, z)$ definida sobre una superficie $S$, la **integral de superficie** es:

$$
\int \int_S f(x, y, z) \, dS
$$

donde $dS = \|\mathbf{r}_u \times \mathbf{r}_v\| \, dudv$ es el elemento de área.

## Integrales de Superficie de Campos Vectoriales
Para un campo vectorial $\mathbf{F}$ y una superficie $S$ con un vector normal unitario $\mathbf{n}$:

$$
\int \int_S \mathbf{F} \cdot \mathbf{n} \, dS
$$

Esto se conoce como el **flujo** del campo vectorial a través de la superficie.

### Aplicaciones de las Integrales de Superficie
- **Masa de una Lámina**: Si una lámina tiene densidad superficial $\rho(x, y, z)$:

  $$
  M = \int \int_S \rho(x, y, z) \, dS
  $$

- **Flujo de un Vector**: El flujo de un campo $\mathbf{F}$ a través de una superficie se interpreta como la cantidad de campo que atraviesa la superficie.

## Teorema de Gauss-Ostrogradski (Divergencia)
El **teorema de Gauss-Ostrogradski** (o teorema de la divergencia) relaciona la integral de superficie de un campo vectorial con la integral triple de su divergencia en el volumen limitado por la superficie:

$$
\int \int_S \mathbf{F} \cdot \mathbf{n} \, dS = \int \int \int_V (\nabla \cdot \mathbf{F}) \, dV
$$

donde $S$ es la frontera del volumen $V$.
