---
cards-deck: Profesional::Universidad::UNISA::Segundo Cuatrimestre::Nanoeletronica
---

## Introduzione
### Applicazioni dell’ossido di silicio in VLSI
1. Maschera per l’impiantazione é diffusione selettiva di drogante
2. Passivazione della superficie di silicio
3. Isolante tra un dispositivo e l’altro
4. Come dielettrico di porta in struttre mos c
5. Come ossido di tunneling in memorie non volatile
![[Pasted image 20240415104804.png]]
Le 4 aplicazione principali sono: Maschera per la diffusione selettiva dei droganti, strato protettivo della superficie, isolante tra diversi strati di metallizzazione e fra un dispositivo e l’altro, come dielettrico di gate.


### Tipi di ossido #tarjeta-anki
#### Ossido nativo
Questo ossido è in genere eliminato in quantocontiene contaminanti. In  applicazioni è utilizzato in dispositivi di memoria o per la passivazione di film. Si forma di manera spontanea quando il sicilio si expone al aire
![[Pasted image 20240415104941.png]]
- Velocitá di crecita 15A per ora a temperatura ambiente
- Satura per spessori di circa 40A
#### Ossido di campo
E’ utilizzato come barriera di isolamento tra un transistore e l’altro.
![[Pasted image 20240415105031.png]]
- Valori tipici degli spessori variano da 2500A a 15000A
- Il metodo di ossidazione utilizzato é quello in ambiente umido
#### Ossido di gate
Costituisce il dielettrico del condensatore della struttura MOS tra gate e
![[Pasted image 20240415105234.png]]
- Valori tipici degli spessori degli ossidi di gate variano da 30 Å a 500 Å.
- Il metodo di ossidazione utilizzato è quello a secco.
#### Ossido di barrera
Protegge i dispositivi attivi ed il silicio dai processi successivi
![[Pasted image 20240415105310.png]]
- Ossido cresciuto termicamente di spessore alcune centinaia di Angstrom
#### Ossido barrierra per i droganti
Materiale di maschera durante impiantazione ionica dei droganti. L’ossido distanziatore è utilizzato durante l’impiantazione di droganti nelle regioni di source e drain
![[Pasted image 20240415105430.png]]
- Lo spessore dipende dall’energia degli atomi impiantati
#### Ossido cuscineto
Provides stress reduction for Si3N4
![[Pasted image 20240415105751.png]]
- Thermally grown and very thin
#### Osside schemata di impianto
A veces conocido como "óxido de sacrificio", óxido de pantalla, se utiliza para reducir la canalización del implante y el daño. Ayuda a la creación de uniones poco profundas
![[Pasted image 20240415110003.png]]
- Thermally grown
^1719767711940



## Fisica dell'ossido #tarjeta-anki
![[Pasted image 20240415110110.png]]
- Il ossdio che stiamo considerando é un ossido amorfo(figura 1b), costituito da un insieme tridimensionale e casuale di tetraedri del tipo rappresentato nella figura 2a. Posizione centrale occupata da ioni silicio, mentre ai vertici sono presenti gli atomi di ossigeno sotto forma di ioni. I tetraedri sono collegati tra loro solamente ai vertici tramite ioni ossigeno detti ioni leganti, appartenenti ai due tetraedi direttamente contigui(figura2b)
	- Fase stabile cristalina → tutti gli ioni ossigeno leganti
	- Fase amorfa → esistono ioni non leganti associati a un solo aotmo di silicio
	- Le propietá chimico-fisiche dell’ossido termico sono funzione della percentuale di ioni non leganti ripetto al totale di quelli leganti
- Struttura amorfa é piú aperta rispetto a quella cristallina
	- La densitá dell’ossido termico aumenta quando la tempertaru di ossidazione si abassa al di sotto di un valore critico, compreso tra 950 e 1000 grados celsius
	- Data la sua struttura relativamente aperta, l’ossido é particolarmente sensibile alla presenza di contaminazione e impurezze, che possono facilmente difondere al suo interno. 
		- Particolare importanza il sodioe il vapore d’acqua. Entrambi tendono a indebolire la struttura dell’ossido, diminuendo il numero di ioni leganti
