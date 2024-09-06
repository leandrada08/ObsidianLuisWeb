---
cards-deck: Profesional::Universidad::UNISA::Segundo Cuatrimestre::Nanoeletronica
---



# Italiano

# Nanoelettronica

## Meccanismi di Conduzione in una Giunzione Metallo-Semiconduttore


### Meccanismi di Trasporto #tarjeta-anki 
Esistono quattro meccanismi principali di trasporto in una giunzione metallo-semiconduttore:
1. **Passaggio degli elettroni sopra la barriera**
2. **Effetto tunnel quantistico**
3. **Corrente di diffusione**
4. **Corrente di deriva**
- La corrente di diffusione è sempre considerata al posto della corrente di deriva.
- L'equazione di _dn_ può essere riscritta in funzione di Ec-Ef, dipendendo solo dal drogaggio. Questo permette di riscrivere l'equazione in funzione di una costante e una esponenziale in una sola variabile.
- La corrente dal semiconduttore al metallo può essere espressa utilizzando una costante di Richardson efficace.
  - Questa costante influenza la corrente totale, che è la somma della corrente dipendente dalla tensione applicata e di quella indipendente.
^1719990812735

![[Pasted image 20240630164708.png]]
#### 1. Passaggio degli Elettroni sopra la Barriera
Questo meccanismo implica che gli elettroni superino la barriera di potenziale tra il metallo e il semiconduttore. La probabilità che un elettrone superi la barriera dipende dalla sua energia e dall'altezza e forma della barriera. A temperature più elevate, più elettroni avranno energia sufficiente per attraversare la barriera.
#### 2. Effetto Tunnel Quantistico
L'effetto tunnel quantistico permette agli elettroni di passare attraverso la barriera di potenziale anche se la loro energia è inferiore all'altezza della barriera. Questo fenomeno quantistico è dovuto alla natura ondulatoria degli elettroni. La probabilità di tunnel dipende dalla larghezza e forma della barriera, così come dall'energia degli elettroni.
- L'effetto tunnel, che permette agli elettroni di passare attraverso la barriera di potenziale, non sarebbe possibile se la barriera fosse infinita.
- La probabilità che un elettrone passi attraverso l'effetto tunnel dipende dalla disponibilità di elettroni e buchi su entrambi i lati della giunzione, e si descrive mediante funzioni esponenziali decrescenti.
- Gli elettroni nella banda di conduzione hanno una maggiore probabilità di passare attraverso l'effetto tunnel, ma sono meno abbondanti a causa del loro movimento diffuso.

#### 3. Generazione e ricombinazione
Nella regione di carica spaziale (deplezione), gli elettroni e i buchi possono essere generati termicamente e ricombinarsi, influenzando la corrente attraverso il dispositivo.
- Si riferisce ai processi dinamici che avvengono nella regione di deplezione di un semiconduttore, e influenza sia la **corrente di diffusione** che la **corrente di deriva**. Questi processi descrivono come gli elettroni e i buchi si creano e si annullano, influenzando le correnti.
##### 3.1 Corrente di Diffusione
La corrente di diffusione è il flusso di elettroni guidato da gradienti di concentrazione. Nella giunzione metallo-semiconduttore, può esserci una differenza nella concentrazione di elettroni su ciascun lato della giunzione, che risulta in un flusso netto di elettroni dall'area di maggiore concentrazione a quella di minore concentrazione.
##### 3.2 Corrente di Deriva
La corrente di deriva risulta dal movimento di elettroni sotto l'influenza di un campo elettrico. Nella giunzione metallo-semiconduttore, un campo elettrico può essere creato da una differenza di potenziale applicata esternamente o dalla distribuzione di carica nella zona di deplezione. Gli elettroni si muoveranno in risposta a questo campo, contribuendo alla corrente.
#### 4. Iniezione di buchi dal metallo alla regione di carica spaziale:
Si riferisce all'iniezione di buchi dal metallo al semiconduttore nei contatti metallo-semiconduttore, contribuendo al trasporto di carica.
- Descrive un aspetto specifico del contatto metallo-semiconduttore, contribuendo alla corrente totale del dispositivo, che può includere componenti di **diffusione** e **deriva**.
- "Iniezione di buchi dal metallo alla regione di carica spaziale" è confusa nei metalli tipici.
- Nei metalli, i portatori maggioritari sono elettroni liberi; i buchi non esistono come nei semiconduttori.
- In certi contesti e condizioni speciali, i buchi possono essere considerati in modo più astratto.
Contesto di "Iniezione di Buchi":
- **Metalli con Stati Superficiali**: Alcuni metalli hanno stati superficiali che accettano elettroni dal semiconduttore, interpretandosi come iniezione di buchi.
- **Metalli con Drogaggio Inverso**: Contatto metallo-semiconduttore tipo p può portare a ricombinazione di elettroni del semiconduttore con buchi, ma non è "iniezione di buchi" dal metallo.
#### Osservazioni del Professore
- Importano i valori di banda, non la quantità di elettroni.
- Effetto tunnel non avviene con barriera di potenziale infinita.
- L'effetto tunnel dipende dagli elettroni e buchi disponibili su entrambi i lati, con una funzione esponenziale decrescente di probabilità di passare.
- Gli elettroni sopra la banda passano più facilmente ma sono meno numerosi a causa della diffusione.
- Giunzione analizzabile come fibra ottica: giunzione = cambio di mezzo, elettroni = luce, differenza di livelli di Fermi = permeabilità elettronica.
- La corrente nella regione di carica spaziale è limitata dai meccanismi di diffusione e deriva.
- Esistono tecniche più sofisticate, come la spettroscopia di transizione, che permettono di studiare in dettaglio gli stati profondi all'interfaccia. La teoria dietro queste tecniche è complessa, ma il concetto di base è alterare gli stati di energia con luce, temperatura o un bias polarizzato, e poi osservare come il sistema evolve dopo aver rimosso la perturbazione.
- I difetti nella struttura cristallina sono fondamentali per la teoria della conduzione. In assenza di difetti, non ci sarebbe resistenza nel dispositivo. La presenza di stati di trappola all'interfaccia permette di regolare le condizioni per un funzionamento ottimale del dispositivo.
- Nella nanoelettronica, la gravità può influire sui meccanismi di trasporto. La corrente dipende dalla polarizzazione applicata e questa dipendenza può influire sulla funzione e sulla costante di trasporto. La lunghezza della regione quasi neutra in un diodo corto, per esempio, dipende dalla polarizzazione applicata, il che a sua volta influisce sulla corrente.



### Emissione Termoionica nei Contatti Metallo-Semiconduttore #tarjeta-anki 
La teoria dell'emissione termoionica descrive il trasporto di elettroni quando questi acquisiscono sufficiente energia termica per superare la barriera di potenziale all'interfaccia metallo-semiconduttore. È valida quando l'altezza della barriera ($q\Phi_{Bn}$) è molto maggiore dell'energia termica ($kT$).
#### Condizioni e Supposizioni
- **Altezza della barriera**: $q\Phi_{Bn} \gg kT$.
  - Questo assicura che solo gli elettroni più energetici possano superare la barriera.
