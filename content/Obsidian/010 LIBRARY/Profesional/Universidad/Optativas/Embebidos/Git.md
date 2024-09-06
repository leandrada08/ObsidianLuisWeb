## Introduccion
Permite llevar el control de los cambios que se hacen a archivos y carpetas. Es una herramienta para control de versiones diseniada por linux Torvald
- Almacena las versiones como una imagen instantanea del sistema de archivo
## Areas de GIT
Un repositorio GIT tiene diferentes areas de trabajo
- *Working Directory:* Nuestra carpeta de trabajo
- *Staging Area:* En esta area esta los cambios que quiero hacer
- *Repositorio:* Se copia los datos que tenemos en nuestra carpeta de trabajo
![[Pasted image 20230317104647.png|500]]
## Estados de un archivo
Cada archivo puede estar en uno de cuatro posibles estados
- *Untracked:* Recien creado
- *Unmodified:* Sin modificar
- *Modified:* Modificado
- *Staged:* Guardado
![[Pasted image 20230317104741.png|500]]
## Conceptos claves
-   *Repositorio:* Es el lugar donde se almacena todo el código fuente de un proyecto.
-   *Commit:* Es una instantánea del código fuente en un punto específico del tiempo, que se almacena en el repositorio.
-   *Branch(Rama):* Es una versión paralela del código fuente principal que se utiliza para trabajar en nuevas características o arreglar errores sin afectar la versión principal.
-   *Merge:* Es la acción de combinar cambios realizados en una rama con otra rama, o con la versión principal.
-   *Remote:* Es una copia del repositorio en otro lugar, como un servidor o un servicio en línea, que permite compartir y colaborar en el código fuente.
-   *Clone:* Es la acción de copiar un repositorio remoto en la máquina local.
-   *Fork:* Es la acción de hacer una copia completa de un repositorio remoto en una cuenta de usuario diferente, lo que permite que otras personas contribuyan al proyecto.
-   *Pull:* Es la acción de descargar cambios desde un repositorio remoto al repositorio local.
-   *Push:* Es la acción de enviar cambios desde el repositorio local al repositorio remoto.
-   *Conflict:* Es la situación en la que los cambios realizados en una rama no se pueden combinar automáticamente con otra rama debido a cambios conflictivos.
-   *Tag:* Es una forma de etiquetar un commit para marcar un hito importante en el proyecto, como un lanzamiento o una versión específica.
-   *Stash:* Es la acción de guardar temporalmente cambios sin comprometerlos, lo que permite trabajar en una tarea diferente sin perder cambios.
-   *Cherry-pick:* Es la acción de seleccionar y aplicar un conjunto específico de cambios de una rama a otra rama.
-   *Rebase:* Es la acción de cambiar la base de una rama para que esté basada en otra rama, lo que permite mantener el historial de cambios lineal y ordenado

### Commit
Es una instantánea del código fuente en un punto específico del tiempo, que se almacena en el repositorio.
- Un commit tiene un enlance a su predecesor
	- Un predecesor contiene la version anterior del remositorio
![[Pasted image 20230317115602.png|500]]
#### Ramas
Son estas referencias moviles con nombre a un commit
![[Pasted image 20230317115648.png|350]]
*HEAD:* es un puntero especial que indica la última confirmación (commit) en la rama (branch) actual en la que se encuentra el usuario. En otras palabras, HEAD es un puntero que apunta al commit más reciente de la rama actual. Cuando se crea un nuevo commit, el puntero HEAD se actualiza para apuntar a ese nuevo commit, y se convierte en el commit más reciente de la rama actual. También es posible tener HEAD apuntando directamente a un commit específico en lugar de a una rama.
Para crear una nueva rama simplemente tenemos que agregar una nueva etiqueta



