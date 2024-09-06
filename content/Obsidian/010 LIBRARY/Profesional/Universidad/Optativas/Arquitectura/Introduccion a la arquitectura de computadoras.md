

- Introduccion
	- Partes de computadoras
	- Arquitecturas de computadoras
	- Memorias
		- Jerarquias
- Lectura recomendada
	- Computer Orgnization and Design
### Vision general
Arquitectura de computadoras consiste fundamentalmente en disminuir las enormes latencia/ancho de banda de las partes que componen una computadora
#### Como haremos esto?
- Paralelismo a nivel intruccion
- Ejecucion fuera de orden
- Ejecucion especulativo
- Multiples niveles de caches
![[Pasted image 20230315082045.png|200]]
##### Modelo por capas
Permite manejar abstracciones
- Esto nos permite independizarnos en un aspecto y abstraernos de los demas para aprender mejorS
## Que es una computadoras
Existen 4 tipos de computadoras principales
- *PCs:* Proposito general. Software muy diverso
	- Sujetas a compromiso entre costo y performance
- *Servidores:* Pequenios o como edificos
	- Mayor capacidad, mayor performance, amyor confiabilidad
- *Supercomputadoras:*
	- Grandes calculos cientificos
	- Representan una fraccion pequenio del mercado
- *Embebidos:*
	- Sujetos a estrictos compromisos entre costo, performance y consumo de energia(Andan a bateria)
### Partes de una computadora
Todas las computadoras tienen la misma componentes
1. Procesador
2. Control
3. Memoria
4. Sistema de entrada
5. Sistema de salida
![[Pasted image 20230313090932.png|400]]
- Procesador
	- Control: Maneja y sincroniza al camino de datos
	- Camino de datos: Por donde se mueven los datos
- Memoria:  Almacena la informacio
	- Se comunica con la memoria(intercambio constante entre ambos)
	- Enta intercambia con el mundo exterior
		- Entradas y salidas: Para ingresar y sacar informacion
		- ojo que los datos entran a la memoria, no van al procesador
- Es un sistema complejo
	- Comunmente estan absado en el esquema Von Neuman
#### Procesador
- Ejecuta los programas
- Realiza el ciclo de introccion([[Sistemas con Microprocesadores]])
	- Fetch->Decode->Execution
- **Repasar micro(Tema 01)**

#### Memoria
Muchos temas de memoria
![[Pasted image 20230313092024.png|400]]
- Las ram estaticos son mas rapidas y mas caras
- Las ram dinamicas necesitan refresco y son mas baratos(son las que compramos)
##### Modos de acceso
- *Primaria:* Accede directamente el procesador(RAM)
- *Secundaria:* Se accede a travez de I/O

##### Principio de localidad 
*Un programa accede a una porcion relativamente pequenia del espacio de direcciones, en cualquier intervalo de tiempo*
- *Temporal:* Cuando un item es accedido, es probable que pronto sea accedido nuevamente 
- *Espacial:* Cuando un item es accedido, es probable que pronto sean accedidos items cercanos
<!--ID: 1679787695781-->



##### Jerarquias de memorias
Este principio es importante en el diseño de las computadoras y en la optimización del rendimiento de los programas. Por ejemplo, si un programa puede aprovechar la localidad temporal, se puede guardar una copia de los datos en una memoria caché cercana para evitar tener que acceder a la memoria principal, lo que puede ser más lento. De esta manera, se puede mejorar significativamente el rendimiento del programa.
Visto de otra manera, lo que haremos para aprovechar mejor los recursos, sera usar *jerarquias de memorias*, de mas chica a mas grande y de mas rapida a mas lenta. Lo beneficioso de la jerarquia de memorias es que es transparente al usuario y permite hacer una ilusion de tener una memoria grande y rapida
![[Pasted image 20230313093518.png|300]]
El CPU accede a la mas rapida, la cual accede a un lugar de memoria de una mas lenta y asi sucesivamente.

