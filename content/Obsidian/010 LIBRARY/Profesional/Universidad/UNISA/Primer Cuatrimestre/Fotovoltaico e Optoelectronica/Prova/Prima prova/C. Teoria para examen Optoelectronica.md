
## Largueza de emision
Lámpara incandescente>LED>Diodo láser Fabry-Perot>Diodo láser VCSEL>Diodo láser DBR>Diodo láser DFB>Láser de estado sólido (ej. Nd:YAG)=Láser de HeNe

## Monomodale y multimodales
- **Monomodales:** DFB y DBR
- **Multimodales:** Fabry-Perot y VCSEL
Los de estado solido pueden ser multimodales o monomodales
## Semiconductores para cada sector del espectro electromagnetico


| Rango espectral | Materiales |
|-|-|  
| Ultravioleta(10nm) | GaN(led, laseres, detector UV), SiC(Led,detector UV) |
| Visible(400-800nm) | GaP(Led rojo), GaAs(Led rojo e infrarrojo), InGaN(Led y laseres verdes y azules), AlGaInP(Leds Rojo y anaranjados) |
| Infrarrojo cercano (700-1400nm) | GaAs(Laseres), AlGaAs(Laseres), InGaAs(fotodetecto y laser), InGaAsP(Laseres) |
| Infrarrojo medio (1.5-5 μm) | InGaAs(Fotodetector), InGaAsP(Fotodetector y laseres), PbS |
| Infrarrojo lejano (8-12 μm) | InSb(Detector infrarrojo), HgCdTe(Detector infrarrojo) |
|Infrarrojo>20um|Transiciones intrabanda InP/InGaAs e GaAs/GaAlAs|

|Color|Material|
|---|---|
|Rojo|AlGaInP,GaAs,GaP,GaAsP(Directo)|
|Verde|InGaN,GaN,GaP(indirecto),AlGaP,AlGaInP(Directo)|
|Blanco|Blue/UV con fosforo|
|Azul|InGaN(directo),SiC,Si|

**Heterouniones de materiales comerciales:**
- GaAs/AlGaAs → Láseres 850-980nm
- InP/InGaAsP → Láseres 1300-1550nm
- GaN/InGaN → Láseres azules/UV


**Estructuras cuánticas**
- InGaAs/InP: Láseres, detectores IR
- GaN/AlGaN: LEDs y láseres UV  

**Algunas pautas generales son:**
- Materiales de bandgap directo para emisión de luz (LEDs, láseres)
- Se buscan bandgaps ligeramente menores a la longitud de onda deseada
- Aleaciones como AlGaAs o InGaAsP permiten ajustar el bandgap
- El Si puede usarse para detección en visible e infrarrojo cercano
- A mayor longitud de onda, materiales como InSb o HgCdTe


## Materiales para hacer pozos cuanticos
- El material de pozo cuántico debe tener un menor ancho de banda prohibida (bandgap) que el material de barrera. Esto confina a los electrones en el pozo.
- **Pequeña diferencia en sus parámetros de red** (distancia interatómica), usualmente no más del ~10%. Esto permite epitaxiarlas juntas.
- Los más utilizados son los semiconductores III-V como GaAs, InP, GaInAs, AlGaAs, etc. También se usan materiales II-VI.

- Ejemplos típicos:

* InGaAs (pozo) / InP o AlInAs (barrera)
* GaInAs (pozo) / AlInAs o AlGaInAs (barrera) 
* GaAs (pozo) / AlGaAs (barrera)

La relación correcta es $\lambda = \frac{1240}{E}$, donde $\lambda$ se mide en nanómetros y $E$ es la energía del fotón en electronvoltios (eV).


| Material | Bandgap (eV) | Longitud de Onda Asociada (nm) |
|----------|--------------|-------------------------------|
| GaAs     | 1.42         | 871                           |
| InP      | 1.35         | 918                           |
| InAs     | 0.36         | 3445                          |
| InSb     | 0.17         | 7294                          |
| GaN      | 3.39         | 365                           |
| GaInN    | 0.7 - 3.4    | 365 - 1771                   |
| AlAs     | 2.16         | 574                           |
| AlGaAs   | 1.42 - 2.16  | 871 - 574                    |
| InGaAs   | 0.36 - 1.42  | 3445 - 871                   |


**Propiedades que debe tener un material para usarse como barrera en un pozo cuántico:**
- Bandgap más grande que el material del pozo: Esto permite confinar electrones en el pozo y que no escapen a la barrera.

- Parámetro de red cercano al del pozo: Usualmente con discrepancia menor al 10%. Permite crecer ambos materiales juntos.

- Buena calidad cristalina con pocos defectos: Para evitar dispersión de portadores. 

