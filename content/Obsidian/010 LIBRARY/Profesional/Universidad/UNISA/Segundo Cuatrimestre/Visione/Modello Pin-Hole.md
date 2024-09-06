
## Resumen
### Modelo de Cámara Pinhole

El modelo de cámara pinhole es uno de los más simples y comunes en la visión artificial. Aquí están los conceptos clave:

1. **Modelo Geométrico**:
   - **Principio de la cámara oscura**: La cámara pinhole se basa en el principio de la cámara oscura, donde una pequeña abertura permite que la luz pase y forme una imagen invertida en la superficie opuesta.
   - **Proyección perspectiva**: Se asume que los rayos de luz pasan por un punto único, conocido como el centro de proyección, y se proyectan en un plano de imagen.

2. **Matemáticas del Modelo Pinhole**:
   - **Ecuación de proyección**: Un punto 3D $\mathbf{X} = [X, Y, Z]^T$ se proyecta en un punto 2D $\mathbf{x} = [x, y]^T$ en la imagen usando la siguiente ecuación:
     $$
     \begin{bmatrix}
     x \\
     y \\
     1
     \end{bmatrix} 
     = K \begin{bmatrix}
     R & t \\
     0 & 1
     \end{bmatrix} \begin{bmatrix}
     X \\
     Y \\
     Z \\
     1
     \end{bmatrix}
     $$
     donde $K$ es la matriz de parámetros intrínsecos de la cámara, $R$ es la matriz de rotación y $t$ es el vector de traslación.

3. **Parámetros Intrínsecos**:
   - **Foco $f$**: Distancia focal de la cámara.
   - **Centro de la imagen $(c_x, c_y)$**: Punto donde el eje óptico de la cámara intersecta el plano de la imagen.
   - **Factores de escala $(s_x, s_y)$**: Relación entre las unidades del mundo real y las unidades de la imagen.
## Desarrollo
![[Pasted image 20240530173601.png]]
- Las coordenadas reales son $M=[x,y,z]$
- Las coordenadas obtenidas son $m=[u,v]$
- El desafio de este capitulo es definir un vinculo analitico que vincule las coordenadas absolutas M con su imagen m.
### Sistemas de referencias
![[Pasted image 20240530175107.png]]
Se utilizan cuatro sistemas de referencia:
- Sistema de referencia absoluto ($x, y, z$): Independiente de la posición y orientación de la cámara.
- Sistema de referencia de la cámara ($x_c, y_c, z_c$): Con origen en el centro de proyección de la lente y el eje $z_c$ alineado con el eje óptico.
- Sistema de referencia de la imagen ($x', y'$): Orientado según los ejes de la matriz de celdas del sensor, con el origen en la intersección del plano del sensor y el eje $z_c$.
- Sistema de referencia en píxeles ($u, v$): Donde las coordenadas están en píxeles.

Las coordenadas de un punto objeto ($x, y, z$) se proyectan en coordenadas de imagen ($u, v$) a través de estas relaciones de transformación, considerando también la discretización del sensor.




![[Pasted image 20240530175149.png]]

### Modelo pin-hole
El modelo pin-hole representa una cámara idealizada con una caja oscura y un pequeño orificio que actúa como apertura, proyectando la imagen invertida en un plano de imagen.


#### Proyección Perspectiva

1. **Componentes del Modelo de Cámara Pin-hole**:
   - **Cámara Idealizada**: Caja oscura con un pequeño orificio (centro óptico).
   - **Plano de Imagen**: Superficie donde se forma la imagen, ubicada opuesta al orificio.
   - **Proyección de Rayos de Luz**: Los rayos de luz pasan a través del orificio y se proyectan invertidos en el plano de imagen.

2. **Geometría de la Proyección**:
   - **Plano Focal y Plano de Retina**: Paralelos y separados por la distancia focal $f$.
   - **Centro Óptico $C$**: Punto central del plano focal.
   - **Eje Óptico**: Línea perpendicular al plano de retina que pasa por el centro óptico.
   - **Punto Principal $c$**: Intersección del eje óptico con el plano de retina.
   - **Coordenadas en el Plano de Retina**: Proyección del punto $M$ en el plano de retina se denota como $m$.

