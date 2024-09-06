---
cards-deck: Profesional::Universidad::UNISA::Segundo Cuatrimestre::Nanoeletronica
---

# Italiano

## Introduzione
La **epitassia** è un processo di crescita di un film cristallino su un substrato cristallino dove il film depositato ha la stessa orientazione cristallina del substrato.

### Homoepitassia e Heteroepitassia
- L'epitassia può essere dello stesso semiconduttore Si/Si → CMOS o GaAs/GaAs → Mesfet, in questi casi si parla di *Homoepitassia*.
- Quando si tratta di 2 semiconduttori diversi, si parla di *Heteroepitassia*, ad esempio $Si/Al_2O_3$ (Zaffiro) = SOI → CMOS, GeSi/Si → GBT, HEMT, GaAs/Si → Mesfet o GaAs/Si → dispositivi fotovoltaici.

### Applicazione
- Nel film epitassiale si fabbricano spesso i dispositivi poiché riduce la resistenza di connessione permettendo di mantenere una elevata tensione di rottura.
- Migliora anche le prestazioni dei dispositivi grazie alla minore concentrazione di ossigeno e carbonio rispetto alla fetta.
![[Pasted image 20240619195251.png|300]]
![[Pasted image 20240619195311.png|300]]

### Caratteristiche Generali Richieste per la Tecnologia Epitassiale

- **Controllo della Composizione Chimica e dello Spessore del Film**
- **Bassa Densità di Difetti e Imperfezioni**
- **Eccellente Adesione**
- **Basso Stress**:
    - Dipendente dalla temperatura del processo e dal vuoto.
    - Raffreddandosi e uscendo dal vuoto, il materiale può comprimersi.
- **Rivestimento Conformale del Substrato**:
    - È cruciale per evitare zone senza contatto a causa di deformazioni.
    - Migliora con una temperatura più alta, anche se deve essere bilanciato con altri fattori.
- **Migliora la conducibilità**
- **Alta purezza**

### Tipi di Epitassia
1. **Epitassia di Fase Solida (SPE)**
   - Osservata nella ricristallizzazione indotta da trattamento termico di strati amorfi dopo l'impianto ionico.
2. **Epitassia di Fase Liquida (LPE)**
   - Utilizzata nella fabbricazione di composti III-V.
3. **Epitassia di Fase Vapore (VPE)**
   - La più utilizzata nella tecnologia del silicio.
   - Offre eccellente controllo sulla concentrazione di impurità e sulla perfezione cristallina.

## Processo di Epitassia tramite CVD #tarjeta-anki 
### Passi Fondamentali
1. **Introduzione di Gas Reattivi**:
    - Introduzione di gas reattivi, dopanti e diluenti inerti.
    - Mantenere vapore costante per una deposizione uniforme.
    - Camera aperta per flusso costante di gas.
2. **Trasporto dei Reattivi al Substrato**:
    - I gas reattivi si trasportano alla superficie del substrato.
3. **Adsorbimento sulla Superficie del Substrato**:
    - I reattivi si adsorbono sulla superficie del substrato, iniziando la crescita.
4. **Reazione Chimica sulla Superficie**:
    - La reazione chimica sulla superficie forma il film epitassiale.
5. **Desorbimento dei Prodotti di Reazione**:
    - I prodotti di reazione si desorbono dalla superficie.
6. **Rimozione dei Prodotti di Reazione**:
    - I prodotti di reazione sono eliminati dalla camera.
### Osservazioni Aggiuntive
- **Modello di Grove**:
    - Considera trasporto dei reattivi e reazione chimica.
    - **Trasporto vs. Flusso**: Il flusso è tangenziale; il trasporto è normale alla superficie.
    - **Migrazione e Reazioni sulla Superficie**: Il riscaldamento migliora l'assorbimento dei reattivi.
^1719767565172



### Modello di Grove 

#### Modello di grove Flussi #tarjeta-anki
Il modello di Grove per l'epitassia considera due flussi principali:
- **Flusso F1:** Trasporto dei reattivi alla superficie del substrato attraverso uno strato limite. Questo flusso descrive il trasporto dei gas reattivi dalla fase gassosa alla superficie di crescita del substrato. $$F_1=h_g(C_g-C_s)$$
    - È importante che non ci sia flusso perché, se c'è, non possiamo calcolare la diffusione. $$h_g=\frac{D_g}{\delta}$$
- **Flusso F2:** Flusso di reattivi consumati sulla superficie di crescita. Questo flusso rappresenta la quantità di reattivi consumati sulla superficie di crescita durante il processo di reazione chimica. $$F2=k_sC_s$$
    - Dove abbiamo la costante di Boltzmann in ks: $$k_s=k_0 \cdot e^{\frac{-E_A}{kT}}$$
- In condizioni stazionarie i due flussi sono uguali, quindi $$C_S=C_g\frac{1}{1+\frac{k_s}{h_g}}$$
    - Per $k_s>>h_g$ → $C_s$ →0 processo limitato dal trasporto di massa
    - Per $h_g>>k_s$ → $C_s$ → $C_g$ processo limitato dalla reazione alla superficie
- Questo modello è di grande importanza perché permette di controllare il processo epitassiale tramite il controllo di due variabili relativamente semplici: la temperatura e la concentrazione di reattivi.
- Si devono mantenere temperature adeguate per favorire la cinetica di reazione e la formazione di film epitassiali di alta qualità.
##### Concentrazione dei reattivi
Questa equazione è per la relazione del gas perfetto, otteniamo l'equazione $$C_g = \frac{P_g}{k \cdot T}$$
- Dove $C_g$ è la concentrazione dei reattivi, $P_g$ è la pressione del gas, $k$ è la costante dei gas e $T$ è la temperatura.
Dove possiamo vedere che la concentrazione dei reattivi in fase gassosa è essenziale per il successo del processo epitassiale. Questa concentrazione è direttamente correlata alla pressione del gas, che si *regola tramite una valvola all'ingresso della camera di deposizione*. 
- Anche in questa equazione si può vedere che la pressione non può essere troppo bassa perché modifica il processo.
- Perché non può essere troppo alta? **??????????** #Consultare
- La pressione neanche può essere troppo alta perché:
    - Collisioni molecolari → Formazione di particelle → Queste possono incorporarsi nel film depositato → Peggiore qualità del materiale
    - Controllo difficile del processo → Variazioni nella composizione e nelle proprietà del film depositato
- La misurazione della pressione nella camera si effettua tramite un sensore di capacità, che varia la sua capacità con la pressione del gas.
- **Supposizione di Gas Perfetto:** Considerando gas ideali, possiamo semplificare il calcolo della concentrazione dei reattivi e la sua relazione con la pressione del gas. Questo ci permette di controllare in modo più efficace il processo epitassiale ed evitare variazioni indesiderate a causa di cambiamenti di temperatura.
    - Supporre gas perfetto ci aiuta a supporre che i gas non interagiscono, per cui si possono sommare le pressioni.
