# Correccion del factor de potencia
Se basa en reducir al maximo la energia reactiva que hay en los conductores para aprovechar mejor la potencia demandada al sistema, ya que demandamos potencia aparente que esta esta compuesta por reactiva y activa pero esta ultima es la unica que realiza trabajo.

## Como se corrige el factor de potencia 
Agregando elementos reactivos en paralelo al sistema, el elemento que se agregue debe ser del opuesto del del sistema, comunmente como en nuestro sistema tendremos muchos transformadores y motores, casi siempre se aplica una correcion con capacitores en paralelos



## Diferencia entre el factor de potencia y el coseno de $\phi$ 
 El coseno de $\phi$ es el angulo entre la tension y la corriente po cual muchas veces tambien sastiface la ecuacion $$FP=\frac{P}{Q}$$
Donde Fp es el factor de potencia. Cuando tenemos cargas no lineales(Como son los dispositivos realizados con semiconductores) el factor de potencia es distinto al coseno de $\phi$. 



## Beneficios de la correccion del factor de potencia 
- Reduccion de la seccion de los conductores
- Reduccion de la caida de tension en los conductores
- Disminucion de las perdidas por efecto joule
- Aumento de la potencia disponible en la instalacion



## Compensacion del coseno de $\phi$ para cargas no lineales 
Si tenemos cargas no lineas, para corregir el coseno de $\phi$ primero hay que filtrar los armonicos 



## Tipos de compensacion 
### Compensacion global
#### Desventaja
- La corriente reactiva esta presente en todo el circuito 
- La perdidas por efecto joule en cable no disminuye
### Compensacion por zona
#### Desventaja
- Disminuye pero no desaparece la perdidas por efecto joule
- La corriente reactiva esta presente en cada circuito
### Compensacion individual
Esta es la mejor



## Modos de compensacion 
Nuestra demanda de potencia reactiva puede o no tener muchas flutuaciones, es por ello que hay que elegir entre 2 compensaciones
### Compensacion fija
- Proporciona un suministro de potencia reactiva constante al circuito 
### Compensacion variable
- Se utiliza cuando la potencia reactiva tiene muchas fluctuaciones
- Se adapta en cada momento a la potencia del circuito
- Dificil de instalar



## Compensacion en motores 
- Para motores menores a 10kW ---> Qc=0,7.So
- PAra motores mayores a 10kW ---> Qc=0,8.So
Donde $So=\sqrt{3}.Un.Io$ 
Donde Io=0,23.In


