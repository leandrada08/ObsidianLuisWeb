---
cards-deck: Profesional::Universidad::UNISA::Segundo Cuatrimestre::Nanoeletronica
---

## Introduzione
### Solidi
- I solidi sono
	- Amorfi
		- Ordinde solo a breve distanza(primi vicini), nessun ordine a lunga distanza
	- Policristallini
		- Regioni ordinate con diversa orientazione cristallografico
	- Cristallini
		- Struttura cristalllografica ordinata
- La strutura policristalina puoi creare difetto di borde di grano

**Observaciones:**
- In policristaliano abbiamo la presenzia del bordo di grano e di grano
- Si usa silano per silicia amorfo in PCVD

### Diffeti
Le diffeti sono imperfezioni dentro delle cristrallo. Vari tipi di difetti possono esistere in un cristallo o possono essere creati durante i passi di processo. I difetti condizionano il trasporto elettrico e peggiorano, generalmente, le prestazioni dei dispositivi.





## Difetti cristallografici nel silicio #tarjeta-anki 
Un difetto cristallografico è una qualunque interruzione nella natura ripetitiva della struttura cristallografica della cella unitaria cristallina.
1. Difetti di punto → Difetti cristallografici localizzati a livello atomico
2. Dislocazioni → Spostamento di celle unitarie
3. Agglomerati → Difetti nella struttura cristallina
### Classificazione dei difetti cristallografici secondo le dimensione
^1719957431336

| Classe     | Dimensioni | Tiplogia                                                                   |
| ---------- | ---------- | -------------------------------------------------------------------------- |
| Puntiformi | 0          | Interstiziale,Vacanza,Coppia frenkel                                       |
| Line       | 1          | Dislocazioni                                                               |
| Area       | 2          | Superfici, Cristalli geminati, difettid i impacchettamento, bordi di grano |
| Volume     | 3          | Precipitati, vuoti                                                         |


### Difetti puntiformi 0D #tarjeta-anki 
Difetti che interessano un volumetto di dimensioni paragonabili alla cella elementare.
Puo essere
- Impurezza in posizione sostituzionale
- Silicio interstiziale
- Vacanz o difetto schottky
- Diffetpo Frenkel
![[Pasted image 20240423112404.png]]
#### Diffeto Schottky o Vacanza
Assenza di un atomo al posto che gli competerebbe nella strutura cristalinna. Concentrazione in equilibrio di vacanze in un critallo monoatomico.
$$C_v^0=Ne^{\frac{S_v}{k}}e^{-\frac{E_v}{kT}}$$
- $S_v$ ed $E_v$: Entropia e Energia di formazione della vacanza($S_v=1-2k$ ed $E_v=3-4eV$), k é la constante di Boltzmann, T la temperatura assoluta ed N la concetrazione di atomi nel cristallo.
*Vacanza e temperatura* 
- Quando vediamo la concentrazione di vacncace, questa dipende della temperatura
- Quando noi fabricamos un dispositivo lo facciamo a una temperatrua de 1685K, qua, abbiamo una concentazione delle ordinde $10^{14}$, ma quando abbiamoa una temperatura de 300K abbiamo una concentrazcion di $5^{-12}$
- Ma, il sicilio, dopo di essere riscaldato, quando si rafredda, si congela la concentrazione di vacance, perche al essere un processo termodinamico, per ritornare alla prima situazione, deve essere un proceso lento, statico, come non si fa cosi, la entropia aumenta, per lo quale, la vacance sono maggiore per fare una entropia maggiore.
	- Tale concentrazione puó esse ridotta mediante una opportuna successione di ricoture(annealing) seguite da lenti raffredamenti in modo da riportare la concentrazione di vacanze vicino al velore di equilibrio, corrispondente alla temperatura ambiente.
