### Sintesis en Vivado
#### Estrategias de sintesis
En vivado se puede oimplementar distintas configuraciones para sintetizar nuestro codigo, estas haran que la herramienta modifique la forma en que lo hace
> Es recomendable usar la estrategia predeterminada
![[Pasted image 20240505125910.png]]

- **Estrategias:**
	- Optimizacion de area → Pocas o mas pequeños componentes
	- Esfuerzo(*Effort*) alto o medio → Invierte mas tiempo es sintesis(itera mas veces buscando la opcion mas optima)
		- Puede llegar a durar horas o dias
	- Rendimiento(*Perf optimize*) → Observa el rendimiento, especialmente la velocidad
	- Timpo de ejecucion(*runtime optimaze*) → Sintesis rapida
	- **Alternate Routability (Ruteabilidad Alternativa) →**  Esta estrategia de síntesis se centra en optimizar la ruteabilidad de la lógica sintetizada en el chip FPGA. Vivado considera diferentes rutas de conexión para los elementos lógicos y busca la mejor combinación para maximizar la ruteabilidad. 
	- **Area Multithreshold DSP (Umbral de área multi-DSP) →** Esta estrategia se enfoca en optimizar el uso de los bloques de procesamiento digital de señales (DSP) en el chip FPGA. Vivado establece umbrales de área específicos para los bloques DSP y optimiza el mapeo de la lógica del diseño para maximizar el uso eficiente de estos recursos.

##### Estrategia manual
- Tambien se pueden elegir los elementos de configuracion de debajo y cambiar uno por uno llegano a una estrategia personalizada.
	- -1 significa sin limites, si pongo 0 significa no usar ninguno en abosluto
1. **max_dsp:** Este parámetro se refiere al número máximo de bloques de procesamiento digital de señales (DSP) que se pueden utilizar en tu diseño. Puedes ajustar este valor para controlar el uso de recursos DSP en la síntesis.
2. **cascade_dsp:** Esta opción controla si se permite o no el encadenamiento (cascada) de bloques DSP en tu diseño. Habilitar esta opción puede permitir una mejor utilización de los recursos DSP al permitir que los bloques se encadenen para realizar operaciones más complejas.
3. **mac_bram y mac_uram:** Estos parámetros se refieren al tipo de memoria que se utiliza para implementar las multiplicaciones en los bloques MAC (Multiply-Accumulate) en tu diseño. Puedes especificar si prefieres utilizar bloques de RAM basados en bloques de memoria BRAM o bloques de memoria URAM más grandes y especializados.
4. **flatten_hierarchy:** Esta opción controla si se debe aplanar la jerarquía del diseño durante la síntesis. La aplanación de la jerarquía puede simplificar la implementación del diseño al reducir la complejidad de la estructura jerárquica.![[Pasted image 20240505125920.png]]
5. **fsm_extraction:** Este parámetro controla cómo se extraen y optimizan las máquinas de estado finito (FSM) en tu diseño durante la síntesis. Puedes ajustar esta opción para optimizar el rendimiento y la utilización de recursos de las FSM en tu diseño.
6. **resource_sharing:** Esta opción controla si se realiza o no la compartición de recursos durante la síntesis. La compartición de recursos permite reutilizar componentes de hardware para reducir el uso total de recursos y mejorar la eficiencia del diseño.


#### Procedimiento de Synthesis
1. Haz clic en **Run Synthesis** bajo las tareas de _SYNTHESIS_ del panel _Flow Navigator_.
    El proceso de síntesis se ejecutará en el archivo lab1.v (y todos sus archivos jerárquicos si existen). Cuando el proceso se complete, se mostrará un cuadro de diálogo _Synthesis Completed_ con tres opciones.
2. Selecciona la opción _Open Synthesized Design_ y haz clic en **OK** ya que queremos ver la salida de la síntesis antes de avanzar a la etapa de implementación.
    Haz clic en **Sí** para cerrar el diseño elaborado si se muestra el cuadro de diálogo.
3. Selecciona la pestaña **Project Summary** y comprende las diferentes ventanas.
    Si no ves la pestaña Project Summary, selecciona **Window > Project Summary** o haz clic en el icono **Project Summary** ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig29.png).
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig30.png)
    _Vista del Resumen del Proyecto_
    Haz clic en los diferentes enlaces para ver qué información proporcionan y cuáles te permiten cambiar las configuraciones de síntesis.
    
