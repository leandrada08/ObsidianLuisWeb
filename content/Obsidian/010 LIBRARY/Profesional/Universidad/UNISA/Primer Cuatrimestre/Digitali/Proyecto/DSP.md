## Introduccion
En los sistemas modernos, los microcontroladores son esenciales para manejar una variedad de tareas, desde el control de procesos industriales hasta la gestión de dispositivos electrónicos de consumo. Los componentes DSP integrados en un microcontrolador proporcionan capacidades adicionales para procesar señales digitales de manera eficiente. 

- Utilizamos un enable desde el control para podes aplicar la tecnica de ahorro de energia clock gatting
### Componente DSP 

#### 1. **Sumadores**
En un microcontrolador, los sumadores son componentes fundamentales para realizar operaciones aritméticas. Los sumadores pueden ser utilizados en varios contextos:

- **Operaciones Matemáticas Básicas:** Soportan operaciones de suma en cálculos matemáticos básicos que son necesarios en aplicaciones como el control de procesos y la manipulación de datos.
- **Acumulación de Señales:** En aplicaciones de procesamiento de señales, los sumadores se utilizan para la acumulación de muestras de señal, que es crucial en algoritmos como la media móvil y los filtros FIR.

#### 2. **Multiplicadores**
Los multiplicadores son esenciales para cualquier aplicación que requiera el procesamiento de señales más complejas. En el contexto de un microcontrolador:

- **Procesamiento de Audio y Video:** Permiten la manipulación de señales de audio y video, como la modulación y demodulación de señales.
- **Filtros Digitales:** Se utilizan en la implementación de filtros FIR e IIR, esenciales para limpiar y mejorar señales ruidosas.

#### 3. **Acumuladores**
Los acumuladores se utilizan para almacenar resultados intermedios y finales en operaciones secuenciales de procesamiento de señales:

- **Filtros Digitales:** En la implementación de filtros, los acumuladores almacenan los resultados parciales de las operaciones de filtrado.
- **Sistemas de Control:** Ayudan en la integración de señales en sistemas de control, permitiendo la sumatoria de errores en controladores PID, por ejemplo.

#### 4. **Filtros Digitales**
Los filtros digitales son una aplicación directa de los componentes DSP, y son vitales para muchas funciones de un microcontrolador:

- **Reducción de Ruido:** Los filtros digitales se utilizan para eliminar ruido de las señales de entrada en sensores y sistemas de comunicación.
- **Análisis de Frecuencia:** En aplicaciones de análisis de señales, los filtros permiten extraer componentes de frecuencia específicas de una señal.

#### 5. **Convolución**
La operación de convolución es crucial en muchas aplicaciones DSP y es soportada por microcontroladores con capacidades DSP integradas:

- **Filtros FIR:** La convolución se usa en la implementación de filtros FIR, que son esenciales para diversas tareas de procesamiento de señales.
- **Reconocimiento de Patrones:** En aplicaciones de reconocimiento de patrones, como el procesamiento de imágenes y señales biomédicas, la convolución ayuda a identificar características específicas.

#### 6. **Restadores**
Los restadores también juegan un papel importante en un microcontrolador con soporte DSP:

- **Operaciones Aritméticas:** Se utilizan en operaciones aritméticas básicas que son fundamentales para el cálculo de diferencias en datos.
- **Procesamiento de Señales:** Ayudan a calcular diferencias en señales, lo que es crucial en operaciones de detección de bordes en imágenes y la derivación de señales en controladores PID.

### Ejemplos de Uso en Microcontroladores

#### **Procesamiento de Audio**
En sistemas de procesamiento de audio, un microcontrolador puede usar componentes DSP para:

- **Ecualización de Audio:** Utilizar filtros digitales para ajustar las diferentes bandas de frecuencia de una señal de audio.
- **Reducción de Ruido:** Implementar filtros de paso bajo o alto para eliminar ruido no deseado de una señal de audio.

#### **Sensores y Actuadores**
En aplicaciones que involucran sensores y actuadores, los componentes DSP permiten:

- **Filtrado de Señales de Sensores:** Eliminar ruido de las señales de sensores para obtener lecturas más precisas.
- **Control de Actuadores:** Implementar controladores PID para mantener el control preciso de motores y otros actuadores.

#### **Comunicaciones Inalámbricas**
En sistemas de comunicaciones inalámbricas, los microcontroladores utilizan componentes DSP para:

- **Modulación y Demodulación:** Procesar señales moduladas y demoduladas para la transmisión y recepción de datos.
- **Codificación y Decodificación:** Implementar esquemas de codificación de canal para mejorar la fiabilidad de las comunicaciones.

### Integración de DSP en Microcontroladores

La integración de capacidades DSP en microcontroladores ofrece varios beneficios, incluyendo:

- **Eficiencia Energética:** Los microcontroladores con DSP pueden realizar operaciones complejas más rápidamente y con menos consumo de energía que un CPU estándar.
- **Flexibilidad de Aplicación:** Permiten a los diseñadores implementar una amplia gama de aplicaciones, desde el procesamiento de señales hasta el control de sistemas en tiempo real.
- **Reducción de Costes:** Al integrar capacidades DSP directamente en el microcontrolador, se reduce la necesidad de hardware adicional, disminuyendo así el costo total del sistema.
## Nuestra DSP

### Diagrama de bloque
![[Pasted image 20240712132502.png]]


### Codigo

```verilog
// Módulo DSP: Implementa una unidad de procesamiento digital con operaciones de suma, resta, multiplicación y filtrado FIR.
// Autor: Luis Elian Andrada

module DSP (
    input clk,                     // Señal de reloj
    input rst,                     // Señal de reinicio
    input start,                   // Señal de inicio de la operación
    input [1:0] operation,         // Selección de la operación: 00 -> Suma, 01 -> Multiplicación, 10 -> Filtrado FIR, 11 -> Resta
    input [31:0] A[7:0],           // Coeficientes del filtro FIR (h)
    input [31:0] B[7:0],           // Valores de la señal (x)
    output reg [31:0] result[7:0], // Salida con 8 valores intermedios de la convolución
    output reg done                // Señal de finalización de la operación
);

    // Declaración de registros y wires
    reg [2:0] state, next_state;   // Estados actuales y siguientes del FSM
    reg [3:0] index, k;            // Contadores de índices
    reg [31:0] acc;                // Acumulador para la operación FIR
    reg [31:0] a_ext[11:0];        // Coeficientes extendidos
    reg [31:0] x_ext[11:0];        // Señal extendida

    wire [31:0] sum, product, diff; // Resultados intermedios de las operaciones
    wire [31:0] a_bus, b_bus;      // Buses para las entradas de las operaciones

    // Instanciación de los módulos independientes para suma, multiplicación y resta
    SUM sum_inst (.a(a_bus), .b(b_bus), .sum(sum));
    MULT mult_inst (.a(a_bus), .b(b_bus), .product(product));
    SUB sub_inst (.a(a_bus), .b(b_bus), .diff(diff));

    // Definición de los estados del FSM
    localparam IDLE        = 3'd0, // Estado de reposo
               LOAD        = 3'd1, // Estado de carga
               EXECUTE     = 3'd2, // Estado de ejecución
               DONE        = 3'd3; // Estado de finalización

    // Lógica de transición de estados
    always @(posedge clk or posedge rst) begin
        if (rst)
            state <= IDLE; // Reiniciar el estado a IDLE
        else
            state <= next_state; // Transición al siguiente estado
    end

    // Lógica de selección del próximo estado
    always @(*) begin
        case (state)
            IDLE: begin
                if (start)
                    next_state = LOAD; // Transición a LOAD si se recibe la señal de inicio
                else
                    next_state = IDLE; // Permanecer en IDLE
            end
            LOAD: begin
                next_state = EXECUTE; // Transición a EXECUTE
            end
            EXECUTE: begin
                if ((operation != 2'b10 && index == 4'd8) || (operation == 2'b10 && index == 4'd12 && k == 4'd8))
                    next_state = DONE; // Transición a DONE si se completan las operaciones
                else
                    next_state = EXECUTE; // Permanecer en EXECUTE
            end
            DONE: begin
                next_state = IDLE; // Transición a IDLE
            end
            default: next_state = IDLE; // Estado por defecto
        endcase
    end

    // Lógica combinacional para a_bus y b_bus
    assign a_bus = (operation == 2'b10) ? a_ext[k] : A[index]; // Selección de a_bus
    assign b_bus = (operation == 2'b10) ? x_ext[index - k] : B[index]; // Selección de b_bus

    // Lógica de control de operaciones
    always @(posedge clk or posedge rst) begin
        if (rst) begin
            // Reinicio de los registros
            index <= 4'd0;
            k <= 4'd0;
            acc <= 32'd0;
            done <= 1'b0;
            a_ext[0] <= 32'd0;
            a_ext[1] <= 32'd0;
            a_ext[2] <= 32'd0;
            a_ext[3] <= 32'd0;
            a_ext[4] <= 32'd0;
            a_ext[5] <= 32'd0;
            a_ext[6] <= 32'd0;
            a_ext[7] <= 32'd0;
            a_ext[8] <= 32'd0;
            a_ext[9] <= 32'd0;
            a_ext[10] <= 32'd0;
            a_ext[11] <= 32'd0;
            x_ext[0] <= 32'd0;
            x_ext[1] <= 32'd0;
            x_ext[2] <= 32'd0;
            x_ext[3] <= 32'd0;
            x_ext[4] <= 32'd0;
            x_ext[5] <= 32'd0;
            x_ext[6] <= 32'd0;
            x_ext[7] <= 32'd0;
            x_ext[8] <= 32'd0;
            x_ext[9] <= 32'd0;
            x_ext[10] <= 32'd0;
            x_ext[11] <= 32'd0;
        end else begin
            case (state)
                IDLE: begin
                    // Reinicio de los contadores y señales
                    k <= 4'd0;
                    acc <= 32'd0;
                    done <= 1'b0;
                    if(operation==2'b10) begin
                        index <= 4'd4;
                    end else begin
                        index <= 4'd0;
                    end
                end
                LOAD: begin
                    // Cargar los coeficientes en los coeficientes extendidos
                    a_ext[0] <= A[0];
                    a_ext[1] <= A[1];
                    a_ext[2] <= A[2];
                    a_ext[3] <= A[3];
                    a_ext[4] <= A[4];
                    a_ext[5] <= A[5];
                    a_ext[6] <= A[6];
                    a_ext[7] <= A[7];

                    // Cargar la señal en la señal extendida
                    x_ext[0] <= B[0];
                    x_ext[1] <= B[1];
                    x_ext[2] <= B[2];
                    x_ext[3] <= B[3];
                    x_ext[4] <= B[4];
                    x_ext[5] <= B[5];
                    x_ext[6] <= B[6];
                    x_ext[7] <= B[7];
                end
                EXECUTE: begin
                    // Ejecución de las operaciones seleccionadas
                    case (operation)
                        2'b00: begin // Suma
                            result[index] <= sum;
                            index <= index + 1;
                        end
                        2'b01: begin // Multiplicación
                            result[index] <= product;
                            index <= index + 1;
                        end
                        2'b11: begin // Resta
                            result[index] <= diff;
                            index <= index + 1;
                        end
                        2'b10: begin // Filtrado FIR
                            if (k <= index) begin
                                acc <= acc + product;
                                k <= k + 1;
                            end else begin
                                // Guardar solo los valores intermedios
                                if (index <= 11) begin
                                    result[index - 4] <= acc;
                                end
                                index <= index + 1;
                                k <= 4'd0;
                                acc <= 32'd0;
                            end
                        end
                    endcase
                end
                DONE: begin
                    // Señalización de la finalización de la operación
                    done <= 1'b1;
                    index <= 4'd0;
                end
            endcase
        end
    end
endmodule
```

