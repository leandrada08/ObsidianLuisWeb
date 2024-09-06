

## Uso de Constraints en Vivado

### Añadir Constraints a un Proyecto

Para que los constraints tengan efecto, deben añadirse a tu proyecto en Vivado. Esto se hace generalmente a través de archivos XDC (Xilinx Design Constraints).

#### Archivo XDC
Un archivo XDC es un archivo de texto que contiene todos los constraints para tu diseño. Este archivo se añade al proyecto de Vivado y se utiliza durante la síntesis y la implementación para guiar el proceso de diseño.

**Ejemplo de Archivo XDC:**
```tcl
# Definición del reloj principal
create_clock -period 10.000 [get_ports clk]

# Restricciones de entrada
set_input_delay -clock clk -max 3.0 [get_ports {input1}]
set_input_delay -clock clk -min 1.0 [get_ports {input1}]

# Restricciones de salida
set_output_delay -clock clk -max 4.0 [get_ports {output1}]
set_output_delay -clock clk -min 2.0 [get_ports {output1}]

# Fijación de pines específicos
set_property PACKAGE_PIN E3 [get_ports clk]
set_property IOSTANDARD LVCMOS33 [get_ports clk]

# Definición de una ruta falsa
set_false_path -from [get_pins {reg1/Q}] -to [get_pins {reg2/D}]

# Asignación de Pblocks
create_pblock pblock_1
resize_pblock [get_pblocks pblock_1] -add {SLICE_X12Y100:SLICE_X15Y105}
add_cells_to_pblock [get_pblocks pblock_1] [get_cells {u1/u2}]

# Definir rutas de señal críticas
set_property LOC SLICE_X12Y100 [get_cells {critical_path_register}]
set_property BEL A6LUT [get_cells {critical_path_register}]
```

#### Integración en Vivado
Para añadir un archivo XDC a tu proyecto en Vivado, sigue estos pasos:
1. Abre tu proyecto en Vivado.
2. En el panel de **Flow Navigator**, selecciona **Add Sources**.
3. Selecciona **Add or Create Constraints**.
4. Añade tu archivo XDC y haz clic en **Finish**.

### 5.2. Herramientas de Análisis de Timing

Vivado proporciona herramientas poderosas para el análisis de timing, que te permiten verificar y optimizar tu diseño.

#### Uso del Informe de Timing
El informe de timing en Vivado proporciona una visión detallada de las rutas de timing en tu diseño, identificando las rutas críticas y los márgenes de setup y hold.

1. **Generar Informe de Timing:**
   - Después de la síntesis o la implementación, selecciona **Report Timing Summary** en el panel de **Flow Navigator**.
2. **Interpretar el Informe de Timing:**
   - **Slack:** Mide cuánto tiempo adicional hay disponible. Un slack positivo indica que el diseño cumple con los requisitos de timing.
   - **Ruta Crítica:** Identifica las rutas con el menor margen de tiempo. Estas son las rutas que más probablemente limiten la frecuencia operativa de tu diseño.

#### Identificación de Violaciones de Timing
1. **Violaciones de Setup:** Ocurren cuando la señal no llega a tiempo al flip-flop para cumplir con el tiempo de setup.
2. **Violaciones de Hold:** Ocurren cuando la señal cambia demasiado pronto después del borde del reloj, violando el tiempo de hold.


## Creacion de timing constrain asistido de Vivado
#### Acceso a los Constraints
Después de completar la síntesis inicial, los constraints se gestionan a través de la opción 'Open Synthesized Design'.
- La herramienta vivada nos da una guia para crear nuestro constrain completo → **Constraints Wizard**
- Pero a nosotros en esta seccion solo nos interesa el apartado de **Edit Timing Constraints**


#### Utilización de Archivos XDC
Vivado requiere la adición de un archivo .xdc (Xilinx Design Constraints) para definir los constraints. Este archivo se integra en la jerarquía de archivos del proyecto, dentro de la sección 'Constraints', y es fundamental para establecer los límites temporales del diseño.


### Edit Timing Constrains
![[Pasted image 20240505204537.png]]
- Sobre la columna izquierda, se puede definir los parametros que influenzan el resultado del STA.

