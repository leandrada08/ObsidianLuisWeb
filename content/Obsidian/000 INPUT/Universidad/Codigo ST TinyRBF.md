
## 1. **Entorno y configuración del proyecto** (Makefile)

### a. **Compilación optimizada para ISPU**

El bloque más importante del Makefile es el que define las **banderas de compilación** y las **opciones de inclusión** para el proyecto:

```makefile
CFLAGS = -mcpu=reiscl -Os -specs=nano.specs -ffunction-sections -fdata-sections -Wl,--gc-sections \
         -mfp32-format=ieee -Wall -Wextra -Wdouble-promotion -fno-strict-aliasing
INCS = -I../ispu_utils -I../src
```

- **`CFLAGS`**: Estas son las banderas que se pasan al compilador para configurar cómo se debe compilar el código.
  - **`-mcpu=reiscl`**: Esta opción específica que el código debe compilarse para la arquitectura `reiscl`, que es el tipo de procesador usado por el ISPU.
  - **`-Os`**: Optimiza el código para **tamaño**. Esto es esencial en entornos embebidos con memoria limitada como el ISPU.
  - **`-specs=nano.specs`**: Usa la especificación `nano.specs`, que es una biblioteca estándar más pequeña para optimizar el uso de recursos.
  - **`-ffunction-sections`** y **`-fdata-sections`**: Coloca cada función y cada sección de datos en su propia sección separada. Esto permite al enlazador eliminar partes no utilizadas del código, lo que ayuda a reducir el tamaño del binario final.
  - **`-Wl,--gc-sections`**: Esta opción se pasa al enlazador (ld) y permite que se eliminen las secciones de código y datos no utilizados, lo que nuevamente reduce el tamaño del ejecutable final.
  - **`-mfp32-format=ieee`**: Configura el formato de números de punto flotante a **IEEE 754**, un estándar común en procesadores.
  - **`-Wall -Wextra`**: Habilita todos los **warnings** posibles durante la compilación. Es útil para identificar posibles errores o comportamientos no deseados.
  - **`-Wdouble-promotion`**: Detecta si se promueven operaciones de tipo `float` a `double` de manera implícita, lo cual es costoso en entornos embebidos.
  - **`-fno-strict-aliasing`**: Desactiva la optimización de aliasing, lo que puede evitar problemas en sistemas embebidos donde las operaciones de puntero son críticas.

- **`INCS`**: Aquí se especifican las **rutas de inclusión** para los archivos `.h` utilizados en el proyecto.
  - **`-I../ispu_utils`**: Incluye las utilidades específicas del ISPU (probablemente definiciones de hardware o bootloader).
  - **`-I../src`**: Incluye el código fuente principal.

### b. **Fuentes y nombres de salida**

```makefile
SRC = ../ispu_utils/crt0.S ../src/main.c
OUTDIR = bin
NAME = ispu
```

- **`SRC`**: Define los archivos fuente que se compilarán. Aquí se están compilando:
  - **`crt0.S`**: Este archivo es el **"C runtime"** y usualmente contiene el código de inicialización (assembly) que se ejecuta antes del `main()`. Configura el entorno básico de ejecución, como la pila y los registros.
  - **`main.c`**: Este es el archivo principal del proyecto que contiene el ciclo de ejecución del algoritmo TinyRBF.

- **`OUTDIR`**: El directorio donde se almacenarán los archivos binarios generados (`bin`).
- **`NAME`**: El nombre del ejecutable final (`ispu`).

### c. **Comandos de compilación y generación de binarios**

```makefile
build: $(SRC) $(OUTDIR) Makefile
	$(CC) $(CFLAGS) -o $(OUTDIR)/$(NAME) $(SRC) -T ../ispu_utils/boot.ld $(INCS)
	$(SIZE_REISC) $(OUTDIR)/$(NAME)
	$(OBJ_COPY) -O srec $(OUTDIR)/$(NAME) $(OUTDIR)/$(NAME).srec
	$(ISPU_GEN) -b -c -s ../conf.txt -d imu_22 -n ispu_conf $(OUTDIR)/$(NAME).srec > $(OUTDIR)/$(NAME).h
	$(ISPU_GEN) -b -s ../conf.txt -d imu_22 -n ispu_conf $(OUTDIR)/$(NAME).srec > $(OUTDIR)/$(NAME).ucf
```

- **`build`**: Es el objetivo principal que se invoca al correr `make build`. Este paso:
  1. **Compila** el código fuente usando las banderas de compilación y el **script de vinculación** (`boot.ld`).
  2. **Muestra el tamaño del binario** compilado con `$(SIZE_REISC)`, que es una utilidad que mide el tamaño del binario final en la memoria del ISPU.
  3. **Convierte el binario a formato SREC** con `$(OBJ_COPY)`. El formato SREC es común para transferir binarios a dispositivos embebidos.
  4. **Genera archivos de configuración** (`.h` y `.ucf`) que probablemente contengan los datos necesarios para cargar y configurar el binario en el ISPU, usando la herramienta `$(ISPU_GEN)`.

### d. **Directorio de salida y limpieza**

```makefile
$(OUTDIR):
	$(MKDIR) $(OUTDIR)

clean:
ifneq (,$(wildcard $(OUTDIR)))
	$(RMDIR) $(OUTDIR)
endif
```

- **`$(OUTDIR)`**: Crea el directorio de salida si no existe.
- **`clean`**: Elimina todos los archivos generados (binarios, configuración, etc.) para dejar el entorno limpio.

---

## 2. **Control del hardware ISPU**

El hardware ISPU (Intelligent Sensor Processing Unit) es un microcontrolador especializado diseñado para procesar datos de sensores de manera eficiente. En este proyecto, se interactúa con el ISPU a través de registros específicos y periféricos mediante macros y definiciones. Esto es fundamental para un dispositivo embebido, donde la interacción con el hardware es directa y debe ser precisa.

### a. **Acceso a registros de hardware** (`peripherals.h`)

El archivo **`peripherals.h`** define macros que permiten acceder y manipular los **registros de hardware** del ISPU. En un sistema embebido como este, no se usa un sistema operativo completo, por lo que el código interactúa directamente con los registros de hardware para controlar el comportamiento del dispositivo.

- **Macros de acceso directo**:
  
```c
#define cast_uint32_t(add) (*((volatile uint32_t *)(add)))
#define cast_uint16_t(add) (*((volatile uint16_t *)(add)))
#define cast_uint8_t(add)  (*((volatile uint8_t *)(add)))
```

