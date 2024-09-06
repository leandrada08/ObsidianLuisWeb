
## Introduccion
Microcontrolador capaz conectarse a una red WiFi o crear la suya propia 
- 4 puertos GPIO 
- VCC 3,3V 
- Tierra
- Enable
- Reset
- Antena
- GPIO-1 -> Tx 
- GPIO-3 -> Rx
![[Pasted image 20230613095209.png]]
## Configuracion
1. Reseteo del módulo: *AT+RST\r\n* 
2. Acceso al router para establecer la conexión : AT+CWJAP=””,”” \r\n 
3. Conexión con el website : AT+CIPSTART=“”,””,\r\n  Type es TCP 4. Especificación del número de bytes a enviar  AT+CIPSEND=\r\n 5. Envío de datos en formato JSON para almecenamiento en el website  “/ferry/fpga/add?data1=&data2=” \r\n