4. Haz clic en la pestaña **Table** en la pestaña **Project Summary**.
    Nota que hay un estimado de 3 LUTs y 8 IOs (4 de entrada y 4 de salida) que se utilizan.
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig31.png)
    _Resumen de estimación de utilización de recursos_
    
5. En _Flow Navigator_, bajo _Synthesis_ (expande _Open Synthesized Design_ si es necesario), haz clic en **Schematic** para ver el diseño sintetizado en una vista esquemática.
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig32.png)
    _Vista esquemática del diseño sintetizado_
    Nota que los IBUFs y OBUFs se instancian (añaden) automáticamente al diseño ya que la entrada y salida están amortiguadas. Las puertas lógicas se implementan en LUTs (1 entrada se enumera como LUT1, 2 entradas se enumeran como LUT2, y 3 entradas se enumeran como LUT3). Cuatro puertas en la salida del análisis RTL se asignan a 3 LUTs en la salida sintetizada.



### Procedimiento de Implementacion



1. Haz clic en **Run Implementation** bajo las tareas de _Implementation_ del panel _Flow Navigator_.
    El proceso de implementación se ejecutará en el diseño sintetizado. Cuando el proceso se complete, se mostrará un cuadro de diálogo _Implementation Completed_ con tres opciones. Puedes elegir cuántos trabajos quieres usar para implementar este diseño. En general, más trabajos consumen más recursos informáticos y menos tiempo de ejecución.
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/choose_jobs.png)
    _Selecciona los hilos (trabajos) que quieres usar para la implementación_
    
2. Selecciona **Open implemented design** y haz clic en **OK** ya que queremos ver el diseño implementado en la pestaña de vista de Dispositivo.
3. Haz clic en **Sí**, si se te solicita, para cerrar el diseño sintetizado. Se abrirá el diseño implementado.
4. En el panel _Netlist_, selecciona una de las redes (por ejemplo, led\_OBUF\[3\]) y nota que la red se muestra en la región de reloj X1Y2 en la pestaña de vista de Dispositivo (es posible que tengas que hacer zoom para verlo).
5. Si no está seleccionado, haz clic en el icono _Recursos de Enrutamiento_ ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig34.png) para mostrar los recursos de enrutamiento.
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig35.png)
    _Viendo el diseño implementado_
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig36.png)
    _Seleccionando una red_
6. Cierra la vista del diseño implementado seleccionando **Archivo > Cerrar Diseño Implementado**, y selecciona la pestaña **Project Summary** (es posible que tengas que cambiar a la vista de Diseño Predeterminado) y observa los resultados.
7. Selecciona la pestaña **Post-Implementation**.
    **Nota** que la utilización real de recursos es de 3 LUTs y 8 IOs. También indica que no se definieron restricciones de temporización para este diseño (ya que el diseño es combinacional).
    
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig37.png)
    _Resultados de implementación para el Boolean_
    Usando el Explorador de Windows, verifica que se ha creado el directorio **impl\_1** al mismo nivel que **synth\_1** bajo el directorio **lab1.runs**. El directorio **impl\_1** contiene varios archivos, incluidos los archivos de informe de implementación.
    
8. En Vivado, selecciona la pestaña **Reports** en el panel inferior (si no es visible, haz clic en _Window_ en la barra de menú y selecciona **Reports**), y haz doble clic en la entrada _Utilization Report_ bajo la sección _Place Design_. El informe se mostrará en el panel de vista auxiliar mostrando la utilización de recursos. Nota que, dado que el diseño es combinacional, no se utilizan registros.
    
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig38.png)
    
    _Informes disponibles para ver_
    


#### Realiza una Simulación de Temporización
1. Selecciona **Run Simulation > Run Post-Implementation Timing Simulation** en las tareas de _Simulation_ del panel _Flow Navigator_.
    Se lanzará el simulador Vivado utilizando el diseño implementado y **lab1\_tb** como el módulo de nivel superior.
    Usando el Explorador de Windows, verifica que se ha creado el directorio **timing** bajo el directorio **lab1.sim > sim\_1 > impl**. El directorio **timing** contiene archivos generados para ejecutar la simulación de temporización.
