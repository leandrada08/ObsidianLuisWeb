---
cards-deck: "Profesional::Universidad::UNISA::Sistemi di interfaccia:: USB"
---



# Italiano
## Introduccion
L’'Universal Serial Bus(USB) é un tipo specifico di bus sviluppato nel 1995. L’obiettivo era creare un’interfaccia unificata per collegare periferiche accessorie, sostituendo le porte parallele, seriali e altre interfacce esistenti sui computer.

### **Versioni USB**

1. **USB 1.0 (1996)**:
    - Prima versione, ma mancava di adeguate protezioni contro inconvenienti come picchi di assorbimento causati dall’inserimento di cavi periferici.
    - Ha dovuto attendere il rilascio delle specifiche USB 1.1 per ottenere successo.
2. **USB 1.1 (1998)**:
    - Riferimento tecnico per la maggior parte delle periferiche e schede madri.
    - Protezioni migliorate e stabilità.
3. **USB 2.0 (2000)**:
    - Aumento significativo della velocità di trasferimento dei dati (480 Mbit/s).
    - La topologia del bus è a stella, con un massimo di 127 dispositivi collegabili al PC.
    - Struttura gerarchica con l’host (PC) come vertice principale.
4. **USB 3.0 (2008)**:
    - Ancora maggiore velocità di trasferimento (5 Gbit/s).
    - Retrocompatibile con USB 2.0.
5. **USB 3.1 e 3.2**:
    - Ulteriori miglioramenti nelle velocità di trasferimento.

## Interfaz USB


### Caracteristica #tarjeta-anki 
- **Topologia a Stella**:
    - I dispositivi periferici non comunicano tra loro direttamente ma rispondono solo ai comandi dell’host (PC).
    - Non è possibile collegare simultaneamente lo stesso dispositivo a più computer.
    - La comunicazione funziona solo se l’host è unico.
- **Hot plug & Play**
	- Consente di  collegare e scollegare periferiche al PC sensa riavviarlo
- **Alimentazione delle Periferiche:** 
	- Il connettore USB ha quttro terminali: due per il trasferimento dei dati e due per l’alimentazione(5V)
	- Le periferiche possono prevale energia dal bus USB
	- Esistono due categorie di periferiche USB: *Self Powered*(alimentate autonomamente) e *Bus Powered*(alimentate dal bus)
		- Puo alimentare dispositivi di bassa pontenza
^1705869251161


#### Tipi di Dispositivi #tarjeta-anki  
Lo standar USB 1.1 definisce due tipi di dispositivi:
- **High-Speed Device:**
	- I dispositivi high-speed operano a full-speed, raggiungendo una velocitá massima di 12 Mbit/s
	- Possono inviare e ricevere dati a questa velocitá.
	- Comuni per dispositivi come dischi rigidi esterni, stampanti e scanner.
- **Low-Speed Device:**
	- I dispositivi low-speed sono limitati a una velocitá massima di 1.5 Mbit/s.
	- I pacchetti informativi inviati a questi dispositivi sono preceduti da un pacchetto di “premessa” per indicare che la transazione é destinata a un dispositivo low-speed.
^1705869251165



### Tipologia di periferiche
- **HOST:** É il controller del bus e sovraintende a tutte le transizioni indirizzando e interrogando i device.
- **DEVICE USB** o function aggiunge capacitá all’host puo essere low speed o full speed é caractterizzato da un indirizzo e dai suoi endpoints
- **Hub USB** é un replicatore di poste che rigenera i segnali. Questo é altro periferiche

#### HOST
La composizione logica del host include quanto segue:
- Controllore USB Host
- Sistema sofware globale dell’USB
- Client
É inoltre responsabilide del controllo e monitoraggio della topologia del dispositivo USB collegato al bus.


