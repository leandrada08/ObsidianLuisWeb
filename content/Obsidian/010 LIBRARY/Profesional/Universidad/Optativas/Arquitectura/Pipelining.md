# Pipeling
## Bases del Pipelining
Procesamiento en serie: Mejora la *productividad*
**Pipeline:** se refiere a un proceso en el que varias tareas se realizan en secuencia, donde la salida de cada tarea se convierte en la entrada de la siguiente.
**Pipelining:** es el proceso de dividir una tarea en una serie de sub-tareas más pequeñas y asignarlas a diferentes unidades de procesamiento para su ejecución simultánea.
- Es una técnica de diseño de microprocesadores que permite que varias instrucciones se ejecuten simultáneamente, dividiendo el proceso de ejecución en etapas más pequeñas y especializadas. Como la recuperación de la instrucción, la decodificación, la ejecución, el acceso a memoria y la escritura en registros.
- Permite que el procesador pueda mantener un flujo constante de instrucciones, mejorando la eficiencia y la velocidad de procesamiento.
- También puede introducir *problemas de latencia,* que se deben a la necesidad de esperar a que se completen todas las etapas del pipeline para que la instrucción se complete. 
- **La productividad de un pipeline esta limitada por la etapa mas lenta**
- **La maxima aceleracion posible es igual al numero de etapas**
- Si la duracion de la etapa no es balanceadas se reduce la aceleracion y el rendimiento
- La aceleracion tambien se reduce por tiempos de llenado y de vaciado de pipeline
### Metricas
- $Productividad=TasaDeSalida=Throughput$:Indica cuántos datos se producen en la unidad de tiempo, medido en bits por segundo
- $Aceleracion=t(serie)/t(pipe)$
- $Latencia=TtotalDemora1Tarea$
- $Eficiencia=T_{realizado}/MaxPosible$
- **Timing (Periodo del Clock):** El tiempo entre dos flancos activos del reloj..
#### Eficiencia vs Productividad
Si tengo *m* trabajadores en pipelining con una eficiencia del 100%, nuestra aceleracion es *m*
- Idealmente, en un pipeline se cumple que: $$Aceleracion=m.Eficiencia$$
- La eficiencia total no es la misma que de cada producto

### Visualizacion
![[Pasted image 20230327083315.png|500]]
- En el eje vertical se ubican los distintos puestos de trabajo.
- En el eje horizontal, el tiempo.
- Las tareas se identifican con diferentes colores (o letras o números).
- Las tareas se van desplazando por los puestos de trabajo, si es que el siguiente está disponible
- $Rendimiento=Aocupada/Atotal$
### Pipeline ideal
- Posee m etapas equilibradas, de timing igual a T.
- Ejecuta una cantidad enorme de tareas idénticas, n -> infinito.
	- Esto se denomina estado de régimen
- Latencia = mT
- Tiempo(serie) = nmT
- $Tiempo(pipeline) = (m-1)T+nT$
- Una vez que se llena, sale una tarea cada T.
- Aceleración = m/(1+(m-1)/n) -> m
- Productividad = 1/T
- Rendimiento = A / m = 100%

### Problemas de pipeline no ideales
- No contar con suficiente tareas para entrar en estado de regimen
	- En este caso hay que considerar los tiempos de llenado y vaciado
- Etapas de distintas duraciones
	- Produce cuello de botella
- Tener distinto tipos de tareas que utilicen distintas combinaciones de etapas

#### Cuello de botella
![[Pasted image 20230327092127.png|500]]
- La etapa cuello de botella es la que esta todo el tiempo trabajando
*Soluciones?*
1. Mejorar la seccion de trabajo para que demore menos
	- En este caso mejoramos la productividad y tambien la latencia
2. Duplicar la seccion de trabajo y trabajar en serie o en paralelo
	- Esta solucion mejora la productividad pero empeora la eficiencia
	- Usar en serie o en paralelo depende exclusivamente de la tarea en si
- Estas soluciones comunmente generan un nuevo cuello de botella
##### Solucion extrema 
![[Pasted image 20230327093502.png|500]]
Hay que sacar el m.c.d de las duraciones de los componentes y comprar tantas estaciones de trabajo como estas. Esto aumenta significativamente el costo
- Esta solucion se conoce como *superescalar* y se usa en micro.

