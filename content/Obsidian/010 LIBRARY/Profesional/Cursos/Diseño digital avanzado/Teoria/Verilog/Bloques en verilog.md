


# Bloques en verilog
## Introducción
- **Always**
	- Que tipo de diseño generan los bloques Alwayas?
	- Cuando es conveniente usarlo?
	- Cuales son los tipo de asignaciones que existen dentro del bloque always?
		- Cuando es conveniente usar cada una?
- **Initial**
	- Cuando se debe usar bloque Initial?
	- Cual es la diferencia con el bloque Always?
- **Generate**
	- Para que se utiliza el bloque generate?
	- Cual es su diferencia con el bloque always?
- **Function**
	- Que es una function en verilog? 
	- Para que se la usa?
	- Como maneja sus variables y entradas?
	- Como debe ser escrita internamente?
- **Task**
	- Cual es la diferenia entre un task y una funcion?





## Always
El bloque `always` se utiliza para describir el comportamiento secuencial de un diseño digital. Puede estar sensibilizado a eventos específicos, como cambios de señales o flancos de reloj, y se ejecuta en respuesta a esos eventos. El código dentro del bloque `always` se ejecuta de forma continua o en ciclos, dependiendo de los eventos especificados. Se utiliza para describir la lógica secuencial, como registros de desplazamiento, contadores, máquinas de estado, entre otros.
El método clásico de listado de sensibilidad es escribir todas las entradas al bloque entre paréntesis, donde cada entrada está separada por una etiqueta “or”. A partir de Verilog-2001 se admiten listas de sensibilidad separadas por comas. También admite escribir un “ \* ” para la lista de sensibilidad, este asterisco significa que todas las entradas estan en la lista de sensibilidad.
- Todo lo que esta dentro del bloque se ejecuta de manera secuencial

#### Ejemplo
```verilog
always @(posedge clk) begin
  // Lógica secuencial
  if (reset)
    count <= 0;
  else
    count <= count + 1;
end
```

En este ejemplo, el bloque `always` está sensibilizado al flanco de subida de la señal de reloj `clk`. El código dentro del bloque se ejecuta cada vez que se detecta un flanco de subida. En este caso, se implementa una lógica de contador que incrementa el valor de `count` en 1 en cada flanco de subida del reloj, a menos que la señal `reset` esté activa, en cuyo caso se restablece a cero.
- Todo lo que esta a la izquierda del bloque always tiene que ser registro

### Asignaciones
Dentro del bloque `always`, puedes utilizar asignaciones bloqueantes y no bloqueantes para especificar cómo se deben actualizar las variables o señales. La elección entre asignaciones bloqueantes y no bloqueantes afecta el comportamiento de las asignaciones dentro del bloque `always`. Aquí te explico la diferencia entre ambos:
Las asignaciones bloqueantes son útiles en situaciones en las que deseas un comportamiento secuencial y predecible, como en máquinas de estados finitos. Las asignaciones no bloqueantes se utilizan comúnmente en descripciones de registros, donde se desea que múltiples eventos ocurran simultáneamente en respuesta a un evento de reloj.
###### Asignación Bloqueante (`=`):
   - Las asignaciones bloqueantes se realizan utilizando el operador `=`.
   - Cuando se utiliza una asignación bloqueante, el valor en el lado derecho de la asignación se calcula y se asigna de manera inmediata al lado izquierdo de la asignación.
   - Las asignaciones bloqueantes se ejecutan secuencialmente en el orden en que aparecen en el código.
   - Se suele usar asterisco en la lista de sensibilidad para que el bloque sea combinacional(sin memoria)
![[Pasted image 20231011102922.png]]

###### Asignación No Bloqueante (`<=`):
   - Las asignaciones no bloqueantes se realizan utilizando el operador `<=`.
   - Cuando se utiliza una asignación no bloqueante, se programan las asignaciones y el valor en el lado derecho de la asignación se calcula, pero la actualización real de la variable o señal en el lado izquierdo se pospone hasta el final del bloque `always`.
   - Las asignaciones no bloqueantes son útiles para describir el comportamiento secuencial de elementos en un diseño.
   - Estas asignaciones nos genera memoria
   - Debemos elegir si se actualizara con flanco ancedente(posedge) o descendente(negedge)
![[Pasted image 20231011103006.png]]


En SystemVerilog, hay tres tipos principales de bloques `always` que se utilizan para asignar valores a señales o registros en un diseño digital: `always_comb`, `always_latch`, y `always_ff`. Cada uno tiene un propósito específico y se utiliza en situaciones diferentes.

1. **`always_comb`**:
   - **Propósito**: Se utiliza para definir una asignación combinacional. Esto significa que las salidas dependen únicamente de las entradas y no tienen memoria interna. Los bloques `always_comb` se utilizan principalmente para lógica combinacional pura.
   - **Diferencia Principal**: Las asignaciones en bloques `always_comb` se evalúan continuamente en función de las entradas y, por lo tanto, no almacenan ningún valor en registros.

   ```systemverilog
   always_comb begin
       // Lógica combinacional
       output = input1 & input2;
   end
   ```

