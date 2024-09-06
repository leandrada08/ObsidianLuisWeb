
## Proposta di Progetto: CPU RISC-V a Ciclo Singolo

### Obiettivo

Progettare e implementare una CPU con architettura RISC-V in grado di eseguire un sottoinsieme critico di istruzioni con un Ciclo per Istruzione approssimativamente uguale a 1 (CPI=1).

### Ambito

La CPU supporterà:

- Istruzioni di riferimento alla memoria: lw, sw
- Istruzioni aritmetico-logiche: add, sub, and, or, mul
- Istruzioni di salto: beq

### Sfide di Implementazione

- Ottenere che il percorso dei dati consenta di completare qualsiasi istruzione in approssimativamente un solo ciclo
- Sincronizzare adeguatamente i componenti sequenziali e combinazionali
- Minimizzare il ritardo massimo all'interno del percorso critico
- Verificare esaustivamente la logica mediante simulazione

### Punti Salienti

Il design si baserà su:

- Percorso dati stile RISC puramente combinazionale
- Banca di registri con 2 porte di lettura, 1 porta di scrittura
- Unità di controllo
- Accessi separati alla memoria delle istruzioni e dei dati
- Un'ALU con ottimizzazione vista nelle lezioni per implementare le operazioni di add e mul

Per consentire il raggiungimento dell'obiettivo di CPI=1.

Successivamente, il design sarà migrato a un'implementazione segmentata a più fasi utilizzando il pipeline.

![[Pasted image 20231203222412.png]]

### Migrazione al Pipeline

Una volta completata la CPU a ciclo singolo, il design sarà migrato verso un'architettura segmentata a più fasi (pipeline), includendo:

- Fasi di Fetch, Decode, Execute, Memory Access e Write Back
- Registri e segnali di controllo aggiuntivi per sincronizzare l'avanzamento delle istruzioni
- Logica di inserimento di bolle per la gestione dei rischi

### Gestione dei Rischi

Saranno adottate le tecniche necessarie per risolvere i diversi tipi di rischi:

**Rischi Strutturali**: risorse funzionali separate per ogni fase.

**Rischi di Dati**: inoltro degli operandi e dei risultati per il forwarding.

**Rischi di Controllo**: predizione dei salti.

In questo modo sarà possibile mantenere il pipeline in avanzamento continuo e sovrapporre l'esecuzione di diverse istruzioni.




![[Pasted image 20231203213225.png]]
