---
cards-deck: Profesional::Universidad::UNISA::Segundo Cuatrimestre::Nanoeletronica
---

# Italiano
## Processi di fabbricazione dei dispositivi #tarjeta-anki 
1. **Progettazione (Diseño)**:
   - Questa fase stabilisce le specifiche e le caratteristiche del dispositivo e non può essere cambiata una volta iniziato il processo, poiché condiziona tutto il processo di fabbricazione.
2. **Preparazione delle fettine (Preparación de las Obleas)**:
   - Si ispezionano e puliscono le fettine di silicio, che possono essere state tagliate da lingotti prodotti con il metodo Czochralski. Questa pulizia è essenziale per eliminare i contaminanti e garantire una superficie adeguata per la crescita delle strati epitassiali.
3. **Epitassia**:
   - Dopo la preparazione delle fettine, si esegue l'epitassia su di esse. Questo processo deposita strati cristallini aggiuntivi sulle fettine con orientazioni e caratteristiche specifiche, ampliando le possibilità di progettazione e funzionalità del dispositivo.
4. **Processamento delle fettine**:
   - **Ossidazione termica**: Si forma uno strato di ossido di silicio sulla superficie della fettina tramite un processo di ossidazione termica. Questo strato funge da barriera dielettrica e da strato di protezione.
   - **Deposizione di nitruro di silicio**: Si deposita uno strato di nitruro di silicio sopra lo strato di ossido utilizzando la tecnica di deposizione chimica in fase vapore a bassa pressione (CVD). Questo strato è usato come barriera di diffusione, come strato di protezione durante l'incisione ed è un isolante termico aggiuntivo.
   - **Deposizione di polisilicio**: Si deposita uno strato di polisilicio sopra lo strato di nitruro di silicio sempre utilizzando la tecnica CVD a bassa pressione. Questo è posizionato per formare le porte dei transistor MOSFET.
5. **Fotolitografia**:
   - Si applicano processi di deposizione di fotoresistenze sulla superficie della fettina, seguiti da processi di esposizione per definire pattern nello strato di fotoresistenze.
6. **Incisione**:
   - Si utilizza un processo di incisione chimica per rimuovere selettivamente le aree esposte di ossido, nitruro di silicio e polisilicio, rivelando le aree desiderate della fettina.
   - Scopo
     - **Definizione di Strutture**: Rimuovere materiale in aree specifiche per creare pattern e strutture negli strati di materiali depositati.
     - **Formazione di Piste e Via**: Creare canali, contatti e altre strutture tridimensionali necessarie per il dispositivo.
7. **Pulizia**:
   - Si esegue una pulizia approfondita della fettina per eliminare eventuali residui dei processi precedenti, sia prima che dopo la deposizione dei materiali e l'incisione selettiva. Viene anche rimossa la fotoresistenza.
8. **Film Sottili**:
   - **Deposizione Chimica in Fase Vapore (CVD) di Dielettrici**:
     - **Scopo**: Formare strati dielettrici (ossido di silicio, nitruro di silicio).
     - **Importanza**: Isolamento elettrico, protezione della superficie, base per la fotolitografia.
   - **CVD di Tungsteno**:
     - **Scopo**: Depositare interconnessioni metalliche di tungsteno.
     - **Importanza**: Eccellente conduttività elettrica, alta resistenza termica.
   - **Deposizione Fisica in Fase Vapore (PVD)**:
     - **Scopo**: Depositare metalli (alluminio, rame) e altri materiali.
     - **Importanza**: Formazione di strati metallici precisi e uniformi per interconnessioni e contatti elettrici.
   - **Pulizia delle Camere di Processo**:
     - **Scopo**: Eliminare residui e contaminanti dalle camere di CVD e PVD.
     - **Importanza**: Mantenere purezza e qualità negli strati depositati, prevenire difetti.
9. **Impiantazione Ionica**:
   - Si introducono ioni dopanti nella fettina per modificare le proprietà elettriche di certe regioni, controllando così la conduttività del materiale.
   - Usi:
     - **Dopaggio di Fonte e Drenaggio nei MOSFET**: Introdurre ioni dopanti nelle regioni di fonte e drenaggio per controllare la conduttività.
     - **Formazione di Pozzi P e N**: Creare regioni drogate di tipo P o N nei dispositivi CMOS.
10. **Planarizzazione**:
    - Si esegue un processo di planarizzazione per livellare la superficie della fettina ed eliminare le irregolarità, garantendo una superficie uniforme per la fase finale di prove e montaggio.
