
Lámpara incandescente>LED>Diodo láser Fabry-Perot>Diodo láser VCSEL>Diodo láser DBR>Diodo láser DFB>Láser de estado sólido (ej. Nd:YAG)=Láser de HeNe

- **Monomodales:** DFB y DBR
- **Multimodales:** Fabry-Perot y VCSEL
Los de estado solido pueden ser multimodales o monomodales

**Heterouniones de materiales comerciales:**
- GaAs/AlGaAs → Láseres 850-980nm
- InP/InGaAsP → Láseres 1300-1550nm
- GaN/InGaN → Láseres azules/UV


**Estructuras cuánticas**
- InGaAs/InP: Láseres, detectores IR
- GaN/AlGaN: LEDs y láseres UV  

**Pozos cuanticos**
* InGaAs (pozo) / InP o AlInAs (barrera)
* GaInAs (pozo) / AlInAs o AlGaInAs (barrera) 
* GaAs (pozo) / AlGaAs (barrera)

La relación correcta es $\lambda = \frac{1240}{E}$, donde $\lambda$ se mide en nanómetros y $E$ es la energía del fotón en electronvoltios (eV).

**Ejercicios practicos**

Fibra plastica: rango de trabajo entre 350nm y 700nm(minimo en 650)
Fibra silicio: Rango de trabajo entre 600nm y 1800nm(minimo en 1100)

$P_{LED}$: Potencia de salida del LED (W) 
α: Coeficiente de atenuación de la fibra (dB/m)  
L: Longitud de la fibra (m) 
R: Responsividad del fotodiodo (A/W) 
$I_{PD}$: Corriente generada en el fotodiodo (A)

$P_{in} = P_{LED} * 10^(-α * L / 10)$ (1)

$I_{PD} = R * P_{in}$ (2)

Sustituyendo (1) en (2):

$I_{PD} = R * P_{LED} * 10^(-α * L / 10)$ (3)

Si la luz tiene un coeficiente de acoplamiento a la fibra, se reduce la potencia de entrada

Cuando se genera un pozo en la curva de longitud de emision en funcion de la corriente es por el efecto de band-filling

Se puede realizar un circuito inversor donde el fotodiodo se encuentre en la entrada y la resistencia rf seria igual a la tension de salida deseada dividida en la corriente de entrada
## Tablas


| Rango espectral | Materiales |
|-|-|  
| Ultravioleta(10nm) | GaN(led, laseres, detector UV) |
| Visible(400-800nm) | GaP(Led rojo), GaAs(Led rojo e infrarrojo), InGaN(Led y laseres verdes y azules), AlGaInP(Leds Rojo y anaranjados) |
| Infrarrojo cercano (700-1400nm) | GaAs(Laseres), AlGaAs(Laseres), InGaAs(fotodetecto y laser), InGaAsP(Laseres) |
| Infrarrojo medio (1.5-5 μm) | InGaAs(Fotodetector), InGaAsP(Fotodetector y laseres), PbS |
| Infrarrojo lejano (8-12 μm) | InSb(Detector infrarrojo), HgCdTe(Detector infrarrojo) |
|Infrarrojo>20um|Transiciones intrabanda InP/InGaAs e GaAs/GaAlAs|

|Color|Material|
|---|---|
|Rojo(620-750nm)|AlGaInP,GaAs,GaP,GaAsP(Directo)|
|Verde(495-570nm)|InGaN,GaN,GaP(indirecto),AlGaP,AlGaInP(Directo)|
|Blanco|Blue/UV con fosforo|
|Azul(450-495nm)|InGaN(directo),AlGaN,GaN|




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
|Ge|0,67|1850|
|Si amorfo|1,7|729|
|Si Poli y mono|1,1|1127|

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
## Tipos de laser

**Edge emitting**
El aumento de la temperatura hace que la banda prohibida del material del diodo láser se expanda. Esto significa que los electrones necesitan más energía para recombinarse, lo que resulta en una longitud de onda de emisión más larga.
- La corrente di soglia de un diodo laser es directamente proporcional con la temperatura de operacion
	- Tambien es directamente proporcional al duty cycle

**Laser Fabry Perot**
- Una cavidad óptica de Fabry-Perot, que consiste en dos espejos, uno totalmente reflectante y otro parcialmente reflectante.
- Una longitud de cavidad óptica de varios milímetros.
- A mayor reflectividad de los espejos, la corriente de soglia es menor
- Para calcular el espectro longitudinal de un diodo FP es necesario:
	- El espectro de ganancia del material activo
	- El coefficiente de absorbimiento del material activo
	- El coeficiente de refraccion del material activo
	- La longitud de la cavidad
	- La frecuencia de resonancia

