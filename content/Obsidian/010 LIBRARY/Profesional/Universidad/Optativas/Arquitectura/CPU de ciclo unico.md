
**Objetivo:** Todas las intrucciones en un ciclo de reloj $$CPI=1$$
## Haciendo nuestro camino de datos
### Metodologia de Clocking
Define cuando las seniales pueden ser leidas y cuando escritas
- La logica combinaacional modifica los datos en un ciclo de reloj.
	- El mayor retardo combinacion determina la duracion del ciclo de reloj.
### Componentes
#### Combinacionales
Sus salida solo dependen de sus entradas
- Compuertas logicas
- Multiplexores
- ALU
- Sumadores
#### Secuenciales
Su salida depende de sus entradas y de su estado actual.
- Registros
- Filp-Flop tipo D
#### Banco de registros
- 32 registros agrupados.
- Dos puertos de lectura de salida, con dos entradas de seleccion correspondientes
	- Se hacen 2 puertos de lectura porque casi siempre leo 2 datos y escribo 1
![[Pasted image 20230416210600.png]]
#### Memoria ideal
Esta memoria tendre:
- Una entrada de direcciones
- Una entrada de datos
- Una salida de datos.
- Dos seniales de control
	- Para lectura y escritura
	- No siempre es asi



## Pasos para diseniar una instruccion 
1. Analizar el ISA
2. Describimos la instruccion en RTL abstracto
3. Analizamos el camino de dato si puede cumplir lo especificado
4. Modificamos el control de ser necesario.
<!--ID: 1682692834908-->



### Subconjunto del ISA de RISC-V
Nuestro camino de datos implementara las instrucciones
- Referencias a memoria: LW, SW
- Procesamiento: ADD, SUB, AND, OR.(todas las tipo R)
- Saltos: BEQ
#### Algunos RTL abstractos
![[Pasted image 20230416212530.png]]





## Diseniando nuestras intrucciones
### Comun en todas las instrucciones
#### Fetch de las instrucciones
1. PC: comun a todas las intrucciones secuenciales
2. Una memoria para instrucciones: la salida de la memoria contiene la instruccion a ejecutar.
3. Un sumador que sume 4
#### Camino de datos para el fetch
![[Pasted image 20230416213453.png]]
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
#### Componentes nuevos que necesitaremos
1. Extensor de signo para la constante inmediata
2. Una memoria de datos
	- Esta debe tener una entrada de direccion
	- Entrada de datos
	- Salida de datos
	- Seniales de contro de lectura y escritura
#### Camino de datos Tipo R/Load/Store
![[Pasted image 20230416215027.png]]
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
![[Pasted image 20230416222811.png]]
### Camino de dato completo
![[Pasted image 20230416222840.png]]






## Seniales de control
La Alu tipicamente tiene 4 bit, aunque nosostros no necesitamos todas las funciones
1. Para LW y SW necesitamos que sume(muchas veces una constante)
2. Para BEQ que reste
3. Para las Tipo R, que haga lo que corresponda.
*Separaremos el control de la ALU del control principal*
### Control de la ALU
Posee como entrada un campo de 2 bits, ALUOp, que permite codificar las tres funciones principales mencionadas.
- Ademas recibe como entrada los campos funcion de las instrucciones de formato R
- Genera una salida los 4 bits para controlar la ALU.
![[Pasted image 20230421191328.png|00]]
### Control principal
Es necesario establecer 6 seniales de control de 1 bit, mas ALUOp de 2 bits.
- Los valores de estas seniales dependen de las instrucciones a ejecutar
![[Pasted image 20230421191351.png|00]]





## Camino de datos+Control
![[Pasted image 20230421190248.png|1000]]
Este camino de datos implementa las funciones:
- lw
- sw
- beq
- algebraicas





## Conclusion
Tema importantes
- RTL abstracto
- Implmentacion con componentes de estos RTL
- La unidad de control resulta combinacional
- La duracion del tiempo de ciclo determinado por la instruccion mas lenta(*problema*)