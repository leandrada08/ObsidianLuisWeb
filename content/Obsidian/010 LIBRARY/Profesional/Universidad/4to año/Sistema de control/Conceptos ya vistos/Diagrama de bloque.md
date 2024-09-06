## Diagrama de bloque
El diagrama de bloques simplemente muestra como se conectan los componentes del sistema y no se proporciona ningun detalle matematico. Si se conoce la relacion matematica y funcional de toddos los elementos del sistema, el diagrama de bloques se puede emplear como una herramienta para obtener la solucion analiticao por computadora del sistema




### Tipos de diagrama de bloque realimentados
Usaremos 2 sistemas realimentados, 1 con operacion en la realimentacion y otro sin operacion en la realimentacion. Al primero lo llamaremos H equivalente (Heq(s)) y al segundo lo llamaremos G eqivalente(Geq(s)). Para pasar de la primera forma a la segunda usaremos la ecuacion $$G'eq(s)=\frac{G(s)}{1+G(s)H(s)}$$


### Conexion de 2 bloques en cascada
Cuando conectamos 2 bloques en cascada estamos asumiendo que un bloque no carga al otro, por lo tanto si queremos hacer un diagrama de bloque de un sistema que tiene 2 bloques, hay que encontrar la expresion de cada uno y una expresion que conecte la entrada de uno con la salida de otro.
#### Observaciones
- Hay que colocar el bloque con mayor ganancia primero para evitar que el ruido tenga tanto incidencia. 
- Si tenemos que agrupar polos, agrupamos los ceros y polos proximos. Hay que evitar agrupar ceros y polos muy distantes porque darian ganancias grandes y atenuaciones grandes





#### Referencia:
- [[Funcion de transferencia]]