#### EndPoint
Un endpoint é una parte unicamente identificabile del dispositivo USB e constituisce un estremo di un flusso di comuncacion tra host e device
- In fase di progetto e realizzazione del device ad ogni Endpoint viene associato un numero indentificativo e una direzione del flusso dati con l’host.
- Quindi la combinazione dell’indirizzo del device, del numero dell’Endpoint e della sua direzione costituiscono un identificazione univoca del destinatario/sorgente dei dati.
- Questa tecnica permette di veicolare dati, destinati a funzioni differenti atraverso un bus a sinsola linea
- Caratteristiche che determinano il tipo di trasferimento tra l’endpoint e il client software:
	- La frequenza d’accesso al bus e la massima latenza consentita
	- La larghezza di banda richiesta
	- Il numero assegnato all’endpoint e la direzione del flusso
	- La massima dimensione del pacchetto che l’endpoint é capace di ricevere o trasmettere
	- Il tipo di trasfereimento che puó sostenere l’endpoint.

##### Endpoint zero
Chiamato Default Control Pipe, é un canale di controllo di default che é costituito dall’endpoint zero.
- Si utilizza tale canale per inizializzare e configurare un device.
	- Il default control pipe provvede all’accesso al dispositivo per recuperare le informazionni necessarie alla configurazione e di monitarare lo stato del device.
- L’endpoint numero zero é sempre accessible non appena il dispositivo é collegato, alimentato e ha ricevuto un comando di reset.

##### Enspoint non-zero
- Le funzione possono avere endpoint addizionali come richiesto dalla specifica implementazione.
- I Device Low Speed sono limitati ad avere al massimo due Endpoints opzionali oltre i due necessari per l’implementazione del default control Pipe. I device
- Sull speed possono avere un numero di endpoint opzionali limitati solo dalle specifiche del protocollo, cioé un massimo di 15 endpoint di input e 15 di output


## BUS USB

- Transmisión mediante tensiones diferenciales en los 4 cables
- Codificación NRZI de los datos
- Bit stuffing para sincronización
- Detección de conexión/desconexión mediante resistencias pull-up/down 
- Comunicación half-duplex serial punto a punto
- Líneas D+/D- para detección de velocidad

### Trasferimento di dati #tarjeta-anki 
- Tensione differenziale: Si fa con vatiazioni di tensioni differenziale fra due dei quattro cavetti costituenti il cavo USB
- Codifica NRZI:I dati da scambiare sono dapprima transormati in una sequenza continua e poi modulati con la codifica NRZI
- BIT STUFFING: Per evitare perdite di sincronizzazione, il trasmettitore inserisce nel flusso dei dati il cosiddetto stuffed bit; ogni volta che vengono inviati sei 1 consecutivi viene inserito questo bit che non oprta informacione e viene rimosso dal demodulatore durante la ricezione della stringa dei dati.
- Si implementa sistema single-enden del ricevitore per riconoscere particolari stati del bus, ad esempio quando entrambe le linee dati sono a livello basso.
![[Pasted image 20231227174737.png]]
- Lo scambio dei dati tra l’host o hub e la periferica é di tipo seriale half-duplex
	- Questo impone che i driver siano posti in uno stato di alta impedenza quando non trasmettono dati.
- La connessione é “Punto-Punto”: su ogni cavetto USB i segnali sono gestini in modo indipendente dagli altri.
#### Riconoscimiento
- Prima di trasferire, il software di sistema deve accertarsi della sua presenza e riconoscere se la periferica é ad alta velocitá o bassa velocitá.
- Ad ogni Device viene assegnato, in fase di collegamento e configurazione, un indirizzo.
**Come lo fa?**
- L’osservazione delle variazionni della tensionni differenziale consente di riconoscere la connessione/disconnessione degli apparati.
	- l’'hub individua la presenza di un dispositivo a una delle sue porte monitorando le linee dei dati dopo l’inserimento del cavo. Quando la periferica non é connessa al bus, le resistenze di pull-down(15k) le linee D+ e D- a massa
	- Se invence la periferica é collegata, si ottiene un partitore di tensione costituito dalla resistenza de pull-down dell’hub e dalla resistenza di pull-up(1.5k)
	- Si la periferica e di alta velocitá presenta una resistenza di pull-up sulla linea D+ ma si é di bassa velocitá presenta una resistenza di pull-up sulla linea D-
![[Pasted image 20231227173924.png]]
^1705869251168




