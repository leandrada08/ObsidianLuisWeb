## Metodos lineales
### Matriz homografica con metodo DLT(2D-2D)
![[Pasted image 20240531100918.png]]
Para estimar una homografía, se utilizan al menos cuatro pares de puntos correspondientes entre dos imágenes. El procedimiento de estimación se puede resumir en los siguientes pasos:

- **Identificación de Puntos Correspondientes:**  
	- Colocar un objeto plano en el plano $x, y$ con $N$ puntos conocidos $(x_i, y_i)$.
		- Este obejto es llamado target de calibracion
	- Puntos de calibración: Coordenadas conocidas con alta precisión.
		- Cada coordenada $\tilde{M}_i$ esta relacionada con una imagen $\tilde{m}_i$ por la ecuacion $\tilde{m}_i=H.\tilde{M}_i$
		- Como en coordinadas homogeneas la igual siginfica que son paralelos → $\tilde{m}_ixH.\tilde{M}_i=0$
		- Al trabajar matricialmente y reducir la matriz, nos podemos dar cuenta que solo 2 filas de la matriz son linealmente independiente.
			- Entonces, cada punto conocido agrega 2 filas a la matriz A.
		- Como la matriz H tiene 8 parametros indenpendientes, son necesarios al menos cuatro pares de puntos entre las dos imágenes.
	- Llegamos al siguiente sistema de ecuacion. $$A \mathbf{h} = 0$$
	- Como los valores de las coordenadas M y m son fruto de mediciones, se usa un numero de puntos de calibracion N mucho mayor a 4, para obtener un sistema sobredeterminado. Luego se resuelve el sistema $A \mathbf{h} = 0$ utilizando el método de los mínimos cuadrados.

   - En presencia de mediciones con error, se usan más puntos de calibración ($N > 4$) para crear un sistema sobredeterminado.
   - Resolver usando mínimos cuadrados:
     $$
     \min || \mathbf{A} \mathbf{h} ||
     $$

- **Descomposición en Valores Singulares (SVD)**:
   - La solución al problema de mínimos cuadrados se obtiene usando SVD en la matriz A:
     $$
     \mathbf{A} = \mathbf{U} \mathbf{S} \mathbf{V}^T
     $$
     donde $\mathbf{U}$ es ortogonal 2Nx2N, $\mathbf{S}$ es diagonal no nulla 2Nx9 y $\mathbf{V}$ es ortogonal 9x9.
   - La solución no trivial $\mathbf{h}$ es la última columna de $\mathbf{V}$(no traspuesta).

- **Direct Linear Transformation (DLT)**:
   - El método descrito se llama Transformación Lineal Directa (DLT).
   - Método para resolver el sistema sobredeterminado y obtener los parámetros de la homografía.

### Calibración de la Cámara con el Método DLT

En este punto buscaremos encontrar los parametros de la matriz de proeyctacion prospectica $P$.La matriz de proyección perspectiva $P$ de una cámara se calcula mediante un procedimiento similar al utilizado para la estimación de la homografía $H$, pero con dimensiones diferentes ($H$ es 3x3 mientras que $P$ es 3x4). Pasos principales:

- **Adquisición de imagen:** Se captura la imagen de un target de calibración.
- **Correspondencia de puntos:** Se establece la correspondencia entre cada uno de los $N$ puntos de calibración $\mathbf{M}_i = (x_i, y_i, z_i)$ y su imagen $\mathbf{m}_i = (u_i, v_i)$.
- **Coordenadas homogéneas:** Se pasa a coordenadas homogéneas $\tilde{\mathbf{M}}_i$ y $\tilde{\mathbf{m}}_i = (m_{i1}, m_{i2}, m_{i3})$.
- **Relación entre puntos:** Cada punto de calibración satisface la relación: $\mathbf{m}_i = P \mathbf{M}_i$. → son paralelos → producto vectorial nulo

