
# CÓNICAS

## Definición de Cónica
Las **cónicas** son las curvas obtenidas al intersectar un cono con un plano. Existen cuatro tipos fundamentales de cónicas: **circunferencia**, **elipse**, **hipérbola**, y **parábola**.

### 1. Circunferencia
#### Definición
Una **circunferencia** es el conjunto de todos los puntos que están a una distancia constante (radio) de un punto fijo (centro).

#### Ecuación Canónica
La **ecuación canónica** de una circunferencia con centro en el origen y radio $r$ es:

$$
x^2 + y^2 = r^2
$$

#### Ecuación General
La **ecuación general** de una circunferencia con centro en $(h, k)$ y radio $r$ es:

$$
(x - h)^2 + (y - k)^2 = r^2
$$

### 2. Elipse
#### Definición
Una **elipse** es el conjunto de puntos cuya suma de distancias a dos puntos fijos llamados **focos** es constante.

#### Ecuación Canónica
La **ecuación canónica** de una elipse con ejes mayores alineados con los ejes coordenados es:

$$
\frac{x^2}{a^2} + \frac{y^2}{b^2} = 1
$$

donde $a > b$ para una elipse horizontal y $b > a$ para una elipse vertical.

### 3. Hipérbola
#### Definición
Una **hipérbola** es el conjunto de puntos cuya diferencia de distancias a dos puntos fijos llamados **focos** es constante.

#### Ecuación Canónica
La **ecuación canónica** de una hipérbola con sus ejes alineados con los coordenados es:

$$
\frac{x^2}{a^2} - \frac{y^2}{b^2} = 1
$$

Esta hipérbola tiene sus **ramas** en las direcciones del eje $x$. Si el término con $y$ es positivo y el de $x$ es negativo, las ramas están alineadas con el eje $y$:

$$
\frac{y^2}{b^2} - \frac{x^2}{a^2} = 1
$$

### 4. Parábola
#### Definición
Una **parábola** es el conjunto de puntos que equidistan de un punto fijo llamado **foco** y de una línea fija llamada **directriz**.

#### Ecuación Canónica
La **ecuación canónica** de una parábola con vértice en el origen es:

$$
y^2 = 4px \quad \text{o} \quad x^2 = 4py
$$

donde $p$ es la distancia del vértice al foco.

## Propiedades de las Cónicas
- Las **circunferencias** tienen todos los puntos a igual distancia del centro.
- Las **elipses** y **hipérbolas** tienen dos **focos** que determinan la curva.
- La **parábola** tiene un **foco** y una **directriz**, que determinan su forma.

## Recta Tangente a una Cónica
La **tangente** a una cónica en un punto es la recta que toca la cónica en ese único punto sin cruzarla.

### Ecuación de la Recta Tangente
- Para una elipse con ecuación canónica:

  $$
  \frac{x^2}{a^2} + \frac{y^2}{b^2} = 1
  $$

  La ecuación de la tangente en el punto $(x_0, y_0)$ es:

  $$
  \frac{x x_0}{a^2} + \frac{y y_0}{b^2} = 1
  $$

## Regla del Desdoblamiento
La **regla del desdoblamiento** es una técnica utilizada para encontrar las ecuaciones de las tangentes a cónicas y otras curvas analizando la simetría y utilizando puntos conocidos sobre la cónica. Esta técnica es útil especialmente en problemas donde se requiere una tangente específica sin necesidad de derivación explícita.


# SUPERFICIE Y LÍNEA

## Definición de Superficie y Línea
- Una **superficie** es una figura bidimensional que puede describirse mediante una ecuación en $\mathbb{R}^3$.
- Una **línea** es una curva unidimensional que puede ser definida mediante ecuaciones vectoriales o paramétricas.

## Superficies Cónicas
Una **superficie cónica** es una superficie generada por todas las líneas rectas que pasan por un punto fijo (el **vértice**) y que interceptan una curva base.

### Ecuación de una Superficie Cónica
La ecuación general de un cono con vértice en el origen es:

$$
z^2 = x^2 + y^2
$$

## Superficies Cilíndricas
Una **superficie cilíndrica** es una superficie generada por una línea que se mueve paralelamente a sí misma a lo largo de una curva directriz.

### Ejemplo
Un **cilindro** con eje en el eje $z$ y radio $r$ tiene la ecuación:

$$
x^2 + y^2 = r^2
$$

## Superficies Cuádricas
Las **cuádricas** son superficies definidas por ecuaciones cuadráticas en tres variables. Ejemplos comunes de superficies cuádricas incluyen:

### 1. Superficie Esférica
Una **esfera** con centro en $(h, k, l)$ y radio $r$ se define como:

$$
(x - h)^2 + (y - k)^2 + (z - l)^2 = r^2
$$

### 2. Elipsoide
Un **elipsoide** es la generalización de una elipse a tres dimensiones. Su ecuación general es:

$$
\frac{x^2}{a^2} + \frac{y^2}{b^2} + \frac{z^2}{c^2} = 1
$$

### 3. Hiperboloide de una Hoja
Un **hiperboloide de una hoja** tiene la forma:

$$
\frac{x^2}{a^2} + \frac{y^2}{b^2} - \frac{z^2}{c^2} = 1
$$

Este hiperboloide tiene una forma de "silla de montar" y se extiende infinitamente.

### 4. Hiperboloide de Dos Hojas
Un **hiperboloide de dos hojas** tiene la ecuación:

$$
-\frac{x^2}{a^2} - \frac{y^2}{b^2} + \frac{z^2}{c^2} = 1
$$

Esta superficie se compone de dos partes separadas (hojas).

### 5. Paraboloides
- **Paraboloide Elíptico**: Tiene la forma de una parábola que se extiende en dos direcciones:

  $$
  z = \frac{x^2}{a^2} + \frac{y^2}{b^2}
  $$

- **Paraboloide Hiperbólico**: Tiene una forma de "silla de montar":

  $$
  z = \frac{x^2}{a^2} - \frac{y^2}{b^2}
  $$

Este tipo de superficie se encuentra en aplicaciones como la óptica y diseño estructural debido a sus propiedades de reflexión y estabilidad.




