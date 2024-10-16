![[Captura de pantalla 2024-10-01 a las 5.21.21 p. m..png]]
### Importación de Bibliotecas
```python
from sklearn.datasets import make_gaussian_quantiles
import matplotlib.pyplot as plt
import numpy as np
```
Estas son las bibliotecas necesarias para el proyecto:
- `make_gaussian_quantiles` para generar datos de ejemplo.
- `matplotlib.pyplot` para visualización.
- `numpy` para operaciones numéricas.

### Creación del Dataset
```python
N = 1000
gaussian_quantiles = make_gaussian_quantiles(mean=None,
                                             cov=0.1,
                                             n_samples=N,
                                             n_features=2,
                                             n_classes=2,
                                             shuffle=True,
                                             random_state=None)
X, Y = gaussian_quantiles
Y = Y[:,np.newaxis]
plt.scatter(X[:,0], X[:,1], c=Y[:,0], s=40, cmap=plt.cm.Spectral);
```
- `N = 1000`: Se define el número de muestras.
- `make_gaussian_quantiles()`: Genera `N` puntos distribuidos según una distribución Gaussiana con dos clases (`n_classes=2`) y dos características (`n_features=2`).
- `X, Y = gaussian_quantiles`: Se extraen los datos (`X`) y las etiquetas (`Y`).
- `Y = Y[:, np.newaxis]`: Convierte `Y` a una matriz de dos dimensiones agregando un eje adicional.
- `plt.scatter()`: Visualiza los datos generados con un diagrama de dispersión, coloreando cada punto según su clase (`c=Y[:,0]`).

### Inicialización de Parámetros de la Red
```python
def initialize_parameters_deep(layer_dims):
    parameters = {}
    L = len(layer_dims)
    for l in range(0, L-1):
        parameters['W' + str(l+1)] = (np.random.rand(layer_dims[l], layer_dims[l+1]) * 2) - 1
        parameters['b' + str(l+1)] = (np.random.rand(1, layer_dims[l+1]) * 2) - 1
    return parameters
```
- `initialize_parameters_deep()`: Inicializa los pesos y sesgos para cada capa de la red neuronal.
- `layer_dims`: Es una lista con el número de neuronas en cada capa.
- `parameters`: Diccionario para almacenar `W` (pesos) y `b` (sesgos) para cada capa.
- `np.random.rand()` genera valores aleatorios entre 0 y 1, que luego se ajustan al rango `[-1, 1]`.

### Funciones de Activación
```python
def sigmoid(x, derivate = False):
    if derivate:
        return np.exp(-x)/(( np.exp(-x) +1)**2)
    else:
        return 1 / (1 + np.exp(-x))

def relu(x, derivate = False):
    if derivate:
        x[x<=0] = 0
        x[x>0] = 1
        return x
    else:
        return np.maximum(0, x)
```
- `sigmoid()`: Calcula la función sigmoide o su derivada.
- `relu()`: Calcula la función `ReLU` o su derivada. ReLU devuelve 0 para valores negativos y mantiene los valores positivos.

### Función de Pérdida
```python
def mse(y, y_hat, derivate=False):
    if derivate:
        return (y_hat - y)
    else:
        return np.mean((y_hat - y)**2)
```
- `mse()`: Calcula el "Error Cuadrático Medio" (`Mean Squared Error`). Puede calcular la pérdida (`derivate=False`) o su derivada (`derivate=True`), útil para la retropropagación.

### Operaciones de Matrices
```python
a = np.array([[2,3], [2,3], [2,3]])
b = np.array([[1,6,5,2], [1,2,7,0]])
np.matmul(a, b)
a @ b
```
- Definen matrices `a` y `b`, y luego muestran cómo multiplicarlas usando `np.matmul()` o `@` que son equivalentes para la multiplicación de matrices.

### Función de Entrenamiento
```python
def train(X_data, lr, params, training=True):
    ## Forward
    params['A0'] = X_data

    params['Z1'] = np.matmul(params['A0'], params['W1']) + params['b1']
    params['A1'] = relu(params['Z1'])

    params['Z2'] = np.matmul(params['A1'], params['W2']) + params['b2']
    params['A2'] = relu(params['Z2'])

    params['Z3'] = np.matmul(params['A2'], params['W3']) + params['b3']
    params['A3'] = sigmoid(params['Z3'])

    output = params['A3']

    if training:
        # Backpropagation
        params['dZ3'] = mse(Y, output, True) * sigmoid(params['A3'], True)
        params['dW3'] = np.matmul(params['A2'].T, params['dZ3'])

        params['dZ2'] = np.matmul(params['dZ3'], params['W3'].T) * relu(params['A2'], True)
        params['dW2'] = np.matmul(params['A1'].T, params['dZ2'])

        params['dZ1'] = np.matmul(params['dZ2'], params['W2'].T) * relu(params['A1'], True)
        params['dW1'] = np.matmul(params['A0'].T, params['dZ1'])

        ## Gradinet Descent:
        params['W3'] = params['W3'] - params['dW3'] * lr
        params['b3'] = params['b3'] - (np.mean(params['dZ3'], axis=0, keepdims=True)) * lr

        params['W2'] = params['W2'] - params['dW2'] * lr
        params['b2'] = params['b2'] - (np.mean(params['dZ2'], axis=0, keepdims=True)) * lr

        params['W1'] = params['W1'] - params['dW1'] * lr
        params['b1'] = params['b1'] - (np.mean(params['dZ1'], axis=0, keepdims=True)) * lr

    return output
```
- `train()`: Realiza la propagación hacia adelante y hacia atrás para ajustar los parámetros de la red.
- **Forward**:
  - Calcula `Z` y `A` para cada capa (`Z` es la entrada de una capa y `A` es la salida después de la activación).
- **Backpropagation**:
  - Calcula los gradientes de los errores (`dZ`) para cada capa y ajusta los pesos (`W`) y sesgos (`b`) usando el gradiente descendente.

### Entrenando la Red
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
- Define la estructura de la red (`layer_dims`) con capas de tamaño `2`, `4`, `8` y `1`.
- Entrena la red durante `50000` iteraciones.
- Imprime el error cada `25` iteraciones y lo agrega a la lista `errors` para luego graficarlo.

### Probando Datos Nuevos
```python
data_test = (np.random.rand(1000, 2) * 2) - 1
y = train(data_test, 0.001, params, training=False)
y = np.where(y >= 0.5, 1, 0)
plt.scatter(data_test[:, 0], data_test[:, 1], c=y[:, 0], s=40, cmap=plt.cm.Spectral);
```
- Genera nuevos datos de prueba (`data_test`) y usa la red entrenada para predecir los valores.
- Los valores predichos (`y`) se binarizan según un umbral de `0.5`.
- Finalmente, se visualizan los resultados con `plt.scatter()`.

### Malla de Visualización
```python
_x0 = np.linspace(-1, 1, 50)
_x1 = np.linspace(-1, 1, 50)
_y = np.zeros((50, 50))

for i0, x0 in enumerate(_x0):
    for i1, x1 in enumerate(_x1):
        _y[i0, i1] = train(np.array([[x0, x1]]), 0.0001, params, training=False)

plt.pcolormesh(_x0, _x1, _y, cmap='coolwarm')
```
- `np.linspace()`: Genera puntos uniformemente espaciados entre `-1` y `1` para crear una malla de datos.
- Realiza una predicción para cada combinación de `x0` y `x1` en la malla, visualizando los resultados con un mapa de colores (`plt.pcolormesh`).