- Le vacanze posso risultare neutre $V^0$ , con cariche positive $V^+$, negative $V^-$ o doppiamente negative $V^=$.
![[Pasted image 20240625192430.png]]
- La formazione di una vacanza richiede la rottura di quattro legami, ma, la formazione di un’altra vacanza adiacente alla prima richiede la rottura di fue soli legami covalente e quindi una ridotta energia di attivazione. Il difetto che ne consegue é chimato *di-vacanza*
	- Questo é anche possibile, in condizioni particolari, che si verifichi la rimozione di altri atomi adiacenti, dando cosi origine a un agglomerato o cluster di vacanze
Si puoi generaliza il numero di vacanze, con le formula $$C_{n_D}^N=\frac{N!}{[(N-n_D)!n_D!]}$$
- E anche si puó calculare le vacanze positive e negative: $$C_{V^+}=C_{V^0}\cdot e^{\frac{E_{V^+}-E_F}{kT}}$$
$$C_{V^-}=C_{V^0}\cdot e^{\frac{E_F-E_{V^-}}{kT}}$$
#### Interstiziali
Presenza di un atomo del cristallo in uno degli interstizi esistenti nella struttura cristallina perfetta. Nella cella elemtare del silicio é possibile individuare cinque posizione interstiziali, occupabili da atomo che si pensano qui migrati dalla superficie del cristallo. La concentrazione é:
$$C_i^0=N_ie^{\frac{S_i}{k}}e^{-\frac{E_i}{kT}}$$
- $Ni=(5/8)N$ : concentrazione di posizioni interstiziali nel cristalo
- La formula é la stessa, cambia il numero di siti che puo fare una interstiziali
- Questi dipende si il nostro semiconductore e instriseco o no, quindi anche dipende della temperatura
- L’entropia e l’energia di formazione di un interstiziale sono dello stesso ordine di grandezza dell’energia richiesta per la formazione della vacanza.
#### Frenkel(vacanza piú interstiziale)
Assenza di un atomo nella posizione che gli competerebbe nella struttura cristallina perfetta e suo inserimento nella posizinoe interstiziale piú vicina. La concentrazione di equilibrio vale:
$$C_F^0=\sqrt{NN_i}e^{-\frac{E_F}{kT}}$$
- Anche é attivato termodinamicamente
- Anche dipende de la radice de N e Ni
- $E_f=5-10eV$ l’energia di formazione del difetto Frenkel
#### Impurità Chimica
Atomo di elemento estraneo presente nella struttura cristallina. É Sostituzionale quando occupa un posto che competerebbe a un atomo del cristallo ospitante e Interstiziale quando si colloca in posizione interstiziale tra gli atomi del cristallo ospitante.
- **Impurità di tipo interstiziale**: Si collocano nei possibili attem di locazione.
- Donatori e accettori, sono impurezze chimiche sostituzionali intenzionalmente inserite nella matrice cristallina, o all'atto del suo accrescimento o durante la fabbricazione del componente. Esempi come Fe, Cu, Ni, dovuti a contaminazioni accidentali di varia origine.
	- **Esempio**: Au, utilizzato in passato per ridurre i tempi di vita dei portatori nel silicio, risulta al 10% interstiziale e al 90% come sostituzionale.
	- SiC, con contaminazioni di ossigeno e carbonio dovute al crogiolo di grafite e provenienti dal clorosilano che alimenta il forno di fusione del polisilicio.
- **Ossigeno**: È presente come interstiziale a concentrazioni elevate fino a $10^{18} \, \text{atomi/cm}^3$, che è il limite di solubilità alla temperatura di fusione.
	- Non risulta elettricamente attivo e quindi non si risente la sua presenza se non quando, a seguito di particolari trattamenti termici, forma microprecipitati tipo $SiO_2$ e compessi elettricamente attivi tipo $SiO_4$ che agiscono come donatori.
	- Quando è presente come sostituzionale a concentrazioni che possono arrivare a $10^{17} \, \text{atomi/cm}^3$, non risulta essere elettricamente attivo, ma agisce come catalizzatore nei riguardi della precipitazione dell'ossigeno.
