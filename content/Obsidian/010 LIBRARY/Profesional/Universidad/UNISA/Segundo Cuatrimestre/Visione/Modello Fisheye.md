---
cards-deck: Profesional::Universidad::UNISA::Segundo Cuatrimestre::Visione
---


# Italiano


## Introduzione e Concetti di Base

### Tipi di Fotocamere

#### Teoria della Formazione delle Immagini in Sistemi Catadiottrici e Diottrici #tarjeta-anki 
**Sistemi Catadiottrici:**
- **Definizione:** Combinano specchi (riflessione) e lenti convenzionali per creare un sistema di visione omnidirezionale.
- **Tipi di Specchi:** Utilizzano specchi parabolici, iperbolici o ellittici.
  - **Specchio Parabolico:** Combinato con una telecamera ortografica, questo sistema fornisce un unico punto di vista efficace.
  - **Specchio Iperbolico/Ellittico:** Utilizzati con telecamere a prospettiva, possono anche ottenere un unico punto di vista efficace.
- **Vantaggi:** Ampio campo visivo, capacità di catturare panoramiche a 360 gradi.
- **Svantaggi:** Complessità nella calibrazione e possibili aberrazioni ottiche.
**Sistemi Diottrici (Telecamere Fisheye):**
- **Definizione:** Utilizzano lenti fisheye per catturare immagini con un ampio campo visivo senza bisogno di specchi.
- **Caratteristiche delle Lenti Fisheye:**
  - **Campo Visivo:** Maggiore di 180 gradi.
  - **Distorsione:** Alta distorsione radiale, dove le linee rette nel mondo reale si curvano significativamente nell'immagine.
- **Tipi di Proiezione:** 
  - **Proiezione Stereografica:** Mantiene gli angoli, comunemente utilizzata in astronomia.
  - **Proiezione Ortografica:** Proiezione perpendicolare al piano dell'immagine, utile in alcune applicazioni di visione artificiale.
  - **Proiezione Ecuangolare:** Mantiene la proporzione angolare, utile nella fotografia panoramica.
^1719822386468

#### Differenze tra Fotocamere Centrali e Non Centrali #tarjeta-anki 
**Fotocamere Centrali:**
- **Definizione:** Tutte le linee di vista passano per un unico punto, noto come il centro di proiezione.
- **Esempi:** Fotocamere convenzionali, alcune telecamere catadiottriche (con specchi parabolici e iperbolici).
- **Vantaggi:** Semplificazione nella modellazione matematica e calibrazione.
^1719822386482

**Fotocamere Non Centrali:**
- **Definizione:** Le linee di vista non convergono in un unico punto.
- **Esempi:** La maggior parte delle telecamere fisheye.
- **Sfide:** Modellazione matematica più complessa, richiede tecniche avanzate di calibrazione.

### Telecamera Fisheye
Le telecamere fisheye sono un tipo di fotocamera grandangolare progettata per catturare un campo visivo estremamente ampio, tipicamente di 180 gradi o più. Questo tipo di telecamera utilizza lenti fisheye, che presentano una caratteristica distorsione sferica, permettendo di coprire un'ampia scena in un'unica immagine. A differenza delle lenti convenzionali, le lenti fisheye non cercano di correggere la distorsione intrinseca, ma la utilizzano per catturare immagini panoramiche.

- Le telecamere fisheye sono un sottoinsieme delle telecamere omnidirezionali che utilizzano esclusivamente lenti per ottenere l'ampio campo visivo.

#### Applicazioni delle Telecamere Fisheye nell'Ingegneria e nella Visione Artificiale

1. **Sicurezza e Sorveglianza**: Sono ideali per la sorveglianza in spazi ampi, come parcheggi, magazzini e aree pubbliche, dove una singola telecamera può sostituire più telecamere convenzionali.
2. **Robotica e Veicoli Autonomi**: Sono cruciali nella navigazione e mappatura di robot e veicoli autonomi, fornendo informazioni visive complete sull'ambiente circostante.
3. **Realtà Virtuale e Aumentata**: Si utilizzano per catturare contenuti a 360 gradi che possono essere utilizzati in applicazioni di realtà virtuale e aumentata.
4. **Fotografia e Cinematografia**: Sono ideali per catturare scatti creativi e artistici che coprono un campo visivo estremamente ampio.
5. **Ispezione Industriale**: In ambienti industriali si utilizzano per ispezionare e monitorare aree di difficile accesso, come l'interno di tubi e contenitori.


#### Vantaggi e Svantaggi Telecamera Fisheye #tarjeta-anki 
**Vantaggi**:
- **Campo Visivo Esteso**: Permette di catturare una vista completa di 180 gradi o più in un'unica immagine.
- **Riduzione dei Costi e della Complessità**: Una singola telecamera fisheye può sostituire più telecamere convenzionali, semplificando l'installazione e riducendo i costi.
- **Versatilità**: Utile in una vasta gamma di applicazioni, dalla sorveglianza alla realtà virtuale.
**Svantaggi**:
- **Distorsione**: La distorsione radiale può complicare l'elaborazione delle immagini e l'interpretazione dei dati.
- **Risoluzione**: La risoluzione effettiva può essere inferiore rispetto alle telecamere convenzionali a causa della distribuzione dei pixel su un'area più ampia.
- **Correzione dell'Immagine**: Può essere necessario applicare tecniche di correzione dell'immagine per eliminare la distorsione in applicazioni che richiedono misure precise.
^1719822386487


## Principi di Funzionamento

### Proiezioni e distorsione #tarjeta-anki 
#### Proiezione Ecuangolare
![[Pasted image 20240620223114.png|400]]
Anche conosciuta come proiezione equidistante, è uno dei modi in cui le telecamere fisheye trasformano la luce entrante da una scena 3D a un'immagine 2D sul sensore della telecamera. Nella proiezione ecuangolare, la distanza radiale $r$ dal centro dell'immagine al punto proiettato nell'immagine è proporzionale all'angolo di incidenza $\theta$ del raggio di luce che arriva alla telecamera.
$$ r = k \cdot \theta $$
dove $k$ è una costante di proporzionalità che dipende dalle caratteristiche della lente e del sensore della telecamera.
- **Angolo di Incidenza $\theta$**: È l'angolo tra l'asse ottico della lente (una linea immaginaria che passa direttamente attraverso il centro della lente) e il raggio di luce che incide sulla lente.
- **Distanza Radiale $r$**: È la distanza dal centro dell'immagine (punto principale dell'immagine) al punto dove quel raggio di luce si proietta sul piano dell'immagine (sensore della telecamera).
##### Esempio
Immagina una telecamera fisheye puntata direttamente verso l'alto al centro di una piazza:
- **Centro dell'Immagine**: Un raggio di luce che incide perpendicolarmente al piano della lente, cioè direttamente verso il basso, ha un angolo di incidenza $\theta = 0$. La distanza radiale $r$ in questo caso sarà 0, e il punto si proietterà al centro dell'immagine.
- **Estremi dell'Immagine**: Un raggio di luce che incide da un angolo molto grande (vicino ai 180 gradi) sarà alla periferia dell'immagine. Qui, l'angolo $\theta$ è grande, e la distanza radiale $r$ sarà massima, posizionando il punto sul bordo dell'immagine.
#### Proiezione Stereografica
![[Pasted image 20240620223100.png|400]]
La proiezione stereografica è un altro modo di mappare la scena 3D all'immagine 2D, ed è particolarmente utile in applicazioni scientifiche e grafiche grazie alle sue proprietà geometriche. *In questa proiezione, gli angoli vengono mantenuti*, il che significa che le forme piccole si conservano meglio, anche se si verifica ancora distorsione.
Nella proiezione stereografica, la distanza radiale $r$ dal centro dell'immagine è correlata con l'angolo di incidenza $\theta$ mediante la seguente formula:
$$ r = 2f \cdot \tan\left(\frac{\theta}{2}\right) $$
dove $f$ è la distanza focale della lente.
##### Mantenimento degli Angoli
La caratteristica chiave della proiezione stereografica è che mantiene gli angoli locali. Questo significa che se hai due linee che si incrociano in un punto nello spazio reale, l'angolo tra queste linee nel mondo reale si preserva nell'immagine. In altre parole, la proiezione stereografica è conforme, cioè mantiene le forme locali degli oggetti.
##### Esempio
Considera una rete di linee rette disegnate su un piano che vengono osservate con una telecamera fisheye:
- **Proiezione Ecuangolare**: Le linee rette nel mondo reale si curveranno significativamente nell'immagine, e gli angoli tra esse possono apparire distorti, specialmente verso i bordi dell'immagine.
- **Proiezione Stereografica**: Anche se le linee rette si curveranno ancora, gli angoli tra le linee nel mondo reale si manterranno nell'immagine. Questo significa che se due linee si incrociano a 90 gradi nella realtà, si incroceranno a 90 gradi anche nell'immagine proiettata.
#### Distorsione Radiale
La distorsione radiale è un fenomeno intrinseco alle lenti fisheye a causa del loro ampio campo visivo. Si riferisce a come i punti alla periferia dell'immagine si distorcono più dei punti vicini al centro. Questa distorsione può essere descritta mediante un modello polinomiale che relaziona la distanza dal centro dell'immagine $r$ con la distanza radiale originale $r'$:
$$ r = r' \left( 1 + k_1 r'^2 + k_2 r'^4 + k_3 r'^6 + ... \right) $$
dove $k_1, k_2, k_3, ...$ sono i coefficienti di distorsione.
- **Caratteristiche**:
  - **Curvatura delle Linee**: Le linee rette nel mondo reale si curvano verso l'esterno man mano che si allontanano dal centro dell'immagine.
  - **Correzione dell'Immagine**: La distorsione radiale può essere corretta mediante algoritmi di elaborazione delle immagini che compensano questa curvatura, trasformando l'immagine in una vista più "naturale".
