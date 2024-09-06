## Type definition
- System Verilog
"Type Definition" (Definición de Tipo) permite definir tus propios tipos de datos personalizados. Esto es útil para crear tipos de datos más legibles y específicos para tu diseño.
### Sintaxis básica de una definición de tipo en SystemVerilog:

```systemverilog
typedef tipo_base nombre_del_tipo;
```

- `typedef`: Palabra clave que indica que estás creando una definición de tipo.
- `tipo_base`: Tipo de datos existente en Verilog o SystemVerilog (por ejemplo, `reg`, `wire`, `int`, etc.), que servirá como base para tu nuevo tipo.
- `nombre_del_tipo`: El nombre que le das a tu nuevo tipo de datos.

### Ejemplo de una definición de tipo en SystemVerilog:

```systemverilog
typedef reg [7:0] byte_t;
```

En este ejemplo, hemos definido un nuevo tipo de datos llamado `byte_t`, que se basa en el tipo de dato `reg` y tiene una longitud de 8 bits. Ahora, puedes utilizar `byte_t` para declarar variables en lugar de `reg [7:0]`, lo que hace que tu código sea más legible y claro.

### Ejemplo de matrices
Las definiciones de tipo en SystemVerilog también se pueden utilizar para crear matrices personalizadas o tipos de datos estructurados.

```systemverilog
typedef reg [7:0] byte_t; // Definimos el tipo de dato para un byte

typedef byte_t [3:0] [3:0] matrix_t; // Definimos el tipo de matriz personalizado
```

```systemverilog
module Test;
    matrix_t my_matrix;

    initial begin
        // Inicializar la matriz con algunos valores
        my_matrix[0][0] = 8'b11011010;
        my_matrix[1][2] = 8'b00110011;
        my_matrix[3][1] = 8'b10101010;

        // Acceder a los elementos de la matriz
        byte_t element = my_matrix[2][3];
        $display("Elemento en (2, 3): %b", element);
    end
endmodule
```

En este ejemplo, hemos declarado una matriz de 4x4 llamada `my_matrix` utilizando el tipo de matriz personalizado `matrix_t`. Luego, hemos inicializado algunos elementos de la matriz y hemos accedido a un elemento específico utilizando la notación de matriz.



## Type Enum
- System Verilog
- Type Enum
	- Sirve para definir tipos enumerados como los estados de una maquina de estado finito
	- Pero tener en cuenta que usa muchos mas recursos cuando usamos enum, usa datos de 32 bit
	- Aunque lo hace de manera mas rapida al sistema ya que se fija que cambie la cantidad menor de bits entre los cambio de estado para evitar errores.

### Sintaxis básica de un tipo enumerado en SystemVerilog:

```systemverilog
typedef enum {valor1, valor2, valor3, ...} nombre_del_enum;
```

- `typedef enum`: Declaración que indica que estás definiendo un tipo enumerado.
- `{valor1, valor2, valor3, ...}`: Lista de los valores discretos que conforman el tipo enumerado. Cada valor se separa por comas.
- `nombre_del_enum`: El nombre que le das al tipo enumerado.

**Ejemplo de un tipo enumerado en SystemVerilog:**

```systemverilog
typedef enum {S0, S1, S2, S3, S4} state_enum;
```

En este ejemplo, hemos definido un tipo enumerado llamado `state_enum` que representa estados discretos, numerados desde `S0` hasta `S4`. Estos estados pueden utilizarse para representar estados en una máquina de estado, opciones de control, eventos, y más.



## Type struct
- System Verilog

Una estructura en SystemVerilog es un tipo de dato compuesto que te permite agrupar múltiples variables de diferentes tipos en una sola entidad. Las estructuras son útiles para organizar datos relacionados en un solo objeto, lo que mejora la legibilidad y la claridad del código. A continuación, se explica cómo funcionan las estructuras en SystemVerilog:

### Sintaxis básica de una estructura en SystemVerilog:

```systemverilog
struct nombre_de_la_estructura;
    tipo_de_dato1 variable1;
    tipo_de_dato2 variable2;
    // ... Más variables
endstruct
```

- `struct`: Palabra clave que indica que estás definiendo una estructura.
- `nombre_de_la_estructura`: El nombre que le das a la estructura.
- `tipo_de_dato1`, `tipo_de_dato2`, etc.: Los tipos de datos de las variables dentro de la estructura.
- `variable1`, `variable2`, etc.: Los nombres de las variables dentro de la estructura.

### Ejemplo de una estructura en SystemVerilog:

```systemverilog
struct Person;
    string name;
    int age;
    bit [7:0] id;
endstruct
```

En este ejemplo, hemos definido una estructura llamada `Person` que agrupa tres variables: `name` (una cadena de texto), `age` (un número entero) e `id` (un byte de 8 bits).

**Uso de una estructura:**


```systemverilog
module Test;
    Person person1;
    Person person2;

    initial begin
        person1.name = "Alice";
        person1.age = 28;
        person1.id = 8'b11011010;

        person2.name = "Bob";
        person2.age = 35;
        person2.id = 8'b00110011;

        $display("Nombre de person1: %s, Edad: %d, ID: %b", person1.name, person1.age, person1.id);
        $display("Nombre de person2: %s, Edad: %d, ID: %b", person2.name, person2.age, person2.id);
    end
endmodule
```




## Type Arrays
- Type arrays
	- Ojo con como se define porque si se define de una manera, sin importar el tamaño del dato usara 32 bits en cada variable, encambio de otra manera se van agrupando para no dejar espacio vacio
En Verilog, puedes trabajar con arrays estáticos y dinámicos para organizar y manipular conjuntos de datos. Aquí te explico ambos tipos de arrays:

###  Arrays Estáticos:
Los arrays estáticos tienen un tamaño fijo que se determina en tiempo de compilación. Esto significa que el número de elementos del array se especifica en la declaración y no puede cambiarse en tiempo de ejecución. Estos arrays son útiles cuando necesitas un conjunto de datos con un tamaño constante y bien definido en tu diseño.

#### Sintaxis de un array estático en Verilog:

```verilog
tipo_de_dato nombre_del_array [tamaño];
```

- `tipo_de_dato`: El tipo de datos de los elementos del array.
- `nombre_del_array`: El nombre que le das al array.
- `tamaño`: El número de elementos del array, que debe ser un valor constante en tiempo de compilación.

#### Ejemplo de un array estático:

```verilog
reg [7:0] static_array [3]; // Array estático de 4 elementos de 8 bits
```


### Arrays Multidimensionales:

Los arrays multidimensionales son arrays que tienen más de una dimensión. Puedes pensar en ellos como una tabla o matriz de datos. Por ejemplo, un array bidimensional se usa comúnmente para representar una matriz, mientras que un array tridimensional se usa para representar un cubo de datos tridimensionales. La utilización de memoria de los arrays multidimensionales depende de la cantidad de elementos en cada dimensión y del tipo de dato que almacenan.

#### Ejemplo de un array bidimensional en Verilog:

```verilog
reg [7:0] matrix [3][4]; // Array bidimensional de 3 filas y 4 columnas
```

En este ejemplo, el array bidimensional `matrix` tiene 3 filas y 4 columnas. La cantidad total de elementos en este array será 3 * 4 = 12 elementos, cada uno de 8 bits. La memoria se asignará para almacenar estos 12 elementos, y la utilización de memoria dependerá de su contenido.
![[Pasted image 20231013175016.png|500]]
![[Pasted image 20231013175057.png|500]]