- **Equilibrio Termodinamico**: Nel piano dove si produce l'emissione, si assume che ci sia equilibrio termodinamico.
- **Sovrapposizione**: L'esistenza di un flusso netto di carica non altera l'equilibrio, permettendo di applicare il principio di sovrapposizione.
#### 1. Emissione Termoionica in Equilibrio Termodinamico (VA = 0)
- **Equilibrio Termodinamico**: Quando non si applica un voltaggio esterno ($V_A = 0$), il sistema è in equilibrio termodinamico.
- **Densità di Corrente**: La densità di corrente in equilibrio è la somma di due flussi di portatori di carica che sono uguali e opposti. Gli elettroni si muovono dal semiconduttore verso il metallo e viceversa in egual quantità.
- **Corrente Totale**: Poiché i flussi sono uguali e opposti, la corrente totale è nulla in equilibrio termodinamico.
$$ J_{total} = J_{semiconductor \to metal} - J_{metal \to semiconductor} = 0 $$
#### 2. Polarizzazione Diretta (VA > 0)
- **Diminuzione della Barriera di Potenziale**: Applicando un voltaggio positivo ($V_A > 0$), la barriera di pot
enziale all'interfaccia metallo-semiconduttore diminuisce.
- **Aumento della Densità di Elettroni**: La densità di elettroni all'interfaccia del semiconduttore aumenta, poiché gli elettroni hanno più facilità a superare la barriera ridotta.
- **Corrente Incrementata dal Semiconduttore al Metallo**: La corrente di elettroni dal semiconduttore verso il metallo aumenta.
- **Barriera Inalterata per gli Elettroni dal Metallo al Semiconduttore**: La barriera per gli elettroni che si muovono dal metallo al semiconduttore rimane invariata in $q\Phi_{Bn}$.
$$ J_{directa} = A^* T^2 e^{-q\Phi_{Bn}/kT} \left( e^{qV_A/kT} - 1 \right) $$
#### 3. Polarizzazione Inversa (VA < 0)
- **Aumento della Barriera di Potenziale**: Applicando un voltaggio negativo ($V_A < 0$), la barriera di potenziale all'interfaccia metallo-semiconduttore aumenta.
- **Diminuzione della Densità di Elettroni**: La densità di elettroni all'interfaccia del semiconduttore diminuisce, poiché la barriera aumentata rende più difficile il passaggio degli elettroni.
- **Corrente Diminuida dal Semiconduttore al Metallo**: La corrente di elettroni dal semiconduttore verso il metallo diminuisce.
- **Barriera Inalterata per gli Elettroni dal Metallo al Semiconduttore**: La barriera per gli elettroni che si muovono dal metallo al semiconduttore rimane invariata in $q\Phi_{Bn}$.
$$ J_{inversa} = A^* T^2 e^{-q\Phi_{Bn}/kT} \left( 1 - e^{-qV_A/kT} \right) $$
#### Equazione di Densità di Corrente Termoionica
L'equazione di densità di corrente termoionica, nota anche come equazione di Richardson-Dushman, descrive la corrente di elettroni che emanano da un metallo o semiconduttore a causa dell'emissione termoionica. La formula è:
^1719990812748

$$ J = A^* T^2 e^{-q\Phi_{Bn}/kT} \left( e^{qV/kT} - 1 \right) $$
dove:
- $J$ è la densità di corrente (corrente per unità di area).
- $A^*$ è la costante di Richardson.
- $T$ è la temperatura assoluta in Kelvin.
- $q$ è la carica dell'elettrone.
- $\Phi_{Bn}$ è l'altezza della barriera di potenziale.
- $k$ è la costante di Boltzmann.
- $V$ è il voltaggio applicato.
#### Costante di Richardson ($A^*$)
La costante di Richardson appare nell'equazione di densità di corrente termoionica e ha la seguente forma:
$$ A^* = \frac{4\pi qm_e k^2}{h^3} $$


### Teoria della Diffusione (Schottky) #tarjeta-anki 
La teoria della diffusione di Schottky è valida per semiconduttori con portatori di carica a bassa mobilità e basso livello di drogaggio. In questo caso, la corrente attraverso un dispositivo è limitata dai processi di diffusione e deriva all'interno della regione di carica spaziale (regione di deplezione) anziché dalla barriera metallo-semiconduttore.
Questo fenomeno si verifica quando i portatori di carica devono diffondersi attraverso questa regione per contribuire alla corrente totale, il che introduce una limitazione aggiuntiva alla corrente che può fluire attraverso la giunzione. Questi fenomeni devono essere considerati nella progettazione di dispositivi nanoelettronici per garantire prestazioni ottimali.
#### Corrente di Diffusione e Deriva
- **Diffusione**: Movimento di portatori da alta concentrazione a bassa concentrazione.
- **Deriva**: Movimento di portatori sotto l'influenza di un campo elettrico.
La corrente totale è una combinazione di questi due contributi:
$$ J = qn_0 \mu E + qD \frac{dn}{dx} $$
dove:
- $J$ è la densità di corrente.
- $q$ è la carica dell'elettrone.
- $n_0$ è la densità di portatori in equilibrio.
- $\mu$ è la mobilità dei portatori.
- $E$ è il campo elettrico.
- $D$ è il coefficiente di diffusione.
- $\frac{dn}{dx}$ è il gradiente di concentrazione dei portatori.
^1719990812752




### Teoria Termoionica-Diffusiva (Crowell e Sze) #tarjeta-anki 
La teoria termoionica-diffusiva sviluppata da Crowell e Sze si applica quando il meccanismo limitante del trasporto di carica non è semplicemente l'emissione di elettroni sopra la barriera, ma il trasporto attraverso la regione di carica spaziale. Questo modello combina gli effetti dell'emissione termoionica e della diffusione dei portatori.
#### Equazione di Corrente
Per il modello termoionico-diffusivo, l'equazione di corrente può essere espressa come:
$$ J = J_0 \left( e^{qV/kT} - 1 \right) $$
dove $J_0$ è una costante che incorpora i contributi dell'emissione termoionica e della diffusione.
^1719990812757



### Effetti di Non Idealità #tarjeta-anki 
#### 1. Resistenza Serie
In condizioni di polarizzazione diretta, l'elevata densità di corrente può causare una caduta di tensione aggiuntiva a causa della resistenza serie del materiale.
In pratica, la resistenza serie del dispositivo può influenzare significativamente i meccanismi di trasporto. Questa resistenza può alterare l'altezza della barriera di potenziale in funzione della polarizzazione applicata, complicando la previsione del comportamento del dispositivo sotto diverse condizioni di operazione.
- È importante considerare gli effetti della resistenza serie nella determinazione sperimentale dei meccanismi di trasporto.
#### 2. Abbassamento della Barriera
L'altezza della barriera di potenziale può dipendere dalla polarizzazione applicata, influenzando l'efficienza del dispositivo.
#### 3. Effetto Tunnel
L'effetto tunnel quantistico può contribuire alla corrente totale quando i portatori attraversano la barriera di potenziale, specialmente nei semiconduttori altamente drogati.
L'effetto tunnel è un meccanismo cruciale nella nanoelettronica, dove la probabilità che gli elettroni attraversino una barriera di potenziale aumenta quando la larghezza della barriera si riduce. La temperatura gioca un ruolo fondamentale in questi processi, poiché può esaltare o ridurre i comportamenti dipendenti da essa. Il professore ha fatto l'analogia di lanciare una palla in un campo di miele, dove la palla (elettrone) rallenta e può cambiare direzione, simile a come gli elettroni attraversano barriere di potenziale ridotte.
- **Equazione di Schrödinger**: Per descrivere l'effetto tunnel, si utilizza l'equazione di Schrödinger:$$ \left( -\frac{\hbar^2}{2m} \nabla^2 + E - U(\mathbf{r}) \right) \psi(\mathbf{r}) = 0 $$
  o, in una dimensione:$$ \frac{d^2 \psi(x)}{dx^2} = \frac{2m}{\hbar^2} \left( V(x) - E \right) \psi(x) $$
