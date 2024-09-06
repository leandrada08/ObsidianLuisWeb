---
cards-deck: Profesional::Universidad::UNISA::Sistemi di interfaccia::Redes Wireless
---


# Español
Una red de sensores inalámbrica (wireless sensor network) es un tipo de red que está compuesta por un conjunto de nodos sensores que se comunican de forma inalámbrica para monitorear condiciones físicas o ambientales
## Introduccion
- *Es importante considerar si es mejor procesar los datos en el edge o enviar las muestras raw*. Procesar consume energía, pero generalmente pesa menos que transmitir, por lo que *es más eficiente enviar menos datos*. 
- *Los sensores tienen relojes internos propios*, *por lo que es necesario sincronizar los datos a una base de tiempo común*. Se pueden usar algoritmos de sincronización como con el GPS, o en cableado sincronizar a un reloj de referencia.
	- El GPS sirve como referencia de hora precisa para teléfonos móviles. El GPS es comunicación unidireccional.
- El protocolo PLC permite transmitir energía y datos por el mismo cable eléctrico. Otros protocolos son MBUS, NFC, WiFi, Bluetooth, LTE, GSM, ANT.
	- Correccion: *Los  PLC permiten trasmitir datos por los cables de energia*, es como lo que explicaba ISE.
- Los teléfonos móviles son nodos sensores con acelerómetro, sensores de temperatura, luz, etc.

### ISM BAND

**ISM BAND(Industrial and medical Band):** Estas son las bandas libres que son fijadas para fines industriales, cientificos y medicos
![[Pasted image 20240119090204.png|400]]
- Está disponible internacionalmente: Las bandas ISM son rangos de frecuencias reservados internacionalmente para uso no comercial, por lo que pueden ser utilizadas sin licencia.
- No requiere pago de licencias: Al ser para uso no comercial, los dispositivos que operan en estas bandas no necesitan pagar costosas licencias de espectro.
- Ancho de banda útil: Las bandas como 2.4 GHz proveen un ancho de banda razonable para varias aplicaciones.
- Regulación flexible: Los rangos ISM tienen regulaciones más flexibles sobre potencia de transmisión y modos de operación. 
- Coexistencia: Varios estándares pueden compartir las mismas bandas ISM utilizando esquemas como salto de frecuencia.
- Disponibilidad de componentes: Al ser ampliamente utilizadas, se encuentran fácilmente componentes de RF para estas frecuencias.
- Bajo costo: La ausencia de licencias y regulaciones flexibles permiten el desarrollo de dispositivos de bajo costo.
En resumen, las bandas ISM han permitido la proliferación de tecnologías inalámbricas de bajo costo al proveer espectro usable internacionalmente sin licencias, con ancho de banda adecuado y regulación flexible.


### Coexistencia de Estándares en la Misma Banda
- *Muchos estándares pueden coexistir en la misma banda utilizando codificación ortogonal de las señales*(Si son ortogonales no se correlacionan). Al codificar las señales de forma ortogonal, pueden transmitirse múltiples señales simultáneamente y decodificarse incluso con ruido.
- *Aunque sean ortogonales, al agregar más señales siempre se introduce ruido*. Se aprovechan los canales ortogonales disponibles.
- *Bluetooth salta a otro canal si detecta mucho ruido o trafico*. Esto se conoce como "Frequency hopping" y aumenta la seguridad al fragmentar los paquetes.
- *La secuencia de saltos de canales es conocida solo por emisor y receptor, se comunica al inicio y salta de forma aleatoria*. Permite coexistir con otros estándares que usen la misma banda.
**Situazione a 2,4 GHz**
![[Pasted image 20240119090208.png|500]]

## Energy Harvesting
La *recolección de energía utiliza fuentes no convencionales* para alimentar los circuitos como los sensores, en este caso *es convenientes ya que estos sensores operan de forma autonoma*, sin cable de alimentacion.
- La energía se convierte en electricidad y se *almacena en una celda* de almacenamiento *duradero como un condensador*, un supercondensador o una celda de microenergía (MEC), que es una forma de batería de estado sólido de litio. 
- El sistema generalmente *incluye circuitos para gestionar la alimentación* y proteger el dispositivo de almacenamiento y otros circuitos.
**Fuentes de Energía:**
![[Pasted image 20240119091529.png|300]]

- **Luz solar:** capturada por celdas fotovoltaicas.
- **Magnetismo.**
- **Vibración (piezo):** capturada por un elemento piezoeléctrico.
- **Diferenciales de temperatura:** capturados por un generador termoeléctrico.
- **Energía de radio (RF).**
- **Energía producida bioquímicamente:** por ejemplo, células que extraen energía del azúcar en la sangre.

### Tecnologías Específicas:

- **Radiofrecuencia (RFID):** Onda de radio que llega al chip, toma energía, carga un condensador y transfiere el contenido de la memoria del chip (su código). Lectura inalámbrica RFID iluminando el dispositivo pasivo con una antena.
- **Termoeléctrica:** utilizando una celda de Peltier, donde el delta de temperatura proporciona energía eléctrica. Por ejemplo, dar frío al frigorífico y expulsar el calor.

### Celle di Peltier
![[Pasted image 20240119095955.png|300]]
#### Effetto Seebeck e Effetto Peltier
- **Effetto Seebeck:** En un circuito de conductores metálicos o semiconductores, una diferencia de temperatura genera una diferencia de potencial eléctrico.
- **Effetto Peltier:** Cuando fluye una corriente entre dos metales/semiconductores diferentes en contacto, se produce una transferencia de calor.

