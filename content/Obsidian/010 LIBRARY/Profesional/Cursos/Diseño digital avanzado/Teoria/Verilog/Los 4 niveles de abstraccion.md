
# Los 4 niveles de abstraccion
## Introducción

- **Niveles de abstracción**
	- Cuales son los niveles de abstraccion que se manejan en diseño digital?
	- Que nivel usaremos en verilog?
	- Cuando es conveniente usar dataflow?
	- Cuando es conveniente utilizar RTL?
	- Cuando es conveniente utilizar switch?
	- Cuando es conveniente utilizar gate?




## Niveles de abstracción
![[Pasted image 20231009203323.png]]

 Estos niveles representan diferentes formas de describir el comportamiento y la estructura de un circuito digital en Verilog, desde el nivel más bajo de detalle hasta el nivel más alto de abstracción.

1. **Switch Level (Nivel de interruptores):**
   - Este es el nivel más bajo de abstracción.
   - Se describe el comportamiento del circuito en términos de interruptores y transistores individuales.
2. **Gate Level (Nivel de compuertas):**
   - En este nivel, el diseño se describe en términos de compuertas lógicas como AND, OR, NOT, etc.

3. **Dataflow Level (Nivel de flujo de datos):**
   - A este nivel, se describe el comportamiento del circuito en términos de cómo fluye y se transforma la información a través de registros y operaciones.

4. **Behavioral Level (Nivel de comportamiento):**
   - Este es el nivel más alto de abstracción y se centra en la descripción del comportamiento del sistema en lugar de su estructura interna.
   - Se utilizan descripciones en lenguaje natural o expresiones matemáticas para definir cómo debe funcionar el sistema.
   - Es el nivel de abstracción más cercano a la especificación del diseño y se utiliza en la etapa inicial de diseño para definir el comportamiento deseado del sistema.


En este curso usaremos los niveles de Dataflow o Behavioral



## Nivel Dataflow o RTL
Este nivel es el que usaremos, es superior al usado en VHDL ya que no hace falta conocer la arquitectura, si no mas una descripcion funcional.Describiremos cuales son los operadores que podemos usar en este nivel

### Operadores de bit
![[Pasted image 20231013113102.png|200]]
### Operadores aritmeticos
![[Pasted image 20231013113124.png|300]]
- La division y el modulo no se sintetizan, solo se puede usar para limites de bucles o algo asi.
	- Para aplicar la division podemos usar un shift
	- Para el modulo se puede usar el overflow
### Operadores relacionales
![[Pasted image 20231013113150.png|300]]
- El triple igual permite analizar desconocido y alta impedancia

### Operadores Logicos
![[Pasted image 20231013113233.png|300]]



### Operadores de corrimiento
![[Pasted image 20231013113327.png|300]]


### Operador condicional
![[Pasted image 20231013113402.png|300]]


### Operadores de concatenacion
![[Pasted image 20231013113423.png]]