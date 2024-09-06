---
cards-deck: Profesional::Universidad::UNISA::Segundo Cuatrimestre::Nanoeletronica
---


# Italiano

## Introduzione
### Film Depositi tramite CVD
La Deposizione Chimica in Fase Vapore (CVD) è un processo versatile che permette di depositare una varietà di materiali in forma di film sottili su substrati. Alcuni dei materiali che si possono depositare mediante CVD includono:
- *Silicio Policristallino:* Utilizzato per gate e altre applicazioni.
- *Ossido di Silicio:* Deposito per creare strati isolanti o protettivi.
- *Nitruro di Silicio:* Utilizzato come strato protettivo esterno.
- *Metalli:* Depositi per realizzare contatti tra diversi livelli.
- *Siliciuri:* Utilizzati come strati intermedi tra il silicio e il metallo per evitare la formazione di unioni Schottky.

### Concetti di Base della CVD #tarjeta-anki 
![[Pasted image 20240514102412.png|400]]
- CVD: reazione chimica che trasforma molecole gassose,![[Pasted image 20240514102327.png|20]] dette precursori in materiale solido in forma di film sottile,![[Pasted image 20240514102340.png|30]] sopra il substrato ![[Pasted image 20240514102403.png|40]]
- *CVD: Formazione di un film solido sopra un substrato attraverso la reazione di specie chimiche in fase gassosa*
^1719958028164


### Tipologie Comuni di CVD

- **APCVD (Atmospheric Pressure CVD):** CVD a pressione atmosferica.
- **LPCVD (Low Pressure CVD):** CVD a bassa pressione.
- **PECVD (Plasma Enhanced CVD):** CVD migliorato al plasma.
- **HDP-CVD (High Density Plasma CVD):** CVD a plasma ad alta densità.

Indipendentemente dal tipo, i sistemi CVD utilizzano gas che si decompongono e reagiscono sulla superficie per formare il film. In alcuni casi, viene utilizzata una sorgente liquida trasportata nella camera di reazione tramite un gas trasportatore, come ad esempio l'idrogeno.

## Fondamenti CVD
### Processo CVD #tarjeta-anki 
- El processo é il stesso che in espitassia
![[Pasted image 20240626183731.png]]
1. Introduzione di gas reattivi e diluenti nella camera di processo a una composizione e flusso specifici.
2. Trasporto delle specie reattive verso il substrato.
3. Adsorbimento delle specie reattive sulla superficie del substrato.
4. Migrazione delle specie reattive sulla superficie e reazione chimica per formare il film desiderato.
5. Desorbimento dei sottoprodotti di reazione.
6. Trasporto dei sottoprodotti di reazione fuori dalla regione di flusso principale.
7. Eliminazione dei sottoprodotti gassosi di reazione e dei gas non consumati dalla camera di reazione.
^1719958028167

![[Pasted image 20240514102731.png]]
- La CVD segue un processo simile all'epitassia, ma con una sostanziale differenza nel regime di lavoro.
- In CVD, si opera in un *regime di reazione in superficie*.
- Anche si fa un analisi con il modello di Grove

### [[T.2. Epitassia#Proceso de Epitaxia por CVD]]

### [[T.2. Epitassia#Modelo de Crecimiento Atómico]]

![[Pasted image 20240626184552.png]]


#### Regimi di Reazione CVD #tarjeta-anki 
Fornendo energia alla reazione, si osservano tre regimi:
1. **Basse temperature:** La velocità di reazione è bassa e la deposizione dipende in gran parte dalla temperatura. Questo *regime è limitato dalla reazione* sulla superficie.
2. **Temperature elevate:** La deposizione diventa meno sensibile ai cambiamenti di temperatura ed è *limitata dal trasporto di massa*. I precursori reagiscono rapidamente al momento dell'adsorbimento sulla superficie del substrato.
3. **Temperature molto alte:** La velocità di deposizione diminuisce a causa della *nucleazione in fase gassosa*, il che risulta in un processo indesiderabile.
- La morfologia dei film depositati, inclusa la dimensione dei grani e la rugosità, è influenzata dalle condizioni di deposizione e dai trattamenti termici successivi. A temperature più alte e per film più spessi, si ottengono grani più grandi.
- La rugosità è connessa con la dimensione dei grani.
^1719958028172


