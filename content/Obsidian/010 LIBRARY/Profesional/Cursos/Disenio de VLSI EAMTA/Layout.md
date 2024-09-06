![[Pasted image 20230311172024.png]]


- Luego de hacer el esquematico hay que hacer el layout
- Hay tecnicas para hacer mas rapido el layout a partir del esquematico
- Luego hay que corroborar que ambos sean el mismo circuito
	- Para esto usamos el LVS(Layout vs Squematics)
	- Ambos se simulacin con Spice based engine 
		- El LVS justamente las compara a ambas spice
		- El spice crea una Netlist de ambas(codigo del circuito basicamente)

## Layer de un proceso
![[Pasted image 20230307095131.png]]
### Leyer de N-Well
Suponiendo una oblea tipo p, los transistores de canal n son fabricado directamente en el oblea; el canal p son fabricado en un "n-pozo"
- Procesos con n-bien sobre p-sustratos se llaman nwell procesos
- El sustrato también se conoce como bulto o cuerpo
- El pozo N forma un diodo (normalmente con polarización inversa, para evitar circulacion de corriente) con el sustrato
- Fuera de donde estan los dispositivos(region no activa) tenemos que poner un oxido que funcione de aislante
	- En cierto sistema se hace un agujero en el silicio y se oxida ahi adentro
	- No hace falta que le indique donde colocaremos esto, los fabricantes ya sabe, *solo le debemos indicar la zona activa*

### Poly Layer
Nos inidica como tenemos que hacer los layer de polisilicio
- No hay que indicar donde colocaremos el oxido, ya que el fabricante sabe que tiene que ir abajo del polisilicio
- Cuando lo colocamos hay que buscar que sobresalga un poco con respecto al ancho de los semiconductores tipo P o tipo N
- ![[Pasted image 20230307100348.png]]


### Metal layers
Esto hacen las conexiones entre las componentes y entre las diferentes capas
- Tener tantas capas de metal nos sirven para hacer circuitos complejos mucho mas facil
- Parecido a lo que hacemos cuando realizamos una pcb y la hacemos de 2 capas
	- *Reglas Lucas:* Cuando hacemos varias capas del metal, comunmente se hace que cada capa vaya en una direccion perpendicular a la siguiente, de esta manera de mas facil hacer el layout sin cruzarnos

#### Metal resistance
$R=\frac{Longitud}{Ancho}\frac{\rho}{t}$
El cociente entre longitud y ancho se mantiene siempre y cuando mantengamos la relacion entre ellos, esta relacion es de cuadrados, por eso que se analiza resistencia por cuadrados. A esto llamamos relacion de aspecto $RA=\frac{W}{L}$
![[Pasted image 20230307101650.png]]
Esto nos sirve para saber el ancho y la restividad del metal.

#### Metal capacidad
Tenemos 2 tipos de cpacidades, la de area y la de fringe, la de area es la ideal y la de fringe es la que ocurre por los campos electricos que viajan por fuera del area, como si fueran parasitos

#### Inductancia parasita
Son despreciables, son apreciable en chips muy rapidos. Esto puedo hacer que simule una linea de trasmision lo cual no queremos

### Capacidad de corriente
Si hacemos que corra mucha corriente podemos hacer que la pista se rompa, por lo cual como regla general, no puede circular mas de $1[mA/um]$


## Regla de disenio
El fabricante nos da regla para cubrirnos antes las imperfecciones(luz,maquinas,alineacion,etc)
Basicamente tenemos las reglas de:
- Reglas de separacion
	- Separacion minima que debe haber entre 2 layout de la misma capa para evitar que por algun defecto estos se toquen
- Reglas de tamanio minimo
	- Tamanio minomo que deben tener las vias para asegurarnos que siempre tendran contacto
- Reglas de tamanio exacto
- Reglas de cubrimiento

## Tipos de disenios
#### Botton-up
Pienso desde lo mas pequenio a lo mas grande
#### Top-Dowm
Peinso de lo mas grande a lo mas pequenio

## Celdas estandar
En la metodologia que usaremos, se basara en usar celdas estandar o tambien llamadas "Pitch" o altura fija, donde como dice el nombre, la altura sera fija y solo modificaremos el ancho
### Importante
- Debemos hacer conexcion automatica de vdd y vdd y otras seniales comunes
	- Esto reduce posibilidades de error