**Laser Nd:YAG**
- El Nd:YAG consiste en una matriz de YAG (Yttrium Aluminum Garnet) dopada con iones Nd3+ como material activo.
- El YAG es un material cristalino con bandas de energía continuas, que sirve como matriz huésped de los iones Nd3+. No contribuye a la emisión láser.
- Los iones Nd3+ presentan niveles electrónicos cuantizados o discretos debido al campo cristalino generado por la matriz de YAG. 
- Estos niveles cuánticos permiten transiciones ópticas entre los electrones 4f del Nd3+.
- Al bombear el material, electrones del Nd3+ pasan a un nivel excitado de mayor energía.
- Al decaer de nuevo a niveles más bajos, emiten fotones cuya longitud de onda depende sólo de la diferencia de energía entre niveles 4f del Nd3+.
- Así, la longitud de onda está determinada por la estructura de niveles cuánticos del ion Nd3+ y no por las bandas continuas del YAG.
- El Nd:YAG emite típicamente luz láser infrarroja de 1064 nm debido a transiciones entre niveles 4f específicos del Nd3+.

**NeHe**
- La diferencia entre un láser HeNe y un láser Nd:YAG es el material activo que utilizan. Ambos láseres utilizan una cavidad óptica para confinar la luz emitida, y ambos láseres utilizan la emisión estimulada para generar luz.
- La longitud de onda de emisión de un láser de estado sólido se determina por la diferencia en energía entre los niveles energéticos discretos del material activo. Esta diferencia en energía es constante, independientemente del índice de refracción del material activo.
- La anchura del espectro de emisión de un láser de estado sólido se debe a la distribución de los átomos o moléculas del material activo en los diferentes niveles energéticos. Esta distribución no depende del índice de refracción del material activo.





**láser DFB**

Los diodos láser DFB (Distributed Feedback Laser) son un tipo de diodo láser que utiliza una rejilla de Bragg distribuida para controlar la longitud de onda de emisión. La rejilla de Bragg está formada por una serie de capas alternas de material con diferentes índices de refracción.

Cuando la luz pasa a través de la rejilla de Bragg, se produce una interferencia constructiva y destructiva que da lugar a un patrón de ondas estacionarias. El patrón de ondas estacionarias está determinado por la estructura de la rejilla de Bragg y la longitud de onda de la luz.

En un diodo láser DFB, la corriente de polarización crea una onda estacionaria en la región activa del diodo. La rejilla de Bragg controla la longitud de onda de esta onda estacionaria, lo que da al diodo láser una longitud de onda de emisión precisa.

  
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

PECVD (Plasma Enhanced CVD): 
- Es una variante de CVD que utiliza plasma para activar los gases precursores.  
- Se aplica para depositar capas delgadas de silicio amorfo hidrogenado.
- La incorporación de hidrógeno se controla con la temperatura del sustrato.
- El hidrógeno influencia el bandgap óptico y fotoconductividad del material.



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

**Cuerpo Negro:**
- Su espectro de emisión depende de la temperatura según la ley de Planck.
- Al aumentar la temperatura, la longitud de onda de emisión máxima disminuye (se desplaza hacia el azul) y la potencia emitida aumenta.
- La explicación del espectro de cuerpo negro llevó al desarrollo de la mecánica cuántica, no de la relatividad.
$$λ_{max} = \frac{2.8977685.10^{-3} [m * K]}{T[K]}$$
**Pozos Cuantico (Quantum Wells):**
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
- Se utiliza en LEDs verdes, azules y blancos de nitruro.

InGaAs:
- Crece sobre InP. Se usa en fotodiodos y láseres para 1300 nm y 1550 nm.
- Permite bandas prohibitivas directas cambiando la fracción molar de In y Ga.

## Heteroestructuras
- Permiten confinar portadores (electrones y huecos) y luz, claves en LEDs y láseres eficientes.
- El confinamiento eléctrico y óptico en la región activa mejora el rendimiento.
	- Disminuye la corriente de soglia
- El desajuste de parámetro de red entre materiales genera tensiones que modifican la estructura de bandas.
	- Hay un espesor crítico superable según el desajuste de la red cristalina entre capas.
- El cálculo del desalineamiento de bandas (band-offset) requiere conocer las afinidades electrónicas y anchos de banda prohibida.
- En transistores HBT la heteroestructura en el emisor mejora la inyección de portadores a la base.
- Las heteroestructuras tensionadas permiten variar la estructura de bandas y construir dispositivos rápidos. 
- Mejora la estabilidad termica

