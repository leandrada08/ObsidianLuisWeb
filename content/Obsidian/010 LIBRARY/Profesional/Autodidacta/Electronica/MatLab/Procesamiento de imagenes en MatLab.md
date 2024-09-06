
## Procesamiento de imagenes
#### Funciones utilies
- Funcion para leer una imagen
	- VeriableGuarda es la matriz que guardara la informacion
	- Esta funcion guarda 3 matrices, por llo que seria una matrix tridimensional
		- Donde cada matrix guarda la informacion de intesidad de cada color primario
		- Cada elemento puede obtener un valor de intesidad de entre 0 y 256, por lo tanto estos son los niveles de colores que puedo ver
``` Python
VaribleGuarda=imread('NombreImagen')
```
- Para visualizar una imagen
```Python
figure,imshow(VectorImagen);
```

- Ejemplo de una imagen donde obtengo su matrix total y la de cada color
![[Pasted image 20240308141318.png|300]]

### Secuencia de imagenes
- Para cargar una secuencia de imagenes
``` Python
load nombre_secuencia;
```

- Para reproducir como una secuencia de imagenes un arreglo multidimensional
``` Python
implay(nombre_secuencia);
```

- Para reproducir un video del tipo .avi
``` Python
implay("nombre_del_archivo.avi");
```

- Para guardar en una variable los datos de un video tipo .avi
``` Python
variable_video=VideoReader("nombre_del_archivo.avi")
```

![[Pasted image 20240315141015.png]]

- Para ver estas propiedades en el comando
``` Python
get(variable_video);
```
![[Pasted image 20240315141252.png]]

## Observaciones

### Procesamiento de objetos en imagenes
- Si queres analizar o diferenciar en nuestro video solo los autos claros de oscuros no nos hace falta los colores, podemos manejar el video en negro y blanco, se muestra un ejermplo de codigo para hacer esto:
``` Python
darkCarValor=50;
darkCar=im2gray(read(trafficVid,71));
noDarkCar=imextendedmax(darkCar,darkCarValue);
imshow(darkCar)
figure,imshow(noDarkCar);
```
- Explicacion del codigo
	- En la primera linea guardamos el valor limite para diferenciar un auto como oscuro
	- En la segunda linea elegimos cual imagen del video analizaremos, en este caso analizaremos en ““momento”” 71 del video, por eso leemos esta posicion y luego la convertimos a escala de gris
	- Esta tercera linea tambien es una transformacion de intensidad a binario, lo que hace nos genera una imagen binaria haciendo una comparacion de cada pixel de intensidad de nuestro imagen con el valor limite ya definido
		- **Preguntar porque no toma el asfalto como claro**
	- Podemos ver que quedan varios pixeles aislados por caracteristicas de luz u otras cosas que hacen algunos pixeles muy claros
	- Para corregir esto podemos aplicar el siguiente codigo

``` Python
sedisk= strel('disk',2);
noSmallStructures = imopen(noDrakCar, sedisk);
imshow(noSmallStructures);
```



``` Python
figure,imshow(noSmallStructures,noDarkCar,'')
regionprops
```
- Con regionprops encontramos el centro del objeto

### Procesamiento de objetos en videos
``` Python
nframes=trafficVid.NumberOfFrames;
I=read(tra

for k=1 : nframes
	singleFram= read(trafficVid,k);
I=rgb2gray(singleFrame);
	noDrak
```
# Chat GPT

### Introduccion
**Píxeles**: Son los elementos más pequeños de una imagen digital. Cada píxel tiene un valor que representa su color o intensidad en una determinada ubicación en la imagen.
**Matrices de píxeles**: Las imágenes digitales se pueden representar como matrices, donde cada elemento de la matriz corresponde al valor de un píxel. Por ejemplo, una imagen en escala de grises se representa mediante una matriz de una sola dimensión, mientras que una imagen a color se representa mediante matrices tridimensionales (altura, anchura y canales de color).
**Pixel Indices**: Cada pixel, describe su ubicacion en base al indice que ocupa dentro de la matriz, el cual crece de valor de fila cuando baja y de valor de columna cuando se mueve a la derecha
**Canales de color**: En una imagen a color, como una imagen RGB (Rojo, Verde, Azul), cada píxel tiene valores para cada uno de estos canales de color, que determinan el color y la apariencia de la imagen.