##### Memoria cache
Es una memoria rapida, ubicada entre el procesador y la memoria principal
La idea de cache no es en si del procesador, si no de tener un espacio de memoria chico rapido almacenado, donde esta lo que mas se usa, este se usa en paginas, computadoras, etc.
- Siempre son transparetnes al usuario
	- Manejado por hardware y por software

##### Ordenes de magnitud
La Frecuencia de un microprocesador actual comunmente es de 3 o 4 GHz, lo cual nos da un ciclo de 0.3 ns , la luz, en el vacio recorre apenas 9cm.
Cuadro de latencia:
![[Pasted image 20230313094619.png]]
- En el cuadro podemos ver que la diferencia entre el ciclo del reloj y una entrada a memoria ram es enorme
	- Si el ciclo de reloj fuera de 1s, un acceso a un ssd demoria entre 2 y 4 dias.
##### Convencion de prefijos
![[Pasted image 20230315081151.png|500]]
- Todo lo que es I/O con decimal
- Todo lo que es dentro del micro es binario

### Modelo jerarquico de las computadoras
![[Pasted image 20230315082705.png]]
- Arquitectura de computadores se encargar de la coordinacion de distintos niveles de abstraccion
	- Como una decision sobre una capa afecta a las superiores o las inferiores
	- Cual capa es mejor para intentar resolver un problema
- Nosotros veremos desde Assembly hasta micro arquitectura










## Conceptos
### Set de instrucciones
Un set de instrucciones de un microprocesador o microcontrolador es un conjunto de instrucciones que el procesador es capaz de ejecutar. Cada instrucción es una orden específica que el procesador puede entender y realizar, y se representa por medio de códigos binarios específicos.
El set de instrucciones define la funcionalidad del microprocesador y, por lo tanto, determina las operaciones que el procesador puede realizar y cómo se realizan. Incluye instrucciones para realizar operaciones aritméticas y lógicas, manipulación de datos, control de flujo de programa, comunicación con dispositivos de entrada y salida, entre otras.
Cada microprocesador o microcontrolador tiene su propio set de instrucciones, que puede ser más o menos completo y variar en la cantidad y complejidad de las instrucciones que ofrece. Los sets de instrucciones pueden evolucionar y actualizarse con nuevas versiones del procesador, y pueden ser compatibles con versiones anteriores o requerir modificaciones en el software que los utiliza.


### Sistema operativo
El sistema operativo (SO) es el software que se encarga de administrar los recursos de un ordenador y proporciona servicios a los programas que se ejecutan en él. El SO es responsable de gestionar la memoria, el procesamiento, el almacenamiento y los dispositivos de entrada/salida, entre otras cosas.
Basicamente gestiona los recursos, busca que esta gestion sea equitativa, segura, confiable, transparente y simple de usar para todas las aplicaciones
#### Multitarea
Cuando se ejecuta un programa, esto tarde miles de millones de ciclos del procesador, por la lentitud de la memoria, entonces en sistema operativo se encarga de usar el procesador para otras cosas durante ese tiempo, hace que estos programas se ejecuten *concurrentemente* para no desperdiciar recursos.
- Ojo, no es en paralelo, es concurrentemente
- Cada programa percibe que esta solo
	- Ninguno afecta a los demas(esto es por seguridad)
- Individualmente, los programas pueden demorar mas en terinar(latencia)
- Pero en promedio, muchos programas demoran menor(productividad)
Hacer esto implica manejar:
- Prioridades
- Interrupciones
- Modos de funcionamiento
##### Prioridades e Interrupciones
- Un progroma de usuario no puede
	- Modificar las prioridades
	- Acceder en forma directa a recursos compartidos
- El sistema operativo se encarga de esto
	- Las excepciones le permite al SO tomar acciones en respuestas a eventos o pedidos que ocurren cuando un programa de usuario esta ejecutandose
		- Comienza desde el manjador de interrupciones
		- O tambien lo hace solicitando servicio al SO