- **Soluzione**: Si usa la soluzione con il segno negativo assumendo che l'elettrone si muova lungo l'asse x positivo.
- **Probabilità di Trasmissione**: La probabilità di trasmissione (tunnelling) può essere approssimata mediante l'approssimazione WKB (Wentzel-Kramers-Brillouin):$$ T \approx e^{-2 \int_{x_1}^{x_2} \kappa(x) dx} $$
  dove $\kappa(x) = \sqrt{\frac{2m}{\hbar^2} (V(x) - E)}$ è il numero d'onda evanescente dentro la barriera.
![[Pasted image 20240630190028.png]]
##### Emissione Termoionica Assistita dal Campo (Thermionic-Field Emission)
- Nei semiconduttori fortemente drogati, la regione di deplezione può essere molto sottile, permettendo agli elettroni di attraversare la barriera per effetto tunnel, specialmente vicino alla cima della barriera. Questo processo è noto come emissione termoionica assistita dal campo.
2. **Condizioni di Operazione**
   - **Semiconduttori Fortemente Drogati**: La regione di deplezione è sufficientemente sottile da permettere il tunnel degli elettroni.
   - **Alta Temperatura e Campo Elettrico**: La combinazione di energia termica e campo elettrico facilita l'emissione di elettroni.
3. **Equazione Corrente-Tensione**
   - La caratteristica corrente-tensione di un diodo Schottky, quando il meccanismo dominante è l'emissione termoionica assistita dal campo, può essere calcolata mediante un approccio simile al modello termoionico. In questo caso, si valuta il prodotto del coefficiente di trasmissione del processo di tunnel e il numero di elettroni a una data energia in funzione dell'energia, integrato su tutti gli stati nella banda di conduzione.
###### Meccanismo
- **Riduzione della Barriera di Potenziale**: In presenza di un campo elettrico, la barriera di potenziale che gli elettroni devono superare si riduce a causa dell'effetto immagine di carica.
- **Densità di Corrente**: La densità di corrente per l'emissione termoionica assistita dal campo può essere approssimata mediante una modifica dell'equazione di Richardson-Dushman, che include il fattore di riduzione della barriera di potenziale.
  $$ J = A^* T^2 e^{-\frac{q(\Phi_{Bn} - \Delta \Phi)}{kT}} \left( e^{qV/kT} - 1 \right) $$
  dove $\Delta \Phi$ rappresenta la riduzione della barriera dovuta al campo elettrico applicato.
###### Applicazioni e Rilevanza
- **Dispositivi Nanoelettronici**: La comprensione di questi meccanismi è cruciale per la progettazione e ottimizzazione di dispositivi come i transistor Schottky e i sensori nanoelettronici.
- **Catodi di Tubo a Vuoto**: Utilizzati in dispositivi di generazione di microonde e tubi a raggi X.
##### Corrente di Emissione Assistita dal Campo (Field Emission)
1. **Descrizione del Fenomeno**
   - Nei semiconduttori degenerati o a basse temperature, gli elettroni possono attraversare la barriera vicino al livello di Fermi. Questo fenomeno è noto come corrente di emissione assistita dal campo e può essere il meccanismo di corrente dominante in queste condizioni.
2. **Condizioni di Operazione**
   - **Semiconduttori Degenerati**: Alta concentrazione di droganti che risulta in un livello di Fermi all'interno della banda di conduzione.
   - **Basse Temperature**: Il contributo termico è minimo e il tunnel quantistico vicino al livello di Fermi diventa il meccanismo principale di trasporto.
3. **Equazione Corrente-Tensione**
   - La corrente di emissione assistita dal campo può essere descritta utilizzando la teoria del tunnel quantistico, dove la probabilità di trasmissione dipende dal coefficiente di trasmissione di tunnel e dalla densità di stati nel livello di Fermi.
##### Osservazioni del Professore
- **Probabilità di Tunnel**: La probabilità che gli elettroni attraversino la barriera di potenziale aumenta con l'assistenza del campo elettrico, specialmente in condizioni dove la temperatura da sola non sarebbe sufficiente per superare la barriera.
- **Indipendenza della Temperatura**: L'emissione assistita dal campo mostra una relativa indipendenza dalla temperatura rispetto alla pura emissione termoionica, che è una caratteristica distintiva importante.
#### Correnti di Generazione
In condizioni di polarizzazione inversa, le correnti di generazione nella regione di deplezione possono essere significative.
#### Effetto degli Stati di Interfaccia
##### Influenza degli Stati di Interfaccia nella Barriera di Potenziale
La densità di stati all'interfaccia metallo-semiconduttore può influenzare l'altezza della barriera e, quindi, la corrente del dispositivo. Gli stati di trappola all'interfaccia sono siti dove gli elettroni possono rimanere temporaneamente intrappolati. L'occupazione di questi stati dipende da diversi fattori, specialmente dalla temperatura.
- **Stati di Trappola**: Gli elettroni possono rimanere intrappolati in questi stati, influenzando il flusso di corrente. L'occupazione degli stati di trappola aumenta con la temperatura, poiché gli elettroni acquisiscono sufficiente energia per occupare questi stati.
- **Livello di Fermi**: La posizione del livello di Fermi, che è influenzata dalla temperatura, influisce anche sull'occupazione degli stati di trappola.
- **Frequenza del Segnale AC**: La frequenza del segnale AC gioca un ruolo nella misurazione dell'occupazione di questi stati. La frequenza e la temperatura sono fondamentali per comprendere la conduzione nel dispositivo.
##### Relazione tra Temperatura e Frequenza
La temperatura e la frequenza del segnale AC sono interrelate e influenzano l'occupazione degli stati di trappola all'interfaccia metallo-semiconduttore.
- **Alta Temperatura**: Aumenta l'energia degli elettroni, permettendo loro di occupare gli stati di trappola.
- **Livello di Fermi**: La temperatura modifica anche la posizione del livello di Fermi, influenzando l'occupazione degli stati di trappola.
- **Frequenza del Segnale AC**: La variazione di capacità e la transizione tra stati dipendono dalla frequenza del segnale.
  - **Bassa Temperatura**: Equivale a alta frequenza.
  - **Alta Temperatura**: Equivale a bassa frequenza.
Questi cambiamenti in temperatura e frequenza possono modificare il movimento degli elettroni nella giunzione metallo-semiconduttore, influenzando i loro stati energetici e la conduttanza del dispositivo.
##### Capacità e Conduttanza
La variazione nella capacità del dispositivo con la frequenza del segnale applicato è un indicatore importante della dinamica degli stati di trappola. La conduttanza del dispositivo può essere misurata come un'evoluzione della capacità.
- **Pico di Conduttanza**: Un pico nella conduttanza indica che gli elettroni hanno raggiunto la banda di conduzione, contribuendo a un segnale di corrente. L'altezza di questo pico è proporzionale alla densità di stati di trappola all'interfaccia.
- **Teoria Complessa**: Anche se la teoria dietro questo fenomeno è complessa, il concetto chiave è che il dispositivo esibisce una combinazione di comportamento capacitivo e resistivo.
###### Risonanza
La risonanza si produce quando la frequenza coincide con la posizione del livello di Fermi, stabilendo un'equivalenza tra energia, frequenza e temperatura. Questa risonanza è cruciale per comprendere la dinamica degli stati di trappola e il loro impatto sulla conduzione.
##### Tecniche di Studio degli Stati Profondi
Per studiare gli stati profondi all'interfaccia metallo-semiconduttore, si utilizzano tecniche avanzate come la spettroscopia di transizione.
- **Spettroscopia di Transizione**: Permette di occupare gli stati con luce, temperatura o un bias polarizzato e poi studiare i transitori al rimuovere la perturbazione. Questa tecnica è essenziale per comprendere la dinamica degli stati di trappola e il loro impatto sulla conduzione.
Queste tecniche avanzate aiutano a rivelare come le perturbazioni influenzano l'occupazione degli stati e come questi transitori si relazionano con la conduttività del dispositivo. Il professore ha sottolineato l'importanza di queste tecniche per una comprensione profonda della dinamica degli stati di trappola.
^1719990812762




