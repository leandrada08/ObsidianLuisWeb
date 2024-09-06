# Introduccion a VHDL
*VHDL:*
*V*ery high speed ICs
*H*ardware
*D*escription
*L*anguage
Significa que atravez de un lenguaje describo un hardware.
Los 2 estandarizados por la IEEE son VHDL y Verilog
## VHDL sintetizable
Hay que tener en cuenta que no todo el codigo que escribimos es sintetizable, esto significa que no todo el codigo que escribimos se implementa en la arquitectura de la FPGA
![[Pasted image 20230323093224.png|500]]
- La gran mayoria de instrucciones que no se implementan se usan para testear y para simular
### Herramientas de sintesis
Se pueden distinguir en:
- Codigo de VHDL
- Retricciones temporales
- Atributos de seniales
- Librerias de componentes de FPGA
#### Implementacion de distintos componentes
##### Formato de un componente
![[Pasted image 20230323094516.png|500]]
- Cada archivo .vhdl es un componente en FPGA
*Partes:*
- Entity: Define entradas y salidas
- Architecture: Como se comporta el componente
##### Multiplexor
![[Pasted image 20230323094335.png]]
##### FFs
![[Pasted image 20230323094413.png]]

## Flujo de disenio FPGA
![[Pasted image 20230323095706.png]]
- Especificacion: Lo que deseamos hacer basicamente
- Front-end: Aqui se escribe el codigo en VHDL, se compila y se verifica 
- Back-end: Sintetizo y optimizo el codigo