>Atención: en la sección clock no se está definiendo el reloj, sino parámetros que resumen su comportamiento de manera creíble. Esto no significa definir el reloj.

1. Lo primero que hacemos es apretar sobre **Create Clock** 
	- Tecnicamente, bastaria con ocuparse solamente de este elemento para dar lugar a una STA
	- Ahi se abrira la siguiente ventana
![[Pasted image 20240505213708.png]]
> En la sección command se reproduce el comando que, en función de lo anterior, se devuelve al archivo .xdc.

- Clock name no es el nombre de la señal, es el nombre del constrain

#### Specify Clock Source Object

Esta ventana le permite hacer un poco de investigación sobre los pines involucrados en el proyecto. En este caso, debe seleccionar un proyecto que contenga un reloj para seleccionar esta señal:
![[Pasted image 20240506185014.png]]
En principio, ya este constraint es suficiente para realizar una buena STA.
A continuación, debe definir el período y el ciclo de trabajo del reloj a través de la siguiente pantalla:
![[Pasted image 20240506185054.png]]
Al hacerlo, hemos añadido el siguiente comando dentro del archivo .xdc.
![[Pasted image 20240506185115.png]]

#### Otras Opciones de Constraints
Además de la creación de clocks, Vivado ofrece una variedad de opciones para ajustar el comportamiento temporal del diseño:
- **Create Generated Clock:** Este constraint se utiliza cuando se deriva un nuevo clock de uno existente, a unque su aplicación es menos común en proyectos con componentes predefinidos.
- **Set Clock Latency:** Agrega una latencia al clock para una definición más precisa de su comportamiento temporal.
- **Set Clock Uncertainty:** Este parámetro representa la variabilidad en la sincronización, una consideración importante para entornos de diseño de alta precisión.
	- Tanto para definir la latencia como la uncertainty, es necesario conocer la fuente (que puede ser, por ejemplo, un oscilador que da lugar al reloj

- **Set Clock Groups:** Útil para proyectos con múltiples clocks, esta opción permite agrupar clocks relacionados para una gestión más eficiente de los constraints temporales.
- **Set Input Jitter:** permite definir el jitter del reloj, es decir, una variación espuria de la frecuencia que puede deberse directamente al reloj de entrada o a un jitter que se crea intermanente (se denomina system jitter);
- **Set External Delay:** rara vez se produce sin FPGA ya con reloj a bordo, sin embargo, a veces hay tarjetas de ASIC prototyping diseñadas para albergar más FPGA. Bueno, estas tarjetas se utilizan para alojar proyectos enormes, que requieran más de un bloque de FPGA. En este caso, es necesario tener la sincronización entre esos bloques que se refieran al mismo proyecto;
	- El reloj se puede realizar tanto interna como externamente. Por ejemplo, se puede pensar en tener dos FPGA sincrónicas entre ellas: en este caso se puede enviar el reloj de la primera a la segunda FPGA.
- **Set Input Delay:** permite definir el desplazamiento de entrada, es decir, el retraso entre la entrada y el reloj;
- **Set Output Delay:** permite definir el desplazamiento de salida, es decir, el retraso con el que se propagan las señales hacia los pines de salida.
**Assertion:** comprobaciones automáticas del cumplimiento de las restricciones.

### Verificación de Constraints
Una vez aplicados los timing constraints, es crucial verificar su cumplimiento. Esto se realiza a través de la herramienta 'Report Timing Summary', que proporciona una visión detallada de parámetros como el Pulse Width y el Worst Negative Slack, permitiendo ajustes finales para garantizar la integridad temporal del diseño.
![[Pasted image 20240508103347.png]]
- Yendo a *intraclock paths*, si ottiene il numero dei path che vengono violati
![[Pasted image 20240508103509.png]]
- Tambien podemos analizr cada path del sistema
![[Pasted image 20240508103540.png]]
![[Pasted image 20240508103546.png]]
![[Pasted image 20240508103555.png]]

### Retrasos de entrada
Si el problema es el constraint del tiempo de hold, si puo introdurre un maggiore *offset in ingreso:*
![[Pasted image 20240508103706.png]]
En el siguiente caso seleccionamos todas las segnales de ingrso y colocamos un offset de ingreso de 0,5ns
![[Pasted image 20240508103747.png]]





