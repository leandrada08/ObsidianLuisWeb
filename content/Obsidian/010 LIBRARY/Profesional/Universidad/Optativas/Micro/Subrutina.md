## Subrutina
La subrutina de un micro es una sección de código que realiza una tarea específica dentro de un programa más grande(funciones).Cuando se llama a una subrutina, el microcontrolador ejecuta una serie de instrucciones específicas en la subrutina y luego regresa a la siguiente instrucción en el programa principal.
### Subrutinas anidadas
Las subrutinas anidadas son subrutinas que invocan a otras subrutinas dentro de ellas.
### Subrutina Recursiva
Subrutina que se llama a si misma. Debe cumplir que sea de codigo puro.
### Pasaje de parametros a las subrutinas
- Por registros
- Por memoria
- Pila
- Referencia a memoria
#### Paso de parametros standar
- Los primeros 4 registros R0, R1, R2, R3 para pasar los primeros cuatro parametros
- Los demas a la pila
- Retorno en R0 obligatoriamente
- Se pueden modificar de R0 a R3 y R12.
	- Si se necesita mas registros, se los pasa en la pila
##### Observaciones
- Si una subrutina llama a otra, sebe guardar primero R0 a R4 y eventualmente R9, si los esta usando
	- Esto tambien debe hacerse por el programa principal
## Variables globales y locales
*Variables globales:*
- Son comunes a todas las subrutinas
- Espacio de memoria donde todas las subrutinas pueden poner y sacar valores
*Variables locales:*
- Solo existen mientras dura un procedimiento
## Abstraccion
Trabajo la subrutina como si fuera una caja negra, solo me interesa lo que entra y lo que sale
#### Driver
El mismo concepto que abstraccion pero aplicado a dispositivos