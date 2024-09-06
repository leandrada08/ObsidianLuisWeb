## Que es un sistema operativos
- Un programa que actúa como un intermediario entre la electrónica y el usuario de una computadora.
- Un gestor de recursos: Maneja todos los recursos y define pedidos conflictivos para una asignación eficiente y justa.
- Un programa de control: Controla la ejecución de los programas para prevenir errores y el uso incorrecto de los recursos.

## Objetivos de un sistema operativo
El sistema operativo nos da concurrencia, se ejecuta un pedazo de cada programa a la vez pero muy rapido, esto hace que macroscopicamente parece que sea en paralelo.
- Simplificar el uso del sistema tanto para los usuarios como para los desarrolladores.
- Utilizar los recursos de forma mas eficiente simplificando el uso compartido de un mismo recurso por varios programas.
- Controlar la ejecución de los programas del usuario fijando limites en las acciones que estos pueden realizar.

## Porque usamos SO en sistemas operativos?
- Para manejar varias tareas al mismo tiempo
- Por las mismas razones que en una computadora de escritorio.
- En lugar de interactuar con el usuario lo hacen con el programador de la aplicación.
- No todos los servicios se requieren en todos los dispositivos.
- Características particulares respecto a los sistemas operativos de propósito general

## Capacidad de configuracion del SO
- Cubrir todas las necesidades no resulta eficiente, por lo que hay que eliminar las funciones del sistema que no utilizamos ya que tenemos poco espacio y necesitamos solo tener lo que usaremos en el SO
	- Eliminar las funciones no utilizadas con el enlazador.
	- Compilación condicional con #if y #ifdef.
	- Herramientas de configuración que validan las opciones seleccionadas.
	- Generación de co ́digo a partir de la configuración definidas.

## Gestion de los dispositivos
En los dispositivos de escritorios, todos dispositivos de entrada salida son gestionados por el sistema operativo
En embebio, esto no hace falta, ya que:
1. Hace que el sistema operativo sea mas grande(No tenemos mucho espacio)
2. Hace mas lento el manejo de dispositivos
![[Pasted image 20230612144242.png]]


## Gestion de las interrupciones
Las gestion de interrupciones hacen que el sistema operativo este por encima de los programas, es por eso, que es muy importante que los SO manejen las interrupciones,  nosotros nunca manejamos las interrupciones, siempre lo hace el SO.
En un embebidos, se permite que el usuario maneje las interrupciones para evitar problemas de latencia.
- Las interrupciones pueden ser utilizadas por cualquier proceso.
- En los sistemas de tiempo real es muy importante conocer el tiempo de respuesta de una interrupción y en lo posible minimizar el mismo.
- Las interrupciones pueden iniciar o detener tareas ya sea en forma directa o bien interactuando con el sistema operativo.
En embebidos, el sistema operativo es como una biblioteca que nos resuelve cosas.

## Sin mecanismos de proteccion
- Los sistemas embebidos son diseñados para un único propósito y normalmente no se utilizan programas que no hayan sido probados.
- Es normal que una tarea realice sus propias operaciones de entrada/salida utilizando los modos privilegiados.
- Puede ser necesario utilizar los mecanismos de protección por razones de seguridad.

## Sistema operativo de tiempo real
- Es un sistema operativo que soporta la construcción de sistemas de tiempo real.
- El comportamiento temporal debe ser predecible: las reglas de ejecución deben permitir conocer de antemano los resultados del mismo.
- Debe ser determinístico: para todos los servicios del sistema operativo existe un limite definido en el tiempo de ejecución.

## Espera activa
Como programabamos hasta ahora
- Es la técnica donde un proceso verifica una condicion repetidamente mediante el uso de un lazo.
- Es la forma más natural de programación en sistemas no concurrentes.
- No debe ser utilizada en sistemas concurrente de tiempo real dado que el proceso no libera uso del procesador.

## Espera pasiva
- Es la técnica donde un proceso permanece sin acceso al procesador hasta que se verifica la condición se espera.
- El sistema operativo brinda servicios para gestionar las condiciones que el proceso espera.


## Programas, Tareas y Procesos
- Un *programa* es una lista de instrucciones.
- Un *proceso* es un programa en ejecución.
	- Un programa se convierte en un proceso cuando el mismo es puesto en ejecución.
	- Un programa es una entidad pasiva que reside en el almacenamiento, mientras que un proceso es una entidad activa.
	- Un único programa puede convertirse en varios procesos, cada uno de ellos tendrá las mismas instrucciones pero distintos estados.
#### Averiguar #Consultar 
- Diferencia entre tarea y proceso
- Diferencia entre proceso e hilo
### Partes de un proceso
- *Text area:* contiene el co ́digo del programa.
- *Data area:* contiene las variables globales.
- *Stack area:* contiene datos temporales como parámetros de funciones, direcciones de retorno y variables locales.
- *Heap area:* contiene datos creados en forma dinámica durante la ejecución.
- *Context:* contiene el estado actual del proceso, por ejemplo el contador de programa y los registros del procesador.
	- Cuando estamos en un proceso, el contexto tiene las medidas de seguridad, cuando estamos en un hilo no tenemos esto, para cambiar de procesos tenemos que hacer un cambio de contexto para un hilo no

### Estados de un proceso
![[Pasted image 20230612151649.png]]
- *Created:* Mientras se lo crea. Aqui se crean las variables, las constantes, etc.
- *Ready:* Una vez que esta listo para comenzar a ejecutarse, en este estado tenemos varios procesos
- *Running:* El procesos que se esta ejecutando 
- *Waiting:* Esta esperando un dato o algo. Cuando el sistema operativo ve que se cumplio lo que esperaba lo manda de nuevo a ready

### Cambio de contexto
![[Pasted image 20230612152647.png]]
- Guardo el estado de un programa con una interrupcion
- Recupero el estado de otro programa despues de la interrupcion

## Partes del Kernel
### Planificador o Scheduler
Es el que elije quien entrara en proceso
- Es la parte del sistema operativo encargada de asignar el uso del procesador.
- La asignación se realiza siguiendo un conjunto de reglas llamadas *Política de Scheduling.*
- Las politicas más utilizadas son *Round Robin y FiFo*
#### Round Robin
Aqui se puede usar espera activa
- El procesador se asigna a todos los procesos por igual siguiendo una ronda.
- Es la política más utilizada en los sistemas operativos de escritorio.
#### FiFo
Aqui no se puede usar espera activa, tampoco si se combina con Round Robin
- El procesador se asigna al proceso de mayor prioridad que lleva más tiempo esperando.
- Es la política más utilizada en los sistemas operativos de tiempo real.

## Tipos de sistemas operativos
### Sistemas cooperativos
El proceso debe dejar voluntariamente el procesador para ir a runing o waiting
- En este tipo de sistemas el proceso que hace uso del procesador debe ceder voluntariamente el mismo para que otro proceso pueda ejecutarse.
- Son más simples de implementar porque no tienen problemas de sección critica.
- Es más difícil cumplir limites de tiempo.


### Sistemas Expropiativos
El sistema operativo saca al proceso sin importar el estado del proceso.
- Este tipo de sistemas cuenta con la capacidad de quitar el procesador al proceso que está ejecutando sin intervención del mismo.
- No existe la posibilitad de que un proceso monopolice el uso del procesador.
- Es más difícil predecir el comportamiento del sistema


