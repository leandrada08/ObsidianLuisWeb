
### Importación de Bibliotecas
```python
from sklearn.datasets import make_gaussian_quantiles
import matplotlib.pyplot as plt
import numpy as np
```
- `sklearn.datasets.make_gaussian_quantiles`: Se utiliza para generar datos de prueba distribuidos de manera gaussiana.
- `matplotlib.pyplot`: Herramienta para crear gráficos y visualizar datos.
- `numpy`: Biblioteca fundamental para cálculos numéricos y operaciones matriciales.

### Creación de un Conjunto de Datos
```python
N = 1000
gaussian_quantiles = make_gaussian_quantiles(mean=None, cov=0.1, n_samples=N, n_features=2, n_classes=2, shuffle=True, random_state=None)
X, Y = gaussian_quantiles
Y = Y[:, np.newaxis]
plt.scatter(X[:, 0], X[:, 1], c=Y[:, 0], s=40, cmap=plt.cm.Spectral)
```
- **N = 1000**: Define el número de muestras a generar.
- `make_gaussian_quantiles()`: Genera `N` muestras con dos características (`n_features=2`) y dos clases (`n_classes=2`).
- `X, Y = gaussian_quantiles`: Separamos los datos (`X`) y las etiquetas (`Y`).
- `Y[:, np.newaxis]`: Expande la dimensión de `Y` para adaptarse a la red neuronal.
- `plt.scatter()`: Crea un diagrama de dispersión para visualizar los datos generados.

### Inicialización de Parámetros
```python
def initialize_parameters_deep(layer_dims):
    parameters = {}
    L = len(layer_dims)
    for l in range(0, L - 1):
        parameters['W' + str(l + 1)] = (np.random.rand(layer_dims[l], layer_dims[l + 1]) * 2) - 1
        parameters['b' + str(l + 1)] = (np.random.rand(1, layer_dims[l + 1]) * 2) - 1
    return parameters
```
- `initialize_parameters_deep()`: Inicializa los pesos (`W`) y sesgos (`b`) para la red neuronal.
- `layer_dims`: Lista que contiene el número de neuronas en cada capa.
- `parameters`: Diccionario que contiene los pesos y sesgos.

### Funciones de Activación
```python
def sigmoid(x, derivate=False):
    if derivate:
        return np.exp(-x) / ((np.exp(-x) + 1) ** 2)
    else:
        return 1 / (1 + np.exp(-x))

def relu(x, derivate=False):
    if derivate:
        x[x <= 0] = 0
        x[x > 0] = 1
        return x
    else:
        return np.maximum(0, x)
```
- `sigmoid()`: Implementa la función sigmoide y su derivada. Se usa como activación para clasificaciones.
- `relu()`: Implementa la función `ReLU` (Rectified Linear Unit) y su derivada. Se usa para capas ocultas.

### Función de Pérdida: Error Cuadrático Medio
```python
def mse(y, y_hat, derivate=False):
    if derivate:
        return y_hat - y
    else:
        return np.mean((y_hat - y) ** 2)
```
- **`mse()`**: Calcula la pérdida usando el Error Cuadrático Medio, útil para retropropagación.

### Entrenamiento de la Red Neuronal
```python
def train(X_data, lr, params, training=True):
    # Propagación hacia adelante
    params['A0'] = X_data
    params['Z1'] = np.matmul(params['A0'], params['W1']) + params['b1']
    params['A1'] = relu(params['Z1'])
    params['Z2'] = np.matmul(params['A1'], params['W2']) + params['b2']
    params['A2'] = relu(params['Z2'])
    params['Z3'] = np.matmul(params['A2'], params['W3']) + params['b3']
    params['A3'] = sigmoid(params['Z3'])
    output = params['A3']

    if training:
        # Retropropagación
        params['dZ3'] = mse(Y, output, True) * sigmoid(params['A3'], True)
        params['dW3'] = np.matmul(params['A2'].T, params['dZ3'])
        params['dZ2'] = np.matmul(params['dZ3'], params['W3'].T) * relu(params['A2'], True)
        params['dW2'] = np.matmul(params['A1'].T, params['dZ2'])
        params['dZ1'] = np.matmul(params['dZ2'], params['W2'].T) * relu(params['A1'], True)
        params['dW1'] = np.matmul(params['A0'].T, params['dZ1'])
        
        # Actualización de los parámetros mediante gradiente descendente
        params['W3'] -= params['dW3'] * lr
        params['b3'] -= (np.mean(params['dZ3'], axis=0, keepdims=True)) * lr
        params['W2'] -= params['dW2'] * lr
        params['b2'] -= (np.mean(params['dZ2'], axis=0, keepdims=True)) * lr
        params['W1'] -= params['dW1'] * lr
        params['b1'] -= (np.mean(params['dZ1'], axis=0, keepdims=True)) * lr

    return output
```
- La función `train()` realiza la propagación hacia adelante y la retropropagación.
- **Propagación hacia adelante**: Calcula `Z` y `A` (salida de la capa).
- **Retropropagación**: Calcula los gradientes y actualiza los parámetros con gradiente descendente.