#### Celda de Peltier
- Dispositivo termoeléctrico formado por uniones de efecto Peltier en serie.
- Funciona como una bomba de calor de estado sólido.
- Absorbe calor en una superficie y lo emite en la otra según la dirección de la corriente aplicada.
- Permite enfriar o calentar según se invierta la corriente.
- Existen aisladas (mejor rendimiento) o no aisladas con material cerámico.
- Junto al efecto Seebeck son aplicaciones de sistemas termoeléctricos.
![[Pasted image 20240119100219.png|400]]
## Rete di Sensori Wireless
Las redes inalambricas de sensores estan compuestas por nodos que se comunican sin cables a traves de medios como radiofrecuencia, infrarrojo u optico.
**Caracteristicas:**
- Movilidad de los Nodos
- Transmision por difusion en el medio radio
- Bajo Costo y con Recursos Energéticos Limitados
- Alta tasa de errores comparado con cableado

### Alcance de Transmisión(Portata Trasmissiva)
El alcance de transmisión depende de:
- Relación señal-ruido: debe estar por encima de cierto umbral
- Potencia de transmisión
- Tipo de antena
- Condiciones de propagación
- Velocidad de transmisión
- Condiciones meteorológicas

### Comunicación entre Nodos(Nodi di comunicazione)
La comunicación entre dos nodos inalámbricos puede ser:
- *Unidireccional:* solo un nodo dentro del alcance del otro
- *Bidireccional:* ambos nodos dentro del alcance mutuo

### Cobertura y mobilidad
![[Pasted image 20240119100352.png]]
 Existen diferentes tipos de redes inalámbricas y sus características en cuanto a cobertura y movilidad:
- Redes Satelitales: Cobertura global, movilidad alta ya que los satélites cubren grandes áreas.
- Redes Celulares: Cobertura regional/nacional, movilidad media-alta dentro del área de cobertura de la red celular. Permiten movimiento pero dentro de una región.
- Redes Locales (WLAN): Cobertura local, movilidad baja ya que cubren áreas pequeñas como un edificio. Permiten movimiento dentro de una habitación o edificio.
- Redes Personales (WPAN): Cobertura personal, movilidad muy baja, cubren distancias cortas alrededor de una persona. Usadas para conectar dispositivos personales.
- Redes de Sensores: Cobertura variable, de baja a media movilidad. Pueden desplegarse en áreas extensas pero los nodos individuales tienen alcance limitado.
- Redes Fijas (Cableadas): Cobertura específica, sin movilidad ya que requieren infraestructura cableada fija. 

### Parámetros de una Red de Sensores Inalámbricos:
- Número de Nodos
- Densidad Espacial de los Nodos en la Red
- El Nodo Sensor Está Sujeto a Fallas/No Transmisión
- La Topología de la Red Puede Cambiar Rápidamente
- Energía Limitada y Baja Capacidad Computacional


## Arquitecturas de redes
Existen dos tipos principales de arquitecturas:

### Redes con Infraestructura Fija:
**Todos los Nodos se Comunican con un Punto de Acceso Fijo**
- Ejemplos: Redes Celulares y Algunas Redes Locales(WLAN)
![[Pasted image 20240119101218.png]]
### Redes Ad Hoc(Sin Infraestructura Fija)
**Los nodos pueden comunicarse directamente entre sí** sin infraestructura fija. Se crean espontaneamente entre nodos en el mismo area. Son sistemas distribuidos donde la topologia puede cambiar rapidamente.
- Ejemplos: Algunas Redes Locales, Redes de Radio de Corto Alcance, Redes de Sensores
#### Comunicacion directa entre nodos
- Dos nodos se comunican directamente si están dentro del alcance inalámbrico uno del otro.
- No requiere otros nodos intermedios.
- Limitada por el alcance de transmisión de cada nodo.
![[Pasted image 20240119101305.png]]
#### Comunicacion Multihop:
- Permite comunicación entre nodos fuera de alcance directo.
- *Los paquetes saltan a través de múltiples nodos intermedios hasta llegar al destino*.
- *Requiere encaminamiento y cooperación de nodos intermedios*.
- Extiende el alcance efectivo más allá del alcance directo.
- **Reducción de Potencia Necesaria para la Comunicación entre Nodos A y B**
![[Pasted image 20240119101311.png]]
#### Características de Redes Ad Hoc:
- Fácil y Rápida de Crear
- *Costos Reducidos*
- Diversas Aplicaciones:
  - Comunicaciones Personales: Teléfonos, Laptops
  - Entornos de Trabajo Cooperativos: Redes de Taxis, Salas de Reuniones
  - Operaciones de Emergencia
  - Entornos Militares
- Cobertura Limitada
- Sistema Distribuido
- *Dificultad para Gestionar la Red*
- Dificultad para Mantener la Comunicación con Alta Movilidad de Nodos
- Costos de Mantenimiento y Operación Más Altos

## Tipos de Redes Inalámbricas

### Redes Satelitales:
- Utilizadas para Radiodifusión, Televisión y GPS
### Redes celulares
#### Problema de Transferencia de Señal (Handover):
- Cambio de un Punto de Acceso a Otro
- Las Frecuencias No Son Ilimitadas
- Reutilización de Bandas en Antenas Distantes
![[Pasted image 20240119101429.png]]
#### Arquitectura de la red de celulares
![[Pasted image 20240119101447.png]]