Estas macros permiten **leer y escribir** valores en direcciones específicas de memoria que corresponden a registros de hardware. El uso de `volatile` es crucial en sistemas embebidos, ya que garantiza que el compilador no optimice el acceso a los registros (pueden cambiar en cualquier momento debido a interrupciones o eventos externos).

Por ejemplo:
```c
cast_uint32_t(ISPU_STATUS) = status;
```
Esta línea escribiría el valor de `status` en el registro `ISPU_STATUS`.

### b. **Registros y control de periféricos** (`reg_map.h`)

El archivo **`reg_map.h`** define las direcciones de los registros de control del ISPU. Estos registros son esenciales para configurar el comportamiento del sistema, manejar interrupciones y acceder a los datos de los sensores.

Ejemplo de registros importantes:

```c
#define ISPU_GLB_CALL_EN  (ctrl_reg_base + 0x00)
#define ISPU_INT1_CTRL    (ctrl_reg_base + 0x50)
#define ISPU_INT_STATUS   (ctrl_reg_base + 0x58)
```

- **`ISPU_GLB_CALL_EN`**: Este registro habilita la **generación de interrupciones** para los algoritmos TinyRBF. Al establecer el valor adecuado en este registro, se puede controlar cuándo deben ejecutarse los algoritmos o cuándo se deben generar interrupciones.
- **`ISPU_INT1_CTRL`**: Controla la configuración de la **interrupción 1** del ISPU, que probablemente esté relacionada con el procesamiento de datos del sensor o de la red neuronal.
- **`ISPU_INT_STATUS`**

: Mantiene el estado de las interrupciones. Leer este registro permite al software saber si una interrupción ha ocurrido y qué acción tomar en consecuencia.

### c. **Ciclo de espera y control de interrupciones**

Otra macro importante es `stop_and_wait_start_pulse`:

```c
#define stop_and_wait_start_pulse do { STOP_CLOCK; asm(""); } while (false)
```

- Esta macro detiene el **reloj** del ISPU para esperar un pulso de inicio. Es un ciclo de espera en el que el procesador queda suspendido hasta que ocurre un evento o interrupción que lo reactiva.

### d. **Interrupciones y manejo de estados**

El código principal (`main.c`) utiliza estos registros para manejar las interrupciones y controlar el flujo de ejecución de los algoritmos:

```c
// get all the algorithms to run in this time slot
cast_uint32_t(ISPU_CALL_EN) = cast_uint32_t(ISPU_ALGO) << 1;
```

Aquí, se está **habilitando** la ejecución de los algoritmos TinyRBF en función del estado del registro `ISPU_ALGO`.

Otro ejemplo importante es la gestión de las **banderas de interrupción**:

```c
cast_uint32_t(ISPU_INT_STATUS) = int_status;
cast_uint8_t(ISPU_INT_PIN) = int_pin;
```

Estas líneas **restablecen** las interrupciones en los registros correspondientes una vez que el algoritmo ha procesado los datos.

---

### Resumen de los puntos 1 y 2:

1. **Entorno y Configuración del Proyecto**:
   - El **Makefile** configura el proceso de compilación con optimizaciones para hardware embebido.
   - Las banderas de compilación están diseñadas para reducir el tamaño del binario y optimizar el uso de memoria.
   - Se generan binarios y archivos de configuración específicos para ser ejecutados en el ISPU.

2. **Control del Hardware ISPU**:
   - Se interactúa directamente con los **registros** del ISPU utilizando macros (`cast_uint32_t`, etc.).
   - Los registros de control, como **`ISPU_GLB_CALL_EN`** y **`ISPU_INT_STATUS`**, manejan la ejecución de algoritmos y el control de interrupciones.
   - El ciclo principal del sistema depende del manejo de interrupciones y la sincronización mediante los registros de hardware.




¡Excelente! Vamos a desarrollar en detalle el **punto 3) Inicialización y ciclo principal del sistema**. Este punto es crucial porque define cómo se **inicia** el sistema TinyRBF, cómo se preparan los algoritmos, y qué sucede en el **bucle principal de ejecución**. Aquí se maneja la interacción continua entre el hardware del ISPU y los algoritmos implementados para procesar los datos del sensor y ejecutar la inferencia en la red neuronal.

## 3: **Inicialización y ciclo principal del sistema**

El archivo que define este comportamiento es el **`main.c`**, donde se gestionan los algoritmos TinyRBF y el ciclo de control del hardware. A continuación, explicaremos cómo se inicializa el sistema, cómo funciona el ciclo principal y cómo se procesan las **interrupciones** y los **algoritmos**.

### a. **Inicialización del sistema**

El **proceso de inicialización** asegura que los registros de control del hardware y los algoritmos estén correctamente configurados antes de que el sistema entre en el bucle principal de ejecución. La inicialización se enfoca en habilitar la generación de interrupciones y preparar los algoritmos TinyRBF para ser ejecutados.

#### Código relevante de inicialización:

```c
int main(void)
{
	// set boot done flag
	uint8_t status = cast_uint8_t(ISPU_STATUS);
	status = status | 0x04u; // Establece un flag para indicar que el sistema ha arrancado.
	cast_uint8_t(ISPU_STATUS) = status;

	// enable algorithms interrupt request generation
	cast_uint8_t(ISPU_GLB_CALL_EN) = 0x01u; // Habilita la generación de interrupciones para los algoritmos.
```

#### Explicación detallada:

1. **Bandera de arranque (`boot flag`)**:
   - El sistema establece una bandera de estado (`status = status | 0x04u`) en el registro **`ISPU_STATUS`**. Esto indica que el sistema ha completado su **proceso de arranque**. Este paso es fundamental porque informa al hardware que todo está preparado y que el ISPU puede empezar a ejecutar algoritmos.

2. **Habilitar interrupciones**:
   - Luego, el sistema habilita la **generación de interrupciones** para los algoritmos configurando el registro **`ISPU_GLB_CALL_EN`**. El valor `0x01u` indica que se habilitan las interrupciones globales para que los algoritmos puedan ejecutarse cuando sea necesario.

   > **Interrupciones**: Estas permiten al sistema detener el flujo normal de ejecución (bucle principal) y realizar acciones específicas cuando ciertos eventos (como la lectura de datos del sensor o la finalización de un algoritmo) ocurren. En un sistema embebido, las interrupciones son críticas para manejar eventos en tiempo real sin perder eficiencia.

---

### b. **Ciclo principal de ejecución**

Una vez completada la inicialización, el sistema entra en un **bucle infinito** (`while (true)`), donde continuamente espera eventos, ejecuta algoritmos y procesa los resultados. Este es el **ciclo principal del sistema**, y es donde se lleva a cabo la mayoría del trabajo real.

