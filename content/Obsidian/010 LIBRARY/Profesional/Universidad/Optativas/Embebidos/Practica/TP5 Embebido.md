Pruebas necesarias

### A realizar
- Debe diseñar una calculadora abstracta que al ser creada no sepa hacer ninguna operación. El programa identificará, en la operación a realizar, los operandos y el operador. Luego, deberá buscar en una tabla dinámica cuál es la función correspondiente a esa operación y utilizarla para completar el cálculo.
- Deberá escribir también un programa principal de prueba que cree una calculadora abstracta, agregue las operaciones básicas de suma, resta multiplicación y división, y la pruebe efectuando un cálculo con cada operación.

### Organizacion de los archivos
- Los archivos calculadora.c y calculadora.h deberán ubicarse en la carpeta src. El ejecutable deberá ubicarse en la carpeta build/bin y los archivos objeto intermedios en la carpeta build/obj. El programa principal estará compuesto solo por la función main, que se ubicará en el archivo main.c.

### Compilacion y documentacion
- Se definirá un archivo de makefile para poder compilar el proyecto con el comando make all. Se documentará todo el código utilizando doxygen. El comando make doc deberá generar la documentación en HTML en la carpeta build/doc.

### Formato
- Se deberá mantener un formato consistente en todo el código desarrollado (posición de llaves, formatos de identificadores y niveles de identado). Se deberá evitar la repetición de código utilizando, adecuadamente, macros y archivos de cabecera.



# Codigo
``` C
// en main.c
//Genero las funciones que tendra mi calculadora
int suma(int a, int b){
	return a+b;
}
int resta(int a, int b){
	return a-b;
}
int producto(int a, int b){
	return a*b;
}
int main(void){
	int resultado
	calculadora_t calculadora= CrearCalculadora();
	AgregarOperacion(calculadora,'+',suma);
	AgregarOperacion(calculadora,'-',resta);
	AgregarOperacion(calculadora,'*',producto);
	resultado = Calcular(calculadora, "2*4");
	printf("resultado %i\r\n", resultado);
}





// en calculadora.h
typedef struct calculadora_s * calculadora_t; //Genero un objeto del tipo candado
typedef int(*funcion_t)();
//typedef int(*operacion_t)();
candado_t CandadoCrear(uint32_t clave, suscess_event_t on_sucess, error_event_t on_error);

void CandadoTick(candado_t self);









// en calculadora.c
typedef struct operacion_s * operacion_t;

struct operacion_s{
	char operador;
	funcion_t funcion;
	operacion_t siguiente;
}

struct calculadora_s{
	struct operacion_s operaciones[OPERACIONES]; //Creo las componentes de calculadoras de manera estatica
};

operacion_t BuscarOperacion(calculadora_t calculadora, char operador){
	operacion_t result = NULL;
	// for(int indice=0;indice<OPERACIONES; indice++){
	for(operacion_t actual=calculadora->operaciones;actual->siguiente!=NULL;){
		//if(calculadora->operaciones[indice].operador==operador){
		if(actual->operador==operador){
			result=actual;
			break;
		}
	}
}

calculadora_t CrearCalculadora(void){ //Creo la calculadora de manera dinamica
	calculadora_t result = malloc(sizoef(struct calculadora_s));
	if (result){
		memset(result, 0, sizeof(struct calculadora_s)); //limpia la memoria que usara la calculadora
	}
	return result; //Devuelve la calculadora vacia
}



/** @brief Funcion para agregar operacion a la calculadora
* @return 1 si operacion es distinto de 0 y 0 si es igual
*
**/
bool AgregarOperacion(calculadora_t calculadora, char operador, funcion_t funcion){
	//operacion_t operacion = BuscarOperacion(calculadora, '\0'); //Busca el terminador nulo, para buscar el primer componente libre
	operacion_t operacion = malloc(sizeof(struct operacion_s)); // Para lista enlazada
	if((opearcion)&& !BuscarOperacion(calculadora, operador)){
		operacion->operador = operador;
		operacion->funcion = funcion;
		operacion->siguiente=calculadora->operaciones;
		calculadora->operaciones=operacion;
	}
	return (operacion!=NULL);
}


/** @brief Funcion para calcular el valor de una determinada operacion
*
*
*
*
**/
int Calcular(calculador_t calculadora, char * cadena){
	int a,b;
	char operador;
	int result = 0;

	for(int indice = 0;indice<strlen(cadena): indice++){
		if(cadena[indice]<'0'){
			operador = candena[indice];
			a = atoi(cadena);
			b = atoi(cadena + indice + 1);
			break;
		}
	}
	operacion_t operacion = BuscarOperacion(calculadora, operador);
	if(operacion) {
		result = operacion->funcion(a,b);
	}
	return result;
}


```