#### Pipes #tarjeta-anki 
Un USB Pipe é il collegamento che si instaura tra una endpoint sul device e un client software sull’host tramite il buffer di memoria associato. Si po comunicare di due modo diverso:
- Stream: I dati vengo trasferiti attraverso un pipe sensa una struttura imposta dalle norme
- Message: I dati vengono trasferiti attraverso un pipe con una struttura definita dalle norme
L’USB non interpreta il contenuto dell’area dati che viene trasferita attraverso un pipe ma si limita a verificare che la struttura che li accoglie sia in accordo con le specifiche USB
##### Caratteristiche
- La richiesta di accesso al bus e la alrgueza di banda usata
- Il tipo di trasferimento
- Le caracteristiche, come la direzione e la massima dimensione del payload
- La pipe che ha come estremi i due endpoint numero zero e chiamato dafaul control pipe
##### Stream pipe
- I dati in un Stream pipe fuiscono con una logica FIFO e tali canali sono sempre unidirezionali
- Il flusso dati é sempre riferito ad un unico client l’USB System Software non fornisce la sincronizzazione tra client multiple che necessitano degli stessi dati
- Un numero di endpoint di un device nella direzione opposta puó essere usato per un altro stream pipe associato al device.
- Uno stream pipe supporta trasferimenti di tipo bulk, isocroni e ad interrupt
##### Message pipes
I message ppipe interagiscono con un endpoint in maniera differente da uno stream pipe. Ogni transazione comincia con una richiesta da parte dell’Host verso il Device. Qiesta richiesta é seguita da uno o piú trasferimenti di dati nella direzione appropriata. Infine Segue una fase di resoconto dello status.
Tale ordine nella comunicazione in un Message Pipe permette che gli ordini siano identificati e comunicati attendibilmente. I canali del messaggio permettono il flusso di comunicazione in entrambi i sensi, anche se il flusso di comunicazione può essere
principalmente one way.
- Il Default Control Pipe è sempre un Message Pipe.
- L’USB System Software assicura che non vengano inviati richieste multiple con un Message Pipe.
- Eventuali richieste provenienti da più client e destinate al Default Control Pipe vengono smaltite con strategia FIFO.
- Normalmente un Host non spedisce un nuovo message fin quando il message corrente non è stato completamente ricevuto dal device.
- Tuttavia, ci sono condizioni di errore per cui un trasferimento del messaggio può essere abbandonato dall'host ed un nuovo message può essere trasmesso prematuramente.
^1705869251171



## Funcionamiento del sistema usb #tarjeta-anki 
- Tutte le trasmissionni devono essere incapsulate in una fram di durata 1ms
- **Quando si collega una periferica USB al PC**, prima che inizi a comunicare, esiste una fase di **configurazione o “enumerazione”**. Questa configurazione avviene attraverso trasferimenti di tipo **control** utilizzando il **Default Control Pipe**. Per questo motivo, **tutte le periferiche devono essere in grado di gestire il trasferimento di controllo**. Durante questa fase, la periferica e l’host scambiano alcune informazioni memorizzate nel dispositivo e organizzate in **descrittori**. Ad esempio, la periferica, su richiesta del PC, comunica quale tipo di trasferimento supporta e il numero di endpoint che possiede. Nel frattempo, l’host comunica al dispositivo un indirizzo tramite il quale il dispositivo sarà indirizzato e sceglie una delle possibili configurazioni.
- **Come avviene la configurazione sull’host**: Una delle caratteristiche del sistema USB è quella di **rilevare la connessione o la rimozione di una periferica in modo autonomo**. Dalla prospettiva dell’utente, il processo di configurazione è quasi invisibile, tranne la prima volta, quando il sistema operativo potrebbe aver bisogno di un file con estensione “.inf” nel quale sono scritte informazioni sulla periferica e, eventualmente, di un driver. In questo caso, l’utente dovrà fornire un file di installazione
**Per capire i differenti stati**, possiamo seguire cosa avviene quando una periferica viene connessa al PC:
1. **L’utente collega la periferica al PC**:
    - La variazione di tensione sulle linee D+/D- segnala all’host che la connessione è avvenuta.
    - Il dispositivo inizia a prelevare l’alimentazione dal connettore e passa allo stato di **Powered**.