11. **Prove e Montaggio**:
    - Si eseguono prove e misurazioni elettriche per verificare il funzionamento e le caratteristiche del dispositivo fabbricato. Successivamente, la fettina viene tagliata in chip individuali e montata su substrati adeguati per il loro incapsulamento e connessione elettrica.
^1719767189251

### [[1.1.3 Impiantazione]]

### Preparazione della Fettina
*Wafer:* Fettina di silicio monocristallino. Diametro: 75mm a 300mm. Spessore: <1mm
#### [[1.1.1 Metodo Czochralski]]

### [[T.2. Epitassia]]
Dopo aver fabbricato i lingotti di silicio e tagliato i wafer, è necessario ricoprire questi con silicio di maggiore purezza o con una certa cristallinità, qui entra l'epitassia.
L'epitassia è una tecnica di crescita di un film di silicio su un wafer che implica le seguenti caratteristiche:
1. **Temperature Elevate**
2. **Ambiente SiH4**
3. **Replica della Struttura Cristallina del Wafer**
4. **Possibilità di Drogaggio Diverso dal Sottostrato**

### Deposizione di Pellicole Sottili
La deposizione di pellicole sottili è un passaggio critico nella fabbricazione di dispositivi semiconduttori, poiché permette la creazione di strati di diversi materiali su substrati di silicio.

#### Materiali Usati nella Deposizione di Pellicole Sottili e Tecniche
1. **Ossido di Silicio (SiO2)**:
   - L'ossido di silicio è ampiamente utilizzato come *materiale isolante* nei dispositivi semiconduttori, specialmente nella fabbricazione di strutture di porte di transistor a effetto di campo (MOSFET). Funzioni principali:
     - Separazione tra canale e porta nei transistor.
     - Isolamento elettrico tra strati di connessione.
     - Protezione selettiva durante l'impiantazione ionica.
   - Le tecniche comuni di deposizione di ossido di silicio includono:
     - *Deposizione chimica da fase vapore (CVD)(450 a 750 °C)*: Si utilizza tetraetilortosilicato (TEOS) o altri precursori gassosi per depositare SiO2 ad alta temperatura e pressione.
     - *Ossidazione termica (>1000°C)*: Il silicio si ossida in presenza di ossigeno ad alta temperatura, formando uno strato di SiO2 sulla superficie.

2. **Nitruro di Silicio (Si3N4)**:
   - Il nitruro di silicio è utilizzato come materiale isolante e di passivazione nei dispositivi semiconduttori, fornendo protezione contro la diffusione di impurità e migliorando le proprietà meccaniche. Funzioni principali:
     - Isolamento elettrico e strato protettivo durante l'ossidazione.
     - Contatti di porta dei transistor ("gate").
   - La deposizione di nitruro di silicio *si realizza comunemente tramite tecniche di CVD*, utilizzando un precursore di gas come il triclorosilano (SiHCl3) e ammoniaca (NH3) ad alta temperatura *(750°C)*.

3. **Polisilicio (Si)**:
   - Il polisilicio è utilizzato nella fabbricazione di dispositivi come contatti metallici, barriere di diffusione e resistenze a film sottile. Funzioni principali:
     - Interconnessioni.
     - Resistori.
   - Le tecniche di deposizione di polisilicio includono la *deposizione chimica da fase vapore (CVD)(650°C)* utilizzando silano (SiH4) come precursore gassoso.

4. **Metalli**:
   - I metalli sono utilizzati per la fabbricazione di contatti elettrici, interconnessioni ed elettrodi nei dispositivi semiconduttori.
   - Le tecniche comuni di deposizione di metalli includono:
     - *Evapor

azione termica in vuoto*: Il metallo viene riscaldato in un forno di evaporazione e depositato sul substrato.
     - *Sputtering*: Si bombarda un target di metallo con ioni per liberare atomi di metallo che si depositano sul substrato.

#### Evaporazione Termica in Vuoto

L'evaporazione termica in vuoto è un metodo comunemente utilizzato per depositare pellicole sottili di metalli su substrati. Il processo implica il riscaldamento del materiale di metallo, tipicamente in forma di filo o pellet, all'interno di una camera a vuoto. Man mano che il materiale si riscalda, gli atomi o le molecole del metallo si vaporizzano e si condensano sul substrato, formando una pellicola sottile. Ecco alcuni aspetti chiave della tecnica di evaporazione termica in vuoto:

