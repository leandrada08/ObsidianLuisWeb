



## Sistema stereo y problema de profundidad
Los sistemas de visión estéreo son utilizados para obtener información tridimensional de una escena a partir de dos imágenes capturadas desde diferentes puntos de vista. Este método se basa en la geometría de proyección y en la triangulación para calcular la posición y la profundidad de los puntos en el espacio.
- Sistemas de medida basados en visión estéreo usan ecuaciones del modelo pin-hole para ligar coordenadas absolutas de un punto M y coordenadas en píxeles de la imagen m.

$$
\lambda \begin{bmatrix}
u \\
v \\
1
\end{bmatrix}
= 

P

\begin{bmatrix}
x \\
y \\
z \\
1
\end{bmatrix}
$$

- La matriz $P$ es crucial para simular el proceso de adquisición de imágenes, pero no permite la inversa, es decir, no se puede determinar unívocamente la posición $(x, y, z)$ de un punto en el espacio a partir de su proyección $(u, v)$.


#### Visión Estéreo y Estimación de Profundidad
.
![[Pasted image 20240601191400.png]]

Para resolver el problema de la ambigüedad en la proyección, se emplean dos cámaras que capturan la misma escena desde diferentes ángulos, conocidas como un *sistema de visión estéreo*. Al considerar dos vistas (izquierda $L$ y derecha $R$), cada cámara tiene su propia matriz de proyección, $P_L$ y $P_R$, respectivamente.

La correspondencia entre los puntos en las dos imágenes (stereo matching) es fundamental. Se trata de localizar sin ambigüedad la imagen $m_R$ en la vista derecha de un punto $M$ dado en la vista izquierda $m_L$. Este proceso se complica, pero es esencial para la triangulación, que permite determinar las coordenadas tridimensionales de $M$.

- Los problemas principales en los sistemas estéreo incluyen:
	1. **Correspondencia stereo:** Identificación de los puntos *correspondientes* entre las dos imágenes.
	2. **Calibración de la pareja:** Determinación de las matrices de proyección $P_L$ y $P_R$ a partir de un conjunto de puntos correspondientes.
	3. **Triangulación(Determinacion de las coordenadas de M):** Cálculo de las coordenadas espaciales de un punto a partir de sus proyecciones en ambas vistas.

- Correspondencia estéreo es compleja y necesita restricciones geométricas o información adicional.
- Calibración y triangulación requieren un sistema calibrado para medir coordenadas de M.

### Estimación de la Profundidad con Geometría Simplificada

- Para entender los sistemas estéreo, se empieza con un problema simplificado 
- Se usan relaciones analíticas simples para comprender las variables principales y dimensionar un sistema estéreo basado en restricciones geométricas y nivel de incertidumbre aceptable.

#### Sistema Estéreo Simplificado
![[Pasted image 20240601193759.png]]
Consideremos un sistema estéreo con dos cámaras idénticas, con la misma distancia focal $f$, ejes ópticos paralelos, y centros de proyección situados en el plano $xz$ a una distancia $b$ (baseline). Las coordenadas de imagen $x'_L$ y $x'_R$ de un punto $M$ en las cámaras izquierda y derecha, respectivamente, se obtienen a partir de las siguientes ecuaciones de proyección:

$$
x'_L = \frac{f x}{z}
$$

$$
x'_R = \frac{f (x - b)}{z}
$$

##### Disparidad
La **disparidad** $d$ es la diferencia entre las coordenadas de los puntos correspondientes en las dos imágenes:

$$
d = x'_L - x'_R
$$

Eliminando $x$ de las ecuaciones de proyección, obtenemos:

$$
z = \frac{b f}{x'_L - x'_R} = \frac{b f}{d}
$$

Esta relación muestra que la profundidad $z$ de un punto $M$ puede determinarse a partir de la disparidad $d$.

##### Importancia de la Disparidad
- Si $x'_L$ y $x'_R$ tienen valores muy similares, la disparidad es pequeña y la incertidumbre relativa en la medida de $z$ se incrementa.
- Una mayor disparidad mejora la estimación de $z$, por lo que se puede considerar aumentar la baseline $b$. Sin embargo, esto reduce el campo de visión común y complica el proceso de correspondencia de puntos debido a las diferencias en la perspectiva.

#### Incertidumbre en la Estimación de Profundidad
La incertidumbre en la profundidad $u_z$ puede evaluarse aplicando la ley de propagación de la incertidumbre:

$$
u_z = \sqrt{\left( \frac{\partial z}{\partial d} \right)^2 u_d^2} = \frac{bf}{d^2} u_d
$$

Donde $u_d$ es la incertidumbre en la disparidad. Si expresamos la disparidad en píxeles $d_u$:

$$
u_z = \frac{z^2}{bf}\cdot\frac{1}{k_u}u_d
$$

Aquí, $k$ es el tamaño de la celda sensitiva del sensor en micrómetros. Esta fórmula se puede usar para diseñar la geometría del sistema en función del nivel de incertidumbre requerido.
![[Pasted image 20240601194508.png]]
#### Ejemplo Numérico
Supongamos:
- $b = 500 \, \text{mm}$
- $f = 10 \, \text{mm}$
- Tamaño de celda sensitiva $k = 5 \, \mu m$

Con una incertidumbre en la disparidad $u_d$ de 1 píxel, la relación entre $z$ y $u_z$ es:

$$
u_z = \frac{500 \times 10}{d^2} \times 1 \approx \frac{5000}{d^2}
$$

#### Gráfico de Incertidumbre
El gráfico de la incertidumbre en función de la profundidad $z$ muestra que a medida que $z$ aumenta, la incertidumbre $u_z$ también lo hace, lo que destaca la importancia de mantener una disparidad alta para mejorar la precisión de la medida.
![[Pasted image 20240601194529.png]]





**Observaciones:**
- A mayor disparidad, mejor precisión en z.
- Baseline grande mejora disparidad pero reduce campo visual común.
- Parejas conjugadas difíciles de encontrar con perspectivas muy diferentes.
- La incertidumbre también depende de la correspondencia estéreo correcta, que es un problema complejo y específico de cada caso.

**Conclusión:**
- Sistemas estéreo requieren un balance entre baseline, campo visual y técnicas de análisis de imagen para lograr precisión en la medida de profundidad.

### Triangulación Estéreo mediante Métodos Lineales

El problema de la triangulación en visión estéreo se refiere a la determinación de las coordenadas tridimensionales $(x, y, z)$ de un punto $M$, dado sus correspondientes puntos de imagen $m_L$ y $m_R$ en las vistas izquierda y derecha, y las matrices de proyección perspectivística $P_L$ y $P_R$. Este proceso se conoce también como reconstrucción 3D o reconstrucción de la estructura euclidiana de la escena.

#### Triangulación mediante Sistema Homogéneo (Linear Eigen)
Se parte de las ecuaciones de proyección de la pareja estéreo:

$$
\lambda_L m_L = P_L M
$$
$$
\lambda_R m_R = P_R M
$$

A partir del paralelismo de los miembros de cada una de las ecuaciones, se obtiene:

$$
0 = m_L \times (P_L M)
$$
$$
0 = m_R \times (P_R M)
$$

Desarrollando el producto vectorial para cada vista, se tiene (considerando solo la vista izquierda para simplificar):

$$
\begin{cases}
m_{L2} (P_{3L}^T M)_3 - m_{L3} (P_{2L}^T M)_2 = 0 \\
m_{L3} (P_{1L}^T M)_1 - m_{L1} (P_{3L}^T M)_3 = 0 \\
m_{L1} (P_{2L}^T M)_2 - m_{L2} (P_{1L}^T M)_1 = 0
\end{cases}
$$

Donde $P_{jL}^L$ representa la $j$-ésima fila de $P_L$. Al omitir la tercera ecuación (por ser linealmente dependiente de las dos primeras) y dividiendo por $m_{L3}$:

$$
\begin{cases}
v_{L} (P_{3L}^T \tilde{M}) - (P_{1L}^T \tilde{M}) = 0 \\
(P_{1L}^T \tilde{M}) - u_{L} (P_{3L}^T \tilde{M}) = 0
\end{cases}
$$

Repitiendo el proceso para la vista derecha y combinando en forma matricial, obtenemos el sistema homogéneo:

$$
\begin{bmatrix}
u_L P_{3L}^T - P_{1L}^T \\
v_L P_{3L}^T - P_{2L}^T \\
u_R P_{3R}^T - P_{1R}^T \\
v_R P_{3R}^T - P_{2R}^T
\end{bmatrix}
\tilde{M} = 0_{4x1}
$$
- De manera matricial esto se puede reescribir como:
$$A\tilde{M}=0$$

Este es un sistema homogéneo de 4 ecuaciones en 4 incógnitas, representado en coordenadas homogéneas. La solución $M$ se determina mediante la descomposición SVD de la matriz, obteniendo la última columna de la matriz ortogonal $V$.