- Debe formar una unión tipo I con el pozo: Bandas de conducción y valencia del pozo están dentro de las bandas de la barrera.



| Material | Parámetro de red (Å) |
|-|-|  
| GaAs | 5.6533 |
| InP | 5.8687 |
| InAs | 6.0584 |
| InSb | 6.4794 |
| GaN | 3.189 |
| AlAs | 5.6611 |
| AlP | 5.4687 |
| InGaAs | 5.6533 - 5.8687 |
| AlGaAs | 5.6533 - 5.6611 |

Algunos puntos clave sobre estos parámetros de red:

- Permite identificar compatibilidad de redes entre materiales.
- Idealmente se busca una coincidencia perfecta entre pozo y barrera.
- Aleaciones como InGaAs y AlGaAs permiten ajustar el parámetro continuamente.
- Diferencias menores al 10% suelen ser aceptables.
- El desajuste de red origina defectos y disminuye rendimiento.
## Tipos de laser

### General
#### Tipos de emisiones

Los tipos de emisiones surface emitting y edge emitting se refieren a la forma en que la luz se emite de un diodo láser.


**Emisión surface emitting**

En un diodo láser de emisión surface emitting, la luz se emite a través de la superficie del diodo. Esto se logra mediante el uso de una unión p-n que está dispuesta en forma de plano. La luz emitida se refleja en la superficie del diodo y se amplifica por el material activo.

Los láseres de emisión surface emitting tienen una serie de ventajas sobre los láseres de emisión edge emitting. Son más eficientes, ya que la luz se emite a través de una superficie más grande. También son más fáciles de fabricar, ya que no requieren la compleja estructura de unión p-n en forma de V utilizada en los láseres de emisión edge emitting.

**Emisión edge emitting**

En un diodo láser de emisión edge emitting, la luz se emite a través de los bordes del diodo. Esto se logra mediante el uso de una unión p-n que está dispuesta en forma de V. La luz emitida se guía a través de los bordes de la unión p-n y se amplifica por el material activo.

Los láseres de emisión edge emitting tienen una serie de ventajas sobre los láseres de emisión surface emitting. Son más compactos, ya que no requieren la estructura de unión p-n plana utilizada en los láseres de emisión surface emitting. También son más fáciles de enfocar, ya que la luz se emite a través de una superficie más pequeña.

**Comparación**

La siguiente tabla compara los dos tipos de emisiones:

|Característica|Emisión surface emitting|Emisión edge emitting|
|---|---|---|
|Tipo de emisión|Superficie|Bordes|
|Unión p-n|Plana|En forma de V|
|Emisión de luz|A través de la superficie|A través de los bordes|
|Ventajas|Más eficiente, más fácil de fabricar|Más compacto, más fácil de enfocar|
|Desventajas|Menos compacto, más difícil de enfocar|Menos eficiente, más difícil de fabricar|

Los dos tipos de emisiones se utilizan en una amplia gama de aplicaciones. Los láseres de emisión surface emitting se utilizan a menudo en aplicaciones que requieren una alta eficiencia, como la telecomunicaciones y el almacenamiento de datos. Los láseres de emisión edge emitting se utilizan a menudo en aplicaciones que requieren un tamaño compacto, como la electrónica de consumo y la medicina.
**Láseres de emisión edge emitting:**

- **Láseres de estado sólido NeHe y Nd:YAG:** Ambos láseres utilizan una unión p-n en forma de V. Por lo tanto, ambos láseres son de emisión edge emitting.
- **Láseres de Fabry-Perot:** Estos láseres utilizan una cavidad óptica formada por dos espejos planos. La luz emitida se refleja en los espejos y se amplifica por el material activo. La luz emitida puede ser de emisión edge emitting o surface emitting, dependiendo de la estructura de la unión p-n.
- **Láseres de DBR:** Estos láseres utilizan una cavidad óptica formada por dos espejos con capas de reflexión distribuidas. La luz emitida se refleja en los espejos y se amplifica por el material activo. La luz emitida suele ser de emisión edge emitting, aunque también puede ser de emisión surface emitting.
- **Láseres de DFB:** Estos láseres utilizan una cavidad óptica formada por un espejo totalmente reflectante y un espejo parcialmente reflectante. La luz emitida se refleja en el espejo totalmente reflectante y se amplifica por el material activo. La luz emitida suele ser de emisión edge emitting, aunque también puede ser de emisión surface emitting.

**Láseres de emisión surface emitting:**

- **Diodos láser comunes:** Los diodos láser comunes suelen utilizar una unión p-n plana. Por lo tanto, estos láseres son de emisión surface emitting.