^1719767565177


#### Velocità di Crescita #tarjeta-anki
##### In funzione della frazione molare
^1719767565181

![[Pasted image 20240409112258.png]]
È cruciale scegliere l'intervallo di lavoro dove il modello di Grove è applicabile. Questo si determina tramite l'analisi della curva di velocità di crescita del film in funzione della frazione molare $Y$. In questo intervallo, la velocità di crescita del film è proporzionale alla frazione molare $Y$, come descrive l'equazione $$V=\frac{k_sh_gC_tY}{(h_s+h_g)N}$$
- La scelta dell'intervallo di lavoro adeguato è anche influenzata da considerazioni fisiche e chimiche. Per esempio, un eccesso nella velocità di crescita può risultare in una mancanza di mobilità degli atomi al contatto con il substrato, compromettendo la qualità del deposito epitassiale.
- L'eccesso di frazione molare può portare alla formazione di acido durante il processo epitassiale. Per esempio, il diossido di silicio () può reagire con l'idrogeno () per formare silicio e acido cloridrico (). Questa reazione chimica può influenzare la crescita del film e la qualità del deposito finale.
    - Quindi allo stesso tempo di crescere, si fa un attacco chimico $SiCl_4+2H_2=Si+4HCl$
        - L'acido è il 4HCl
        - L'idrogeno serve per creare questo acido che è più "leggero" dell'ac ido che si crea senza idrogeno.
        - Anche si mette questo acido prima di iniziare il processo per pulire la superficie.
##### In base alla temperatura
Se sostituiamo l'equazione vista in precedenza con $Y = \frac{C_g}{C_t}$, otteniamo l'equazione: $V = \frac{k_s h_g C_g}{(k_s + h_g) N}$.
Il modello di Grove fornisce strumenti per comprendere e controllare la velocità di crescita nel processo epitassiale. Considerando diverse condizioni e variabili, possiamo distinguere tra due principali aree di operazione: il controllo per trasferimento di massa e il controllo per reazione.
![[Pasted image 20240409113041.png]]
**Controllo per Trasferimento di Massa:**
- $h_g \ll k_s \rightarrow V = \frac{h_g C_g}{N}$
  - Quando $h_g$ è molto minore di $k_s$, la velocità di crescita $V$ è determinata principalmente dalla concentrazione dei reagenti e dalla velocità di trasferimento di massa. In questo caso, il processo è controllato dal trasferimento di massa e la velocità di crescita segue l'equazione $V = \frac{h_g C_g}{N}$.
  - Questo tipo di controllo è generalmente più stabile, ma il processo può essere più lento a causa della limitazione nel trasferimento di massa.
**Controllo per Reazione:**
- $k_s \ll h_g \rightarrow V = \frac{k_s C_g}{N}$
  - Quando $k_s$ è molto minore di $h_g$, la velocità di crescita $V$ è influenzata principalmente dalla reazione chimica sulla superficie di crescita. In questo caso, il processo è controllato dalla reazione e la velocità di crescita segue l'equazione $V = \frac{k_s C_g}{N}$.
  - Sebbene questo tipo di controllo possa portare a una velocità di crescita più rapida, il processo può diventare più instabile a causa della sensibilità alle variazioni nella concentrazione dei reagenti e ad altri fattori.
- È fondamentale evitare le condizioni in cui sia il trasferimento di massa sia la reazione contribuiscono in modo significativo al processo. La regione mista può portare a un'operazione meno prevedibile e a risultati inconsistenti.
- **Grafico di Arrhenius:** La relazione tra la temperatura e la velocità di crescita segue un modello di Arrhenius, in cui la velocità di crescita è attivata termicamente e segue l'equazione $A = A_0 e^{-\frac{E_q}{kT}}$.
#### Osservazioni Importanti
- L'uso di acido cloridrico per pulire la superficie del substrato può danneggiare il tubo di quarzo, cosa da considerare durante il processo.
- La non uniformità della temperatura nel tubo può essere mitigata utilizzando diversi sistemi di riscaldamento, come resistenze o lampade al quarzo.
- Per garantire condizioni uniformi lungo tutta la lunghezza del tubo, si può applicare un gradiente di temperatura per bilanciare la pressione dei gas precursori.
- Nella pratica si può vedere come il modello si adempie nella realtà.
    - Si mantiene anche questo modello per diversi gas precursori del silicio.
    - Il silano è efficace come gas precursore, ma il suo uso a alte temperature può generare polvere di silicio, influenzando la qualità del deposito epitassiale.
    - Quando si graficano sperimentalmente per diversi gas, si può vedere che le rette decrescenti sono parallele, per cui l'attivazione e l'energia di attivazione sono le stesse.
    - Questa energia di attivazione è quella dell'atomo di silicio-silicio, quindi ha senso che sia la stessa, dato che è sempre il silicio.
##### Da Sistemare
- L'acido cloridrico caldo si pulisce con l'argo.

## Modello di Crescita Atomica #tarjeta-anki
Il processo di crescita atomica è fondamentale per la deposizione epitassiale, soprattutto in sistemi di alta temperatura come 1000-1500°C. Durante questo processo, possono verificarsi reazioni in fase gassosa, che possono essere omogenee o eterogenee.
### Reazioni Omogenee e Eterogenee
- **Reazioni Omogenee:** Queste reazioni avvengono tra gas in fase vapore (per questo omogenee) e possono dare luogo alla formazione di particelle indesiderate, che possono nuclearsi e formare particelle solide nel gas causando la formazione di film con scarsa adesione, bassa densità e alta concentrazione di difetti. Questa reazione si deve al fatto che si lavora a alte temperature.
- **Reazioni Eterogenee:** Avvengono all'interfaccia delle due fasi (gassosa e solida), per cui si chiamano eterogenee. Il gas precursore arriva alla superficie del substrato, poi sulla superficie si dissocia e l'atomo del semiconduttore si adagia sulla superficie e i sottoprodotti gassosi rimangono nella camera. Questi atomi di semiconduttore (ad-atomi) si spostano sulla superficie incorporandosi nella rete cristallina del substrato e contribuendo alla crescita epitassiale, questi atomi si spostano verso siti a bassa energia, come difetti.
### Modello di Crescita per Diclorosilano (DCS) e Drogaggio con Arsina
![[Pasted image 20240409120713.png]]
#### Processo di Adsorbimento e Reazione
1. **Adsorbimento di specie chimiche:** Il diclorosilano (DCS) e l'arsina si adsorbono sulla superficie del substrato.
2. **Reazioni chimiche sulla superficie:** Queste specie reagiscono chimicamente sulla superficie, liberando atomi che si integrano nella struttura del materiale.
3. **Migrazione di atomi adsorbiti:** Gli atomi adsorbiti (ad-atomi) migrano verso posizioni di legame più stabili sulla superficie, preferibilmente lungo scalini e angoli.
#### Nucleazione e Crescita
- **Nucleazione su superfici piane:** È più difficile iniziare la nucleazione su superfici piane, ma è facilitata negli scalini e angoli della superficie. Sulla superficie è necessaria un raggio critico minimo.
- **Crescita laterale:** Una volta che gli atomi si sono nucleati, la crescita continua lateralmente aumentando il numero di legami con gli atomi del substrato.
- **Crescita cristallina vs. policristallina:** Se la velocità di crescita è troppo alta, gli ad-atomi non hanno tempo sufficiente per migrare alle posizioni "cristalline" ideali, risultando in crescita policristallina.
### Regione di Transizione e Energia di Attivazione
- **Transizione tra crescita cristallina e policristallina:** La regione di transizione varia esponenzialmente con la temperatura ed è associata a una energia di attivazione comparabile all'autodiffusione del silicio.
- **Importanza del controllo della temperatura:** Un controllo preciso della temperatura è essenziale per garantire una crescita epitassiale di alta qualità ed evitare la formazione di policristalli.
- Questo modello atomistico è coerente con il risultato sperimentale della massima velocità di crescita di silicio monocristallino.
- Con una velocità elevata di accrescimento, gli atomi adsorbiti ("ad-atomi") non hanno tempo sufficiente per migrare verso le posizioni cristalline, agli angoli → crescita policristallina.
- La regione di transizione varia esponenzialmente con la temperatura con energia di attivazione $E_a \approx$ 5eV. Questa energia è comparabile con l'energia di attivazione per l'autodiffusione del silicio.
^1719767565185