2. Haz clic en el botón **Zoom Fit** para ver la ventana de la forma de onda desde 0 hasta 200 ns.
3. Haz clic derecho en 50 ns (donde la entrada btns se establece en 0000b) y selecciona **Markers > Add Marker**.
4. De manera similar, haz clic derecho y añade un marcador alrededor de los 58.000 ns donde cambian los **leds**.
5. También puedes añadir un marcador haciendo clic en el botón Add Marker ( ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig39.png) ). Haz clic en el botón **Add Marker** y haz clic izquierdo alrededor de los 60 ns donde cambian los **e\_led**.
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig40.png)
    _Salida de simulación de temporización_
    Nota que monitoreamos la salida esperada del led a los 10 ns después de que cambia la entrada (ver el banco de pruebas), mientras que el retraso real es de aproximadamente 8 a 9.7 ns (dependiendo de la placa).
6. Cierra el simulador seleccionando **Archivo > Cerrar Simulación** sin guardar ningún cambio.



### Procedimiento de generacion del bitstrem
1. Asegúrate de que el cable Micro-USB esté conectado al conector JTAG PROG.
2. El Boolean y PYNQ-Z2 pueden alimentarse a través de la energía USB a través del JTAG PROG.
    Asegúrate de que la placa esté configurada para usar energía USB.
    
    ![image](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/boolean_sche.png)
    _Conexión de la placa para el Boolean_
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig42.png)
    _Conexión de la Placa para el PYNQ-Z2_
3. Enciende la placa.
4. Haz clic en la entrada **Generate Bitstream** bajo las tareas de _PROGRAM AND DEBUG_ del panel _Flow Navigator_.
    El proceso de generación del bitstream se ejecutará en el diseño implementado. Cuando el proceso se complete, se mostrará un cuadro de diálogo _Bitstream Generation Completed_ con tres opciones.
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig43.png)
    _Generación de Bitstream_
    Este proceso habrá generado un archivo **lab1.bit** bajo el directorio **lab1.runs > impl\_1**.
5. Selecciona la opción _Open Hardware Manager_ y haz clic en **OK**.
    La ventana del Administrador de Hardware se abrirá indicando el estado “desconectado”.
6. Haz clic en el enlace **Open target**.
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig44.png)
    _Abriendo un nuevo objetivo de Hardware_
7. Desde el menú desplegable, haz clic en **Auto Connect.**
    **Para PYNQ-Z2**:
    El estado de la Sesión de Hardware cambia de Desconectado al nombre del servidor y el dispositivo se resalta. También nota que el Estado indica que no está programado.
    
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig45.png)
    _Sesión del administrador de hardware abierta_
    Selecciona el dispositivo y verifica que lab1.bit esté seleccionado como el archivo de programación en la pestaña General.
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig46.png)
    _Archivo de Programación_
    **Para Boolean**:
    El estado de la Sesión de Hardware cambia de Desconectado al nombre del servidor y el dispositivo se resalta. También nota que el Estado indica que no está programado.
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/boolean_hwmg.png)
    _Sesión del administrador de hardware abierta_
    Selecciona el dispositivo y verifica que lab1.bit esté seleccionado como el archivo de programación en la pestaña General.
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/boolean_hw_dev_prop.png)
8. Haz clic en el enlace _Program device_ en la barra de información verde para programar el dispositivo FPGA objetivo. Otra forma es hacer clic derecho en el dispositivo y seleccionar _Program Device._
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig47.png)
    _Seleccionando programar el FPGA_
9. Haz clic en **Programar** para programar el FPGA.
    El LED DONE se encenderá cuando el dispositivo esté programado. Es posible que veas algunos otros LEDs encendidos dependiendo de la posición de los interruptores.
10. Verifica la funcionalidad cambiando los interruptores y observando la salida en los LEDs (Consulta el diagrama lógico anterior).
11. Cuando estés satisfecho, cierra la sesión del administrador de hardware seleccionando **Archivo > Cerrar Administrador de Hardware.**
12. Haz clic en **OK** para cerrar la sesión.
13. Apaga la placa.
14. Cierra el programa **Vivado** seleccionando **Archivo > Salir** y haz clic en **OK**.






