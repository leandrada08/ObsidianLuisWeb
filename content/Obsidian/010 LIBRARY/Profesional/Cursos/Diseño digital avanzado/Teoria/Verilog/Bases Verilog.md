


## Modulo en Verilog
En Verilog, el módulo es una unidad de diseño que encapsula la funcionalidad de un circuito o componente específico. Un módulo en Verilog se define utilizando la palabra clave `module`. Dentro del módulo, se especifican los puertos de entrada y salida, así como las señales internas y la lógica de diseño.
```verilog
module MiModulo(
  input wire A,
  input wire B,
  output wire C
);
  // Declaración de señales internas
  wire D;

  // Lógica de diseño
  // Aquí se define el comportamiento del módulo
  // utilizando operaciones y lógica de Verilog

  // Ejemplo de asignación de valor a una señal interna
  assign D = A & B;

  // Ejemplo de asignación de valor a una señal de salida
  assign C = D ^ A;
endmodule
```

Recuerda que en Verilog, los módulos se pueden interconectar para crear jerarquías más complejas y sistemas digitales completos. Se pueden instanciar múltiples copias del mismo módulo o combinar diferentes módulos para construir el diseño deseado.
- Se recomienda usar 1 modulo por archivo para que sea mas escalable
- Por defecto las entradas y salida con wire
	- Los puertos de entrada siempre deben ser wire
	- Los de salida pueden ser reg
- Para asignar un valor a la señal de salida necesitamos la palabra clave *"assign"*

### Declaracion e instanciacion de un modulo
Los módulos se consideran "declarados" cuando se define su estructura, es decir, se especifican los puertos de entrada y salida, así como las señales internas y la lógica de diseño. Al declarar un módulo, estás creando una plantilla o una descripción de cómo se verá y funcionará ese componente.

```verilog
module MiModulo(
  input wire A,
  input wire B,
  output wire Y
);
  // Lógica interna del módulo
  // ...

  // Asignación de salida
  assign Y = A & B;
endmodule
```

Por otro lado, los módulos se "instancian" cuando se utilizan en el diseño para crear una copia concreta de ese componente. La instancia es esencialmente una "copia" del módulo declarado, con todos los puertos de entrada y salida conectados a señales o a otros módulos. 
#### Instancias
- La instancia consiste en 3 partes
	1. Nombre del modulo(Nombre cuando se declaro el modulo)
	2. Nombre de la instancia(Nombre que tendra el componente en nuestro codigo)
		- Puedo instanciar varias veces un mismo modulo
	3. Declaracion de puertos

```verilog
module TopModule;
  // Declaración de señales y otras lógicas

  // Instanciación de MiModulo
  MiModulo instancia1 (.A(in1), .B(in2), .Y(out1));

  // Más lógica y conexiones
endmodule
```

La distinción entre declaración e instancia es importante porque te permite crear múltiples copias de un módulo y conectarlos de diferentes maneras para formar un sistema digital más complejo. Cada instancia del módulo tiene su propia definición de puertos de entrada y salida, y puede tener su propia lógica interna y señales internas.
Al declarar un módulo, estás definiendo su estructura y comportamiento general. Al instanciar un módulo, estás creando una copia concreta de ese módulo con conexiones específicas.
- Tener en cuenta que todas las instancias son recurrente, por lo tanto no importa el orden en cual la hagamos

### Tipos de instancias
- *Posicional:* Se sigue el orden posicional predefinido cuando declaramos el modulo
	- La desventaja que puede ser confuso para un lector externo y puede generar errores para nosotros porque hay que recordar bien la posicion en que se definio cada puerto
- *Nominal(O paso por nombre):* Cada asignacion de puerte se asigna explicitamente al nombre de un puerto. Es mejor que la anterior porque evita confusiones y errores
![[Pasted image 20231013112230.png|500]]