^1719767711945

![[Pasted image 20240415110153.png]]



## Tecnologie di crecita dell'ossido di silicio #tarjeta-anki
Per formare film di ossido: Accrescimentoper via termica o per via anodica, deposizione per mezzo de una reazione chimica in fase vapore o mediante sputtering. Quando sono determinanti le caratteristiche elettriche dell’ossido e dell’interfaccia ossido/silicio, la tecnica utilizzata é l’oddisazione termica.
- *Ossidazione termica:* Gli atomi di silicio in superficie si legano con ossigeno
	- Ossido stechiometrico (SiO2)
	- Buona qualità dell’interfaccia Si/SiO2
	- Proprietà elettriche stabili e controllabili
- *Deposizione:* Sia il silico che l'ossigeno sono trasportati sulla superficie del wafer dove reagiscono tra loro
	- Abbiamo deposizione chimica da fase vapore(CVD)
- Anodizzazioneo o ossidazione in plasma
^1719767711950


## Ossidazione termica #tarjeta-anki
A contatto con l’aria, il silicio tende a ossidarsi anche a temperatura ambiente, peró lo spessore di ossido che si accresce é limitato a qualche decina di angstrom. Per aumentare lo spessore, ocorre attivare termicamente la reazione chimica. 
In un tubo di quarzo a elevata temperatura a si puo generar una ossidacione a secco o umida , la prima con ossigeneo molecolare e la seconda con vapore di acquea.
- Ossidazione "a secco"(dry): ossigeno molecolare
$$Si(s)+O_2(g) ->SiO_2(s)$$
- Ossidazione "umida"(wet): con vapore acque
$$Si(s)+2H_2O(g) -> SiO_2(s)+ 2H_2(g)$$
	- SI preferisce usare sistemi pirogenici in cui si fa avvenire direttamente la reazione tra H2 e O2 in modo da ottenere acqua piú pura in condizione pi controllabili
- Le reazioni chimiche avvengono all’interfaccia ossido/silicio e non alla superficie ossido/gas
	- La specie ossidante, deve diffondere attraverso l’ossido gia formato fino all’interfaccia
### Meccanismo di ossidazione
![[Pasted image 20240415111610.png]]
- Cuando facciamo il substrato si fa in piú perche sopo nella ossidazione si mangia parte dil substrato
	- Dil 100% sono 56% volumen nuovo e 44% volumen si silicio consumato
- Anche cresce per lado, quindi cresce come un cono, questo genera stress
	- Questo puo essere buono o malo, 
- Anche la variazione di temperatura genera stress, che genera stress
^1719767711956


- Nella reazione una mole di SI viene convertira in una mole si SiO2
- Quando cresce, non solo cresce per supra, anche cresce in diagonales, questo produce un stress di compressione
### Seco vs umito
La cinetica di ossidazione é di solito caratterizzata misurando lo spessore di ossido accresciuto in funzinoe del tempo di ossidazione per una fissata temperatura
- Humita piú veloce di quella secca, soprattuto per temperatura <1000 grados
- Il silicio <111> si ossida piú velocemente di quello con orientazione <100>
#### Ossidazione a secco
*Svantaggi*
- Ossido crece lentamente
*Vantaggi*
- Strati di ossido molto uniformi
- Si prenseta piú denso e con un campo di rottura piú elevato
- Relativamente pochi 
![[Pasted image 20240415111853.png]]
- Quando guardiamo la velocida di ossidazione possiamo vedere che dipende della temperatura 
	- Anche della direzzione cristalografica
	- Succede lo stesso in ossidazione in umido


#### Ossidazione in umido
- Vapore di acquo ultra puro
- *Svantaggio*
	- Gli atomi di idrogeno liberati dalla decomposizione delle molecole di acqua producono delle imperfezoini che possono degradare la qualitá dell’ossido