1. **Riscaldamento del Materiale**:
   - Il materiale di metallo viene riscaldato utilizzando una fonte di calore, come un filamento resistivo o un fascio di elettroni.
   - La temperatura di riscaldamento è controllata attentamente per raggiungere il punto di evaporazione del metallo senza surriscaldare o danneggiare il substrato.

2. **Generazione di Vapore**:
   - Man mano che il metallo si riscalda, gli atomi o le molecole del metallo si vaporizzano e si spostano attraverso la camera a vuoto verso il substrato.

3. **Deposizione sul Substrato**:
   - Gli atomi o le molecole vaporizzate del metallo si condensano sulla superficie del substrato, formando una pellicola sottile di metallo.

4. **Controllo dello Spessore e della Uniformità**:
   - Lo spessore e la uniformità della pellicola depositata sono controllati tramite la durata dell'evaporazione e la velocità di deposizione.

#### Sputtering

Lo sputtering è un'altra tecnica ampiamente utilizzata per depositare pellicole sottili di metalli su substrati. In questo processo, si bombarda un target di metallo con ioni in un vuoto, il che genera l'espulsione di atomi del metallo. Questi atomi espulsi si depositano sul substrato, formando una pellicola sottile. Ecco gli aspetti chiave del processo di sputtering:

1. **Bombardamento di Ioni**:
   - Si utilizzano ioni, generalmente di un gas inerte come argon, per bombardare il target di metallo all'interno di una camera a vuoto.

2. **Espulsione di Atomi**:
   - Il bombardamento di ioni causa l'espulsione di atomi dal materiale del target di metallo, che si spostano attraverso la camera a vuoto.

3. **Deposizione sul Substrato**:
   - Gli atomi espulsi si depositano sulla superficie del substrato, formando una pellicola sottile di metallo.

4. **Controllo dello Spessore e della Uniformità**:
   - Lo spessore e la uniformità della pellicola depositata sono controllati tramite la durata del bombardamento di ioni e la velocità di deposizione.

### [[1.1.2 Fotolitografia]]

### Attacco (Etching) #tarjeta-anki 
#### Tipi di Etching
1. **Wet Etching (Incisione Umida)**:
    - **Descrizione**: Uso di soluzioni chimiche liquide per incidere il materiale del substrato.
    - **Vantaggi**: Semplice ed economico.
    - **Svantaggi**: Può essere meno selettivo e meno controllato in termini di direzione dell'incisione.
2. **Dry Etching (Incisione Secca)**:
    - **Descrizione**: Uso di plasmi e gas reattivi per incidere il materiale.
    - **Vantaggi**: Più controllato, permette un'incisione anisotropica.
    - **Svantaggi**: Richiede attrezzature più complesse e costose.
- L'incisione anisotropica (secca) fornisce una maggiore direzionalità nell'attacco rispetto all'uso di acidi.
  - È più lenta e meno selettiva rispetto ai metodi chimici, ma offre un controllo migliore nel processo di incisione.
#### Attacco Secco
- **Sputtering Etching** e **Plasma Etching** sono due tecniche di incisione secca.
  - **Sputtering Etching** utilizza principalmente il trasferimento di momento degli ioni inerti per rimuovere il materiale.
  - **Plasma Etching** utilizza sia reazioni chimiche (specie reattive) sia bombardamento ionico (specie ioniche) per rimuovere il materiale.
##### Sistema di Piastra Parallela
- **Sistemi di Piastra Parallela** sono configurazioni di apparecchiature utilizzate in questi processi di incisione secca:
###### Modo Plasma
1. **Elettrodi di Aree Uguali**:
    - **Descrizione**: Gli elettrodi hanno aree uguali o l'elettrodo del wafer è collegato a terra insieme alla camera.
    - **Voltaggio nella Guaina**: Moderato (10-100V), risultando in un componente ionico moderato e un forte componente chimico.
    - **Applicazioni**: Incisione relativamente isotropica (uniforme in tutte le direzioni) e selettiva con poco danno al substrato.
    - **Pressione**: 100 mtorr - 1 torr.
###### Modo RIE (Reactive Ion Etching)
2. **Elettrodi di Aree Diverse**:
    - **Descrizione**: I wafer sono posizionati sull'elettrodo più piccolo, dove viene applicata la potenza RF.
    - **Maggiore Caduta di Voltaggio nella Guaina**: 100-700V, risultando in un bombardamento ionico più forte.
    - **Direzionalità**: Maggiore direzionalità nell'incisione (più anisotropica) a causa della maggiore energia degli ioni.
    - **Pressione**: 10-100 mtorr.
