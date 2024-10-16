

## **2. Dataset y Preprocesamiento**

El dataset y su preprocesamiento son fundamentales para comprender cómo el sistema de calibración dinámica del sensor de presión utiliza las **redes RBF** para mejorar la precisión de las lecturas del sensor. En este proyecto, se emplean los datos de diferentes dispositivos de prueba (DUTs, por sus siglas en inglés: **Device Under Test**), y el preprocesamiento se centra en preparar estos datos para el **entrenamiento y evaluación** del modelo de red RBF. 

#### **2.1 Dataset: Estructura de los Datos**

Los datos se encuentran almacenados en un archivo `.pickle`, que es una forma serializada en Python para guardar objetos, como dataframes de pandas. El dataset que estás utilizando proviene de lecturas de presión y temperatura de un sensor de presión, junto con los **errores** asociados a estas lecturas. A continuación, veamos la estructura de estos datos.

##### **2.1.1 Dataset `normal_usage.pickle`**

Este archivo contiene datos sobre las lecturas de presión y temperatura para diferentes DUTs (dispositivos de prueba), así como los errores de medición asociados a cada DUT. Al cargar el dataset utilizando `pandas`, se crea un dataframe que tiene varias columnas correspondientes a diferentes dispositivos.

```python
df = pd.read_pickle("../data/LPS22HH/normal_usage.pickle")
df.describe()
```

El dataset contiene, entre otros:

- **dutX_press**: Lectura de presión para el dispositivo DUT X.
- **dutX_temp**: Lectura de temperatura para el dispositivo DUT X.
- **dutX_error**: Error de predicción para el dispositivo DUT X.

Por ejemplo:
- `dut1_press`, `dut1_temp`, `dut1_error` para el dispositivo DUT 1.
- `dut23_press`, `dut23_temp`, `dut23_error` para el dispositivo DUT 23, que es utilizado principalmente para pruebas (testing).

##### **2.1.2 Organización de los Datos**
Los dispositivos DUTs que se están utilizando en los experimentos son: **1, 4, 9, 12, 18, y 23**. El dataset se organiza de manera que puedas seleccionar los datos de presión y temperatura de varios dispositivos para usarlos como **entrenamiento**, y los de un dispositivo específico para **pruebas**.

Por ejemplo, los datos de **entrenamiento** se construyen concatenando las lecturas de varios dispositivos, mientras que los datos de **prueba** se concentran en un solo dispositivo:

```python
x_train = np.concatenate(
    [
        np.column_stack((df["dut1_press"], df["dut1_temp"])),
        np.column_stack((df["dut4_press"], df["dut4_temp"])),
        np.column_stack((df["dut9_press"], df["dut9_temp"])),
        np.column_stack((df["dut12_press"], df["dut12_temp"])),
        np.column_stack((df["dut18_press"], df["dut18_temp"])),
    ]
)
x_test = np.column_stack((df["dut23_press"], df["dut23_temp"]))
```

Aquí:
- **x_train**: Se crean las entradas de entrenamiento combinando las columnas de presión y temperatura de los dispositivos DUT 1, 4, 9, 12 y 18.
- **x_test**: Se toman los datos del DUT 23 (presión y temperatura) para pruebas.

##### **2.1.3 Objetivo de la Predicción**
El **objetivo** del sistema es predecir el **error de presión** basado en las lecturas del sensor. El sistema utiliza los datos de presión y temperatura como **entrada** para la red RBF, y la salida esperada es el **error de predicción**.

La salida de entrenamiento (los errores) se prepara de manera similar a las entradas:

```python
yhat_train = np.concatenate(
    [
        df["dut1_error"],
        df["dut4_error"],
        df["dut9_error"],
        df["dut12_error"],
        df["dut18_error"],
    ]
)
yhat_test = df["dut23_error"].to_numpy()
```

