

## UART - Errores de desfasaje en los relojes.

![[Pasted image 20230511091749.png|500]]
- Se mal interpreta el bit de stop y el de start produciendo la perdida de todo el paquete.
- El desfase en el ejemplo es menor que 5%

## UART - Ruido
Para evitar ruidos hay que trabajar con margen de ruido
![[NMOS y PMOS#Margen de ruido]]

## Caracteristicas funcionales
![[Pasted image 20230511094044.png|400]]
### Procedimiento de conexion
![[Pasted image 20230511094118.png|400]]

## BUS
- *BUS:* Grupo de conductores en paralelo que interconectan dos o ams dispositivos de una red
- *BUS serial:* Bus para la comunicacion serial entre dos o mas dispositivos 
- En ambas se necesita una interconexion cableada entre los dos dispositivos.
## Configuracion
### Velocidad
*Baudio:* Metrica que marca los bit por segundo
*Duracion de un bit:* $T=DuracionBit=1/Velocidad(bps)$
*Velocidades del protocolo UART:* 2400, 4800, 9600, 19200, 38400, 76800 y 153600 baudios
### Paridad
![[Pasted image 20230511095451.png|200]]
### Especificaciones
- Bits a transmitir
- Velocidad
- Paridad
- Bits de parada
*IMPORTANTE:* Ambos equipos deben tener la misma configuracion.
### Ejemplo
![[Pasted image 20230511095708.png|400]]
## Ejemplo de comunicacion con UART
![[Pasted image 20230511094930.png]]
- Para saber que el bit de arranque es un bit de arranque y no es ruido, se tiene un clock 16 veces mas rapido que muestrea que este bit sea 16 veces 0.

