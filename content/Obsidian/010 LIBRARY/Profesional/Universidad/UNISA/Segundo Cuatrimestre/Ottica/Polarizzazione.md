## Introduzione
### Storia
- Nel anno 1670 il matematico Bartholinus osservo che quando un raggio di luce si propagava attraverso un cristallo di calcite romboedrico, emergono due raggi
- Entrambi i raggi obbediscono alla legge di Snell, ma sperimentano indice di rigrazione differenti
![[Pasted image 20240410201427.png]]
- Nel stessi anni Huygens mostró  che routando un cristallo di ulexite l’intensitá di un raggio veniva massimizzata e l’altro raggio scompariva. Una rotazione ulteriore mostrava che il primo raggio riappariva con un’intensitá massima e il secondo raggio scompariva
- A causa di questo comportamente opposto dell’intensitá si congetturo che un raggio di luce naturale consiste di due raggi indipendenti e polarizzati in maniera ortogonale
- I due raggi sono detti rappresentare gli stati di polarizzazione s(senkrecht) e p(parallele)

### Caratteristiche di un campo elettromagnetico
- Un campo elettromagnetico(onda) posside tre caratteristiche
	- Intesitá
	- Lunguezza d’onda o frequenza
	- Polarizzazione

![[Pasted image 20240410202231.png]]
- Il occhio umano puo interpretare l´intensitá come “luminositá” e la lunguezza d´onda come colore
	- Ma non puo discriminare la polarizzazione del vettore campo elettrico
	- Ma ci sono alcuni animali che “vedono” la polarizzazione
		- Questi specie possono individuare predde o predatori cosi
		- Anche possono distinguere “miraggi”
		- O possono tramite la polarizzazione riescono a orientarsi laddove non ci sono punti di riferimento

![[Pasted image 20240410202456.png]]


## Polarizzazione
### Piano di polarizzazione
Sia un’onda piano uniforme che si propaga lungo z e osserviamo l´evoluzione temporale di e(z,t) fissato z(per semplicitá z=0)
![[Pasted image 20240411090234.png]]

#### Polarizzazione piana
![[Pasted image 20240411090246.png]]
- Il campo é polarizzato linearmente nel piano x-y lungo una retta con coefficiente angolare positivo(se $E_{ox}=E_{oy}$ →$\alpha=\pi/4$)
	- La polarizzazione cosi ottenuta é lineare, perche il rapporto tra la componente x e la componente y é una constante
	- Il rapporto tra le ampiezze delle singole componteti ci dá il coefficiente angolare, si le due ampiezze sono uguali, allora $\alpha=\pi/4$ 