- **Maggiore Pressione in RIE e Plasma Etching**: Si richiede di aumentare la pressione rispetto a quella usata nello sputtering per migliorare l'efficienza dell'incisione.
^1719767189258






# Espagnolo
## Processi di fabbricazione dei dispositivi
![[Pasted image 20240315120609.png]]
1. **Progettazione (Diseño)**:
   - Esta etapa establece las especificaciones y características del dispositivo, y no se puede cambiar una vez iniciado el proceso, ya que condiciona todo el proceso de fabricación.
2. **Preparazione de las fetas (Preparación de las Obleas)**:
    - Se inspeccionan y limpian las obleas de silicio, que pueden haber sido cortadas de lingotes producidos por el método Czochralski. Esta limpieza es esencial para eliminar contaminantes y asegurar una superficie adecuada para el crecimiento de capas epitaxiales.
3. **Epitaxia**:
    - Después de la preparación de las obleas, se lleva a cabo la epitaxia sobre las mismas. Este proceso deposita capas cristalinas adicionales sobre las obleas con orientaciones y características específicas, ampliando las posibilidades de diseño y funcionalidad del dispositivo.
4. **Procesamiento de las fetas**:
   - **Oxidación térmica**: Se forma una capa de óxido de silicio sobre la superficie de la oblea mediante un proceso de oxidación térmica. Esta capa actua como barrera dieletrica y una capa de proteccion
   - **Deposición de nitruro de silicio**: Se deposita una capa de nitruro de silicio sobre la capa de óxido utilizando la técnica de deposición química en fase vapor a baja presión (CVD). Esta capa se usa como barrera de difusion, como capa de proteccion durante el grabado y es un aislante termico adicional.
   - **Deposición de polisilicio**: Se deposita una capa de polisilicio sobre la capa de nitruro de silicio también utilizando la técnica de CVD a baja presión. Este es colocado para formar las puertas de los transistores MOSFET
5. **Fotolitografia**:
   - Se aplican procesos de deposición de fotoresistencias sobre la superficie de la oblea, seguidos de procesos de exposición para definir patrones en la capa de fotoresistencias.
6. **Ataque**:
   - Se utiliza un proceso de ataque químico para eliminar selectivamente las áreas expuestas de óxido, nitruro de silicio y polisilicio, revelando las áreas deseadas de la oblea.
   - Proposito
	   - **Definición de Estructuras**: Eliminar material en áreas específicas para crear patrones y estructuras en las capas de materiales depositados.
	  - **Formación de Pistas y Vías**: Crear canales, contactos y otras estructuras tridimensionales necesarias para el dispositivo.
7. **Limpieza**:
   - Se realiza una limpieza exhaustiva de la oblea para eliminar cualquier residuo de los procesos anteriores, tanto antes como después de la deposición de materiales y el ataque selectivo. También se elimina la capa de fotoresistencias.
8. **Film sottili:
- **Deposición Química en Fase Vapor (CVD) de Dieléctricos**:
    - **Propósito**: Formar capas dieléctricas (óxido de silicio, nitruro de silicio).
    - **Importancia**: Aislamiento eléctrico, protección de superficie, base para fotolitografía.
- **CVD de Tungsteno**:
    - **Propósito**: Depositar interconexiones metálicas de tungsteno.
    - **Importancia**: Excelente conductividad eléctrica, alta resistencia térmica.
- **Deposición Física en Fase Vapor (PVD)**:
    - **Propósito**: Depositar metales (aluminio, cobre) y otros materiales.
    - **Importancia**: Formación de capas metálicas precisas y uniformes para interconexiones y contactos eléctricos.
- **Limpieza de Cámaras de Proceso**:
    - **Propósito**: Eliminar residuos y contaminantes de las cámaras de CVD y PVD.
    - **Importancia**: Mantener pureza y calidad en las capas depositadas, prevenir defectos.
9. **Implantación Iónica**:
   - Se introducen iones dopantes en la oblea para modificar las propiedades eléctricas de ciertas regiones, controlando así la conductividad del material.
   - Usos:
	   - **Dopaje de Fuente y Drenaje en MOSFETs**: Introducir iones dopantes en las regiones de fuente y drenaje para controlar la conductividad.
	   - **Formación de Pozos P y N**: Crear regiones dopadas de tipo P o N en dispositivos CMOS.
