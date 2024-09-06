- Todas las dependencias nos podrian generar problemas
	- En nuestro disenio solo nos afecta la read after write


## Superpipelining
Los procesadores avanzados tienen mas etapas de las que nosotros vimos. Hacen esto para reducir el tiempo de las etapas mas largas y buscar que todas tengan el mismo tiempo. Como haciamos en el Tema 3.
Los procesadores actuales tienen distintas etapas dependiento el tipo de procesador. Los pequenios tienen entre 1 y 3 etapas, en medianos entre 5 y 8 etapas y en los de alta performance suelen tener entre 10 y 20 etapas.
### Inconvenientes
- Se debe poder dividir la etapas
	- No puedo hacer media busqueda en memoria.
- Los retardos de los buffer intermedios pasan a ser significativos.
- Aumenta el consumo de energia
- Los riesgos se incrementan
	- Aumentan las penalidades.



## Prediccion de saltos 
### Estatica
Mas simple. Nunca salta o siempre salta. Esto es mejor que no hacer nada como haciamos.
Mejor pediccion seria para atras casi siempre salta y para adelante son casi siempre no tomados.
- Practicamente no se usan estas
### Dinamica
Se basa en tener una historia de los ultimos N saltos. El historial guarda la *direccion origen del salto* y *si se tomo o no(BTH)*. Se mantiene tambien una especie de cache de las *direcciones destino de los saltos(BTB)*.
Procedimiento:
1. Revisa la BHT para saber si es un salto
2. Si lo es, se espera la misma salida de la ultima vez, y se prepara la direccion destino(BTB o PC+4)
3. Si no se acierta, se vacia el pipeline y se actualiza la prediccion.
- Toda la prediccion se puede hacer en el Fetch.
*Cuantos bits se usan para mantener la historia:*
- 1bit: Tasa de acierto no tan alta.
- 2bits: Se cambia la prediccion cunando se equivoca 2 veces consecutivas.
- Hoy en dia se toman multiple cantidad de bits para la historia
	- Alguno disenios usan redes neuronales.






## Paralelismo a nivel de la instruccion 
Mejoraremos mas la performance. Para eso haremos *multiples pipelines en paraleo* (*superescalar.*)
Un procesador en pipeline con CPI=1 tiene 2 caracteristicas implicitas:
- En cada ciclo se emite una nueva instruccion
- En cada ciclo se finaliza una instruccion.
Un procesador superescalar busca emitir y finalizar mas de una instruccion en cada ciclo.
Cuando el CPI<1 , definimos IPC(1/CPI)
Para lograr esta idea, nos basaremos en tres ideas fundamentales.
1. Emision dinamica de multiples instrucciones
2. Ejecucion fuera de orden
3. Ejecucion especulativa.



### Emision multiple de instrucciones(ILP)
Varios pipeline en paralelo no tienen varias memorias de instrucciones. Por esto se usa la *emision estatica y dinamica*
#### Emision estatica(Very long instruction word)
El compilador agrupa las instrucciones que pueden ser emitidas juntas en el mismo ciclo. El compilador tambien se encarga de detectar y evitar los riesgos.
![[Pasted image 20230426081622.png]]
- *El IPC maximo es igual a la cantidad de instrucciones que se ejecutan en paralelo*
##### Incovenientes
- IPC real lejos del maximo.
- Limitacion fuerte de las dependencias
- El adelantamiento es mucho mas complejo
- Un ciclo de demora por culpa de LW, ahora perdemos dos intrucciones.
##### Camino de datos con emision doble
Los pipelines no suelen ser identicos. Ejemplo: Uno puede ser de tipo R o branch y la otra puede ser Load/Store. En este caso el compilar deberia acomodar los paquetes de esta manera.
- De la etapa If se leen dos instrucciones
- Se deben duplicar los puertos de lectura en el banco de registros para la etapa ID
- Debemos agregar una ALU.
- La memoria de datos solo se conecta a esta nueva ALU
- Se debe duplicar el puerto de escritura en el banco de registros apra la etapa WB.
![[Pasted image 20230426082804.png|500]]

### Emision dinamica de multiples instrucciones
El procesador analiza la secuencia, no el compilador, y decide cuales instrucciones emitir en cada ciclo.
- Basado en un diagrama de precedencias.
- Si emite n instrucciones por ciclo, se denomina n-wide.
#### Ejecucion fuera de orden(OoO) (Solo de multiple y dinamica)
*Las instrucciones se ejecutan en un orden distinto del que esta en el codigo. Pero sigue terminando en orden*
$$EmisionOrden->EjecucionFueraOrden->TerminacionOrden$$
- Implica que hacen falta buffers antes y despues de la ejecucion
![[Pasted image 20230426093815.png|500]]
- Se debe preserva el flujo de datos para asegurar la exactitud de un programa.
**Front-End:**
- *Etapas de IF y ID(fetch y decode).*
- *Las estaciones de reserva:* mantienen las instrucciones en espera hasta que puedan ser ejecutadas.
	- Hasta que todos sus operandos esten disponibles
	- Tambien se los denomina etapas de *Scheduler*.