#### Triangulación mediante Pseudoinversa
Otra formulación alternativa es mediante pseudoinversa. Partimos de las ecuaciones:

![[Pasted image 20240601200259.png]]

Siendo $q_j^T$ los primeros tres elementos de la $j$-ésima fila de $P$, se tiene:
![[Pasted image 20240601200338.png]]

Se calcula ahora las coordenadas cartesianas $m=(u,v)$ dividiendo las primeras 2 ecuaciones por la tercera

$$
\begin{cases}
u = \frac{q_1^T M + p_{14}}{q_3^T M + p_{34}} \\
v = \frac{q_2^T M + p_{24}}{q_3^T M + p_{34}}
\end{cases}
$$

Reordenando para despejar $M$:

$$
\begin{cases}
q_1^T M + p_{14} - u (q_3^T M + p_{34}) = 0 \\
q_2^T M + p_{24} - v (q_3^T M + p_{34}) = 0
\end{cases}
$$
![[Pasted image 20240601200511.png]]
Esto se puede expresar en forma matricial:
![[Pasted image 20240601200531.png]]

$$
A M = b
$$

Donde $A$ es la matriz de coeficientes y $b$ es el vector de términos independientes. Este sistema se resuelve mediante el método de mínimos cuadrados con pseudoinversa:

$$
M = A^\dagger b
$$

#### Observaciones sobre los Métodos Lineales

- **Ventajas y desventajas**:
  - **Similares a los métodos de calibración lineal**.
  - **Minimización de errores algebraicos, no geométricos**.
  - **Soluciones no óptimas con datos de entrada inciertos**.
  - **Refinamiento**: Minimización de una función objetivo geométrica con un algoritmo de minimización numérica.

- La precisión del método basado en pseudoinversa disminuye cuando el punto $M$ se aleja, debido a inestabilidades numéricas.



### Propagación de la Incertidumbre en la Triangulación Linear Eigen

Para medir las coordenadas absolutas $(x, y, z)$ del punto $M$ en el espacio a partir de las imágenes $(u_L, v_L)$ y $(u_R, v_R)$ del punto $M$ en las cámaras izquierda y derecha, respectivamente, y las matrices de proyección $P_L$ y $P_R$, se resuelve el sistema homogéneo:

$$
0 = A M
$$

Donde $A$ es una matriz de coeficientes derivada de las matrices de proyección y las coordenadas de imagen, y $M$ es el vector de coordenadas homogéneas del punto $M$.

#### Sistema de Ecuaciones Implicito
Siguiendo la metodología de propagación de la incertidumbre utilizada en la calibración, el sistema puede escribirse como una ecuación vectorial implícita:

$$
f(\nu, M) = 0
$$

Aquí, $\nu$ es el vector de grandezan de entrada que incluye tanto las coordenadas de los puntos de imagen $(u_L, v_L, u_R, v_R)$ como los parámetros de calibración, en total tiene 24 elementos.

#### Vectores y Matrices de Covarianza
La matriz de covarianza de la entrada $\nu$ se denota como $\Lambda_{\nu}$. La propagación de la covarianza al vector de salida $M$ se realiza mediante la ley de propagación de incertidumbre para sistemas multivariados implícitos:

$$
\Lambda_M = J_{\nu} \Lambda_{\nu} J_{\nu}^T
$$

Donde $J_{\nu}$ es la matriz jacobiana de las variables de entrada:

$$
(J_{\nu})_{ij} = \frac{\partial f_i}{\partial \nu_j}
$$

Y $J_M$ es la matriz jacobiana de las variables de salida:

$$
(J_M)_{ij} = \frac{\partial f_i}{\partial x_j}
$$

La matriz de covarianza de la salida se obtiene como:

$$
\Lambda_M = J_{\nu} \Lambda_{\nu} J_{\nu}^T
$$

Y la matriz pseudoinversa de $J_M$ es:

$$
J_M^\dagger = (J_M^T J_M)^{-1} J_M^T
$$

La matriz de covarianza de las coordenadas absolutas de $M$ se obtiene finalmente como:

$$
\Lambda_M = J_M^\dagger J_{\nu} \Lambda_{\nu} J_{\nu}^T J_M^\dagger
$$

