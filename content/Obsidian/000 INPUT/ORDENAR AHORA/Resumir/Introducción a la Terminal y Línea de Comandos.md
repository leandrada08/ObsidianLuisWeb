

## Introducción a la Terminal y Línea de Comandos


**Preguntas:**
- ¿Por qué debemos de aprender a manejar la terminal?
- ¿A qué nos referimos cuando hablamos de una línea de comandos?
- ¿Qué nos muestra la terminal?
- ¿Qué aloja nuestra terminal?
- ¿Qué tipos de shell o líneas de comandos tenemos?
- De forma sencilla ¿Qué es un comando?

> La terminal es una herramienta indispensable que toda persona que se dedique a la tecnología debería de conocer.

- Razones por las que debemos de aprender a manejar la terminal de comandos a la perfección:
- Tiene mucha flexibilidad, es decir, con unos cuantos comandos podemos hacer procesos dentro de nuestra computadora de forma eficaz.
- La velocidad, ya que hacer actividades dentro de la terminal es mucho más rápido que hacerlo por la terminal gráfica.
- No siempre contaremos con una interfaz gráfica y en ocasiones incluso nos puede fallar.
- Podemos invocar demonios, es decir, nos permite interactuar con nuestro sistema informático a un nivel muy bajo.
- La terminal es una interfaz gráfica que simula una línea de comandos (shell).
- Terminal: es la ventana que nos muestra el prompt (la barra que normalmente esta titilando). Esta es la que aloja a la shell.
- Línea de comandos (shell): es un programa que toma comandos y los pasa al sistema operativo para hacer algo.
- Comandos: es un programa que se puede ejecutar desde la terminal y esta puede recibir algunos parámetros y opciones.
- Bash Shell (de las más comunes)
- Z Shell (de las más comunes), esta esta presente en las mac del 2019 en adelante.
- PowerShell (esta es de Windows)
![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

> SUMMARY: conocer de terminal y línea de comandos es muy importante si nos vamos a dedicar a trabajar en el mundo de la tecnología, ya que en algún punto necesitaremos usarla. Trabajar con la terminal y línea de comandos es muy útil, ya que nos permite tener más flexibilidad y velocidad al momento de interactuar con nuestra computadora. Una terminal es una interfaz gráfica que simula a una línea de comandos o shell. Una shell es un programa que toma comandos y los pasa al sistema operativo para hacer algo. Un comando de forma sencilla es un programa que se puede ejecutar desde la terminal y este puede recibir algunos parámetros y opciones. Los tipos de shell más comúnes son: Bash Shell (Linux), Z Shell (Mac a partir del 2019) y Power Shell (Windows).


*investigar que tipos de shell existen y su utilidad.*


## Terminal
**Preguntas:**
- ¿Por dónde comienzan las rutas que tenemos dentro de nuestra terminal?
- ¿En qué carpeta se encuentran directorios que almacenan la información de nuestros usuarios?
- ¿Qué nos encontramos al abrir nuestra terminal?
- ¿Cuál es el símbolo que hace referencia a que estamos en el home?
- ¿Qué comandos podemos usar para navegar entre nuestros archivos?
- ¿De qué necesitan ser acompañados algunos comandos para funcionar?
- ¿Qué símbolo necesitamos para acceder a las opciones de los comandos?
- ¿Qué opciones tenemos dentro del comando ls?
- ¿Qué son operadores de ruta absoluta?
- ¿Cuáles son operadores de ruta relativa?
- ¿Cómo podemos copiar dentro de la terminal?


- Antes de caminar dentro de la terminal, debemos saber en que lugar estamos.
- El sistema de archivos de nuestro sistema operativo esta distribuido de la siguiente forma:
- Todo comienza con el / y partir de el se van desplegando las carpetas que podemos observar.
- Estas carpetas contienen archivos del sistema operativo, drivers y ejecutables.
- Una carpeta especial que debemos conocer su existencia es la de home, dentro de ella se almacena la información de nuestros usuarios.

### / de sistemas de archivos
![](https://notionenespanol.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fd647d3a9-2b28-4599-aa93-04d5c4d947f4%2FUntitled.png?table=block&id=a8928dbd-e2b1-4240-af96-ff99cd00d180&spaceId=e1aecfd5-e167-4495-af92-c53aabe7d985&width=1040&userId=&cache=v2)


Lo primero que aparece es nuestro nombre de usuario, después del arroba tendremos el nombre del equipo o host name. El símbolo ~ hace referencia a que estamos en el directorio home. Por defecto entraremos siempre ahí.

### Comandos basicos
#### ls
- **ls**: significa list, nos permite listar los archivos donde nosotros estamos. Los comandos también reciben opciones y estas se ponen con un \- y la letra de esa opción.
	- **ls -l**: la letra "l" significa long y lo que nos permite es ver: cuándo fue creado, peso del archivo (bits), nombre.
	- **ls -lh**: la h significa human, lo que nos permite es visualizar igual que arriba, pero con la diferencia de que el peso se muestra en mega bits.
	- **ls -la**: nos va a mostrar todos los archivos, incluso los ocultos (los ocultos son todos los que tienen un punto al inicio)
	- **ls -lS**: la S es te size o tamaño y nos ordenara todos nuestros documentos por tamaños.
	- **ls -lSh**: nos muestras los archivos ordenados por tamaño con el tamaño que tiene cada archivo.
	- **ls -lr:** nos muestra los datos de reversa al alfabeto a lo que normalmente vienen
- **tree**: este nos permite desplegar todos nuestros directorios como si fueran un árbol.
- **tree -L 2:** la L es de levels y el número indica los niveles a los queremos profundizar. Estos números pueden ir a los que necesitemos.
#### CD
- **cd:** significa change directory, este comando necesita una ruta o parámetro para poder movernos a una carpeta. Si a cd no le ponemos parámetros nos llevará siempre a home.
- Operadores de ruta absoluta: Es la que nos muestra específicamente hacia donde queremos ir. /home/codevars/Documents/Dev
	- Este lo podemos usar para ir de forma específica a un directorio cd /home/codevars/Documents/Dev
- Operadores de ruta relativa: 
	- **.** nos sirve para ubicarnos dentro de nuestro directorio actual. cd ./Documents/Dev
	- **..**: nos permite regresarnos a un directorio atrás. cd .. o cd ../..


#### Otros
- **clear:** significa limpiar y nos permite limpiar nuestra pantalla, también podemos usar la combinación Ctrl + L
- **pwd:** significa print working directory, nos dice la ruta de donde estamos.
- **file:** nos permite describir un tipo de archivo.

> Bash o la shell tiene un archivo en el home llamado history que normalmente nos dirá todo lo que hemos estado haciendo, usualmente guarda los primeros mil comendas. Por ello si queremos volver a usar un comando podemos con las flechas de arriba y abajo volver a un comando que ya hayamos utilizado antes.

> Para copiar dentro de la terminal podemos usar la combinación Ctrl + Shift + C.

> Podemos escribir el inicio del nombre de nuestros archivos y aplastar Tab, esto hará que si hay una coincidencia se autocomplete el texto.

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

> SUMMARY: para movernos dentro de nuestros archivos en nuestra terminal debemos conocer cómo están distribuidas las carpetas dentro de Linux, todo comienza desde / y a partir de ella se desprende más carpetas, la que nos interesa a nosotros es home, ya que está almacena carpetas con el nombre de usuario de nosotros y dentro de ella almacena todos nuestros archivos. Al entrar a nuestra terminal podremos observar nuestro nombre de usuario y el nombre de nuestro computador. Entre los comandos esenciales para movernos dentro de la terminal tenemos: ls, cd,pwd y file. Al usar cd tenemos dos opciones para utilizar rutas: operadores de ruta absoluta (muestran la ruta específica para movernos) y operadores de ruta relativa (varían de acuerdo al directorio donde nos encontremos).

![☝](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

## Manipulacion de directorios y archivos

**Preguntas:**
¿Qué comando nos permite desplegar todos nuestros directorios en forma de árbol?
¿Cómo podemos indicar los niveles a los que queremos profundizar con tree?
¿Qué comando usamos para crear directorios y archivos?
¿Cómo podemos crear un directorio con palabras separadas?
¿Cómo podemos crear muchos archivos y directorios a la vez?
¿Qué comandos usamos para manipular archivos?
¿Qué opciones tenemos para usar rm?

### Comandos
mkdir: significa make directory y al ponerle un nombre nos permite crear un directorio o carpeta. Si queremos crear un directorio con un nombre separado con espacios necesitamos ponerlo entre comillas mkdir "Hola Mundo", pero esto no es tan recomendable, ya que no nos permite manipularlos adecuadamente.

touch: significa tocar y nos permite crear un nuevo archivo. Para crearlo debemos de asignar un nombre al archivo con su extensión si así lo necesitamos.

> Si queremos crear más de un directorio o archivo a la vez podemos usar el mismo comando y separando a los nombres de cada archivo o directorio por un espacio mkdir dir1 dir2 dir3 o touch file1 file2 file3.

cp: significa copy y nos permite copiar un archivo. Para hacerlo necesitamos poner el nombre del archivo que queremos copiar y cómo se va a llamar el nuevo archivo cp file1 file\_bk.

mv: significa move y nos permite mover un archivo. mv file\_bk .. o otro directorio mv dir1 dir2

Con esta opción también podemos renombrar un archivo o directorio, para hacerlo debemos de poner el nombre del archivo o directorio y poner el nuevo nombre que queremos asignarle mv file\_bk fileCopy

rm: significa remove y nos permite borrar archivos y carpetas. Debemos tener mucho cuidado con este comando.

rm -i: con la función interactiva i podemos borrar y al hacerlo nos preguntará si en realidad estamos seguros de borrar un archivo.

rm -r: la r significa recursive y nos permite borrar directorios. Podemos usarla junto con la función interactiva rm -ri nombrearchivo

rm -rf: la f significa force y es muy peligrosa, ya que borrará todo sin importar que sea.

Podemos borrar un conjunto de archivos usando rm -r nombre1 nombre2 nombre3 'Nombre4'

> La función interactiva nos permite tener más control de todo lo que estamos eliminando y de esta forma no eliminar archivos que no queríamos.

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

SUMMARY: la terminal nos permite manipular nuestros archivos y directorios de una manera mucho más rápida. Tenemos comando para: creación de directorios y archivos (mkdir y touch) y manipulación de archivos (cp, mv y rm). Dentro de la opción remove podemos usar: rm -i (añade menu interactivo), rm -r(borra directorios), rm -ri (añade menú interactivo al borrado de directorios) y rm -rf (borra todo de manera forzada). Otro comando importante es tree, este nos permite ver nuestros archivos cómo un árbol y usando tree -L 1 podemos definir el nivel al que queremos llegar.

![☝](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

ACTIONS NEEDED: practicar manipulando archivos y directorios.

Date: @17 de noviembre de 2021

¿Cuál es la ventaja de usar comandos para ver el contenido de nuestros archivos desde la terminal?

¿Qué comandos tenemos para explorar el contenido de nuestros archivos de texto?

¿Qué comando nos permite ver el contenido de nuestros archivos de forma interactiva?

¿Cómo podemos buscar una palabra dentro de less?

¿Cómo salimos de la ventana de less?

¿Qué comando nos permite abrir archivos desde su aplicación nativa?

¿Qué otro comando nos permite abrir directorios desde nuestra interfaz gráfica?

Desde la terminal tenemos la opción de explorar el contenido de nuestros archivos sin necesidad de utilizar la interfaz gráfica.

Para hacerlo tenemos varios comandos:

head: este nos mostrará la cabecera de nuestro archivo de texto. Esto nos mostrará las primeras 10 líneas de nuestro archivo de texto.

head nombrearchivo.txt -n 15: con n podemos modificar las líneas que vienen por defecto.

tail: es muy parecido a head, este nos muestra las últimas 10 líneas de nuestro archivo de texto.

tail nombre.txt -n 20: al igual que head con n podemos elegir que últimas líneas necesitamos.

less: nos permite entrar a una ventana interactiva para visualizar todo el texto. Una vez estamos dentro de la ventana interactiva podemos usar la tecla / y podremos buscar palabras desde la terminal. Para salir debemos de aplastar la tecla Q que significa quit.

xdg-open: nos permite ver nuestro archivos de texto con nuestro editor de texto predeterminado. Siempre que se abra un programa externo de la terminal se crea un proceso que es muy útil cuando hay errores en la terminal gráfica. Si queremos terminal cualquier proceso en la terminal que se este ejecutando debemos aplastar Ctrl + C.

nautilus: nos permite abrir una carpeta en la interfaz gráfica. Para terminarlo desde la terminal debemos usar Ctrl + C.

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

SUMMARY: con la terminal podemos explorar el contenido que tenemos dentro de nuestros archivos sin necesidad de abrirlos, esto es muy útil porque nos ahorra tiempo. Los comandos que tenemos para ver el contenido de nuestros archivos son: head, head nombre -n 12, tail, tail nombre -n 12 y cat. Además de estas opciones dentro de la terminal tenemos la opción de usar less que nos muestra una ventana interactiva con todo el contenido que tenemos dentro de un archivo, podemos buscar palabras con / y para salir de esta opción usamos q. También podemos usar comandos para abrir nuestros archivos con la aplicación por defecto de nuestro computador con: open en Mac, xdg-open en Linux y wslview para WSL, si se nos queda corriendo la aplicación en la terminal podemos finalizarla usando Ctrl + C. Otro comando que funciona de igual manera es nautilus.

![☝](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

ACTIONS NEEDED: practicar revisando el contenido que tenemos dentro de archivos.

Date: @17 de noviembre de 2021

¿Qué comando nos muestra en que categoría entra un comando?

¿Qué necesitamos para pasar una palabra completa a nuestros comandos?

¿Qué es un alias en la terminal?

¿De qué debemos tener cuidado con el comando alias?

¿Qué comando nos da información sobre cómo usar un comando?

Un comando básicamente puede ser 4 cosas:

Un programa ejecutable, es decir, que se compilo en un lenguaje de programación y nosotros lo podemos utilizar. Estos ejecutables normalmente se guardan en la ruta de /user/bin.

Un comando de utilidad shell, es decir, es un comando que ya viene dentro de este programa.

Una función de shell, que son funciones de shell que no vienen dentro del programa.

Tenemos un comando que nos muestra la naturaleza de los comandos, este es type y nos permite determinar que comando es de las 4 categorías que acabmos de ver. type cd.

Podemos crear nuestro propios alias, para ello usamos:

alias l="ls -lh": el nombre que lo pongamos es el que va después de alias y la función que queremos que haga es lo que va después del signo =.

> Los alias no duran para toda la vida, es decir, son temporales.

Hay una utilidad de la shell que nos ayuda mucho para saber sobre los comandos:

help: si ponemos esto y el comando que queremos saber se nos mostrara todo lo que podemos hacer con el.

ls --help: es otra forma de invocar la ayuda para un comando.

man: nos muestra un manual de usuario del comando con el nombre, sinopsis, descripción, etc. Para salir de esta pantalla usamos Q quit.

info: es un comando similar a man, pero de una manera un poco más resumida, para salir usamos la letra Q.

whatis: nos da una descripción muy corta de que hace el comando. Este no funciona con todos.

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

SUMMARY: los comandos básicamente pueden ser 4 cosas: programas ejecutables, comandos de utilidad de la shell, funciones de la shell o un alias. Si queremos saber en cuál de estas 4 categorías entra un comando podemos usar type. Crear un alias es muy útil, ya que nos permite ejecutar un comando con una palabra elegida por nosotros, para crearlos usamos alias nombre\_que\_queremos\_dar="comando", pero debemos tener cuidado porque al cerrar la terminal el comando se borrará. Si no sabemos para que funciona un comando o queremos obtener más información sobre uno en específico podemos usar: help, comando --help, man, info y whatis; estos nos mostrarán información sobre el comando que queramos.

![☝](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

ACTIONS NEEDED: practicar creando alias y revisando información de comandos.

Date: @17 de noviembre de 2021

¿Con qué comandos podemos usar las wildcards?

¿Qué combinación nos permite buscar archivos?

¿Cuáles son las wildcards tenemos?

¿Qué opción extra tenemos con ls?

![👨🏾💻](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

Las wildcards son una serie de caracteres especiales que nos permiten encontrar patrones o realizar búsquedas mucho más avanzadas. Estas búsquedas las vamos a hacer con el comando ls.

Para empezar a buscar archivos usamos:

ls \*.txt: nos mostrará todas las coincidencias que terminen en .txt.

ls datos\*: nos muestra todos archivos que tengan la palabra datos, sin importar que venga después.

ls datos?: nos muestra todas las palabras que tengan datos al inicio y solo tengan un carácter al final. Para aumentar los caracteres que queremos que busque solo agregamos más signos de interrogación.

ls \[\[:upper:\]\]\*: nos muestra directorios que empiecen por mayúsculas y que tengan cualquier contenido más. Esto buscará en dos niveles de las carpetas.

ls -d \[\[:upper:\]\]\*: nos sirve para buscar solo los directorios que inicien con mayúscula.

ls -d \[\[:lower:\]\]\*: nos mostrará todos los archivos o directorios al agregarle -d que empiecen con mayúscula.

ls \[ad\]\*: nos mostrará todos los archivos que inicien con una a o con una d y le siga cualquier carácter.

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

SUMMARY: las wildcards son una serie de caracteres especiales que nos permiten encontrar patrones o realizar búsquedas mucho más avanzadas. Estas las podemos usar junto con: ls, cp, mv, y rm. Entre las wildcards más útiles tenemos: \*, ?, \[\[:upper:\]\], \[\[:lower:\]\], \[\]. Al usar wildcards y ls tenemos la opción de usar ls -d que nos permite realizar acciones solo dentro del directorio en el que estamos.

![☝](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

ACTIONS NEEDED: practicar usando las wildcards.

Date: @17 de noviembre de 2021

¿Qué son las entradas y salidas en la terminal?

¿Cómo se le conoce a una entrada?

¿Cómo se les conoce a las salidas?

¿Cómo se les conoce a los números que asigna la terminal a nuestras inputs y outputs?

¿Qué file descriptors tenemos en la terminal?

¿Para qué nos sirven las redirecciones?

¿Cómo podemos hacer redirecciones?

¿Por qué debemos tener cuidado al usar redirecciones con \>?

Cómo hemos visto a lo largo de las clases, normalmente ingresamos un comando o texto en la terminal y ella produce una acción o salida. Es decir, nosotros vemos un Output.

Para entender las redirecciones debemos de aprender a manejar las entradas y salidas por medio de operadores especiales para hacer diferentes utilidades.

![](https://notionenespanol.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F25a5eea3-4a8c-4940-80be-f55fe868e14e%2FUntitled.png?table=block&id=4ec88f64-6cf2-462c-9f84-ef1f9e87ba4e&spaceId=e1aecfd5-e167-4495-af92-c53aabe7d985&width=860&userId=&cache=v2)

En el diagrama tenemos una entrada que se la conoce cómo standar input (stdin) y se describe con un 0 (file descriptors) entran en nuestro comando y tenemos dos opciones: que nos muestre todos nuestros directorios (standar output) o que nos salga un error (standar error). Ambas salidas se manejan con un file descriptor diferente.

Para poder hacer redirecciones usamos:

ls Pictures > archivo.txt: para redirigir algo usamos el símbolo mayor que y se guardara en el archivo que pongamos o creará uno si no existe. Este operador solo crea un archivo nuevo y sobre escribe el anterior.

ls Pictures >> archivos.txt: nos permite concatenar el contenido que tenemos dentro.

ls lsdafladsf > error.txt: nos dirigir lo que pusimos a un archivo de texto. Con esto solo redirigiremos el estándar Output.

ls lalsdflsd 2> error.txt: nos permite dirigir el estándar error.

ls adsfasdf > output.txt 2>&1: nos permite redirigir el estándar output y el estándar error. Nos permite redirigir el comando a un archivo output y dentro de el guardar el error.

> Esto nos sirve para redirigir todo lo que hemos trabajado y almacenarlos en un archivo para guardarlos. Es muy peligroso porque también puede reescribir sobre los archivos de nuestra computadora.

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

SUMMARY: dentro de la terminal tenemos dos procesos que se dan al utilizar comandos, las entradas (standard inputs) y las salidas (standard outputs). La terminal le asigna números a estos standard, conocidos como file descriptors estos son: stdin 0, stdout 1 y stderr 2. Con estos files description podemos hacer redirecciones que nos permitan almacenar nuestros outputs en archivos, para hacerlo tenemos: ls Documents > archivo.txt, ls Documents >> archivo.txt, ls archivo\_inexistente 2> archivo.txt y ls archivo\_inexistente > output.txt 2>&1.

![☝](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

ACTIONS NEEDED: practicar con las redirecciones.

Date: @18 de noviembre de 2021

¿Qué nos permite hacer el pipe operator?

¿Qué nos permite generar el pipe operator?

¿Qué comandos nos permite imprimir algo en la terminal?

¿Qué comando nos permite concatenar la salida los archivos de texto?

¿Qué símbolo usamos para utilizar pipe operators?

¿Qué comandos podemos usar con los pipe operator?

¿Qué comando nos permite mostrar un mensaje con una vaca?

¿Qué comando nos permite mostrar el texto con otro color?

![💡](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

El pipe operator nos permite ejecutar un comando que su standard output pase como standard input a otro comando y esto nos permitirá generar diferentes filtros, encadenamientos o funcionalidades que al final incluso pueden desencadenar en un archivo.

echo "Hola": genera un estándar output en la terminal de cualquier cosa que le escribamos.

cat: nos sirve para concatenar la salida de los archivos al poner el nombre de las archivos que queremos concatenar.

> El estándar input no se usa tanto en la terminal.

ls -lh | less: el pipe lo usamos con el signo | y con este podemos redirigir hacia otro lado.

ls -lh | tee output.txt | less: tee hace lo mismo que el signo <, con la diferencia que nos permite generar un nuevo archivo y luego verlo con less.

ls -lh | sort | tee output.txt | less: nos permite ordenar los archivos que tenemos dentro de un directorio para después guardarlo en un archivo.

cowsay: nos mostrara un mensaje con una vaca. Si queremos instalarlo debemos usar sudo apt install cowsay.

lolcat: nos mostrará el texto que tenemos en la terminal con colores sudo apt install lolcat.

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

SUMMARY: el pip operator | nos permite ejecutar un comando que su standard output pase como standard input de otro comando, esto nos sirve para generar filtros, encadenamientos o funcionalidades que pueden llegar a terminar en un archivo si así lo queremos. Algunos comandos que podemos añadir a nuestros pip operators son: tee para guardar un standard output en un archivo y sort para ordenar de forma alfabética algo. Otros comandos que se pueden usar dentro de la terminal son: echo para imprimir un mensaje en la consola, cat para concatenar en la vista de múltiples archivos en la consola, cowsay para imprimir mensajes en consola con imágenes de una vaca y lolcat para mostrar los mensajes de la terminal con colores.

![☝](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

ACTIONS NEEDED: practicar usando el pip operator.

Date: @18 de noviembre de 2021

¿Qué son los operadores de control?

¿De qué forma podemos correr los operadores de control?

¿Qué comandos usamos para ver fechas?

![💡](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

Los operadores de control son símbolos reservados por la terminal que nos permiten ejecutar más de un comando o encadenarlos. Podemos correrlos: sincronamente, asincronamente y con condicionales.

Uso de comandos de forma sincrona (uno después del otro):

ls; mkdir holi; cal: el comando "cal" nos permite acceder al calendario. Con el ";" podemos unir los comandos.

Uso de comandos de forma asíncrona (por cada comando ejecutado se abrirá una shell en segundo plano):

ls & date & cat: para ejecutar de forma síncrona usamos el signo "&". El comando "date" nos permite ver la fecha.

Uso de comandos de manera condicional (si se cumple un comando se ejecutará otro):

AND mkdir test && cd test: para ejecutar los condicionales utilizamos "&&"

OR mkdir test || cd test: para ejecutarlo usamos el signo "||".

> El comando echo nos imprime un texto en la terminal.

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

SUMMARY: los operadores de control son símbolos reservados por la terminal que nos permiten ejecutar más de un comando o encadenarlos. Estos operadores de control pueden correr de forma: sincrónica (;), asincrónica (&) y condicional (&&o ||).

![☝](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

ACTIONS NEEDED: practicar con operadores de control.

Date: @18 de noviembre de 2021

¿Dónde podemos encontrar los permisos que tenemos?

¿Qué tipo de archivo existen dentro de la terminal?

¿Que tipo de modos tenemos dentro de la terminal?

¿Qué tipo de permiso tiene los modos?

¿Cómo se activa los permisos?

¿Cuál es el orden que tienen 3 permisos?

¿Cómo se representa a la suma de números de los tres permisos?

¿Qué tipos de modos simbólicos tenemos?

¿Por qué los permisos dentro de la terminal se repiten tres veces?

Cuando listamos archivos con ls nos podemos dar cuenta que a un lado aparecen unos pequeños atributos, estos son los permisos que tiene cada archivo.

Dentro de los permisos lo primero que vamos a identificar son los tipos de archivos que tenemos, estos pueden ser:

![](https://notionenespanol.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fe616066c-3602-42d8-a25a-12a61ed68854%2FUntitled.png?table=block&id=bbf3453c-9a99-4cc1-9e50-7c32c4035928&spaceId=e1aecfd5-e167-4495-af92-c53aabe7d985&width=960&userId=&cache=v2)

Después del tipo de archivo que tengamos tendremos los tipos de modos, entre estos tenemos:

![](https://notionenespanol.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F0af7b649-0b0f-449e-b6ac-06aae6f2466e%2FUntitled.png?table=block&id=1605125d-5e90-4102-8d52-c8570780508a&spaceId=e1aecfd5-e167-4495-af92-c53aabe7d985&width=960&userId=&cache=v2)

Dueño: es la persona que creo el archivo.

Grupo: son archivos que son creados entre diferentes usuarios.

World: también conocidos como otros, es todo lo que no entra en la categoría ni de dueño ni de grupo.

Cada una de estas categorías puede tener 3 tipos de permiso:

![](https://notionenespanol.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F53dd3923-44e3-4534-9e2b-cdce8ed69bef%2FUntitled.png?table=block&id=234bc63c-5546-4fbc-b9c8-0ea3b55e8237&spaceId=e1aecfd5-e167-4495-af92-c53aabe7d985&width=1060&userId=&cache=v2)

Cuando asignamos un permiso se le asigna un 1 y cuando no lo asignamos se pone un 0.

Cómo para los permisos utilizamos tres números, podemos usar bits y con ello usar un sistema octal. Con este modo damos una ponderación de una base de 2 (4, 2, 1).

![](https://notionenespanol.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F30e72b0a-2b39-4ea5-b294-e8dba6ce902c%2FUntitled.png?table=block&id=e29769c4-8e3f-4a6e-af94-a5f1e7aacdde&spaceId=e1aecfd5-e167-4495-af92-c53aabe7d985&width=960&userId=&cache=v2)

El modo simbólico nos permite asignar permisos tácitamente desde la terminal con el comando change mood o change owner y esta asignación la podemos hacer por medio de letras.

![](https://notionenespanol.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fe4565355-cdd7-41e0-afa4-8fe1166c94ff%2FUntitled.png?table=block&id=b00b1c97-e796-4955-a0d5-6d5fa4e71e40&spaceId=e1aecfd5-e167-4495-af92-c53aabe7d985&width=960&userId=&cache=v2)

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

SUMMARY: dentro de la terminal podemos ver los permisos con los que contamos en todos nuestros archivos, estos salen en forma de letras en la parte izquierda al momento de hacer ls -l, estas letras representan: tipo de archivo (\-, d, l, b ), tipo de modo (dueño, grupo, world), tipos de permisos (r, w, x). Además de esto tenemos la opción de usar el modo simbólico, este nos permite asignar permisos tácticamente desde la terminal (u, g, o, a).

![☝](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

ACTIONS NEEDED: practicar revisando los permisos que tengo en mis archivos.

Date: @18 de noviembre de 2021

¿Cuál es el usuario que tiene privilegios para hacerlo todo dentro de nuestro computador?

Además de touch¿De qué otra forma podemos crear un nuevo archivo?

¿Cómo podemos abrir un procesador de texto sencillo desde la terminal?

¿Qué comando nos permite cambiar los permisos de un archivo?

¿Qué comandos nos ayudan a cambiar de usuarios?

En todos los sistemas existen diferentes tipos de usuarios y dentro de la terminal podemos cambiar entre los diferentes tipos de usuarios.

Existe un usuario muy conocido, el usuario "root". Este usuario tiene privilegios para hacer de todo, pero necesitamos aprender a manejarlo adecuadamente.

Podemos crear un archivo también con la tecla \> y poniendo el nombre que queremos que tenga.

chmod 755 mitexto.txt: significa change mod y usamos el sistema octal para asignar los permisos.

chmod u-r mitexto.txt: nos permite quitar permisos y aquí usamos el modo simbólico. Si queremos añadir permisos podemos cambiar el - por un +.

chmod u-x,go=w mitexto.txt: nos permite sobre escribir los permisos con el modo simbólico.

whoami: se traduce como quién soy yo y nos permite identificar con que usuario estamos.

id: nos ofrece el id de nuestro usuario.

su: significa switch usuer y nos permite cambiar de usuario. Podemos cambiar al usuario "root"

sudo: nos permite tener los permisos de administrador y hacer cosas en nombre del "root"

passwd: nos permite cambiar la contraseña de cualquier usuario.

> Una buena recomendación es que la contraseña del root sea diferente a la nuestra y que la mantengamos separada de nuestro usuario normal.

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

SUMMARY: dentro de Linux existe un usuario que puede realizar todo sin ningún problema dentro de nuestro computador, este es el usuario root. Para poder cambiar los permisos que tenemos dentro de la terminal usamos el comando chmod para cambiar podemos usar el sistema octal chmod 755 mitexto.txt o el modo simbólico chmod u-x,go=w mitexto.txt usaremos el que más sencillo nos resulte. Además dentro de la terminal tenemos comandos para administrar los usuarios: whoami (nos muestra el usuario que tenemos), id (nos muestra el id de nuestro usuario), su (nos permite cambiar entre usuarios), sudo (nos permite tener momentáneamente permiso de root) y passwd (nos pemrite cambiar la clave de nuestro usuarios). Una muy buena práctica es cambiar la clave de nuestro root y usuario, ya que por defecto son las mismas.

![☝](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

ACTIONS NEEDED: practicar los cambios de usuario.

Date: @18 de noviembre de 2021

¿Qué son los links simbólicos?

¿Cómo creamos un link simbólico?

¿Para qué nos sirven los links simbólicos?

¿Qué tipos de permisos tienen los links simbólicos?

¿Qué comando nos ayuda a ver todas las variables de entrono que tenemos?

¿Cómo podemos imprimir una variable de entorno?

¿Qué variables de entorno son importantes conocer?

¿Dónde encontramos nuestras variables de entorno?

¿Cómo podemos crear alias que se guarden en nuestro terminal permanentemente?

¿Cómo podemos agregar una nueva ruta a nuestro PATH?

Nuestra terminal tiene su propia configuración y a estas podemos acceder a través de las variables de entorno.

Estos son archivos que hacen referencia a un lugar y para usarlos necesitamos:

ln -s Documents/Dev Desarrollo: nos permite crearlos. Son como accesos directos desde la terminal. Los links simbólicos como tal no tienen permisos.

printenv: esta nos muestra todas las variables de entorno que tenemos guardadas.

echo $HOME: nos permite imprimir una variable de entorno al final se pone el nombre de la variable. Esta nos dice donde es el home de nuestro usuario.

$PATH: esta tiene todas las rutas de donde se encuentran los binarios que ejecuta nuestro sistema. Esto nos sirve para cuidar los repositorios que instalamos.

Modificar las variables de entorno:

Dentro del home vamos a encontrar el archivo .bashrc, este archivo lo que debemos modificar con un editor de texto. Dentro de este archivo encontramos nuestras variables y alias. Aquí podemos crear alias. También podemos crear o editar una variable de entorno, esto normalmente se escribe con mayúsculas.

bash: nos permite actualizar la terminal.

PATH=$PATH:/home/carlosqzh/bin: nos permite modificar la ruta de nuestro PATH para agregar una nueva ruta de binarios.

> Los alias es muy importante que tengamos mucho cuidado con como los asignamos.

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

SUMMARY: las variables de entorno nos permiten pasar información de forma simple de un programa a otro, si queremos ver todas las variables de entorno que tenemos en nuestro computador usamos printenv. Para acceder a nuestras variables de entorno podemos usar echo y la variable que se representa con $. Las dos variables de entorno más importantes para nosotros son HOME (nos indica donde esta el home de nuestro usuario) y PATH (muestra la ruta de todos nuestros binarios). Si queremos guardar un alias dentro de nuestra terminal para tenerlo siempre con nosotros debemos acceder a las variables de entorno .bash (Linux) y .zshrc (Mac) y dentro de ellas añadir nuestro alias. Otra cosa que podemos hacer en nuestra terminal es crear links simbólicos, estos nos permiten referenciar una dirección específica y llegar ahí rápidamente, para crearlos usamos: ln -s ruta/directorio nombre\_link\_simbolico.

![☝](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

ACTIONS NEEDED: crear nuevos alias para usar.

Date: @18 de noviembre de 2021

¿Para qué nos sirven los comandos de búsqueda?

¿Qué comandos de búsqueda tenemos?

¿Cómo podemos hacer mucho más potente nuestra búsqueda?

Estos nos ayudan a encontrar archivos o directorios.

Para implementarlos usamos:

which code: nos ayuda a encontrar la ruta de nuestros binarios añadiendo el nombre del programa que queremos buscar.

find ./ -name file: nos sirve para encontrar un archivo. Necesitamos poner la ruta donde iniciara a buscar. Name busca por el nombre de los archivos. Dentro de esta opción podemos usar wildcards.

find ./ -type fd -name Documents: la opción f nos permite buscar archivos y d directorios.

find ./ -size 20M: nos permite buscar por tamaños.

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

SUMMARY: la terminal nos ayuda a realizar búsquedas mucho más profundas y rápidas que usando una interfaz gráfica. Para buscar dentro de la terminal usamos: which para encontrar la dirección de los binarios, find ./ -name file para buscar un archivo por su nombre, find ./ -type fd -name Documents para buscar un archivo por su nombre y tipo, y find ./ -size 20M para buscar un archivo por tamaño.

![☝](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

ACTIONS NEEDED: practicar con búsquedas.

Date: @18 de noviembre de 2021

¿Para qué nos sirve grep?

¿De qué debemos tener cuidado con grep?

¿Qué opciones tenemos dentro de grep?

¿Qué comando nos ayuda a contar cuántas palabras hay?

¿Qué opciones tenemos con wc?

Este es uno de los comandos más útiles que tiene la terminal. grep nos permite encontrar coincidencias de una búsqueda dentro de un archivo de texto o cualquier texto.

grep Towers movies.csv: nos permite encontrar dentro de nuestro archivo la línea relacionada con lo que queremos buscar. En estas búsquedas importa mucho si es con minúscula y mayúscula (key sensitive).

grep -i the movies.csv: la i nos permite ignorar el key sensitive.

grep -c the movies.csv: la c nos muestra el número de ocurrencias que hay, es decir, cuantas veces aparece la palabra.

grep -ci the movies.csv: nos permite hacer lo mismo de arriba pero ignorando si son mayúsculas o minúsculas.

grep -v towers movies.csv: la v nos permite encontrar todas las palabras que no contienen la palabra que ponemos.

grep -v towers movies.csv > sintowers.txt: lo que hacemos aquí es guardar el resultado dentro de un archivo.

wc movies.csv: significa words count y nos permite contar cuántas palabras hay. Nos mostrará datos donde: el primero indica cuántas lineas tiene el archivo, la segunda cuántas letras o carcteres en general tiene y el último el número de bits.

wc -l movies.csv: nos permite contar solo el número de líneas.

wc -w movies.csv: nos permite contar solo las palabras.

wc -c movies.csv: nos permite ver solo el número de bits.

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

SUMMARY: grep es un comando muy usado dentro de la terminal, ya que nos permite realizar búsquedas avanzadas dentro de cualquier archivo que contenga texto. grep tiene varias opciones: \-i para ignorar el key sensitive, \-c para mostrar el número de concurrencias, \-ci para mostrar concurrencias ignorando el key sensitive, \-v mostrar las palabras que no contienen una palabra. Además de grep otro comando importante es wc o words count, este nos permite contar las palabras que hay dentro de un archivo, aquí también tenemos varias opciones: \-l nos da el número de líneas que hay, \-w nos da el número de palabras y \-c el número de bits.

![☝](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

ACTIONS NEEDED: practicar buscando con grep.

Date: @18 de noviembre de 2021

¿Qué comandos usamos para manejar nuestra red?

Para esto utilizaremos los comandos:

ifconfig: este nos muestra la información de nuestra red.

ping: esto nos dice si una página esta activa. Si nos responde constantemente con paquetes la página estará activa. Para salir de la ejecución aplastamos Ctrl + C.

curl: nos trae un archivo de manera de texto a través de la red.

curl www.google.com > index.html: nos permite guardar el texto de un nuevo archivo y guardar ese archivo.

wget: nos permite traer algo desde internet. Funciona similar a curl pero nos permite llevar directamente el documento a nuestra computadora.

traceroute: nos va a decir cuando visitamos un sito o dirección ip a que computadores y servidores nos vamos a conectar e intervienen en el proceso.

netstat -i: nos muestra de una forma más amigable nuestra red y su funcionamiento, la opción i nos muestra los dispositivos de red.

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

SUMMARY: dentro de la terminal tenemos comandos que nos ayudan a manejar las utilidades de red. Entre los comandos que tenemos están: ifconfig para ver nuestra información de red, ping para saber si una página esta activa, curl para traer un archivo en formato de texto desde la red, wget para traernos un archivo desde la red directamente y mejor organizado, traceroute para trazar el camino que hace nuestro ordenador para conectarnos a una página web y netstat -i para mostrar nuestra red de forma más amigable.

![☝](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

ACTIONS NEEDED: practicar con los comandos de red.

Date: @18 de noviembre de 2021

¿Qué son archivos comprimidos?

¿Qué comandos tenemos para comprimir archivos?

¿Qué comandos nos permiten descomprimir archivos?

Veremos cómo crear archivos comprimidos que encapsulan archivos o carpetas.

Para comprimir archivos usamos:

tar -cvf nombrearchivos.tar carpetaacomprimir: nos permite comprimir un archivo a .tar. La opción c comprime el archivo, v nos permite ver lo que hace y f nos lo guarda en un archivo.

tar -cvzf nombrearchivos.gz carpetaacomprimir: añadir la z nos permite comprimir en un formato de gip zip. Este sirve mucho para texto plano.

tar -xzvf nombrearchivocomprimirdo.tar.gz: nos permite descomprimir archivos .gz.

zip -r Nombrearchivo.zip archivoacomprimir: nos permite comprimir en formato .zip.

unzip nombredelarchivo.zip: nos permite descomprimir el archivo .zip.

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

SUMMARY: con la terminal podemos comprimir y descomprimir archivos fácilmente, para hacerlo usamos: tar -cvf archivo.tar directorio para comprimir a .tar, tar -cvzf archivo.gz directorio para comprimir a .gz y zip -r archivo.zip directorio para comprimir a .zip. Para descomprimir los archivos usamos: tar -xzvf archivo\_comprimido.tar para descomprimir en .tar y el mismo pero cambiando la extensión por .tar.gz para descomprimir en .gz y unzip archivo.zip para descomprimir archivos .zip.

![☝](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

ACTIONS NEEDED: practicar comprimiendo archivos.

Date: @18 de noviembre de 2021

¿Para qué nos sirve el manejo de procesos?

¿Qué comandos usamos para manejar procesos?

Para hacerlo necesitamos los siguientes comandos:

ps: nos muestra los procesos o comandos que están corriendo actualmente.

kill 435: nos permite finalizar el proceso al poner el id del proceso que queremos finalizar. Con esto podemos matar procesos.

top: nos muestra una vista donde se muestran los procesos que usan más recursos de nuestra computadora. Si aplastamos h nos dará una ventana de ayuda.

htop: es más avanzado que top.

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

SUMMARY: en algunas ocasiones tendremos inconvenientes con nuestros programas o procesos, para ello se utiliza el manejo de procesos, este nos permite finalizar con un tarea, similar al administrador de tareas de windows. Los comandos que usamos son: ps para ver los procesos y comandos que están corriendo, kill #PID para matar un proceso, top para mostrar una vista avanzada de los procesos que están corriendo y htop para tener una vista más avanzada que top.

![☝](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

ACTIONS NEEDED: practicar con el administrador de procesos.

Date: @18 de noviembre de 2021

¿Qué es background en la terminal?

¿Qué es foreground en la terminal?

¿Qué comandos nos ayudan a mover un proceso a background y foreground?

¿Para qué nos sirve llevar un proceso a background o foreground?

Como viste en la clase de procesos podemos correr de manera asíncrona comandos, y si estos no se completan quedarán activos dentro de los procesos de la terminal.

Cuando un proceso está en ejecución sin que sea mostrado en la terminal se dice que se está ejecutando en el background. Si se muestra la ejecución del comando dentro de la terminal se dice que está en el foreground. En esta clase aprenderás a cómo mover los procesos del background al foreground a tu voluntad, incluso a cómo suspenderlos.

¿Te acuerdas del truco que aprendimos para tener un editor de texto supersencillo en la terminal? Lo usaremos en esta ocasión. Imagina que queremos una nota desde la terminal y para eso usamos:

Nuestra terminal se verá de la siguiente manera, con el prompt esperando a que ingresemos texto.

![](https://notionenespanol.notion.site/image/https%3A%2F%2Fstatic.platzi.com%2Fmedia%2Fuser_upload%2F1-65129f78-f8b3-4db3-9485-96bb94e1481e.jpg?table=block&id=7ffbb4e6-7838-4e0a-81cc-7260f0e4ac43&spaceId=e1aecfd5-e167-4495-af92-c53aabe7d985&width=1060&userId=&cache=v2)

Podemos escribir algo y después terminar el input del texto con CTRL+D, pero en esta ocasión no haremos eso. Lo que queremos hacer será suspender el proceso, esto lo podemos hacer con CTRL+Z. El resultado que nos mostrará la terminal deberá ser uno donde nos indique la suspensión del comando cat.

![](https://notionenespanol.notion.site/image/https%3A%2F%2Fstatic.platzi.com%2Fmedia%2Fuser_upload%2F2-0906e521-894d-4c24-af55-9b5e119d5948.jpg?table=block&id=448b558a-f4f9-4a5b-9066-7c1046b45ce0&spaceId=e1aecfd5-e167-4495-af92-c53aabe7d985&width=1150&userId=&cache=v2)

Ahora hemos movido nuestro comando exitosamente al background de la terminal. Para consultar todos los procesos que tenemos en background podemos hacerlo con el comando jobs.

![](https://notionenespanol.notion.site/image/https%3A%2F%2Fstatic.platzi.com%2Fmedia%2Fuser_upload%2F3-75170eaf-c131-4c7d-accb-38747edf9e0a.jpg?table=block&id=91e7bfda-c425-4b7d-bd6b-b523994b877c&spaceId=e1aecfd5-e167-4495-af92-c53aabe7d985&width=1340&userId=&cache=v2)

A la izquierda aparece el número del trabajo ( ![⚠](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) cuidado que no es lo mismo que el process ID). Si queremos traer la ejecución de nuevo a la terminal, es decir, al foreground; debemos usar el comando fg y especificar qué número de trabajo queremos continuar. Para nuestro caso será el 1.

En caso de que estés usando ZSH como shell el formato para llamar el trabajo sería con un porcentaje. ZSH tiende a interpretar algunas cosas incluyendo las wildcards de manera diferente.

Una vez enviado al foreground veremos como se activa la ejecución del comando en la terminal y podremos seguir escribiendo nuestra nota. Recuerda que una vez terminemos de escribir presionamos CTRL+D para terminar el input y guardar.

![](https://notionenespanol.notion.site/image/https%3A%2F%2Fstatic.platzi.com%2Fmedia%2Fuser_upload%2F4-b554577a-0b6c-4bbf-85c9-48f33406dfcf.jpg?table=block&id=2bb69880-912c-4214-b111-84a94e73a316&spaceId=e1aecfd5-e167-4495-af92-c53aabe7d985&width=1630&userId=&cache=v2)

Cuando se guarda nuestra nota nos daremos cuenta de que el proceso por fin termina y si usamos jobs no nos mostrará ningún trabajo en background.

Otras formas de enviar al background

Existen otras formas de enviar comandos al background. La primera es usando el operador de control & al final de un comando. Este operador nos permite enviar de manera directa un proceso al background una vez ejecutado. Por ejemplo:

![](https://notionenespanol.notion.site/image/https%3A%2F%2Fstatic.platzi.com%2Fmedia%2Fuser_upload%2F5-02654ace-d20d-455f-b149-a6184ff820d0.jpg?table=block&id=09087170-54cb-443a-a72a-cf9c40f96910&spaceId=e1aecfd5-e167-4495-af92-c53aabe7d985&width=1340&userId=&cache=v2)

La segunda forma es con el comando bg. Este sirve de manera similar que fg solo que en vez de traerlo al foreground este lleva un trabajo al background. Por ejemplo:

Bien, la pregunta ahora es ¿Cómo usamos bg? Imagina que abrimos algún programa de interfaz gráfica desde la terminal. En mi caso abriré el navegador Google Chrome. Para hacerlo desde la terminal solo ejecuta:

Y verás como se ejecuta pero no nos deja hacer ninguna otra tarea ya que la ventana del navegador está abierta:

![](https://notionenespanol.notion.site/image/https%3A%2F%2Fstatic.platzi.com%2Fmedia%2Fuser_upload%2FScreenshot%2520from%25202021-04-23%252017-14-17-52751c95-ccb7-4377-a9b5-b12cd588aea5.jpg?table=block&id=5823a16b-f6d4-47dc-8035-160916998d83&spaceId=e1aecfd5-e167-4495-af92-c53aabe7d985&width=1340&userId=&cache=v2)

Para suspender el proceso como ya sabes lo hacemos con CTRL+Z y si revisamos con jobs veremos como el proceso se encuentra en pausa. En este caso la ventana del navegador que se abrió no nos dejará interactuar ni escribir en ella.

![](https://notionenespanol.notion.site/image/https%3A%2F%2Fstatic.platzi.com%2Fmedia%2Fuser_upload%2FScreenshot%2520from%25202021-04-23%252017-17-05-122a7d59-f9db-4946-b265-7a78e72adf25.jpg?table=block&id=33a1536f-e265-4ce0-8101-9ee8273d1207&spaceId=e1aecfd5-e167-4495-af92-c53aabe7d985&width=1440&userId=&cache=v2)

Como se ve en la imagen el navegador tiene el número de trabajo 1. Para dejar nuestro navegador corriendo y al mismo tiempo seguir trabajando en la terminal tenemos que reactivar este proceso y a la vez mandarlo al background. Para ello ejecutamos:

Con esto podremos ver como nuestro proceso de Google Chrome sigue corriendo en el background dejando la terminal disponible para nosotros.

![](https://notionenespanol.notion.site/image/https%3A%2F%2Fstatic.platzi.com%2Fmedia%2Fuser_upload%2FScreenshot%2520from%25202021-04-23%252017-22-26-91c8a1ff-3936-484b-a1d9-a46bdbf7498f.jpg?table=block&id=200a8cb3-44d6-4609-b196-6c793dac385a&spaceId=e1aecfd5-e167-4495-af92-c53aabe7d985&width=1340&userId=&cache=v2)

¡Genial! Con esto ya sabes cómo mover procesos dentro de la terminal del foreground al background. Esto es muy útil cuando solo tenemos una terminal y necesitamos ejecutar varios comandos en paralelo.

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

SUMMARY: existen dos conceptos importantes que debemos de conocer en la terminal: backgrounds (es cuando un proceso está en ejecución sin que sea mostrado en la terminal) y foregrounds (es cuando se muestra la ejecución del comando dentro de la terminal). Para conocer el estado de nuestros procesos usamos jobs y para mover nuestros programas entre foreground y background usamos: fg 1, bg 1 y comando & (envía directamente al background una vez ejecutado).

![☝](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

ACTIONS NEEDED: practicar con procesos en foreground y background.

Date: @19 de noviembre de 2021

¿Cómo podemos tener un editor de texto en la terminal?

¿Cómo crear un archivo con vim?

¿Qué opciones tenemos dentro de vim?

Hay diferentes opciones para editar texto dentro de la terminal. El más común en VIM.

vim: nos permite iniciar VIM en nuestra terminal. Para salir usamos :q.

vim index.html: nos permite crear un archivo de texto. Vim tiene dos modos, para ingresar al modo de inserción debemos aplastar la tecla i.

Para salir del modo inserción usamos la tecla Esc.

Para buscar dentro del archivo podemos usar /.

Para eliminar una línea usamos las teclas 1.

Para guardar y salir usamos :wq.

Para forzar la salida usamos :wq!.

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

SUMMARY: dentro de nuestra terminal podemos usar editores de texto, el más conocido es vim y para usarlo solo debemos de escribirlo tal cual en la terminal. Dentro de vim tenemos varias opciones: :q para salir, :w para guardar, :wq para guardar y salir, :wq! para forzar la salida, i para escribir dentro de nuestros archivos, Esc para entrar a nuestros archivos, /palabra nos permite encontrar coincidencias y 1 al presionarla dos veces en el modo normal nos permite eliminar líneas de código.

![☝](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

ACTIONS NEEDED: investigar cómo es programar con vim.

Date: @19 de noviembre de 2021

¿Por qué deberíamos personalizar nuestra terminal?

¿Qué comando nos permite cambiar nuestra terminal por defecto?

¿Qué comando nos permite recargar nuestra shell?

Para hacerlo necesitamos:

Instalar un emulador de terminal llamado Tilix (si estamos en WSL o Mac podemos usar el del sistema)

Instalar una Z shell sudo apt install zsh.

Convertir a Zsh nuestra shell por defecto chsh -s $(which zsh)

Reiniciar nuestra terminal y elegir la opción 0

Instalar un tema (en esta caso power level 10k)

Cambiar dentro de nuestro .zshrc el tema que viene por defecto

Descargar las fuentes que necesitamos para le terminal e instalarlas

Dentro de la terminal elegir la fuente que instalamos

Recargar nuestra shell con zsh

Configurar con los parámetros que más nos gusta.

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

SUMMARY: es muy importante que nos sintamos lo más cómodos posibles dentro de la terminal, ya que será un lugar donde pasaremos largo rato. Por ello si tenemos la opción de personalizarla debemos de usarla.

![☝](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

ACTIONS NEEDED: investigar más temas.

![](https://notionenespanol.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Ff3db8239-44b0-4735-8bab-6103573b966d%2Fplantilla_Hoja_comandos_.jpg?table=block&id=9c28cebe-d664-435a-9d93-bb74e9e11ec7&spaceId=e1aecfd5-e167-4495-af92-c53aabe7d985&width=2000&userId=&cache=v2)

![](https://notionenespanol.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F1865e42a-4720-4ddb-bf0c-5da78296dd87%2FUntitled.png?table=block&id=09de0c8e-c05a-4d5e-9951-7a8be4efdd1d&spaceId=e1aecfd5-e167-4495-af92-c53aabe7d985&width=960&userId=&cache=v2)

![](https://notionenespanol.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fd9d1f4ea-ebc1-4129-b815-3d21cffa1012%2FUntitled.png?table=block&id=533b3368-7c78-4c81-8598-931c89e927ff&spaceId=e1aecfd5-e167-4495-af92-c53aabe7d985&width=960&userId=&cache=v2)

![](https://notionenespanol.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F6a1acabb-1faa-42d4-b449-667084733401%2FUntitled.png?table=block&id=ac5b7809-7131-4fbb-afdd-d3716cbff907&spaceId=e1aecfd5-e167-4495-af92-c53aabe7d985&width=960&userId=&cache=v2)