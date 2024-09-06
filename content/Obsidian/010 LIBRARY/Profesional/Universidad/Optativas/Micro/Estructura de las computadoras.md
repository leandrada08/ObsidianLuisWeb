
## Partes de una computadora
- CPU
- Memoria
- Entrada y Salidas
![[Pasted image 20230317174948.png]]

### CPU
Manipula los datos de la memoria
La CPU es basicamente una maquina de estado finito que sigue la secuencia $$Leer-->Decodifica-->Ejecuta$$
Cuando hablamos de ejecuta, lo que puede hacer la cpu es leer, escribir datos de memoria, recibir, enviar datos a I/O y realizar operacions logica aritmeticas.
Esta compuesta por:
- Unidad de control: Maquina de estado finito
- Camino de datos: Registro, Alu, interconexiones
![[Pasted image 20230317184708.png|450]]
![[Pasted image 20230317184828.png|500]]
#### Conceptos importantes
##### ALU
Una ALU (Unidad Lógica Aritmética, por sus siglas en inglés) es un componente fundamental en un microprocesador, que se encarga de realizar operaciones aritméticas y lógicas en los datos que se procesan. La ALU es la unidad que ejecuta las operaciones fundamentales, como sumar, restar, multiplicar y dividir, así como también operaciones lógicas como AND, OR, NOT, entre otras.
Esta operacion depende de la senial de control que le demos(c3 en la grafica)
En la grafica a continuacion se puede ver 2 registros que guardan valores que entraran a la ALU y su valor se guardara en L.
![[Pasted image 20230317173718.png|250]]
##### BUS
Un BUS, por su parte, es un sistema de interconexión utilizado en los microprocesadores para transferir datos entre diferentes componentes, como la memoria, la ALU y otros dispositivos de entrada y salida. El BUS es un conjunto de cables y líneas de control que permiten que los datos sean enviados y recibidos en diferentes direcciones dentro del microprocesador.
![[Pasted image 20230317174051.png]]
La grafica muestra como se puede subir y bajar datos de un bus. En este caso cuando algunas de las entrada de OE=1 se sube datos al bus y cuando LD=1 se baja datos del bus a los respectivos registros.
##### Banco de registros
Un banco de registros es un conjunto de registros de alta velocidad que se utilizan para almacenar temporalmente datos y resultados intermedios en un microprocesador. Los registros son un tipo de memoria interna de alta velocidad que se utilizan para realizar operaciones aritméticas y lógicas en los datos que se procesan.
El banco de registros se utiliza para almacenar los operandos de las operaciones que realiza la ALU, y los resultados intermedios y finales. Los registros se organizan en grupos o bancos, cada uno de los cuales puede contener varios registros. El número de registros en un banco puede variar según el diseño del microprocesador.
El acceso a los registros es muy rápido, ya que se encuentran ubicados en el chip del microprocesador, lo que permite un acceso casi instantáneo a los datos almacenados en ellos. Además, el banco de registros permite que el microprocesador realice varias operaciones simultáneas, lo que puede mejorar significativamente su rendimiento.
![[Pasted image 20230317174642.png|300]]
- Las entrada SEL(elije el registro), WR(Escribir) y RD(Leer) son las entradas de control
	- SEL requiere $log2(N)$ cantidad de lineas



### Memoria
Es como una gran tabla unidimensional
- Una direccion de memoria es un indice de la tabla
![[Pasted image 20230317175214.png|75]]
Tipos de memoria:
- RAM(Acceso aleatorio)
	- SRAM: Estatica(el contenido se mantiene indefinidamente con Vcc), hecha con ffs, baja densidad, alto consumo, cara y rapida
	- DRAM: Dinamica(se necesita resfrecar regularmente), hecha con capacitores, alta densidad, bajo consumo, barata, lenta
- ROM(Acceso no aleatorio)
	- Dispositivos de estado solido(Discos,cintas,CD)
#### SRAM y DRAM
Ambas funcionan igual solo que en la DRAM tenemos 2 entradas extras de control que indica si estamos trabajando con la parte baja o alta la misma
![[Pasted image 20230317175845.png]]
- A: Busca los datos
- WE: Indica si se desea escribir
- OE: Indica si se desea leer
- D: Salida y entrada de datos
Las entradas de control que dije en DRAM se llaman CAS y RAS
### Interfaz Memoria-CPU
Se conecta las entradas de control de la memoria con registros del CPU con BUSES
![[Pasted image 20230317180401.png|400]]
En la figura se puede ver 1 bus de direccion(Addres bus), 1 de dato(data bus) y 3 de control(los 3 inferiores)
- MAR: Contiene la direccion de los datos
- MDR: Contiene los datos
*Registros adicionales:*
- PC: *Direccion* proxima instruccion
- IR: Intruccion actual
### Entrada/Salida
Son los dispositivos que permiten que el microprocesador se comunique con el mundo exterior. Se controlan leyendo y escribiendo registro.
#### Digitales
Normalmente se pueden configurar como entrada y salida. Se agrupan en conjuntos de 8, 16 o 32 entradas/salidas(puertos GPIO)
*Entrada:* El valor de tension en un terminal del dispositov se traduce en el estado de un bit en una direccion de memoria determinado
*Salida:* El estado de un bir de una direccion de memoria determinada se traduce en el valor de tension de un terminal del dispositivo.
#### Analogicas
Comunmente los terminales son entrada o salida, dificil que sea un mismo terminal para ambos. Se puede remplazar una salida por una digital y un PWM
Los valores en los registros se traducen a un valor proporcional.
#### Implementacion de entrada/salida
- Como lazo de polling permanente
- Cada n intrucciones, reviso una bandera
- Senial externa, provoca salto a rutina servicio de interrupcion
- Periferico transfiere datos directamente a memoria
- IOP con programa preparado por CPU