#### Efecto dark line y catastrophical optical damage

El dark line defect (DLD) es una zona de baja reflectancia que se forma en la superficie de un diodo láser. El DLD puede ser causado por un número de factores, incluyendo el calentamiento excesivo, la exposición a radiación o la presencia de defectos en el material del diodo láser.

El catastrophical optical damage (COD) es un evento que ocurre cuando un diodo láser se calienta demasiado y se funde. El COD puede causar daños permanentes en el diodo láser, incluso la destrucción completa del dispositivo.

La relación entre el DLD y el COD es que el DLD puede ser un precursor del COD. Un DLD puede concentrar la energía del láser, lo que puede conducir al calentamiento excesivo y al COD.

En el caso de un diodo láser con un alto valor de temperatura característica, la corriente de umbral es más alta. Esto significa que el diodo láser requiere una mayor potencia para alcanzar el umbral de las ondas estacionarias. Como resultado, el diodo láser con un alto valor de temperatura característica es menos propenso a sufrir un calentamiento excesivo y, por lo tanto, es menos propenso a desarrollar DLD y COD.


#### Observaciones
  
El efecto de la temperatura en la longitud de onda de emisión de un diodo edge emitting es relativamente pequeño. El aumento de la temperatura puede causar un aumento de la longitud de onda de emisión de un diodo edge emitting, pero este efecto es generalmente menor que el efecto del relleno de banda.

El aumento de la temperatura hace que la banda prohibida del material del diodo láser se expanda. Esto significa que los electrones necesitan más energía para recombinarse, lo que resulta en una longitud de onda de emisión más larga.

- LEDs y láseres de semiconductor se basan en recombinación espontánea y estimulada respectivamente. 
- El efecto de llenado de bandas hace que la longitud de onda de emisión aumente con la corriente de inyección.
### Laser Fabry Perot
Los diodos láser Fabry-Perot (FP) son un tipo de láser semiconductor que utilizan una cavidad óptica de Fabry-Perot para confinar los fotones emitidos. La cavidad óptica consiste en dos espejos, uno totalmente reflectante y otro parcialmente reflectante.

El funcionamiento de un diodo láser FP es similar al de cualquier otro láser semiconductor. Cuando el diodo está polarizado en directa, los electrones y los huecos se recombinan en la región activa del diodo, emitiendo fotones. Estos fotones son reflejados por los espejos de la cavidad óptica, lo que les da la oportunidad de interactuar con otros electrones y huecos. Si la intensidad de la luz es lo suficientemente alta, se producirá una reacción en cadena de emisión estimulada, en la que los fotones emitidos estimulan la emisión de más fotones.

La diferencia clave entre un diodo láser FP y otros tipos de láseres semiconductores es la longitud de la cavidad óptica. La longitud de la cavidad óptica determina la frecuencia de resonancia de la cavidad. Los fotones emitidos que tienen la frecuencia de resonancia de la cavidad se reflejan con mayor eficiencia que los fotones emitidos con otras frecuencias. Esto da lugar a una interferencia constructiva entre los fotones emitidos, lo que aumenta la intensidad de la luz emitida.


La longitud de la cavidad óptica de un diodo láser FP suele ser de varios milímetros, este hace que estos laseres sean multimodal, ya que con una cavidad tan grande varias longitudes de onda pueden resonar. Esta longitud es necesaria para obtener una anchura espectral estrecha, que es una característica importante de los láseres FP.
- Para calcular el espectro longitudinal de un diodo FP es necesario:
	- El espectro de ganancia del material activo
	- El coefficiente de absorbimiento del material activo
	- El coeficiente de refraccion del material activo
	- La longitud de la cavidad
	- La frecuencia de resonancia

Los diodos láser FP se utilizan en una amplia gama de aplicaciones, incluyendo telecomunicaciones, almacenamiento de datos, procesamiento de imágenes y medicina.

En resumen, las características especiales de los diodos láser FP son:

- Una cavidad óptica de Fabry-Perot, que consiste en dos espejos, uno totalmente reflectante y otro parcialmente reflectante.
- Una longitud de cavidad óptica de varios milímetros.
- La corrente di soglia de un diodo laser es directamente proporcional con la temperatura de operacion, esto se debe a que con menor temperatura, la velocidad de recombinacion aumenta
- La corriente di soglia tambien es directamente proporcional al duty cycle, esto se debe a que la optencia media generada por el laser es inferior con un duty cycle inferior, esto es por la temperatura
- A mayor reflectividad de los espejos, la corriente de soglia es menor
### Laser Nd:YAG
Aquí un resumen sobre el láser de estado sólido Nd:YAG:
- El Nd:YAG consiste en una matriz de YAG (Yttrium Aluminum Garnet) dopada con iones Nd3+ como material activo.
- El YAG es un material cristalino con bandas de energía continuas, que sirve como matriz huésped de los iones Nd3+. No contribuye a la emisión láser.
- Los iones Nd3+ presentan niveles electrónicos cuantizados o discretos debido al campo cristalino generado por la matriz de YAG. 
- Estos niveles cuánticos permiten transiciones ópticas entre los electrones 4f del Nd3+.
- Al bombear el material, electrones del Nd3+ pasan a un nivel excitado de mayor energía.
- Al decaer de nuevo a niveles más bajos, emiten fotones cuya longitud de onda depende sólo de la diferencia de energía entre niveles 4f del Nd3+.
- Así, la longitud de onda está determinada por la estructura de niveles cuánticos del ion Nd3+ y no por las bandas continuas del YAG.
- El Nd:YAG emite típicamente luz láser infrarroja de 1064 nm debido a transiciones entre niveles 4f específicos del Nd3+.


Entiendo tu confusión, déjame intentar una explicación más completa sobre el fundamento del Nd:YAG:
- El objetivo es crear un material que emita luz láser de forma eficiente al ser excitado ópticamente. 
- Ni el Nd3+ solo ni el YAG tienen buenas propiedades para la emisión láser:
	1) El Nd3+ es sólo un ion aislado que no puede emitir láser eficientemente por sí solo. 
	2) El YAG tiene bandas continuas que no permiten una emisión estimulada de luz coherente.
- Pero al combinarlos, el YAG proporciona una matriz sólida que aloja ordenadamente a los iones Nd3+.
- Esta matriz cristalina crea un campo eléctrico en los iones Nd3+ (campo cristalino) que cuantiza sus niveles electrónicos.
- Así el Nd3+ presenta ahora niveles discretos entre los que puede darse emisión estimulada, generando luz láser. 
- El YAG como matriz aporta además buenas propiedades térmicas y mecánicas.
- En resumen, ninguno puede emitir luz láser por separado, pero su combinación crea un nuevo material con propiedades únicas de emisión.
#### NeHe
- La diferencia entre un láser HeNe y un láser Nd:YAG es el material activo que utilizan. Ambos láseres utilizan una cavidad óptica para confinar la luz emitida, y ambos láseres utilizan la emisión estimulada para generar luz.
- La longitud de onda de emisión de un láser de estado sólido se determina por la diferencia en energía entre los niveles energéticos discretos del material activo. Esta diferencia en energía es constante, independientemente del índice de refracción del material activo.
- La anchura del espectro de emisión de un láser de estado sólido se debe a la distribución de los átomos o moléculas del material activo en los diferentes niveles energéticos. Esta distribución no depende del índice de refracción del material activo.





### Laser DFB
**Funcionamiento de los diodos láser DFB**

Los diodos láser DFB (Distributed Feedback Laser) son un tipo de diodo láser que utiliza una rejilla de Bragg distribuida para controlar la longitud de onda de emisión. La rejilla de Bragg está formada por una serie de capas alternas de material con diferentes índices de refracción.

Cuando la luz pasa a través de la rejilla de Bragg, se produce una interferencia constructiva y destructiva que da lugar a un patrón de ondas estacionarias. El patrón de ondas estacionarias está determinado por la estructura de la rejilla de Bragg y la longitud de onda de la luz.

En un diodo láser DFB, la corriente de polarización crea una onda estacionaria en la región activa del diodo. La rejilla de Bragg controla la longitud de onda de esta onda estacionaria, lo que da al diodo láser una longitud de onda de emisión precisa.

**Construcción de los diodos láser DFB**

Un diodo láser DFB consta de los siguientes componentes:

- **Unión p-n:** La unión p-n es la región activa del diodo láser. En esta región, los electrones y los huecos se recombinan para emitir luz.
- **Rejilla de Bragg:** La rejilla de Bragg está formada por una serie de capas alternas de material con diferentes índices de refracción.
- **Espejos:** Los espejos reflejan la luz de la rejilla de Bragg, lo que ayuda a mantener la onda estacionaria.

El diodo láser DFB se fabrica mediante un proceso de epitaxia. En este proceso, se depositan capas alternas de material con diferentes índices de refracción sobre una base semiconductora.

**Ventajas de los diodos láser DFB**

Los diodos láser DFB tienen una serie de ventajas sobre otros tipos de diodos láser, incluyendo:

- **Longitud de onda de emisión precisa:** La rejilla de Bragg permite al diodo láser DFB emitir una luz con una longitud de onda precisa. Esto es importante para aplicaciones como la comunicación óptica y la medición de longitud de onda.
- **Estabilidad de la longitud de onda:** La longitud de onda de emisión del diodo láser DFB es estable a lo largo del tiempo y con los cambios de temperatura.
- **Ancho de línea estrecho:** El ancho de línea del diodo láser DFB es estrecho, lo que significa que la luz emitida es monocromática. Esto es importante para aplicaciones como la comunicación óptica y la espectroscopia.

**Aplicaciones de los diodos láser DFB**

Los diodos láser DFB se utilizan en una amplia gama de aplicaciones, incluyendo:

- **Comunicación óptica:** Los diodos láser DFB se utilizan en redes de telecomunicaciones para transmitir datos a largas distancias.
- **Medición de longitud de onda:** Los diodos láser DFB se utilizan en instrumentos de medición de longitud de onda para determinar la longitud de onda de la luz.
- **Espectroscopia:** Los diodos láser DFB se utilizan en espectroscopios para analizar la composición química de las muestras.
- **Grabado de materiales:** Los diodos láser DFB se utilizan en sistemas de grabado para grabar materiales con precisión.

La rejilla de Bragg es un dispositivo que utiliza la difracción de la luz para controlar su comportamiento. Está formada por una serie de capas alternas de material con diferentes índices de refracción.

Cuando la luz pasa a través de una rejilla de Bragg, se produce una interferencia constructiva y destructiva que da lugar a un patrón de ondas estacionarias. El patrón de ondas estacionarias está determinado por la estructura de la rejilla de Bragg y la longitud de onda de la luz.

En el caso de los diodos láser DFB, la rejilla de Bragg está formada por una serie de capas alternas de material semiconductor con diferentes índices de refracción. Cuando la luz pasa a través de la rejilla de Bragg, se produce una interferencia constructiva que da lugar a una onda estacionaria con una longitud de onda específica.

La longitud de onda de la onda estacionaria está determinada por la siguiente fórmula:

```
λ = 2d / n
```

donde:

- λ es la longitud de onda de la onda estacionaria, en nm
- d es el espaciado entre las capas de la rejilla de Bragg, en nm
- n es el índice de refracción medio de las capas de la rejilla de Bragg

En un diodo láser DFB, la corriente de polarización crea una onda estacionaria en la región activa del diodo. La rejilla de Bragg controla la longitud de onda de esta onda estacionaria, lo que da al diodo láser una longitud de onda de emisión precisa.

Para entender mejor el funcionamiento de la rejilla de Bragg, podemos imaginar un ejemplo sencillo. Supongamos que tenemos una rejilla de Bragg formada por dos capas de material con índices de refracción 1.5 y 1.2, respectivamente. El espaciado entre las capas es de 100 nm.

Según la fórmula anterior, la longitud de onda de la onda estacionaria sería:

```
λ = 2 * 100 nm / (1.5 + 1.2)
```

```
λ = 200 nm / 2.7
```

```
λ = 74,07 nm
```

En este caso, la rejilla de Bragg controlaría la longitud de onda de la luz emitida por el diodo láser a 74,07 nm.

Por supuesto, las rejillas de Bragg reales son mucho más complejas que nuestro ejemplo sencillo. Sin embargo, el principio de funcionamiento es el mismo.

  
La principal diferencia entre los diodos láser DFB y DBR es la ubicación de la rejilla de Bragg. En los diodos láser DFB, la rejilla de Bragg está formada por una serie de capas alternas de material semiconductor que se extienden a lo largo de toda la longitud del diodo. En los diodos láser DBR, la rejilla de Bragg está formada por una serie de capas alternas de material semiconductor que se encuentran en la superficie del diodo.

## Metodos de crecimientos semiconductores

MBE (Molecular Beam Epitaxy):
- Es una técnica de crecimiento de epitaxia de haces moleculares. 
- Se utiliza para crecer semiconductores del tipo III-V como los utilizados en láseres o dispositivos optoelectrónicos.  
- Requiere el uso de celdas de Knudsen que controlan precisamente los flujos de los átomos.
- Permite un control preciso del espesor y las interfases de las capas crecidas.
- Richiede una ricottura del campione dopo la deposizione 

MOCVD (Metal Organic Chemical Vapor Deposition):
- Utiliza precursores organometálicos en fase gas para depositar los átomos del semiconductor.
- Es útil para crecer estructuras de múltiples capas cuánticas como los láseres de pozo cuántico.  
- No requiere celdas de Knudsen ni recocido posterior del material.
- Permite dopar las capas durante el crecimiento.
- Es indispensable para fabricar LEDs, láseres de semiconductor y células solares de alto rendimiento.


