  
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
<!--ID: 1683126206256-->




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


### Modos de direccionamiento #Completar
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
<!--ID: 1683126206263-->





### Extension C
La mayoria de las instruccion de I se mapean a una version equivalente de 16 bits.
- Para hacer esto, acceden a los 10 registros mas populares, sobreescriben un operando y usan constantes mas pequenas.
- Muy usado para sistemas embebidos, apra reducir costos
- Puede mejorar el performance(en promedio se buscan 3 bytes por instrucciones)
*Idea clave:* Nosotros escribimos siempre igual y el ensablador se encarga de elegir la version comprimida cuando sea posible

# Consultas
- Los ISA definen la implementacion? Osea, yo tengo que hacer un micro en funcion del isa que usare?
- No entiendo la instruccion *LUI*
- Nosotros aprendemos a elegir ISA. Pero a diseniar un ISA?
- Es un problema que no defina una implmentacion?