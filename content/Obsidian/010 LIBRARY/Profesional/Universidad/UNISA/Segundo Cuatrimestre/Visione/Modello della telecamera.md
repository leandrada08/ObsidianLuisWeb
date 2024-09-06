## Introducción a los Modelos de Cámara

Un modelo de cámara es una representación matemática que describe cómo un punto tridimensional en el mundo real se proyecta en un punto bidimensional en la imagen capturada por la cámara.
### Conceptos Básicos

1. **Proyección**: La cámara proyecta puntos en el espacio tridimensional a puntos en un plano bidimensional (la imagen). 
2. **Parámetros Intrínsecos**: Describen las propiedades internas de la cámara, como la distancia focal, el centro de la imagen y los coeficientes de distorsión.
3. **Parámetros Extrínsecos**: Describen la posición y orientación de la cámara en el espacio 3D respecto a una referencia.

### Tipos de Modelos de Cámara

#### Modelo Pinhole

- Es el modelo más simple y ampliamente utilizado.
- Se basa en la proyección perspectiva, donde todos los rayos de luz pasan a través de un punto llamado centro de proyección.

**Ecuación de Proyección:**
$$
\begin{bmatrix}
x \\
y \\
1
\end{bmatrix}
=
K \begin{bmatrix}
R & t \\
0 & 1
\end{bmatrix}
\begin{bmatrix}
X \\
Y \\
Z \\
1
\end{bmatrix}
$$

**Aplicaciones:**
- Visión por computadora general
- Calibración de cámaras

#### Modelo Fisheye

- Utilizado para lentes de gran angular que capturan un campo de visión muy amplio.
- Introduce una distorsión radial significativa.

**Ecuaciones de Proyección:**
- Varias ecuaciones matemáticas, como la proyección equisólida, estereográfica, ortográfica y rectilínea, que describen cómo se proyecta la esfera visual en el plano de la imagen.

**Aplicaciones:**
- Captura panorámica
- Robótica y navegación autónoma

#### Modelo de Cámara de Proyección Ortogonal

**Características:**
- Proyección paralela en lugar de perspectiva.
- No tiene en cuenta la profundidad, lo que significa que los objetos no se escalan con la distancia.

**Ecuación de Proyección:**
$$
\mathbf{x} = K \cdot [I | 0] \cdot \mathbf{X}
$$
donde \(I\) es la matriz identidad.

**Aplicaciones:**
- Ingeniería y diseño asistido por computadora (CAD)
- Cartografía y planos arquitectónicos

####  Modelo de Cámara de Ojo de Gato (Catadioptric)
- Combina lentes y espejos para capturar un campo de visión muy amplio.
- Utiliza espejos parabólicos o hiperbólicos junto con una lente de cámara.

**Aplicaciones:**
- Visión omnidireccional
- Sistemas de vigilancia

#### Modelo de Cámara Estereoscópica
- Utiliza dos o más cámaras para obtener diferentes perspectivas de la misma escena.
- Permite la reconstrucción 3D mediante la triangulación de puntos correspondientes en diferentes imágenes.
**Aplicaciones:**
- Reconstrucción 3D
- Vehículos autónomos



### 2. Fundamentos de la Proyección de Cámara

#### Introducción

La proyección de cámara es el proceso mediante el cual una escena tridimensional se convierte en una imagen bidimensional. Este proceso es fundamental para la visión por computadora y se basa en principios geométricos y ópticos. Comprender estos fundamentos es esencial para trabajar con modelos de cámara, ya sea para calibración, corrección de distorsión o reconstrucción 3D.

#### Conceptos Clave

1. **Proyección Perspectiva**: Describe cómo los rayos de luz que pasan a través de un punto de proyección (o pinhole) forman una imagen en el plano de la cámara.
2. **Proyección Ortográfica**: En esta proyección, los rayos de luz son paralelos y no convergen en un punto. Es una aproximación útil para ciertos tipos de imágenes técnicas y cartográficas.

### Proyección Perspectiva (Modelo Pinhole)

#### Principios Básicos

**Centro de Proyección**:
- El centro de proyección es el punto desde el cual los rayos de luz que pasan a través de la lente convergen para formar una imagen en el plano de la cámara.
- Este punto es análogo al "agujero" en una cámara estenopeica (pinhole camera).