## Lenguajes de programacion
### Lenguaje de maquina
Instrucciones tal como son cargadas en memoria y leidad por el CPu
- Expresador como cadenas de 0 y 1
### Lenguaje ensamblador
Escritas en codigo Mnemotecnico
- Correspondencia uno a uno con LM
- Es necesario traducirlas antes de ejecutarlas
- Ensamblador=Traductor. Traduce las instrucciones y las ejecuta
- Cuando debemos darle instrucciones especificas al traductor se usan las directivas
	- Las directivas son instrucciones especiales que se utilizan para configurar el entorno de programación y definir cómo se compila y se ejecuta el código del programa. Las directivas se escriben en el código fuente del programa y se procesan durante la compilación para generar el código ejecutable.
#### Directivas vs intrucciones
Imagina que estás construyendo una casa y tienes dos tipos de herramientas: herramientas básicas, como martillos, clavos y destornilladores, y herramientas especiales, como sierras eléctricas y taladros. Las herramientas básicas son como las instrucciones en un microprocesador. Son las herramientas que utilizas para construir cosas específicas, como paredes y techos. Las herramientas especiales, por otro lado, son como las directivas en un microprocesador. Son herramientas que utilizas para configurar el entorno de trabajo, como preparar el terreno, nivelar la superficie, y así sucesivamente.
En un microprocesador, las instrucciones son las herramientas básicas que se utilizan para ejecutar las operaciones de bajo nivel, como sumar, restar y almacenar datos. Las directivas, por otro lado, son herramientas especiales que se utilizan para configurar el entorno de programación y definir cómo se compila y se ejecuta el código del programa.
##### Algunas directivas
- .cpu cortex-m4
	- Indica para cual procesador esta escrito el codigo
- .syntax unified
	- Usa notacion para codigo THUMB2
- .thumb
	- Emsambla el codigo usando instruccione THUMB
- .section
	- .text
		- memoria ROM
	- .data
		- Memoria RAM
- .word / .hword /.byte
	- Almacena contantes en memoria en 4,2 y 1 byte
- .align
	- Realinea el codigo
- .pool
	- *completar*
- .space n
### Lenguaje superior
A diferencia del lenguaje de maquina y ensamblador,  este es igual para todas las maquinas. En estos codigos, luego de escribirlo necesitamos traducirlo a lenguaje esamblador o de maquina, para esto hay 2 tipos de forma de hacerlo
#### Compilador vs interprete
Un compilador y un intérprete son programas que se utilizan para traducir código de programación escrito en un lenguaje de alto nivel a código de máquina que puede ser ejecutado por un ordenador.
Un compilador es un programa que traduce el código de un lenguaje de alto nivel en un archivo ejecutable que puede ser ejecutado directamente por la CPU del ordenador. El compilador traduce todo el código del programa de una sola vez y genera un archivo ejecutable independiente del código fuente. Cuando se ejecuta un programa compilado, el ordenador no necesita el código fuente original, ya que todo el código se ha traducido y se ha incorporado en el archivo ejecutable.
Por otro lado, un intérprete es un programa que ejecuta el código de un lenguaje de alto nivel línea por línea en tiempo real. El intérprete lee cada línea del código fuente, la traduce a código de máquina y la ejecuta inmediatamente. A diferencia del compilador, el intérprete no genera un archivo ejecutable independiente y necesita el código fuente original para poder ejecutar el programa.
La principal diferencia entre un compilador y un intérprete es que el compilador traduce todo el código de una sola vez y genera un archivo ejecutable independiente, mientras que el intérprete traduce y ejecuta el código línea por línea en tiempo real. Además, el compilador es capaz de generar un código ejecutable más rápido y eficiente que el intérprete, ya que puede realizar optimizaciones y análisis en el código completo del programa. Sin embargo, el intérprete es más fácil de depurar y modificar, ya que no requiere la compilación del código cada vez que se realiza un cambio.



## [[ISA]]

## Tipos de arquitecturas
### Harvard
Memoria de intrucciones separada de memoria de datos
- No se puede cambiar el programa
- Al trabajar en paralelo es mas rapida
### Von Newman
Es la mas usada, unifica las memoria
- Permite cambiar el programa con el concepto de *programa almacenado*
## Tipos de escritura
### Bid-endian
- Byte mas significativo en la direccion baja
- Mas facil de leer para los humanos
### Little-endian
- Byte menos significativo en la direccion baja
- Mas facil de operar para las maquinas
![[Pasted image 20230317185457.png|300]]









#### Observaciones
- Los programa se pueden ver como datos, entonces otros programas los pueden manipular(*Concepto de programa almacenado*)