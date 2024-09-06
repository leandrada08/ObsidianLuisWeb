# TP4(HAL)
Cuando hagamos un proyecto, hay que incluir un makefile, donde pondremos en una variable donde esta MUJU, en otra variable que BOARD usaremos y agregamos un include en nuestro makefile
``` python
BOARD ?= edu-ciaa-nxp ##<! Variable donde indico la board
MUJU ?=~/proyectos/muju ##<! Variable donde coloco la direccion de muju

include $(MUJU)/module/base/makefile ##<! Incluimos el makefile de MUJU

## Todas las reglas que usaremos vienen de MUJU
```


## Configurando los pines
#### 1. Configuro funcion del terminar
```C
Chip_SCU_PinMuxSet(Numero de puerto,Numero de pin, Configuraciones juntas)
```
- Configuraciones: Habilitacion de los buffer de entrada| Configuracion Pull up, Pulldown | Funcion del puero
- SCU_MODE_INACT: Desactiva el modo pulls up y pulldown.
- SCU_MODE_PULLUP: Activa el modo pullup
- SCU_MODE_PULLDOWN: Activa el modo pulldown.
- SCU_MODE_INBUFF_EN: Buffer de entrada habilitado para leer la salida, tambien lo necesitamos para leer las entradas.
En nuestro caso configuramos el puerto de esta manera
``` C
Chip_SCU_PinMuxSet(LED_R_PORT, LED_R_PIN, SCU_MODE_INBUFF_EN | SCU_MODE_INACT | LED_R_FUNC); //<! Configuro el pin LED_R_PIN del puerto LED_R_PORT con en buffer de entrada activo, modo pullup y pulldown inactivo y en funcion 4(#define LED_R_FUNC SCU_MODE_FUNC4)
```
#### 2. Configuro el estado del terminar
``` C
Chip_GPIO_SetPinState(LPC_GPIO_PORT, GPIOConfigurando, BITdelGPIO, Estado(Apagado o prendido(Con true y false)));
```
#### 3. Configuracion entrada o salida
``` C
Chip_GPIO_SetPinDIR(LPC_GPIO_PORT, GPIOConfigurando, BITdelGPIO, Funcion(Salida o entrada(Con true y false)));
```
- LPC_GPIO_PORT: Puntero a los registros de GPIO
### Analizando los pines
``` C
Chip_GPIO_ReadPortBit(LPC_GPIO_PORT, TEC_1_GPIO, TEC_1_BIT)//<! Lee el estado el bit de un puerto gpio y nos devuelve 0 o 1()
```
Esto nos sirve para analizar si un boton esta apretado o no

``` C
Chip_GPIO_SetPinToggle(LPC_GPIO_PORT, LED_1_GPIO, LED_1_BIT);//<! Esta funcion si esta prendido un gpio lo apaga y si esta apagago lo prende
```
Esta funcion nos sirve para conmutar un estado

## BSP
Haremos un objeto placa que nos representara a nuestro hardware. Es para utilizar distintas placas con el mismo micro.
Realizamos el struct y el objeto que representa a nuestro objeto placa.
- Para mayor facilidad, haremos que nuestro struct sea publico
	- Pero este puntero sera constante
``` C
/*En bsp.h
*/

#include "digital.h"
// Creo el struct tipo board
typedef struct board_s{
	digital_output_t led_azul;
	digital_output_t led_rojo;
	digital_output_t led_amarillo;
	digital_output_t led_verde;
	
	digital_input_t boton_prueba;
	digital_input_t boton_cambiar;
	digital_input_t boton_prender;
	digital_input_t boton_apagar;
	
} const * const board_t; //La direccion de memoria del puntero y los almacenado es constante

//Creo la funcion para crear el struct
board_t BoardCreate(void);



/* En bsp.c
*/

static struct board_s board = {0};

board_t BoardCreate(void){
	
	return &board;
}


```

#Consultar 
El BSP es algo del proyecto?
#Consultar : Que hace este codigo
``` C
return input->inverted ^ Chip_GPIO_ReadPortBit();//El operador ^ es XOR
```

### Observaciones
- Falso es 0 y el Verdadero es $\neq$ 0
- Es bueno poner la constante a la izquierda, ya que no funciona cuando esta mal.
