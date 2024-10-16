- Dobbiamo avere in conto che per potere implementare un sistema RBF, dobiamos implementare le seguente operazioni
	- sub:$-$
	- pot:$^2$ 
	- sqrt: $\sqrt{}$  
	- Gaussiana
	- Comb lineal

- Tutti le operazioni lineali sono facile di risolvere, il problema è potere risolvere in manera veloce e con poco risorse la pot, sqrt e gaussiana
- Per la gaussiana è facile
	- Si puoi metere comparatore in valores de sigma, per exempio
		- sub<0,5 sigma. -> 1
		- 0,5sigma<sub< 1,5 sigma -> 0,5
		- 1,5sigma <sub< 2 sigma -> 0,25
		- sub> 2 sigma -> 0

- Dopo possiamo fare che ogni neurona avra un bit di uso, con la sua etiqueta, per potere togliare e aggiungere neuron
	- Ogni volta que sub>2sigma si incrementa il bit di uso
		- E la etiqueta serve per ordenare e sapere fino a che valore di memoria leggeremo quando facciamo la iterazione 
		- Questi bit di uso abra un valore di valita, si queste è 1 si chiama una interruzione che fai che il CPU risc-v la tolge, facendo il cambiamento bisognante

- Pensanto in tutto questo, si doveva analizare le funzione di
	- previsione di uscita
		- usa togliere -> supportato per ISA
		- usa calcolo di attivazione
			- usa distanza euclidiana -> norma -> Supportato per ISA
			- usa approssimazione gaussiana -> Supportato per ISA
		- percetron
			- usa MAC -> sopportato per ISA
	- allenamento di redi
		- usa agiungere -> Supportato per ISA
		- usa calcolo di errore
		- aggistamento di peso
			- Operazione punto -> Supportato per ISA
			- Operazione vettore per scalar -> Supportato per ISA
		- aggiustamente di radio
			- Operazione punto -> Supportato per ISA
			- Operazione vettore per scalar -> Supportato per ISA
		- aggistamento di centro
			- Operazione punto -> Supportato per ISA
			- Operazione vettore per scalar -> Supportato per ISA

- Anche si puoi aggiungere operazione di SUB e ADD vettoriales per megliorare la velocita



- Lo meglio in questo caso e fare un analisis delle istruzioni per vedere il porcentuale di ogni istruzione che hanno bisogno di cercare valore di memoria pero vedere si e megliore usare cpu con pipeline, con sistema de memoria cache e un protocolo AXi o si è meglio usare un sistema di cpu multiciclo con protocolo AXI