### Tipos de imágenes
- **Binaria (Binary)**: Este tipo de imagen tiene solo dos posibles valores de píxel, generalmente 0 y 1, donde 0 representa el color negro y 1 el color blanco.
- **Indexada (Indexed)**: En este tipo de imagen, los píxeles se indexan a una tabla de colores (paleta), donde cada valor de píxel corresponde a un índice en la tabla de colores.
- **Escala de grises (Grayscale)**: Las imágenes en escala de grises tienen un solo canal de color donde cada píxel tiene un valor que representa su intensidad luminosa, generalmente en el rango de 0 a 255, donde 0 es negro y 255 es blanco.
- **Truecolor (Color verdadero)**: Este tipo de imagen tiene tres canales de color (rojo, verde y azul) y cada píxel tiene valores para cada canal, lo que permite representar una amplia gama de colores.
- **High Dynamic Range (HDR) image**: Las imágenes de alto rango dinámico son aquellas que capturan y representan un rango más amplio de niveles de intensidad luminosa que las imágenes estándar. Esto significa que pueden mostrar detalles tanto en áreas muy oscuras como en áreas muy brillantes de una escena, lo que las hace útiles en aplicaciones donde se necesitan detalles precisos en condiciones de iluminación variadas.
- **Imágenes multispectrales y hiperespectrales**:
	- **Multispectral**: Estas imágenes contienen información en múltiples bandas espectrales, lo que permite capturar características específicas de una escena que no son visibles para el ojo humano. Son útiles en diversas aplicaciones, como la agricultura, la teledetección y la vigilancia medioambiental. 
	- **Hiperespectrales**: Son similares a las imágenes multispectrales, pero con una mayor cantidad de bandas espectrales, lo que proporciona una información más detallada sobre las propiedades de los objetos en la escena. Se utilizan en aplicaciones más especializadas, como la cartografía geológica, la clasificación de materiales y la monitorización de la salud de los cultivos.
- **Label images**:Las imágenes de etiquetas (label images) son aquellas en las que cada píxel está asociado con una etiqueta o categoría específica en lugar de un valor de intensidad de color. Se utilizan comúnmente en tareas de segmentación y análisis de objetos en imágenes, donde cada región de interés se asigna a una etiqueta única.

#### Tipo de datos de la matriz de imagen:
   - Para imágenes indexadas y en escala de grises: las matrices suelen ser matrices numéricas con valores enteros (uint8 para escalas de grises, uint16 para indexadas).
   - Para imágenes en color verdadero: las matrices son matrices tridimensionales con valores numéricos que representan la intensidad de cada canal de color (generalmente uint8).

### Funciones para lectura y muestra de imágenes:
   - **imread**: Esta función se utiliza para leer imágenes desde archivos en varios formatos compatibles por MATLAB, como JPEG, PNG, BMP, etc.
   - **imshow**: Se utiliza para mostrar imágenes en una ventana de visualización. Puedes usarlo para mostrar imágenes en diferentes tipos de figuras, incluidas figuras de gráficos.
   - **imwrite**: Esta función te permite escribir una imagen en un archivo en un formato específico, como JPEG, PNG, BMP, etc.






### Imágenes binarias
   - En una imagen binaria, cada píxel se representa mediante un solo bit, donde 0 generalmente indica el color negro (fondo) y 1 indica el color blanco (objeto).
   - Las operaciones básicas en imágenes binarias incluyen la binarización (umbralización), dilatación, erosión, y operaciones de segmentación.

**Aplicaciones prácticas**:
   - La binarización se utiliza en aplicaciones de visión por computadora para separar objetos de interés del fondo, como detección de bordes, segmentación de imágenes y reconocimiento de formas.
   - Las operaciones morfológicas, como la dilatación y erosión, se utilizan para mejorar la calidad de las imágenes binarias, eliminar pequeños artefactos y ruido, y ajustar la forma y tamaño de los objetos detectados.

**Beneficios y limitaciones**:
   - Beneficios:
     - Eficiencia computacional: Las imágenes binarias son fáciles de procesar y requieren menos recursos computacionales en comparación con imágenes de escala de grises o a color.
     - Claridad en la interpretación: Las imágenes binarias son intuitivas y fáciles de interpretar visualmente, lo que las hace útiles en aplicaciones donde se necesita una segmentación clara de objetos.
   - Limitaciones:
     - Pérdida de información: La binarización puede resultar en la pérdida de detalles finos y sutilezas presentes en la imagen original, especialmente en áreas de transición entre objetos y fondo.
     - Sensibilidad al umbral: La calidad de la binarización depende en gran medida de los parámetros de umbralización utilizados, lo que puede afectar la precisión y exactitud de los resultados.

