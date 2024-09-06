---
cards-deck: Profesional::Universidad::UNISA::Sistemi di interfaccia::CANBUS
---

## Introduccion

El protocolo CAN (Controller Area Network) es un protocolo de comunicación digital serial de tipo broadcast. Permite el control distribuido en tiempo real con un alto nivel de seguridad. El BUS está definido en el documento ISO 11898.

- **Parte 1:** Especifica el protocolo CAN.
- **Parte 2:** Especifica el nivel físico de alta velocidad no tolerante a fallas.
- **Parte 3:** Especifica el nivel físico de baja velocidad tolerante a fallas.
- **Parte 4:** Trata sobre la comunicación TTCAN (time-triggered).

### Ventajas del protocolo CAN: #tarjeta-anki 
1. **Tiempos de respuesta rigurosos:** La tecnología CAN cuenta con hardware y software, así como sistemas de desarrollo para protocolos de alto nivel que permiten conectar muchos dispositivos y, al mismo tiempo, cumplir con estrictas restricciones temporales.
2. **Simplicidad y flexibilidad en el cableado:** CAN es un bus serial típicamente implementado en un par trenzado blindado o no. Los nodos tienen una dirección que los identifica, lo que permite agregar o quitar dispositivos sin tener que reorganizar el sistema o parte de él.
3. **Carga útil efectiva del mensaje:** 8 bytes.
4. **Alta inmunidad a interferencias:** El estándar ISO 11898 recomienda que los chips de interfaz puedan seguir comunicándose incluso en condiciones extremas, como la interrupción de uno de los dos cables o el cortocircuito de uno de ellos con tierra o con la alimentación.
5. **Alta confiabilidad:** La detección de errores y la solicitud de retransmisión se manejan directamente en el HARDWARE con 5 modos diferentes (2 a nivel de bit y 3 a nivel de mensaje). Tiene una gestión de errores cuidadosa directamente relacionada con la gestión eléctrica del bus. En tiempo real, gracias al transceptor, se puede determinar si hay un error en curso en la transmisión. No puede haber una colisión destructiva durante la transmisión, lo que significa que nunca se pierde una transmisión debido a una colisión.
6. **Confinamiento de errores:** Cada nodo puede detectar su propio mal funcionamiento y autoexcluirse del bus si este error persiste. Este es uno de los mecanismos que permiten a la tecnología CAN mantener la rigidez de las temporizaciones, imponiendo que un solo nodo colapse todo el sistema.
7. **Madurez del estándar:** La amplia difusión de este protocolo ha llevado a una amplia disponibilidad de chips transceptores de microcontroladores que integran puertos CAN, herramientas de desarrollo y una disminución significativa del costo de estos sistemas. Esto es muy importante y lo ha consolidado en el ámbito automotriz e industrial.
^1705482391074


- El bus CAN permite la comunicación entre dispositivos inteligentes, sensores y actuadores capaces de producir datos de manera autónoma para luego insertarlos en el medio de transmisión. El sensor inteligente alberga un módulo CAN para la comunicación en el bus.

![[Pasted image 20240104105457.png]]

## Principio de comunicacion
- Solo cuenta con 2 cables diferenciales o de modo comun apantallados
### Comunicacion Broadcast
![[Pasted image 20240104105522.png]]

- Cada estación de la red CAN puede escuchar los frames enviados por la entidad transmisora (→ BUS PARTY LINE). 
- Después de recibir el frame, cada nodo decide si aceptar o no el mensaje.
- El ACCEPTANCE FILTERING debe implementarse en cada nodo.
- El filtrado de aceptación es hardware, se implementa en el transceptor y es programable y confiable. Lo programo y le digo la máscara, esta es un filtro que se impone en una parte de los bits. Si el mensaje es aceptado, llega a nivel de aplicación, de lo contrario, no. Sirve para acelerar el funcionamiento y la velocidad del bus.

### Comunicacion con accesso multiple al bus
**BUS party line:** Todos escuchan y todos escriben. No hay comunicación punto a punto.
- Se permite el accesso simultane al bus por varios nodos
	- Para estos casos se recurre a un arbitraje del bus basado en bits y no destructivo
	- El metodo adoptado es Carrier Sense Multiple Access with Collision Detection an Arbitration on Message Priority
	- La prioridad esta codificada en el identificador CAN bus del nodo que trasmite

