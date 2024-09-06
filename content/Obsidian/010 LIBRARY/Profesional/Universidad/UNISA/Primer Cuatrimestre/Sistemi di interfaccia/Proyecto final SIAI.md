
## Requisitos
- 80 a 140hz maschile
- 180 a 250 femminile

- 2 filtri per separare parlatore maschili o feminili
- Riprodurre i segnali dei 2 parlatori


## afgad
- 2 filtro pasa banda
	- Ambos butter



## Diseño
- Elijo frecuencias analogicas
- Las normalizo con fs/2
- Utilizo la funcion butterd donde requiere
	- Nos devuelve el orden de filtro y la frecuencia de corte del filtro pasa bajo normalizado(**Analizar**)
- Con la funcion butter paso de pasa bajo a pasa banda
	- Nos da el vector denominador y nominador(**IIR**)


# Slide

## Introduccion del proyecto(1 slide)
- Enunciado
	- Detectar si es voz de hombre o de mujer
	- Frecuencias de mujer y de hombre
- Problema
	- Armonicos infinitos y que se solapan
- Solucion
	- Analizar un rango donde no se solapen

## Desarrollo del proyecto(4 slide)

### Primera slide(bases de proyecto)
- Enfoque dado
	- 1 Filtro pasa bajo para la voz de hombre
	- 1 Filtro pasa banda para la voz de la mujer
- Especificaciones
	- Bandas de frecuencias
		- 85 a 180 hombre
		- 165 a 255 mujer


### Segunda slide
- FIR
	- PAra manejar y reproducir


- IIR
	- Para solo manejar informacion
### Tercera slide(filtros)
- Se opto por Cheby de primer tipo
	- Mejor transicion entre banda de paso y banda de rechazo con menor orden
	- Mejor rechazo con menor orden
	- Mayor riple en banda de paso





# Presentacion
## Luis 1

Buenos dias, a nuestro grupo le toco el proyecto de separacion de hablante con filtro. 

**Buongiorno, al nostro gruppo è stato assegnato il progetto di separazione del parlante con filtro.** 


---
Basicamente este nos requeria que detectemos si se trataba de una voz de hombre o de mujer, esto parecia en un principio bastante sencillo, pero nos encontramos con el problema que el armonico fundamental de la voz de una mujer tenia el mismo rango de valores que el primer armonico de la voz de un hombre. Para solucionar esto, usamos como base de analisis el rango de voz de hombre. Pero antes de ver a profundidad nuestro proyecto, analizaremos ciertos aspectos teoricos.

**Per questo, dobiamos rilevare si é una voce di uomo o di donna.
Questo sembrava inizialmente molto semplice, ma aveva un problema, l'armonico fa sì che la voce delle donne si sovrapponga alla voce degli uomini. Per risolvere questo problema, abbiamo utilizzato come base di analisi l'intervallo di voce maschile.
Ma prima di esaminare piú il nostro progetto, analizzeremo alcuni aspetti teorici.**



---
A la hora de analizar si usar filtro FIR o IIR en nuestro filtro, tuvimos que tenes en cuenta varios aspecto. El filtro FIR es facil de proyectar, es siempre estable y evita distorsion de fase, pero, este sirve mucho en los casos en los cuales queremos reproducir una señal de audio luego de filtrarla, en nuestro caso, como solo queremos analizar si es femenina o masculina, nos conviene un filtro IIR, ya que logra corte de bandas  nitidos y exponenciales, y se puede lograr un mejor filtrado con un orden menor de filtro.


**Per valutare si utilizzare un filtro FIR o IIR nel nostro progetto, abbiamo dovuto tenere in conto diversi aspetti.
Il filtro FIR è facile da progettare
É sempre stabile 
E evita distorsioni di fase
Ma è utile soprattutto nei casi in cui vogliamo riprodurre un segnale audio dopo di filtrare. Nel nostro caso, come vogliamo solo analizzare se è femminile o maschile, conviene utilizzare un filtro IIR, perche
Ha tagli di banda nitidi ed esponenziali
E si può ottenere i stessi risultati con ordine inferiore.**



---
Para nuestro caso, tenemos las voces masculinas que van desde los 80 a 140 Hz aproximadamente el armonico fundamental, por lo cual usaremos un filtro passa bajo, usamos este ya que se requeria de un mayor orden para hacer un pasa banda. Para el caso de las mujeres, la frecuencia fundamental va desde los 180 a 250 Hz, para este rango usaremos un filtro passa banda.

**Per il nostro caso, abbiamo le voci maschili che vanno dai 80 ai 140 Hz per l'armonico fondamentale, pertanto utilizzeremo un filtro passa basso. Abbiamo scelto questo tipo di filtro perche era necessario un ordine maggiore per realizzare un passa banda.
Per le voci femminili, la frequenza fondamentale va dai 180 ai 250 Hz; per questo intervallo utilizzeremo un filtro passa banda.**




---
Como decidimos que nuestros filtros van a ser del tipo IIR, ahora debemos diseñarlos, para esto lo podemos hacer por el metodo directo o indirecto, en nuestro caso elegimos el segundo, por cual, primero debemos encontrar el filtro analogico y despues transformarlo a digital.

