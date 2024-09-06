
# ISA ARM Cortex M4
Los procesadores de la familia ARM son conocidos por su bajo consumo de energía y su alta eficiencia energética, lo que los hace especialmente adecuados para dispositivos móviles y embebidos.
Cortex M es una familia de microcontroladores ARM diseñados específicamente para aplicaciones embebidas que requieren una baja potencia y un alto rendimiento en tiempo real. Estos procesadores se utilizan comúnmente en dispositivos como sensores, medidores y controladores de motor.
Cortex M3 es un miembro de la familia Cortex M y es conocido por su alto rendimiento en tiempo real y su bajo consumo de energía. Cuenta con una arquitectura de procesador de 32 bits y es adecuado para aplicaciones que requieren una alta capacidad de procesamiento en tiempo real.
Thumb 2, por otro lado, es una extensión de la arquitectura ARM que permite el uso de instrucciones de 16 bits para reducir el tamaño del código y mejorar el rendimiento en dispositivos con memoria limitada. Esta extensión también mejora la eficiencia energética al reducir el número de ciclos de reloj necesarios para ejecutar las instrucciones. En resumen, Thumb 2 es una tecnología de compresión de código que ayuda a mejorar el rendimiento y la eficiencia energética en dispositivos con recursos limitados.
El Cortex M4 es otro miembro de la familia de microcontroladores Cortex M de ARM. Al igual que el Cortex M3, cuenta con una arquitectura de procesador de 32 bits y es conocido por su alto rendimiento en tiempo real y su bajo consumo de energía. Sin embargo, el Cortex M4 ofrece varias mejoras con respecto al Cortex M3, incluyendo:
-   Una unidad de coma flotante integrada (FPU) que permite la realización de operaciones de punto flotante de manera más eficiente y rápida.
-   Soporte para instrucciones DSP (Digital Signal Processing), que son útiles en aplicaciones que requieren el procesamiento de señales en tiempo real, como audio y video.
-   Soporte para el muestreo de señales y la conversión analógico-digital (ADC), que son útiles en aplicaciones de sensores y adquisición de datos.
![[Pasted image 20230318121007.png]]

- De los dos operandos que van al ALU, uno siempre pasa por el barrel shifter
- Cuando sale la dirección de M al MAR, puede guardarse en banco de registros.
- Se incluye un multiplicador y divisor en Hw.
## Registros
16 registros, 12 de uso general, PC, LR y PSR(contiene N,Z,C,V)
![[Pasted image 20230318115426.png|200]]
## Memoria
El compilador divide la memoria de datos en tres fragmentos:
- Static: Area de datos estaticos utilizada para variables globales
- Heap: Area de datos dinamica utilizada con las primitivas *malloc* y *free*
- Stack: Area de datos dinamica utilizada para variable locales y llamadas a procedimientos
### Mapa de memoria
El mapa de memoria de un microcontrolador es una representación de cómo se organizan y se acceden a las distintas áreas de memoria del microcontrolador. El mapa de memoria describe cómo se divide la memoria del microcontrolador en distintas regiones o secciones y cómo se utilizan esas regiones.
El mapa de memoria es importante para el desarrollo de software de microcontroladores, ya que permite a los desarrolladores de software entender cómo se utilizan las distintas áreas de memoria y cómo se accede a ellas. Por ejemplo, el mapa de memoria puede indicar dónde se ubican las variables del programa, los registros, las interrupciones, el código del programa, los datos de entrada/salida, entre otros.
### Unidades direccionables
Tenemos bytes(8 bit), media palabra(2 bytes) y palabra(4 bytes)
## Barrel Shiffter
El barrel shiffter nos permite multiplicar por 1,x2,x4,x8,x16 de manera inmediata
![[Pasted image 20230318121347.png|200]]

## Instruccion
### Ciclo de instrucciones
![[Pasted image 20230317180728.png|500]]
### [[Paralelismo]]

