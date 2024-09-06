## Introduccion
El proceso de formacion de la imagen puede ser intendido como el proceso opuesto a la vision
![[Pasted image 20240321190342.png]]

### Descripción Matemática de Imágenes
  - Las imágenes pueden describirse matemáticamente como funciones bidimensionales \(f(x, y)\), donde \(x\) y \(y\) representan las coordenadas espaciales y \(f(x, y)\) representa la intensidad luminosa en cada punto del plano. En imágenes digitales, estas funciones se representan discretamente mediante matrices de píxeles.

### Representación de Imágenes Digitales
  - Las imágenes digitales se representan mediante una matriz de píxeles, donde cada píxel contiene información sobre el color y la intensidad de la luz en una ubicación específica de la imagen. Cada píxel se representa mediante valores numéricos que indican la intensidad de los componentes de color (rojo, verde, azul) en el caso de imágenes a color.

### Proceso de Formación de Imágenes
  - El proceso de formación de imágenes comienza con la captura de la luz incidente por un sistema óptico, que proyecta una imagen en un sensor de imagen, como un CCD o un CMOS. El sensor convierte la luz en señales eléctricas que se digitalizan y procesan para formar una imagen digital. La óptica se encarga de enfocar la luz en el sensor, mientras que el sensor convierte la luz en una señal eléctrica que representa la intensidad de la luz en cada punto de la imagen.

### La Telecámara
  - Una telecámara es un dispositivo electrónico que utiliza un sensor de imagen para capturar y transmitir imágenes a distancia. Consiste en una combinación de una cámara de video y un sistema de transmisión, que puede ser cableado o inalámbrico. Las telecámaras se utilizan en aplicaciones de vigilancia, televisión, videollamadas, entre otras.

### Sensor
  - Un sensor es un dispositivo que detecta o mide cambios en su entorno y convierte estos cambios en señales eléctricas o digitales. En el contexto de la imagen, un sensor de imagen es un tipo de sensor que captura la luz incidente y la convierte en señales eléctricas que se pueden procesar para formar una imagen digital.
Los sensores para adquisicion de imagenes utilizados hoy en dia son:
- CCD(charge coupled device)
- CMOS(complementary metal ocide semiconductor)
#### Clasificacion de sensores
Los sensores pueden ser clasificados:
- En base a la caracteristicas de las imagenes formadas
	- Monocromatico
	- A color

- Basado en su disposicion de pixeles
	- Lineal: Capturan una sola linea de pixeles
	- Matricial: captural imagenes en una matriz bidimensional de pixeles


## CCD: Charge-coupled device
El CCD (Dispositivo de Acoplamiento de Carga) es un sensor de imagen que convierte la luz en señales eléctricas. Está constituido por una matriz de celdas fotosensibles y se utiliza en aplicaciones como fotografía digital, astronomía y microscopía.
**Completar diapos**


### Caracteristicas

1. **Calidad de imagen:** Produce imágenes de alta calidad con bajo ruido y alta resolución.
2. **Sensibilidad:** Tiene una alta sensibilidad a la luz, lo que permite capturar imágenes en condiciones de baja iluminación.
3. **Linealidad:** Proporciona una respuesta lineal a la intensidad de la luz incidente.
4. **Uniformidad:** Ofrece una uniformidad en la respuesta de los píxeles a través de la matriz.
5. **Estabilidad:** Mantiene su rendimiento a lo largo del tiempo y bajo diversas condiciones ambientales.
6. **Velocidad de lectura:** Tiene una velocidad de lectura más lenta en comparación con los sensores CMOS.
7. **Consumo de energía:** Tiende a consumir más energía que los sensores CMOS.
8. **Profundidad de bits:** Permite una alta profundidad de bits para capturar detalles finos en la imagen.
9. **Rango dinámico:** Ofrece un amplio rango dinámico para capturar tanto áreas brillantes como oscuras en una escena.
10. **Compatibilidad:** Es compatible con una variedad de aplicaciones que requieren imágenes de alta calidad y precisión.


### Generalitá
El CCD consiste en una matriz de píxeles fotosensibles dispuestos en filas y columnas, que convierten la luz en carga eléctrica.
El sensor CCD esta compuesto principalmente por:
- Una matriz de pixeles
	- Captura la luz incidente y convertirla en carga eléctrica, lo que permite la formación de la imagen
- Un filtro de luz
	- Se utiliza para capturar información en color al dividir la luz en componentes rojo, verde y azul, lo que permite la formación de imágenes a todo color.


