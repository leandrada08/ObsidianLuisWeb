## Tipos de datos en Python


Los tipos de datos son esenciales en Python para definir el tipo de información que se puede almacenar en una variable. El lenguaje soporta una variedad de tipos de datos, cada uno con sus propias características y usos específicos.

### Tipos de datos básicos:

- **Numéricos:**
    - **int:** Números enteros (por ejemplo, 1, 2, 3).
    - **float:** Números de punto flotante (por ejemplo, 1.5, 3.14).
    - **complex:** Números complejos (por ejemplo, 1+2j, 3-4j).
- **Texto:**
    - **str:** Cadenas de caracteres (por ejemplo, "Hola mundo", "Python").
- **Binario:**
    - **bytes:** Secuencias de bytes (por ejemplo, b"Hola mundo").

### Tipos de datos compuestos:

- **Listas:** Secuencias ordenadas y mutables de cualquier tipo de dato (por ejemplo, \[1, 2, 3\], \["a", "b", "c"]).
- **Tuplas:** Secuencias ordenadas e inmutables de cualquier tipo de dato (por ejemplo, (1, 2, 3), ("a", "b", "c")).
	- Imnutable significa que no se puede cambiar su contenido
- **Diccionarios:** Colecciones de pares clave-valor (por ejemplo, {"nombre": "Juan", "edad": 30}).
- **Conjuntos:** Colecciones no ordenadas y únicas de cualquier tipo de dato (por ejemplo, {1, 2, 3}, {"a", "b", "c"}). 
	- Se pueden modificar
### Conversiones de tipos:

Python permite convertir entre diferentes tipos de datos de forma explícita o implícita.

- **Explícita:** Usando funciones como `int()`, `float()`, `str()` o `list()`.
- **Implícita:** Python realiza conversiones automáticas cuando es necesario (por ejemplo, al sumar un int y un float).

**Ejemplo:**

``` Python
numero_int = 10
numero_float = 3.14

# Conversión explícita
numero_str = str(numero_int)  # "10"
numero_int_2 = int(numero_float)  # 3

# Conversión implícita
suma = numero_int + numero_float  # 13.14
```

### Conjuntos
Los sets en Python son una estructura de datos usada para almacenar elementos de una manera similar a las listas, pero con ciertas diferencias.
- Los elementos de un set son único, lo que significa que no puede haber elementos duplicados
	- Aunque quieramos agregar un elemento duplicado, el lenguaje no nose deja
- Los set son *desordenados*, lo que significa que no mantienen el orden de cuando son declarados.

Resumen: Los conjuntos son un tipo de dato que nos permite almacenar datos que no se repitan, que no tengan orden específico y se puedan modificar.
- Estos tambien se pueden castear a una lista

#### Definir un Set

``` Python
# Definir con palabra reservada
my_set = set()

# De forma explifica
## Es como el diccionario pero sin la clave,valor
my_set_countries={'col','ecu','mx'}

# A partie de un string
set_from_string = set('hola')

# A partir de tuplas
set_from_tuples = set (('abc','cbv','as','abc'))
print (set_from_tuples) 
# Output:
 {'as', 'abc', 'cbv'}

# A partir de listas
numbers = [1,2,3,1,2,3,4]
set_numbers= set(numbers)
print (set_numbers) 
# Output:
 {1, 2, 3, 4}
```

#### Funciones de set:
- conjunto.add(‘elemto‘)→ Añade un elemento.
- conjunto.update(‘listas/tuplas/sting‘)→ Añade cualquier tipo de objeto iterable como: listas, tuplas.
- conjunto.discard()→ Elimina un elemento y si ya no existe no lanza ningún error.
- conjunto.remove(‘elemento‘)→ Elimina un elemento y si este no existe lanza el error “keyError”.
- conjunto.pop()→ Nos devuelve un elemento aleatorio y lo elimina y si el conjunto está vacío lanza el error “key error”.
- conjunto.clear()→ Elimina todo el contenido del conjunto
- len(conjunto) → Tamaño del conjunto


- Para analizar si un elemento esta dentro del conjunto solo debemos hacer el analisis logico
	- ‘ElementoAnalizar’ in ConjuntoAnalizar

