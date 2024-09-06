## Métodos no lineales para la Estimación de la Matriz $P$

Los métodos lineales, como el DLT y la pseudoinversa, son eficientes pero presentan limitaciones:

**Ventajas y Limitaciones**
- Tanto el método DLT como el método de pseudoinversa son fáciles de implementar.
- **Minimización de Funciones Objetivo Algebricas:** 
  - **DLT:** Minimiza $\|Ap\|_2$.
  - **Pseudoinversa:** Minimiza $\|Aq - b\|_2$.
- Ambos métodos minimizan funciones que no consideran directamente la incertidumbre en las coordenadas.
- Para obtener resultados más precisos, especialmente con incertidumbre en las coordenadas, es mejor minimizar funciones objetivo con significado geométrico.

#### Algoritmos Iterativos de Minimización
- **Ventajas:**
  - Mayor precisión en condiciones de incertidumbre.
  - Mejor ajuste en configuraciones con datos dispersos.
- **Desventajas:**
  - **Tiempo de Cálculo:** Mayor tiempo requerido, aunque manejable con tecnologías modernas.
  - **Dificultad en la Gestión:** La precisión depende de la calidad de la solución inicial.
  - **Solución Inicial:** Puede calcularse previamente usando DLT.

**Algoritmos Comunes**
- **Downhill Simplex**
- **Levenberg-Marquardt**

#### Consideraciones Prácticas
- **Dependencia de la Solución Inicial:** La calidad de los resultados depende en gran medida de la precisión de la solución inicial.
- **Dispersión de Resultados:** La incertidumbre en las coordenadas puede causar variabilidad en los resultados de los algoritmos iterativos.
- **Calibración Repetida:** Promedia los resultados para mejorar la precisión en presencia de incertidumbre.

### Algoritmi di Calibrazione Alternativi

#### Limiti del Metodo DLT
L'algoritmo DLT descritto richiede che i punti di calibrazione abbiano coordinate assolute note e che non siano complanari, il che significa che è "a target noto in pose note". Questo può risultare difficile da eseguire sul campo per vari motivi, come lo spazio angusto o la mancanza di supporti adeguati.

#### Algoritmi "a Target Noto in Pose non Note"
In questi algoritmi, il target di calibrazione è noto solo rispetto al piano su cui è stampato, e può essere posizionato in pose arbitrarie e sconosciute. Uno degli algoritmi più diffusi in questo contesto è l'algoritmo di Zhang.

#### Algoritmo di Zhang

- **Introduzione:** L'algoritmo di Zhang, descritto in Zhang (2000) e nel technical report (Zhang, 1998), è progettato per calibrare una telecamera usando un piano di calibrazione posizionato in diverse pose arbitrarie.
  
- **Procedura di Calibrazione:**
  1. **Target di Calibrazione:** Un piano con un pattern di punti noto, come una griglia di scacchi, che può essere facilmente rilevato in immagini.
  2. **Posizionamento del Target:** Il target viene posizionato in diverse pose arbitrarie rispetto alla telecamera.
  3. **Cattura delle Immagini:** Si catturano immagini del target in queste diverse pose.
  4. **Rilevamento del Pattern:** Si rilevano le coordinate dei punti del pattern nell'immagine.
  5. **Calcolo della Matrice di Calibrazione:** Si utilizza un algoritmo di ottimizzazione per minimizzare la differenza tra le posizioni osservate dei punti e quelle previste dal modello della telecamera.

- **Vantaggi:**
  - Non richiede un setup rigido e preciso.
  - Può essere eseguito in condizioni meno controllate rispetto al metodo DLT.
  - Adeguato per applicazioni sul campo.

- **Implementazione di Base:**
  - **Rilevamento dei Punti:** Utilizzo di tecniche di rilevamento di pattern per identificare i punti del target nelle immagini.
  - **Ottimizzazione:** Applicazione di metodi di ottimizzazione come Levenberg-Marquardt per minimizzare l'errore di riproiezione.


## Metodo Zhang
La calibración de cámaras en la visión por computadora 3D es muy imporante para extraer información métrica de imágenes 2D. Se discuten dos categorías principales de técnicas de calibración:

1. **Calibración fotogramétrica:**
   - Se realiza observando un objeto de calibración cuya geometría en el espacio 3D es conocida con alta precisión.
   - Normalmente, el objeto de calibración consiste en dos o tres planos ortogonales.
   - Este método requiere un equipo de calibración costoso y una configuración elaborada.

2. **Auto-calibración:**
   - No utiliza ningún objeto de calibración.
   - Se basa en mover una cámara en una escena estática, aprovechando la rigidez de la escena para proporcionar restricciones en los parámetros internos de las cámaras.
   - A pesar de su flexibilidad, no es aún madura y a veces no produce resultados confiables debido a la cantidad de parámetros que deben estimarse.

Zhang introduce una nueva técnica de calibración que solo requiere que la cámara observe un patrón plano en diferentes orientaciones, que puede ser movido libremente sin necesidad de conocer el movimiento. Esta técnica se sitúa entre la calibración fotogramétrica y la auto-calibración, usando información métrica 2D en lugar de 3D. Es más flexible y robusta que las técnicas clásicas y auto-calibración, haciéndola apta para aplicaciones del mundo real en sistemas de visión de escritorio (DVS)【15:0†source】.

### Capítulo 2: Ecuaciones Básicas

En este capítulo se examinan las restricciones en los parámetros intrínsecos de la cámara proporcionadas por la observación de un solo plano.

#### Notación

- Un punto 2D se denota por $m = [u, v]^T$.
- Un punto 3D se denota por $M = [X, Y, Z]^T$.
- Se usa $\tilde{x}$ para denotar el vector aumentado añadiendo 1 como último elemento: $\tilde{m} = [u, v, 1]^T$ y $\tilde{M} = [X, Y, Z, 1]^T$.

#### Modelo de Cámara Pinhole

La relación entre un punto 3D $M$ y su proyección en la imagen $m$ está dada por:

$$ s \tilde{m} = A \begin{bmatrix} R & t \end{bmatrix} \tilde{M} $$

donde:
- $s$ es un factor de escala arbitrario.
- $A$ es la matriz de parámetros intrínsecos de la cámara.
- $R$ y $t$ son los parámetros extrínsecos (rotación y traslación que relacionan el sistema de coordenadas del mundo con el sistema de coordenadas de la cámara).

La matriz $A$ se define como:

$$ A = \begin{bmatrix} \alpha & c & u_0 \\ 0 & \beta & v_0 \\ 0 & 0 & 1 \end{bmatrix} $$

donde:
- $\alpha$ y $\beta$ son los factores de escala en los ejes $u$ y $v$.
- $c$ describe el sesgo entre los dos ejes de la imagen.
- $(u_0, v_0)$ son las coordenadas del punto principal.

#### Homografía entre el Plano Modelo y su Imagen

Asumiendo que el plano modelo está en $Z = 0$, la relación entre un punto en el plano modelo $M$ y su imagen $m$ está dada por una homografía $H$:

$$ s \tilde{m} = H \tilde{M} $$

donde $H = A \begin{bmatrix} r_1 & r_2 & t \end{bmatrix}$ y $r_1$, $r_2$ son las primeras dos columnas de la matriz de rotación $R$.

#### Restricciones en los Parámetros Intrínsecos

Dado que los vectores $r_1$ y $r_2$ son ortonormales, se derivan dos restricciones básicas sobre los parámetros intrínsecos:

$$ h_1^T A^{-T} A^{-1} h_2 = 0 $$
$$ h_1^T A^{-T} A^{-1} h_1 = h_2^T A^{-T} A^{-1} h_2 $$

Estas ecuaciones permiten obtener restricciones sobre los parámetros intrínsecos a partir de una homografía, que tiene 8 grados de libertad mientras que hay 6 parámetros extrínsecos【15:6†source】【15:8†source】.

¿Te gustaría que profundicemos en algún aspecto específico de estas ecuaciones o en la forma de resolver la calibración usando estas restricciones?



### Capítulo 3: Resolución de la Calibración de la Cámara

