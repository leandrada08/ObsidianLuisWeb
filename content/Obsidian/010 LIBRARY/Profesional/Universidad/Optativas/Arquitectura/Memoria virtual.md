## Necesidad de memoria virtual
- Mediante multiprogramacion varios programas se ejecutan concurrentemente
- El sistema operativo se encarga de administrar los recursos
- La memoria principal es un recurso mas
	- En un momento dado, varios programas pueden estar en memoria al mismo tiempo
	- Cada programa debe creer que es el unico
	- Los programas no deben interferis entre ellos
**Como hacemos esto?**
La solucion hace que los dintintos programas accedan a direccion virtuales. Luego el SO se encarga de ubicar a P1 y P2 en luegares fisicos de memoria y de proveer un mecanismo para traducir esas direcciones virtuales a direcciones fisicas.
## Paginacion
### Idea basica de Paginacion
- Se divide la memoria principal en partes iguales, de tamaño fijo, a las que se denomina *marcos*.
- Se divide el espacio de direcciones virtuales en partes iguales, del mismo tamaño fijo que los marcos, a las que se denomina *paginas*.
- La idea es que cada *pagina* de un programa sera ubicada en un *marco* de memoria principal.
- Para hacer la traduccion de direcciones virtuales a direcciones fisicas, el SO utiliza una tabla, que se denomina *tabla de paginas.*
	- Cada programa tendra su propia tabla de paginas.
	- Se le prohibe a una programa acceso a una tabla de paginas que no sea la propia
Cuando tenemos programas muy grande que no entran en la asignacion en memoria que se le hizo, se mantiene las paginas mas usadas y el resto en el nivel siguiente de la jerarquia. Las tablas de paginas deben indicar si una pagina esta ubicada o no en un marco. Bit de validez
- Si necesitamos datos de una pagina que no esta en ningun marco, se produce una excepcion por *fallo de pagina*
	- El SO se encarga de traer la pagina y actualizar las tablas.
### Sintesis
Cada programa posee un espacio de direcciones propio y contiguo e infinito.
- Pero este espacio de direcciones es virtual. Puede ser mayor que la memoria fisica instalada
- La suma del espacio requerido por varios programa puede ser mayor que la memoria fisica instalada
El SO le hace creer que es continua y realiza la traduccion de direcciones virtual a fisico mendiante tablas, ademas este garantiza:
- Transparencia
- Seguridad
- Eficiencia
La memoria virtual es un conjunto entre el SO y el procesador
- El hardware provee soporte a las funcinoes necesarias del SO. Lo hace a traves de una unidad e manejo de memoria.
- Se encarga de administrar dos niveles de la jerarquia de memoria: Memoria Principal y disco
## Diseño y caracteristicas
- Tamaño de las paginas: 4kiB
- Proceso de traduccion de direcciones virtuales a direcciones fisicas
- Politica de reemplazo de paginas
- Politica de escritura
### Mapeo de direcciones
- Se parte de un espacio de irecciones virtuales de $2^{N}$ byte, donde N es la cantidad de bits de las direcciones virtuales, en RISC-V soporta N=32 o 39 o 48
- Se busca traducir a un espacio de direcciones sificas de $2^{M}$ bytes. M es la cantidad de bits de las direcciones fisicas
--- 
#### Direcciones viturales
Se descomponen en dos campos
- Numero de pagina virtual(VPN)
- Offset de pagina *(no entiendo: sirve para direcciones los bytes dentro de la pagina)*
#### Direcciones fisicas
Se descomponen en dos campos
- Numero de marco(PPN)
- Offset de pagina
Ambos offset son igual ya que paginas y marcos son de igual tamaño
--- 
El mapeo consiste en traducir un VPN a un PPN
![[Pasted image 20230524091430.png|500]]
### Tabla de paginas
*VPN:* Indice con el cual se accede a la tabla de paginas
- Con el VPN se obtiene una *entrada de la tabla de pagina*
*PTE:* Entrada de tabla de pagina. Contiene 3 datos:
- Bit de validez: Indica si esta en memoria
- Bits de estado: Indican si la pagina fue modificada, ayudas para algoritmo de remplazo, etc.
- *PPN:* Numero de marco donde esta alojada la pagina
![[Pasted image 20230524110109.png|500]]
#### Mapeo de direccion con tabla de pagina
![[Pasted image 20230524110511.png|500]]

