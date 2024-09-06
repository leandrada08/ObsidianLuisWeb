
## Introduzione
![[Pasted image 20240424092847.png]]
- La calibrazione di una fotocamera è un processo che definisce con precisione i parametri intrinseci ed estrinseci del modello della stessa.
### Tipos de algoritmos de calibración

Existen tres categorías principales de algoritmos de calibración:

- **Algoritmos lineales:** Basados en coordenadas absolutas de puntos de la escena. Procedimiento lineal con solución directa para el número mínimo de puntos conocidos; no lineal para más puntos, usando minimización mediante mínimos cuadrados o métodos iterativos.
- **Algoritmos no lineales:** Basados en ecuaciones no lineales del modelo pinhole.
- **Algoritmos multipaso:** Híbridos, inician como lineales para estimaciones iniciales y luego pasan a análisis no lineal.

Todos requieren coordenadas absolutas de puntos de la escena para obtener parámetros de calibración. Utilizan blancos en paneles con marcadores de formas y posiciones conocidas.

#### Algoritmos utilizados
Clasificados según el tipo de blanco:

1. **Blancos con coordenadas conocidas, posiciones conocidas.**
2. **Blancos con coordenadas conocidas, poses desconocidas.**
3. **Blancos de geometría desconocida, poses desconocidas.**

Ejemplos: DLT (Direct Linear Transform), algoritmo de Roger Y. Tsai, método de Z. Zhang, autocalibración.

### Parámetros

**Parámetros intrínsecos**
Definen la geometría interna de la cámara:
- **Distancia focal:** Distancia entre el centro óptico del objetivo y el plano de la imagen.
- **Punto principal:** Intersección del eje óptico con el plano de la imagen.
- **Distorsión:** Desviación de la imagen real respecto a la imagen ideal.

**Parámetros extrínsecos**
Definen la posición y orientación de la cámara en el espacio 3D:
- **Rotación:** Orientación de la cámara.
- **Traslación:** Posición de la cámara.



## [[Metodos lineales de calibracion de una telecamara]]

## [[Metodos no lineales para calibrazion de una telecamara]]

## [[Errori di riproiezione]]



# Anexo
## El Target de Calibración

El target de calibración es una estructura con puntos de referencia conocidos que se utiliza para la calibración de cámaras. Puede ser una cuadrícula o un patrón de puntos, donde las posiciones de los puntos son conocidas con precisión.

#### Datos de Entrada
El algoritmo DLT requiere:
- **Coordenadas absolutas $\mathbf{M}_i = (x_i, y_i, z_i)$** de los $N$ puntos del objetivo de calibración.
- **Coordenadas en píxeles $\mathbf{m}_i = (u_i, v_i)$** de las imágenes de los puntos de calibración.
#### Emparejamiento de Coordenadas
Es crucial que ambos conjuntos de coordenadas estén correctamente emparejados, es decir, que la i-ésima coordenada absoluta $\mathbf{M}_i$ corresponda a la i-ésima coordenada en píxeles $\mathbf{m}_i$. Esto requiere algoritmos de ordenamiento apropiados para los puntos $\mathbf{m}_i$, localizados mediante técnicas de análisis de imágenes.

#### Sensibilidad a la Incertidumbre
La incertidumbre de los parámetros de calibración es muy sensible a la incertidumbre de $\mathbf{M}_i$. Por eso, es vital fabricar el objetivo con precisión, utilizando materiales rígidos y estables ante cambios de temperatura. Soluciones comunes incluyen:
- **Impresiones en planos de vidrio.**
- **Placas metálicas mecanizadas con control numérico.**

Después de la fabricación, el objetivo puede someterse a mediciones mecánicas precisas para determinar los valores de $\mathbf{M}_i$.



#### Condición de No Coplanaridad
Para que el algoritmo DLT funcione correctamente, los puntos del objetivo no deben ser coplanares. Algunas soluciones incluyen:
- **Estructuras tridimensionales.**
- **Objetivos planarios movidos a diferentes poses y distancias de la cámara**

![[Pasted image 20240531123646.png]]
- Tenga en cuenta que, en el caso de la Figura 3.3c), se utiliza un objetivo plano que se mueve en varias poses a diferentes distancias de la cámara. En este caso es necesario adquirir y procesar más imágenes para construir el conjunto completo de la empresa.
#### Sistema de Referencia Absoluto
En algoritmos como DLT, el sistema de referencia de $\mathbf{M}_i$, generalmente fijado al objetivo, se convierte en el sistema de referencia absoluto $(x, y, z)$ del modelo pin-hole. Los resultados de la medición se expresarán en este sistema.

