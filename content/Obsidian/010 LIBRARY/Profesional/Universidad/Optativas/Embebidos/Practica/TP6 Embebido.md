# TP6
Codigo para la pantalla de 7 segmento
``` C
//en pantalla.h

//Definiciones de bits asociados a cada segmento para construir los digitales
#define SEGMENT_A(1 << 0)
#define SEGMENT_B(1 << 1)
#define SEGMENT_C(1 << 2)
#define SEGMENT_D(1 << 3)
#define SEGMENT_E(1 << 4)
#define SEGMENT_F(1 << 5)
#define SEGMENT_G(1 << 6)
#define SEGMENT_P(1 << 7)

//! Refencia a un descritor para gestionar una pantalla de siete segmento multiplezada
typedef struct display_s * display_t;

//! Funcion de callback para apagar los segmentos y digitos de la pantalla
typedef void(*display_screen_off_t)(void);

//! Funcion de callback para prender los segmentos de la pantalla
typedef void(*display_segments_on_t)(uint8_t segments);

//! Funcion de callback para prender un digito de la pantalla
typedef void(*display_digit_on_t)(uint8_t digit);

//! Estructura de bajo nivel para manejo de la pantalla
typedef struct display_driver_s{
	display_screen_off_t ScreenTurnOff;  
	display_segments_on_t SementsTurnOn;
	display_digit_on_t DigitTurnOn;
}const * const display_driver_t; //<! Puntero al controlador de pantalla


/** @brief Metodo para crear una pantalla multiplezada de siete segmento
* @param digits cantidad de digitos que forman la pantalla multiplexada
* @param driver Puntero a la estructura con las funciones de bajo nivel
* @return display_t Piunto al descritor de la pantalla creada
*
**/
display_t DisplayCreate(uint8_t digits, display_driver_t driver);

/** @brief Funcion para escribir un numero BCD en la pantalla de siete segmento
* @param display puntero al descritor de la pantalla en la que se escribe
* @param number Puntero al primer elemento de numero BDC a escribir
* @param size Cantidad de elemntos en el vector que contiene al numero BCD
*
**/
void DisplayWriteBCD(display_t display, uint8_t * number, uint8_t size);

/** @brief Funcion para refrescar la pantalla
* @param display Puntero al descritor de la pantalla que se debe resfrescar
* 
**/
void DisplayRefresh(display_t display);


```