2. **L’host riconosce il dispositivo**:
    - L’hub controlla le tensioni su ciascuna linea del bus e determina se il dispositivo è di tipo **Low Speed** o **Full Speed**.
3. **L’host esegue il reset del dispositivo**:
    - Accertata la presenza di una nuova periferica, il PC emette un comando di reset (passiamo allo stato di **Default**).
    - La periferica viene inizializzata e attiva la comunicazione di tipo **control** sull’**endpoint zero**.
    - Finora, periferica e host non hanno scambiato alcuna informazione, ma hanno semplicemente eseguito operazioni preliminari.
4. **L’host assegna un indirizzo alla periferica**:
    - Il PC assegna alla periferica un indirizzo (da 0 a 127), tramite il quale indirizzarla una volta configurata.
    - La periferica, ricevuto l’indirizzo, lo memorizza ed emette un **handshake di conferma**.
    - A questo punto, la periferica è nello stato di **Address**.
    - L’indirizzo assegnato non è univoco; la stessa periferica può ricevere un indirizzo diverso ogni volta che viene scollegata e poi ricollegata al PC.
5. **L’host richiede alla periferica i descrittori**:
    - Le richieste da parte dell’host avvengono tramite una **transazione di controllo**.
    - In fase di configurazione, queste richieste sono di tipo standard.
    - Il dispositivo risponde con un **descrittore**.
    - Con questi descrittori, la periferica fornisce al PC una sorta di **scheda personale** in cui sono scritte tutte le informazioni necessarie per la corretta configurazione.
    - Ad esempio:
        - Costruttore
        - Tipo di periferica
        - Numero degli eventuali endpoint
        - Corrente ass
6. **Il PC host assegna un driver alla periferica**:
	- In base ai descrittori e, eventualmente, al file con estensione “.inf” che il sistema operativo può richiedere, viene associato alla periferica il driver che si adatta meglio alle sue caratteristiche.
	- Nel caso il sistema operativo non disponga di un driver adatto, verrà richiesto all’utente tramite una finestra di dialogo.
7. **Il driver sceglie la configurazione**:
	- Dopo aver acquisito tutte le informazioni sulla periferica, il driver le assegna la configurazione.
	- Alcune periferiche possono avere diverse configurazioni; in tal caso, il driver può decidere quale assegnare o chiederlo all’utente tramite una finestra di dialogo.
	- A questo punto, il dispositivo è connesso ed è pronto per scambiare dati. 
^1705869251174


## Vantaggi e limit del bus USB
### Rispetto al bus seriale RS232 il bus USB offre:
1. Maggiore largueza di banda e diversi tipi di trasferimento con latenza o larghezza di banda assicurata
2. Possibilitá di connettere un numero maggiore di periferiche
3. Connettivitá a “Caldo” delle periferiche(Hot Plug and Play)

### Rispetto alla piú preformante 488 l’USB presenta:
1. Maggiore diffusione del bus sui compute
2. Minor corto e complessitá dei controller

I limiti di tale bus sono rappresentati invece dalla scarsa diffusione di periferiche di misura dotate di tale interfaccia ma soprattutto della scarsa trasparenza della gestione del bus da parte del sistema operativo e dalla difficoltá ello scrivere driver generici.

## USB 3.0
![[Pasted image 20231228162509.png|500]]
La versione 3.0 ha mantenuto la retrocompatibilitá con USB 2.0 e 1.0. Infatti i nuovi connettori(con un maggiori numero di piedi) permettono l’inserzione in una parte dei suoi piedini dei connettore USB 2.0
- Questo novo USB estende il tipo di trasferimento di massa in SuperSpeed. Questa estensione consente a un host e a un dispositivo di creare e trasferire piú flussi di dati attraverso un singolo supporto. Nuove funzioni di gestione dell’alimentazione includono il supporto di inattivitá, stand by e sospendione dello stato. 
- USB 3.0 non definisce le lunguezze dei cavi, in teoria puó essere usata qualsiasi lunguezza, perché soddisfi tutti i requissiti definiti nella specifia. Tuttavia alcune stime indicano una limitazione di 3m usando SuperSpeed