### Effetto Schottky #tarjeta-anki 
L'effetto Schottky descrive la diminuzione della barriera di potenziale per l'emissione di un elettrone a causa dell'applicazione di un campo elettrico esterno. Questo fenomeno può essere spiegato mediante l'interazione della carica immagine.
#### Carica di Immagine
- **Carica di Immagine**: Quando un elettrone si avvicina a un metallo, induce una carica positiva sulla superficie del metallo. La forza di attrazione tra l'elettrone e la carica indotta può essere descritta come una forza tra un elettrone nella posizione $x$ e una carica positiva nella posizione $-x$.
#### Energia Potenziale di Immagine
L'energia potenziale di un elettrone a una distanza $x$ dal metallo può essere valutata mediante il lavoro necessario per portare l'elettrone dall'infinito al punto $x$:
$$ E_p(x) = -\frac{q^2}{4\pi\epsilon_0 2x} $$
#### Effetto del Campo Elettrico Esterno
In presenza di un campo elettrico esterno $E$, l'energia potenziale totale si modifica:
$$ E_{p,tot}(x) = -\frac{q^2}{4\pi\epsilon_0 2x} - qEx $$
#### Riduzione della Barriera (Effetto Schottky)
La riduzione della barriera di potenziale a causa dell'applicazione del campo elettrico esterno è:
$$ \Delta\Phi = \sqrt{\frac{qE}{4\pi\epsilon_0}} $$
Questa riduzione influisce sulla corrente di emissione termoionica:
$$ J = A^* T^2 e^{-(q\Phi_{Bn} - \Delta\Phi)/kT} \left( e^{qV/kT} - 1 \right) $$
![[Pasted image 20240630175107.png]]
^1719990812766


## Ordinare
### Dipendenza della Corrente nella Polarizzazione Applicata
Esiste una corrente che non dipende dalla polarizzazione, il che indica un'indipendenza dall'altezza della barriera. 
In nanoelettronica, la corrente attraverso i dispositivi dipende significativamente dalla polarizzazione applicata. La corrente può cambiare la dipendenza dalla funzione e la costante a causa della polarizzazione. Questo non è un fatto nuovo, poiché, come osservato nei diodi corti, la regione quasi neutra del dispositivo dipendeva anche dalla polarizzazione applicata, influenzando così la lunghezza di questa regione e, conseguentemente, la corrente.
In una giunzione metallo-semiconduttore, la corrente che non dipende dalla polarizzazione si produce a causa dell'altezza della barriera di potenziale che rimane costante. Questo tipo di corrente è cruciale perché il suo comportamento non cambia con la polarizzazione applicata, il che si traduce in un'operazione stabile e prevedibile.
- La buona distruzione della corrente si deve all'indipendenza dalla polarizzazione, che è una caratteristica desiderabile in questi dispositivi.

#### Emissione Termoionica Assistita dal Campo

- **Effetto Tunnel:** Se gli elettroni hanno più energia, c'è una maggiore probabilità di attraversare la barriera per effetto tunnel, specialmente nell'emissione termoionica assistita dal campo. Questo processo è molto associato alla temperatura.
- **Indipendenza dalla Temperatura:** L'emissione assistita dal campo non dipende dalla temperatura.

Nell'emissione termoionica assistita dal campo, la probabilità che gli elettroni attraversino la barriera di potenziale dipende dalla larghezza della barriera e non dalla temperatura. Questo differisce da altri meccanismi dove la temperatura gioca un ruolo cruciale.
- Comprendere la dipendenza di questi processi dalla temperatura e dalla larghezza della barriera è fondamentale per ottimizzare la progettazione e il funzionamento dei dispositivi.

### Dipendenza della Corrente nella Polarizzazione Applicata

In nanoelettronica, la corrente attraverso la giunzione metallo-semiconduttore può dipendere dalla polarizzazione applicata. Ad esempio, nell'effetto tunnel, la probabilità che gli elettroni attraversino la barriera di potenziale aumenta quando la larghezza della barriera si riduce. La temperatura è un fattore chiave che può modificare questi comportamenti, poiché può accentuare o ridurre gli effetti della polarizzazione e della barriera di potenziale.
- Nel diodo corto, la regione quasi neutra dipendeva dalla polarizzazione applicata, influenzando la corrente.
In nanoelettronica, la corrente attraverso i dispositivi dipende significativamente dalla polarizzazione applicata. Il professore ha spiegato che la corrente può cambiare la dipendenza dalla funzione e dalla costante a causa della polarizzazione. Questo non è un fatto nuovo, poiché, come osservato nei diodi corti, la regione quasi neutra del dispositivo dipendeva anche dalla polarizzazione applicata, influenzando così la lunghezza di questa regione e, conseguentemente, la corrente.



# Espagnolo

## Mecanismos de Conducción en una Unión Metal-Semiconductor
### Mecanismos de Transporte

Existen cuatro mecanismos principales de transporte en la unión metal-semiconductor:

1. **Paso de electrones sobre la barrera**
2. **Atravesamiento cuántico (Efecto Túnel)**
3. **Corriente de difusión**
4. **Corriente de deriva**

- La corriente de difusión es siempre considerada en lugar de la corriente de deriva.
- La ecuación de _dn_ puede reescribirse en función de Ec-Ef, dependiendo solo del dopaje. Esto permite reescribir la ecuación en función de una constante y una exponencial en una sola variable.
- La corriente del semiconductor al metal puede expresarse utilizando una constante de Richardson eficaz.
	-  Esta constante influye en la corriente total, que es la suma de la corriente dependiente de la tensión aplicada y la independiente

![[Pasted image 20240630164708.png]]
#### 1. Paso de Electrones por Encima de la Barrera

Este mecanismo implica que los electrones superan la barrera de potencial entre el metal y el semiconductor. La probabilidad de que un electrón supere la barrera depende de su energía y de la altura y forma de la barrera. A temperaturas más altas, más electrones tendrán la energía suficiente para cruzar la barrera.

#### 2. Túnel Cuántico

El efecto túnel cuántico permite que los electrones pasen a través de la barrera de potencial incluso si su energía es menor que la altura de la barrera. Este fenómeno cuántico se debe a la naturaleza ondulatoria de los electrones. La probabilidad de túnel depende de la anchura y forma de la barrera, así como de la energía de los electrones.
- El efecto túnel, que permite que los electrones pasen a través de la barrera de potencial, no sería posible si la barrera fuera infinita.
- La probabilidad de que un electrón pase por el efecto túnel depende de la disponibilidad de electrones y huecos en ambos lados de la unión, y se describe mediante funciones exponenciales decrecientes.
- Los electrones en la banda de conducción tienen una mayor probabilidad de pasar por el efecto túnel, pero son menos abundantes debido a su movimiento difusivo.