- *Vatnaggi*
	- Velocita di crescita elevata
	- Utile per la crsci di strati di ossido spessi
![[Pasted image 20240415111903.png]]



### Cinetica dell’ossidazione termica #tarjeta-anki
#### Modello di Deal-Grove
Aggiunggiamo una fase al modello di grove.
Dobbiamo considerare tre fasi:
1. Trasferimento della specie ossidante dalle fase gassosa alla superficie dell’ossido
2. Difussione dalla specie osidante attraverso l’ossido fino all’interfaccia con il silicio
3. Reazione della specie ossidante con il silicio sottostante
- Quella piú lenta influenzerá in modo determinante la velocitá di formazione dell’ossido termico, e quindi controllera la cinetica dell’ossidazione
#### Trasferimente della specie ossidante dalla fase gassosa alla superficie dell’ossido
Il flusso qua(F1) é il flusso della specie gassosa alla superficie, é iquale al del modello di grove
![[Pasted image 20240624205229.png]]
- $\delta:$ Spessore di strato gassoso immobile all’interfaccia
- $D_g$: Coefficiente di diffusion della specie ossidante attraverso lo strato gassoso immobile
- $C_g,C_s$ : concentraciones
- Si consideriamo gase é perfetto e la legge di Henry possiamo dire che in condizione stazionarie:$$C^*=Hp_g=HkTC_g$$ $$C_0=Hp_s=HkTC_s$$
Dove $C_0$ é la concentrazione delle specie ossidanti all’interfaccia gas-ossido nell´osiido e $C^*$ concentrazione delle specie ossidanti all’interfaccia ossido-silicio se l´ossido é in equilibrio con l´atmosfera del reattore.
Utilizzando le due equazione é possibile riscrivere la equacione di F1:
^1719767711961

$$F_1=h(C*-C_0)$$
- Dove h é il coefficiente di trasporto della specie ossidante in fase gassosa
$$h=\frac{D_g}{\delta H k T}=\frac{h_g}{HkT}$$
#### Difussione delle specie ossidante attraverso l´ossido fino all´interfaccia con il silicio
Dalla prima legge di Fick possiamo sapere che: $F2=-D\frac{dC}{dx}$
- D = coefficiente di diffusione della specie ossidante attraverso l’ossido, supposto indipendente dallo spessore dell’ossido e dC/dx é il gradiente di concentrazione della specie stessa.
	- Ipotesi: D non varii con lo spessore dell’ossido

$$F_2=D\frac{C_0-C_i}{X_0}$$

- $X_0$ = spessore dell’ossido, dipendente dal tempo
- Ci = concentrazione della specie ossidante all’interfaccia ossido - silicio
#### Reazione della specie ossidante con il silicio sottostante
Si suponiamo che le reazoini chimice sono del primo orden(lineali), il flusso consumado dalle reazione é
$$F_3=K_sC_i$$
- $K_S$ = costante di velocità della reazione
#### Svillupo
![[Pasted image 20240415114321.png]]
Si consideriamo un regimen staionario dove i 3 flussi sono in equilibrio
$$F_1=F_2=F_3=F$$

![[Pasted image 20240415114345.png]]
Lavorando matematicamente trovamo il valor di $C_0$ e $C_i$
- Si $D<<K_sX_0$ e $D<<hX_0$ il processo é controllato per il mecanismo di difussione, é un processo limitato
	- $C_i$ → 0 e $C_0$→$C^*$ 
	- Questo é la diffusione in base solita, la che limita il processo
- Si $D>>K_sX_0$ e $D>>hX_0$ il processo é controllato per il mecanismo di reazione
	- $C_i=C_0$ →$\frac{C^*}{1+\frac{k_s}{h}}$ 
- Nelle condizione normali di processo il valore di h é elevato $h$~$10^3K_s$ → $h>>K_s$ → Il trasporto della specie ossidante attraverso la fase gassosa non limita la velocitá di ossidazione 
	- $C_0=C^*$  →  $C_i=\frac{C^*}{1+\frac{K_s X_0}{D}}$
	- $F=F_3=K_sC_i$