#### Velocità di Reazione Superficiale
La velocità di reazione superficiale può essere espressa come una funzione della temperatura:
$$CR = A * e^{(-Ea/kT)}$$
Dove CR è la velocità di reazione, A è una costante, Ea è l'energia di attivazione, k è la costante di Boltzmann, e T è la temperatura del substrato.

- Nel *regime limitato dalla reazione*, la velocità di deposizione è *molto sensibile ai cambiamenti di temperatura* a causa della velocità della reazione chimica.
	- È *necessaria una buona uniformità della temperatura* sul substrato.
- Nel *regime limitato dal trasporto di massa*, la velocità di deposizione dipende dal *trasporto efficiente dei precursori* alla superficie.
	- È necessaria una *buona uniformità del flusso* e della densità della specie attiva sul substrato.
- Al raggiungimento di certe temperature, la velocità di reazione è determinata dalla velocità dei reagenti che arrivano sulla superficie del substrato.


### Dinamica dei Fluidi
![[Pasted image 20240514114143.png|300]]
La dinamica dei fluidi all'interno di un reattore di deposizione è fondamentale per comprendere il comportamento dei gas reattivi e i loro profili di velocità e temperatura. 
- *Il profilo di velocità* in un reattore tubolare tipico mostra che la velocità del fluido sulla superficie del reattore è zero e aumenta man mano che ci si allontana dalle pareti. A una distanza specifica, il profilo assume una forma parabolica.
#### Profili di Temperature
- La concentrazione dei gas reattivi varia a seconda del design del reattore. 
  - In un reattore con pareti calde, la concentrazione di reagenti è più alta vicino alle pareti riscaldate.
	  - I gas a contatto con le pareti si riscaldano per primi, e man mano che fluiscono attraverso il reattore, i gas vicini al centro aumentano anche la loro temperatura.
	  - In un reattore sufficientemente lungo, si raggiunge una temperatura uniforme del gas.
  - ![[Pasted image 20240514114224.png|300]]
  - In un reattore con pareti fredde, la concentrazione sulla superficie del substrato è zero e aumenta rapidamente man mano che ci si allontana da essa.
	  - la temperatura del gas è più alta sulla superficie del substrato e diminuisce rapidamente verso un valore costante, creando un gradiente di temperatura.
  - ![[Pasted image 20240514114203.png|300]]
#### Influenza della Geometria 
La geometria del reattore e del substrato può influenzare anche la dinamica dei fluidi.
- Nella deposizione epitassiale del silicio ad alte temperature, il processo è controllato dal trasferimento di massa dalla fase di vapore alla superficie del substrato.
- Il coefficiente di trasferimento di massa, $h_G=\frac{D_G}{\delta_S}$, è correlato alla diffusione delle specie reattive attraverso uno strato limite di spessore variabile $\delta_S$.
	- Ma $\delta_S$ non e costante nella misura in cui il gas fluisce lungo la superficie.
- Per ottenere una deposizione uniforme, si può inclinare il substrato, aumentando la velocità del gas e mantenendo $\delta_S$ costante.
![[Pasted image 20240514114127.png|300]]



## Tipi CVD #tarjeta-anki 
![[Pasted image 20240627132512.png]]
^1719958028176



### [[T.2. Epitassia]]
### LPCVD (Deposizione Chimica da Fase Vapore a Bassa Pressione)
#### Sistemi APCVD
![[Pasted image 20240523093434.png]]
- I sistemi CVD a pressione atmosferica (APCVD) presentano alcune sfide, soprattutto quando è necessaria una deposizione ad alte temperature(per ottenere una crecita di mono cristallo di elevata qualitá), In tali casi, si deve utilizzare una configurazione orizzontale, poiché il flusso deve essere identico su tutti i substrati, processando solo poche wafer in ogni ciclo.
- Se la deposizione avviene a basse temperature, la velocità di deposizione diminuisce, risultando in una bassa resa del processo.
- È sensibile alle reazioni in fase gassosa (reazioni omogenee) → Formazione di particolato e film poco denso.
- È utilizzato per la deposizione di $SiO_2$ a bassa temperatura

**Vantaggi:**
- Struttura del reattore abbastanza semplice.
- Elevate velocità di deposizione.