## Geometría Epipolar
La geometría epipolar describe las relaciones entre diferentes vistas de una escena en sistemas con dos o más cámaras. Considere un sistema con dos cámaras, "izquierda" y "derecha", con centros de proyección $C_L$ y $C_R$, que ven el punto $M$ y producen las imágenes $m_L$ y $m_R$.
![[Pasted image 20240601202254.png]]
- **Plano Epipolar:** El plano que pasa por $M$, $C_L$ y $C_R$.
- **Baseline:** La línea que une $C_L$ y $C_R$.
- **Epipolos:** La imagen del centro de proyección de una cámara vista desde la otra cámara. Los epipolos izquierdo y derecho se denotan como $e_L$ y $e_R$.

Los epipolos tienen coordenadas homogéneas:

$$
\tilde{e}_R = P_R \tilde{C}_L
$$
$$
\tilde{e}_L = P_L \tilde{C}_R
$$

La **recta epipolar** es la línea que pasa por la imagen $m_L$ (o $m_R$) y el epipolo $e_L$ (o $e_R$).

#### Fasces de Rectas Epipolares
Al mover el punto $M$, los centros de proyección y los epipolos no cambian, pero las imágenes $m_L$ y $m_R$ se desplazan, formando dos conjuntos de rectas epipolares centradas en los epipolos izquierdo y derecho.


![[Pasted image 20240601202342.png]]
![[Pasted image 20240601202350.png]]
#### Rectas Epipolares
El punto $m_{Ri}$ se encuentra en la recta epipolar $l_{Ri}$, que pasa por $m_{Ri}$ y el epipolo derecho $e_R$. Utilizando coordenadas homogéneas, la recta que pasa por dos puntos es igual al producto vectorial de los puntos:

$$
l_{Ri} = [e_R]_\times \tilde{m}_{Ri}
$$

Donde $[e_R]_\times$ es la matriz de producto cruzado de $e_R$:

$$
[e_R]_\times = \begin{bmatrix}
0 & -e_{R3} & e_{R2} \\
e_{R3} & 0 & -e_{R1} \\
-e_{R2} & e_{R1} & 0
\end{bmatrix}
$$

Entonces:

$$
l_{Ri} = [e_R]_\times \pi H \tilde{m}_{Li}
$$


### La Matriz Fundamental

La matriz fundamental es crucial para describir el vínculo algebraico entre puntos correspondientes en dos vistas de un sistema estereoscópico. Esta relación se deriva utilizando homografías y geometría epipolar.
![[Pasted image 20240603194605.png]]
Consideremos un plano $\pi$ en el espacio que contiene un conjunto de puntos $\{M_i\}$ observados por ambas cámaras. Existen homografías que mapean estos puntos en las imágenes de ambas cámaras. 

La homografía $H_{\pi}$ establece una correspondencia entre los puntos imagen en las vistas izquierda $m_L$ y derecha $m_R$:

$$
\tilde{m}_{Ri} = H_{\pi} \tilde{m}_{Li}
$$


#### Definición Matematica de la Matriz Fundamental
La matriz fundamental $F$ se define como:

$$
F = [e_R]_\times \pi H
$$

Así, la recta epipolar derecha se calcula como:

$$
l_{R} = F \tilde{m}_{L}
$$

#### Propiedades de la Matriz Fundamental
- Tiene rango 2.
- Relaciona puntos en dos vistas sin necesidad de conocer las matrices de proyección de las cámaras.

#### Cálculo de la Matriz Fundamental
Para calcular $F$ en función de las matrices de proyección $P_L$ y $P_R$:

$$
\tilde{m}_L = P_L \tilde{M}
$$

La ecuación paramétrica de la línea de vista es:

$$
\tilde{M}( \lambda)= P_L^\Delta \tilde{m}_L + \lambda \tilde{C}_L
$$

Donde $P_L^\Delta$ es la pseudoinversa de $P_L$ y $C_L$ es el centro de proyección de la cámara izquierda.

La recta epipolar derecha pasa por $P_R P_L^\dagger \tilde{m}_L$ y el epipolo derecho $e_R = P_R C_L$:

$$
l_{Ri} = [e_R]_\times P_R P_L^\Delta \tilde{m}_L
$$

Entonces:

$$
F = [e_R]_\times P_R P_L^\Delta
$$

#### Relación de Correspondencia
Un punto $\tilde{x}$ en coordenadas homogéneas pertenece a una recta $\tilde{l}$ si:

$$
\tilde{x}^T l = 0
$$

Para la relación de correspondencia:

$$
\tilde{m}_R^T F \tilde{m}_L = 0
$$