#### Velocita di crescita ossidazione(lineare parabolica) #tarjeta-anki
Per calcolare la velocitá di crecita dell’ossido, occorre rapportare il flusso F al nuevo N di molecule ossidanti incoporate in un centrimetro cubo di ossido(Cioe il n di molecula ossidanti necesarie a formare 1 cm di ossido).
- $2,2x10^{22}$ $molecole/cm^3$ ossidazione dry
- $4,4x10^{22}$ $molecole/cm^3$ ossidazione wet
$$\frac{dX_0}{dt}=\frac{F}{N}$$
- Sontituendo F per F3, integrando la ecuassione e considerando che per t=0 esista sulla superficie del silicio uno spessore di ossido iniziale $X_i$ si puo arribare a la expresione
![[Pasted image 20240415115532.png]]
Si ottiene la legge lineare-parabolica di crescita dell’ossido in funzione del tempo t di ossidazione:
$$t=\frac{(X_0^2-X_i^2)}{k_p}+\frac{(X_0-X_i)}{k_l}$$
^1719767711965


$$k_p=\frac{2DC^*}{N}=\frac{2DHp_g}{N}$$
$$k_l=\frac{K_sC^*}{N}=\frac{K_sHp_g}{N}$$
- $k_l$ e il coefficeiente di crescita lineale → controllato dalla difusione
- $k_p$ é il coefficesiente di crecita parabolica → controllato dalla reazione chimica
- Entrambi proporzionali alla concentrazione di equilibiro $C^*$
Risolvendo la equzione iniciale di velocitá, si ricava che: 
![[Pasted image 20240415115625.png]]
- Questa equazione permette di calcolare lo spessore $X_0$ di ossido che si viene formando sulla superficie del silicio, noti che siano il tempo t di ossidazione e la condizione iniziale $X_i$
	- Si puoí vedere che si $\frac{4k_i^2(t+\tau)}{k_p}<<1$ , la equazione di $X_0$ si semplifica al termino di primo orde:$$X_0=k_l(t+\tau)$$
		- Il processo é controllato dalla reazione all’interfaccia e l’ossido crece con una legge lineare → $k_l$ viene chiamata velocita di ossidazione lineare
		- La condizione si dara quando:
			- t é molto piccola
			- $k_l^2$<<$k_p$ → temperatura bassa
	- Quando $\frac{4k_i^2(t+\tau)}{k_p}>>1$ si ha $$X_0^2=k_p(t+\tau)$$
		- La crescita dell’ossido segue una legge parabolica → $k_p$ viene detto velocitá di ossidazione parabolica.
		- L’ossidazione é controlata dunque dalla diffusione della specie ossidante attraverso l’ossido e la velocitá di ossidazione diminuisce
- L’ossidazione sara descrivibile con una legge lineare per tempi brevi e/o bassa temeperatura, mentre prevarra il regime parabolico al crescere del tempo e/o della temperatura di ossidazione. Occorre conoscere come variano  $k_p$ e $k_l$ con i parametri del processo, in particolare con la temperatura di ossidazione
#### Reggioni parabolica e lineale
Per temperatura di ossidazione maggiori di circa 900 grados C, $k_l$ e $k_g$ possono essere esprese da relazioni tipo Arrhenius.
- L’ossidazione steam aumenta sia $k_p$ che $k_l$, questo si devi que embtre costanti sono proporzionali alle concentrazione di equilibrio $C^*$, la solubilitá dell’$H_2O$ nella silice é circa tre ordini di gradezza maggiore della solubilitá dell ossigeno. La dipendenza dei coefficienti di ossidazione da $C^*$, e quindi dalla $p_g$, possibilitá di modificare la cinetica di ossidazione agendo sulla pressione parziale dell’ossidante.

