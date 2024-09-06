## Evolucion historica de ISAs
- 1970 - 1980 --> CISC
- 1990's - Actualidad --> RISC
### Actualidad
Hay dos ISAs dominantes
- x86_64
	- En PCs, servidores y supercomputadores
		- 99% del mercado
- ARM
	- Sistemas embebidos, celular, etc
		- 99% del mercado
	- Enrealidad son varioas ISAs
		- Thumb, Thumb-2, ARMv7, ARMv8
Estos ISAs son propiedad intelectual.
- El ISA es la interfaz mas importante en un sistema de computadoras
	- Es donde el software se encuentra con el hardware.
		- Es la capa que aisla esto 2 mundos
	- El hardware puede cambiar radicalmente, pero el codigo que se ejecutaba en la maquina de ayer tiene que ejecutarse exactamente igual en la de manania
#### Avances
Hay 2 nuevas tendencias en los ultimos anios
- ARM esta ingresando en el otro mercado
	- De la mano de procesadores M de apple
	- De la mano de Fugaku
- Hay un tercer ISA ganando mercado: *RISC-V*
	- Originado hace 10 anios en una universidad
	- Se esta acercando rapidamente a los valores de performance, costo y consumo de energia de los chips de ARM
	- Recibio grande apoyos economicos por parte de Intel.

## Que es un ISA 
Es conocido como *el Modelo del Programador de la maquina*. Es un nivel de abstraccion que permite separar el desarrollo del software del desarrollo del hardware. Es la informacion que se requiere para escribir programa para un determinado procesador.
### Componentes del ISA
Esta compuesto por 4 componentes:
#### 1. Celdas de almacenamiento
Todo ISA debe especificar sus celdas de almacenamientos(cuantas tiene, cual es el tamanio, etc.)
- Registros de proposito general y especial del CPU
- Muchas celdas de proposito general de igual tamanio en memoria
- Almacenamiento relacionado con los dispositivos de I/O
#### 2. Formatos de las intrucciones
Me indica el tamanio y el significado de cada diferente campo de las intrucciones(Basicamente el tipo de instrucciones y el tamanio de cada una)
- Modos de direccionamiento soportado
#### 3. El conjunto(SET) de instrucciones
Repertorio completo de las operaciones de la maquina. Es lo que usa las celdas de almacenamiento, formatos y resultados del ciclo de la intruccion.
#### 4. Naturaleza del ciclo de la instruccion
Cosas que se hacen independiente de la instruccion en cuestion.
- Son los detalles finos.



