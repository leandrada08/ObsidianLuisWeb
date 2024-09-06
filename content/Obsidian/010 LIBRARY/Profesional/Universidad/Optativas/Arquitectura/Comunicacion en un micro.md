


## ![[PROFES~1/UNIVER~1/UNISA/Sistemi di interfaccia/BUS#BUS para Computadoras]]



## Esquemas tipicos de un sistema de I/O
### Clasico
![[Pasted image 20230606231251.png]]
Se uso desde 1998 hasta 2008
- *Arquitectura de 3 buses*
- Con distintas frencuencias que se conectaban entre si mediante puentes
	- Los dispositivos mas rapido se conectaban al puente *Nortbridge*
	- Los dispositivos mas lentos se conectaban al punte *Southbridge*

### Moderno
Desde 2008, los procesadores de intel integraron dentro del mismo chip el controlador de memoria y de PCIe
- Aumentaron la complejidad del procesador
- Aumenta el ancho de banda y sobre todo la escabilidad
- Ya no hubo necesidad del Northbridge
- Reemplazaron el Southbridge
![[Pasted image 20230606231943.png]]
![[Pasted image 20230606232027.png]]

### System On a Chip
#### Esquema
![[Pasted image 20230606232125.png]]

#### Conexiones
Muy populares en los procesadores mas nuevos
- Definen los controladores y capa fisica
- Suelen ser *paralelos*, con una topologia que coencte todos contra todos

### Infinity fabric de AMD
Criterio fundamental: *escalabilidad*
- No tiene limitacion en cuanto a cantidad o tipo de dispositivo conectados.
- No tiene limitacion en cuanto a la topologia de red. Tiene un fabrica
Es sincronico, tiene su propio clk independiente de la frecuencia del core.
- 2 Planos de comunicaciones: SDF(datos) y SCF(Control)

### Advanced Interface Bus de Intel
- Bus paralelo muy ancho
- Sincronico, punto a punto, en configuracion Master- Slave

### AMBA de ARM
Estandar abierto. Es un conjunto de varios protocolos:
- APB ( Advanced Peripheral Bus ): usado para dispositivos más lentos y/o simples.
- AHB ( Advanced High performance Bus ): es usado en los diseños más pequeños. 
- AXI ( Advanced eXtensible Interface )): usado en los de mayor performance.

## Otros buses/ interfaces actuales
- *CXL*:
	- Diseñado para ser usado en datacenter
	- Conecta multiples CPU con multiples dispositivos, todos bajo un mismo espacio de memoria unificado
	- Agrega una cpaa de funciones sobre PCIexpres 5.0
	- Esta recibiendo muy buena aceptacion en la instrucion con nuevas versiones completamente compatibles
- *NVLink:* De NVIDIA
	- 3ra generacion (2020), promete 600 GB/s para conectar sus GPUs(4x mas rapido que PCIe 5.0)
	- Serial, de multiples Ianes, usa una topologia mesh

### Universal Chiplet Interconnect Express(UCIe)
Nueva propuesta de estandar para conexiones die-to-die(2022)
- Basado en buses exitentes: PCIe y CXL(no reiventar la rueda)
- Objetivos:
	- Amplicar el ecosistema de chiplets disponibles
	- Convertirse en universa, como USB o PCIe
	- Ser muy personalizable y adaptable. Tambien apra conexiones off-chip

### Conexiones de gran escala
Las supercomputadoras o los datacenter de gran escala necesitan ademas otro tipo de conexiones.
- Basadas en topologias tipo crossbar, que evolucionan en complejos toroides 3D
- Hay varios tipos de interconeciones, siendo la mas popular *Infiniband*
	- Aunque cada vez se va imponiendo la simpleza de Ethernet

## Comparacion de buses vistos
![[Pasted image 20230607113235.png]]