### Servicios de Comunicación

Existen dos servicios de comunicación en el protocolo CAN:

#### Write Object Service
El Write Object Service transmite un marco de datos de información (CAN Data Frame) desde un nodo productor a uno o más nodos receptores (consumidores). El servicio Write Object representa la comunicación ordinaria en el bus CAN. Todos escriben y leen, y si está destinado a mí, me activo. 
![[Pasted image 20240104105634.png]]
#### Read Object Service
El Read Object Service consiste en la solicitud de un mensaje específico. Es iniciado por uno o más consumidores con la transmisión en el BUS de un CAN Remote Frame. El nodo que posee la información solicitada la transmitirá con un Data Frame.
![[Pasted image 20240104105642.png]]


**Esquema de solicitud de transmisión remota**
![[Pasted image 20240104105727.png]]
## CAN BUS SEGÚN LA PILA ISO OSI
El protocolo CAN implementa solo el físico(Physical) y el enlace de datos(Data Link). La capa de aplicación se deja al diseñador, no es estándar y le corresponde al diseñador los detalles de la interfaz de los usuarios hacia el bus.
![[Pasted image 20240104184944.png]]
## Physical(BUS CAN)
### Physical Layer especificaciones #tarjeta-anki 
Según el estándar ISO 11898, el Nivel Físico debe especificar:
- El **medio de transmisión**.
- La **representación de bits y el nivel de la señal**.
![[Pasted image 20240104185351.png]]
#### Medio de Transmisión
En el bus CAN, se prevé un solo canal bidireccional que puede ser diferencial o de un solo extremo (poco utilizado). Se suele utilizar un par trenzado, apantallado o no, según el ruido (eléctrico y magnético) del entorno.
El par trenzado consta de dos líneas, H y L.
- Para representar el bit 0, ambas líneas permanecen a 2.5 V para que la diferencia de voltaje sea 0.
- El bit 1 se representa llevando la línea H a 3.5 V respecto a la tierra y la línea L a 1.5 V, por lo que la diferencia de potencial es de 2 V.
#### Codificación de Bits
El flujo de bits se codifica con el método NRZ, es decir, bits no separados. Los dos niveles utilizados en el bus se llaman dominante (d) o recesivo (r) en relación con la posibilidad de transmisión simultánea de un bit r y de un bit d. El valor que debe estar presente en el bus es d.
La correspondencia entre d y r, hace referencia a los niveles logicos en la linea, comunmente el bit dominante es 0 y el bit recesivo es 1, aunque esto depende del cableado.
![[Pasted image 20240104190613.png]]
- Este sistema permite que cuando dos nodos tramiten simultaneamente, se compara bit a bit los mensajes, estos mensajes se comienzan a trasmitir casi simultaneamente.
- Aqui se compara bit a bit los identificadores de ambos mensajes, si en un bit hay una colision entre recesivo y dominante, se genera un arbitraje que lo gana el que tenga identificado con bit dominante primero y puede continuar con su transmision intacta
- El otro nodo, al detectar un bit dominante cuando transmite un recesito, asume que perdio el arbitraje y se detiene
^1705482391084


### Physical Layer construccion #tarjeta-anki 
El Physical Layer del protocolo CAN se puede dividir en 3 subgrupos:
1. **Physical Signaling (PLS):** Se ocupa de la temporización y sincronización.
2. **Physical Medium Attachment (PMA):** Define la estructura de un nodo.
3. **Medium Dependent Interface (MDI):** Define algunas características eléctricas y físicas.
#### PLS (Physical Signaling)
^1705482391089

##### Sincronización de Bits

- Uso de Bit Stuffing. Durante la transmisión del mensaje, un máximo de 5 bits consecutivos puede tener la misma polaridad.
![[Pasted image 20240104192504.png]]
##### Temporización de Bits
Cada bit de transmisión se define como la sucesión de 4 segmentos temporalmente no superpuestos. 
- Cada segmento está compuesto por un número entero de Time Quantum. 
- El Time Quantum es la resolución temporal utilizada por cada nodo CAN 
- Su duración se genera mediante una división de frecuencia de la señal generada por el Oscilador local del CAN Controller.
- Cada bit puede estar compuesto por un mínimo de 8 y un máximo de 25 Time Quanta.
![[Pasted image 20240104192520.png]]