![[Pasted image 20240625115805.png]]
##### Regione parabolica
Tipo arrhenius → $Kp=C2e^{\frac{-E_2}{kT}}$
- $k$ deriva dal coefficiente di difussione D della specie ossidante e $E_2$ corrisponde all’energia necesaria epr muovere a livello atomico le molecole della specie ossidante attraverso l’ossido
- Possiamo vedere che i grafici non sono paraleli, questi dice che la energia di attivazione sono diversa
	- Questo si debe perche, a diferenza di epitassia, qua le molecula di ossidazione sono diversa
	- Varia la ossidazione in 900 grado C.
	- Questa fase dipende della difussione in fase solida, per questo non dipende della orientazione cristalografica

![[Pasted image 20240415115922.png]]
- $k_p$ é legato al coefficiente di diffusione della specie ossidante
- $E_2$ é l´energia necessaria a muovere a livello atomico le molecole della specie ossidante nell´ossido
- $k_p$ dipende dalla specie ossidante
##### Regione lineare
Tipo arrhenius → $Kl=C1e^{\frac{-E_1}{kT}}$
La energia di attivazione $E_1$ corrisponde all’energia necessaria per rompere il legame covalente Si-Si e formare la molecola di SiO2
- Nel modello lineare si puó vedere che dipende de la direzzione cristalografica e anche che le recte sono paralela
	- Questo significa, che si sono parallela, ha la stessa energia di activazione, perche qua il processo é tra ossigeno e ossigeno, quindi, la energia con la quale si une, é la stessa
	- Qua si dipende della direzione cristalografica, gia che in queste caso, il processo é in fase gaseosa, dove si é importante la direzione delle atomi, e la direzione cristalografica varia la quantita di atomo supra la superficie
	- L’energia di attivazione $E_1$ é la stessa, diversa é la costante preesponenciale $C_1$
	- Ció che cambia non é il meccanismo limitante la reazione chimica interfacciale ma il numero dei legami ‘‘disponibili’’ per reazione
![[Pasted image 20240415115947.png]]
- $k_l$ e legato al coefficiente di reazione chimica $k_s$ processo limtante
- $E_1$ é crica uguale all´energia necessaria a rompere il legame $S_i-S_i$ e formare la molecola di $SiO_2$ 
- $k_l$ dipende dalla specie ossidante
- $k_l$ dipende dall´orientazione cristallografica: stessa energia di attivazione ma diverso fattore esponenziale.



### Osservazione del Modello Deal-Grove
Il modello di Deal-Grove offre un buon accordo con i risultati sperimentali per spessori superiori a 350 Å, tenendo conto della dipendenza dalla temperatura, dell'ambiente gassoso e dell'orientazione cristallina del substrato.
#### Regime Iniziale di Crescita

Il regime iniziale di crescita è caratterizzato da una velocità di ossidazione più alta rispetto a quanto previsto dal modello. Questo può essere spiegato attraverso vari modelli:

1. **Modelli basati sugli effetti di "carica spaziale"**: L'incremento dell'ossidazione è dovuto alla diffusione dell'ossidante assistita da un campo elettrico.
2. **Modelli basati sull'esistenza di difetti nell'ossido**: La presenza di micropori (~10 Å di diametro) permette alle molecole di ossigeno di diffondere più rapidamente.
3. **Modelli basati sugli effetti da "stress"**: Lo stress indotto durante la crescita porta ad un incremento della diffusività delle specie ossidanti.
4. **Modelli che ipotizzano un aumento della solubilità dell'ossidante**: Negli ossidi sottili, si osserva un aumento della concentrazione dell'ossidante alla superficie del silicio.
5. **Modelli basati sulla presenza di un sottile strato superficiale nel silicio**: Questo strato contiene ulteriori siti per la reazione di ossidazione.

##### Soluzione al Problema del Valore Iniziale

Per risolvere il problema del valore iniziale nel modello, si aggiunge un termine chiamato equazione fenomenologica, che introduce una componente esponenziale decrescente. Questo termine diminuisce di importanza con l'aumentare dello spessore dell'ossido.

