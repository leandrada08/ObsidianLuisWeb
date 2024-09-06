**Nombre:** Luis Elian Andrada
**DNI:** 43362912

## Enunciado
### Pirmera parte
- Utilizando la herramienta Vivado generar un proyecto para cada escenario de prueba.
- Los escenarios de prueba son:
	- Sumadores
	- Multiplicadores
	- Filtros FIR
- [x] Incluir en el proyecto los archivos entregados por la cátedra para cada escenario.
	- Ejemplo: Para el proyecto sumador, en la pestaña Sources deberíamos incluir:
		- En la carpeta Design Sources: rca.v, bcla.v y hierarchicalcsa.v.
		- En la carpeta Constraint: adderConstraint.xdc.
		- En la carpeta Simulation Sources: tb_adder.v.
- [x]  Una vez incluido los archivos, ejecutar la simulación comportamental para verificar la correcta instancia de los bloques.
- [x] Elaborar el módulo Top Level que instancie todas las opciones de módulos de cada escenario. El nombre de los puertos de entrada y salida deben ser iguales que los definidos en los archivos xdc.
	- El diseño debe incluir condicionales de síntesis (‘ifdef - ‘elsif - ‘else - ‘endif) para seleccionar que bloque sintetizar.




- [x] Para verificar que el diseño se realizó correctamente, incluir en el TestBench el módulo Top Level y verificar el funcionamiento comparando la salida del módulo Top contra la salida del módulo individual.
	- Ejemplo: Para el proyecto sumadores, en la pestaña Sources deberíamos incluir
		- El nuevo módulo TopAdder.v (diseñado por el alumno) en la carpeta Design Sources.
		- En el archivo tb_adder.v debemos instanciar el módulo TopAdder.v y comparar la salida del módulo rca.v del testbench si definimos internamente en el módulo Top el sumador RCA.

- [x]  Síntesis
	- [x]  Report Cell Usage
	- [x]  Report Instance Areas
	- [x]  ROM, RAM, DSP and Shift Register Reporting
- [x]  Esquemáticos
	- [x]  Obtener los esquemáticos de RTL e Implementation.
	- [x]  Nota: Generar estos esquemáticos para una sola frecuencia de reloj.
- [ ]  Implementación
	- [ ]  Implementar el diseño variando las frecuencias de reloj para 50MHz, 100MHz y 200MHz.
	- [ ]  En cada caso obtener el Slack Histogram (Create Slack Histogram) y el Worst Slack del camino crítico.

- [x] Elaborar un informe que incluya todos los resultados.
- [ ] Analizar cual de las técnicas es menos complejo y cual puede trabajar a mayor frecuencia para cada uno de los escenarios propuestos.




## Creacion de proyecto y verificacion de los codigos dado
### Sumadores
![[Pasted image 20240219194502.png]]


### Multiplicadores
![[Pasted image 20240220114519.png]]
### FIR
![[Pasted image 20240220110739.png]]


## Creacion del top y verificacion de su correcto funcionamiento
- Hay que tener en cuenta que nuestro modulo Top atrasa 1 T la señal, es por eso que al ver el valor no es la misma pero la comparacion da 0, porque cree una señal auxiliar tambien retrasada de cada modulo para compararla con la del top
### SUM
#### TOP vs RCA
![[Pasted image 20240220103447.png]]

#### TOP vs HCSA
![[Pasted image 20240220103107.png]]
#### TOP vs BCLA
![[Pasted image 20240220103833.png]]



### FIR

#### TOP vs BASICO
![[Pasted image 20240220111433.png]]


#### TOP vs CSD
![[Pasted image 20240220111757.png]]

#### TOP vs CV
![[Pasted image 20240220111936.png]]


#### TOP vs DA
- La comparacion no es 1 porque los bloques tienen clock distintos
![[Pasted image 20240220112208.png]]

#### TOP vs TD
![[Pasted image 20240220112331.png]]







### MUL

#### TOP vs MULT BASICO
![[Pasted image 20240220114750.png]]
#### TOP vs BOOTH
![[Pasted image 20240220114905.png]]

## Sintesis

### SUM
#### Basico
![[Pasted image 20240220194820.png]]
#### HCSA
![[Pasted image 20240220194019.png]]

#### BCLA
![[Pasted image 20240220191444.png]]