### Redes Locales (WLANs - Redes de Área Local Inalámbricas):
- **Estándares Dominantes:** IEEE 802.11 (WiFi), Hiperlan
- **Canal de Radio (RF)**
- **Con Infraestructura o Ad Hoc**
- En el Pasado No Proporcionaban Calidad de Servicio (Servicio de Datos)
- **Ethernet Inalámbrica:** Altas Velocidades de Transmisión

### Redes Personales (WPAN - Redes de Área Personal Inalámbricas):
- **Estándar Dominante:** Bluetooth (IEEE 802.15)
- **Canal de Radio (RF)**
- **Ad Hoc**
- Servicios de Voz y Datos
- Velocidad de Transmisión Inferior en Comparación con las Redes Locales Inalámbricas

### Redes de Sensores:
- **Medios de Transmisión:** Infrarrojo, RF, Óptico
- **Ad Hoc**
- Muchos Nodos que Envían Información a un Nodo de Puerta a través de Saltos Múltiples
- Dispositivos Muy Simples
- Bajas Velocidades de Transmisión (1-100 kb/s)
- Sin Estándar Dominante



## Partes Fundamentales de un Sensor Inalámbrico:
- **El Microcontrolador que implementa el estándar de comunicación**
- Interfaz del Sensor
- Gestion de energia y duracion de bateria
- Modulo radio y bateria
![[Pasted image 20240119101724.png]]


### Date rate DSSS
![[Pasted image 20240119102403.png]]

### Eleccion de antena
- En funcion de la eficiencia
- Ganancia
- Potencia efectiva irradiana
- Distancia a enviar
![[Pasted image 20240119102407.png]]

### Bateria y alimentacion
![[Pasted image 20240119102419.png]]
- Resistencia interna baja para soportar el transistor del trasreceptor
- Descarga natural critica per regular linealidades
- Condesadores con bajo ESR
![[Pasted image 20240119102424.png]]



### Interfaz del Sensor
- *Relacionada con el tipo de aplicación:* Presión, humedad, temperatura, proximidad, movimiento, tensión, bioquímicos, luz...
- *Sensor alimentado solo durante la medición* (¿tiempo de estabilización?)
- Conversión AD interna al microcontrolador general (modo de ahorro de energía)
- Amplificadores operacionales:
	- *Alimentados solo durante la medición*
	- Consumo ultra bajo de corriente rail to rail (~10 μA)
- ¿Futuro?
	- SoC (System on Chip)

#### Ventajas de SoC
- Dimensiones mínimas
- Optimización de recursos
- Configurabilidad
	- Microcontroladores que integran A/D y circuitos programables analógicos (PSoC de Cypress)

### Microcontrolador
- El consumo medio de corriente determina la duración de las baterías
- Modo RUN solo cuando sea necesario
- Modo de reposo y mecanismos de despertar
- ¿Cuántas instrucciones se ejecutan en un cierto tiempo? ¡Velocidad, Arquitectura!
- Sistemas de reloj y tiempos de inicio


#### Ventajas del Estándar COORDINATOR (ZigBee 802.15.4)
- Múltiples arquitecturas de red:
  1. Estrella
  2. Peer to Peer
  3. Árbol
- *Nodos de diferente complejidad:*
	- *Nodos de alta funcionalidad(FFD):* Mayor potencia y memoria, pueden actuar como coordinadores o routing nodes en la red (37KB) → ¿ZigBee? ¡También Router!
	- *Nodos de baja funcionalidad (RFD):* Menos potencia de procesamiento y memoria. No implementa todas las funciones (18KB), dispositivo esclavo, puede comunicarse solo con FFD. Normalmente actuan como sensores o actuares en la red




## Eleccion de tecnologia
### Componentes y arquitectura
- El Consumo de Energía de Componentes Siempre Encendidos Puede Contribuir de Manera Significativa al Consumo Total
- La Interfaz del Sensor y la Duración de la Batería Son Críticas para el Funcionamiento Óptimo de los Sensores Inalámbricos
- La Velocidad de Transmisión y la Cobertura Varían Entre Diferentes Categorías de Redes Inalámbricas
![[Pasted image 20240119101746.png]]
### Tecnologias actuales
![[Pasted image 20240119195507.png]]

### Teconologia 2.4GHz
- ISM libre en todo el mundo
- Permite soluciones
- Mayor espacio en canales
![[Pasted image 20240119101939.png]]



### Interferencia con otras fuentes de radio frecuencia

Tecnologia en las cuales se puede hablar en el mismo espacio y estrategias usadas:
![[Pasted image 20240119102226.png]]
En el caso de estar ocupado el espacio, las tecnologias y estrategias usadas son:
![[Pasted image 20240119102252.png]]








## IEEE 1451

El estándar IEEE 1451 Standard for Smart Transducer Interface for Sensor and Actuators *intenta establecer una serie de interfaces comunes para conectar entre los sensores con dispositivos microprocesadores*, además de definir el prototipo de un **smart sensor**(sensor inteligente) independientemente de la red en la que se encuentre.

## Smart Sensor (IEEE 1451.2)
**Un transductor que integra las funciones necesarias para la correcta representación de la magnitud medida o controlada. Estas funciones suelen ser capaces de simplificar la integración del transductor en aplicaciones que utilizan estructuras de red.**
En el estándar se describe cómo debe ser el nodo del sensor. Se prevé incluir información sobre el propio sensor dentro del sensor. 
### Modelo general de un Smart Sensor
![[Pasted image 20240119112730.png]]


