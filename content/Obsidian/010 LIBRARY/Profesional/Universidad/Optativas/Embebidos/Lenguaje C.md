
Se utiliza mucho en sistemas embebidos porque el codigo que genera en ensamblador es muy parecido al que generariamos nosotros, y quizas mejor, aparte tiene la ventaja que es comun para todos los embebidos.
## Tipo de dato INT
- El tipo de datos int permite la definicion de un numero entero con signo
- El tamanio peude cambiar segun la plataforma
- Para evitar problemas con esto en C90 se crea la biblioteca *stdint.h*
![[Pasted image 20230322122725.png]]
- La recomendacion
	- Las variables de lazo son de tipo int
	- Las otras variables la usamos para donde enserio necesitamos un tamanio fijo(cuando trabajamos la memoria)
### Definicion y declaracion
La declaracion importa al compilador que la variable existe, es un indentificador
La definicion se le pide al compilador la construccion de un recurso represntado por un identificador
Para usar un recurso necesitamos declararlo, no definirlo, esto lo haremos en algun momento pero no ahce falta que sea desde el inicio
![[Pasted image 20230322123132.png]]
## Directivas
#### const
Declara una variable como constante
- Califica a un parametro par impedir que el mismo sea alterado dentro de una funcion
- Tambien califica a un puntero para saber si se puede cambiar la memoria apuntada por dicho puntero
- En los sistemas embebidos implica ademas que la misma se ubica en flash y no en RAM
##### Declaracion
![[Pasted image 20230322123654.png]]
- En el segundo caso estamos diciendo que lo constante es lo apuntado
- En la primera lo constante es donde estamos apuntado, no el valor de lo apuntado
- En el tercero ambas cosas son constantes
##### Variables y constantes
Si pido una constante y paso una variable no hay drama
Pero si pido una variable y paso una constante puede generar problema
- Si no modificamos la variable tenemos que calificarla como const
	- Si la modificamos no
![[Pasted image 20230322143822.png]]

#### volatile
Avisa que una variable puede cambiar sin el control del codigo que se esta ejecutando.
- Desactiva la optimizacion de codigo para la variable
- Se lee el valor de memoria en cada acceso
- Se aplica a variables globales o locales


#### static
En variables locales
- Conserva el valor entre llamado
- Las convierte en variables globales
- Sin visibildiad para el resto del codigo
En variables globales y funcion
- Vuelven privada del archivo la funcion o variables
- Impide el uso extern en otro modulo
- Sin visibilidad para el resto del proyecto

## Punteros
En C, un puntero es una variable que almacena la dirección de memoria de otra variable. Los punteros se utilizan para acceder y manipular datos en la memoria de un programa. A continuación, se muestran algunas de las diferentes formas en que se pueden utilizar los punteros en C:

1.  Declaración de un puntero: Para declarar un puntero en C, se utiliza el operador asterisco (\*). Por ejemplo, la siguiente declaración define un puntero a un entero:
``` C
int *p;
```
2.  Asignación de un puntero: Para asignar una dirección de memoria a un puntero, se utiliza el operador de dirección (&). Por ejemplo:
``` C
int x = 10;
int *p = &x;
```
En este ejemplo, el puntero "p" apunta a la dirección de memoria de la variable "x".
3.  Acceder al valor apuntado por un puntero: Para acceder al valor apuntado por un puntero, se utiliza el operador de indirección (\*). Por ejemplo:
``` C
int x = 10;
int *p = &x; 
printf("%d\n", *p);// imprime 10
```
En este ejemplo, el operador de indirección se utiliza para obtener el valor almacenado en la dirección de memoria apuntada por el puntero "p".
4.  Aritmética de punteros: Los punteros también se pueden utilizar en operaciones aritméticas para acceder a diferentes posiciones de memoria. Por ejemplo:
``` C
int arr[5] = {1, 2, 3, 4, 5};
int *p = arr; 
printf("%d\n", *(p + 2)); // imprime 3
```
En este ejemplo, el puntero "p" apunta al inicio del arreglo "arr". El operador de indirección junto con la aritmética de punteros se utiliza para acceder al tercer elemento del arreglo.
5.  Punteros a funciones: En C, también se pueden utilizar punteros para almacenar direcciones de funciones. Por ejemplo:
``` C
int suma(int a, int b) {     
return a + b;
} 
int (*p)(int, int);
p = &suma;
printf("%d\n", (*p)(2, 3)); // imprime 5
```
En este ejemplo, se declara un puntero a una función que toma dos argumentos enteros y devuelve un entero. Luego, el puntero se asigna a la dirección de la función "suma". Finalmente, el operador de indirección junto con la sintaxis de llamada de función se utiliza para invocar la función a través del puntero.
Estas son solo algunas de las formas en que se pueden utilizar los punteros en C. Los punteros son una herramienta poderosa y versátil en C, pero también requieren precaución y atención a la gestión de la memoria para evitar errores y problemas de seguridad.


