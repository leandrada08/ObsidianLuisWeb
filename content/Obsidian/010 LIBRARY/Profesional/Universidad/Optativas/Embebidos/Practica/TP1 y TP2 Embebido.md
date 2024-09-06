
# TP1 y TP2
- Sizeof solo es un codigo de compilador y no de instruccion, por lo tanto solo se lo puede usar si el valor no estara definido por el usuario si no por nosotros.
- Las variables locales se almacenan en pila osea en ram
- Para definir variables globales tengo que hacerlo fuera del int main.
	- Si esta sera una constante es importante que la defina con const, para que no pase a ram y se quede solo en flash
- Si quiere guardar en flash un valor adentro de main tengo que hacerlo con static const y definirla si o si
``` C
const int a=3; /* Defino una variable global que se guardara en flash*/

int mains(void){
	static const b=5; //Defino una variable global adentro del main
}
```


``` C
static int SerializarCadena(){
	return 0;

}

static int SerializarCadena(){
	return 0;

}


int Serializar(const alumno_t alumno, char cadena[],uint32_t espacio){
	return 0;

}

```


---

#### snprintf()
La función `snprintf()` es una función de la biblioteca estándar de C que se utiliza para escribir una cadena de caracteres formateada en un buffer de caracteres
. Esta función es similar a la función `printf()`, pero en lugar de escribir en la consola, escribe en una cadena de caracteres.
La sintaxis de la función `snprintf()` es la siguiente:

```cpp
int snprintf(char *buffer, size_t n, const char *format, ...);
```
Donde:
-   `buffer`: Es el buffer de caracteres donde se escribirá la cadena de caracteres formateada.
-   `n`: Es el tamaño máximo del buffer de caracteres.
-   `format`: Es la cadena de formato que especifica cómo se deben formatear los argumentos adicionales.
-   `...`: Son los argumentos adicionales que se deben formatear.
La función `snprintf()` devuelve el número de caracteres que se han escrito en el buffer de caracteres, sin contar el carácter nulo final. Si el número de caracteres que se han escrito es mayor o igual a `n`, entonces la cadena de caracteres resultante se truncará para que se ajuste al tamaño del buffer o devolvera -1
``` C
snprintf(cadena, espacio, "\"%s\":\"%s\",",campo,valor)
/* snprintf fserializarunciona igual que printf, en este caso, lo que hace es agarra una cadena con un espacio dado, y muestra el campo dado y el valor dado

```
---

- Los vectores y los punteros es lo mismo porque el puntero es un espacio de memoria, que comience desde ese punto y el vector tambie, ya que lo que guardamos es el espacio de memoria
- Mientras mas identado esta el codigo es malo, esto complica la compilacion, por lo tanto  hay que buscar que nuestro codigo basicamente sea sin identados y cada que necesitemos usar muchas sentencias de control(if, while, etc) usar funciones
- Para definir una cadena de caracteres, lo hago de la siguiente forma, donde lo primero que debo poner es el nombre del vector, luego el valor que el daremos a cada componente del vector y al final el tamanio del vector
``` C
strncpy(yo.apellido, "Andrada", sizeof(yo.apellido));
```
## Guarda
``` C
#ifndef __BAT_H__ //Directiva al preprocesador
MuchasCosas
#endif // Finalizo la difectiva al propocesador
```
La guarda es una directiva al preprocesador que le indica si ejecuta cierto codigo o no, basicamente este codigo que se analizara si se ejecuta es todo lo que esta entre #ifndef y #endif

