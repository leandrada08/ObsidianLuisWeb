**Nombre:** Andrada Luis Elian
**DNI:** 43362912

## Punto 1
### a) Dibujar el grafico de flujo de datos (DFG), y mapearlo en una arquitectura (FDA).
![[Pasted image 20240404203250.png]]

### b) c) Escribir el codigo: aplicar redondeo, truncado, overflow y saturacion
``` verilog
module corrector_fase
#(
    parameter NB_INPUT      = 16,
    parameter NB_OUTPUT     = 16,
    parameter NB_COEFF      = 16,
    parameter NBF_INPUT     = 15,
    parameter NBF_OUTPUT    = 15,
    parameter NBF_COEFF     = 15
)
(
    input   signed [NB_INPUT-1:0] in_real, // Datos de entrada x[n] en formato S(16,15)
    input   signed [NB_INPUT-1:0] in_img, // Datos de entrada x[n] en formato S(16,15)
    output  signed [NB_INPUT-1:0] out_phase, // Resultado y[n] en formato S(16,15)
    input                 i_rst,
    input                 clk
);
  
// Parametros locales
localparam NB_PROD      = NB_INPUT  + NB_COEFF + 3;
localparam NB_PROD_IN   = NB_INPUT  + NB_OUTPUT;
localparam NB_TRUC      = NB_PROD   - NB_COEFF;
localparam NB_TRUC_IN   = NB_PROD_IN- NB_INPUT;
localparam NBF_PROD     = NBF_IMPUT + NB_COEFF;
localparam NBI_PROD     = NB_PROD   - NBF_PROD;
localparam NB_SAT       = NBI_PROD  - NBI_OUTPUT;

// Variables locales
    // Auxiliares de productos
wire signed [NB_PROD_IN : 0] mixer_in_real;
wire signed [NB_PROD_IN : 0] mixer_in_img;
wire signed [NB_PROD    : 0] delay_real_aux[2:0];
wire signed [NB_PROD    : 0] delay_img_aux[2:0];
wire signed [NB_PROD    : 0] mixer_real_aux[2:0];
wire signed [NB_PROD    : 0] mixer_img_aux[2:0];
wire signed [NB_PROD    : 0] offset;
wire signed [NB_PROD    : 0] offset_delay_aux[2:0];
wire signed [NB_PROD    : 0] phase_corr_aux;
  

    // Registros
reg signed [NB_COEFF    : 0] delay_real[2:0];
reg signed [NB_COEFF    : 0] delay_img[2:0];
reg signed [NB_COEFF    : 0] mixer_real[2:0];
reg signed [NB_COEFF    : 0] mixer_img[2:0];
reg signed [NB_COEFF    : 0] offser_delay[1:0];
reg signed [NB_COEFF    : 0] phase_corr;
  
    // Constantes
reg signed [NB_COEFF    : 0] Kp;
reg signed [NB_COEFF    : 0] Ki;
reg signed [NB_COEFF    : 0] A[2:1];
reg signed [NB_COEFF    : 0] B[2:0];
  
    //Registro de acumulacion
reg signed [NB_PROD   : 0] phase;
  

always @(posedge clk) begin
    if(i_rst==1'b1) begin
    mixer_real[2] <= {NB_PROD_IN{1'b0}};
    mixer_real[1] <= {NB_PROD_IN{1'b0}};
    mixer_real[0] <= {NB_PROD_IN{1'b0}};
  
    mixer_img[2] <= {NB_PROD_IN{1'b0}};
    mixer_img[2] <= {NB_PROD_IN{1'b0}};
    mixer_img[2] <= {NB_PROD_IN{1'b0}};
  
    delay_real[2] <= {NB_PROD{1'b0}};
    delay_real[1] <= {NB_PROD{1'b0}};
    delay_real[0] <= {NB_PROD{1'b0}};
  
    delay_img[2] <= {NB_PROD{1'b0}};
    delay_img[1] <= {NB_PROD{1'b0}};
    delay_img[0] <= {NB_PROD{1'b0}};
  
    offset_delay[0] <={NB_PROD{1'b0}};
    offset_delay[1] <={NB_PROD{1'b0}};
  
    phase_corr <= {NB_PROD{1'b0}};
  
    phase <= {NB_PROD{1'b0}};
    end
    else begin
        mixer_real[2] <= mixer_real[1];
        mixer_real[1] <= mixer_real[0];
        mixer_real[0] <= mixer_in_real[NB_PROD_IN-1:NB_TRUC_IN];//trunco
        mixer_img[2] <= mixer_img[1];
        mixer_img[2] <= mixer_img[1];
        mixer_img[2] <= mixer_in_img[NB_PROD-1:NB_TRUC_IN];//trunco
        delay_real[2] <= delay_real[1];
        delay_real[1] <= delay_real[0];
        delay_real[0] <= delay_real_aux[0][NB_PROD-1:NB_TRUC];
        delay_img[2] <= delay_img[1];
        delay_img[1] <= delay_img[0];
        delay_img[0] <= delay_img_aux[0][NB_PROD-1:NB_TRUC];
        offset_delay[0] <= offset_delay[1];
        offset_delay[1] <= offset[NB_PROD-1:NB_TRUC];//Trunco
        phase_corr <= phase_corr_aux[NB_PROD-1:NB_TRUC]; //trunco
        phase <= phase + phase_corr;
    end
end
  
  
assign mixer_in_real = in_img * phase;
assign mixer_in_img = - in_real * phase;
//Redondeo
assign mixer_in_real=(~|mixer_in_real[NB_TRUC_IN-1:0])?mixer_in_real:
                        (mixer_in_real[NB_PROD_IN-1])?mixer_in_real-(1 << (NB_TRUC_IN - 1)):mixer_in_real+(1 << (NB_TRUC_IN - 1));
assign mixer_in_img=(~|mixer_in_img[NB_TRUC_IN-1:0])?mixer_in_img:
                        (mixer_in_img[NB_PROD_IN-1])?mixer_in_img-(1 << (NB_TRUC_IN - 1)):mixer_in_img+(1 << (NB_TRUC_IN - 1));
  
  
assign delay_real_aux[2] = delay_real[2] * A[2];
assign delay_real_aux[1] = delay_real[1] * A[1];

  
assign delay_img_aux[2] = delay_img[2] * A[2];
assign delay_img_aux[1] = delay_img[1] * A[1];
  
assign mixer_real_aux[2] = mixer_real[2] * B[2];
assign mixer_real_aux[1] = mixer_real[1] * B[1];
assign mixer_real_aux[0] = mixer_real[0] * B[0];
  
assign mixer_img_aux[2] = mixer_img[2] * B[2];
assign mixer_img_aux[1] = mixer_img[1] * B[1];
assign mixer_img_aux[0] = mixer_img[0] * B[0];
  
assign delay_real_aux[0] = mixer_real_aux[0] + mixer_real_aux[1] + mixer_real_aux[2] - delay_real_aux[2] - delay_real_aux[1];
assign delay_img_aux[0] = mixer_img_aux[0] + mixer_img_aux[1] + mixer_img_aux[2] - delay_img_aux[2] - delay_img_aux[1];
// Redondeo
assign delay_real_aux[0]=(~|delay_real_aux[0][NB_TRUC-1:0])?delay_real_aux[0]:
                        (delay_real_aux[0][NB_PROD-1])?delay_real_aux[0]-(1 << (NB_TRUC - 1)):delay_real_aux[0]+(1 << (NB_TRUC - 1));
assign delay_img_aux[0]=(~|delay_img_aux[0][NB_TRUC-1:0])?delay_img_aux[0]:
                        (delay_img_aux[0][NB_PROD-1])?delay_img_aux[0]-(1 << (NB_TRUC - 1)):delay_img_aux[0]+(1 << (NB_TRUC - 1));
  

assign offset = delay_real[2]*delay_real[0] + delay_img[2]*delay_img[0];
//Redondeo
assign Input_img_aux=(~|Input_img_aux[NB_TRUC-1:0])?Input_img_aux:
                        (Input_img_aux[NB_PROD-1])?Input_img_aux-(1 << (NB_TRUC - 1)):Input_img_aux+(1 << (NB_TRUC - 1));
  
  
assign offset_delay_aux[0] = Kp * offset_delay[0];
assign offset_delay_aux[1] = Kp * offset_delay[1];
assign offset_delay_aux[2] = Ki * offset_delay[1];
  
//Overflow
assign phase_corr_aux = phase_corr + offset_delay_aux[0] + offset_delay_aux[2] - offset_delay_aux[1];
  
  
assign out_phase = ( ~|phase[NB_ADD-1 -: NB_SAT+1] || &phase[NB_ADD-1 -: NB_SAT+1]) ? phase[NB_ADD-(NBI_ADD-NBI_OUTPUT) - 1 -: NB_OUTPUT] :
                    (phase[NB_ADD-1]) ? {{1'b1},{NB_OUTPUT-1{1'b0}}} : {{1'b0},{NB_OUTPUT-1{1'b1}}};
  
endmodule
```