#### Volumen de Calibración
El volumen de calibración es el espacio en el que los parámetros estimados, especialmente la matriz $P$, representan con mayor precisión el comportamiento de la cámara calibrada. Las medidas serán más precisas si los objetos están dentro de este volumen, que puede definirse, por ejemplo, como el menor paralelepípedo que contenga todos los puntos de calibración.

#### Consideraciones Prácticas
- **Colocación del objetivo:** Posicionar el objetivo de calibración de modo que defina el volumen donde se medirán los objetos.
- **Enfoque de la cámara:** Asegurarse de que la cámara esté correctamente enfocada durante la adquisición de las imágenes de calibración, ya que el modelo pin-hole asume un enfoque correcto.
- **Fijación de parámetros:** Después de la calibración, los parámetros de la cámara (enfoque, posición, orientación) no deben cambiar, ya que los valores estimados de $P$ dejarían de ser válidos.







## Localización de las Miras del Target


Para garantizar la precisión en la calibración, es crucial escoger adecuadamente las formas de las miras y los algoritmos de estimación de coordenadas $\mathbf{m}_i$. Los resultados deben ser:
1. **Con resolución sub-píxel.**
2. **Invariantes a deformaciones perspectivas.**
3. **Invariantes a desenfoques de la cámara.**
![[Pasted image 20240531124713.png]]
#### Miras Circulares
La solución más común es usar miras circulares, que bajo deformación perspéctica se aproximan bien a elipses (Heikkilä, 2000). La estimación de $\mathbf{m}_i = (u_i, v_i)$ se realiza calculando el centroide de la región ocupada por el disco circular en la imagen (Figura 3.5a).

- **Cálculo del centroide:** 
  Si $D(i,j)$ son los píxeles de la imagen que pertenecen al disco circular de la mira i-ésima, el centroide se define como:

  $$
  u_i = \frac{1}{N} \sum_{k=1}^{N} u_k, \quad v_i = \frac{1}{N} \sum_{k=1}^{N} v_k
  $$

#### Miras Cuadradas
Otra opción es usar miras cuadradas, considerando puntos de calibración las intersecciones de las rectas de regresión 2D calculadas sobre los bordes de cada lado (Figura 3.5b).

- **Cálculo de intersecciones:**
  - Se identifican los bordes de la mira cuadrada.
  - Se calculan las rectas de regresión para estos bordes.
  - Las intersecciones de estas rectas se utilizan como puntos de calibración.



## De la Matriz de Proyección Perspectiva a los Parámetros de la Cámara

La matrice di proiezione $P$ spesso basta per molte aplicaciones, ma a volte è necesario determinar los parámetros intrínsecos y extrínsecos de la cámara, como en los siguientes casos:

- **Posición del Vehículo:** Determinar la posición del vehículo en el espacio.
- **Sistemas Estereoscópicos:** Evaluar la posición relativa de dos cámaras.
- **Verificación de Calibración:** Comprobar la corrección de la calibración, ya que los elementos de $P$ no son inmediatamente interpretables.


A continuación, se presentan dos de los métodos más utilizados para determinar los parámetros intrínsecos y extrínsecos a partir de $P$.



### Descomposición de la Matriz $P$ Mediante Factorización QR

Para descomponer la matriz $P$ en sus componentes intrínsecos y extrínsecos, se puede usar la factorización QR. Se asume que $P$ tiene la forma:

$$ P = K [R | t] $$

Donde $K$ es una matriz triangular superior que contiene los parámetros intrínsecos y $[R | t]$ contiene los parámetros extrínsecos (rotación $R$ y traslación $t$).

#### Paso a Paso:

1. **Seleccionar las primeras tres columnas de $P$:**
   
   $$ P_{3x3} = KR $$

   Aquí, $P_{3x3}$ es la submatriz de $P$ que incluye solo las primeras tres columnas.
   - K es una matriz triangular superior ortogolonal y R es una amtriz ortogonal
   - Algoritmo de factorizacion QR → Una matriz cuadrada se puede descomponer en el producto de una matriz triangular superior y una ortogolar $P_{3x3}^{-1}=UB$