#### Código del ciclo principal:

```c
	while (true) {
		stop_and_wait_start_pulse;  // Espera por un evento o interrupción.

		// reset status registers and interrupts
		int_status = 0u;
		cast_uint32_t(ISPU_INT_STATUS) = 0u;
		cast_uint8_t(ISPU_INT_PIN) = 0u;

		// get all the algorithms to run in this time slot
		cast_uint32_t(ISPU_CALL_EN) = cast_uint32_t(ISPU_ALGO) << 1;

		// wait for all algorithms execution
		while (cast_uint32_t(ISPU_CALL_EN) != 0u) {
			// Espera a que todos los algoritmos hayan terminado de ejecutarse.
		}

		// get interrupt flags
		uint8_t int_pin = 0u;
		int_pin |= ((int_status & cast_uint32_t(ISPU_INT1_CTRL)) > 0u) ? 0x01u : 0x00u;
		int_pin |= ((int_status & cast_uint32_t(ISPU_INT2_CTRL)) > 0u) ? 0x02u : 0x00u;

		// set status registers and generate interrupts
		cast_uint32_t(ISPU_INT_STATUS) = int_status;
		cast_uint8_t(ISPU_INT_PIN) = int_pin;
	}
```

#### Explicación detallada:

1. **Ciclo infinito**:
   - El ciclo `while (true)` asegura que el sistema se mantenga en funcionamiento de manera continua, esperando y ejecutando tareas cuando sea necesario. En sistemas embebidos, este ciclo es común porque el dispositivo no tiene "final" en su operación; continúa ejecutando tareas hasta que es apagado.

2. **Esperar por interrupciones o eventos (`stop_and_wait_start_pulse`)**:
   - El sistema usa la macro **`stop_and_wait_start_pulse`** para detenerse y esperar un evento o pulso de inicio (por ejemplo, la llegada de datos de un sensor o una interrupción de temporizador). Este paso asegura que el sistema no desperdicie recursos de procesamiento mientras no tiene ninguna tarea que realizar.
   - **`STOP_CLOCK`**: Esto probablemente desactiva el reloj de la CPU para ahorrar energía hasta que ocurra un evento.

3. **Reinicio de registros de estado e interrupciones**:
   - Cada vez que el ciclo principal vuelve a empezar, se restablecen los **registros de estado** y las **banderas de interrupción**:
     - `int_status = 0u`: Se restablece la variable `int_status` que lleva el estado de las interrupciones.
     - Los registros de interrupciones **`ISPU_INT_STATUS`** y **`ISPU_INT_PIN`** se reinician para que el sistema esté listo para recibir nuevas interrupciones.

4. **Ejecución de los algoritmos TinyRBF**:
   - En este punto, el sistema habilita todos los **algoritmos que deben ejecutarse** en el ciclo actual. Esto se hace configurando el registro **`ISPU_CALL_EN`**:
     ```c
     cast_uint32_t(ISPU_CALL_EN) = cast_uint32_t(ISPU_ALGO) << 1;
     ```
     - El valor en el registro `ISPU_ALGO` es desplazado y escrito en `ISPU_CALL_EN`, indicando qué algoritmos deben ejecutarse. Este registro es clave para el control de flujo de los algoritmos TinyRBF.

5. **Esperar la ejecución de los algoritmos**:
   - El ciclo espera que todos los algoritmos configurados terminen de ejecutarse:
     ```c
     while (cast_uint32_t(ISPU_CALL_EN) != 0u) {
         // Ciclo de espera hasta que los algoritmos finalicen.
     }
     ```
     Esto garantiza que no se continúe el flujo del sistema hasta que todos los algoritmos han procesado los datos.

6. **Lectura de banderas de interrupción**:
   - Una vez que los algoritmos han terminado de ejecutarse, el sistema **lee las banderas de interrupción**. Estas banderas indican qué algoritmos o sensores han provocado una interrupción:
     ```c
     int_pin |= ((int_status & cast_uint32_t(ISPU_INT1_CTRL)) > 0u) ? 0x01u : 0x00u;
     int_pin |= ((int_status & cast_uint32_t(ISPU_INT2_CTRL)) > 0u) ? 0x02u : 0x00u;
     ```
     Aquí, el código verifica si `int_status` tiene bits activos que corresponden a las **interrupciones controladas** por `ISPU_INT1_CTRL` y `ISPU_INT2_CTRL`. Dependiendo del resultado, se activan los bits 0 y 1 en `int_pin`.

7. **Establecer los registros de estado**:
   - Finalmente, el sistema actualiza los **registros de estado** y las **interrupciones** para reflejar el estado actual del sistema:
     ```c
     cast_uint32_t(ISPU_INT_STATUS) = int_status;
     cast_uint8_t(ISPU_INT_PIN) = int_pin;
     ```
     Esto asegura que las interrupciones estén debidamente registradas y que el sistema esté listo para manejar el siguiente ciclo de ejecución.

---

### Resumen del punto 3:

1. **Inicialización del sistema**:
   - Se establece una bandera de arranque (`boot flag`) para indicar que el sistema está listo.
   - Se habilitan las interrupciones globales para los algoritmos TinyRBF mediante el registro `ISPU_GLB_CALL_EN`.

2. **Ciclo principal de ejecución**:
   - El sistema entra en un bucle infinito que:
     1. **Espera eventos** o interrupciones.
     2. **Restablece los registros de estado** e interrupciones.
     3. **Ejecuta los algoritmos** habilitados.
     4. **Espera la finalización de todos los algoritmos**.
     5. **Actualiza las banderas de interrupción** y el estado.

3. **Interacción con los algoritmos TinyRBF**:
   - El ciclo principal invoca los algoritmos TinyRBF, donde se procesan los datos de los sensores y se realiza la inferencia en la red neuronal. Estos algoritmos pueden generar interrupciones cuando finalizan su ejecución.




## 4: **Estructura de la Red Neuronal TinyRBF**

La estructura de la red neuronal TinyRBF está definida principalmente en el archivo **`tiny_rbf.h`** y utiliza varias estructuras auxiliares para manejar los nodos de la red, los pesos y las operaciones de cálculo. Aquí se implementan las funciones de inferencia y aprendizaje que permiten a la red ajustarse dinámicamente a las entradas.

---

### a. **Estructura de la red neuronal (`network_t`)**

La estructura principal que define la red neuronal es **`network_t`**, que almacena los nodos, los pesos, y varios parámetros de control.

#### Código relevante:

```c
typedef struct {
    node_list_t nodes;               // Lista de nodos en la capa oculta.
    float bias_weights[NUM_OUTPUTS]; // Pesos de sesgo para las salidas.
    weight_matrix_t weights;         // Matriz de pesos para la capa de salida.
    float distance_threshold;        // Umbral de distancia para agregar nuevos nodos.
    float error_threshold;           // Umbral de error para agregar nuevos nodos.
    float distance_mean;             // Media aproximada de la distancia a los nodos.
    float distance_std;              // Desviación estándar de la distancia a los nodos.
} network_t;
```

#### Explicación detallada:

1. **`node_list_t nodes`**: Esta es la **lista de nodos** que forman la **capa oculta** de la red RBF. Cada nodo es una función radial que calcula la distancia de entrada y decide si se debe activar. La estructura **`node_list_t`** está definida en el archivo **`node_list.h`**, y su tamaño es dinámico (puede aumentar o disminuir en función del aprendizaje).
   
2. **`float bias_weights[NUM_OUTPUTS]`**: Estos son los **pesos de sesgo** para la salida de la red. Cada vez que se calcula una salida, estos valores se suman al resultado. Esto es similar a cómo los sesgos funcionan en redes neuronales tradicionales, ajustando el resultado final.

3. **`weight_matrix_t weights`**: Esta es la **matriz de pesos** que conecta los nodos ocultos con la salida de la red. Cada columna de esta matriz representa los pesos asociados a un nodo, y cada fila corresponde a una salida de la red.

4. **`float distance_threshold`**: Este parámetro controla el **umbral de distancia**. Si la distancia entre una entrada y el nodo más cercano es mayor que este umbral, y el error también es alto, la red puede **agregar un nuevo nodo** para mejorar la representación de los datos.

5. **`float error_threshold`**: Similar al umbral de distancia, este parámetro define el **umbral de error**. Si el error de predicción es mayor que este valor, la red puede agregar nodos para mejorar el rendimiento.

6. **`float distance_mean` y `float distance_std`**: Estos parámetros se usan para calcular y mantener la **media** y la **desviación estándar** de las distancias entre las entradas y los nodos. Estos valores son importantes para actualizar dinámicamente el umbral de distancia a lo largo del tiempo.

---

### b. **Lista de nodos (`node_list_t`)**

La estructura **`node_list_t`** maneja los nodos ocultos de la red RBF. Los nodos representan funciones radiales que responden a ciertas entradas.

#### Código relevante de `node_list.h`:

```c
typedef struct {
    node_t data[MAX_NUM_NODES];  // Array de nodos, con un máximo de MAX_NUM_NODES.
    uint32_t size;               // Número de nodos actualmente en la lista.
} node_list_t;
```

- **`node_t data[MAX_NUM_NODES]`**: Un array de **nodos** que forman la capa oculta de la red. Cada nodo se almacena en el tipo de dato `node_t`, que contiene la información sobre su centro (ubicación en el espacio de características) y su radio (que define el área de influencia del nodo).
- **`uint32_t size`**: Número actual de nodos en la red. Este valor cambia dinámicamente durante el aprendizaje, ya que los nodos pueden ser agregados o eliminados.

---

### c. **Matriz de pesos (`weight_matrix_t`)**

La **matriz de pesos** conecta los nodos de la capa oculta con la salida de la red. Cada nodo tiene un conjunto de pesos que determinan su contribución a la salida de la red.

#### Código relevante de `weight_matrix.h`:

```c
typedef struct {
    float data[NUM_OUTPUTS][MAX_NUM_NODES]; // Matriz de pesos.
    uint32_t n_cols;                        // Número de columnas (número de nodos).
} weight_matrix_t;
```

- **`float data[NUM_OUTPUTS][MAX_NUM_NODES]`**: Esta matriz almacena los pesos que conectan cada nodo con las salidas. Cada fila de la matriz representa una salida, y cada columna representa los pesos asociados a un nodo.
- **`uint32_t n_cols`**: El número actual de nodos (o columnas) en la red. Este valor aumenta cuando se agregan nuevos nodos y disminuye cuando se eliminan.

---

### d. **Constantes y parámetros de la red**

Los parámetros clave que controlan el comportamiento de la red están definidos en el archivo **`constants.h`**. Estos valores incluyen límites en el tamaño de la red, tasas de aprendizaje y umbrales de activación.

#### Código relevante de `constants.h`:

```c
#define ACTIVATION_THRESHOLD (float)0.01
#define AVERAGE_WINDOW 100
#define LEARNING_RATE (float)0.2
#define MAX_NUM_NODES 10
#define NUM_INPUTS 2
#define NUM_OUTPUTS 1
#define OVERLAP_FACTOR (float)0.8
#define PRUNING_WINDOW 4294967295
```

- **`ACTIVATION_THRESHOLD`**: Este valor define el **umbral de activación** para los nodos. Si un nodo tiene una activación menor a este umbral en varias iteraciones, se elimina de la red.
- **`AVERAGE_WINDOW`**: Define el tamaño de la ventana de muestreo para calcular la media y la desviación estándar de las distancias entre nodos.
- **`LEARNING_RATE`**: Tasa de aprendizaje para ajustar los pesos de la red. Este valor controla la velocidad con la que se ajustan los pesos durante el proceso de aprendizaje.
- **`MAX_NUM_NODES`**: El número máximo de nodos que la red puede contener. Este límite asegura que la red no crezca indefinidamente.
- **`NUM_INPUTS` y `NUM_OUTPUTS`**: El número de entradas y salidas de la red.
- **`OVERLAP_FACTOR`**: Cuando se agrega un nuevo nodo, su **radio** se ajusta usando este factor de superposición, que asegura que los nodos nuevos no tengan demasiada superposición con los existentes.
- **`PRUNING_WINDOW`**: El número de iteraciones consecutivas que se permite que un nodo tenga baja activación antes de ser podado (eliminado) de la red.

---

### e. **Funciones clave para la gestión de la red**

#### 1. **Agregar y eliminar nodos (`add_node`, `remove_node_at`)**

La red puede **crecer dinámicamente** agregando nuevos nodos cuando es necesario, o **reducirse** eliminando nodos con baja activación. Estas funciones manejan este proceso.

#### Código relevante de `node_list.h`:

```c
static inline bool add_node(node_list_t *list, node_t item) {
    if (is_node_list_full(list)) {
        return false;
    }
    list->data[list->size] = item;
    list->size++;
    return true;
}

static inline bool remove_node_at(node_list_t *list, uint32_t index) {
    if (index >= list->size) {
        return false;
    }
    for (uint32_t i = index; i < list->size - 1; i++) {
        list->data[i] = list->data[i + 1];
    }
    list->size--;
    return true;
}
```