---
---
---

# Español
## Introduccion
**Universal Serial Bus (USB)** es un tipo específico de bus desarrollado en 1995. El objetivo era crear una interfaz unificada para conectar periféricos, reemplazando los puertos paralelos, seriales y otras interfaces existentes en las computadoras.

### **Versiones de USB**

1. **USB 1.0 (1996)**:
    - Primera versión, pero carecía de protecciones adecuadas contra inconvenientes como picos de absorción causados por la conexión de cables periféricos.
    - Tuvo que esperar el lanzamiento de las especificaciones USB 1.1 para lograr el éxito.
2. **USB 1.1 (1998)**:
    - Punto de referencia técnico para la mayoría de los dispositivos periféricos y placas madre.
    - Mejora en protecciones y estabilidad.
3. **USB 2.0 (2000)**:
    - Aumento significativo en la velocidad de transferencia de datos (480 Mbit/s).
    - Topología de bus en estrella, con un máximo de 127 dispositivos conectables a la PC.
    - Estructura jerárquica con el host (PC) como vértice principal.
4. **USB 3.0 (2008)**:
    - Mayor velocidad de transferencia aún (5 Gbit/s).
    - Retrocompatible con USB 2.0.
5. **USB 3.1 y 3.2**:
    - Mejoras adicionales en las velocidades de transferencia.
## Interfaz USB

### Características generales
#### Arquitectura
**Topología en Estrella**:
- Los dispositivos periféricos no se comunican directamente entre sí, sino que responden solo a los comandos del host (PC).
- No es posible conectar simultáneamente el mismo dispositivo a varios ordenadores.
- La comunicación solo funciona si el host es único.
- La **conexion** es punto a punto
#### Conexiones
**Cables:**
- Transmisión mediante 4 cables
	- 2 diferenciales para transferencia de datos
		- Tambien se usan las lineas diferenciales para deteccion de velocidad
	- 2 de alimentacion(gnd y vdd).
**Alimentación de los Periféricos:** 
- Los periféricos pueden obtener energía del bus USB mediante las 2 lineas de alimentacion
- Existen dos categorías de periféricos USB: *Self Powered* (alimentados de forma autónoma) y *Bus Powered* (alimentados por el bus).
- Pueden alimentar dispositivos de baja potencia.
**Hot Plug & Play:**
- Permite conectar y desconectar dispositivos al PC sin necesidad de reiniciar.

#### Comunicacion
- **Codificación** NRZI de los datos
- **Comunicación** half-dúplex serial punto a punto

### Tipos de Dispositivos
#### Por su velocidad
El estándar USB 1.1 define dos tipos de dispositivos:
- **High-Speed Device:**
	- Los dispositivos de alta velocidad operan a velocidad completa, alcanzando una velocidad máxima de 12 Mbit/s.
	- Pueden enviar y recibir datos a esta velocidad.
	- Comunes para dispositivos como discos duros externos, impresoras y escáneres.
- **Low-Speed Device:**
	- Los dispositivos de baja velocidad están limitados a una velocidad máxima de 1.5 Mbit/s.
	- Los paquetes de información enviados a estos dispositivos son precedidos por un paquete de "premisa" para indicar que la transacción está destinada a un dispositivo de baja velocidad.

#### Por su funcion
- **HOST:** Es el controlador del bus y supervisa todas las transiciones dirigiéndose e interrogando a los dispositivos.
- **DEVICE USB** o función agrega capacidad al host y puede ser de baja velocidad o velocidad completa, está caracterizado por una dirección y sus puntos finales (endpoints).
- **Hub USB** es un replicador de puertos que regenera las señales. Esto se considera otro periférico.
	- Tenemos un maximo de 6 niveles de profundidad, luego de eso los dispositivos ya no se reconoceran
- **Endpoint:** Parte del dispositivo

##### HOST
La composición lógica del host incluye lo siguiente:
- Controlador USB Host
- Sistema de software global de USB
- Cliente
También es responsable del control y monitoreo de la topología del dispositivo USB conectado al bus.

