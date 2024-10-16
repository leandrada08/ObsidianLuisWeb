

## **Programación Tradicional vs. Aprendizaje Automático**
- **Programación Tradicional**: Consiste en escribir reglas explícitas que actúan sobre datos para obtener respuestas. Por ejemplo, en un juego de ladrillos, se programa cómo rebotará una pelota o qué sucede al golpear un ladrillo. Esto funciona bien en escenarios simples, pero a medida que los problemas se vuelven más complejos, escribir todas las reglas se vuelve impracticable.
  ![[Captura de pantalla 2024-10-10 a las 11.31.59 a. m..png]]
- **Ejemplo de detección de actividad**: Si intentas escribir reglas para identificar si alguien está caminando, corriendo o andando en bicicleta usando solo la velocidad, pronto notarás que estas reglas pueden ser inexactas o insuficientes, como cuando alguien corre cuesta abajo más rápido que lo que pedalea cuesta arriba.

### **Cómo Soluciona Esto el Aprendizaje Automático**

![[Captura de pantalla 2024-10-10 a las 11.32.13 a. m..png]]
En lugar de escribir reglas explícitas, el **aprendizaje automático** invierte el proceso:
1. Se proporcionan datos etiquetados (con las respuestas correctas) y se deja que la computadora **aprenda** las reglas que relacionan esos datos con las etiquetas.
2. Este proceso crea un **modelo** que puede generalizar las reglas aprendidas a datos nuevos, generando inferencias basadas en probabilidades.

### **Funcionamiento del Aprendizaje Automático**
1. **Adivinar relaciones**: El sistema hace una suposición inicial sobre la relación entre los datos y las etiquetas.
2. **Medir la precisión**: Se mide qué tan buena o mala es la suposición (usando una métrica llamada **pérdida**). Una mayor pérdida indica menor precisión.
3. **Optimización**: El sistema ajusta su suposición basándose en el error de la predicción anterior, y repite el proceso, mejorando la precisión con cada intento.
![[Captura de pantalla 2024-10-10 a las 11.34.33 a. m..png]]
Finalmente, esto construye un modelo que puede recibir nuevos datos y generar inferencias, es decir, estimar las probabilidades de que esos datos correspondan a las etiquetas conocidas.
![[Captura de pantalla 2024-10-10 a las 11.35.13 a. m..png]]




- Ejemplo de calculo de error: [https://colab.research.google.com/github/tinyMLx/colabs/blob/master/2-1-4-ExploringLoss.ipynb](https://colab.research.google.com/github/tinyMLx/colabs/blob/master/2-1-4-ExploringLoss.ipynb)
- Ejemplo de minizacion de perdida: https://colab.research.google.com/github/tinyMLx/colabs/blob/master/2-1-6-MimimizingLoss.ipynb
- Codigo para definir modelo: https://colab.research.google.com/github/tinyMLx/colabs/blob/master/2-1-9-FirstNeuralNetwork.ipynb#scrollTo=qtu5rJBA8o9M
- Modelo con minimizacion de perdida: https://colab.research.google.com/github/tinyMLx/colabs/blob/master/2-2-3-MimimizingLoss.ipynb







## **Problema del Sobreajuste**
Imagina que entrenas una red neuronal para reconocer zapatos, usando una gran cantidad de ejemplos. Después de entrenar, obtienes una precisión del 100%. Sin embargo, cuando pruebas la red con un zapato nuevo, que no estaba en el conjunto de entrenamiento, la red falla. Esto ocurre porque el modelo aprendió demasiado bien los ejemplos de entrenamiento, pero no es capaz de **generalizar** a datos nuevos o no vistos.

### **División de los Datos**
Para evitar esto, es importante dividir los datos en tres conjuntos:
1. **Entrenamiento (Training set)**: La red aprende de estos datos.
2. **Validación (Validation set)**: No se usa para entrenar, sino para evaluar el rendimiento de la red en cada paso del entrenamiento. Esto permite monitorear si la red está sobreajustando.
3. **Prueba (Test set)**: Este conjunto se usa al final del entrenamiento para verificar cómo se comporta la red con datos completamente nuevos.

### **Ejemplo en el Código**
Al entrenar una red con el conjunto de datos MNIST, que contiene dígitos escritos a mano, puedes dividir los datos en conjuntos de entrenamiento y validación usando **TensorFlow**:

```python
model.fit(train_images, train_labels, epochs=20, validation_data=(val_images, val_labels))
```

Durante el entrenamiento, verás dos métricas:
- **Precisión en el conjunto de entrenamiento**: Cómo de bien está aprendiendo la red con los datos de entrenamiento.
- **Precisión en el conjunto de validación**: Cómo de bien generaliza la red en datos que no ha visto durante el entrenamiento.

El objetivo es que las dos precisiones sean lo más cercanas posible. Si la precisión de entrenamiento es muy alta, pero la de validación es baja, indica que el modelo está sobreajustado, es decir, ha aprendido demasiado bien los datos de entrenamiento, pero no sabe generalizar.

### **Evaluación Final**
Al finalizar el entrenamiento, puedes evaluar el modelo con el conjunto de prueba, si el dataset lo tiene, para obtener una métrica más objetiva sobre la capacidad del modelo para generalizar:

```python
test_loss, test_acc = model.evaluate(test_images, test_labels)
```


- **Ejemplo practico:** https://colab.research.google.com/github/tinyMLx/colabs/blob/master/2-3-7-FashionMNISTConvolutionsVisualizations.ipynb#scrollTo=C0tFgT1MMKi6