## Gas Precursori
#### Velocità di Crescita
![[Pasted image 20240409120223.png]]
#### Commenti
![[Pasted image 20240409120234.png]]

- Il silano è efficace come gas precursore, ma il suo uso a alte temperature può generare polvere di silicio, influenzando la qualità del deposito epitassiale.
    - Anche può essere un problema di sicurezza.
- Si usa adesso il silano perché lavora a una bassa temperatura.

## Tipi di Reattori
### Reattore Orizzontale
In questo tipo di reattore, i substrati sono posizionati orizzontalmente all'interno della camera di crescita. L'alimentazione di gas e reattivi si effettua tramite iniettori situati nella parte superiore del reattore. La disposizione orizzontale permette un flusso di gas uniforme sulla superficie dei substrati, favorendo una crescita epitassiale uniforme su tutta la superficie.
![[Pasted image 20240409120951.png]]
### Reattore Verticale
I reattori verticali sono simili agli orizzontali, ma in questo caso, i substrati sono posizionati verticalmente all'interno della camera di crescita. I gas e i reattivi si introducono dalla parte inferiore del reattore e salgono verso i substrati. Questo design fornisce una distrib
uzione uniforme di gas e reattivi lungo la superficie verticale dei substrati, promuovendo una crescita epitassiale uniforme.
![[Pasted image 20240409121006.png]]
### Reattore a Barile
I reattori a barile, noti anche come reattori di tipo barile, hanno una disposizione cilindrica. I substrati sono posizionati all'interno del barile, che può ruotare per garantire una deposizione uniforme su tutta la superficie. I gas e i reattivi si introducono nel barile dalla parte superiore, creando un flusso ascendente che interagisce con i substrati. Questo design facilita una crescita epitassiale uniforme e controllata in tutte le direzioni.
![[Pasted image 20240409121015.png]]
### Reattore di Wafer Singoli
1. La camera sigillata si riempie di un ambiente di idrogeno.
2. Capacità per multiple camere in un telaio principale.
3. Dimensione del wafer grande (fino a 300 mm).
4. Miglior controllo dell'uniformità nella crescita dei strati.
![[Pasted image 20240409140011.png]]




In un sistema di wafer singoli, il processo di epitassia segue i seguenti passi:

1. Purga di idrogeno, pulizia e aumento graduale della temperatura.
2. Crescita dello strato epitassiale.
3. Purga di idrogeno e spegnimento del riscaldamento.
4. Scarico e carico del wafer.
5. Pulizia con HCl in situ.

### Processo di Epitassia in Lotti

1. Purga di idrogeno e aumento graduale della temperatura.
2. Pulizia con HCl.
3. Crescita dello strato epitassiale.
4. Purga di idrogeno e raffreddamento graduale della temperatura. Questo non si fa più nell'industria.
5. Purga con azoto.
6. Apertura della camera, scarico e carico dei wafer.

### Tendenze Future:

- Aumento delle dimensioni dei wafer.
- Crescita epitassiale di wafer singoli.
- Epitassia a bassa temperatura.
- Vuoto ultra alto (UHV, fino a 10^(-9) Torr).
- Epitassia selettiva.

### Osservazioni
- Riscaldamento Superiore e Inferiore:
    - Con il riscaldamento a lampada si aumenta la temperatura dall'alto.
    - Si integra con un altro sistema di riscaldamento dalla parte inferiore del substrato.
- La rotazione del silicio durante il processo è cruciale per assicurare una deposizione uniforme.
    - Non è banale la rotazione del silicio; dobbiamo non rompere il vuoto.

## Problemi del Processo #tarjeta-anki
### Autodrogaggio e Diffusione Indesiderata
#### Problemi
- Mantenere il silicio ad alta temperatura può:
    - Causare il movimento dei droganti fuori dal substrato, risultando in:
        - Una perdita di controllo sul profilo di drogaggio. *Diffusione indesiderata*
            - Variazioni indesiderate nella concentrazione dei droganti.
        - Modificando la concentrazione dei droganti nella camera di reazione. *Autodrogaggio*
            - I sottoprodotti gassosi della dissociazione dei precursori devono essere rimossi per evitare la loro rideposizione.
#### Soluzioni
- Si utilizza il silano per la deposizione a basse temperatura, minimizzando i problemi.
    - L'arsenico richiede condizioni specifiche di temperatura. L'uso di basse temperature non è adeguato, poiché potrebbe non incorporare adeguatamente il drogante nel substrato.
- Aumentare la pressione sul substrato può aiutare a prevenire che i droganti escano dal substrato, migliorando il controllo sulla concentrazione dei droganti.
- Selezionare droganti con bassa pressione di vapore o basso coefficiente di diffusione può minimizzare la diffusione indesiderata. Ad esempio, evitare l'uso del fosforo che ha alta mobilità alle alte temperature.
- Diminuire la pressione nel reattore può aiutare a eliminare i droganti non voluti tramite il flusso di gas, riducendo il rischio di autodrogaggio.
- Crescere uno strato iniziale di substrato non drogato prima di introdurre il drogante può aiutare a stabilizzare il processo ed evitare la diffusione di droganti non voluti.
#### Mantenimento della Qualità del Substrato
- **Pulizia Chimica:**
    - È cruciale effettuare una pulizia chimica del substrato per eliminare contaminanti superficiali prima del processo epitassiale.