### Estructura del CCD
   - Las celdas de un CCD generalmente consisten en un fotodiodo(llamado pixel) y una serie de electrodos.
   - Cada píxel puede almacenar y transferir cargas eléctricas generadas por la luz incidente.
   - Estas cargas se mueven a través del chip del CCD mediante el acoplamiento de carga (charge-coupled) hacia los canales de lectura para su posterior conversión en una señal digital.

### Proceso de captura de imagen y principio de funcionamiento
- El proceso de captura de imagen en un CCD comienza con la exposición del sensor a la luz. 
- Los fotones incidentes en los fotodiodos generan electrones, que se acumulan en una región de potencial bajo el fotodiodo. 
- La carga acumulada es forzada a moverse un paso a la vez mediante aplicaciones de impulsos a los electrones
- La carga electrica acumulada en todas las celdas viene transferido simultaneamente al CDD shift register vertical.
	- El movimiento de las cargas a través del shift register vertical implica la transferencia secuencial de cargas desde cada fila de píxeles hacia el registro de desplazamiento.
- Las cargas de los registros verticalse son transferidos paso a paso al CCD Shift register horizontal hasta llegar a la etapa de conversión y amplificación
- En esta etapa, la señal eléctrica generada por las cargas se amplifica y se convierte en una señal digital que representa la intensidad de la luz incidente en cada píxel.

**Insertar foto**



- El proceso de transferencia secuencial de carga a través de los shift registers vertical y horizontal, junto con la lectura y conversión de señales, requiere tiempo adicional, lo que resulta en una velocidad de captura más lenta en comparación con los sensores CMOS.
- Esto tambien permite una alta calidad ya que solo tiene un amplificador y conversor por lo que este puede ser de mejor calidad y con solo mejorar este se puede mejorar la calidad de toda la imagen


### Diferentes configuraciones del CCD

1. **Interline Transfer CCD (CCD de Transferencia Interlineal)**:
   - Utiliza una estructura donde cada píxel tiene un fotodiodo y un área de almacenamiento adicional.
   - Permite la transferencia rápida de cargas mediante shift registers entre los píxeles fotosensibles y las áreas de almacenamiento, lo que facilita la lectura continua de la imagen sin interrupciones.

2. **Frame Transfer CCD (CCD de Transferencia de Cuadro)**:
   - Divide la matriz de píxeles en dos secciones: una para la captura de la imagen y otra para la lectura.
   - La carga acumulada en la sección de captura se transfiere rápidamente a la sección de lectura para su posterior procesamiento, lo que permite una mayor velocidad de captura en comparación con los CCD de transferencia interlineal.

3. **Full Frame Readout CCD (CCD de Lectura de Cuadro Completo)**:
   - Captura y lee toda la imagen en un solo paso.
   - Adecuado para aplicaciones donde se requiere una alta calidad de imagen y una velocidad de captura moderada.
   - No tiene áreas de almacenamiento adicionales como en el CCD de transferencia interlineal, lo que puede limitar la velocidad de lectura en comparación con el CCD de transferencia de cuadro.




### Parametros
1. **Eficiencia Cuántica (QE)**:
   - La eficiencia cuántica representa la proporción de fotones incidentes que generan electrones en el fotodiodo.
   - Se calcula como el cociente entre el número de electrones generados y el número de fotones incidentes.
   - Ec: $QE = \frac{n_e}{N_f}$, donde $n_e$ es el número de electrones generados y $N_f$ es el número de fotones incidentes.

2. **Sensibilidad Espectral**:
   - La sensibilidad espectral representa la capacidad del CCD para detectar la luz en diferentes longitudes de onda.
   - Se calcula como la respuesta del CCD a diferentes longitudes de onda de luz.
   - No hay una ecuación específica, pero se puede determinar experimentalmente mediante la medición de la respuesta del CCD a diferentes longitudes de onda.

3. **Capacidad Electrónica por Píxel**:
   - La capacidad electrónica por píxel representa la cantidad máxima de carga eléctrica que puede almacenarse en un píxel del CCD.
   - Se calcula como el producto de la capacidad de carga del fotodiodo y el área del píxel.
   - Ec: $C_{\text{pixel}} = C_{\text{diode}} \times A_{\text{pixel}}$, donde $C_{\text{diode}}$ es la capacidad de carga del fotodiodo y $A_{\text{pixel}}$ es el área del píxel.

4. **Corriente de Oscuro (Dark Current)**:
   - La corriente de oscuro representa la corriente eléctrica generada en ausencia de luz, debido a la generación térmica de portadores de carga.
   - Se calcula como la corriente promedio medida en ausencia de luz.
   - Ec: $I_d = I_{d0} \cdot (T/T_0)^{\frac{3}{2}} \cdot e^{\frac{-E_g}{k \cdot T}}$, donde $I_{d0}$ es la corriente de oscuro a una temperatura de referencia $T_0$, $T$ es la temperatura actual, $E_g$ es la energía de la banda prohibida del material del CCD, $k$ es la constante de Boltzmann y $e$ es la carga del electrón.


