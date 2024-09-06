---
cards-deck: Profesional::Universidad::UNISA::Segundo Cuatrimestre::Nanoeletronica
---


![[Pasted image 20240524120823.png]]

# Italiano

## Introduzione
Il "sputtering" è un processo di deposizione fisica da vapore (PVD) in cui gli atomi vengono espulsi dalla superficie di un materiale bersaglio mediante il bombardamento di particelle ad alta energia (ioni). Gli atomi espulsi vengono poi depositati su un substrato, formando un sottile strato. A differenza di altre tecniche di deposizione in fase vapore, il materiale bersaglio non si fonde durante il processo.

### Storia
Il termine "sputtering" deriva dal latino "sputare," che significa emettere saliva rumorosamente. Questo fenomeno è stato descritto per la prima volta più di 150 anni fa:
- **Grove (1852)** e **Plücker (1858)** furono i primi a segnalare la vaporizzazione e la formazione di film metallici tramite sputtering.
- Questa scoperta fu fondamentale per la comprensione degli elettroni e degli ioni positivi in scariche di gas a bassa pressione, così come per lo sviluppo della struttura atomica, con contributi significativi di scienziati come **J.J. Thomson** e **Rutherford**.



## Processo di Sputtering
### Principi Fisici dello Sputtering
![[Pasted image 20240524101049.png]]
Lo sputtering si basa sul principio di trasferimento di momento, dove un atomo o ione impatta una superficie e provoca l'espulsione di atomi da quella superficie. 
- **Interazioni Ione-Superficie**:
  - **Effetti Anaelastici**: Generazione di fotoni, raggi X ed elettroni secondari.
  - **Effetti Elastici**: Emissione di atomi (sputtering) e riflessione di ioni o atomi neutri.


### Passaggi del Processo di Sputtering #tarjeta-anki 
#### 1. Generazione di Ioni
Si genera un plasma in una camera a vuoto utilizzando un gas inerte, comunemente argon (Ar). Gli atomi del gas vengono ionizzati dall'essere bombardati con elettroni ad alta energia, producendo ioni positivi (Ar+).
#### 2. Direzione degli Ioni verso il Bersaglio
Gli ioni generati sono accelerati verso il materiale bersaglio mediante un campo elettrico applicato. Gli ioni accelerati colpiscono la superficie del bersaglio con alta energia, causando l'espulsione di atomi dal materiale.
##### Energia di bombardamento e i suoi effetti
- **< 5 eV**:
    - **Fenomeni di Collisione**:
        - **Riflessione o Adsorbimento**: A queste basse energie, gli ioni sono principalmente riflessi o adsorbiti sulla superficie senza causare significativo sputtering.
        - **Impatto Basso**: Non generano significativi effetti anaelastici né elastici.
- **5-10 eV**:
    - **Fenomeni di Collisione**:
        - **Danni Superficiali e Migrazione**: Gli ioni in questo intervallo di energia possono causare danni superficiali e promuovere la migrazione superficiale di atomi.
        - **Effetti Anaelastici**: Possono iniziare a generare elettroni secondari e fotoni a causa delle collisioni.
- **10 eV - 10 keV**:
    - **Fenomeni di Collisione**:
        - **Sputtering e Danni Cristallografici**: Gli ioni in questo intervallo di energia sono in grado di causare l'emissione di atomi (sputtering) e possibili danni alla struttura cristallografica del materiale bersaglio.
        - **Effetti Elastici**: Sputtering e riflessione di ioni o atomi neutri sono predominanti.
        - **Effetti Anaelastici**: Emissione di fotoni, raggi X ed elettroni secondari a causa delle collisioni energetiche.
- **> 10 keV**:
    - **Fenomeni di Collisione**:
        - **Impiantazione di Ioni**: Gli ioni ad alta energia possono penetrare profondamente nella superficie del materiale bersaglio, causando l'impiantazione e l'alterazione della struttura interna.
        - **Effetti Elastici ed Anaelastici Intensificati**: I fenomeni di sputtering, riflessione ed emissione di fotoni ed elettroni secondari sono più pronunciati.
        - **Danni Interni**: Possono indurre danni più profondi nella struttura cristallina del materiale a causa dell'alta energia degli ioni.
#### 3. Espulsione di Atomi dal Bersaglio
L'energia e il momento degli ioni incidenti si trasferiscono agli atomi del bersaglio, espellendoli dalla loro posizione. Gli atomi espulsi si staccano dal bersaglio e si spostano nella camera a vuoto.
##### Modello della Biliardo
![[Pasted image 20240524104206.png]]
Un atomo incidente colpisce un altro atomo sulla superficie, provocando la sua espulsione.
- Ad angoli obliqui (45º-90º), c'è una maggiore probabilità di sputtering a causa di collisioni più vicine alla superficie.
#### 4. Trasporto di Atomi al Substrato
Gli atomi espulsi viaggiano attraverso la camera a vuoto, muovendosi verso il substrato. Durante il loro tragitto, gli atomi possono subire collisioni con altre molecole di gas, influenzando la loro traiettoria e energia.
#### 5. Condensazione sul Substrato
Gli atomi infine arrivano al substrato e si condensano sulla sua superficie. L'accumulo di atomi sul substrato forma un film sottile del materiale bersaglio.
^1719957945818


### Efficienza e Rendimento dello Sputtering #tarjeta-anki 
#### Rendimento dello Sputtering
L'efficienza del processo è misurata dal rendimento dello sputtering, che è il numero di atomi espulsi per ogni ione incidente. Il rendimento dello sputtering (γ) è una misura dell'efficienza del processo e dipende da vari fattori:
- **Materiale del Bersaglio**: Diversi materiali hanno diverse energie di legame e efficienze di trasferimento di momento.
- **Massa dell'Ione Bombardante**: L'efficienza di trasferimento di momento è maggiore quando la massa dell'ione è comparabile a quella dell'atomo bersaglio.
- **Energia dell'Ione Bombardante**: Diversi livelli di energia influenzano l'efficienza dello sputtering e la probabilità di impiantazione degli ioni nel materiale bersaglio.
^1719957945822

![[Pasted image 20240524102118.png]]

$$\gamma=\frac{ejected-particles}{incident-particles}$$



### Applicazioni dello Sputtering

