## Métricas de Clasificación y Métricas de Regresión
- **Métricas de Clasificación**:
    - **Accuracy**: Proporción de predicciones correctas sobre el total de predicciones.
    - **Precision**: Proporción de verdaderos positivos sobre el total de positivos predichos.
    - **Recall (Sensibilidad)**: Proporción de verdaderos positivos sobre el total de positivos reales.
    - **F1 Score**: Media armónica entre **precision** y **recall**, útil cuando el dataset es desbalanceado.
- **Métricas de Regresión**:
    - **Mean Squared Error (MSE)**: Promedio de los cuadrados de las diferencias entre los valores reales y predichos.
    - **Mean Absolute Error (MAE)**: Promedio de los valores absolutos de las diferencias entre las predicciones y los valores reales.
    - **R-Squared (R²)**: Mide qué tan bien los valores predichos se alinean con los valores reales, proporcionando una idea de la calidad del ajuste.


## Imbalanced Classification Problems y Técnicas para Manejar Datos Desbalanceados
![[Captura de pantalla 2024-10-03 a las 3.14.27 p. m..png]]

- **Problemas de Clasificación Desbalanceada**:
    - Los **problemas de clasificación desbalanceada** ocurren cuando una clase tiene muchas más muestras que las demás. Esto puede llevar a un sesgo del modelo hacia la clase mayoritaria.

- **SMOTE (Synthetic Minority Over-sampling Technique)**:
    - **Descripción**: Crea nuevas muestras sintéticas de la clase minoritaria interpolando entre ejemplos existentes. Es útil para aumentar el tamaño del conjunto de datos minoritarios sin replicar exactamente las muestras.

- **Random Undersampler**:
    - **Descripción**: Reduce la cantidad de muestras de la clase mayoritaria de forma aleatoria para balancear el dataset.
    - **Ventaja**: Puede ayudar a balancear el dataset, pero podría eliminar información valiosa si se pierde demasiada variabilidad.

- **Borderline-SMOTE**:
    - **Descripción**: Variante de **SMOTE** que se enfoca en crear ejemplos sintéticos solo cerca de los límites de decisión, donde los ejemplos de la clase minoritaria están más cercanos a la clase mayoritaria.
    - **Ventaja**: Mejora el rendimiento del clasificador al prestar atención a las muestras críticas en el límite entre clases.

- **Adaptive Synthetic Sampling (ADASYN)**:
    - **Descripción**: ADASYN genera nuevas muestras sintéticas adaptativamente, prestando más atención a aquellas regiones donde el clasificador tiene más problemas (áreas donde hay menos ejemplos de la clase minoritaria).
    - **Ventaja**: Focaliza el aumento de datos en las regiones más difíciles, mejorando así el rendimiento general del clasificador.


## Breve Introducción a Técnicas de Detección de Outliers
![[Captura de pantalla 2024-10-03 a las 3.15.13 p. m..png]]

- **Outliers**: Los **outliers** son datos que se desvían significativamente del patrón general de un dataset y pueden influir negativamente en el rendimiento de un modelo.
### Standard Deviation Method
- **Método de Desviación Estándar**:
    - Consiste en identificar puntos de datos que están a varias desviaciones estándar de la media. En general, se considera que los puntos con un **Z-Score** mayor a 3 (es decir, tres desviaciones estándar de la media) son outliers.
    - **Fórmula del Z-Score**:$Z=\frac{X−μ}{σ}$​ donde $X$ es el valor del dato, $μ$ es la media del conjunto de datos, y $σ$ es la desviación estándar.

### Interquartile Range (IQR) Method
- **Método del Rango Intercuartílico (IQR)**:
    - Calcula el **rango intercuartílico** para definir los límites superiores e inferiores para detectar outliers. Se define el IQR como la diferencia entre el tercer cuartil (Q3Q3) y el primer cuartil (Q1Q1).
    - **Fórmulas**:
        - $IQR=Q3−Q1$
        - Outliers: $X<Q1−1.5×IQR$ o $X>Q3+1.5×IQR$
    - Es una técnica robusta que no se ve afectada por la distribución específica de los datos.

### Isolation Forest
- **Isolation Forest**:
    - **Concepto**: Algoritmo basado en árboles de decisión que intenta aislar observaciones dividiendo el espacio de características de manera aleatoria. Los outliers tienden a aislarse con menos divisiones, lo cual indica que se desvían del patrón general.
    - **Ventajas**:
        - Tiene una complejidad lineal respecto al tamaño del conjunto de datos.
        - Funciona bien en datasets con alta dimensionalidad.

















## Proceso de Cuantización
La **cuantización** es un proceso para reducir la precisión de los valores numéricos, transformándolos de un espacio de mayor precisión (por ejemplo, de 32 bits) a un espacio de menor precisión (por ejemplo, de 8 bits). La cuantización es muy útil para la implementación de modelos en dispositivos con recursos limitados.