- **Pulizia In Situ:**
    - Si utilizza una pulizia in situ con una miscela di HCl (1-5%) e H₂ a temperature superiori a 1100°C per eliminare lo strato di ossido e altri contaminanti, garantendo una superficie pulita per la crescita epitassiale.
### Difetti nel Processo di Epitassia
#### Origine dei Difetti
1. **Difetti nel Substrato:**
    - **Preparazione del Substrato:**
        - La qualità del film epitassiale è direttamente limitata dalla qualità del substrato originale. I difetti presenti nel substrato si propagano al film epitassiale.
        - Per ottenere un film di alta qualità, è fondamentale iniziare con un substrato privo di difetti e ben preparato.
    - **Imperfezioni del Substrato:**
        - Le imperfezioni nel substrato, come dislocazioni, vacanze e difetti interstiziali, possono agire come siti di nucleazione per difetti aggiuntivi nel film epitassiale.
#### Difetti nei Film Epitassiali
1. **Dislocazioni:**
    - Si formano quando abbiamo stress sulla fetta.
    - **Origine delle Dislocazioni:**
        - Possono originarsi dalle dislocazioni esistenti nel substrato.
        - Causate da alto drogaggio, noto come dislocazioni tipo "misfit".
        - Generate da gradienti termici nel substrato, a causa del contatto termico disomogeneo con il susceptor.
	        - Questo può generare un effetto di tazza (prossima immagine).
![[Pasted image 20240409143136.png]]
2. **Difetti di Impacchettamento (Stacking Faults - SF):**
    - **Origine dei Difetti di Impacchettamento:**
        - Questi difetti si originano a causa di qualche imperfezione sulla superficie del silicio, che perturba la crescita locale e genera SF.
        - Esempi di imperfezioni includono particelle di SiO₂, Si₃N₄, SiC, o la presenza di vapore di CO₂ nel reattore che forma SiO.
#### Soluzioni ai Difetti
1. **Dislocazioni:**
    - **Uso del "Gettering":**
        - Tecnica che implica l'introduzione di un materiale che cattura le impurità e difetti, allontanandoli dalle aree critiche del substrato.
        - Per evitare lo stress termico dobbiamo riscaldare da entrambi i lati, e anche si modifica per evitare il contatto sotto.
		- Questo è meno efficiente.
![[Pasted image 20240409143422.png]]
    - **Uso di Substrati con Strati Intermedi:**
        - Utilizzare substrati con strati di materiali che hanno parametri di reticolo diversi per alleviare lo stress e ridurre la formazione di dislocazioni tipo "misfit". Ad esempio, utilizzare leghe di Si-Ge che hanno un parametro reticolare diverso da quello del silicio, aiutando a rilassare lo stress tramite la formazione controllata di dislocazioni.
2. **Difetti di Impacchettamento:**
    - **Minimizzazione dei Contaminanti:**
        - Mantenere un'atmosfera del reattore pulita per minimizzare la presenza di particelle e vapori che possono causare difetti di impacchettamento.
    - **Controllo della Superficie:**
        - Assicurarsi che la superficie del substrato sia priva di imperfezioni prima dell'inizio del processo epitassiale.
^1719767565190



### Influenza dei Parametri di Processo nella Epitassia

#### Dipendenza da Variabili di Processo

1. **Orientamento del Substrato:**
   - L'orientamento del substrato influenza il modo in cui gli atomi si dispongono sulla superficie durante la crescita epitassiale. Differenti orientamenti possono favorire la formazione di dislocazioni o difetti superficiali.

2. **Velocità di Deposizione:**
   - La velocità di deposizione deve essere ottimizzata. Una velocità troppo alta può causare la formazione di difetti a causa dell'incapacità degli atomi di organizzarsi correttamente sulla superficie, mentre una velocità troppo bassa può essere inefficiente e costosa.

3. **Temperatura di Deposizione:**
   - La temperatura influenza la mobilità degli atomi sulla superficie. Una temperatura troppo bassa può ridurre la mobilità, portando a una crescita disordinata, mentre una temperatura troppo alta può causare la desorbimento dei precursori o la diffusione indesiderata

 dei dopanti.

4. **Sorgente di Si:**
   - La scelta del precursore di silicio (ad esempio, SiH₄ o SiCl₄) influisce sui meccanismi di crescita e sulla qualità del film. Differenti precursori possono indurre differenti tipi di difetti o reazioni secondarie.

5. **Pressione:**
   - La pressione nel reattore deve essere attentamente controllata. Una pressione troppo alta può aumentare le collisioni molecolari nel gas, mentre una pressione troppo bassa può ridurre la quantità di materiale disponibile per la deposizione.

#### Effetti di Spostamento, Distorsione e Scomparsa delle Strutture

1. **Condizioni di Deposizione e Effetti sui Pattern:**
   - **Spostamento delle Strutture:**
     - Il pattern shift (spostamento delle strutture) può essere influenzato dalle condizioni di temperatura e pressione. Ad esempio, a 1110°C e 100 Torr, i reattori radiali possono mostrare spostamenti maggiori rispetto ai reattori verticali.
   - **Distorsione delle Strutture:**
     - La distorsione del pattern è minore in presenza di agenti clorurati come Cl₂ o HCl rispetto all'uso di SiH₄.
   - **Scomparsa delle Strutture:**
     - Condizioni estreme di temperatura e pressione possono portare alla scomparsa delle strutture epitassiali desiderate.

#### Soluzioni per Minimizzare i Difetti

1. **Compromesso Empirico:**
   - Poiché le dipendenze influenzano i difetti in modo opposto, spesso è necessario trovare un compromesso empirico che ottimizzi tutti i parametri chiave per ridurre al minimo i difetti senza compromettere la velocità di deposizione e la qualità del film.

2. **Uso di Reattori Ottimizzati:**
   - **Reattori Verticali Riscaldati Induttivamente:**
     - Producono minori pattern shift rispetto ai reattori radiali nelle stesse condizioni di deposizione.
   - **Scelta del Precursore:**
     - L'uso di SiH₄ riduce il pattern shift. Tuttavia, la presenza di Cl₂ o HCl può ridurre ulteriormente la distorsione del pattern.





## Observaciones
- Quando facciamos misura con luce, dobbiamo avere in conto che la reflexione multiple nel nostro substrato e divresa con la spessore del nostro substrato e anche del nostro metallo supra 
- Per fare materiales transparente e conductivi, abbiamo bisogno di molto temperatura
- Anche is puoi ussare la polarizacione per evitare luce riflesata 
- La presione no puoi essere troppo bassa per
- Il flusso di gas si misura in []
	- Si misura en valore standar preciso
	- Anche si misura con flusimetro
		- In la entrada abbiamo un flusimetro
		- Questa usano valvula mecanica, perche il flusso e combustible e puoi combustionare si le valvule é electronica
		- Si prendi 1/100 di gase o 1/1000 y si la fa passare per una resistencia di flusso, ma cio é resistencia mecanica
			- Sapiendo quale gase é e quando muove la resistencia, possiamo sapere il flusso
		- Anche si puoi misurare con le variazione di temperatura