PECVD (Plasma Enhanced CVD): 
- Es una variante de CVD que utiliza plasma para activar los gases precursores.  
- Se aplica para depositar capas delgadas de silicio amorfo hidrogenado.
- La incorporación de hidrógeno se controla con la temperatura del sustrato.
- El hidrógeno influencia el bandgap óptico y fotoconductividad del material.
- Los elementos típicos son: generador de RF, cámara de vacío, sistemas de flujo de gases, bombas de vacío, sistema de calentamiento del sustrato.


## Aplicaciones(telecomunicaciones)

Semiconductores en Telecomunicaciones

- Los sistemas de comunicaciones ópticas se basan en la transmisión de señales luminosas a través de fibras ópticas. Requieren de fuentes de luz (emisores), detectores de luz (fotodetectores) y amplificadores ópticos.

Emisores
- Popularmente se utilizan láseres de semiconductor basados en heteroestructuras de materiales III-V (GaAs, InP, etc) que permiten confinar portadores y luz (efecto láser).
- Para transmitir en la tercera ventana de las fibras ópticas (1550nm) se emplean aleaciones como InGaAsP o InGaAlAs sobre sustratos de InP.

Detectores
- Los fotodiodos PIN de InGaAs son ampliamente utilizados como detectores por su rápida respuesta y bajo ruido en comunicaciones de 850nm y 1550nm.
- El silicio también se usa en detectores de 850nm aprovechando su menor coste.

Amplificadores
- Los amplificadores ópticos de fibra dopada con Erbio compensan la atenuación de la señal, sin necesidad de repetidos ciclos de conversión opto-eléctrica. Son parte integral en los enlaces de fibra óptica.

Heteroestructuras 
- La unión de diferentes semiconductores (heterouniones) es indispensable para crear guías de onda ópticas y eléctricas que mejoren el rendimiento de los dispositivos optoelectrónicos.

Espero que este resumen integrador de los conceptos clave de semiconductores para telecomunicaciones le sea de utilidad. Por favor no dude en indicarme si necesita que profundice o amplíe algún punto en particular.


## Medidas 

Slope efficiency de un láser:
- Se mide en W/A. Indica la eficiencia de conversión de corriente a potencia óptica.
- Se obtiene derivando la curva de potencia vs corriente sobre el umbral láser.

Responsividad de un fotodiodo: 
- Se mide en A/W. Representa la corriente generada por unidad de potencia óptica incidente.

Coeficiente de absorción (α):
- Se mide en cm−1. Indica la fracción de luz absorbida al propagarse en el material. 
- Se determina a partir de medidas de transmitancia en función de la longitud de onda. Requiere conocer el espesor de la muestra.
- Si la longitud de onda de la luz que estamos analizando está muy cerca de la longitud de onda del borde de absorción del material, calculada a partir de su banda prohibida como 1240 nm/E_g, entonces esperamos que el coeficiente de absorción α sea muy elevado.

Comparando α entre materiales a una longitud de onda dada:
- El GaAs tiene un α mayor que el Si y Ge a 1300 nm y 1550 nm.
- El InGaAs presenta un α mayor al del Si y GaN a 1550 nm.

Eficiencia "pared-enchufe" de un láser: 
- Relación entre potencia óptica de salida y potencia eléctrica de entrada. 
- Valores típicos: 10-30% para diodos láser de semiconductor.


## Mecanica cuantica

### Cuerpo Negro:
- Su espectro de emisión depende de la temperatura según la ley de Planck.
- Al aumentar la temperatura, la longitud de onda de emisión máxima disminuye (se desplaza hacia el azul) y la potencia emitida aumenta.
- La explicación del espectro de cuerpo negro llevó al desarrollo de la mecánica cuántica, no de la relatividad.
$$λ_{max} = \frac{2.8977685.10^{-3} [m * K]}{T[K]}$$
### Pozos Cuantico (Quantum Wells):
- La función de onda de los electrones en un pozo cuántico tiene valores positivos y negativos, y es cero fuera del pozo sólo para barreras de potencial infinitas.
- En un pozo finito la función de onda decae exponencialmente fuera del pozo pero no es rigorosamente cero.
- El bandgap efectivo de una estructura de múltiples pozos cuánticos disminuye al aumentar el número de pozos y al hacerlos más angostos.





## Ternarios

GaAlAs:
- Es un semiconductor ternario basado en GaAs.
- Puede crecer libre de defectos sobre GaAs ajustando adecuadamente la fracción molar x. 
- Se utiliza en láseres e intercapas en dispositivos optoelectrónicos con emisión en el rojo e infrarrojo cercano.

