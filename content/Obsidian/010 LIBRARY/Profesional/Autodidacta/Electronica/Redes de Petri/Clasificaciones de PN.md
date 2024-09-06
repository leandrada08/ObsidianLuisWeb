# Clasificaciones de PN

## Clases de redes Petri
- Una PN es *ordinaria* si el peso de sus arcos es siempre uno
- Una PN es *pura* si no existen auto bucles
	- Un auto bucle es un par lugar y transición donde el lugar p es el lugar de entrada y salida de la transición t


## Criterios topológicos

- $ºt$ = lugares de entrada antes de t

- $tº$ = lugares de salida posteriores a t

- $ºp$ = transiciones de entrada antes de p

- $pº$ = transiciones de salida posteriores a p

## Subclases de PN
Estas clasificaciones fueron realizadas por Murata y Pessen en https://ieeexplore.ieee.org/abstract/document/24143. Hasta el momento no existía una técnica eficiente para el análisis de una PN general. Sin embargo, tales técnicas están disponibles para analizar un subconjunto de PN. En esta sección, se presentan dichas subclases de PN
Se clasifican las redes en:
- Maquina de estado
- Grafico de marcados
- Red de libre escogencia
- Red de libre escogencia extendida
- Red de escogencia asimétrica

### Maquina de estado(SM)

Es una PN ordinaria tal que cada transición t tiene exactamente un lugar de entrada y uno de salida, es decir:$$ºt=tº=1$$![[Pasted image 20230201173250.png]]

### Grafico marcado(MG)

Es una PN ordinaria tal que cada lugar p tiene exactamente una transición de entrada y una transición de salida, es decir:$$ºp=pº=1$$![[Pasted image 20230201173427.png]]

### Red de libre elección(FC)

Es una PN ordinaria tal que cada arco es único arco de salida de un lugar o único arco de entrada en una transición, es decir:$$p1º\bigcap p2º\neq0=>p1º=p2º=1$$

![[Pasted image 20230201174524.png]]

### Red de libre elección extendida(EFC)

Es una PN ordinaria tal que cada arco que comparte transición o lugar con otro arco, tiene que compartir lugar de salida con la misma cantidad que el otro arco al igual que compartir transición de entrada con la misma cantidad de arcos. Es decir: $$p1º\bigcap p2º\neq0=>p1º=p2º$$

![[Pasted image 20230201175950.png]]

### Red de libre elección asimétrica

Igual que la de libre elección extendida solo que ahora no hace falta que compartan lugar y transición con la misma cantidad de arcos.$$p1º\bigcap p2º\neq0=>p1º\subset p2º or p2º\subset p1º$$![[Pasted image 20230201180312.png]]

## Referencia 
- [[Bases de Redes de Petri]]