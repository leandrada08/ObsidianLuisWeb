
## Mutiprocesamiento
Ventajas:
- *Aumentan* la performance
- *Disminuye* el consumo de energia
- *Aumentan* la disponibilidad
Desventaja:
- *Disminuyen* la eficiencia
- *Generan problemas* de sincronizacion y de coherencia de datos
- *Generan dificultad* para los programadores

### Implicacion
- Cuando se *divide* la tarea, se busca *balancear la carga*
	- Para esto se necesita *sincronizar* a los trabajadores
		- Esto es aumiendo que se peude dividir en partes iguales
- Tambien hay que ver de que manera se divide el trabajo(*echeduling*)
- Problablemente tambien tengamos problemas de comunicacion entre los trabajadores(*Overhead por Comunicacion*)
- Por otro aldo mientras mas aumentan los trabajadores, esto se agraba

### Consideraciones sobre performance
Un sistema es *escalable* si al incrementar los recursos (Hw), se logra una mejora proporcional en la performance:$$A(p)=\frac{Tiempo1Procesador}{TiempoPProcesadores}$$
Primer incoveniente a la escalabilidad: *La sincronizacion*
Recordando la Ley de Amdahl: La mejora total de un sistema esta limitado por la parte no modificada. Esto limita muchisimo nuestra aceleracion,  ya que casi siempre que procesamos gran aprte del codigo es secuencial, por lo que no se puede ejecutar en paralelo
![[Pasted image 20230612083024.png|500]]
El mayor desafío del procesamiento paralelo es decidir cómo es mejor partir un problema en pedazos que puedan ser procesados por separado.
- La fraccion serial impone una fuerte limitacion al paralelismo
- Con muchos procesadores empieza a disminuir la aceleracion, debido a problemas de comunicacion y/o coordinacion
- Asume que el problema a resolver es de tamaño fijo
	- La carga de trabajo de cada procesador va disminuyendo
- Esto se conoce como *Escalabilidad fuerte*

#### Alternativas para mejorar escalabilidad
*Adaptar la cantidad de trabajo al paralelismo disponible*.
- Cuanto mayor sea el conjunto de datos, ams proximo sera la aceleracion al ideal.
	- La carga de trabajo de cada procesador se mantiene constante.
- Esto se conoce como *Escalabilidad debil*
![[Pasted image 20230612083451.png|500]]


## Taxonomia de Flynn
*SISD:* Single instruction, single data.
**SIMD:** Single instruction, multiple data.
*MISD:* Multiple instruction, single data.
**MIMD:** Multiple instruction, multiple data.

### SIMD
Operan elemento a elemento sobre un vector de datos.
- Bastante simples. Sincronizados.
![[Pasted image 20230612084535.png|500]]
- Para esto agregamos una instruccion en el ISA
	- La longitud de los registros es fija, *definida por el ISA*
	- Es un problema para los ISA de formato de longitud fija
		- Por esto es muy popular en la arquitectura X86
		- En la arquitectura ARM, existe la extension NEON
		- En RISC-V, hay una extension no estandar (P)
- Explotan el **paralelismo a nivel datos(DLP)**

Dentro de esat categroria podrian entrar tambien arquitectura vectoriales y los procesadores graficos
- Distinta esencia, pero tambien explotan el DLP
- El ISA de RISC-V provee una extension especial (V) para operaciones vectoriales

### MIMD
La mayoria del tiempo el procesador esta parado sin hacer nada. Entonces surgio la idea de hilos de ejucucion(*Theads*).
#### Threads
Son hilos de ejcucion, son funciones **independientes** de un mismo programa.
- Comparten los recursos del programa
- Cada Threads tiene su propio PC y su propio estado
- Es mucho mas rapido cambiar de thread que de proceso

#### Multithreading
La idea es que un unico procesador maneje varios Threads. Para lograr esto, se ejecuta un thread y este se ve detenido por alguna parada, se cambia a otro thread, esto se conoce como *coarse-grained multithreading.(coarse MT)*
- La clave es que el cambio de thread sea ams rapido que la resolucion de parada

**Multithreading simultaneo(SMT)** aprovecha las caracteristicas de un procesador superescalar con emision dinamica multiples de instrucciones, y busca emitir siempre instrucciones de diferentes threads para llenar las unidades funcionales disponibles.
![[Pasted image 20230612090653.png|500]]
- El SMT explota el paralelismo a nivel threads.
- Caso ideal: Cuando tenemos un theread principal mas un thread pequeño que ejecuta en paralelo, y cuando haya mucha comunicacion entre ambos.
##### Desventaja de SMT
- Limitacion 1: *software*
	- Los programas no usan tantos threads, entonces la ejecucion de programas de un unico thread peuede empeorar
	- Conclusion: *Varios nucleos, pocos threads por nucleo*
- Limitacion 2: *Seguridad*
	- El soporte para SMT representa una seria vulnerabilidad de seguridad

## Otra clasificacion de multiprocesamiento
 Se clasifican segun si su acceso a memoria es compartida o no.
 En un *acceso compartido a memoria*, todos los procesadores comparten un unico espacio de direcciones fisicas.
 - Todos los datos de memoria estan disponibles para todos los procesadores en todo momento
 - Mucho mas simple de programar
 - Se necesitan operaciones atomicas en memoria para sincronizacion.