#### Observaciones tabla de paginas
- La tabla de paginas obviamente debe estar en memoria principal
- La direccion base de esta tabla viene dada por un registro del procesador *PTBR*
	- Este registro se preserva al igual que PC
- La entradas de la tabla de paginas pueden ser de cualquier cantidad de bits, pero normalmente se usan tamaños que sean potencias de 2(32 o 64) #Consultar : Cuando tenemos varios niveles se sigue manteniendo esto?
### Algoritmo de traduccion
1. Con la direccion virtual se obtiene esu numero de pagina virtual(VPN)
2. Con el VPN, se accede a la tabla de paginas y se obtiene una entrada(PTE)
	1. Bit de validez inactivo
		1. Fallo de pagina y se trae de disco
	2. Bit de validez activo
		1. No concibe los permisos
			1. *Fallo de proteccion*
		2. Cumple los permisos
			1. Se devuelve el numero de marco en el que esta ubicada la pagina(PPN)
### Fallos de pagina
Como se demoran *millones de ciclos* El SO se encarga de gestionarlos, hacen un cambio de contexto, para que se ejecute otro programa mientra se espera.
La memoria virtual usa una organizacion asociativa para minimizar los fallos de pagina, cualqueir pagina puede ir a cualquier bloque #Consultar No se dividia en espacios para cada programa
## Problemas de la Paginacion
- Tamaño de la tabla de pagina
- Multiples acceso a memoria
### Solucion a el tamaño de pagina: Multiples niveles de traduccion
Dividiremos la tabla de paginas en partes igual de tamaño fijo, y usaremos solamente las partes necesarias. Esta division tambien sera de 4kB
- Basicamente son como tabla de paginas a otras tablas de paginas
- Tambien dividiremos nuestra direccion de memoria en varias partes, cada una encargada de la direccion de las distintas tablas, por esto neecestaremos tantos bit y de numeros raros(36,39,48)
![[Pasted image 20230524112607.png]]
### Solucion a multiples accesos a memoria: Cache TLB
Se agrega un cache llamado *cache de traducciones(TLB)* que guarda las traducciones de varias direcciones virtuales para evitar tantos accesos para traduccion.
## TLB
### Funcionamiento de TLB con cache
![[Pasted image 20230529082856.png|750]]
![[Pasted image 20230529083640.png|750]]
![[Pasted image 20230529084124.png|750]]
- Con nuestro numero virtual de pagina entramos a TLB
- Si este falla falla recien entramos a la tabla de pagina

#### Observaciones
- El TLB no es parte de la jerarquia de memoria
- El fallo de pagina es un fallo de la jerarquia de memoria
- El tamaño de la pagina se lo saca del offset
	- De los bit restante son los numeros de paginas

### TLB en paralelo con cache
1. Si se accede al TLB y luego al cache, aumenta el tiempo de acierto de cache
2. Si se accede al cache con direcciones virtuales, puede ocurrir un problema de aliases
	- Puede generar que varios bloques de cache esten cargados con el mismo dato
	- Si se modifica un dato, deberian modificarse el resto de las entradas
*Solucion: Acceder a ambos al mismo tiempo*
- Se accede al TLB con los bits mas significativos de la direccion virtual
- El cache es accedido con los bits menos significativos de la direccion fisica
- Se puede lograr que el cache sea accedido con los bits del offset de pagina de manera de no esperar la traduccion
	- indice+offset<= cantidad de bits de offset
	- Esto nos limita el tamaño del cache
		- Nos indica el tamaño maximo de una memoria cache de mapeo directo
- Para evitar el problema de alias, la eetiqueta que se almacena en el cache es de la direccion fisica, no virtual.


## Protecciones de Memoria
Es la funcion principal de la memoria virtual.
*Como se comparten datos entre programa?*
P1 pide a SO accede a datos de P2. Si P2 permite, SO copia la entrada de la TP de P2 a la TP de P1.
![[Pasted image 20230529093723.png]]

## Cambio de contexto
Cuando el SO decide empezar a ejecutar un programa P1 en vez de un programa P2.
- Se deben borrar en el TLB todas las entradas pertenecientes a P2.
- Puede consumir mucho tiempo
Se suele exteneder el pacio de direcciones virtuales agregando un *identificador de procesos*
- Se mantiene un registro adicional (ASID).
- Se concatena este valor con la etiqueta del TLB.

