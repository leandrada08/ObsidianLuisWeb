
Se puede dividir la creacion de esta red neuronal en 4 pasos:

- Cargar las librerías a utilizar.
``` python
import numpy as np
from keras import layers, models
from keras.utils import to_categorical 
from keras.datasets import mnist 
import matplotlib.pyplot as plt
from tensorflow.keras.utils import to_categorical
```

- Cargar los datos y separarlos en datos de entrenamiento y prueba.
``` python
(train_data, train_labels), (test_data, test_labels) = mnist.load_data()
```

- Cargar y configurar el modelo de la red neuronal.
``` python
model = models.Sequential()
model.add(layers.Imput(shape=(28*28,)))
model.add(layers.Dense(512, activation='relu')) 
model.add(layers.Dense(10,activation='softmax')) 
model.compile(optimizer='rmsprop',
			  loss='categorical crossentropy',
			  metrics = ['accuracy'])`
```

- Realizar una limpieza a los datos para un mejor procesamiento.
``` python
x_train = train_data.reshape((60000, 28*28))
x_train = x_train.astype('float32')/255

x_test = test_data.reshape((10000, 28*28))
x_test = x_test.astype('float32')/255

y_train = to_categorical(train_labels)
y_test = to_categorical(test_labels)
```

- Entrenando a la red:
```Python
model.fit(x_train, y_train, epochs=5, batch_size=128)` 
```

- Evaluando a la red:
```Python
model.evaluate(x_test, y_test)`
```

Resultados personales:
![[Captura de pantalla 2024-10-01 a las 10.31.18 a. m..png]]