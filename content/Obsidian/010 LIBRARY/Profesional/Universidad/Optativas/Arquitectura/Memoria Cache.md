## Repaso
### ![[Introduccion a la arquitectura de computadoras#Principio de localidad]]
### ![[Introduccion a la arquitectura de computadoras#Jerarquias de memorias]]
Normalmente las memorias mas rapida (SRAM) son muy caras y por lo tanto pequeña y las mas baratas, son lentas y grandes
*Objetivo:* Brindar al usuario el mayor almacenamiento posible, lo mas rapido posible, con el menor costo posible. Como se logra esto:
- Mayoria de accesos sea a las memorias mas rapidas
- Todo su espacio de direccionamiento disponible en la memoria mas barata.

## Performance memoria vs CPU
- Procesdores duplican su performance cada 2 años
- DRAM mejoraba su performance un 40% cada 10 %
Entonces los procesadores cada vez la ven mas lento a las memorias.
![[Pasted image 20230510083624.png]]
Combinado esto con el paralelismo agregado, hace que cada vez tenga mas burbuja nuestro procesador.


### Memory wall(pared de memoria)
![[Pasted image 20230510084340.png|500]]
Brecha entre la velocidad del procesdor y velocidad de la memoria.

### Impacto en la performance
$$CPI=CPIideal+ParadasPromedioPorInstruccion$$


## Memoria Cache: Concepto
Son los niveles mas superiores de la jerarquia de memoria, estas usualmente son SRAM, muy rapidas y costosas. Ahora consideraremos que nuestras memorias seran caches.
- La memoria cache no tiene valor por si mismas, solo es una etapa intermedia en una enorme brecha(jerarquia).
	- Ocupan un gran porcentaje del area de procesadores modernos.
	- Son responsables de un gran porcentaje del consumo de energia
### Como funciona la jerarquia?
1. Almacenar toda la informacion en la memoria grande y barata
2. Cuando necesite un dato, moverlo hasta las memorias mas rapidas
3. Al moverlo, no movamos solamente el dato solicitado, sino tambien sus vecinos.
- Independiente de la cantidad de niveles que tenga la jerarquia, los movimientos son siempre entre dos niveles adyacentes

## Terminologia Memoria Cache
*Nivel superior:* El mas cercano al procesador
*Bloque:* La minima cantidad de informacion que se transfiere entre dos niveles.
- Cuando un dato solicitado *esta* en algun bloque del nivel superior, se dice que hubo un *acierto*
	- *Tasa de acierto(hit rate):* Fraccion de accesos a la memoria que se encuentran en el nivel superior #Consultar (el nivel mas bajo(mas cerca a la memoria mas grande), tiene un acierto del 100%)
	- *Tiempo de acierto(hit time):* Tiempo total en que el nivel superior es capaz de entregar un dato. Es la suma del tiempo de acceso de este nivel mas el tiempo para determinar si es un aceirto o no(pregunta) #Consultar 
- Cuando un dato *no esta* en el nivel superior, y hay que buscarlo en el nivel inferior, se dice que hubo *fallo(miss)*.
	- *Tasa de fallos:* Complemento de la tasa de acierto. Veces que tuve fallos sobre cantidad de veces que le pedi datos.
	- *Penalidad por fallor(Miss penality):* Tiempo total para mover un bloque del nivel inferior al superior
- Toda la jerarquia de memoria se basa en la idea que para un dado nivel, el tiempo de acierto sea mucho menor que la penalidad por fallo.
	- **HIT Time<<Miss penality**

## Diseño de una jerarquia de memorias: Idea Basica
La *traza de memoria* es una secuencia de direcciones de memoria que representa el comportamiento de acceso a la memoria de un programa o aplicación. Se utiliza para analizar el comportamiento de acceso a la memoria y diseñar una jerarquía de memorias caché adecuada para optimizar el rendimiento.
En algunos casos, los benchmarks pueden utilizar trazas de memoria para simular el comportamiento de acceso a la memoria de una aplicación o programa y evaluar el rendimiento de un sistema en un escenario realista.
- El objetivo es optimizar la jerarquia para minimizar el tiempode ejecucion del benchmark.
### Cuatro cuestiones basicas de diseños
- Donde ubico un bloque en el cache?
- Como encuentro si un bloque esta en cache?
- Cual bloque reemplazo en caso de tener un fallo?
- Que se hace en caso de escritura?

