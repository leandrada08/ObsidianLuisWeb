## Operadores y condicionales en Python

**Operadores:**

Python ofrece una amplia gama de operadores para realizar operaciones matemáticas, lógicas y de comparación.

**Operadores matemáticos:**

- **+:** Suma
- **-:** Resta
- ***:** Multiplicación
- **/:** División
- **//:** División entera
- **%:** Módulo

**Operadores lógicos:**

- **and:** Conjunción
- **or:** Disyunción
- **not:** Negación

**Operadores de comparación:**

- **==:** Igualdad
- **!=:** Desigualdad
- **<:** Menor que
- **<=:** Menor o igual que
- **>:** Mayor que
- **>=:** Mayor o igual que

**Ejemplos:**


``` Python
# Operadores matemáticos
suma = 1 + 2  # 3
resta = 5 - 3  # 2
multiplicacion = 4 * 5  # 20
division = 10 / 2  # 5.0
division_entera = 10 // 3  # 3
modulo = 10 % 3  # 1

# Operadores lógicos
resultado_and = True and False  # False
resultado_or = True or False  # True
resultado_not = not True  # False

# Operadores de comparación
igualdad = 1 == 1  # True
desigualdad = 2 != 2  # False
menor_que = 3 < 4  # True
menor_o_igual_que = 4 <= 4  # True
mayor_que = 5 > 4  # True
mayor_o_igual_que = 6 >= 5  # True
```

**Condicionales:**

Las sentencias condicionales permiten ejecutar diferentes bloques de código en función de una condición.

**Sentencia `if`:**

``` Python
if condicion:
    # Bloque de código si la condición es verdadera
else:
    # Bloque de código si la condición es falsa
```

**Ejemplo:**

``` Python
edad = 18

if edad >= 18:
    print("Eres mayor de edad")
else:
    print("Eres menor de edad")
```

**Sentencia `elif`:**

``` Python
if condicion1:
    # Bloque de código si la condición1 es verdadera
elif condicion2:
    # Bloque de código si la condición2 es verdadera
else:
    # Bloque de código si ninguna condición es verdadera
```

**Ejemplo:**

``` Python
calificacion = 8

if calificacion >= 9:
    print("Excelente")
elif calificacion >= 7:
    print("Bien")
else:
    print("Regular")
```

**Operadores ternarios:**

Permiten realizar una comparación y asignar un valor a una variable en una sola línea.

``` Python
variable = condicion if expresion_verdadera else expresion_falsa
```

**Ejemplo:**

``` Python
es_mayor_de_edad = True
mensaje = "Eres mayor de edad" if es_mayor_de_edad else "Eres menor de edad"

print(mensaje)
```

