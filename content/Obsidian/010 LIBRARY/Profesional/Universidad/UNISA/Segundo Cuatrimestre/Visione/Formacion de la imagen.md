
## Lente delgada
Hacemos uso de lo aprendido en [[2. Lenti e Sistemi Ottici#Lente delgada]] 
### 2.1. Modelo de Lente Delgada
#### Hipótesis de la Lente Delgada
- **Grosor de la Lente**: Se considera que el grosor de la lente es mucho menor que las distancias $l_1$ (distancia objeto-lente) y $l_2$ (distancia lente-imagen).
- **Rayos Paraxiales**: Los resultados son válidos para rayos poco inclinados con respecto al eje óptico.
#### Foco y Longitud Focal
- **Foco (F)**: Es el punto donde convergen los rayos paralelos al eje óptico.
- **Longitud Focal ($l_f$)**: La distancia entre la lente y el foco.
#### Distancias Conjugadas
- **Relación de Distancias Conjugadas de Gauss**:
  $$
  \frac{1}{l_f} = \frac{1}{l_1} + \frac{1}{l_2}
  $$

### 2.2. Formación de la Imagen
- **Fuente Puntual (Objeto)**: Los rayos generados por una fuente puntual a una distancia $l_1$ convergen más allá de la lente en un punto (imagen) situado a una distancia $l_2$.
- **Imagen Enfocada**: Si los rayos se recogen en una pantalla a una distancia $l_2$, se forma una imagen puntual.
- **Imagen Desenfocada**: Si los rayos se recogen en una pantalla a una distancia diferente de $l_2$, la proyección aparecerá desenfocada.

### 2.3. Aumento de una Lente
- **Definición**: El aumento ($m$) de una lente se define como el cociente entre la longitud de la imagen ($h_2$) y la longitud del objeto ($h_1$):
  $$
  m = \frac{h_2}{h_1} = \frac{l_2}{l_1}
  $$

![[2. Lenti e Sistemi Ottici#Aumento trasversale M]]


### 2.4. Dimensiones y Selección de la Óptica
![[Pasted image 20240404104437.png]]
##### Área de Visión (FOV)
- **Definición**: Es la dimensión máxima enmarcada en el plano del objeto que cubre toda el área del sensor.
- **Ecuación**: 
  $$
  l_f = l_{\text{sensor}} \cdot \left( \frac{WD}{FOV} \right)
  $$
  donde $l_{\text{sensor}}$ es la longitud del sensor, $WD$ es la distancia de trabajo, y $FOV$ es el campo de visión.

##### Distancia de Trabajo (WD)
- **Definición**: Distancia entre la cámara y el objeto en la escena.

##### Tamaño del Sensor
- **Importancia**: Seleccionar una óptica compatible con el tamaño del sensor para una cobertura adecuada.

##### Tamaño de los Píxeles
- **Importancia**: La óptica debe ser compatible con el tamaño de los píxeles para obtener una resolución óptima.



### 2.5. Profundidad de Campo (DOF)
- **Definición**: Máximo desplazamiento a lo largo del eje óptico que el objeto puede experimentar manteniéndose enfocado.
- **Ecuación**:
  $$
  DOF = 2 \cdot F \cdot \Delta L
  $$
  donde $\Delta L$ es el desenfoque máximo aceptado.

![[Pasted image 20240404110218.png]]

### 2.6. Apertura
- **Relación de Apertura ($F$)**:
  $$
  F = \frac{l_f}{D}
  $$
  donde $l_f$ es la longitud focal y $D$ es el diámetro libre de la óptica.

El parámetro $F$ influye en:

- **Luminosidad de la imagen**: Aumenta si $F$ disminuye, lo que significa que una apertura más grande permite más luz, mejorando la luminosidad de la imagen.
  
- **Profundidad de campo**: Aumenta si $F$ aumenta. Una apertura más pequeña conlleva a una mayor profundidad de campo, lo que significa que más objetos estarán enfocados simultáneamente.

- **Resolución**: Mejora si $F$ disminuye. Una apertura más pequeña reduce los efectos de la difracción, lo que resulta en una mejor resolución de la imagen.
### 2.7. Resolución Óptica y Disco de Airy

#### Disco de Airy
La resolución de una óptica se refiere a su capacidad para distinguir dos características visibles cercanas entre sí en un objeto. El fenómeno de la difracción establece un límite último para esta capacidad: debido al diámetro finito de la apertura libre de la lente, la imagen de un objeto puntual se presenta como un disco de Airy. El diámetro del disco de Airy está dado por:
$$
D_{\text{Airy}} = 2.44 \cdot \lambda \cdot F
$$
donde:
- $\lambda$ es la longitud de onda de la luz incidente.
- $F$ es el número f de la lente.

#### Modelo de Fraunhofer
La intensidad en el modelo de difracción de Fraunhofer para una apertura circular está dada por:
$$
I(\theta) = I_0 \left( \frac{2J_1(k \cdot a \cdot \sin(\theta))}{k \cdot a \cdot \sin(\theta)} \right)^2
$$
donde:
- $J_1(x)$ es la función de Bessel de primer tipo.
- $a$ es el radio de la apertura.
- $k$ es el número de onda, $k = \frac{2 \pi}{\lambda}$.
- $I_0$ es la intensidad máxima de la luz.

Esta fórmula describe cómo se distribuye la intensidad de la luz difractada a lo largo del ángulo $\theta$ después de pasar a través de la apertura de la lente.

#### Criterio de Rayleigh
El criterio de Rayleigh establece que la resolución de un sistema óptico está limitada por el primer mínimo del patrón de difracción de Airy. Esto ocurre donde los máximos de un punto de luz se superponen con los mínimos adyacentes. En contraste, los ceros de la función de Bessel indican puntos donde la intensidad difractada se anula completamente.

- **Criterio de Rayleigh**: Límite práctico de resolución, donde se considera que dos puntos son resolvibles si el máximo de uno coincide con el primer mínimo del otro.
- **Ceros de Bessel**: Indican los puntos en el espacio donde la intensidad de la luz difractada se anula completamente.

#### Conclusiones
Los ceros de la función de Bessel de primer tipo, $J_1(X)$, en el contexto del modelo de Fraunhofer para una apertura circular, indican los puntos en el espacio donde la intensidad de la luz difractada se anula completamente. Estos puntos corresponden a los mínimos locales de intensidad luminosa en la imagen formada por la apertura circular.

En el caso del disco de Airy:
- **Disco de Airy**: Describe la distribución de intensidad de la luz difractada alrededor del punto central de una imagen formada por una apertura circular.
- **Mínimos locales**: Los ceros de la función de Bessel señalan las posiciones angulares donde las ondas difractadas se cancelan, resultando en una reducción o anulación de la intensidad luminosa.

El ancho del lente, representado por el parámetro $D$ en la fórmula del disco de Airy, afecta la resolución óptica de un sistema:
- **Lente más ancha (mayor $D$)**: Resulta en un disco de Airy más grande, lo que significa que la difracción será más pronunciada y la resolución será menor.
- **Lente más estrecha (menor $D$)**: Produce un disco de Airy más pequeño y, por lo tanto, una mejor resolución.

### 2.8. Consideraciones Finales
- **Corrección de Distorsiones**: Minimizar distorsiones para garantizar mediciones precisas.
- **Diseño Óptico**: El diseño debe considerar todos los factores mencionados para asegurar la calidad de la imagen y la precisión de las mediciones.






## Puntos adicionales
### Optica real
Las lentes reales son sistemas ópticos compuestos por múltiples lentes. Los diseñadores utilizan combinaciones de lentes con curvaturas, índices de refracción y tratamientos superficiales (recubrimientos) diseñados para:

- Obtener el rendimiento deseado en condiciones específicas.
- Controlar las aberraciones, es decir, desviaciones del comportamiento ideal, dentro de límites aceptables, al menos en las condiciones de uso especificadas para ese tipo particular de óptica.
![[Pasted image 20240404110231.png]]


### Optica especial
![[Pasted image 20240404110349.png]]
Ópticas especiales:
- Ópticas zoom: tienen una longitud focal variable. Son útiles en la fase de prototipado, pero suelen ser más grandes, menos robustas, más costosas y a veces presentan más problemas de distorsión.
- Ópticas macro: diseñadas para proporcionar un aumento cercano a 1. Ofrecen mejores resultados que las ópticas tradicionales con distanciadores.
- Ópticas telecéntricas: aseguran un aumento constante al variar la distancia del objeto. Son diseñadas para aplicaciones de medición, aunque suelen ser más costosas y voluminosas.


*Distorsione:*
La distorsión es una aberración geométrica introducida por las lentes de la óptica. Provoca un error en la localización de las características visibles del objeto a analizar. En general, es más evidente en ópticas de longitud focal reducida


### Attacco para optica
Los diferentes tipos de attacco para ópticas, como C-Mount, F-Mount, CS-Mount y otros, tienen distintas aplicaciones en sistemas de visión industrial:

- **Attacco C-Mount**: Ampliamente utilizado en visión industrial por su versatilidad y compatibilidad con una amplia gama de sistemas de cámaras.

- **Attacco F-Mount**: Empleado en cámaras lineales y de alta resolución, es ideal para aplicaciones que requieren una alta calidad de imagen y precisión.

- **Attacco CS-Mount**: Similar al C-Mount pero con una longitud focal de brida más corta, es preferido en espacios reducidos donde se necesita una cámara compacta sin comprometer la calidad óptica.

- **Attacchi de 42,58 y 72**: Utilizados en cámaras de alta resolución para garantizar una transmisión de imagen óptima y una calidad superior.


### Dimensiones del sensor
Las dimensiones de los sensores de las cámaras se expresan comúnmente en unidades imperiales, pero no siempre corresponden exactamente a las dimensiones físicas reales del sensor. Estos valores son heredados de la era pre-digital, cuando muchas cámaras utilizaban tubos de vacío en lugar de sensores digitales. Es importante tener en cuenta que estos formatos pueden variar entre fabricantes y modelos de cámaras, y no necesariamente reflejan las dimensiones físicas precisas del sensor digital en uso actualmente.
![[Pasted image 20240404104916.png]]



## Ejemplo practico
### Ejemplo Práctico: Diseño de un Sistema de Visión para Inspección de Calidad

#### Contexto
En una línea de producción industrial, se requiere un sistema de visión para inspeccionar la calidad de piezas pequeñas que tienen dimensiones de aproximadamente 50 mm. La cámara debe estar situada a 200 mm de distancia de las piezas (distancia de trabajo), y se utiliza una cámara con un sensor de 6 mm de ancho.

#### Objetivos
1. Seleccionar la óptica adecuada para obtener una imagen clara y enfocada de las piezas.
2. Calcular la profundidad de campo necesaria para asegurar que todas las piezas estén enfocadas dentro de una tolerancia de desenfoque aceptable de 0.5 mm.
3. Asegurar que la resolución del sistema sea suficiente para detectar defectos de hasta 0.1 mm en las piezas.

#### Pasos y Cálculos

##### 1. Selección de la Óptica

**Área de Visión (FOV):**
- FOV requerido: 50 mm
- Ancho del sensor: 6 mm

La longitud focal necesaria ($l_f$) se puede calcular utilizando la ecuación:
$$
l_f = l_{\text{sensor}} \cdot \left( \frac{WD}{FOV} \right)
$$
donde:
- $l_{\text{sensor}} = 6$ mm
- $WD = 200$ mm
- $FOV = 50$ mm

Sustituyendo los valores:
$$
l_f = 6 \cdot \left( \frac{200}{50} \right) = 6 \cdot 4 = 24 \text{ mm}
$$

Por lo tanto, se necesita una lente con una longitud focal de aproximadamente 24 mm.

##### 2. Profundidad de Campo (DOF)

La profundidad de campo ($DOF$) se calcula usando:
$$
DOF = 2 \cdot F \cdot \Delta L
$$
donde:
- $F$ es el número f de la lente
- $\Delta L = 0.5$ mm (máximo desenfoque aceptado)

Primero, calculamos el número f ($F$):
$$
F = \frac{l_f}{D}
$$
Asumimos un diámetro de apertura $D = 12$ mm:
$$
F = \frac{24}{12} = 2
$$

Ahora calculamos el DOF:
$$
DOF = 2 \cdot 2 \cdot 0.5 = 2 \text{ mm}
$$

Esto significa que la profundidad de campo del sistema es de 2 mm, lo cual es suficiente para mantener las piezas enfocadas dentro de la tolerancia de desenfoque aceptada.

##### 3. Resolución Óptica

La resolución de la lente está limitada por el disco de Airy:
$$
D_{\text{Airy}} = 2.44 \cdot \lambda \cdot F
$$
donde:
- $\lambda = 0.5$ μm (luz visible)
- $F = 2$

Sustituyendo los valores:
$$
D_{\text{Airy}} = 2.44 \cdot 0.5 \cdot 2 = 2.44 \text{ μm}
$$

La resolución mínima detectable está dentro del rango aceptable, considerando que queremos detectar defectos de hasta 0.1 mm (100 μm).

#### Conclusión

- **Óptica Seleccionada**: Lente con longitud focal de 24 mm.
- **Profundidad de Campo**: 2 mm, suficiente para la aplicación.
- **Resolución Óptica**: Capacidad para detectar defectos de hasta 0.1 mm, con el disco de Airy calculado.

Este ejemplo demuestra cómo aplicar los conceptos de formación de la imagen, selección de óptica, y cálculos de profundidad de campo y resolución óptica en un sistema de visión industrial para inspección de calidad.