**Per progettare i nostri filtri IIR, si puo fare con il metodo diretto o indiretto, per il nostro caso abbiamo scelto il secondo. Quindi prima dobiamos trovare il filtro analogico y dopo trasformarlo in digitale**




## Jerry
Per la scelta del filtro ci siamo guidati dal seguente diagramma:

Nel nostro caso il triplo ripple era accettabile dato che vogliamo solo differenziare le voci, non abbiamo bisogno di una regione di transizione così stretta da richiedere un filtro ellittico.

Inoltre, per poter distinguere bene la prima e la seconda armonica è importante che non ci sia ripple nella banda di attenuazione, per cui alla fine abbiamo optato per il filtro Chebyshev.

------------------------------------------------------------------------------------------------------------------------------

Abbiamo scelto filtri analogici Chebyshev di Tipo I per alcune caratteristiche vantaggiose:

**Transizioni più veloci:** i filtri Chebyshev raggiungono l'attenuazione voluta con meno poli rispetto ad altri, quindi le transizioni tra banda passante e di attenuazione sono più ripide.

**Ordine minore:** grazie alle transizioni più veloci, possiamo ottenere le prestazioni volute con filtri di ordine inferiore. Meno poli e zeri equivalgono ad una minore complessità computazionale.

**Risposta non piatta:** i filtri Chebyshev presentano ondulazioni in banda passante. Ma dato che vogliamo solo separare le frequenze vocali maschili e femminili, non è necessaria una risposta perfettamente piatta.

**Ricci sulla banda passante:** gli "scalini" nella risposta in frequenza ci aiutano ad attenuare meglio le frequenze indesiderate al di fuori della banda vocale di interesse.

**Difficoltà di progettazione:** l'unico svantaggio è che i filtri Chebyshev sono più complessi da progettare rispetto ad altri, ma con MATLAB questo non è un problema.

In sintesi, i vantaggi in termini di prestazioni e complessità computazionale superano gli svantaggi, rendendo i filtri Chebyshev una scelta ideale per la nostra applicazione.

----------------------------------------------------------------------------------------------------------------------------

Nel programma, prima viene effettuata la registrazione della voce, che passa attraverso il filtro femmile/maschile. Se l'uscita supera una certa soglia, la voce può essere sia maschile che femminile, e non è silenzio. Successivamente passa dal filtro maschile e se c'è un armonico sopra la soglia, la voce è maschile.

Per quanto riguarda le funzioni MATLAB utilizzate:

 - [n,Wn] = cheb1ord(Wp,Ws,Rp,Rs)
	 - Questa funzione ci permette di determinare l'ordine minimo necessario per un filtro Chebyshev di Tipo I, dati i parametri di progettazione.
	- Wp e Ws sono le frequenze di passa-banda e stop-banda. Rp e Rs sono le ondulazioni massime ammesse in banda passante e stop-banda. La funzione restituisce l'ordine minimo n.

- [b,a] = cheby1(n,Rp,Wn,'bandpass')
	- Progetta un filtro Chebyshev di Tipo I di ordine n, con ondulazione di banda passante Rp e frequenza di taglio Wn. Il tipo 'bandpass' specifica appunto un filtro passa-banda.

- audiorecorder(fs_audio,16,1)
	- Crea un oggetto registratore audio con frequenza di campionamento fs_audio, 16 bit per campione e 1 canale mono.

- recordblocking(recorder,6)
	- Avvia la registrazione audio dal registratore per 6 secondi.

- getaudiodata(recorder)
	- Ottiene i dati audio registrati come vettore di campioni.

- filter(b,a,audioData)
	- Filtra il segnale audio contenuto in audioData utilizzando la risposta in frequenza definita dai coefficienti b e a.

In questo modo applichiamo il filtraggio progettato con le specifiche desiderate al segnale audio acquisito.


## Luis 2
---
Como ideas futuras, tuvimos pensado combinar este proyecto con uno anterior nuestro en el cual en base a distribuciones probabilisticas, detectamos el idioma de un texto o de un audio, tambien, una vez detectado el idioma se podria mejorar el proyecto actual modificando la frecuencia de los filtros ya que cada idioma, varia un poco el rango de sus frecuencias fundamentales de habla. Tambien nos preguntamos si se podria detectar el hablante en funcion solo de la frecuencia y no se puede, si queremos implementar esta ultima funcion, seria necesario analizar otros factores, como se hace hoy en dia, como la entonacion, el ritmo, la duracion de las pausas y otras cosas.

**Como idee future, abbiamo pensato di combinare questo progetto con uno dei nostri progetti precedenti, nel quale, basandoci su distribuzioni probabilistiche, abbiamo rilevato la lingua di un testo o di un audio. 
Una volta rilevata la lingua, potremmo migliorare il progetto attuale modificando la frequenza dei filtri, perche ogni lingua varia l'intervallo delle sue frequenze fondamentali del parlato.
Anche, noi abbiamo cercato si e possibile rilevare il parlante solo in base alla nostro frequenza, ma non é possibile, per questo, dobbiamo implementare funzione come l'intonazione, il ritmo, la durata delle pause e altre caratteristiche.**