En un *acceso no compartido a memoria*,  los procesdaores tienen cada uno un espacio de direccionamiento privado.
- Es necesario un mecanismo explicito para compartir datos.
### Acceso compartido a memoria
![[Pasted image 20230612094043.png|500]]
Se los denomina SMP(shared memory multiprocessors)
*Acceso uniforme a memoria(UMA):* Misma latencia para todos
- Comparten datos a traves del LLC(actualmente, L3)
*Acceso no uniforme a memoria(NUMA):* Los procesadores poseen memoria local, y por lo tanto la latencia de memoria no es siempre la misma.

- La popularidad de SMP tipo UMA es porque son mas faciles de programar
- Sin embargo, en algunos casos un sistema NUMA peude proveer latencias menores.
	- Esto hizoq ue se hagan mas populares las conexiones tipo NUMA


#### Problemas de coherencia de caches
Como la memoria es compartida, es necesario que se provea un mecanismo para *mantener la coherencia da datos*
- Mantener la ilusion de que los datso son almacenados en una unica gran memoria
- Estos mecanismos se denominan *protocolo de coherencia de cache*
	- Se basa en llevar un registro de como y cuando es compartido cada bloque de cache
	- Los protocolos de coherencia mas populares son de tipo *snooping*
		- Todos los cache son accesibles desde un unico bus compartido
		- Las transacciones en ese bus se realizan de a una por vez
		- Todos los caches monitorean permanentemente ese bus compartido para saber si tienen un copia del bloque que se esta solicitando

##### Protocolo simple de coherencia
Cuando un procesdaor A escribe en una direccion de memoria X, se marcan como invalidad todas las copias de X que puedan existir en los caches de los demas procesadores(*write invalidate* )
- Esto implica que una escritura hace que un dato sea exclusivo de un procesador
- Genera nuevos fallos, porque puede que el procesador B haya leido antes el dato X, y al intentar leerlo nuevamente no lo encuentra.
- Si un procesador B quiere leer una dirección de memoria X que es exclusiva de otro procesador A, se fuerza a que A haga un write back a memoria de X y luego se produce la lectura.
	- En realidad, cuando A hace el write back , al mismo tiempo le pasa el valor de X a B, porque el bus es compartido. 
- Estos protocolos son usualmente implementados como una MEF. Estrictamente, en el limite entre memoria privada y memoria compartida
Esta version ams simple, un bloque puede esta en uno de tres estados:
- Invalido(I): el cache no posee este bloque 
- Modificado(M): el bloque es exclusivo, solo este cache tiene la version valida 
- Compartido: igual que en memoria, puede estar en otros procesadores
En procesadores mas actuales tiene mas estados
![[Pasted image 20230614082748.png]]
- Transiciones en negro son generadas por el procesador (Pr).
- Transiciones azules son generadas por el Bus (otros procesadores).
- Las transiciones al estado M son por escrituras (acierto o fallo).
	- Invalidan el bloque en los demás cachés.
- Cuando un caché tiene un bloque en estado M que es solicitado en el bus, hace un write back ( flush)
	- Y pasa el bloque al estado S.
- BusRd vs BusRdX : el primero es por fallos de lectura, el segundo por fallos de escritura (invalida el bloque en los demás caches).

###### Problema de falsa coherencia
- Adicionalmente, puede haber otro problema en bloques de múltiples palabras.
- Los movimientos en caché siempre son a nivel de bloques.
- Puede ocurrir que dos variables compartidas no relacionadas X e Y estén ubicadas en el mismo bloque.
	- El procesador A escribe siempre X y el procesador B escribe siempre Y.
	- Ambos están permanentemente invalidando todo el bloque.
	- Generan fallos innecesarios y tráfico por el bus compartido.
- Se puede evitar teniendo mucho cuidado al ubicar las variables en memoria.


### Acceso no compartido a memoria
Para computadoras que no comparten memoria
![[Pasted image 20230614084236.png]]
- Las redes de interconexión comunican nodos completos procesador memoria a través del sistema de I/O.
- Se comunican mediante un mecanismo explícito de paso de mensajes (MPI, Message Passing Interface
- Las aplicaciones empaquetan los datos que quieren transmitir en forma de mensajes.
	- La comunicación es explícita, mediante rutinas para enviar send (Pi, Dk ) y recibir wait (Pj,Dk)
	- Hay librerías que implementan estas rutinas para muchos lenguajes de programación, e iniciativas abiertas como OpenMPI.
#### Cluster de paso de mensaje
- Las redes de comunicación pueden ser de muy alta performance y muy alto costo.
	- Usadas en supercomputadoras.
- O ser redes de bajo costo (Ethernet).
	- Conectan computadoras completas en configuraciones denominadas clusters
	- Muy populares para ejecutar aplicaciones que aprovechan paralelismo a nivel aplicación (ALP)
		- Búsqueda web, servidor de mail, servidor de archivos, bases de datos.
	- Poseen una alta disponibilidad, a diferencia de SMP.
	- Son fáciles de escalar.
- Proveen Software as a Service(SaaS)
	- Tambien conocido como la popular "nube"

## Como podemos explotar el paralelismo
- Reescribiendo programas con algoritmos/lenguajes que usen paralelismo.
	- Concentrarse en la parte más lenta ( Amdahl
	- Concentrarse en cómo particionar los datos, y cómo hacer la sincronización.
- Distintos enfoques
	- Paralelismo a nivel datos.
	- Paralelismo a nivel thread
	- Paralelismo a nivel aplicación.
- No escalar paralelismo sin escalar datos.