- La presenza di impurità chimiche crea nel cristallo difetti puntiformi che introducono livelli energetici nel gap di energia del semiconduttore (vedi, con riferimento al silicio, fig. 1.23).
- La concentrazione di questi livelli è definita dalla concentrazione degli atomi dell'impurezza, mentre la loro posizione nel gap dipende dalla natura chimica dell'impurezza e del semiconduttore che la ospita.
	- Dalla tabella periodica (fosforo, arsenico, antimonio) introducono livelli permessi assai vicini alla banda di conduzione.
		-  Si troverà sotto i livelli energetici introdotti dalle impurezze in questione, cosìché sarà prossima a uno la probabilità che tali atomi siano ionizzati rendendo così disponibile un elettrone in banda di conduzione.
	- (boro, alluminio, gallio) introducono livelli energetici assai vicini alla banda di valenza.
		 -  Sarà pertanto elevata la probabilità di cattura di un elettrone da parte di questi atomi che, ionizzandosi, renderanno disponibile una lacuna in banda di valenza.
- L'introduzione di un livello energetico permesso in vicinanza della banda di conduzione o di valenza è condizione necessaria, ma non sufficiente, perché un elemento si comporti da efficace donatore o accettore: occorre anche, infatti, che le dimensioni e la configurazione dello strato elettronico più esterno siano tali da permettere all'atomo in questione di inserirsi stabilmente nella matrice cristallina nel semiconduttore e di contribuire ai legami covalenti che li agiscono tra gli atomi della matrice stessa.
- **Deformazione del reticolo cristallino**: Rileviamo inoltre che la presenza di impurità chimiche induce nel reticolo cristallino una deformazione elastica localizzata; nel caso, particolarmente importante, di impuritá sostituzionali, questa, dipende dal rapporto tra il raggio atomico dell’imputirá e quello dell’elemento che costituisce il cristallo
^1719957431371


### Difetto di linea 1D #tarjeta-anki 
I difetti di linea interessano regioni delimitate da una superficie cilindrica con una sezione paragonabile alle dimensioni della cella elementare e distribuite attorno a una linea che si allunga attraverso il cristallo per migliaia di distanze interatomiche. Si possono considerare come una traslazione di una parte del volume della struttura cristallina rispetto al rimanente: il difetto di linea rappresenta il contorno della regione traslata.
- É causato dal processo di estrazione del cristallo
	- Sollecitazione meccanica eccessiva
	- Riscaldamento o raffreddamento irregolare, diffusione drogante nel reticolo
- Le dislocazione devono essere minimizzati
	- Elettroni di dispersione aumentare la resistivitá
	- Legami penzolanti → intrappolano gli atomi di impuritá diventano immobilizzati
- Le impurità tendono a migrare verso le dislocazioni a causa della energia più bassa in quelle regioni.
	- Sul retro i defetti sono creati intenzionalmente per intrappolare impuritá mobili indesiderate all´interno del wafer 
	- Questo fenomeno puó influenzare le proprietá elettriche del materiale, specialmente se le impuritá sono di natura metallica e possono cortocircuitare le giunzioni o influenzare la conducibilitá elettrica del materiale.