#### Incisione con Sputtering (Sputter Etching)
- **Pulizia delle Superfici**: Utilizzato per pulire la superficie del substrato prima della deposizione.
- **Incisione Anisotropica**: Tecnica usata per creare motivi precisi sul substrato, cambiando la polarità per incidere il film depositato. → Litografia
- Il plasma di RF di argon è la tecnica standard per rimuovere l'ossido nativo dalla superficie metallica e preparare il wafer per la deposizione.
![[Pasted image 20240629191101.png]]


### Vantaggi e Svantaggi dello Sputtering #tarjeta-anki 
#### Vantaggi dello Sputtering
1. **Uniformità dello Spessore del Film**:
   - Consente l'utilizzo di bersagli (targets) di dimensioni molto maggiori rispetto al substrato, facilitando l'ottenimento di film con buona uniformità.
2. **Controllo Preciso dello Spessore e della Composizione**:
   - Attraverso un controllo preciso dei parametri del processo, è possibile regolare e mantenere lo spessore del film con alta precisione.
   - Facilita la deposizione di leghe come Al-Si, Al-Cu, Ti-W con un migliore controllo sulla composizione.
3. **Copertura di Dislivelli**:
   - Offre una migliore copertura dei dislivelli rispetto all'evaporazione termica grazie alla fonte estesa (target) anziché una fonte puntuale.
4. **Controllo dello Stress e dell'Adesione**:
   - Lo stress e l'adesione del film possono essere controllati mediante regolazioni nella potenza e nella pressione del plasma.
5. **Pulizia In-Situ**:
   - È possibile effettuare una pulizia in-situ della superficie del substrato prima della deposizione, migliorando la qualità del film senza interrompere il vuoto.
6. **Minore Radiazione al Substrato**:
   - Il substrato subisce meno radiazione rispetto alla deposizione per fascio di elettroni (e-beam)
#### Svantaggi dello Sputtering
1. **Alto Costo dell'Equipaggiamento**:
   - L'attrezzatura necessaria per lo sputtering, specialmente quando si utilizzano tecniche avanzate come il magnetrone, è costosa.
2. **Maggiore Possibilità di Incorporare Impurità**:
   - Poiché il processo si svolge a pressioni intermedie, esiste una maggiore possibilità di incorporare impurità nel film.
3. **Inefficienza Energetica**:
   - Solo una piccola frazione (2-3%) dell'energia trasferita all'atomo emittente viene utilizzata nella deposizione effettiva; il resto si dissipa come calore.
^1719957945826



### Condizioni Tipiche dello Sputtering
#### Condizioni di Gas e Pressione
La scelta del gas di lavoro e della pressione all'interno della camera a vuoto sono parametri essenziali:
- **Gas Inerte (Argon)**: Si preferisce l'argon per la sua inerzia, peso relativamente elevato e basso costo.
- **Pressione**: 
  - **Minima**: Per mantenere la scarica (2-3 mtorr nei magnetroni).
  - **Massima**: Per evitare di limitare la diffusione (~100 mtorr).
  - La pressione influisce sulla velocità di deposizione, con pressioni ottimali intorno a 100 mtorr che forniscono un equilibrio tra il numero di ioni di argon e la dispersione degli atomi espulsi.
	  - Si utilizza bassa pressione per mantenere la carica.
##### Proprietà dell'Argon
Il gas utilizzato nel processo di sputtering, comunemente argon, ha proprietà specifiche che lo rendono adatto a questo scopo:
- **Inerte**: Non reagisce né con il materiale bersaglio né con il substrato.
- **Relativamente Pesante**: Sufficiente massa per trasferire il momento in modo efficiente.
- **Abbondante e a Basso Costo**: Costituisce circa l'1% dell'atmosfera ed è economico da ottenere.

#### Potenza e Tensione
- **Tensione**: Generalmente nell'ordine di centinaia di volt (250-5000 V) per ottimizzare il rendimento dello sputtering.
- **Corrente di Ionizzazione**: Regolata per massimizzare la velocità di deposizione, tipicamente nell'intervallo di 10-100 mA/cm² nei sistemi con magnetrone.
	- Aumentando la corrente → aumenta la velocità di crescita
- **Efficienza Energetica**: Solo il 2-3% dell'energia trasferita all'atomo emittente viene utilizzata nella deposizione effettiva, con il resto che contribuisce al riscaldamento del substrato e alla produzione di elettroni secondari e fotoni.

##### Tensione di polarizzazione
Applicare una tensione negativa al substrato può variare il flusso e l'energia delle particelle depositate, migliorando l'adesione, la densità, e altre proprietà del film.
- **Valori Tipici**: Tensioni di -50 a -300 V vengono utilizzate per migliorare le caratteristiche dei film depositati.

#### Requisiti di Vuoto
- Mantenere la camera di deposizione in un vuoto di 10^-9 Torr per minimizzare la contaminazione.
- Mantenere pressioni di 10^-6 a 10^-8 Torr nelle camere di trasferimento e pre-camera per ridurre l'introduzione di contaminanti.

#### Temperatura del Substrato
- **Vantaggi del Raffreddamento del Substrato**:
  - Minore mobilità degli atomi, evitando diffusione indesiderata.
  - Miglior controllo sulla crescita del film.
- **Vantaggi del Riscaldamento del Substrato**:
  - Migliora la copertura dei dislivelli.
  - Riduce la porosità del film.
  - Aumenta la mobilità superficiale, migliorando la qualità del film.

##### Compromesso Pressione-Temperatura
- **Compromesso Necessario**: Si deve trovare un equilibrio tra un'alta pressione per avere sufficienti atomi di argon e una bassa temperatura per evitare surriscaldamenti e danni al substrato.
### Osservazioni del processo
- Caratteristiche Generali Desiderate
	- Precisione nel controllo dello spessore del film.
	- Meno del 5% di variazione nell'uniformità.
	- Film con bassa resistività.
	- Film che aderiscono bene al substrato.
	- Copertura superiore al 50% dei dislivelli.
	- Film resistenti alla migrazione elettrica.
	- Minimizzazione dei difetti superficiali.
	- Controllo preciso della riflettività ottica.
	- Film con basso livello di stress per minimizzare il rischio di delaminazione.

