# Modelado de redes de Petri orientado a los recursos

Al estudiar el problema de evitacion de puntos muertos en sistemas de fabricacion de automatizados, se propuso por primera vez redes de Petri orientadas a recursos(ROPN). En esta red, cada recurso esta modelado por un solo lugar, y los procesos de fabricacion de piezas estan modelados por los caminos en los que las piezas visitan los recursos.

## Pasos del modelado ROPN
Los modeladores de ROPN piensan que los procesos de produccion de piezas en un AMS son un proceso de asignacion dinamica de recursos, y un recurso puede considerarse como un servidor. Por lo tanto, modelan cada recurso en el sistema por un solo lugar. Las partes a ser procesadas por el sistema llegan a los recursos que compiten por ellas. Los modeladores de ROPN tratan a las *maquinas y su buffer como el mismo tipo de recurso(recurso H)*. No hay diferencia entre una pieza procesada por una maquina y esperando en un buffer en el sentido de ocupacion de recursos. *Los dispositivos de maneja de materias(traslado de materiales) se tratan como otro tipo de recurso(recurso G)*
Debido a que los recursos en los sitemas de fabricacion son limitados, se utilizan PN de capacidad finita, junto con sus correspondientes reglas de activacion y habilitacion de transicion.
El modelado de un AMS por ROPN se puede realizar en dos fases:
1. Modelar los procesos de produccion de piezas independientemente del transporte del material
2. Segun el modelo de la fase 1, modelar el material y procesos de entrega.
### Interpretacion de lugares, transiciones y tokens
1. Un lugar de los Recursos H
	-  Un token en el indica que un trabajo utiliza el recurso
	- Si no hay token indica que el recurso es gratis
	- Su disponibilidad esta determinada por el numero de espacios libres disponibles en el. Los espacio libres se definen como la capacidad del lugar menos el numero de fichas que hay en el.
2. Un lugar representa el almacenamiento centro en un AMS como un recuros H especial: su capacidad se considera infinita. Por lo tanto, tal recurso esta siempre disponible. Las fichas en dicho lugar indican que las ordenes de trabajo estan esperando para ser procesadas. Si no hay token indica que no hay ningun trabajo para procesar
3. Un lugar de los Recursos G
	- El numero inicial de fichas en el es una constante. Un token en el indica que el recurso esta disponible; ningun token indica que no esta disponible
4. Una transicion en un modelo ROPN representa que un trabajo se mueve de un recurso a otro recurso