**Pedir apuntes de esto**
- Il spectrometro di massa per misurare le perdida *???????*
- Si ho un impianto dove c’é perdida, per sapere quale é il impianto o dove é la rotura si mette helio, e mettiamo prima de la uscita, mettiamo un spectrometro di massa, il quale é calibrato per helio, quindi si mediamo qualcosa nel espectrometro de massa é perche c’é rotura
- Anche si puo utilizzare questi sistema ver vedere le particula que sono nel nostro tubo
- Anche si puoi medire il helio dentro gia che questi pasa per il filamento del espectrometro, e generano una corrente gia che sono ionizanos, quindi si puoi sapere quanto helio ci sono


**Domandare questo**
- Guarnizione di goma e di ram 




## Dudas
Perche sono inclinato waffer e non sotto verticale in totale o horizontale in totale *??????* #Consultar






































# Espagnolo
## Introduccion
La **epitaxia** es un proceso de crecimiento de una película cristalina sobre un sustrato cristalino donde la película depositada tiene la misma orientación cristalina que el sustrato. 
### Homoepitaxia e Heteroepitaxia
- La epitaxia puede ser del mismo semiconductor Si/Si → CMOS o GaAs/GaAs → Mesfet, en estos casos hablamos de una *Homoepitaxia*
- Cuando es de 2 semiconductores distintos hablamos de una *Heteroepitaxia*, por ejemplo $Si/Al_2O_3$(Zaffiro) = SOI → CMOS, GeSi/Si → GBT,HEMT, GaAs/Si → Mesfet o GaAs/Si → dispositivos fotovoltaicos


### Aplicazione
- En la capa epitaxial se suelen fabricar los dispositivos ya que reduce la resitencia de conexion permitiendo mantener una elevada tension de rotura
- Esta tambien suele mejorar las prestaciones de los dispositvos por la menor concentracion de oxigeno y carbono respecto a la fete
![[Pasted image 20240619195251.png|300]]
![[Pasted image 20240619195311.png|300]]

### Características Generales Requeridas para la Tecnología Epitaxial

- **Control de la Composición Química y del Espesor del Film**
- **Baja Densidad de Defectos e Imperfecciones**
- **Excelente Adhesión**
- **Bajo Estrés**:
	- Dependiente de la temperatura del proceso y el vacío.
	- Al enfriarse y salir del vacío, el material puede comprimirse.
- **Recubrimiento Conformal del Sustrato**:
	- Es crucial para evitar zonas sin contacto debido a deformaciones.
	- Mejora con una mayor temperatura, aunque debe equilibrarse con otros factores.
- **Mejora conductividad**
- **Alta pureza**



### Tipos de Epitaxia
1. **Epitaxia de Fase Sólida (SPE)**
   - Observada en la recristalización inducida por tratamiento térmico de capas amorfas después de la implantación iónica.
2. **Epitaxia de Fase Líquida (LPE)**
   - Utilizada en la fabricación de compuestos III-V.
3. **Epitaxia de Fase Vapor (VPE)**
   - La más utilizada en la tecnología del silicio.
   - Ofrece excelente control sobre la concentración de impurezas y la perfección cristalina.

## Proceso de Epitaxia por CVD
### Pasos Fundamentales

1. **Introducción de Gases Reactivos**:
    - Introducción de gases reactivos, dopantes y diluyentes inertes.
    - Mantener vapor constante para deposición uniforme.
    - Cámara abierta para flujo constante de gases.
2. **Transporte de Reactivos al Sustrato**:
    - Gases reactivos se transportan a la superficie del sustrato.
3. **Adsorción en la Superficie del Sustrato**:
    - Reactivos se adsorben en la superficie del sustrato, iniciando el crecimiento.
4. **Reacción Química en la Superficie**:
    - Reacción química en la superficie forma el film epitaxial.
5. **Desorción de Productos de Reacción**:
    - Productos de reacción se desorben de la superficie.
6. **Remoción de Productos de Reacción**:
    - Productos de reacción son eliminados de la cámara.

### Observaciones Adicionales

- **Modelo de Grove**:
    - Considera transporte de reactivos y reacción química.
    - **Transporte vs. Flujo**: Flujo es tangencial; transporte es normal a la superficie.
    - **Migración y Reacciones en la Superficie**: Calentamiento mejora absorción de reactivos.


### Modelo de Grove

#### Flujos
El modelo de Grove para epitaxia considera dos flujos principales:

- **Flujo F1:** Transporte de los reactivos a la superficie del sustrato a través de una capa límite. Este flujo describe el transporte de los gases reactivos desde la fase gaseosa hacia la superficie de crecimiento del sustrato. $$F_1=h_g(C_g-C_s)$$
	- É importante che non c’é flusso perche, si c’é non possiamo calculare la difussione.$$h_g=\frac{D_g}{\delta}$$
- **Flujo F2:** Flujo de reactivos consumidos en la superficie de crecimiento. Este flujo representa la cantidad de reactivos que se consumen en la superficie de crecimiento durante el proceso de reacción química. $$F2=k_sC_s$$
	- Donde tenemos la constante de boltzmann en ks: $$k_s=k_0 \cdot e^{\frac{-E_A}{kT}}$$

- En condizione stazionarie le due flusso sono equale, quindi $$C_S=C_g\frac{1}{1+\frac{k_s}{h_g}}$$
	- Per $k_s>>h_g$ → $C_s$ →0 processo limitato dal trasporto di masssa
	- Per $h_g>>k_s$ → $C_s$ → $C_g$ processo limitato dalla reazione alla superficie

- Este modelo es de gran importancia porque permite controlar el proceso epitaxial mediante el control de dos variables relativamente simples: la temperatura y la concentración de reactivos.
- Se deben mantener temperaturas adecuadas para favorecer la cinética de reacción y la formación de películas epitaxiales de alta calidad.


##### Concentracion de reactivos
Esta ecuacion es por la relacion de gas perfecto obtenemos la ecuacion $$C_g = \frac{P_g}{k \cdot T}$$
- donde $C_g$ es la concentración de reactivos, $P_g$ es la presión del gas, $k$ es la constante de los gases y $T$ es la temperatura.
Donde podemos ver que la concentración de reactivos en fase gaseosa es esencial para el éxito del proceso epitaxial. Esta concentración está directamente relacionada con la presión del gas, que se *ajusta mediante una válvula en la entrada de la cámara de deposición*. 
- Tambien en esta ecuaciones si puede ver que la presion no puede ser demasiado baja porque modifica el proceso
- Perche non puoi essere troppo altra **??????????** #Consultar 
- La presione neanche puó essere troppo alta perche:
	- Collisioni molecolari → Fomarzione di particelle → Questi possono incorporarsi nel fil depositato → Peggiore qualita del materiale
	- Controllo Difficile del processo → Variazioni nella composizione e nelle propietá del film depositato

  - La medición de la presión en la cámara se realiza mediante un sensor de capacitancia, que varía su capacitancia con la presión del gas.