- Si verifica quando le particelle riflesse dal gas bombardano il substrato, potenzialmente contaminando il film, rompendo il substrato e riducendo la mobilità.
	- **Controllo**: È cruciale utilizzare materiali compatibili per minimizzare la contaminazione da backscattering.

- Le particelle emesse sono tipicamente neutre (~10^-4 sono cariche).
	- Le particelle hanno un'energia alta (5-20 eV) rispetto all'evaporazione (~0.1 eV), migliorando l'adesione e la copertura dei dislivelli.
	- Questa è una delle differenze più importanti tra l'evaporazione e lo Sputtering

- **Riscaldamento intenzionale del Substrato:** Utilizzo di lampade IR o aria calda per controllare la temperatura del substrato. Il substrato può essere riscaldato o raffreddato a seconda dei requisiti del processo.

- **Riscaldamento non intenzionale del Substrato:** Riscaldamento dovuto agli elettroni secondari e al calore di condensazione. Importante ad alte velocità di crescita (>1 μm/min), che possono elevare significativamente la temperatura del substrato. Il bersaglio viene raffreddato durante il processo per mantenere la stabilità del materiale.

- **Ossidazione dell'Alluminio:** Per evitare l'ossidazione dell'alluminio, si esegue una pulizia preliminare con sputtering in vuoto e si protegge il substrato.

- **Triodo nello Sputtering:** Si posiziona una piastra intermedia che funge da triodo per gestire e controllare meglio il processo.

- Quando gli ioni rompono i legami, possono generare elettroni secondari che aumentano la produzione di ioni.
	- Gli elettroni secondari sono cruciali poiché aumentano la produzione di ioni e migliorano l'efficienza dello sputtering.

## Tipi di Sputtering #tarjeta-anki 
Esistono vari metodi di sputtering, ognuno adattato a diversi materiali e requisiti di deposizione. Di seguito sono descritti i principali tipi di sputtering:
### DC Sputtering (Sputtering a Corrente Continua)
Il DC Sputtering è una tecnica di deposizione di film sottili che utilizza corrente continua (DC) per creare un plasma e bombardare un materiale bersaglio con ioni, espellendo atomi del materiale che si depositano su un substrato.
Gli elettroni accelerati colpiscono l'alluminio, rompendo i legami e causando l'estrazione di atomi dal materiale bersaglio. Le particelle espulse si diffondono verso il substrato.
- Gli atomi emessi si condensano sul substrato e sulle pareti del reattore.
#### Parametri Tipici
- **Gas di Scarico**: Argon (Ar).
- **Pressione di Base (Pbase)**: 10^-6 a 10^-9 torr.
- **Pressione di Lavoro (Par)**: 20 – 200 mtorr.
- **Tensione DC (VDC)**: -250 a -5000 V.
- **Densità di Corrente (J)**: 0,1 a 2,0 mA/cm².
##### Bombardamento del Substrato
- **Atomi del catodo e contaminanti**:
  - **Velocità di Crescita**: ~200 Å/min (batch) e ~1 μm/min (single wafer).
  - **Flusso di atomi**: ~10^15 atomi/cm²-s (~1 monolayer/s).
  - **Minimizzazione della contaminazione**: Aumentando il bombardamento e il flusso se la fonte di contaminazione non è il gas di sputtering.
- **Atomi di Argon (Ar)**:
  - A 20 mtorr, il flusso è ~10^19 atomi/cm²-s.
  - **Coefficiente di Adsorbimento**: Diminuisce con la temperatura, aumenta con l'energia dell'Ar.
##### Crescita del Film
- Gli atomi raggiungono il substrato con un'energia di ~1-2 eV.
- Possono essere retro-diffusi al bersaglio e termalizzati per diffusione.
#### Vantaggi
- **Uniformità dello Spessore del Film**: Permette di ottenere film con buona uniformità.
- **Controllo Preciso dello Spessore**: Regolazione precisa dei parametri del processo.
- **Deposizione di Leghe**: Facilita la deposizione di leghe con un miglior controllo sulla composizione.
- **Minore Radiazione al Substrato**: Rispetto ad altri metodi come il fascio di elettroni (e-beam).
#### Svantaggi
- **Alto Costo dell'Equipaggiamento**: Attrezzature costose, specialmente con tecniche avanzate.
- **Maggiore Possibilità di Incorporare Impurità**: A causa delle pressioni intermedie.
- **Inefficienza Energetica**: Solo una piccola frazione dell'energia viene utilizzata nella deposizione effettiva.
### Sputtering Reattivo
Lo **sputtering reattivo** è una variante del processo di sputtering in cui si introduce un gas reattivo nella camera a vuoto insieme al gas inerte (generalmente argon). Questo gas reattivo, come ossigeno (O₂) o azoto (N₂), reagisce chimicamente con gli atomi espulsi dal materiale bersaglio, formando composti sulla superficie del substrato.
#### Funzionamento
1. **Gas Inerte e Gas Reattivo**: Si introduce un gas inerte (come Ar) e un gas reattivo (come O₂ o N₂) nella camera a vuoto.
2. **Bombardamento Ionico**: Gli ioni del gas inerte bombardano il bersaglio, espellendo atomi del materiale.
3. **Reazione Chimica**: Gli atomi espulsi reagiscono con il gas reattivo per formare composti, come ossidi (ad esempio, Al₂O₃) o nitruri (ad esempio, TiN), che si depositano sul substrato.
#### Applicazioni
- **Formazione di Film di Ossidi e Nitruri**: Utilizzato per creare strati di ossidi e nitruri, che hanno applicazioni nei semiconduttori, nei rivestimenti duri, e nell'ottica.
#### Limitazioni dello Sputtering Reattivo nei Materiali Isolanti
##### Problemi negli Isolanti
Lo sputtering reattivo incontra problemi quando utilizzato con materiali isolanti a causa dell'accumulo di carica sul bersaglio. I materiali isolanti non permettono la conduzione dell'elettricità, causando l'accumulo di carica sulla superficie del bersaglio durante il processo di sputtering. Questo può portare a vari problemi:
1. **Accumulo di Carica**: La superficie dell'isolante si carica positivamente a causa del bombardamento ionico, impedendo un bombardamento continuo e uniforme.
2. **Arco Elettrico**: L'accumulo di carica può portare alla formazione di archi elettrici, che possono danneggiare l'attrezzatura e il materiale bersaglio.
3. **Squilibrio del Plasma**: La carica accumulata può influenzare la stabilità del plasma, rendendo difficile mantenere un processo uniforme.
### Sputtering a Radiofrequenza (RF Sputtering)
L'RF Sputtering è una tecnica che utilizza una fonte di radiofrequenza (RF) per generare un plasma, consentendo lo sputtering di materiali sia conduttori sia non conduttori.
![[Pasted image 20240630093648.png]]
#### Parametri Tipici
- **Frequenza RF**: Generalmente 13.56 MHz.
- **Tensione RF**: Variabile, adattata al materiale del bersaglio.
- **Pressione di Lavoro**: Simile allo Sputtering DC.
#### Funzionamento
- Alle frequenze radio (13.56 MHz) l'elettrodo alimentato svilupperà una carica netta negativa (il "bias automatico") a causa della differenza nelle mobilità tra elettroni e ioni.
- Gli ioni positivi bombarderanno l'elettrodo alimentato, portando così alla sputtering di questo bersaglio.
- I substrati da rivestire vengono quindi posizionati sull'elettrodo collegato a terra (o in qualsiasi altro punto della camera).
1. **Generazione di Plasma**: Una fonte RF alterna rapidamente il campo elettrico, evitando l'accumulo di carica sul bersaglio.
2. **Scarica di Carica**: L'alternanza di polarità permette che la carica accumulata sulla superficie dell'isolante si scarichi periodicamente, evitando l'accumulo eccessivo.
3. **Mantenimento del Plasma**: Il campo alternato aiuta a mantenere un plasma stabile e uniforme, consentendo il bombardamento continuo del bersaglio.
#### Uso negli Isolanti
Per superare i problemi di accumulo di carica nei materiali isolanti, si utilizza lo **sputtering a radiofrequenza (RF Sputtering)**. La radiofrequenza permette di alternare la polarità del campo elettrico, evitando l'accumulo di carica sulla superficie del materiale isolante.
#### Funzionamento dello Sputtering RF
1. **Campo Elettrico Alternato**: Si applica una fonte di radiofrequenza (generalmente a 13.56 MHz) che alterna rapidamente il campo elettrico.
2. **Efectos por encima de 1 MHz**:
   - **Mecanismo de Ping Pong**: Los electrones ganan energía circulando entre la vaina y el plasma.
   - **Acoplamiento de Voltaje de RF**: El voltaje de RF puede acoplarse a través de cualquier impedancia.
   - **Reducción de la Energía Iónica**: Menor energía de iones, más energía para los electrones.