#### Soluzione a Bassa Pressione LPCVD
$h_G=\frac{D_G}{\delta_S}$, anche $D_G$ e $\delta_S$ sono inversamente proporzionali alla pressione, ma $D_g$ aumenti piú quando diminuimo la pressione.
![[Pasted image 20240514115135.png|300]]
- Una soluzione a questi problemi è operare a bassa pressione, nel regime limitato dal trasporto di massa.
- Riducendo la pressione, la distanza di diffusione $D_G$ aumenta significativamente, mentre $\delta_s$ aumenta poco, quindi,  aumenta a sua volta il coefficiente di trasferimento di massa $h_G$ di circa 100 volte.
- Questo significa che il trasporto di reagenti in fase gassosa verso la superficie del substrato attraverso lo strato limite non è più il fattore limitante nella velocità di crescita.
- A bassa pressione, il processo diventa molto più sensibile alla temperatura.

##### LPCVD orizzontale a parete calda
![[Pasted image 20240514115239.png|300]]
- Si può utilizzare un sistema a parete calda per un migliore controllo della temperatura, e anche è possibile impilare le wafer, processando più substrati simultaneamente (fino a circa 200).
- Inoltre, una pressione residua di 0,25 a 2,0 Torr aumenta ulteriormente la diffusività delle specie reattive (fino a 1000 volte).

**Le Caratteristiche di un Sistema LPCVD**
- Riduzione delle reazioni in fase gassosa, diminuendo la generazione di particelle indesiderate.
- Buona uniformità nella deposizione.
- Buona copertura degli scalini.
- Velocità di deposizione relativamente basse (10-50 nm/min).
- L'uniformità della temperatura è più critica rispetto all'uniformità del flusso di gas, permettendo l'uso di un forno convenzionale.

##### Applicazioni di LPCVD
Il LPCVD è comunemente utilizzato per la deposizione di silicio policristallino, nitruro di silicio (Si3N4), ossido di silicio (SiO2), PSG, BPSG e tungsteno (W), tra altri materiali. Un design tipico di reattore LPCVD è orizzontale con pareti calde, permettendo di processare un gran numero di substrati in ogni ciclo.

### PECVD (Deposizione Chimica da Fase Vapore Potenziata dal Plasma)

#### Introduzione
- I reattori CVD assistiti dal plasma (PECVD) operano in un *regime limitato dalla velocità di reazione*, risultando in velocità di deposizione più alte rispetto alla deposizione LPCVD.
- PECVD *può operare a temperature più basse* rispetto ai processi APCVD e LPCVD, *permettendo la deposizione di film di SiO2 e Si3N4 su metalli con bassi punti di fusione, come l'alluminio.*

#### Principio del Metodo
- Utilizza una sorgente di tensione o corrente oscillante a radiofrequenza (tipicamente 13.56 MHz o 100 KHz) *per ionizzare parte delle molecole dei gas precursori, generando radicali molto reattivi pronti per legarsi al substrato*.
- Il gas parzialmente ionizzato generato in questi processi è detto plasma.
- La presenza di RF permette temperature di processo relativamente basse.
#### Caratteristiche del PECVD
- **Velocità di Deposizione**: Elevata velocità di deposizione grazie al plasma, maggiore rispetto alla deposizione LPCVD.
- **Temperatura di Processo**: Opera a temperature inferiori rispetto ai processi APCVD e LPCVD.
- **Adesione e Copertura dei Gradini**: Buona adesione e copertura dei gradini dovuta alla maggiore mobilità superficiale delle specie adsorbite.
- **Composizione del Film**: I film depositati spesso non hanno una composizione stechiometrica e possono contenere sottoprodotti di reazione incorporati (idrogeno, ossigeno, azoto).
  - **Problemi Potenziali**: Degasificazione durante i passi di lavorazione successivi, formazione di bolle e delaminazione del film.
- **Complessità del Processo**: Processo più complesso con più parametri da controllare attentamente.
- **Materiali Depositabili**: SiO2, Si3N4, ossinitruri, SiC, silicio amorfo (a-Si), e altro. PECVD a temperature molto alte permette anche la crescita epitassiale di Si, Ge e composti III-V.

#### Struttura e Proprietà dei Film di Silicio Depositati tramite PECVD
- **Struttura**:
  - Generalmente amorfa e compatta, ma può essere microcristallina in condizioni particolari (alta diluizione di idrogeno).
  - Ordine a corto raggio (primi vicini) e disordine a lungo raggio dovuto a fluttuazioni delle distanze e angoli di legame.
  - Presenza di difetti sotto forma di legami non saturi che formano trappole e centri di ricombinazione per i portatori di carica.
  - La flessibilità della struttura amorfa permette di formare leghe a stechiometria variabile in modo continuo con C, O, N, Ge, Sn.
