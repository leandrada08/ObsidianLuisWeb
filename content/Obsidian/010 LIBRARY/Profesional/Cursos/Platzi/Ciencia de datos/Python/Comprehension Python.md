
## List comprehension en Python

Las list comprehensions en Python son una forma concisa y poderosa de crear listas a partir de iterables (como listas, cadenas o tuplas) o generando elementos nuevos. Ofrecen una alternativa más compacta y legible a los bucles `for` tradicionales a la hora de crear listas.

**Sintaxis básica:**

``` Python
nueva_lista = [expresion for elemento in iterable if condición]
```

#### Veamos los componentes de la sintaxis:

- **`expresion`:** Representa la operación o transformación que se aplica a cada elemento del iterable.
- **`elemento`:** Variable temporal que representa cada elemento del iterable durante la iteración.
- **`iterable`:** Puede ser una lista, cadena, tupla u otro objeto iterable del cual se obtienen los elementos.
- **`condición` (opcional):** Es una expresión booleana que se evalúa para cada elemento. Solo los elementos para los que la condición sea verdadera se incluyen en la nueva lista.

**Ejemplo:**

Crear una lista que duplique el valor de cada elemento en una lista original:


``` Python
lista_original = [1, 2, 3, 4]
lista_duplicada = [elemento * 2 for elemento in lista_original]

print(lista_original)  # [1, 2, 3, 4]
print(lista_duplicada)  # [2, 4, 6, 8]
```

- Ejemplo con condicion
```Python

# Sin comprehension
squares = []
for i in range(1, 10 + 1):
    if i % 2 == 0:
				squares.append(i**2)
print(squares)

# Con comprehension
squares_2 = [i**2 for i in range(1, 10+1) if i % 2 == 0]
print(squares_2)
```

#### Ventajas de las list comprehensions:

- **Concisión:** Permiten crear listas en una sola línea de código, mejorando la legibilidad del programa.
- **Flexibilidad:** Se pueden aplicar expresiones complejas y condiciones para filtrar y transformar elementos.
- **Rendimiento:** En general, las list comprehensions pueden ser más eficientes que los bucles `for` tradicionales para crear listas.

#### Ejemplos adicionales:

- **Filtrar elementos:** Crear una lista con solo los números pares de una lista original:

``` Python
lista_numeros = [1, 2, 3, 4, 5, 6]
numeros_pares = [numero for numero in lista_numeros if numero % 2 == 0]

print(numeros_pares)  # [2, 4, 6]
```

- **Crear elementos nuevos:** Crear una lista con las iniciales en mayúsculas de los nombres en una lista:

``` Python
nombres = ["juan", "maria", "pedro"]
iniciales_mayusculas = [nombre.upper()[0] for nombre in nombres]

print(iniciales_mayusculas)  # ["J", "M", "P"]
```

