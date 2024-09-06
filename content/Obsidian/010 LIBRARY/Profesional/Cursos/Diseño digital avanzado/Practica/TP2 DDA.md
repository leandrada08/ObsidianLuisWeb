**Nombre:** Luis Elian Andrada
**DNI:** 43362912




## Punto 1

### Codigo
``` verilog
module multiplicador_flotante (
    input [12:0] i_valor1,
    input [12:0] i_valor2,
    output[12:0] o_valor
  );

  wire        sig1;
  wire        sig2;
  wire        sig_final;
  wire [3:0]  exp1;
  wire [3:0]  exp2;
  wire [7:0]  mant1;
  wire [7:0]  mant2;
  wire [5:0]  sum;
  wire [15:0] mul;

  
  

  assign sig1 = i_valor1[12];
  assign sig2 = i_valor2[12];
  
  assign exp1 = i_valor1[11:8];
  assign exp2 = i_valor2[11:8];
  
  assign mant1 = i_valor1[7:0];
  assign mant2 = i_valor2[7:0];
  
    
  // Signo
  assign  sig_final = sig1 ^ sig2;
  
  // Suma de los exponentes y resta del sesgo
  assign    sum = exp1 + exp2 - 4'b0111;
  
  // Multiplicacion de las mantisas
  assign  mul = mant1 * mant2;
  
  
  assign o_valor = {sig_final,sum[3:0],mul[15:8]};
  
  
endmodule
```

### Diagrama de bloque
![[Pasted image 20240205104247.png]]
















## Punto 4
## Codigo
``` verilog
module filtro_FIR_directo
#(
    parameter NB_INPUT      = 16,
    parameter NBF_INPUT     = 15,
    parameter NB_OUTPUT     = 16,
    parameter NBF_OUTPUT    = 15,
    parameter NB_COEFF      = 16,
    parameter NBF_COEFF     = 15
)
(
    input   signed [30:0] i_data, // Datos de entrada x[n] en formato S(16,15)
    output  signed [30:0] o_data, // Resultado y[n] en formato S(16,15)
    input                 i_en,
    input                 i_rst,
    input                 clk
);
localparam NB_ADD_INPUT = 18;
  
// Parametrizo los productos y suma
//localparam NB_ADD     = NB_COEFF  + NB_INPUT + 2;
localparam NB_ADD     = NB_ADD_INPUT + 2;
localparam NBF_ADD    = NBF_COEFF + NBF_INPUT;
localparam NBI_ADD    = NB_ADD    - NBF_ADD;
localparam NBI_OUTPUT = NB_OUTPUT - NBF_OUTPUT;
localparam NB_SAT     = (NBI_ADD) - (NBI_OUTPUT);
localparam NB_TRUC    = NB_INPUT  + NB_COEFF - NB_ADD_INPUT;
  
  //! Internal Signals
reg  signed [NB_INPUT         -1:0] register [3:1]; //! Registros para retardo
wire signed [         NB_COEFF-1:0] coeff    [3:0]; //! Coeficientes
wire signed [NB_ADD_INPUT     -1:0] prod     [3:0]; //! Productos
wire signed [NB_INPUT+NB_COEFF-1:0] prod_aux [3:0]; //! Productos auxiliar
wire signed [NB_ADD           -1:0] sum      [3:1]; //! Sumas
  
 //! Coeff = [-1 1/2 -1/4 1/8]
assign coeff[0] = 8'b1000_0000;
assign coeff[1] = 8'b0100_0000;
assign coeff[2] = 8'b1110_0000;
assign coeff[3] = 8'b0001_0000;
  
  //! Modelo de los registros de retardos
always @(posedge clk) begin:shiftRegister
    if (i_rst == 1'b1) begin //Reseteo de los registros
      register[1] <= {NB_INPUT{1'b0}};
      register[2] <= {NB_INPUT{1'b0}};
      register[3] <= {NB_INPUT{1'b0}};
    end else begin
      if (i_en == 1'b1) begin
        register[1] <= i_data;
        register[2] <= register[1];
        register[3] <= register[2];
      end
    end
  end
  

    //! Products
  assign prod_aux[0] = coeff[0] * i_data;
  assign prod_aux[1] = coeff[1] * register[1];
  assign prod_aux[2] = coeff[2] * register[2];
  assign prod_aux[3] = coeff[3] * register[3];
  
  //! Redondeo
  assign prod_aux[0]=(~|prod_aux[0][NB_TRUC-1:0])?prod_aux[0]:
  (prod_aux[0][NB_INPUT+NB_COEFF-1])?prod_aux[0]-(1 << (NB_TRUC - 1)):prod_aux[0]+(1 << (NB_TRUC - 1));
  assign prod_aux[1]=(~|prod_aux[1][NB_TRUC-1:0])?prod_aux[1]:
  (prod_aux[1][NB_INPUT+NB_COEFF-1])?prod_aux[1]-(1 << (NB_TRUC - 1)):prod_aux[0]+(1 << (NB_TRUC - 1));
  assign prod_aux[2]=(~|prod_aux[2][NB_TRUC-1:0])?prod_aux[2]:
  (prod_aux[2][NB_INPUT+NB_COEFF-1])?prod_aux[2]-(1 << (NB_TRUC - 1)):prod_aux[0]+(1 << (NB_TRUC - 1));
  assign prod_aux[3]=(~|prod_aux[3][NB_TRUC-1:0])?prod_aux[3]:
  (prod_aux[3][NB_INPUT+NB_COEFF-1])?prod_aux[3]-(1 << (NB_TRUC - 1)):prod_aux[0]+(1 << (NB_TRUC - 1));
  
  //! Truncado
  assign prod[0]=prod_aux[0][NB_INPUT+NB_COEFF-1:NB_TRUC];
  assign prod[1]=prod_aux[1][NB_INPUT+NB_COEFF-1:NB_TRUC];
  assign prod[2]=prod_aux[2][NB_INPUT+NB_COEFF-1:NB_TRUC];
  assign prod[3]=prod_aux[3][NB_INPUT+NB_COEFF-1:NB_TRUC];
  
  //! Sumas
  assign sum[1] = prod[0] + prod[1];
  assign sum[2] = sum[1]  + prod[2];
  assign sum[3] = sum[2]  + prod[3];
  
  //! Output
  //! En la primera linea de codigo, se realiza una operacion NOR entre los primeros bits que debo saturar para saber si alguno es 1, en caso de ser todos 0, la salida es 1.
  //! Aplico lo mismo luego para con and para saber si alguno es 0, en caso de ser todos 1, la salida es 1.
  //! Si esto es verdadero, se coloca a la salida NB_OUTPUT valores desde el valor NB_ADD-(NBI_ADD-NBI_OUTPUT), con la segunda se sabe resta se sabe cuanto valores de deben acortar y con la primera se los acota
  //! En la segunda linea se analiza si el bit mas significativo es positivo o negativo para saber a que valor saturar la salida
  assign o_os_data = ( ~|sum[3][NB_ADD-1 -: NB_SAT+1] || &sum[3][NB_ADD-1 -: NB_SAT+1]) ? sum[3][NB_ADD-(NBI_ADD-NBI_OUTPUT) - 1 -: NB_OUTPUT] :
                      (sum[3][NB_ADD-1]) ? {{1'b1},{NB_OUTPUT-1{1'b0}}} : {{1'b0},{NB_OUTPUT-1{1'b1}}};
  
  
endmodule
```

## Esquema optimizado
![[Pasted image 20240205103035.png]]