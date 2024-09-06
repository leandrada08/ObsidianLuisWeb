
# Base Teoricas

## ISA RISC-V

### Introducción del RISC-V
- **Nuevo ISA:** Introducido en 2014, RISC-V es un conjunto de instrucciones (ISA) que define una arquitectura de conjunto de instrucciones, no una implementación específica.
- **Gratuito y Abierto:** RISC-V es de código abierto y gratuito. El desarrollo y las especificaciones están disponibles en [GitHub](https://github.com/riscv/).

### Características Generales
- **Basado en la Experiencia:** Aprovecha los aciertos y errores de arquitecturas previas como x86, AMD64, ARMv7, ARMv8, Thumb, Thumb2, y MIPS.
- **Modularidad:** Único ISA modular, permitiendo su uso para diversas aplicaciones al elegir las extensiones necesarias.
- **Exploración de Conceptos:** Enfocado en explorar nuevos conceptos más que en la compatibilidad con productos existentes.

#### Convenciones de Nombres de ISA
- $RV[###][abc...xyz]$
  - **RV:** ISA de RISC-V.
  - **\[\#\#\#\]:** {32, 64, 128} Ancho de registros de entero y tamaño de las direcciones de memoria.
  - **\[abc...xyz\]:** Extensiones soportadas.

#### Extensiones RISC-V
##### Estándar
- Extensiones estándar con amplia aceptación:
  - **M:** Multiplicación y división.
  - **A:** Instrucciones atómicas en memoria (para sistemas operativos).
  - **F y D:** Punto flotante de precisión simple y doble.
  - **G:** Conjunto que incluye I, M, A, F, y D.
  - **C:** Versiones comprimidas en 16 bits de I.

##### Adicionales
- Extensiones adicionales personalizadas permiten agregar funcionalidades específicas según las necesidades.

### Celdas de Almacenamiento
- **3 Operandos:** Tipo LOAD/STORE con direcciones de memoria de 32 bits (*32I*).
  - Espacio de direcciones: 4 GB.
  - Direccionable a nivel de byte.
  - Little Endian.
- **32 Registros:** x0 a x31, del ancho definido (32 en *32I*).
  - Registro x0 cableado a 0.
  - Extensiones pueden agregar registros.
- **Registro PC:** Program Counter.
- **Registros de Estado y Control:** 17 registros para monitoreo de rendimiento en *32I*.

### Formatos de Instrucciones
- Longitud fija de 32 bits independientemente del ancho del registro (32I, 64I, 128I).
- 4 Formatos Base:
  - TIPO R: Operaciones aritméticas.
  - TIPO I: Operaciones con constantes inmediatas.
  - TIPO S: Operaciones con Store.
  - TIPO U: Manejo de constantes más grandes.
![[Pasted image 20230405092632.png]]

#### Detalles de Opcodes y Formatos Adicionales
- Opcodes identifican grupos de instrucciones en RISC-V.
- Regularidad en la posición de campos simplifica la decodificación.
- Campos inmediatos siempre se extienden en signo.
- Instrucción con todos los bits en 0 o 1 es inválida para evitar errores comunes.





# Diseño general
## Analisis de nuestro ISA
### Subconjunto del ISA de RISC-V
Implementaremos la base RV32I de RISC-V que es la base de este ISA, tambien implementaremos las intrucciones de multiplicacion y una de multiplicacion y suma para poder realizar el filtro FIR. A continuacion nombrare todas las instrucciones que se implementaran y luego se las describira:
- **SHIFT**
	- SLL
	- SLLI
	- SRL
	- SRLI
	- SRA
	- SRAI
- **Aritmetica**
	- ADD
	- ADDI
	- SUB
	- LUI
	- AUIPC
- **Logica**
	- XOR
	- XORI
	- OR
	- ORI
	- AND
	- ANDI
- **Comparacion**
	- SLT
	- SLTI
	- SLTU
	- SLTIU
- **Branches**
	- BEW
	- BNE
	- BLT
	- BGE
	- BLTU
	- BGEU
- **LOADS**
	- LW
- **Store**
	- SW

### Descripcion de nuestras instrucciones

#### SHIFT
- **SLL**: Desplazamiento lógico a la izquierda. Mueve los bits de un registro (rs1) hacia la izquierda un número de posiciones especificado por otro registro (rs2), y guarda el resultado en un tercer registro (rd). Los bits vacíos se rellenan con ceros. Tiene un formato R. Por ejemplo, `SLL x1, x2, x3` desplaza los bits de x2 hacia la izquierda x3 posiciones y los guarda en x1.
- **SLLI**: Desplazamiento lógico a la izquierda inmediato. Mueve los bits de un registro (rs1) hacia la izquierda un número de posiciones especificado por un valor inmediato (imm), y guarda el resultado en otro registro (rd). Los bits vacíos se rellenan con ceros. Tiene un formato I. Por ejemplo, `SLLI x1, x2, 4` desplaza los bits de x2 hacia la izquierda 4 posiciones y los guarda en x1.
- **SRL**: Desplazamiento lógico a la derecha. Mueve los bits de un registro (rs1) hacia la derecha un número de posiciones especificado por otro registro (rs2), y guarda el resultado en un tercer registro (rd). Los bits vacíos se rellenan con ceros. Tiene un formato R. Por ejemplo, `SRL x1, x2, x3` desplaza los bits de x2 hacia la derecha x3 posiciones y los guarda en x1.
- **SRLI**: Desplazamiento lógico a la derecha inmediato. Mueve los bits de un registro (rs1) hacia la derecha un número de posiciones especificado por un valor inmediato (imm), y guarda el resultado en otro registro (rd). Los bits vacíos se rellenan con ceros. Tiene un formato I. Por ejemplo, `SRLI x1, x2, 4` desplaza los bits de x2 hacia la derecha 4 posiciones y los guarda en x1.
- **SRA**: Desplazamiento aritmético a la derecha. Mueve los bits de un registro (rs1) hacia la derecha un número de posiciones especificado por otro registro (rs2), y guarda el resultado en un tercer registro (rd). Los bits vacíos se rellenan con el bit de signo del valor original. Tiene un formato R. Por ejemplo, `SRA x1, x2, x3` desplaza los bits de x2 hacia la derecha x3 posiciones y los guarda en x1, conservando el signo de x2.
- **SRAI**: Desplazamiento aritmético a la derecha inmediato. Mueve los bits de un registro (rs1) hacia la derecha un número de posiciones especificado por un valor inmediato (imm), y guarda el resultado en otro registro (rd). Los bits vacíos se rellenan con el bit de signo del valor original. Tiene un formato I. Por ejemplo, `SRAI x1, x2, 4` desplaza los bits de x2 hacia la derecha 4 posiciones y los guarda en x1, conservando el signo de x2.

#### Aritmetica
- **ADD**: Suma dos registros y guarda el resultado en otro registro. Tiene un formato R. Por ejemplo, `ADD x1, x2, x3` suma los valores de x2 y x3 y los guarda en x1.
- **ADDI**: Suma un registro y un valor inmediato y guarda el resultado en otro registro. Tiene un formato I. Por ejemplo, `ADDI x1, x2, 4` suma el valor de x2 y 4 y lo guarda en x1.
- **SUB**: Resta dos registros y guarda el resultado en otro registro. Tiene un formato R. Por ejemplo, `SUB x1, x2, x3` resta el valor de x3 a x2 y lo guarda en x1.
####  Logica
- **XOR**: Operación lógica de exclusivo o. Solo devuelve 1 si los bits correspondientes de los dos operandos son diferentes, y 0 si son iguales. Tiene un formato R. Por ejemplo, `XOR x1, x2, x3` hace la operación x2 XOR x3 y guarda el resultado en x1.
- **XORI**: Operación lógica de exclusivo o inmediato. Solo devuelve 1 si los bits correspondientes del registro y del valor inmediato son diferentes, y 0 si son iguales. Tiene un formato I. Por ejemplo, `XORI x1, x2, 4` hace la operación x2 XOR 4 y guarda el resultado en x1.
- **OR**: Operación lógica de o. Devuelve 1 si al menos uno de los bits correspondientes de los dos operandos es 1, y 0 si ambos son 0. Tiene un formato R. Por ejemplo, `OR x1, x2, x3` hace la operación x2 OR x3 y guarda el resultado en x1.
- **ORI**: Operación lógica de o inmediato. Devuelve 1 si al menos uno de los bits correspondientes del registro y del valor inmediato es 1, y 0 si ambos son 0. Tiene un formato I. Por ejemplo, `ORI x1, x2, 4` hace la operación x2 OR 4 y guarda el resultado en x1.
- **AND**: Operación lógica de y. Devuelve 1 si los bits correspondientes de los dos operandos son 1, y 0 si alguno es 0. Tiene un formato R. Por ejemplo, `AND x1, x2, x3` hace la operación x2 AND x3 y guarda el resultado en x1.
- **ANDI**: Operación lógica de y inmediato. Devuelve 1 si los bits correspondientes del registro y del valor inmediato son 1, y 0 si alguno es 0. Tiene un formato I. Por ejemplo, `ANDI x1, x2, 4` hace la operación x2 AND 4 y guarda el resultado en x1.



#### Comparacion
- **SLT**: Establece menos que. Establece un registro (rd) a 1 si un registro (rs1) es menor que otro registro (rs2), considerando el signo, y a 0 si no. Tiene un formato R. Por ejemplo, `SLT x1, x2, x3` establece x1 a 1 si x2 es menor que x3, considerando el signo, y a 0 si no.
- **SLTI**: Establece menos que inmediato. Establece un registro (rd) a 1 si un registro (rs1) es menor que un valor inmediato (imm), considerando el signo, y a 0 si no. Tiene un formato I. Por ejemplo, `SLTI x1, x2, 4` establece x1 a 1 si x2 es menor que 4, considerando el signo, y a 0 si no.
- **SLTU**: Establece menos que sin signo. Establece un registro (rd) a 1 si un registro (rs1) es menor que otro registro (rs2), sin considerar el signo, y a 0 si no. Tiene un formato R. Por ejemplo, `SLTU x1, x2, x3` establece x1 a 1 si x2 es menor que x3, sin considerar el signo, y a 0 si no.
- **SLTIU**: Establece menos que inmediato sin signo. Establece un registro (rd) a 1 si un registro (rs1) es menor que un valor inmediato (imm), sin considerar el signo, y a 0 si no. Tiene un formato I. Por ejemplo, `SLTIU x1, x2, 4` establece x1 a 1 si x2 es menor que 4, sin considerar el signo, y a 0 si no.

#### Branches

- **BEQ**: Salta si son iguales. Salta a una etiqueta si dos registros (rs1 y rs2) son iguales, y continúa la ejecución si no. Tiene un formato SB. Por ejemplo, `BEQ x1, x2, loop` salta a la etiqueta loop si x1 y x2 son iguales, y continúa la ejecución si no.
- **BNE**: Salta si no son iguales. Salta a una etiqueta si dos registros (rs1 y rs2) no son iguales, y continúa la ejecución si sí. Tiene un formato SB. Por ejemplo, `BNE x1, x2, exit` salta a la etiqueta exit si x1 y x2 no son iguales, y continúa la ejecución si sí.
- **BLT**: Salta si es menor que. Salta a una etiqueta si un registro (rs1) es menor que otro registro (rs2), considerando el signo, y continúa la ejecución si no. Tiene un formato SB. Por ejemplo, `BLT x1, x2, then` salta a la etiqueta then si x1 es menor que x2, considerando el signo, y continúa la ejecución si no.
- **BGE**: Salta si es mayor o igual que. Salta a una etiqueta si un registro (rs1) es mayor o igual que otro registro (rs2), considerando el signo, y continúa la ejecución si no. Tiene un formato SB. Por ejemplo, `BGE x1, x2, else` salta a la etiqueta else si x1 es mayor o igual que x2, considerando el signo, y continúa la ejecución si no.
- **BLTU**: Salta si es menor que sin signo. Salta a una etiqueta si un registro (rs1) es menor que otro registro (rs2), sin considerar el signo, y continúa la ejecución si no. Tiene un formato SB. Por ejemplo, `BLTU x1, x2, then` salta a la etiqueta then si x1 es menor que x2, sin considerar el signo, y continúa la ejecución si no.
- **BGEU**: Salta si es mayor o igual que sin signo. Salta a una etiqueta si un registro (rs1) es mayor o igual que otro registro (rs2), sin considerar el signo, y continúa la ejecución si no. Tiene un formato SB. Por ejemplo, `BGEU x1, x2, else` salta a la etiqueta else si x1 es mayor o igual que x2, sin considerar el signo, y continúa la ejecución si no.

#### Loads
- **LW**: Carga una palabra (32 bits) desde la memoria y la almacena en el registro de destino (32 bits). Tiene un formato I. Por ejemplo, `LW x1, 4(x2)` carga una palabra desde la dirección de memoria x2 + 4 y la guarda en x1.

#### Store
- **SW**: Almacena una palabra (32 bits) desde un registro (rs2) en la memoria. Tiene un formato S. Por ejemplo, `SW x1, 4(x2)` almacena una palabra desde x1 en la dirección de memoria x2 + 4.




## Diseniando nuestras intrucciones
### Comun en todas las instrucciones

1. PC: comun a todas las intrucciones secuenciales
2. Una memoria para instrucciones: la salida de la memoria contiene la instruccion a ejecutar.
3. Un sumador que sume 4
#### Camino de datos para el fetch
Componentes necesario:
- PC
- Instruccion Memory
- ADD
![[Pasted image 20231210133119.png]]
### Instrucciones tipo R
- *Fech*
1. Necesito leer dos registros del banco del registro
2. Necesito realizar operaciones aritmeticos/logica en una ALU
3. Escribir nuevamente en el banco de registros
Para todo esto necesitremos a banco de registro que se pueda escribir y leer y una ALU
### Instruccion Load/Store
- *Fech*
1. Tambien se necesitan leer banco de registros.
2. Calcula la direccion de memoria en la ALU usando la constante inmediata que viene con la instruccion.
- Esta memoria tiene que ser distinta a las de instrucciones ya que queremos que todo se ejecute en un ciclo.
#### Camino de datos Tipo R/Load/Store
Componentes nuevos que necesitaremos
1. Extensor de signo para la constante inmediata
2. Una memoria de datos
	- Esta debe tener una entrada de direccion
	- Entrada de datos
	- Salida de datos
	- Seniales de contro de lectura y escritura

![[Pasted image 20231210140229.png|600]]
- Surge la necesitadad de agregar 2 multiplexores
	- El segundo operando de la alu puede venir del banco de registros o de la constante inmediata
	- El dato a escribir en el banco de registros puede venir de la ALU o de la memoria
### Instruccion Branch
1. Leen 2 registros de los bancos de registros
2. Usan la ALU para compararlos
3. Calcula la direccion destino
4. Genera la necesidad de un nuevo sumador
	- Y de un nuevo multiplexor


#### Camino de datos branch
![[Pasted image 20231210172207.png]]


#### Observaciones
- Para poder analizar el tipo de comparacion se usara un bloque que con la señal de control decidira en base a las señales de negativo y zero de la alu si se debe o no realizar el salto
- Este bloque se lo vera luego en el pipeline completo
- Se podria decir que forma parte de los bloques de control
## CPU sin pipeline #Completar 
Para realizar nuestro CPU, solo debemos agrupar las distintas etapas del diseño de nuestras instrucciones, este diseño basico no tiene en cuenta la etapa de control, la cual sera agregada las adelante
![[Pasted image 20231210172803.png|900]]


## CPU con pipeline sin control #Completar 
### RTL 
![[Pasted image 20240402184814.png]]


# Control y coordinacion

![[Pasted image 20240410174711.png]]
## Control general

El módulo **CONTROL** decodifica el opcode de la instrucción para generar las señales de control necesarias para las diferentes etapas del pipeline del CPU.

- **Entradas**:
  - `opcode`: Código de operación de la instrucción.

- **Salidas**:
  - `RegWrite`: Señal para escribir en el banco de registros.
  - `ALUSrc`: Señal para seleccionar el segundo operando de la ALU.
  - `MemWrite`: Señal para escribir en la memoria de datos.
  - `MemRead`: Señal para leer de la memoria de datos.
  - `Branch`: Señal para realizar un salto condicional.
  - `MemToReg`: Señal para seleccionar el dato que se escribe en el registro destino.
  - `ALUop`: Código de operación para la ALU.

- **Funcionamiento**:
  - Decodifica `opcode` para asignar las señales de control correspondientes.
  - Genera señales específicas para instrucciones tipo R, I, S, B, y loads.

### Tabla de funcionamiento

| Instrucción      | RegWrite | ALUSrc | MemWrite | MemRead | Branch | MemToReg | ALUop |
| ---------------- | -------- | ------ | -------- | ------- | ------ | -------- | ----- |
| Tipo R           | 1        | 0      | 0        | 0       | 0      | 0        | 10    |
| Tipo I sin loads | 1        | 1      | 0        | 0       | 0      | 0        | 11    |
| Tipo I Loads     | 1        | 1      | 0        | 1       | 0      | 1        | 00    |
| Tipo S           | 0        | 1      | 1        | 0       | 0      | 0        | 00    |
| Tipo B           | 0        | 0      | 0        | 0       | 1      | 0        | 01    |

### RTL
![[Pasted image 20240712131438.png]]
### Simulaciones
![[Pasted image 20240422134017.png]]
### Utilizacion
![[Pasted image 20240712132910.png]]

## Control ALU
El módulo **ALU_CONTROL** determina las señales de control para la ALU basándose en los campos `funct3`, `funct7` de la instrucción y el código de operación ALUop.

- **Entradas**:
  - `ALUop`: Código de operación de la ALU.
  - `funct3`: Campo funct3 de la instrucción.
  - `funct7`: Campo funct7 de la instrucción.
  
- **Salidas**:
  - `ALUControl`: Señal de control para la ALU.
  - `BranchOp`: Señal de operación de branch.
  - `SLTc`: Señal de control para SLT.

- **Funcionamiento**:
  - `ALUControl` se asigna en base a las combinaciones de `funct3`, `funct7` y `ALUop`.
  - `BranchOp` determina la operación de branch en base a `ALUop` y `funct3`.
  - `SLTc` se activa para las operaciones SLT y SLTU.

### Tabla de funcionamiento

| Instrucción | ALUop | funct3 | funct7  | ALU_Control | BranchOp | SLTc |
| ----------- | ----- | ------ | ------- | ----------- | -------- | ---- |
| ADD         | 10    | 000    | 0000000 | 000         | 00       | 0    |
| SUB         | 10    | 000    | 0100000 | 001         | 00       | 0    |
| SLL         | 10    | 001    | 0000000 | 010         | 00       | 0    |
| SLT         | 10    | 010    | 0000000 | 001         | 10       | 1    |
| SLTU        | 10    | 011    | 0000000 | 011         | 10       | 1    |
| XOR         | 10    | 100    | 0000000 | 101         | 00       | 0    |
| SRL         | 10    | 101    | 0000000 | 100         | 00       | 0    |
| SRA         | 10    | 101    | 0100000 | 100         | 00       | 0    |
| OR          | 10    | 110    | 0000000 | 110         | 00       | 0    |
| AND         | 10    | 111    | 0000000 | 111         | 00       | 0    |
| SRAI        | 11    | 101    | -       | 100         | 00       | 0    |
| ADDI        | 11    | 000    | -       | 000         | 00       | 0    |
| SRLI        | 11    | 101    | -       | 100         | 00       | 0    |
| SLLI        | 11    | 001    | -       | 010         | 00       | 0    |
| SLTI        | 11    | 010    | -       | 001         | 10       | 1    |
| SLTIU       | 11    | 011    | -       | 011         | 10       | 1    |
| XORI        | 11    | 100    | -       | 101         | 00       | 0    |
| ORI         | 11    | 110    | -       | 110         | 00       | 0    |
| ANDI        | 11    | 111    | -       | 111         | 00       | 0    |
| LW          | 00    | 010    | -       | 000         | 00       | 0    |
| SW          | 00    | 010    | -       | 000         | 00       | 0    |
| BEQ         | 01    | 000    | -       | 001         | 00       | 0    |
| BNE         | 01    | 001    | -       | 001         | 01       | 0    |
| BLT         | 01    | 100    | -       | 001         | 10       | 0    |
| BGE         | 01    | 101    | -       | 001         | 11       | 0    |
| BLTU        | 01    | 110    | -       | 011         | 10       | 0    |
| BGEU        | 01    | 111    | -       | 011         | 11       | 0    |
### RTL
![[Pasted image 20240712200423.png]]
### Simulaciones
![[Pasted image 20240422135200.png]]

### Utilizacion
![[Pasted image 20240712202242.png]]


## RTL con Control

![[Pasted image 20240712121150.png]]




# Descripcion y analisis cada bloque

## REGISTERS

El módulo **REGISTERS** se encarga de manejar los registros del CPU. Tiene las siguientes características:

- **Entradas**:
  - `clk`: Señal de reloj.
  - `RA`, `RB`, `RW`: Direcciones de los registros de lectura A, lectura B y escritura, respectivamente.
  - `RegWrite`: Señal de control para permitir la escritura en un registro.
  - `busW`: Datos a escribir en el registro.
  
- **Salidas**:
  - `busA`, `busB`: Datos leídos de los registros A y B.
  
- **Funcionamiento**:
  - Los registros se actualizan en el flanco positivo del reloj (`clk`).
  - Si `RegWrite` está activo, el dato de `busW` se escribe en el registro especificado por `RW`.
  - `busA` y `busB` siempre reflejan el contenido de los registros especificados por `RA` y `RB`.

### RTL
![[Pasted image 20240712125709.png]]

### Utilizacion
![[Pasted image 20240712131231.png]]

### Conclusion
- Para una implementacion en caso de necesitar recursos, se debe reducir el tamañó
	- Esto se debe a que la FPGA no cuenta con componente de memoria de doble lectura
## PC

El módulo **PC** (Program Counter) es responsable de mantener la dirección actual de la instrucción que se está ejecutando.

- **Entradas**:
  - `clock`: Señal de reloj.
  - `next_address`: La dirección de la siguiente instrucción a ejecutar.

- **Salida**:
  - `address`: La dirección actual de la instrucción.

- **Funcionamiento**:
  - En el flanco positivo del reloj, se actualiza `address` con `next_address`.
  - Si `next_address` contiene bits indeterminados, `address` se reinicia a `32'h1000`.

### RTL
![[Pasted image 20240714195632.png]]

### Utilizacion
![[Pasted image 20240712220248.png]]
## ADD4

El módulo **ADD4** incrementa la dirección de la instrucción en 4, que es el tamaño de una instrucción en RISC-V.

- **Entrada**:
  - `current_address`: La dirección actual de la instrucción.

- **Salida**:
  - `next_address`: La dirección incrementada en 4.

- **Funcionamiento**:
  - `next_address` se actualiza continuamente con `current_address + 4`.
### RTL
![[Pasted image 20240712204643.png]]

### Utilizacion
![[Pasted image 20240712205008.png]]


### Observaciones
- Teoricamente es PC+4 pero en la realidad esto no sucede
- Debemos hacer PC+1, ya que definimos la memoria con espacios de 64 bits y no de 8
## ADD

El módulo **ADD** realiza la suma de dos valores de entrada.

- **Entradas**:
  - `A`, `B`: Valores a sumar.

- **Salida**:
  - `C`: Resultado de la suma.

- **Funcionamiento**:
  - `C` es el resultado de `A + B`.

### Simulaciones
![[Pasted image 20240422105711.png]]

## MUX32

El módulo **MUX32** es un multiplexor que selecciona entre dos entradas de 32 bits basado en una señal de selección.

- **Entradas**:
  - `A`, `B`: Entradas de datos.
  - `select`: Señal de control para seleccionar entre `A` y `B`.

- **Salida**:
  - `C`: Salida de datos seleccionada.

- **Funcionamiento**:
  - Si `select` es `1`, `C` toma el valor de `B`.
  - Si `select` es `0`, `C` toma el valor de `A`.


### RTL 
![[Pasted image 20240712202547.png]]


### Simulaciones
![[Pasted image 20240422110229.png]]

### Utilizacion
![[Pasted image 20240712204439.png]]

## GENERADOR_CONSTANTE

El módulo **GENERADOR_CONSTANTE** genera la constante inmediata (inmediato) a partir de la instrucción, necesaria para operaciones aritméticas y de acceso a memoria.

- **Entradas**:
  - `instruccion`: La instrucción de la cual se extrae la constante inmediata.

- **Salida**:
  - `constante`: La constante inmediata generada.

- **Funcionamiento**:
  - Extrae y asigna los bits correspondientes para los diferentes tipos de instrucciones (I, S, B).
  - Sign-extiende las constantes inmediatas según sea necesario.

### Tabla de funcionamiento

| Tipo de Instrucción | Opcode    | Constante Generada          |
| ------------------- | --------- | --------------------------- |
| Tipo I (sin loads)  | 0010011   | Sign-extend de I_imm        |
| Tipo I (loads)      | 0000011   | Sign-extend de I_imm        |
| Tipo S              | 0100011   | Sign-extend de S_imm        |
| Tipo B              | 1100011   | Sign-extend de B_imm (formato especial) |
| Otro                | Otros     | 0                           |

- **I_imm**: Bits \[31:20] de la instrucción.
- **S_imm**: Bits \[31:25] y \[11:7] de la instrucción.
- **B_imm**: Bits \[31], \[7], \[30:25], \[11:8] de la instrucción.


### RTL
![[Pasted image 20240712125547.png]]
### Simulaciones

![[Pasted image 20240429111654.png]]

### Utilizacion
![[Pasted image 20240712125354.png]]
## MEM_INST

El módulo **MEM_INST** es responsable de almacenar y recuperar las instrucciones de la memoria.

- **Entradas**:
  - `i_pc`: Dirección del contador de programa (PC).
  
- **Salida**:
  - `o_instruccion`: Instrucción leída de la memoria.

- **Funcionamiento**:
  - La memoria de instrucciones (`inst`) se inicializa con el contenido del archivo especificado por `MEM_INIT_FILE`.
  - La instrucción correspondiente a la dirección `i_pc` se recupera de la memoria (`inst[i_pc/4]`).

### RTL
![[Pasted image 20240712221503.png]]

### Utilizacion
![[Pasted image 20240712221512.png]]
## MEM_DATA

El módulo **MEM_DATA** gestiona la memoria de datos, permitiendo leer y escribir datos en la memoria.

- **Entradas**:
  - `i_memwrite`: Señal de control para habilitar la escritura en la memoria.
  - `i_memread`: Señal de control para habilitar la lectura de la memoria.
  - `i_address`: Dirección de memoria.
  - `i_write_data`: Datos a escribir en la memoria.

- **Salida**:
  - `o_read_data`: Datos leídos de la memoria.

- **Funcionamiento**:
  - La memoria de datos (`data`) se inicializa a 0.
  - Si `i_memread` está activo, se leen los datos de la dirección especificada (`data[i_address>>2]`).
  - Si `i_memwrite` está activo, se escriben los datos en la dirección especificada (`data[i_address>>2]`).

### Utilizacion
![[Pasted image 20240713102709.png]]



### Conclusion
- Se deberia reducir el tamaño de la memoria ya que utiliza muchos recursos por la naturaleza de la misma
	- Esto se debe a que la FPGA no cuenta con la componente de memoria de 

## BRANCH

El módulo **BRANCH** determina si se debe realizar una operación de salto (branch) en base a las señales de control y los resultados de la ALU.

- **Entradas**:
  - `i_zero`: Señal de la ALU que indica si el resultado es cero.
  - `i_neg`: Señal de la ALU que indica si el resultado es negativo.
  - `i_branch`: Señal de control para habilitar la operación de branch.
  - `i_BranchOp`: Código de operación de branch.

- **Salidas**:
  - `o_PCSrc`: Señal de control para la fuente del PC.
  - `o_slt_data`: Resultado del set less than (slt).

- **Funcionamiento**:
  - Calcula si el resultado de la ALU es igual, menor o mayor que cero.
  - Determina la señal `PCSrc` en base a `i_BranchOp`.
  - Si `i_branch` está activo, `PCSrc` se asigna a `PCSrc_aux`.

### Tabla de operaciones

| BranchOp | Comparacion logica |
| -------- | ------------------ |
| 00       | Igual que          |
| 01       | Distinto que       |
| 10       | Menor que          |
| 11       | Mayor o igual que  |

### RTL
![[Pasted image 20240712223042.png]]
### Utilizacion
![[Pasted image 20240712223250.png]]
### Simulaciones
![[Pasted image 20240422120131.png]]

## ALU

El módulo **ALU** (Arithmetic Logic Unit) realiza operaciones aritméticas y lógicas en dos operandos.

- **Entradas**:
  - `A`, `B`: Operandos de entrada.
  - `ALU_Sel`: Código de operación de la ALU.

- **Salidas**:
  - `ALU_Out`: Resultado de la operación de la ALU.
  - `Zero`: Señal que indica si el resultado es cero.
  - `Negativo`: Señal que indica si el resultado es negativo.

- **Funcionamiento**:
  - La ALU realiza operaciones como suma, resta, desplazamiento lógico, AND, OR y XOR en base a `ALU_Sel`.
  - `Zero` es `1` si el resultado es cero.
  - `Negativo` es `1` si el bit más significativo del resultado es `1`.

### Tabla de operaciones

| ALU_Control | Operacion         |
| ----------- | ----------------- |
| 000         | ADD               |
| 001         | SUB               |
| 010         | Shift Left Logico |
| 011         | SUB unsigned      |
| 100         | Shift Righ        |
| 101         | XOR               |
| 110         | OR                |
| 111         | AND               |
|             |                   |
### RTL
![[Pasted image 20240712221728.png]]
### Utilizacion
![[Pasted image 20240712222801.png]]
### Simulaciones

![[Pasted image 20240422114327.png]]



# Descripcion y analisis cada stage
## IF

El bloque IF (Instruction Fetch) se encarga de obtener la instrucción desde la memoria de instrucciones en base a la dirección actual del programa. Este bloque maneja la lógica para seleccionar la siguiente dirección de instrucción, incrementarla, y acceder a la memoria para obtener la instrucción correspondiente.
1. **Entradas y Salidas**:
   - **Entradas**:
     - `i_branch_address`: Dirección de instrucción en caso de un salto (branch).
     - `i_select`: Señal de control para seleccionar entre la dirección de salto y la dirección incrementada.
     - `i_clock`: Señal de reloj para sincronizar las operaciones.
   - **Salidas**:
     - `o_address`: Dirección actual de la instrucción.
     - `o_instruccion`: Instrucción obtenida de la memoria.

2. **Conexión entre Componentes**:
   - El `MUX32` selecciona la próxima dirección de instrucción (`next_address`), que puede ser una dirección de salto o la dirección incrementada (`address_4`).
   - El `ADD4` incrementa la dirección actual (`address`) en 4.
   - El `PC` actualiza la dirección del programa a la siguiente dirección (`next_address`) en cada ciclo de reloj.
   - La `MEM_INST` obtiene la instrucción desde la memoria en la dirección actual (`address`).

3. **Funcionamiento**:
   - En cada ciclo de reloj, el bloque IF selecciona la siguiente dirección de instrucción (`next_address`) basada en si hay un salto o no (`i_select`).
   - La dirección actual (`address`) es incrementada en 4 por el `ADD4` y actualizada por el `PC`.
   - La instrucción en la dirección actual es obtenida desde la `MEM_INST` y enviada como salida (`o_instruccion`).





### Simulacion
#### Pre sintesis
![[Pasted image 20240709185305.png]]
![[Pasted image 20240709185335.png]]
- Este bloque funciona bien solo cuando se lo mantiene dentro de la memoria creada, cuando sale de esa memoria nos da instrucciones indefinidas
#### Post sintesis 
### RTL
![[Pasted image 20240713213122.png]]
### Analisis 
#### Reporte utilizacion post sintesis
![[Pasted image 20240715215520.png]]

#### Reporte utilizacion post implementacion
![[Pasted image 20240715215554.png]]


#### Reporte de tiempo post implementacion
![[Pasted image 20240715215613.png]]


![[Pasted image 20240715215708.png]]
## EX

El módulo **EX** (Execute) es responsable de realizar operaciones aritméticas y lógicas, así como de calcular la dirección de salto.

- **Entradas**:
  - `i_PC`: Dirección del contador de programa.
  - `i_register1`, `i_register2`: Datos leídos de los registros.
  - `i_constante`: Valor inmediato generado.
  - `i_ALUSrc`: Señal de control para seleccionar el segundo operando de la ALU.
  - `i_ALUControl`: Señal de control de la ALU.

- **Salidas**:
  - `o_ALUResult`: Resultado de la operación de la ALU.
  - `o_PCBranch`: Dirección de salto calculada.
  - `o_zero`: Señal que indica si el resultado de la ALU es cero.
  - `o_negative`: Señal que indica si el resultado de la ALU es negativo.

- **Funcionamiento**:
  - La ALU realiza operaciones aritméticas y lógicas en base a las señales de control.
  - El módulo ADD calcula la dirección de salto sumando `i_PC` y `i_constante`.
  - El multiplexor selecciona entre `i_register2` e `i_constante` como segundo operando de la ALU.
### Simulacion
![[Pasted image 20240710155533.png]]
![[Pasted image 20240710155553.png]]
### RTL
![[Pasted image 20240710150137.png]]
### Utilizacion
![[Pasted image 20240710193859.png]]

## ID

El módulo **ID** (Instruction Decode) decodifica la instrucción y genera señales de control necesarias para las siguientes etapas del pipeline.

- **Entradas**:
  - `i_clk`: Señal de reloj.
  - `i_instruccion`: Instrucción a decodificar.
  - `i_WriteData`: Datos a escribir en el registro.
  - `i_RegWrite`: Señal de control para escribir en el registro.

- **Salidas**:
  - `o_register1`, `o_register2`: Datos leídos de los registros.
  - `o_constante`: Valor inmediato generado.
  - `o_WriteReg`: Dirección del registro a escribir.
  - Señales de control: `o_RegWrite`, `o_ALUSrc`, `o_MemWrite`, `o_MemRead`, `o_Branch`, `o_MemToReg`, `o_SLTc`, `o_ALUControl`, `o_BranchOp`.

- **Funcionamiento**:
  - Extrae los campos de la instrucción para obtener las direcciones de los registros.
  - Genera la constante inmediata usando el módulo GENERADOR_CONSTANTE.
  - Lee los datos de los registros usando el módulo REGISTERS.
  - Decodifica el opcode para generar señales de control usando el módulo CONTROL.
  - Determina las señales de control para la ALU usando el módulo ALU_CONTROL.
### Simulacion
![[Pasted image 20240710121251.png]]
![[Pasted image 20240710121255.png]]

### RTL
![[Pasted image 20240710104530.png]]

### Utilizacion
![[Pasted image 20240710194224.png]]

## MEM

El módulo **MEM** (Memory Access) gestiona las operaciones de lectura y escritura en la memoria de datos, así como la evaluación de las condiciones de salto.

- **Entradas**:
  - `i_Address`: Dirección de la memoria.
  - `i_WriteData`: Datos a escribir en la memoria.
  - `i_BranchOp`: Código de operación de salto.
  - `i_negative`, `i_zero`: Señales de la ALU.
  - `i_branch`, `i_MemWrite`, `i_MemRead`, `i_SLTc`: Señales de control.

- **Salidas**:
  - `o_PCSrc`: Señal para seleccionar la fuente del PC.
  - `o_ReadData`: Datos leídos de la memoria.
  - `o_Mux`: Salida del multiplexor.

- **Funcionamiento**:
  - Evalúa las condiciones de salto usando el módulo BRANCH.
  - Realiza operaciones de lectura y escritura en la memoria de datos usando el módulo MEM_DATA.
  - Selecciona entre `a_slt_data` y `i_Address` para la salida del multiplexor usando el módulo MUX32.

### Simulacion
#### Pres sintesis
![[Pasted image 20240710204532.png]]
![[Pasted image 20240710204535.png]]
#### Post sintesis
![[Pasted image 20240716115654.png]]
![[Pasted image 20240716115649.png]]
### RTL
![[Pasted image 20240716105757.png]]

### Utilizacion
![[Pasted image 20240716112115.png]]


# CPU top
## Codigo

El módulo `CPU_pipeline` implementa una CPU basada en el ISA RISC-V con pipeline. Este diseño consta de cinco etapas: IF (Instruction Fetch), ID (Instruction Decode), EX (Execute), MEM (Memory Access), y WB (Write Back) ya definidas y conocidas anteriormente. Se utilizan registros de pipeline para almacenar los resultados intermedios entre las etapas y mantener el flujo continuo de instrucciones.

#### Interfaz del Módulo
```verilog
module CPU (
    input           clk,
    input           reset,
    output [31:0]   pc,          // Contador de programa
    output [31:0]   alu_result   // Resultado de la ALU
);
```
- `clk`: Señal de reloj para sincronizar las operaciones de la CPU.
- `reset`: Señal de reset para inicializar la CPU.
- `pc`: Salida del contador de programa que indica la dirección de la instrucción actual.
- `alu_result`: Salida del resultado de la ALU que muestra el resultado de la operación aritmética/lógica más reciente.

#### Señales Internas y Registros de Pipeline
- **IF/ID Pipeline Registers**: Almacenan la instrucción y la dirección actual después de la etapa de Instruction Fetch (IF).
- **ID/EX Pipeline Registers**: Almacenan los valores leídos de los registros, la constante inmediata, y señales de control después de la etapa de Instruction Decode (ID).
- **EX/MEM Pipeline Registers**: Almacenan el resultado de la ALU, el segundo operando, y señales de control después de la etapa de Execute (EX).
- **MEM/WB Pipeline Registers**: Almacenan los datos leídos de la memoria y señales de control después de la etapa de Memory Access (MEM).

#### Etapa IF (Instruction Fetch)
```verilog
// Etapa IF
IF if_stage (
    .o_address(if_address),
    .o_instruccion(if_instruccion),
    .i_branch_address(exmem_PCBranch),
    .i_reset(reset),
    .i_select(mem_PCSrc),
    .i_clock(clk)
);
```
- `o_address`: Dirección actual del PC.
- `o_instruccion`: Instrucción leída de la memoria de instrucciones.
- `i_branch_address`: Dirección de destino en caso de una instrucción de salto.
- `i_reset`: Señal de reset.
- `i_select`: Señal para seleccionar entre la dirección siguiente y la dirección de salto.
- `i_clock`: Señal de reloj.

#### Registros de Pipeline IF/ID
```verilog
// Pipeline IF/ID
always @(posedge clk or posedge reset) begin
    if (reset) begin
        ifid_instruccion <= 32'b0;
        ifid_address <= 31'b0;
    end else begin
        ifid_instruccion <= if_instruccion;
        ifid_address <= if_address;
    end
end
```
- `ifid_instruccion`: Instrucción almacenada para la etapa de ID.
- `ifid_address`: Dirección actual del PC almacenada para la etapa de ID.

#### Etapa ID (Instruction Decode)
```verilog
// Etapa ID
ID id_stage (
    .i_clk(clk),
    .i_reset(reset),
    .i_instruccion(ifid_instruccion),
    .i_WriteData(wb_WriteData),
    .i_RegWrite(memwb_RegWrite),
    .i_WriteReg(memwb_WriteReg),
    .o_register1(id_register1),
    .o_register2(id_register2),
    .o_constante(id_constante),
    .o_WriteReg(id_WriteReg),
    .o_RegWrite(id_RegWrite),
    .o_ALUSrc(id_ALUSrc),
    .o_MemWrite(id_MemWrite),
    .o_MemRead(id_MemRead),
    .o_Branch(id_Branch),
    .o_MemToReg(id_MemToReg),
    .o_SLTc(id_SLTc),
    .o_ALUControl(id_ALUControl),
    .o_BranchOp(id_BranchOp)
);
```
- `i_clk`: Señal de reloj.
- `i_reset`: Señal de reset.
- `i_instruccion`: Instrucción a decodificar.
- `i_WriteData`: Datos a escribir en el registro destino.
- `i_RegWrite`: Señal de control para habilitar escritura en registros.
- `i_WriteReg`: Registro destino para la escritura.
- `o_register1`: Valor leído del primer registro fuente.
- `o_register2`: Valor leído del segundo registro fuente.
- `o_constante`: Constante inmediata decodificada.
- `o_WriteReg`: Registro destino decodificado.
- `o_RegWrite`: Señal de control para habilitar escritura en registros.
- `o_ALUSrc`: Señal de control para seleccionar el segundo operando de la ALU.
- `o_MemWrite`: Señal de control para escribir en la memoria de datos.
- `o_MemRead`: Señal de control para leer de la memoria de datos.
- `o_Branch`: Señal de control para realizar un salto condicional.
- `o_MemToReg`: Señal de control para seleccionar el dato que se escribe en el registro destino.
- `o_SLTc`: Señal de control para la instrucción SLT.
- `o_ALUControl`: Señal de control para determinar la operación de la ALU.
- `o_BranchOp`: Señal de control para determinar el tipo de salto.

#### Registros de Pipeline ID/EX
```verilog
// Pipeline ID/EX
always @(posedge clk or posedge reset) begin
    if (reset) begin
        idex_PC <= 32'b0;
        idex_register1 <= 32'b0;
        idex_register2 <= 32'b0;
        idex_constante <= 32'b0;
        idex_ALUSrc <= 1'b0;
        idex_ALUControl <= 3'b0;
        idex_MemWrite <= 1'b0;
        idex_MemRead <= 1'b0;
        idex_Branch <= 1'b0;
        idex_MemToReg <= 1'b0;
        idex_RegWrite <= 1'b0;
        idex_BranchOp <= 2'b0;
        idex_SLTc <= 1'b0;
        idex_WriteReg <= 5'b0;
    end else begin
        idex_PC <= {ifid_address, 1'b0};
        idex_register1 <= id_register1;
        idex_register2 <= id_register2;
        idex_constante <= id_constante;
        idex_ALUSrc <= id_ALUSrc;
        idex_ALUControl <= id_ALUControl;
        idex_MemWrite <= id_MemWrite;
        idex_MemRead <= id_MemRead;
        idex_Branch <= id_Branch;
        idex_MemToReg <= id_MemToReg;
        idex_RegWrite <= id_RegWrite;
        idex_BranchOp <= id_BranchOp;
        idex_SLTc <= id_SLTc;
        idex_WriteReg <= id_WriteReg;
    end
end
```
- `idex_PC`: Dirección actual del PC almacenada para la etapa de EX.
- `idex_register1`: Valor del primer registro fuente almacenado para la etapa de EX.
- `idex_register2`: Valor del segundo registro fuente almacenado para la etapa de EX.
- `idex_constante`: Constante inmediata almacenada para la etapa de EX.
- `idex_ALUSrc`: Señal de control almacenada para la etapa de EX.
- `idex_ALUControl`: Señal de control para la ALU almacenada para la etapa de EX.
- `idex_MemWrite`: Señal de control almacenada para la etapa de EX.
- `idex_MemRead`: Señal de control almacenada para la etapa de EX.
- `idex_Branch`: Señal de control almacenada para la etapa de EX.
- `idex_MemToReg`: Señal de control almacenada para la etapa de EX.
- `idex_RegWrite`: Señal de control almacenada para la etapa de EX.
- `idex_BranchOp`: Señal de control almacenada para la etapa de EX.
- `idex_SLTc`: Señal de control almacenada para la etapa de EX.
- `idex_WriteReg`: Registro destino almacenado para la etapa de EX.

#### Etapa EX (Execute)
```verilog
// Etapa EX
EX ex_stage (
    .i_PC(idex_PC),
    .i_register1(idex_register1),
    .i_register2(idex_register2),
    .i_constante(idex_constante),
    .i_ALUSrc(idex_ALUSrc),
    .i_ALUControl(idex_ALUControl),
    .o_ALUResult(ex_ALUResult),
    .o_PCBranch(ex_PCBranch),
    .o_zero(ex_zero),
    .o_negative(ex_negative)
);
```
- `i_PC`: Dirección del PC de entrada.
- `i_register1`: Primer operando de la ALU.
- `i_register2`: Segundo operando de la ALU.
- `i_constante`: Constante inmediata.
- `i_ALUSrc`: Señal de control

 para seleccionar el segundo operando de la ALU.
- `i_ALUControl`: Señal de control para determinar la operación de la ALU.
- `o_ALUResult`: Resultado de la ALU.
- `o_PCBranch`: Dirección de salto calculada.
- `o_zero`: Señal que indica si el resultado de la ALU es cero.
- `o_negative`: Señal que indica si el resultado de la ALU es negativo.

#### Registros de Pipeline EX/MEM
```verilog
// Pipeline EX/MEM
always @(posedge clk or posedge reset) begin
    if (reset) begin
        exmem_ALUResult <= 32'b0;
        exmem_register2 <= 32'b0;
        exmem_PCBranch <= 32'b0;
        exmem_zero <= 1'b0;
        exmem_negative <= 1'b0;
        exmem_MemWrite <= 1'b0;
        exmem_MemRead <= 1'b0;
        exmem_Branch <= 1'b0;
        exmem_MemToReg <= 1'b0;
        exmem_RegWrite <= 1'b0;
        exmem_BranchOp <= 2'b0;
        exmem_SLTc <= 1'b0;
        exmem_WriteReg <= 5'b0;
    end else begin
        exmem_ALUResult <= ex_ALUResult;
        exmem_register2 <= idex_register2;
        exmem_PCBranch <= ex_PCBranch;
        exmem_zero <= ex_zero;
        exmem_negative <= ex_negative;
        exmem_MemWrite <= idex_MemWrite;
        exmem_MemRead <= idex_MemRead;
        exmem_Branch <= idex_Branch;
        exmem_MemToReg <= idex_MemToReg;
        exmem_RegWrite <= idex_RegWrite;
        exmem_BranchOp <= idex_BranchOp;
        exmem_SLTc <= idex_SLTc;
        exmem_WriteReg <= idex_WriteReg;
    end
end
```
- `exmem_ALUResult`: Resultado de la ALU almacenado para la etapa de MEM.
- `exmem_register2`: Valor del segundo operando almacenado para la etapa de MEM.
- `exmem_PCBranch`: Dirección de salto calculada almacenada para la etapa de MEM.
- `exmem_zero`: Señal de resultado cero almacenada para la etapa de MEM.
- `exmem_negative`: Señal de resultado negativo almacenada para la etapa de MEM.
- `exmem_MemWrite`: Señal de control almacenada para la etapa de MEM.
- `exmem_MemRead`: Señal de control almacenada para la etapa de MEM.
- `exmem_Branch`: Señal de control almacenada para la etapa de MEM.
- `exmem_MemToReg`: Señal de control almacenada para la etapa de MEM.
- `exmem_RegWrite`: Señal de control almacenada para la etapa de MEM.
- `exmem_BranchOp`: Señal de control almacenada para la etapa de MEM.
- `exmem_SLTc`: Señal de control almacenada para la etapa de MEM.
- `exmem_WriteReg`: Registro destino almacenado para la etapa de MEM.

#### Etapa MEM (Memory Access)
```verilog
// Etapa MEM
MEM mem_stage (
    .i_clk(clk),
    .i_reset(reset),
    .i_Address(exmem_ALUResult),
    .i_WriteData(exmem_register2),
    .i_BranchOp(exmem_BranchOp),
    .i_negative(exmem_negative),
    .i_zero(exmem_zero),
    .i_branch(exmem_Branch),
    .i_MemWrite(exmem_MemWrite),
    .i_MemRead(exmem_MemRead),
    .i_SLTc(exmem_SLTc),
    .o_PCSrc(mem_PCSrc),
    .o_ReadData(mem_ReadData),
    .o_Mux(mem_Mux)
);
```
- `i_clk`: Señal de reloj.
- `i_reset`: Señal de reset.
- `i_Address`: Dirección de memoria a acceder.
- `i_WriteData`: Datos a escribir en la memoria.
- `i_BranchOp`: Señal de control para determinar el tipo de salto.
- `i_negative`: Señal de resultado negativo.
- `i_zero`: Señal de resultado cero.
- `i_branch`: Señal de control para realizar un salto condicional.
- `i_MemWrite`: Señal de control para escribir en la memoria de datos.
- `i_MemRead`: Señal de control para leer de la memoria de datos.
- `i_SLTc`: Señal de control para la instrucción SLT.
- `o_PCSrc`: Señal de control para seleccionar la dirección siguiente del PC.
- `o_ReadData`: Datos leídos de la memoria de datos.
- `o_Mux`: Salida del multiplexor.

#### Registros de Pipeline MEM/WB
```verilog
// Pipeline MEM/WB
always @(posedge clk or posedge reset) begin
    if (reset) begin
        memwb_ALUResult <= 32'b0;
        memwb_ReadData <= 32'b0;
        memwb_MemToReg <= 1'b0;
        memwb_RegWrite <= 1'b0;
        memwb_WriteReg <= 5'b0;
    end else begin
        memwb_ALUResult <= exmem_ALUResult;
        memwb_ReadData <= mem_ReadData;
        memwb_MemToReg <= exmem_MemToReg;
        memwb_RegWrite <= exmem_RegWrite;
        memwb_WriteReg <= exmem_WriteReg;
    end
end
```
- `memwb_ALUResult`: Resultado de la ALU almacenado para la etapa de WB.
- `memwb_ReadData`: Datos leídos de la memoria almacenados para la etapa de WB.
- `memwb_MemToReg`: Señal de control almacenada para la etapa de WB.
- `memwb_RegWrite`: Señal de control almacenada para la etapa de WB.
- `memwb_WriteReg`: Registro destino almacenado para la etapa de WB.

#### Etapa WB (Write Back)
```verilog
// Etapa WB
MUX32 wb_mux (
    .A(memwb_ALUResult),
    .B(memwb_ReadData),
    .select(memwb_MemToReg),
    .C(wb_WriteData)
);
```
- `A`: Resultado de la ALU.
- `B`: Datos leídos de la memoria.
- `select`: Señal de control para seleccionar el dato que se escribe en el registro destino.
- `C`: Datos a escribir en el registro destino.


## Analisis

![[Pasted image 20240716172751.png]]

### Codigo de simulacion

#### Código en Ensamblador RISC-V

```assembly
.section .text
.globl _start

_start:
    # Inicializar los registros usando ADDI
    addi x1, x0, 0    # x1 = 0
    addi x2, x0, 4    # x2 = 4
    addi x3, x0, 0    # x3 = 0
    addi x4, x0, 16   # x4 = 16
    addi x5, x0, 256  # x5 = 256
    addi x6, x0, 512  # x6 = 512
	addi x7, x0, 1792  # x7 = 1792
    

    # Pipeline delay simulation
    nop               # No operation (simulate delay)
    nop               # No operation (simulate delay)
    nop               # No operation (simulate delay)
    nop               # No operation (simulate delay)

loop:
    add x8, x7, x2    # Add offset to the loaded value, result in x8

    # Pipeline delay simulation for ALU operation
    nop               # No operation (simulate ALU delay)
    nop               # No operation (simulate ALU delay)

    sw x8, 0(x7)      # Store result to output_data

    # Pipeline delay simulation for memory write
    nop               # No operation (simulate memory write delay)
    nop               # No operation (simulate memory write delay)
    nop               # No operation (simulate memory write delay)

    addi x5, x5, 4    # Move to the next input_data element
    addi x6, x6, 4    # Move to the next output_data element
    addi x3, x3, 4    # Update base address for input_data
    
	nop              
    nop
    nop
    
    blt x3, x4, loop  # Loop if not all elements are processed

    # End of program (infinite loop)
end:
    nop               # Infinite loop
    nop
    nop
```
#### Archivo `mem.mem`

```
00000093
00400113
00000193
01000213
10000293
20000313
70100393
00000013
00000013
00000013
00000013
00238433
00000013
00000013
0073A023
00000013
00000013
00000013
00428293
00430313
00418193
00000013
00000013
00000013
FE41CAE3
00000013
00000013
00000013
00000013
```


#### Tabla de Ejecución

| PC (Hex)   | Instrucción      | Registro/Espacio de Memoria Modificado | Resultado de la ALU                                     |
| ---------- | ---------------- | -------------------------------------- | ------------------------------------------------------- |
| 0x00000000 | addi x1, x0, 0   | x1                                     | 0                                                       |
| 0x00000001 | addi x2, x0, 4   | x2                                     | 4                                                       |
| 0x00000002 | addi x3, x0, 0   | x3                                     | 0                                                       |
| 0x00000003 | addi x4, x0, 16  | x4                                     | 16                                                      |
| 0x00000004 | addi x5, x0, 256 | x5                                     | 256                                                     |
| 0x00000005 | addi x6, x0, 512 | x6                                     | 512                                                     |
| 0x00000006 | addi x7, x0, 256 | x7                                     | 1792                                                    |
| 0x00000007 | nop              | -                                      | -                                                       |
| 0x00000008 | nop              | -                                      | -                                                       |
| 0x00000009 | nop              | -                                      | -                                                       |
| 0x0000000A | nop              | -                                      | -                                                       |
| 0x0000000B | add x8, x7, x2   | x8                                     | 14 (10 + 4)                                             |
| 0x0000000C | nop              | -                                      | -                                                       |
| 0x0000000D | nop              | -                                      | -                                                       |
| 0x0000000E | sw x8, 0(x7)     | Memoria en 0x1792                      | 14                                                      |
| 0x0000000F | nop              | -                                      | -                                                       |
| 0x00000010 | nop              | -                                      | -                                                       |
| 0x00000011 | nop              | -                                      | -                                                       |
| 0x00000012 | addi x5, x5, 4   | x5                                     | 260 (0x104)                                             |
| 0x00000013 | addi x6, x6, 4   | x6                                     | 516 (0x204)                                             |
| 0x00000014 | addi x3, x3, 4   | x3                                     | 4                                                       |
| 0x00000015 | blt x3, x4, loop | PC                                     | Salta a 0x0000000B (x3 < x4)                            |
| 0x0000000B | add x8, x7, x2   | x8                                     | 24 (20 + 4) (nota: se debe ejecutar lw x7, 0(x5) antes) |
| 0x0000000C | nop              | -                                      | -                                                       |
| 0x0000000D | nop              | -                                      | -                                                       |
| 0x0000000E | sw x8, 0(x7)     | Memoria en 0x204                       | 3073                                                    |
| 0x0000000F | nop              | -                                      | -                                                       |
| 0x00000010 | nop              | -                                      | -                                                       |
| 0x00000011 | nop              | -                                      | -                                                       |
| 0x00000012 | addi x5, x5, 4   | x5                                     | 264 (0x108)                                             |
| 0x00000013 | addi x6, x6, 4   | x6                                     | 520 (0x208)                                             |
| 0x00000014 | addi x3, x3, 4   | x3                                     | 8                                                       |
| 0x00000015 | blt x3, x4, loop | PC                                     | Salta a 0x0000000B (x3 < x4)                            |
| 0x0000000B | add x8, x7, x2   | x8                                     | 34 (30 + 4) (nota: se debe ejecutar lw x7, 0(x5) antes) |
| 0x0000000C | nop              | -                                      | -                                                       |
| 0x0000000D | nop              | -                                      | -                                                       |
| 0x0000000E | sw x8, 0(x6)     | Memoria en 0x208                       | 34                                                      |
| 0x0000000F | nop              | -                                      | -                                                       |
| 0x00000010 | nop              | -                                      | -                                                       |
| 0x00000011 | nop              | -                                      | -                                                       |
| 0x00000012 | addi x5, x5, 4   | x5                                     | 268 (0x10C)                                             |
| 0x00000013 | addi x6, x6, 4   | x6                                     | 524 (0x20C)                                             |
| 0x00000014 | addi x3, x3, 4   | x3                                     | 12                                                      |
| 0x00000015 | blt x3, x4, loop | PC                                     | Salta a 0x0000000B (x3 < x4)                            |
| 0x0000000B | add x8, x7, x2   | x8                                     | 44 (40 + 4) (nota: se debe ejecutar lw x7, 0(x5) antes) |
| 0x0000000C | nop              | -                                      | -                                                       |
| 0x0000000D | nop              | -                                      | -                                                       |
| 0x0000000E | sw x8, 0(x6)     | Memoria en 0x20C                       | 44                                                      |
| 0x0000000F | nop              | -                                      | -                                                       |
| 0x00000010 | nop              | -                                      | -                                                       |
| 0x00000011 | nop              | -                                      | -                                                       |
| 0x00000012 | addi x5, x5, 4   | x5                                     | 272 (0x110)                                             |
| 0x00000013 | addi x6, x6, 4   | x6                                     | 528 (0x210)                                             |
| 0x00000014 | addi x3, x3, 4   | x3                                     | 16                                                      |
| 0x00000015 | blt x3, x4, loop | PC                                     | No salta (x3 no < x4)                                   |
| 0x00000016 | nop              | -                                      | -                                                       |
| 0x00000017 | nop              | -                                      | -                                                       |
| 0x00000018 | nop              | -                                      | -                                                       |

### Analisis con placa Artix A7 35t
#### Pre sintesis
![[Pasted image 20240717212852.png]]
#### Post sintesis
![[Pasted image 20240717160714.png]]
![[Pasted image 20240716174921.png]]
![[Pasted image 20240716174923.png]]

##### Funcional
![[Pasted image 20240717212911.png]]
##### Timing
![[Pasted image 20240717212933.png]]
#### Post implementacion
##### Timing
![[Pasted image 20240717161523.png]]
![[Pasted image 20240717161651.png]]

##### Utilizacion
![[Pasted image 20240717161558.png]]
![[Pasted image 20240717161602.png]]
##### Funcional
![[Pasted image 20240717213024.png]]
##### Timing
![[Pasted image 20240717213107.png]]
![[Pasted image 20240716175006.png]]
### Analisis con placa CMOD 35t
#### Simulacion pre sintesis
![[Pasted image 20240719115339.png]]
#### Utilizacion post sintesis
![[Pasted image 20240719130524.png]]
![[Pasted image 20240719130526.png]]
#### Utilizacion post implementacion
![[Pasted image 20240719130552.png]]
![[Pasted image 20240719130554.png]]
#### Analisis de timing post implementacion
![[Pasted image 20240719130356.png]]
![[Pasted image 20240719130908.png]]

### Analisis con VIO e ILA
#### Utilizacion post sintesis
![[Pasted image 20240719201545.png]]
![[Pasted image 20240719201548.png]]
#### Utilizacion post implementacion
![[Pasted image 20240719201556.png]]
![[Pasted image 20240719201558.png]]

#### Timing post implementacion
![[Pasted image 20240719201441.png]]

## Observaciones
### Porque tiene puerto el modulo CPU y porque son PC y ALU result?
1. Si el modulo no tendria puertos, cuando se sintetize se eliminaria toda la logica
2. En la realidad la interfaz con el microprocesador es mucho mas complicada y se suele dar mediante el compartimiento de memoria
3. Para realizar este tipo de interfaces, se necesita aprender estandares muy complicado y por lo general realizar sistemas de memoria con memorias caches y una virtualizacion de la memoria
4. Por lo tanto se eligen solo 2 salidas: `pc` y `alu_result` 
5. Esta eleccion se basa en la necesidad de asegurar que la lógica interna de la CPU no sea optimizada fuera durante la síntesis en Vivado. Aquí está la justificación detallada para la elección de estas señales específicas:

### Salida `pc` (Program Counter)
1. **Visibilidad del Flujo de Instrucciones**:
   - El contador de programa (`pc`) es una señal fundamental en cualquier microprocesador. Representa la dirección de la instrucción actual que se está ejecutando.
   - Tener `pc` como una salida proporciona visibilidad directa del flujo de instrucciones durante la simulación y la depuración, asegurando que el microprocesador está avanzando correctamente a través de su espacio de instrucciones.

2. **Asegurar la Retención de la Lógica de Control del Flujo**:
   - El `pc` está conectado a múltiples componentes dentro del diseño, como la memoria de instrucciones y las unidades de control de salto (branch). Al exponer `pc`, garantizamos que la lógica relacionada con el control del flujo de instrucciones no sea eliminada durante la síntesis.

### Salida `alu_result` (Resultado de la ALU)
1. **Visibilidad de las Operaciones de Cálculo**:
   - La Unidad Aritmética y Lógica (ALU) es otro componente crítico en cualquier CPU. Realiza operaciones matemáticas y lógicas sobre los operandos.
   - Exponer `alu_result` permite verificar que las operaciones de cálculo se están realizando correctamente.

2. **Asegurar la Retención de la Lógica de Procesamiento**:
   - La ALU interactúa con múltiples partes del diseño, como los registros y la memoria de datos. Tener el resultado de la ALU como una salida asegura que toda la lógica relacionada con las operaciones de cálculo no sea eliminada.

### Consideraciones Adicionales
- **Minimización de la Interfaz**: Elegimos las salidas mínimas necesarias para mantener la simplicidad del diseño mientras garantizamos que Vivado no optimice fuera la lógica esencial. Añadir más salidas innecesarias podría complicar la interfaz y hacer más difícil el análisis y la depuración.
- **Evitar Señales Intermedias**: No elegimos señales intermedias o específicas de etapas internas porque no garantizan la retención completa de toda la lógica. `pc` y `alu_result` son señales de alto nivel que abarcan múltiples componentes y etapas, lo que ayuda a asegurar que la lógica completa del microprocesador se retenga.


# Anexos

## TDD
- Las pruebas se realizaron con un sistema TDD para ser mas ordenada y mas eficientes
























## Cosas que deberia agregar a futuro
- Manejo de operaciones con operandos unsigned
- Manejo de escritura y lectura de byte y de media palabra
- Manejo de instrucciones de control status register
- Manejo de instrucciones de ambiente
- Manejo de instrucciones de sinc
- Manejo de instrucciones de jump & link
- Manejo de comparaciones y modificacion de bit de estado


### CPU con procesamiento vectorial

#### Etapa necesaria para el procesamiento vectorial

![[Pasted image 20231213162213.png]]

#### CPU completo con procesamiento vectorial

![[Pasted image 20231213162855.png]]


#### CPU con procesamiento vectorial y pipeline

##### Etapas
##### IF
![[Pasted image 20231213170641.png]]
##### ID

![[Pasted image 20231213170814.png]]

##### EX
![[Pasted image 20231213170859.png]]


##### ME
![[Pasted image 20231213171037.png]]


##### WB
Esta etapa tiene las mismas componentes que la etapa de ID, ya que se escribe en los registros de vectores y normales

#### Pipeline 
![[Pasted image 20231213173310.png]]








## 9.1)Test-Driven Development TDD
El desarrollo basado en pruebas (Test-Driven Development, TDD) es una práctica de desarrollo de software que se basa en escribir pruebas automatizadas antes de escribir el código de implementación. Es un enfoque iterativo e incremental en el que las pruebas unitarias impulsan el diseño y desarrollo del software.

El proceso de desarrollo basado en pruebas sigue generalmente estos pasos:

1. Escribir una prueba: Se escribe una prueba automatizada que describe el comportamiento esperado del código. Esta prueba inicialmente fallará porque el código aún no ha sido implementado.

2. Ejecutar la prueba: Se ejecuta la prueba automatizada y se verifica que falle, lo cual es esperado en este punto.

3. Escribir el código de implementación mínimo: Se implementa la cantidad mínima de código necesaria para que la prueba pase.

4. Ejecutar todas las pruebas: Se ejecutan todas las pruebas automatizadas, incluyendo la que se acaba de implementar. Se verifica que todas pasen correctamente.

5. Refactorizar el código: Se mejora la estructura y calidad del código sin cambiar su comportamiento. Durante este paso, se pueden identificar nuevas pruebas o mejoras en las existentes.

6. Repetir el ciclo: Se repiten los pasos anteriores para desarrollar nuevas características o modificar las existentes.

En VHDL, el enfoque de desarrollo basado en pruebas (TDD) se puede implementar utilizando las sentencias `assert` para escribir las pruebas automatizadas


## 9.2)CPU Multiciclo
La idea de la CPU multiciclo es realizar una cpu muy eficienciente respecto a area ocupado pero lenta, ya que abusara de la reutilizacion de recursos. Basicamente es una CPU con diseño basado en maquina de estado 
``` verilog
module RISCVCPU (clock);
// Instruction opcodes
	parameter LW = 7'b000_0011, SW = 7'b010_0011, BEQ = 7'b110_0011, NOP = 32'h0000_0013, ALUop = 7'b001_0011;
input clock;
reg [31:0] PC, Regs[0:31], IDEXA, IDEXB, EXMEMB, EXMEMALUOut, MEMWBValue;
reg [31:0] IMemory[0:1023], DMemory[0:1023], // separate memories
		IFIDIR, IDEXIR, EXMEMIR, MEMWBIR; // pipeline registers
wire [4:0] IFIDrs1, IFIDrs2, IDEXrs1, IDEXrs2, EXMEMrd, MEMWBrd; // Access register fields
wire [6:0] IFIDop, IDEXop, EXMEMop, MEMWBop; // Access opcodes
wire [31:0] Ain, Bin; // the ALU inputs
// declare the bypass signals
wire bypassAfromMEM, bypassAfromALUinWB,
	bypassBfromMEM, bypassBfromALUinWB,
	bypassAfromLDinWB, bypassBfromLDinWB;
wire stall; // stall signal
wire takebranch;
assign IFIDop = IFIDIR[6:0];
assign IFIDrs1 = IFIDIR[19:15];
assign IFIDrs2 = IFIDIR[24:20];
assign IDEXop = IDEXIR[6:0];
assign IDEXrs1 = IDEXIR[19:15];
assign IDEXrs2 = IDEXIR[24:20];
assign EXMEMop = EXMEMIR[6:0];
assign EXMEMrd = EXMEMIR[11:7];
assign MEMWBop = MEMWBIR[6:0];
assign MEMWBrd = MEMWBIR[11:7];
// The bypass to input A from the MEM stage for an ALU operation
assign bypassAfromMEM = (IDEXrs1 == EXMEMrd) && (IDEXrs1 != 0) && (EXMEMop == ALUop);
// The bypass to input B from the MEM stage for an ALU operation
assign bypassBfromMEM = (IDEXrs2 == EXMEMrd) && (IDEXrs2 != 0) && (EXMEMop == ALUop);
// The bypass to input A from the WB stage for an ALU operation
assign bypas sAfromALUinWB = (IDEXrs1 == MEMWBrd) && (IDEXrs1 != 0) && (MEMWBop == ALUop);
// The bypass to input B from the WB stage for an ALU operation
assign bypassBfromALUinWB = (IDEXrs2 == MEMWBrd) && (IDEXrs2 != 0) && (MEMWBop == ALUop);
// The bypass to input A from the WB stage for an LW operation
assign bypassAfromLDinWB = (IDEXrs1 == MEMWBrd) && (IDEXrs1 != 0) && (MEMWBop == LW);
// The bypass to input B from the WB stage for an LW operation
assign bypassBfromLDinWB = (IDEXrs2 == MEMWBrd) && (IDEX rs2 != 0) && (MEMWBop == LW);
// The A input to the ALU is bypassed from MEM if there is a bypass there,
// Otherwise from WB if there is a bypass there, and otherwise comes from the IDEX register
assign Ain = bypassAfromMEM ? EXMEMALUOut :
			(bypassAfromALUinWB || bypassAfromLDinWB) ? MEMWBValue :
IDEXA;
// The B input to the ALU is bypassed from MEM if there is a bypass there,
// Otherwise from WB if there is a bypass there, and otherwise comes from the IDEX register
assign Bin = bypassBfromMEM ? EXMEMALUOut :
			(bypassBfromALUinWB || bypassBfromLDinWB) ? MEMWBValue:
IDEXB;
// The signal for detecting a stall based on the use of a result from LW
assign stall = (MEMWBop == LW) && ( // source instruction is a load
				(((IDEXop == LW) || (IDEXop == SW)) && (IDEXrs1 == MEMWBrd))|| // stall for address calc
				((IDEXop == ALUop) && ((IDEXrs1 == MEMWBrd) || (IDEXrs2 == MEMWBrd)))); // ALU use
// Signal for a taken branch: instruction is BEQ and registers are equal
assign takebranch = (IFIDop == BEQ) && (Regs[IFIDrs1] == Regs[IFIDrs2]);
integer i; // used to initialize registers
initial
begin
	PC = 0;
	IFIDIR = NOP; IDEXIR = NOP; EXMEMIR = NOP; MEMWBIR = NOP; // put NOPs in pipeline registers
	for (i=0;i<=31;i=i+1) Regs[i] = i; // initialize registers--just so they aren't cares
	end
// Remember that ALL these actions happen every pipe stage and with the use of <= they happen in parallel!
	always @(posedge clock)
	begin
		if (~stall)
		begin // the first three pipeline stages stall if there is a load hazard
			if (~takebranch)
			begin // first instruction in the pipeline is being fetched normally
				IFIDIR <= IMemory[PC >> 2];
				PC <= PC + 4;
			end
			else
			begin // a taken branch is in ID; instruction in IF is wrong; insert a NOP and reset the PC
				IFIDIR <= NOP;
				PC <= PC + {{52{IFIDIR[31]}}, IFIDIR[7], IFIDIR[30:25], IFIDIR[11:8], 1'b0};
			end
// second instruction in pipeline is fetching registers
			IDEXA <= Regs[IFIDrs1]; IDEXB <= Regs[IFIDrs2]; // get two registers
			IDEXIR <= IFIDIR; // pass along IR--can happen anywhere, since this affects next stage only!
			// third instruction is doing addre ss calculation or ALU operation
			if (IDEXop == LW)
				EXMEMALUOut <= IDEXA + {{53{IDEXIR[31]}}, IDEXIR[30:20]};
			else if (IDEXop == SW)
				EXMEMALUOut <= IDEXA + {{53{IDEXIR[31]}}, IDEXIR[30:25], IDEXIR[11:7]};
			else if (IDEXop == ALUop)
				case (IDEXIR[31:25]) // case for the various R-type instructions
					0: EXMEMALUOut <= Ain + Bin; // add operation
					default: ; // other R-type operations: subtract, SLT, etc.
				endcase
				EXMEMIR <= IDEXIR; EXMEMB <= IDEXB; // pass along the IR & B register
			end
			else EXMEMIR <= NOP; // Freeze first three stages of pipeline; inject a nop into the EX output
// Mem stage of pipeline
			if (EXMEMop == ALUop) MEMWBValue <= EXMEMALUOut; // pass along ALU result
			else if (EXMEMop == LW) MEMWBValue <= DMemory[EXMEMALUOut >> 2];
			else if (EXMEMop == SW) DMemory[EXMEMALUOut >> 2] <= EXMEMB; //store
			MEMWBIR <= EXMEMIR; // pass along IR 
			
			// WB stage
			if (((MEMWBop == LW) || (MEMWBop == ALUop)) && (MEM WBrd != 0)) // update registers if load/ALU operation and destination not 0
			Regs[MEMWBrd] <= MEMWBValue;
		end
endmodule
```



# Referencias
- [Cátedra de Arquitectura de Computadoras](https://microprocesadores.unt.edu.ar/arqcom/)
-  Patterson, D. A., & Hennessy, J. L. (2017). Computer Organization and Design RISC-V Edition: The Hardware Software Interface.
- Tocci, R. J. (Ed.). (n.d.). Sistemas Digitales (7.ª edición).
- Vivado Design Suite User Guide UG906