- **Conseguenze**:
  - La variabilità composizionale comporta la variabilità delle caratteristiche ottiche ed elettriche, che, nonostante i difetti elettricamente attivi, permette di preparare leghe "su misura" per applicazioni diverse.
#### Reattori PECVD
- **Reattore di Flusso Radiale (Elettrodi Paralleli)**:
![[Pasted image 20240514121636.png|300]]
  - Temperatura di lavorazione relativamente bassa.
  - Capacità di lavorazione limitata.
  - Operazione manuale.
  - Può generare particelle che si depositano sul substrato o film.

- **Reattore di Capacità (Elettrodi Contrapposti)**:
![[Pasted image 20240514121625.png|300]]
  - Le wafer sono posizionate verticalmente e in parallelo al flusso di gas.
  - Maggiore capacità di lavorazione.
  - Temperatura di processo ancora più bassa.
  - Operazione manuale.
  - Può generare particelle.

##### Schema di un Impianto di Deposizione PECVD
![[Pasted image 20240514121607.png|300]]
![[Pasted image 20240628180807.png|300]]
- Il sistema include un controller di temperatura, catodo, anodo, alimentazione RF, rete di adattamento, misuratore di vuoto, substrato, sistema di pompaggio e controllo del gas di zavorra.
- L'alimentazione RF genera una frequenza diversa dalla radiofrequenza, e la rete di adattamento garantisce un trasferimento di potenza ottimale, critica a causa delle variazioni di impedenza del plasma.
- Si utilizza Ar per la pulizia, non è controllato ma è simile alla pulizia con acqua.

### RPECVD (PECVD Potenziata dal Reattore a Risonanza Elettronica)
![[Pasted image 20240627132401.png]]
- I reattori CVD a plasma remoto, anche noti come RPECVD o PECVD indiretta, utilizzano un approccio unico in cui la camera di generazione del plasma è separata dalla camera in cui si trova il substrato. Questa separazione garantisce che i substrati non siano esposti direttamente alla radiazione del plasma e al bombardamento di ioni ad alta energia.

#### ECR (Electron Cyclotron Resonance)
- Il plasma è generato da un campo elettrico a microonde in presenza di un campo magnetico. Questa configurazione provoca una risonanza ciclotronica degli elettroni, risultando in una densità di plasma circa 100 volte maggiore in specie reattive rispetto ad altri reattori PECVD.
- Si utilizza un reattore ECR per generare elettroni rotanti che possono rompere molti legami. Questa tecnica è utile perché il plasma di solito è un po' sporco.



























































# Español
## CVD
### Introduzione
#### Film Depositi tramite CVD
La Deposición Química en Fase Vapor (CVD) es un proceso versátil que permite depositar una variedad de materiales en forma de películas delgadas sobre sustratos. Algunos de los materiales que se pueden depositar mediante CVD incluyen:
- *Silicio Policristallino:* Utilizzato per gate e altre applicazioni.
- *Ossido di Silicio:* Deposito per creare strati isolanti o protettivi.
- *Nitruro di Silicio:* Utilizzato come strato protettivo esterno.
- *Metalli:* Depositi per realizzare contatti tra diversi livelli.
- *Siliciuri:* Utilizzati come strati intermedi tra il silicio e il metallo per evitare la formazione di unioni Schottky.

#### Concetti di Base della CVD
![[Pasted image 20240514102412.png|400]]
- CVD: reazione chimica che trasforma molecole gassose,![[Pasted image 20240514102327.png|20]] dette precursori in materiale solido in forma di film sottile,![[Pasted image 20240514102340.png|30]] sopra il substrato ![[Pasted image 20240514102403.png|40]]
- *CVD: Formazione di un film solido sopra un substrato attraverso la reazione di specie chimiche in fase gassosa*


#### Tipologie Comuni di CVD

- **APCVD (Atmospheric Pressure CVD):** CVD a pressione atmosferica.
- **LPCVD (Low Pressure CVD):** CVD a bassa pressione.
- **PECVD (Plasma Enhanced CVD):** CVD migliorato al plasma.
- **HDP-CVD (High Density Plasma CVD):** CVD a plasma ad alta densità.

