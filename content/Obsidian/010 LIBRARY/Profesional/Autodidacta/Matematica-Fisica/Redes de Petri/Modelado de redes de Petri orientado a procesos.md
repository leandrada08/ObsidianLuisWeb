# Modelado de redes de Petri orientado a procesos

Al operar un *sistema de fabricación automatizado(AMS)*, es muy importante que su flexibilidad se explote lo suficiente. Durante las últimas décadas, el modelado, el análisis, la simulación y el control de AMS se han convertido en temas emergentes y han sido ampliamente estudiados.

Debido a que las redes de Petri pueden modelar bien las concurrencias, se usan ampliamente para modelar AMS para análisis, simulación y control.

Para evaluar procesos, sintetizar modelos conservativos, reversible, vivos, para modelar AMS para la prevención y evitación de puntos muertos, se usa redes de Petri orientadas a procesos(POPN)

## Método de modelado

En el modelado de sistema de eventos discretos (DES) por PN, a menudo se usan lugares y tokens para las condiciones y las transiciones se usan para la ocurrencia de eventos. Al modelas AMS por POPN, se emplean las siguientes interpretaciones para lugares, transiciones y tokens:

### Representación de lugar, tokens y transicion

#### Lugar y tokens

Un lugar representa un recuro, un estado de orden de trabajo o una operación

- Si un lugar representa el *estado de un recurso*, uno o más tokens indican que el recurso esta disponible y ningún tokens indica que no está disponible

- Si representa el *estado de la orden de trabajo*, los tokens que contiene indican que hay trabajo que esperan ser procesador y ningún token indica que no hay ningún trabajo para procesar

- Si representa una *operación*, un token muestra que se está ejecutando una operación y ningún token muestra que no se está realizando

#### Transición

Una transición representa el inicio o la finalización de un evento o proceso de operación

### Pasos a seguir para conseguir el modelo POPN

1. *Identificar las actividades y los recursos* necesarios para la producción de un artículo de cada producto

2. *Ordenar las actividades* por la relación de precedencia dada en lo planes de procesos

3. Para cada actividad, en orden:
	1. Cree y etiquete un lugar para representar el estado de esa actividad
	2. Cree una transición con arcos que entren al lugar
	3. Cree una transición que tengas arcos de entrada que sean salida del lugar
	- Cuando se ejecute la red, un token en un lugar de actividad indica que la actividad se está llevando a cabo. Multiples tokens indican la actidad que ocurre en multiplicidad

4. Para cada elemento del producto:
	1. Cree y etiquete un lugar que represente el estado de la orden de trabajo con
	2. Arcos de salida para las transiciones de inicio de la primera actividad
	3. Arcos de entrada desde la transición final

5. Para cada actividad, en orden:
	1.  Cree y etiquete un lugar para cada recurso que necesita la actividad para comenzar
	2. Conecto todos los lugares de disponibilidad de recursos apropiados de modo que haya un arco de entrada desde cada recurso hasta la transición inicial de la actividad
	3. Cree arcos de salida para conectar la transición de parada, siguiendo la actividad a cualquier lugar de recursos que represente recursos que estén disponibles al finalizar la actividad

6. Especifique la marca inicial para el sistema


## Referencia
- [[Bases de Redes de Petri]]
- [[Propiedades de la Red de Petri]]