Los 4 segmentos en los que se divide el intervalo correspondiente a 1 bit son:

- **SYNC_SEG:** de duración fija igual a 1 Time Quantum, se utiliza para sincronizar los diferentes nodos.
- **PROP_SEG:** de duración programable de 1 a 8 Time Quanta para compensar los retrasos en la transmisión y recepción de bits a lo largo de la red.
- **PHASE_SEG1 y PHASE_SEG2:** se ajustan de manera que la transición entre ellos, en la cual los nodos leen el nivel del Bus (Punto de Muestreo), cumpla con los requisitos de todo el hardware conectado al bus. Phase_Seg1 puede durar de 1 a 8 Time Quanta, y Phase_Seg2 tiene la misma duración que Phase_Seg1.

![[Pasted image 20240104192530.png]]
La programabilidad del Punto de Muestreo permite optimizar la Temporización de Bits: un muestreo retrasado permite la máxima longitud del bus.

##### Retardo de propagacion
![[Pasted image 20240104192615.png]]

El retardo de propagación en la transmisión debe tener en cuenta 4 contribuciones:

1. **CAN Controller (de 50 a 62 ns)**
2. **Circuito optoelectrónico (de 50 a 62 ns)**
3. **Transceiver (de 120 a 250 ns)**
4. **Medio Trasmissivo (5 ns/m)**

Cada contribución debe considerarse dos veces porque, además de la sincronización en el primer bit, se debe tener en cuenta el retardo con el cual el transmisor se da cuenta de la sobreescritura del Acknowledgement Bit por parte de los nodos RX (dimensionamiento sobre el nodo más lejano):

$$ t_{\text{propagación}} = 2 \times (t_{\text{cable}(L)} + t_{\text{controller}} + t_{\text{optocoupler}} + t_{\text{transceiver}}) < \text{PROP\_SEG} $$

##### Velocidad de Transmisión
![[Pasted image 20240104192817.png]]

Para cumplir con la relación anterior, se obtiene el siguiente diagrama. Una tasa de datos de 1 Mbit/s se puede lograr con un cable de hasta 10 m. La longitud máxima (para cumplir con el Estándar ISO 11898) es de 1 km (con una transmisión de 50 kbit/s).

#### PMA (Physical Medium Attachment) y MDI (Medium Dependent Interface)

El **Physical Medium Attachment (PMA)** define la estructura de un nodo CAN y cómo está conectado al bus. Se distinguen 3 partes principales:

1. **Transceptor (Transceiver):** Detecta el estado del bus evaluando la diferencia de voltaje entre las líneas CAN_H y CAN_L.

2. **Controlador CAN (CAN Controller):** Transmite y recibe datos seriales entre el microprocesador y el bus (y viceversa).

3. **Microcontrolador (Microcontroller):** Es el corazón del nodo CAN y gestiona todas las operaciones que la periferia debe realizar.

El **Medium Dependent Interface (MDI)** define las características eléctricas y físicas estandarizadas que deben tener:

- **Cable del Bus:** En términos de medio de transmisión, impedancia terminadora (120 Ω), retardo de línea, etc.
  
- **Conector:** Conecta el nodo (transceptor) al bus.








## Data link Layer(Protocolo CAN) #tarjeta-anki 
El Data Link Layer del protocolo CAN se implementa a través de 2 niveles:
### Object Layer
Este nivel se encarga de:
- **Filtrar los mensajes.**
- **Interpretar los mensajes.**
![[Pasted image 20240105094502.png]]
- El filtrado de mensajes se realiza mediante el uso de un Acceptance Filter que descarta los mensajes no relevantes para ese nodo.
- Además, se encarga de gestionar los mensajes que deben transmitirse y establecer la interfaz con la capa de aplicación.
### Transfer Layer
Este nivel define:
- El formato de los mensajes(formato dei Frame).
- La gestión de errores.
- El arbitraje.
^1705482391096