^1719822386491



#### Necessità delle Proiezioni e della Distorsione Radiale
Nella calibrazione di una telecamera fisheye, solitamente si seleziona una proiezione (ecuangolare o stereografica) basata sulle caratteristiche del sistema ottico e sull'applicazione specifica:
- **Proiezione Ecuangolare**: Si utilizza quando è richiesta una rappresentazione semplice e veloce dell'immagine, comune in applicazioni dove la distorsione radiale può essere gestita successivamente tramite software. È adatta per applicazioni generali di visione artificiale e sorveglianza.
- **Proiezione Stereografica**: Si sceglie quando è necessario preservare la geometria locale e gli angoli nell'immagine, essendo utile in applicazioni di cartografia, modellazione 3D e realtà virtuale, dove la precisione geometrica è cruciale.
Nella pratica, si utilizza solo uno di questi modelli di proiezione per un sistema specifico, basato sui requisiti dell'applicazione e sulle caratteristiche della lente.
La distorsione radiale viene sempre applicata, indipendentemente dal modello di proiezione selezionato, perché è una caratteristica intrinseca a tutte le lenti fisheye. Il modello di distorsione radiale si utilizza per correggere la distorsione introdotta dalla lente per ottenere una rappresentazione più precisa dell'immagine.
#### Processo di Conversione del Mondo Reale all'Immagine della Lente
##### 1. Coordinate nel Mondo Reale
Immaginiamo un punto $P$ nello spazio 3D con coordinate $(X, Y, Z)$.
##### 2. Trasformazione alle Coordinate della Telecamera
Prima, convertiamo le coordinate del punto $P$ dal sistema di riferimento del mondo al sistema di riferimento della telecamera mediante una trasformazione di rotazione e traslazione. Se la telecamera è nella posizione $(X_c, Y_c, Z_c)$ e ha un'orientazione data dalla matrice di rotazione $R$:
$$ P_{c} = R \cdot (P - C) $$
dove $P_{c} = (X_c, Y_c, Z_c)$ sono le coordinate del punto nel sistema di riferimento della telecamera.
##### 3. Proiezione del Punto sul Piano dell'Immagine
Ora proiettiamo il punto $P_{c}$ sul piano dell'immagine utilizzando la proiezione ecuangolare o stereografica.
- **Proiezione Ecuangolare**:
$$ r = k \cdot \theta $$

dove $\theta$ è l'angolo di incidenza, calcolato come:

$$ \theta = \arctan\left(\frac{\sqrt{X_c^2 + Y_c^2}}{Z_c}\right) $$

La distanza radiale $r$ sul piano dell'immagine è proporzionale a questo angolo.

- **Proiezione Stereografica**:

$$ r = 2f \cdot \tan\left(\frac{\theta}{2}\right) $$

dove $f$ è la distanza focale della lente e $\theta$ è l'angolo di incidenza calcolato allo stesso modo.

##### 4. Applicazione della Distorsione Radiale

Il punto proiettato sul piano dell'immagine $(x, y)$ sperimenta una distorsione radiale. Il modello di distorsione radiale può essere espresso come:

$$ r' = r \left( 1 + k_1 r^2 + k_2 r^4 + k_3 r^6 + ... \right) $$

dove $r$ è la distanza radiale originale e $r'$ è la distanza radiale distorta. I coefficienti $k_1, k_2, k_3, ...$ descrivono il grado di distorsione.

##### 5. Trasformazione Affine

Infine, applichiamo una trasformazione affine per adattare l'immagine al piano del sensore della telecamera. Questa trasformazione include scalatura, rotazione e traslazione all'interno del piano dell'immagine:

$$ \begin{pmatrix} u \\ v \end{pmatrix} = A \cdot \begin{pmatrix} x' \\ y' \end{pmatrix} + t $$

dove $A$ è una matrice di trasformazione e $t$ è un vettore di traslazione.

#### Riassunto del Flusso di Coordinate

1. **Coordinate del Mondo Reale** $(X, Y, Z)$
2. **Trasformazione di Telecamera** $(X_c, Y_c, Z_c)$
3. **Proiezione** (ecuangolare o stereografica) per ottenere $r$
4. **Applicazione della Distorsione Radiale** per ottenere $r'$
5. **Trasformazione Affine** per ottenere le coordinate finali sul sensore della telecamera $(u, v)$




## Modello di Telecamera Omnidirezionale
### Introduzione #tarjeta-anki 
![[Pasted image 20240617101922.png]]
- In una telecamera convenzionale, ogni raggio di luce che passa per il centro ottico si interseca con il piano dell'immagine in un unico punto. Tuttavia, quando l'angolo di visione è maggiore di 180°, una linea retta (raggio) può intersecare il piano dell'immagine in più di un punto. Una linea che passa per il centro ottico può avere due punti diversi della scena che si proiettano nell'immagine. Ad esempio, nella Figura 2c, i raggi p e -p rappresentano punti diversi sulla stessa linea che intersecano il piano dell'immagine in luoghi distinti.
- In una telecamera omnidirezionale, entrambi i punti possono essere visti simultaneamente, il che complica la rappresentazione in un piano di immagine bidimensionale.
- Non è possibile rappresentare la proiezione di tutti i punti della scena X in un unico piano di immagine senza ambiguità.
- *Soluzione:*
    - Per risolvere questa ambiguità e rappresentare correttamente i punti della scena, si utilizza una rappresentazione tridimensionale anziché un piano bidimensionale. Ogni raggio di luce è rappresentato come un vettore unitario nello spazio tridimensionale $\mathbb{R}^3$.
    - **Vantaggio**: Questa rappresentazione permette di descrivere in modo univoco e preciso la direzione di ogni raggio di luce, indipendentemente da quanti punti della scena si proiettano sullo stesso raggio.
^1719822386496


### Piani #tarjeta-anki 
Nel modello generale di telecamera centrale, identifichiamo due riferimenti distinti: il piano dell'immagine della telecamera $(u', v')$ e il piano del sensore $(u'', v'')$. Il piano dell'immagine della telecamera coincide con il CCD della telecamera, dove i punti sono espressi in coordinate di pixel. Il piano del sensore è un piano ipotetico ortogonale all'asse dello specchio, con l'origine situata all'intersezione piano-asse.
![[Pasted image 20240617183213.png]]
Nella Figura 1, sono mostrati i due piani di riferimento nel caso di un sistema catadiottrico. Nel caso diottrico, il segno di $u''$ si invertirebbe a causa dell'assenza di una superficie riflettente. Tutte le coordinate saranno espresse nel sistema di coordinate posto in $O$, con l'asse $z$ allineato con l'asse del sensore (vedi Fig. 1a).
^1719822386500



### Acquisizione del Modello 
![[Pasted image 20240617101938.png]] #tarjeta-anki 
#### Immagine nel piano del sensore (a):
- $u''$ È il punto nel piano del sensore della telecamera. Questo è il punto fisico dove la luce catturata dalla lente della telecamera incide sul sensore. Questo punto è in coordinate metriche.
#### Immagine digitalizzata (b):
   - $u'$ È il punto nell'immagine digitalizzata. Questo punto è il risultato della conversione delle coordinate metriche del piano del sensore in coordinate in pixel, cioè l'immagine che può essere processata digitalmente.
   - L'immagine digitalizzata è quella che otteniamo direttamente dal sensore della telecamera dopo la sua elaborazione iniziale.
#### Trasformazione Affine
- La trasformazione affine relaziona il punto nel piano del sensore $u''$ con il punto nell'immagine digitalizzata $u'$. La trasformazione affine è una combinazione di scalatura, rotazione e traslazione.
$$ Au' + t = u''$$
	- Dove $A$ è una matrice 2x2 e $t$ è un vettore 2x1.
#### Trasformazione da ellisse a cerchio (c):
- A causa delle distorsioni della lente, il campo visivo della telecamera può apparire come un'ellisse nell'immagine digitalizzata. Per facilitare l'elaborazione, questa ellisse viene trasformata in un cerchio. Questa trasformazione può includere una scalatura e una rotazione aggiuntive.
   - Questo passaggio è cruciale per la calibrazione, poiché semplifica la geometria dell'immagine. Questo passaggio è chiamato pre-calibrazione.