## Diseños de caches
### Etiqueta y bit de validez
Para diferenciar cual de todas las direcciones de memoria esta guardada en el cache, necesitamos almacenar adicionalmente el resto de la direccion, a modo de identificador unico. Esto se denomina *etiqueta(tag)*
Suponiendo direccion de memoria de 32bits, y un cache de mapeo directo de $2^N$ bytes:
- Los N bits menos significativos se usan para el indice
- Los 32-N bits mas significativos se usan para la etiqueta.
Para indicar si en el bloque de cache tiene datos validos(o si tiene datos), existe un bit de validez de ese bloque.
- Ambos son considerados como parte del *estado* de un cache.
![[Pasted image 20230514193848.png]]
### Cache de Mapeo directo
- Es la forma mas simple de organizacion
- Cada direccion de memoria se mapea directamente a un unico bloque del cache.
	- Se utiliza los bits menos significativos de la direccion, a modo de indice
![[Pasted image 20230514192136.png]]
Basicamente, cuando copiemos un bloque, se copiaran en el cache, respetando el lugar de los 3 bit menos significativos.
- Pero un bloque de cache puede ser ocupado por muchas direcciones de memoria.
	- Ocupara el lugar dependiendo el principio de localidad, basicamente la que necesitemos ahora.
	- Para poder ubicar cual de todos bloques esta en cache, se copia adicionalmente el resto de la direccion, a modo de indentificador unico.
#### Ejemplo 1
Al buscar 1 dato:
1. Verificamos el indice de validez
2. Si esta inactivo
	1. Copio el dato de memoria en cache
	2. Coloco el indice de validez como activo
	3. Copio la etiqueta
3. Si esta activo
	1. Verificamos la etiqueta
	2. Si son igual
		1. Es un acierto
	3. Si son distintas
		1. Es un fallo
		2. Descartamos lo almacenado en este lugar de cache
		3. Copio el dato de memoria en cache
		4. Copio la etiqueta nueva
		5. Mantengo el bit de validez como valido
#### Ejemplo 2
![[Pasted image 20230514201128.png|300]]
![[Pasted image 20230514201139.png|300]]
- Lo importante de este ejemplo, es darse cuenta del ofset, lo sacamos ya que al mover los 4 bytes juntos, no importa cual de los 4 elegimos, por eso no hace falta analizar


### Bloques de cache mas grandes
- Es conveniente que los bloques tengan mas palabra para aprovechar la localidad espacial.
	- Mientras mas grande es el bloque, mas se reduce la tasa de fallo
- Entonces, para saber que palabra estamos leyendo, necesitamos un offset de la palabra dentro del bloque
#### Offset total
$$Offset= OffsetBloque+OffsetByte$$
- *OffsetBloque:* Offset para determinar la palabra en el bloque
- *OffsetByte:* Offset para determinar el bit en la palabra
Ejemplo: Un bloque de 16 bytes necesitamos 4 bits de offset, 2 de palabras y 2 de bytes(suponiendo palabras de 4 bytes).
- En la direccion del bits: Lo menos significativo son los de bytes, luego van los de bloque, luego va el indice y al final la etiqueta
![[Pasted image 20230515083307.png|600]]
- Ahora hay que recalcular el indice ya que tenemos el offset, ahora nuestro indice no seran los menos significativo, sino los menos significativos despues del offset.
	- Para calcular el indice(que es movernos a la izquierza), tenemos que dividir en $2^{offset}$
- El tamaño total de un cache esta dado por $2^{indice+offset}$, si el tamaño total se mantiene constante, indice +offset se mantiene constante.
- Si aumento el tamaño pero mantengo fijo el tamaño total, disminuye la cantidad de bloques
	- Hay menos localidad temporal y aumenta la tasa de fallos.
	- Por lo que hay un *compromiso entre el tamaño del bloque y la tasa de fallos*.
	- Mientras mas grande es el bloque, mas aumenta la penalidad por fallos.
	- Tener menos fallos con una alta penalidad puede ser contraproducente.
#### Incoveniente Mapeo Directo: Competencias
- Se cargan continuamente datos en el cache, para ser descartados antes de ser usados nuevamente, ya que se cargan en el mismo bloque. *Efecto Ping Pong*
	- Esto genera ocasiona *Fallos por conflicto*(fallo por no encontrar algo que antes estaba en cache)
	- 2 posibles soluciones
		- Aumentar el tamaño del cache(cambia funcion de mapeo)
		- Cambiar la organizacion del cache: *Asociatividad*.

