


## **Introducción**
Un **protocolo de comunicación** es un sistema de reglas que permite que dos o más entidades (como computadoras, teléfonos celulares, etc.) de un sistema de comunicación se comuniquen entre sí para transmitir información mediante cualquier tipo de variación de una magnitud física. Estas reglas definen la sintaxis, semántica y sincronización de la comunicación, así como los posibles métodos de recuperación de errores. Los protocolos pueden ser implementados por hardware, software o una combinación de ambos

## **Características de un Protocolo de Comunicación**

1. **Integridad de los Datos**:
    - Garantía de que los datos lleguen correctamente y sin errores.
    - Mecanismos de retransmisión y corrección de errores.
2. **Orden de los Datos**:
    - Asegurar que los datos lleguen en el orden correcto.
    - Ventana deslizante y confirmaciones (ACK).
3. **Control de Flujo**:
    - Evitar saturación de la red.
    - Ajuste dinámico según el ancho de banda disponible.
4. **Control de Congestión**:
    - Evitar pérdida de paquetes en routers.
5. **Formato de los Datos**:
    - Definición clara de cómo se estructuran los mensajes.
6. **Seguridad y Autenticación**:
    - Protección contra accesos no autorizados.
    - Cifrado y autenticación.

## **Tipos de Protocolos de Comunicación**

1. **TCP/IP**:
    - Ampliamente utilizado en Internet.
    - Protocolo de capa de transporte.
2. **HTTP/HTTPS**:
    - Para transferencia de páginas web.
    - Basado en TCP/IP.
3. **SMTP/POP/IMAP**:
    - Para correo electrónico.
    - Protocolos de capa de aplicación.
4. **FTP/SFTP**:
    - Transferencia de archivos.
    - Seguridad en SFTP.
5. **Bluetooth**:
    - Comunicación inalámbrica entre dispositivos cercanos.
6. **Modbus**:
    - En automatización industrial.
    - Comunicación maestro-esclavo.


## Clasificaciones de tipos de comunicaciones
![[Pasted image 20230511085825.png|400]]

![[Pasted image 20230511085827.png|400]]

## Caracteristicas
### **Tipos de conexion:**
Hace referencia a la cantidad de receptores, multipunto es 1 trasmisor y multiples receptor, puede ser punto-punto o multipipunto
### **Tipo de trasmision:**

#### Serie o paralelo
##### Serie
Serie es cuando los bit de informacion son trasmitidos en decuencias por una unica linea, se utiliza para largas distancias y baja velocidad
- Se caracteriza por la trama regular de bits que pueden ser separados en un intervalo cualquiera de tiempo, este intervalo de lla bit-time y su inverso es el bit-rate
$$B=1/T$$
##### Paralela
- Paralela es cuando los bit son codificados simultaneamente sobre distintas lineas, se utiliza para distancias cortas a causa de que son muy caras


#### Sincrona e Asincrona
##### Sincrona
Se sincroniza la señal de clock, esto permite distinguir con mayor presicion bits sucesivos
- La duracion de cada bit es la misma y todos los caracteres son continuos, solo se debe localizar el primer bit de cada caracter, para esta sincronizacion se usa una sequenza tipica antes de cada trasmision

##### Asincrona
El tramisor sobre envia el dato pero el receptor debe conocer la velocidad de los datos enviados para evitar errores de sincronizacion
- No existe una relacion temporal entre un caracter y el sucesivo
- El destinatario debe establece la sincronizacion para cada catacter y tambien para el primer bit
- Al principio cada caracter tiene un bit de inicio, luego se espera medio ciclo para hacer la muestra, y al final del caracter viene trasmitido el bit de stop




#### Simplex, Half-Duplex o Full Duplex
**Simplex**: La trasmissione é sempre in un solo verso
**Half duplex:** La trasmisione é bidirezionale ma non conteporaneo nei due versi
**Full Duplex:** La trasmissione é bidirezionale e conteporanea nei due versi