### Coordenadas en píxeles → Cordenadas de la imagen
Las dimensiones de los píxeles en el sensor ($s_u$ y $s_v$) se utilizan para convertir las coordenadas en píxeles ($u, v$) a coordenadas en la imagen ($x', y'$) con las siguientes relaciones:
$$
x' = (u - u_0) \cdot s_u
$$
$$
y' = (v - v_0) \cdot s_v
$$
Donde ($u_0, v_0$) son las coordenadas del punto principal en píxeles. Esto facilita el paso a un sistema continuo y homogéneo de coordenadas.
![[Pasted image 20240530181423.png]]

1. El centro óptico de la cámara no coincide con el centro físico del CCD, sino que tiene coordenadas $(u_0, v_0)$.
2. Las coordenadas de un punto en el sistema de referencia estándar de la cámara se miden en píxeles, por lo que se introduce un factor de escala $s_u$ y $s_v$
3. La forma de los píxeles, en general, no es cuadrada: se deben considerar dos factores de escala diferentes, a lo largo de $u$ y $v$.
4. Debido a los desajustes en el escaneo de filas sucesivas de la pantalla, los ejes de referencia de la imagen $u$ y $v$ no son ortogonales, sino inclinados en un ángulo $\theta$.


### Coordenadas de la imagen → Coordenadas de la cámara(Proyección Perspectiva)
Utilizando las similitudes de triángulos en la **proyección perspectiva**, las coordenadas de la imagen ($x', y'$) se relacionan con las coordenadas de la cámara ($x_c, y_c, z_c$) mediante:
$$
x' = \frac{x_c \cdot f}{z_c}
$$
$$
y' = \frac{y_c \cdot f}{z_c}
$$
Donde $f$ es la constante de la cámara (distancia focal). Al resolver estas ecuaciones, se obtiene:
$$
u = -k_uf \cdot \frac{x_c}{z_c} + u_0
$$
$$
v = -k_v f \cdot \frac{y_c}{z_c} + v_0
$$
Estas ecuaciones permiten obtener las coordenadas de los píxeles ($u, v$) a partir de las coordenadas de la cámara ($x_c, y_c, z_c$).
![[Pasted image 20240530181613.png]]


#### Coordenadas homogéneas
Las coordenadas homogéneas son una forma conveniente de representar las transformaciones de proyección. Un punto en coordenadas cartesianas ($x, y$) puede ser representado en coordenadas homogéneas como ($X_1, X_2, X_3$), donde:
$$
x = \frac{X_1}{X_3}
$$
$$
y = \frac{X_2}{X_3}
$$
- Coordenadas homogéneas: usadas en geometría proyectiva, representan todos los puntos del plano, incluidos los del infinito.
	- Ej.: representan punto de intersección de rectas paralelas.
- Punto en el infinito tiene coordenadas (X1, X2, 0).
- No únicas: multiplicables por un factor de escala no nulo sin alterar la posición en el plano.
- Punto cartesiano (x1, x2) se vuelve homogéneo añadiendo una coordenada unitaria: (x1, x2, 1).
- Símbolo "~" indica coordenadas homogéneas.
- En espacio tridimensional: punto $(x1, x2, x3)$ se vuelve $(X1, X2, X3, X4)$ con $x1 = X1/X4$, $x2 = X2/X4$, $x3 = X3/X4$
	- Ejemplo de representación homogénea: $(x1, x2, x3, 1)$.