### Cache Asociativo puro
No tiene indice. Un bloque de memoria puede ubicarse en cualquier bloque del cache.
- Se compara las etiquetas de todos los bloques al mismo tiempo para ver si hay un acierto.
	- Requiere un comparador por cada bloque de cache. Mas costoso
$$Direccion Memoria=Etiqueta+Offset$$
Por definicion no posee fallos por conflicto
- Tiempo de acierto mayor que en Mapeo Directo.
	- Porque en Mapeo Directo puedo acceder al bloque mientras evalua si es un acierto o no.
![[Pasted image 20230515093936.png|500]]

### Cache Asociativo por conjuntos de N vias
Combina las ventajas de asociativo puro y de mapeo directo
Si tiene indice, pero este indice selecciona un conjunto de N bloques. Dentro de este conjunto, los bloques son asociativos.
- Dado un valor de indice, el dato de memoria puede ir a cualquier bloque de ese conjunto de bloques.
*Es como tener N caches de mapeo directo en paralelo.*
- Mas costoso que mapeo directo, pero menos que asociativo puro
- Menor tasa de fallos que mapeo directo, pero mas que asociativo puro..
![[Pasted image 20230515093947.png|400]]
![[Pasted image 20230515093954.png|300]]
![[Pasted image 20230515094900.png]]
*Consideraciones sobre asociatividad:*
- Aumentar la asociatividad disminuye la tasa de fallos
	- Pero con rendimiento decrecientes
- Aumentar la asociatividad aumenta el manaño y el costo del cache
- Aumentar la asociatividad aumenta el tiempo de acierto


## Remplazo y Escritura
### Politicas de remplazo
- Politica mas simple: Reemplazar al azar
- Politica ideal: Reemplazar el que no vaya a usar proximamente
- Politica alternativa: Reemplazar el menos recientemente usado(LRU, Least Recently Used)
El LRU es el mas usado en asociativo por conjuntos de 2 o 4 vias. La Random genera una tasa de fallos 1,1 veces mayor que LRU, cuando hay alta asociatividad, por eso se lo suele usar.
### Politicas de Escritura
Dos alternativas:
- Write-Through
- Write-Back

#### Write-Through
Se propone escribir en cache y en memoria en simultaneo.
- Para evitar problemas con la velocidad de la memoria principal, se agregar un *buffer de escritura* entre el cache y memoria principal
	- Este buffer vuelca el contenido a memoria cuando puede
	- Funciona bien si la frecuencia de escrituras no es alta
		- $fmax=\frac{1}{TcicloDRAM}$
#### Write-Back
Se propone escribir solo en el cache, y marcar el bloque como modificado y copiarlo unicamente cuando este por ser remplazado
- Necesitaun bit de estado adicional por cada bloque
Ventajas:
- Reduce mucho el ancho de banda requerido a memoria
- Permite unifica varias escrituras en un unico acceso a memoria
Desventaja:
- Aumenta la penalidad por fallo, ya que en caso de fallo se deben hacer varias tareas.
#### Politicas de fallo de escrituras
*Que ocurre si al intentar escribir un dato en el cache, el bloque no esta?*
- Si la politica de escritura es Write-Back, la respuesta suele ser afismativa.
- Si la politica de escritura es Write-Through, la respues suele ser negativa.


## Las 3C: Modelo para evaluar los fallos
Clasifica los fallos en 3:
- *Inevitable:* Ocurre en el primer acceso a un dato o instruccion
	- No confundir con un cache vacio
	- No depende de la organizacion, sino del programa a ejecutar
	- Disminuyen al incrementar el tamaño del bloque
- *Conflicto:* Cuando multiples direcciones de memoria se mapena al mismo bloque de cache
- *Capacidad:* Cuando el cache no puede contener todos los datos necesarios para el programa.
	- Solucion: Incrementar el tamaño del cache
![[Pasted image 20230517094410.png|500]]
### Consideraciones sobre las 3C
- Es un modelo empirico, no teorico.
	- No explican un fallo en particular, sino un comportamiento general
	- Intentan explicar por que un dato no esta en el cache:
		- Porque nunca estuvo
		- Porque fue reemplazado por conflicto
		- Porque fue remplazado por falta de lugar
![[Pasted image 20230517094750.png]]

## Impacto de caches en performance
Los caches reemplazan a las memorias ideales de los diseños vistos en temas previos.
Modifican el CPI introduciendo nuevas paradas
$$CPI=CPIideal+(\frac{MemAcc}{Inst})*MissRate*MissPenality$$
Un acierto en el cache hacer que el pipeline trabaje normalmente, entonces, el tiempo de acierto de los caches es un camino critico para un pipeline.

