# TP3
``` C
//En .h definimos de esta manera un objeto
typedef struct alumno_s *alumno_t; //!< alumno_t es un punte a alumno_s


//En .c creamos el objeto
//Creamos una funcion para crear un alumno
// Basicamente creamos el objeto, en este caso nos devuelve un puntero
// Hay que pasarle el nombre el apellido y el documento
alumno_t CrearAlumno(char * apellido, char * nombre, int documento);
// Creamos una funcion(metodo) para mostrar los atributos de los alumnos
// Devuelve el int con las misma condiciones que serializar
// Hacemos lo mismo con el dcoumento
int GetCompleto(alumno_t alumno, char cadena[], uint32_t espacio);
int GetDocumento(alumon_t alumno);

//En .c implemento estas funciones
// La implementacion de getcompleto y getdocumento son iguales a serializar


//Como creo un alumno
alumno_t CrearAlumno(char * apellido, char * nombre, int documento){
	/** @brief Creo un puntero para el objeto
	 * Con lo colocado a la izquierda de la igualdad estamos creando un puntero del tipo alumno_t llamado 
	 * resultado, el problema es que este puntero esta apuntando a un espacio vacio.
	 * Para cambiar esto usamos la funcion malloc, la cual nos devuelve una direccion de memoria a partir
	 * de la cual nos reservara una cantidad de memoria especificada. En nuestro caso la cantidad de memoria 
	 * que necesitamos es la que ocupa una esstructura del tipo alumno_s
	**/
	alumno_t resultado = malloc(sizeof(struct alumno_s));
	strcpy(resultado->nombre, nombre); //!< escribo en el atributo nombre de mi estructura el nombre pasado por funcion
	return resultado;
}


```

Este patron de codigo en C se lo conoce como *tipo abstracto de dato*. Ya que objeto no es esto.
Beneficios de este patron:
- No se puede alterar la estructura
- Se necesito un metodo para crear la estructura y para ver los campos del mismo
	- El metodo para crear se llama constructor
Otra manera de hacer un constructor es

``` C
//Otra manera es guarda espacio en memoria estatica durante el momento de compilacion, para esto tenemos que aclarar en un principio cuantos objetos usaremos

static struct alumno_s instancias[50]={0};//!< Inicializo todo en 0
// Para que esto funcione cada objeto tiene que tener una variable auxiliar(para saber si se esta ocupando ese espacio de memoria)
bool libre: //!< variable que se le agregara
/*
Luego lo que hacemos es hacer un lazo donde buscamos un objeto libre para usarlo(libre=0)
*/
```