Indipendentemente dal tipo, i sistemi CVD utilizzano gas che si decompongono e reagiscono sulla superficie per formare il film. In alcuni casi, viene utilizzata una sorgente liquida trasportata nella camera di reazione tramite un gas trasportatore, come ad esempio l'idrogeno.

### Processo CVD

#### Passi del processo CVD
1. Introducción de gases reactivos y diluyentes en la cámara de proceso a una composición y flujo específicos.
2. Transporte de las especies reactivas hacia el sustrato.
3. Adsorción de las especies reactivas sobre la superficie del sustrato.
4. Migración de las especies reactivas sobre la superficie y reacción química para formar la película deseada.
5. Desorción de los subproductos de reacción.
6. Transporte de los subproductos de reacción fuera de la región de flujo principal.
7. Eliminación de los subproductos gaseosos de reacción y de los gases no consumidos de la cámara de reacción.
#### Processo Simile all'Epitassia
![[Pasted image 20240514102731.png]]
- La CVD segue un processo simile all'epitassia, ma con una sostanziale differenza nel regime di lavoro.
- In CVD, si opera in un *regime di reazione in superficie*.
- Anche si fa un analisi con il modello di Grove


### Reazioni Chimiche nei Processi

- Las reacciones químicas en los procesos de deposición están iniciadas por diferentes fuentes de energía, incluyendo térmica, fotones o electrones. 
- Estas reacciones pueden ser homogéneas, que ocurren en la fase de vapor y pueden resultar en partículas indeseables, o heterogéneas, que tienen lugar en la superficie o cerca de ella, lo que es deseable. 

#### Regimnes de reaccion
Al proporcionar energía a la reacción, se observan tres regímenes:
1. **Bajas temperaturas:** La velocidad de reacción es baja y la deposición depende en gran medida de la temperatura. Este *régimen está limitado por la reacción* en la superficie.
2. **Temperaturas elevadas:** La deposición se vuelve menos sensible a cambios de temperatura y está *limitada por el transporte de masa*. Los precursores reaccionan rápidamente al ser adsorbidos en la superficie del sustrato
3. **Temperaturas muy altas:** La velocidad de deposición disminuye debido a la *nucleación en fase gaseosa*, lo que resulta en un proceso indeseable.

- La morfología de las películas depositadas, incluyendo el tamaño de los granos y la rugosidad, está influenciada por las condiciones de deposición y tratamientos térmicos posteriores. A temperaturas más altas y para películas más gruesas, se obtienen granos más grandes.
- La rugosidad esta conectada con la dimensione de los granos


#### Velocidad de reaccion superficial
La velocidad de reacción superficial se puede expresar como una función de la temperatura:
$$CR = A * e^{(-Ea/kT)}$$
Donde CR es la velocidad de reacción, A es una constante, Ea es la energía de activación, k es la constante de Boltzmann, y T es la temperatura del sustrato.

- En el régimen limitado por reacción, la velocidad de deposición es muy sensible a cambios en la temperatura debido a la velocidad de la reacción química. 
	- Es necesaria una buena uniformidad de la temperatura sobre el substracto
- Mientras que en el régimen limitado por transporte de masa, la velocidad de deposición depende del transporte eficiente de precursores a la superficie.
	- Es necesario una buena uniformidad del flujo y de la densidad de la especie activa sobre el substracto
- Al alcanzar ciertas temperaturas, la velocidad de reacción se determina por la velocidad de los reactivos que llegan a la superficie del sustrato

### Dinamica de fluidos
![[Pasted image 20240514114143.png|300]]
La dinámica de fluidos dentro de un reactor de deposición es fundamental para comprender el comportamiento de los gases reactivos y sus perfiles de velocidad y temperatura. 
- *El perfil de velocidad* en un reactor tubular típico muestra que la velocidad del fluido en la superficie del reactor es cero y aumenta a medida que nos alejamos de las paredes. A una distancia específica, el perfil asume una forma parabólica.

#### Perfiles de temperaturas
- La concentración de gases reactivos varía según el diseño del reactor. 
	- En un reactor con paredes calientes, la concentración de reactivos es más alta cerca de las paredes calentadas.![[Pasted image 20240514114224.png|300]]
	- En un reactor con paredes frías, la concentración en la superficie del sustrato es cero y aumenta rápidamente a medida que nos alejamos de la misma. ![[Pasted image 20240514114203.png|300]]