### TEDS(Transducer Electronic Data Sheet)
TEDS (Transducer Electronic Data Sheet) es de particular interés, ya que permite *almacenar información que permite la identificación del dispositivo*. El standar IEEE 1451.2 prevee de hecho un set de informacion que permiten la identificacion de cada dispositivo mediante el TEDS 
*Conociendo esta información almacenada dentro del mismo sensor, la sustitución de un sensor antiguo por uno que mida el mismo fenómeno físico es sencilla*. 
- El sistema continúa funcionando gracias a la hoja de datos electrónicos almacenada en el sensor. Siempre hay una parte de memoria que permite almacenar esta información incluso si el sensor es analógico. El sistema reconoce automáticamente el sensor sin necesidad de reprogramar el sistema, convirtiéndolo en plug and play. Si cambio el sensor, todo funcionará porque el sistema interroga al sensor inteligente y este responde con la hoja de datos electrónicos, donde se almacena el modelo, fabricante, rango de medida, sensibilidad, etc.
#### Informaciones que TEDS prevé son:
- *Identificación* (*Número de modelo*, ID de fabricación, etc.)
- *Dispositivo* (*Tipo de sensor*, rango de medida, sensibilidad, unidad de medida)
- *Calibración* (Fecha de la última calibración, factores de corrección)
- *Aplicación* (Canal utilizado, coordenadas de la medida)
- *Algoritmos de aplicación*
### Consideraciones Generales
- *El módulo "Algoritmos de aplicación" incluirá algoritmos específicos para la aplicación en cuestión*
- Tambien contempla rutinas que permitan, entre otras cosas, actividades de autodiagnóstico para determinar el estado de funcionamiento del dispositivo. 
- *Al igual, incluye algoritmos que identifican las medidas a lo largo del tiempo* (mediante un sello temporal interno o en referencia a una señal de sincronización externa) *y permiten la localización en el espacio* (implementando sistemas de detección de posición GPS). 
	- En las redes de sensores y, en particular, en las redes de sensores inalámbricos, la referencia temporal es muy importante para extraer correctamente la información de los datos adquiridos.
- Técnicas de sincronización de los relojes internos de los sensores son necesarias para mejorar la coherencia entre los datos.

## Standar IEEE1451
### Blocchi Funzionali
La familia de estándares IEEE 1451 divide las partes de un sistema en dos categorías generales de dispositivos: Los NCAP (Network Capable Application Processor) y los TIM (Transducer Interface Modules).
![[Pasted image 20240119112756.png|400]]
- *El NCAP es un dispositivo basado en microcontrolador* y equipado con dos interfaces: *actúa como puente entre la red y los TIM*.
- *El TIM es el módulo que contiene los sensores y actuadores*, implementa funciones básicas, *el protocolo de comunicación hacia el NCAP es proporcionado por el TEDS* (Transducer Electronic Data Sheet).
### Desarrollo
![[Pasted image 20240119112816.png|400]]

- El estándar IEEE P1451.001 define los algoritmos de procesamiento de señales y la estructura de datos con la intención de comunicar la información en un sistema de instrumentación.
- Estos algoritmos se basan en el tipo de señal y el tipo de transductor conectado al sistema.


#### Desarrolo computacional y estacion de informacion
![[Pasted image 20240119112925.png]]
#### Algoritmo Real time segmentation and labeling(NCAP)
*Se utiliza para particionar y etiquetar en tiempo real la información proveniente de múltiples sensores en el bloque NCAP. Permite procesar y ordenar los datos antes de transmitirlos a la red*.
#### Algoritmo MCT(TIM)
- Funciona filtrando ruido y conservando sólo los puntos clave donde la señal varía significativamente. Se usa en los TIMs antes de enviar el dato al NCAP, para ahorrar en envios de datos
- Es una decimación que conserva solo los puntos fundamentales donde la señal varía. 
- Si la señal es constante y el ruido superpuesto siempre está contenido en el rango de error, descarto los puntos. 
- Extracción de la información solo donde la señal tiene la información y no debo perder puntos fundamentales. Una especie de filtrado de ruido.
- También debo almacenar el tiempo porque ya no es un muestreo uniforme. En la definición del ESTÁNDAR se eligió el que da el error más bajo.
![[Pasted image 20240119112837.png]]
##### Fase 1: Segmentacion
- Se divide la señal en segmentos basados en los puntos donde ocurre una variacion significativa
	- Estos puntos son donde la derivada excede cierto umbral
	- Los segmentos entre dos puntos sucesivos corresponde a zonas donde la señal es relativamente constante.

##### Fase 2: Etiquetado
- Cada segmento se etiqueta con informacion relevante para caracterizarlo
	- Dark:
	- Class
	- Temp

#### Algoritmos de Sincronización(TIMs)
Estos algoritmos permiten sincronizar los relojes internos de los diversos TIMs para tener una base temporal comun
- Uso de un módulo GPS -> costo mayor. Puede tomar incluso 10 s para tener la señal GPS o encender ese nodo, por lo que no siempre podemos usarlo. Si el sistema está alimentado desde la red, no hay problemas de consumo, al igual que un teléfono móvil que siempre se puede recargar. Si, en cambio, tenemos un nodo sensor, utilizar un nodo GPS no siempre es conveniente.
- TPSN (Time-Period Synchronization Network)
	- Más simple y ampliamente utilizado.


