# Documentacion
- La documentacion publica va en los .h
- La documentacion privada va en los .c
- Los comentarios en c se hacen con //
	- Podemos escribir a la par el comentario, para que quede mas limpio poner //!<
## Diagramas UML con Plantul
- Permite generar la mayoría de los diagramas de UML para documentar el diseño del proyecto.
- Los diagramas se generan a partir de un archivo de texto con comandos muy sencillos.
- Es muy fácil de mantener y muy rápido dado que no hay que preocuparse por la parte gráfica.
### Diagrama de actividades
![[Pasted image 20230327141557.png|500]]
### Diagrama de secuencia
Grafica como se van pasando mensajes, eventos, llamadas a funcion, etc.
![[Pasted image 20230327141842.png|500]]
### Diagrama de maquina de estado finito



## [[MARKDOWN]]

## Documentacion con Doxygen
bitbucket.org(pagina de doxygen)
- Permite generar documentación de estructuras, tipos y funciones.
- Se genera a partir de comentarios especiales en el código fuente.
- La documentación puede generarse en HTML, Latex, PDF, Man Pages, RTF y XML.
- También puede documentase parte del diseño utilizándolo con plantuml y markdown.
- Es una API que permite hacer todo lo que dijimos
Esta documentacion va antes de las definiciones de la funcion
``` C
/** @brief Declaracion corta de la funcion que esta abajo de esta(Titulo basicamente)
* @param Muestro el parametro de la funcion
* @param Muestra el siguiente parametro
* @return Introducimos que devuelve
*
*/
```
#### API
Una API (Application Programming Interface) es un conjunto de reglas, protocolos, herramientas y definiciones que permiten a diferentes aplicaciones interactuar entre sí. Básicamente, es una interfaz que proporciona una manera estándar y estructurada para que las aplicaciones se comuniquen entre sí.
En términos simples, una API actúa como un intermediario entre dos aplicaciones, permitiendo que una aplicación solicite datos o servicios de otra aplicación y que la otra aplicación responda a la solicitud. Las API son muy comunes en la programación web, ya que permiten que diferentes aplicaciones web se comuniquen y compartan datos.
Por ejemplo, una API de Google Maps permite a un sitio web mostrar mapas y direcciones utilizando los datos de Google Maps. Una API de Twitter permite a una aplicación mostrar tweets en su sitio web o aplicación.