- **yhat_train**: Los errores de los DUTs 1, 4, 9, 12 y 18 se concatenan para crear el vector de salida de entrenamiento.
- **yhat_test**: Los errores del DUT 23 se usan para evaluar la precisión de las predicciones.

---

#### **2.2 Preprocesamiento de los Datos**

El preprocesamiento es clave para convertir las lecturas de presión y temperatura en un formato adecuado para entrenar la red RBF y hacer predicciones precisas. A continuación, exploramos los pasos de preprocesamiento que son importantes para este proyecto.

##### **2.2.1 Conversión de los Datos en Numpy Arrays**

El proyecto utiliza **Numpy** para manejar las matrices de datos. Las lecturas de presión y temperatura se convierten en arreglos de numpy usando el método `np.column_stack`, que permite combinar dos columnas (presión y temperatura) en un solo arreglo bidimensional que puede ser pasado al modelo de red RBF:

```python
x_train = np.concatenate(
    [
        np.column_stack((df["dut1_press"], df["dut1_temp"])),
        np.column_stack((df["dut4_press"], df["dut4_temp"])),
        np.column_stack((df["dut9_press"], df["dut9_temp"])),
        np.column_stack((df["dut12_press"], df["dut12_temp"])),
        np.column_stack((df["dut18_press"], df["dut18_temp"])),
    ]
)
```

El **resultado final** de `x_train` es una matriz donde cada fila contiene una muestra, y cada columna representa una característica (presión o temperatura) correspondiente a una medición del sensor.

##### **2.2.2 Normalización de los Datos (opcional)**

En muchos proyectos de redes neuronales, la **normalización** de los datos es un paso crítico para garantizar que las entradas se mantengan dentro de un rango consistente (generalmente entre 0 y 1, o -1 y 1). Sin embargo, no se observa un paso explícito de normalización en el código que proporcionaste. Sería útil comprobar si el modelo RBF puede beneficiarse de este proceso o si ya se tiene en cuenta implícitamente en las funciones gaussianas de los nodos.

##### **2.2.3 Uso de `pickle` para Guardar y Cargar Datos**

Este proyecto utiliza `pickle` para serializar y deserializar objetos de Python. Esto es especialmente útil para guardar los modelos entrenados o los datasets preprocesados para su uso posterior, sin tener que repetir el preprocesamiento.

Por ejemplo:

- **Guardar modelos**:
  ```python
  with open(f"lps22hh_normal_dut{dut}out.pickle", "wb") as f:
      pickle.dump(net, f)
  ```

- **Cargar modelos**:
  ```python
  with open(f"lps22hh_normal_dut{dut}out.pickle", "rb") as f:
      net: Network = pickle.load(f)
  ```

Esto es útil para guardar redes RBF entrenadas en un DUT y reutilizarlas para hacer predicciones o continuar con el entrenamiento sin necesidad de inicializar la red desde cero.

---

#### **2.3 División de Datos para Entrenamiento y Pruebas**

Es esencial que el modelo sea evaluado con **datos nuevos** que no se hayan utilizado durante el entrenamiento para verificar su capacidad de **generalización**. En este proyecto, el DUT 23 se reserva para las pruebas, mientras que los DUTs 1, 4, 9, 12, y 18 se utilizan para el entrenamiento.

```python
x_test = np.column_stack((df["dut23_press"], df["dut23_temp"]))
yhat_test = df["dut23_error"].to_numpy()
```

Esto sigue un enfoque tradicional de **división de datos**, donde:
- **Entrenamiento**: Se utiliza un conjunto de DUTs para entrenar el modelo, ajustando los nodos y los pesos de la red RBF.
- **Pruebas**: Se utiliza un DUT diferente (DUT 23) para probar la precisión de las predicciones del modelo en datos no vistos anteriormente.

---

#### **2.4 Evaluación del Dataset: Visualización y Métricas**