#### Arbitraje del Bus #tarjeta-anki 
El protocolo CAN permite el acceso simultáneo al bus por parte de múltiples nodos, y utiliza **un arbitraje basado en bits y de tipo no destructivo**. El método adoptado es el **Carrier Sense Multiple Access with Collision Detection and Arbitration on Message Priority** (CSMA/CD + AMP).
- La prioridad del mensaje está codificada en el identificador CAN del nodo que está transmitiendo.
- Si dos o más nodos comienzan la transmisión al mismo tiempo, la colisión se evita mediante el acceso al bus de tipo CSMA/CD + AMP.
Cada nodo TX compara el nivel del bit transmitido con el nivel monitoreado en el canal:
- Si los dos bits coinciden, el nodo continúa la transmisión.
- Si el nivel asociado al bit es recessivo y el nivel del canal es dominante, la unidad interrumpe inmediatamente la transmisión y se coloca en escucha (transmisión de bits recessivos).
##### Ejemplo:
- En el bit 5, los nodos 1 y 3 envían un bit dominante mientras que el nodo 2 envía un bit recessivo.
- El nodo 2 pierde el arbitraje y se coloca en escucha del canal.
- En el bit 2, el nodo 1 pierde el arbitraje a favor del nodo 3.
- El identificador del mensaje del nodo 3 tiene una codificación binaria inferior y, por lo tanto, una mayor prioridad (en comparación con los nodos 1 y 2), por lo que gana el arbitraje y continúa la transmisión sin pérdida de tiempo asociada a una retransmisión.
![[Pasted image 20240105094749.png]]
^1705482391101


#### Formato de la frame #tarjeta-anki 
En el protocollo CAN existen 5 estructuras de mensajes:
![[Pasted image 20240105100103.png|300]]
- **Data Frame:** mensaje ordinario que se utiliza para la transmisión de datos desde un nodo transmisor (TX) a todos los demás que actúan como receptores (RX).
- **Remote Frame:** La estructura del Remote Frame es similar al Data Frame, pero carece del campo de datos. Se utiliza para solicitar el envío de un Data Frame específico por parte del nodo interrogado.
- **Error Frame:** Un nodo envía un Error Frame para revelar un error y provocar la retransmisión del mensaje por parte del nodo transmisor.
- **Overload Frame**: Un nodo envía un Overload Frame cuando está ocupado para retrasar la siguiente transmisión.
- **Interframe Space:** Precede a cada Data Frame y Remote Frame y actúa como función separadora.
##### Data Frame
Il Data Frame é constituido de 7 campos:
![[Pasted image 20240105100226.png]]
- **Start of Frame (SoF):** 1 bit dominante para la sincronización de los nodos en el bus.
- **Arbitration Field:** Formado por el identificador del contenido del mensaje y un bit RTR (Remote Transmission Request). Puede ser de 12 o 32 bits.
	- *RTR:* Distingue entre Data Frame y Remote Frame. Dominante en Data Frame y recesivo en Remote Frame.
	- El *identificador* es de 11 bits en el protocolo CAN 2.0A (Standard CAN) y de 29 bits en el CAN 2.0B (Extended CAN).
![[Pasted image 20240105102507.png|400]]
- **Control Field:** Especifica principalmente el número de bytes de datos en el mensaje (carga útil).
	- *Incluye el bit IDE* (Identifier Extension, dominante para Standard Frame y recesivo para Extended Frame, privilegiando el primero en caso de colisión).
	- 1 o 2 bits reservados (r0, r1).
	- Un campo de 4 bits *DLC* (Data Length Code) que define el número de bytes de datos (Data Byte Length).
![[Pasted image 20240105102348.png|400]]
- **Data Field:** Contiene los datos reales, que van desde un máximo de 8 bytes (64 bits) hasta un mínimo de 0 según el DLC. Los bytes se envían de más significativo a menos.
- **CRC Field:** Formado por 16 bits, de los cuales los primeros 15 contienen la secuencia de control de error (cyclic redundancy check), y el último es un bit recesivo de delimitación (CRC Delimiter).
![[Pasted image 20240105102552.png]]
- **Acknowledge Field:** Compuesto por 2 bits ACK Slot y ACK Delimiter.
	- El nodo TX transmite ambos bits del campo como recesivos.
	- Un nodo RX que detecta un mensaje correcto sobrescribe el ACK Slot con un bit dominante.
	- El nodo TX, al detectar la confirmación positiva, reconoce que al menos un nodo ha recibido correctamente su mensaje.
