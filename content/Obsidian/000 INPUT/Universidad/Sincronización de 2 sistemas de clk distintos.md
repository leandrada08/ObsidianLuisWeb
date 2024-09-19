- Si el sistema tiene clock que sea multiplo uno del otro(por ejemplo 10 y 5 o 10 y 20) se puedo hacer mediante contadores
- Si el sistema tienen clock que no son multiplos, como 10 y 4, se pueden hacer un sistema con 2 bloques always activados por cada clk y una bandera que comunique ambos.

``` verilog

always @(posedge clock_fast) begin
	lantch <= signal_fast
end

always @(posedge clock_slow) begin
	signal_sinc <= lantch
end
```