3. **Frecuencias inferiores a 1 MHz**:
   - **Movilidad de Electrones e Iones**: Electrones e iones siguen la alternancia del ánodo y el cátodo.
   - **Pulverización Catódica**: Pulverización de ambas superficies con corriente continua.
4. **Frecuencias por encima de 1 MHz**:
   - **Iones Pesados**: Iones pesados no siguen la conmutación rápida.
   - **Neutralización de Carga**: Electrones neutralizan la carga positiva acumulada.
#### Vantaggi dello Sputtering RF
- **Adatto per Isolanti e Condutors**: Permette lo sputtering di materiali isolanti e conduttori.
- **Controllo sul Processo**: Offre un buon controllo sulla velocità di deposizione e sulla composizione del film.
- **Stabilità del Plasma**: Mantiene un plasma stabile, essenziale per un processo di deposizione uniforme.
#### Svantaggi
- **Complessità dell'Equipaggiamento**: Richiede attrezzature più complesse.
- **Costo**: Generalmente più costoso dello Sputtering DC a causa dell'equipaggiamento RF.
#### Observazione
1. **Sputtering RF vs. Sputtering DC**:
   - **Sputtering DC**: 
     - Útil para blancos conductores.
     - Ineficaz para materiales no conductores como SiO2 debido a la necesidad de voltajes extremadamente altos (~10^12 V).
     - Baja tasa de deposición y menor control del plasma.
   - **Sputtering RF**:
     - Utiliza una frecuencia estándar de 13.56 MHz.
     - Más eficiente y controla mejor el plasma.
     - Supera problemas de impedancia elevada.
2. **Uso de Capacitores en Sputtering RF**:
   - Facilitan la creación y el mantenimiento del self-DC bias.
   - Permiten el paso de corriente alterna (AC) mientras bloquean la corriente continua (DC).
   - Ayudan a estabilizar el plasma y mejorar la calidad de la película depositada.
   - A frecuencias altas, como 13.56 MHz, la impedancia de los capacitores disminuye, permitiendo un acoplamiento eficiente del voltaje de RF.
3. **Self-DC Bias**:
   - Diferencia de potencial que se desarrolla espontáneamente entre los electrodos.
   - Depende del área relativa de los electrodos, aumentando significativamente con la diferencia de áreas.
   - Se anula con electrodos de igual área o sin capacitores de bloqueo.
   - Permite el control de la energía de los iones, minimizando el daño a los materiales sensibles.
4. **Ventaja de Inversión de Polaridad en RF**:
   - Permite realizar pre-etching del sustrato antes de la deposición.
   - Mejora la adherencia y calidad de la capa delgada.
### Magnetron Sputtering
![[Pasted image 20240630095926.png]]
Il Magnetron Sputtering è una variante dello sputtering che utilizza campi magnetici per aumentare la densità del plasma vicino al bersaglio, migliorando l'efficienza del processo di deposizione.
#### Parametri Tipici
- **Campi Magnetici**: Utilizza magneti per creare campi magnetici perpendicolari al campo elettrico.
- **Pressione di Lavoro**: Simile allo Sputtering DC e RF.
#### Vantaggi
- **Alta Velocità di Deposizione**: Maggiore efficienza e velocità di deposizione grazie all'alta densità di plasma.
- **Minore Riscaldamento del Substrato**: Riduce il riscaldamento del substrato rispetto ad altri metodi.
- **Uniformità Migliorata**: Fornisce una migliore uniformità del film depositato.
#### Svantaggi
- **Consumo Non Uniforme del Bersaglio**: Può risultare in un consumo non uniforme del materiale bersaglio.
- **Complessità del Design**: Richiede un design più complesso dell'equipaggiamento.
#### Funzionamento
1. **Generazione di Plasma**: Si introduce un gas inerte nella camera e si applica una tensione, mentre si utilizzano campi magnetici per confinare gli elettroni vicino al bersaglio.
2. **Bombardamento del Bersaglio**: Gli ioni bombardano il bersaglio, e gli elettroni confinati aumentano l'efficienza del processo di ionizzazione.
3. **Deposizione sul Substrato**: Gli atomi espulsi si depositano sul substrato, formando un film sottile.
### Resoconto Comparativo
^1719957945830