### TB

``` verilog
`timescale 1ns / 1ps // Especifica la escala de tiempo para la simulación
  
module corrector_fase_tb; // Definición del test bench
  
    // Parámetros y constantes
    parameter NB_INPUT      = 16;
    parameter NB_OUTPUT     = 16;
    parameter NB_COEFF      = 16;
    parameter NBF_INPUT     = 15;
    parameter NBF_OUTPUT    = 15;
    parameter NBF_COEFF     = 15;
    parameter CLK_PERIOD    = 10;
  
    // Definición de señales de entrada
    reg signed in_real;
    reg signed in_img;
    reg in_clk;
    reg in_reset;
  

    // Definir de señales de salida
    wire out_phase;
  
    // Instanciar el módulo bajo prueba
    corrector_fase#(
        .NB_COEFF(NB_COEFF),
        .NB_INPUT(NB_INPUT),
        .NB_OUTPUT(NB_OUTPUT),
        .NBF_OUTPUT(NBF_OUTPUT),
        .NBF_INPUT(NBF_INPUT),
        .NBF_COEFF(NBF_COEFF)
    )u_corrector_fase(
        .in_real(in_real),
        .in_img(in_img),
        .out_phase(out_phase),
        .clk(in_clk),
        .i_rst(in_reset)
    );
  
    // Generar el reloj
    always #((CLK_PERIOD)/2) clk = ~clk;
  
    always@(posedge clock) begin
        in_real <= $random;
        in_img <= $random;
     end
    // Inicialización
    initial begin
        in_clk = 0; // Inicializar reloj en bajo
        in_reset = 1; // Inicializar señal de reset en activo bajo
        #20;
        in_reset = 0;
        #10000;
        // Agregar más inicializaciones si es necesario
        $finish;
    end
  
  
endmodule
```

## Punto 4
![[Pasted image 20240406110435.png]]