Para resolver el problema de calibración de la cámara, se parte de una solución analítica que luego se refina mediante una técnica de optimización no lineal basada en el criterio de máxima verosimilitud. Además, se tiene en cuenta la distorsión de la lente, proporcionando tanto soluciones analíticas como no lineales.

- **Matriz $B$:** 
  $$ B = A^{-T} A^{-1} = \begin{pmatrix} B_{11} & B_{12} & B_{13} \\ B_{12} & B_{22} & B_{23} \\ B_{13} & B_{23} & B_{33} \end{pmatrix} $$

  Donde $B$ es una matriz simétrica definida por un vector de 6D $b = [B_{11}, B_{12}, B_{22}, B_{13}, B_{23}, B_{33}]^T$.

- **Ecuaciones Homogéneas:**
  Las dos restricciones fundamentales se pueden reescribir como ecuaciones homogéneas en $b$:
  $$ \begin{pmatrix} v_{12}^T \\ (v_{11} - v_{22})^T \end{pmatrix} b = 0 $$

  Con múltiples imágenes del plano modelo, se acumulan estas ecuaciones para obtener una solución única para $b$.

- **Parámetros Intrínsecos:**
  Una vez estimada la matriz $B$, se pueden extraer los parámetros intrínsecos de la cámara.

#### Estimación de Máxima Verosimilitud

- **Funcional a Minimizar:**
  $$ \sum_{i=1}^n \sum_{j=1}^m \|m_{ij} - \hat{m}(A, R_i, t_i, M_j)\|^2 $$

  Aquí, $\hat{m}(A, R_i, t_i, M_j)$ es la proyección del punto $M_j$ en la imagen $i$. La minimización se realiza usando el algoritmo de Levenberg-Marquardt.

#### Consideración de la Distorsión Radial

- **Modelado de la Distorsión:**
  Se consideran los primeros dos términos de la distorsión radial:
  $$ x' = x + x[k_1(x^2 + y^2) + k_2(x^2 + y^2)^2] $$
  $$ y' = y + y[k_1(x^2 + y^2) + k_2(x^2 + y^2)^2] $$

  Donde $k_1$ y $k_2$ son los coeficientes de distorsión radial. La estimación de $k_1$ y $k_2$ se realiza alternando entre la estimación de los parámetros intrínsecos y la distorsión.

### Capítulo 4: Configuraciones Degeneradas

Este capítulo aborda las configuraciones en las que imágenes adicionales no proporcionan más restricciones sobre los parámetros intrínsecos de la cámara. 

- **Dependencia de la Matriz de Rotación:**
  Si las matrices de rotación $R_2$ y $R_1$ no son independientes, la segunda imagen no proporciona restricciones adicionales. En particular, si un plano experimenta una traslación pura, entonces $R_2 = R_1$ y la imagen no es útil para la calibración de la cámara.

- **Proposición 1:**
  Si el plano modelo en la segunda posición es paralelo a su primera posición, la segunda homografía no proporciona restricciones adicionales. En la práctica, es fácil evitar esta configuración degenerada cambiando la orientación del plano modelo entre capturas.

Estos puntos permiten comprender las limitaciones del método de calibración y la necesidad de evitar ciertas configuraciones que no aportan información adicional para la estimación de parámetros【19:0†source】【19:1†source】【19:11†source】.

¿Te gustaría que profundicemos en algún aspecto específico de estos capítulos o necesitas algún detalle adicional?








































## Chat gpt
El algoritmo de Zhang se utiliza para calibrar cámaras mediante el uso de un patrón de referencia plano (como un tablero de ajedrez) que se visualiza en varias posiciones. El objetivo es determinar los parámetros intrínsecos y extrínsecos de la cámara, así como la distorsión de la lente.

#### 1. **Modelo de Cámara Pinhole**

El algoritmo de Zhang se basa en el modelo de cámara pinhole, donde se asume que la cámara proyecta puntos 3D en el mundo real en puntos 2D en la imagen a través de un proceso de proyección.

La relación entre un punto 3D en el mundo real $(X, Y, Z)$ y su correspondiente punto 2D en la imagen $(u, v)$ se puede expresar mediante la ecuación:

$$ s \begin{pmatrix} u \\ v \\ 1 \end{pmatrix} = \mathbf{A} \begin{pmatrix} R & t \end{pmatrix} \begin{pmatrix} X \\ Y \\ Z \\ 1 \end{pmatrix} $$

Donde:
- $s$ es un factor de escala.
- $\mathbf{A}$ es la matriz de parámetros intrínsecos de la cámara.
- $R$ es la matriz de rotación.
- $t$ es el vector de traslación.

#### 2. **Parámetros Intrínsecos**

La matriz de parámetros intrínsecos $\mathbf{A}$ tiene la forma:

$$ \mathbf{A} = \begin{pmatrix} f_x & 0 & c_x \\ 0 & f_y & c_y \\ 0 & 0 & 1 \end{pmatrix} $$

Donde:
- $f_x$ y $f_y$ son las distancias focales en términos de píxeles.
- $c_x$ y $c_y$ son las coordenadas del punto principal (centro óptico) de la imagen.

#### 3. **Distorsión de la Lente**

El algoritmo también considera la distorsión radial y tangencial de la lente. Los parámetros de distorsión típicos son $k_1, k_2, p_1$ y $p_2$, donde $k_1$ y $k_2$ son los coeficientes de distorsión radial y $p_1$ y $p_2$ son los coeficientes de distorsión tangencial.

#### 4. **Método de Calibración**

El método de Zhang sigue los siguientes pasos:

1. **Captura de Imágenes:** Se capturan varias imágenes del patrón plano en diferentes posiciones y orientaciones.
2. **Detección de Puntos de Referencia:** Se detectan los puntos de referencia (esquinas del tablero de ajedrez) en cada imagen.
3. **Estimación Inicial:** Se estima una solución inicial para los parámetros intrínsecos y extrínsecos utilizando un método lineal.
4. **Optimización no Lineal:** Se refina la estimación inicial mediante optimización no lineal (generalmente mediante el método de Levenberg-Marquardt) para minimizar el error de reproyección.

#### 5. **Error de Reproyección**

El error de reproyección es la diferencia entre las posiciones proyectadas de los puntos 3D en la imagen y las posiciones detectadas de esos puntos en la imagen. El objetivo de la calibración es minimizar este error.

### Ventajas y Limitaciones

- **Ventajas:**
  - No requiere un sistema de calibración complejo.
  - Es robusto y fácil de implementar.
  - Funciona bien con datos reales.

- **Limitaciones:**
  - La precisión puede verse afectada por errores en la detección de los puntos de referencia.
  - Requiere varias imágenes del patrón en diferentes posiciones y orientaciones.
### Estimación Inicial

La estimación inicial en el algoritmo de calibración de cámara de Zhang se realiza en dos partes principales: la estimación de los parámetros intrínsecos y la estimación de los parámetros extrínsecos. Aquí está el proceso detallado:

#### 1. **Estimación de los Parámetros Intrínsecos**

Primero, se realiza una estimación lineal de la matriz de parámetros intrínsecos $\mathbf{A}$. Esto se hace utilizando la homografía entre el plano del patrón y la imagen de ese patrón.

**Homografía:**

Una homografía es una transformación 2D que mapea puntos en el plano del patrón $(X, Y)$ a puntos en la imagen $(u, v)$ bajo la suposición de que $Z = 0$ (el patrón es plano).

$$ \begin{pmatrix} u \\ v \\ 1 \end{pmatrix} = \mathbf{H} \begin{pmatrix} X \\ Y \\ 1 \end{pmatrix} $$

Donde $\mathbf{H}$ es la matriz de homografía $3 \times 3$.

Para cada imagen del patrón, se calcula una homografía $\mathbf{H}$ usando correspondencias de puntos entre el patrón y la imagen.

**Cálculo de $\mathbf{A}$ a partir de Homografías:**

La matriz de parámetros intrínsecos $\mathbf{A}$ puede ser estimada resolviendo un sistema lineal de ecuaciones basado en las homografías. Si $\mathbf{H}_i$ es la homografía para la i-ésima imagen, entonces se construyen las siguientes ecuaciones:

$$ \mathbf{H}_i = \mathbf{A} [\mathbf{r}_1 \, \mathbf{r}_2 \, \mathbf{t}] $$

Donde $\mathbf{r}_1$ y $\mathbf{r}_2$ son las primeras dos columnas de la matriz de rotación $R$, y $\mathbf{t}$ es el vector de traslación.

Descomponiendo estas ecuaciones y agrupando términos, se obtiene un sistema lineal que se puede resolver utilizando métodos como la descomposición en valores singulares (SVD) para obtener una estimación inicial de $\mathbf{A}$.

#### 2. **Estimación de los Parámetros Extrínsecos**

Con $\mathbf{A}$ conocido, se pueden calcular las matrices de rotación $R$ y los vectores de traslación $t$ para cada imagen mediante descomposición de $\mathbf{H}_i$:

$$ \mathbf{H}_i = \mathbf{A} [\mathbf{r}_1 \, \mathbf{r}_2 \, \mathbf{t}] $$

Descomponiendo $\mathbf{H}_i$, se obtiene:

$$ \mathbf{r}_1 = \mathbf{A}^{-1} \mathbf{h}_1 $$
$$ \mathbf{r}_2 = \mathbf{A}^{-1} \mathbf{h}_2 $$
$$ \mathbf{t} = \mathbf{A}^{-1} \mathbf{h}_3 $$

Donde $\mathbf{h}_1, \mathbf{h}_2, \mathbf{h}_3$ son las columnas de $\mathbf{H}_i$.

Las columnas $\mathbf{r}_1$ y $\mathbf{r}_2$ se ortogonalizan y normalizan para obtener una matriz de rotación válida.

### Optimización No Lineal

Una vez que se tiene una estimación inicial de los parámetros intrínsecos y extrínsecos, el siguiente paso es refinar estos parámetros utilizando optimización no lineal. El objetivo es minimizar el error de reproyección.

#### Método de Levenberg-Marquardt

El método de optimización no lineal comúnmente utilizado es el método de Levenberg-Marquardt. Este método es una técnica iterativa que combina las características del método de Gauss-Newton y el método de gradiente descendente. Es particularmente adecuado para problemas de mínimos cuadrados no lineales.

**Función de Costo:**

La función de costo que se minimiza es el error de reproyección, definido como la suma de los errores cuadrados entre los puntos de imagen proyectados y los puntos de imagen observados.

$$ \text{Costo} = \sum_{i=1}^n \| \mathbf{p}_i - \mathbf{\hat{p}}_i \|^2 $$

Donde:
- $\mathbf{p}_i$ es la posición observada del punto $i$ en la imagen.
- $\mathbf{\hat{p}}_i$ es la posición proyectada del punto $i$ calculada a partir de los parámetros de la cámara.

**Iteraciones del Método:**

El método de Levenberg-Marquardt actualiza los parámetros de la cámara en cada iteración para reducir el error de reproyección:

$$ \mathbf{\theta}_{k+1} = \mathbf{\theta}_k - (\mathbf{J}^T \mathbf{J} + \lambda \mathbf{I})^{-1} \mathbf{J}^T \mathbf{r} $$

Donde:
- $\mathbf{\theta}$ son los parámetros de la cámara.
- $\mathbf{J}$ es la matriz Jacobiana de las derivadas parciales de los residuos $\mathbf{r}$ con respecto a $\mathbf{\theta}$.
- $\lambda$ es un parámetro de ajuste que controla el tamaño de los pasos.

El algoritmo ajusta $\lambda$ en cada iteración para garantizar la convergencia.

### Resumen

- **Estimación Inicial:**
  - Uso de homografías para obtener una estimación inicial de la matriz de parámetros intrínsecos $\mathbf{A}$.
  - Descomposición de homografías para obtener matrices de rotación $R$ y vectores de traslación $t$.

- **Optimización No Lineal:**
  - Refinamiento de los parámetros utilizando el método de Levenberg-Marquardt.
  - Minimización del error de reproyección.

¿Te gustaría profundizar más en algún aspecto específico de esta explicación, como los detalles matemáticos del método de Levenberg-Marquardt o el proceso de cálculo de homografías?