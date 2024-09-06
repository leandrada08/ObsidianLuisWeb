

## Pasos

### Crear un Proyecto Vivado

#### Iniciar Vivado y crear un proyecto vacío apuntando a XC7S50CSGA324-1 (para Boolean) o XC7Z020CLG400-1 (para PYNQ-Z2), seleccionando Verilog como lenguaje objetivo. Usa los archivos lab1.v y lab1\_zynq.xdc (para PYNQ-Z2) y lab1\_spartan.xdc (para Boolean) de _.\\sources\\lab1\\_.

1. Abre Vivado seleccionando **Inicio > Xilinx Design Tools > Vivado 2021.2**.
2. Haz clic en **Crear Nuevo Proyecto** para iniciar el asistente. Verás el cuadro de diálogo _Crear un Nuevo Proyecto Vivado_. Haz clic en **Siguiente**.
3. Haz clic en el botón Examinar del campo _Ubicación del proyecto_ del formulario **Nuevo Proyecto**, navega hasta **{TUTORIAL}**, es decir, **C:\\vivado\_tutorial**, y haz clic en **Seleccionar**.
4. Ingresa **lab1** en el campo _Nombre del proyecto_. Asegúrate de que la casilla _Crear subdirectorio del proyecto_ esté marcada. Haz clic en **Siguiente**.
    
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig3.png)
    
    _Entrada de Nombre y Ubicación del Proyecto_
    
5. Selecciona la opción **Proyecto RTL** **ÚNICAMENTE** en el formulario _Tipo de Proyecto_ y haz clic en **Siguiente**.
    
6. Usando los botones desplegables, selecciona **Verilog** como _Lenguaje Objetivo_ y _Lenguaje del Simulador_ en el formulario _Agregar Fuentes_.
    
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig4.png)
    
    _Seleccionando el Lenguaje Objetivo y del Simulador_
    
7. Haz clic en el botón **Más Azul**, luego haz clic en **Agregar Archivos…** y navega hasta el directorio **{sources}\\{BOARD}\\lab1**, selecciona _lab1.v_ y haz clic en **OK**.
    
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig5.png)
    
    _Agregando archivos fuente_
    
    Si no está ya marcada, marca **Copiar fuentes en el proyecto**
    
8. Haz clic en **Siguiente** para llegar al formulario _Agregar Restricciones_.
    
9. Haz clic en el botón **Más Azul**, luego haz clic en **Agregar Archivos…** y navega hasta el directorio **{SOURCES}\\lab1** (si es necesario), selecciona _lab1\_pynq.xdc_ (para PYNQ-Z2) o _lab1\_boolean.xdc_ (para Boolean) y haz clic en **OK** (si es necesario), y luego haz clic en **Siguiente.**
    
    El archivo de restricciones de diseño de Xilinx asigna las ubicaciones físicas de IO en FPGA a los interruptores y LEDs ubicados en la placa. Esta información se puede obtener a través del esquema de la placa o la guía del usuario de la placa.
    
10. En el formulario _Parte Predeterminada_, usa la opción **Partes** y varios campos desplegables de la sección **Filtro**. Selecciona el **XC7Z020clg400-1** (para PYNQ-Z2) o **xc7s50csga-1** (para Boolean).
    
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig6.png)
    
    _Selección de Parte para el PYNQ_
    
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/boolean_select.png)
    
    _Selección de Parte para el Boolean_
    
    También puedes seleccionar la opción **Placas**, `tulembedded.com` para la placa PYNQ-Z2 o `RealDigital.org` para la placa Boolean bajo el filtro _Proveedor_ y seleccionar la placa apropiada. Nota que Boolean y PYNQ-Z2 pueden no estar listadas ya que no están en la base de datos de herramientas. Si no están listadas, puedes descargar los archivos de las placas deseadas desde la página web del proveedor de la placa respectiva.
    
11. Haz clic en **Siguiente**.
    
12. Haz clic en **Finalizar** para crear el proyecto Vivado.

Usa el Explorador de Windows y mira el directorio **{TUTORIAL}\\lab1**. Encontrarás que se han creado los directorios lab1.cache y lab1.srcs y el archivo de proyecto lab1.xpr (Vivado). El directorio lab1.cache es un marcador de posición para la base de datos del programa Vivado. Se crean dos directorios, constrs\_1 y sources\_1, bajo el directorio lab1.srcs; en lo profundo de ellos, se colocan respectivamente los archivos lab1\_.xdc (restricción) y lab1.v (fuente) copiados.

```
lab1
│  lab1.xpr
│  struc.txt
│  
├─lab1.cache
│  └─wt
│          project.wpc
│          
├─lab1.hw
│      lab1.lpr
│      
├─lab1.ip_user_files
├─lab1.sim
└─lab1.srcs
    ├─constrs_1
    │  └─imports
    │      └─lab1
    │              lab1_spartan.xdc
    │              
    └─sources_1
        └─imports
            └─lab1
                    lab1.v
```

### Abre el archivo lab1.v y analiza el contenido.

