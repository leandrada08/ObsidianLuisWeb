- El esquematico nos dice como estan conectado los transistores
	- Hoy en dia es posible darlo con codigo como VHDL o Verilog
- La mascara tiene mas informacion que el esquematico
	- Ya que la primera nos dice no solo como estan conectado sino tambien la longitud de los cables, el tamanio de los transistores, etc.
- Hay cierto tipo de interfaces que no nos sirven los esquematicos, si o si necesitamos la mascara porque juega un papel importante en como estan ordenadas las componentes
	- Ejemplo: Puerto USB

## Proceso de fabricacion de un sistema integrado
1. CAD
2. Disenio
3. Fabricacion
4. Encapsulamiento

- Nosostros solo veremos el CAD y el disenio


## Proceso de fabricacion
1. *Material base*
	- Se arranca desde el material base que suele ser una oblea de silicio
2. Operacion sucesivas de colocacion de material y remocion selectiva
	- La colocacion del material se hace en la oblea entera
	- Luego se hace la remocion selectiva que es basicamente sacar el material de donde no queremos que este
### Transferencia de un patron
-  Litografia
-  Crecimiento de oxido
-  Material fotosensible
-  Mascara
-  Exposicion
-  Revelado
-  Remocion
-  Lavado
![[Pasted image 20230305114607.png]]
a. Oxidacion
b. mascara y exposicion
c. Revelacion
d. Remocion
e. Lavado
f. Final

#### Oxidacion
Se oxida con oxido, se lo puede hacer con oxidacion humeda o seca. Ambas funcionan de la misma manera
![[Pasted image 20230305114750.png]]
*Oxidacion humeda:* Rapida y gruesa $Si+2H2O-->SiO2+2H2$
*Oxidacion seca:* Lenta y delgada $Si+O2-->SiO2$

#### Remocion
Se hace con acidos, hay 2 tipos
A. Isotropica
b. Anisotropica
![[Pasted image 20230305115509.png]]

#### Colocacion de impurezas
- *Difusion*
	- Se puede hacer con fuente ilimitada o con fuente limitada
	- ![[Pasted image 20230305115629.png|400]]
- *Implatantacion de iones*
	- ![[Pasted image 20230305115710.png]]
	- La ventaja es que con este metodo sabemos cuantos portadores tendremos
	- La desventaja es que dania la barra de silicion
- *Deposicion*

## Fabricacion de una resistencia
![[Pasted image 20230305121543.png|500]]
## Fabricacion de un transistor
![[Pasted image 20230305121553.png|300]]![[Pasted image 20230305121709.png|300]]