##### Endpoint
Un endpoint es una parte única identificable del dispositivo USB y constituye un extremo de un flujo de comunicación entre el host y el dispositivo.
- En la fase de diseño e implementación del dispositivo, a cada endpoint se le asocia un número identificativo y una dirección del flujo de datos con el host.
- La combinación de la dirección del dispositivo, el número del endpoint y su dirección constituyen una identificación única del destinatario/fuente de datos.
- Esta técnica permite transportar datos destinados a funciones diferentes a través de un bus de una sola línea.
- Características que determinan el tipo de transferencia entre el endpoint y el software cliente:
	- La frecuencia de acceso al bus y la máxima latencia permitida.
	- El ancho de banda requerido.
	- El número asignado al endpoint y la dirección del flujo.
	- El tamaño máximo del paquete que el endpoint puede recibir o transmitir.
	- El tipo de transferencia que el endpoint puede admitir.
###### Endpoint cero
Llamado Default Control Pipe, es un canal de control predeterminado que está constituido por el endpoint cero.
- Se utiliza este canal para inicializar y configurar un dispositivo.
	- El default control pipe se encarga de acceder al dispositivo para recuperar la información necesaria para la configuración y monitorear el estado del dispositivo.
- El endpoint número cero siempre es accesible tan pronto como el dispositivo está conectado, alimentado y ha recibido una orden de reinicio.
###### Enspoint no cero
- Las funciones pueden tener endpoints adicionales según lo requiera la implementación específica.
- Los dispositivos de baja velocidad están limitados a tener como máximo dos endpoints opcionales además de los dos necesarios para la implementación del default control Pipe. Los dispositivos de alta velocidad pueden tener un número de endpoints opcionales limitado solo por las especificaciones del protocolo, es decir, un máximo de 15 endpoints de entrada y 15 de salida.


## BUS USB

### Transferencia de datos
La transferencia de datos se realiza fisicamente con la variazion de 2 tensiones diferenciales de 2 cables de los 4, estos datos estan codificados en codificacion NRZI, la cual primero es transformada en una secuancia continua y recien se modula a NRZI.
- Esta transferencia de datos es del tipo half-duplex.
![[Pasted image 20240103185213.png]]
- Al ser Half Duplex necesitamos que el driver sea puesto en un stado de alta impendancia quando non trasmite dato. 
- A cada dispositivo se le asigna, en la conexión y configuración, una dirección.
#### Reconocimiento de velocidad
- Antes de la transferencia, el software del sistema debe asegurarse de su presencia y reconocer si el dispositivo es de alta velocidad o baja velocidad.
**¿Cómo lo hace?**
- La observación de las variaciones de la tensión diferencial permite reconocer la conexión/desconexión de los dispositivos.
	- El hub identifica la presencia de un dispositivo en uno de sus puertos monitoreando las líneas de datos después de insertar el cable. Cuando el dispositivo no está conectado al bus, las resistencias de pull-down (15k) bajan las líneas D+ y D- a tierra.
	- Si, en cambio, el dispositivo está conectado, se obtiene un divisor de tensión formado por la resistencia pull-down del hub y la resistencia pull-up (1.5k).
	- Si el dispositivo es de alta velocidad, presenta una resistencia pull-up en la línea D+, pero si es de baja velocidad, presenta una resistencia pull-up en la línea D-
![[Pasted image 20231227173924.png]]
#### Single-Ended e Differential Driver
- Existe ademas de la trasmision diferencial un sistema Single-Ended
	- Este sistema sirve para reconocer estado particulares
	- Estos estados pueden ser de reset o de bajo nivel de la lineas
- Tambien vale la pena aclarar que no es un sistema totalmente diferencial ya que tenemos las lineas conectadas(entonces referidas) a massa.
- El differential driver es un circuito que envia los datos a las lineas D+ y D- en forma de señal diferencial, este envia una señal poditiva por una linea o negativa y alterna para crear la diferencia de voltaje necesaria
![[Pasted image 20231227174737.png]]