#### Operaciones de set:
- set_a.union(set_b): Realiza la operacion “union” entre dos conjuntos. La unión entre dos conjuntos es sumar los elementos de estos sin repetir elementos. Esta operación tambien se puede realizar con el signo “|”: set\_a | set\_b, esta forma es eficiente para cuando queremos hacer print
- set_a.intersection(set_b): Realiza la operacion “intersection” entre dos conjuntos. La intersección entre dos conjuntos es tomar unicamente los elementos en común de los conjutnos. Esta operación tambien se puede realizar con el signo “&”: set\_a & set\_b.
- set_a.difference(set_b): Realiza la operacion “difference” entre dos conjuntos. La diferencia entre dos conjuntos es restar los elementos del segundo conjunto al primero. Esta operación tambien se puede realizar con el signo “-”: set\_a - set\_b.
- set_a.symmetric_difference(set_b): Realiza la operacion “symmetric_difference” entre dos conjuntos. La diferencia simetrica entre dos conjutnos consta de restar todos los elementos de ambos exceptuando el elemento en común. Esta operación tambien se puede realizar con el signo “^”: set\_a ^ set\_b.





### Listas

Las listas en Python son estructuras de datos que permiten almacenar una colección ordenada y mutable de elementos de cualquier tipo.

#### Creación de listas:

Las listas se pueden crear utilizando el constructor `list()` o mediante corchetes `[]`.

``` Python
# Creando una lista vacía
lista = []

# Creando una lista con elementos
lista = [1, 2, "Hola", True]

# Creando una lista con el constructor list()
lista = list(range(10))  # Crea una lista con los números del 0 al 9
```

#### Acceso a elementos:

Se puede acceder a los elementos de una lista por su índice, que comienza en 0.

``` Python
lista = ["a", "b", "c", "d"]

# Accediendo al primer elemento
primer_elemento = lista[0]  # "a"

# Accediendo al último elemento
ultimo_elemento = lista[-1]  # "d"

# Accediendo a un rango de elementos
sublista = lista[1:3]  # ["b", "c"]
```

#### Modificación de listas:

Las listas son mutables, lo que significa que se pueden modificar después de su creación.

``` Python
lista = [1, 2, 3]

# Agregando un elemento al final de la lista
lista.append(4)

# Insertando un elemento en una posición específica
lista.insert(1, "Hola")

# Eliminando un elemento por su índice
lista.pop(2)

# Eliminando un elemento por su valor
lista.remove("Hola")
```

#### Operaciones con listas:

Las listas admiten una gran variedad de operaciones, como concatenación, ordenación y búsqueda.

``` Python
lista1 = [1, 2, 3]
lista2 = [4, 5, 6]

# Concatenación de listas
lista_concatenada = lista1 + lista2  # [1, 2, 3, 4, 5, 6]

# Ordenación de una lista
lista.sort()

# Búsqueda de un elemento en una lista
elemento_encontrado = "Hola" in lista
```

### Diccionarios en Python

Los diccionarios en Python son estructuras de datos que te permiten almacenar colecciones de pares clave-valor. A diferencia de las listas ordenadas por índice, los diccionarios te brindan una forma flexible de organizar información y acceder a ella utilizando claves únicas.

#### Creación de diccionarios:**

Existen dos formas principales para crear diccionarios en Python:

- **Utilizando llaves `{}`:**

``` Python
# Diccionario vacío
diccionario = {}

# Diccionario con pares clave-valor
diccionario = {"nombre": "Juan", "edad": 30, "ciudad": "Madrid"}
```

- **Utilizando el constructor `dict()`:**

``` Python
diccionario = dict(nombre="Juan", edad=30, ciudad="Madrid")
```

#### Acceso a valores:

Para acceder a un valor en un diccionario, se utiliza la clave asociada a ese valor entre corchetes `[]`.

``` Python
diccionario = {"nombre": "Juan", "edad": 30, "ciudad": "Madrid"}

nombre = diccionario["nombre"]  # "Juan"
edad = diccionario["edad"]      # 30
```

#### Iteración sobre diccionarios:

Puedes iterar sobre las claves o los valores de un diccionario utilizando un bucle `for`.

``` Python
diccionario = {"nombre": "Juan", "edad": 30, "ciudad": "Madrid"}

# Iterar sobre las claves
for clave in diccionario:
    print(clave)  # "nombre", "edad", "ciudad"

# Iterar sobre los valores
for valor in diccionario.values():
    print(valor)  # "Juan", 30, "Madrid"
```

#### Comprobación de claves y valores:

- **Comprobar si una clave existe:** Utiliza el operador `in` para verificar si una clave específica está presente en el diccionario.

``` Python
diccionario = {"nombre": "Juan", "edad": 30}

if "ciudad" in diccionario:
    print("La clave 'ciudad' existe en el diccionario")
else:
    print("La clave 'ciudad' no existe en el diccionario")
```

- **Obtener valor por defecto:** El método `get(clave, valor_por_defecto)` te permite recuperar el valor asociado a una clave o un valor por defecto si la clave no existe.