### Imágenes indexadas
   - En las imágenes indexadas, cada píxel se representa mediante un índice que corresponde a un color específico en un mapa de colores (paleta).
   - El mapa de colores puede contener una selección limitada de colores, lo que permite una representación eficiente de imágenes con un rango reducido de colores.
   - La profundidad de bits utilizada para representar los índices depende del tamaño de la tabla de colores y puede variar, pero es comúnmente de 8 bits (256 colores) en aplicaciones estándar.

- Un mapa de colores es una matriz de m por 3 de clase doble que contiene valores en el rango \[0, 1\]. Cada fila del mapa de colores especifica los componentes rojo, verde y azul de un solo color. Los valores de píxeles en la matriz de la imagen son índices directos en el mapa de colores. Por lo tanto, el color de cada píxel en la imagen indexada se determina asignando el valor del píxel en la matriz de la imagen al color correspondiente en el mapa de colores. El mapeo depende de la clase de la matriz de imagen:
	- Si la matriz de imagen es de clase simple o doble, el mapa de color normalmente contiene valores enteros en el rango \[1, p\], donde p es la longitud del mapa de color. El valor 1 apunta a la primera fila del mapa de colores, el valor 2 apunta a la segunda fila, y así sucesivamente.
	- Si la matriz de imagen es de clase lógica, uint8 o uint16, el mapa de colores normalmente contiene valores enteros en el rango \[0, p-1\]. El valor 0 apunta a la primera fila del mapa de colores, el valor 1 apunta a la segunda fila, y así sucesivamente.
- Un mapa de color a menudo se almacena con una imagen indexada y se carga automáticamente con la imagen cuando utiliza la función imread. Después de leer la imagen y el mapa de colores en el espacio de trabajo como variables separadas, debe realizar un seguimiento de la asociación entre la imagen y el mapa de colores. Sin embargo, no está limitado a utilizar el mapa de colores predeterminado, puede utilizar cualquier mapa de colores que elija.

La figura ilustra una imagen indexada, la matriz de imagen y el mapa de colores, respectivamente. La matriz de imágenes es de clase doble, por lo que el valor 7 apunta a la séptima fila del mapa de colores.

![[Pasted image 20240312100251.png]]

**Aplicaciones prácticas**:
   - Las imágenes indexadas se utilizan en aplicaciones donde se requiere una representación eficiente de imágenes con un número limitado de colores, como imágenes de diagramas, logotipos y gráficos.
   - También se utilizan en aplicaciones donde la velocidad de procesamiento y la eficiencia de almacenamiento son críticas, como en sistemas incrustados y aplicaciones de baja potencia.

**Beneficios y limitaciones**:
   - Beneficios:
     - Eficiencia de almacenamiento: Las imágenes indexadas ocupan menos espacio de almacenamiento que las imágenes en escala de grises o a color, ya que solo almacenan los índices de color en lugar de los valores de color completos.
     - Eficiencia de procesamiento: Las operaciones en imágenes indexadas son más rápidas que en imágenes a color verdadero, ya que solo se realizan cálculos en los índices de color en lugar de en los valores de color completos.
   - Limitaciones:
     - Limitación de colores: La representación limitada de colores en la tabla de colores puede afectar la calidad y precisión de la imagen, especialmente en imágenes con gradientes suaves o transiciones de color.
     - Artefactos de cuantización: La discretización de colores puede provocar artefactos visuales, como bandas de color y pérdida de gradaciones suaves, especialmente en imágenes con gradientes complejos.




### Imágenes en escala de grises (Grayscale)

   - En las imágenes en escala de grises, cada píxel se representa mediante un solo valor numérico que indica su intensidad luminosa.
   - Los valores típicos van desde 0 (negro) hasta 255 (blanco), donde 0 representa la intensidad mínima y 255 la intensidad máxima.
   - Estas imágenes tienen un solo canal de color y se representan mediante matrices bidimensionales, donde cada valor de la matriz corresponde a la intensidad de un píxel en esa ubicación.

**Aplicaciones prácticas**:
   - Las imágenes en escala de grises se utilizan en una amplia variedad de aplicaciones, como procesamiento de imágenes médicas, análisis de texturas, detección de bordes y reconocimiento de patrones.
   - Son especialmente útiles en aplicaciones donde el color no es esencial para la interpretación de la imagen, pero se necesita una representación precisa de la intensidad luminosa, como en imágenes médicas o científicas.

**Beneficios y limitaciones**:
   - Beneficios:
     - Simplificación de datos: Las imágenes en escala de grises contienen menos información que las imágenes a color verdadero, lo que puede facilitar el procesamiento y análisis de imágenes.
     - Mayor contraste: La representación de la intensidad luminosa puede resaltar características importantes en la imagen, como bordes y texturas.
   - Limitaciones:
     - Pérdida de información cromática: Al eliminar la información de color, se pierden detalles relacionados con la percepción cromática de la escena, lo que puede ser crucial en ciertos contextos.