| Caratteristica         | DC Sputtering                         | RF Sputtering                        | Magnetron Sputtering                |
|------------------------|---------------------------------------|--------------------------------------|-------------------------------------|
| **Fonte di Energia**  | Corrente Continua (DC)                | Radiofrequenza (RF)                 | Corrente Continua (DC) + Campi Magnetici |
| **Applicabilità**      | Materiali Conduttori                | Materiali Conduttori e Non Conduttori | Materiali Conduttori e Non Conduttori |
| **Vantaggi**           | Uniformità, Controllo Preciso          | Adatto per Isolanti, Stabilità  | Alta Velocità di Deposizione, Minore Riscaldamento |
| **Svantaggi**        | Impurità, Inefficienza Energetica    | Complessità e Costo                  | Consumo Non Uniforme del Bersaglio     |
| **Efficienza**         | Moderata                              | Alta                                 | Molto Alta                            |

## [[T.5.3 Plasma]]










# Espagnolo
## Introducción
El sputtering es un proceso de deposición física de vapor (PVD) en el cual los átomos son expulsados de la superficie de un material objetivo mediante el bombardeo de partículas de alta energía (iones). Estos átomos expulsados son luego depositados en un sustrato, formando una capa delgada. A diferencia de otras técnicas de deposición en fase vapor, el material objetivo no se funde durante el proceso.

### Historia
El término "sputtering" proviene del latín "sputare," que significa emitir saliva con ruido. Este fenómeno fue descrito por primera vez hace más de 150 años:
- **Grove (1852)** y **Plücker (1858)** fueron los primeros en reportar la vaporización y formación de películas metálicas mediante sputtering.
- Este descubrimiento fue clave para la comprensión de los electrones y los iones positivos en descargas de gas a baja presión, así como para el desarrollo de la estructura atómica, con contribuciones significativas de científicos como **J.J. Thomson** y **Rutherford**.




## Proceso de Sputtering

### Principios Físicos del Sputtering
![[Pasted image 20240524101049.png]]
El sputtering se basa en el principio de transferencia de momento, donde un átomo o ion impacta una superficie y provoca la expulsión de átomos de dicha superficie. 
- **Interacciones Ione-Superficie**:
  - **Efectos Anaelásticos**: Generación de fotones, rayos X y electrones secundarios.
  - **Efectos Elásticos**: Emisión de átomos (sputtering) y reflexión de iones o átomos neutros.

### Pasos del Proceso de Sputtering
#### 1. Generación de Iones
Se genera un plasma en una cámara de vacío utilizando un gas inerte, comúnmente argón (Ar). Los átomos del gas se ionizan al ser bombardeados con electrones de alta energía, produciendo iones positivos (Ar+).

#### 2. Dirección de Iones hacia el Objetivo
Los iones generados son acelerados hacia el material objetivo mediante un campo eléctrico aplicado. Los iones acelerados impactan la superficie del objetivo con alta energía, causando la expulsión de átomos del material.
##### Energia de bombardeo y sus efectos
- **< 5 eV**:
    - **Fenómenos de Colisión**:
        - **Reflexión o Adsorción**: A estas bajas energías, los iones son principalmente reflejados o adsorbidos en la superficie sin causar sputtering significativo.
        - **Bajo Impacto**: No generan efectos anáelásticos ni elásticos significativos.
- **5-10 eV**:
    - **Fenómenos de Colisión**:
        - **Daños Superficiales y Migración**: Los iones en este rango de energía pueden causar daños superficiales y promover la migración superficial de átomos.
        - **Efectos Anáelásticos**: Pueden comenzar a generar electrones secundarios y fotones debido a las colisiones.
- **10 eV - 10 keV**:
    - **Fenómenos de Colisión**:
        - **Sputtering y Daños Cristalográficos**: Los iones en este rango de energía son capaces de causar la emisión de átomos (sputtering) y posibles daños en la estructura cristalográfica del material objetivo.
        - **Efectos Elásticos**: Sputtering y reflexión de iones o átomos neutros son predominantes.
        - **Efectos Anáelásticos**: Emisión de fotones, rayos X y electrones secundarios debido a las colisiones energéticas.
- **> 10 keV**:
    - **Fenómenos de Colisión**:
        - **Implantación de Iones**: Los iones de alta energía pueden penetrar profundamente en la superficie del material objetivo, causando implantación y alteración de la estructura interna.
        - **Efectos Elásticos y Anáelásticos Intensificados**: Los fenómenos de sputtering, reflexión y emisión de fotones y electrones secundarios son más pronunciados.
        - **Daños Internos**: Pueden inducir daños más profundos en la estructura cristalina del material debido a la alta energía de los iones.
#### 3. Expulsión de Átomos del Objetivo
La energía y el momento de los iones incidentes se transfieren a los átomos del objetivo, expulsándolos de su posición. Los átomos expulsados se desprenden del objetivo y se desplazan en la cámara de vacío.
##### Modelo de Bola de Billar
![[Pasted image 20240524104206.png]]
Un átomo incidente impacta otro átomo en la superficie, provocando su expulsión.
- En ángulos oblicuos (45º-90º), hay una mayor probabilidad de sputtering debido a colisiones más cercanas a la superficie.
#### 4. Transporte de Átomos al Sustrato
Los átomos expulsados viajan a través de la cámara de vacío, moviéndose hacia el sustrato. Durante su trayecto, los átomos pueden sufrir colisiones con otras moléculas de gas, afectando su trayectoria y energía.

#### 5. Condensación en el Sustrato
Los átomos finalmente llegan al sustrato y se condensan en su superficie. La acumulación de átomos en el sustrato forma una película delgada del material objetivo.


### Eficiencia y Rendimiento del Sputtering