$$\alpha=tg^{-1}(\frac{E_{ox}}{E_{oy}})$$
Vogliamo ora capire cosa succede quando una delle due componenti ha uno sfasamento rispetto all´altra 
- Si sfasiamo una delle componenti mas/menos $\pi$ il campo é polarizzato linearmente nel piano x-y lungo una retta con coefficiente angolare negativo (se $E_{ox}=E_{oy}$ →$\alpha=-\pi/4$
![[Pasted image 20240411090255.png]]


- Si sfasiamo $\pi/2$ il campo, possiamo vede come la polarizzato sia diventata circolarmente nel piano x-y con rotazione orario
![[Pasted image 20240411090311.png]]
- Si sfasiamo $-\pi/2$ lo stesso ma con rotazione antiorario
![[Pasted image 20240411090320.png]]



### Polarizazione ellittica
Sia la ellisse
![[Pasted image 20240411092608.png]]
- E i vettore $u$ e $v$ sono polarizzati linearmente. $$u(t)=a\cdot cos(wtx)$$
$$v(t)=b \cdot sin(wty)$$

- Si considerino i due vettori. 
![[Pasted image 20240411092828.png]]
- $w_1$ descrive una polarizzazione circolare, di velocitá angolare $\alpha$ e ampiezza $\frac{a+b}{2}$
- $w_2$ descrive una polarizzazione circolare, di velocita angolare $-\alpha$ e ampienzza $|\frac{a-b}{2}|$ 
- Possiamo notare che $w_1+w_2=u+v$
	- Quindi, la composizione dei due vettori $w_1(t)+w_2(t)$ riproduce ancora l´originaria polarizzazione elittica

- Allora, si considerino i vettori:
![[Pasted image 20240411093143.png]]
- Un vettore arbitrario puó essere scomposto in una delle due basi

### Campi non polarizzati
- Un campo elettromagnetico puó anche essere non polarizzato, in questi casi, consideriamo come composto dalla sovrapposizione di campi polarizzati linearmente o circolarmente
- Come si rende “polarizzato” un fascio di luce non polarizzato?
- Esistono tre tecniche di polarizzazione

#### Per riflessione
La luce riflessa da un piano dielettrico risula parzialmente polarizzata
*Angolo di Brewster:* É l’angolo d´incidenza in corrispondenza del quale si annulla il coefficiente di riflessione
- Solo la polarizzazione $||$ ha un angolo di Brewster(quela perpendiculare no)
![[Pasted image 20240411093515.png]]

#### Per rifrazione
Esistono dei cristalli, detti birifrangenti, che presentano indice di rifrazione diverso a seconda dello stato di polarizzazione
*Birifrangenza o doppia rifrazzione:* Dalla teoria della propagazione di un’onda in un mezzo anisotropo si dimostra che ad ogni direzione di incidenza corrispondono due stati di polarizzazione tra loro ortogonali che si propagano nel mezzo con differente velocitá
![[Pasted image 20240411094025.png]]

#### Per dicroismo
Esistono materiali in grado di polarizzare la luce che li attraversa. Su questo principio si badano i filtri polaroid
Sulla polarizzazione per dicroismo verifivheremo sperimentalemte la *Legge di Malus-Dupin*
![[Pasted image 20240411094152.png]]
- La luce polarizzata lungo una particolare direzione chiamato *asse del materiale*, “vede” un materiale trasparente
	- La componente polarizzata in direzione ortogonale all’asse viene invence assorbita quasi del tutto
	- La luce che emerge dal materiale risulta polarizzata linearmente lungo l’asse(*filtro polarizzatore*)


### Ellise di polarizzazione
Generalizziamo il caso di un´onda piana uniforme che si propaga lungo z con uno sfasamento arbitratio tra le componenti
$$E(z)=E_{0x}cos(wt-kz+\delta_x)+E_{0y}cos(wt-kz+\delta_y)$$
- Si cerca di eliminare la dipendenza da z e da t
1. Prima escribo ogni componenti(x e y) per diviso
2. Dopo, uso la proprietá trigonometrica dil coseno de la suma
![[Pasted image 20240416100246.png]]
3. Paso $E_0$ per il altro termino e arrivo a questa expresione
![[Pasted image 20240416100338.png]]
4. A questa expresione la posso moltiplicare per $cos(\delta_{y})$ nella componente *x* e $cos(\delta_x)$ nella componente *y*
5. Dopo sottraiamo membro a membro e siamo arrivati all´espressione
$$\frac{E_x}{E_{0x}}cos(\delta_y)-\frac{E_y}{E_{0y}}cos(\delta_x)=sin(wt-kz)sin(\delta_y-\delta_x)$$
- Si retorniamo al passo 4, invece di moltiplicare per coseno lo facciamo per seno, si puo arrivare a le expressione $$\frac{E_x}{E_{0x}}sin(\delta_y)-\frac{E_y}{E_{0y}}sin(\delta_x)=cos(wt-kz)sin(\delta_y-\delta_x)$$
6. Si eleviamo al quadrato e sommiamo, si calcela quasi tutto la parte de destra della expresione, lavoriando matematicamente le expressione della siniestra siamo arrivati a $$(\frac{E_x}{E_0x})^2+(\frac{E_y}{E_{0y}})^2-2\frac{E_xE_y}{E_{0x}E_{0y}}(cos(\delta_y)cos(cos\delta_x)+sin(\delta_y)sin(\delta_x))=sin(\delta)^2$$
- Dove $\delta=\delta_y-\delta_x$
- Questo é l´equazione di un´elisse
- Al variare di z e t l'elisse rimane fissata
- L'elisse e inscritta nel rettangolo $2E_{0x}x2E_{0y}$ e tocca i lati del rettangolo nei punti
![[Pasted image 20240416102206.png]]
- Di questa equazione possiamo sapere che:
	- Si $E_{oy}=0$ → $E_{oy}\neq0$ → LHP(linearly horizontal)
	- Si $E_{ox}=0$ →$E_{oy}\neq0$ → LVP(linearly vertical)
	- Si $\delta$=0 → $E_{oy}=E_{ox}$ → L+45
	- Si $\delta=\pi$ → $E_{oy}=E_{ox}$ → L-45
	- Si $\delta=\pi/2$ → $E_{oy}=E_{ox}=E_0$ → RCP(Righ circularly)
	- Si $\delta=-\pi/2$ → $E_{oy}=E_{ox}=E_0$ → LCP(Left circularly)

![[Pasted image 20240416105829.png]]
- Questo stati di polarizzazioni (stati degenari) sono importanti perche
	- Facilmente realizzabili mediante polarizzatori
	- Semplificano calcoli e misure
### Angoli
#### Angolo di rotazione dell´ellisse
- In generale gli assi delll´ellisse non sono directti come x e y ma l´elisse e routata di un angolo $\psi$,$(0<\psi<\pi)$ *angolo di rotazione* e
![[Pasted image 20240416110314.png]]

#### Angolo di ellitticita
- Per identificare univocamente l´elisse, detti a e b il semiasse maggiore e quello minore, sidefinisce l´angolo di ellitticitá $\chi$, $(-\pi/4<\chi<\pi/4)$
$$\pm\frac{b}{a}=tan(\chi)$$
![[Pasted image 20240416110703.png]]

#### Angoli per stati di polarizzazione degeneri
- Ricaviamo i valori di $\chi$ e $\psi$ per gli stati di polarizzazione degeneri
	- Si $E_{oy}=0$ → $E_{oy}\neq0$ → LHP(linearly horizontal) → $\chi=\psi=0$
	- Si $E_{ox}=0$ →$E_{oy}\neq0$ → LVP(linearly vertical) → $\chi=0,\psi=\pi/2$
	- Si $\delta$=0 → $E_{oy}=E_{ox}$ → L+45 → $\chi=0,\psi=\pi/4$
	- Si $\delta=\pi$ → $E_{oy}=E_{ox}$ → L-45 → $\chi=0,\psi=-\pi/4$
	- Si $\delta=\pi/2$ → $E_{oy}=E_{ox}=E_0$ → RCP(Righ circularly) → $\chi=\pi/4, \psi=0$
	- Si $\delta=-\pi/2$ → $E_{oy}=E_{ox}=E_0$ → LCP(Left circularly) → $\chi=-\pi/4,\psi=0$


### La sfera di Poincare
Solo é una rappresentazione grafica per vedere, dopo di sapere il valore di $\chi,\psi$, che polarizzazion ce l’ha mia segnale
Se si reppresentato tutti i posssibili stati di polarizzazione su un sistema di assi in coordinate polari {$R,2\psi,2\chi$} si ha la sferea di Poincare (1892)
![[Pasted image 20240417153130.png]]

- Tutti gli stati di polarizzazione lineare si trovano sull´equatore
- Poinché $\chi>0$ rappresenta polarizzazioni destrorse → i punti dell´emisfero superior sono stati di polarizazzione ad elicitá positiva(RCP)
- $\chi<0$ rappreseta polarizzazioni sinistrorse quindi ad elicitá negativa(LCP)

#### Limiti
- I punti che la costituiscono(ellissi di polarizzzzione) sono dipendenti dal tempo
- L´angolo di rotazione dell´elisse $\psi$ e quello di ellitticitá $\chi$ sono quantita non misurabili

- Per superare questi due limiti si introducono quatro nuovi parametri(tre indipendenti) che rappresentano le coordinate della sfera di Poincare
- In questa sfera, ogni punto rappresenta uno stato di polarizzazione specifico, e i parametri di Stokes sono utilizzati per definire la posizione di ogni punto sulla sfera.
![[Pasted image 20240417154240.png]]

#### I parametri di Stokes
I parametri di Stokes sono quattro numeri reali che descrivono completamente lo stato di polarizzazione della luce in termini di intensità, polarizzazione lineare, polarizzazione ellittica e circolarità. Questi parametri vengono utilizzati per calcolare le coordinate di un punto nella sfera di Poincaré, consentendo di visualizzare facilmente lo stato di polarizzazione di un'onda elettromagnetica.
- Il raggio della sfera di Poincare é l´intensitá della radiazione ovvero
$$S_0=E_{0x}^2+E_{0y}^2$$
- E poinché
![[Pasted image 20240417155113.png]]
- Possiamo trovare il valore di tutti i parametri
![[Pasted image 20240417155143.png]]
- Anche si puo scribere di manera matricial
![[Pasted image 20240417155223.png]]
- Questa sono quantitá misurabili
	- $S_0$ → Intensitá totale della radiazione $I_0$
	- $S_1$ → Preponderanza della luce polarizzata LHP sulla luce poalrizzata LVP
	- $S_2$ → Prepoderanza della luce polarizzata L+45 sulla luce polarizzata L-45
	- $S_3$ → Prepoderanza della luce polarizzata RCP sulla luce polarizzata LCP


- Per eliminare la dipendenza del tempo si effetua una media nel perior dei proddotti
- Spesso é conveniente utilizzare la notazione fasoriale
$$E_x=E_{0x}e^{-i\delta_x},E_y=E_{0y}e^{-i\delta_y}$$
- E ottenere
![[Pasted image 20240417155652.png]]

Quindi
![[Pasted image 20240417155956.png]]
![[Pasted image 20240417155933.png]]

#### Misurare i parametri di Stokes **Continuar pagina 24**
I parametri di Stokes identifano univocamente uno stato di polarizzazione e sono misurabili.
- Usiamo una notazione fasoriale $$E_x=E_{0x}e^{-i\delta_x},E_y=E_{0y}e^{-i\delta_y}$$
1. Lo facciamo passare il fascio attraverso una lamina polarizzatrice o ritardatrice $$E_x'=E_{0x}e^{-i\delta_x}e^{i\phi/2},E_y'=E_{0y}e^{-i\delta_y}e^{-i\phi/2}$$
2. Dopo facciamo passare il campo in uscita ad una lamita polaroid con asse inclinato di $\theta$, questi é
$$E=E'_xcos(\theta)+E'_ysin(\theta)=E_{x}e^{i\phi/2}cos(\theta)+E_{y}e^{-i\phi/2}sin(\theta)$$