El proyecto también incluye funciones para evaluar la **calidad de los datos** y las **predicciones**. Una vez que los datos han sido preprocesados y el modelo ha sido entrenado o probado, se utiliza `matplotlib` para visualizar los errores de predicción y el comportamiento de la red RBF.

- **Errores de predicción**: Se trazan los valores reales frente a las predicciones para observar la precisión de la red RBF.
  
  ```python
  plot_error_prediction(yhat_test, y_test, "Error Prediction - DUT 23")
  ```

- **Evolución de la red**: Se visualizan las distancias y errores a lo largo del tiempo, así como la cantidad de nodos en la red para analizar cómo la red ajusta su estructura.

  ```python
  plot_distance_and_error(stats)
  plot_neurons(stats)
  ```

---

### **Resumen Final**

Para entender a fondo el **preprocesamiento de datos** en este proyecto, debes:

1. **Cargar y entender la estructura del dataset** (presión, temperatura y error de varios DUTs).
2. **Organizar los datos de entrenamiento y prueba**, seleccionando DUTs específicos para cada tarea.
3. Analizar el **preprocesamiento**

 (cómo se convierten los datos en numpy arrays) y el uso de `pickle` para guardar y reutilizar modelos o datasets.
4. **Evaluar los datos** utilizando las métricas implementadas (`MAE`, `RMSE`, `SMAPE`) y visualizaciones de errores y la evolución de la red.

Si puedes comprender cómo el proyecto estructura, procesa y organiza los datos, estarás bien preparado para entender cómo la red RBF se entrena y ajusta en tiempo real para mejorar la precisión de las lecturas del sensor.

## **3. Red RBF y Aprendizaje en Línea**

El **núcleo del proyecto** de calibración dinámica del sensor de presión se basa en una implementación de una **red de funciones de base radial (RBF)**. Esta red es responsable de ajustar dinámicamente las predicciones de error del sensor a través del **aprendizaje en línea**. En esta sección, profundizaremos en el **código fuente** que implementa la red RBF y cómo esta realiza tanto **inferencia** como **aprendizaje en línea**.

### **3.1 Estructura de la Red RBF**

La red RBF se construye con una **capa oculta** de nodos RBF, donde cada nodo aplica una **función de base radial** (como la función Gaussiana) para calcular su activación en función de la distancia entre la entrada y el **centro** del nodo. Luego, las activaciones de estos nodos se combinan con un conjunto de **pesos** para generar la **salida final**.

##### **3.1.1 Clase `GaussianRBFNode`**

El nodo RBF es el componente fundamental de la red. La clase `GaussianRBFNode` representa un **nodo** de la capa oculta que utiliza una función de activación Gaussiana.

```python
class GaussianRBFNode:
    def __init__(self, center: np.ndarray, radius: float) -> None:
        self.center = center   # Centro del nodo
        self.radius = radius   # Radio del nodo
```

- **Centro del nodo (`center`)**: Define la posición en el espacio de entrada donde la función radial tiene su pico.
- **Radio (`radius`)**: Controla la "amplitud" de la función Gaussiana; es decir, cuánto se extiende la influencia del nodo.

La función de activación Gaussiana está definida de esta manera:

```python
def forward(self, x: np.ndarray) -> float:
    return np.exp(-np.linalg.norm(x - self.center) ** 2 / (2 * self.radius**2))
```

- La **distancia Euclidiana** entre la entrada \( x \) y el centro del nodo \( c \) se utiliza para calcular la activación. Cuanto más cerca esté la entrada del centro del nodo, mayor será la activación.


##### **3.1.2 Clase `Network`: Definición de la Red RBF**

La clase `Network` representa la red completa y maneja tanto la **inferencia** como el **aprendizaje en línea**. Esta red tiene una **capa de nodos RBF** y una **capa de salida** donde las activaciones de los nodos se combinan con pesos para producir una predicción.

```python
class Network:
    _input_size: int
    _output_size: int
    _hidden_nodes: List[GaussianRBFNode]
    _bias_weights: np.ndarray
    _weights: np.ndarray
    # otros parámetros...
```

