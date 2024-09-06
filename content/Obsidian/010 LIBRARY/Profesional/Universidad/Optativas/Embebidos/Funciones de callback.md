*Callback:* un callback es una función que se pasa como argumento a otra función. El propósito del callback es permitir que la función llamada pueda llamar de vuelta a la función pasada como argumento en algún momento posterior.
Los callbacks son comúnmente utilizados en sistemas embebidos para manejar eventos asíncronos. En lugar de tener una función de espera que bloquee la ejecución del programa hasta que un evento ocurra, se puede pasar una función de callback que se llame cuando ocurra el evento.
Por ejemplo, en un sistema de control de motor, se puede tener una función que lea los sensores de temperatura del motor y luego llame a una función de callback cuando se alcanza una temperatura crítica. La función de callback podría entonces apagar el motor o tomar otra acción apropiada.
Los callbacks también son útiles para la programación de interfaces de usuario. Por ejemplo, una función de botón de un GUI puede tener un callback asociado que se llama cuando se hace clic en el botón.
``` C
calculadora -> operacion

int Suma(int a, int b);
int Resta(int a, int b);

typedef int(*operacion_t)(int,int);
operacion_t operacion;

operacion = Suma;
resultado = operacion(1,5);
operacion = Resta;
resultado = operacion(1,5);
```


Ejemplo mas completo pero mas complicado
## Candado
``` C
// En candado.h
typedef struct candado_s * candado_t; //Genero un objeto del tipo candado
typedef int(*error_event_t)(candato_t); //Genero un callback que devuelve un entero, se llama error_event_t y recibe un tipo candado_t
typedef void(*suscess_event_t)(candado_t);//Genero un callback que devuelve un void, se llama suscess_event_t y recibe un tipo candado_t

/** @brief Funcion para crear candado
* @param clave: Numero que sera la clave del candado
* @param on_sucess:
* @param on_error:
* Ojo, suscess_event_t y error_event_t son tipos de datos, mientras que on_sucess y on_error son variables
*
*/
candado_t CandadoCrear(uint32_t clave, suscess_event_t on_sucess, error_event_t on_error);

void CandadoTick(candado_t self);


// En el main.c
/*A diferencia de success_event_t y on_sucess, onSucess es una funcion
*
*
* A modo de explicacion como funciona los callback, hare un paralelismo con funciones normales
* suscess_event_t:es el tipo de dato INT
* on_sucess: Es una variables entera llamada clave
* onSucess: Es un valor entero=4
*
* intentar combinar tipos suscess_event_t con error_event_t es como combinar
* tipo de datos char con tipos de datos enteros.
*
* Tengo la necesidad de generar un tipo de dato callback por cada funciones de recibe o
* genera algo distinto a las demas
*
*/
void onSucess(candado_t candado){
	...
}

void onError(candado_t candado){
	...
}




// En el candado.c
// Ver consulta
struct candado_s{
	uint32_t clave;
	uint32_t penalidad;
	char ingresada[MAX_LENGTH];
	sucess_event_t on_sucess; //<! Ingreso los callback en el objeto como si fueran metodos
	error_event_t on_error;
};
// Le asigno un valor cuando inicializo el objeto(tambien tengo que asignarle un valor a mis funciones de callback ya que tengo que indicarle que haran cada una)
candado_t candadoCrear(uint32_t clave, suscess_event_t on_sucess, error_event_t on_error){
	candado_t self = malloc(sizeof(struct candado_s));
	if(self){
		keyboardInit();
		self->clave=clave;
		self->on_sucess = on_sucess;
		self->on_error = on_error;
	}
}

static void limpiarEntrada(candado_t self){
	menset(self->ingresada, 0, sizeof(self->ingresada));
}

static void agregarEntrada(candado_t self, char key){
	self->ingresada[strlen(self->ingresada)]=key;
}


// Que hace lo siguiente? 
#define agregarEntrada(self,key) \
	self->ingresada[strlen(self->ingresada)]=key 



void candadoTick(candato_t self){
	// Aqui hago uso de los callback como si fuera una funcion normal
	char key;
	if(self->penalidad){
		self->penalidad--;
	}else{
		int key = getchar(); //Esta funcion lee los valores de entrada
		if((key >= '0') && (key <= '9')){
		// strlen cuenta la cantidad de elementos de un vector y sizeof el tamaño en bytes
			if(strlen(self->ingresada)< sizeof(self->ingresada)-1){ //Porque hace esta pregunta?
				agregarEntrada(self, key); //Agrego lo ingresado a ingresada
				if(self->clave == atoi(self->ingresada)){ //Se compara la clave con lo ingresado
					self->on_sucess(self); //Uso funcion para avisar que la clave es correcta
					limpiarEntrada(self); 
				} else {
					self->penalidad= self->on_error(self); //Uso callback para avisar que fue incorrecto
					limpiarEntrada(self);
				}
			
			}
		} else if(key ==''){
			limpiarEntrada(self);
		}
	}
}



```
#Consultar : Osea, el callback es como un metodo que tiene nuestro objeto pero para definir su funcionamiento necesitamos de funciones que se definiran en el main(osea externas al objeto?)
- En otras palabras, nuestro objeto tiene un metodo(el callback) que es definido por un archivo externo(main.c)
	*Respuesta:* Enrealidad no. Lo definimos dentro de nuestro struct porque al ser una variable necesitamos que este dentro de un struct, si no lo pondriamos dentro del struct del objeto habria que hacerlo en uno auxiliar
#Consultar : En el caso de que los callback no esten en la funcion crearcandado. Se seguirian comportando como metodos del objeto
#Consultar No entiendo que hace este codigo
	No entiendo porque dice que esto aumenta el rendimiento
``` C
#define agregarEntrada(self,key) \
	self->ingresada[strlen(self->ingresada)]=key
```
