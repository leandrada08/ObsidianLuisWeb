
## Bases
### ![[Construccion TestBench VHDL#Test bench]]
### Observaciones importantes
- El modulo de TB no tiene puertos
- Debemos inicializar el bloque que queremos simular y conectar a señales internar del TB
## Control de tiempo
- Todo esto se utiliza para modelado

1. **Unidades de Tiempo en Verilog:**
   - Verilog no trabaja internamente con unidades de tiempo, por lo que no tiene una relación directa con el tiempo real.
   - El tiempo simulado en cualquier instancia del diseño se puede acceder utilizando la variable especial `$time`, que proporciona el tiempo transcurrido desde el inicio de la simulación.

2. **Retardos en Verilog:**
   - En Verilog, puedes insertar retardos en el código utilizando la directiva `#<numero>`, donde `<numero>` representa la cantidad de unidades de tiempo a esperar.
   - Cuando el simulador encuentra esta sentencia, detiene la ejecución de la sentencia hasta que haya transcurrido el número especificado de unidades de tiempo.
   - Una vez que se cumple el tiempo especificado, el control se libera de esa sentencia o bloque, permitiendo que otros procesos se ejecuten.

3. **Directiva de Control de Evento (`@`):**
   - La directiva `@` se utiliza para modelar el control basado en eventos.
   - Detiene la ejecución de la sentencia hasta que ocurra el evento especificado.
   - Esta construcción de control de tiempo se utiliza comúnmente para modelar lógica combinacional y secuencial en bloques procedurales.

4. **Timescale en Simulación:**
   - En simulación, es posible asignar una unidad de tiempo representativa a los retardos mediante la directiva `timescale`.
   - La directiva `timescale` se define como `timescale <time_unit>/<time_precision>`, donde `<time_unit>` define la unidad de tiempo para los retardos en la simulación, y `<time_precision>` define cómo se redondean antes de utilizarse en la simulación.
   - Por ejemplo, `timescale 1ns/100ps` significa que 1 nanosegundo es la unidad de tiempo y los retardos se redondearán a 100 picosegundos.

El control de tiempo en Verilog es fundamental para asegurarse de que el diseño digital se comporte de acuerdo con las especificaciones temporales. Las directivas de tiempo y las unidades de tiempo permiten describir de manera precisa cómo se deben ejecutar los eventos en la simulación, lo que es esencial para verificar el comportamiento correcto de un diseño digital antes de su implementación en hardware real.

## Generacion de señales
### Inizializacion de clk y rst
- Normalmente estas señales provienen de un oscilador de cristal fuera del chip o FPGA (clock) y un pulsador (reset).
- El Clock se distribuye o encamina utilizando árboles de reloj (clock trees). Se trata de rutas especialmente diseñadas que llevan los relojes a los registros causando un mínimo sesgo (skew) a estas señales especiales.
- En la FPGA las fuentes de clock externas se deben asociar a uno de los pines dedicados para este propósito. En Xilinx, la asociación de pines se define en un archivo de constraints con la extensión XDC (Xilinx Design Constraints). Esta extensión se adoptó en Vivado reemplazando al archivo UCF (User Constraint File) usado en ISE.
- En la simulación, estas señales son generadas como estímulos para poder llevar a cabo la verificación del código RTL, como se muestra en el siguiente ejemplo.
![[Pasted image 20231012124834.png]]

### Generacion de clk
- Usamos un bloque always para poder simular un clk(caso 1)
- Esto solo lo debemos hacer si queremos hacer una prueba continua
- Tambien podriamos hacer de a 1 los clock para cuando los necesitamos(caso 2)
	- Esto nos sirve si queremos usar TDD
#### Caso 1

``` verilog
always
begin
	clk = 1'b1;
	#20; \\Buscarmos que este numero multiplicado por la escala sea medio periodo
	clk = 1'b0;
	#20;
end
```

#### Caso 2
- En este caso hay que hacerlo manualmente y luego de cada secuencia de señal probar el estado de una señal por display
## Control de Simulaciones
Verilog provee varias funciones para el control de las simulaciones.
- *$finish:* Sale de la simulación.
- *$stop:* Detiene la simulación, que luego puede ser retomada desde el punto de suspensión.
- *$display:* Imprime una salida.
- *$monitor:* Es similar a $display pero está activo todo el tiempo. Solo puede ejecutarse un $monitor a la vez en toda la simulación.
- *\$fmonitor,\$fdisplay:* Escriben los valores en archivos, que deben ser abiertos previamente con la función$fopen.
- *\$readmemb,\$readmemh:* Permiten la carga de datos desde archivos en formato binario o hexadecimal a memorias.





## TB con archivo
### Definicion
Estructura de datos utilizadas para representar informacion almacenada en memoria. En VHDL, los archivos se utilizan principalmente para la simulacion y verificacion de diseños digitales.
![[Pasted image 20230606090020.png|300]]

### Uso

*En declaracion de variables:*
1. Genero un banco de registros para almacenar el contenido del file

``` verilog
reg[Ancho:0] read_data [0:Largo];
```

2. Genero una variable para la escritura

``` verilog
integer write_data;
```

*En un bloque initial*
3. Leo un archivo

``` verilog
$readmemb("Direccion_Del_Archivo_Lectura/Nombre_Archivo_Lectura.txt", read_data);
```

4. Abro el archivo que quiero escribir

``` verilog
write_data = $fopen("Direccion_Del_Archivo_Escritura/Nombre_Archivo_Escritura.txt");
```

*Donde lo requerimos en el codigo*
5. Leo una linea del registro con el contenido de la memoria
	- En este ejemplo nuestro archivo contenia el valor de 3 señales

``` verilog
for(i=0;i<6;i=i+1) begin
	{a,b,c}=read_data[i];
end
```

6. Escribo mi archivo de escritura

```
$fdisplay(write_data,"%b_%b_%b_%b", a, b, sum, carry);
```

7. Cierrro el archivo de escritur
``` verilog
$fclose(write_data);
```

## Observaciones
- Las variables conectadas a la entrada de nuestro bloque de prueba deben ser **reg** y las que se conectan a las salidas deben ser **wire**