# Claude

## Estándar IEEE 1451 para Sensores Inteligentes

- Busca establecer interfaces comunes para conectar sensores con dispositivos de procesamiento. 

- Define sensores inteligentes para simplificar su integración en redes.

## Características

- Incluye información del sensor en el propio sensor (TEDS).

- Permite identificación, modelo, calibración, rango, etc. 

- Facilita el reemplazo de sensores, reconocimiento automático.

- Incluye algoritmos de aplicación, diagnóstico, sincronización temporal.

## Consideraciones

- La sincronización temporal es clave en redes de sensores para coherencia de datos. 

- IEEE 1451 busca estandarizar interfaces para integrar fácilmente sensores inteligentes en redes.

- La información TEDS en el sensor permite plug-and-play y cambio sin reprogramar.

 Aquí un resumen sobre los bloques funcionales y algoritmos relevantes del estándar IEEE 1451 para sensores inteligentes:



## Bloques Funcionales 

- NCAP: Procesador con interfaz de red y sensores/actuadores. Puente entre red y TIMs.

- TIM: Módulo con sensores/actuadores. Implementa funciones básicas y TEDS. 

## Algoritmos 

- Procesamiento de señales y estructuras de datos definidos.

- Algoritmo MCT para decimación conservando puntos clave. Filtrado de ruido.

## Sincronización Temporal

- Módulo GPS tiene costo y consumo elevados.

- TPSN es un algoritmo simple y ampliamente usado para sincronización. 

 El "Edge Sensor Signal Processing Algorithms for Earthquake Early Detection" se refiere a algoritmos de procesamiento de señales de sensores en el borde de la red (edge) para la detección temprana de terremotos. 

Algunos puntos clave:

- Procesamiento en el borde (edge) significa que los algoritmos se ejecutan en los nodos sensores o cerca de la fuente de datos, no en la nube.

- Permite una detección más rápida al evitar latencias de comunicación.

- Los sensores pueden ser acelerómetros que detectan vibraciones sísmicas.

- Los algoritmos analizan las señales en tiempo real para identificar patrones indicadores de un posible terremoto. 

- Por ejemplo, pueden medir amplitudes o frecuencias específicas de vibración y compararlas con umbrales.

- Si se detecta un evento sísmico, se puede activar rápidamente una alerta temprana antes de que llegue la onda principal.

- El procesamiento en el borde reduce el volumen de datos a transmitir y la latencia.

En resumen, son algoritmos que se ejecutan en nodos sensores para detectar terremotos a partir de señales sísmicas y activar alertas tempranas de forma más rápida y eficiente.





# Italiano
## Introduzione
- È importante considerare se è meglio elaborare i dati sul bordo o inviare campioni grezzi. L'elaborazione consuma energia, ma pesa generalmente meno della trasmissione, quindi è più efficiente inviare meno dati.
- I sensori hanno orologi interni propri, quindi è necessario sincronizzare i dati su un tempo comune. Algoritmi di sincronizzazione possono essere utilizzati, come con il GPS, o nel cablaggio sincronizzato a un orologio di riferimento.
	- Il GPS funge da riferimento di tempo preciso per i telefoni cellulari. Il GPS è una comunicazione unidirezionale.
- Il protocollo PLC consente di trasmettere energia e dati attraverso lo stesso cavo elettrico. Altri protocolli sono MBUS, NFC, WiFi, Bluetooth, LTE, GSM, ANT.
- I telefoni cellulari sono nodi sensori con accelerometro, sensori di temperatura, luce, ecc.

### BANDA ISM

**BANDA ISM (Industrial and Medical Band):** Queste sono le bande libere fissate per scopi industriali, scientifici e medici.

### Coesistenza di Standard nella Stessa Banda
- Molti standard possono coesistere nella stessa banda utilizzando la codifica ortogonale dei segnali. Codificando i segnali in modo ortogonale, è possibile trasmettere più segnali contemporaneamente e decodificarli anche in presenza di rumore.
- Anche se sono ortogonali, aggiungendo più segnali si introduce sempre del rumore. Si sfruttano i canali ortogonali disponibili.
- Il Bluetooth salta su un altro canale se rileva molto rumore o traffico. Questo è noto come "Frequency hopping" e aumenta la sicurezza frammentando i pacchetti.
- La sequenza di salto di canale è conosciuta solo da mittente e destinatario, viene comunicata all'inizio e salta in modo casuale. Consente di coesistere con altri standard che utilizzano la stessa banda.
**Situazione a 2,4 GHz**


## Harvesting dell'Energia #tarjeta-anki 
La raccolta di energia utilizza fonti non convenzionali per alimentare i circuiti come i sensori, in questo caso è conveniente poiché questi sensori operano in modo autonomo, senza cavi di alimentazione.
- L'energia viene convertita in elettricità e immagazzinata in una cella di stoccaggio resistente come un condensatore, un supercondensatore o una cella di microenergia (MEC), che è una forma di batteria a stato solido al litio.
- Il sistema include generalmente circuiti per gestire l'alimentazione e proteggere il dispositivo di archiviazione e altri circuiti.
**Fonti di Energia:**
- **Luce solare:** catturata da celle fotovoltaiche.
- **Magnetismo.**
- **Vibrazione (piezo):** catturata da un elemento piezoelettrico.
- **Differenziali di temperatura:** catturati da un generatore termoeléctrico.
- **Energia radio (RF).**
- **Energia prodotta biochimicamente:** ad esempio, cellule che estraggono energia dallo zucchero nel sangue.
### Tecnologie Specifiche:
- **Radiofrequenza (RFID):** Onda radio che raggiunge il chip, assorbe energia, carica un condensatore e trasferisce il contenuto della memoria del chip (il suo codice). Lettura wireless RFID illuminando il dispositivo passivo con un'antenna.
- **Termoelétrica:** utilizzando una cella di Peltier, dove la differenza di temperatura fornisce energia elettrica. Ad esempio, fornire freddo al frigorifero ed espellere il calore.
^1706458227481