- Le dislocazioni possono influenzare la mobilitá dei portatori di carica, come gli elettroni o i buchi, nel materiale.
#### Dislocazione a Spigolo (Dislocazione di Borde)
![[Pasted image 20240625214001.png]]
La regione di cristallo sopra il piano di scorrimento ABCD ha subito una traslazione rigida unitaria. Il controno della regione traslata, linea retta AD, é per definizione il difetto di linea. Gli atomi lungo la linea di dislocazione non sono distribuiti regolarmente.
- **Formazione**: Si verifica quando c'è una dislocazione in cui una mezza strato di atomi si inserisce nel cristallo. Cioé quando ci sono disallineamenti nella disposizione degli atomi lungo una direzione nel cristallo, creando una discontinuità a forma di spigolo.
- **Impatto**: Provoca una traslazione degli atomi in una direzione perpendicolare alla dislocazione.
#### Dislocazione a Vite (Dislocazione di Tornillo)
![[Pasted image 20240625214007.png]]
La regione di cristallo adiacente sopra il piano ABCD ha subito una traslazione rigida unitaria parallela alla linea di dislocazione.
- **Formazione**: Si presenta come una spirale nella struttura cristallina dove gli strati del cristallo sono spostati in forma di spirale attorno a una linea. Si formano quando gli strati di atomi nel cristallo sono sfalsati lungo una direzione parallela alla linea di dislocazione, presentandosi come una spirale nella struttura cristallina.
- **Impatto**: Provoca una traslazione degli atomi parallela alla dislocazione, creando una struttura elicoidale nel cristallo.
- Le dislocazione a spigolo e a vite rappresentano casi limite: si trtta di diffetti di linea rigorosamente rettilineo. In generale la dislozacione non é mai a spigolo e a vite, ma segue, una linea cruva la cui tangente forma un angolo continuamente variabile ripetto alla tralazione unitaria che l’ha generata, in certi trattipuó esse puramente o prevalentemente a spigolo o a vite. 
- La dislocazione non puó terminare all interno del cristallo, deve chiudersi su se stessa o terminare alla superficie o in corrispondenza di altre dislocazioni.
#### Formazione e muovimento di una dislocazione
Associate alle dislocazioni, hanno deformazioni elastiche nella struttura reticolare. La dislocazione é caratterizzata da una energia di tipo elastico che corrisponde all’energia ceduta al cristallo all’atto della formazione delle dislocazione stessa
- L'energia necessaria per formare una dislocazione nel cristallo è alta (15-20 eV per il silicio). Le dislocazioni si possono muovere con una energia bassa (0.1-0.5 eV per distanza interatomica) → dificile a formarzi ma facile da movere.
	- É possibile, con opportuni accorgimenti, evitare la formazione di siffatte dislocazioni o nel caso siano presente, muoverlo verso la superficie del cristallo. 
##### Formazione di dislocationes
![[Pasted image 20240423184416.png]]
- Si puo formare per collapse e per agglomeration 
	- Il collapse é una dislocazione di tipo instriseca
	- La aglomerazione é una dislocazione dil tipo extrinzeca
- Si puo formare aggiungiendo vacanze
	- Claster di vacanza
- Le dislocazioni si formano principalmente durante il processo di crescita del cristallo, quando ci sono imperfezioni o disallineamenti nella disposizione degli atom
##### Meccanismi di Propagazione delle Dislocazioni 
La propagazione delle dislocazioni attraverso il reticolo cristallino avviene principalmente attraverso due meccanismi: il movimento per clip e il movimento per glide.
1. **Movimento per clip (o climb):**
![[Pasted image 20240423185844.png]]
   - In questo meccanismo, le dislocazioni si spostano lungo la direzione verticale, muovendosi attraverso i piani cristallini del reticolo.
   - Durante il movimento per clip, gli atomi lungo la linea di dislocazione possono diffondere attraverso i piani cristallini circostanti.
   - Questo processo richiede energia sotto forma di calore per consentire agli atomi di diffondersi e consentire alla dislocazione di muoversi attraverso il cristallo.
2. **Movimento per glide:**
![[Pasted image 20240626100010.png]]
   - Nel movimento per glide, le dislocazioni si spostano lateralmente lungo il piano del reticolo cristallino.
   - Durante il movimento per glide, gli atomi lungo la dislocazione scivolano lungo il piano cristallino, spingendo o tirando gli atomi circostanti.
   - Questo processo non richiede energia termica aggiuntiva come nel movimento per clip, ma richiede una forza esterna sufficiente per superare la resistenza dei legami atomici nella direzione di movimento della dislocazione.
^1719957431380