2. **Invertir $P_{3x3}$:**
   
   $$ P_{3x3}^{-1} = (KR)^{-1} $$
   $$ P_{3x3}^{-1} = R^{-1} K^{-1} $$

3. **Aplicar la factorización QR a $P_{3x3}^{-1}$:**
   
   $$ P_{3x3}^{-1} = UB $$

   Donde $U$ es una matriz ortogonal y $B$ es una matriz triangular superior.

4. **Determinar $K$ y $R$:**
   
   $$ R = U^{-1} $$
   $$ K = B^{-1} $$

5. **Calcular la cuarta columna $q_4$ de $P$:**
   
   $$ q_4 = Kt $$
   $$ t = K^{-1} q_4 = B q_4$$

6. **Normalizar $K$:**
   
   Asegurarse de que el elemento (3,3) de $K$ sea igual a 1.

#### Consideraciones Adicionales:

- **Ajuste de Signos:**
  - Los signos de los elementos diagonales de $K$ (focales en píxeles) pueden no ser los deseados. Los signos pueden modificarse ajustando consecuentemente $R$.
  - Si $f_k K_{11}$ es negativo y se desea positivo, se puede multiplicar $K$ y $R$ por matrices de signo adecuadas.

- **Determinante de $U$:**
  - Si $\det(U) = -1$, se debe multiplicar $U$ y el vector $q_4$ por -1.

- **Verificación de Resultados:**
  - Verificar que $U^{-1} B P_{3x3} \approx I$ para confirmar que la factorización fue correcta.

#### Implementación en MATLAB:

```matlab
% Cargar los puntos desde archivos
load -ASCII coordassolute.txt
load -ASCII coordpixelDX.txt

% Determinar el número de puntos cargados
N = size(coordassolute, 1);

% Convertir los puntos en coordenadas homogéneas
M = [coordassolute ones(N, 1)];
m = [coordpixelDX ones(N, 1)];

% Preparar la matriz de coeficientes del sistema
A = zeros(2 * N, 12);
for i = 1:N
    A(2 * i - 1, :) = [zeros(1, 4) -m(i, 3) * M(i, :) m(i, 2) * M(i, :)];
    A(2 * i, :) = [m(i, 3) * M(i, :) zeros(1, 4) -m(i, 1) * M(i, :)];
end

% Resolver el sistema Ap = 0 con descomposición SVD
[U, S, V] = svd(A);

% La solución p es la última columna (la 12) de V
p = V(:, 12);

% Construir la matriz de proyección P
P = [p(1:4)'; p(5:8)'; p(9:12)'];

% Seleccionar las primeras tres columnas de P
P_3x3 = P(:, 1:3);

% Invertir P_3x3
P_3x3_inv = inv(P_3x3);

% Aplicar factorización QR a P_3x3_inv
[U, B] = qr(P_3x3_inv);

% Determinar K y R
K = inv(B);
R = inv(U);

% Normalizar K
K = K / K(3, 3);

% Calcular t usando la cuarta columna de P
q4 = P(:, 4);
t = K \ q4;

% Ajustar signos si es necesario
if K(1, 1) < 0
    K(:, 1) = -K(:, 1);
    R(1, :) = -R(1, :);
end
if K(2, 2) < 0
    K(:, 2) = -K(:, 2);
    R(2, :) = -R(2, :);
end

% Mostrar resultados
disp('Matriz K:');
disp(K);
disp('Matriz R:');
disp(R);
disp('Vector t:');
disp(t);
```






### Descomposición analitica de P (SVD)

#### Paso 1: SVD de $P$
Descomponer $P$ usando la descomposición en valores singulares.

$$ P = U \Sigma V^T $$

#### Paso 2: Extraer Matrices
- **Matriz de Rotación $R$:** Se obtiene de la matriz $U$.
- **Matriz $K$:** Se obtiene a partir de $\Sigma$ y $V^T$.

#### Paso 3: Calcular Parámetros
- **Parámetros Intrínsecos:** A partir de $K$.
- **Parámetros Extrínsecos:** A partir de $R$ y la traslación derivada.

#### Ejemplo:
1. **Realizar SVD:**
   
   $$ P = U \Sigma V^T $$

2. **Extraer y normalizar $K$:**
   
   $$ K = \Sigma \times V^T $$