### Imágenes en color verdadero (Truecolor)
   - En las imágenes en color verdadero, cada píxel se representa mediante tres valores numéricos que indican la intensidad de los tres canales de color: rojo, verde y azul (RGB).
   - Los valores típicos para cada canal van desde 0 hasta 255, donde 0 representa la ausencia de color y 255 la intensidad máxima de ese color.
   - Estas imágenes se representan mediante matrices tridimensionales, donde cada dimensión corresponde a un canal de color.

**Aplicaciones prácticas**:
   - Las imágenes en color verdadero se utilizan en una amplia variedad de aplicaciones, como fotografía digital, diseño gráfico, visión por computadora y aplicaciones multimedia.
   - Proporcionan una representación más fiel de la escena real, ya que capturan información sobre los colores y tonalidades presentes en la misma.

**Beneficios y limitaciones**:
   - Beneficios:
     - Fidelidad cromática: Las imágenes en color verdadero capturan la información cromática completa de la escena, lo que permite una representación más precisa y realista de la misma.
     - Flexibilidad en el procesamiento: Los tres canales de color proporcionan una mayor flexibilidad en el ajuste y procesamiento de la imagen, permitiendo realizar correcciones de color y manipulaciones más sofisticadas.
   - Limitaciones:
     - Mayor complejidad de datos: Las imágenes en color verdadero contienen más información que las imágenes en escala de grises, lo que puede aumentar la complejidad del procesamiento y análisis de imágenes.




### Imágenes de etiquetas (Label images)
   - En una imagen de etiquetas, cada píxel se asigna a una etiqueta o categoría específica en lugar de un valor de intensidad de color.
   - Las etiquetas suelen ser valores enteros que representan diferentes objetos, regiones o clases en la imagen.
   - Estas imágenes se utilizan comúnmente en tareas de segmentación y análisis de objetos en imágenes, donde cada región de interés se asigna a una etiqueta única.

**Aplicaciones prácticas**
   - Las imágenes de etiquetas se utilizan en una variedad de aplicaciones, como segmentación semántica, detección de objetos, análisis de imágenes médicas y reconocimiento de patrones.
   - Son especialmente útiles en aplicaciones donde es necesario identificar y distinguir diferentes objetos o regiones en una imagen, como en la detección de células en imágenes médicas o la segmentación de objetos en imágenes satelitales.

**Beneficios y limitaciones**
   - Beneficios:
     - Segmentación precisa: Las imágenes de etiquetas permiten una segmentación precisa de diferentes objetos o regiones en una imagen, lo que facilita el análisis y procesamiento de datos.
     - Flexibilidad en el análisis: Al asignar etiquetas a regiones específicas de la imagen, se pueden realizar análisis detallados y específicos de cada objeto o región por separado.
   - Limitaciones:
     - Requiere preprocesamiento: Antes de generar una imagen de etiquetas, a menudo se requiere un preprocesamiento de la imagen original para identificar y segmentar las regiones de interés.
     - Sensible a la calidad de la segmentación: La calidad de la segmentación inicial puede afectar la precisión y calidad de la imagen de etiquetas resultante, especialmente en imágenes con objetos superpuestos o formas complejas.

**Métodos de generación**
   - Las imágenes de etiquetas se generan comúnmente mediante algoritmos de segmentación, como segmentación por umbralización, segmentación por crecimiento de regiones, segmentación por contornos activos (snakes) o mediante el uso de redes neuronales convolucionales (CNN) en el caso de segmentación semántica.



## **Matriz para secuencia de imágenes**:
   - Para representar una secuencia de imágenes, necesitas una matriz multidimensional que agregue una dimensión adicional para cada imagen en la secuencia.
   - Si todas las imágenes en la secuencia tienen las mismas dimensiones y características (por ejemplo, tamaño, tipo de color), puedes crear una matriz donde las primeras dos dimensiones representen las dimensiones espaciales de cada imagen, y la tercera dimensión represente el índice de la imagen en la secuencia.
   - Por ejemplo, para una secuencia de imágenes en escala de grises, tendrías una matriz tridimensional con dimensiones `(alto, ancho, numImagenes)`, donde `alto` y `ancho` son las dimensiones espaciales de las imágenes y `numImagenes` es el número total de imágenes en la secuencia.
   - Si las imágenes en la secuencia tienen características diferentes (por ejemplo, diferentes tamaños o tipos de color), puede ser necesario realizar un preprocesamiento para ajustarlas o convertirlas antes de almacenarlas en la matriz de secuencia.