#### Punti 3D (d):
Proponiamo il modello di una telecamera omnidirezionale nella forma:
$$\exists \alpha > 0 : \alpha g(Au + t) = PX, $$
che assegna un punto $X \in \mathbb{R}^4$ della scena alla sua immagine digitalizzata $u'$ mediante una matrice di proiezione prospettica $P \in \mathbb{R}^{3 \times 4}$, un cambio di sistema di coordinate nell'immagine $A$, $t$, e una funzione non lineare $g: \mathbb{R}^2 \rightarrow \mathbb{R}^3$ definita nel piano del sensore.
^1719822386510

   - **Vettore $g(Au' + t)$**: Rappresenta la proiezione di un punto nell'immagine digitalizzata a un vettore tridimensionale. Questa funzione non lineare $g$ trasforma le coordinate del punto nell'immagine digitalizzata per rappresentare il raggio di luce corrispondente in un sistema di coordinate 3D.
#### Equazione finale
La relazione tra un punto pixel $u'$ e un punto della scena $X$ è:

$$
\lambda \cdot p = \lambda \cdot g(u'') = \lambda \cdot g(Au' + t) = PX, \quad \lambda > 0
$$
dove $X \in \mathbb{R}^4$ è espresso in coordinate omogenee e $P \in \mathbb{R}^{3 \times 4}$ è la matrice di proiezione in prospettiva.




### Costruzione della Mappatura $f$ #tarjeta-anki 
La figura 4 mostra come si costruisce la mappatura $f$ dal piano del sensore alla retina sferica.
![[Pasted image 20240617111244.png]]
Il diagramma mostra la costruzione della funzione di mappatura $f$ dal piano del sensore $\pi$ alla retina sferica $\rho$. Il punto $(u'', v'', 1)^T$ nel piano dell'immagine $\pi$ viene trasformato da $f(.)$ a $(u'', v'', w'')^T$, poi viene normalizzato a $(p'', q'', s'')^T$ con lunghezza unitaria, e così si proietta sulla sfera $\rho$.
   - Il piano del sensore è dove la luce catturata dalla lente si proietta inizialmente. In questo piano, ogni punto $(u'', v'')$ rappresenta una posizione nell'immagine catturata dal sensore.
   - Dopo aver applicato la funzione $f$, il punto $(u'', v'', w'')$ viene normalizzato per avere lunghezza unitaria, risultando nel punto $(p'', q'', s'')$.
   - Questo punto normalizzato si proietta sulla retina sferica $\rho$, che è una rappresentazione tridimensionale dell'immagine.
#### Osservazione
Un raggio non distorto rappresentato dal vettore unitario $p$ può essere espresso come:
$$ p'' = k g(u'', a'', b'') = k \begin{pmatrix} u'' \\ v'' \\ w'' \end{pmatrix} = k \begin{pmatrix} A u' + t \\ f(u'', a'', b'') \end{pmatrix}, $$
dove:
$$ f(u'', a'', b'') = \frac{r''}{\tan \theta} = \frac{r''}{\tan \left( \frac{a''r''}{1 + b''r''^2} \right)}, \quad k > 0. $$
L'equazione precedente cattura la relazione tra il punto $u$ nell'immagine digitalizzata e il vettore $p$ che emana dal centro ottico verso un punto della scena $X$.
^1719822386516




## Calibrazione
### Introduzione
Sia l'equazione: 
$$\lambda \cdot p = \lambda \cdot g(u'') = \lambda \cdot g(Au' + t) = PX, \quad \lambda > 0$$
La calibrazione della telecamera si completa determinando i parametri della trasformazione affine $A$ e $t$, e la funzione non lineare $g$, in modo che tutti i vettori $g(Au' + t)$ soddisfino la geometria epipolare.

La funzione g ha la forma
$$\mathbf{g}(u'', v'') = (u'', v'', f(u'', v''))^T $$
dove $f(u)$ è simmetrica rispetto a un punto $(u_0, v_0)$. Il raggio che passa per $(u_0, v_0)$ è l'asse ottico della telecamera.
La funzione $f$ può avere diverse forme determinate dalla costruzione della lente. Ad esempio, il modello $\theta = ar$ si avvicina alla realtà per la lente fisheye Nikon FC–E8, dove $a$ è un parametro, $\theta$ è l'angolo tra un raggio e l'asse ottico, $r = \sqrt{u^2 + v^2}$ è il raggio di un punto nel piano del sensore rispetto a $(u_0, v_0)$, e si verifica $f(u) = \frac{r}{\tan \theta}$. Un modello più preciso richiede una parte non lineare. Utilizziamo il modello di divisione:

$$ \theta = \frac{ar}{1 + br^2}, \quad r = \frac{a - \sqrt{a^2 - 4b\theta^2}}{2b\theta}, $$
dove $b$ è un parametro aggiuntivo.



### $f$ generico #tarjeta-anki 
Invece di utilizzare un modello specifico per il sensore in uso, optiamo per applicare un modello parametrico generalizzato di $f$, adatto a diversi tipi di sensori. La ragione di ciò è che vogliamo che questo modello compensi qualsiasi disallineamento tra il punto focale dello specchio (o della lente fisheye) e il centro ottico della telecamera. Inoltre, desideriamo che la nostra funzione generalizzata si adatti approssimativamente ai sensori dove la proprietà di un solo punto di vista non si verifica esattamente (ad esempio, telecamere fisheye generiche). Nel nostro lavoro precedente, abbiamo proposto la seguente forma polinomica per $f$:
^1719822386520

$$
f(u'', v'') = a_0 + a_1\rho' +a_2\rho^2 + \ldots + a_N\rho^N
$$
dove i coefficienti $a_i$ e il grado polinomico $N$ sono i parametri da determinare mediante la calibrazione. Pertanto, l'equazione (1) può essere riscritta come:
![[Pasted image 20240617184306.png]]
Come menzionato nell'introduzione, in questo articolo vogliamo ridurre il numero di parametri di calibrazione. Questo si può ottenere osservando che tutte le definizioni di $f$, che sono valide per specchi iperbolici e parabolici o telecamere fisheye, soddisfano sempre quanto segue:
$$
\left. \frac{df}{d\rho} \right|_{\rho=0} = 0
$$
Questo ci permette di assumere $a_1 = 0$, e così, l'equazione (3) può essere riscritta come:
$$
f(u'', v'') = a_0 + a_2\rho^

2 + \ldots + a_N\rho^N
$$


### Procedura di calibrazione 
Per calibrazione di una telecamera omnidirezionale intendiamo la stima dei parametri $$A, t, a_0, a_2, ..., a_N$$
#### Stima di A e t #tarjeta-anki 
Per stimare A e t, introduciamo un metodo che si basa su una procedura iterativa. 
1. Si inizia configurando A come matrice unitaria. I suoi elementi verranno stimati utilizzando un raffinamento non lineare.
2. Assumiamo che il centro dell'immagine omnidirezionale O coincida con il centro dell'immagine Ic, cioè, $O_c = I_c$, e quindi $t = α(O_c − I_c) = 0$. 
	- Allora assumiamo che $u' ⋅ α = u''$. Così, sostituendo questa relazione in (4) e utilizzando (6), otteniamo la seguente equazione di proiezione:
![[Pasted image 20240617220324.png]]
	- Dove u' e v' sono le coordinate di pixel di un'immagine rispetto al centro dell'immagine, e ρ' è la distanza euclidea. 
- Inoltre, si noti che il fattore α può essere integrato direttamente nel fattore di profondità λ; pertanto, è necessario stimare solo N parametri (a0, a2, ..., aN).
##### Osservazioni
- Per A, l'assunzione di essere unitaria è ragionevole perché l'eccentricità del bordo esterno nell'immagine omnidirezionale è solitamente vicina a 0. 
- Al contrario, Oc può essere molto lontano dal centro dell'immagine Ic. Il metodo che discuteremo non si preoccupa di questo.
^1719822386553


#### Soluzione per i Parametri Estrinseci della Telecamera #tarjeta-anki 
Durante la procedura di calibrazione, viene mostrato un modello piano di geometria nota in diverse posizioni sconosciute, che sono correlate con il sistema di coordinate del sensore tramite una rotazione $R = [r_1, r_2, r_3]$ e una traslazione t, chiamati parametri estrinseci. 
- Sia $I^i$ un'immagine osservata del modello di calibrazione $M_{ij}=[X_{ij},Y_{ij},Z_{ij}]$ le coordinate 3D dei suoi punti nel sistema di coordinate del modello, e $m_{ij}=[u_{ij},v_{ij}]$ le coordinate di pixel corrispondenti nel piano dell'immagine. 
- Poiché assumiamo che il modello sia piano, con la perdita della generalità abbiamo $Z_{ij}=0$. Quindi, l'equazione (7) diventa:
![[Pasted image 20240617221132.png]]
Pertanto, per risolvere la calibrazione della telecamera, il parametro estrinseco deve essere determinato per ogni posizione del modello di calibrazione.
Eliminiamo la dipendenza dalla scala di profondità moltiplicando entrambi i lati dell'equazione (8) vettorialmente per Pi.
![[Pasted image 20240617221912.png]]
Da (9), abbiamo che ogni punto p, del modello contribuisce con tre equazioni omogenee.
![[Pasted image 20240617221943.png]]
- Qui sono conosciuti $X_j, Y_j$ e $Z_j$, così come $u_j,v_j$. Inoltre, si noti che solo (10.3) è lineare nelle incognite $r_{11},r_{12},r_{21},r_{22},t_1,t_2,..$. 
- Accumulando tutte le voci sconosciute di (10.3) in un vettore, riscriviamo l'equazione (10.3) per L punti del modello di calibrazione come un sistema di equazioni lineari.
![[Pasted image 20240617222139.png]]
- Una stima lineare di H può essere ottenuta minimizzando il criterio dei minimi quadrati $min||M ⋅ H||^2$, soggetto a $||H||^2 = 1$. Questo si ottiene utilizzando la decomposizione ai valori singolari (SVD). 
- La soluzione di (11) è conosciuta fino a un fattore di scala, che può essere determinato in modo univoco poiché i vettori $r_1$ e $r_2$ sono ortonormali. A causa dell'ortonormalità, le voci sconosciute $r_{31}$ e $r_{32}$ possono anche essere calcolate in modo univoco.
>Per riassumere, il primo passo della calibrazione consente di trovare i parametri estrinseci $r_{11}, r_{12}, r_{21}, r_{22}, r_{31}, r_{32}$ e $t_1, t_2$ per ogni posizione del modello di calibrazione, eccetto il parametro di traslazione $t_3$. Questo parametro verrà calcolato nel passaggio successivo, che riguarda la stima della funzione di proiezione dell'immagine.
^1719822386558


#### Soluzione per i Parametri Intrinseci della Telecamera #tarjeta-anki 
Sostituiamo i valori stimati (estrinseci) nelle equazioni (10.1) e (10.2), e risolviamo i parametri intrinseci della telecamera $a_0, a_2, ..., a_N$ che descrivono la forma della funzione di immagine $\mathbf{g}$. 
- Allo stesso tempo, calcoliamo anche il $t_3$ sconosciuto per ogni posizione del modello di calibrazione. 
Come fatto in precedenza, accumuliamo tutte le voci sconosciute di (10.1) e (10.2) in un vettore e riscriviamo le equazioni come un sistema di equazioni lineari. Ma ora, incorporiamo tutte le osservazioni K della scacchiera di calibrazione. Otteniamo il seguente sistema:
![[Pasted image 20240617222921.png]]
dove $A_i, B_i, C_i$ e $D_i$ sono matrici che contengono le coordinate conosciute del modello e i parametri stimati.
Infine, la soluzione dei minimi quadrati del sistema sovradeterminato si ottiene utilizzando la pseudoinversa. Pertanto, ora sono disponibili i parametri intrinseci $a_0, a_2, ..., a_N$ che descrivono il modello.
Per calcolare il miglior grado polinomiale N, iniziamo con N=2. Poi, aumentiamo N in passi unitari e calcoliamo il valore medio dell'errore di riproiezione di tutti i punti di calibrazione. La procedura si interrompe quando si trova un errore minimo.
^1719822386562


#### Raffinamento Lineare dei Parametri Intrinseci ed Estrinseci #tarjeta-anki 
Questo raffinamento viene eseguito tramite una minimizzazione lineare. La struttura dell'algoritmo di raffinamento lineare è la seguente:
1. Il primo passo utilizza il modello di telecamera $(a_0, a_2, ..., a_N)$ stimato nel passo precedente, e ricalcola tutti i parametri estrinseci risolvendo congiuntamente le equazioni (10.1), (10.2) e (10.3). 
	- Il problema porta a un sistema lineare omogeneo, che può essere risolto, fino a un fattore di scala, utilizzando SVD. 
	- Poi, il fattore di scala viene determinato in modo univoco sfruttando l'ortonormalità tra i vettori $r_1$ e $r_2$.
2. Nella seconda fase, i parametri estrinseci ricalcolati nel passo precedente vengono sostituiti nelle equazioni (10.1) e (10.2) per affinare ulteriormente il modello intrinseco della telecamera.
	- Il problema porta a un sistema lineare, che può essere risolto come di consueto utilizzando la pseudoinversa.
^1719822386566


#### Rilevamento Iterativo del Centro #tarjeta-anki 
Vogliamo che la nostra suite di calibrazione sia il più automatica possibile, e pertanto, desideriamo la capacità di identificare il centro dell'immagine omnidirezionale Oc anche quando il bordo esterno del sensore non è visibile nell'immagine.
- Si noti che la nostra procedura di calibrazione stima correttamente il modello parametrico intrinseco solo se Oc è preso come origine delle coordinate dell'immagine. 
- Se non è così, proiettando di nuovo i punti 3D della scacchiera nell'immagine, osserveremmo un grande errore di riproiezione rispetto ai punti di calibrazione (vedi Figura 2a).
- Motivati da questa osservazione, eseguiamo molti test della nostra calibrazione per diverse posizioni del centro, e per ogni test, calcoliamo la Somma degli Errori di Riproiezione Quadrati (SSRE). Di conseguenza, verifichiamo che la SSRE ha sempre un minimo globale nella posizione corretta del centro.
- Questo risultato ci porta a una ricerca iterativa del centro Oc, che si interrompe quando la differenza tra due posizioni potenziali del centro è inferiore a una certa frazione di pixel ε (stabiliamo ragionevolmente ε = 0,5 pixel):
1. In ogni passaggio di questa ricerca iterativa, si campiona uniformemente una regione dell'immagine in un certo numero di punti.
2. Per ciascuno di questi punti, si esegue la calibrazione utilizzando quel punto come posizione potenziale del centro, e si calcola la SSRE.
3. Il punto che dà la SSRE minima è assunto come centro potenziale.
4. La ricerca continua raffinando il campionamento nella regione intorno a quel punto, e i passaggi 1, 2 e 3 si ripetono fino a che non si soddisfa la condizione di arresto.
Si noti che il costo computazionale di questa ricerca iterativa è così basso che si ferma solo dopo 3 secondi.
^1719822386571


#### Raffinamento Non Lineare
La soluzione lineare data nelle sottosezioni precedenti A, B e C si ottiene minimizzando una distanza algebrica, che non è fisicamente significativa. Per questo, scegliamo di raffinarla tramite inferenza di massima verosimiglianza.
Supponiamo di avere K immagini di un piano modello, ciascuna contenente L punti di angolo. Poi, supponiamo che i punti dell'immagine siano corrotti da rumore indipendente e distribuito in modo identico. Allora, la stima di massima verosimiglianza può essere ottenuta minimizzando il seguente funzionale:
$$ E = \sum_{i=1}^K \sum_{j=1}^L ||m_{ij} - m(\hat{R}_i, T_i, A,O_c, a_0, a_2, ..., a_N, M_j)||^2 $$

dove $m(\hat{R}_i, T_i, A,O_c, a_0, a_2, ..., a_N, M_j)$ è la proiezione del punto $M_j$ del piano i secondo l'equazione (1). $R_i$ e $T_i$ sono le matrici di rotazione e traslazione di ogni posa del piano; $R_i$ è parametrizzato tramite un vettore di 3 parametri relativi a $R_i$ dalla formula di Rodrigues. Si noti che ora incorporiamo nel funzionale sia la matrice affine A che il centro dell'immagine omnidirezionale Oc.

Minimizzando il funzionale definito in (14), calcoliamo effettivamente i parametri intrinseci ed estrinseci che minimizzano l'errore di riproiezione. 

Per accelerare la convergenza, decidiamo di dividere la minimizzazione non lineare in due passaggi. 
- Il primo affina i parametri estrinseci, ignorando gli intrinseci. 
- Poi, il secondo passo utilizza i parametri estrinseci appena stimati e affina gli intrinseci.
- Eseguendo molte simulazioni, abbiamo scoperto che questa divisione non influisce sul risultato finale rispetto a una minimizzazione globale.

Per minimizzare (14), utilizziamo l'algoritmo di Levenberg-Marquardt, come implementato dalla funzione $lsqnonlin$ di Matlab. L'algoritmo richiede una stima iniziale dei parametri intrinseci ed estrinseci. Questi parametri vengono ottenuti utilizzando la tecnica lineare descritta nelle sottosezioni precedenti. Come prima stima per A, utilizziamo la matrice unitaria, mentre per Oc utilizziamo la posizione stimata tramite la procedura iterativa spiegata nella sottosezione D.


## Calibrazione in MatLab #tarjeta-anki 
Per eliminare la distorsione della lente di un'immagine fisheye, è possibile rilevare un modello di calibrazione a scacchiera e poi calibrare la telecamera. È possibile trovare i punti della scacchiera utilizzando le funzioni *detectCheckerboardPoints* e *generateCheckerboardPoints*. La funzione *estimateFisheyeParameters* utilizza i punti rilevati e restituisce l'oggetto *fisheyeParameters* che contiene i parametri intrinseci ed estrinseci di una telecamera fisheye. È possibile utilizzare l'oggetto *fisheyeCalibrationErrors* per verificare la precisione della calibrazione.



### Procedura
- Eliminare la distorsione della lente di un'immagine fisheye rilevando un modello di calibrazione a scacchiera e calibrando la telecamera. Quindi, visualizzare i risultati.
1. Raccogliere un insieme di immagini di calibrazione a scacchiera.
``` Python
images = imageDatastore('calibrationImages');
```
2. Rilevare il modello di calibrazione dalle immagini. L'argomento *'PartialDetections' Name-Value* è impostato su true per impostazione predefinita, consentendo il rilevamento di scacchiere parziali.
``` Python
[imagePoints,boardSize] = detectCheckerboardPoints(images.Files, 'HighDistortion', true);
```
3. Generare coordinate del mondo per gli angoli dei quadrati della scacchiera.
``` Python
squareSize = 20; % millimeters
worldPoints = generateCheckerboardPoints(boardSize,squareSize);
```
4. Stimare i parametri di calibrazione della telecamera fisheye basati sui punti immagine e sui punti del mondo. Utilizzare la prima immagine per ottenere le dimensioni dell'immagine.
``` Python
I = readimage(images,10); 
imageSize = [size(I,1) size(I,2)];
params = estimateFisheyeParameters(imagePoints,worldPoints,imageSize);
```
5. Rimuovere la distorsione della lente dalla prima immagine I e visualizzare i risultati.
``` Python
J1 = undistortFisheyeImage(I,params.Intrinsics);
figure
imshowpair(I,J1,'montage')
title('Immagine Originale (sinistra) vs. Immagine Correggita (destra)')
J2 = undistortFisheyeImage(I,params.Intrinsics,'OutputView','same', 'ScaleFactor', 0.2);
figure
imshow(J2)
```


# Espagnolo
## Introducción y Conceptos Básicos

### Tipos de camaras

#### Teoría de la Formación de Imágenes en Sistemas Catadióptricos y Dioptricos

**Sistemas Catadióptricos:**
- **Definición:** Combinan espejos (reflexión) y lentes convencionales para crear un sistema de visión omnidireccional.
- **Tipos de Espejos:** Utilizan espejos parabólicos, hiperbólicos o elípticos.
  - **Espejo Parabólico:** Combinado con una cámara ortográfica, este sistema proporciona un único punto de vista efectivo.
  - **Espejo Hiperbólico/Elíptico:** Utilizados con cámaras de perspectiva, también pueden lograr un único punto de vista efectivo.
- **Ventajas:** Amplio campo de visión, capacidad para capturar panorámicas de 360 grados.
- **Desventajas:** Complejidad en la calibración y posibles aberraciones ópticas.

**Sistemas Dioptricos (Cámaras Fisheye):**
- **Definición:** Utilizan lentes de ojo de pez para capturar imágenes con un amplio campo de visión sin necesidad de espejos.
- **Características de la Lente Fisheye:**
  - **Campo de Visión:** Mayor de 180 grados.
  - **Distorsión:** Alta distorsión radial, donde las líneas rectas en el mundo real se curvan significativamente en la imagen.
- **Tipos de Proyección:** 
  - **Proyección Estereográfica:** Mantiene los ángulos, comúnmente utilizada en astronomía.
  - **Proyección Ortográfica:** Proyección perpendicular al plano de la imagen, útil en ciertas aplicaciones de visión por computadora.
  - **Proyección Ecuangular:** Mantiene la proporción angular, útil en fotografía panorámica.

#### Diferencias entre Cámaras Centrales y No Centrales

**Cámaras Centrales:**
- **Definición:** Todas las líneas de visión pasan por un único punto, conocido como el centro de proyección.
- **Ejemplos:** Cámaras convencionales, algunas cámaras catadióptricas (con espejos parabólicos e hiperbólicos).
- **Ventajas:** Simplificación en la modelización matemática y calibración.

**Cámaras No Centrales:**
- **Definición:** Las líneas de visión no convergen en un único punto.
- **Ejemplos:** La mayoría de las cámaras fisheye.
- **Desafíos:** Modelización matemática más compleja, requiere técnicas avanzadas de calibración.


### Camara Fisheye

Las cámaras fisheye son un tipo de cámara de gran angular diseñadas para capturar un campo de visión extremadamente amplio, típicamente de 180 grados o más. Este tipo de cámara utiliza lentes de ojo de pez, que presentan una distorsión esférica característica, permitiendo abarcar una amplia escena en una sola imagen. A diferencia de las lentes convencionales, las lentes fisheye no intentan corregir la distorsión inherente, sino que la utilizan para capturar imágenes panorámicas.

- Las cámaras fisheye son un subconjunto de las cámaras omnidireccionales que utilizan únicamente lentes para lograr el amplio campo de visión.

#### Aplicaciones de Cámaras Fisheye en la Ingeniería y la Visión por Computadora

1. **Seguridad y Vigilancia**: Son ideales para la vigilancia en espacios amplios, como estacionamientos, almacenes y áreas públicas, donde una sola cámara puede reemplazar múltiples cámaras convencionales.
2. **Robótica y Vehículos Autónomos**: Son cruciales en la navegación y mapeo de robots y vehículos autónomos, proporcionando información visual completa del entorno circundante
3. **Realidad Virtual y Aumentada**: Se utilizan para capturar contenido de 360 grados que luego se puede utilizar en aplicaciones de realidad virtual y aumentada
4. **Fotografía y Cinematografía**: Son ideales para capturar tomas creativas y artísticas que abarcan un campo de visión extremadamente amplio.
5. **Inspección Industrial**: En entornos industriales se utilizan para inspeccionar y monitorear áreas de difícil acceso, como el interior de tuberías y recipientes.


#### Ventajas y Desventajas
**Ventajas**:
- **Campo de Visión Extenso**: Permite capturar una vista completa de 180 grados o más en una sola imagen.
- **Reducción de Costo y Complejidad**: Una sola cámara fisheye puede reemplazar múltiples cámaras convencionales, simplificando la instalación y reduciendo costos.
- **Versatilidad**: Útil en una amplia gama de aplicaciones, desde vigilancia hasta realidad virtual.
**Desventajas**:
- **Distorsión**: La distorsión radial puede complicar el procesamiento de imágenes y la interpretación de datos.
- **Resolución**: La resolución efectiva puede ser menor en comparación con las cámaras convencionales debido a la distribución de píxeles sobre un área más grande.
- **Corrección de Imagen**: Puede ser necesario aplicar técnicas de corrección de imagen para eliminar la distorsión en aplicaciones que requieren medidas precisas.



## Principios de Funcionamiento

### Proyecciones y distorcion

#### Proyección Ecuangular
![[Pasted image 20240620223114.png|400]]
También conocida como proyección equidistante, es una de las formas en que las cámaras fisheye transforman la luz entrante desde una escena 3D a una imagen 2D en el sensor de la cámara. En la proyección ecuangular, la distancia radial $r$ desde el centro de la imagen hasta el punto proyectado en la imagen es proporcional al ángulo de incidencia $\theta$ del rayo de luz que llega a la cámara.

$$ r = k \cdot \theta $$


donde $k$ es una constante de proporcionalidad que depende de las características de la lente y el sensor de la cámara.
- **Ángulo de Incidencia $\theta$**: Es el ángulo entre el eje óptico de la lente (una línea imaginaria que pasa directamente a través del centro de la lente) y el rayo de luz que incide en la lente.
- **Distancia Radial $r$**: Es la distancia desde el centro de la imagen (punto principal de la imagen) hasta el punto donde ese rayo de luz se proyecta en el plano de la imagen (sensor de la cámara).

##### Ejemplo

Imagina una cámara fisheye apuntando directamente hacia arriba en el centro de una plaza:

- **Centro de la Imagen**: Un rayo de luz que incide perpendicularmente al plano de la lente, es decir, directamente hacia abajo, tiene un ángulo de incidencia $\theta = 0$. La distancia radial $r$ en este caso será 0, y el punto se proyectará en el centro de la imagen.
- **Extremos de la Imagen**: Un rayo de luz que incide desde un ángulo muy grande (cerca de 180 grados) estará en la periferia de la imagen. Aquí, el ángulo $\theta$ es grande, y la distancia radial $r$ será máxima, colocando el punto en el borde de la imagen.


#### Proyección Estereográfica
![[Pasted image 20240620223100.png|400]]
La proyección estereográfica es otra forma de mapear la escena 3D a la imagen 2D, y es especialmente útil en aplicaciones científicas y gráficas debido a sus propiedades geométricas. *En esta proyección, los ángulos se mantienen*, lo que significa que las formas pequeñas se conservan mejor, aunque aún se produce distorsión.
En la proyección estereográfica, la distancia radial $r$ desde el centro de la imagen se relaciona con el ángulo de incidencia $\theta$ mediante la siguiente fórmula:

$$ r = 2f \cdot \tan\left(\frac{\theta}{2}\right) $$

donde $f$ es la distancia focal de la lente.
##### Mantenimiento de Ángulos

La característica clave de la proyección estereográfica es que mantiene los ángulos locales. Esto significa que si tienes dos líneas que se cruzan en un punto en el espacio real, el ángulo entre estas líneas en el mundo real se preserva en la imagen. En otras palabras, la proyección estereográfica es conforme, es decir, mantiene las formas locales de los objetos.

##### Ejemplo

Considera una red de líneas rectas dibujadas en un plano que se observan con una cámara fisheye:

- **Proyección Ecuangular**: Las líneas rectas en el mundo real se curvarán significativamente en la imagen, y los ángulos entre ellas pueden parecer distorsionados, especialmente hacia los bordes de la imagen.
- **Proyección Estereográfica**: Aunque las líneas rectas aún se curvarán, los ángulos entre las líneas en el mundo real se mantendrán en la imagen. Esto significa que si dos líneas se cruzan en 90 grados en la realidad, también se cruzarán en 90 grados en la imagen proyectada.

#### Distorsión Radial
La distorsión radial es un fenómeno inherente a las lentes fisheye debido a su amplio campo de visión. Se refiere a cómo los puntos en la periferia de la imagen se distorsionan más que los puntos cercanos al centro. Esta distorsión puede describirse mediante un modelo polinomial que relaciona la distancia desde el centro de la imagen $r$ con la distancia radial original $r'$:

$$ r = r' \left( 1 + k_1 r'^2 + k_2 r'^4 + k_3 r'^6 + ... \right) $$

donde $k_1, k_2, k_3, ...$ son los coeficientes de distorsión.

- **Características**:
  - **Curvatura de Líneas**: Las líneas rectas en el mundo real se curvan hacia afuera a medida que se alejan del centro de la imagen.
  - **Corrección de Imagen**: La distorsión radial puede corregirse mediante algoritmos de procesamiento de imágenes que compensan esta curvatura, transformando la imagen de vuelta a una vista más "natural".


#### Necesidad de las Proyecciones y la Distorsión Radial

En la calibración de una cámara fisheye, usualmente se selecciona una proyección (ecuangular o estereográfica) basada en las características del sistema óptico y la aplicación específica:

- **Proyección Ecuangular**: Se utiliza cuando se requiere una representación simple y rápida de la imagen, común en aplicaciones donde la distorsión radial puede ser manejada posteriormente mediante software. Es adecuada para aplicaciones generales de visión por computadora y vigilancia.
- **Proyección Estereográfica**: Se elige cuando se necesita preservar la geometría local y los ángulos en la imagen, siendo útil en aplicaciones de cartografía, modelado 3D y realidad virtual, donde la precisión geométrica es crucial.

En la práctica, solo se utiliza uno de estos modelos de proyección para un sistema específico, basado en los requisitos de la aplicación y las características de la lente.

La distorsión radial siempre se aplica, independientemente del modelo de proyección seleccionado, porque es una característica inherente a todas las lentes fisheye. El modelo de distorsión radial se utiliza para corregir la distorsión introducida por la lente para obtener una representación más precisa de la imagen.
#### Proceso de Conversión del Mundo Real a la Imagen de la Lente

##### 1. Coordinadas en el Mundo Real

Imaginemos un punto $P$ en el espacio 3D con coordenadas $(X, Y, Z)$.

##### 2. Transformación a Coordenadas de la Cámara

Primero, convertimos las coordenadas del punto $P$ desde el sistema de referencia del mundo al sistema de referencia de la cámara mediante una transformación de rotación y traslación. Si la cámara está en la posición $(X_c, Y_c, Z_c)$ y tiene una orientación dada por la matriz de rotación $R$:

$$ P_{c} = R \cdot (P - C) $$

donde $P_{c} = (X_c, Y_c, Z_c)$ son las coordenadas del punto en el sistema de referencia de la cámara.

##### 3. Proyección del Punto en el Plano de la Imagen

Ahora proyectamos el punto $P_{c}$ en el plano de la imagen utilizando la proyección ecuangular o estereográfica.

- **Proyección Ecuangular**:

$$ r = k \cdot \theta $$

donde $\theta$ es el ángulo de incidencia, calculado como:

$$ \theta = \arctan\left(\frac{\sqrt{X_c^2 + Y_c^2}}{Z_c}\right) $$

La distancia radial $r$ en el plano de la imagen es proporcional a este ángulo.

- **Proyección Estereográfica**:

$$ r = 2f \cdot \tan\left(\frac{\theta}{2}\right) $$

donde $f$ es la distancia focal de la lente y $\theta$ es el ángulo de incidencia calculado de la misma manera.

##### 4. Aplicación de la Distorsión Radial

El punto proyectado en el plano de la imagen $(x, y)$ experimenta distorsión radial. El modelo de distorsión radial se puede expresar como:

$$ r' = r \left( 1 + k_1 r^2 + k_2 r^4 + k_3 r^6 + ... \right) $$

donde $r$ es la distancia radial original y $r'$ es la distancia radial distorsionada. Los coeficientes $k_1, k_2, k_3, ...$ describen el grado de distorsión.

##### 5. Transformación Afín

Finalmente, aplicamos una transformación afín para ajustar la imagen al plano del sensor de la cámara. Esta transformación incluye escalado, rotación y traslación dentro del plano de la imagen:

$$ \begin{pmatrix} u \\ v \end{pmatrix} = A \cdot \begin{pmatrix} x' \\ y' \end{pmatrix} + t $$

donde $A$ es una matriz de transformación y $t$ es un vector de traslación.

#### Resumen del Flujo de Coordenadas

1. **Coordenadas del Mundo Real** $(X, Y, Z)$
2. **Transformación de Cámara** $(X_c, Y_c, Z_c)$
3. **Proyección** (ecuangular o estereográfica) para obtener $r$
4. **Aplicación de Distorsión Radial** para obtener $r'$
5. **Transformación Afín** para obtener las coordenadas finales en el sensor de la cámara $(u, v)$






## Modelo de cámara omnidireccional
### Introduccion
![[Pasted image 20240617101922.png]] 
- En una cámara convencional, cada rayo de luz que pasa por el centro óptico se intersecta con el plano de la imagen en un único punto. Sin embargo, cuando el ángulo de visión es mayor a 180°, una línea recta (rayo) puede intersectar el plano de la imagen en más de un punto. Una línea que pasa por el centro óptico puede tener dos puntos diferentes de la escena que se proyectan en la imagen. Por ejemplo, en la Figura 2c, los rayos p y −p representan puntos diferentes en la misma línea que intersectan el plano de la imagen en lugares distintos.
- En una cámara omnidireccional, se pueden ver ambos puntos simultáneamente, lo que complica la representación en un plano de imagen bidimensional.
- No se puede representar la proyección de todos los puntos de la escena X en un único plano de imagen sin ambigüedad.
- *Solucion:*
    - Para resolver esta ambigüedad y representar correctamente los puntos de la escena, se utiliza una representación tridimensional en lugar de un plano bidimensional. Cada rayo de luz se representa como un vector unitario en el espacio tridimensional $\mathbb{R}^3$.
    - **Ventaja**: Esta representación permite describir de manera única y precisa la dirección de cada rayo de luz, sin importar cuántos puntos de la escena se proyecten en el mismo rayo.
### Planos
En el modelo general de cámara central, identificamos dos referencias distintas: el plano de imagen de la cámara $(u', v')$ y el plano del sensor $(u'', v'')$. El plano de imagen de la cámara coincide con el CCD de la cámara, donde los puntos se expresan en coordenadas de píxeles. El plano del sensor es un plano hipotético ortogonal al eje del espejo, con el origen ubicado en la intersección plano-eje.
![[Pasted image 20240617183213.png]]
En la Figura 1, se muestran los dos planos de referencia en el caso de un sistema catadióptrico. En el caso dióptrico, el signo de $u''$ se invertiría debido a la ausencia de una superficie reflectante. Todas las coordenadas se expresarán en el sistema de coordenadas colocado en $O$, con el eje $z$ alineado con el eje del sensor (ver Fig. 1a).




### Adquisicion del modelo
![[Pasted image 20240617101938.png]]

#### Imagen en el plano del sensor (a):
- $u''$ Es el punto en el plano del sensor de la cámara. Este es el punto físico donde la luz capturada por la lente de la cámara incide sobre el sensor. Este punto está en coordenadas métricas.


#### Imagen digitalizada (b):
   - $u'$ Es el punto en la imagen digitalizada. Este punto es el resultado de convertir las coordenadas métricas del plano del sensor a coordenadas en píxeles, es decir, la imagen que puede ser procesada digitalmente.
   - La imagen digitalizada es la que obtenemos directamente del sensor de la cámara después de su procesamiento inicial.

#### Transformacion Afin
- La transformación afín eelaciona el punto en el plano del sensor $u''$ con el punto en la imagen digitalizada $u'$. La transformación afín es una combinación de escalado, rotación y traslación.$$   Au' + t = u''$$
	- Donde $A$ es una matriz 2x2 y $t$ es un vector 2x1.
#### Transformación de elipse a círculo (c):
- Debido a las distorsiones de la lente, el campo de visión de la cámara puede aparecer como una elipse en la imagen digitalizada. Para facilitar el procesamiento, se transforma esta elipse en un círculo. Esta transformación puede incluir un escalado y rotación adicionales.
   - Este paso es crucial para la calibración, ya que simplifica la geometría de la imagen. Este paso es llamado precalibrazion

#### Puntos 3D (d):
Proponemos el modelo de una cámara omnidireccional en la forma:
$$\exists \alpha > 0 : \alpha g(Au + t) = PX, $$
que asigna un punto $X \in \mathbb{R}^4$ de la escena a su imagen digitalizada $u'$ mediante una matriz de proyección perspectiva $P \in \mathbb{R}^{3 \times 4}$, un cambio de sistema de coordenadas en la imagen $A$, $t$, y una función no lineal $g: \mathbb{R}^2 \rightarrow \mathbb{R}^3$ definida en el plano del sensor.

   - **Vector $g(Au' + t)$**: Representa la proyección de un punto en la imagen digitalizada a un vector tridimensional. Esta función no lineal $g$ transforma las coordenadas del punto en la imagen digitalizada para representar el rayo de luz correspondiente en un sistema de coordenadas 3D.

#### Ecuacion final
La relación entre un punto de píxel $u'$ y un punto de la escena $X$ es:

$$
\lambda \cdot p = \lambda \cdot g(u'') = \lambda \cdot g(Au' + t) = PX, \quad \lambda > 0
$$

donde $X \in \mathbb{R}^4$ se expresa en coordenadas homogéneas y $P \in \mathbb{R}^{3 \times 4}$ es la matriz de proyección en perspectiva
### Construcción de la Mapeo $f$
La figura 4 muestra cómo se construye el mapeo $f$ desde el plano del sensor hasta la retina esférica.

![[Pasted image 20240617111244.png]]
El diagrama muestra la construcción de la función de mapeo $f$ desde el plano del sensor $\pi$ hasta la retina esférica $\rho$. El punto $(u'', v'', 1)^T$ en el plano de imagen $\pi$ se transforma por $f(.)$ a $(u'', v'', w'')^T$, luego se normaliza a $(p'', q'', s'')^T$ con longitud unitaria, y así se proyecta en la esfera $\rho$.
   - El plano del sensor es donde la luz capturada por la lente se proyecta inicialmente. En este plano, cada punto $(u'', v'')$ representa una posición en la imagen capturada por el sensor.
   - Después de aplicar la función $f$, el punto $(u'', v'', w'')$ se normaliza para que tenga longitud unitaria, resultando en el punto $(p'', q'', s'')$.
   - Este punto normalizado se proyecta en la retina esférica $\rho$, que es una representación tridimensional de la imagen.
#### Observacion
Un rayo no distorsionado representado por el vector unitario $p$ puede expresarse como:
$$ p'' = k g(u'', a'', b'') = k \begin{pmatrix} u'' \\ v'' \\ w'' \end{pmatrix} = k \begin{pmatrix} A u' + t \\ f(u'', a'', b'') \end{pmatrix}, $$
donde:
$$ f(u'', a'', b'') = \frac{r''}{\tan \theta} = \frac{r''}{\tan \left( \frac{a''r''}{1 + b''r''^2} \right)}, \quad k > 0. $$

La ecuación anterior captura la relación entre el punto $u$ en la imagen digitalizada y el vector $p$ que emana del centro óptico hacia un punto de la escena $X$.



## Calibrazion
### Introduccion
Sea la ecuacion: $$\lambda \cdot p = \lambda \cdot g(u'') = \lambda \cdot g(Au' + t) = PX, \quad \lambda > 0$$
La calibración de la cámara se completa al determinar los parámetros de la transformación afín $A$ y $t$, y la función no lineal $g$, de modo que todos los vectores $g(Au' + t)$ satisfacen la geometría epipolar.

La funcion g tiene la forma
$$\mathbf{g}(u'', v'') = (u'', v'', f(u'', v''))^T $$
donde $f(u)$ es simétrica respecto a un punto $(u_0, v_0)$. El rayo que pasa por $(u_0, v_0)$ es el eje óptico de la cámara.


La función $f$ puede tener varias formas determinadas por la construcción de la lente. Por ejemplo, el modelo $\theta = ar$ se aproxima a la realidad para el lente ojo de pez Nikon FC–E8, donde $a$ es un parámetro, $\theta$ es el ángulo entre un rayo y el eje óptico, $r = \sqrt{u^2 + v^2}$ es el radio de un punto en el plano del sensor respecto a $(u_0, v_0)$, y se cumple $f(u) = \frac{r}{\tan \theta}$. Un modelo más preciso requiere una parte no lineal. Utilizamos el modelo de división:

$$ \theta = \frac{ar}{1 + br^2}, \quad r = \frac{a - \sqrt{a^2 - 4b\theta^2}}{2b\theta}, $$
donde $b$ es un parámetro adicional.





### $f$ generica
En lugar de utilizar un modelo específico para el sensor en uso, optamos por aplicar un modelo paramétrico generalizado de $f$, adecuado para diferentes tipos de sensores. La razón de esto es que queremos que este modelo compense cualquier desalineamiento entre el punto focal del espejo (o la lente ojo de pez) y el centro óptico de la cámara. Además, deseamos que nuestra función generalizada se ajuste aproximadamente a los sensores donde la propiedad de un solo punto de vista no se verifica exactamente (por ejemplo, cámaras ojo de pez genéricas). En nuestro trabajo anterior, propusimos la siguiente forma polinómica para $f$:

$$
f(u'', v'') = a_0 + a_1\rho' +a_2\rho^2 + \ldots + a_N\rho^N
$$

donde los coeficientes $a_i$ y el grado polinómico $N$ son los parámetros a determinar mediante la calibración. Por lo tanto, la ecuación (1) puede reescribirse como:
![[Pasted image 20240617184306.png]]

Como se mencionó en la introducción, en este artículo queremos reducir el número de parámetros de calibración. Esto se puede lograr observando que todas las definiciones de $f$, que son válidas para espejos hiperbólicos y parabólicos o cámaras ojo de pez , siempre satisfacen lo siguiente:

$$
\left. \frac{df}{d\rho} \right|_{\rho=0} = 0
$$

Esto nos permite asumir $a_1 = 0$, y así, la ecuación (3) puede reescribirse como:

$$
f(u'', v'') = a_0 + a_2\rho^2 + \ldots + a_N\rho^N
$$


### Procedimiento
Por calibración de una cámara omnidireccional entendemos la estimación de los parámetros $$A, t, a_0, a_2, ..., a_N$$
#### Estimar A y t

Para estimar A y t, introducimos un método que se basa en un procedimiento iterativo. 
1. Se comienza configurando A como la matriz unitaria. Sus elementos se estimarán usando un refinamiento no lineal.
2. Asumimos que el centro de la imagen omnidireccional O coincide con el centro de la imagen Ic, es decir, $O_c = I_c$, y por lo tanto $t = α(O_c − I_c) = 0$. 
	- Entonces asumimos que $u' ⋅ α = u''$. Así, al sustituir esta relación en (4) y usar (6), tenemos la siguiente ecuación de proyección:
![[Pasted image 20240617220324.png]]
	- Donde u' y v' son las coordenadas de píxeles de una imagen con respecto al centro de la imagen, y ρ' es la distancia euclidiana. 
- También note que el factor α puede integrarse directamente en el factor de profundidad λ; por lo tanto, solo es necesario estimar N parámetros (a0, a2, ..., aN).

##### Observaciones
- Para A, la suposición de ser unitaria es razonable porque la excentricidad del borde externo en la imagen omnidireccional suele estar cerca de 0. 
- Por el contrario, Oc puede estar muy lejos del centro de la imagen Ic. El método que discutiremos no se preocupa por esto.


#### Solucion para los parametros extrinsecos de la camara
Durante el procedimiento de calibración, se muestra un patrón plano de geometría conocida en diferentes posiciones desconocidas, que están relacionadas con el sistema de coordenadas del sensor por una rotación $R = [r_1, r_2, r_3]$ y una traslación t, llamados parámetros extrínsecos. 
- Sea $I^i$ una imagen observada del patrón de calibración $M_{ij}=[X_{ij},Y_{ij},Z_{ij}]$ las coordenadas 3D de sus puntos en el sistema de coordenadas del patrón, y $m_{ij}=[u_{ij},v_{ij}]$ las coordenadas de píxeles correspondientes en el plano de la imagen. 
- Desde que asumimos que el patrón es plano, con la pérdida de la generalidad tenemos $Z_{ij}=0$. Entonces, la ecuación (7) se convierte en:
![[Pasted image 20240617221132.png]]
Por lo tanto, para resolver la calibración de la cámara, el parámetro extrínseco debe determinarse para cada pose del patrón de calibración

Eliminamos la dependencia de la escala de profundidad multiplicando ambos lados de la ecuación (8) vectorialmente por Pi
![[Pasted image 20240617221912.png]]
De (9), tenemos que cada punto p, del patrón contribuye con tres ecuaciones homogéneas
![[Pasted image 20240617221943.png]]
- Aquí se conocen $X_j, Y_j$ y $Z_j$, al igual que $u_j,v_j$. Además, observe que sólo (10.3) es lineal en la incógnita $r_{11},r_{12},r_{21},r_{22},t_1,t_2,..$. 
- Al apilar todas las entradas desconocidas de (10.3) en un vector, reescribimos la ecuación (10.3) para L puntos del patrón de calibración como un sistema de ecuaciones lineales.

![[Pasted image 20240617222139.png]]
- Una estimación lineal de H se puede obtener minimizando el criterio de mínimos cuadrados $min||M ⋅ H||^2$, sujeto a $||H||^2 = 1$. Esto se logra usando la  descomposición en valores singulares (SVD). 
- La solución de (11) es conocida hasta un factor de escala, que puede determinarse de manera única debido a que los vectores $r_1$ y $r_2$ son ortonormales. Debido a la ortonormalidad, las entradas desconocidas $r_{31}$ y $r_{32}$ también pueden calcularse de manera única.

>Para resumir, el primer paso de la calibración permite encontrar los parámetros extrínsecos $r_{11}, r_{12}, r_{21}, r_{22}, r_{31}, r_{32}$ y $t_1, t_2$ para cada posición del patrón de calibración, excepto el parámetro de traslación $t_3$. Este parámetro se calculará en el siguiente paso, que se refiere a la estimación de la función de proyección de la imagen.

#### Solución para los parámetros intrínsecos de la cámara
Sustituimos los valores estimados(extrinsecos) en las ecuaciones (10.1) y (10.2), y resolvemos los parámetros intrínsecos de la cámara $a_0, a_2, ..., a_N$ que describen la forma de la función de imagen $\mathbf{g}$. 
- Al mismo tiempo, también calculamos el $t_3$ desconocido para cada posición del patrón de calibración. 

Como se hizo anteriormente, apilamos todas las entradas desconocidas de (10.1) y (10.2) en un vector y reescribimos las ecuaciones como un sistema de ecuaciones lineales. Pero ahora, incorporamos todas las observaciones K del tablero de calibración. Obtenemos el siguiente sistema:
![[Pasted image 20240617222921.png]]

donde $A_i, B_i, C_i$ y $D_i$ son matrices que contienen las coordenadas conocidas del patrón y los parámetros estimados.

Finalmente, la solución de mínimos cuadrados del sistema sobredeterminado se obtiene usando la pseudoinversa. Por lo tanto, ahora están disponibles los parámetros intrínsecos $a_0, a_2, ..., a_N$ que describen el modelo.

Para calcular el mejor grado polinomial N, comenzamos con N=2. Luego, aumentamos N en pasos unitarios y calculamos el valor promedio del error de reproyección de todos los puntos de calibración. El procedimiento se detiene cuando se encuentra un error mínimo.

#### Refinamiento lineal de los parámetros intrínsecos y extrínsecos
Este refinamiento se realiza mediante una minimización lineal. La estructura del algoritmo de refinamiento lineal es la siguiente:
1. El primer paso utiliza el modelo de cámara $(a_0, a_2, ..., a_N)$ estimado en el paso anterior, y vuelve a calcular todos los parámetros extrínsecos resolviendo conjuntamente las ecuaciones (10.1), (10.2) y (10.3). 
	- El problema lleva a un sistema lineal homogéneo, que se puede resolver, hasta un factor de escala, utilizando SVD. 
	- Luego, el factor de escala se determina de manera única explotando la ortonormalidad entre los vectores $r_1$ y $r_2$.

2. En la segunda etapa, los parámetros extrínsecos recalculados en el paso anterior se sustituyen en las ecuaciones (10.1) y (10.2) para refinar ulteriormente el modelo intrínseco de la cámara.
	- El problema lleva a un sistema lineal, que se puede resolver como de costumbre utilizando la pseudoinversa.

#### Detección iterativa del centro
Queremos que nuestra caja de herramientas de calibración sea lo más automática posible, y por lo tanto, deseamos la capacidad de identificar el centro de la imagen omnidireccional Oc incluso cuando el borde externo del sensor no es visible en la imagen.
- Observe que nuestro procedimiento de calibración estima correctamente el modelo paramétrico intrínseco solo si Oc se toma como el origen de las coordenadas de la imagen. 
- Si no es el caso, al proyectar de nuevo los puntos 3D del tablero de ajedrez en la imagen, observaríamos un gran error de reproyección con respecto a los puntos de calibración (ver Figura 2a).
- Motivados por esta observación, realizamos muchas pruebas de nuestra calibración para diferentes ubicaciones del centro, y para cada prueba, calculamos la Suma de Errores de Reproyección Cuadrados (SSRE). Como resultado, verificamos que la SSRE siempre tiene un mínimo global en la ubicación correcta del centro.
- Este resultado nos lleva a una búsqueda iterativa del centro Oc, que se detiene cuando la diferencia entre dos ubicaciones potenciales del centro es menor que una cierta fracción de píxel ε (razonablemente establecemos ε = 0.5 píxeles):
1. En cada paso de esta búsqueda iterativa, se muestrea uniformemente una región de la imagen en un cierto número de puntos.

2. Para cada uno de estos puntos, se realiza la calibración utilizando ese punto como una ubicación potencial del centro, y se calcula la SSRE.

3. El punto que da la SSRE mínima se asume como un centro potencial.

4. La búsqueda continúa refinando el muestreo en la región alrededor de ese punto, y los pasos 1, 2 y 3 se repiten hasta que se cumple la condición de parada.

Observe que el costo computacional de esta búsqueda iterativa es tan bajo que solo tarda 3 segundos en detenerse.

#### Refinamiento no lineal

La solución lineal dada en las subsecciones anteriores A, B y C se obtiene minimizando una distancia algebraica, que no es físicamente significativa. Para ello, elegimos refinarla mediante inferencia de máxima verosimilitud.

Supongamos que tenemos K imágenes de un plano modelo, cada una conteniendo L puntos de esquina. Luego, supongamos que los puntos de la imagen están corruptos por ruido independiente y distribuido de manera idéntica. Entonces, la estimación de máxima verosimilitud se puede obtener minimizando el siguiente funcional:
$$ E = \sum_{i=1}^K \sum_{j=1}^L ||m_{ij} - m(\hat{R}_i, T_i, A,O_c, a_0, a_2, ..., a_N, M_j)||^2 $$

donde $m(\hat{R}_i, T_i, A,O_c, a_0, a_2, ..., a_N, M_j)$ es la proyección del punto $M_j$ del plano i según la ecuación (1). $R_i$ y $T_i$ son las matrices de rotación y traslación de cada pose del plano; $R_i$ se parametriza mediante un vector de 3 parámetros relacionados con $R_i$ por la fórmula de Rodrigues. Observe que ahora incorporamos en el funcional tanto la matriz afín A como el centro de la imagen omnidireccional Oc.

Al minimizar el funcional definido en (14), en realidad calculamos los parámetros intrínsecos y extrínsecos que minimizan el error de reproyección. 

Para acelerar la convergencia, decidimos dividir la minimización no lineal en dos pasos. 
- El primero refina los parámetros extrínsecos, ignorando los intrínsecos. 
- Luego, el segundo paso utiliza los parámetros extrínsecos recién estimados y refina los intrínsecos.
- Al realizar muchas simulaciones, encontramos que esta división no afecta el resultado final con respecto a una minimización global.

Para minimizar (14), utilizamos el algoritmo de Levenberg-Marquardt, tal como lo implementa la función $lsqnonlin$ de Matlab. El algoritmo requiere una estimación inicial de los parámetros intrínsecos y extrínsecos. Estos parámetros se obtienen utilizando la técnica lineal descrita en las subsecciones anteriores. Como primera estimación para A, utilizamos la matriz unitaria, mientras que para Oc utilizamos la posición estimada a través del procedimiento iterativo explicado en la subsección D.







## Calibrazion en MatLab
Para eliminar la distorsión de la lente de una imagen de ojo de pez, puede detectar un patrón de calibración de tablero de ajedrez y luego calibrar la cámara. Puede encontrar los puntos de tablero de ajedrez utilizando las funciones *detectCheckerboardPoints* y *generateCheckerboardPoints*. La función *estimateFisheyeParameters* utiliza los puntos detectados y devuelve el objeto *fisheyeParameters* que contiene los parámetros intrínsecos y extrínsecos de una cámara ojo de pez. Puede utilizar el objeto *fisheyeCalibrationErrors* para comprobar la precisión de la calibración.

### Procedimiento

- Elimine la distorsión de la lente de una imagen de ojo de pez detectando un patrón de calibración de tablero de verificación y calibrando la cámara. Luego, muestre los resultados.

1. Reúna un conjunto de imágenes de calibración de tablero de ajedrez.
``` Python
images = imageDatastore('calibrationImages');
```

2. Detectar el patrón de calibración de las imágenes. El argumento *'PartialDetections' Name-Value* se establece en true de forma predeterminada, lo que permite la detección de tableros de ajedrez parciales.
``` Python
[imagePoints,boardSize] = detectCheckerboardPoints(images.Files, 'HighDistortion', true);
```


3. Generar coordenadas del mundo para las esquinas de los cuadros de tablero de ajedrez.
``` Python
squareSize = 20; % millimeters
worldPoints = generateCheckerboardPoints(boardSize,squareSize);
```


4. Estimar los parámetros de calibración de la cámara ojo de pez en función de la imagen y los puntos del mundo. Utilice la primera imagen para obtener el tamaño de la imagen.
``` Python
I = readimage(images,10); 
imageSize = [size(I,1) size(I,2)];
params = estimateFisheyeParameters(imagePoints,worldPoints,imageSize);
```


5. Retire la distorsión de la lente de la primera imagen I y mostrar los resultados.
``` Python
J1 = undistortFisheyeImage(I,params.Intrinsics);
figure
imshowpair(I,J1,'montage')
title('Original Image (left) vs. Corrected Image (right)')

J2 = undistortFisheyeImage(I,params.Intrinsics,'OutputView','same', 'ScaleFactor', 0.2);
figure
imshow(J2)
```




# Referencia
[https://it.mathworks.com/help/vision/ug/fisheye-calibration-basics.html](https://it.mathworks.com/help/vision/ug/fisheye-calibration-basics.html)
# Analizar
![[Pasted image 20240618095529.png]]