GaInN: 
- Forma pozos cuánticos con GaN, útiles en LEDs blancos y láseres azules de alta eficiencia.
- Tiene banda prohibida directa, ideal para dispositivos emisores de luz.  
- Se hace crecer sobre sustratos de zafiro.

InGaAs:
- Crece sobre InP. Se usa en fotodiodos y láseres para 1300 nm y 1550 nm.
- Permite bandas prohibitivas directas cambiando la fracción molar de In y Ga.

InGaN:
- Banda prohibida directa, ideal para LEDs de alta luminosidad.
- Se utiliza en LEDs verdes, azules y blancos de nitruro.


## Heteroestructuras


- Las heteroestructuras son uniones de diferentes semiconductores apilados. 

- Permiten confinar portadores (electrones y huecos) y luz, claves en LEDs y láseres eficientes.

- El confinamiento eléctrico y óptico en la región activa mejora el rendimiento.

- El desajuste de parámetro de red entre materiales genera tensiones que modifican la estructura de bandas.

- El cálculo del desalineamiento de bandas (band-offset) requiere conocer las afinidades electrónicas y anchos de banda prohibida.

- En transistores HBT la heteroestructura en el emisor mejora la inyección de portadores a la base.

- Las heteroestructuras tensionadas permiten variar la estructura de bandas y construir dispositivos rápidos. 

- Hay un espesor crítico superable según el desajuste de la red cristalina entre capas.


## Fotodiodo y Fototransistor


**Fotodiodos PN:** Están formados por una unión PN. Cuando la luz incide sobre la unión PN, los fotones pueden excitar electrones de la banda de valencia de la región P a la banda de conducción de la región N. Los fotodiodos PN se utilizan en una amplia gama de aplicaciones

**Fotodiodos PIN:** Los fotodiodos PIN son similares a los fotodiodos PN, pero tienen una región de material intrínseco (región I) entre las regiones N y P. La región I tiene una conductividad muy baja, lo que reduce la corriente de fuga y mejora la sensibilidad del dispositivo. Los fotodiodos PIN se utilizan en aplicaciones que requieren una alta sensibilidad

**Fotodiodos de avalancha:** Los fotodiodos de avalancha son un tipo especial de fotodiodo que utiliza el efecto de avalancha para amplificar la corriente generada por la luz. El efecto de avalancha se produce cuando un electrón libre colisiona con otro electrón, lo que libera un segundo electrón libre. Este proceso se puede repetir, generando una cascada de electrones libres.Los fotodiodos de avalancha tienen una región de material tipo N con una alta concentración de dopaje. Los fotodiodos de avalancha se utilizan en aplicaciones que requieren una alta sensibilidad

**Fototransistores:** Los fototransistores son dispositivos semiconductores que combinan las propiedades de un transistor con las de un fotodiodo. Están formados por un transistor bipolar, con una unión PN o PIN en la base. La corriente generada en la base se amplifica por el transistor bipolar, lo que proporciona una señal de salida mucho mayor que la corriente eléctrica generada por el fotodiodo.

**Diferencias**
- Los fotodiodos PN tienen una baja sensibilidad y una alta velocidad de respuesta. Los fotodiodos PIN tienen una alta sensibilidad y una baja velocidad de respuesta. Los fotodiodos de avalancha tienen una muy alta sensibilidad y una velocidad de respuesta intermedia.

**Los fotoconductores** son dispositivos semiconductores que cambian su resistencia eléctrica cuando se exponen a la luz. Están formados por un material semiconductor que tiene una conductividad eléctrica muy baja en ausencia de luz. Los fotoconductores se pueden clasificar en dos tipos principales:- **Fotoconductores sensibles a la luz y Fotoconductores sensibles a la radiación** 


**Generalidades de los fotoreceptores**
- La relación señal-ruido disminuye a medida que aumenta la temperatura. Esto se debe a que el ruido térmico aumenta a medida que aumenta la temperatura.
- La SNR aumenta a medida que aumenta la tensión inversa. Esto se debe a que la tensión inversa aumenta la cantidad de fotoelectrones generados por la luz. La tensión inversa crea un campo eléctrico que acelera a los fotoelectrones generados por la luz. Este campo eléctrico aumenta la probabilidad de que los fotoelectrones alcancen el electrodo positivo del fotodiodo, lo que genera una corriente eléctrica.
- Fotodiodos PN y PIN se utilizan en receptores ópticos por su rápida respuesta. La velocidad aumenta con tensión inversa.
- Los fotodiodos de avalancha (APD) proveen ganancia interna por ionización, útiles cuando se requiere alta sensibilidad.
- Los fototransistores ofrecen ganancia, aumentando la sensibilidad. Son más lentos que fotodiodos. Se usan en optoacopladores y controles optoelectrónicos.
- Los fotoconductores tienen menor ancho de banda que fotodiodos pero pueden dar mayor ganancia.
- El acoplamiento entre emisor y detector define la eficiencia de transferencia de corriente (CTR), a esta tambien se la puede definir como responsabilidad

