## Compilador de C
![[Pasted image 20230322125528.png]]
#### Preprocesador
En esta etapa, el preprocesador procesa el código fuente del programa y genera una versión modificada del mismo. En esta versión se han incluido todas las directivas del preprocesador y se han resuelto las macros definidas por el usuario.
- Durante el preprocesamiento, tambien se llevan a cabo las siguientes tareas:
		-   Inclusión de archivos de cabecera
		-   Eliminación de comentarios
#### Compilador
Toma como entrada el archivo de código fuente modificado generado en la etapa de preprocesado, y lo convierte en un archivo objeto, que contiene el código objeto correspondiente a cada función y variable definida en el programa. Tambien realiza varias tareas, como la verificación de la sintaxis y la semántica del programa, la optimización del código, entre otras.
-  Análisis sintáctico: El compilador analiza la estructura sintáctica del código fuente para asegurarse de que se ajusta a la sintaxis de C.
-   Análisis semántico: El compilador verifica que el código fuente tenga un significado coherente y que todas las variables y funciones estén declaradas correctamente.
**Codigo Objeto:** En términos técnicos, el código objeto es una forma intermedia entre el código fuente y el código ejecutable. Contiene código de máquina y datos que se han generado a partir del código fuente, pero aún no se ha vinculado con otras bibliotecas para crear un ejecutable completo.
#### Enlazador
El enlazador se encarga de combinar todos los módulos objeto generados por el compilador en un archivo ejecutable.
- La etapa de enlazador es responsable de:
	1.  Unir todos los módulos objeto generados por el compilador en un solo archivo ejecutable.
	2.  Resolver todas las referencias y símbolos externos en el código objeto.
	3.  Asegurarse de que todas las funciones y variables utilizadas en el programa estén disponibles.
	4.  Generar el archivo ejecutable final que puede ser ejecutado por el sistema operativo.
- También puede realizar otras tareas, como optimizar el código generado por el compilador y manejar bibliotecas externas utilizadas por el programa.
#### .h y .c
Los archivos con la extensión *.c* contienen el código fuente en sí mismo, es decir, el *programa* escrito en lenguaje C.
Los archivos con extensión *.h* contienen declaraciones de funciones, variables y estructuras que se utilizan en el programa. Estas declaraciones proporcionan información sobre cómo se deben usar las funciones, variables y estructuras que se definen en el archivo .c correspondiente. *Basicamente los archivos .h son librerias*
Es común que en los archivos .c se incluyan los archivos .h correspondientes utilizando la directiva *#include*.
#### Compilar un codigo simple en C
1.  Abrir una terminal y navegar hasta el directorio donde se encuentra el archivo "programa.c".
2.  Ejecutar el siguiente comando para compilar el archivo:
``` 
gcc programa.c -o programa
```
- Donde "gcc" es el compilador de C y "programa" es el nombre del archivo ejecutable que se generará. El parámetro "-o" se utiliza para especificar el nombre del archivo ejecutable.
	- Este como es un archivo simple pasamos del codigo fuente al ejecutable en un solo paso
3.  Si el código fuente contiene errores, el compilador mostrará mensajes de error en la terminal. En este caso, es necesario corregir los errores antes de volver a compilar el archivo.
4.  Si la compilación fue exitosa, se habrá generado un archivo ejecutable llamado "programa". Para ejecutar el programa, se debe escribir en la terminal:
``` 
./programa
```
Este comando ejecutará el archivo "programa" generado en el paso anterior.


### Compilacion de un proyecto
Ejemplo de un proyecto de 3 archivos
![[Pasted image 20230322125846.png]]
Lo primero que hariamos en un proyecto como este si nunca compilamos antes un proyecto, es intentar compilar los 3 archivos tipo C:
``` 
gcc main.c
gcc main.c foo.c bar.c
```
Esto generaria un grabe error, ya que como vemos en la imagen, necesitamos varios pasos para compilar cuando tenemos varios archivos. 
1. *Pasar del .c al .o:*
- En este paso estamos pasando por las etapas de preprocesado y compilacion.
- Tenemos que hacer esto con cada archivo para obtener el archivo con codigo objeto .o.
``` 
gcc -c main.c -o main.o
gcc -c bar.c -o bar.o
gcc -c foo.c -o foo.o
```
- La opcion *-o* se utiliza para especificar el nombre del archivo ejecutable generado por el compilador y la opcion *-c* se utiliza para compilar el codigo fuente en archivo objeto
2. *Generar el ejecutable apartir de los .o:*
- En este paso unimos todos los archivo objeto generamos por las etapas de copilacion y los pasamos por la etapa de enlazador generando el programa ejecutable
```
gcc bar.o foo.o main.o -o app
```

