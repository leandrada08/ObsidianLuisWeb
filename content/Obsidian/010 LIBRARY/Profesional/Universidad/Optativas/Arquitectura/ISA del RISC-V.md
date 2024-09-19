
# Ingles


## Introduction to RISC-V
- It's a new ISA (2014)
- Defines an ISA, not an implementation
- It's *free and open*. https://github.com/riscv/

## General characteristics
- Being new, it is based on the successes and failures of other architectures:
	- x86 and AMD64.
	- ARMv7, ARMv8, Thumb, and Thumb2.
	- MIPS.
- It is fully *modular:*
	- It's the only modular ISA
	- This allows it to be used for many things, using only the parts that each one needs
	- It has a focus on exploring new concepts rather than compatibility with existing products.
### ISA Naming Conventions
$$RV[###][abc...xyz]$$
- RV: RISC-V ISA
- \[\#\#\#\]: **{32,64,128} width of integer registers and memory address size**
- \[abc...xyz\]: Supported extensions
	- *RV32I* is the base core, the only mandatory extension (Actually, only *I* is mandatory)
	- Very few instructions (47)
### RISC-V Extensions
#### Standard
They are widely accepted by the community
- *M:* Adds multiplication and division
- *A:* Adds atomic memory instructions (for operating systems)
- *F:* Adds floating point (Single precision)
- *D:* Adds floating point (Double precision)
- *G:* $I+M+A+F+D$
- *C:* Adds 16-bit compressed versions of *I*
#### Additional
![[Pasted image 20230405085146.png|500]]
- Custom extensions allow adding any desired functionality. Basically, anyone can add an extension they want.

### Storage cells
- 3 operands, *LOAD/STORE* type
- 32-bit memory address (*32I*).
	- Address space: 4GB
	- Byte addressable
	- Little endian
- 32 registers (x0 to x31) of the defined width (32 if it is *32I*)
	- The x0 register is hardwired to 0
	- Extensions can add registers
- Has a PC register
- Has 17 status and control registers
- Several performance monitoring registers for 32I

### Instruction formats 
Fixed length of 32 bits, regardless if it is 64I or 128I
- 4 base formats:
	- TYPE R: Arithmetic operations
	- TYPE I: Operations with immediate constants
	- TYPE S: For Store operations
	- TYPE U: For handling larger constants
![[Pasted image 20230405092632.png]]

#### Opcode Details
The Opcode in RISC-V identifies groups of instructions, which are distinguished by the function fields. This is why out of the 47 base instructions, only 11 of the 128 available opcodes are used (*Genius*).
#### Format Details
Notice that always, in all format types, the same fields are in the same place. This helps with *Regularity*. It simplifies decoding, saves time by accessing registers before decoding, avoids adding extra hardware, and facilitates the implementation of new instructions.
- Immediate fields are always sign-extended.
- An instruction with all bits set to 0 or 1 is invalid.
	- This is to avoid common mistakes.
#### Additional Format
Used for jumps.
- TYPE B: Almost the same as S
- TYPE J: Almost the same as U
	- The difference in both is that the immediate field is shifted one bit to the left. This is equivalent to multiplying the constant by 2.
		- This allows it to jump further. But it can only jump to even addresses, which is not an issue since the smallest instructions are half-words (even addresses).
### Instructions
![[Pasted image 20230411204725.png]]
- LW has indexed addressing mode, just like SW
	- So, LW rd, rs, imm     R\[rd\]<-M\[R\[rs\]+imm\]
- Jump instructions with registers (compare two registers)
	- slt rd, rs1, rs2     R\[rd\]=1 If R\[rs1\]<R\[rs2\]
		- If the condition is not met, it sets 0
- Jump instructions (also done by comparing registers)
	- JAL rd, imm    PC\[imm\] and R\[rd\]=PC+4
#### Instruction Comments
- No instruction generates overflow, checking must be done via software.
- The LUI instruction is used to load very large constant values.
- The AUIPC instruction adds the immediate constant to the most significant part of the PC.

### Addressing Modes 
![[Pasted image 20230411211802.png]]

### Register Usage Conventions
Defines standard functions for registers. Indicates which registers should be preserved by the caller routine and which by the callee routine. Allows program interoperability.
These conventions are called ABI; there are several. We will use *dasd*.
![[Pasted image 20230412135621.png]]
- x1: return address
- x2: stack pointer
### Pseudo-instructions
Implemented with ISA instructions, easier for the programmer.
### Memory Usage
- The first block is reserved for the OS
- Program code starts at 0x0040.0000
- Static data starts immediately after the program
- Dynamic data starts after the static data and grows toward the stack
- The stack starts at high addresses and grows downwards
![[Pasted image 20230412202953.png]]
### Subroutine Calling Convention 
6 steps
1. Place arguments somewhere the subroutine can access
2. Jump to the subroutine (use *jal ra, destination*)
3. Reserve the memory space required by the subroutine (decrement *sp*), storing necessary registers (*ra* at minimum)
4. Perform the subroutine’s task
5. Place the result in a location accessible by the caller, restore registers (*ra* at minimum), and free memory (incrementing *sp*)
6. Return control to the origin (using *ret*)

### Extension C
Most of the instructions in I are mapped to an equivalent 16-bit version.
- To do this, they access the 10 most popular registers, overwrite an operand, and use smaller constants.
- Widely used for embedded systems to reduce costs.
- Can improve performance (on average, 3 bytes per instruction are fetched).
*Key Idea:* We always write the same way, and the assembler takes care of choosing the compressed version when possible.




# Español
## Introduccion del RISC-V
- Es un isa nuevo(2014)
- Define un ISA, no una implementacion
- Es *gratuito y abierto*. https://github.com/riscv/

## Caracteristicas generales
- Al ser nuevo, esta basado en los aciertos y en los errores de las otras arquitecturas:
	- x86 y AMD64.
	- ARMv7, ARMv8, Thumb y Thumb2.
	- MIPS.
- Es totalmente *modular:*
	- Es el unico ISA modular
	- Esto permite que se pueda usar para multitud de cosas, usando las partes que necesita cada uno
	- tiene un enfoque de exploracion de nuevos conceptos, mas que en compatibilidad con productos existentes.
### Convenciones de nombres de ISA
$$RV[###][abc...xyz]$$
- RV: ISA de RISC-V
- \[\#\#\#\]: **{32,64,128} ancho de registros de entrero y el tamanio de las direcciones de memoria**
- \[abc...xyz\]: Extensiones soportada
	- *RV32I* es el nucleo base, la unica extension obligatoria(En realidad lo es la *I*)
	- Muy pocas instrucciones(47)
### Entensiones RISC-V 
#### Estandar
Cuentan con amplica aceptacion por parte de la comunidad
- *M:* Agrega multiplicaciones y division
- *A:* Agrega instrucciones atomicas en memoria(para sistemas operativos)
- *F:* Agrega punto flotante(Precision simple)
- *D:* Agrega punto flotante(Precision doble)
- *G:* $I+M+A+F+D$
- *C:* Agrega versiones comprimidas en 16 bits de *I*
#### Adicionales
![[Pasted image 20230405085146.png|500]]
- Las extensiones customizadas permiten agregar cualquier funcionalidad deseada. Basicamente cualquiera puede agregar una extension que desee.


### Celdas de almacenamiento
- 3 operandos, de tipo *LOAD/STORE*
- Direccion de memoria de 32 bits(*32I*).
	- Espacio de direcciones: 4GB
	- Direccionable de a byte
	- Little endian
- 32 registros(x0 a x31) del ancho definido(32 si es *32I*)
	- El registro x0 esta cableado a 0
	- Las extensiones pueden agregar registros
- Tiene un registro PC
- Tiene 17 registros de estado y de control
- Varios registros para monitoreo de 32Iperformance

### Formatos de instrucciones 
Longitud fija de 32 bits. Sin importar si es 64I, 128I
- 4 formatos base:
	- TIPO R: Operaciones aritmetica
	- TIPO I: Operaciones con constantes inmediatas
	- TIPO S: Para operaciones con Store
	- TIPO U: Para manejo de constantes mas grandes
![[Pasted image 20230405092632.png]]





#### Detalles del Opcodes
El Opcode en RISC-V identifica grupos de instrucciones, que se distinguen mediante los campos de funcion. Es por ello que de las 47 instrucciones base solo usan 11 de los 128 opcodes disponible(*Genios*).
#### Detalles del formato
Ver que siempre, en todos los tipos de formato, los campos iguales estan en el mismo lugar. Esto nos ayuda para la *Regularidad*. Esto simplifica la decodificaion, permite ganas tiempo, al acceder a los registros antes de la decodificacion, evita tener que agregar hardware extra y facilita la implementacion de nuevas intrucciones
- Los campos inmediatos siempre son extendidos en signos.
- Una instruccion con todos sus bits en 0 o en 1 es invalida.
	- Esto es para evitar errores comunes.
#### Formato adicionales
Utilizados para saltos.
- TIPO B: Casi igual que S
- TIPO J: Casi igual que U
	- La diferencia en ambos es que el campo inmediato esta desplazado un bit hacia la izquierda. Esto es equivalente a multiplicar por 2 la constante
		- Esto lo hace para que pueda salta mas lejos. Pero solo puedo saltar a direcciones pares, esto no es un problema ya que las intrucciones mas pequenia son de media palabras(direcciones pares)
### InstruccionesS
![[Pasted image 20230411204725.png]]
- LW tiene un modo de direccionamiento indexado, al igual que SW
	- Osea LW rd, rs, inm     R\[rd\]<-M\[R\[rs\]+inm\]
- Instrucciones de saltos con registros(compara 2 registros)
	- slt rd, rs1, rs2     R\[rd\]=1 Si R\[rs1\]<R\[rs2\]
		- Si no se cumple la condicion, pone 0
- Intruciones de saltos(tambien se hace comparando registros)
	- JAL rd, inm    PC\[inm\] y R\[rd\]=PC+4
#### Comentarios de las instrucciones
- Ninguna instruccion genera overflow, la comprobacion debe hacerse mediante software
- La instruccion LUI sirve para cargar valor de constantes muy grandes
- La instruccion AUIPC suma la constante inmediata a los valores mas significativos de PC


### Modos de direccionamiento 
![[Pasted image 20230411211802.png]]



### Convencion de uso de registros
Define funciones estandares para los registros. Indica cuales registros deben ser preservados por la rutina caller y cuales por la rutina callee. Permite la interoperabilidad de los programas.
Estas convenciones se llaman abi, hay varias, nosotros usaremos la *dasd*
![[Pasted image 20230412135621.png]]
- x1: direccion de retorno
- x2: puntero a pila
### Pseudoinstrucciones
Se implementan con instrucciones del ISA, son mas faciles para el programador
### Uso de la memoria 
- El primer bloque es reservado para el SO
- El codigo de programa comienza en 0x0040.0000
- Los datos estaticos mienzan inmediatamente despues del programa
- Los datos dinamicos comienzan despues de los estaticos y crecen hacia el stack
- El stack comienza en direcciones altas y crecen hacia abajo
![[Pasted image 20230412202953.png]]
### Convencio de llamado a subrutina 
6 pasos
1. Poner argumentos en algun lugar donde la subrutina pueda accederlo
2. Saltar a la subrutina(usar *jal ra, destino*)
3. Reservar el espacio de memoria requerido por la subrutina(decremento *sp*), almacenando los registros necesarios(*ra* como minimo)
4. Realizar la tarea requerida de la subrutina
5. Poner el resultado de la subrutina en algun lugar accesible por el que la mando, restaurar los registros(*ra* como minimo) y liberar la memoria(incrementando *sp*)
6. Retornar el control al punto de origen(usando *ret*)




### Extension C
La mayoria de las instruccion de I se mapean a una version equivalente de 16 bits.
- Para hacer esto, acceden a los 10 registros mas populares, sobreescriben un operando y usan constantes mas pequenas.
- Muy usado para sistemas embebidos, apra reducir costos
- Puede mejorar el performance(en promedio se buscan 3 bytes por instrucciones)
*Idea clave:* Nosotros escribimos siempre igual y el ensablador se encarga de elegir la version comprimida cuando sea posible