#### Optimizacion del diseño del reactor
El perfil de temperatura también difiere entre reactores con paredes calientes y frías. 
- En un reactor con paredes calientes, los gases en contacto con las paredes se calientan primero, y a medida que fluyen a través del reactor, los gases cercanos al centro también aumentan su temperatura.
	- En un reactor lo suficientemente largo, se alcanza una temperatura de gas uniforme. 
- Por otro lado, en un reactor con paredes frías, la temperatura del gas es más alta en la superficie del sustrato y disminuye rápidamente hacia un valor constante, creando un gradiente de temperatura.

#### Influencia de la geometria
La geometría del reactor y del sustrato también pueden influir en la dinámica de fluidos.
- En la deposición epitaxial de silicio a altas temperaturas, el proceso está controlado por la transferencia de masa desde la fase de vapor hacia la superficie del sustrato. 
- El coeficiente de transferencia de masa, $h_G=\frac{D_G}{\delta_S}$, está relacionado con la difusión de especies reactivas a través de una capa límite de espesor variable $\delta_S$. 
- Para lograr una deposición uniforme, se puede inclinar el sustrato, aumentando la velocidad del gas y manteniendo $\delta_S$ constante.
![[Pasted image 20240514114127.png|300]]

## Tipi CVD

### [[T.2. Epitassia]]
### LPCVD(Deposizione Chimica da Fase Vapore a Bassa Pressione)
#### Sistemas APCVD
![[Pasted image 20240523093434.png]]
Los sistemas CVD a presión atmosférica (APCVD) presentan algunos desafíos, especialmente cuando se requiere deposición a altas temperaturas.
- En tales casos, se debe utilizar una configuración horizontal, ya que el flujo debe ser identico sobre todos los substratos, procesando solo unas pocas obleas en cada corrida.
- Por otro lado, si la deposición se realiza a bajas temperaturas, la velocidad de deposición disminuye, lo que resulta en un bajo rendimiento del proceso.
- É sensibile alle reazioni in fase gassosa(reazioni omogenee) → Formazione di particolate e fil poco denso
- É utilizzato per la deposizione di $SiO_2$ a bassa temperatura
**Vantaggi:**
- Struttura del reattore abbastanza semplice
- Elevate velocitá di deposizione
#### Solucion a baja presion LPCVD
$h_G=\frac{D_G}{\delta_S}$ ,anche $D_G$ e $\delta_S$ sono inversamente proporcionale alle presione
![[Pasted image 20240514115135.png|300]]
- Una solución a estos problemas es operar a baja presión, en el régimen limitado por el transporte de masa.
- Al reducir la presión, la distancia de difusión (DG) aumenta significativamente, lo que a su vez aumenta el coeficiente de transferencia de masa (hG) en aproximadamente 100 veces.
- Esto significa que el transporte de reactivos en fase gaseosa hacia la superficie del sustrato a través de la capa límite ya no es el factor limitante en la velocidad de crecimiento.
- A baja presión, el proceso se vuelve mucho más sensible a la temperatura.

##### Diseño del reactor
![[Pasted image 20240514115239.png|300]]
- Se puede utilizar un sistema de pared caliente para un mejor control de la temperatura, y también es posible apilar las obleas, procesando múltiples sustratos simultáneamente (hasta alrededor de 200).
- Además, una presión residual de 0,25 a 2,0 Torr aumenta aún más la diffusividad de las especies reactivas (hasta 1000 veces).

##### Las características de un sistema LPCVD
- Reducción de reacciones en fase gaseosa, lo que disminuye la generación de partículas no deseadas.
- Buena uniformidad en la deposición.
- Buena cobertura de escalones.
- Velocidades de deposición relativamente bajas (10-50 nm/min).
- La uniformidad de la temperatura es más crítica que la uniformidad del flujo de gas, lo que permite el uso de un horno convencional.

##### Aplicaciones de LPCVD
El LPCVD se utiliza comúnmente para la deposición de silicio policristalino, nitruro de silicio (Si3N4), óxido de silicio (SiO2), PSG, BPSG y tungsteno (W), entre otros materiales. Un diseño típico de reactor LPCVD es horizontal con paredes calientes, lo que permite procesar un gran número de sustratos en cada corrida.