-  **Suposición de Gas Perfecto:** Al considerar gases ideales, podemos simplificar el cálculo de la concentración de reactivos y su relación con la presión del gas. Esto nos permite controlar de manera más efectiva el proceso epitaxial y evitar variaciones no deseadas debido a cambios en la temperatura.
	- Suponer gas perfecto nos ayuda a suponer que los gases no interactuan por lo cual se puede sumar las presiones 
#### Velocita di crescita
##### En funcion de la fraccion molar

![[Pasted image 20240409112258.png]]
 Es crucial elegir el rango de trabajo donde el modelo de Grove es aplicable. Esto se determina mediante el análisis de la curva de tasa de crecimiento del film en función de la fracción molar $Y$. En este rango, la velocidad de crecimiento del film es proporcional a la fracción molar $Y$, como describe la ecuación
 $$V=\frac{k_sh_gC_tY}{(h_s+h_g)N}$$
- La elección del rango de trabajo adecuado también está influenciada por consideraciones físicas y químicas. Por ejemplo, un exceso en la tasa de crecimiento puede resultar en una falta de movilidad de los átomos al encontrarse con el sustrato, lo que compromete la calidad del depósito epitaxial.
- El exceso de fracción molar puede llevar a la formación de ácido durante el proceso epitaxial. Por ejemplo, el dióxido de silicio () puede reaccionar con hidrógeno () para formar silicio y ácido clorhídrico (). Esta reacción química puede afectar el crecimiento del film y la calidad del depósito final.
	- Quindi al stesso tempo di crescere , si fa un attaco quimico $SiCl_4+2H_2=Si+4HCl$
		- Il acido é il 4HCl
		- Il hidrogene serve per creare queste acido che é piú “liviano” che il acido che si crea sensa hidrogeno
		- Anche si mette questi acido prima di inziare il proceso per pulire la superficie

##### In base alla temperatura

Se sostituiamo l'equazione vista in precedenza con $Y = \frac{C_g}{C_t}$, otteniamo l'equazione: $V = \frac{k_s h_g C_g}{(k_s + h_g) N}$.

Il modello di Grove fornisce strumenti per comprendere e controllare la velocità di crescita nel processo epitassiale. Considerando diverse condizioni e variabili, possiamo distinguere tra due principali aree di operazione: il controllo per trasferimento di massa e il controllo per reazione.
![[Pasted image 20240409113041.png]]
**Controllo per Trasferimento di Massa:**
- $h_g \ll k_s \rightarrow V = \frac{h_g C_g}{N}$
  - Quando $h_g$ è molto minore di $k_s$, la velocità di crescita $V$ è determinata principalmente dalla concentrazione dei reagenti e dalla velocità di trasferimento di massa. In questo caso, il processo è controllato dal trasferimento di massa e la velocità di crescita segue l'equazione $V = \frac{h_g C_g}{N}$.
  - Questo tipo di controllo è generalmente più stabile, ma il processo può essere più lento a causa della limitazione nel trasferimento di massa.

**Controllo per Reazione:**
- $k_s \ll h_g \rightarrow V = \frac{k_s C_g}{N}$
  - Quando $k_s$ è molto minore di $h_g$, la velocità di crescita $V$ è influenzata principalmente dalla reazione chimica sulla superficie di crescita. In questo caso, il processo è controllato dalla reazione e la velocità di crescita segue l'equazione $V = \frac{k_s C_g}{N}$.
  - Sebbene questo tipo di controllo possa portare a una velocità di crescita più rapida, il processo può diventare più instabile a causa della sensibilità alle variazioni nella concentrazione dei reagenti e ad altri fattori.

- È fondamentale evitare le condizioni in cui sia il trasferimento di massa sia la reazione contribuiscono in modo significativo al processo. La regione mista può portare a un'operazione meno prevedibile e a risultati inconsistenti.
- **Grafico di Arrhenius:** La relazione tra la temperatura e la velocità di crescita segue un modello di Arrhenius, in cui la velocità di crescita è attivata termicamente e segue l'equazione $A = A_0 e^{-\frac{E_q}{kT}}$.


#### Observaciones imporatntes
- El uso de ácido clorhídrico para limpiar la superficie del sustrato puede dañar el tubo de cuarzo, lo que debe tenerse en cuenta durante el proceso.
 - La no uniformidad de la temperatura en el tubo puede mitigarse utilizando diferentes sistemas de calentamiento, como resistencias o lámparas de cuarzo.
 - Para garantizar condiciones uniformes en toda la longitud del tubo, se puede aplicar un gradiente de temperatura para equilibrar la presión de los gases precursores.

- En la practica se puede ver como el modelo se cumple en la realidad
	- Tambien se mantiene este modelo para distintos gases precursores de silicio
	- El silano es efectivo como gas precursor, pero su uso a altas temperaturas puede generar polvo de silicio, lo que puede afectar la calidad del depósito epitaxial
	- Cuando se grafica experimentalmente para distintos gases se puede ser que las rectas decrecientes son paralelas, por lo cual la actividacion y la energia de acticacion es la misma
	- Esta energia de activacion es la del atomo silicio-silicio, por lo cual tiene sentido que sea la misma, ya que siempre es el silicio 
##### Falta acomodar
- Il acido cloridrico caliente se limpia con el argo



## Modelo de Crecimiento Atómico

El proceso de crecimiento atómico es fundamental para la deposición epitaxial, especialmente en sistemas de alta temperatura como 1000-1500°C. Durante este proceso, pueden ocurrir reacciones en fase gaseosa, que pueden ser homogéneas o heterogéneas.

### Reacciones Homogéneas y Heterogéneas

- **Reacciones Homogéneas:** Estas reacciones ocurren entre gases en fase vapor(por eso homogenea) y pueden dar lugar a la formación de partículas no deseadas, estos pueden nuclearse y formar particulas solidas en el gas causando la formación de películas con mala adhesión, baja densidad y alta concentración de defectos. Esta reaccion se debe a que se trabaja a altas temperaturas

- **Reacciones Heterogéneas:** Ocurren en la interfaz de las dos fases(gaseosa y solida) por eso se llama heterogenea. El gas precurso llega a la superficie del subtrato,luego en la superficie se disocia y el atomo del semiconductor se adhiere a la superficie y los subproductos gaseosos quedan en la camara, luegos estos atomos de semicondcutores(adatomos), se desplazan por la superficie incorporandoce en la red cristalina del subtrato y contribuyendo al crecimiento epitaxial, estos atomos se desplazan a sitios de baja energia, como defectos