## Preguntas diferentes

**Crecimiento de heteroestructuras: **
- El desajuste de red entre materiales genera tensiones que pueden modificar las bandas de energía.
- El espesor crítico está limitado por la acumulación de tensiones y formación de defectos.


**HEMT (Transistor de alta movilidad de electrones):** Es un tipo de transistor de efecto de campo (FET) que utiliza una estructura de puerta especial para crear un canal de electrones de alta movilidad. Esto permite que los HEMT funcionen a frecuencias más altas y con un consumo de energía menor que los FET convencionales.
- Es usado en alta frecuencia con materiales III-V.
- Es unipolar


**HBT (Transistor bipolar de heterounión):** Es un tipo de transistor bipolar de unión (BJT) que utiliza una estructura de heterounión especial para reducir la resistencia de la base. Esto permite que los HBT funcionen a frecuencias más altas y con una ganancia mayor que los BJT convencionales.
- Se usa en circuitos de alta velocidad.


**VCSEL (Láser emisor de superficie de cavidad vertical):** Es un tipo de diodo láser que emite luz desde una cavidad vertical. Esto permite que los VCSEL sean muy compactos y eficientes. Los VCSEL se utilizan comúnmente en la comunicación óptica, como la comunicación por fibra óptica y el almacenamiento de datos.
- Tienen problemas de disipación de calor y resistencia en serie.
- No es edge emitting
- Frecuencia de funcionamiento baja


**SAGM (Fotodiodo de avalancha multipíxel de ganancia mejorada y selección de modo de ánodo único):** Es un tipo de fotodiodo que utiliza una estructura especial para mejorar la ganancia y seleccionar el modo de funcionamiento. Esto permite que los SAGM APD logren una alta sensibilidad y un bajo ruido. 
- En los APDs SAGM la capa de multiplicación M está en el InP mientras que la absorción A ocurre en el InGaAs.


**Tabla que resume las características clave de cada tipo de dispositivo:**

| Dispositivo | Frecuencia de funcionamiento | Consumo de energía | Ganancia | Ruido | Aplicaciones |
|---|---|---|---|---|---|
| HEMT | Alta | Baja | Baja | Baja | Microondas, ondas milimétricas |
| HBT | Alta | Alta | Alta | Media | RF, microondas |
| VCSEL | Baja | Baja | Baja | Baja | Comunicación óptica |
| SAGM APD | Baja | Alta | Alta | Alta | Visión nocturna, detección de láser, lidar |


#### Eccitoni

Los eccitones son pares electrón-hueco unidos por fuerzas coulombianas en semiconductores y aislantes. Se forman cuando un electrón en la banda de conducción se une a un hueco en la banda de valencia.
Los eccitones pueden influir en varias propiedades optoelectrónicas de semiconductores como GaP:
- Los eccitones aumentan la absorción de fotones cerca del borde de la banda prohibida debido a transiciones eccitónicas permitidas.
- Los eccitones tienden a disipar su energía en forma de calor antes que emitir fotones útiles. Por lo tanto reducen la eficiencia de emisión en LEDs.
- Los eccitones no afectan significativamente la movilidad.
- La presencia de eccitones no cambia el valor de la banda prohibida de un semiconductor

# Observaciones
Muy buena pregunta. La diferencia entre dispositivo semiconductor bipolar y unipolar es la siguiente:

- Dispositivo bipolar: la conducción se realiza mediante portadores de carga tanto positivos (huecos) como negativos (electrones). Un ejemplo son los transistores bipolares (BJT).

- Dispositivo unipolar: la conducción se realiza mayoritariamente por un solo tipo de portador de carga, either electrones o huecos. Algunos ejemplos son los transistores de efecto campo (FETs, como los MOSFETs o JFETs) y los transistores HEMT.

Esto tiene implicaciones en el funcionamiento y prestaciones de los dispositivos:

- Los dispositivos bipolares sufren del efecto de inyección, que los hace más lentos.
- Los unipolares al depender de un solo tipo de portador pueden conmutar más rápido. Pero también tienen más ruido.

# Preguntas profesor
- Orden de largueza de espectro
- VCSEL es monomodal?
- Coeficiente de absorbimiento y bandgap de Ge,GaAs, Si policristalino, monocristalino e amorfo
- De que depende el coeficiente de absorbimiento?
- El ecciton aumenta o disminuye la eficacia?
- 