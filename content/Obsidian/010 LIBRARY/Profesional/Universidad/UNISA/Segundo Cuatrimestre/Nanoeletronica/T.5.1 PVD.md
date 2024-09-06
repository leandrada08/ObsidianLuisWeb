---
cards-deck: Profesional::Universidad::UNISA::Segundo Cuatrimestre::Nanoeletronica
---

# Italiano

## Deposizione Fisica da Vapore (PVD)
![[Pasted image 20240628113938.png]]
La **Deposizione Fisica da Vapore (PVD)** è una tecnica di rivestimento utilizzata per depositare film sottili di materiale su un substrato.
1. Il materiale che deve essere depositato(allo stato solido) e convertito in fase vapore attravers oun processo fisico
2. Il vapore é trasportato dalla sorgente al substrato attraverso una regione a bassa pressione
3. Il vapore condensa sopra il substrato formando il fil sottile

- La PVD è ampiamente utilizzata nell'industria elettronica, ottica e dei rivestimenti decorativi a causa della sua capacità di produrre strati sottili di alta qualità con un controllo preciso della composizione e delle proprietà del film.

### Principali Metodi di PVD

1. **Sputtering**
   - **Principio**: Consiste nel bombardare un bersaglio di materiale solido con ioni energetici, generalmente argon. Gli atomi del bersaglio vengono espulsi e depositati sul substrato formando un film sottile.
   - **Tipi di Sputtering**:
     - **DC Sputtering**: Utilizzato principalmente per materiali conduttori.
     - **RF Sputtering**: Utilizzato per materiali isolanti.
     - **Magnetron Sputtering**: Migliora l'efficienza del processo utilizzando campi magnetici.

2. **Evaporazione Termica**
   - **Principio**: Il materiale viene riscaldato fino al suo punto di evaporazione in una camera a vuoto e il vapore si condensa sul substrato.
   - **Metodi**:
     - **Resistenza Elettrica**: Il materiale viene riscaldato tramite una resistenza.
     - **Vaschette:** Si riscalda un vaschette per evaporare
     - **Fascio di Elettroni (e-beam)**: Un fascio di elettroni riscalda il materiale fino alla sua evaporazione.
	     - **Vantaggi**: Alta purezza del film depositato, controllo preciso del deposito.



### Caratteristiche della PVD
#### Vantaggi
1. **Alta Purezza del Film**: I film depositati mediante PVD sono di alta purezza a causa della tecnica a vuoto utilizzata.
2. **Forte Adesione**: Il metodo PVD assicura una forte adesione del film depositato al substrato.
3. **Controllo Preciso**: Permette un controllo preciso dello spessore e della composizione del film depositato.
4. **Versatilità**: Capacità di depositare una vasta gamma di materiali, inclusi metalli, ossidi e composti.
5. **Temperature di Processo Più Basse**: Rispetto ad altre tecniche come la CVD, la PVD può operare a temperature più basse.

#### Svantaggi 

1. **Copertura dei Gradienti**: Copertura inferiore dei gradienti rispetto alla CVD.
2. **Attrezzatura Costosa**: L'attrezzatura richiesta per la PVD può essere costosa e complessa.
3. **Processo a Vuoto**: Necessita di una camera a vuoto, il che può limitare la dimensione dei substrati processati.


## [[T.5.1.1 Sputtering]]



## Evaporazione Termica #tarjeta-anki 

### Principio dell'Evaporazione Termica
L'evaporazione termica è un processo in cui il materiale solido viene riscaldato fino al suo punto di evaporazione in una camera a vuoto. Il vapore metallico risultante si condensa sulla superficie del substrato, formando un film sottile.
 - Si muove grazie alla variazione di presione
![[Pasted image 20240628122215.png]]
### Caratteristiche dell'Evaporazione Termica
- **Processo Semplice e Diretto**: È un metodo semplice e diretto per depositare film sottili.
- **Richiede Camera a Vuoto**: L'evaporazione si svolge in una camera a vuoto per evitare ossidazione e contaminazione.
- **Alta Purezza del Film**: Produce film di alta purezza a causa dell'assenza di reazioni chimiche.
- **Controllo dello Spessore**: Lo spessore del film può essere controllato regolando la quantità di materiale evaporato e il tempo di deposizione.
### Sensore del Metallo Depositato
- **Uso del Quarzo**:
    - Viene posizionato un sensore di quarzo vicino al substrato.
    - Il quarzo agisce come un oscillatore la cui frequenza varia con la quantità di metallo depositato.
    - Questa variazione di frequenza viene utilizzata per monitorare e controllare la deposizione, fornendo feedback in tempo reale sullo spessore e l'uniformità del deposito.
