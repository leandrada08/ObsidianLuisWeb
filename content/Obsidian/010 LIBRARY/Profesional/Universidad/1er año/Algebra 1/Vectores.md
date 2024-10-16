
# VECTORES EN $\mathbb{R}^n$

## Definición de Vector
Un **vector** en $\mathbb{R}^n$ se representa como un conjunto ordenado de $n$ números reales:

$$
\mathbf{v} = (v_1, v_2, \ldots, v_n)
$$

Los números $v_1, v_2, \ldots, v_n$ se denominan **componentes** del vector.

## Igualdad de Vectores
Dos vectores $\mathbf{u} = (u_1, u_2, \ldots, u_n)$ y $\mathbf{v} = (v_1, v_2, \ldots, v_n)$ son **iguales** si y solo si:

$$
u_i = v_i, \quad \forall i = 1, 2, \ldots, n
$$

## Operaciones con Vectores

### 1. Suma de Vectores
La **suma** de dos vectores $\mathbf{u}$ y $\mathbf{v}$ es:

$$
\mathbf{u} + \mathbf{v} = (u_1 + v_1, u_2 + v_2, \ldots, u_n + v_n)
$$

### 2. Producto por un Escalar
El **producto de un vector** $\mathbf{v}$ por un escalar $k$ es:

$$
k \mathbf{v} = (k v_1, k v_2, \ldots, k v_n)
$$

## Propiedades de los Vectores
- **Conmutatividad**: $\mathbf{u} + \mathbf{v} = \mathbf{v} + \mathbf{u}$
- **Asociatividad**: $(\mathbf{u} + \mathbf{v}) + \mathbf{w} = \mathbf{u} + (\mathbf{v} + \mathbf{w})$
- **Elemento neutro**: Existe un vector $\mathbf{0} = (0, 0, \ldots, 0)$ tal que $\mathbf{v} + \mathbf{0} = \mathbf{v}$
- **Elemento opuesto**: Para cada vector $\mathbf{v}$, existe un vector $-\mathbf{v}$ tal que $\mathbf{v} + (-\mathbf{v}) = \mathbf{0}$

## Producto Escalar
El **producto escalar** (o producto punto) de dos vectores $\mathbf{u} = (u_1, u_2, \ldots, u_n)$ y $\mathbf{v} = (v_1, v_2, \ldots, v_n)$ se define como:

$$
\mathbf{u} \cdot \mathbf{v} = u_1 v_1 + u_2 v_2 + \cdots + u_n v_n
$$

El producto escalar tiene varias propiedades importantes:
- **Conmutatividad**: $\mathbf{u} \cdot \mathbf{v} = \mathbf{v} \cdot \mathbf{u}$
- **Distribución respecto a la suma**: $\mathbf{u} \cdot (\mathbf{v} + \mathbf{w}) = \mathbf{u} \cdot \mathbf{v} + \mathbf{u} \cdot \mathbf{w}$

## Paralelismo y Ortogonalidad
- Dos vectores $\mathbf{u}$ y $\mathbf{v}$ son **paralelos** si existe un escalar $k$ tal que $\mathbf{u} = k \mathbf{v}$.
- Dos vectores son **ortogonales** si su producto escalar es cero: $\mathbf{u} \cdot \mathbf{v} = 0$.

## Norma o Módulo de un Vector
La **norma** (o **módulo**) de un vector $\mathbf{v} = (v_1, v_2, \ldots, v_n)$ se denota como $\|\mathbf{v}\|$ y se calcula como:

$$
\|\mathbf{v}\| = \sqrt{v_1^2 + v_2^2 + \cdots + v_n^2}
$$

## Ángulo entre Vectores
El **ángulo** $\theta$ entre dos vectores $\mathbf{u}$ y $\mathbf{v}$ se determina usando el producto escalar:

$$
\cos(\theta) = \frac{\mathbf{u} \cdot \mathbf{v}}{\|\mathbf{u}\| \|\mathbf{v}\|}
$$

## Proyección Vectorial y Escalar
- **Proyección Escalar** de $\mathbf{u}$ sobre $\mathbf{v}$:

  $$
  \text{proj}_{\mathbf{v}}(\mathbf{u}) = \frac{\mathbf{u} \cdot \mathbf{v}}{\|\mathbf{v}\|}
  $$

- **Proyección Vectorial** de $\mathbf{u}$ sobre $\mathbf{v}$:

  $$
  \text{Proj}_{\mathbf{v}}(\mathbf{u}) = \left( \frac{\mathbf{u} \cdot \mathbf{v}}{\mathbf{v} \cdot \mathbf{v}} \right) \mathbf{v}
  $$

## Producto Vectorial
El **producto vectorial** de dos vectores en $\mathbb{R}^3$, $\mathbf{u} = (u_1, u_2, u_3)$ y $\mathbf{v} = (v_1, v_2, v_3)$, se define como:

$$
\mathbf{u} \times \mathbf{v} = (u_2 v_3 - u_3 v_2, u_3 v_1 - u_1 v_3, u_1 v_2 - u_2 v_1)
$$

El resultado es un vector ortogonal tanto a $\mathbf{u}$ como a $\mathbf{v}$.

## Doble Producto Mixto
El **doble producto mixto** se define para tres vectores $\mathbf{u}, \mathbf{v}, \mathbf{w} \in \mathbb{R}^3$ como:

$$
(\mathbf{u} \times \mathbf{v}) \cdot \mathbf{w}
$$

Este producto tiene aplicaciones en la geometría del espacio, como el cálculo del volumen de un paralelepípedo.

# APLICACIONES DE VECTORES A LA GEOMETRÍA ANALÍTICA

## Ecuaciones de la Recta

### 1. Ecuación Vectorial de la Recta
La **ecuación vectorial** de una recta que pasa por un punto $\mathbf{r_0}$ y tiene un vector director $\mathbf{d}$ es:

$$
\mathbf{r}(t) = \mathbf{r_0} + t \mathbf{d}, \quad t \in \mathbb{R}
$$

### 2. Ecuación Paramétrica de la Recta
Dada la ecuación vectorial, las **ecuaciones paramétricas** son:

$$
x = x_0 + t d_1, \quad y = y_0 + t d_2, \quad z = z_0 + t d_3
$$

donde $(x_0, y_0, z_0)$ es un punto en la recta y $(d_1, d_2, d_3)$ son las componentes del vector director.

### 3. Ecuación Cartesiana de la Recta en $\mathbb{R}^2$
En $\mathbb{R}^2$, la **ecuación general** de la recta es:

$$
Ax + By + C = 0
$$

Y la **forma segmentaria** se utiliza cuando se conocen los interceptos con los ejes:

$$
\frac{x}{a} + \frac{y}{b} = 1
$$

### 4. Recta por Dos Puntos
La **ecuación de la recta** que pasa por dos puntos $A(x_1, y_1)$ y $B(x_2, y_2)$ se puede hallar usando el vector director:

$$
\mathbf{d} = (x_2 - x_1, y_2 - y_1)
$$

Y la ecuación vectorial es:

$$
\mathbf{r}(t) = (x_1, y_1) + t (x_2 - x_1, y_2 - y_1)
$$

## Ángulo entre Dos Rectas
El **ángulo** $\theta$ entre dos rectas viene dado por:

$$
\cos(\theta) = \frac{\mathbf{d_1} \cdot \mathbf{d_2}}{\|\mathbf{d_1}\| \|\mathbf{d_2}\|}
$$

donde $\mathbf{d_1}$ y $\mathbf{d_2}$ son los vectores directores de las rectas.

## Paralelismo y Ortogonalidad de Rectas
- Dos rectas son **paralelas** si sus vectores directores son **proporcionales**.
- Dos rectas son **ortogonales** si el producto escalar de sus vectores directores es cero.

## Ecuación del Plano

### 1. Ecuación Vectorial del Plano
La **ecuación vectorial** de un plano que pasa por un punto $\mathbf{r_0}$ y tiene vectores directores $\mathbf{u}$ y $\mathbf{v}$ es:

$$
\mathbf{r}(s, t) = \mathbf{r_0} + s \mathbf{u} + t \mathbf{v}, \quad s, t \in \mathbb{R}
$$

### 2. Ecuación Cartesiana del Plano
La **ecuación cartesiana** de un plano en $\mathbb{R}^3$ se escribe como:

$$
Ax + By + Cz + D = 0
$$

donde $(A, B, C)$ es un **vector normal** al plano.

## Paralelismo y Ortogonalidad de Planos
- Dos planos son **paralelos** si sus **vectores normales** son proporcionales.
- Son **ortogonales** si el producto escalar de sus vectores normales es cero.

## Paralelismo y Ortogonalidad entre Rectas y Planos
- Una **recta es paralela** a un plano si el vector director de la recta es ortogonal al vector normal del plano.
- Una **recta es ortogonal** a un plano si su vector director es paralelo al vector normal del plano.

## Distancias

### 1. Distancia de un Punto a una Recta
La **distancia** de un punto $P(x_1, y_1, z_1)$ a una recta viene dada por:

$$
d = \frac{\|\mathbf{AP} \times \mathbf{d}\|}{\|\mathbf{d}\|}
$$

donde $\mathbf{AP}$ es el vector desde un punto en la recta $A$ hasta el punto $P$, y $\mathbf{d}$ es el vector director de la recta.

### 2. Distancia de un Punto a un Plano
La **distancia** de un punto $P(x_1, y_1, z_1)$ a un plano $Ax + By + Cz + D = 0$ se calcula como:

$$
d = \frac{|A x_1 + B y_1 + C z_1 + D|}{\sqrt{A^2 + B^2 + C^2}}
$$

Esta fórmula es útil para encontrar la distancia mínima entre estructuras en el espacio tridimensional.