- Las coordenadas homogeneas son solo otra manera de representar las mismas coordenadas, es una transformacion de coordenads, que te permite representar puntos en el infinito
- **Símbolo de igualdad**: En coordenadas homogéneas expresa el paralelismo.
#### Ecuaciones de Proyección Perspectiva en notacion matricial
##### Matriz de parametros instrisecos
   - Coordenadas homogéneas de m y M: $m'$ y $M'$ $$
     m' = \begin{bmatrix} u \\ v \\ 1 \end{bmatrix}, \quad M' = \begin{bmatrix} x \\ y \\ z \\ 1 \end{bmatrix}
     $$
   - Reescribiendo m en ecuaciones de la camara:$$
     \lambda \begin{bmatrix} u \\ v \\ 1 \end{bmatrix}  = \begin{bmatrix} -k_uf & 0 & u_0\\ 0 & -k_vf & v_0  \\ 0 &0 & 1 \end{bmatrix} \begin{bmatrix} x_c \\ y_c \\ z_c  \end{bmatrix}
     $$
   - Pasando a notacion matricial nos que:
     $$
     \lambda m'=K M_c
     $$
    
Donde K es la matriz de los parametros intrisecos: $$K=\begin{bmatrix} -k_uf & 0 & u_0\\ 0 & -k_vf & v_0  \\ 0 &0 & 1 \end{bmatrix}$$
- Matriz K: contiene parámetros del modelo pin-hole de la cámara, depende solo de su geometría interna.
- Parámetros $fk_u$ y $fk_v$: Estos parametros son las constante f (en mm) multiplicada por factores de conversión horizontal y vertical $k_v$ y $k_u$ (en pixel/mm)
- $fk_u$ y $fk_v$: también llamados focal horizontal y vertical (en pixeles).
- Nota: terminología puede ser confusa, *f no es longitud focal*.
- Signos de $fk_u$ y $fk_v$ pueden variar según la orientación de los ejes x y y.
- $fk_u$ y $fk-v$ suelen tratarse como variables únicas, no separadas en $f, k_u$ y $k_v$.



### Coordenadas de la cámara → Coordenadas absolutas
El vínculo entre las coordenadas del punto en el sistema de referencia de la cámara ($x_c, y_c, z_c$) y sus coordenadas en el sistema de referencia absoluto ($x, y, z$) se realiza mediante una rototranslación:

$$
\begin{pmatrix}
x_c \\
y_c \\
z_c
\end{pmatrix} = R \begin{pmatrix}
x \\
y \\
z
\end{pmatrix} + t
$$

$$M_c=RM+t$$

donde $R$ es la matriz de rotación y $t$ es el vector de traslación. 
- Con $z = y = x = 0$, t = coordenadas de la cámara en el origen *O* del sistema absoluto.
- Matriz de rotación permite expresae *M* en coordenadas orientadas como la cámara con origen en *O*.
- Vector de traslación añade traslación de *O* a *C*.

Se puede reescribir la ecuacion como: $$M_C=R[M-C]$$
- $C= R^{-1}t$ es el centro de proyección de la cámara en coordenadas absolutas.
- Matriz de rotación tiene 9 elementos, no todos independientes, solo alteran orientación, no magnitud.
- Matriz de rotación es ortogonal $(R⁻¹ = R^{T})$, depende solo de 3 parámetros que describen completamente la rotacion.
	- Métodos para definir estos 3 parametro parámetros: eje de rotación (2 cosenos directores) y ángulo de rotación, o 3 ángulos de Euler.






### Formulación general del modelo pin-hole
Combinamos la ecuacion que relaciona las coordendas de la imagen a las coordendas de camara con la que relaciona las coordenas de la camara a las absolutas, podemos eliminar las coordenas de la camara llegando a la siguiente ecuacion. $$\lambda \tilde{m}=K[R|t]\tilde{M}$$
- $\tilde{M}$ coordinadas absolutas en sistemas de referencia homogeneo
- $G=[R|t]$ *matriz de parametros extrinsecos*.

Por lo cual podemos reescribir la ecuacion como: $$\lambda \tilde{m}=KG.\tilde{M}$$
Definimos la matriz de proyectacion prospectica como: $$P=K.G=K.[R|t]$$
Esta matriz combina los parámetros intrínsecos y extrínsecos de la cámara y tiene 11 parámetros independientes debido a la escala de proyección.