##### Modos de funcionamiento
Hay 2
- Usuario: Con restricciones
- Kernel/Supervisor: Sin restricciones
Las arquitecturas actuales tiene mas niveles de funcionamiento
- El micro que veremos en el curso tiene 3 niveles
El estado del procesador se mantiene en un registro especial


### Cache
Cuando hablamos de cache nos referimos a la memoria que se encuentran en el micro, la cual es una de muy alta velocidad pero de muy baja capacidad.
La caché se divide en bloques, cada uno de los cuales contiene una pequeña cantidad de datos de la memoria principal. Cada bloque en la caché se identifica por una dirección única en la memoria principal. El sistema de caché utiliza un algoritmo para determinar qué bloques de memoria se deben almacenar en la caché y cuándo deben ser reemplazados. Los algoritmos de caché suelen basarse en el principio de localidad, que establece que los programas tienden a acceder a los mismos datos de forma repetida y en la cercanía temporal o espacial.
#### Sistema cache
El sistema de memoria caché es una técnica de memoria en la que se utiliza una pequeña cantidad de memoria de alta velocidad y baja latencia para almacenar temporalmente los datos que se acceden con frecuencia. La caché es el componente físico en el que se almacenan los datos en la memoria caché.
Cuando un programa accede a los datos en la memoria, el sistema de caché primero verifica si los datos solicitados están disponibles en la caché. Si los datos se encuentran en la caché, se acceden directamente desde allí, lo que es mucho más rápido que acceder a los datos en la memoria principal. Si los datos no están en la caché, se acceden desde la memoria principal y, al mismo tiempo, se copian a la caché para futuros accesos.
La principal diferencia entre el sistema de memoria caché y la caché en sí es que el primero se refiere al conjunto completo de hardware y software utilizado para implementar la memoria caché, mientras que la caché se refiere específicamente al componente físico que almacena los datos en la memoria caché. La caché es una parte importante del sistema de memoria caché, pero también incluye otros componentes como controladores de caché, algoritmos de reemplazo de caché, y mecanismos de coherencia de caché en sistemas multiprocesador.
#### Usuario y cache
En general, el sistema de memoria caché está diseñado para ser transparente al programa de usuario, lo que significa que el programa no es consciente de la existencia de la caché y no tiene control directo sobre el proceso de almacenamiento y acceso a los datos en la caché. La caché funciona en segundo plano de manera automática y transparente para el programa de usuario.
Sin embargo, hay situaciones en las que la caché puede ser visible o controlada directamente por el programa de usuario. Por ejemplo, algunos lenguajes de programación y compiladores proporcionan instrucciones especiales que permiten al programador acceder directamente a la caché y controlar la forma en que se almacenan y acceden los datos en la caché.
Además, en algunos casos, el programa puede interactuar directamente con la caché a través de la manipulación de las líneas de caché. Esto puede ser útil en situaciones en las que el programa necesita acceder a datos específicos de manera rápida y frecuente, y puede aprovechar la caché para lograr un mejor rendimiento.
En general, el sistema de caché está diseñado para funcionar de manera transparente al programa de usuario, pero en algunos casos específicos, el programa puede interactuar directamente con la caché para obtener un mejor rendimiento.




### Compilador
El compilador es un programa que traduce el código fuente de un programa escrito en un lenguaje de programación de alto nivel a un código objeto, que es un código de bajo nivel específico del procesador. El compilador realiza varios procesos como análisis léxico, análisis sintáctico, optimización de código y generación de código objeto
### Ensamblador
El ensamblador es un programa que traduce el código ensamblador, que es un lenguaje de bajo nivel que representa el código objeto en una forma legible para los humanos, a código máquina, que es el código binario que el procesador entiende
### Enlanzador o linker
El enlazador o linker es un programa que se encarga de combinar varios módulos de código objeto generados por el compilador o el ensamblador, junto con las bibliotecas necesarias, para crear un programa ejecutable. El enlazador resuelve las referencias entre los módulos y las bibliotecas, y genera la tabla de símbolos.