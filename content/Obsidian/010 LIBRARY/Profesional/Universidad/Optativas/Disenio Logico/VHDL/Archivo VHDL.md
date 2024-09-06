## Definicion
Estructura de datos utilizadas para representar informacion almacenada en memoria. En VHDL, los archivos se utilizan principalmente para la simulacion y verificacion de diseños digitales.
![[Pasted image 20230606090020.png|300]]

## Caracteristicas de archivos
- Por defecto se almacenan en ASCII
- Para almacenar en formato texto se necesita emplear el paquete *textio* de la libreria *std*
- Para utilizar el archivo se necesita:
	- *Definir el tipo de archivo:* Especifica el tipo de datos que se almacena en el objeto
	- *Declarar el objeto archivo:* Las operaciones se realizan especificando el identificador con el que se declara el objeto
### Definicion del tipo de archivo
``` VHDL
type identificador_tipo is file of tipo_objeto;
```
*Tipo_objeto:* Tipo de datos que se guardan en el archivo
*Identificador: del tipo* Nombre que le daremos a este tipo de archivo

### Declaracion del objeto archivo
``` VHDL
file identificador:identificador_tipo[open tipo_acceso][is nombre];
```
*Idenficador:* Handler del fichero
*Tipo_acceso:* Mode en que se esta por usar el archivo(lectura, escritura). Este peude ser
- read_mode
- write_mode
- append_mode
*Nombre:* Nombre fisico del fichero. Se pone la ruta con el nombre del archivo o directamente solo el nombre del archivo y se guarda en la carpeta de trabajo

### Ejemplo completo
![[Pasted image 20230606093052.png|600]]

## Paquete TEXTIO
El paquete de *textio* de la libreria std contiene tipos fichero y subprogramas para gestionar ficheros de texto con formato. El tipo de fichero definido en *textio* es TEXT.
``` VHDL
use std.textio.all;
...
file estimulos: text open READ_MODE is "signalin.txt"
```
Las operaciones de lectura o escritura se realizan a traves de un buffer intermedio de tipo *LINE*. Es un puntero a una cadena de caracteres *STRING*

![[Pasted image 20230606095020.png|600]]