#### Rendimiento del Sputtering
La eficiencia del proceso se mide por el rendimiento del sputtering, que es el número de átomos expulsados por cada ion incidente.
El rendimiento del sputtering (γ) es una medida de la eficiencia del proceso y depende de varios factores:
- **Material del Objetivo**: Diferentes materiales tienen diferentes energías de enlace y eficiencias de transferencia de momento.
- **Masa del Ion Bombardante**: La eficiencia de transferencia de momento es mayor cuando la masa del ion es comparable a la del átomo objetivo.
- **Energía del Ion Bombardante**: Diferentes niveles de energía afectan la eficiencia del sputtering y la probabilidad de implantación de los iones en el material objetivo.
![[Pasted image 20240524102118.png]]
El rendimiento del sputtering típicamente varía entre 0.1 y 3 átomos expulsados por ion incidente, afectando directamente la tasa de deposición de la película delgada.



### 6. Aplicaciones del Sputtering

#### Sputter Etching (Grabado por Sputtering)
- **Limpieza de Superficies**: Se utiliza para limpiar la superficie del sustrato antes de la deposición.
- **Grabado Anisotrópico**: Técnica utilizada para crear patrones precisos en el sustrato, cambiando la polaridad para etchar el film depositado. → Litografia
- El plasma de RF de argón es la técnica estándar para remover el óxido nativo de la superficie metálica y preparar el wafer para la deposición.

#### Deposición de Películas por Sputtering: DC Sputtering
Los electrones acelerados impactan en el aluminio, rompiendo enlaces y causando la extracción de átomos del material objetivo. Las partículas desprendidas se difunden hacia el sustrato.
- Los átomos emitidos se condensan en el sustrato y en las paredes del reactor.
##### Parámetros Típicos:
- **Gas de descarga**: Argón (Ar)
- **Presión base (Pbase)**: 10^-6 a 10^-9 torr
- **Presión de trabajo (Par)**: 20 – 200 mtorr
- **Voltaje DC (VDC)**: -250 a -5000 V
- **Densidad de corriente (J)**: 0.1 a 2.0 mA/cm²

##### Bombardeo del Sustrato
- **Átomos del cátodo y contaminantes**:
  - **Velocidad de crecimiento**: ~200 Å/min (batch) y ~1 μm/min (single wafer).
  - **Flujo de átomos**: ~10^15 átomos/cm²-s (~1 monolayer/s).
  - **Minimización de contaminación**: Aumentando el bombardeo y el flujo si la fuente de contaminación no es el gas de sputtering.
- **Átomos de Argón (Ar)**:
  - A 20 mtorr, el flujo es ~10^19 átomos/cm²-s.
  - **Coeficiente de adsorción**: Disminuye con la temperatura, aumenta con la energía del Ar.
##### Crecimiento de la Película
- Los átomos alcanzan el sustrato con una energía de ~1-2 eV.
- Pueden ser retro-difundidos al blanco y termalizados por difusión.




#### Aplicaciones Específicas
- **Electrónica y Semiconductores**: Deposición de contactos metálicos, capas de barrera y capas de difusión.
- **Óptica**: Producción de recubrimientos ópticos de alta calidad y películas dieléctricas.
- **Memorias y Sensores**: Fabricación de películas delgadas para memorias magnetorresistivas y sensores.
- **Protección y Decoración**: Aplicación de películas protectoras y decorativas en diversos materiales.


### Ventajas y Desventajas del Sputtering

#### Ventajas del Sputtering
1. **Uniformidad del Espesor del Film**:
   - Permite la utilización de blancos (targets) de dimensiones mucho mayores que el sustrato, facilitando la obtención de películas con buena uniformidad.

2. **Control Preciso del Espesor y Composición**:
   - A través de un control preciso de los parámetros del proceso, es posible ajustar y mantener el espesor del film con alta precisión.
   - Facilita la deposición de aleaciones como Al-Si, Al-Cu, Ti-W con un mejor control sobre la composición.

3. **Cobertura de Desniveles**:
   - Ofrece una mejor cobertura de los desniveles en comparación con la evaporación térmica debido a la fuente extendida (target) en lugar de una fuente puntual.

4. **Control de Estrés y Adhesión**:
   - El estrés y la adhesión del film pueden ser controlados mediante ajustes en la potencia y la presión del plasma.

5. **Limpieza In-Situ**:
   - Es posible realizar una limpieza in-situ de la superficie del sustrato antes de la deposición, mejorando la calidad del film sin romper el vacío.

6. **Menor Radiación al Sustrato**:
   - El sustrato sufre menos radiación en comparación con la deposición por haz de electrones (e-beam).

#### Desventajas del Sputtering
1. **Alto Costo del Equipamiento**:
   - El equipo necesario para el sputtering, especialmente cuando se utilizan técnicas avanzadas como el magnetrón, es costoso.

2. **Mayor Posibilidad de Incorporar Impurezas**:
   - Dado que el proceso se lleva a cabo a presiones intermedias, existe una mayor posibilidad de incorporar impurezas en el film.

3. **Ineficiencia Energética**:
   - Solo una pequeña fracción (2-3%) de la energía transferida al átomo emisor se utiliza en la deposición efectiva; el resto se disipa como calor.


### Condiciones del Sputtering tipico
#### Condiciones de Gas y Presión
La elección del gas de trabajo y la presión dentro de la cámara de vacío son parámetros esenciales:
- **Gas Inerte (Argón)**: Se prefiere el argón debido a su inercia, peso relativamente alto y bajo costo.
- **Presión**: 
  - **Mínima**: Para mantener la descarga (2-3 mtorr en magnetrones).
  - **Máxima**: Para evitar limitar la difusión (~100 mtorr).
  - La presión afecta la tasa de deposición, con presiones óptimas alrededor de 100 mtorr proporcionando un equilibrio entre el número de iones de argón y la dispersión de los átomos expulsados.
	  - Se utiliza baja presión para mantener la carga.
##### Propiedades del Argon
El gas utilizado en el proceso de sputtering, comúnmente argón, tiene propiedades específicas que lo hacen adecuado para este propósito:
- **Inerte**: No reacciona con el material objetivo ni con el sustrato.
- **Relativamente Pesado**: Suficiente masa para transferir momento de manera eficiente.
- **Abundante y de Bajo Costo**: Constituye aproximadamente el 1% de la atmósfera y es económico de obtener.