Entonces, la relación general que vincula las coordenadas de un punto en el sistema de referencia absoluto ($x, y, z$) con las coordenadas en píxeles de su imagen proyectada ($u, v$) se expresa como:

$$
\lambda \tilde{m} = P \tilde{M}
$$

→ $$\tilde{m}=P\tilde{M}$$
#### Observaciones
- La Matriz de proyección perspectiva P (MPP o "camera matrix") contiene toda la info para describir completamente la proyección.
	- Dimension de 3x4, con 11 parámetros independientes.
- Debido a la indeterminación intrínseca de la proyección, el resultado no cambia si todos los elementos de P se multiplican por un mismo factor de escala no nulo.
- P puede ser calculada con 10 parámetros: $k_uf,k_vf,u_0,v_0,\phi,\theta,\psi,t_x,t_y,t_z$ 
- Como 𝑃 es determinada a menos de un factor de escala, se puede escribir omitiendo $\lambda$
- En coordenadas homogéneas, el paralelismo de los vectores a la derecha e izquierda de la ecuación implica la igualdad.
### La distorsión de la lente
- **Modelo pin-hole**: Supone que el punto $M$ y su imagen $m$ están unidos por una línea recta que pasa por el centro de proyección de la lente.
  - **Realidad**: La lente (grupo de lentes) es un sistema no lineal; el modelo pin-hole es una aproximación.
  - **Distorsión**: Introduce diferencias dependiendo del tipo y calidad de la óptica.

#### Modelo de distorsion
![[Pasted image 20240530211729.png]]
- **Coordenadas distorsionadas**: $(u_d, v_d)$, las observadas en la imagen.
- **Coordenadas no distorsionadas**: $(u, v)$, las que seguirían el modelo pin-hole exacto.
- **Relación**: Conocer el vínculo entre coordenadas distorsionadas y no distorsionadas permite corregir la distorsión antes de aplicar el modelo pin-hole.
- **Proceso**: 
    - Aplicar modelo de distorsión inverso a las coordenadas distorsionadas para obtener coordenadas no distorsionadas.
    - Aplicar modelo pin-hole a las coordenadas no distorsionadas.
  
- **Requisitos del modelo de distorsión**:
	- Debe ser invertible.
	- Parámetros del modelo calculables analizando una o más imágenes (preferiblemente de un objeto con geometría conocida).


### Caso de coordenadas de imagen no ortogonales

Il modello più generale prevede anche la possibilità che gli assi $u$, $v$ non siano ortogonali ma inclinati di un angolo $\theta$. La matrice $K$ più generale è quindi la seguente:

$$
K = \begin{bmatrix} -fk_u & k_u \cot{\theta} & u_0 \\ 0 & -fk_v/sin\theta & v_0 \\ 0 & 0 & 1 \end{bmatrix}
$$

Tuttavia, nei moderni sistemi di acquisizione, le disomogeneità lungo $u$ e $v$ della matrice di CCD sono minime, per cui si può considerare $\theta \approx \pi/2$.




### Correspondencia 2D-2D

Medición de objetos planos en un plano fijo, por ejemplo, objetos en una cinta transportadora.
- **Sistema de referencia** está fijado en el plano; las coordenadas absolutas $z$ no son relevantes.
- **Descripción de la proyección**: Correspondencia biunívoca entre las coordenadas absolutas $(x, y)$ del plano y las coordenadas en píxeles $(u, v)$.

#### Relación de homografía
L'omografia $H$ è una matrice che descrive una trasformazione proiettiva tra due piani proiettivi bidimensionali nello spazio tridimensionale
- **Coordenadas homogéneas**: Relación expresada como:
  $$
  \begin{bmatrix}
  \lambda u \\
  \lambda v \\
  \lambda
  \end{bmatrix}
  = 
  \begin{bmatrix}
  h_{11} & h_{12} & h_{13} \\
  h_{21} & h_{22} & h_{23} \\
  h_{31} & h_{32} & h_{33}
  \end{bmatrix}
  \begin{bmatrix}
  x \\
  y \\
  1
  \end{bmatrix}
  = H
  \begin{bmatrix}
  x \\
  y \\
  1
  \end{bmatrix}
  $$