### PECVD (Deposizione Chimica da Fase Vapore Potenziata dal Plasma)
#### Introduccion
Los reactores CVD asistidos por plasma, o PECVD, operan en el régimen limitado por la velocidad de reacción, lo que resulta en velocidades de deposición más altas en comparación con la deposición LPCVD. 
- Una ventaja clave de la PECVD es que pueden operar a temperaturas más bajas que los procesos APCVD y LPCVD, lo que permite la deposición de películas de SiO2 y Si3N4 sobre metales con bajos puntos de fusión.
	- Esto es especialmente importante cuando se trabaja con capas de aluminio u otros metales sensibles a la temperatura.

#### Caracteristicas
- Las películas depositadas por PECVD generalmente muestran una buena adhesión y una excelente cobertura de escalones debido a la mayor movilidad superficial de las especies adsorbidas. 
- Sin embargo, uno de los desafíos es que estas películas a menudo no tienen una composición estequiométrica y pueden contener subproductos de reacción incorporados, como hidrógeno, oxígeno o nitrógeno. 
- Durante pasos de procesamiento posteriores, esto puede llevar a un fenómeno de degasificación, formando burbujas y causando delaminación de la película.
- El proceso PECVD es más complejo, con más parámetros que deben ser controlados cuidadosamente. 
- Sin embargo, ofrece una gran flexibilidad en términos de materiales que se pueden depositar, incluyendo SiO2, Si3N4, oxinitruros, SiC, silicio amorfo (a-Si) y más. La PECVD a temperaturas muy altas incluso permite el crecimiento epitaxial de Si, Ge y compuestos III-V.


#### Estructura y propiedades de las peliculas de silicio depositadas por PECVD
- Las películas delgadas de silicio depositadas por PECVD suelen ser amorfas y compactas, aunque en condiciones específicas (alta dilución de hidrógeno) pueden mostrar una estructura microcristalina. 
- Estas películas exhiben orden a corto alcance (entre vecinos cercanos) pero desorden a largo alcance debido a fluctuaciones en las distancias y ángulos de enlace. 
- La estructura amorfa contiene defectos en forma de enlaces no saturados que forman trampas y centros de recombinación para portadores de carga. 
- Sin embargo, esta flexibilidad estructural permite la preparación de aleaciones con composiciones variables para aplicaciones específicas


#### Reactores PECVD
Los reactores PECVD pueden tener diferentes diseños, incluyendo reactores de flujo radial con electrodos paralelos y reactores de capacitancia con electrodos enfrentados.
##### Reactor de Flujo Radial (Electrodos Paralelos):
![[Pasted image 20240514121636.png|300]]
- Temperatura de procesamiento relativamente baja.
- Capacidad de procesamiento limitada.
- Operación manual.
- Puede generar partículas que se depositan en el sustrato o película.

##### Reactor de Capacitancia (Electrodos Enfrentados):
![[Pasted image 20240514121625.png|300]]
- Las obleas se colocan verticalmente y en paralelo al flujo de gas.
- Mayor capacidad de procesamiento.
- Temperatura de proceso aún más baja.
- Operación manual.
- También puede generar partículas.

##### Esquema de una instalación de deposición PECVD:
![[Pasted image 20240514121607.png|300]]
- El sistema incluye un controlador de temperatura, cátodo, ánodo, fuente de alimentación RF, red de adaptación, medidor de vacío, sustrato, sistema de bombeo, y control de gas de lastre. 
- La fuente de alimentación RF genera una frecuencia diferente a la radiofrecuencia, y la red de adaptación garantiza una transferencia de potencia óptima, que es crítica debido a las variaciones de impedancia del plasma.
- Si utilizza Ar per la pulizia, non è controllato ma è simile alla pulizia con acqua.

### RPECVD (PECVD Potenziata dal Reattore a Risonanza Elettronica)
Los reactores CVD a plasma remoto, también conocidos como RPECVD o PECVD indirecta, utilizan un enfoque único donde la cámara de generación de plasma está separada de la cámara donde se encuentra el sustrato. Esta separación garantiza que los sustratos no estén expuestos directamente a la radiación del plasma y al bombardeo de iones de alta energía.


### ECR
- El plasma se genera a partir de un campo eléctrico de microondas en presencia de un campo magnético. Esta configuración provoca una resonancia ciclotrónica de electrones, lo que resulta en una densidad de plasma aproximadamente 100 veces mayor en especies reactivas en comparación con otros reactores PECVD
- Si utilizza un reattore ECR per generare elettroni rotanti che possono rompere molti legami.
- Questa tecnica è utile perché il plasma di solito è un po' sporco