3. **Extraer parámetros:**
   - **Focal Lengths:** $f_x, f_y$
   - **Principal Point:** $u_0, v_0$


#### Introduzione
Un metodo alternativo per determinar los parámetros intrínsecos y extrínsecos de la cámara a partir de la matriz de proyección $P$ se basa en las expresiones analíticas de los parámetros de calibración en función de los elementos de $P$.

#### Matriz de Proyección $P$
Se considera la matriz de proyección $P$ en la forma:

$$ P = \begin{bmatrix} q_1^T \\ q_2^T \\ q_3^T \end{bmatrix} = \begin{bmatrix} p_{11} & p_{12} & p_{13} & p_{14} \\ p_{21} & p_{22} & p_{23} & p_{24} \\ p_{31} & p_{32} & p_{33} & p_{34} \end{bmatrix} $$

#### Suposiciones y Ecuaciones Base

Se asume un ángulo de skew $\beta = \frac{\pi}{2}$, y se tiene la relación:

$$ P = K [R | t] $$

Donde:

$$ K = \begin{bmatrix} f_u & 0 & u_0 \\ 0 & f_v & v_0 \\ 0 & 0 & 1 \end{bmatrix} $$

$$ [R | t] = \begin{bmatrix} r_{11} & r_{12} & r_{13} & t_x \\ r_{21} & r_{22} & r_{23} & t_y \\ r_{31} & r_{32} & r_{33} & t_z \end{bmatrix} $$

#### Desarrollo

La matriz de proyección $P$ se puede escribir como:

$$ P = \begin{bmatrix} f_u r_{11} & f_u r_{12} & f_u r_{13} & f_u t_x + u_0 r_{31} \\ f_v r_{21} & f_v r_{22} & f_v r_{23} & f_v t_y + v_0 r_{32} \\ r_{31} & r_{32} & r_{33} & t_z \end{bmatrix} $$

Comparando con la forma general de $P$, tenemos:

$$ P = \begin{bmatrix} p_{11} & p_{12} & p_{13} & p_{14} \\ p_{21} & p_{22} & p_{23} & p_{24} \\ p_{31} & p_{32} & p_{33} & p_{34} \end{bmatrix} $$

#### Determinación de Parámetros

1. **Traslación $t_z$:**

$$ t_z = \pm p_{34} $$

2. **Punto Principal:**

$$ u_0 = \frac{p_{11} p_{32} - p_{12} p_{31}}{p_{31}^2} $$
$$ v_0 = \frac{p_{21} p_{32} - p_{22} p_{31}}{p_{31}^2} $$

3. **Longitudes Focales:**

$$ f_u = \pm \sqrt{\frac{(p_{11} - u_0 p_{31})^2 + (p_{12} - u_0 p_{32})^2 + (p_{13} - u_0 p_{33})^2}{p_{31}^2}} $$
$$ f_v = \pm \sqrt{\frac{(p_{21} - v_0 p_{31})^2 + (p_{22} - v_0 p_{32})^2 + (p_{23} - v_0 p_{33})^2}{p_{32}^2}} $$

4. **Componentes de Traslación:**

$$ t_x = \frac{p_{14} - u_0 p_{34}}{f_u} $$
$$ t_y = \frac{p_{24} - v_0 p_{34}}{f_v} $$

5. **Componentes de la Rotación:**

$$ r_{11} = \frac{p_{11}}{f_u} $$
$$ r_{12} = \frac{p_{12}}{f_u} $$
$$ r_{13} = \frac{p_{13}}{f_u} $$
$$ r_{21} = \frac{p_{21}}{f_v} $$
$$ r_{22} = \frac{p_{22}}{f_v} $$
$$ r_{23} = \frac{p_{23}}{f_v} $$
$$ r_{31} = p_{31} $$
$$ r_{32} = p_{32} $$
$$ r_{33} = p_{33} $$

#### Signos y Ambigüedad

- Hay cuatro posibles conjuntos de parámetros, debido a la elección de signos y la posición relativa del centro de proyección respecto al plano del sensor.

#### Ejemplo en MATLAB