#### 3. Generazion y recombinazion
En la region de carga espacial(deplecion), los electrones y huecos pueden ser generador termicamente y recombinarse,a fectando la corriente a traves del dispositivo
- Se refiere a los procesos dinámicos que ocurren en la región de depleción de un semiconductor, y afecta tanto la **corriente de difusión** como la **corriente de deriva**. Estos procesos describen cómo los electrones y huecos se crean y aniquilan, afectando las corrientes.
##### 3.1 Corriente de Difusión
La corriente de difusión es el flujo de electrones impulsado por gradientes de concentración. En la unión metal-semiconductor, puede haber una diferencia en la concentración de electrones a cada lado de la unión, lo que resulta en un flujo neto de electrones desde el área de mayor concentración a la de menor concentración.
##### 3.2 Corriente de Deriva

La corriente de deriva resulta del movimiento de electrones bajo la influencia de un campo eléctrico. En la unión metal-semiconductor, un campo eléctrico puede ser creado por una diferencia de potencial aplicada externamente o por la distribución de carga en la zona de depleción. Los electrones se moverán en respuesta a este campo, contribuyendo a la corriente.

#### 4. Inteccion de lagunas del emtla a la region de carga espacial:
Se refiere a la inyeccion de huecos desde el metal hacia el semiconductor en contactos metal-semiconductor, contribuyendo al transporte de carga
- Describe un aspecto específico del contacto metallo-semiconductor, contribuyendo a la corriente total del dispositivo, que puede incluir componentes de **difusión** y **deriva**.

- "Inyección de huecos del metal a la región de carga espacial" es confusa en metales típicos.
- En metales, los portadores mayoritarios son electrones libres; los huecos no existen como en semiconductores.
- En ciertos contextos y condiciones especiales, los huecos pueden considerarse de manera más abstracta.

Contexto de "Inyección de Huecos":

- **Metales con Estados Superficiales**: Algunos metales tienen estados superficiales que aceptan electrones del semiconductor, interpretándose como inyección de huecos.
- **Metales con Dopaje Inverso**: Contacto metal-semiconductor tipo p puede llevar a recombinación de electrones del semiconductor con huecos, pero no es "inyección de huecos" desde el metal.


#### Observaciones del Profesor
- Importan los valores de banda, no la cantidad de electrones.
- Efecto túnel no ocurre con barrera de potencial infinita.
- El efecto túnel depende de los electrones y huecos disponibles en ambos lados, con una función exponencial decreciente de probabilidad de pasar.
- Electrones sobre la banda pasan más fácilmente pero son menos debido a la difusión.
- Unión analizable como fibra óptica: unión = cambio de medio, electrones = luz, diferencia de niveles de Fermi = permeabilidad electrónica.


- La corriente en la región de carga espacial está limitada por los mecanismos de difusión y deriva.
- Existen técnicas más sofisticadas, como la espectroscopia de transición, que permiten estudiar en detalle los estados profundos en la interfaz. La teoría detrás de estas técnicas es compleja, pero el concepto básico es alterar los estados de energía con luz, temperatura o un sesgo polarizado, y luego observar cómo el sistema evoluciona después de eliminar la perturbación.
- Los defectos en la estructura cristalina son fundamentales para la teoría de la conducción. En ausencia de defectos, no habría resistencia en el dispositivo. La presencia de estados de trampa en la interfaz permite ajustar las condiciones para un funcionamiento óptimo del dispositivo.
- En la nanoelectrónica, la gravedad puede influir en los mecanismos de transporte. La corriente depende de la polarización aplicada y esta dependencia puede afectar la función y la constante de transporte. La longitud de la región casi neutra en un diodo corto, por ejemplo, depende de la polarización aplicada, lo que a su vez influye en la corriente.


### Emisión Termoiónica en Contactos Metal-Semiconductor
La teoría de la emisión termoiónica describe el transporte de electrones cuando estos adquieren suficiente energía térmica para superar la barrera de potencial en la interfaz metal-semiconductor. Es válida cuando la altura de la barrera ($q\Phi_{Bn}$) es mucho mayor que la energía térmica ($kT$).

#### Condiciones y Suposiciones
- **Altura de la barrera**: $q\Phi_{Bn} \gg kT$.
	- Esto nos asegura que solo los electrones mas energeticos pueden superar la barrera
- **Equilibrio Termodinámico**: En el plano donde se produce la emisión, se asume que hay equilibrio termodinámico.
- **Superposición**: La existencia de un flujo neto de carga no altera el equilibrio, permitiendo aplicar el principio de superposición.


#### 1. Emisión Termoiónica en Equilibrio Termodinámico (VA = 0)

- **Equilibrio Termodinámico**: Cuando no se aplica un voltaje externo ($V_A = 0$), el sistema está en equilibrio termodinámico.
- **Densidad de Corriente**: La densidad de corriente en equilibrio es la suma de dos flujos de portadores de carga que son iguales y opuestos. Los electrones se mueven desde el semiconductor hacia el metal y viceversa en igual cantidad.
- **Corriente Total**: Debido a que los flujos son iguales y opuestos, la corriente total es nula en equilibrio termodinámico.

$$ J_{total} = J_{semiconductor \to metal} - J_{metal \to semiconductor} = 0 $$

#### 2. Polarización Directa (VA > 0)

- **Disminución de la Barrera de Potencial**: Al aplicar un voltaje positivo ($V_A > 0$), la barrera de potencial en la interfaz metal-semiconductor disminuye.
- **Aumento de la Densidad de Electrones**: La densidad de electrones en la interfaz del semiconductor aumenta, ya que los electrones tienen más facilidad para superar la barrera reducida.
- **Corriente Incrementada del Semiconductor al Metal**: La corriente de electrones desde el semiconductor hacia el metal aumenta.
- **Barrera Inmutable para Electrones del Metal al Semiconductor**: La barrera para los electrones que se mueven del metal al semiconductor permanece inalterada en $q\Phi_{Bn}$.

$$ J_{directa} = A^* T^2 e^{-q\Phi_{Bn}/kT} \left( e^{qV_A/kT} - 1 \right) $$

#### 3. Polarización Inversa (VA < 0)

- **Aumento de la Barrera de Potencial**: Al aplicar un voltaje negativo ($V_A < 0$), la barrera de potencial en la interfaz metal-semiconductor aumenta.
- **Disminución de la Densidad de Electrones**: La densidad de electrones en la interfaz del semiconductor disminuye, ya que la barrera aumentada dificulta el paso de los electrones.
- **Corriente Disminuida del Semiconductor al Metal**: La corriente de electrones desde el semiconductor hacia el metal disminuye.
- **Barrera Inmutable para Electrones del Metal al Semiconductor**: La barrera para los electrones que se mueven del metal al semiconductor permanece inalterada en $q\Phi_{Bn}$.

$$ J_{inversa} = A^* T^2 e^{-q\Phi_{Bn}/kT} \left( 1 - e^{-qV_A/kT} \right) $$

#### Ecuación de Densidad de Corriente Termoiónica

La ecuación de densidad de corriente termoiónica, también conocida como ecuación de Richardson-Dushman, describe la corriente de electrones que emanan de un metal o semiconductor debido a la emisión termoiónica. La fórmula es:

$$ J = A^* T^2 e^{-q\Phi_{Bn}/kT} \left( e^{qV/kT} - 1 \right) $$

donde:
- $J$ es la densidad de corriente (corriente por unidad de área).
- $A^*$ es la constante de Richardson.
- $T$ es la temperatura absoluta en Kelvin.
- $q$ es la carga del electrón.
- $\Phi_{Bn}$ es la altura de la barrera de potencial.
- $k$ es la constante de Boltzmann.
- $V$ es el voltaje aplicado.

#### Constante de Richardson ($A^*$)

La constante de Richardson aparece en la ecuación de densidad de corriente termoiónica y tiene la siguiente forma:

$$ A^* = \frac{4\pi qm_e k^2}{h^3} $$



### Teoría de la Difusión (Schottky)

La teoría de la difusión de Schottky es válida para semiconductores con portadores de carga de baja movilidad y bajo nivel de dopaje. En este caso, la corriente a través de un dispositivo está limitada por los procesos de difusión y deriva dentro de la región de carga espacial (región de depleción) en lugar de la barrera metal-semiconductor.
Este fenómeno ocurre cuando los portadores de carga deben difundirse a través de esta región para contribuir a la corriente total, lo cual introduce una limitación adicional a la corriente que puede fluir a través de la unión.Estos fenómenos deben considerarse en el diseño de dispositivos nanoelectrónicos para garantizar un rendimiento óptimo.
#### Corriente de Difusión y Deriva
- **Difusión**: Movimiento de portadores de alta concentración a baja concentración.
- **Deriva**: Movimiento de portadores bajo la influencia de un campo eléctrico.

La corriente total es una combinación de estas dos contribuciones:

$$ J = qn_0 \mu E + qD \frac{dn}{dx} $$

donde:
- $J$ es la densidad de corriente.
- $q$ es la carga del electrón.
- $n_0$ es la densidad de portadores en equilibrio.
- $\mu$ es la movilidad de los portadores.
- $E$ es el campo eléctrico.
- $D$ es el coeficiente de difusión.
- $\frac{dn}{dx}$ es el gradiente de concentración de portadores.

### Teoría Termoiónica-Difusiva (Crowell y Sze)
La teoría termoiónica-difusiva desarrollada por Crowell y Sze se aplica cuando el mecanismo limitante del transporte de carga no es simplemente la emisión de electrones por encima de la barrera, sino el transporte a través de la región de carga espacial. Este modelo combina los efectos de la emisión termoiónica y la difusión de portadores.

#### Ecuación de Corriente
Para el modelo termoiónico-difusivo, la ecuación de corriente se puede expresar como:

$$ J = J_0 \left( e^{qV/kT} - 1 \right) $$

donde $J_0$ es una constante que incorpora las contribuciones de la emisión termoiónica y la difusión.

### Efectos de No Idealidad

#### 1. Resistencia Serie
En condiciones de polarización directa, la elevada densidad de corriente puede causar una caída de tensión adicional debido a la resistencia serie del material.

En la práctica, la resistencia serie del dispositivo puede influir significativamente en los mecanismos de transporte. Esta resistencia puede alterar la altura de la barrera de potencial en función de la polarización aplicada, complicando la predicción del comportamiento del dispositivo bajo diferentes condiciones de operación.
- Es importante considerar los efectos de resistencia seria en la determinación experimental de los mecanismos de transporte.
#### 2. Abbassamento della Barriera
La altura de la barrera de potencial puede depender de la polarización aplicada, lo que afecta la eficiencia del dispositivo.

#### 3. Efecto Túnel
El efecto túnel cuántico puede contribuir a la corriente total cuando los portadores atraviesan la barrera de potencial, especialmente en semiconductores altamente dopados.
El efecto túnel es un mecanismo crucial en la nanoelectrónica, donde la probabilidad de que los electrones atraviesen una barrera de potencial aumenta cuando la anchura de la barrera se reduce. La temperatura juega un papel fundamental en estos procesos, ya que puede resaltar o reducir los comportamientos dependientes de ella. El profesor hizo la analogía de lanzar una pelota en un campo de miel, donde la pelota (electrón) se ralentiza y puede cambiar de dirección, similar a cómo los electrones atraviesan barreras de potencial reducidas.


- **Ecuación de Schrödinger**: Para describir el efecto túnel, se utiliza la ecuación de Schrödinger:
  $$ \left( -\frac{\hbar^2}{2m} \nabla^2 + E - U(\mathbf{r}) \right) \psi(\mathbf{r}) = 0 $$
  o, en una dimensión:
  $$ \frac{d^2 \psi(x)}{dx^2} = \frac{2m}{\hbar^2} \left( V(x) - E \right) \psi(x) $$

- **Solución**: Se usa la solución con el signo negativo asumiendo que el electrón se mueve a lo largo del eje x positivo.

- **Probabilidad de Transmisión**: La probabilidad de transmisión (tunnelling) se puede aproximar mediante la aproximación WKB (Wentzel-Kramers-Brillouin):
  $$ T \approx e^{-2 \int_{x_1}^{x_2} \kappa(x) dx} $$
  donde $\kappa(x) = \sqrt{\frac{2m}{\hbar^2} (V(x) - E)}$ es el número de onda evanescente dentro de la barrera.




![[Pasted image 20240630190028.png]]

##### Emisión Termoiónica Asistida por Campo (Thermionic-Field Emission)
- En semiconductores fuertemente dopados, la región de depleción puede ser muy delgada, permitiendo que los electrones atraviesen la barrera por efecto túnel, especialmente cerca de la cima de la barrera. Este proceso se conoce como emisión termoiónica asistida por campo.

2. **Condiciones de Operación**
   - **Semiconductores Fuertemente Dopados**: La región de depleción es lo suficientemente delgada como para permitir el túnel de electrones.
   - **Alta Temperatura y Campo Eléctrico**: La combinación de energía térmica y campo eléctrico facilita la emisión de electrones.

3. **Ecuación de Corriente-Tensión**
   - La característica corriente-tensión de un diodo Schottky, cuando el mecanismo dominante es la emisión termoiónica asistida por campo, se puede calcular mediante un enfoque similar al modelo termoiónico. En este caso, se evalúa el producto del coeficiente de transmisión del proceso de túnel y el número de electrones a una dada energía en función de la energía, integrado sobre todos los estados en la banda de conducción.
###### Mecanismo
- **Reducción de la Barrera de Potencial**: En presencia de un campo eléctrico, la barrera de potencial que los electrones deben superar se reduce debido al efecto de la imagen de carga.
- **Densidad de Corriente**: La densidad de corriente para la emisión termoiónica asistida por campo puede ser aproximada mediante una modificación de la ecuación de Richardson-Dushman, que incluye el factor de reducción de la barrera de potencial.

  $$ J = A^* T^2 e^{-\frac{q(\Phi_{Bn} - \Delta \Phi)}{kT}} \left( e^{qV/kT} - 1 \right) $$

  donde $\Delta \Phi$ representa la reducción de la barrera debido al campo eléctrico aplicado.

###### Aplicaciones y Relevancia
- **Dispositivos Nanoelectrónicos**: La comprensión de estos mecanismos es crucial para el diseño y optimización de dispositivos como transistores Schottky y sensores nanoelectrónicos.
- **Cátodos de Tubos de Vacío**: Utilizados en dispositivos de generación de microondas y tubos de rayos X.
##### Corriente de Emisión Asistida por Campo (Field Emission)

