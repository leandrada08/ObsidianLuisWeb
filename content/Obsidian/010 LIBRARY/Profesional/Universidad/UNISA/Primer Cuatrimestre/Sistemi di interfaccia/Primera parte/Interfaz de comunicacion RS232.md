---
cards-deck: Profesional::Universidad::UNISA::Sistemi di interfaccia::RS232
---




- Usa una singola linea
- Non richiede hardware aggiuntivo
- Collegamento PC-PC o PC-Strumento

![[Pasted image 20231227095820.png]]

### Caracteristicas #tarjeta-anki 
- Non bilanciata
- Full duplex
- Velocita massima di trasmissione 11520bps aprox 100kbps
- Logica negata
	- 5.15V →0
	- -5.15V→1
- Tensione
	- *MARK*: tra -12V e -3V
	- *SPACE*: tra +3 e +12V
- Lungueza maxima 20m
^1705479600787


### Connettori #tarjeta-anki 
- **DTE:** PC, terminali
- **DCE:** Modem, stampanti …
Esistono connettori a 9 pin(DB-9) ed a 25 pin(DB-25)
- Connettore femmina dovrebbe essere associato a la periferica
- Connettore maschio a il computer
^1705479600791

#### Parametri di connessione

- Numero della porta: 0 per COM1:, 1 per COM2
- Baud rate: Valori tipici sono 1200, 2400, 4800, 9600, 19200, 38400, 57600, 115200
- Data bit: Scelta tra 5,6,7 o 8 bit dati
- Stop bit: Scelta tra 1, 1.5 e 2 bit dei stop
- Parity: Pari, dispari o nessuna
- Control:
	- Hanshake harware: Si usano ulteriori linee per fissare inizio e fine di una sequenza di dati
	- Handshake software: Si racchiude il messaggio tramesso tra due caratteri di controllo ““XON” e ““XOFF”
![[Pasted image 20231227100739.png]]



### Collegamento
#### Collegamento DTE-DCE
![[Pasted image 20231227100833.png]]

#### Collegamento DTE-DTE(Null modem)
![[Pasted image 20231227100907.png]]

### Programmi per PC
- Hyperterminal
- Termite
- Serial port monitor
- Controllo porta seriale


### Observaciones #tarjeta-anki 
- Tensione di riposo(IDLE) della linea é negata(MARK)
- 1 bit di start: segna l’inizio del fram con la transiizone MARK→SPACE
- Codifica binaria: MARK=1 e SPACE=0
	- Bit meno significativo trasmesso per primo(LSD)
- Bit di paritá: 0 si é vero la parita
- Bit di stop riporta la tensione della linea a IDLE(MARK)
^1705479600795