### Blackside illumintated CCD
Un CCD iluminado por el lado oscuro (BSI, por sus siglas en inglés) es un tipo de sensor de imagen CCD diseñado para mejorar la eficiencia cuántica y la sensibilidad de la luz al invertir la arquitectura convencional del CCD. En lugar de tener los circuitos de lectura y amplificación en la parte frontal del sensor, como en un CCD convencional, en un BSI, estos circuitos se colocan en la parte posterior del sustrato de silicio, lo que permite que la luz incida directamente en los fotodiodos sin obstáculos.

Esto tiene varias ventajas:
1. **Mayor Eficiencia Cuántica**: Al eliminar los circuitos de lectura y amplificación de la trayectoria de la luz, más fotones pueden alcanzar los fotodiodos, lo que resulta en una mayor eficiencia cuántica y sensibilidad a la luz.
2. **Menor Cantidad de Ruido**: Al colocar los circuitos de lectura y amplificación más cerca de los fotodiodos, se reduce la cantidad de ruido introducido en la señal de imagen, lo que mejora la relación señal-ruido y la calidad de la imagen.
3. **Mayor Resolución y Sensibilidad**: Debido a la mejora en la eficiencia cuántica y la reducción del ruido, los sensores BSI pueden capturar imágenes con una mayor resolución y sensibilidad en comparación con los sensores CCD convencionales.



## CMOS
- Los sensores CCD utilizan una estructura de matriz de píxeles y shift registers para transferir la carga eléctrica generada por la luz incidente a través del sensor.
- Los sensores CMOS, en cambio, incorporan circuitos de lectura y amplificación individuales en cada píxel, lo que elimina la necesidad de shift registers y permite la lectura de píxeles de forma independiente.

### Elementos
El sensor CMOS incluye 4 elementos
- La matriz de luz
- El filtro de luz
- El controlador digital
- El conversor analogico digital

1. **Matriz de Píxeles CMOS (Complementary Metal-Oxide-Semiconductor)**:
   - La matriz de píxeles CMOS consiste en una disposición bidimensional de fotodiodos individuales, cada uno capaz de convertir la luz incidente en carga eléctrica.

2. **Controladores de Píxeles y Circuitos de Lectura y Amplificación**:
   - Cada píxel en la matriz CMOS está equipado con su propio circuito de control, que incluye amplificadores, selectores y circuitos de reset. Estos circuitos controlan la lectura y amplificación de la señal eléctrica generada por el fotodiodo.

3. **Circuitos de Conversión Analógico-Digital (ADC)**:
   - Después de que la señal eléctrica se amplifica en cada píxel, se envía a los circuitos de conversión ADC para su digitalización. Aquí, la señal analógica se convierte en una señal digital que representa la intensidad de la luz en cada píxel.


### Acumulacion de carga
En los sensores CMOS, la acumulación de carga ocurre cuando la luz incide en los fotodiodos de cada píxel, generando electrones que se acumulan en una región de potencial bajo el fotodiodo. Esta carga eléctrica representa la intensidad luminosa en cada punto de la imagen. Posteriormente, la carga se lee, amplifica y convierte en una señal digital para formar la imagen. Este proceso permite que los sensores CMOS capturen la luz de manera eficiente y la conviertan en señales digitales, lo que los hace ideales para una amplia gama de aplicaciones de imágenes digitales.

### Fuentes de ruido
Las fuentes de ruido en los sensores de imagen CMOS pueden incluir:

1. **Corriente de Oscuridad (Dark Current)**:
   - Es la corriente eléctrica generada en ausencia de luz, debido a la generación térmica de portadores de carga en los fotodiodos. Afecta la calidad de la imagen al agregar una señal no deseada en las regiones oscuras de la imagen.

2. **Ruido de Disparo (Shot Noise)**:
   - Es la variación aleatoria en la cantidad de fotones detectados por los fotodiodos debido a la naturaleza discreta de la luz. Se produce incluso en condiciones de luz constante y se manifiesta como patrones de grano en la imagen.

3. **Ruido de Parpadeo (Flicker Noise)**:
   - Es el ruido electrónico generado por fluctuaciones aleatorias en los componentes electrónicos del sensor CMOS, como los transistores de conmutación. Puede manifestarse como variaciones temporales en la señal de salida y afectar la estabilidad de la imagen.

