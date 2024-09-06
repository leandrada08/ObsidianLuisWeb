## Entidad
En VHDL, una entidad (entity) es una descripción abstracta de un componente digital que especifica su interfaz y comportamiento. Una entidad describe la estructura lógica de un componente digital, lo que significa que define las entradas y salidas del componente, así como su funcionalidad. Basicamente en esta parte le tengo que avisar al bloque que debe esperar y que debe enviar
Declaracion general
``` VHDL
ENTITY <entity_name> IS
	DeclaracionesGenericas
	DeclaracionDePuertos
END ENTITY <entity_name>;
```
Declaracion mas especifica
``` VHDL
ENTITY <entity_name> IS
	GENERIC(
		tmax_cnt : integer=324;
	);
	PORT(
		clk :IN std_logic;
		q: OUT std_logic
	);
END ENTITY <entity_name>;
```
Una vez definida la entidad, se puede describir su comportamiento mediante una arquitectura (architecture) que implemente la entidad. La arquitectura define la lógica interna del componente digital utilizando procesos, asignaciones, operadores lógicos, etc. La arquitectura se asocia con la entidad mediante la palabra clave

## Arquitectura
En VHDL, una arquitectura (architecture) es una descripción concreta de la lógica interna de una entidad, que implementa su comportamiento. Una arquitectura contiene la lógica que describe el funcionamiento interno del componente digital que se ha definido en la entidad
- Analogo a un esquematico.
- Se asocia a una Entidad
Declaracion
``` VHDL
ARCHITECTURE Arq_Nombre OF Entidad_Nombre IS
	Declaracion de seniales internas
	Declaracion de tipo de datos enumerados
	Declaracion de componentes
BEGIN
	Sentencias de asignación de señal
	Procesos
	Instanciacion de componentes
END ARCHITECTURE Arq_Nombre;
```
### Componentes
En VHDL, un componente es una entidad que se puede utilizar en la descripción de otra entidad o arquitectura. En otras palabras, un componente es una pieza de hardware digital que se puede utilizar en la construcción de un sistema más grande.
#### Declaracion de componentes
La declaración de componentes en VHDL se utiliza para definir piezas de hardware digital que se pueden utilizar en la construcción de sistemas más grandes. La declaración del componente se realiza utilizando la misma sintaxis que en la declaración de la entidad, y se incluyen las declaraciones de entradas y salidas correspondientes. El componente se utiliza dentro de una entidad o arquitectura utilizando la palabra clave "port map", asignando las entradas y salidas correspondientes a los puertos definidos en el componente
``` VHDL
COMPONENT Nombre_Componente IS
	PORT(
		Nombre_Puerto1:Mode Tipo;
		Nombre_Puerto2:Mode Tipo;
	);
END COMPONENT Nombre_Componente;
```
#### Instanciacion de componentes
La instanciación de un componente en VHDL es el proceso de crear una instancia de ese componente en una entidad o arquitectura. Es decir, se crea una copia del componente dentro de la entidad o arquitectura para que se pueda utilizar en el diseño.
*Instaciacion generica:*
``` VHDL
nombre_instancia : nombre_componente
port map (lista_de_asignaciones);

```

**Instanciacion sin componente:**
``` VHDL
U1: entity work.NAND2 port map (a=>S1, z=>S3, b=>S2);

```
##### Listas de asignaciones
1. *Posicionales:*
``` VHDL
U1: NAND2 port map(s1, s2);
-- En este caso s1 es el puerto 1 y s2 el puerto 2
```
2. *Nominal:*
``` VHDL
U1: NAND2 port map(Puerto1=>s1, Puerto2=>s2);
```

*Ejemplo estructura completa:*
``` VHDL

entity mi_entidad is
    port (entrada1, entrada2 : in std_logic;
          salida1, salida2 : out std_logic);
end entity mi_entidad;

architecture mi_arquitectura of mi_entidad is
    component mi_componente is
        port (entrada : in std_logic;
              salida : out std_logic);
    end component mi_componente;
    
    signal intermedio : std_logic;
begin
    componente1 : mi_componente
        port map (entrada => entrada1, salida => intermedio);
    salida1 <= intermedio and entrada2;
    componente2 : mi_componente
        port map (entrada => entrada2, salida => salida2);
end architecture mi_arquitectura;
```
##### Seniales desconectadas
Para dejar desconectar una entrada hay que conectarla a open
``` VHDL
U2: NAND2 port map(Puerto1=>s1,Puerto2=>open);
```
- Una entrada digital no puede quedar al aire