- **Factor $\lambda$** desaparece al determinar las coordenadas cartesianas $(u, v)$ a partir de las observadas $(\lambda u, \lambda v)$.

  - Con $H$ conocida, se pueden determinar $(x, y)$ a partir de $(u, v)$.

#### Notación
- Relación en coordenadas homogéneas:
  $$
  \lambda \tilde{m} = H \tilde{M}
  $$
  donde $\tilde{m}$ y $\tilde{M}$ son las representaciones homogéneas de $(u, v)$ y $(x, y)$ respectivamente.


## Ejemplo práctico
**Ejercicio:** Calcular las coordenadas en píxeles de un punto en el espacio ($x = 100 \, mm, y = 200 \, mm, z = 500 \, mm$) para una cámara con los siguientes parámetros:
- Distancia focal $f = 50 \, mm$
- Tamaño de píxel: $k_u = k_v = 10 \, pix/mm$
- Centro de la imagen: $u_0 = 320, v_0 = 240$
- Sin distorsión de la lente
- La cámara está ubicada en ($t = [0, 0, 100] \, mm$) y rotada 30 grados alrededor del eje $y$

**Solución:**
1. Convertir el punto a coordenadas de la cámara usando la rotación y traslación:
   $$
   R = \begin{pmatrix}
   \cos(30^\circ) & 0 & \sin(30^\circ) \\
   0 & 1 & 0 \\
   -\sin(30^\circ) & 0 & \cos(30^\circ)
   \end{pmatrix} = \begin{pmatrix}
   \sqrt{3}/2 & 0 & 1/2 \\
   0 & 1 & 0 \\
   -1/2 & 0 & \sqrt{3}/2
   \end{pmatrix}
   $$

   $$
   \begin{pmatrix}
   x_c \\
   y_c \\
   z_c
   \end{pmatrix} = R \begin{pmatrix}
   100 \\
   200 \\
   500
   \end{pmatrix} + \begin{pmatrix}
   0 \\
   0 \\
   100
   \end{pmatrix}
   $$

   $$
   = \begin{pmatrix}
   \sqrt{3}/2 \cdot 100 + 1/2 \cdot 500 \\
   200 \\
   -1/2 \cdot 100 + \sqrt{3}/2 \cdot 500 + 100
   \end{pmatrix} = \begin{pmatrix}
   293.2 \\
   200 \\
   423.2
   \end{pmatrix}
   $$

2. Proyectar las coordenadas de la cámara a la imagen usando la matriz $K$:
   $$
   \tilde{m} = \lambda K \tilde{M_c}
   $$
   $$
   K = \begin{pmatrix}
   500 & 0 & 320 \\
   0 & 500 & 240 \\
   0 & 0 & 1
   \end{pmatrix}
   $$
   $$
   \tilde{m} = \begin{pmatrix}
   500 & 0 & 320 \\
   0 & 500 & 240 \\
   0 & 0 & 1
   \end{pmatrix} \begin{pmatrix}
   293.2 \\
   200 \\
   423.2
   \end{pmatrix}
   $$
   $$
   = \begin{pmatrix}
   500 \cdot 293.2 + 320 \cdot 423.2 \\
   500 \cdot 200 + 240 \cdot 423.2 \\
   423.2
   \end{pmatrix} = \begin{pmatrix}
   146600 + 135424 \\
   100000 + 101568 \\
   423.2
   \end{pmatrix} = \begin{pmatrix}
   282024 \\
   201568 \\
   423.2
   \end{pmatrix}
   $$