### FIR
#### Basico
![[Pasted image 20240220190253.png]]
#### DA
![[Pasted image 20240220185451.png]]
#### CSD
![[Pasted image 20240220183730.png]]
#### CV
![[Pasted image 20240220182227.png]]
#### TDFComp
![[Pasted image 20240220124016.png]]

### MULT
#### BASICO
![[Pasted image 20240220122616.png]]
#### BOOTH
![[Pasted image 20240220122008.png]]
## Esquematico

### SUM
#### Basico
![[Pasted image 20240220194725.png]]
![[Pasted image 20240220194757.png]]
#### HCSA
![[Pasted image 20240220193823.png]]
![[Pasted image 20240220193911.png]]
#### BCLA
![[Pasted image 20240220190658.png]]
![[Pasted image 20240220191425.png]]
### FIR
#### Basico
![[Pasted image 20240220185606.png]]
![[Pasted image 20240220190200.png]]
#### DA
![[Pasted image 20240220185244.png]]
![[Pasted image 20240220185316.png]]
#### CSD
![[Pasted image 20240220182450.png]]
![[Pasted image 20240220183719.png]]
#### CV
![[Pasted image 20240220181624.png]]
![[Pasted image 20240220182003.png]]


#### TDFComp
![[Pasted image 20240220122930.png]]
![[Pasted image 20240220124044.png]]

### MULT

#### BASICO
![[Pasted image 20240220115714.png]]
![[Pasted image 20240220122658.png]]

#### BOOTH
![[Pasted image 20240220115542.png]]
![[Pasted image 20240220121840.png]]
## Implementacion

### SUM
#### BASICO
##### 100 MHz

##### 50 MHz

##### 200 MHz
#### BOOTH
##### 100 MHz

##### 50 MHz

##### 200 MHz

### FIR
#### BASICO
##### 100 MHz

##### 50 MHz

##### 200 MHz
#### BOOTH
##### 100 MHz

##### 50 MHz

##### 200 MHz

### MULT
#### BASICO
##### 100 MHz

##### 50 MHz

##### 200 MHz
#### BOOTH
##### 100 MHz

##### 50 MHz

##### 200 MHz

## Informe de resultados
- Primero debemos hacer una analisis de la cantidad de elementos y de que tipo de elemento
### Sumadores
#### RCA
- La mayoria de elementos son de registros de entrada y salida
- La complejidad es muy poca
- Se busco forzar el uso de LUT para hacer un mejor analisis de comparacion
	- En este caso tenemos LUT de 1 a 6 entrada y carrys

#### BCLA
- En este caso no tenemos elementos de carry debido a que hacemos las operaciones logica de manera minusiosa por lo cual la herramiento no inferiere carry para estas operaciones
	- Entonces como solo tenemos operaciones logica la herramienta las implementa a todas con LUT
	- Seria distintos si realizamos la operacion en mayor nivel como A+B porque al sintetizar la herramienta esta operacion usaria elementos de carry

#### HCSA
- Ocurre exactamente lo mismo que con el BCLA

### Multiplicador
- En el multiplicador de BOOTH se usa menos carry ya que tenemos una diminusion en los productos parciales por lo cual al tener menos sumas de productos parciales se usa menos elementos de carry
	- Esto tambien se debe que tenemos menos cantidad de niveles
	- Esto tambien genera que sea mas rapido


### Filtros
- Si nos focalizamos en area, el que menos utiliza es el basico, ya que utiliza DSP
- Cuando aplicamos las otras tecnicas se utilizan mas registros respecto al basico
	- En el transpuestos se utilizan muchos mas registros, casi el doble
- En que mejor se adapta a la frecuencia de trabajo es el transpuesto
	- Esto se debe a que tenemos camino critico solo de un multiplicar y un sumador
- Las limitacion del bascio se debe a la comunicacion entre los DSP y los CLB 
- Cuando incluimos el vector de correccion obtenemos mejor velocidad de trabajo y ademas reducimos los elementos logicos
#### Basico
- Se utilizan DPS para poder ahcer las operaciones
- No utiliza elementos de acarreo
	- Esto se debe a que se resuelve todo con DPS y sus acarreos internos
- En otras estructuras no se usan DPS por lo cual se usa elementos de carry y LUT ya que rompemos la logica de DPS e implementamos el diseño con logica


