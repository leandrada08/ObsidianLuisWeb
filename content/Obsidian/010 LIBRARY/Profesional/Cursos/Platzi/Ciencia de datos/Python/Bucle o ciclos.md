## Bucles o ciclos en Python

**Introducción:**

Los bucles o ciclos en Python permiten ejecutar un bloque de código de forma repetitiva hasta que se cumpla una condición.

### Tipos de bucles:

#### Bucle `for`:
Se utiliza para iterar sobre una secuencia de elementos.

``` Python
for elemento in secuencia:
    # Bloque de código que se ejecuta para cada elemento
```

**Ejemplo:**

``` Python
numeros = [1, 2, 3, 4, 5]

for numero in numeros:
    print(numero)
```

#### Bucle `while`:
Se utiliza para ejecutar un bloque de código mientras se cumpla una condición.

``` Python
while condicion:
    # Bloque de código que se ejecuta mientras la condición sea verdadera
```

**Ejemplo:**


``` Python
numero = 1

while numero <= 5:
    print(numero)
    numero += 1
```

#### Bucle `else` (opcional):
Se puede usar con un bucle `for` o `while` para ejecutar un bloque de código cuando el bucle termina.

``` Python
for elemento in secuencia:
    # Bloque de código que se ejecuta para cada elemento
else:
    # Bloque de código que se ejecuta cuando el bucle termina
```

**Ejemplo:**

``` Python
numeros = [1, 2, 3, 4]

for numero in numeros:
    print(numero)
else:
    print("Se ha terminado de iterar la lista")
```

#### Sentencias `break` y `continue`:

- **`break`:** Se utiliza para salir de un bucle de forma anticipada.
- **`continue`:** Se utiliza para pasar a la siguiente iteración del bucle sin ejecutar el resto del código del bloque.

**Ejemplo:**

``` Python
numeros = [1, 2, 3, 4, 5]

for numero in numeros:
    if numero == 3:
        break
    print(numero)
```

