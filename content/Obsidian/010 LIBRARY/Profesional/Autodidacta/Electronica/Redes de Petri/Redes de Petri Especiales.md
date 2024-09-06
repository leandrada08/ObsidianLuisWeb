# Redes de Petri especiales
## Redes de Petri Cronometrada
Para analizar el rendimiento asociado con el tiempo, se introduce el tiempo en la PN. El tiempo se puede asocia con lugares, transiciones o ambos lugares y transiciones. Si el tiempo está asociado con lugares, entonces cuando una ficha ingrese a un lugar, la ficha debe permanecer en este lugar durante un periodo de tiempo específico. Si el tiempo está asociado con las transiciones, hay un retardo de tiempo específico para disparar la transición. A continuación se puede ver un ejemplo de transiciones con retardo.![[Pasted image 20230201182319.png]]
Un uso importante de una PN cronometrada es calcular el tiempo de ciclo en una máquina de estado(MG).

## Redes de Petri con Arcos Inhibidores
Un arco inhibidor conecta un lugar con una transición. Pictóricamente, termina con un pequeño circulo, no con una flecha. Si (p,t) es un arco inhibidor y hay fichas en p, entonces t no puede disparar. La introducción de arcos inhibidores puede aumentar la potencia de la PN, ya que usando arco inhibidor podemos modelar la prioridad en un sistema de fabricación.
![[Pasted image 20230208204853.png]]