### Celle di Peltier #tarjeta-anki 
#### Effetto Seebeck e Effetto Peltier
- **Effetto Seebeck:** In un circuito di conduttori metallici o semiconduttori, una differenza di temperatura genera una differenza di potenziale elettrico.
- **Effetto Peltier:** Quando scorre una corrente tra due metalli/semiconduttori diversi a contatto, si verifica un trasferimento di calore.
#### Cellula di Peltier
- Dispositivo termoelettrico formato da giunzioni di effetto Peltier in serie.
- Funziona come una pompa di calore a stato solido.
- Assorbe calore su una superficie e lo emette sull'altra in base alla direzione della corrente applicata.
- Permette di raffreddare o riscaldare a seconda dell'inversione della corrente.
- Esistono isolate (migliore resa) o non isolate con materiale ceramico.
- Insieme all'effetto Seebeck sono applicazioni di sistemi termoelettrici.
^1706458227487



## Rete di Sensori Wireless
Le reti wireless di sensori sono composte da nodi che comunicano senza fili attraverso mezzi come la radiofrequenza, l'infrarosso o ottico.

### Caratteristiche di rete di sensori wireless #tarjeta-anki 
- Mobilità dei Nodi
- Trasmissione mediante diffusione nel mezzo radio
- Basso costo e risorse energetiche limitate
- Alta percentuale di errori rispetto al cablaggio
^1706458227493


### Portata di Trasmissione Rete di sensori wireless #tarjeta-anki 
La portata di trasmissione dipende da:
- Rapporto segnale-rumore: deve essere al di sopra di una certa soglia
- Potenza di trasmissione
- Tipo di antenna
- Condizioni di propagazione
- Velocità di trasmissione
- Condizioni meteorologiche
^1706458227508

### Comunicazione tra Nodi #tarjeta-anki 
La comunicazione tra due nodi senza fili può essere:
- Unidirezionale: solo un nodo entro la portata dell'altro
- Bidirezionale: entrambi i nodi entro la portata reciproca
^1706458227513

### Copertura e Mobilità 
Esistono diversi tipi di reti wireless e le loro caratteristiche in termini di copertura e mobilità:
- Reti Satellitari: Copertura globale, alta mobilità poiché i satelliti coprono vaste aree.
- Reti Cellulari: Copertura regionale/nazionale, mobilità media-alta all'interno dell'area di copertura della rete cellulare. Consentono il movimento ma all'interno di una regione.
- Reti Locali (WLAN): Copertura locale, bassa mobilità poiché coprono aree ridotte come un edificio. Consentono il movimento all'interno di una stanza o di un edificio.
- Reti Personali (WPAN): Copertura personale, mobilità molto bassa, coprono distanze brevi intorno a una persona. Usate per collegare dispositivi personali.
- Reti di Sensori: Copertura variabile, da bassa a media mobilità. Possono essere dispiegate in aree estese ma i singoli nodi hanno portata limitata.
- Reti Fisse (Cablate): Copertura specifica, senza mobilità poiché richiedono infrastrutture cablate fisse.

### Parametri di una Rete di Sensori Wireless:
- Numero di Nodi
- Densità Spaziale dei Nodi nella Rete
- Il Nodo Sensore è Soggetto a Guasti/Non Trasmissione
- La Topologia della Rete Può Cambiare Rapidamente
- Energia Limitata e Bassa Capacità Computazionale


## Architetture di reti #tarjeta-anki 
Ci sono due tipi principali di architetture:
### Reti con Infrastruttura Fissa:
**Tutti i Nodi Comunicano con un Punto di Accesso Fisso**
- Esempi: Reti Cellulari e Alcune Reti Locali (WLAN)
### Reti Ad Hoc (Senza Infrastruttura Fissa)
**I nodi possono comunicare direttamente tra loro** senza infrastruttura fissa. Si creano spontaneamente tra nodi nella stessa area. Sono sistemi distribuiti dove la topologia può cambiare rapidamente.
- Esempi: Alcune Reti Locali, Reti Radio a Corto Raggio, Reti di Sensori
#### Comunicazione diretta tra nodi
- Due nodi comunicano direttamente se sono entro la portata wireless l'uno dell'altro.
- Non richiede altri nodi intermedi.
- Limitata dalla portata di trasmissione di ciascun nodo.
#### Comunicazione Multihop:
- Consente la comunicazione tra nodi al di fuori della portata diretta.
- I pacchetti saltano attraverso diversi nodi intermedi fino a raggiungere la destinazione.
- Richiede instradamento e cooperazione dei nodi intermedi.
- Estende la portata effettiva oltre la portata diretta.
- **Riduzione della Potenza Necessaria per la Comunicazione tra i Nodi A e B**
^1706458227519