![[Pasted image 20240105103945.png|400]]
- **End of Frame (EoF):** Secuencia de 7 bits recesivos. Si se interrumpe la secuencia de 7 bits recesivos, indica que hay un error.
![[Pasted image 20240105104014.png]]
##### Remote Frame
![[Pasted image 20240105104222.png]]
1. El Remote Frame es enviado por un nodo receptor que necesita un dato específico. El tipo de dato deseado se especifica mediante el Identifier en el campo Arbitration Field.
2. El nodo transmisor interesado responderá con un Data Frame que contiene la información solicitada en el campo Data Field.
La estructura del mensaje es muy similar a la de un Data Frame:
- No hay Data Field.
- El bit RTR (que distingue el Data Frame del Remote Frame) es recessivo en lugar de dominante. En el caso de Data Frame y Remote Frame con el mismo Identifier transmitidos simultáneamente, el Data Frame gana el arbitraje gracias al bit RTR dominante después del Identifier, asegurando que el nodo solicitante reciba la información de inmediato.
##### Interframe Space (Espacio entre Marcos)
![[Pasted image 20240105105234.png|400]]
El Interframe Space se utiliza para separar dos Data o Remote Frames, mientras que los Overload Frame o Error Frame pueden enviarse consecutivamente en el bus.
- **Intermission:** 3 bits recessivos que solo pueden ser interrumpidos por un Overload Frame. No se permite la interrupción por parte de un Data Frame o Remote Frame.
- **Bus Idle:** Una secuencia de bits recessivos de longitud no especificada que permanece hasta que hay un Start of Frame de un nuevo Data o Remote Frame. Esta secuencia se interpreta como una señal de bus libre, lo que permite que cualquier nodo inicie la transmisión cuando lo considere necesario.
- **Suspend Transmission:** Es una interpretación diferente de los 8 bits recessivos siguientes al Intermission por parte de un nodo en estado de error pasivo. Si un nodo experimenta frecuentes errores, debe esperar un tiempo igual a 8 bits antes de tomar posesión del bus para una nueva transmisión.
##### Overload Frame (Marco de Sobrecarga)
![[Pasted image 20240105182611.png]]
El Overload Frame consiste en dos partes:
- **OverLoad Flag:** Formado por 6 bits dominantes y puede sobrescribir un Interframe Space si interrumpe dentro del campo Intermission (primeros 3 bits). Si un bit dominante llega después de este período, se interpreta como el Start of Frame de un Data o Remote Frame.
- **OverLoad Delimiter:** Formado por 8 bits recessivos (el mismo formato que el campo Error Delimiter de un Error Frame).
Dado que es suficiente que un nodo envíe un Overload Frame para retrasar automáticamente la comunicación de todos los demás, el protocolo CAN establece un mecanismo de confinamiento para los nodos más lentos: no se pueden enviar más de 2 Overload Frame consecutivos por parte del mismo receptor.
##### Marco de Error (Error Frame)
El Error Frame es enviado por un nodo que detecta la presencia de un error en un Data o Remote Frame. Las principales causas por las cuales puede ocurrir un error de transmisión o recepción en el bus son las siguientes:
1. **Punto de muestreo divergente:** Cada nodo puede tener un punto de muestreo diferente y, debido a una interferencia, dos nodos pueden leer dos niveles lógicos diferentes.
2. **Umbral de reconocimiento divergente:** Dos nodos diferentes pueden tener diferentes umbrales para reconocer los niveles lógicos.
3. **Atenuación de la señal:** La señal a lo largo de la línea se atenúa, y en tramos largos, puede haber una degradación que genere un error en la lectura.
![[Pasted image 20240105110107.png]]
###### **Flag de Error (Error Flag)**
El Error Flag viola deliberadamente la regla de bit stuffing para que todas las estaciones detecten un error y envíen un Error Flag. Hay dos tipos de Error Flag:
- **Active Error Flag:** 6 bits dominantes (cuando el sistema de confinamiento de fallas asigna al nodo un estado "Error Active").
- **Passive Error Flag:** 6 bits recesivos.
La transmisión simultánea de todos los Error Flags puede resultar en un máximo de 12 bits dominantes consecutivos. La transición de un bit recesivo se interpreta como el final de la transmisión de los Error Flags, y el primer bit recesivo se reconoce como Error Delimiter.
###### Error Delimiter
Contituito de 8 bit recessivos
##### Observaciones
- 6 bits dominantes durante una trama = Error Flag
- 6 bits dominantes en Intermission = Overload Flag
^1705482391106