### Tipos de codificaciones para la sincronizacion
#### Codificacion no return to zero(NRZ)
- En la codificación NRZ, un **cero binario** se representa mediante un **nivel constante de tensión** (sin transiciones), mientras que un **uno binario** se representa con un **cambio de nivel de tensión**.
- No hay retorno al nivel cero de tensión entre bits consecutivos de valor uno.
- Es simple pero no recomendable para largas distancias debido a niveles residuales de corriente continua y la posible falta de suficientes transiciones de señal para una recuperación confiable de la temporización
![[Pasted image 20231226172345.png]]
#### Codificacion **Return to Zero (RZ)**:
- En la codificación RZ, un **cero binario** se representa mediante un **cambio de nivel de tensión** en el punto medio del bit.
- Un **uno binario** también tiene una transición en el punto medio del bit, pero luego regresa al nivel cero.
- Proporciona sincronización y evita problemas de corriente continua, pero requiere más ancho de banda
![[Pasted image 20231226172348.png]]
#### Codificacion **Non Return to Zero Inverted (NRZI)**:
- En la codificación NRZI, un **cero binario** no produce transición (sin cambio de nivel de tensión), mientras que un **uno binario** envía una transición a nivel positivo o negativo.
- Utiliza cambios de fase para representar los bits.
- Se utiliza en algunos sistemas de transmisión de datos y es autosincronizante
- Con questo metodo si ha nel peggiore dei casi una transizione ogni bit
	- In media si ha un numero di transizione pari alla meta dei bit trasmessi
![[Pasted image 20231226172351.png]]


### Controles de error de trasmision

#### **Controllo di Ridondanza Orizzontale (Paridad)**:
- La **paridad** es un método simple de detección de errores.
- Se agrega un bit adicional (bit de paridad) al final de cada palabra de datos.
- El bit de paridad se establece para que el número total de unos en la palabra (incluido el bit de paridad) sea par o impar.
- Si hay un error en la transmisión y el número de unos cambia, se detecta la paridad incorrecta.
- Es común en sistemas antiguos y no es muy eficiente para detectar errores más complejos


#### **Controllo di Ridondanza Verticale (VRC)**:
- El **VRC (Vertical Redundancy Check)** es otro método de detección de errores.
- Se agrega un bit de paridad a cada columna de datos en una matriz.
- La suma de los bits de paridad en cada columna debe ser par o impar.
- Similar a la paridad, pero se aplica a grupos de bits en lugar de palabras completas
- Si calcola l’OR esclusivo su tutti i bit che si trovano nella stessa posizione all’interno di ciascun carattere.


#### **Controllo Ciclico di Ridondanza (CRC)**:
- El **CRC (Cyclic Redundancy Check)** es un algoritmo más avanzado utilizado para verificar la integridad de los datos almacenados en unidades de memoria como discos duros, unidades USB, CD-ROM, DVD y Blu-ray.
- Calcula un valor de verificación (checksum) basado en los datos y lo compara con un valor previamente calculado.
- Si los valores no coinciden, se detecta un error.
- Es ampliamente utilizado en redes digitales y dispositivos de almacenamiento



### Trasmision balanceada y no balanceada
#### **Transmisión No Balanceada**:
- En una transmisión no balanceada, la señal se envía a través de un solo conductor (generalmente el cable central) y se referencia a tierra (masa).
- Es más susceptible a interferencias electromagnéticas y ruido.
- Se utiliza en conexiones como **RCA** (audio y video) y **TS/TRS** (conectores de audio).


#### **Transmisión Balanceada**:
- En una transmisión balanceada, la señal se envía a través de dos conductores: uno positivo y otro negativo (diferencial).
- La señal se refiere a tierra como referencia común.
- Es menos susceptible a interferencias y proporciona una mejor calidad de señal.
- Se utiliza en conexiones como **XLR** (audio profesional) y **Ethernet**.



#### Balanceada vs No balanceada

|  | Non bilanciata | Bilanciata |
| ---- | ---- | ---- |
| Vantaggi | Conessioni minime, basso coste per brevi distanza, unica linea | Alta immunitá al rumore di modo comune, idoneo per lunghe distanze |
| Svantaggi | Bassa immunitá al rumore di modo comune, degradazione del segnale, costo di schematura per lunghe distanza | Costi piú elevato, Corretta terminazione della linea |

![[Pasted image 20231226173638.png]]