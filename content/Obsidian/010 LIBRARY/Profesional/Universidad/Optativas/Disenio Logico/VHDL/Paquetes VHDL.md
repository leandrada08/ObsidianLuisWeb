## Paquetes
Los paquetes en VHDL son una forma de agrupar elementos relacionados, como tipos de datos, constantes, funciones y procedimientos, en un solo lugar para facilitar su reutilización en diferentes partes del diseño. Los paquetes se definen en una entidad separada y se pueden utilizar en otras entidades o arquitecturas mediante la directiva "use" o "library".
``` VHDL
USE STD_LOGIC_1164.all;
```
Si el paquete esta en una libreria distinta a la que viene por defecto hay que agregarla
``` VHDL
library work;

```
#### Estandar por defecto
Paquete que viene instalado por defecto y no hace falta declararlo. Tiene los siguientes tipos
- *Tipo BIT:* Solo tiene los valores 0 y 1, pero tienen que ser ideales si no no funciones
``` VHDL
SIGNAL a_temp : BIT;
SIGNAL temp : BIT_VECTOR(3 DOWNTO 0);
```
- *Tipo BOOLEAN:* Asume un falso o verdadero para la senial intermedia, se usa para asignaciones condicionales.
- *Tipo INTEGER:* Es un tipo de dato entero, tiene valores positivos y negativos
	- Hay que definir el rango de nuestro valor
	- Tambien existe el tipo NAURAL o POSITIVE.
``` VHDL
SIGNAL int_tmp: INTEGER; -- Reserva 32 bit
SIGNAL int_tap1: INTEGER RANGE 0 TO 255; -- 8 bit
```
- *Tipo CHARACTER:* Para describir caracteres con codigo ASCII
- *Tipo STRING:* Vector de caracteres
- *Tipo TIME:* PAra poner numeros en unidades de tiempo
- *Tipo REAL:* Punto flotante de doble precision(64 bit)
### Estandar de IEEE
El estándar IEEE 1076-2008 define las características y requisitos para los paquetes VHDL. Los paquetes estándar más utilizados son:
#### Paquete *STD_LOGIC_1164:* 
- *Tipo STD_LOGIC:* Variable que puede tomar 9 valores(U(indefinido),X(Desconocido),0,1,Z(3 estado, alta impendacia),W,L,H,-) 
	- Resuelto situaciones de varias conexiones a un mismo cable, mediante alta impedancia
- *Tipo STD_LOGIC_VECTOR:* Vector de STD_LOGIC
- Permite detectar flancos de subida y bajada(risng_edge() y folling_edge())
- Define los operadores relacionales y lógicos para el manejo de señales. 
#### Paquete *NUMERIC_STD:* 
- Define los tipos de datos enteros y de punto flotante y los operadores aritméticos correspondientes.
- Define los tipos de daos unsigned y signe y permite operaciones para estos tipos
- *NUMERIC_STD_UNSIGNED:*
	- Trata a los std_logic_vector como unsigned.
### Crear tu tipo de dato
VHDL permite crear tipos nuevos de variables, contantes y seniales: *Subtipos, tipos de datos enumerados y arreglos*
#### Subtipo
Es un tipo limitable, es sintetizable si el tipo base es sintetizable, ayuda a convertir el codigo mas legible. Se lo define en la arquitectura y solo existe aqui
``` VHDL
ARCHITECTURE logic OF subtipo_test IS
	SUBTYPE word IS std_logic_vector(31 downto 0);-- Defino el subtipo
	SIGNAL mem_read, mem_write: word; -- Uso el subtipo
BEGIN
```
#### Tipos de datos enumerados
Permite crear datos de tipo "nombre" y de diferentes "valores". Usado para maquinas de estado finito.
``` VHDL
-- Declaracion generica
TYPE NombreTipo IS
	(Valores_Del_Tipo_Separado_con_Comas);

-- Ejemplo
TYPE enum IS(idle, fill, heat_w, wash, drain);
```

#### Arreglos
Crea un tipo de datos multidimensional. Es muy usado en meoria. Basicamente es como un vector columna de los datos que le pongamos
``` VHDL
TYPE Array_Nombre IS ARRAY Cantidad_De_Filas OF
	Tipo_de_Dato;
```

### Crea tu paquete
1.  Crear un archivo nuevo con extensión ".vhd".
2.  Escribir el código para definir el paquete. El código debe incluir los elementos que se desean agrupar, como tipos de datos, constantes, funciones y procedimientos. La sintaxis para definir un paquete es la siguiente:
``` VHDL
package nombre_paquete is
  -- Declaraciones de tipos, constantes, funciones y procedimientos
end nombre_paquete;
```
3.  Guardar el archivo con el nombre del paquete y la extensión ".vhd".
4.  Utilizar el paquete en otras partes del diseño mediante la directiva "use" o "library".