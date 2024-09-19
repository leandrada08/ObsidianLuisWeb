

Te explico cómo puedes utilizar los puntos 1, 2 y 3 de TerosHDL en tu **Mac** de manera sencilla:

### 1. **Edición de código HDL**
   - **Autocompletado**: A medida que escribes en **VHDL o Verilog**, TerosHDL sugiere automáticamente entidades, señales y palabras clave. Esto mejora la velocidad y evita errores tipográficos.
   - **Navegación de código**: Puedes hacer clic o usar atajos para saltar entre definiciones de entidades y módulos. Esto es útil cuando trabajas con proyectos grandes.
   - **Linting**: Mientras escribes, TerosHDL detecta errores de sintaxis en tiempo real, subrayando los errores para corregirlos antes de la simulación.

### 2. **Simulación**
   - **Instalación de simuladores**: Para usar simuladores como **GHDL o Verilator**, primero instálalos en tu Mac (se recomienda Homebrew: `brew install ghdl verilator`).
   - **Correr simulaciones**: Una vez instalados, seleccionas el simulador dentro de la configuración de TerosHDL. Puedes correr simulaciones directamente desde VSCode, utilizando el menú o atajos, y ver los resultados sin salir del editor.
   - **Configuración de simulaciones**: TerosHDL permite personalizar parámetros como tiempos de simulación o tipos de análisis para cada proyecto.

### 3. **Testbenches**
   - **Generación automática**: TerosHDL puede generar un **testbench básico** a partir de tu módulo principal, lo que acelera el proceso de verificación.
   - **Simulación de testbenches**: Una vez creado el testbench, puedes ejecutarlo directamente desde VSCode usando las herramientas de simulación. Se visualizan los resultados en la consola, y puedes hacer ajustes rápidamente.

### Configuración inicial en Mac:
1. Instala **VSCode** y luego **TerosHDL** desde la tienda de extensiones.
2. Usa **Homebrew** para instalar los simuladores necesarios.
3. Configura las rutas a los simuladores en la configuración de TerosHDL (puedes acceder desde el menú de ajustes de VSCode).


### 4. **Verificación formal**
   - **Integración con herramientas**: TerosHDL se integra con **Yosys** y **SymbiYosys** para verificación formal. Instala Yosys usando Homebrew (`brew install yosys`).
   - **Propiedades formales**: Puedes definir propiedades en tu código HDL para verificar que cumplen con ciertas condiciones lógicas, asegurando que tu diseño es correcto antes de la implementación.

### 5. **Visualización de resultados**
   - **Trazado de señales**: Después de simular, puedes visualizar las señales de entrada y salida como gráficos temporales usando **GTKWAVE** (también se puede instalar con Homebrew: `brew install gtkwave`).
   - **Interpretación gráfica**: Esto te permite identificar errores y comportamientos inesperados en los resultados de la simulación.

### 6. **Automatización**
   - **Scripts predefinidos**: TerosHDL permite crear scripts o **Makefiles** que automatizan tareas repetitivas, como compilar, simular o verificar módulos HDL. Puedes ejecutar estos scripts desde el editor, lo que ahorra tiempo en proyectos grandes.
   - **Integración continua**: Puedes combinarlo con pipelines de **CI/CD** para automatizar pruebas en cada commit del código.

### Configuración:
1. Instala **Yosys** y **GTKWAVE** en tu Mac para la verificación formal y visualización de señales.
2. Configura TerosHDL para ejecutar scripts automatizados desde el editor.





















## Referencias
### Notas relacionadas
- **Nota:**[[Verilog]] [[Bases VHDL]]
	- **Relacion-Reflexion:**