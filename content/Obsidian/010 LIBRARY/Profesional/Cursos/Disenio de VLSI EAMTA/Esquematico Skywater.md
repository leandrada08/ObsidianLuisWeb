
## Nuestro disenio
Lo haremos con the skywater, ellos nos permiten hacer el disenio con codigo abierto y nos dan algo parecido a una placa, la cual ya tiene varias componenentes para poder probar mejor nuestro chip
- La contra es que las herramientas dadas por the skywater son muy dificiles

## Instalacion maquina virtual
Go to https://www.virtualbox.org/wiki/Linux_Downloads for Linux downloads or to https://www.virtualbox.org/wiki/Downloads for generic downloads. Install the software as recommended on the official website according to your operating system. If there is some launching error, please make sure that hardware virtualization is enable on BIOS.

## Instalar Icdesign
- Hay que agregar a nuestra maquina vistual el archivo dentro de la carpeta icdesign icdesing-1.16-windows

## Abrir el programa
### Esquematico
Para entrar al esquematico hay que entrar a la carpeta SCH dentro de icdesign, aqui creamos las carpetas de las componentes que vamos a trabajar y luego hay que abrir el terminal e introducir el codigo *xschem_design*
- Aqui adentro tenemos que armar nuestro circuito, para ello hay un par de atajos que nos facilitan todo
- ![[Pasted image 20230309123721.png]]
	- Observacion, cuando colocamos componentes tenemos 3 carpetas importantes,
	- ![[Pasted image 20230309123810.png]]
		- La que esta marcada nos sirve para introducir pmos y nmos
		- La primera para componentes basicos
		- La ultima para componentes creador por nosotros
#### Generar simbolo
PAra simbolizar un componente creado por nosotros debemos colocar en *symbol-->make symbol from schematic*
Esto nos generar un archivo tipo .sym, el cual si abrimos podemos modificar su forma con las siguientes reglas
![[Pasted image 20230309124017.png|300]]
#### Simular el esquematico
Para simular un nuevo archivo que seria el tb de este, aqui armar el circuito con generadores necesarios y luego hay que generar una componentes del tipo *netlist_not_shown.sym* 
Aqui debemos introducir un codigo del tipo

	name=SIMULATION only_toplevel=false
	
	value="
	
	* Circuit Parameters(incluyo los parametro del circuito)
	.param vdd = 1.8
	.param vss = 0.0
	.param Tclk = 10n
	.options TEMP = 65.0
	
	* Include Models
	.lib ~/skywater/skywater-pdk/libraries/sky130_fd_pr_ngspice/latest/models/corners/sky130.lib TT
	* OP Parameters & Singals to save(Guarda todos los datos definidos)
	.save all
	*Simulations
	.control(comienza la simulacion)
		tran 0.01u 100n(nos indica el tiempo cada cuanto toma una muestra y el tiempo total de muestreo)
		setplot tran1
		plot v(vin) v(vout)+2
	reset
		dc V6 0 1.8 0.01
		setplot dc
		plot vin vout ylabel vout xlabel vin
		set filetype = ascii
		write dcsweep.raw
	.endc(Termina la simulacion)
	.end(Termina el codigo)
### Observaciones del simulador esquematico
- iopin nos genera pin en el dispositivo(Usar para generar los pines del dispositivos)
- lab.wire nos conecta 2 pines(Usar para generar pin hijo)
- lab.pin nos conecta 2 pines(Usar para generar el pin padre)
- Para definir un fuente alterna *value="TipoFuente(VInicial VFinal Delay TiempoSubida TiempoBajada TiempoActivo Periodo) DC ComponenteDeDC AC *
	- Ejemplo *value="PULSE({vdd} 0 0.0 1p 1p {Tclk/4} {Tclk/2}) DC 0 AC 0"*
- Para definir una fuente continua *value=DC{vdd}*
- Hay que fijarse el W y el L de cada transistor(estos definiran mucho del mismo)
	- Para modificarlo solo hay que entrar en las propiedades de estos mismos