---
cards-deck: Profesional::Universidad::UNISA::Sistemi di interfaccia::I2C
---

Interfaccia di comunicacione seriale per il trasferimento dei dati tra dispositivi a bassa velocitá e basso costo

![[Pasted image 20240103113751.png]]
## Interfaz I2C #tarjeta-anki 
- Tipi multi-master/multi-slave
- Half duplex
- Comunicacione a stella (1-N)
- Velocitá normale 100kbps
- Velocitá massima 4Mbps
^1705479962949

### Funcionamiento
- Il master:
	- Da inizio alla comunicaciones
	- Genera il clock
	- Chiude la comunicaciones
- Il Slave:
	- Indirizato per il master **1ra diferenza con il SPI**
	- I Slave ha indirizzi unico

### Hardware #tarjeta-anki 
- Ci sono 2 wire
	- SDA serial data
	- SCL serial CLK
		- **2da diferenza con il SPI**
^1705479962953


## BUS I2C #tarjeta-anki 
Open darin e open collector per evitare conflicto del bus fra piú master.
![[Pasted image 20240103144047.png]]
- 2 resistencias pull-up.
	- Le linee SDA e SCL sono collegate attraverso resistenze pull-up alla tensione di alimentazione.
	- Quando non viene trasmesso alcun dato, le resistenze pull-up esterne mantengono le linee in alto.
- I driver master e slave sono configurati come open-drain o open-collector, in modo che possano tirare giù le linee SCL e SDA per trasmettere un 0 logico, ma dipendono dalle resistenze pull-up per tornare al livello alto.
	- Questa configurazione open-drain è interna ad ogni dispositivo.
- Poiché abbiamo multipli master, quando due o più cercano di iniziare una trasmissione contemporaneamente, chi invia per primo un 0 vince l'arbitraggio.
- Il master genera impulsi di clock con SCL e quando invia dati mette le informazioni in SDA, che gli schiavi leggono durante gli impulsi di clock.
- Gli schiavi possono modificare SDA solo quando il master lo indica e quando sono stati indirizzati.
^1705479962958

## Protocollo di comunicazione in I2C #tarjeta-anki 
- La comunicazione coinvolge una sequenza di inizio, bit di indirizzo, bit di controllo, payload di dati e bit di stop. Il clock SCL sincronizza tutto.
![[Pasted image 20240103145015.png]]
1. Bit di inizio (start condition): 1→0 in SDA, indicando l'inizio della trasmissione dati.
2. Indirizzo (Address): Il master invia i 7 bit di indirizzo dello slave di destinazione. SDA cambia per indicare l'indirizzo, SCL fornisce gli impulsi di clock.
3. R/W: Il master invia un bit indicando se l'operazione è di Lettura (1) o Scrittura (0). Ancora una volta SDA e SCL cambiano.
4. ACK: Lo slave risponde con un bit di riconoscimento (ACK) portando SDA basso. SCL fornisce l'impulso di clock per l'ACK.
5. Dati: Vengono inviati i byte di dati dal master allo slave (scrittura) o viceversa (lettura). SDA cambia con ogni bit di dati e SCL genera gli impulsi di clock.
6. ACK: Ogni byte è nuovamente riconosciuto dal ricevitore con un bit ACK (SDA basso).
7. STOP: Il master indica la fine della transazione portando SDA alto mentre SCL è alto. 0 →1 in SDA.
^1705479962964

