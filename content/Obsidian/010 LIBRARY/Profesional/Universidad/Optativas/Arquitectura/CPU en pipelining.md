
## Pipelining en el camino de datos(etapas del mismo) 
Separar el camino de datos en etapas independientes, esto lo haremos con buffers.
**Etapas de nuestro PIPELINING**:
1. IF: Busqueda de la instruccion
2. ID: Decodificacion de la instruccion
3. EX: Ejecucion de la operacion
4. ME: Acceso a memoria
5. WB: Escritura del resultado
- Cada etapa se ejecutara en 1 ciclo
- La separacion anteriore de etapas es posible gracias a que el ISA de RISC-V fue diseniado pensando en pipelining
<!--ID: 1682692834916-->



#### Caso practico con numeros
![[Pasted image 20230417084540.png]]
- Cuando tendemos a infinito el analisis, la acelaracion es 4.
- Cuando analizamos 3 LW, la aceleracion es mucho menor, es entre 1,5 y 2
#### Pipelining vs ciclo unico
- En estado de regimen, conseguimos que salgan una instruccion en cada ciclo
- Pero la aceleracion no es igual a la cantidad de etapadas(ya que no demoran lo mismo)
- La latencia de una instruccion aumento
	- Pero no nos importa, ya que nos importa la productividad
### Camino de datos en pipelining
![[Pasted image 20230417085547.png]]
### Control en Pipeline
La unidad de control es igual a la del ciclo unico, las seniales de control tambien se escriben en los registros intermedios y se propagan junto con la instruccion
![[Pasted image 20230417093625.png]]
### Camino de datos en pipeline completo
![[Pasted image 20230417093727.png|700]]



## Problemas del procesador en pipeline 
Los problemas que pueden ocurrir se llaman riesgos, y pueden ser:
- *Estructurales:* 2 instruccion intenta ocupar la misma etapa
- *De Datos:* Hay que esperar que una instruccion previa se complete(dependencias)
- *De Control:* La decision de que accion tomar depende de una instruccion previa(saltos)
$$CPIpipeline=CPIideal+ParadasRiesgoEstructural+ParadasRiesgoDatos+ParadasRiesgosControl$$
<!--ID: 1682692834920-->




### Cuando hay que parar el pipeline
- Si el riesgo no se soluciona, hay que *para el pipeline* hasta que se resuelva el riesgo.
	- Se dice que se insertan una o mas "burbujas" en el pipeline



#### Como insertar una burbuja 
1. Hay que poner todas las senialse de control del registro ID/EX en cero.
	- Hace que en las etapas no se haga nada.
2. Evitar la actualizacion de PC y del registro IF/EX(esto lo haremos sacando el clk)
<!--ID: 1682692834925-->


### Como solucionamos cada riesgo
*Estructual*
*Dato*
*Control*

### Riesgos estructurales
*Condiciones para evitar riesgos estructurales:*
- Memorias separadas y recursos duplicados
- Todas las instruccion pasan por todas las etapas
- Solo se utiliza una unidad funcional por etapa
- Todas las instrucciones usan la misma unidad funcional en la misma etapa
### Riesgo de Datos
Una instruccion depende del resultado de una instruccion previa que aun esta dentro del pipeline.
- Para solucionar estos riesgos con solo 2 burbuja bastaria
- No necesitamos burbujas, cuando necesitemos traemos en dato en medio de la ejecucion,
#### Adelantamiento
![[Pasted image 20230419083611.png]]
A esto le llamaremos *adelantamiento*
Para esto necesitamos agregar muchas interconexiones nuevas y mas multiplexores
- No soluciona el caso de un load es seguido inmediatamente por una instruccion que usa el registro destino.
	- Para esto tendremos que agregar una burbuja
![[Pasted image 20230419084835.png]]
#### Reordenamiento con dependencias
Cambiamos el orden de las instrucciones en el codigo. Tambien hay que tener en cuenta que no todas las dependencias constituyen un riesgo de datos.
#### Pipeline con adelantamiento
![[Pasted image 20230419093424.png]]
- La unidad de adelantamiento necesita detectar el riesgo
	- Compara si alguno dde los registro que se leen en la etapa 2 es igual al registro que se escribe de la instruccion en la etapa 3.
	- Y si es que las instruccion en la etapa 3 o 4 escriben en un registro
	- Y solo si el registro destino es distinto de cero
	- Esto soluciona el problema del store

### Riesgo de control
Los saltos son los que determinan el flujo de control de un programa. La busquema de la sigiuente instruccion depende del resultado de un salto y el salto se resuelve completamente en la etapa 4. Esto implica que habria que agregar 3 burbujas.
La resolucion de un salto implica dos tareas:
1. Determinar si *realmente se efectuara o no*
	- Para determinar si realmente se efectuara antes, sacaremos la tarea de comparar a la ALU y ponemos un comparador en la etapa ID. Esto nos permite resolver todo el salto en la etapa ID.
		- La condicion a evaluar debe ser simple?
		- Genera nuevo riesgos de datos, que necesitan nuevos adelantamiento
		- Aun asi necesitamos 1 burbuja
2. Determinar cual es la *direccion destino del salto*.
*Solucion de 1:*
Para determinar si realmente se efectuara antes, sacaremos la tarea de comparar a la ALU y ponemos un comparador en la etapa ID. Esto nos permite resolver todo el salto en la etapa ID.
- La condicion a evaluar debe ser simple?
- Genera nuevo riesgos de datos, que necesitan nuevos adelantamiento
- Aun asi necesitamos 1 burbuja
El problema de la alternativa anterior, es que en pipeline mas largos, es muy dificil adelantar toda la resolucion del salto.Idealmente deberiamos intentar hacer toda la resolucion del salto en la etapa IF, lo cual es muy ilogico
- Entonces *usamos predccion de salto*
	- Basicamente esto consta en recordar donde tengo salto y luego verificar si estamos por hacer esta instrucciones
#### Pipeline completo:
![[Pasted image 20230425134335.png]]