``` Python
diccionario = {"nombre": "Juan", "edad": 30}

ciudad = diccionario.get("ciudad", "Desconocida")
print(ciudad)  # "Desconocida" (porque la clave "ciudad" no existe)
```

#### Modificación de diccionarios:

Los diccionarios son mutables, lo que significa que puedes modificar su contenido después de la creación.

- **Agregar un par clave-valor:** Asigna un nuevo valor a una clave inexistente para añadirlo al diccionario.

``` Python
diccionario = {"nombre": "Juan", "edad": 30}
diccionario["ciudad"] = "Madrid"
```

- **Modificar un valor:** Asigna un nuevo valor a una clave existente para actualizar el valor asociado.

``` Python
diccionario = {"nombre": "Juan", "edad": 30}
diccionario["edad"] = 31
```

- **Eliminar un par clave-valor:** Utiliza la instrucción `del` para eliminar un par clave-valor por su clave.

``` Python
diccionario = {"nombre": "Juan", "edad": 30, "ciudad": "Madrid"}
del diccionario["ciudad"]
```

#### Funciones útiles con diccionarios:

- **`keys()`:** Devuelve una vista de las claves del diccionario como una lista.
- **`values()`:** Devuelve una vista de los valores del diccionario como una lista.
- **`items()`:** Devuelve una vista de los pares clave-valor del diccionario como una lista de tuplas.



### Tuplas en Python

Las tuplas en Python son colecciones ordenadas e inmutables de elementos. Esto significa que, a diferencia de las listas, una vez creada una tupla, no puedes modificar sus elementos.

#### Creación de tuplas:

Las tuplas se pueden crear utilizando dos métodos principales:

1. **Paréntesis `()` (opcional):** Aunque las tuplas se pueden definir sin paréntesis si contienen un solo elemento, se recomienda usarlos siempre para mayor claridad.

``` Python
# Tupla con un elemento (requiere paréntesis)
tupla_un_elemento = (1,)

# Tupla con varios elementos
tupla = (1, "Hola", 3.14)
```

2. **Constructor `tuple()`:** El constructor `tuple()` se puede utilizar para convertir elementos iterables (como listas) en tuplas.

``` Python
lista = [1, "Hola", 3.14]
tupla = tuple(lista)
```

**Acceso a elementos:**

Al igual que en las listas, se accede a los elementos de una tupla por su índice, que comienza en 0.

Python

```
tupla = (1, "Hola", 3.14)

primer_elemento = tupla[0]  # 1
segundo_elemento = tupla[1]  # "Hola"

# También puedes acceder a elementos desde el final con índices negativos
ultimo_elemento = tupla[-1]  # 3.14
```

**Desempaquetado de tuplas:**

El desempaquetado de tuplas te permite asignar valores de la tupla a variables individuales en una sola línea.

Python

```
tupla = ("Juan", 30, "Madrid")
nombre, edad, ciudad = tupla

print(nombre)  # "Juan"
print(edad)    # 30
print(ciudad)  # "Madrid"
```

**Operaciones con tuplas:**

Las tuplas admiten algunas operaciones básicas como:

- **Concatenación:** Puedes concatenar dos tuplas para crear una nueva.

Python

```
tupla1 = (1, 2, 3)
tupla2 = (4, 5, 6)

tupla_concatenada = tupla1 + tupla2
print(tupla_concatenada)  # (1, 2, 3, 4, 5, 6)
```

- **Comprobación de pertenencia:** Utiliza el operador `in` para verificar si un elemento está presente en la tupla.

Python

```
tupla = (1, "Hola", 3.14)

if "Hola" in tupla:
    print("El elemento 'Hola' está en la tupla")
```

- **Obtener el tamaño de la tupla:** Utiliza la función `len()` para obtener el número de elementos en la tupla.

Python

```
tupla = (1, "Hola", 3.14)

largo_tupla = len(tupla)
print(largo_tupla)  # 3
```

**Cuándo usar tuplas:**

Las tuplas son útiles cuando necesitas una colección de elementos ordenada y que no se modifique después de su creación. Por ejemplo, las tuplas se pueden usar para representar coordenadas (x, y), representar días de la semana o almacenar valores constantes.

**Recursos adicionales:**

- **Documentación oficial de Python:** [https://docs.python.org/3/tutorial/datastructures.html](https://docs.python.org/3/tutorial/datastructures.html)
- **Tutorial sobre tuplas en Python:** [https://www.w3schools.com/python/python_tuples.asp](https://www.w3schools.com/python/python_tuples.asp)

Te invito a consultarme si tienes alguna duda o si quieres que profundice en algún aspecto específico de las tuplas.