## Make y Makefile
#### Porque usar MAKEFILE
Para simplificar la tarea de compilar y evitar que cada vez que se compile, todos los programas lo hagan, basicamente solo lo tiene que hacer el archivo que se modifico. Ademas nos ayudara a eliminar los archivos intermedio de codigo objeto para que la compilacion sea mas limpia
#### Make 
Es una herramienta que automatiza el proceso de construcción de un programa a partir del código fuente.
#### Makefile
Es un archivo de texto que contiene una serie de objetivos, reglas y dependencias que describen cómo construir el software.
*Objetivo:* Es un archivo de salida, como un ejecutable o una biblioteca compartida.Es basicamente que queremos obtener
*Regla:* Es una acción que se ejecuta para crear un objetivo, como compilar un archivo fuente, basicamente nos describen como se generara un objetivo y que dependencias se necesitan para su generacion.
- Dentro de las reglas, tambien existe algo muy importante llamado instrucciones
	- *Instrucciones:* Son las instrucciones de codigo que se deben ejecutar, basicamente son como los comandos de terminal que make realizara por nosotros
*Dependencia:* Es un archivo necesario para construir el objetivo, como un archivo de cabecera. Por ejemplo: El programa es dependiente de los archivos objetos.
### Como hacer un makefile
1. Crear un archivo llamado makefile
2. Escribir el makefile
	- Para esto necesitamos generar una reglas con sus depedencias e instrucciones
``` Python
# Regla 1
objetivo: dependecias
	intrucciones
# Regla 2
objetivo: dependecias
	intrucciones
```
- Tener en cuenta como escribi las reglas:
	- Objetivo separado con : de dependecias
	- Instrucciones tabulado abajo
#### Ejemplo programa simple de una calculadora
``` Python
# Regla1: Compila el programa principla
programa: main.o salida.o calculadora.o
	gcc -o programa main.o salida.o calculadora.o

# Genero reglas para cada .o
main.o: main.c funciones.h
	gcc -c main.c

salida.o: salida.c funciones.h
	gcc -c salida.c

calculadora.o: calculadora.c funciones.h
	gcc -c calculadora.c

```
### Tipos de reglas
#### Basicas
- Tenemos las *reglas basicas* que son las que usamos para compilar el programa y para generar las dependencias del mismo(son las que se pueden ver arriba)
#### Limpieza de codigo
- Tambien podemos agregar *reglas para limpiar el codigo*, ya que las reglas anteriores, me dejaran la carpeta llena de programa de codigo objeto, tambien para que el terminal este mas limpio
``` Python
# Reglas de limpieza de archivos codigo objeto
clean: # Fijarse que no tiene dependencias de nadie
	rm -f programa *.o #Aqui usamos los comandos rm -f para borrar todo lo siguiente

```
- Tener en cuenta que el * hace referencias a cualquier combinacion de caracteres que exista, en este caso le estamos diciendo que borre cualquier combinacion de caracteres que termine en .o
#### Principal
- Lo que se hace es generar una regla que indica cual es la regla principal que quiero que se compile cuando compile el programa, ya que si no indico esto, cuando haga make y no detalle la regla, se ejecutara la primera regla que el compilador encuentre en el programa makefile
``` Python
all: programa1 programa2 #aqui colocamos todos los programas que queremos que se ejecuten por defecto
```
- Comunmente le llamamos all a esta reglas principal

#### Imprimir
Podemos usar reglas para imprimir, ya sea para depurar o para ver algo de nuestro interes
``` Python
# Regla para imprimir
imprimir:
	echo $(x)
	@echo $(y)
```
Cuando imprimimos debemos utilizar el comando echo, esto hace que el compilador nos muestre 2 veces el programa, para eso utilizamos el comando @, que hace que solo se nos muestre la variable
- En el ejemplo se mostratia 2 veces el valor de x y 1 vez el valor de y

### Reglas implcitas
Son reglas que el makefile ya sabe como compilar por lo tanto no necesitamos darle las instrucciones, con solo poder el objetivo y las dependencias es suficiente.
Las reglas implicitas de make son:
- Compilacion de .c a .o
- compilacion de C++ a .o
- Compilacion de pascal a .o
- Compilacion de assembler a .o

Para ver todas estas reglas y los prefijos a utilizar para usarlo ver en:https://www.gnu.org/software/make/manual/html_node/Catalogue-of-Rules.html
Esto nos resumiria el texto en:
 Python
main.o: main.c funciones.h

salida.o: salida.c funciones.h

calculadora.o: calculadora.c funciones.h


### Recompilacion dependencias
Make tiene las fechas y hora de cuando se modifico cada .c y cuando se genero cada .o de esta menera puede saber si se modifico un archivo o no, para saber si recompilarlo o no