- **_input_size**: El tamaño de la entrada (número de características, en este caso, 2: presión y temperatura).
- **_output_size**: El tamaño de la salida (generalmente 1, porque el objetivo es predecir el error del sensor).
- **_hidden_nodes**: Lista de nodos RBF en la capa oculta.
- **_weights**: Matriz de pesos entre la capa oculta y la capa de salida.
- **_bias_weights**: Peso del nodo de bias en la capa de salida.

La red tiene varios parámetros ajustables que afectan su comportamiento, como:
- **learning_rate** (tasa de aprendizaje),
- **error_threshold** (tolerancia de error),
- **overlap_factor** (factor de solapamiento para los radios de los nodos),
- **activation_threshold** (umbral de activación para la poda de nodos).

---

#### **3.2 Inferencia en la Red RBF**

La **inferencia** es el proceso mediante el cual la red RBF toma una entrada y calcula la salida correspondiente (es decir, la predicción del error del sensor). 

##### **3.2.1 Proceso de Inferencia**

El método `inference()` de la clase `Network` calcula la salida de la red para una entrada dada \( x \).

```python
def inference(self, x: np.ndarray) -> np.ndarray:
    self._update_mean_std(x)
    activations = [node(x) for node in self._hidden_nodes]  # Activaciones de cada nodo
    return self._bias_weights + np.dot(self._weights, activations)  # Suma ponderada
```

1. **Activaciones de los nodos RBF**:
   - Cada nodo en la capa oculta calcula su activación utilizando su **centro** y **radio**.
   - La activación está determinada por la proximidad de la entrada al centro del nodo, con valores más altos para entradas cercanas.

2. **Salida final**:
   - Las activaciones de los nodos se multiplican por los **pesos** correspondientes.
   - Se suma el **bias** a la salida para producir la predicción final.

##### **3.2.2 Actualización de la Media y Desviación Estándar de la Distancia**

El método `inference()` también llama a `_update_mean_std()`, que actualiza la media y la desviación estándar de la distancia a los nodos. Esto es importante porque el algoritmo de aprendizaje en línea usa esta información para ajustar la red (agregando o eliminando nodos).

```python
def _update_mean_std(self, x: np.ndarray) -> None:
    if self._avg_w is not None and len(self._hidden_nodes) > 0:
        self._d = np.min([np.linalg.norm(x - n.center) for n in self._hidden_nodes])
        self._d_mean -= self._d_mean / self._avg_w
        self._d_mean += self._d / self._avg_w
        self._d_std -= self._d_std / self._avg_w
        self._d_std += (self._d - self._d_mean) ** 2 / self._avg_w
```

- **_d**: Es la distancia mínima entre la entrada \( x \) y el centro de los nodos RBF.
- Esta distancia se utiliza para ajustar el **umbral de distancia** (_d_th_), que influye en cuándo se agregan nuevos nodos a la red.

---

#### **3.3 Aprendizaje en Línea**

El **aprendizaje en línea** es el mecanismo que permite que la red RBF ajuste su estructura y pesos dinámicamente en función de las entradas y los errores observados. Esto es clave para la calibración del sensor, ya que los datos se reciben de forma continua y la red debe adaptarse sin necesidad de entrenamientos prolongados fuera del dispositivo.

##### **3.3.1 Proceso de Aprendizaje**

El método `learning()` realiza el ajuste de la red en respuesta a una nueva entrada \( x \) y su error asociado \( y \).

```python
def learning(self, x: np.ndarray, y: np.ndarray) -> np.ndarray:
    activations = [node(x) for node in self._hidden_nodes]
    y_pred = self._bias_weights + np.dot(self._weights, activations)  # Predicción
    self._e = y - y_pred  # Error de predicción
```

1. **Inferencia inicial**:
   - Se realiza una predicción usando las activaciones de los nodos RBF, al igual que en la inferencia.
   