### Entrenamiento de la Red y Visualización de Errores
```python
layer_dims = [2, 4, 8, 1]
params = initialize_parameters_deep(layer_dims)
errors = []
for _ in range(50000):
    output = train(X, 0.001, params)
    if _ % 25 == 0:
        print(mse(Y, output))
        errors.append(mse(Y, output))
plt.plot(errors)
```
- **`layer_dims`**: Define las dimensiones de las capas (entrada, ocultas y salida).
- Se realiza el entrenamiento durante `50000` iteraciones, imprimiendo el error cada `25` iteraciones.

### Evaluación del Modelo
```python
data_test = (np.random.rand(1000, 2) * 2) - 1
y = train(data_test, 0.001, params, training=False)
y = np.where(y >= 0.5, 1, 0)
plt.scatter(data_test[:, 0], data_test[:, 1], c=y[:, 0], s=40, cmap=plt.cm.Spectral)
```
- Se generan nuevos datos de prueba y se predicen las etiquetas con el modelo entrenado.
- Se grafican los resultados utilizando `plt.scatter()`.

### Visualización de la Malla de Resultados
```python
_x0 = np.linspace(-1, 1, 50)
_x1 = np.linspace(-1, 1, 50)
_y = np.zeros((50, 50))

for i0, x0 in enumerate(_x0):
    for i1, x1 in enumerate(_x1):
        _y[i0, i1] = train(np.array([[x0, x1]]), 0.0001, params, training=False)

plt.pcolormesh(_x0, _x1, _y, cmap='coolwarm')
```
- Se crea una malla de puntos para visualizar la clasificación sobre toda el área.
- `np.linspace()` genera puntos uniformemente espaciados entre `-1` y `1`.
- `plt.pcolormesh()` visualiza el resultado de clasificación en la malla de datos.

# Clasificacion binaria con overfitting

### 1. **Importación de Bibliotecas**
El cuaderno empieza con la importación de las bibliotecas necesarias:

```python
from sklearn.datasets import make_gaussian_quantiles
import matplotlib.pyplot as plt
import numpy as np
```
- **`sklearn.datasets.make_gaussian_quantiles`**: Utilizado para generar un conjunto de datos de ejemplo distribuidos de forma gaussiana.
- **`matplotlib.pyplot`**: Para visualización de gráficos.
- **`numpy`**: Biblioteca para manejo de matrices y operaciones matemáticas.

### 2. **Generación de Datos**
```python
N = 1000
gaussian_quantiles = make_gaussian_quantiles(mean=None, cov=0.1, n_samples=N, n_features=2, n_classes=2, shuffle=True, random_state=None)
X, Y = gaussian_quantiles
Y = Y[:, np.newaxis]
plt.scatter(X[:, 0], X[:, 1], c=Y[:, 0], s=40, cmap=plt.cm.Spectral)
```
- **`N = 1000`**: Se genera un conjunto de datos con 1000 puntos.
- **`make_gaussian_quantiles()`**: Crea un conjunto de datos distribuidos de forma gaussiana, con dos características y dos clases.
- **Visualización**: Se realiza un gráfico de dispersión con `plt.scatter()`, para visualizar la distribución de las dos clases.

### 3. **Inicialización de Parámetros para la Red Neuronal**
El siguiente bloque de código se enfoca en la inicialización de parámetros:

```python
def initialize_parameters_deep(layer_dims):
    parameters = {}
    L = len(layer_dims)
    for l in range(0, L - 1):
        parameters['W' + str(l + 1)] = (np.random.rand(layer_dims[l], layer_dims[l + 1]) * 2) - 1
        parameters['b' + str(l + 1)] = (np.random.rand(1, layer_dims[l + 1]) * 2) - 1
    return parameters
```
- **`initialize_parameters_deep()`**: Esta función inicializa los pesos (`W`) y sesgos (`b`) de la red neuronal de manera aleatoria.
- Los parámetros se almacenan en un diccionario llamado `parameters`, que tiene una clave específica para cada capa.

### 4. **Función de Activación**
```python
def sigmoid(x, derivate=False):
    if derivate:
        return np.exp(-x) / ((np.exp(-x) + 1) ** 2)
    else:
        return 1 / (1 + np.exp(-x))

def relu(x, derivate=False):
    if derivate:
        x[x <= 0] = 0
        x[x > 0] = 1
        return x
    else:
        return np.maximum(0, x)
```
- **`sigmoid()`**: Esta función calcula la función sigmoide o su derivada si `derivate=True`.
- **`relu()`**: Calcula la función `ReLU`, que devuelve 0 para los valores negativos y deja pasar los valores positivos. También puede devolver su derivada.