Desde aqui se hace el mismo trabajo agebraico que se realizo para la matriz homografica, en este caso tambien, cada correspondencia de punto nos da 2 ecuaciones independientes, por lo cual tambien nos queda un sistema con una matriz $A$, comprendida con 2N filas correspondientes a estas ecuaciones independientes y 12 columnas, y una matriz $p$ con 12 elementos, los cuales son los parametros de la camara. $$Ap=0$$
- Este sistema tambien se resuelve con sistema de minimos cuadrados mediante descomposicion SVD: $$A=USV^T$$

- **Descomposición SVD:** La matriz $U$ es ortogonal $2N \times 2N$, $S$ es diagonal $2N \times 12$, y $V$ es ortogonal $12 \times 12$.
- **Solución $p$:** Se obtiene como la última columna de $V$ (no transpuesta).
- **Formación de $P$:** Los elementos de $p$ se reorganizan en una matriz 3x4 para obtener $P$.

#### Condiciones para una Solución Válida
- **No coplanaridad:** Los $N$ puntos de calibración $\mathbf{M}_i$ no deben ser coplanares.
- **Preferencia:** Es preferible que no sean ni siquiera aproximadamente coplanares.


#### Ventajas del DLT
  - **Simplicidad:** La descomposición SVD está disponible como función de librería.
  - **Precisión:** Aunque DLT no siempre proporciona la mejor solución con datos inciertos, sus resultados son típicamente muy cercanos a los óptimos, incluso con niveles de incertidumbre relativamente altos.
### 3.2.1 Ejemplo de Calibración DLT en Matlab(Pagina 40 del libro)

### Estimación de la Matriz de Proyección mediante Pseudoinversa

Para estimar la matriz de proyección $\mathbf{P}$ de una cámara, se puede usar la pseudoinversa, este método basado en la matriz pseudoinversa puede ser computacionalmente menos costoso en algunos casos.

La relación fundamental es $\mathbf{m}_i \sim P \mathbf{M}_i$.

#### Descomposición de la Matriz $P$
La matriz $P$ se descompone de la siguiente manera:

$$ P =  \begin{bmatrix}
   q_1^T & |& p_{14} \\
   q_2^T & | & p_{24} \\
   q_3^T & | & p_{34} 
   \end{bmatrix}
$$

La relación (3.10) en coordenadas cartesianas es:

$$
\lambda\begin{bmatrix}
u_i \\
v_i \\
1
\end{bmatrix}  =  \begin{bmatrix}
   q_1^TM_i + p_{14} \\
   q_2^TM_i + p_{24} \\
   q_3^TM_i + p_{34} 
   \end{bmatrix} 
$$

Dividiendo las primeras dos ecuaciones por la tercera para eliminar $\lambda$:

$$
\begin{cases}
q_1^T+p_{14}-u_i(q_3^TM_i+p_{34})=0 \\
q_2^T+p_{24}-u_i(q_3^TM_i+p_{34})=0
\end{cases}
$$

#### Sistema Lineal
Separando coeficientes e incógnitas, y fijando $p_{34} = 1$ para establecer la escala de $P$, obtenemos:

$$
\begin{bmatrix}
\vdots \\
-\mathbf{M}_i^T & 1 & 0_{1x3} & 0 & -u_i\mathbf{M}_i^T \\
0_1x3 & 0 & \mathbf{M}_i^T & 1 & -v_i \mathbf{M}_i^T  \\
\vdots
\end{bmatrix}
\begin{bmatrix}
q_1 \\
p_{14}\\
q_2 \\
p_{24}\\
q_3
\end{bmatrix}
= 
\begin{bmatrix}
\vdots \\
u_i \\
v_i \\
\vdots
\end{bmatrix}
$$

Que es un sistema linean, no homogeneo, sobredeterminado, que se puede escribir de la forma:

$$
Aq = b
$$


Para resolver el sistema sobredeterminado $Aq = b$ por mínimos cuadrados, se encuentra el vector $q$ que minimiza $\| Aq - b \|_2$. La solución se da mediante la pseudoinversa de $A$:

$$
q = A^{\Delta} b
$$


La pseudoinversa de $A$ se define como:

$$
A^{\Delta} = (A^T A)^{-1} A^T
$$

.