- **`add_node`**: Agrega un nuevo nodo a la red si no ha alcanzado el tamaño máximo definido por **`MAX_NUM_NODES`**. Este nodo se inicializa en la función `learning()` cuando se detecta un error de predicción alto o una distancia alta a los nodos existentes.
  
- **`remove_node_at`**: Elimina un nodo en una posición específica de la lista y reorganiza los nodos restantes. Esta función es clave para el **proceso de pruning**.

#### 2. **Agregar y eliminar columnas en la matriz de pesos (`add_column`, `remove_column_at`)**

Cuando se agrega o elimina un nodo, también es necesario actualizar la **matriz de pesos** que conecta los nodos con la salida.

#### Código relevante de `weight_matrix.h`:

```c
static inline bool add_column(weight_matrix_t *matrix, const float *column) {
    if (matrix->n_cols == MAX_NUM_NODES) {
        return false;
    }
    for (uint32_t i = 0; i < NUM_OUTPUTS; i++) {
        matrix->data[i][matrix->n_cols] = column[i];
    }
    matrix->n_cols++;
    return true;
}

static inline bool remove_column_at(weight_matrix_t *matrix, uint32_t index) {
    if (index >= matrix->n_cols) {
        return false;
    }
    for (uint32_t i = 0; i < NUM_OUTPUTS; i++) {
        for (uint32_t j = index; j < matrix->n_cols - 1; j++) {
            matrix->data[i][j] = matrix->data[i][j + 1];
        }
    }
    matrix->n_cols--;
    return true;
}
```

- **`add_column`**: Añade una nueva columna de pesos asociada a un nodo recién agregado.
- **`remove_column_at`**: Elimina la columna correspondiente cuando un nodo es podado.


### f. **Umbrales de distancia y error**

Estos parámetros son fundamentales para controlar cuándo se deben agregar nodos nuevos y cuándo los existentes son suficientes para representar la información.

#### Código relevante de `tiny_rbf.h`:

```c
network->distance_threshold = network->distance_mean + (float)2.0 * sqrtf(network->distance_std);
```

El umbral de distancia se **actualiza dinámicamente** basado en la media y la desviación estándar de las distancias entre los nodos y las entradas. Si la distancia de una nueva entrada a los nodos existentes supera este umbral, y el error de predicción es alto, se agrega un nuevo nodo a la red.



### g. **Poda (Pruning) de nodos**

El proceso de **poda** se usa para eliminar nodos que no contribuyen significativamente a la salida de la red, optimizando el uso de memoria y evitando el crecimiento innecesario de la red.

#### Código relevante de `learning()`:

```c
if (network->nodes.data[i].low_activation_count >= PRUNING_WINDOW) {
    remove_node_at(&network->nodes, i);
    remove_column_at(&network->weights, i);
    i--;
}
```

Cada nodo tiene un contador (`low_activation_count`) que se incrementa cada vez que su activación está por debajo del umbral. Si un nodo tiene activación baja durante muchas iteraciones consecutivas (definidas por `PRUNING_WINDOW`), es eliminado.


### Resumen del punto 4:

1. **Estructura de la red (`network_t`)**: Almacena los nodos, los pesos y los umbrales clave para la inferencia y el aprendizaje.
2. **Lista de nodos (`node_list_t`)**: Maneja los nodos ocultos de la red, que pueden agregarse o eliminarse dinámicamente.
3. **Matriz de pesos (`weight_matrix_t`)**: Conecta los nodos ocultos con la salida de la red.
4. **Constantes y parámetros clave**: Controlan el tamaño máximo de la red, las tasas de aprendizaje y los umbrales de activación.
5. **Agregar/eliminar nodos y pesos**: Funciones que permiten que la red crezca o se reduzca dinámicamente según los datos.
6. **Umbrales de distancia y error**: Determinan cuándo se debe agregar un nuevo nodo a la red.
7. **Poda (Pruning)**: Elimina nodos que no son útiles para optimizar la red y reducir el uso de recursos.



## 5: **Inferencia y Aprendizaje de la Red TinyRBF**

Los procesos de inferencia y aprendizaje están implementados principalmente en el archivo **`tiny_rbf.h`**. Estos dos procesos están diseñados para trabajar juntos: la inferencia permite que la red produzca una salida a partir de una entrada dada, mientras que el aprendizaje ajusta los nodos y los pesos de la red para mejorar la precisión de las predicciones.

### a. **Proceso de Inferencia (`inference()`)**

La inferencia en la red **TinyRBF** es el proceso mediante el cual la red toma una **entrada** y genera una **salida**. En una red RBF, esto implica calcular la **activación** de cada nodo en la capa oculta (basada en la distancia entre la entrada y el centro del nodo), multiplicar esas activaciones por los pesos correspondientes y luego sumar el sesgo para producir la salida final.

#### Código relevante:

```c
void inference(network_t *network, const float *input, float *output) {
    // Compute the activations
    vec_t activations = {
        .data = {0},
        .size = network->nodes.size
    };
    for (uint32_t i = 0; i < network->nodes.size; i++) {
        activations.data[i] = forward_node(&network->nodes.data[i], input);
    }

    // Compute the distance to the nearest RBF node and update the statistics
    if (!is_node_list_empty(&network->nodes)) {
        float distance;
        for (uint32_t i = 0; i < network->nodes.size; i++) {
            float dist_vec[NUM_INPUTS];
            sub(input, network->nodes.data[i].center, dist_vec, NUM_INPUTS);
            float dist = sqrtf(dot(dist_vec, dist_vec, NUM_INPUTS));
            if (i == 0 || dist < distance) {
                distance = dist;
            }
        }
        _update_distance_stats(network, distance);
    }
    
    // Compute the outputs
    matrix_vector_mul(&network->weights, &activations, output);
    add(output, network->bias_weights, output, NUM_OUTPUTS);
}
```

#### Explicación detallada:

1. **Cálculo de activaciones (`forward_node()`)**:
   - Para cada nodo en la capa oculta de la red, la función `inference()` calcula la **activación** utilizando la función **`forward_node()`**, que compara la **entrada** con el **centro del nodo** y calcula una activación basada en la **distancia** entre ellos.
   - Los valores de activación se almacenan en el vector `activations`.

   ```c
   activations.data[i] = forward_node(&network->nodes.data[i], input);
   ```

   **Cómo funciona `forward_node()`**:
   - La función `forward_node()` calcula la **distancia euclidiana** entre el vector de entrada y el **centro del nodo**. La salida de un nodo RBF generalmente depende de esta distancia.
   - Mientras más cerca esté la entrada del centro del nodo, mayor será la activación del nodo.

