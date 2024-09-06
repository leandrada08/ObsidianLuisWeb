El C de CMOS hace referencia a la combinacion de las tecnologias MOS para conseguir lo mejor de cada una
- El Cmos seguira funcionando aunque arriba o abajo haya mas Mosfet en paralelos, ya que esto solo hace que la resistencia interna disminuya y que el capacitor aumente(Cuando hablo de la cantidad de transistores es para hacer referencia al ancho que le damos a estos)
	- Al igual que no importa la naturaleza de cada uno para ser compatibles, esto solo modificaria el punto donde haria el corte
	- Esto hace que esta tecnologia sea muy robusta

## Inversor CMOS

![[Pasted image 20230227195202.png]]
Se combinan los inversores NMOS y PMOS poniendolos de carga a uno con el otro
De esta manera se logra:
- Buen nivel de bajo
- Buen nivel de alto



## Compuertas no inversoras
- Mas complicada que las inversoras
- Se obtienen con 2 inversores
## NOR Y NAND
### NAND
![[Pasted image 20230227195619.png]]
### NOR
![[Pasted image 20230227195635.png]]
## Potencia
**Introducir foto de porque solo hay potencia en las transiciones(celular)**
La corriente en un [[Capacitores]] es $i=C.\frac{dV}{dt}$ ---> $Pot=i(t).Vdd$ --->$E=C.Vdd^2$ 
Lo cual es lo mismo que la energia en un capacitor pero multiplicado por 2 por los 2 ciclos de carga y descargas
- Por lo tanto la potencia necesario de una fuente para un sistema de estos es $Pot=f.\alpha.C.Vdd^2$
	- Este $\alpha$ hace referencia a la probabilidad de cambiar de estado, ya que no siempre esta cambiando de estado
	- Podemos ver que la potencia depende de C, entonces podemos hacer menos ancho el mosfet para simular paralelismo de los mismos y que este mas grande la capacidad
		- Esto significa que al hacer mas chico todo, ocupa menos potencia, por esto podemos hacer en un celular lo mismo que en una computadora basicamente
	- Tambien podemos hacer que la potencia sea menor disminuyendo la tension de entrada
### Consumo dinamico de potencia
Se debe a la conmutacion $Pt=Cpd.Vcc^2.f$
- C capacitor de los mosfet
En este caso se deja de consumir potencia estatica ya que no hay camino directo entre alimentacion y gnd


## Logica combinacional
Se hace basicamente combinando redes pull up o pull dowm. Hay distintas redes de este tipo dependiendo el tipo de transistor que ponemos y como lo ponemos
- Siempre necesitamos colocar la red dual para evitar cortocircuito
![[Pasted image 20230309130316.png]]
### Red de pull dowm con NMOS
![[Pasted image 20230309130401.png]]
### Red de pull up con PMOS
![[Pasted image 20230309130419.png]]
## Adaptacion de celdas
Cuando tenemos muchas compuertas en serie, muchas veces tenemos que colocar a una compuerta 10 a la salida, esto hace que sea el sistema sea mas lento, para evitar esto tenemos que conectar varios inversos en serie para hacer una transicion mas amena