### 5. **Definición de la Función de Pérdida**
```python
def mse(y, y_hat, derivate=False):
    if derivate:
        return y_hat - y
    else:
        return np.mean((y_hat - y) ** 2)
```
- **`mse()`**: Calcula la "Error Cuadrático Medio" (Mean Squared Error, MSE) y su derivada. Esta función se usa durante el entrenamiento para medir qué tan bien o mal está funcionando la red neuronal.

### 6. **Entrenamiento del Modelo**
```python
def train(X_data, lr, params, training=True):
    params['A0'] = X_data
    params['Z1'] = np.matmul(params['A0'], params['W1']) + params['b1']
    params['A1'] = relu(params['Z1'])
    params['Z2'] = np.matmul(params['A1'], params['W2']) + params['b2']
    params['A2'] = relu(params['Z2'])
    params['Z3'] = np.matmul(params['A2'], params['W3']) + params['b3']
    params['A3'] = sigmoid(params['Z3'])
    output = params['A3']

    if training:
        # Retropropagación
        params['dZ3'] = mse(Y, output, True) * sigmoid(params['A3'], True)
        params['dW3'] = np.matmul(params['A2'].T, params['dZ3'])
        params['dZ2'] = np.matmul(params['dZ3'], params['W3'].T) * relu(params['A2'], True)
        params['dW2'] = np.matmul(params['A1'].T, params['dZ2'])
        params['dZ1'] = np.matmul(params['dZ2'], params['W2'].T) * relu(params['A1'], True)
        params['dW1'] = np.matmul(params['A0'].T, params['dZ1'])

        # Actualización de parámetros (gradiente descendente)
        params['W3'] -= params['dW3'] * lr
        params['b3'] -= (np.mean(params['dZ3'], axis=0, keepdims=True)) * lr
        params['W2'] -= params['dW2'] * lr
        params['b2'] -= (np.mean(params['dZ2'], axis=0, keepdims=True)) * lr
        params['W1'] -= params['dW1'] * lr
        params['b1'] -= (np.mean(params['dZ1'], axis=0, keepdims=True)) * lr

    return output
```
- **Propagación hacia adelante**: Se calculan los valores de `Z` y `A` para cada capa.
- **Retropropagación**: Se calculan los gradientes de los errores y se ajustan los parámetros para minimizar la pérdida.
- **Gradiente descendente**: Se actualizan los pesos (`W`) y sesgos (`b`) usando la tasa de aprendizaje (`lr`).

### 7. **Entrenamiento de la Red Completa**
```python
layer_dims = [2, 4, 8, 1]
params = initialize_parameters_deep(layer_dims)
errors = []
for _ in range(50000):
    output = train(X, 0.001, params)
    if _ % 25 == 0:
        print(mse(Y, output))
        errors.append(mse(Y, output))
plt.plot(errors)
```
- **`layer_dims`**: Define las dimensiones de las capas de la red neuronal, que en este caso tiene 4 capas con tamaños `2`, `4`, `8` y `1` respectivamente.
- **Entrenamiento en 50000 iteraciones**: El modelo se entrena durante 50000 iteraciones, registrando y graficando el error cada 25 iteraciones.

### 8. **Probando con Nuevos Datos**
```python
data_test = (np.random.rand(1000, 2) * 2) - 1
y = train(data_test, 0.001, params, training=False)
y = np.where(y >= 0.5, 1, 0)
plt.scatter(data_test[:, 0], data_test[:, 1], c=y[:, 0], s=40, cmap=plt.cm.Spectral)
```
- Se generan nuevos datos de prueba, se pasa por la red y se utiliza la salida (`output`) para clasificar.
- Luego se visualizan los datos predichos en un gráfico.

### 9. **Visualización de la Malla de Decisión**
```python
_x0 = np.linspace(-1, 1, 50)
_x1 = np.linspace(-1, 1, 50)
_y = np.zeros((50, 50))

for i0, x0 in enumerate(_x0):
    for i1, x1 in enumerate(_x1):
        _y[i0, i1] = train(np.array([[x0, x1]]), 0.0001, params, training=False)

plt.pcolormesh(_x0, _x1, _y, cmap='coolwarm')
```
- **`np.linspace()`**: Genera una malla de puntos para evaluar cómo la red neuronal clasifica los puntos en la región de entrada.
- **Visualización con `plt.pcolormesh()`**: Muestra una visualización del mapa de calor que representa la decisión de la red en cada punto de la malla.