### Difetti di Superficie 2D #tarjeta-anki 
I difetti di superficie interessano una regione del cristallo di spessore paragonabile alla distanza interatomica e di estensione pari a centinaia o migliaia di distanze interatomiche nelle altre due dimensioni. La zona difettiva è quindi tipicamente bidimensionale. Nel caso dei cristalli semiconduttori, assumono particolare importanza i difetti di superficie.
- La superficie può essere vista come una dislocazione a causa della mancanza di atomi, rappresentando una regione di contorno diversa da quelle nel volume del materiale. C'è una ricostruzione della superficie in modo tale che i legami insaturi ("dangling bonds"), estremamente reattivi, si uniscono l’uno con l'altro.
- Lo stesso fenomeno può accadere nelle interfacce di due materiali diversi. È la diversa configurazione che fa sì che l'interfaccia appaia come un difetto.
![[Pasted image 20240423191341.png]]
#### Difetti di impacchettamento (Stacking Faults)
![[Pasted image 20240626103850.png]]
Possono essere di tipo estrinseco o intrinseco.
  - **Estrinseco**: Quando corrispondono a una porzione limitata di un piano cristallografico inserita nella matrice. Questi difetti si verificano quando gli atomi estranei o stranieri si trovano sulla superficie del materiale cristallino. Esempi comuni includono atomi di impurità incorporati durante il processo di fabbricazione o attraverso l'esposizione ambientale.
  - **Intrinseco**: Quando è assente una porzione di piano cristallografico. Questi difetti si verificano quando gli atomi della superficie del materiale non sono completamente impilati o allineati secondo la struttura cristallina ideale. Esempi comuni includono lacune di atomi o disordini nella disposizione degli atomi superficiali.
#### Superficie di Separazione fra Cristalli Geminati (Twin Boundary)
![[Pasted image 20240423194150.png]]
Si verificano durante il tracciamento del monostrato, quando parte della superficie di cristallizzazione si discosta dalla planaritá. Possono essere associati a piani cristallografici con orientazione diversa da quella voluta, formando quindi cristalli geminati all’interno o ai bordi della barra.
- Nei cristalli geminati, i difetti di superficie si manifestano come discontinuità o dislocazioni lungo il piano di geminazione, dove i due cristalli si uniscono
- La superficie difettiva è il piano rispetto al quale gli atomi dei due cristalli adiacenti occupano posizioni speculari, causando discontinuità e dislocazioni lungo il piano di geminazione. 
- Questi difetti influenzano la propagazione di altri difetti e la diffusione di atomi lungo la giunzione di geminazione.
#### Bordi di Grano (Grain Boundary)
Si formano quando i cristalli si incontrano in modo non perfettamente allineato, creando una discontinuità nell'orientazione cristallografica lungo il confine tra i due cristalli. Questi difetti sono spesso il risultato di processi di crescita cristallina, deformazione plastica o recristallizzazione.
- I bordi di grano influenzano le proprietà meccaniche, elettriche e termiche del materiale e possono servire da siti di nucleazione per la formazione di altre imperfezioni o difetti nel cristallo. 
- Possono essere classificati in diverse categorie in base alla loro struttura e all'angolo di orientazione tra i cristalli adiacenti, come bordi di grano a basso angolo e bordi di grano ad alto angolo.
^1719957431387








 
### Difetti di Volume 3D #tarjeta-anki 
I difetti di volume, o difetti tridimensionali, sono imperfezioni che interessano regioni interne alla matrice cristallina, estese per decine o centinaia di distanze interatomiche nelle tre direzioni. Questi difetti includono precipitati, vuoti e altre fasi chimicamente distinte che possono influenzare significativamente le proprietà e il comportamento dei materiali.
#### Precipitati e Vuoti
- **Precipitati**: Sono fasi secondarie che si formano all'interno di un materiale quando una soluzione solida diventa sovrasatura e gli atomi o le molecole si aggregano per formare nuclei cristallini.
	- La sovrasaturazione chimica può essere causata da varie condizioni, come cambiamenti di temperatura o di pressione, o dall'introduzione di impurità nel materiale. La solubilità degli elementi donatori e accettori e delle impurità comuni nel silicio diminuisce con la temperatura. Un rapido raffreddamento può portare a una sovrasaturazione nel cristallo, favorendo la formazione di microprecipitati.
	- Affinché si verifichi la formazione di precipitati, è necessario che siano soddisfatte due condizioni principali:
	    - **Forza motrice termodinamica**: Una sovrasaturazione chimica che spinge gli atomi o le molecole a formare nuclei di precipitazione.
	    - **Mobilità atomica sufficiente**: Permette la nucleazione e la crescita dei precipitati.
  - I precipitati possono causare una variazione del volume del materiale, portando alla formazione di dislocazioni loop che influenzano le proprietà meccaniche ed elettriche del materiale. Un esempio di microprecipitato di fosforo nel silicio può essere osservato, evidenziando come il raffreddamento rapido favorisca la formazione di tali difetti.