## Como usar GIT
1.  *Instalar Git:* Si aún no tienes Git instalado en tu computadora, debes descargar e instalar Git en tu sistema operativo. Puedes encontrar la descarga en el sitio web oficial de Git: [https://git-scm.com/downloads](https://git-scm.com/downloads)
2. *Configuro* los valores globales de nombres y correo electronico
``` C
git config --global user.name "You Name"
git config --global user.email "youremail@yourdomain.com"
git config --list
```
3.  *Crear un repositorio:* Para empezar a usar Git, debes crear un repositorio. Puedes crear un nuevo repositorio vacío en tu computadora con el siguiente comando en la terminal:
    `git init`
3.  *Agregar archivos al repositorio:* Una vez que has creado el repositorio, puedes empezar a agregar archivos al mismo. Puedes agregar un archivo específico al repositorio con el siguiente comando:
    `git add <nombre del archivo>`
    En este caso lo que estamos haciendo en agregar el archivo al area de preparacion (staging) ara el siguiente commit
    También puedes agregar todos los archivos nuevos o modificados en una sola vez con el siguiente comando:
    `git add .`
4.  *Confirmar cambios:* Después de agregar archivos al repositorio, debes confirmar los cambios con un mensaje descriptivo. Puedes hacerlo con el siguiente comando:
    `git commit -m "mensaje descriptivo"`
5.  *Verificar estado del repositorio:* Puedes verificar el estado del repositorio en cualquier momento con el siguiente comando:
    `git status`
    
6.  *Subir cambios al repositorio remoto:* Si deseas compartir tus cambios con otros colaboradores en el proyecto, debes subir tus cambios al repositorio remoto. Para ello, debes agregar un repositorio remoto con el siguiente comando:
    `git remote add origin <url del repositorio>`
    Y luego subir tus cambios al repositorio remoto con el siguiente comando:
    `git push -u origin master`
    
7.  *Obtener cambios del repositorio remoto:* Si otros colaboradores han realizado cambios en el repositorio remoto, debes obtener los cambios y actualizar tu repositorio local con el siguiente comando:
    `git pull`

### Otras funciones importantes
-  `git clone <url>`: Clona un repositorio Git existente en una nueva carpeta.
-  `git log`: Muestra un registro de todos los commits que se han hecho en el repositorio.
-  `git checkout <rama>`: Cambia a una rama específica en el repositorio.
-  `git merge <rama>`: Fusiona los cambios de una rama específica en la rama actual.
-  `git remote`: Muestra una lista de los repositorios remotos asociados con el repositorio local.
-  `git fetch`: Descarga los cambios remotos al repositorio local, pero no los fusiona con la rama actual.
-  `git diff`: Muestra las diferencias entre dos commits o entre el estado actual y un commit anterior.
-  `git tag`: Lista todas las etiquetas (tags) existentes en el repositorio.
-  `git show <commit>`: Muestra información detallada sobre un commit específico.
-  `git reset <archivo>`: Quita un archivo del área de preparación (staging) y lo deshace de los cambios que se hayan hecho.
-  `git revert <commit>`: Crea un nuevo commit que revierte los cambios introducidos en un commit específico.
-  `git stash`: Guarda temporalmente los cambios actuales en una pila (stack) de cambios y los oculta del historial del repositorio.
-  `git cherry-pick <commit>`: Copia un commit específico de una rama y lo aplica en la rama actual.
-  `git rm <archivo>`: Elimina un archivo del repositorio y prepara el cambio para ser commiteado.

## El archivo
###  .gitignore
El archivo .gitignore en Git es un archivo que se utiliza para especificar los archivos o directorios que Git debe ignorar al realizar seguimiento de cambios en un proyecto.
Esto es útil cuando se trabaja en un proyecto de software y hay ciertos archivos o directorios que no deben ser incluidos en el repositorio Git. Al agregar esos archivos o directorios al archivo .gitignore, Git los ignorará y no los incluirá en el historial de cambios.
Algunos ejemplos de patrones comunes que se pueden agregar a un archivo ".gitignore" son:
-   Archivos de compilación generados por el lenguaje de programación que estés utilizando (por ejemplo, archivos .class para Java, archivos .pyc para Python).
-   Archivos de configuración específicos de la máquina, como archivos de registro o archivos de configuración de IDE.
-   Archivos de salida generados por herramientas o scripts de construcción, como archivos de informe o de registro.
-   Directorios y archivos que contienen datos confidenciales o información de acceso, como archivos de credenciales, claves privadas, archivos de configuración con contraseñas, entre otros.
-   Archivos y directorios que contienen dependencias de terceros, ya que estos archivos no necesitan ser controlados de versiones ya que pueden ser descargados en tiempo de compilación o ejecución.
Es importante que cada proyecto tenga su propio archivo ".gitignore" adaptado a sus necesidades específicas. Además, asegúrate de revisar regularmente el archivo ".gitignore" para asegurarte de que no estés ignorando accidentalmente archivos importantes o incluyendo archivos que no deberían estar en el control de versiones.
#### Pasos a seguir para crear un gitignore
Se pueden seguir estos pasos para crear un archivo ".gitignore":
1.  Abre un editor de texto y crea un nuevo archivo llamado ".gitignore" en la raíz del repositorio Git.
2.  Agrega las siguientes líneas al archivo ".gitignore":
```
*.html *.java
mi_carpeta/*
```

Esto indica a Git que ignore todos los archivos con la extensión ".html" y ".java". Al igual que estoy omitiendo todos los archivos de la carpaeta mi carpeta
- El asterisco (_) es un comodín que representa cualquier cantidad de caracteres, lo que significa que se puede utilizar para coincidir con cualquier archivo que tenga una determinada extensión o nombre. En el caso del ejemplo mencionado anteriormente, el patrón "_.html" significa "ignorar cualquier archivo con la extensión .html", y el patrón "*.java" significa "ignorar cualquier archivo con la extensión .java".*
Si no se utiliza el asterisco en las líneas del archivo ".gitignore", Git interpretará la línea de manera literal y no como un patrón, lo que significa que solo ignorará archivos que tengan el nombre exacto que se especificó en la línea. Esto no es lo que generalmente se quiere lograr al utilizar un archivo ".gitignore", ya que el objetivo es ignorar todos los archivos de un cierto tipo, independientemente de su nombre exacto. Por lo tanto, es importante incluir el asterisco en las líneas de patrón del archivo ".gitignore".
3.  Guarda el archivo ".gitignore" y ciérralo.
4.  Asegúrate de agregar el archivo ".gitignore" al control de versiones de Git para que otros miembros del equipo también puedan ignorar estos tipos de archivo.
Una vez que se han realizado estos pasos, Git ignorará automáticamente los archivos con las extensiones ".html" y ".java" en el repositorio, lo que significa que no se rastrearán ni se incluirán en los commits de Git.
### .gitkeep
El archivo ".gitkeep" es un archivo vacío que se utiliza en proyectos de Git para mantener vacías las carpetas vacías en el repositorio Git.Como git no almacena carpetas sino archivos, se utiliza un archivo vacío con nombre .gitkeep para forzar la creación de una carpeta.
En Git, normalmente solo se rastrean y almacenan en el repositorio los archivos que tienen contenido. Sin embargo, a veces es necesario mantener una carpeta vacía en el repositorio por razones de organización, estructura de directorios, etc. Para hacerlo, se puede crear un archivo vacío llamado ".gitkeep" en la carpeta vacía.
La razón por la que se utiliza el nombre ".gitkeep" es porque Git ignora por defecto los archivos y carpetas que comienzan con un punto ("."). De esta manera, el archivo ".gitkeep" se considera como un archivo oculto, pero aún así se incluirá en el repositorio Git, permitiendo que la carpeta vacía se mantenga en su lugar.
Es importante tener en cuenta que el archivo ".gitkeep" no tiene una funcionalidad especial dentro de Git, es simplemente una convención de nombres utilizada por algunos proyectos para indicar que una carpeta vacía debe ser mantenida en el repositorio Git.


## Buenas practicas
- Necesitamos que los cambios sean significativos para poder analizar los cambios en el codigo.
	- Algo muy importante para esto es que hay que evitar cambios de formato
	- Por eso son importante los formateadores de codigo
### Hooks de git
Los hooks de Git son scripts que se ejecutan automáticamente en determinados momentos del flujo de trabajo de Git. Estos scripts se pueden usar para automatizar tareas, realizar verificaciones de calidad, ejecutar pruebas, enviar notificaciones y realizar otras acciones personalizadas.
Los hooks de Git están ubicados en la carpeta ".git/hooks" dentro del repositorio Git local. Estos scripts pueden ser escritos en cualquier lenguaje de programación, como Bash, Python, Perl, Ruby, etc.
Git tiene una variedad de hooks que se pueden utilizar en diferentes momentos del ciclo de vida de un commit, como:
-   pre-commit: se ejecuta antes de confirmar los cambios en un commit.
-   prepare-commit-msg: se ejecuta después de que se haya escrito un mensaje de confirmación, pero antes de que se abra el editor para editarlo.
-   post-commit: se ejecuta después de que se haya confirmado los cambios en un commit.
-   pre-push: se ejecuta antes de enviar los cambios al repositorio remoto.
-   post-receive: se ejecuta después de que los cambios han sido recibidos en el repositorio remoto.
Existen muchos otros hooks disponibles en Git, y los desarrolladores pueden personalizarlos para ajustarse a sus necesidades específicas. Los hooks pueden ser útiles para mantener la consistencia y calidad del código, realizar tareas de automatización de pruebas y notificaciones, y personalizar el flujo de trabajo de Git para satisfacer las necesidades de un proyecto específico.



#### Consultas
- Como organizar tus carpetas en la pagina de git
- Como salir de carpetas viejas







