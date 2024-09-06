## Ideas basicas de disenio multiciclo
Dividir las instrucciones en multiples "pasos" modulares. Cualquier instruccion se forma mediante la combinacion de estos pasos entonces cada instruccion demora distintas cantidad de ciclos.
- Buscamos que cada paso se ejecute en un ciclo T pequenio. Buscamos que sean baleanceados los pasos.
- Reutilizamos recursos para minimizar costos.
## Camino de datos
![[Pasted image 20230503081923.png|1300]]
### Pasos de ejecucion de las instrucciones
Los mismo que vimos en pipeline *IF, ID, EX, ME y WB*. La diferencia es que ahora cada instruccion utiliza los que necesita. Algunos pasos pueden utilizar dos unidades funcionales, pero lo hacen en paralelo y no secuencialmente.
![[Pasted image 20230503082625.png|1200]]
## Unidad de control
El control de la ALU es igual. Se agregaron nuevos multiplexores que necesitan nuevas seniales de control. En este caso, las señales de control no depende unicamente de la instruccion, tambien depende de que ciclo esta ejecutando, por ejemplo la ALU en add, en el primer ciclo suma 4 pero en el segundo suma pc con inmediate y recien en el tercero suma add, entonces la ALU debe saber que hacer en cada ciclo. Por lo tanto, *el control es secuencial* y no combinacional.
![[Pasted image 20230503083101.png|600]]
### MEF de control
La MEF tiene 9 estado. Uno por cada "paso" diferente. Pero el camino mas largo tiene 4 estados. La maquina sera de Moore.
![[Pasted image 20230503085241.png|300]]
Otra manera mas didactica
![[Pasted image 20230503122603.png|300]]
#### Transicion de estados
- 3 estados pasan siempre al siguiente
- 4 estados vuelven siempre a 0
- 2 estados tienen bifurcaciones que dependen de la instruccion
![[Pasted image 20230503090640.png|500]]
![[Pasted image 20230503090653.png|500]]
#### Implementacion tradicional
Recibe como entradas los bits del opcode y los del estado actual. La logica de control determina las señales para el camino de datos y para el proximo estado.
#### Implementa con ROM
Tenemos 7 entradas y 4 bit de estado= 11 bit. Esto nos da 2048 direcciones diferentes
- Cada uno representa un estado de la MEF
	- No tenemos 2048 estado !ojo!
- Salidas: 16 para el camino de datos y 4 para el estado
$$2^{11}.20=40Kbits$$
##### Observaciones:
- Si tenemos mas instrucciones, aumentan las salidas
- No tiene en cuenta ondiciones de indiferencias
#### Implmentacion con ROM mejorada
La MEF es de tipo Moore. Las seniales de salida dependen unicamente del estado actual.
Es posible dividir la ROM anterior en dos:
- ROM1: 4 bits de entrada producen 16 bits de salida
	- El estado actual genera las seniales de control
- ROM2: 11 bits de entrada producen 4 bits de salida
	- El estado actual+el opcode determinan el estado siguiente.
$$2^4.16+2^{11}.4=8,25Kbits$$
Mucho mas eficiente que la ROM inicial pero sigue teniendo problema ya que no vemos las condiciones redudantes.
#### Microprogramacion 
- Las salidas de la ROM1 la llamamos microinstrucciones. Son las señales de control para el camino de datos.
- Se remplaza la ROM2 por un circuito denominado secuenciador.
	- Un registro que mantiene el estado actual "*State*"
	- Un sumador que incremente en 1 el estado "*Adder*"
	- Una logica para determinar el proxima estado "*Address select logic*"
		- Las seniales de control para esta logica deben estar en la microinstruccion "*AddrCtl*"
![[Pasted image 20230503093343.png|400]]
##### Detalle del secuenciador
- La logica para determinar el proximo estado se implementa simplemente con un multiplexor
- Agregamos 2 ROM muy pequenias para los casos en los que haya bifurcaciones en la MEF 
![[Pasted image 20230503093515.png|400]]
##### Contenido de la ROM1
- A las saldias de control para el camino de datos se le agregan las salida de control para el secuenciador(2 bits)
- Cada fila representa un estado
![[Pasted image 20230503093741.png|400]]
##### Microprogramacion (TEMA IMPORTANTE)
Un programa es una secuencia de instrucciones, que indica que hacer con datos y como sigue la secuencia
- En la ROM1 las salidas indican al camino de datos que hacer, y como sigue la secuencia.
	- Entonces cada linea de la ROM1 se denomina microinstruccion.
	- El contenido de la ROM1 se denomina *microprograma*
##### Conclusiones Luis
La ROM1 basicamente maneja las salidas de control en funcion del estado y el secuenciador solo se encarga de modificar el estado

##### Implicancias de microprogramacion 
Cada instruccion del programa se mapea en una secuencia de microinstrucciones, mientras las microinstrucciones manejan señales de control, mientras que las instrucciones manejan datos
- Las microinstrucciones son fijas
	- Las instrucciones pueden cambiar entre cada programa
	- Cambiar las microinstrucciones implica cambiar la ROM de microcodigo, cambiar el firmware
	- Es muy facil agregar nuevas instruccciones, mas complejas, como combinaciones de microinstrucciones
##### Conclusiones de microprogramacion 
![[Pasted image 20230503124825.png|500]]
## Manejo de interrupciones/excepciones
En la MEF de control se agregan estados para las interrupciones/excepciones
- Siempre hay que tener en cuenta que las instrucciones con problemas no modifiquen los registros ni memoria