### Ventajas de la Cuantización
- **Reducción del Tamaño del Modelo**:
  - La cuantización reduce significativamente el tamaño del modelo, haciéndolo más adecuado para dispositivos embebidos y móviles.
  - Reducir de **float32** a **int8** puede reducir el tamaño del modelo hasta 4 veces.
- **Aumento de la Velocidad de Inferencia**:
  - Los cálculos en números enteros son menos costosos computacionalmente que en punto flotante, lo cual acelera la inferencia.
- **Reducción del Consumo de Energía**:
  - Los cálculos en aritmética de enteros requieren menos energía, lo cual es crítico en dispositivos alimentados por batería.

### Entero vs Floating Point
- **Punto Flotante**:
  - Representa números utilizando una base y un exponente, lo cual permite una representación flexible y precisa. Utilizado comúnmente en entrenamiento debido a la alta precisión que se necesita para ajustar los pesos.
- **Entero (Integer)**:
  - Utiliza una representación más simple y menos precisa, pero los cálculos son considerablemente más rápidos. La cuantización a enteros permite que los modelos sean más eficientes en dispositivos con limitaciones de recursos.



### Proceso de Cuantización


#### Técnicas de Cuantización
- **Cuantización Estática (Static Quantization)**:
  - En esta técnica, las activaciones y los pesos se convierten a **enteros** antes del inicio de la inferencia.
  - Utiliza un factor de escala que mapea el rango original en punto flotante al nuevo rango en enteros.
- **Cuantización Dinámica (Dynamic Quantization)**:
  - Aquí, los pesos se cuantizan a enteros, pero las activaciones se cuantizan dinámicamente durante la inferencia.
  - Este método es menos preciso que la cuantización estática, pero puede ser más eficiente dependiendo de la aplicación.
- **Cuantización Completa en Enteros (Full Integer Quantization)**:
  - Tanto los pesos como las activaciones se convierten a **int8**, lo cual permite que el hardware optimice al máximo la eficiencia durante la inferencia.

#### Quantization Aware Training (QAT)
**Quantization Aware Training (QAT)** es una técnica donde se simula la cuantización durante el entrenamiento del modelo, permitiendo que la red aprenda a compensar las imprecisiones introducidas por el proceso de cuantización.

- **Pasos del QAT**:
  1. **Inicialización con un Modelo Preentrenado**: Comienza con un modelo ya entrenado en punto flotante.
  2. **Simulación de Cuantización Durante el Entrenamiento**: Durante el forward pass, los pesos y activaciones se simulan como si estuvieran cuantizados, mientras los gradientes se calculan en punto flotante durante el backward pass.
  3. **Optimización**: El modelo ajusta los pesos para adaptarse a las restricciones de cuantización, asegurando que la precisión final sea cercana a la del modelo original en punto flotante.

- **Ventajas de QAT**:
  - Mejora la **precisión** del modelo cuantizado al permitir que se adapte a las restricciones de menor precisión.
  - Ideal para situaciones donde se busca el máximo rendimiento en hardware con baja capacidad de procesamiento.



### Dynamic Range

El **Dynamic Range** en el contexto de la cuantización se refiere al rango de valores que los datos pueden tomar. Al realizar la cuantización, el rango dinámico de los pesos y activaciones se mapea a un conjunto más limitado de valores.

- **Escala y Offset**:
  - En la cuantización estática y dinámica, los valores en punto flotante se mapean a valores enteros utilizando una **escala** y un **offset**.
  - El **rango dinámico** de los valores cuantizados depende de estos parámetros, y un ajuste adecuado es crucial para minimizar la pérdida de precisión.



### ¿Cuál Técnica de Cuantización Elegir?
![[Captura de pantalla 2024-10-03 a las 3.16.03 p. m..png]]

- **Cuantización Estática**:
  - Adecuada para **dispositivos móviles y embebidos** donde se requiere máxima eficiencia durante la inferencia.
  - Requiere un proceso de calibración antes de la inferencia para determinar el rango dinámico.

- **Cuantización Dinámica**:
  - Recomendada para **CPU y hardware general**, donde la inferencia se realiza en tiempo real pero no se necesita la máxima eficiencia posible.
  - Fácil de implementar y funciona bien con modelos donde las activaciones pueden cambiar drásticamente.

- **Cuantización Completa en Enteros**:
  - Preferida para **hardware especializado** como TPUs, donde los cálculos en enteros son muy eficientes.
  - Utilizada en aplicaciones de producción para despliegue en entornos con recursos limitados.

- **Quantization Aware Training (QAT)**:
  - Ideal cuando se requiere la **máxima precisión** en el modelo cuantizado. Se utiliza principalmente cuando la degradación de rendimiento es inaceptable, como en **aplicaciones críticas** que requieren precisión casi equivalente al modelo en punto flotante.