#### Potencia y Voltaje
- **Voltaje**: Generalmente en el rango de cientos de voltios (250-5000 V) para optimizar el rendimiento del sputtering.
- **Corriente de Ionización**: Ajustada para maximizar la tasa de deposición, típicamente en el rango de 10-100 mA/cm² en sistemas con magnetrón.
	- Aumentando la corriente → aumenta la velocidad de crecimiento
- **Eficiencia Energética**: Solo el 2-3% de la energía transferida al átomo emisor se utiliza en la deposición efectiva, con el resto contribuyendo al calentamiento del sustrato y la producción de electrones secundarios y fotones.

##### Voltaje al bias
Aplicar un voltaje negativo al sustrato puede variar el flujo y la energía de las partículas depositadas, mejorando la adhesión, densidad, y otras propiedades del film.
- **Valores Típicos**: Voltajes de -50 a -300 V se utilizan para mejorar las características de las películas depositadas.

#### Requisitos de Vacío
- Mantener la cámara de deposición en un vacío de 10^-9 Torr para minimizar la contaminación.
- Mantener presiones de 10^-6 a 10^-8 Torr en las cámaras de transferencia y pre-cámara para reducir la introducción de contaminantes.

#### Temperatura del Sustrato
- **Ventajas de Enfriar el Sustrato**:
  - Menor movilidad de átomos, evitando difusiones indeseadas.
  - Mejor control sobre el crecimiento de la película.
- **Ventajas de Calentar el Sustrato**:
  - Mejora la cobertura de desniveles.
  - Reduce la porosidad de la película.
  - Aumenta la movilidad superficial, mejorando la calidad del film.

##### Compromiso Presión-Temperatura
- **Compromiso Necesario**: Se debe encontrar un equilibrio entre una alta presión para tener suficientes átomos de argón y una baja temperatura para evitar sobrecalentamientos y daños en el sustrato.
### Observaciones del proceso
- Características Generales Deseadas
	- Precisión en el control del espesor de la película.
	- Menos del 5% de variación en uniformidad.
	- Películas con baja resistividad.
	- Películas que se adhieren bien al sustrato.
	- Cobertura superior al 50% de los disliveles.
	- Películas resistentes a la electromigración.
	- Minimización de defectos en la superficie.
	- Control preciso de la reflectividad óptica.
	- Películas con bajo nivel de estrés para minimizar el riesgo de delaminación.

- Ocurre cuando partículas reflejadas del gas bombardean el sustrato, potencialmente contaminando el film, rompiendo el sustrato y reduciendo la movilidad.
	- **Control**: Es crucial utilizar materiales compatibles para minimizar la contaminación por backscattering.

- Las partículas emitidas son típicamente neutras (~10^-4 son cargadas).
	- Las partículas tienen una energía alta (5-20 eV) en comparación con la evaporación (~0.1 eV), mejorando la adhesión y la cobertura de disliveles.
	- Esta es una de las diferencias mas importantes entre la evaporacion y el Sputtering

- **Calentamiento intencional del Sustrato:** Utilización de lámparas IR o aire caliente para controlar la temperatura del sustrato. El sustrato puede ser calentado o enfriado dependiendo de los requisitos del proceso.

- **Calentamiento del Sustrato no intencional:** Calentamiento debido a electrones secundarios y el calor de condensación. Importante a altas tasas de crecimiento (>1 μm/min), lo que puede elevar la temperatura del sustrato significativamente. El objetivo se enfría durante el proceso para mantener la estabilidad del material.

- **Oxidación del Aluminio:** Para evitar la oxidación del aluminio, se realiza una limpieza previa con sputtering en vacío y se protege el sustrato.

- **Triodo en Sputtering:** Se coloca una placa intermedia que funciona como un triodo para manejar y controlar mejor el proceso.

- Cuando los iones rompen enlaces, pueden generar electrones secundarios que incrementan la producción de iones.
	-  Los electrones secundarios son cruciales ya que aumentan la producción de iones y mejoran la eficiencia del sputtering.


## Tipos de Sputtering

Existen varios métodos de sputtering, cada uno adaptado a diferentes materiales y requisitos de deposición. A continuación se describen los principales tipos de sputtering:

### 1. DC Sputtering (Sputtering por Corriente Directa)
El DC Sputtering es una técnica de deposición de películas delgadas que utiliza corriente directa (DC) para crear un plasma y bombardear un material objetivo con iones, expulsando átomos del material que se depositan sobre un sustrato.

#### Parámetros Típicos
- **Gas de Descarga**: Argón (Ar).
- **Presión Base (Pbase)**: 10^-6 a 10^-9 torr.
- **Presión de Trabajo (Par)**: 20 – 200 mtorr.
- **Voltaje DC (VDC)**: -250 a -5000 V.
- **Densidad de Corriente (J)**: 0.1 a 2.0 mA/cm².

#### Ventajas
- **Uniformidad del Espesor del Film**: Permite obtener películas con buena uniformidad.
- **Control Preciso del Espesor**: Ajuste preciso de los parámetros del proceso.
- **Deposición de Aleaciones**: Facilita la deposición de aleaciones con un mejor control sobre la composición.
- **Menor Radiación al Sustrato**: Comparado con otros métodos como el e-beam.

#### Desventajas
- **Alto Costo del Equipamiento**: Equipos costosos, especialmente con técnicas avanzadas.
- **Mayor Posibilidad de Incorporar Impurezas**: Debido a las presiones intermedias.
- **Ineficiencia Energética**: Solo una pequeña fracción de la energía se utiliza en la deposición efectiva.

#### Funcionamiento
1. **Generación de Plasma**: Se introduce un gas inerte (Argón) en una cámara de vacío y se aplica un voltaje DC para ionizar el gas, creando un plasma.
2. **Bombardeo del Objetivo**: Los iones de argón son acelerados hacia el objetivo, expulsando átomos del material.
3. **Deposición en el Sustrato**: Los átomos expulsados se depositan sobre el sustrato formando una película delgada.
### Sputtering reactivo