#### Caratteristiche delle Reti Ad Hoc:
- Facile e Veloce da Creare
- Costi Ridotti
- Diverse Applicazioni:
  - Comunicazioni Personali: Telefoni, Laptop
  - Ambienti di Lavoro Cooperativi: Reti di Taxi, Sale Riunioni
  - Operazioni di Emergenza
  - Ambienti Militari
- Copertura Limitata
- Sistema Distribuito
- Difficoltà nella Gestione della Rete
- Difficoltà nel Mantenere la Comunicazione con Elevata Mobilità dei Nodi
- Costi di Manutenzione e Operativi Più Alti

## Tipi di Reti Wireless #tarjeta-anki 
### Reti Satellitari:
- Utilizzate per Radiodiffusione, Televisione e GPS
![[Pasted image 20240119101218.png]]
### Reti Cellulari
#### Problema del Trasferimento di Segnale (Handover):
- Passaggio da un Punto di Accesso a un Altro
- Le Frequenze Non Sono Illimitate
- Riutilizzo delle Bande su Antenne Distanti
#### Architettura della Rete Cellulare
![[Pasted image 20240119101305.png]]
### Reti Locali (WLAN - Reti di Area Locale Wireless):
- **Standard Dominanti:** IEEE 802.11 (WiFi), Hiperlan
- **Canale Radio (RF)**
- **Con Infrastruttura o Ad Hoc**
- In Passato Non Fornivano Servizio di Qualità (Servizio Dati)
- **Ethernet Wireless:** Alte Velocità di Trasmissione
### Reti Personali (WPAN - Reti di Area Personale Wireless):
- **Standard Dominante:** Bluetooth (IEEE 802.15)
- **Canale Radio (RF)**
- **Ad Hoc**
- Servizi Vocali e Dati
- Velocità di Trasmissione Inferiori Rispetto alle Reti Locali Wireless
### Reti di Sensori:
- **Mezzi di Trasmissione:** Infrarosso, RF, Ottico
- **Ad Hoc**
- Molti Nodi che Inviando Informazioni a un Nodo Gateway tramite Salti Multipli
- Dispositivi Molto Semplici
- Basse Velocità di Trasmissione (1-100 kb/s)
- Nessuno Standard Dominante
^1706458227524


## Parti Fondamentali di un Sensore Wireless: #tarjeta-anki 
- **Il Microcontrollore che Implementa lo Standard di Comunicazione**
- Interfaccia del Sensore
- Memoria
- Gestione dell'Energia e Durata della Batteria
- Modulo Radio e Batteria
### Scelta dell'Antenna
- In Base all'Efficienza
- Guadagno
- Potenza Irraggiata Efficace
- Distanza da Coprire
### Batteria e Alimentazione
- Bassa Resistenza Interna per Supportare il Transistor del Trasmettitore-Ricevitore
- Scarica Naturale Critica per Regolare Linearità
- Condensatori con Basso ESR
### Interfaccia del Sensore
- Collegata al Tipo di Applicazione: Pressione, Umidità, Temperatura, Prossimità, Movimento, Tensione, Biochimici, Luce...
- Sensore alimentato solo durante la misurazione (Tempo di Stabilizzazione?)
- Conversione AD interna al microcontrollore generale (Modalità Risparmio Energetico)
- Amplificatori Operazionali:
  - Alimentati solo durante la misurazione
  - Consumo ultra basso di corrente rail to rail (~10 μA)
### Microcontrollore
- Il Consumo Medio di Corrente Determina la Durata delle Batterie
- Modalità RUN solo quando necessario
- Modalità di Riposo e Meccanismi di Svegliare
- Quante Istruzioni si Eseguono in un Cert
 Tempo? Velocità, Architettura!
- Sistemi di Orologi e Tempi di Avvio
^1706458227530



### Vantaggi dello Standard COORDINATOR (ZigBee 802.15.4)
- Multiple Architetture di Rete:
  1. Stella
  2. Master/slave
  3. Peer to Peer
  4. Albero
- Nodi di Diverse Complessità:
  - FFD: può essere coordinatore PAN, tutte le funzioni implementate (37KB) → ZigBee? Anche Router!
  - RFD: non implementa tutte le funzioni (18KB), dispositivo schiavo, può comunicare solo con FFD



## IEEE 1451
### Introduzione  #tarjeta-anki 
Lo standard IEEE 1451 Standard for Smart Transducer Interface for Sensor and Actuators cerca di stabilire una serie di interfacce comuni per collegare i sensori a dispositivi microprocessori, oltre a definire il prototipo di un **smart sensor** (sensore intelligente) indipendentemente dalla rete in cui si trova.
^1706458227535



### Smart Sensor (IEEE 1451.2)  #tarjeta-anki 
**Un trasduttore che integra le funzioni necessarie per la corretta rappresentazione della grandezza misurata o controllata. Queste funzioni sono spesso in grado di semplificare l'integrazione del trasduttore in applicazioni che utilizzano strutture di rete.**
Nello standard viene descritto come dovrebbe essere il nodo del sensore. Si prevede di includere informazioni sul sensore stesso all'interno del sensore.
#### Modello generale di uno Smart Sensor
![[Pasted image 20240119112730.png]]
^1706458227540