#### Errores #tarjeta-anki 
El procedimiento de detección de errores y el subsiguiente aislamiento de fallas hacen que el protocolo CAN sea muy confiable.
##### Gestion de errores
La detección de errores se divide en 5 fases:
1. **Detección del Error:** El controlador CAN de un nodo detecta un error (en TX o RX).
2. **Transmisión Inmediata del Error Frame:** Se transmite inmediatamente un Error Frame.
3. **Ignorar el Mensaje Corrupto:** El mensaje corrupto es ignorado por todos los nodos de la red.
4. **Actualización del Estado del CAN Controller:** El CAN Controller actualiza su estado.
5. **Retransmisión del Mensaje:** El mensaje se vuelve a transmitir (puede tener que competir por el acceso al bus con otros mensajes).
##### Tipos de errores
El protocolo CAN define 5 tipos diferentes de errores (3 a nivel de bit y 2 a nivel de mensaje), detectados mediante las siguientes técnicas:
- **Bit Monitoring:** Cada nodo compara los bits que envía con los presentes en el bus. En caso de discrepancia, se produce un Bit Error (excepción: campo Identifier de un Data y Remote Frame utilizado para la arbitraje del bus).
- **Bit Stuffing:** Esta técnica implica transmitir, durante los Data y Remote Frames, un sexto bit complementario después de cada secuencia de 5 bits iguales. Si un receptor detecta 6 bits consecutivos del mismo tipo, se considera un Stuff Error.
- **Control de Redundancia Cíclica (CRC):** Cada nodo RX calcula la secuencia CRC del mensaje recibido y la compara con la que el TX ha adjuntado al mensaje. En caso de diferencia, se produce un CRC Error.
- **Control de Formato:** Si el receptor detecta que no se han respetado las 5 posibles estructuras de los frames CAN, se genera un Form Error.
- **Envío del bit ACKnowledgement:** Cada nodo que recibe correctamente un Data y Remote Frame está obligado a enviar un bit dominante en el bit-time del campo ACK de este frame. Si la sobrescritura no ocurre, el bit ACK-Slot permanece recesivo y el transmisor envía un mensaje de error. Solo se produce un Acknowledgement Error si ninguno de los otros nodos envía un bit dominante.
##### Gravedad
A cada uno de los 5 tipos de errores se le asigna una gravedad específica, que se cuantifica en un aumento de 1 a 8 en los 2 contadores presentes en cada nodo CAN.
- **Receive Error Counter (REC):** Registra los errores detectados por el nodo cuando está en modo receptor.
- **Transmit Error Counter (TEC):** Registra los errores en los mensajes que el nodo transmite, ya sea detectados por el nodo mismo o informados por otros nodos mediante un Error Frame.
##### Estados de error de un nodo
Según el valor de estos 2 contadores, cada nodo se coloca en uno de los 3 estados:
- **Error Active:** Si ambos contadores son inferiores a 128. La frecuencia y gravedad de los errores son despreciables, y el nodo puede participar normalmente en las actividades del bus, incluso enviando un Active Error Flag en caso de detección de errores.
- **Error Passive:** Si al menos 1 de los 2 contadores es mayor que 128. La frecuencia y gravedad de los errores hacen que el nodo sea considerado menos confiable. La señalización de errores solo puede realizarse con un Passive Error Flag (que no provoca automáticamente la retransmisión) y, para la transmisión, debe esperar un tiempo superior a los nodos activos (Intermission + Suspend Transmission). 
- **Bus Off:** Si 1 de los 2 contadores alcanza el valor 256. El nodo está gravemente sujeto a errores y no participa en las actividades del bus. Sin embargo, permanece atento para detectar una secuencia de 128 bits recesivos consecutivos que señala su readmisión.
![[Pasted image 20240105111209.png]]
^1705482391113