### Generalidad
En lugar de reemplazar por completo a los sensores CCD, los sensores CMOS han creado un nuevo mercado aprovechando ciertas ventajas. Aunque los sensores CMOS han ganado popularidad en diversas aplicaciones, especialmente en dispositivos de consumo como cámaras digitales y teléfonos inteligentes, los sensores CCD aún tienen su lugar en aplicaciones especializadas donde se requiere alta calidad de imagen y baja luz. Por lo tanto, en lugar de eliminar por completo a los CCD, los CMOS han diversificado el mercado al ofrecer una alternativa más económica y versátil para algunas aplicaciones, mientras que los CCD continúan siendo utilizados en otras donde son más adecuados.





### Sensores de control
Los sensores line-scan son dispositivos diseñados para capturar imágenes de manera lineal, en lugar de capturar una imagen completa en un instante. Estos sensores están organizados en una única fila de píxeles, y al mover el objeto o la escena frente al sensor, se captura una imagen línea por línea. Son comúnmente utilizados en aplicaciones donde se requiere alta resolución en una dimensión y alta velocidad de captura, como en sistemas de inspección industrial y escáneres de documentos.

Por otro lado, los sensores matriciales a colores son sensores de imagen que utilizan un patrón de filtros de color, como el filtro de Bayer, para capturar información de color en cada píxel. Estos sensores están organizados en una matriz bidimensional de píxeles, donde cada píxel tiene capacidad para detectar luz en una determinada longitud de onda. Son ampliamente utilizados en cámaras digitales y otros dispositivos que requieren captura de imágenes a color.

### Sensor a color CCD
El sensor a color de CCD único es una tecnología que utiliza un único sensor CCD para capturar información de color. Esto se logra mediante la implementación de un filtro de color, como el filtro de Bayer, sobre el sensor CCD. Este filtro divide la luz en diferentes componentes de color (rojo, verde y azul) y permite que cada píxel del sensor CCD detecte la luz en una longitud de onda específica, lo que facilita la captura de imágenes a color.


### Filtros de color
El filtro de Bayer es un tipo común de filtro utilizado en los sensores de imagen digitales. Consiste en una matriz de patrones de filtros rojo, verde y azul, que se coloca sobre la matriz de píxeles del sensor de imagen. Este filtro permite capturar información de color en cada píxel de la imagen, aunque cada píxel solo detecta un componente de color primario (rojo, verde o azul). Posteriormente, se utiliza un algoritmo de interpolación para completar la información de color en cada píxel de la imagen final.

#### Alternativas
Existen alternativas al filtro de Bayer que también se utilizan en sensores de imagen digitales. Algunas de estas alternativas incluyen:

1. **CYGM (Cyan, Yellow, Green, Magenta)**: Este es un tipo de filtro de color que utiliza cuatro componentes de color: cian, amarillo, verde y magenta. Se utiliza en algunos sensores de imagen para mejorar la precisión del color y reducir los artefactos de color.

2. **RGBW (Red, Green, Blue, White)**: Este tipo de filtro de color añade un componente de color blanco al tradicional filtro de Bayer RGB. El componente blanco ayuda a mejorar la sensibilidad a la luz en condiciones de baja iluminación y puede mejorar el rendimiento en la captura de detalles en áreas de alta luminosidad.

3. **EXR (Extended Range)**: Este tipo de filtro de color utiliza una combinación de filtros de color RGB y filtros de captura de luz adicional. Esto permite una mayor flexibilidad en la captura de detalles tanto en áreas de alta como de baja luminosidad, proporcionando una mayor riqueza tonal y un rango dinámico extendido en la imagen final.

### Telecamara
Una telecámara a color puede utilizar la solución de 3CCD (3 Charged-Coupled Device) para capturar imágenes en color con alta calidad. Este sistema utiliza tres sensores CCD separados para capturar la luz en los componentes de color rojo, verde y azul de la imagen. 

#### Prisma tricuico
El prisma tricromático, también conocido como prisma tricuóico, es un componente óptico utilizado en las cámaras de vídeo de 3CCD para dividir la luz entrante en sus tres componentes de color primarios (rojo, verde y azul) y dirigir cada componente hacia su propio sensor CCD. Este prisma consta de dos prismas que se combinan para dividir y dirigir la luz correctamente hacia los sensores CCD.

### Sensores CCD
Los sensores matriciales RGB son sensores de imagen que utilizan una matriz bidimensional de píxeles, donde cada píxel tiene la capacidad de detectar luz en los componentes de color rojo, verde y azul. Estos sensores son similares a los sensores CCD, pero están diseñados específicamente para capturar imágenes en color. La información de color de cada píxel se utiliza para generar una imagen en color completa.