# Bases de Redes de Petri

- Las Redes de Petri clásicas se conciben como un grafo dirigido que posee dos tipos de nodos principales: los lugares representados por círculos(plazas) y las transiciones representadas por barras rectangulares(transiciones).

- Las redes de Petri fueron utilizadas inicialmente para el análisis de algoritmos en la computación paralela o concurrente

## Elementos

Una red de Petri está representa por 4 elementos:

**Plazas:** Representa lugar , espacio y estado del sistema

**Transiciones:** Relaciona 2 plazas, son las acciones o eventos que causan un cambio de estado, ósea un movimiento de plaza.

**Arcos:** Describen el flujo del sistema, relacionan plazas con transiciones

**Tokens:** Puntos dentro del proceso, indican producto terminado, en proceso o por comenzar o en cierto estado. Básicamente indican donde se encuentra en proceso

Los Tokens permite el trabajo en paralelo, ya que puede haber casos en qué una transición unifique 2 Tokens en una plaza o que de una plaza salgan 2 Tokens

### Propiedades de los elementos

**Plazas:**

- Nombre: Nombre de la plaza

- Almacenamiento: Cantidad de Tokens que puede admitir

**Transiciones:**

- Nombre: Nombre de la transición

- Tiempo: Tiempo que impide el paso libre de los Tokens
	- Existen 2 tipos de transiciones adicionales. La transición *fuente* que es aquella que no posee un lugar de entrada y la transición sin un lugar de salida es llamada transición *sumidero*

**Arcos:**

- Peso: cantidad de Tokens que podrán pasar al mismo tiempo por un arco

## Definición de Red de Petri como una matriz

Formalmente, una Red de Petri se define como una quíntupla $$PN=(P,T,F,W,M0)$$

Donde:

- P es el conjunto de lugares(plazas)

- T es el conjunto de Transiciones

- F es el conjunto de arcos dirigidos, este conjunto es la unión de los conjuntos de arcos de lugares a transiciones y de transiciones a arcos

- W es la función de pesos de arcos

- M0 es el marcado inicial de la red

Una Red de Petri sin especificar su marcado inicial es denotada por N, una PN con un marcado inicial dado es denotado por $PN=(N,M0)$

## Reglas de disparo

El marcado de la PN cambia de acuerdo a las reglas de disparo

1. Se dice que una transición es habilitada si la capacidad de los arcos es menor a las marcas que tienen los lugares

2. Una transición habilitada puede o no ser disparada. Esto depende del tiempo de disparo y otras cosas

3. Un disparo habilitado mueve la cantidad de marcas del peso del arco.


## Casos usuales de redes Petri
### Ensamble y desamble
![[Pasted image 20230114115557.png|500]]
En el caso de la sincronización podemos ver como 2 Tokens que vienen de procesos distintos se unen luego de una transición y en el segundo el caso opuesto
### Representación de una maquina en redes Petri
![[Pasted image 20230114115328.png|500]]
La imagen anterior representa una maquina en diagrama Petri, donde A es el estado inicial o materia prima y D es el estado final o producto finalizado, las plazas C y B son los 2 estado de la máquina, cuando el tokens está en C significa que la maquina está libre y cuando está en B significa que está trabajando

## Referencia
- [[Introduccion Petri]]