El **sputtering reactivo** es una variante del proceso de sputtering donde se introduce un gas reactivo en la cámara de vacío junto con el gas inerte (generalmente argón). Este gas reactivo, como oxígeno (O₂) o nitrógeno (N₂), reacciona químicamente con los átomos expulsados del material objetivo, formando compuestos en la superficie del sustrato.
#### Funcionamiento
1. **Gas Inerte y Gas Reactivo**: Se introduce un gas inerte (como Ar) y un gas reactivo (como O₂ o N₂) en la cámara de vacío.
2. **Bombardeo Iónico**: Los iones del gas inerte bombardean el objetivo, expulsando átomos del material.
3. **Reacción Química**: Los átomos expulsados reaccionan con el gas reactivo para formar compuestos, como óxidos (por ejemplo, Al₂O₃) o nitruros (por ejemplo, TiN), que se depositan en el sustrato.

#### Aplicaciones
- **Formación de Películas de Óxidos y Nitruros**: Utilizado para crear capas de óxidos y nitruros, que tienen aplicaciones en semiconductores, recubrimientos duros, y óptica.

#### Limitaciones del Sputtering Reactivo en Materiales Aislantes

##### Problemas en Aislantes
El sputtering reactivo enfrenta problemas cuando se utiliza con materiales aislantes debido a la acumulación de carga en el objetivo. Los materiales aislantes no permiten la conducción de la electricidad, lo que provoca que la carga se acumule en la superficie del objetivo durante el proceso de sputtering. Esto puede llevar a varios problemas:

1. **Acumulación de Carga**: La superficie del aislante se carga positivamente debido al bombardeo de iones, lo que impide un bombardeo continuo y uniforme.
2. **Arco Eléctrico**: La acumulación de carga puede llevar a la formación de arcos eléctricos, lo que puede dañar el equipo y el material objetivo.
3. **Desbalance de Plasma**: La carga acumulada puede afectar la estabilidad del plasma, dificultando el mantenimiento de un proceso uniforme.

### Sputtering con Radiofrecuencia (RF Sputtering)
El RF Sputtering es una técnica que utiliza una fuente de radiofrecuencia (RF) para generar un plasma, permitiendo el sputtering de materiales tanto conductores como no conductores.

#### Parámetros Típicos
- **Frecuencia de RF**: Generalmente 13.56 MHz.
- **Voltaje RF**: Variable, adaptado al material del objetivo.
- **Presión de Trabajo**: Similar al DC Sputtering.


#### Funcionamiento
1. **Generación de Plasma**: Una fuente RF alterna rápidamente el campo eléctrico, evitando la acumulación de carga en el objetivo.
2. **Descarga de Carga**: La alternancia de polaridad permite que la carga acumulada en la superficie del aislante se descargue periódicamente, evitando la acumulación excesiva.
3. **Mantención del Plasma**: El campo alterno ayuda a mantener un plasma estable y uniforme, permitiendo el bombardeo continuo del objetivo.
#### Uso en Aislantes
Para superar los problemas de acumulación de carga en materiales aislantes, se utiliza el **sputtering con radiofrecuencia (RF Sputtering)**. La radiofrecuencia permite alternar la polaridad del campo eléctrico, evitando la acumulación de carga en la superficie del material aislante.

#### Funcionamiento del RF Sputtering
1. **Campo Eléctrico Alterno**: Se aplica una fuente de radiofrecuencia (generalmente a 13.56 MHz) que alterna rápidamente el campo eléctrico.


#### Ventajas del RF Sputtering
- **Adecuado para Aislantes y Conductores**: Permite el sputtering de materiales aislantes y conductores.
- **Control sobre el Proceso**: Ofrece un buen control sobre la tasa de deposición y la composición del film.
- **Estabilidad del Plasma**: Mantiene un plasma estable, esencial para un proceso de deposición uniforme.

#### Desventajas
- **Complejidad del Equipo**: Requiere equipamiento más complejo.
- **Costo**: Generalmente más costoso que el DC Sputtering debido al equipo RF.







### Magnetron Sputtering

El Magnetron Sputtering es una variante del sputtering que utiliza campos magnéticos para aumentar la densidad del plasma cerca del objetivo, mejorando la eficiencia del proceso de deposición.

#### Parámetros Típicos
- **Campos Magnéticos**: Utiliza imanes para crear campos magnéticos perpendiculares al campo eléctrico.
- **Presión de Trabajo**: Similar al DC y RF Sputtering.

#### Ventajas
- **Alta Tasa de Deposición**: Mayor eficiencia y tasa de deposición debido a la alta densidad de plasma.
- **Menor Calentamiento del Sustrato**: Reduce el calentamiento del sustrato comparado con otros métodos.
- **Uniformidad Mejorada**: Proporciona una mejor uniformidad del film depositado.

#### Desventajas
- **Consumo No Uniforme del Objetivo**: Puede resultar en un consumo no uniforme del material objetivo.
- **Complejidad del Diseño**: Requiere un diseño más complejo del equipo.

#### Funcionamiento
1. **Generación de Plasma**: Se introduce un gas inerte en la cámara y se aplica un voltaje, al mismo tiempo que se utilizan campos magnéticos para confinar los electrones cerca del objetivo.
2. **Bombardeo del Objetivo**: Los iones bombardean el objetivo, y los electrones confinados aumentan la eficiencia del proceso de ionización.
3. **Deposición en el Sustrato**: Los átomos expulsados se depositan sobre el sustrato, formando una película delgada.

### Resumen Comparativo

| Característica         | DC Sputtering                         | RF Sputtering                        | Magnetron Sputtering                |
|------------------------|---------------------------------------|--------------------------------------|-------------------------------------|
| **Fuente de Energía**  | Corriente Directa (DC)                | Radiofrecuencia (RF)                 | Corriente Directa (DC) + Campos Magnéticos |
| **Aplicabilidad**      | Materiales Conductores                | Materiales Conductores y No Conductores | Materiales Conductores y No Conductores |
| **Ventajas**           | Uniformidad, Control Preciso          | Aptitud para Aislantes, Estabilidad  | Alta Tasa de Deposición, Menor Calentamiento |
| **Desventajas**        | Impurezas, Ineficiencia Energética    | Complejidad y Costo                  | Consumo No Uniforme del Objetivo     |
| **Eficiencia**         | Moderada                              | Alta                                 | Muy Alta                            |


## [[T.5.3 Plasma]]