2. **`always_latch`**:
   - **Propósito**: Se utiliza para definir latches o memorias de nivel bajo, que almacenan información en función de condiciones de habilitación y cambios en las entradas. Es una estructura no recomendada y se debe evitar en diseños modernos debido a su tendencia a generar problemas de sincronización y comportamientos inesperados.
   - **Diferencia Principal**: `always_latch` crea latches, que son estructuras de almacenamiento sensibles a condiciones lógicas que pueden generar problemas de diseño.

   ```systemverilog
   always_latch begin
       if (enable)
           latch = data_in;
   end
   ```

3. **`always_ff`**:
   - **Propósito**: Se utiliza para definir bloques de registro de reloj, que almacenan información sincronizada con una señal de reloj. Los registros son esenciales en diseños secuenciales, como microprocesadores y sistemas de control.
   - **Diferencia Principal**: `always_ff` crea registros que almacenan valores sincronizados con el flanco del reloj. Los registros son elementos de memoria que almacenan datos en el flanco del reloj.

   ```systemverilog
   always_ff @(posedge clock) begin
       if (reset)
           reg <= 0;
       else
           reg <= data_in;
   end
   ```

En Verilog 2001, la estructura es similar, pero no se tienen las mismas convenciones de nomenclatura. Puedes utilizar `always` para crear bloques combinacionales y bloques de registro, pero debes tener cuidado de definir los flancos del reloj y las habilitaciones manualmente en lugar de utilizar `always_ff` o `always_latch`.

Por ejemplo, en Verilog 2001, un bloque de registro en el flanco de subida del reloj se definiría de la siguiente manera:

```verilog
always @(posedge clock) begin
    if (reset)
        reg <= 0;
    else
        reg <= data_in;
end
```

La clave es definir correctamente las condiciones de activación y flancos de reloj según tus necesidades. El uso de `always_comb` o `always_latch` depende del comportamiento deseado de tu diseño, pero `always_ff` es el más común para la sincronización de registros en circuitos digitales.


## Initial
El bloque `initial` se utiliza para inicializar variables y señales antes del inicio de la simulación. El código dentro del bloque `initial` se ejecuta solo una vez al comienzo de la simulación y se utiliza para establecer los valores iniciales de las variables y señales.
**El initial solo se utiliza para simulaciones, no es sintetizable**

Aquí tienes un ejemplo de cómo se utiliza el bloque `initial` en Verilog:

```verilog
reg [7:0] data;

initial begin
  // Inicialización de variables
  data = 8'b00000000;
end
```

En este ejemplo, el bloque `initial` se utiliza para asignar un valor inicial de cero (`8'b00000000`) a la variable `data`.



## Generate
- Un bloque generate se puede usar para crear múltiples instancias de módulos y código, o instanciar modulos y definir código condicionalmente.
- Se definen dentro de un módulo, usando las palabras clave *generate* y *endgenerate*.
- Pueden contener instancias de módulos, declaraciones de asignación continua y bloques procedurales.
- No pueden contener declaraciones de puertos ni de parámetros.
- Pueden ser anidados.
- Tipos:
	- Generate loop (for)
	- Generate condicional (if o case)
### Generate for loop
Permite instancias un modulo o replicar asignaciones N veces
- La variable del loop se debe definir usando el tipo genvar
![[Pasted image 20231013181237.png|500]]

### Generate condicional
- *Generate if:* Permite hacer uso de la sentencia if - else if - else para instanciar módulos o definir bloques de código condicionalmente.
- *Generate case:* Permite hacer uso de la sentencia case para instanciar módulos o definir bloques de código condicionalmente.
![[Pasted image 20231013181331.png|500]]


## Function