```matlab
% Supongamos que ya hemos calculado la matriz P
P = [ ... ]; % Matriz de proyección 3x4

% Extraemos los elementos de P
p11 = P(1,1); p12 = P(1,2); p13 = P(1,3); p14 = P(1,4);
p21 = P(2,1); p22 = P(2,2); p23 = P(2,3); p24 = P(2,4);
p31 = P(3,1); p32 = P(3,2); p33 = P(3,3); p34 = P(3,4);

% Determinamos t_z
tz = p34;

% Determinamos el punto principal
u0 = (p11*p32 - p12*p31) / (p31^2);
v0 = (p21*p32 - p22*p31) / (p31^2);

% Determinamos las longitudes focales
fu = sqrt((p11 - u0*p31)^2 + (p12 - u0*p32)^2 + (p13 - u0*p33)^2) / abs(p31);
fv = sqrt((p21 - v0*p31)^2 + (p22 - v0*p32)^2 + (p23 - v0*p33)^2) / abs(p32);

% Determinamos la traslación
tx = (p14 - u0*p34) / fu;
ty = (p24 - v0*p34) / fv;

% Determinamos la matriz de rotación
R = [
    p11/fu, p12/fu, p13/fu;
    p21/fv, p22/fv, p23/fv;
    p31, p32, p33
];

% Normalizamos la matriz de rotación si es necesario
[U,~,V] = svd(R);
R = U * V';

% Mostrar resultados
disp('Longitud focal (fu):'); disp(fu);
disp('Longitud focal (fv):'); disp(fv);
disp('Punto principal (u0, v0):'); disp([u0, v0]);
disp('Vector de traslación (tx, ty, tz):'); disp([tx, ty, tz]);
disp('Matriz de rotación (R):'); disp(R);
```


## Propagación de la Incertidumbre en la Calibración Lineal

La incertidumbre en la calibración puede afectar la precisión de los parámetros estimados:

1. **Modelado de la Incertidumbre:** Utilizar modelos estadísticos para evaluar cómo el ruido en los datos de entrada se propaga a los parámetros calibrados.
2. **Análisis de Sensibilidad:** Evaluar la sensibilidad de los parámetros de la cámara a las perturbaciones en los datos de entrada.


### 9 Propagazione dell’Incertezza nella Calibrazione Lineare

Uno dei vantaggi dei metodi di calibrazione lineari, come il metodo DLT, è che permettono di applicare la legge di propagazione dell’incertezza per stimare analiticamente l’incertezza dei parametri di calibrazione. Questa sezione introduce brevemente un metodo descritto da Chen et al. (2008) e Di Leo et al. (2010), che sarà ulteriormente esplorato nel capitolo sui sistemi di misura stereoscopici.

#### Metodo DLT e Incertezza

Il metodo DLT stima i parametri della telecamera risolvendo ai minimi quadrati il sistema $0 = Ap$ (3.48). La calibrazione può essere vista come una misurazione indiretta, con le grandezze indipendenti in ingresso $(x_i, y_i, z_i, u_i, v_i)$ che definiscono la matrice $A$, raccolte nel vettore $\mathbf{c}$:

$$ \mathbf{c} = [x_1, y_1, z_1, u_1, v_1, x_2, y_2, z_2, u_2, v_2, \ldots, x_n, y_n, z_n, u_n, v_n]^T $$

e i parametri di calibrazione in uscita, rappresentati dal vettore $\boldsymbol{\alpha}$:

$$ \boldsymbol{\alpha} = [f_u, f_v, u_0, v_0, \phi, \theta, \psi, t_x, t_y, t_z]^T $$

La calibrazione può essere allora scritta sotto forma di funzione vettoriale implicita:

$$ \mathbf{F}(\mathbf{c}, \boldsymbol{\alpha}) = 0 $$

#### Propagazione dell’Incertezza

Le matrici di covarianza degli ingressi $\mathbf{c}$ e delle uscite $\boldsymbol{\alpha}$ sono legate dalla relazione:

$$ \Lambda_{\alpha} = J_{\alpha} \Lambda_{c} J_{\alpha}^T $$

dove:
- $\Lambda_{\alpha}$ è la matrice di covarianza dei parametri di calibrazione.
- $\Lambda_{c}$ è la matrice di covarianza delle coordinate di ingresso.

#### Calcolo delle Matrici Jacobiane

La matrice Jacobiana degli ingressi $J_c$ e la matrice Jacobiana delle uscite $J_{\alpha}$ si definiscono come:

$$ J_c = \left[ \frac{\partial \mathbf{F}}{\partial \mathbf{c}} \right] $$
$$ J_{\alpha} = \left[ \frac{\partial \mathbf{F}}{\partial \boldsymbol{\alpha}} \right] $$

La matrice di covarianza delle uscite si ottiene quindi come:

$$ \Lambda_{\alpha} = J_{\alpha}^{\dagger} \Lambda_{c} (J_{\alpha}^{\dagger})^T $$

dove $J_{\alpha}^{\dagger}$ è la pseudoinversa di $J_{\alpha}$.

#### Procedura di Calcolo

1. **Definire il sistema di equazioni implicite:**

$$ \mathbf{F}(\mathbf{c}, \boldsymbol{\alpha}) = 0 $$

2. **Calcolare le matrici Jacobiane:**

$$ J_c = \left[ \frac{\partial \mathbf{F}}{\partial \mathbf{c}} \right] $$
$$ J_{\alpha} = \left[ \frac{\partial \mathbf{F}}{\partial \boldsymbol{\alpha}} \right] $$

3. **Determinare la matrice di covarianza delle uscite:**

$$ \Lambda_{\alpha} = J_{\alpha}^{\dagger} \Lambda_{c} (J_{\alpha}^{\dagger})^T $$

4. **Estrarre le incertezze dei parametri di calibrazione dalla diagonale di $\Lambda_{\alpha}$:**

Gli elementi sulla diagonale di $\Lambda_{\alpha}$ rappresentano le varianze dei parametri di calibrazione, e quindi le incertezze si ottengono come la radice quadrata di questi elementi.

### Esempio in MATLAB

```matlab
% Supponiamo che A, p e c siano definiti
% A = ... % matrice di calibrazione
% p = ... % soluzione dei parametri
% c = ... % vettore delle coordinate

% Calcolare le matrici Jacobiane
J_c = ... % Calcolare la Jacobiana degli ingressi
J_alpha = ... % Calcolare la Jacobiana delle uscite

% Definire la matrice di covarianza degli ingressi (esempio)
Lambda_c = diag([1e-4, 1e-4, 1e-4, 1e-2, 1e-2]);

% Calcolare la pseudoinversa di J_alpha
J_alpha_pseudo = pinv(J_alpha);

% Calcolare la matrice di covarianza delle uscite
Lambda_alpha = J_alpha_pseudo * Lambda_c * J_alpha_pseudo';

% Estrarre le incertezze dei parametri di calibrazione
incertezze = sqrt(diag(Lambda_alpha));

% Mostrare le incertezze
disp('Incertezze dei parametri di calibrazione:');
disp(incertezze);
```


## Ejemplo de todo lo visto
Claro, a continuación te proporcionaré un ejercicio práctico que abarca varios de los conceptos de calibración de cámaras discutidos en los apartados resumidos. Este ejercicio utilizará la estimación de la matriz de proyección mediante pseudoinversa, la evaluación del error de reproyección, y la descomposición de la matriz de proyección para obtener los parámetros intrínsecos y extrínsecos de la cámara.

### Ejercicio Práctico: Calibración de Cámara usando Pseudoinversa y Descomposición

#### Parte 1: Datos de Entrada
Disponemos de las siguientes correspondencias entre puntos 3D y sus proyecciones 2D en la imagen.

| Punto 3D (X, Y, Z) | Coordenadas 2D (u, v) |
|-------------------|-----------------------|
| (0, 0, 0)         | (150, 200)            |
| (1, 0, 0)         | (250, 200)            |
| (1, 1, 0)         | (250, 300)            |
| (0, 1, 0)         | (150, 300)            |
| (0, 0, 1)         | (175, 175)            |
| (1, 0, 1)         | (275, 175)            |
| (1, 1, 1)         | (275, 275)            |
| (0, 1, 1)         | (175, 275)            |

#### Parte 2: Construcción de la Matriz de Diseño y Estimación de $\mathbf{P}$

1. **Construcción de la Matriz de Diseño $A$:**