1. **Descripción del Fenómeno**
   - En semiconductores degenerados o a temperaturas bajas, los electrones pueden atravesar la barrera cerca del nivel de Fermi. Este fenómeno se conoce como corriente de emisión asistida por campo y puede ser el mecanismo de corriente dominante en estas condiciones.

2. **Condiciones de Operación**
   - **Semiconductores Degenerados**: Alta concentración de dopantes que resulta en un nivel de Fermi dentro de la banda de conducción.
   - **Bajas Temperaturas**: La contribución térmica es mínima y el túnel cuántico cerca del nivel de Fermi se convierte en el mecanismo principal de transporte.

3. **Ecuación de Corriente-Tensión**
   - La corriente de emisión asistida por campo se puede describir utilizando la teoría del túnel cuántico, donde la probabilidad de transmisión depende del coeficiente de transmisión de túnel y la densidad de estados en el nivel de Fermi.

##### Observaciones del Profesor
- **Probabilidad de Túnel**: La probabilidad de que los electrones atraviesen la barrera de potencial aumenta con la asistencia del campo eléctrico, especialmente en condiciones donde la temperatura por sí sola no sería suficiente para superar la barrera.
- **Independencia de la Temperatura**: La emisión asistida por campo muestra una independencia relativa de la temperatura en comparación con la pura emisión termoiónica, lo que es una característica distintiva importante.
#### 4. Corrientes de Generación
En condiciones de polarización inversa, las corrientes de generación en la región de depleción pueden ser significativas.

#### 5. Efecto de los Estados de Interfaz

##### Influencia de los Estados de Interfaz en la Barrera de Potencial

La densidad de estados en la interfaz metal-semiconductor puede afectar la altura de la barrera y, por tanto, la corriente del dispositivo. Los estados de trampa en la interfaz son sitios donde los electrones pueden quedar atrapados temporalmente. La ocupación de estos estados depende de varios factores, especialmente de la temperatura.

- **Estados de Trampa**: Los electrones pueden quedar atrapados en estos estados, afectando el flujo de corriente. La ocupación de los estados de trampa aumenta con la temperatura, ya que los electrones adquieren suficiente energía para ocupar estos estados.
- **Nivel de Fermi**: La posición del nivel de Fermi, que se ve influenciada por la temperatura, también afecta la ocupación de los estados de trampa.
- **Frecuencia de la Señal AC**: La frecuencia de la señal AC juega un papel en la medición de la ocupación de estos estados. La frecuencia y la temperatura son fundamentales para entender la conducción en el dispositivo.

##### Relación entre Temperatura y Frecuencia

La temperatura y la frecuencia de la señal AC están interrelacionadas y afectan la ocupación de los estados de trampa en la interfaz metal-semiconductor.

- **Temperatura Alta**: Aumenta la energía de los electrones, permitiendo que ocupen los estados de trampa.
- **Nivel de Fermi**: La temperatura también modifica la posición del nivel de Fermi, influyendo en la ocupación de los estados de trampa.
- **Frecuencia de la Señal AC**: La variación de capacidad y la transición entre estados dependen de la frecuencia de la señal.
  - **Baja Temperatura**: Equivale a alta frecuencia.
  - **Alta Temperatura**: Equivale a baja frecuencia.
  
Estos cambios en temperatura y frecuencia pueden modificar el movimiento de electrones en la unión metal-semiconductor, afectando sus estados de energía y la conductancia del dispositivo.

##### Capacidad y Conductancia

La variación en la capacidad del dispositivo con la frecuencia de la señal aplicada es un indicador importante de la dinámica de los estados de trampa. La conductancia del dispositivo puede medirse como una evolución de la capacidad.

- **Pico de Conductancia**: Un pico en la conductancia indica que los electrones han alcanzado la banda de conducción, contribuyendo a una señal de corriente. La altura de este pico es proporcional a la densidad de estados de trampa en la interfaz.
- **Teoría Compleja**: Aunque la teoría detrás de este fenómeno es compleja, el concepto clave es que el dispositivo exhibe una combinación de comportamiento capacitivo y resistivo.

###### Resonancia

La resonancia se produce cuando la frecuencia coincide con la posición del nivel de Fermi, estableciendo una equivalencia entre energía, frecuencia y temperatura. Esta resonancia es crucial para comprender la dinámica de los estados de trampa y su impacto en la conducción.

##### Técnicas de Estudio de Estados Profundos

Para estudiar los estados profundos en la interfaz metal-semiconductor, se utilizan técnicas avanzadas como la espectroscopía de transición.

- **Espectroscopía de Transición**: Permite ocupar los estados con luz, temperatura o un bias polarizado y luego estudiar los transientes al remover la perturbación. Esta técnica es esencial para comprender la dinámica de los estados de trampa y su impacto en la conducción.

Estas técnicas avanzadas ayudan a revelar cómo las perturbaciones afectan la ocupación de los estados y cómo estos transientes se relacionan con la conductividad del dispositivo. El profesor destacó la importancia de estas técnicas para una comprensión profunda de la dinámica de los estados de trampa.


### Efecto Schottky
El efecto Schottky describe la disminución de la barrera de potencial para la emisión de un electrón debido a la aplicación de un campo eléctrico externo. Este fenómeno puede explicarse mediante la interacción de la carga de imagen.

#### Carga de Imagen
- **Carga de Imagen**: Cuando un electrón se aproxima a un metal, induce una carga positiva en la superficie del metal. La fuerza de atracción entre el electrón y la carga inducida puede describirse como una fuerza entre un electrón en la posición $x$ y una carga positiva en la posición $-x$.

#### Energía Potencial de Imagen
La energía potencial de un electrón a una distancia $x$ del metal puede evaluarse mediante el trabajo necesario para llevar el electrón desde el infinito al punto $x$:

$$ E_p(x) = -\frac{q^2}{4\pi\epsilon_0 2x} $$

#### Efecto del Campo Eléctrico Externo
En presencia de un campo eléctrico externo $E$, la energía potencial total se modifica:

$$ E_{p,tot}(x) = -\frac{q^2}{4\pi\epsilon_0 2x} - qEx $$

#### Reducción de la Barrera (Efecto Schottky)
La reducción de la barrera de potencial debido a la aplicación del campo eléctrico externo es:
$$ \Delta\Phi = \sqrt{\frac{qE}{4\pi\epsilon_0}} $$
Esta reducción afecta la corriente de emisión termoiónica:
$$ J = A^* T^2 e^{-(q\Phi_{Bn} - \Delta\Phi)/kT} \left( e^{qV/kT} - 1 \right) $$

![[Pasted image 20240630175107.png]]


## Ordendar
### Dependencia de la Corriente en la Polarización Aplicada
existe una corriente que no depende de la polarización, lo que indica una independencia de la altura de la barrera
En nanoelectrónica, la corriente a través de los dispositivos depende significativamente de la polarización aplicada. La corriente puede cambiar la dependencia de la función y la constante debido a la polarización. Esto no es un hecho nuevo, ya que, como se observó en los diodos cortos, la región casi neutra del dispositivo también dependía de la polarización aplicada, afectando así la longitud de esta región y, consecuentemente, la corriente.
En una unión metal-semiconductor, la corriente que no depende de la polarización se produce debido a la altura de la barrera de potencial que permanece constante. Este tipo de corriente es crucial porque su comportamiento no cambia con la polarización aplicada, lo que se traduce en una operación estable y predecible.
- La buena destrucción de la corriente se debe a la independencia de la polarización, lo que es una característica deseable en estos dispositivos.