#### Observaciones
- Evitamos pegar el componente
- El archivo del componente deber estar en la carpeta del proyecto para poder usarlo



## Identificadores
En VHDL, un identificador es un nombre que se utiliza para identificar una entidad, arquitectura, señal, variable, constante, tipo de datos u otro objeto en el código. 
Al elegir un identificador en VHDL, es importante seleccionar un nombre descriptivo y significativo que refleje la función o propósito del objeto que se está identificando. Esto hace que el código sea más fácil de entender y mantener. Al continuacion reglas que se deben seguir a la hora de elegir un identificador:
- Solo puede contener letras del alfabeto(de la A a la Z), digitos decimales(del 0 al 9) y el guion bajo(\_)
- Debe comenzar con una letra
- No puede terminar con el caracter guion bajo
- No puede inclui dos guiones bajos sucesivos
- VHDL no es sensible  a la mayuscula
- No se permiten espacio en blanco
## Objeto
En VHDL, un objeto es una entidad que se utiliza para representar una entidad física o lógica en el diseño digital. Los objetos pueden ser señales, variables, constantes, tipos de datos, componentes, instancias de entidades, puertos y procesos.
Los objetos en VHDL se utilizan para modelar el comportamiento de los circuitos digitales y para definir las entradas y salidas del sistema. Por ejemplo, una señal en VHDL representa una línea de comunicación física o lógica en el circuito, y se utiliza para transmitir información entre diferentes componentes.
Los objetos en VHDL son importantes porque permiten definir el comportamiento y la estructura del circuito digital de manera clara y precisa. Esto hace que sea más fácil diseñar, simular y verificar el circuito, y ayuda a garantizar que el diseño cumpla con los requisitos del sistema.
Cada objeto tiene *tipo y clase*. El *tipo* indica la naturaleza del dato que se espera del objeto y la *clase* indica que se puede hacer con el objeto y los valroes posibles que pueden tomar.Por ejemplo, un objeto de tipo entero en VHDL puede contener valores enteros entre -2^31 y 2^31-1 y se pueden realizar operaciones aritméticas como la suma y la resta.
![[Pasted image 20230328082646.png|500]]
### Senial
Representan interconexiones fisicas entre bloques funcionales o de entrada/salida
![[Pasted image 20230328083504.png|500]]
- Las entradas y salidas se declaran en la entidad
- Las internas en la arquitectura
**Declaracion de seniales en arquitectura:**
- Se realiza en la parte de la arquitectura
- Se separa con punto y coma
``` VHDL
signal count_i: std_logic; --signal: es identificador reservado para seniales
-- count_i: nombre de la senial
--std_logic: tipo de senial
```
**Declaracion de seniales en la Entidad:**
- Se separan con punto y coma
- Se realizar en PORT en la entidad
``` VHDL
reset_n: in std_logic; --reset_n: nombre de la senial
--in: Modo de puerto(in,out,inout)
--std_logic: Type signal
```
**Valores Iniciales:**
- Solo se usa para simulacion. No genera hardware
- Son transparentes para la sintesis
- Se puede asignar el valor en la declaracion o por defaut. Por defecto toma el valor '0',std_logic toma U y Bolean es falso
``` VHDL
signal ini_cnt: std_logic_vector(3 downto 0) :="1111"; -- En este caso estamos definiendo un vector y asignandole un valor 
constant bus_width: integer := 16;
```
- Si es constant genera hardware
- Tener cuidado si lo definimos creciente o decreciente, para que cuando hagamos asignacion no tengamos problemas
- Tambien se lo puede escribir en Hexadecimal
``` VHDL
temp <= "10101010";
temp <= x"aa";
```
##### Asignaciones de seniales
**Asignacion simple de seniales:**
- Siempre de izquierda a derecha
- Tener en cuenta el tipo de senial
``` VHDL
count <= count+1 --En este caso necesitamos que sea tipo entero
carry_out <= (a and b) or (a and c) --En este caso se puede podria trabajar con bool o std_logic
```
**Condicional:**
``` VHDL
Nombre_senial <= Valor1Senial WHEN Condicion1 ELSE
				Valor2Senial WHEN Condicion2 ELSE
				Valor3Senial WHEN Condicion3 ELSE
				--...
				ValornSenial WHEN Condicionn ELSE
				ValorDefecto;
```
**Seleccionada:**
``` VHDL
WITH Expresion SELECT
Nombre_senial<= Valor1Senial WHEN Condicion1,
				Valor2Senial WHEN Condicion2,
				--...
				ValornSenial WHEN OTHERS;
```
### Variable
En VHDL, las variables se utilizan para almacenar valores temporales y realizar cálculos dentro de un proceso. Las variables son similares a las variables en otros lenguajes de programación y pueden tener un tipo de dato específico, como integer, boolean, o std_logic.
Las variables se declaran dentro de un proceso usando la palabra clave "variable" seguida de un identificador y el tipo de dato deseado. A diferencia de las señales, las variables se inicializan automáticamente al valor predeterminado del tipo de dato, por lo que no es necesario asignar un valor inicial explícito.
Las variables en VHDL tienen algunas características importantes que deben tenerse en cuenta:
-   El ámbito de la variable está limitado al proceso en el que se declaró. No se puede acceder a una variable fuera del proceso en el que se declaró.
-   El valor de una variable se actualiza inmediatamente después de que se le asigna un nuevo valor.
-   Las variables se utilizan para realizar cálculos y almacenar valores temporales dentro de un proceso, y no para representar conexiones físicas entre componentes.
### Diferencia entre variable y senial
La principal diferencia entre ambos es que las señales representan una conexión física entre los componentes del circuito, mientras que las variables se utilizan para realizar cálculos y almacenar valores temporales dentro de un proceso.
-   Comportamiento: Las señales tienen un comportamiento asíncrono, lo que significa que pueden cambiar de valor en cualquier momento. Las variables, por otro lado, tienen un comportamiento síncrono, lo que significa que sólo cambian de valor cuando se ejecuta un proceso. 
-   Asignación de valores: En VHDL, las señales se asignan mediante el operador <=, que indica una asignación no bloqueante. Esto significa que la señal mantiene su valor anterior hasta que se completa la asignación. Por otro lado, las variables se asignan mediante el operador :=, que indica una asignación bloqueante. Esto significa que la variable se actualiza inmediatamente después de la asignación.  
-   Alcance: Las señales tienen un alcance global dentro de la arquitectura y se pueden acceder desde cualquier proceso. Las variables, por otro lado, tienen un alcance local dentro de un proceso y no se pueden acceder desde fuera de él.
-   Tipo de dato: Las señales y las variables pueden tener el mismo tipo de dato, pero las señales también pueden tener un tipo de dato compuesto, como un array o una estructura.
-   Uso: Las señales se utilizan para representar conexiones físicas entre componentes, como entradas y salidas de un módulo. Las variables se utilizan para realizar cálculos y almacenar valores temporales dentro de un proceso.
### Constante
Mantiene un valor de un tipo especifico. El valor asignado no puede cambiar.
- Tienen alcance local
*Declaracion:* 
``` VHDL
constant <identifier>: type := value;
```
**Usos:**
- Se puede utilizar para crear paquetes
``` VHDL
package my_package is
	constant mi_contador: integer:=5;
	constant mi_cuenta: std_logic_vector(3 downto 0):="1111";
end package;
```
- Para valores genericos 
``` VHDL
entity CPU is
end CPU;
```






## Observaciones
- VHDL no es sensible a mayusculas
- Las palabras que se pintan en azul son reservadas para sintaxsis del lenguaje
- En VHDL cada proceso es secuencial, se ejecuta linea a linea, en cambio, en la arquitectura se ejecuta todo en paralelo, no importa el orden de las cosas.
- Los comentarios van con \- \- 
- *Consultar a profe sobre procesos sin lista de sensibilidad*