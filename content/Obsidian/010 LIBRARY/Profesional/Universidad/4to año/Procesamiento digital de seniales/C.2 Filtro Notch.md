Los filtros Notch son unos filtros rechaza-banda especiales que permiten eliminar una frecuencia en concreto. el uso de filtros notch, especialmente el filtro notch puro, es ampliamente aceptado en aquellas aplicaciones donde se requiere eliminar una componente frecuencial concreta como, por ejemplo, las interferencia de 50Hz procedentes de lineas electricas.

## Filtros Notch analogicos
La funcion de transferencia tipo  notch de segundo orden esta dada por la expresion
![[Pasted image 20230203194641.png]]
Donde wz es la frecuencia del cero de trasmision y w0 es la frecuencia natural del filtro donde se encuentra los polos del mismo. comparando estas dos frecuencia, pueden suceder 3 cosas
- wz=w0 --> filtro notch puro
![[Pasted image 20230203194748.png]]
- wz>w0 ---> Filtro notch pasa bajos
![[Pasted image 20230203194820.png]]
- wz<w0< ---> Filtro notch pasa altos
![[Pasted image 20230203194912.png]]
### Disenio de filtro analogico Notch
Este se puede implementar con componentes activas, pasivas o como la cascada de 1 filtro pasa bajo y 1 pasa alto
#### Con Amplificador Operacional
![[Pasted image 20230203195251.png|700]]
Suponemos el capacitor y encontramos las resistencias
#### Con componentes pasivos
![[Pasted image 20230203195445.png]]
![[Pasted image 20230203195448.png]]

## Filtros Notch Digitales
A diferencia de los filtros analogicos aqui trabajamos con frecuencia digital, por lo que hay que ubicar los polos y los ceros en el plazo Z. Los ceros se ubicaran sobre el circulo de radio 1 y los polos en la misma frecuencia pero sin tocar el circulo de radio 1
.![[Pasted image 20230203200107.png]]
Al colocar de esta manera los polos y los ceros, logramos que la respuesta en frecuencia se mantenga casi invariante para todas las frecuencias distintas a la seleccionadas, para ver esto, aplicamos el metodo grafico para calcular la magnitud.
![[Pasted image 20230203200253.png]]
Donde esto se cumple para casi todas las frecuencias, salvo cuando nos acercamos a las singularidades.
### Calculo de frecuencia digital con la frecuencia analogica
Sabemos que el semi eje real positivo del plano z representa a las frecuencia digital 0(0 grados) y el semi eje real negativo del plano z representan a la frecuencia fs/2(180 grados). 
Dada una frecuencia f=f1 que deseamos filtrar, para saber en que frecuencia digital se encuentra solo debemos aplicar regla de 3 simples y la obtenemos.
Dada una funcion de transferencia generica en el plano z de segundo orden
![[Pasted image 20230203200837.png]]
Donde $c1=e^{j.\phi c}$  donde $\phi c$ es la frecuencia digital expresada en radianes y $p1=\alpha .e^{j.\phi c}$  donde $\alpha$ es la cercania entre el cero y el polo, la cual adoptaremos como 0.95 comunmente. Trabajando esta expresion llegamos a
![[Pasted image 20230203201344.png]]
donde $wo=\phi c$ y $a=\alpha$ 

![[Pasted image 20231112195350.png]]