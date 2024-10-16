



# MATRICES

## Definición de Matriz
Una **matriz** es un arreglo rectangular de números, organizado en **filas** y **columnas**. Se denota típicamente como:

$$
A = \begin{bmatrix}
a_{11} & a_{12} & \cdots & a_{1n} \\
a_{21} & a_{22} & \cdots & a_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
a_{m1} & a_{m2} & \cdots & a_{mn}
\end{bmatrix}
$$

donde $a_{ij}$ representa el elemento de la fila $i$ y columna $j$.

## Tipos Particulares de Matrices
- **Matriz Cuadrada**: Tiene el mismo número de filas y columnas ($n \times n$).
- **Matriz Diagonal**: Es una matriz cuadrada en la cual todos los elementos fuera de la diagonal principal son cero.
- **Matriz Identidad ($I$)**: Es una matriz diagonal con todos los elementos de la diagonal principal iguales a 1.
- **Matriz Cero ($0$)**: Todos sus elementos son cero.

## Operaciones con Matrices

### 1. Suma
La **suma** de dos matrices $A$ y $B$ del mismo tamaño se define como la suma elemento a elemento:

$$
A + B = \begin{bmatrix} a_{ij} + b_{ij} \end{bmatrix}
$$

### 2. Producto por un Escalar
El **producto de una matriz** $A$ por un escalar $k$ es:

$$
kA = \begin{bmatrix} k a_{ij} \end{bmatrix}
$$

### 3. Producto de Matrices
El **producto de matrices** $A$ y $B$ es posible si el número de columnas de $A$ es igual al número de filas de $B$. El elemento $c_{ij}$ de la matriz producto $C$ se calcula como:

$$
c_{ij} = \sum_{k=1}^n a_{ik} b_{kj}
$$

### Propiedades de las Operaciones con Matrices
- **Asociatividad de la Suma**: $A + (B + C) = (A + B) + C$
- **Distributividad**: $k(A + B) = kA + kB$
- **Matriz Identidad**: $A I = A = I A$

## Matriz Transpuesta
La **matriz transpuesta** de una matriz $A$, denotada como $A^T$, se obtiene intercambiando filas por columnas:

$$
A = \begin{bmatrix} a_{ij} \end{bmatrix} \quad \implies \quad A^T = \begin{bmatrix} a_{ji} \end{bmatrix}
$$

## Matrices Simétricas y Antisimétricas
- **Matriz Simétrica**: $A = A^T$
- **Matriz Antisimétrica**: $A = -A^T$

## Partición de Matrices
Una **matriz particionada** es una matriz que se divide en submatrices menores. Esta técnica es útil para realizar cálculos simplificados y análisis de sistemas grandes.

## Operaciones Elementales de Fila
Las **operaciones elementales de fila** se utilizan para simplificar matrices:
1. **Intercambio de Filas**.
2. **Multiplicación de una Fila por un Escalar**.
3. **Suma de un Múltiplo de una Fila a Otra Fila**.

Estas operaciones son fundamentales para la eliminación de Gauss y la reducción de matrices.

## Matriz Elemental
Una **matriz elemental** es una matriz que se obtiene aplicando una sola operación elemental a la matriz identidad.

## Matrices Equivalentes por Filas
Dos matrices $A$ y $B$ son **equivalentes por filas** si se pueden obtener una de la otra mediante una serie de operaciones elementales de fila.

## Matriz Escalón Reducida por Fila
Una matriz está en **forma escalón reducida** si cumple las siguientes condiciones:
- Cada fila no nula tiene un 1 principal.
- El 1 principal de cada fila está a la derecha del 1 principal de la fila anterior.
- Todos los elementos bajo y sobre el 1 principal son ceros.

## Rango de una Matriz
El **rango** de una matriz es el número de filas no nulas en su forma escalón reducida. Representa el número máximo de columnas linealmente independientes.

## Matrices Inversibles
Una **matriz inversible** es una matriz cuadrada $A$ para la cual existe una matriz $A^{-1}$ tal que:

$$
A A^{-1} = I
$$

### Obtención de la Inversa por Gauss-Jordan
El **método de Gauss-Jordan** se utiliza para encontrar la inversa de una matriz $A$ aplicando operaciones elementales a la matriz aumentada $[A | I]$ hasta obtener $[I | A^{-1}]$.

# SISTEMAS DE ECUACIONES LINEALES

## Definición de Sistema de Ecuaciones Lineales
Un **sistema de ecuaciones lineales** es un conjunto de ecuaciones de la forma:

$$
\begin{cases}
a_{11}x_1 + a_{12}x_2 + \cdots + a_{1n}x_n = b_1 \\
a_{21}x_1 + a_{22}x_2 + \cdots + a_{2n}x_n = b_2 \\
\vdots \\
a_{m1}x_1 + a_{m2}x_2 + \cdots + a_{mn}x_n = b_m
\end{cases}
$$

### Expresión Escalar y Matricial
En **forma matricial**, un sistema lineal se expresa como:

$$
A \mathbf{x} = \mathbf{b}
$$

donde:
- $A$ es la matriz de coeficientes.
- $\mathbf{x}$ es el vector de incógnitas.
- $\mathbf{b}$ es el vector de términos independientes.

## Definición de Solución
Una **solución** de un sistema de ecuaciones lineales es un conjunto de valores para las incógnitas que satisface todas las ecuaciones del sistema.

## Clasificación de los Sistemas
- **Sistema Compatible Determinado**: Tiene una única solución.
- **Sistema Compatible Indeterminado**: Tiene infinitas soluciones.
- **Sistema Incompatible**: No tiene solución.

### Sistemas Equivalentes
Dos sistemas de ecuaciones son **equivalentes** si tienen el mismo conjunto solución.

## Existencia de Soluciones
La **existencia** de soluciones depende del rango de la matriz de coeficientes $A$ y de la matriz aumentada $[A | \mathbf{b}]$.

### Conjunto Solución
El **conjunto solución** de un sistema compatible indeterminado se describe usando **parámetros libres** que permiten describir todas las soluciones posibles.

## Compatibilidad y Rango
Un sistema lineal es **compatible** si el rango de la matriz de coeficientes $A$ es igual al rango de la matriz aumentada $[A | \mathbf{b}]$.

$$
\text{rango}(A) = \text{rango}([A | \mathbf{b}])
$$

## Método de Eliminación de Gauss
El **método de eliminación de Gauss** es un procedimiento para resolver sistemas de ecuaciones lineales. Consiste en aplicar operaciones elementales de fila para transformar la matriz del sistema en una forma triangular, facilitando la resolución por **sustitución regresiva**.

### Pasos del Método de Eliminación de Gauss
1. Convertir la matriz del sistema a una **forma triangular** superior.
2. Resolver el sistema comenzando desde la última ecuación (sustitución hacia atrás).

## Teorema de Rouché-Frobenius
El **teorema de Rouché-Frobenius** establece que un sistema de ecuaciones lineales $A\mathbf{x} = \mathbf{b}$ tiene solución si y solo si:

$$
\text{rango}(A) = \text{rango}([A | \mathbf{b}])
$$

- Si el rango es igual al número de incógnitas, el sistema tiene una **única solución**.
- Si el rango es menor que el número de incógnitas, el sistema tiene **infinitas soluciones**.