### Parametros(Parameter)
- Los parametros son constantes que son locales a un modulo
- A un parámetro se le asigna un valor por defecto en el módulo y para cada instancia de este módulo se le puede asignar un valor diferente.
- Los parámetros son muy útiles para mejorar la reutilización de los módulos desarrollados.
- Un módulo se llama parametrizado (parametered) si está escrito de tal manera que el mismo módulo se pueda instanciar para diferentes anchos de puertos de entrada y salida.
#### Parametros locales
- Es una constante local al módulo.
- No pueden cambiar su valor en una instancia.

![[Pasted image 20231013180731.png|600]]
### Puertos
En Verilog, los puertos son las interfaces de comunicación entre un módulo y su entorno. Los puertos definen las entradas y salidas del módulo y permiten la conexión con otros módulos o componentes externos. Hay tres tipos de puertos en Verilog: puertos de entrada, puertos de salida y puertos bidireccionales. Los puertos siguen el formato $$<Direccion><Tipo><Tamaño><Nombre>$$
``` verilog
module MiModulo(
  input wire A, //entrada tipo wire
  input wire B, //entrada tipo wire
  output wire Y, //salida tipo wire
  inout wire [7:0] BUS //entrada/salida tipo wire
);
  // Lógica interna del módulo
  // ...

  // Asignación de salida
  assign Y = A & B;
endmodule

```


### Jerarquias
- Verilog funciona de manera eficiente con un concepto de modelado jerárquico.
- El código Verilog contiene un módulo de nivel superior y puedo o no tener más módulos instanciados.
- El módulo de nivel superior (top level) no se instancia en ningún lugar.
- Pueden existir varias instancias de un módulo de nivel inferior.
- Verilog es un HDL y, a diferencia de otros lenguajes de programación, una vez sintetizado cada instanciación infiere una copia física del hardware con sus propias compuertas lógicas, registros y cables.

## Valores logicos
En Verilog, los valores lógicos se representan utilizando los valores 0 y 1. Estos valores indican los niveles lógicos "bajo" y "alto", respectivamente. Además de estos dos valores, también existen otros valores especiales como x (desconocido), z (alta impedancia) e h (alta impedancia débil), los cuales se utilizan en situaciones específicas.
![[Pasted image 20230611195653.png|500]]

## Tipos de datos
### Wire y Reg
En cuanto a los tipos de datos estándar en Verilog, algunos de ellos son:
*wire:* 
- Se utiliza para representar conexiones lógicas entre componentes. 
- Es un tipo de dato continuo que se utiliza para interconectar las salidas de un módulo con las entradas de otro módulo. 
- Los `wire` transmiten información de manera unidireccional y se utilizan para propagar señales de un lugar a otro dentro del diseño.
- En la sintesis, las variables tipo wire infieren fisicamente un cable.
*reg:*
 - Se utiliza para representar variables secuenciales o combinacionales en el diseño. 
 - Las variables reg se usan para el almacenamiento implícito. Es decir que, al asignarle un determinado valor a una variable reg, a menos que se modifique dicha variable, conservará el valor previamente asignado.
- Una variable reg es inferida como registro o dispositivo de almacenamiento cuando tiene asociado una señal de reloj (clock).
- Es importante notar que una variable de tipo reg no implica necesariamente un registro un hardware, sino que puede inferir un cable físico una vez sintetizada.
![[Pasted image 20230611200640.png]]

### Genvar
El tipo de dato `genvar` es una característica de SystemVerilog, una extensión del lenguaje Verilog, que se utiliza principalmente en contextos de generación de código. El término "genvar" es una abreviatura de "generate variable" (variable de generación) y se utiliza para controlar la creación de instancias de módulos y estructuras de control en bloques `generate`.

**Sintaxis de `genvar` en SystemVerilog:**

