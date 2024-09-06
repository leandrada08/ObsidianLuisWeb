## Medicion
- Conductividad
- PH
- Oxigeno disuelto
- Turbidez
### Como medirlo
1.  Conductividad: La conductividad se puede medir utilizando un sensor de conductividad. Este sensor tiene dos electrodos separados por una distancia conocida. Cuando se aplica un voltaje a los electrodos, la corriente que fluye a través del líquido es proporcional a su conductividad. El sensor de conductividad puede ser un sensor de 2 electrodos o de 4 electrodos, dependiendo de la precisión requerida.
2.  pH: El pH se puede medir utilizando un sensor de pH. Este sensor consiste en un electrodo de vidrio que genera una señal eléctrica proporcional al pH del líquido. El electrodo de vidrio debe ser calibrado para asegurar mediciones precisas.
3.  Oxígeno: El oxígeno disuelto en el líquido se puede medir utilizando un sensor de oxígeno disuelto. Este sensor utiliza una membrana permeable al oxígeno que permite que el oxígeno disuelto en el líquido reaccione con un electrodo de platino para generar una señal eléctrica proporcional a la concentración de oxígeno.
4.  Turbidez: La turbidez se puede medir utilizando un sensor de turbidez. Este sensor utiliza una fuente de luz y un detector para medir la cantidad de luz dispersada o absorbida por el líquido. La turbidez se calcula a partir de la cantidad de luz que se dispersa o se absorbe.
### Implementacion
A los sensores explicados arriba se los puede implementar con una entrada 
#### Implementacion total
Para unir todos los sensores necesitamos un microcontrolador con 4 entrada analogicas para poder todas las seniales de los sensores y un modulo wifi integrado para poder mandar lo datos a una nube. Ademas este microcontrolador es compatible con el kit de desarrollo PICDEM PIC18, lo cual facilitaria su integracion.
El microcontrolador que cumple estas especificaciones es el PIC16F18446. Características del PIC16F18446 incluyen:
-   22 pines de entrada/salida programables.
-   10 bits de resolución de conversión analógica a digital (ADC).
-   Módulo de comunicación Wi-Fi integrado.
-   Interfaz I2C, SPI y UART.
-   Temporizador/contador de 8 bits y 16 bits.
-   Funciones de reloj interno y externo.