- **Vuoti**: Sono regioni all'interno del materiale dove mancano atomi o molecole. Possono essere creati da diversi processi, come la diffusione di atomi verso la superficie del materiale o la formazione di gas durante la solidificazione.
	- I vuoti possono influenzare la resistenza meccanica, la conducibilità elettrica e la capacità termica del materiale. Inoltre, possono agire come siti di diffusione per gli atomi o le molecole, facilitando la migrazione di impurità o la crescita di precipitati. La presenza di vuoti può influenzare anche la densità del materiale e la sua capacità di resistere a sforzi meccanici
#### Conziderazioni
- I difetti cristallografici influenzano significativamente le proprietà chimico-fisiche ed elettriche, risultando cruciali nella tecnologia dei semiconduttori. Le impurità chimiche elettricamente attive, come donatori e accettori, e le impurità metalliche influenzano la durata di vita e le prestazioni del semiconduttore.
- **Monocristalli di Silicio**: È possibile produrre monocristalli di silicio privi di difetti di linea e di superficie, ma i difetti possono essere introdotti durante i processi termici richiesti per la fabbricazione dei circuiti integrati.
- **Difetti Elettricamente Neutri**: Questi difetti, se non attivati da contaminazioni metalliche, non influenzano le prestazioni del materiale. Tuttavia, le contaminazioni metalliche dotate di alta diffusività tendono a muoversi attraverso il cristallo e precipitare in corrispondenza di dislocazioni e stacking faults, fungendo da centri di nucleazione per precipitati metallici.
- **Impurità Metalliche**: Le dislocazioni e stacking faults decorati costituiscono percorsi preferenziali per la corrente di perdita, inducendo "microplasmi" e scariche localizzate premature nelle giunzioni sotto polarizzazione inversa, compromettendo le prestazioni dei transistori bipolari.
- **Importanza delle Impurità**: Le impurità chimiche elettricamente attive, come donatori e accettori, e le impurità metalliche influenzano la durata di vita e le prestazioni del semiconduttore.
- **Vacanze e Interstiziali**: Giocano un ruolo fondamentale nei processi di diffusione e nella formazione dei difetti di volume, influenzando le proprietà del semiconduttore e la sua durata di vita.
##### Raggio Critico per i Precipitati
Il raggio critico ($r*$) è la dimensione minima che un nucleo deve raggiungere per crescere e formare un precipitato stabile in un materiale. Si definisce come:
$$ r* = \frac{2 \gamma}{\Delta g} $$
dove $\gamma$ è l'energia superficiale e $\Delta g$ è la differenza di energia libera tra le fasi solida e liquida. I nuclei con raggi minori di $r*$ tendono a dissolversi perché aumentano l'energia del sistema, mentre i nuclei con raggi maggiori di $r*$ possono crescere, diminuendo l'energia del sistema e formando precipitazioni stabili.
^1719957431396