### Variable
Nos permiten hacer mas flexible nuestro makefile y nos lo simplifica
- Se declaran en la parte superior
``` Python
# Declaro las variables que usare
# Declaro una variable para lo archivos objetos
OBJS = main.o salida.o calculadora.o # Declaro la variable

# Declaro una variable con los programas principal
BINARY= programa # Declaro la variable

```
- Se utilizan con $(Variable)
``` Python
# Regla usando variable
programa: $(OBJS)
	gcc -o $(BYNARY) $(OBJS)

# Regla sin usar variable
programa: main.o salida.o calculadora.o
	gcc -o programa main.o salida.o calculadora.o
```
#### Variables recursivas y expansion simple
Cuando en la definicion de la variable tenemos la definicion de otra variable adentro, tenemos 2 manera de que ese variable interna tome un valor. En el caso de recursiva, se toma el valor que tiene la variable interna en el momento que se la usa y en el caso de expansion simple se toma el valor que tiene en el momento que se la define
``` Python
x = hola
y = $(x) adios # Variable recursiva
z := $(x) adios #Variable con expansion simple
x = adios
imprimir:
	@echo $(y) # Muestra "adios adios"
	@echo $(z) # Muestra "hola adios"

```
#### Variables comunes
``` Python
CC = arm-none-eabi-gcc  # compilador a utilizar
CFLAGS = -Wall -O2 -mthumb -mcpu=cortex-m0plus  # opciones de compilación
LDSCRIPT = stm32f072rb.ld  # archivo de script de enlazado
TARGET = main  # nombre del archivo de salida
```
*CFLAGS:* Son banderas cuando compilamos programas en c. Se lo utiliza siempre que pasemos de un .c a un .o

### Patrones
El % se remplaza por 1 o mas caracteres, parecido a lo que haciamos con *
``` Python
%.o: %.c # A partir de cualquier archivo .c podemos generar su correspondiente .o
```
Esto lo usaremos para hacer reglas distintas para distintas carpetas
``` Python
carpeta1/%.o: carpeta1/%.c # Todos los archivos .c de carpeta, compilar en .o
```
### Variables automaticas
Variables definidas por MAKEFILE para hacer cosas automaticamente. Esto nos simplifica escribir varias veces lo mismo
*$<* para  hacer referencia al primero de las dependencias(al nombre)
*$@* para hacer referencias al objetivo(al nombre)



### Caracteres utilizados
Los caracteres $, /, % y @ son utilizados en los Makefiles para realizar diversas tareas, entre las que se incluyen:
-   $: Se utiliza para referirse a variables. En los Makefiles, las variables se definen con la sintaxis VARNAME=value. Para utilizar una variable, se utiliza la sintaxis ${VARNAME}. Por ejemplo, ${CC} se refiere al compilador que se está utilizando.
-   /: Es utilizado para separar directorios en rutas de archivo. En sistemas Unix, se utiliza el caracter / para separar los directorios en las rutas de archivo, mientras que en sistemas Windows se utiliza el caracter . En los Makefiles, se utiliza el caracter / para referirse a directorios o rutas de archivo.
-   %: Es utilizado en las reglas de patrones para hacer coincidir cualquier cadena de caracteres. Por ejemplo, si se define la regla %.o: %.c, Make buscará todos los archivos con extensión .c y los compilará en archivos con extensión .o.
-   @: Se utiliza para indicar que no se muestre la regla que se está ejecutando. Cuando se utiliza el caracter @ antes de una regla, Make no mostrará la salida de esa regla en la consola. Esto se utiliza para evitar que la salida de la regla ensucie la consola.
- `$<` se utiliza para hacer referencia al primer elemento en la lista de dependencias. En este caso, se refiere al archivo fuente que se está compil
- El carácter '^' se utiliza en el Makefile como un símbolo de continuación de línea. Esto significa que si una regla es demasiado larga para caber en una sola línea, se puede dividir en varias líneas y utilizar el carácter '^' al final de cada línea para indicar que la regla continúa en la siguiente línea. De esta manera, el Makefile se puede escribir de manera más legible y fácil de mantener.


### Wildcard y patsubs
#### Wildcard
En un archivo Makefile, un "wildcard" es un carácter especial que se utiliza para representar una cadena de caracteres arbitraria en un patrón de búsqueda. La instrucción wildcard en un Makefile permite que el programa busque y utilice automáticamente un conjunto de archivos que cumplan con ciertos criterios, basados en patrones de nombres de archivo.

La sintaxis de la instrucción wildcard es la siguiente:
``` Python
$(wildcard pattern)
```
Donde "pattern" es una cadena de caracteres que incluye uno o más caracteres especiales de comodín

#### Patsubs
La instrucción "patsubst" en un Makefile es utilizada para realizar una sustitución de patrones en una lista de cadenas. En otras palabras, patsubst reemplaza un patrón específico en una cadena con otra cadena.
La sintaxis de la instrucción "patsubst" es la siguiente:
``` Python
$(patsubst pattern,replacement,text)

```
Donde "pattern" es el patrón a buscar, "replacement" es la cadena de reemplazo y "text" es la lista de cadenas que contienen el patrón a reemplazar.




# Consultas TINI
- Hace falta poner el -o cuando queremos obtener el objeto?
- Diferencia entre poner % y *
- No podemos dejar que se haga automaticamente el paso de .c a .o



## Observaciones de TINI
- A la hora de analizar consecuentes en la regla, estas lo hacen de izquierda a derecha