### TEDS(Transducer Electronic Data Sheet) #tarjeta-anki 
TEDS (Transducer Electronic Data Sheet) è di particolare interesse, poiché consente di memorizzare informazioni che permettono l'identificazione del dispositivo. Lo standard IEEE 1451.2 prevede infatti un set di informazioni che consentono l'identificazione di ogni dispositivo tramite il TEDS.
Conoscendo queste informazioni memorizzate all'interno dello stesso sensore, la sostituzione di un vecchio sensore con uno che misura lo stesso fenomeno fisico è semplice.
- Il sistema continua a funzionare grazie alla scheda dati elettronici memorizzata nel sensore. C'è sempre una parte di memoria che consente di memorizzare queste informazioni anche se il sensore è analogico. Il sistema riconosce automaticamente il sensore senza la necessità di riprogrammare il sistema, rendendolo plug and play. Se cambio il sensore, tutto funzionerà perché il sistema interroga il sensore intelligente e questo risponde con la scheda dati elettronici, dove sono memorizzati il modello, il produttore, la gamma di misurazione, la sensibilità, ecc.
#### Informazioni previste da TEDS sono:
- Identificazione (Numero di modello, ID del produttore, ecc.)
- Dispositivo (Tipo di sensore, gamma di misurazione, sensibilità, unità di misura)
- Calibrazione (Data dell'ultima calibrazione, fattori di correzione)
- Applicazione (Canale utilizzato, coordinate della misura)
- Algoritmi di applicazione
#### Considerazioni Generali
- Il modulo "Algoritmi di applicazione" includerà algoritmi specifici per l'applicazione in questione
- Contempla anche routine che consentono, tra le altre cose, attività di autodiagnosi per determinare lo stato operativo del dispositivo.
- Allo stesso modo, include algoritmi che identificano le misurazioni nel tempo (tramite un timestamp interno o in riferimento a un segnale di sincronizzazione esterna) e consentono la localizzazione nello spazio (implementando sistemi di rilevamento della posizione GPS).
	- Nelle reti di sensori e, in particolare, nelle reti di sensori wireless, il riferimento temporale è molto importante per estrarre correttamente le informazioni dai dati acquisiti.
- Tecniche di sincronizzazione degli orologi interni dei sensori sono necessarie per migliorare la coerenza tra i dati.
^1706458227544




### Blocchi Funzionali
La famiglia di standard IEEE 1451 divide le parti di un sistema in due categorie generali di dispositivi: i NCAP (Network Capable Application Processor) e i TIM (Transducer Interface Modules).
![[Pasted image 20240119112816.png]]
- Il NCAP è un dispositivo basato su microcontrollore e dotato di due interfacce: funge da ponte tra la rete e i TIM.
- Il TIM è il modulo che contiene i sensori e gli attuatori, implementa funzioni di base, il protocollo di comunicazione verso il NCAP e fornisce il TEDS (Transducer Electronic Data Sheet).


### Sviluppo
- Lo standard IEEE P1451.001 definisce gli algoritmi di elaborazione del segnale e la struttura dei dati con l'intenzione di comunicare le informazioni in un sistema di strumentazione.
- Questi algoritmi si basano sul tipo di segnale e sul tipo di trasduttore collegato al sistema.

### Algoritmi #tarjeta-anki 
#### Algoritmo di segmentazione e etichettatura in tempo reale (NCAP)
*Viene utilizzato per partizionare ed etichettare in tempo reale le informazioni provenienti da sensori multipli nel blocco NCAP. Consente di elaborare e ordinare i dati prima di trasmetterli alla rete*.
#### Algoritmo MCT (TIM)
- Funziona filtrando il rumore e conservando solo i punti chiave dove il segnale varia significativamente. Viene utilizzato nei TIM prima di inviare i dati al NCAP, per risparmiare nell'invio dei dati.
- È una decimazione che conserva solo i punti fondamentali dove il segnale varia.
- Se il segnale è costante e il rumore sovrapposto è sempre contenuto nell'intervallo di errore, scarto i punti.
- Estrazione delle informazioni solo dove il segnale ha le informazioni e non devo perdere punti fondamentali. Una sorta di filtraggio del rumore.
- Devo anche memorizzare il tempo perché non è più un campionamento uniforme. Nella definizione dello STANDARD è stata scelta quella che fornisce l'errore più basso.
![[Pasted image 20240119112837.png|300]]
##### Fase 1: Segmentazione
- Si divide il segnale in segmenti basati sui punti in cui avviene una variazione significativa
	- Questi punti sono dove la derivata supera una certa soglia
	- I segmenti tra due punti successivi corrispondono alle zone in cui il segnale è relativamente costante.
##### Fase 2: Etichettatura
- Ogni segmento viene etichettato con informazioni rilevanti per caratterizzarlo
	- Scuro:
	- Classe
	- Temperatura
#### Algoritmi di Sincronizzazione (TIMs)
Questi algoritmi permettono di sincronizzare gli orologi interni dei vari TIMs per avere una base temporale comune
- Uso di un modulo GPS -> costo maggiore. Può impiegare anche 10 s per ricevere il segnale GPS o accendere quel nodo, quindi non sempre possiamo usarlo. Se il sistema è alimentato dalla rete, non ci sono problemi di consumo, come un telefono cellulare che può essere sempre ricaricato. Se, invece, abbiamo un nodo sensore, utilizzare un nodo GPS non è sempre conveniente.
- TPSN (Time-Period Synchronization Network)
	- Più semplice e ampiamente utilizzato.
^1706458227549