## Nueva metrica: AMAT
Tiempo medio de acceso a memoria(AMAT)
$$AMAT=HitTime+MissRate*MissPenalty$$
- Compara jerarquias de memoria

### Reduccion del tiempo de acierto
- Es la más difícil de las optimizaciones.
- Reduciendo el tamaño del caché.
	- Principio de Diseño: más pequeño es más rápido.
	- Pero aumenta la tasa de fallos.
- Reduciendo la asociatividad.
	- También aumenta la tasa de fallos.

### Reduccion tasa de fallos
1.  Aumentar el tamaño del bloque, para aprovechar localidad espacial. Reduce el fallo inevitable.
	- Disminuye la localidad temporal
	- Tambien aumenta la penalidad por fallo
2. Aumentar la Asociatividad, para disminuir los fallos por conflicto
	- Aumenta el tiempo de acierto
	- Aumenta el costo
3. Aumentar el tamaño del cache, para disminuir los fallos por capacidad
	- Aumenta el tiempo de acierto
	- Mas costoso y consume mas energia.
4. *Prebusqueda por Hw(Hardware Prefetchers):* En caso de fallo buscar dos bloque en vez de uno y lo guardo en un buffer extra
	- Tambien van analizando la secuencia de accesos a memoria, e intentan predecir el siguiente.
5. *Prebusqueda por Sw(Software Prefetchers):* El ISA provee instrucciones especiales para buscar datos en memoria.
	- El compilador o el programador se encarga de analizar la traza de memoria e insertar estas instrucciones
	- Estas instrucciones tambien consumen tiempo
		- Tener tambien en cuenta la ejecucion especulativa.
6. Varias tecnicas de alto nivel *Optimizaciones del compilador*
	- Reordenar instrucciones o datos para mejorar localidad espacial.
	- Unificar vectores, para mejorar localidad espacial.
	- Intercambia el orden de lazos anidados
	- Fusionar lazos que iteran sobre las mismas variables, pero con operaciones intepediente.
	- Dividir datos frandes en bloques, para aprovechar localidad espacial

### Reduccion de penalidad por fallos
1. Mejorar la tecnologia de memoria principal
	- El ancho de banda de memoria principal aumenta aproximadamente 23%/año
	- La latencia de memoria principal aumenta un 4%/año
	- Los procesadores para muy alta performance inccorporan memoria HBM en remplazo de DDR.
		- Estas son memorias incorporadas en un chip y no unas que vienen para conectar en la placa
![[Pasted image 20230519092139.png]]
2. No esperar que se cargue el bloque completo
	- *Early restart:* se van cargando las palabras del bloque, y cuando llega la palabra solicitada se transfiere el control al procesador y se continua la carga en paralelo.
	- *Critical word first:* Se trae de memoria la palabra solicitada primero, y se devuelve el control al procesador, continuando con la carga del resto del bloque en paralelo.
3. Priorizar lecturas sobre escritura. Es un cache Write-Back ocurre un fallo y hay que remplazar un blque modificado
	- Ya que en las lecturas estamos esperando un dato para seguir.
	- Es mejor usar un buffer de escritura, copiar el bloque modificado alli y traer el nuevo bloque solicitado al cache
	- El procesador toma el control apenas recibe el nuevo bloque solicitado.
	- El buffer de escritura escribe el bloque modificado en memoria cuando pueda.
4. *Multiples niveles de cache:*
	- Si tenemos n niveles, tendremos las memorias L1,L2,...,Ln
	- $PenalidadPorFallos(Ln)=AMAT(Ln+1)$
	- El en ultimo nivel de cache, se prioriza tener una muy baja tasa de fallos.
		- Para evitar acceder a memoria principal
		- Por esto suele ser Write-Back
	- En el primer nivel se prioriza tener un tiempo de acierto minimo.
		- Porque influye directamente en la duracion de las etapas del pipeline.
5. *Caches no bloqueantes:*
	- El cache continua sirviendo accesos de otras instrucciones. *Acierto bajo fallo*
		- El fallo se sigue procesando en paralelo.
		- *La penalidad es solo el tiempo que efectivamente esta parado esperando datos*
		- Requiere que el cache tenga al menos dos puertos de acceso
		- Usando en caches de datos de procesadores cone ejecucion fuera de orden
		- Agregando mas puertos de accesos al cache, podemos solapar multiples fallos en simultaneo, y reducir aun mas la penalidad efectiva.
		- Permite ocultar notoriamente la alta latencia de la memoria principal