## Gettering #tarjeta-anki 
![[Pasted image 20240626122338.png]]
Il gettering è un processo progettato per intrappolare le impurità lontano dai dispositivi attivi nel materiale semiconduttore, migliorando le prestazioni dei dispositivi. Questo viene realizzato introducendo deliberatamente difetti cristallini per creare siti di cattura per le impurità. Il gettering può essere intrinseco o estrinseco:
### Gettering Intrinseco
- Utilizza impurità incorporate durante il processo di crescita del silicio per creare precipitati di ossido di silicio ($SiO_2$) che fungono da siti di cattura per le impurità. Questo processo sfrutta la supersaturazione di ossigeno nel silicio durante il raffreddamento dalla temperatura di crescita.
- Favorisce la diffusione delle impurità metalliche dalla superficie verso il retro della fetta, formando microprecipitati di ossido di silicio che agiscono come centri di nucleazione. Questi centri aiutano ad allontanare le impurità dalla regione attiva del dispositivo.
##### Procedura
  1. **Trattamento Termico per la Zona Denudata**: Eliminazione dell'ossigeno dalla superficie della wafer per evitare reazioni indesiderate durante i passaggi successivi. È importante eseguire questo passaggio a una pressione adeguata per evitare la presenza di ossigeno residuo, che potrebbe reagire con altri composti chimici durante i passaggi successivi del processo.
  2. **Nucleazione dei Cluster SiOx**: Formazione controllata di cluster contenenti un elevato numero di atomi a temperature ottimali. Questo processo avviene a temperature più basse per evitare la formazione di cluster indesiderati. È importante mantenere una temperatura ottimale per garantire una nucleazione controllata e uniforme dei cluster.
  3. **Crescita dei Precipitati e Gettering**: Crescita dei precipitati di SiO2 che catturano le impurità presenti nel materiale semiconduttore, mantenendo basso il livello di impurità e migliorando le prestazioni dei dispositivi.
### Gettering Estrinseco
- Coinvolge l'introduzione di difetti intenzionali sul retro della wafer per intrappolare impurità metalliche e ioni alcalini. Ad esempio, il polisilicio applicato sul retro della wafer intrappola impurità metalliche alle dislocazioni.
- **Funzionamento**: Promuove la diffusione delle impurità metalliche e la loro precipitazione in corrispondenza di centri di nucleazione introdotti nel retro delle fette mediante abrasione meccanica.
- **Caratteristiche**: 
  - Il gettering estrinseco richiede un maggiore movimento delle impurità per raggiungere i siti di cattura.
  - È chiamato estrinseco perché viene applicato fuori dalla fetta.
##### Procedura
Los defectos se introducen en la parte trasera de la oblea. Se pueden utilizar métodos como la abrasión mecánica o la aplicación de una capa de polisilicio en la parte trasera de la oblea.
Las impurezas metálicas se difunden desde la región activa hacia la parte trasera de la oblea, donde los defectos intencionales las atrapan. Las impurezas quedan atrapadas en los defectos creados en la parte trasera de la oblea, alejándolas de la región activa del dispositivo.
### Observazione
- Le impurità metalliche, essendo dotate di alta diffusività, tendono a muoversi attraverso il cristallo e a precipitare in corrispondenza di dislocazioni e stacking faults. Questi difetti decorati costituiscono percorsi preferenziali per la corrente di perdita, inducendo "microplasmi" e scariche localizzate premature nelle giunzioni sotto polarizzazione inversa, compromettendo le prestazioni dei transistori bipolari.
-  Mentre il gettering intrinseco si concentra sulla creazione di precipitati di SiO2 durante la crescita del silicio, il gettering estrinseco introduce difetti intenzionali nella parte posteriore della wafer per intrappolare impurità metalliche.
- **Ossigeno**: È importante mantenere un livello controllato di ossigeno nel silicio. L'ossigeno può formare precipitati di SiO2 che fungono da centri di nucleazione per le impurità.
  - Livelli tipici: 10-20 ppm (parti per milione), equivalenti a $10^{17}$ atomi di ossigeno.