1. En el panel _Sources_, haz doble clic en la entrada **lab1.v** para abrir el archivo en modo texto.
    
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig8.png)
    
    _Abriendo el archivo fuente_
    
2. Observa en el código Verilog que la primera línea define la directiva de escala de tiempo para el simulador. Las líneas 2-4 son líneas de comentario que describen el nombre del módulo y el propósito del módulo.
    
3. La línea 7 define el comienzo (marcado con la palabra clave **module**) y la línea 17 define el final del módulo (marcado con la palabra clave **endmodule**).
    
4. Las líneas 8-9 definen los puertos de entrada y salida, mientras que las líneas 12-15 definen la funcionalidad real.
    

### Abre el archivo lab1\_{BOARDS}.xdc y analiza el contenido.

#### Para PYNQ-Z2:

1. En el panel _Sources_, expande la carpeta _Constraints_ y haz doble clic en la entrada **lab1\_pynq.xdc** para abrir el archivo en modo texto.
    
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig9.png)
    
    _Abriendo el archivo de restricciones_
    
2. Las líneas 5-8 definen las ubicaciones de los pines para los botones de entrada y las líneas 13-16 definen las ubicaciones de los pines para los LEDs de salida.
    

#### Para Boolean:

1. En el panel _Sources_, expande la carpeta _Constraints_ y haz doble clic en la entrada **lab1\_boolean.xdc** para abrir el archivo en modo texto.
    
    ![image](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/boolean_constr.png)
    
2. Las líneas 17-20 definen las ubicaciones de los pines para los botones de entrada y las líneas 10-13 definen las ubicaciones de los pines para los LEDs de salida.
    

### Realiza el análisis RTL en el archivo fuente.

Expande la entrada _Open Elaborated Design_ bajo las tareas de _RTL Analysis_ del panel _Flow Navigator_ y haz clic en **Schematic**.

El modelo (diseño) será elaborado y se mostrará

 una vista lógica del diseño.

![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig10.png)

_Vista Lógica del Diseño_

### Simula el Diseño usando el Simulador de Vivado

### Añade el archivo de banco de pruebas lab1\_tb.v.

1. Haz clic en **Add Sources** bajo las tareas de _Project Manager_ del panel _Flow Navigator_.
    
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig11.png)
    
    _Agregar Fuentes_
    
2. Selecciona la opción _Add or Create Simulation Sources_ y haz clic en **Siguiente**.
    
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig12.png)
    
    _Seleccionando la opción de Fuentes de Simulación_
    
3. En el formulario _Add Sources Files_, haz clic en el botón **Más Azul** y luego en **Agregar Archivos…**.
    
4. Navega hasta la carpeta **{SOURCES}\\lab1** y selecciona _lab1\_tb.v_ y haz clic en **OK**.
    
5. Haz clic en **Finalizar**.
    
6. Selecciona la pestaña _Sources_ y expande el grupo _Simulation Sources_.
    
    El archivo lab1\_tb.v se agrega bajo el grupo _Simulation Sources_ y **lab1.v** se coloca automáticamente en su jerarquía como una instancia dut (dispositivo bajo prueba).
    
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig13.png)
    
    _Jerarquía de Fuentes de Simulación_
    
7. Usando el Explorador de Windows, verifica que se haya creado el directorio **sim\_1** al mismo nivel que los directorios _constrs\_1_ y _sources\_1_ bajo el directorio _lab1.srcs_, y que se haya colocado una copia de lab1\_tb.v bajo **lab1.srcs > sim\_1 > imports > lab1**.
    
8. Haz doble clic en **lab1\_tb** en el panel _Sources_ para ver su contenido.
    
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig14.png)
    
    _El banco de pruebas autocomprobante_
    
    El banco de pruebas define el tamaño del paso de simulación y la resolución en la línea 1. La definición del módulo del banco de pruebas comienza en la línea 5. La línea 15 instancia el DUT (dispositivo/módulo bajo prueba). Las líneas 17 a 25 definen la misma funcionalidad del módulo para el cálculo del valor esperado. Las líneas 27 a 38 definen la generación de estímulos y comparan la salida esperada con lo que proporciona el DUT. La línea 40 finaliza el banco de pruebas. La tarea **$display** imprimirá el mensaje en la ventana de la consola del simulador cuando se ejecute la simulación.
    

#### Simula el diseño durante 200 ns usando el simulador de Vivado.

1. Selecciona **Settings** bajo las tareas de _Project Manager_ del panel _Flow Navigator_.
    
    Aparecerá un formulario **Settings** que muestra el formulario de propiedades de **Simulation**.
    
2. Selecciona la pestaña **Simulation** y establece el valor **Simulation Run Time** en 200 ns y haz clic en **OK**.
    
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig15.png)
    
    _Estableciendo el tiempo de ejecución de la simulación_
    