3. Convertir a coordenadas cartesianas dividiendo por $z_c$:
   $$
   u = \frac{282024}{423.2} \approx 666
   $$
   $$
   v = \frac{201568}{423.2} \approx 476
   $$

Las coordenadas en píxeles del punto en la imagen son aproximadamente $(u, v) = (666, 476)$.

¿Hay algún otro aspecto que te gustaría que clarifique o alguna otra sección del libro que necesites resumir?


# Observaciones

## Representacion de objetos geometricos con coordinadas homogeneas
### Bidimensional
#### Representación de una recta en coordenadas homogéneas bidimensional
![[Pasted image 20240410103000.png]]
- En espacio homogéneo, una recta 2D se representa por vector $l = (a, b, c)$.
- Ecuación lineal: $ax + by + c = 0$.
- Un punto pertenece a la recta si y solo si el producto escalar entre los vectores es cero.
- Vector normal $n = (\cos \theta, \sin \theta)$ define la recta.
- $l$ compuesto por el versor y ángulo $\theta$; dirección y paralelas determinadas por $\theta$, tercer componente dado por $d$.
- Al pasar a coordenadas homogéneas, se añade una dimensión, ingresando a un espacio 3D.

##### Observaciones
- Intersección de dos rectas: producto vectorial de los vectores de las rectas.
- Recta que pasa por dos puntos: producto vectorial de los vectores de los puntos; obtenemos vector $l$ asociado a la recta.

### Tridimensional
- En un sistema cartesiano 3D (x, y, z), un punto se representa en coordenadas homogéneas como $(x, y, z, 1)$ y el factor de escala $w$. Este es el espacio proyectivo tridimensional.

#### Definición de un plano en el espacio tridimensional
- Un plano en espacio proyectivo 3D tiene la ecuación: producto escalar entre vector $m = (a, b, c, d)$ y vector aumentado $(x, y, z, 1)$.
- Plano puede ser identificado por versor ortogonal y dos ángulos ($\theta, \phi$).

#### Definición de una recta en el espacio tridimensional
- Para representar una recta en espacio 3D, se necesitan dos puntos.
- Forma paramétrica: $\mathbf{r} = (1 - \lambda) \mathbf{p} + \lambda \mathbf{q}$, donde $\mathbf{p}$ y $\mathbf{q}$ son los puntos que definen la recta.
- En espacio homogéneo: sustituir $\mathbf{p}$ y $\mathbf{q}$ por sus vectores aumentados.
- Considerando un punto en el infinito, se define el vector dirección aumentado $\tilde{d}$.

Representaciones en coordenadas homogéneas de $m$ y $M$:

$$ m=\begin{bmatrix} u \\ v \\ 1 \end{bmatrix}, \quad M=\begin{bmatrix} x \\ y \\ z \\ 1 \end{bmatrix} $$

- Con tercera coordenada 1, se excluyen puntos en el infinito (última coordenada homogénea = 0).
- Ecuaciones de proyección perspectiva simplificadas:

$$ \frac{f}{z} = \frac{-u}{x} = \frac{-v}{y} $$

En notación matricial:

$$ \begin{bmatrix} u \\ v \\ 1 \end{bmatrix} = \begin{bmatrix} -f & 0 & 0 & 0 \\ 0 & -f & 0 & 0 \\ 0 & 0 & 1 & 0 \end{bmatrix} \begin{bmatrix} x \\ y \\ z \end{bmatrix} \quad \text{o} \quad \mathbf{m} \approx \mathbf{P} \mathbf{M} $$

- $\approx$ significa "igual a menos un factor de escala".
- Matriz $\mathbf{P}$ representa el modelo geométrico de la cámara, llamada matriz de proyección perspectiva (MPP).

Modelo completo de la cámara considera:
1. "Pixelización" por el sensor CCD, visto como matriz 2D de pixeles, y su posición respecto al eje óptico.
2. Transformación isométrica entre sistema de referencia absoluto ("sistema mundo") y el de la cámara, representable mediante una rototraslación.