#### Emisión Termoiónica Asistida por Campo

- **Efecto Túnel:** Si los electrones tienen más energía, hay mayor probabilidad de atravesar la barrera por efecto túnel, especialmente en la emisión termoiónica asistida por campo. Este proceso está muy asociado a la temperatura.
- **Independencia de la Temperatura:** La emisión asistida por campo no depende de la temperatura.


En la emisión termoiónica asistida por campo, la probabilidad de que los electrones atraviesen la barrera de potencial depende de la anchura de la barrera y no de la temperatura. Esto difiere de otros mecanismos donde la temperatura juega un papel crucial.
- Entender la dependencia de estos procesos en la temperatura y la anchura de la barrera es fundamental para optimizar el diseño y funcionamiento de los dispositivos.






### Dependencia de la Corriente en la Polarización Aplicada

En nanoelectrónica, la corriente a través de la unión metal-semiconductor puede depender de la polarización aplicada. Por ejemplo, en el efecto túnel, la probabilidad de que los electrones atraviesen la barrera de potencial aumenta cuando la anchura de la barrera se reduce. La temperatura es un factor clave que puede modificar estos comportamientos, ya que puede acentuar o reducir los efectos de la polarización y la barrera de potencial.
- En el diodo corto, la región casi neutra dependía de la polarización aplicada, afectando la corriente.
En nanoelectrónica, la corriente a través de los dispositivos depende significativamente de la polarización aplicada. El profesor explicó que la corriente puede cambiar la dependencia de la función y la constante debido a la polarización. Este no es un hecho nuevo, ya que, como se observó en los diodos cortos, la región casi neutra del dispositivo también dependía de la polarización aplicada, afectando así la longitud de esta región y, consecuentemente, la corriente.


## Transcripcion

"En cuanto a los mecanismos de transporte, hemos revisado el principio fundamental. La corriente que no depende de la polarización es la que se produce entre el metal y el semiconductor, ya que la altura de la barrera no cambia. La buena destrucción de la corriente se debe a la independencia de la polarización.

Existen mecanismos de transporte que no vamos a profundizar, como la corriente limitada por la teoría de la difusión, que se produce cuando la corriente es limitada por los mecanismos de difusión dentro de la región de carga espacial.

La importancia de la determinación experimental de los mecanismos de transporte radica en que todas estas consideraciones están limitadas por efectos de resistencia seria. La altura de la barrera depende de la polarización, lo que no se puede predecir de manera simple.

Hemos hablado sobre la importancia de la temperatura en la ocupación de los estados de trampa en la interfaz. Al aumentar la temperatura, los electrones pueden tener suficiente energía para ocupar los estados de trampa.

La temperatura también afecta la posición del nivel de Fermi, lo que a su vez influye en la ocupación de los estados de trampa. La frecuencia del señal AC también juega un papel importante en la medición de la ocupación de los estados de trampa.


"La novedad en la señal es la variación de capacidad entre un nivel más bajo y otro nivel. La transición se produce cuando los estados responden a la frecuencia. La profundidad de los estados depende de la velocidad de variación, la derivada y la derivada segunda. La conductancia se mide como una evolución de la capacidad. Un pico de conductancia indica que los electrones han alcanzado la banda de conducción y han dado un señal de corriente.

La altura de este grupo es proporcional a la densidad de estados de trampa en la interfaz. La teoría es complicada, pero el concepto es claro: el dispositivo tiene dos componentes, una capacidad y una resistencia.

La frecuencia y la temperatura son fundamentales para entender la conducción en el dispositivo. La resonancia se produce cuando la frecuencia coincide con la posición del nivel de Fermi. La energía, la frecuencia y la temperatura son equivalentes.

Existen técnicas más complejas para estudiar los estados profundos en la interfaz, como la espectroscopia de transición. La teoría es complicada, pero el concepto es que puedo ocupar los estados con la luz, la temperatura o un bias polarizado, y luego remover la perturbación para estudiar los transientes.

Los defectos son fundamentales en la teoría de la conducción. Sin defectos, no hay resistencia en el dispositivo. La existencia de los estados de trampa me permite combinar las condiciones para que el dispositivo funcione."



"Otro problema que no hemos estudiado es el efecto de no idealidad, que se refiere al abatimiento de la barrera. La barrera se reduce cuando un electrón sale del metal y se encuentra con una carga positiva igual y opuesta en la superficie del metal. Esta carga positiva atrae al electrón con una fuerza equivalente a la presencia de una carga positiva.

La teoría del abatimiento de la barrera se basa en la idea de que la carga imagen del electrón en la superficie del metal es equivalente a una carga positiva. La fuerza de atracción entre el electrón y la carga imagen es equivalente al cambio de energía electrónica.

La energía potencial de la carga imagen tiene un máximo en la posición X, que se puede calcular utilizando la forma de las dos energías. La aplicación de un campo eléctrico externo cambia la forma de la energía potencial y, por lo tanto, la posición del máximo.



"En la nanoelectrónica, es importante considerar la gravedad en los mecanismos de transporte. La corriente depende de la polarización aplicada y cambia la dependencia de la función y la constante. Esto no es un hecho nuevo, ya que recordamos que en el diodo corto, la región casi neutra dependía de la polarización aplicada.

La longitud de la región dependía de la polarización aplicada, lo que afectaba la corriente. El prefactor dependía de la anchura de la región. La corriente de polarización inversa no era constante, sino que dependía de la tensión.

En el efecto túnel, la probabilidad de atravesar la barrera es más significativa cuando la anchura de la barrera se reduce. La temperatura es fundamental en estos procesos, ya que puede esaltar o reducir los comportamientos que dependen de ella.

En la emisión termoiónica asistida por campo, la probabilidad de atravesar la barrera depende solo de la anchura de la barrera y no de la temperatura. La temperatura es clave para entender en qué condiciones estamos trabajando.



"Lo más importante es comprender los conceptos. La función fundamental de los libros es recordar lo que otros han hecho para poder pensar cosas nuevas. Existe una barrera alta que puede ser eficiente desde el punto de vista del contacto eléctrico, permitiendo un buen contacto eléctrico a pesar de la barrera elevada. Esto se debe al efecto túnel.

Las dependencias de la temperatura son complicadas. Me preguntaba si en la trattazione matemática se llega a una analogía similar a la del modelo de transmisión en un medio con un índice de refracción más alto, como la onda evanescente para el contagio.


"Imagina que lanzas una pelota en un campo de miel. La pelota se ralentiza y puede cambiar de dirección. En nanoelectrónica, esto se aplica a la combinación de mecanismos de transporte, como el efecto túnel y la difusión.

La capacidad de los materiales depende de la temperatura y la velocidad de crecimiento. La técnica de deposición química de vapor (CVD) se utiliza para crear materiales con propiedades específicas.

La selección de átomos se hace con un campo eléctrico y magnético. La deposición se realiza en un entorno de vacío para evitar colisiones con moléculas.

El curso tiene como objetivo proporcionar una visión global de los procesos de transporte en nanoelectrónica, incluyendo las relaciones funcionales y las propiedades de los materiales.

Para la deposición de óxido, se utilizan técnicas como la CVD a baja temperatura y alta velocidad de crecimiento. La limpieza del material se hace con sustancias químicas como HCL.

La deposición de fotoresist se hace con lámparas UV que convierten el polímero en soluble o insoluble. La remoción del óxido se hace con ácido fluorhídrico (BHF) diluido."