#### Tareas diferentes
En estos casos las tareas no van secuencialmente por las estaciones de trabajo ni duran lo mismo en cada estacion de trabajo.
- Para estos casos, en todas las soluciones se producen choques. Este problema lo llamaremos *Riesgos estructurales*
	- Lo mas facil para solucionar este problema es que toddas las tareas pasen por todas las etapas
		- De esta manera se puede suponer que el pipeline es ideal.

### Resumen
- Hay que agregar minimo recursos
- Tareas secuencias dependientes
- Tasa de salida ideal=m.tasa(serie)
	- Si las etapass estan equilibrada y trabajando
**Desventajas:**
- La latencia aumenta con el número de etapas de la pipeline.
- Aumentan los retardos.
- Aumenta la potencia disipada.

**Ventajas:**
- En estado estacionario, el tiempo se reduce.
- El rendimiento aumenta.

## Aplicado a diseño digital

Es un error asociar el rendimiento electrónico únicamente al reloj. El throughput, que indica la cantidad de datos producidos en una unidad de tiempo, está estrechamente relacionado con la latencia y el timing. Reducir el timing al agregar más registros puede aumentar el throughput, pero también puede empeorar la latencia y aumentar la potencia disipada y el área ocupada.

Aumentar el throughput se puede lograr mediante el uso de pipelines y no necesariamente reduciendo el período del reloj, por ejemplo, mediante el uso de procesadores multicore mientras se mantiene un timing bajo. Sin embargo, esto también puede aumentar significativamente el área ocupada.

### Aplicacion a circuitos del pipelining 
![[Pasted image 20230329082936.png|500]]
Dividimos las etapas con buffers.

#### Ejemplo de Pipeline con sumadores
![[Pasted image 20230329082541.png|500]]
![[Pasted image 20230329082957.png|500]]


### Cuantas etapas de pipelining coloco?
![[Pasted image 20231129150829.png|500]]
Aumentar el tiempo de manera significativa para mejorar el rendimiento no es una estrategia sostenible. Existe un límite físico, ya que la pipeline es ventajosa siempre y cuando el camino crítico sea significativamente mayor que los retardos intrínsecos de los registros. Recordemos que el período del reloj debe cumplir con los "timing constraints". Si llegamos a esta situación límite, el período del reloj no puede disminuir de manera significativa sin perder la ventaja.

Sin pipeline, todos tenían una latencia de 1 y después de 1 ciclo de reloj, leía todos los resultados. Al introducir una pipeline, los datos se desalinean. Si necesito datos alineados y tengo etapas de pipeline, sincronizarlos puede ser complicado, o debo agregar más registros para mantener la consistencia de los datos.
Cuando aplicamos un registro, cambiamos la base de tiempo, esto tambien es un punto a tener en cuenta, por lo tanto es importante tener en cuenta esto cuando colocamos un registro para hacer pipeline

- La pipeline no es útil si no tengo un flujo continuo de datos.
- Para cada dato, siempre debo esperar la latencia inicial.
- El tiempo puede reducirse hasta el límite impuesto por los registros.
- $T_{clk} > t_{su} + t_{cq} + t_{crítico}$.


### Como se donde colocar el registro?
Cuando se crea una pipeline, es crucial preservar la consistencia de los datos intermedios, es decir, los resultados de las operaciones parciales. Introducir etapas de pipeline puede ser complicado. En máquinas de estado o Carry Look Ahead, por ejemplo, se debe tener precaución. 
Se identifican los **forward cutset** es decir, los caminos del circuito que esencialmente dividen el circuito en dos partes, cortando todos los caminos que permiten la propagación de datos de izquierda a derecha.
Tambien se puede hacer un analisis por transferencia de registros

- **Regla general:** las etapas de pipeline solo se pueden insertar a lo largo de los "feedforward cutset".
- **Cutset**: un conjunto de conexiones en un circuito que, si se interrumpen, la señal ya no puede propagarse (el circuito se corta en dos).
- **Feedforward cutset:** un "cutset" en el que todas las señales de las conexiones se propagan en una sola dirección (hacia adelante).
#### Teorema de transferencia de registros
- Se pueden transferir N registros de cada flecha entrante en un nodo de un DFG a todas las flechas salientes del mismo nodo o viceversa, sin afectar a la función original.
	- Esto es bidireccional, tambien se puede hacer a la viceversa.
	- Se puede considerar el cut-set un caso particular de este metodo