- **Carbonio**: La presenza di carbonio nel silicio CZ (Czochralski) è attentamente monitorata. Le tecniche di gettering intrinseco sono utilizzate per rimuovere le impurità metalliche e migliorare le prestazioni dei circuiti integrati, delle memorie e dei microprocessori.
#### Zona Denudata (Denuded Zone)
- **Descrizione**: Una regione superficiale della fetta con una bassa concentrazione di ossigeno per prevenire la formazione di precipitati nella regione attiva.
- **Formazione**: Si crea mediante trattamenti termici controllati che eliminano l'ossigeno dalla superficie della wafer. Questa zona è cruciale per evitare che le impurità influenzino le prestazioni del circuito integrato.
- **Importanza**: Particolarmente rilevante per le memorie RAM dinamiche (DRAM) dove l'alto tempo di vita dei cristalli semiconduttori è fondamentale per la frequenza dei "cicli di rinfresco".
#### Formazione della nucleazione
- Quando si forma una sfera, la variacione é data da 2 contributi
	- Uno con relazione cubica e altra con relazione cuadrata
	- Che un valore de radio critico, dopo del quale, la sfera rimane formata e non si disolve piú
		- Il radio critico cresce con la temperatura
^1719957431404





# Observaciones
- I defetti sono proporzionali a il costo di farlo
- Anche depende della entropia e della historia
- Quando parliamo di istoria, parliamo della temeperatura o stress a il quale si ha sometido il proceso 
- Il PSG si mete sopra la superficie di silicio



# LCD
- Funzionamiento di LCD
	- Problema con per la velocitá di comunmutazion quando funzionada con filtro
	- Adesso si depositá silicia amorfo supra il vetro
- Per potere riscaldare il SI sensa riscaldare il vetro/sustrato si riscalda con un laser de UV, perche il silicio ha un coefficiente di assorbimento tropo elevato in UV
	- Cosi si funde solo il primo ubstratto di silicio, il quale si diventa liquida
	- Con il calore di questo primo sustrato, riscalda la altra parte dil cristalo e anche si funde, ferma quando arriva al vetr
	- Con questa tecnica si riesca a trovare movilita di **….** 
	- Il 70% dell´area di un pixel e vuoto
	- Questa é altra tipo di epitassia(epitassia via laser)
		- In questo processo il hidrogeno é un problema
		- Fa che explote
		- Quindi prima di cristalizare, devo enviare a via a hidrogeno
			- Per enviare a via a hidrogeno si devi riscaldare
			- Questo si fa un tratamento di 200 o 300 grados durante 24 ora
			- Dopo si cristaliza
			- É metto di nuovo hidrogeno, per saturare il bordo di grano pero fare meglio ligamo


TFT (Thin Film Transistor) y SLC (Super Twisted Nematic Liquid Crystal) son tecnologías utilizadas en pantallas de cristal líquido (LCD). Aquí hay una breve descripción del funcionamiento de cada una:

1. **TFT (Thin Film Transistor)**:
   - En las pantallas TFT, cada píxel de la pantalla está asociado a un transistor de película delgada. Este transistor actúa como un interruptor controlado eléctricamente que permite que la luz pase a través del píxel.
   - Cuando se aplica un voltaje al transistor de película delgada, este se activa, permitiendo que la luz pase a través del píxel correspondiente.
   - La activación individual de los transistores TFT en cada píxel permite un control preciso de la intensidad de la luz y, por lo tanto, la generación de imágenes de alta calidad en la pantalla.

2. **SLC (Super Twisted Nematic Liquid Crystal)**:
   - Las pantallas SLC son un tipo de LCD que utiliza cristales líquidos superretorcidos para controlar la orientación de la luz polarizada.
   - En una pantalla SLC, los cristales líquidos están dispuestos en una configuración superretorcida, lo que significa que están torcidos más de lo habitual.
   - Al aplicar un voltaje a través de los cristales líquidos, su orientación cambia, lo que modifica la cantidad de luz que puede pasar a través de ellos.
   - Las pantallas SLC se utilizan en aplicaciones donde se requiere un tiempo de respuesta rápido y un bajo consumo de energía, como en monitores de computadora y paneles de instrumentos.

En resumen, las pantallas TFT utilizan transistores de película delgada para controlar la luz que pasa a través de cada píxel, mientras que las pantallas SLC utilizan cristales líquidos superretorcidos para lograr un control similar. Ambas tecnologías son comunes en pantallas LCD y ofrecen diferentes ventajas en términos de calidad de imagen, tiempo de respuesta y consumo de energía.