### Modelo de Crecimiento para Diclorosilano (DCS) y Dopado con Arsina
![[Pasted image 20240409120713.png]]



#### Proceso de Adsorción y Reacción

1. **Adsorción de especies químicas:** El diclorosilano (DCS) y la arsina se adsorben en la superficie del sustrato.
2. **Reacciones químicas en la superficie:** Estas especies reaccionan químicamente en la superficie, liberando átomos que se integran en la estructura del material.
3. **Migración de átomos adsorbidos:** Los átomos adsorbidos (adátomos) migran hacia posiciones de unión más estables en la superficie, preferentemente a lo largo de escalones y ángulos.

#### Nucleación y Crecimiento

- **Nucleación en superficies planas:** Es más difícil iniciar la nucleación en superficies planas, pero es facilitada en los escalones y ángulos de la superficie. Sulla superficie é necessaria un raggio critico minimo
- **Crecimiento lateral:** Una vez que los átomos se han nucleado, el crecimiento continúa lateralmente al aumentar el número de enlaces con los átomos del sustrato.
- **Crecimiento cristalino vs. policristalino:** Si la velocidad de crecimiento es demasiado alta, los adátomos no tienen tiempo suficiente para migrar a las posiciones "cristalinas" ideales, lo que resulta en crecimiento policristalino.

### Región de Transición y Energía de Activación

- **Transición entre crecimiento cristalino y policristalino:** La región de transición varía exponencialmente con la temperatura y está asociada a una energía de activación comparable a la autodifusión del silicio.
- **Importancia del control de la temperatura:** Un control preciso de la temperatura es esencial para asegurar un crecimiento epitaxial de alta calidad y evitar la formación de policristales.

- Questo modello atomistico é coerente con il risultato sperimentale della massima velocitá di crescita di silicio monocristalino
- Con una velocitá elevata di acrescimento, gli atomi adsorbiti(“adatomi“) non hanno tempo sufficiente per migrare verso le posizione cristalline, agli angoli → crece policristalino
- Le regione di transizione varia esponenzialmente con la temperatura con energiadi attivazione $E_a \approx$ 5eV. Questa energia é comparabile con l’energia di arrivazione per láutodiffusinoe del silicio


## Gases precursores
#### Velocidad de crescita
![[Pasted image 20240409120223.png]]
#### Comentariow
![[Pasted image 20240409120234.png]]

  - El silano es efectivo como gas precursor, pero su uso a altas temperaturas puede generar polvo de silicio, lo que puede afectar la calidad del depósito epitaxial.
	  - Anche puo essere un problema di sicurezza
  - Si usa adesso il silano perche lavora a una bassa temperatura


## Tipos de ractores

### Reactor Horizontal

En este tipo de reactor, los sustratos se colocan horizontalmente dentro de la cámara de crecimiento. La alimentación de gases y reactivos se realiza a través de inyectores ubicados en la parte superior del reactor. La disposición horizontal permite un flujo de gases uniforme sobre la superficie de los sustratos, lo que favorece un crecimiento epitaxial uniforme en toda la superficie.
![[Pasted image 20240409120951.png]]
### Reactor Vertical

Los reactores verticales son similares a los horizontales, pero en este caso, los sustratos se colocan verticalmente dentro de la cámara de crecimiento. Los gases y reactivos se introducen desde la parte inferior del reactor y ascienden hacia los sustratos. Este diseño proporciona una distribución uniforme de gases y reactivos a lo largo de la superficie vertical de los sustratos, lo que promueve un crecimiento epitaxial uniforme.
![[Pasted image 20240409121006.png]]
### Reactor de Barril

Los reactores de barril, también conocidos como reactores de tipo barril, tienen una disposición cilíndrica. Los sustratos se colocan en el interior del barril, que puede girar para garantizar una deposición uniforme en toda su superficie. Los gases y reactivos se introducen en el barril desde la parte superior, creando un flujo ascendente que interactúa con los sustratos. Este diseño facilita un crecimiento epitaxial uniforme y controlado en todas las direcciones.

![[Pasted image 20240409121015.png]]

### Reactor de obleas individuales
1. La cámara sellada se llena de un ambiente de hidrógeno.
2. Capacidad para múltiples cámaras en un marco principal.
3. Tamaño de oblea grande (hasta 300 mm).
4. Mejor control de uniformidad en el crecimiento de las capas.
![[Pasted image 20240409140011.png]]
En un sistema de obleas individuales, el proceso de epitaxia sigue los siguientes pasos:

1. Purga de hidrógeno, limpieza y aumento gradual de la temperatura.
2. Crecimiento de la capa epitaxial.
3. Purga de hidrógeno y apagado del calentamiento.
4. Descarga y carga de la oblea.
5. Limpieza con HCl in situ.
### Proceso de epitasia en lotes

1. Purga de hidrógeno y aumento gradual de la temperatura.
2. Limpieza con HCl.
3. Crecimiento de la capa epitaxial.
4. Purga de hidrógeno y enfriamiento gradual de la temperatura. Esto ya no se hace mas en la industria
5. Purga con nitrógeno.
6. Apertura de la cámara, descarga y carga de las obleas.


### Tendencias Futuras:

- Aumento en el tamaño de obleas.
- Crecimiento epitaxial de obleas individuales.
- Epitaxia a baja temperatura.
- Vacío ultra alto (UHV, hasta 10^(-9) Torr).
- Epitaxia selectiva.
### Observaciones 
- Riscaldamento Superiore e Inferiore
    - Con il riscaldamento a lampada si aumenta la temperatura da sopra
    - Si integra con un altro sistema di riscaldamento dalla parte inferiore del substrato
- La rotazione del silicio durante il processo é cruciale per assicurare una deposizione uniforme.
    - Non è banale la rotazione del silicio; dobbiamo non rompere il vuoto


## Problemas del proceso
### Autodrogaggio e difusione indesiderata
#### Problemi
- Mantenere il silicio ad alta temperatura può: 
	- Causare il movimento dei droganti fuori dal substrato, risultando in
		- Una perdita di controllo sul profilo di drogaggio. *Difusione indesiderata*
			- Variazioni indesiderate nella concentrazione dei droganti.
		- Modificando la concentrazione dei droganti nella camera di reazione. *Autodrogaggio*
			- I sottoprodotti gassosi della dissociazione dei precursori devono essere rimossi per evitare la loro rideposizione
#### Soluzioni
- Si utilizza il silano per la deposizione a basse temperatura, minimizzando i problemi
	- L'arsenico richiede condizioni specifiche di temperatura. L'uso di basse temperature non è adeguato, poiché potrebbe non incorporare adeguatamente il drogante nel substrato.