## Pipes 
Un Pipe USB es la conexión establecida entre un endpoint en el dispositivo y un software cliente **en el host** a través del búfer de memoria asociado.
USB no interpreta el contenido del área de datos que se transfiere a través de un pipe, pero se limita a verificar que la estructura que los alberga esté de acuerdo con las especificaciones USB.
### Características
- La solicitud de acceso al bus y el ancho de banda utilizado.
- El tipo de transferencia.
- Las características, como la dirección y el tamaño máximo de la carga útil.
- El pipe que tiene como extremos los dos endpoints número cero se llama default control pipe.
### Comunicacion
 Se puede comunicar de dos maneras diferentes:
- Stream: Los datos se transfieren a través de un pipe sin una estructura impuesta por las normas.
- Message: Los datos se transfieren a través de un pipe con una estructura definida por las normas.
#### Stream pipe
- Los datos en un Stream pipe fluyen con una lógica FIFO y estos canales **son siempre unidireccionales**.
- El flujo de datos siempre está dirigido a un solo cliente; el software del sistema USB no proporciona la sincronización entre múltiples clientes que necesitan los mismos datos.
- Un número de endpoints de un dispositivo en la dirección opuesta puede usarse para otro stream pipe asociado al dispositivo.
- Un stream pipe **admite transferencias de tipo bulk, isócronas y de interrupción**.
- **Utiles para transferir grande cantidad de datos continuos.**
#### Message pipes
- Cada transacción comienza con una solicitud del host al dispositivo. Esta solicitud es seguida por uno o más traslados de datos en la dirección apropiada. Finalmente, sigue una fase de informe de estado.
- Este orden en la comunicación en un Message Pipe permite que las órdenes se identifiquen y comuniquen de manera confiable. 
- Son bidireccionales, con intercambio de mensajes en ambos sentidos.
- Se usan para transferencias de control, como el Default Control Pipe.
- Se usa para comunicacion sincrona y structured.


##### Observaciones
- El software del sistema USB asegura que no se envíen múltiples solicitudes con un Message Pipe.
- Cualquier solicitud proveniente de varios clientes y destinada al Default Control Pipe se maneja con una estrategia FIFO.
- Normalmente, un host no envía un nuevo mensaje hasta que el mensaje actual ha sido completamente recibido por el dispositivo.
- Sin embargo, hay condiciones de error por las cuales una transferencia de mensaje puede ser abandonada por el host y un nuevo mensaje puede ser transmitido prematuramente.



## Funcionamiento del sistema USB
- BIT STUFFING: Para evitar pérdidas de sincronización, el transmisor inserta en el flujo de datos el llamado bit de relleno; cada vez que se envían seis 1 consecutivos, se inserta este bit que no lleva información y es eliminado por el demodulador durante la recepción de la cadena de datos.
- Todas las transmisiones deben estar encapsuladas en un marco de duración de 1 ms.
- **Cuando se conecta un dispositivo USB a la PC**, antes de que comience a comunicarse, hay una fase de **configuración o "enumeración"**. Esta configuración se realiza mediante transferencias de tipo **control** utilizando el **Default Control Pipe**. Por esta razón, **todos los dispositivos deben ser capaces de manejar la transferencia de control**. Durante esta fase, el dispositivo y el host intercambian información almacenada en el dispositivo y organizada en **descriptores**. Por ejemplo, el dispositivo, a solicitud de la PC, comunica qué tipo de transferencia admite y el número de endpoints que posee. Mientras tanto, el host comunica al dispositivo una dirección a través de la cual se dirigirá al dispositivo y elige una de las posibles configuraciones.
- **Cómo se realiza la configuración en el host**: Una de las características del sistema USB es la de **detectar la conexión o desconexión de un dispositivo de manera autónoma**. Desde la perspectiva del usuario, el proceso de configuración es casi invisible, excepto la primera vez, cuando el sistema operativo puede necesitar un archivo con extensión ".inf" en el que se escriban información sobre el dispositivo y, posiblemente, un controlador. En este caso, el usuario deberá proporcionar un archivo de instalación.


**Para entender los diferentes estados**, podemos seguir lo que sucede cuando se conecta un dispositivo a la PC:

1. **El usuario conecta el dispositivo a la PC**:
    
    - La variación de tensión en las líneas D+/D- informa al host que la conexión ha tenido lugar.
    - El dispositivo comienza a tomar la alimentación del conector y pasa al estado de **Powered**.