- **Calibrazione**:
    - Realizzare una curva di calibrazione per conoscere come varia la frequenza di oscillazione con la quantità di metallo depositato.
    - Misurare variazioni di capacità tra le piastre in funzione della distanza.
- **Prevenzione dell'Aglomerazione**:
    - Implementare un sistema per evitare l'agglomerazione di metallo sul quarzo.
### Considerazioni Generali
- **Camera a Vuoto**:
    - Il processo deve essere realizzato in una camera a vuoto per evitare l'interferenza di particelle indesiderate.
- **Controllo della Deposizione**:
    - Si può utilizzare una piastra per controllare la deposizione del metallo, migliorando l'uniformità.
- **Temperatura**:
    - Anche se non è fondamentale, una temperatura adeguata può migliorare il processo.
### Movimento del sustrato
- Il substrato deve essere mosso con un movimento planetario per garantire una deposizione uniforme.
    - **Sistema Planetario**:
        - I substrati sono montati su un supporto che ruota attorno al proprio asse e contemporaneamente attorno a un asse centrale.
        - Questo movimento assicura che tutte le aree del substrato ricevano una quantità uniforme di materiale evaporato.
![[Pasted image 20240628122333.png]]
![[Pasted image 20240628122406.png]]
- Velocitá di crescita uniforme e controllata come sorgente puntiforme
#### Riscaldamento
Si fa un rescaldamento resistivo e uno tipi vaschette
![[Pasted image 20240628122624.png]]
- Limitazione di baschette → Elevato grado di contaminazione, non é possibile l’evaporazione di metalli refrattari, carica picola → spessore limitato
- Per questo si usa la evaporazione con e-bear
^1719957725245


## Evaporazione con Fascio di Elettroni (E-beam) #tarjeta-anki 

### Principio del Metodo
Consiste nel riscaldare il metallo utilizzando elettroni accelerati mediante un campo elettrico e magnetico. Questi elettroni impattano il metallo solido, provocando il suo riscaldamento e la sua eventuale vaporizzazione senza riscaldare il recipiente circostante.
- **Riscaldamento con Elettroni**:
    - Gli elettroni sono accelerati mediante campi elettrici e magnetici.
    - Questi elettroni impattano il metallo (ad esempio, alluminio), riscaldandolo.
    - Il metallo si vaporizza senza la necessità di riscaldare il recipiente.
### Collegamento del Metallo Liquido
- Nel riscaldare il metallo per vaporizzarlo, è cruciale collegare il metallo liquido a terra.
- Questo collegamento assicura:
    - Flusso costante di elettroni.
    - Mantenimento di un potenziale elettrico adeguato.
    - Processo stabile e controllato.
### Vantaggi della Evaporazione con Fascio di Elettroni
- **Alta Purezza del Film**: Grazie al controllo preciso del fascio di elettroni e della camera a vuoto, si ottengono film di alta purezza.
- **Controllo Preciso dello Spessore**: Il sistema permette un controllo molto preciso dello spessore della pellicola depositata.
- **Adatto per Materiali con Alti Punti di Fusione**: L'alta energia del fascio di elettroni permette l'evaporazione di materiali con punti di fusione elevati che non possono essere facilmente evaporati con metodi termici convenzionali.
### Applicazioni della Evaporazione con Fascio di Elettroni
- **Fabbricazione di Componenti Elettronici**: Deposito di materiali conduttori e dielettrici per dispositivi elettronici.
- **Ottica di Alta Precisione**: Rivestimenti per specchi e lenti in applicazioni laser.
- **Rivestimenti Protettivi**: Strati resistenti all'usura e alla corrosione su utensili e componenti meccanici.
^1719957725251


## Uso Attuale nella CVD

Attualmente, questi metodi di evaporazione con fascio di elettroni e evaporazione termica sono utilizzati come una fase preliminare nei processi di Deposizione Chimica da Vapore (CVD), fornendo una fonte di vapore metallico puro e controllato per il processo di deposizione.

- **Vapore Metallico per CVD**:
  - Il metallo vaporizzato viene utilizzato come precursore nei processi di CVD.
  - Fornisce una fonte pura e controllata di vapore metallico.