**Plano de Imagen**:
- El plano de imagen es la superficie sobre la cual se proyectan los puntos tridimensionales del mundo real.
- En una cámara, esto corresponde al sensor de imagen o al plano de la película.

#### Ecuación de Proyección

La proyección de un punto tridimensional $\mathbf{X}$ en el espacio al plano de la imagen se describe mediante la ecuación de proyección:
$$
\begin{bmatrix}
x \\
y \\
1
\end{bmatrix} 
= K \begin{bmatrix}
R & t \\
0 & 1
\end{bmatrix} 
\begin{bmatrix}
X \\
Y \\
Z \\
1
\end{bmatrix}
$$

Donde:
- $\begin{bmatrix} X & Y & Z \end{bmatrix}^T$ es un punto en el espacio tridimensional en coordenadas homogéneas.
- $\begin{bmatrix} x & y \end{bmatrix}^T$ es la proyección de ese punto en el plano de la imagen en coordenadas homogéneas.
- $K$ es la matriz de parámetros intrínsecos de la cámara.
- $R$ es la matriz de rotación y $t$ es el vector de traslación, representando la orientación y posición de la cámara en el espacio.

#### Parámetros Intrínsecos

La matriz de parámetros intrínsecos $K$ describe las propiedades internas de la cámara:
$$
K = \begin{bmatrix}
f_x & 0 & c_x \\
0 & f_y & c_y \\
0 & 0 & 1
\end{bmatrix}
$$

Donde:
- $f_x$ y $f_y$ son las distancias focales en los ejes $x$ e $y$, respectivamente.
- $c_x$ y $c_y$ son las coordenadas del centro óptico (el punto donde el eje óptico intersecta el plano de la imagen).

#### Parámetros Extrínsecos

Los parámetros extrínsecos ($R$ y $t$) describen la posición y orientación de la cámara en el espacio tridimensional:
- **Rotación ($R$)**: Matriz de rotación que describe cómo está orientada la cámara respecto a un marco de referencia global.
- **Traslación ($t$)**: Vector de traslación que describe la posición de la cámara en el espacio tridimensional.

### Proyección Ortográfica

#### Principios Básicos

En la proyección ortográfica, los rayos de luz son paralelos y no convergen en un punto. Esto implica que no hay perspectiva y los objetos no cambian de tamaño con la distancia:
- **Aplicaciones**: Este tipo de proyección se utiliza comúnmente en aplicaciones de ingeniería, diseño asistido por computadora (CAD) y cartografía.

#### Ecuación de Proyección

La proyección ortográfica de un punto tridimensional $\mathbf{X}$ al plano de la imagen se describe mediante la ecuación:
$$
\mathbf{x} = K \cdot [I | 0] \cdot \mathbf{X}
$$

Donde:
- $I$ es la matriz identidad.
- $\mathbf{X}$ es un punto en el espacio tridimensional.

### Diferencias entre Modelos Pinhole y Fisheye

#### Modelo Pinhole

- **Proyección Lineal**: La relación entre la distancia en el mundo real y la distancia en la imagen es lineal.
- **Ángulo de Visión Limitado**: Generalmente, el ángulo de visión es más estrecho y sin distorsión significativa en los bordes.

#### Modelo Fisheye

- **Proyección No Lineal**: Introduce distorsión radial significativa, especialmente en los bordes de la imagen.
- **Ángulo de Visión Amplio**: Puede capturar hasta 180 grados o más, lo que permite ver más del entorno en una sola imagen.

### Fundamentos Matemáticos de la Proyección

#### Coordenadas Homogéneas

Las coordenadas homogéneas se utilizan para simplificar las transformaciones lineales y las proyecciones en visión por computadora:
- **Punto 3D**: Un punto en el espacio 3D $(X, Y, Z)$ se representa como $(X, Y, Z, 1)$.
- **Punto 2D**: Un punto en el plano de la imagen $(x, y)$ se representa como $(x, y, 1)$.

#### Transformación de Coordenadas

- **Rotación ($R$)**: Describe cómo la cámara está orientada en el espacio tridimensional. Es una matriz 3x3 que rota puntos en el espacio.
- **Traslación ($t$)**: Describe la posición de la cámara en el espacio tridimensional. Es un vector 3x1 que traslada puntos en el espacio.


## [[Modello Pin-Hole]]

## [[Modello Fisheye]]