2. **El host reconoce el dispositivo**:
    
    - El concentrador verifica las tensiones en cada línea del bus y determina si el dispositivo es de tipo **Low Speed** o **Full Speed**.
3. **El host realiza el reset del dispositivo**:
    
    - Después de confirmar la presencia de un nuevo dispositivo, la PC emite un comando de reinicio (pasamos al estado **Default**).
    - El dispositivo se inicializa y activa la comunicación de tipo **control** en el **endpoint zero**.
    - Hasta ahora, el dispositivo y el host no han intercambiado ninguna información, simplemente han realizado operaciones preliminares.
4. **El host asigna una dirección al dispositivo**:
    
    - La PC asigna al dispositivo una dirección (de 0 a 127), mediante la cual se dirigirá una vez configurado.
    - El dispositivo, al recibir la dirección, la almacena y emite un **handshake de confirmación**.
    - En este punto, el dispositivo se encuentra en el estado de **Address**.
    - La dirección asignada no es única; el mismo dispositivo puede recibir una dirección diferente cada vez que se desconecta y luego se vuelve a conectar a la PC.
5. **El host solicita los descriptores al dispositivo**:
    
    - Las solicitudes del host se realizan mediante una **transacción de control**.
    - En la fase de configuración, estas solicitudes son de tipo estándar.
    - El dispositivo responde con un **descriptor**.
    - Con estos descriptores, el dispositivo proporciona a la PC una especie de **tarjeta de presentación** en la que se escriben todas las informaciones necesarias para la correcta configuración.
    - Por ejemplo:
        - Fabricante
        - Tipo de dispositivo
        - Número de endpoints, si los hubiera
        - Corriente absorbida
6. **La PC asigna un controlador al dispositivo**:

	- Con base en los descriptores y, posiblemente, en el archivo con extensión ".inf" que el sistema operativo puede requerir, se asigna al dispositivo el controlador que mejor se adapta a sus características.
	- En caso de que el sistema operativo no tenga un controlador adecuado, se solicitará al usuario a través de un cuadro de diálogo.

7. **El controlador elige la configuración**:

	- Después de adquirir toda la información sobre el dispositivo, el controlador le asigna la configuración.
	- Algunos dispositivos pueden tener diferentes configuraciones; en este caso, el controlador puede decidir cuál asignar o preguntar al usuario a través de un cuadro de diálogo.
	- En este punto, el dispositivo está conectado y listo para intercambiar datos.



## Ventajas y limitaciones del bus USB
### En comparación con el bus serie RS232, el bus USB ofrece:
1. Mayor ancho de banda y diferentes tipos de transferencia con latencia o ancho de banda asegurado.
2. Posibilidad de conectar un mayor número de periféricos.
3. Conectividad "Hot Plug and Play" de los dispositivos.

### En comparación con el más rendimiento GPIB 488, USB presenta:
1. Mayor prevalencia del bus en las computadoras.
2. Menor costo y complejidad de los controladores.

Los límites de este bus se deben a la escasa presencia de dispositivos de medición con esta interfaz, pero sobre todo a la falta de transparencia en la gestión del bus por parte del sistema operativo y a la dificultad para escribir controladores genéricos.

## USB 3.0
![[Pasted image 20231228162509.png|500]]

La versión 3.0 ha mantenido la retrocompatibilidad con USB 2.0 y 1.0. De hecho, los nuevos conectores (con más pines) permiten la inserción en una parte de sus pines del conector USB 2.0.
- Este nuevo USB extiende el tipo de transferencia de masa en SuperSpeed. Esta extensión permite que un host y un dispositivo creen y transfieran múltiples flujos de datos a través de un solo puerto. Las nuevas funciones de gestión de energía incluyen el soporte para los estados de inactividad, espera y suspensión.
- USB 3.0 no define las longitudes de los cables, en teoría, puede usarse cualquier longitud que cumpla con todos los requisitos definidos en la especificación. Sin embargo, algunas estimaciones indican una limitación de 3 m utilizando SuperSpeed.