Para cada correspondencia \((X, Y, Z) \leftrightarrow (u, v)\), la matriz $A$ se construye de la siguiente manera:
$$
A = \begin{bmatrix}
X_1 & Y_1 & Z_1 & 1 & 0 & 0 & 0 & 0 & -u_1X_1 & -u_1Y_1 & -u_1Z_1 & -u_1 \\
0 & 0 & 0 & 0 & X_1 & Y_1 & Z_1 & 1 & -v_1X_1 & -v_1Y_1 & -v_1Z_1 & -v_1 \\
\vdots & \vdots & \vdots & \vdots & \vdots & \vdots & \vdots & \vdots & \vdots & \vdots & \vdots & \vdots \\
X_n & Y_n & Z_n & 1 & 0 & 0 & 0 & 0 & -u_nX_n & -u_nY_n & -u_nZ_n & -u_n \\
0 & 0 & 0 & 0 & X_n & Y_n & Z_n & 1 & -v_nX_n & -v_nY_n & -v_nZ_n & -v_n \\
\end{bmatrix}
$$

2. **Cálculo de $\mathbf{P}$ mediante Pseudoinversa:**

Resolvemos $A \mathbf{p} = 0$, donde $\mathbf{p}$ contiene los elementos de la matriz de proyección $\mathbf{P}$.

#### Parte 3: Evaluación del Error de Reproyección

Calculamos las coordenadas reproyectadas utilizando $\mathbf{P}$ y comparamos con las observadas para obtener el error de reproyección.

#### Parte 4: Descomposición de $\mathbf{P}$ para Obtener Parámetros de la Cámara

1. **Descomposición QR:** Descomponemos $\mathbf{P}$ en $\mathbf{K}$, $\mathbf{R}$, y $\mathbf{t}$.
2. **Evaluación de Parámetros Intrínsecos y Extrínsecos:** Interpretamos las matrices obtenidas para definir los parámetros de la cámara.

### Solución

#### Parte 2: Construcción de la Matriz de Diseño y Estimación de $\mathbf{P}$

```python
import numpy as np

# Datos de entrada
puntos_3D = np.array([
    [0, 0, 0],
    [1, 0, 0],
    [1, 1, 0],
    [0, 1, 0],
    [0, 0, 1],
    [1, 0, 1],
    [1, 1, 1],
    [0, 1, 1]
])

puntos_2D = np.array([
    [150, 200],
    [250, 200],
    [250, 300],
    [150, 300],
    [175, 175],
    [275, 175],
    [275, 275],
    [175, 275]
])

# Construcción de la matriz A
num_puntos = puntos_3D.shape[0]
A = []

for i in range(num_puntos):
    X, Y, Z = puntos_3D[i]
    u, v = puntos_2D[i]
    A.append([X, Y, Z, 1, 0, 0, 0, 0, -u*X, -u*Y, -u*Z, -u])
    A.append([0, 0, 0, 0, X, Y, Z, 1, -v*X, -v*Y, -v*Z, -v])

A = np.array(A)

# Solución mediante pseudoinversa
U, S, Vt = np.linalg.svd(A)
P = Vt[-1].reshape(3, 4)

print("Matriz de Proyección P:")
print(P)
```

#### Parte 3: Evaluación del Error de Reproyección

```python
# Reproyección de puntos 3D usando la matriz P
puntos_3D_homog = np.hstack((puntos_3D, np.ones((num_puntos, 1))))
puntos_2D_proj = (P @ puntos_3D_homog.T).T
puntos_2D_proj /= puntos_2D_proj[:, 2][:, np.newaxis]

# Error de reproyección
error_reproy = np.linalg.norm(puntos_2D - puntos_2D_proj[:, :2], axis=1)
error_total = np.sum(error_reproy)

print("Error total de reproyección:", error_total)
```

#### Parte 4: Descomposición de $\mathbf{P}$ para Obtener Parámetros de la Cámara

```python
# Descomposición QR para obtener parámetros intrínsecos y extrínsecos
M = P[:, :3]
R, K = np.linalg.qr(np.linalg.inv(M))
K = np.linalg.inv(K)
K /= K[2, 2]  # Normalización
t = np.linalg.inv(K) @ P[:, 3]

print("Matriz Intrínseca K:")
print(K)
print("Matriz de Rotación R:")
print(R)
print("Vector de Traslación t:")
print(t)
```

Este ejercicio ilustra cómo utilizar técnicas de calibración de cámaras para obtener la matriz de proyección, evaluar la precisión de la calibración mediante el error de reproyección y descomponer la matriz de proyección para obtener los parámetros intrínsecos y extrínsecos de la cámara. Si tienes alguna pregunta o necesitas más detalles, no dudes en decírmelo.