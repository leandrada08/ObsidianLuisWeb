**Nombre:** Luis Elian Andrada
**DNI:** 43362912

## Punto 1
### Apartado a y b

``` verilog
module punto1
(
    input [2:0]     i_data1,
    input [2:0]     i_data2,
    input [1:0]     i_sel,
    input           i_rst_n,
    input           clk,
    output [5:0]    o_data,
    output          o_overflow
);
  
reg     [6:0] sumador_reg;
wire    [5:0] result;
wire    [6:0] sum2;
wire    [3:0] sum1;
wire    [3:0] multi;
  
always @(posedge i_rst_n) begin
    if (i_rst_n) begin
        sumador_reg <= 7'b0; // Reset asincrónico del registro
    end
end
  
always @(posedge clk) begin
    sumador_reg <= sum2;
end
  
//Suma1
assign sum1 = i_data1 + i_data2;
  
  
//Multiplexor
assign multi = (i_sel==2'b00) ? {1'b0, i_data1}:
               (i_sel==2'b10) ? {1'b0, i_data2}:
               (i_sel==2'b01) ? i_data1 + i_data2:{5'b00000};
//Suma2
assign sum2 = {2'b00, multi} + sumador_reg[5:0]; // Suma con el registro
  

// Overflow
assign o_overflow = sumador_reg[6]; // Detecta overflow
// Salida de datos
assign o_data = sumador_reg[5:0]; // Salida de los 6 bits menos significativos del registro

  
  

endmodule
```

### Apartado c

``` verilog
`timescale 1ns / 1ps
  
module punto1_tb;
  
    // Parámetros
    parameter CLK_PERIOD = 10; // Periodo del reloj en unidades de tiempo
    // Señales
    reg [2:0] i_data1_tb;
    reg [2:0] i_data2_tb;
    reg [1:0] i_sel_tb;
    reg       i_rst_n_tb;
    reg       clk_tb;
    wire [5:0] o_data_tb;
    wire       o_overflow_tb;
  
    // Instancia del módulo bajo prueba
    punto1 dut (
        .i_data1(i_data1_tb),
        .i_data2(i_data2_tb),
        .i_sel(i_sel_tb),
        .i_rst_n(i_rst_n_tb),
        .clk(clk_tb),
        .o_data(o_data_tb),
        .o_overflow(o_overflow_tb)
    );
  
    // Generación del reloj
  always #5 clk_tb = ~clk_tb;
  
    // Estímulo
    initial begin
        // Reset inicial
        i_data1_tb = 3'b000;
        i_data2_tb = 3'b000;
        i_sel_tb = 2'b00;
        i_rst_n_tb = 1'b0;
        clk_tb = 1'b0;
        #20 i_rst_n_tb = 1'b1; // Liberar el reset
  
        // Test 1: Suma de dos números
        #10 i_data1_tb = 3'b010;
        #10 i_data2_tb = 3'b011;
        #10 i_sel_tb = 2'b10;
        #10;
        // Test 2: Selección de entrada 1
        i_data1_tb = 3'b101;
        i_data2_tb = 3'b001;
        i_sel_tb = 2'b10;
        #10;
        // Test 3: Selección de entrada 2
        i_data1_tb = 3'b010;
        i_data2_tb = 3'b011;
        i_sel_tb = 2'b10;
        #10;
        // Test 4: Reset
        #10 $finish; // Finalizar simulación
    end
  
endmodule
```





### Apartado d
Si inicialmente tenemos un valor de 0 en el registro
1. Para tener overflow necesitamos que en valor mas significativo del registro sea igual a 1(reg[6]=1) 
	-  Entonces El overflow se generara cuando el registro llegue al valor 64teniendo
2. La señal de seleccion vale 1, por lo cual el multiplexor seleccionara siempre la entrada de la suma de ambas entradas.
3. La suma es igual a 2 ya que ambas entradas son 1
4. El valor 2 se sumara de manera recurrente en cada clk al registro, por lo cual tendriamos la ecuacion $$reg=reg+2$$
5. Teniendo en cuenta esto, la cantidad de clock que necesitariamos es $$clk_{necesiarioOver}=\frac{64}{2}$$
- Por lo cual la cantidad todal de clk necesarias para un overflow es de 32



## Punto 4
### Apartado 1
![[Pasted image 20240131103951.png]]

### Apartado b

```verilog
module punto4
#(
    N_BITS = 8
)
(
    input  [N_BITS-1:0]    x,
    input           clk,
    output [N_BITS-1:0]    y
);
  
reg [N_BITS-1:0] y_prev1, y_prev2;
reg [N_BITS-1:0] x_prev1, x_prev2, x_prev3;
  
always @(posedge clk) begin
    x_prev3 <= x_prev2;
    x_prev2 <= x_prev1;
    x_prev1 <= x;
    y_prev2 <= y_prev1;
    y_prev1 <= y;
end
  
assign y = x - x_prev1 + x_prev2 + x_prev3 + (y_prev1 >> 1) + (y_prev2 >> 2);
  
endmodule
```


### Apartado c

``` verilog
`timescale 1ns / 1ps
  
module punto4_tb;
  
    // Parámetros
    parameter N_BITS = 8; // Número de bits de entrada/salida
    parameter CLK_PERIOD = 10; // Periodo del reloj en unidades de tiempo
    // Señales
    reg [N_BITS-1:0] x_tb;
    reg clk_tb;
    wire [N_BITS-1:0] y_tb;
  
    // Instancia del módulo bajo prueba
    punto_4 #(
        .N_BITS(N_BITS)
    ) dut (
        .x(x_tb),
        .clk(clk_tb),
        .y(y_tb)
    );
  
    // Generación del reloj
  always #5 clk_tb = ~clk_tb;
  
    // Estímulo
    initial begin
        // Reset inicial
        x_tb = 0;
        clk_tb = 0;
        #20 clk_tb = 1; // Ciclo de reloj
        #20 clk_tb = 0;
        // Test 1: Entrada constante
        x_tb = 8'b11111111; // x = 255
        #20;
        // Test 2: Cambio brusco en la entrada
        x_tb = 8'b00000000; // x = 0
        #20;
        x_tb = 8'b11110000; // x = 240
        #20;
        // Test 3: Reset
        x_tb = 8'b01010101; // x = 85
        #20;
        x_tb = 8'b00000000; // x = 0
        #20;
        #20 $finish; // Finalizar simulación
    end
  
endmodule
```