10. **Planarización**:
   - Se realiza un proceso de planarización para nivelar la superficie de la oblea y eliminar irregularidades, asegurando una superficie uniforme para la etapa final de pruebas y montaje.
11. **Pruebas y Montaje**:
    - Se realizan pruebas y mediciones eléctricas para verificar el funcionamiento y las características del dispositivo fabricado. Luego, la oblea se corta en chips individuales y se monta en sustratos adecuados para su encapsulado y conexión eléctrica.




### [[T.1.1.3 Impiantazion]]

### Preparacion de la feta
*Wafer:* Feta de silicio monocristalino. Diametro: 75mm a 300mm. Spessore: <1mm
#### [[T.1.1.1Metodo Czocharlski]]

### [[T.2. Epitassia]]
Luego de fabricar los lingotes de silicios y cortar los wafer, hace falta recubrir estos son silicio de mayor pureza o con cierta cristalinidad, ahi entra la epitaxia.
La epitaxia es una técnica de crecimiento de una película de silicio sobre un wafer que implica las siguientes características:
1. **Temperaturas Elevadas**
2. **Ambiente SiH4**
3. **Replica de la Estructura Cristalina del Wafer**
4. **Posibilidad de Drogado Diferente del Substrato**.



### Deposicion de pelicula delgadas
La deposición de películas delgadas es un paso crítico en la fabricación de dispositivos semiconductores, ya que permite la creación de capas de diferentes materiales sobre sustratos de silicio. 

#### Materiales usados en la deposicion de peliculas delgadas y tecnicas
1. **Óxido de Silicio (SiO2)**:
   - El óxido de silicio es ampliamente utilizado como *material aislante* en dispositivos semiconductores, especialmente en la fabricación de estructuras de puertas de transistores de efecto de campo (MOSFET). Funciones principales:
	   - Separación entre canal y puerta en transistores.
	   - Aislamiento eléctrico entre estratos de conexión.
	   - Protección selectiva durante la implantación iónica.
   - Las técnicas comunes de deposición de óxido de silicio incluyen:
     - *Depósito químico de vapor (CVD)(450 a 750 °C)*: Se utiliza tetraetilortosilicato (TEOS) u otros precursores gaseosos para depositar SiO2 a alta temperatura y presión.
     - *Oxidación térmica(>1000°C):* El silicio se oxida en presencia de oxígeno a alta temperatura, formando una capa de SiO2 en la superficie.

2. **Nitruro de Silicio (Si3N4)**:
   - El nitruro de silicio se utiliza como material aislante y de pasivación en dispositivos semiconductores, proporcionando protección contra la difusión de impurezas y mejorando las propiedades mecánicas. Funciones principales:
	   - Aislamiento eléctrico y capa protectora durante la oxidación.
	   - Contactos de puerta de los transistores ("gate").
   - La deposición de nitruro de silicio *se realiza comúnmente mediante técnicas de CVD*, donde se utiliza un precursor de gas como el triclorosilano (SiHCl3) y amoníaco (NH3) a alta temperatura*(750°C)*.

3. **Polisilicio (Si)**:
   - El polisilicio se utiliza en la fabricación de dispositivos como contactos metálicos, barreras de difusión y resistencias de capa delgada. Funciones principales:
	   -  Interconexiones.
	   - Resistores.
   - Las técnicas de deposición de polisilicio incluyen la *deposición química de vapor (CVD)(650°C)* utilizando silano (SiH4) como precursor gaseoso.

4. **Metales**:
   - Los metales se utilizan para la fabricación de contactos eléctricos, interconexiones y electrodos en dispositivos semiconductores.
   - Las técnicas comunes de deposición de metales incluyen:
     - *Evaporación térmica en vacío:* El metal se calienta en un horno de evaporación y se deposita sobre el sustrato.
     - *Sputtering:* Se bombardea un blanco de metal con iones para liberar átomos de metal que se depositan sobre el sustrato.



#### Evaporación Térmica en Vacío:

La evaporación térmica en vacío es un método comúnmente utilizado para depositar películas delgadas de metales en sustratos. El proceso implica calentar el material de metal, típicamente en forma de alambre o pellets, dentro de una cámara de vacío. A medida que el material se calienta, los átomos o moléculas del metal se vaporizan y se condensan sobre el sustrato, formando una película delgada. Aquí hay algunos aspectos clave de la técnica de evaporación térmica en vacío:

