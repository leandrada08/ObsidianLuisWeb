# Arduino
![[Pasted image 20221013004848.png]]
#### USB plug(PC+alimentacion)
Sirve para pasar el codigo fuente desde la computadora como tambien para alimentar a la placa
#### External Power Supply(Alimentacion)
Sirve solo de alimentacion
#### Digital
Cuenta con pines digitales que 5V(1) a 0V(0)
Estos pines cuentan con un modulador de ancho de banda PWM para conseguir valores intermedio
#### Analogico
Tiene una desde 0 a 3V que en el codigo van de 0 a 1023 bit para representar estos valores de voltaje
#### TRasmisor de datos
Cuenta con un trasmisor y receptor serial de datos(TX y RX)

## Software
El codigo consta de 2 partes: Void Setup y Void loop
### Void Setud
Se ejecuta una sola vez y se usa para definir pines
#### Funciones usadas
- Pin Mode(numeroPin,Estado)
	- El estado va en imput o output dependiendo como trabajara el pin
### Void loop
Se ejecuta como un ciclo infinito, aqui va el codigo que buscamos que nuestro arduino ejecute
#### Funciones usadas
- Delay(tiempo)
	- El tiempo esta en mili segundos

