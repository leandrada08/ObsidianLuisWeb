



## Máquina de Estado de Mealy en Verilog 2001

```verilog
module MealyFSM (
    input clk,        // Señal de reloj
    input rst,        // Señal de reinicio
    input in_data,    // Entrada de datos
    output reg out1,  // Salida 1
    output reg out2   // Salida 2
);
```

``` verilog
// Declaración de estados
typedef enum logic[1:0]{
	S0, S1, S2, S3
} state_t;

```

``` verilog
state_t current_state, next_state;
```

``` verilog
// Logica de memoria y reset
always @(posedge clk or posedge rst) begin
    if (rst)
        current_state <= S0;
    else
        current_state <= next_state;
end
```
``` verilog
// Logica para la salida
always @(*) begin
    // Lógica para el siguiente estado
    case (current_state)
        S0:
            next_state = (in_data) ? S1 : S0;
        S1:
            // Define las transiciones para el estado 01
        S2:
            // Define las transiciones para el estado 10
        S3:
            // Define las transiciones para el estado 11
    endcase
end
```

``` verilog
// Logica para las salida
always @(*) begin
    // Lógica para las salidas de Mealy
    case (current_state)
        S0:
            out1 = (in_data) ? 1'b1 : 1'b0;
            out2 = 1'b0;
        S1:
            // Define las salidas para el estado 01
        S2:
            // Define las salidas para el estado 10
        S3:
            // Define las salidas para el estado 11
    endcase
end

endmodule
```

## Máquina de Estado de Moore en Verilog 2001

La implementación de una máquina de estado de Moore en Verilog 2001 es similar a la de Mealy. La diferencia principal radica en que las salidas se calculan únicamente en función del estado actual. Puedes usar el mismo código que se muestra arriba, pero en el bloque `always @(*)`, solo definirías las salidas basadas en `current_state`.




## Maquina de estado finito temporizada


Para implementar una máquina de estado finito (FSM) temporizada en Verilog, debes agregar una lógica que controle el tiempo y las transiciones basadas en el tiempo. Esto se logra utilizando una señal de reloj y un contador de tiempo en el diseño. A continuación, se muestra un ejemplo de cómo puedes implementar una FSM temporizada en Verilog:

Supongamos que deseas crear una máquina de estado que realice una secuencia de tres estados, con tiempos específicos en cada estado antes de avanzar al siguiente. Aquí hay un ejemplo de cómo podrías hacerlo:

```verilog
module TimedFSM (
    input wire clk,           // Señal de reloj
    input wire rst,           // Señal de reinicio
    output reg state_done,   // Estado finalizado
    output wire [2:0] state  // Estado (3 estados posibles)
);

// Parámetros de temporización
parameter STATE1_TIME = 1000000; // Tiempo en unidades de tiempo
parameter STATE2_TIME = 2000000; // Tiempo en unidades de tiempo
parameter STATE3_TIME = 1500000; // Tiempo en unidades de tiempo

// Contador de tiempo
reg [31:0] timer;

// Estados de la máquina de estado
localparam S0 = 3'b000, S1 = 3'b001, S2 = 3'b010, S3 = 3'b011;

always @(posedge clk or posedge rst) begin
    if (rst) begin
        state <= S0;
        timer <= 0;
    end else begin
        case (state)
            S0:
                if (timer >= STATE1_TIME)
                    state <= S1;
            S1:
                if (timer >= STATE2_TIME)
                    state <= S2;
            S2:
                if (timer >= STATE3_TIME)
                    state <= S3;
            default:
                // Mantén el estado actual
        endcase

        // Incrementa el contador de tiempo
        if (state != S3)
            timer <= timer + 1;
    end
end

always @(posedge clk or posedge rst) begin
    if (rst)
        state_done <= 0;
    else if (state == S3)
        state_done <= 1;
    else
        state_done <= 0;
end

endmodule
```

Puedes personalizar los tiempos y estados según tus necesidades específicas. Asegúrate de que el período de tu señal de reloj esté configurado adecuadamente para que los tiempos se ajusten a tus requisitos. La señal `state_done` indica cuándo se ha completado la secuencia de estados.