1. **Calentamiento del Material:**
   - El material de metal se calienta utilizando una fuente de calor, como un filamento resistivo o un haz de electrones.
   - La temperatura de calentamiento se controla cuidadosamente para alcanzar el punto de evaporación del metal sin sobrecalentar o dañar el sustrato.

2. **Generación de Vapor:**
   - A medida que el metal se calienta, los átomos o moléculas del metal se vaporizan y se desplazan a través de la cámara de vacío hacia el sustrato.

3. **Deposición sobre el Sustrato:**
   - Los átomos o moléculas vaporizados del metal se condensan sobre la superficie del sustrato, formando una película delgada de metal.

4. **Control de Espesor y Uniformidad:**
   - El grosor y la uniformidad de la película depositada se controlan mediante la duración de la evaporación y la velocidad de deposición.

#### Sputtering

El sputtering es otra técnica ampliamente utilizada para depositar películas delgadas de metales sobre sustratos. En este proceso, se bombardea un blanco de metal con iones en un vacío, lo que genera la expulsión de átomos del metal. Estos átomos expulsados se depositan sobre el sustrato, formando una película delgada. Aquí están los aspectos clave del proceso de sputtering:

1. **Bombardeo de Iones:**
   - Se utilizan iones, generalmente de un gas inerte como argón, para bombardear el blanco de metal dentro de una cámara de vacío.

2. **Expulsión de Átomos:**
   - El bombardeo de iones causa la expulsión de átomos del material del blanco de metal, que se desplazan a través de la cámara de vacío.

3. **Deposición sobre el Sustrato:**
   - Los átomos expulsados se depositan sobre la superficie del sustrato, formando una película delgada de metal.

4. **Control de Espesor y Uniformidad:**
   - El grosor y la uniformidad de la película depositada se controlan mediante la duración del bombardeo de iones y la tasa de deposición.


### [[T.1.1.2Fotolitografia]]

### Attaco (Etching)

#### Tipi di Etching

1. **Wet Etching (Incisione Umida)**:
    - **Descrizione**: Uso di soluzioni chimiche liquide per incidere il materiale del substrato.
    - **Vantaggi**: Semplice ed economico.
    - **Svantaggi**: Può essere meno selettivo e meno controllato in termini di direzione dell'incisione.
2. **Dry Etching (Incisione Secca)**:
    - **Descrizione**: Uso di plasmi e gas reattivi per incidere il materiale.
    - **Vantaggi**: Più controllato, permette un'incisione anisotropica.
    - **Svantaggi**: Richiede attrezzature più complesse e costose.

- L'incisione anisotropica (secca) fornisce una maggiore direzionalità nell'attacco rispetto all'uso di acidi.
	- È più lenta e meno selettiva rispetto ai metodi chimici, ma offre un controllo migliore nel processo di incisione.
#### Atacco Secco
- **Sputtering Etching** e **Plasma Etching** sono due tecniche di incisione secca.
    - **Sputtering Etching** utilizza principalmente il trasferimento di momento degli ioni inerti per rimuovere il materiale.
    - **Plasma Etching** utilizza sia reazioni chimiche (specie reattive) sia bombardamento ionico (specie ioniche) per rimuovere il materiale.
##### Sistema di piastra parallela
- **Sistemi di Piastra Parallela** sono configurazioni di apparecchiature utilizzate in questi processi di incisione secca:
###### Modo Plasma

1. **Elettrodi di Aree Uguali**:
    - **Descrizione**: Gli elettrodi hanno aree uguali o l'elettrodo del wafer è collegato a terra insieme alla camera.
    - **Voltaggio nella Guaina**: Moderato (10-100V), risultando in un componente ionico moderato e un forte componente chimico.
    - **Applicazioni**: Incisione relativamente isotropica (uniforme in tutte le direzioni) e selettiva con poco danno al substrato.
    - **Pressione**: 100 mtorr - 1 torr.

###### Modo RIE (Reactive Ion Etching)

2. **Elettrodi di Aree Diverse**:
    - **Descrizione**: I wafer sono posizionati sull'elettrodo più piccolo, dove viene applicata la potenza RF.
    - **Maggiore Caduta di Voltaggio nella Guaina**: 100-700V, risultando in un bombardamento ionico più forte.
    - **Direzionalità**: Maggiore direzionalità nell'incisione (più anisotropica) a causa della maggiore energia degli ioni.
    - **Pressione**: 10-100 mtorr.

- **Maggiore Pressione in RIE e Plasma Etching**: Si richiede di aumentare la pressione rispetto a quella usata nello sputtering per migliorare l'efficienza dell'incisione.
