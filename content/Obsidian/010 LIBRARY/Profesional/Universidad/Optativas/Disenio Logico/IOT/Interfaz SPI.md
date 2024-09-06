---
cards-deck: Profesional::Universidad::Optativas::Disenio Logico::IOT::SPI
---

El protocolo de comunicación SPI (Serial Peripheral Interface) es un protocolo de comunicación serie utilizado para la transferencia de datos entre dispositivos electrónicos. Es ampliamente utilizado en la comunicación entre microcontroladores, sensores, actuadores y otros dispositivos periféricos. No es un estandar
![[Pasted image 20230523082204.png]]

## Hardware
En el protocolo SPI, hay dos tipos de dispositivos: 
- El maestro (master)
- El esclavo (slave). 

### Cables #tarjeta-anki 
- *MOSI:* Master output, slave input
- *MISO:* Master input, slave output
- *SCK:* Serial clock
	- Para sincronizar la transferencia
- *SS:* Slave select
	- Para seleccionar el esclavo
^1705479813443

### Conexiones entre dispositivos #tarjeta-anki 
- El maestro y el esclavo tienen un registro interno de desplazamiento por los cuales se envian y se reciben los datos
![[Pasted image 20240103104552.png]]
![[Pasted image 20230523083310.png|500]]
Hay que tener en cuenta que hay 2 tipos de conexiones
- FULL DUPLEX: Sincrono 4 cables
- HALF DUPLEX: Sincrono 3 cables
En el segundo caso, el cable MOSI y MISO son uno solo
^1705479813449



## Comunicacion
El maestro es el dispositivo que inicia y controla la comunicación, mientras que los esclavos son los dispositivos que responden a las solicitudes del maestro.
El maestro controla la comunicación enviando una señal de reloj (SCLK) y una señal de selección de dispositivo (SS) a los esclavos. La señal de reloj sincroniza la transferencia de datos entre el maestro y el esclavo, mientras que la señal de selección de dispositivo se utiliza para indicar qué esclavo debe recibir o enviar datos en un momento determinado.

1. El MASTER abitlita la linea SS del SLAVE seleccionado
2. La transferencia se hace entre registros que se actualizan con el SCLK


## Observaciones
- Non é presente un protocollo di comunicacione
- La frequenza de trasmessione dipende de master e de slave


| Comunicacion | Ventajas | Desventajas |
| ---- | ---- | ---- |
| SPI | - Alta velocidad de transmisión (hasta 10 Mbps)<br> - Simplicidad y flexibilidad del protocolo <br> - Bajo consumo de recursos <br> - Posibilidad de encadenar varios dispositivos en serie | - Requiere más líneas de señal (4 o más)<br> - No tiene direccionamiento ni comprobación de estado <br> - No soporta el cambio dinámico del rol del maestro <br> - El reloj del maestro no puede ser más rápido que el del esclavo |