**Back-End:**
- Hay multiples unidades funcionales diferentes en paralelo en la etapa de ejecucion
	- Se requiere caminos de adelantamiento entre todos ellos.
- La unidad de terminacion se encarga de reordenar las instrucciones, para asegurar que los registros se escriban en el orden deseado.
	- Se encarga que los resultados calculados se vuelvan permanentes
	- Tienen un buffer de reordenamiento(ROB)
		- Cuando mayor sea el ROB, mas instrucciones pueden ser mantenidas en ejecucion al mismo tiempo
			- Cuantas instrucciones adelante se pueden ir buscando instrucciones independientes para ejecutar.
#### Renombramiento de registros. (Esto es solo de la dinamica)SI
En las estaciones de reserva se puede cambiar el "nombre" de los registros,  de modo de elimnar dependencias.
- Los procesadores modernos tienen muchos mas registros fisicos que los que se exponen en el ISA.
- Cuando se emite una instruccion, se revisa si el operando esta disponible en el banco de registros o en el ROB.
	- Si esta libre, se lo copia a la unidad de reserva y puede ser sobrescrito
- Despues vuelven a su nombre original en la unidad de terminacion
- Algoritmo diseniado por *Tomasulo* en 1967 para IBM.
*ROB:* Bufer de reordenamiento,
### Estatica vs Dinamina
La dinamica con la ejecucion fuera de orden es mucho mas compleja que la estatico. Sin embargo, es la mas usada en procesadores media y alta performance, porque:
- Hay muchas paradas que no pueden ser predichas por el compilador, porque ocurren en tiempo de ejecucion.
- Es muy dificil predecir en tiempo de compilacion el resultado de los saltos para armar mejor los paquetes.
- Diferentes implementaciones de un mismo ISA pueden tener distintas latencias y distintos riegos.






## Tecnicas para mejorar el CPI
Estas tecnicas se usan comunmente en procesadores superescalares aunque pueden ser usados en procesadores simples.


### Desenrrolado de lazos 
**IDEA: Repetir el cuerpo del lazo para expoenr mas paralelismo**
Tecnica utilizada por el compilador apra mejorar la performance de un programa que incluya lazos. Puede ser usada en los procesadores simples como en los superescalares.
![[Pasted image 20230426085112.png|400]]
![[Pasted image 20230426085900.png|400]]
#### Ventaja
Sepuede mejorar la performance "casi gratis". Es una optimizacion muy utilizada por los compiladores
#### Desventaja
- Se necesitan mas registros
- Ocupa mas memoria
- La cantidad de veces a derenrollar depende de la cantidad de iteraciones del lazo.
<!--ID: 1683126643513-->




### Ejecucion Especulativa 
Consiste en "adivinar" que va a pasar con una instuccion, para comenzar con su ejecucion lo antes posible
- Si acertamos, ganamos tiempo
- Si no acertamos, igual hubiesemos perdido tiempo esperando
Ejemplo tipico: en los saltos. No espera la resolucion del salto, sino ejecutar ambas alternativas y cuando se resuelva el salto, terminamos la correcta.
- Tambien suele especularse en los LOAD.
- El compilador tambien ayuda a la especulacion
- Tambien se anticipa la ejecucion de algunas instrucciones "por las dudas"
*La ejecucion especulativa resulto ser un serio problema se seguridad*
#### Limitaciones de la emision multiple de instrucciones
La mayoria de procesadores modernos de performance media y alta son superescalares. Funcionan muy bien pero no tanto como nos gustaria.
- Es fuertemente limitado por dependencias.
- Tanta complejidad agrega costos(area) y consume energia.
<!--ID: 1683126643517-->




## Manejo de interrupciones/excepciones
*Preservar el comportamiento de las excepciones es la segunda propiedad esencial para asegurar la exactitud de un programa.*
Cuando llega una interrupcion:
1. Guardo PC de la instruccion interrumpida es un registro adicional
2. Se debe guarda en otro registro adicional la causa de la interrupcion
3. Se escribe el PC con la direccion donde se ubica el manejador de interrupciones/excepciones
4. Esto agrega al camino de datos un par de registros y una entrada mas al multiplexor de PCSrc
Supongamos que una instruccion add esta en la etapa EX generea una excepcion
- Se debe evitar que se escriba en el banco de registros
- Se termina de completar las instrucciones que fueron emitidas antes y se quita del pipeline las que fueron emitidas despues
- Cuando se retorna del manejador de excepciones, la instruccion problematica vuelve a ser buscada en IF y ejecutada.