# Spagnlo
## Deposición Física de Vapor (PVD)

### Introducción a la PVD

La **Deposición Física de Vapor (PVD)** es una técnica de recubrimiento utilizada para depositar películas delgadas de material sobre un sustrato. El proceso implica la transición del material de la fase sólida a la fase vapor y su posterior condensación sobre el sustrato. PVD se usa ampliamente en la industria electrónica, óptica y de recubrimientos decorativos debido a su capacidad para producir capas finas de alta calidad con control preciso de la composición y propiedades del film.

### Métodos Principales de PVD

1. **Sputtering**
   - **Principio**: Consiste en bombardear un blanco (target) de material sólido con iones energéticos, generalmente argón. Los átomos del blanco son expulsados y depositados sobre el sustrato formando una película delgada.
   - **Tipos de Sputtering**:
     - **DC Sputtering**: Utilizado principalmente para materiales conductores.
     - **RF Sputtering**: Utilizado para materiales aislantes.
     - **Magnetron Sputtering**: Mejora la eficiencia del proceso utilizando campos magnéticos.
   - **Aplicaciones**: Fabricación de circuitos integrados, películas delgadas para sensores, recubrimientos ópticos.

2. **Evaporación Térmica**
   - **Principio**: El material se calienta hasta su punto de evaporación en una cámara de vacío y el vapor se condensa sobre el sustrato.
   - **Métodos**:
     - **Resistencia Eléctrica**: El material se calienta mediante una resistencia.
     - **Haz de Electrones (e-beam)**: Un haz de electrones calienta el material hasta su evaporación.
   - **Aplicaciones**: Recubrimientos metálicos, películas ópticas, recubrimientos decorativos.

3. **Evaporación por Haz de Electrones (E-beam)**
   - **Principio**: Utiliza un haz de electrones para calentar y evaporar el material, que luego se deposita en el sustrato.
   - **Ventajas**: Alta pureza del film depositado, control preciso del depósito.
   - **Aplicaciones**: Fabricación de componentes electrónicos, ópticos y recubrimientos protectores.

### Características y Ventajas de la PVD

1. **Alta Pureza del Film**: Los films depositados mediante PVD son de alta pureza debido a la técnica de vacío utilizada.
2. **Adhesión Fuerte**: El método PVD asegura una fuerte adhesión de la capa depositada al sustrato.
3. **Control Preciso**: Permite un control preciso sobre el espesor y la composición del film depositado.
4. **Versatilidad**: Capacidad para depositar una amplia variedad de materiales, incluyendo metales, óxidos y compuestos.
5. **Temperaturas de Procesamiento Más Bajas**: Comparado con otras técnicas como CVD, PVD puede operar a temperaturas más bajas.

### Desventajas de la PVD

1. **Cobertura de Gradientes**: Menor cobertura de gradientes en comparación con CVD.
2. **Equipo Costoso**: El equipo requerido para PVD puede ser costoso y complejo.
3. **Proceso de Vacío**: Necesita una cámara de vacío, lo que puede limitar el tamaño de los sustratos procesados.

### Aplicaciones Comunes de la PVD

1. **Microelectrónica**: Deposición de capas conductoras, dieléctricas y de barrera en la fabricación de circuitos integrados.
2. **Óptica**: Recubrimientos antirreflectantes, espejos, filtros ópticos.
3. **Decorativos**: Revestimientos metálicos decorativos en joyería, relojes y artículos de lujo.
4. **Protección**: Recubrimientos duros y resistentes al desgaste en herramientas de corte y componentes mecánicos.


## [[T.5.1.1 Sputtering]]

## Evaporación por Haz de Electrones (E-beam)

### Principio del Método

Consiste en calentar el metal utilizando electrones acelerados mediante un campo eléctrico y magnético. Estos electrones impactan el metal sólido, provocando su calentamiento y eventual vaporización sin calentar el recipiente circundante.

- **Calentamiento con Electrones**:
    - Los electrones son acelerados mediante campos eléctricos y magnéticos.
    - Estos electrones impactan el metal (por ejemplo, aluminio), calentándolo.
    - El metal se vaporiza sin necesidad de calentar el recipiente.

### Conexión del Metal Líquido

- Al calentar el metal para vaporizarlo, es crucial conectar el metal líquido a tierra.
- Esta conexión asegura:
    - Flujo constante de electrones.
    - Mantener un potencial eléctrico adecuado.
    - Proceso estable y controlado.