- Aumentare la pressione sul substrato può aiutare a prevenire che i droganti escano dal substrato, migliorando il controllo sulla concentrazione dei droganti.
- Selezionare droganti con bassa pressione di vapore o basso coefficiente di diffusione può minimizzare la diffusione indesiderata. Ad esempio, evitare l'uso del fosforo che ha alta mobilità alle alte temperature.o
- Diminuire la pressione nel reattore può aiutare a eliminare i droganti non voluti attraverso il flusso di gas, riducendo il rischio di autodrogaggio.
- Crescere uno strato iniziale di substrato non drogato prima di introdurre il drogante può aiutare a stabilizzare il processo e evitare la diffusione di droganti non voluti.

#### Mantenimiento de la Calidad del Sustrato

- **Limpieza Química:**
    - Es crucial realizar una limpieza química del sustrato para eliminar contaminantes superficiales antes del proceso epitaxial.
- **Limpieza In Situ:**
    - Se utiliza una limpieza in situ con una mezcla de HCl (1-5%) y H₂ a temperaturas superiores a 1100°C para eliminar la capa de óxido y otros contaminantes, asegurando una superficie limpia para el crecimiento epitaxial.
### Defectos en el Proceso de Epitaxia
#### Origen de los Defectos
1. **Defectos en el Sustrato:**
    - **Preparación del Sustrato:**
        - La calidad del film epitaxial está directamente limitada por la calidad del sustrato original. Los defectos presentes en el sustrato se propagan al film epitaxial.
        - Para obtener un film de alta calidad, es fundamental empezar con un sustrato libre de defectos y bien preparado.
    - **Imperfecciones del Sustrato:**
        - Las imperfecciones en el sustrato, como dislocaciones, vacancias y defectos intersticiales, pueden actuar como sitios de nucleación para defectos adicionales en el film epitaxial.


#### Defectos en los Films Epitaxiales

1. **Dislocaciones:**
- Si formano quando abbiamo stress supra la fetta
    - **Origen de las Dislocaciones:**
        - Pueden originarse a partir de las dislocaciones existentes en el sustrato.
        - Causadas por alto dopaje, conocido como dislocaciones tipo "misfit".
        - Generadas por gradientes térmicos en el sustrato, debido al contacto térmico desigual con el susceptor.
	        - Questo puo generare un effeto di tassa(prossima imagine)
![[Pasted image 20240409143136.png]]
2. **Defectos de Empaquetamiento (Stacking Faults - SF):**
    - **Origen de los Defectos de Empaquetamiento:**
        - Estos defectos se originan debido a alguna imperfección en la superficie del silicio, que perturba el crecimiento local y genera SF.
        - Ejemplos de imperfecciones incluyen partículas de SiO₂, Si₃N₄, SiC, o la presencia de vapor de CO₂ en el reactor que forma SiO.

#### Soluciones a los Defectos

1. **Dislocaciones:**
    - **Uso del "Gettering":**
        - Técnica que implica la introducción de un material que captura las impurezas y defectos, alejándolos de las áreas críticas del sustrato.
        - - Per evitare il stress termico dobbiamos riscaldare di emtrambi lado, e anche si modifica per evitare contatto sotto
			- Questo é meno efficiente
![[Pasted image 20240409143422.png]]
    - **Uso de Substratos con Capas Intermedias:**
        - Utilizar substratos con capas de materiales que tienen parámetros de red diferentes para aliviar el estrés y reducir la formación de dislocaciones tipo "misfit". Por ejemplo, utilizar aleaciones de Si-Ge que tienen un parámetro reticular diferente al del silicio, lo que ayuda a relajar el estrés mediante la formación controlada de dislocaciones.
2. **Defectos de Empaquetamiento:**
    - **Minimización de Contaminantes:**
        - Mantener una atmósfera de reactor limpia para minimizar la presencia de partículas y vapores que pueden causar defectos de empaquetamiento.
    - **Control de la Superficie:**
        - Asegurarse de que la superficie del sustrato esté libre de imperfecciones antes del inicio del proceso epitaxial.


-




### Influenza dei Parametri di Processo nella Epitassia

#### Dipendenza da Variabili di Processo

1. **Orientazione del Sottostrato:**
   - La orientazione del sottostrato influenza il modo in cui gli atomi si dispongono sulla superficie durante la crescita epitassiale. Differenti orientazioni possono favorire la formazione di dislocazioni o difetti superficiali.

2. **Velocità di Deposizione:**
   - La velocità di deposizione deve essere ottimizzata. Una velocità troppo alta può causare la formazione di difetti a causa dell'incapacità degli atomi di organizzarsi correttamente sulla superficie, mentre una velocità troppo bassa può essere inefficiente e costosa.

3. **Temperatura di Deposizione:**
   - La temperatura influenza la mobilità degli atomi sulla superficie. Una temperatura troppo bassa può ridurre la mobilità, portando a una crescita disordinata, mentre una temperatura troppo alta può causare la desorbimento dei precursori o la diffusione indesiderata dei dopanti.

4. **Sorgente di Si:**
   - La scelta del precursore di silicio (ad esempio, SiH₄ o SiCl₄) influisce sui meccanismi di crescita e sulla qualità del film. Differenti precursori possono indurre differenti tipi di difetti o reazioni secondarie.

5. **Pressione:**
   - La pressione nel reattore deve essere attentamente controllata. Una pressione troppo alta può aumentare le collisioni molecolari nel gas, mentre una pressione troppo bassa può ridurre la quantità di materiale disponibile per la deposizione.

#### Effetti di Spostamento, Distorsione e Scomparsa delle Strutture

1. **Condizioni di Deposizione e Effetti sui Pattern:**
   - **Spostamento delle Strutture:**
     - Il pattern shift (spostamento delle strutture) può essere influenzato dalle condizioni di temperatura e pressione. Ad esempio, a 1110°C e 100 Torr, i reattori radiali possono mostrare spostamenti maggiori rispetto ai reattori verticali.
   - **Distorsione delle Strutture:**
     - La distorsione del pattern è minore in presenza di agenti clorurati come Cl₂ o HCl rispetto all'uso di SiH₄.
   - **Scomparsa delle Strutture:**
     - Condizioni estreme di temperatura e pressione possono portare alla scomparsa delle strutture epitassiali desiderate.

#### Soluzioni per Minimizzare i Difetti

1. **Compromesso Empirico:**
   - Poiché le dipendenze influenzano i difetti in modo opposto, spesso è necessario trovare un compromesso empirico che ottimizzi tutti i parametri chiave per ridurre al minimo i difetti senza compromettere la velocità di deposizione e la qualità del film.

2. **Uso di Reattori Ottimizzati:**
   - **Reattori Verticali Riscaldati Induttivamente:**
     - Producono minori pattern shift rispetto ai reattori radiali nelle stesse condizioni di deposizione.
   - **Scelta del Precursore:**
     - L'uso di SiH₄ riduce il pattern shift. Tuttavia, la presenza di Cl₂ o HCl può ridurre ulteriormente la distorsione del pattern.