## Funciones
Las variables a funciones se mandan por valores, entonces si declaramos una variable en ella el valor que entra a la funcion es el valor que tiene ese variable en ese moemento, no la direccion de memoria que esta misma tiene.
Para mandar la direccion de memoria, osea que si queremos manipular una variable, necesitamos mandarla por puntero, aqui se envia el espacio de memoria
- Cuando enviamos un vector, esto se manejan por direccion de memoria, este tiene la direccion de donde comienza el vector y hasta donde va

## Estructuras
Son tipos de datos compuesto formados por campos
- Siempre ocupa direcciones de memoria consecutivos
- El espacio ocupado por la estructura puede ser mayor que la suma de todos los campos
	- Esto se debe a que los espacio de memoria estan alineados
	- Entonces para que no se llene de espacio vacios, hay que acomodar desde el mas grande al mas chico
- Se utiliza para hacer POO
### Declaracion 
#### Tipo 1
``` C
struct Persona_a{
	char nombre[50];
	int edad;
	float altura;
};
```
En este caso estamos declarando una estructura llamada Persona_a con los atributos de nombre, edad y altura.
*Inicializacion de una estructura*
``` C
struct persona p = {"Juan", 30, 1.75};
```

Tipo 1:
``` C
typedef struct Persona_a{
	char nombre[50];
	int edad;
	float altura;
} *persona_t;
```
Tipo 2:
``` C
typedef struct {
	char nombre[50];
	int edad;
	float altura;
} *persona_t;
```
Tipo 3:
``` C
typedef struct Persona_a{
	char nombre[50];
	int edad;
	float altura;
} persona_t;
```
*Consultar TINI a las 12*

### Formato Json
JSON (JavaScript Object Notation) es un formato ligero de intercambio de datos que se utiliza para transmitir información estructurada entre diferentes aplicaciones. Es muy común en la programación web porque es fácil de leer y escribir, y puede ser utilizado por muchos lenguajes de programación diferentes.
La sintaxis de JSON es muy parecida a la de los objetos de JavaScript, y se compone de pares de nombre-valor, separados por comas, y encerrados entre llaves {}. Los valores pueden ser cadenas de texto, números, booleanos, objetos o arreglos.
Por ejemplo, este es un objeto JSON que representa información sobre un libro:


``` C

`{    "titulo": "El gran Gatsby",    "autor": "F. Scott Fitzgerald",    "anioPublicacion": 1925,    "generos": ["Ficción", "Novela"],    "editorial": {       "nombre": "Charles Scribner's Sons",       "ciudad": "Nueva York"    } }`
```

En este ejemplo, el objeto tiene cinco propiedades: "titulo", "autor", "anioPublicacion", "generos" y "editorial". "titulo" y "autor" son cadenas de texto, "anioPublicacion" es un número entero, "generos" es un arreglo de cadenas de texto, y "editorial" es un objeto anidado que tiene dos propiedades: "nombre" y "ciudad".


## Acceso a los dispositivos del micro
Se declara una estructura donde cada campo corresponde a un registro del dispositivo
- Se declara un punte a esa estructura
- Se declara una constante como un cast al puntero de la direccion de memoria base de dispositivo

## Manejo de variables en memoria
Hay que tener en cuenta que cada posicion de la memoria tiene 4 bytes, entonces cuando queremos almacenar un dato, a este lo podemos hacer a multiplos de 4 si nuestro dato es una palabra, ahora si es media palabra se lo puede agregar en numero pares.


### Operador a nivel bits
![[Pasted image 20230322125127.png]]
![[Pasted image 20230322125259.png]]
### Mascaras de bits
Verificar el estado de un bit en una variable
![[Pasted image 20230322125359.png]]

### Lenguaje en C90
Primera version estandar. La usaremos para evitar tener problemas
- 100% compatible con C89 y anteriores
- Solo soporta comentarios con /* * /.
- No soporta tipos de 64 bits.
- Definicion de variables al inicio de un bloque
- No se soporta las directivas *inline*
- Es el minimo comun denominar.

### Maquina de estados finitos en codigo
Ejemplo que implementaremos
![[Pasted image 20230322154900.png]]
#### 1. Estructura de datos
Se genera una estructura con los estados de la maquina de estado finito.
![[Pasted image 20230322155118.png]]
#### 2.Implementacion
Necesitamos un codigo que transicione de estado dependiendo de lo que hace.
![[Pasted image 20230322155041.png]]



### Grabacion y depuracion
Cuando se compila un proyecto para un sistema embebido es una imagen con el contenido de la memoria flash.
- Para ello el procesador dispone de un modulo destinado a comunicarse con las herramientas de desarrollo
![[Pasted image 20230322155815.png|500]]