### Sensor de Metal Depositado

- **Uso de Cuarzo**:
    - Se coloca un sensor de cuarzo cerca del sustrato.
    - El cuarzo actúa como un oscilador cuya frecuencia varía con la cantidad de metal depositado.
    - Esta variación en frecuencia se utiliza para monitorear y controlar la deposición, proporcionando retroalimentación en tiempo real sobre el grosor y la uniformidad del depósito.

### Consideraciones Generales

- **Cámara de Vacío**:
    - El proceso debe realizarse en una cámara de vacío para evitar la interferencia de partículas no deseadas.
- **Movimiento del Sustrato**:
    - El sustrato debe moverse con un movimiento planetario para asegurar una deposición uniforme.
    - **Sistema Planetario**:
        - Los sustratos se montan en un soporte que gira alrededor de su propio eje y simultáneamente alrededor de un eje central.
        - Este movimiento asegura que todas las áreas del sustrato reciban una cantidad uniforme de material evaporado.
- **Control de Deposición**:
    - Se puede usar una placa para controlar la deposición del metal, mejorando la uniformidad.
- **Temperatura**:
    - Aunque no es fundamental, una temperatura adecuada puede mejorar el proceso.
- **Calibración**:
    - Realizar una curva de calibración para conocer cómo varía la frecuencia de oscilación con la cantidad de metal depositado.
    - Medir variaciones de capacidad entre placas en función de la distancia.
- **Prevención de Aglomeración**:
    - Implementar un sistema para evitar la aglomeración de metal sobre el cuarzo.

### Ventajas de la Evaporación por Haz de Electrones

- **Alta Pureza del Film**: Debido al control preciso del haz de electrones y la cámara de vacío, se obtienen films de alta pureza.
- **Control Preciso del Espesor**: El sistema permite un control muy preciso sobre el espesor de la película depositada.
- **Adecuado para Materiales con Altos Puntos de Fusión**: La alta energía del haz de electrones permite la evaporación de materiales con puntos de fusión elevados que no se pueden evaporar fácilmente mediante métodos térmicos convencionales.

### Aplicaciones de la Evaporación por Haz de Electrones

- **Fabricación de Componentes Electrónicos**: Depósito de materiales conductores y dieléctricos para dispositivos electrónicos.
- **Óptica de Alta Precisión**: Recubrimientos para espejos y lentes en aplicaciones láser.
- **Revestimientos Protectores**: Capas resistentes al desgaste y la corrosión en herramientas y componentes mecánicos

## Evaporación Térmica

### Principio de la Evaporación Térmica

La evaporación térmica es un proceso en el que el material sólido se calienta hasta su punto de evaporación en una cámara de vacío. El vapor metálico resultante se condensa sobre la superficie del sustrato, formando una película delgada.

1. **Calentamiento Directo**:
    
    - El material a depositar se coloca en un crisol y se calienta mediante una resistencia eléctrica.
    - Al alcanzar su punto de evaporación, el material se convierte en vapor.
2. **Condensación del Vapor**:
    
    - El vapor metálico se condensa sobre el sustrato colocado en la parte superior de la cámara de vacío, formando una película delgada.

### Características de la Evaporación Térmica

- **Proceso Simple y Directo**: Es un método sencillo y directo para depositar películas delgadas.
- **Requiere Cámara de Vacío**: La evaporación se realiza en una cámara de vacío para evitar la oxidación y la contaminación.
- **Alta Pureza del Film**: Produce películas de alta pureza debido a la ausencia de reacciones químicas.
- **Control del Espesor**: El espesor del film se puede controlar ajustando la cantidad de material evaporado y el tiempo de deposición.

### Aplicaciones de la Evaporación Térmica

- **Recubrimientos Metálicos**: Depósito de metales como aluminio, oro, y plata.
- **Películas Ópticas**: Depósito de materiales para recubrimientos antirreflectantes y espejos.
- **Recubrimientos Decorativos**: Utilizado en joyería y relojería.



## Uso Actual en CVD

Actualmente, estos métodos de evaporacion por haz de electrones y evaporacion termica se utilizan como una etapa previa en procesos de Deposición Química de Vapor (CVD), proporcionando una fuente de vapor de metal puro y controlado para el proceso de deposición.

- **Vapor de Metal para CVD**:
  - El metal vaporizado se utiliza como precursor en procesos de CVD.
  - Proporciona una fuente pura y controlada de vapor metálico.