2. **Cálculo de la distancia a los nodos**:
   - Tras calcular las activaciones, se calcula la **distancia** entre la entrada y el nodo más cercano. Esta distancia se usa luego para actualizar las estadísticas de la red (media y desviación estándar de las distancias). Esto es clave para ajustar los **umbrales de distancia** y decidir cuándo agregar nuevos nodos durante el aprendizaje.

   ```c
   float dist_vec[NUM_INPUTS];
   sub(input, network->nodes.data[i].center, dist_vec, NUM_INPUTS);
   float dist = sqrtf(dot(dist_vec, dist_vec, NUM_INPUTS));
   ```

   **Detalles del cálculo**:
   - `sub()` resta las coordenadas del centro del nodo a las coordenadas de la entrada para obtener un vector de diferencias.
   - `dot()` calcula el producto punto de este vector consigo mismo, lo que resulta en la **distancia euclidiana** entre el nodo y la entrada.

3. **Multiplicación de activaciones por los pesos (`matrix_vector_mul()`)**:
   - Una vez calculadas las activaciones de los nodos, estas se multiplican por los pesos correspondientes en la **matriz de pesos** (que conecta la capa oculta con la salida de la red). Este paso produce la salida preliminar.

   ```c
   matrix_vector_mul(&network->weights, &activations, output);
   ```

   **Cómo funciona `matrix_vector_mul()`**:
   - Esta función toma el vector de activaciones y lo **multiplica** por la **matriz de pesos** para generar la salida preliminar de la red. Cada nodo tiene un peso asociado que determina su contribución a la salida final.

4. **Suma del sesgo (`bias_weights`)**:
   - Finalmente, los **pesos de sesgo** se suman a las salidas preliminares para obtener la **salida final**. Estos sesgos ajustan la salida de la red para mejorar su precisión.

   ```c
   add(output, network->bias_weights, output, NUM_OUTPUTS);
   ```

   - **`add()`** es una función que suma el vector de pesos de sesgo al vector de salida, ajustando los resultados según la configuración del sesgo.

---

### b. **Proceso de Aprendizaje (`learning()`)**

El **aprendizaje** en la red TinyRBF se lleva a cabo ajustando los **pesos** y **nodos** de la red con base en el **error de predicción**. Si el error es lo suficientemente alto, o si la distancia entre la entrada y los nodos existentes es grande, se puede agregar un nuevo nodo a la red.

#### Código relevante:

```c
void learning(network_t *network, const float *input, const float *target, float *output) {
    // Compute the activations
    vec_t activations = {
        .data = {0},
        .size = network->nodes.size
    };
    for (uint32_t i = 0; i < network->nodes.size; i++) {
        activations.data[i] = forward_node(&network->nodes.data[i], input);
    }
    
    // Compute the outputs
    matrix_vector_mul(&network->weights, &activations, output);
    add(output, network->bias_weights, output, NUM_OUTPUTS);

    // Compute prediction error.
    float error[NUM_OUTPUTS];
    sub(target, output, error, NUM_OUTPUTS);
    
    if (is_node_list_empty(&network->nodes)) {
        // === ALLOCATE A NEW NODE ===
        add_node(&network->nodes, new_node(input, network->distance_threshold));
        add_column(&network->weights, error);
        return;
    }
    
    // Compute the distance to the nearest RBF node.
    float distance = 0.0;
    for (uint32_t i = 0; i < network->nodes.size; i++) {
        float dist_vec[NUM_INPUTS];
        sub(input, network->nodes.data[i].center, dist_vec, NUM_INPUTS);
        float dist = sqrtf(dot(dist_vec, dist_vec, NUM_INPUTS));
        if (i == 0 || dist < distance) {
            distance = dist;
        }
    }

    // Update distance statistics.
    _update_distance_stats(network, distance);

    // Determine if a new node should be added.
    if (sqrtf(dot(error, error, NUM_OUTPUTS)) > network->error_threshold
        && distance > network->distance_threshold
        && !is_node_list_full(&network->nodes)) {
        // === ALLOCATE A NEW NODE ===
        add_node(&network->nodes, new_node(input, OVERLAP_FACTOR * distance));
        add_column(&network->weights, error);
    } else {
        // === UPDATE WEIGHTS ===
        for (uint32_t i = 0; i < NUM_OUTPUTS; i++) {
            network->bias_weights[i] += LEARNING_RATE * error[i];
        }
        for (uint32_t i = 0; i < network->nodes.size; i++) {
            node_t *node = &network->nodes.data[i];
            float weight_column[NUM_OUTPUTS];
            for (uint32_t j = 0; j < NUM_OUTPUTS; j++) {
                weight_column[j] = network->weights.data[j][i];
            }
            float k = LEARNING_RATE * ((float)2.0 / powf(node->radius, 2))
                      * activations.data[i] * dot(weight_column, error, NUM_OUTPUTS);
            for (uint32_t j = 0; j < NUM_INPUTS; j++) {
                node->center[j] += k * (input[j] - node->center[j]);
            }
            // Update the corresponding weights for the output layer.
            for (uint32_t j = 0; j < NUM_OUTPUTS; j++) {
                network->weights.data[j][i] += LEARNING_RATE * error[j] * activations.data[i];
            }
        }
    }
}
```

#### Explicación detallada:

1. **Cálculo de activaciones y salida (reutilizando `inference()`)**:
   - El proceso de aprendizaje **comienza calculando las activaciones** de los nodos (similar a la inferencia) y luego **genera una salida preliminar**. Esto permite comparar la salida generada con el **objetivo** (`target`) para calcular el **error de predicción**.

   ```c
   matrix_vector_mul(&network->weights, &activations, output);
   add(output, network->bias_weights, output, NUM_OUTPUTS);
   ```

2. **Cálculo del error de predicción (`sub()`)**:
   - Una vez calculada la salida, se resta de la salida deseada o objetivo (`target`) para obtener el **error de predicción**. Este error es el que se utilizará para ajustar los pesos de la red o para decidir si se debe agregar un nuevo nodo.

   ```c
   sub(target, output, error, NUM_OUTPUTS);
   ```

3. **Agregar un nuevo nodo (si es necesario)**:
   - Si el **error de predicción** es alto y la distancia entre la entrada y el nodo más cercano es mayor que el **umbral de distancia**, el algoritmo decide agregar un nuevo nodo para mejorar la precisión de la red.
   
   ```c
   if (sqrtf(dot(error, error, NUM_OUTPUTS)) > network->error_threshold
       && distance > network->distance_threshold
       && !is_node_list_full(&network->nodes)) {
       add_node(&network->nodes, new_node(input, OVERLAP_FACTOR * distance));
       add_column(&network->weights, error);
   }
   ```

   - **`add_node()`** agrega un nuevo nodo en la posición de la entrada.
   - **`add_column()`** agrega una nueva columna de pesos en la matriz de pesos para conectar el nuevo nodo con la salida.