- Para aplicar este teorema a Pipeline, debemos conectar en los path de entrada la cantidad de registros de pipeline que queremos colocar en nuetro sistema y luego comenzar a moverlos
	- Esto nos ayuda a evitar problemas de coherencia
![[Pasted image 20240222112305.png]]
#### Aprendiendo a colocar un pipeline con metodo de cutset
1. Hacer nuestro diagrama de flujo
![[Pasted image 20231201141829.png]]
2. Analizar nuestros cutset
![[Pasted image 20231201141840.png]]
3. Buscar que un cutset, tal que cuando dividamos al circuito con esto, todas nuestras etapas tengas el mismo tiempo
![[Pasted image 20231201141853.png]]
4. Ver si existe otro cutse adicional para mejorar la velocidad
![[Pasted image 20231201141926.png]]
- Observacion, si tenemos una etapa que es significativamente mayor que las otras, podemos dividirla en 2. **Fine-Grain Pipelining**
![[Pasted image 20231201142141.png]]

### Problemas de pipeline
Los problemas de la pipelining son los mismo que visto en el curso de arquitectura en un micro 
![[CPU en pipelining#Problemas del procesador en pipeline]]
#### Gestion de errores en la pipeline
- Lo que hacemos es habilitar la memorizacion en cada etapa de  la pipeline si toda la pipeline para adelante esta funcionando bien, en caso de que todo no esta bien todo lo sucesivo, se frenara la pipeline, de esta manera no se pierde datos
![[Pasted image 20231201145154.png]]
- Basicamente lo que se ahce es que los registros de la pipeline solo se habiliten con valores de buen funcionamiento de etapas sucesivas.
- Esto es muy bueno, ya que para parar toda la pipeline solo ahce falta que se frene la primera etapa, entonces con que se frenen todas las etapas anteriores a la que esta funcionando mal hace que todo quede igual




# Italiano
## Basi del Pipelining

### Definizione e Concetti Base

**Pipeline:** Si riferisce a un processo in cui varie attività vengono eseguite in sequenza, dove l'uscita di ciascuna attività diventa l'ingresso della successiva.

**Pipelining:** È il processo di suddivisione di un'attività in una serie di sotto-attività più piccole e di assegnarle a diverse unità di elaborazione per la loro esecuzione simultanea.

- È una tecnica di progettazione di microprocessori che permette l'esecuzione simultanea di più istruzioni, dividendo il processo di esecuzione in fasi più piccole e specializzate. Come il recupero dell'istruzione, la decodifica, l'esecuzione, l'accesso alla memoria e la scrittura nei registri.
- Permette al processore di mantenere un flusso costante di istruzioni, migliorando l'efficienza e la velocità di elaborazione.
- Può anche introdurre *problemi di latenza,* dovuti alla necessità di attendere il completamento di tutte le fasi della pipeline affinché l'istruzione sia completata.
- **La produttività di una pipeline è limitata dalla fase più lenta.**
- **La massima accelerazione possibile è pari al numero di fasi.**
- Se la durata delle fasi non è bilanciata, si riducono accelerazione e prestazioni.
- L'accelerazione si riduce anche a causa dei tempi di riempimento e svuotamento della pipeline.

### Metriche

- **Productività (Tasso di Uscita o Throughput):** Indica quanti dati vengono prodotti nell'unità di tempo, misurata in bit al secondo.
- **Accelerazione:** $\text{Accelerazione} = \frac{t_{\text{serie}}}{t_{\text{pipeline}}}$
- **Latenza:** $\text{Latenza} = \text{TtotaleRitardo1Attività}$
- **Efficienza:** $\text{Efficienza} = \frac{T_{\text{realizzato}}}{\text{MaxPossibile}}$
- **Timing (Periodo del Clock):** Il tempo tra due fronti attivi del clock.

#### Efficienza vs Produttività

Se ho *m* lavoratori in pipelining con un'efficienza del 100%, la nostra accelerazione è *m*.
- Idealmente, in una pipeline si applica: $$\text{Accelerazione} = m \times \text{Efficienza}$$
- L'efficienza totale non è la stessa di ogni prodotto.

### Visualizzazione
![[Pasted image 20230327083315.png|500]]
- Sull'asse verticale si trovano i diversi posti di lavoro.
- Sull'asse orizzontale, il tempo.
- Le attività si identificano con colori diversi (o lettere o numeri).
- Le attività si spostano attraverso i posti di lavoro, se il successivo è disponibile.
- **Rendimento:** $\text{Rendimento} = \frac{A_{\text{occupata}}}{A_{\text{totale}}}$

### Pipeline Ideale

- Possiede m fasi equilibrate, con un timing uguale a T.
- Esegue una grande quantità di attività identiche, n -> infinito.
  - Questo si chiama stato di regime.
- **Latenza:** $mT$
- **Tempo (serie):** $nmT$
- **Tempo (pipeline):** $(m-1)T + nT$
- Una volta riempita, esce un'attività ogni T.
- **Accelerazione:** $m/(1+(m-1)/n) \rightarrow m$
- **Produttività:** $1/T$
- **Rendimento:** $\frac{A}{m} = 100\%$

### Problemi di Pipeline Non Ideale

- Non avere abbastanza attività per entrare nello stato di regime.
  - In questo caso, bisogna considerare i tempi di riempimento e svuotamento.
- Fasi di durata diversa.
  - Produce un collo di bottiglia.
- Avere tipi di attività diversi che utilizzano combinazioni diverse di fasi.

#### Collo di Bottiglia
![[Pasted image 20230327092127.png|500]]
- La fase collo di bottiglia è quella che lavora tutto il tempo.

**Soluzioni:**
1. Migliorare la sezione di lavoro per ridurre i tempi.
   - In questo caso, miglioriamo la produttività e anche la latenza.
2. Duplicare la sezione di lavoro e lavorare in serie o in parallelo.
   - Questa soluzione migliora la produttività ma peggiora l'efficienza.
   - Usare in serie o in parallelo dipende esclusivamente dall'attività stessa.
- Queste soluzioni comunemente generano un nuovo collo di bottiglia.

#### Soluzione Estrema
![[Pasted image 20230327093502.png|500]]
Bisogna prendere il m.c.d delle durate dei componenti e acquistare tante stazioni di lavoro quante queste. Questo aumenta significativamente il costo.
- Questa soluzione si conosce come *superescalare* e si usa nei microprocessori.

#### Attività Diverse

In questi casi, le attività non vanno sequenzialmente attraverso le stazioni di lavoro né durano lo stesso tempo in ogni stazione.
- Per questi casi, in tutte le soluzioni si producono conflitti. Questo problema si chiama *Rischi strutturali.*
  - La soluzione più semplice per risolvere questo problema è che tutte le attività passino per tutte le fasi.
    - In questo modo, si può supporre che la pipeline sia ideale.

### Riassunto

- Aggiungere il minimo delle risorse.
- Attività sequenziali dipendenti.
- Tasso di uscita ideale = m.tasso(serie).
  - Se le fasi sono equilibrate e funzionanti.

**Svantaggi:**

- La latenza aumenta con il numero di fasi della pipeline.
- Aumentano i ritardi.
- Aumenta la potenza dissipata.

**Vantaggi:**

- In stato stazionario, il tempo si riduce.
- Aumenta il rendimento.

## Applicato al Design Digitale

È un errore associare il rendimento elettronico unicamente al clock. Il throughput, che indica la quantità di dati prodotti in un'unità di tempo, è strettamente correlato con la latenza e il timing. Ridurre il timing aggiungendo più registri può aumentare il throughput, ma può anche peggiorare la latenza e aumentare la potenza dissipata e l'area occupata.

Aumentare il throughput si può ottenere mediante l'uso delle pipeline e non necessariamente riducendo il periodo del clock, per esempio, utilizzando processori multicore mantenendo un timing basso. Tuttavia, questo può anche aumentare significativamente l'area occupata.

### Applicazione ai Circuiti del Pipelining
![[Pasted image 20230329082936.png|500]]
Dividiamo le fasi con buffers.

#### Esempio di Pipeline con Sommatori
![[Pasted image 20230329082541.png|500]]
![[Pasted image 20230329082957.png|500]]
### Quante Fasi di Pipelining Collocare?
![[Pasted image 20231129150829.png|500]]
Aumentare il tempo in modo significativo per migliorare il rendimento non è una strategia sostenibile. Esiste un limite fisico, poiché la pipeline è vantaggiosa finché il percorso critico è significativamente maggiore dei ritardi intrinseci dei registri. Ricordiamo che il periodo del clock deve soddisfare i "timing constraints". Se si arriva a questa situazione limite, il periodo del clock non può diminuire significativamente senza perdere il vantaggio.

Senza pipeline, tutti avevano una latenza di 1 e dopo 1 ciclo di clock leggevano tutti i risultati. Introdurre una pipeline fa sì che i dati si disallineino. Se ho bisogno di dati allineati e ho fasi di pipeline, sincronizzarli può essere complicato, o devo aggiungere più registri per mantenere la consistenza dei dati.
Quando si applica un registro, si cambia la base temporale, questo è anche un punto da considerare, quindi è importante tenerne conto quando si colloca un registro per fare pipelining.

- La pipeline non è utile se non ho un flusso continuo di dati.
- Per ogni dato, devo sempre attendere la latenza iniziale.
- Il tempo può essere ridotto fino al limite imposto dai registri.
- $T_{clk} > t_{su} + t_{cq} + t_{critico}$.

### Come Si Sa Dove Collocare il Registro?

Quando si crea una pipeline, è cruciale preservare la consistenza dei dati intermedi, cioè i risultati delle operazioni parziali. Introdurre fasi di pipeline può essere complicato. In macchine a stati o Carry Look Ahead, ad esempio, bisogna fare attenzione.
Si identificano i **forward cutset**, ovvero i percorsi del circuito che dividono essenzialmente il circuito in due parti, tagliando tutti i percorsi che consentono la propagazione dei dati da sinistra a destra.
Si può anche

 fare un'analisi per trasferimento di registri.

- **Regola Generale:** Le fasi di pipeline possono essere inserite solo lungo i "feedforward cutset".
- **Cutset:** Un insieme di connessioni in un circuito che, se interrotte, la segnale non può più propagarsi (il circuito si divide in due).
- **Feedforward Cutset:** Un "cutset" in cui tutte le segnalazioni delle connessioni si propagano in una sola direzione (in avanti).

#### Teorema del Trasferimento dei Registri

- Si possono trasferire N registri da ogni freccia entrante in un nodo di un DFG a tutte le frecce uscenti dello stesso nodo o viceversa, senza influire sulla funzione originale.
  - Questo è bidirezionale, si può fare anche viceversa.
  - Si può considerare il cut-set un caso particolare di questo metodo.
- Per applicare questo teorema a Pipeline, bisogna collegare nei percorsi di ingresso il numero di registri di pipeline che vogliamo collocare nel nostro sistema e poi iniziare a spostarli.
  - Questo ci aiuta a evitare problemi di coerenza.
![[Pasted image 20240222112305.png]]
#### Imparare a Collocare una Pipeline con il Metodo del Cutset

1. Creare il diagramma di flusso.
![[Pasted image 20231201141829.png]]
2. Analizzare i cutset.
![[Pasted image 20231201141840.png]]
3. Cercare un cutset tale che, quando si divide il circuito con esso, tutte le fasi abbiano lo stesso tempo.
![[Pasted image 20231201141853.png]]
4. Verificare se esiste un altro cutset aggiuntivo per migliorare la velocità.
![[Pasted image 20231201141926.png]]
- Osservazione: Se abbiamo una fase significativamente più lunga delle altre, possiamo dividerla in 2. **Fine-Grain Pipelining**
![[Pasted image 20231201142141.png]]
### Problemi di Pipeline

I problemi della pipeline sono gli stessi visti nel corso di architettura in un micro.

#### Gestione degli Errori nella Pipeline

- Quello che si fa è abilitare la memorizzazione in ogni fase della pipeline se tutta la pipeline successiva funziona correttamente, in caso contrario si ferma la pipeline, evitando così la perdita di dati.
![[Pasted image 20231201145154.png]]
- Fondamentalmente, i registri della pipeline si abilitano solo con valori di buon funzionamento delle fasi successive.
- Questo è molto buono, poiché per fermare l'intera pipeline basta fermare la prima fase, quindi è sufficiente fermare tutte le fasi precedenti a quella che funziona male affinché tutto rimanga invariato.


## Problemi del Processore in Pipeline

I problemi che possono verificarsi si chiamano rischi e possono essere:

- **Estructurali:** Due istruzioni cercano di occupare la stessa fase.
- **Di Dati:** Bisogna aspettare che un'istruzione precedente si completi (dipendenze).
- **Di Controllo:** La decisione su quale azione intraprendere dipende da un'istruzione precedente (salti).

$$CPI_{pipeline} = CPI_{ideale} + \text{ParadasRiesgoEstructural} + \text{ParadasRiesgoDatos} + \text{ParadasRiesgosControl}$$

### Quando Fermare il Pipeline

- Se il rischio non viene risolto, bisogna **fermare il pipeline** finché il rischio non viene risolto.
  - Si dice che vengono inserite una o più "bolle" nel pipeline.

#### Come Inserire una Bolla

1. Bisogna impostare tutti i segnali di controllo del registro ID/EX a zero.
   - Questo fa sì che nelle fasi non si faccia nulla.
2. Evitare l'aggiornamento del PC e del registro IF/EX (lo faremo disattivando il clock).

### Come Risolvere Ogni Rischio

- **Estructurale**
- **Dato**
- **Control**

### Rischi Estructurali

**Condizioni per Evitare i Rischi Estructurali:**

- Memorie separate e risorse duplicate.
- Tutte le istruzioni passano attraverso tutte le fasi.
- Si utilizza solo un'unità funzionale per fase.
- Tutte le istruzioni usano la stessa unità funzionale nella stessa fase.

### Rischio di Dati

Un'istruzione dipende dal risultato di un'istruzione precedente che è ancora nel pipeline.

- Per risolvere questi rischi, bastano solo 2 bolle.
- Non abbiamo bisogno di bolle quando possiamo portare il dato durante l'esecuzione.

#### Avanzamento
![[Pasted image 20230419083611.png]]
Questo si chiama *avanzamento*. Per farlo, bisogna aggiungere molte nuove interconnessioni e più multiplexer.

- Non risolve il caso in cui un load è seguito immediatamente da un'istruzione che usa il registro di destinazione.
  - Per questo, bisogna aggiungere una bolla.

![[Pasted image 20230419084835.png]]

#### Riordinamento con Dipendenze

Cambiamo l'ordine delle istruzioni nel codice. Bisogna anche tenere presente che non tutte le dipendenze costituiscono un rischio di dati.

#### Pipeline con Avanzamento
![[Pasted image 20230419093424.png]]
- L'unità di avanzamento deve rilevare il rischio.
  - Confronta se uno dei registri letti nella fase 2 è uguale al registro scritto dall'istruzione nella fase 3.
  - E se le istruzioni nella fase 3 o 4 scrivono in un registro.
  - E solo se il registro di destinazione è diverso da zero.
  - Questo risolve il problema dello store.

### Rischio di Controllo

I salti sono quelli che determinano il flusso di controllo di un programma. La ricerca della prossima istruzione dipende dal risultato di un salto e il salto viene risolto completamente nella fase 4. Questo implica che bisogna aggiungere 3 bolle.
La risoluzione di un salto implica due compiti:
1. Determinare se **effettivamente si verificherà o meno**.
   - Per determinare se effettivamente si verificherà prima, togliamo il compito di confronto dalla ALU e mettiamo un comparatore nella fase ID. Questo ci permette di risolvere tutto il salto nella fase ID.
     - La condizione da valutare deve essere semplice?
     - Genera nuovi rischi di dati, che richiedono nuovi avanzamenti.
     - Abbiamo comunque bisogno di 1 bolla.
2. Determinare quale sia la **direzione di destinazione del salto**.

*Soluzione 1:*
Per determinare se effettivamente si verificherà prima, togliamo il compito di confronto dalla ALU e mettiamo un comparatore nella fase ID. Questo ci permette di risolvere tutto il salto nella fase ID.
- La condizione da valutare deve essere semplice?
- Genera nuovi rischi di dati, che richiedono nuovi avanzamenti.
- Abbiamo comunque bisogno di 1 bolla.

Il problema dell'alternativa precedente è che in pipeline più lunghe è molto difficile anticipare tutta la risoluzione del salto. Idealmente dovremmo cercare di fare tutta la risoluzione del salto nella fase IF, il che è molto illogico.
- Quindi **usiamo la previsione del salto**.
  - Fondamentalmente, consiste nel ricordare dove ho un salto e poi verificare se stiamo per eseguire questa istruzione.

#### Pipeline Completo
![[Pasted image 20230425134335.png]]