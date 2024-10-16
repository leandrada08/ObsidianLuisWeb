# ESPACIO VECTORIAL

## Definición de Espacio Vectorial
Un **espacio vectorial** (o espacio lineal) sobre un campo $\mathbb{K}$ (típicamente $\mathbb{R}$ o $\mathbb{C}$) es un conjunto $V$ de objetos (llamados **vectores**) junto con dos operaciones:
1. **Suma de vectores**: $+ : V \times V \to V$
2. **Producto por un escalar**: $\cdot : \mathbb{K} \times V \to V$

Estas operaciones deben cumplir las siguientes propiedades:
1. **Asociatividad y Conmutatividad de la Suma**.
2. **Elemento Neutro Aditivo**: Existe un vector $\mathbf{0} \in V$ tal que $\mathbf{v} + \mathbf{0} = \mathbf{v}$ para todo $\mathbf{v} \in V$.
3. **Elemento Opuesto**: Para cada vector $\mathbf{v} \in V$, existe un vector $-\mathbf{v} \in V$ tal que $\mathbf{v} + (-\mathbf{v}) = \mathbf{0}$.
4. **Compatibilidad y Distributividad** para el producto por un escalar.

## Combinación Lineal
Una **combinación lineal** de los vectores $\mathbf{v_1}, \mathbf{v_2}, \ldots, \mathbf{v_n} \in V$ con coeficientes $c_1, c_2, \ldots, c_n \in \mathbb{K}$ es un vector de la forma:

$$
\mathbf{w} = c_1 \mathbf{v_1} + c_2 \mathbf{v_2} + \cdots + c_n \mathbf{v_n}
$$

## Subespacio
Un **subespacio** $W$ de un espacio vectorial $V$ es un subconjunto de $V$ que también es un espacio vectorial bajo las mismas operaciones de suma y producto por escalar.

### Condición Necesaria y Suficiente
Un conjunto $W \subseteq V$ es un subespacio de $V$ si cumple:
1. **Cerradura bajo la suma**: Si $\mathbf{u}, \mathbf{v} \in W$, entonces $\mathbf{u} + \mathbf{v} \in W$.
2. **Cerradura bajo el producto por un escalar**: Si $\mathbf{v} \in W$ y $c \in \mathbb{K}$, entonces $c \mathbf{v} \in W$.

## Dependencia e Independencia Lineal
- Un conjunto de vectores $\{\mathbf{v_1}, \mathbf{v_2}, \ldots, \mathbf{v_n}\}$ es **linealmente dependiente** si existen coeficientes $c_1, c_2, \ldots, c_n$, no todos nulos, tales que:

  $$
  c_1 \mathbf{v_1} + c_2 \mathbf{v_2} + \cdots + c_n \mathbf{v_n} = \mathbf{0}
  $$

- Si la única combinación lineal que da como resultado el vector nulo es aquella en la que todos los coeficientes son cero, entonces los vectores son **linealmente independientes**.

### Consecuencias
- Si un conjunto de vectores es **dependiente linealmente**, al menos uno de los vectores puede escribirse como combinación lineal de los otros.
- En un espacio vectorial de dimensión $n$, un conjunto de más de $n$ vectores será necesariamente **linealmente dependiente**.

## Generador y Espacio Generado
Un conjunto de vectores **genera** un espacio vectorial si toda combinación lineal de los vectores en el conjunto produce cualquier vector en ese espacio.

El **espacio generado** por un conjunto de vectores $S = \{\mathbf{v_1}, \mathbf{v_2}, \ldots, \mathbf{v_n}\}$ se denota como:

$$
\text{span}(S) = \{c_1 \mathbf{v_1} + c_2 \mathbf{v_2} + \cdots + c_n \mathbf{v_n} \mid c_i \in \mathbb{K}\}
$$

## Base y Dimensión
- Una **base** de un espacio vectorial $V$ es un conjunto de vectores linealmente independientes que **genera** $V$.
- La **dimensión** de un espacio vectorial es el número de vectores en una base de ese espacio.

### Ejemplo
En $\mathbb{R}^3$, la base canónica es $\{(1,0,0), (0,1,0), (0,0,1)\}$, y la dimensión es 3.

## Coordenadas y Cambio de Base
Dado un vector $\mathbf{v}$ y una base $B = \{\mathbf{b_1}, \mathbf{b_2}, \ldots, \mathbf{b_n}\}$, las **coordenadas** de $\mathbf{v}$ en la base $B$ son los coeficientes $c_1, c_2, \ldots, c_n$ tales que:

$$
\mathbf{v} = c_1 \mathbf{b_1} + c_2 \mathbf{b_2} + \cdots + c_n \mathbf{b_n}
$$

### Matriz de Cambio de Base
La **matriz de cambio de base** de una base $B$ a otra base $B'$ es una matriz que transforma las coordenadas de un vector en la base $B$ a las coordenadas en la base $B'$.

Si $P$ es la matriz de cambio de base, entonces:

$$
[\mathbf{v}]_{B'} = P [\mathbf{v}]_B
$$

# TRANSFORMACIÓN LINEAL

## Definición de Transformación Lineal
Una **transformación lineal** (o aplicación lineal) $T: V \to W$ entre dos espacios vectoriales $V$ y $W$ es una función que cumple:

1. **Suma**: $T(\mathbf{u} + \mathbf{v}) = T(\mathbf{u}) + T(\mathbf{v})$ para todos $\mathbf{u}, \mathbf{v} \in V$.
2. **Producto por Escalar**: $T(c\mathbf{v}) = c T(\mathbf{v})$ para todo $c \in \mathbb{K}$ y $\mathbf{v} \in V$.

### Ejemplo
La función $T: \mathbb{R}^2 \to \mathbb{R}^2$ definida como $T(x, y) = (2x, 3y)$ es una transformación lineal.

## Consecuencias de una Transformación Lineal
Las transformaciones lineales **preservan** operaciones básicas como la suma de vectores y la multiplicación por un escalar, lo que facilita su uso en álgebra lineal para el análisis de sistemas y estructuras vectoriales.

## Álgebra de las Transformaciones Lineales
Dadas dos transformaciones lineales $T_1, T_2: V \to W$:
- **Suma de Transformaciones**: $(T_1 + T_2)(\mathbf{v}) = T_1(\mathbf{v}) + T_2(\mathbf{v})$
- **Composición de Transformaciones**: Si $T_1: V \to W$ y $T_2: W \to U$, entonces la composición $T_2 \circ T_1: V \to U$ es también una transformación lineal.

## Teorema Fundamental de las Transformaciones Lineales
Toda transformación lineal de un espacio vectorial $V$ de dimensión finita se puede representar mediante una **matriz**. Si $T: V \to W$ y $V$ tiene dimensión $n$, entonces existe una matriz $A$ de tamaño $m \times n$ tal que:

$$
T(\mathbf{v}) = A [\mathbf{v}]
$$

## Núcleo e Imagen
- **Núcleo (Kernel)**: El **núcleo** de una transformación lineal $T: V \to W$ es el conjunto de todos los vectores de $V$ que se transforman en el vector cero en $W$:

  $$
  \text{Ker}(T) = \{\mathbf{v} \in V \mid T(\mathbf{v}) = \mathbf{0}\}
  $$

- **Imagen**: La **imagen** de una transformación lineal es el conjunto de todos los vectores de $W$ que son la imagen de algún vector de $V$:

  $$
  \text{Im}(T) = \{T(\mathbf{v}) \mid \mathbf{v} \in V\}
  $$

### Propiedades
- La **dimensión del núcleo** y la **dimensión de la imagen** están relacionadas por el **teorema del rango-nulidad**:

  $$
  \dim(V) = \dim(\text{Ker}(T)) + \dim(\text{Im}(T))
  $$

## Matriz Asociada a una Transformación Lineal
Dada una transformación lineal $T: \mathbb{R}^n \to \mathbb{R}^m$, la **matriz asociada** $A$ se construye aplicando $T$ a los vectores de la base canónica de $\mathbb{R}^n$. Los resultados se colocan como columnas de la matriz $A$.

Si $T(\mathbf{e_i}) = \mathbf{a_i}$, donde $\mathbf{e_i}$ es un vector de la base canónica de $\mathbb{R}^n$, entonces:

$$
A = [T(\mathbf{e_1}) \,\, T(\mathbf{e_2}) \,\, \cdots \,\, T(\mathbf{e_n})]
$$

# DETERMINANTE

## Definición de Determinante
El **determinante** es un valor asociado a una matriz cuadrada que proporciona información importante sobre las propiedades de la matriz. Para una matriz $A$ de tamaño $n \times n$, el determinante se denota como $\text{det}(A)$ o $|A|$.

Para una matriz $2 \times 2$:

$$
A = \begin{bmatrix} a & b \\ c & d \end{bmatrix}
$$

El determinante es:

$$
\text{det}(A) = ad - bc
$$

Para una matriz de orden $n \geq 3$, el determinante se calcula mediante **expansión por cofactores**.

## Propiedades del Determinante
1. **Determinante de la Matriz Identidad**: $\text{det}(I) = 1$.
2. **Intercambio de Filas**: Si se intercambian dos filas de una matriz, el determinante cambia de signo.
3. **Fila Multiplicada por un Escalar**: Si una fila se multiplica por un escalar $k$, el determinante también se multiplica por $k$.
4. **Filas Proporcionales**: Si dos filas de una matriz son proporcionales, el determinante es $0$.
5. **Determinante del Producto**: Para dos matrices $A$ y $B$ de tamaño $n \times n$:

   $$
   \text{det}(AB) = \text{det}(A) \cdot \text{det}(B)
   $$

## Definición de Matriz Adjunta
La **matriz adjunta** (o **adjunta**) de una matriz $A$ es la transpuesta de la matriz de **cofactores** de $A$. Para una matriz $A$ de orden $n$:

$$
\text{adj}(A) = [C_{ij}]^T
$$

donde $C_{ij}$ es el **cofactor** del elemento $a_{ij}$.

### Propiedad de la Adjunta
La matriz adjunta se utiliza para calcular la **inversa** de una matriz. Si $A$ es una matriz cuadrada e **inversible**:

$$
A^{-1} = \frac{1}{\text{det}(A)} \text{adj}(A)
$$

## Matriz Inversible y Determinante
Una matriz cuadrada $A$ es **inversible** si y solo si su determinante es distinto de cero:

$$
\text{det}(A) \neq 0
$$

En este caso, la matriz tiene una **única inversa**.

## Aplicaciones a Sistemas de Ecuaciones Lineales
El determinante se utiliza para determinar la **existencia y unicidad** de la solución de un sistema lineal. Según el **teorema de Cramer**, si el determinante de la matriz de coeficientes es distinto de cero ($\text{det}(A) \neq 0$), el sistema tiene una única solución, dada por:

$$
x_i = \frac{\text{det}(A_i)}{\text{det}(A)}
$$

donde $A_i$ es la matriz obtenida al reemplazar la $i$-ésima columna de $A$ con el vector de términos independientes.

# POLINOMIO EN UNA INDETERMINADA

## Definición de Polinomio
Un **polinomio** en una indeterminada $x$ es una expresión de la forma:

$$
P(x) = a_n x^n + a_{n-1} x^{n-1} + \cdots + a_1 x + a_0
$$

donde los coeficientes $a_i \in \mathbb{R}$ y $n$ es un número natural.

## Operaciones con Polinomios

### 1. Suma y Resta
La **suma** y **resta** de dos polinomios se realizan sumando o restando sus coeficientes correspondientes.

### 2. Producto
El **producto** de dos polinomios $P(x)$ y $Q(x)$ se calcula multiplicando cada término de $P(x)$ por cada término de $Q(x)$.

### 3. Cociente
El **cociente** de dos polinomios se calcula mediante la **división larga de polinomios**, que determina cuántas veces el divisor cabe en el dividendo.

## Regla de Ruffini
La **Regla de Ruffini** es un método simplificado para dividir un polinomio por un binomio de la forma $(x - r)$. Se utiliza principalmente para evaluar valores específicos de polinomios y para encontrar ceros potenciales.

## Teorema del Resto
El **teorema del resto** establece que, si se divide un polinomio $P(x)$ por $(x - a)$, el resto de la división es igual a $P(a)$.

### Ejemplo
Si $P(x) = x^3 - 4x + 2$ y se divide por $(x - 1)$, el resto es $P(1) = -1$.

## Divisibilidad
Un polinomio $P(x)$ es **divisible** por un polinomio $Q(x)$ si el resto de la división de $P(x)$ por $Q(x)$ es cero.

## Polinomios Primos y Compuestos
- Un **polinomio primo** es aquel que no puede factorizarse en el producto de polinomios de menor grado con coeficientes en $\mathbb{R}$.
- Un **polinomio compuesto** es el que puede escribirse como el producto de dos o más polinomios de menor grado.

## Ceros de un Polinomio
Los **ceros** de un polinomio $P(x)$ son los valores de $x$ para los cuales $P(x) = 0$. Los ceros representan las intersecciones del polinomio con el eje $x$.

### Existencia de Ceros
El **teorema fundamental del álgebra** garantiza que todo polinomio de grado $n$ con coeficientes complejos tiene $n$ ceros (contando multiplicidades).

## Ceros Múltiples
Un **cero múltiple** de un polinomio es un valor que es solución de la ecuación $P(x) = 0$ más de una vez. Por ejemplo, si $(x - a)^k$ es un factor de $P(x)$, entonces $a$ es un cero de multiplicidad $k$.

## Factorización
La **factorización** de un polinomio consiste en escribirlo como el producto de factores irreducibles. 

### Ejemplo
El polinomio $P(x) = x^3 - 3x^2 + 3x - 1$ se puede factorizar como:

$$
P(x) = (x - 1)^3
$$

## Ecuaciones Polinómicas
Las **ecuaciones polinómicas** se resuelven buscando los ceros del polinomio correspondiente. La **factorización** y el uso del **teorema del resto** son métodos comunes para resolver este tipo de ecuaciones.

### Teorema Fundamental del Álgebra
El **teorema fundamental del álgebra** establece que cualquier polinomio no constante de grado $n$ tiene exactamente $n$ ceros (en el campo complejo). Esto incluye ceros reales e imaginarios.

### Factorización en $\mathbb{R}$ y $\mathbb{C}$
- En $\mathbb{R}$, los polinomios se pueden factorizar como el producto de factores lineales y factores cuadráticos irreducibles.
- En $\mathbb{C}$, cualquier polinomio puede ser factorado completamente en factores lineales.


# VALORES Y VECTORES PROPIOS

## Valores y Vectores Propios de un Operador Lineal
Dado un **operador lineal** $T: V \to V$, un **valor propio** $\lambda \in \mathbb{K}$ es un escalar tal que existe un **vector propio** $\mathbf{v} \in V$, $\mathbf{v} \neq \mathbf{0}$, que satisface:

$$
T(\mathbf{v}) = \lambda \mathbf{v}
$$

El vector $\mathbf{v}$ se denomina **vector propio** asociado al valor propio $\lambda$.

## Espacio Propio Asociado a un Valor Propio
El **espacio propio** asociado a un valor propio $\lambda$ de un operador lineal $T$ es el conjunto de todos los vectores propios asociados a $\lambda$, junto con el vector cero. Formalmente:

$$
E_{\lambda} = \{ \mathbf{v} \in V \mid T(\mathbf{v}) = \lambda \mathbf{v} \}
$$

El espacio propio es un **subespacio** del espacio vectorial $V$.

## Vectores Propios Asociados a Valores Propios Diferentes
Si $\lambda_1$ y $\lambda_2$ son dos **valores propios distintos** de un operador lineal $T$, entonces sus respectivos **espacios propios** son **linealmente independientes**.

## Valores y Vectores Propios de una Matriz de Orden $n$
Dada una **matriz cuadrada** $A$ de orden $n \times n$, un **valor propio** $\lambda$ es un escalar tal que existe un vector $\mathbf{v} \neq \mathbf{0}$ tal que:

$$
A \mathbf{v} = \lambda \mathbf{v}
$$

El vector $\mathbf{v}$ es un **vector propio** de la matriz asociado al valor propio $\lambda$.

## Espacio Propio Asociado a un Valor Propio de una Matriz
El **espacio propio** asociado a un valor propio $\lambda$ de una matriz $A$ es el conjunto de todos los vectores $\mathbf{v}$ que satisfacen la ecuación $A \mathbf{v} = \lambda \mathbf{v}$, y se denota como $E_{\lambda}$:

$$
E_{\lambda} = \{ \mathbf{v} \in \mathbb{R}^n \mid A \mathbf{v} = \lambda \mathbf{v} \}
$$

Este espacio propio es un subespacio de $\mathbb{R}^n$.

## Relación entre los Valores y Vectores Propios de un Operador Lineal y los de su Matriz Asociada
Para un operador lineal $T$ y una base dada de $V$, los **valores propios** y **vectores propios** del operador $T$ son los mismos que los valores y vectores propios de su **matriz asociada**.

## Matriz Característica y Polinomio Característico
La **matriz característica** de una matriz $A$ se obtiene restando $\lambda$ multiplicado por la matriz identidad de $A$:

$$
A - \lambda I
$$

El **polinomio característico** de la matriz $A$ se obtiene calculando el **determinante** de la matriz característica:

$$
p(\lambda) = \text{det}(A - \lambda I)
$$

El **polinomio característico** es un polinomio de grado $n$, donde $n$ es el tamaño de la matriz $A$.

## Ecuación Característica
La **ecuación característica** se obtiene igualando el polinomio característico a cero:

$$
\text{det}(A - \lambda I) = 0
$$

Las soluciones de esta ecuación son los **valores propios** de la matriz.

## Teorema de Cayley-Hamilton
El **teorema de Cayley-Hamilton** establece que toda matriz cuadrada $A$ satisface su propio polinomio característico. Es decir, si $p(\lambda)$ es el polinomio característico de $A$, entonces:

$$
p(A) = 0
$$

Este teorema tiene aplicaciones en el cálculo de potencias de matrices y en la diagonalización.

## Multiplicidad Algebraica y Geométrica de un Valor Propio

### Multiplicidad Algebraica
La **multiplicidad algebraica** de un valor propio $\lambda$ es el número de veces que aparece como raíz del polinomio característico.

### Multiplicidad Geométrica
La **multiplicidad geométrica** de un valor propio $\lambda$ es la **dimensión** del espacio propio asociado a $\lambda$. Esta multiplicidad indica el número de vectores linealmente independientes asociados al valor propio.

### Relación entre Multiplicidad Algebraica y Geométrica
Para un valor propio $\lambda$, su **multiplicidad geométrica** siempre es menor o igual a su **multiplicidad algebraica**:

$$
\text{multiplicidad geométrica} \leq \text{multiplicidad algebraica}
$$

# DIAGONALIZACIÓN DE OPERADORES LINEALES

## Definición de Diagonalización
Un operador lineal $T: V \to V$ se dice **diagonalizable** si existe una base de vectores propios de $V$. En términos de matrices, una matriz cuadrada $A$ es **diagonalizable** si existe una matriz invertible $P$ tal que:

$$
P^{-1} A P = D
$$

donde $D$ es una **matriz diagonal** que contiene los **valores propios** de $A$ en su diagonal.

## Polinomio Característico y Diagonalización
El **polinomio característico** de una matriz es fundamental para la diagonalización, ya que los **valores propios** son las raíces de este polinomio. Para que una matriz sea diagonalizable, es necesario que tenga suficientes vectores propios linealmente independientes para formar una base del espacio.

## Diagonalización de Matrices
Para **diagonalizar** una matriz $A$:

1. **Encuentra los Valores Propios**: Calcula el polinomio característico y encuentra los valores propios de $A$.
2. **Encuentra los Vectores Propios**: Para cada valor propio $\lambda$, resuelve $(A - \lambda I) \mathbf{v} = 0$ para encontrar los vectores propios.
3. **Forma la Matriz de Cambio de Base** $P$: La matriz $P$ tiene como columnas los vectores propios de $A$.
4. **Calcula la Matriz Diagonal** $D$: La matriz diagonal $D$ tiene los valores propios de $A$ en su diagonal.

Si se puede formar una base completa de vectores propios, la matriz $A$ es diagonalizable.

## Condiciones para la Diagonalización
- Una matriz cuadrada de orden $n$ es **diagonalizable** si tiene $n$ **vectores propios linealmente independientes**.
- Esto equivale a que la suma de las **multiplicidades geométricas** de todos los valores propios sea igual a $n$.

## Aplicaciones de la Diagonalización
- **Resolución de Sistemas de Ecuaciones Diferenciales**: La diagonalización se usa para simplificar sistemas de ecuaciones diferenciales lineales.
- **Potencias de Matrices**: Si una matriz $A$ es diagonalizable, es más fácil calcular sus potencias mediante:

  $$
  A^n = P D^n P^{-1}
  $$

- **Análisis de Estabilidad**: En sistemas dinámicos, los valores propios de una matriz de estado indican la **estabilidad** del sistema.

### Ejemplo de Diagonalización
Sea la matriz:

$$
A = \begin{bmatrix} 4 & 1 \\ 2 & 3 \end{bmatrix}
$$

1. **Polinomio Característico**:

   $$
   \text{det}(A - \lambda I) = \begin{vmatrix} 4 - \lambda & 1 \\ 2 & 3 - \lambda \end{vmatrix} = (\lambda - 5)(\lambda - 2)
   $$

   Los valores propios son $\lambda_1 = 5$ y $\lambda_2 = 2$.

2. **Vectores Propios**:
   - Para $\lambda_1 = 5$, se resuelve $(A - 5I) \mathbf{v} = 0$.
   - Para $\lambda_2 = 2$, se resuelve $(A - 2I) \mathbf{v} = 0$.

3. **Matriz de Cambio de Base** $P$:
   La matriz $P$ se forma con los vectores propios como columnas.

4. **Matriz Diagonal** $D$:

   $$
   D = \begin{bmatrix} 5 & 0 \\ 0 & 2 \end{bmatrix}
   $$

   Finalmente:

   $$
   P^{-1} A P = D
   $$

Este proceso simplifica cálculos posteriores, como el cálculo de $A^n$ o la evaluación del comportamiento del sistema asociado.

