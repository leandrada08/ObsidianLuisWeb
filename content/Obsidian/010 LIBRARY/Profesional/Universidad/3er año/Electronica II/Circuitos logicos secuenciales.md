
## Introducción a los Circuitos Lógicos Secuenciales

Los circuitos lógicos secuenciales son componentes fundamentales en la electrónica digital que incorporan elementos de memoria para almacenar información sobre el estado anterior del sistema. A diferencia de los circuitos lógicos combinacionales, que producen salidas basadas únicamente en las entradas actuales, los circuitos lógicos secuenciales tienen en cuenta el estado previo para determinar la salida actual. Esto los hace esenciales para la construcción de sistemas secuenciales y dispositivos de almacenamiento de información.

## Elementos Básicos de los Circuitos Lógicos Secuenciales

Los circuitos lógicos secuenciales incluyen los siguientes elementos:

1. **Elementos de Memoria**: Estos elementos, como biestables (flip-flops), registros, y memorias, almacenan información sobre el estado anterior del sistema. Pueden ser elementos de almacenamiento de un solo bit o de múltiples bits.

2. **Combinacional (Combinational Logic)**: Los circuitos combinacionales están interconectados con los elementos de memoria y determinan la lógica que se ejecuta en función de las entradas actuales y el estado anterior.

3. **Entradas (Inputs)**: Son las señales que ingresan al circuito lógico secuencial y afectan el comportamiento de la máquina.

4. **Salidas (Outputs)**: Representan la información que la máquina produce en función del estado actual y las entradas.

5. **Reloj (Clock)**: El reloj es una señal periódica que sincroniza las operaciones del circuito lógico secuencial. Las operaciones se realizan en los flancos (subida o bajada) del reloj.

## Diseño de Circuitos Lógicos Secuenciales

El diseño de circuitos lógicos secuenciales implica los siguientes pasos:

1. **Definición de Requisitos**: Identificar las necesidades y el comportamiento del sistema, incluyendo las entradas, salidas y las secuencias de operación.

2. **Diseño de la Lógica Combinacional**: Crear circuitos combinacionales que determinen cómo el sistema responde a las entradas y al estado anterior.

3. **Selección de Elementos de Memoria**: Elegir los elementos de memoria adecuados (por ejemplo, biestables) y diseñar la estructura de registro que almacene el estado anterior.

4. **Implementación y Conexión**: Diseñar circuitos lógicos secuenciales y conectar los elementos de memoria, la lógica combinacional y las entradas/salidas.

5. **Simulación y Verificación**: Utilizar herramientas de simulación para verificar el diseño y asegurarse de que el circuito funcione correctamente.

## Aplicaciones de Circuitos Lógicos Secuenciales

Los circuitos lógicos secuenciales se utilizan en una amplia variedad de aplicaciones, incluyendo:

- **Microprocesadores y Microcontroladores**: En estos dispositivos, se utilizan circuitos lógicos secuenciales para implementar la lógica de control de la CPU y los registros de trabajo.

- **Memorias Digitales**: Las memorias RAM y ROM utilizan circuitos lógicos secuenciales para leer y escribir datos.

- **Sistemas de Comunicación**: Los circuitos lógicos secuenciales se utilizan para codificar y decodificar datos en sistemas de comunicación digital.

- **Sistemas de Control**: Los sistemas de control industriales y automatizados utilizan circuitos lógicos secuenciales para regular procesos y controlar dispositivos.

- **Sistemas de Almacenamiento**: Los dispositivos de almacenamiento, como discos duros y unidades flash, emplean circuitos lógicos secuenciales para acceder y almacenar datos.

Los circuitos lógicos secuenciales son vitales para el funcionamiento de sistemas digitales y su diseño es un componente clave en la electrónica digital y la ingeniería de sistemas.


## Logica secuencia vs logica combinacional
Los *sistemas combinacionales*, su salida solo depende de la entrada actual, basicamente su salida es funcion de una combinacion de las entradas actuales
![[Pasted image 20230321084154.png|500]]
Los *sistemas secuenciales(ss)* son sistemas donde la entrada depende de las entradas actuales y de las entradas anteriores, estas entradas anteriores formaran el *estado interno*
![[Pasted image 20230321084335.png|550]]
![[Pasted image 20230321084409.png|500]]
donde Xu son las entradas actuales y Su el estado interno([[Sistema de control]],variables de estado)
### Sistemas secuenciales asincronicos y sincronicos
![[Pasted image 20230321084645.png]]
Los sistemas secuenciales se dividen en dos categorías principales: sistemas secuenciales síncronos y sistemas secuenciales asíncronos.
Los **sistemas secuenciales síncronos** utilizan una señal de reloj para coordinar la operación de los elementos de memoria en el circuito. *La ventaja de los sistemas secuenciales síncronos es que son más rápidos y precisos que los sistemas asíncronos, ya que el reloj asegura que todos los elementos se actualicen en el mismo momento*. Sin embargo, los sistemas síncronos también pueden ser más complejos y costosos debido a la necesidad de un oscilador de reloj.
Los **sistemas secuenciales asíncronos** no utilizan una señal de reloj y en su lugar se basan en la lógica combinacional para controlar el flujo de datos. La ventaja de los sistemas secuenciales asíncronos es que son más simples y económicos que los sistemas síncronos, ya que no requieren un oscilador de reloj. Sin embargo, los sistemas asíncronos son más propensos a errores y pueden ser más lentos que los sistemas síncronos debido a la necesidad de propagación de señales.
**En resumen**, las ventajas de los sistemas secuenciales síncronos son su velocidad y precisión, mientras que las ventajas de los sistemas secuenciales asíncronos son su simplicidad y bajo costo. La elección entre ambos tipos dependerá de las necesidades específicas del sistema y de los recursos disponibles.