- **Wolf** propone una ricetta per la crescita di un'ossidazione nanometrica, che, sebbene empirica, si è dimostrata efficace.

### Approcci per il Controllo della Velocità di Crescita

1. **Crescita con O₂ a pressione atmosferica a temperature più basse** (800-900°C).
2. **Crescita a basse pressioni totali** (inferiori alla pressione atmosferica).
3. **Crescita a ridotte pressioni parziali di O₂** (utilizzando diluenti come H₂, Ar, H₂).

- Il metodo più utilizzato è il primo, con risultati di spessore tipici di 100 Å.



![[Pasted image 20240415120941.png]]




### Effetto del Cloro

Il cloro viene utilizzato come agente per migliorare la velocità di crescita dell'ossido, sia nel regime lineare che parabolico, oltre a svolgere una funzione di pulizia superficiale.

#### Benefici dell'Aggiunta di Cloro

1. **Aumento della velocità di crescita**: Sia nel regime lineare che parabolico. Sebbene sia possibile la reazione \(2HCl + \frac{1}{2} O₂ = H₂O + Cl₂\), non c'è una spiegazione accettabile per l'incremento della velocità.
^1719767711972
2. **Miglioramento delle proprietà del materiale**:
    1. Riduzione delle cariche mobili in SiO₂.
    2. Aumento del tempo di vita dei portatori minoritari in silicio.
    3. Riduzione del numero di difetti, con conseguente aumento della tensione di rottura.
    4. Riduzione della carica fissa all'interfaccia.
    5. Riduzione dei difetti di impacchettamento indotti dal processo nel silicio.

L'uso del cloro e la gestione precisa delle condizioni di ossidazione portano a un miglioramento significativo delle caratteristiche dei dispositivi semiconduttori, sia in termini di affidabilità che di prestazioni elettriche.

---

Se hai bisogno di ulteriori chiarimenti o di approfondire qualche punto specifico, fammelo sapere!

## Processo industriale
![[Pasted image 20240415121213.png]]
![[Pasted image 20240415121227.png]]
![[Pasted image 20240415121237.png]]
### Placa verticale
- quando facciamo il proceso, si mette il substrato in verticale uno vicino a otro, si puo fare questo in ossidazione ma non in epitassia perche qua e troppo importante la variazione di temperatura ma non e imporatnte la distribucione del gas supra il substratto, come si lo é in la epitassia
	- In questi processo é molto importante la temperatura
		- Gia che la oxidassione dipende molto della temperatura
	- Nella epitassia é piú importante la distribuzione del gase supra il substratto, que no
	- Anche si fa a bassa pressione PVCD
- In questi processo la ossidazione dipende lineare di la concentrazione ma esponenciale della temperatura
# Observaciones
- Quando vediamo la curva di como é il processo di ossidasione, possiamo vedere che é simili a la curva della caraga de un capacitore,
	- Questo sucede perche il processo satura, questo si devi perche é autoalimentado
	- Quando gia abbiamo ossidazione, queste evita piú ossidazione, per quello dobbiamo modificare alcuni cosa per avere piú ossidazione, questo puo essere aumentare la temperatura o aumentarie il ossido nel ambiente

- Per potere ussare il modello di grove, abbiamo un probla, che c’é un flusso di difussione interno che il modello di grove non analizza(imagen 56% y 44%)
	- Anche questa difussione dipende del espessore del ossido che, questo varia durante il processo
	- Non avevamo il stesso problema in epitassia, perche in questa il processo era superficiale

- Il modello di ossidazzione di deal-grove non funziona per basso spesore
- Anche in questi modello dobbiamo ricordare que abbiamo due concentrazione, una tra il gas e il ossio e altra tra ossido e silicio


- La bassa tempertaura in epitassia fa il processo piú lento e anche meno puro, gia che lo fa policristalino → Per questo si fa a bassa pressione, lo quale ci permitiamo lavorare nella zona de control con una maggiore temperatura


- Il grafico di arrehinius ci lascia vedere la energia di attivazione

# Aprender
- redersi in conto