2. **Cálculo del error**:
   - El error se calcula restando la predicción de la red \( y_{\text{pred}} \) del valor objetivo \( y \).

##### **3.3.2 Actualización de los Nodos**

Dependiendo del error observado y la distancia a los nodos existentes, la red puede agregar nuevos nodos o ajustar los existentes.

- **Agregar nodos nuevos**:
   - Si el error es mayor que un umbral (\( e > e_{\text{th}} \)) y la distancia a los nodos más cercanos es mayor que un umbral (\( d > d_{\text{th}} \)), se **agrega un nuevo nodo**.
   
```python
if np.linalg.norm(self._e) > self._e_th and self._d > self._d_th:
    self._hidden_nodes.append(GaussianRBFNode(center=x, radius=self._overlap * self._d))
    self._weights = np.append(self._weights, self._e.reshape((self._output_size, 1)), axis=1)
```

- **Actualización de los pesos y centros de los nodos**:
   - Si no se agrega un nuevo nodo, la red ajusta los **centros** de los nodos y los **pesos** de la capa de salida usando **gradiente descendente**.

```python
self._bias_weights += self._lr * self._e
for i, n in enumerate(self._hidden_nodes):
    old_weights = self._weights[:, i].copy()
    old_center = n.center.copy()

    self._hidden_nodes[i].center += (
        self._lr * (2 / n.radius**2) * activations[i] * old_weights.dot(self._e) * (x - old_center)
    )
    self._weights[:, i] += self._lr * self._e * activations[i]
```

- El ajuste de los centros y pesos se realiza de manera que los nodos se **desplacen** hacia

 las entradas con mayores errores, y los pesos se ajusten para mejorar las predicciones futuras.

##### **3.3.3 Poda de Nodos**

La red también incluye una estrategia de **poda**, eliminando nodos que tienen una activación baja durante un número consecutivo de iteraciones.

```python
if act_norm[i] < self._act_th:
    n.low_activation_count += 1
else:
    n.low_activation_count = 0

if n.low_activation_count > self._pr_w:
    self._hidden_nodes.pop(i)
    self._weights = np.delete(self._weights, i, axis=1)
```

- Si un nodo tiene una activación por debajo de un umbral durante varias iteraciones consecutivas, se considera que el nodo ya no es útil y se elimina.

---

#### **3.4 Inicialización con K-Means**

Para iniciar la red con un conjunto de nodos razonables, se utiliza **K-Means** para determinar los centros iniciales de los nodos a partir de los datos de entrenamiento.

```python
def init_with_kmeans(self, x: np.ndarray, y: np.ndarray, n_nodes: int) -> None:
    kmeans = KMeans(n_clusters=n_nodes, random_state=42, n_init="auto").fit(x)
    centers = kmeans.cluster_centers_
```

- Los **centros** de los nodos se eligen como los centros de los clusters obtenidos mediante K-Means.
- Los **radios** de los nodos se calculan como la distancia mínima entre centros.

---

#### **3.5 Resumen Final: Red RBF y Aprendizaje en Línea**

El **aprendizaje en línea** de esta red RBF permite que el sistema de calibración del sensor de presión ajuste dinámicamente su comportamiento a medida que se recopilan nuevas lecturas. Los pasos clave del proceso son:

1. **Inferencia**: La entrada se pasa por los nodos RBF, y las activaciones se combinan con los pesos para producir una salida.
2. **Aprendizaje en línea**: La red ajusta sus nodos y pesos basándose en el error observado, agregando nuevos nodos si es necesario y ajustando los centros y los pesos existentes.
3. **Poda**: Los nodos que no son activados lo suficiente se eliminan para mantener la red eficiente.

Este enfoque permite que el sistema realice **ajustes dinámicos y continuos** sin requerir entrenamientos fuera de línea extensos, lo que es clave para aplicaciones de sensores embebidos y calibración en tiempo real.