3. Haz clic en **Simulation > Run Simulation > Run Behavioral Simulation** bajo las tareas de _Project Manager_ del panel _Flow Navigator_.
    
    El banco de pruebas y los archivos fuente se compilarán y se ejecutará el simulador de Vivado (asumiendo que no haya errores). Verás una salida del simulador como la mostrada a continuación.
    
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig16.png)
    
    _Salida del simulador_
    
    Verás cuatro vistas principales: (i) _Scopes,_ donde se muestra la jerarquía del banco de pruebas así como las instancias de glbl, (ii) _Objects,_ donde se muestran las señales de nivel superior, (iii) la ventana de la forma de onda, y (iv) _Tcl Console_ donde se muestran las actividades de simulación. Nota que, dado que se utiliza un banco de pruebas autocomprobante, los resultados se muestran a medida que se ejecuta la simulación.
    
    Nota que se crea el directorio **lab1.sim** bajo el directorio **lab1**, junto con varios directorios de nivel inferior.
    
    ```
    //Estructura de directorios después de ejecutar la simulación conductual
    lab1.sim  
    └─sim_1
       └─behav
          └─xsim
                │  compile.bat
                │  compile.log
                │  elaborate.bat
                │  elaborate.log
                │  glbl.v
                │  lab1_tb.tcl
                │  lab1_tb_behav.wdb
                │  lab1_tb_vlog.prj
                │  simulate.bat
                │  simulate.log
                │  xelab.pb
                │  xsim.ini
                │  xvlog.log
                │  xvlog.pb
                │  
                └─xsim.dir
                   ├─lab1_tb_behav
                   │  │  Compile_Options.txt
                   │  │  TempBreakPointFile.txt
                   │  │  xsim.dbg
                   │  │  xsim.mem
                   │  │  xsim.reloc
                   │  │  xsim.rlx
                   │  │  xsim.rtti
                   │  │  xsim.svtype
                   │  │  xsim.type
                   │  │  xsim.xdbg
                   │  │  xsimcrash.log
                   │  │  xsimk.exe
                   │  │  xsimkernel.log
                   │  │  
                   │  └─obj
                   │          xsim_0.win64.obj
                   │          xsim_1.c
                   │          xsim_1.win64.obj
                   │          
                   └─xil_defaultlib
                            glbl.sdb
                            lab1.sdb
                            lab1_tb.sdb
                            xil_defaultlib.rlx
    ```
    
    Verás varios botones junto a la ventana de la forma de onda que pueden ser utilizados para propósitos específicos como se lista en la siguiente tabla.
    
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig18.png)
    
    _Varios botones disponibles para ver la forma de onda_
    
4. Haz clic en el botón _Zoom Fit_ (![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig19.png)) para ver la forma de onda completa.
    
    Nota que la salida cambia cuando cambia la entrada.
    
    También puedes flotar la ventana de la forma de onda de la simulación haciendo clic en el botón Flotar (![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig20.png)) en la esquina superior derecha de la vista. Esto te permitirá tener una ventana más amplia para ver las formas de onda de la simulación. Para reintegrar la ventana flotante de nuevo en la GUI, simplemente haz clic en el botón Acoplar Ventana (![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig21.png)).
    

#### Cambia el formato de visualización si lo deseas.

Selecciona **i\[31:0\]** en la ventana de la forma de onda, haz clic derecho, selecciona _Radix_, y luego selecciona _Unsigned Decimal_ para ver el índice del bucle for en forma de entero sin signo. De manera similar, cambia la radix de **btn\[3:0\]** a _Hexadecimal_. Deja la radix de **leds\[3:0\]** y **e\_led\[3:0\]** en _binario_ ya que queremos ver cada bit de salida.

#### Añade más señales para monitorear las señales de nivel inferior y continúa ejecutando la simulación durante 500 ns.

1. Expande la instancia **lab1\_tb**, si es necesario, en la ventana _Scopes_ y selecciona la instancia **dut**.
    
    Las señales btn\[3:0\] y led\[3:0\] se mostrarán en la ventana _Objects_.
    
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig22.png)
    
    _Seleccionando Señales de Nivel Inferior_
    
2. Selecciona **btn\[3:0\]** y **led\[3:0\]** y arrástralos a la ventana de la forma de onda para monitorear esas señales de nivel inferior.
    
3. En la barra de herramientas del simulador (![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig23.png)), escribe 500 en el campo de tiempo de ejecución de la simulación, haz clic en el botón desple

gable del campo de unidades y selecciona _ns_ ya que queremos ejecutar durante 500 ns (un total de 700 ns), y haz clic en el botón (![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig25.png)). La simulación se ejecutará durante 500 ns adicionales.
4. Haz clic en el botón _Zoom Fit_ y observa la salida.
    
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig26.png)
    
    _Ejecutando la simulación durante 500 ns adicionales_
    
    Observa la ventana de la consola Tcl y ve que la salida se muestra a medida que el banco de pruebas utiliza la tarea $display.
    
    ![](https://xilinx.github.io/xup_fpga_vivado_flow/images/lab1/Fig28.png)
    
    _Salida de la consola Tcl después de ejecutar la simulación durante 500 ns adicionales_
    
5. Cierra el simulador seleccionando **Archivo > Cerrar Simulación**.
    
6. Haz clic en **OK** y luego en **Descartar** para cerrarlo sin guardar la forma de onda.