## Repaso
### Ciclo de instruccion
![[Descripcion funcional de un microcontrolador#Ciclo de instrucciones]]
### Niveles de abstracciones
![[Pasted image 20230331183322.png|400]]
### Contenido de una instruccion
![[Pasted image 20230331183503.png|400]]
![[Pasted image 20230331183637.png|400]]
### Clases de instrucciones
![[Descripcion funcional de un microcontrolador#ISA ARM Cortex M4#Clases de intrucciones]]
### Modos de direccionamiento
![[Descripcion funcional de un microcontrolador#Modos de direccionamiento]]






## Clasificacion de ISAs 
Se clasifican en como y donde se ubican los operandos y como estos operandos son especificados por la instruccion
- Algunos registros tienen como una "personalidad" propia.
	- PC, Acumuladores, Stack Pointer
- Hay clasificaiones basadas en las instrucciones aritmeticas que tienen dos operando y un resultado.
- ISAs de mas de 3 operandos, no se ven actualmente
*ISA de 3 operando:* Usa modos de direccionamiento tato para los operandos fuente como para el resultado
*ISA de 2 operando:* Usa un operador destino como fuente
*ISA de 1 operando:* Emplea de manera implicita un registro llamado acumulador
*ISA de 0 operando:* Se maneja comunmente con los datos que estan en la pila




### Comparacion
- 0 y 1 operando: intrucciones mas cortas
- 2 y 3 operando: performance



#### Posibles metricas
- Tamanio de las intrucciones
- Cantidad de instrucciones del ISA
- Tamanio del prograa escrito con ese ISA
- Cantidad de acceso a memoria
*Ninguna de estas es buena*
**La metrica para comparar estos son el TIEMPO**



## Pasaje de parametros entre programas
- Programa que llama a otro (*caller*)
- Programa que es llamada(*Callee*)
- Un programapuede cumplir ambos roles
*ABI:* Estandar para el uso de los registros y del mapa de memoria
	Permite a los programas interactuar eficientemente aun sin ser desarrollados ni compilados de manera conjunta
### Convencio de llamados a subrutina
Se denomina "convencion de llamadas" al subconjunto de la ABI que especifica como se pasan datos de un programa a otro
- Algunos registros deben ser preservados
	- Si un callee planea utilizar un registro, debe guardar en algun lugar de memoria su valor al incio, y restablecer este valor antes de retornar.
	- Si un callee planea utilizar un registro, no debe ser preservado entre llamadas, sebe ser consciente que otro programa podria modificar su valor.
#### Pasos
Seis pasos generales
1. El progrma caller debe poner los argumentos en algun lugar donde la subrutina callee pueda accederlo
2. El programa caller invoca a la subrutina callee
3. La subrutina calle debe reservar el espacio de memoria requerido y almacenar los registros necesarios.
4. La subrutina callee debe realizar su tarea requerida
5. La subrutina callee debe poner su resultado en algun lugar accesible por el programa caller
6. La subrutina calle debe retornar el control al punto de origen del programa caller
- El paso 3 se conoce como PROLOGO
- Los pasos 5 y 6 se conocen como EPILOGO de la subrutina
- La diferencia entre los dintintos ISAs es donde se guardara y como se guardara
### Manejo de la pila(stack)
Es el metodo estandar para pasaje de parametros entre distintos programas. 
- El stack es una fraccion de la memoria reservada para un uso especifico
- Usado para guardar el estado de una tarea en caso de excepciones o interrupciones
- Se puede manejar de manera implica o explicita(siempre tienen pila)
	- Si es explicito: Tiene un Stack Pointer(SP)
		- Tambien tiene instrucciones dedicadas: PUSH y POP
		- Algunas tambien tienen instrucciones especificas
			- CALL: Guarda el PC en stack, guarda el estado actual
			- RETURN: Restaura lo que guardo y luego restaura PC
	- Los ISA sin STACK explicito lo implementan medianteSi tiene 
		- Un registro de proposito general
		- Incrementos y decrementos de punteros
		- Lo mismo tiene que manejar el STACK, sin importar que no tenga un stack explicito



## Falacias comunes sobre ISAs
- Instrucciones mas poderosas equivalen a ams performance
	- Esto puede hacer mas lenta a la simple porque dificulta pipeline
- Usar assembler mejora la performance
	- Los compiladores modernos son bastante buenos para los procesadores actuales
#### Para que usamos asembler entonces?
- Para conocer el funcionamiento del procesador.
- Para poder diseniar un buen compilador.
- Aveces permite sacarle mas provecho al micro cuando se sabe asembler, sin necesidad de programar en el.





# De MICRO
## ISA(Arquitectura del set de instrucciones)
La arquitectura del set de instrucciones (ISA, por sus siglas en inglés) de un microprocesador es el conjunto de instrucciones que están diseñadas para ser ejecutadas por el microprocesador. El ISA define el repertorio de instrucciones que se pueden utilizar para programar el microprocesador y controlar su funcionamiento.
El ISA define la sintaxis y semántica de las instrucciones que se pueden utilizar para acceder a la memoria, realizar operaciones aritméticas y lógicas, controlar el flujo de ejecución del programa, y acceder a dispositivos de entrada/salida. El ISA también define el conjunto de registros que están disponibles para almacenar datos e instrucciones.
El diseño del ISA tiene un impacto significativo en el rendimiento y la eficiencia del microprocesador, ya que afecta la cantidad de instrucciones necesarias para realizar una tarea determinada, el tamaño de las instrucciones, el número de registros disponibles, y otros aspectos del diseño del procesador.
### RISC vs CISC
Los conjuntos de instrucciones RISC y CISC son dos enfoques diferentes para diseñar arquitecturas de microprocesadores.
*RISC, o Reduced Instruction Set Computer:* Es una arquitectura de microprocesador que se caracteriza por tener un conjunto de instrucciones pequeño y simple. En los procesadores RISC, las instrucciones se dividen en operaciones simples que se ejecutan en un solo ciclo de reloj, lo que mejora la velocidad de ejecución y reduce la complejidad del procesador. Los procesadores RISC también suelen tener una estructura de pipeline más profunda que permite ejecutar instrucciones en paralelo, lo que mejora aún más su velocidad.
*CISC, o Complex Instruction Set Computer:* Es una arquitectura de microprocesador que se caracteriza por tener un conjunto de instrucciones más complejo y variado. En los procesadores CISC, las instrucciones pueden realizar múltiples operaciones y acceder a múltiples registros en una sola instrucción, lo que reduce la cantidad de instrucciones necesarias para realizar una tarea determinada. Esto puede hacer que los programas se escriban en menos líneas de código, pero también puede ralentizar el procesador debido a la complejidad de las instrucciones.
Ambos enfoques tienen sus ventajas y desventajas. Los procesadores RISC suelen ser más rápidos y eficientes, ya que su conjunto de instrucciones es más simple y se ejecutan en un solo ciclo de reloj. Sin embargo, los procesadores CISC suelen tener un conjunto de instrucciones más completo y pueden realizar tareas más complejas en menos ciclos de reloj.
En general, el conjunto de instrucciones RISC se utiliza en procesadores para aplicaciones donde la velocidad y la eficiencia son primordiales, como en sistemas embebidos y dispositivos móviles. Por otro lado, los procesadores CISC se utilizan en aplicaciones que requieren un conjunto de instrucciones más complejo y variado, como en computadoras de escritorio y servidores.