``` verilog
genvar nombre_de_genvar;`
```
- `genvar`: La palabra clave que indica que estás declarando una variable de generación.
- `nombre_de_genvar`: El nombre que le das a la variable `genvar`.

## Declaraciones de variables
- Tipo de dato: Especifica el tipo de dato wire/reg.
- Signed/Unsigned: Definición de variable signada o no signada. Por defecto las variables son no signadas.
- Range:
	- Define el número de bits o ancho de palabra de la variable.
	- En el caso de definición de memorias o arreglos la segunda definición determina el número de filas.
	- Sino se definen el rango el valor por defecto es un bit.
- Name: Nombre de la variable.
$$Wire/Reg<signed/unsigned>[<rangeOrWidthword>] <Name> [<RangeOrLenMemory>]$$

![[Pasted image 20231013111016.png]]

## Constantes
- Al igual que las variables, una constante en Verilog puede ser de cualquier tamaño.
- Se puede escribir en formato decimal (d), binario (b), octal (o) o hexadecimal (h). Decimal es el formato predeterminado.
- Una constante se representa como < width >0< type >< value >:
	- Width: Tamaño de la constante.
	- Type: Tipo de formato. 
	- Value: Valor representado.
- Los números decimales sin especificación de tamaño y formato se tratan como enteros con signo.
- Los números decimales con tamaño y formato especificados se tratan como enteros sin signo.
![[Pasted image 20230611202521.png]]
- La base se puede especificar con una letra precedida de un apostrofe
- El tamaño o longitud en bits se puede especificar ingresando un numero antes del apostrofe

## Otras cosas
### Directivas del pre-procesador:
- *‘define:* Define una macro, que consiste en la sustitución de una o varias lineas de texto por un nombre. Se suele usar para definir constantes.
``` verilog
‘define COEFF 6 ’b001101
reg [ 5 : 0 ] term;
initial begin
term = ‘COEFF;
end
```
- *‘ifdef - ‘else - ‘endif :* Condicional pre-compilación.
- *‘include:* Permite insertar el contenido de un archivo fuente en otro archivo durante la compilación en el lugar donde se define el comando. La compilación continúa como si el contenido del archivo fuente incluido apareciera en lugar del comando ‘include. Se suele usar para incluir definiciones y tareas de uso común, evitando código repetido dentro de los módulos. Ejemplo: ‘include “utiles.v”
#### Comentarios en verilog: 
Al igual que C se utilizan // y /* \*/


### Documentacion
- Debemos agregar una extension llamada TerosHDL
- Al principio hay que agregar //! con ciertos datos para que se arme la documentacion de manera automatica


### Observaciones
- A la hora de elegir los bloques que divideremos, analizar fuertemente la cantidad de net(cables)
	- Tambien se puede analizar la posicion de registros para buscarlos tenerlos a la salida de cada bloque
- Todo es concurrente, por lo cual no importa el orden en el cual escribimos, ya que todo se ejecuta al mismo tiempo
- Diferencia entre el latch y el flip flop es que el primero cambio cuando el reloj es 1 y el segundo solo con los flancos positivos.


## Verilog vs VHDL
En Verilog, a diferencia de VHDL, no se utilizan explícitamente las palabras clave "variables" y "señales". En su lugar, se utilizan los conceptos de "reg" (registro) y "wire" (cable).

En Verilog, los registros (`reg`) se utilizan para almacenar valores y representan tanto variables combinacionales como secuenciales. Los registros pueden ser asignados dentro de bloques `always` o `initial` y pueden tener un comportamiento secuencial o combinacional dependiendo de cómo se utilicen.

Por otro lado, los cables (`wire`) se utilizan para representar las conexiones lógicas entre componentes. Los cables transmiten información de manera unidireccional y se utilizan para interconectar las salidas de un módulo con las entradas de otro. Los cables son declarados y asignados utilizando la palabra clave `wire`.

```verilog
module ExampleModule(input a, input b, output c);
  reg result;

  always @(a or b) begin
    // Lógica interna
    if (a & b)
      result = 1;
    else
      result = 0;
  end

  assign c = result; // Asignación de la salida a un cable
endmodule
```
En ambos lenguajes, se utiliza una asignación (`assign` en Verilog y una asignación normal en VHDL) para conectar la salida (`c`) al valor del registro (`result`).