### Explicación y Documentación del Código
Se utiliza un diseño basado en maquina de estados para reutiizar recursos

1. **Declaración del Módulo y Entradas/Salidas:**
   - `clk`: Señal de reloj.
   - `rst`: Señal de reinicio.
   - `start`: Señal de inicio de la operación.
   - `operation`: Selección de la operación
	   - 00 -> Suma
	   - 01 -> Multiplicación
	   - 10 -> Filtrado FIR
	   - 11 -> Resta
   - `A[7:0]`: Coeficientes del filtro FIR.
   - `B[7:0]`: Valores de la señal.
   - `result[7:0]`: Salida con 8 valores intermedios de la convolución.
   - `done`: Señal de finalización de la operación.

2. **Declaración de Registros y Wires:**
   - `state`, `next_state`: Estados actuales y siguientes del FSM.
   - `index`, `k`: Contadores de índices

.
   - `acc`: Acumulador para la operación FIR.
   - `a_ext[11:0]`, `x_ext[11:0]`: Coeficientes y señal extendidos.
   - `sum`, `product`, `diff`: Resultados intermedios de las operaciones.
   - `a_bus`, `b_bus`: Buses para las entradas de las operaciones.

3. **Instanciación de los Módulos Independientes:**
   - `SUM`, `MULT`, `SUB`: Módulos para las operaciones de suma, multiplicación y resta.

4. **Definición de Estados del FSM:**
   - `IDLE`: Estado de reposo.
   - `LOAD`: Estado de carga.
   - `EXECUTE`: Estado de ejecución.
   - `DONE`: Estado de finalización.

5. **Lógica de Transición de Estados:**
   - Cambia el estado basado en la señal de reloj y la señal de reinicio.
   - Define las transiciones entre los estados en función de las condiciones específicas.

6. **Lógica Combinacional para `a_bus` y `b_bus`:**
   - Asigna valores a `a_bus` y `b_bus` en función de la operación seleccionada.

7. **Lógica de Control de Operaciones:**
   - Reinicia los registros y contadores en caso de reinicio.
   - Carga los coeficientes y la señal en los registros extendidos en el estado `LOAD`.
   - Ejecuta las operaciones seleccionadas en el estado `EXECUTE`.
   - Almacena los resultados intermedios y controla la acumulación para el filtrado FIR.
   - Señaliza la finalización de la operación en el estado `DONE`.



### Simulacion
![[Pasted image 20240711215918.png]]
![[Pasted image 20240711215832.png]]
### RTL
![[Pasted image 20240711220016.png]]

### Utilizacion
![[Pasted image 20240715220617.png]]

### Reporte de timing post sintesis
![[Pasted image 20240715222554.png]]





# Mejoras necesarias
- La DSP debe funcionar de manera que los valores manejados sean con representacion de punto fijo
	- Para esto es necesario bloques de saturacion y redondeo