Esta ecuación permite determinar $F$ conociendo solo las imágenes de puntos correspondientes, sin necesidad de calibrar las cámaras.

#### Estimación Experimental de la Matriz Fundamental
Con un conjunto de puntos correspondientes $\tilde{m}_L$ y $\tilde{m}_R$, podemos construir un sistema de ecuaciones lineales homogéneo para los elementos de $F$:

$$
A \tilde{f} = 0
$$

Donde $\tilde{f}$ es el vector de los elementos de $F$ y $A$ es una matriz de coeficientes. Este sistema se resuelve mediante descomposición SVD, determinando $\tilde{f}$ como la última columna de la matriz $V$ obtenida de $A = USV^T$.

#### Algoritmo de los 8 Puntos
Para determinar $F$ se requieren al menos 8 correspondencias. En la práctica, el método se ajusta por mínimos cuadrados y se puede mejorar con normalización de datos.




### Aplicaciones de la Geometría Epipolar

La geometría epipolar y las ecuaciones de las rectas epipolares tienen múltiples aplicaciones prácticas, especialmente en el contexto de la visión estéreo y la calibración de sistemas de cámaras. A continuación, se detallan algunas de las aplicaciones más relevantes:

#### 1. Búsqueda de Correspondencia Estéreo
Cuando se tiene un punto de imagen $m_L$ en la vista izquierda, la recta epipolar correspondiente en la vista derecha $l_R = F m_L$ restringe la búsqueda del punto correspondiente $m_R$ a esta línea en lugar de toda la imagen. Esto simplifica enormemente el problema de la correspondencia estéreo, conocido como **vinclo epipolar**. La matriz fundamental $F$ puede calcularse analíticamente usando la ecuación:

$$
F = [P_R C_L]_\times P_R P_L^\dagger
$$

o determinarse experimentalmente mediante el algoritmo de los 8 puntos.

#### 2. Error Epipolar
El error epipolar mide la distancia geométrica entre un punto de imagen y su recta epipolar correspondiente, definido como:

$$
e_{\text{epipolar}}(m_L, m_R) = d(F m_L, m_R) + d(F^T m_R, m_L)
$$

donde $d(l, m)$ es la distancia entre un punto $m$ y una recta $l$. Este error debería ser nulo en condiciones ideales, y se utiliza para evaluar la calidad de la calibración del sistema estéreo y la adecuación del modelo. Para un conjunto de $N$ puntos:

$$
E_{\text{epipolar}} = \sum_{i=1}^N \left[ d(F m_{Li}, m_{Ri}) + d(F^T m_{Ri}, m_{Li}) \right]
$$

Este valor puede promediarse para obtener el error epipolar medio:

$$
E_{\text{epipolar}}^{\text{medio}} = \frac{1}{N} \sum_{i=1}^N \left[ d(F m_{Li}, m_{Ri}) + d(F^T m_{Ri}, m_{Li}) \right]
$$

#### 3. Afinación de Resultados de Triangulación
El error epipolar puede utilizarse como una función objetivo a minimizar para mejorar los resultados de la triangulación obtenida por el método DLT (Direct Linear Transform). La minimización del error epipolar permite ajustar los puntos tridimensionales reconstruidos:

$$
\min_M \sum_{i=1}^N \left[ d(F m_{Li}, m_{Ri}) + d(F^T m_{Ri}, m_{Li}) \right]
$$

#### 4. Refinamiento de Parámetros de Calibración
El error epipolar también se puede usar para afinar los parámetros de calibración de las cámaras. Tras obtener una calibración inicial con el método DLT, se pueden ajustar los parámetros de las cámaras minimizando el error epipolar:

$$
\min_{\alpha_L, \alpha_R} \sum_{i=1}^N \left[ d(F m_{Li}, m_{Ri}) + d(F^T m_{Ri}, m_{Li}) \right]
$$

donde $\alpha_L$ y $\alpha_R$ son los vectores de parámetros de calibración de las cámaras izquierda y derecha, respectivamente. Esto incluye considerar modelos de distorsión de lentes, por ejemplo, una distorsión de lente de primer término.

### Conclusión
La geometría epipolar es una herramienta poderosa en la visión por computadora, que no solo simplifica la búsqueda de correspondencias estéreo sino que también proporciona métricas valiosas para la calibración y el ajuste fino de los sistemas de cámaras. Las aplicaciones del error epipolar son fundamentales para garantizar la precisión y robustez de los sistemas de visión estéreo.