La declaración de funciones en Verilog permite crear funciones reutilizables que pueden realizar cálculos o transformaciones en los datos dentro de un diseño digital. Las funciones en Verilog son especialmente útiles para modularizar el código, mejorar la legibilidad y reducir la duplicación de código. 
- Similar a una tarea, ya que también implementa código que se puede llamar varias veces dentro de un módulo.
- Se define en el módulo usando las palabras clave function y endfunction.
- Sólo puede calcular una salida, debiendo tener al menos una entrada.
- La salida debe asignarse a una variable implícita que lleve el nombre y el alcance de la función.
- *No puede utilizar construcciones de tiempo* (#,@).
- Puede ser llamada desde un bloque de procedimiento o una declaración de asignación continua.
- *Puede llamarse desde otras funciones y tareas, mientras que una función no puede llamar a una tarea.*
- *Sólo pueden utilizarse para modelar lógica combinacional* (no soportan asignaciones no bloqueantes).
### Sintaxis

```verilog
function return_type function_name (input_type1 arg1, input_type2 arg2);
    data_type local_variable;
    // Código de la función
    return result;
endfunction
```
- `function`: Palabra clave que indica que estás definiendo una función.
- `return_type`: Tipo de dato que especifica el tipo de valor que devuelve la función. Puede ser `int`, `reg`, `wire`, etc.
- `function_name`: Nombre de la función que se utilizará para invocarla.
- `(input_type1 arg1, input_type2 arg2)`: Parámetros de entrada que la función acepta. Puedes definir múltiples argumentos separados por comas.
- `data_type local_variable`: Declaración de variables locales que la función puede utilizar para cálculos internos.
- `return result`: Declaración que devuelve un valor de acuerdo con el tipo de dato especificado en `return_type`.

### Llamado
Se la debe invocar dentro de un modulo y pasar sus parametros
- Se puede colocar sus argumentos de manera posicional o de manera explicita(igual que los modulos)
### Observaciones
- La asignaciones internas deben ser bloqueantes
- Se puede generar funciones que no retornan anda(como las void)
	- Se lo utiliza por ejemplo para imprimir el tiempo cen el tb
- Se puede pasar el valor por referencia como en C
	- Si queremos que esta funcion reciba la referencia de un valor tenemos que colocar "ref a" pero si queremos que sea el parametro por valor colocamos "input b"
- Una funcion solo puede devolver 1 valor
- Puede tener multiples entradas
- Es costosa con tiempo
- Ten en cuenta que las funciones en Verilog son principalmente útiles en contextos de simulación y no se utilizan en diseños RTL (Register-Transfer Level) para la síntesis.
- Cuando reutilizas una función en Verilog, como en un módulo de diseño, no se duplica el hardware físico en términos de compuertas o elementos lógicos en el FPGA o el ASIC. En cambio, se crean múltiples caminos a través del mismo hardware subyacente.
### Ejemplo
```verilog
function int add(int a, int b);
    reg [31:0] result;
    result = a + b;
    return result;
endfunction
```

En este ejemplo, hemos definido una función llamada `add` que toma dos argumentos de tipo `int`. La función suma los dos números y devuelve el resultado como un valor de tipo `int`.
Para utilizar una función en Verilog, debes invocarla dentro de un bloque siempre (`always`) o un bloque inicial (`initial`) o en otro contexto de diseño apropiado. Aquí tienes un ejemplo de cómo se invoca la función `add`:

```verilog
module Test;
    reg [31:0] a, b;
    wire [31:0] sum;

    initial begin
        a = 5;
        b = 7;
        sum = add(a, b);
        $display("La suma de %d y %d es %d", a, b, sum);
    end
endmodule
```

En este ejemplo, el módulo `Test` utiliza la función `add` para sumar dos números `a` y `b`. La función devuelve el resultado, que se muestra en la simulación utilizando la función `$display`.
.
## Task

Las "tasks" son especialmente útiles cuando necesitas realizar operaciones secuenciales o tareas específicas en tu diseño.
- Se puede utilizar para codificar una funcionalidad que se repite varias veces en un módulo.
- Tiene entradas, salidas y puede tener sus variables locales.
- Todas las variables definidas en el módulo también son accesibles en la tarea.
- Debe definirse en el mismo módulo. Se puede llamar desde varios módulos siempre y cuando esté definida en un archivo aparte que se incluye utilizando la palabra clave ’include dentro de cada módulo.
- Se llaman desde bloques initial o always o desde otras tareas en un módulo.
- Pueden contener declaraciones de tiempo (#,@).
- Pueden usar y/o asignar valores a cualquier señal declarada como global.
- Importa el orden de los puertos de entrada y salida al momento de llamar una tarea.
- Pueden utilizarse para modelar lógica combinacional o secuencial.
- Nos puede servir por ejemplo la generacion de un periodo de reloj durante la simulacion
### Sintaxis básica de una tarea
```systemverilog
task task_name(imput o_sum, input i_in1, in2);
    // Declaraciones locales
    // Código de la tarea
endtask
```

- `task`: Palabra clave que indica que estás definiendo una tarea.
- `task_name`: Nombre de la tarea que se utilizará para invocarla.
- `// Declaraciones locales`: Espacio para declarar variables locales que la tarea utilizará.
- `// Código de la tarea`: Espacio para definir el conjunto de instrucciones y operaciones que compondrán la tarea.

### Ejemplo de una tarea

```systemverilog
module Test;
    reg [3:0] data;
    reg [1:0] result;

    task calculate_parity(
        input [3:0] in_data,
        output [1:0] parity_result);
        reg [3:0] temp;
        reg [1:0] parity;

        begin
            temp = in_data;
            parity = 0;
            while (temp != 0) begin
                parity = parity ^ (temp & 1);
                temp = temp >> 1;
            end
            parity_result = parity;
        end
    endtask

    initial begin
        data = 4'b1101;
        calculate_parity(data, result);
        $display("Parity result for data %b is %b", data, result);
    end

endmodule
```

En este ejemplo, hemos definido una tarea llamada `calculate_parity` que toma un valor de entrada (`in_data`) y calcula la paridad de los bits. Luego, en el bloque `initial`, hemos invocado la tarea `calculate_parity` para calcular la paridad del valor `data` y mostrar el resultado.











