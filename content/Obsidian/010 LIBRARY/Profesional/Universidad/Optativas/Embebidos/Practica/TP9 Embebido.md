

``` C
#include "bsp.h"
#include "reloj.h"
#include "bcd.h"
#include <stdbool.h>
#include <stddef.h>
#include "FreeRTOS.h"
#include "task.h"

/* Definicion de macros */
#ifndef TICS_POR_SEGUNDO
#define TICS_POR_SEGUNDO 1000
#endif

#ifndef PERIODO_PARPADEO
#define PERIODO_PARPADEO 200
#endif

#ifndef POSPONER_MINUTOS
#define POSPONER_MINUTOS 5
#endif

#ifndef MODIFICAR
#define MODIFICAR 3 * TICS_POR_SEGUNDO
#endif

#ifndef CANCELAR_MODIFICAR
#define CANCELAR_MODIFICAR MODIFICAR * 10
#endif

/* Delacacion de datos privados */
typedef enum {
    SIN_CONFIGURAR,
    MOSTRANDO_HORA,
    AJUSTANDO_MINUTOS_ACTUAL,
    AJUSTANDO_HORAS_ACTUAL,
    AJUSTANDO_MINUTOS_ALARMA,
    AJUSTANDO_HORAS_ALARMA,
} modo_t;

/* Declaracion de funciones Privadas */
void ToggleAlarma(clk_t reloj);
void CambiarModo(modo_t valor);
void TareaPrincipal(void* pvParameters);
void TareaTeclado(void* pvParameters);

/* Definicion de variables globales */
board_t board;
clk_t reloj;
modo_t modo;
bool sonando_alarma = false;
const uint8_t LIMITE_MINUTO[] = { 6, 0 };
const uint8_t LIMITE_HORA[] = { 2, 4 };
uint16_t tiempo_presionado_hora_actual;
uint16_t tiempo_presionado_hora_alarma;
uint16_t tiempo_sin_presionar;

/* Definicion de colas */
QueueHandle_t colaTeclado;

/* Imprementacion de funciones publicas */
void ToggleAlarma(clk_t reloj) {
    if (sonando_alarma) {
        sonando_alarma = false;
        DigitalOutputDesactivate(board->buzzer);
    } else {
        sonando_alarma = true;
        DigitalOutputActivate(board->buzzer);
    }
}

void CambiarModo(modo_t valor) {
    modo = valor;
    switch (modo) {
        case SIN_CONFIGURAR:
            DisplayFlashDigits(board->display, 0, 3, PERIODO_PARPADEO);
            break;
        case MOSTRANDO_HORA:
            DisplayFlashDigits(board->display, 0, 0, 0);
            break;
        case AJUSTANDO_MINUTOS_ACTUAL:
            DisplayFlashDigits(board->display, 0, 1, PERIODO_PARPADEO);
            break;
        case AJUSTANDO_HORAS_ACTUAL:
            DisplayFlashDigits(board->display, 2, 3, PERIODO_PARPADEO);
            break;
        case AJUSTANDO_MINUTOS_ALARMA:
            DisplayFlashDigits(board->display, 0, 1, PERIODO_PARPADEO);
            break;
        case AJUSTANDO_HORAS_ALARMA:
            DisplayFlashDigits(board->display, 2, 3, PERIODO_PARPADEO);
            break;
        default:
            break;
    }
}

void TareaPrincipal(void* pvParameters) {
    uint8_t entrada[4]; // Vector en el cual guardaremos el valor de entrada y lo que mostraremos mientras configuro la hora

    while (1) {
        // Leer el valor del teclado de la cola
        if (xQueueReceive(colaTeclado, &entrada, 0) == pdTRUE) {
            // Procesar la entrada del teclado y realizar las acciones correspondientes
            if (sonando_alarma) {
                PosponerAlarma(reloj, POSPONER_MINUTOS, sonando_alarma);
            } else {
                switch (modo) {
                    case MOSTRANDO_HORA:
                        ClkActivateAlarma(reloj, 1);
                        break;
                    case AJUSTANDO_MINUTOS_ACTUAL:
                        CambiarModo(AJUSTANDO_HORAS_ACTUAL);
                        break;
                    case AJUSTANDO_HORAS_ACTUAL:
                        ClkSetTime(reloj, entrada, sizeof(entrada));
                        CambiarModo(MOSTRANDO_HORA);
                        break;
                    case AJUSTANDO_MINUTOS_ALARMA:
                        CambiarModo(AJUSTANDO_HORAS_ALARMA);
                        break;
                    case AJUSTANDO_HORAS_ALARMA:
                        ClkSetAlarma(reloj, entrada, sizeof(entrada));
                        CambiarModo(MOSTRANDO_HORA);
                        break;
                    default:
                        break;
                }
            }
        }

        // Verificar otros eventos y realizar acciones correspondientes

        vTaskDelay(pdMS_TO_TICKS(10));
    }
}

void TareaTeclado(void* pvParameters) {
    uint8_t entrada[4]; // Vector para almacenar la entrada del teclado

    while (1) {
        // Leer el estado del teclado y guardar la entrada
        // ...
        // Aquí deberías implementar la lectura del teclado y guardar la entrada en el vector 'entrada'

        // Enviar la entrada a la cola
        xQueueSend(colaTeclado, &entrada, portMAX_DELAY);

        vTaskDelay(pdMS_TO_TICKS(10));
    }
}

int main(void) {
    // Crear la cola para el teclado
    colaTeclado = xQueueCreate(1, sizeof(uint8_t) * 4);

    // Crear tarea principal
    xTaskCreate(TareaPrincipal, "TareaPrincipal", configMINIMAL_STACK_SIZE, NULL, tskIDLE_PRIORITY, NULL);

    // Crear tarea del teclado
    xTaskCreate(TareaTeclado, "TareaTeclado", configMINIMAL_STACK_SIZE, NULL, tskIDLE_PRIORITY, NULL);

    // Iniciar el planificador de tareas
    vTaskStartScheduler();

    // El código no debería llegar aquí
    while (1) {
    }
}

```



## Tarea de lectura de teclas

``` C
void TareaTeclado(void* pvParameters) {
    uint8_t entrada[4]; // Vector para almacenar la entrada del teclado

    while (1) {
        // Leer el estado del teclado y guardar la entrada
        // Aquí debes completar la implementación de la lectura del teclado utilizando funciones de BSP
        // Por ejemplo, supongamos que tienes 4 botones identificados como 'button1', 'button2', 'button3' y 'button4'
        // Puedes utilizar las funciones de BSP para leer el estado de cada botón y asignar el valor correspondiente en el vector 'entrada'

        if (DigitalInputGetState(button1)) {
            entrada[0] = 1;
        } else {
            entrada[0] = 0;
        }

        if (DigitalInputGetState(button2)) {
            entrada[1] = 1;
        } else {
            entrada[1] = 0;
        }

        if (DigitalInputGetState(button3)) {
            entrada[2] = 1;
        } else {
            entrada[2] = 0;
        }

        if (DigitalInputGetState(button4)) {
            entrada[3] = 1;
        } else {
            entrada[3] = 0;
        }

        // Enviar la entrada a la cola
        xQueueSend(colaTeclado, &entrada, portMAX_DELAY);

        vTaskDelay(pdMS_TO_TICKS(10));
    }
}

```