### Que debe contener cada intruccion?
![[Pasted image 20230317181114.png|400]]
1. Que operacion realizar(Op-Code)
2. Donde guardo el resultado(Operando 1)
3. Donde estan los operandos(Operandos 2 en adelante)
4. Donde esta la proxima instruccion(siguiente linea de codigo)
- Atras del op-code va el Label. Un label se utiliza para crear una referencia a esa posición en el código
- Al final de la instruccion va el comentario con //
#### Segundo operando flexible
En una instrucción de procesador, el segundo operando flexible se refiere a la fuente de datos o dirección que puede ser especificada de varias maneras, según el modo de direccionamiento utilizado.
El primer operando suele ser el destino de los datos, es decir, la ubicación en la que se almacenará el resultado de la operación. El segundo operando puede ser el origen de los datos, es decir, la ubicación desde la que se leerán los datos a operar.
El segundo operando flexible permite una mayor flexibilidad en la forma en que se especifica la ubicación de los datos. Por ejemplo, en una instrucción de "MOV" (mover), el segundo operando flexible puede especificarse de diferentes maneras, como una dirección de memoria directa, una dirección basada en un registro, una dirección indexada, etc.
El uso de un segundo operando flexible puede mejorar la eficiencia del código y reducir la complejidad de la programación, ya que permite a los programadores utilizar una amplia gama de modos de direccionamiento según las necesidades de la aplicación.
##### Que es el barrel shifter y como influye en op2
El barrel shifter es un bloque de hadware que se encarga de multiplicar el op2 por 1,2,3,4,5,... lo cual hacer que el op2 sea flexible, ya que puede hacer operaciones de desplazamiento sin pasar por la ALU
- Como usar esto→R2,LSL #3
### Clases de intrucciones
- Movimientos de datos: Siempre tiene una fuente y un destino
	- Load: Carga de datos de memoria
	- Store: Cargo datos en memoria
- Procesamiento: Opera varios operando y los guarda en un lugar de destino
	- add, sub, shift, etc.
- Control de flujo de intrucciones: Saltos, altera el flujo de control normal.
	- Pueden ser condicionales o incondicionales
- Miscelaneas: Otras funciones no encasillas en los tipos anteriores
### PSR
Registro de condicion. Esta compuesto por banderas que indican como fue el ultimo resultado(negativo, si hubo residuo, si fue 0,etc)
- Esto nos permite usar saltos con condiciones
En nuestro micro esta compuesto por (N,Z,V,C)
- Carry(C):Residuo
- Zero(Z): =0
- Negative(N):<0
- Overflow(V):El resultado no puede ser representado en la cantidad de BIT
*Observacion:* No todas las banderas modifican en PSR

## Modos de direccionamiento
Los modos de direccionamiento en un microprocesador se refieren a la forma en que la CPU accede a los datos o instrucciones almacenados en la memoria o en los registros internos del microprocesador. Son diferentes para cada tipo de ISA.
Existen varios tipos de modos de direccionamiento en los microprocesadores, entre ellos:
1.  Modo de direccionamiento implícito: este modo se utiliza cuando la dirección de memoria se encuentra implícita en la operación que se está ejecutando. Por ejemplo, la instrucción "CLC" (limpiar el flag de acarreo) no requiere una dirección de memoria, ya que la operación se aplica directamente al registro de flags de la CPU.
2.  Modo de direccionamiento inmediato: este modo se utiliza cuando los datos se encuentran en la misma instrucción que se está ejecutando. Por ejemplo, la instrucción "MOV AX, 1234H" mueve el valor inmediato 1234H al registro AX.
3.  Modo de direccionamiento de registro: en este modo, la dirección de memoria se especifica utilizando el contenido de uno de los registros de la CPU. Por ejemplo, la instrucción "MOV AX, BX" mueve el contenido del registro BX al registro AX.
4.  Modo de direccionamiento de registro indirecto: en este modo, se utiliza el contenido de un registro como dirección de memoria. Por ejemplo, la instrucción "MOV AX, [BX]" mueve el valor almacenado en la dirección de memoria contenida en el registro BX al registro AX.
5.  Modo de direccionamiento indexado: en este modo, se utiliza un registro como índice para acceder a una dirección de memoria. Por ejemplo, la instrucción "MOV AX, [SI+10H]" mueve el contenido de la dirección de memoria resultante de sumar el contenido del registro SI más el valor 10H al registro AX. 
6.  Modo de direccionamiento rotativo: en este modo, se utiliza un registro como contador para acceder a una dirección de memoria que se va rotando. Por ejemplo, la instrucción "MOV AX, [BX+SI]" mueve el contenido de la dirección de memoria resultante de sumar el contenido del registro BX más el registro SI rotado al registro AX.



