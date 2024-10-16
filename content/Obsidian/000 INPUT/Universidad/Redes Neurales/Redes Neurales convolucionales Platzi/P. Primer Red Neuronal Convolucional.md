
### Descripción Línea a Línea

#### Definición del Modelo
```python
model = tf.keras.Sequential()
```
- **`tf.keras.Sequential()`**: Se utiliza `Sequential` para definir una red neuronal secuencial, que es útil para apilar capas de manera lineal, es decir, cada capa tiene exactamente una entrada y una salida.

```python
model.add(Conv2D(filters=64, kernel_size=2, padding='same', activation='relu', input_shape=(28,28,1)))
```
- **`Conv2D(filters=64, kernel_size=2, padding='same', activation='relu', input_shape=(28,28,1))`**:
  - **`filters=64`**: Número de filtros (kernels) utilizados en esta capa de convolución. Cada filtro aprenderá características diferentes de la imagen.
  - **`kernel_size=2`**: Tamaño del kernel o ventana de filtro (2x2).
  - **`padding='same'`**: Mantiene el tamaño de la salida igual al de la entrada, añadiendo ceros en los bordes si es necesario.
  - **`activation='relu'`**: La función de activación ReLU (Rectified Linear Unit) se usa para añadir no linealidad al modelo.
  - **`input_shape=(28,28,1)`**: Especifica la forma de entrada de las imágenes, que en este caso es de 28x28 píxeles en escala de grises (1 canal).

```python
model.add(MaxPooling2D(pool_size=2))
```
- **`MaxPooling2D(pool_size=2)`**: Reduce el tamaño de la representación espacial (dimensiones de las características) al aplicar una operación de pooling con una ventana de 2x2. Esto reduce la cantidad de parámetros y el coste computacional, a la vez que resalta las características más prominentes.

```python
model.add(Dropout(0.3))
```
- **`Dropout(0.3)`**: Apaga aleatoriamente el 30% de las neuronas durante el entrenamiento, para reducir el sobreajuste y hacer que el modelo generalice mejor.

```python
model.add(Conv2D(filters=32, kernel_size=2, padding='same', activation='relu'))
```
- **`Conv2D(filters=32, kernel_size=2, padding='same', activation='relu')`**: Añade otra capa convolucional con 32 filtros y una ventana de 2x2. Al disminuir el número de filtros (de 64 a 32), el modelo aprende características menos complejas pero sigue añadiendo profundidad.

```python
model.add(MaxPooling2D(pool_size=2))
model.add(Dropout(0.3))
```
- Estas líneas realizan pooling y dropout similares a los anteriores, pero después de la segunda convolución.

```python
model.add(Flatten())
```
- **`Flatten()`**: Convierte el tensor multidimensional en un vector unidimensional, preparando la salida de las capas convolucionales para ser usada por las capas densas.

```python
model.add(Dense(256, activation='relu'))
```
- **`Dense(256, activation='relu')`**: Añade una capa densa totalmente conectada con 256 neuronas y la función de activación ReLU. Esta capa es capaz de aprender combinaciones complejas de las características detectadas por las capas anteriores.

```python
model.add(Dropout(0.5))
```
- **`Dropout(0.5)`**: Apaga aleatoriamente el 50% de las neuronas para evitar el sobreajuste.

```python
model.add(Dense(10, activation='softmax'))
```
- **`Dense(10, activation='softmax')`**: Añade la capa de salida con 10 neuronas y la función de activación Softmax. Esta capa se utiliza para la clasificación, ya que `softmax` convierte las salidas en probabilidades que suman 1, útil para problemas de clasificación de múltiples clases (en este caso, 10 clases).

```python
model.summary()
```
- **`model.summary()`**: Muestra un resumen del modelo, incluyendo las capas, los parámetros y las formas de las salidas. Es una forma útil de verificar la arquitectura antes de entrenar el modelo.

#### Compilación del Modelo
```python
model.compile(loss='categorical_crossentropy', optimizer='rmsprop', metrics=['accuracy'])
```
- **`loss='categorical_crossentropy'`**: La función de pérdida utilizada es la entropía cruzada categórica, comúnmente usada para problemas de clasificación multiclase.
- **`optimizer='rmsprop'`**: RMSprop es el optimizador utilizado para ajustar los pesos del modelo basándose en la función de pérdida.
- **`metrics=['accuracy']`**: Se utiliza la métrica de precisión para evaluar el rendimiento del modelo.

#### Entrenamiento del Modelo
```python
model.fit(train_images, train_labels, batch_size=64, epochs=10)
```
- **`model.fit()`**: Comienza el entrenamiento del modelo con los datos de entrenamiento.
  - **`train_images`** y **`train_labels`**: Datos de entrada y etiquetas para el entrenamiento.
  - **`batch_size=64`**: Tamaño de lote, es decir, cuántas muestras se procesan antes de actualizar los pesos.
  - **`epochs=10`**: Número de iteraciones sobre el conjunto de datos completo.

#### Evaluación del Modelo
```python
score = model.evaluate(test_images, test_labels, verbose=0)
```
- **`model.evaluate()`**: Evalúa el rendimiento del modelo con los datos de prueba.
  - **`test_images`** y **`test_labels`**: Datos de entrada y etiquetas para la evaluación.
  - **`verbose=0`**: No muestra información del proceso de evaluación.

### Callbacks
- **`EarlyStopping`** y **`ModelCheckpoint`** se utilizan para mejorar el proceso de entrenamiento:
  - **`EarlyStopping`**: Detiene el entrenamiento cuando la métrica deseada no mejora, lo cual evita un entrenamiento innecesario.
  - **`ModelCheckpoint`**: Guarda el modelo cada vez que se logra una mejor precisión.





- https://cs231n.github.io/convolutional-networks/
- https://cs231n.github.io/understanding-cnn/
- https://cs231n.github.io/transfer-learning/