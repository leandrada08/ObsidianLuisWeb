**Nombre:** Luis Elian Andrada
**DNI:** 43362912

## Actividad
Análisis de Reportes
- [x] Realizar el diagrama de flujo de datos (DFG) en base al diseño entregado sin considerar los módulos VIO e ILA.
- [x] Crear un proyecto nuevo e incluir los archivos Arty_Master_tx.xdc (constraint), tb_top_phy_all.v (testbench) y top_phy_all.v (source). Nota: el resto de los archivos se incluirán en forma automática por los includes utilizados en el código (revisar los path a los archivos).
- [x] Simular el diseño sin los módulos VIO e ILA (revisar sección de simulaciones).
- [x] Crear los módulos VIO e ILA, instanciarlos y sintetizar el sistema para una frecuencia de referencia de 100MHz (revisar sección de síntesis).
- [x] Determinar el número de celdas por jerarquía y los componentes (DSP, BRAM, LUT, etc).
- [x] Implementar en FPGA y obtener la forma de ondas desde el ILA.
- [x] Analizar los caminos críticos y obtener el histograma de timing para las frecuencias de reloj de 50MHz, 100MHz y 200MHz. Nota: Generar la implementación pero no implementarlo en la FPGA.
	- [x] 50 MHz
	- [x] 100MHz
	- [x] 200MHz
	


## DFG
![[Pasted image 20240214113519.png]]


## Simulacion sin VIO y ILA
![[Pasted image 20240210205625.png]]


## 100 MHz
### Texto de sintesis
![[Pasted image 20240209214104.png]]
### Determinar el numero de celdas por jerarquia y los componentes
![[Pasted image 20240209213114.png]]

### Caminos criticos
![[Pasted image 20240209214259.png]]
### Histograma
![[Pasted image 20240210185349.png]]


## Implementacion en FPGA y formas de ondas
![[Pasted image 20240210185010.png]]


## 50 MHz
### Camino critico
![[Pasted image 20240211110931.png]]
### Histograma
![[Pasted image 20240211110818.png]]


## 200 MHz
![[Pasted image 20240405100424.png]]
![[Pasted image 20240405100640.png]]
![[Pasted image 20240405100529.png]]