4. **Actualizar los pesos de la red**:
   - Si no se agrega un nuevo nodo, el algoritmo ajusta los **pesos de los nodos existentes** y los **pesos de sesgo** en función del error calculado. Esto se hace usando la **tasa de aprendizaje** (`LEARNING_RATE`), que controla qué tan rápido se ajustan los pesos.

   ```c
   network->bias_weights[i] += LEARNING_RATE * error[i];
   ```

   - Luego, se ajustan los **pesos de los nodos** usando la activación de cada nodo y el error. También se ajustan los **centros** de los nodos para acercarlos a las entradas que producen grandes errores.

   ```c
   node->center[j] += k * (input[j] - node->center[j]);
   network->weights.data[j][i] += LEARNING_RATE * error[j] * activations.data[i];
   ```

---

### Resumen del punto 5:

1. **Inferencia (`inference()`)**:
   - **Activación de los nodos**: La entrada se compara con los centros de los nodos para calcular su activación.
   - **Cálculo de la salida**: Las activaciones se multiplican por los pesos de salida y se suma el sesgo para obtener la salida final.
   - **Actualización de estadísticas**: Las distancias entre la entrada y los nodos se registran para usarlas en decisiones futuras (como agregar nodos).

2. **Aprendizaje (`learning()`)**:
   - **Cálculo del error**: Se compara la salida generada con la deseada para calcular el error de predicción.
   - **Agregar nodos**: Si el error es grande y la entrada está lejos de los nodos existentes, se agrega un nuevo nodo a la red.
   - **Ajuste de pesos**: Los pesos de los nodos y los centros de los nodos se ajustan para minimizar el error en futuras predicciones.

El aprendizaje permite que la red **se ajuste dinámicamente**, agregando nodos cuando sea necesario y ajustando sus parámetros para mejorar su rendimiento con el tiempo.



## 6: **Manejo Dinámico de Nodos y Pesos**

El manejo de los nodos y los pesos en la red TinyRBF se implementa en varias funciones que se encargan de **agregar**, **eliminar**, y **ajustar** tanto los nodos como los pesos. A continuación, veremos cómo estos procesos se llevan a cabo en detalle.

---

### a. **Agregar nodos (`add_node`)**

El proceso de **agregar un nuevo nodo** a la red ocurre cuando el error de predicción es alto y la distancia entre la entrada y los nodos existentes supera un umbral. Esto indica que los nodos actuales no son suficientes para representar la entrada, por lo que la red necesita expandirse.

#### Código relevante de `node_list.h`:

```c
static inline bool add_node(node_list_t *list, node_t item) {
    if (is_node_list_full(list)) {
        // No se puede agregar más nodos, la lista está llena.
        return false;
    }
    // Agregar el nuevo nodo al final de la lista de nodos.
    list->data[list->size] = item;
    list->size++;  // Aumenta el tamaño de la lista de nodos.
    return true;
}
```

#### Explicación detallada:

1. **Comprobación de si la lista de nodos está llena**:
   - Antes de agregar un nuevo nodo, el sistema verifica si la lista de nodos ha alcanzado el **número máximo de nodos** permitido, definido por **`MAX_NUM_NODES`**.
   - Si la lista está llena, no se puede agregar el nodo y la función retorna `false`.

2. **Agregar el nodo**:
   - Si la lista no está llena, el nuevo nodo se **inserta** en la última posición disponible en el array `data[]` de la estructura `node_list_t`.
   - Luego, se incrementa el contador de tamaño `size` para reflejar que hay un nodo más en la red.

3. **Devuelve `true` si se agrega exitosamente**:
   - Si se agrega el nodo, la función devuelve `true`. Esto asegura que el código principal sepa que el nodo se ha añadido correctamente.

Este mecanismo es crucial para que la red crezca de forma **adaptativa**, agregando nodos cuando detecta que la estructura actual no es suficiente para capturar la complejidad de los datos de entrada.

---

### b. **Eliminar nodos (`remove_node_at`)**

El proceso de **eliminar un nodo** ocurre cuando la red detecta que un nodo tiene **baja activación** durante varias iteraciones consecutivas. Este es el proceso de **poda** o **"pruning"**, diseñado para reducir el tamaño de la red eliminando nodos que no contribuyen significativamente a la salida.

#### Código relevante de `node_list.h`:

```c
static inline bool remove_node_at(node_list_t *list, uint32_t index) {
    if (index >= list->size) {
        // El índice está fuera de los límites.
        return false;
    }
    // Mover todos los nodos hacia la izquierda para llenar el hueco.
    for (uint32_t i = index; i < list->size - 1; i++) {
        list->data[i] = list->data[i + 1];
    }
    list->size--;  // Reducir el tamaño de la lista.
    return true;
}
```

#### Explicación detallada:

1. **Verificación del índice**:
   - La función comienza comprobando si el índice dado está dentro de los límites de la lista de nodos (es decir, debe ser menor que el tamaño actual de la lista).
   - Si el índice es mayor o igual al tamaño de la lista, significa que no existe un nodo en esa posición, y la función retorna `false`.

2. **Eliminar el nodo**:
   - Para eliminar un nodo, se utiliza un **bucle** que **mueve** todos los nodos a la derecha del nodo eliminado una posición hacia la izquierda, sobrescribiendo el nodo que se va a eliminar.
   - De esta manera, se mantiene la **contigüidad** de los nodos en el array, sin dejar "huecos".

3. **Reducir el tamaño de la lista**:
   - Una vez que el nodo ha sido eliminado, se decrementa el contador de tamaño `size` de la lista de nodos, reflejando que hay un nodo menos en la red.

4. **Devuelve `true` si se elimina exitosamente**:
   - Si se elimina el nodo correctamente, la función devuelve `true`.

Este proceso es clave para reducir la complejidad de la red y optimizar el uso de memoria, ya que los nodos que no son útiles se eliminan dinámicamente.

---

### c. **Agregar columnas de pesos (`add_column`)**

Cuando se agrega un nuevo nodo a la red, también es necesario agregar una **columna de pesos** en la matriz de pesos que conecta los nodos ocultos con la salida. Cada nodo tiene un conjunto de pesos asociados que determinan su contribución a la salida de la red.

#### Código relevante de `weight_matrix.h`:

```c
static inline bool add_column(weight_matrix_t *matrix, const float *column) {
    if (matrix->n_cols == MAX_NUM_NODES) {
        // No se puede agregar una columna, la matriz está llena.
        return false;
    }
    // Agregar la nueva columna de pesos al final de la matriz.
    for (uint32_t i = 0; i < NUM_OUTPUTS; i++) {
        matrix->data[i][matrix->n_cols] = column[i];
    }
    matrix->n_cols++;  // Incrementar el número de columnas.
    return true;
}
```

#### Explicación detallada:

1. **Comprobación del límite de columnas**:
   - La función verifica si el número de columnas en la matriz de pesos ha alcanzado el límite definido por **`MAX_NUM_NODES`**. Si el número de columnas es igual al número máximo de nodos, no se puede agregar una nueva columna y la función retorna `false`.

2. **Agregar la nueva columna**:
   - Si aún hay espacio en la matriz, la nueva columna (es decir, los nuevos pesos asociados al nodo recién agregado) se inserta en la última columna disponible de la matriz `data[][]`.
   - Cada fila de la matriz representa un conjunto de pesos para una salida de la red, y cada columna representa los pesos de un nodo.

3. **Incrementar el número de columnas**:
   - Una vez que la nueva columna se ha agregado con éxito, se incrementa el contador `n_cols` para reflejar que hay una nueva columna en la matriz.

4. **Devuelve `true` si se agrega exitosamente**:
   - La función retorna `true` si la columna de pesos ha sido agregada correctamente.

Este proceso asegura que cuando se agrega un nuevo nodo, también se actualizan los **pesos correspondientes**, manteniendo la coherencia entre los nodos y las salidas.

---

### d. **Eliminar columnas de pesos (`remove_column_at`)**

Cuando un nodo es eliminado, también es necesario eliminar la **columna correspondiente** de la matriz de pesos, para que la estructura de la red siga siendo coherente.

#### Código relevante de `weight_matrix.h`:

```c
static inline bool remove_column_at(weight_matrix_t *matrix, uint32_t index) {
    if (index >= matrix->n_cols) {
        // El índice está fuera de los límites.
        return false;
    }
    // Mover todas las columnas a la izquierda para llenar el hueco.
    for (uint32_t i = 0; i < NUM_OUTPUTS; i++) {
        for (uint32_t j = index; j < matrix->n_cols - 1; j++) {
            matrix->data[i][j] = matrix->data[i][j + 1];
        }
    }
    matrix->n_cols--;  // Reducir el número de columnas.
    return true;
}
```

#### Explicación detallada:

1. **Verificación del índice**:
   - La función comienza comprobando si el índice de la columna a eliminar está dentro de los límites de la matriz (es decir, debe ser menor que el número actual de columnas).
   - Si el índice es mayor o igual al número de columnas, la función retorna `false` porque no existe una columna en esa posición.

2. **Eliminar la columna**:
   - Similar al proceso de eliminación de nodos, las columnas a la derecha de la columna eliminada se **desplazan hacia la izquierda** para llenar el hueco.
   - Esto asegura que la matriz de pesos siga siendo **contigua**, sin huecos entre las columnas.

3. **Reducir el número de columnas**:
   -

 Una vez que la columna ha sido eliminada, se decrementa el contador `n_cols`, lo que indica que hay una columna menos en la matriz.

4. **Devuelve `true` si se elimina exitosamente**:
   - Si la columna se elimina correctamente, la función devuelve `true`.

Este mecanismo es clave para mantener la coherencia de los **pesos de la red** cuando se eliminan nodos, asegurando que la estructura de la red siempre refleje el número actual de nodos.

---

### e. **Actualización de pesos y centros de nodos**

Cuando se ajustan los pesos durante el **aprendizaje**, la red TinyRBF también ajusta los **centros de los nodos** para que reflejen mejor la distribución de los datos. Este ajuste dinámico es esencial para que los nodos respondan correctamente a las nuevas entradas.

#### Código relevante de `learning()` en `tiny_rbf.h`:

```c
for (uint32_t i = 0; i < network->nodes.size; i++) {
    node_t *node = &network->nodes.data[i];
    
    // Calcular el ajuste del centro del nodo.
    float weight_column[NUM_OUTPUTS];
    for (uint32_t j = 0; j < NUM_OUTPUTS; j++) {
        weight_column[j] = network->weights.data[j][i];
    }
    float k = LEARNING_RATE * ((float)2.0 / powf(node->radius, 2))
              * activations.data[i] * dot(weight_column, error, NUM_OUTPUTS);
    
    // Ajustar el centro del nodo.
    for (uint32_t j = 0; j < NUM_INPUTS; j++) {
        node->center[j] += k * (input[j] - node->center[j]);
    }
    
    // Actualizar los pesos del nodo.
    for (uint32_t j = 0; j < NUM_OUTPUTS; j++) {
        network->weights.data[j][i] += LEARNING_RATE * error[j] * activations.data[i];
    }
}
```

#### Explicación detallada:

1. **Ajustar el centro del nodo**:
   - Para cada nodo, se calcula un valor de ajuste **`k`** que determina cuánto debe moverse el centro del nodo hacia la entrada actual. Este valor depende de la **tasa de aprendizaje** (`LEARNING_RATE`), el radio del nodo, y la activación del nodo.
   - El centro del nodo se ajusta sumando una fracción del **desplazamiento** entre la entrada y el centro actual del nodo.

2. **Actualizar los pesos del nodo**:
   - Los **pesos** de cada nodo también se ajustan en función del **error de predicción** y la activación del nodo. Los pesos que conectan el nodo con la salida se incrementan o decrementan para reducir el error en futuras predicciones.

Este ajuste dinámico asegura que los nodos se mantengan **actualizados** y puedan adaptarse a los cambios en los datos de entrada, mejorando la precisión de la red.

---

### Resumen del punto 6:

1. **Agregar nodos**: Se añaden nuevos nodos cuando el error de predicción es alto y los nodos existentes no son suficientes para representar la entrada.
2. **Eliminar nodos**: Los nodos se eliminan cuando tienen baja activación durante varias iteraciones, optimizando el uso de memoria.
3. **Agregar columnas de pesos**: Cuando se agrega un nuevo nodo, se añade una nueva columna de pesos en la matriz que conecta los nodos con la salida.
4. **Eliminar columnas de pesos**: Cuando se elimina un nodo, se elimina la columna correspondiente de la matriz de pesos.
5. **Ajuste de pesos y centros de nodos**: Durante el aprendizaje, los pesos y los centros de los nodos se ajustan dinámicamente para reducir el error de predicción.

