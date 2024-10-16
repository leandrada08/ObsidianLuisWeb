
# UNIDAD 1: ESTADÍSTICA DESCRIPTIVA

## Tipos de Variables
- **Cualitativas**: Describen características o cualidades (Ej: color de ojos).
  - **Nominales**: Sin orden específico (Ej: género).
  - **Ordinales**: Tienen un orden natural (Ej: nivel de educación).

- **Cuantitativas**: Expresan cantidades.
  - **Discretas**: Toman valores específicos (Ej: número de hijos).
  - **Continuas**: Pueden tomar cualquier valor dentro de un intervalo (Ej: peso).

## Diagramas y Representación Gráfica

### Diagrama de Puntos
Representa cada observación como un punto a lo largo de una línea. Ideal para datos discretos.

### Diagrama de Barras
Usado para representar **variables cualitativas** o **cuantitativas discretas**. La altura de cada barra es proporcional a la frecuencia de cada categoría.

### Histogramas
Un **histograma** se usa para representar variables cuantitativas continuas, donde los datos se agrupan en **intervalos** y se representan con barras.

## Redondeo
Redondear los valores a un número adecuado de cifras significativas para facilitar la presentación de datos.

## Medidas de Posición y Dispersión

### Medidas de Posición
- **Media**: Promedio de todos los valores.
- **Mediana**: Valor que divide los datos en dos partes iguales.
- **Moda**: Valor que ocurre con mayor frecuencia.

### Medidas de Dispersión
- **Varianza** (\( s^2 \)): Mide la dispersión respecto a la media.
- **Desviación estándar** (\( s \)): Raíz cuadrada de la varianza.
- **Rango**: Diferencia entre el valor máximo y el mínimo.

### Coeficiente de Variación
El **coeficiente de variación** es la relación entre la desviación estándar y la media, expresada como porcentaje:

\[
CV = \frac{s}{\bar{x}} \times 100
\]

## Desigualdad de Tchebychev
Para cualquier conjunto de datos, al menos una fracción de \( (1 - \frac{1}{k^2}) \) de los valores se encuentra dentro de \( k \) desviaciones estándar de la media, donde \( k > 1 \).

## Análisis Exploratorio de Datos
**Exploración visual** de los datos mediante gráficos (histogramas, diagramas de cajas, etc.) para entender la estructura de los datos, posibles outliers, y distribución general.

## Distribuciones de Frecuencia Bivariadas y Marginales
- **Distribución Bivariada**: Describe la relación entre dos variables mediante una tabla de frecuencias.
- **Distribuciones Marginales**: Se obtienen sumando las frecuencias sobre una dimensión de la distribución bivariada.

# UNIDAD 2: CONCEPTO DE PROBABILIDAD

## Experimento Aleatorio
Un **experimento aleatorio** es un proceso que conduce a uno de varios resultados posibles, sin poder predecir cuál será el resultado (Ej: lanzamiento de una moneda).

## Frecuencia Relativa de un Suceso
La **frecuencia relativa** de un suceso es la proporción de veces que ocurre dicho suceso en un número grande de repeticiones del experimento.

## Probabilidad como Límite de la Frecuencia Relativa
La **probabilidad** de un suceso puede entenderse como el **límite** de su frecuencia relativa cuando el número de repeticiones del experimento tiende a infinito.

## Modelo Matemático de un Experimento Aleatorio
Un **modelo matemático** describe el espacio muestral (\( S \)), el conjunto de todos los resultados posibles del experimento, y asigna probabilidades a los sucesos.

## Propiedades de la Probabilidad
1. **No Negatividad**: \( P(A) \geq 0 \).
2. **Normalización**: \( P(S) = 1 \).
3. **Adición**: Si \( A \) y \( B \) son eventos mutuamente excluyentes, entonces \( P(A \cup B) = P(A) + P(B) \).

## Probabilidad Condicional
La **probabilidad condicional** de un suceso \( A \), dado que \( B \) ha ocurrido, se denota como \( P(A|B) \):

\[
P(A|B) = \frac{P(A \cap B)}{P(B)}, \quad P(B) > 0
\]

### Regla del Producto
Para dos sucesos \( A \) y \( B \):

\[
P(A \cap B) = P(A|B) P(B)
\]

## Sucesos Independientes
Dos sucesos \( A \) y \( B \) son **independientes** si:

\[
P(A \cap B) = P(A) P(B)
\]

# UNIDAD 3: MODELOS DE DISTRIBUCIÓN DE PROBABILIDAD

## Variables Aleatorias
Una **variable aleatoria** asigna un número a cada resultado posible de un experimento aleatorio.

### Variables Discretas y Continuas
- **Discretas**: Toman valores específicos (Ej: número de llamadas).
- **Continuas**: Toman cualquier valor dentro de un rango (Ej: peso de una persona).

## Función de Distribución
La **función de distribución acumulativa** (CDF) de una variable aleatoria \( X \), denotada como \( F(x) \), da la probabilidad de que \( X \) tome un valor menor o igual a \( x \).

## Esperanza Matemática y Varianza

### Esperanza Matemática
La **esperanza** de una variable aleatoria \( X \) es el valor promedio esperado de \( X \):

\[
E(X) = \sum_{i} x_i p(x_i) \quad \text{(discreta)}, \quad E(X) = \int_{-\infty}^{\infty} x f(x) \, dx \quad \text{(continua)}
\]

### Varianza
La **varianza** mide la dispersión de la variable respecto a su media:

\[
\text{Var}(X) = E[(X - E(X))^2]
\]

### Cota de Tchebychev
Para cualquier variable aleatoria \( X \):

\[
P(|X - E(X)| \geq k\sigma) \leq \frac{1}{k^2}
\]

Esto proporciona una cota sobre la probabilidad de que \( X \) esté lejos de la media.

# UNIDAD 4: VARIABLES ALEATORIAS CON NOMBRES PROPIOS

## Pruebas de Bernoulli y Distribución de Bernoulli
- **Prueba de Bernoulli**: Es un experimento aleatorio que tiene dos posibles resultados: éxito (\( p \)) y fracaso (\( 1-p \)).
- **Distribución de Bernoulli**: Describe el resultado de una sola prueba de Bernoulli. Si \( X \) es una variable aleatoria de Bernoulli:

  \[
  P(X = 1) = p, \quad P(X = 0) = 1 - p
  \]

## Distribución Binomial
La **Distribución Binomial** cuenta el número de éxitos en \( n \) pruebas de Bernoulli independientes. Si \( X \) es una variable aleatoria binomial con parámetros \( n \) y \( p \):

\[
P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}, \quad k = 0, 1, \ldots, n
\]

## Distribución Geométrica
La **Distribución Geométrica** modela el número de ensayos necesarios hasta obtener el primer éxito en una secuencia de pruebas de Bernoulli independientes. La probabilidad de obtener el primer éxito en el ensayo \( k \) es:

\[
P(X = k) = (1-p)^{k-1} p, \quad k = 1, 2, 3, \ldots
\]

## Proceso de Poisson y Distribución de Poisson
- **Proceso de Poisson**: Describe eventos que ocurren al azar en un intervalo de tiempo o espacio.
- **Distribución de Poisson**: Modela el número de eventos que ocurren en un intervalo fijo. Si la tasa de ocurrencia es \( \lambda \):

  \[
  P(X = k) = \frac{e^{-\lambda} \lambda^k}{k!}, \quad k = 0, 1, 2, \ldots
  \]

- La **Distribución de Poisson** se puede obtener como el **límite** de la **Distribución Binomial** cuando \( n \to \infty \) y \( p \to 0 \), con \( n p = \lambda \).

## Distribución Exponencial
La **Distribución Exponencial** modela el tiempo entre eventos en un proceso de Poisson. Su función de densidad es:

\[
f(x) = \lambda e^{-\lambda x}, \quad x \geq 0
\]

## Distribución Normal
La **Distribución Normal** es una de las más importantes en estadística. Está definida por dos parámetros: la media (\( \mu \)) y la desviación estándar (\( \sigma \)):

\[
f(x) = \frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{(x - \mu)^2}{2\sigma^2}}
\]

### Relación entre las Distribuciones
- La **Binomial** se aproxima a la **Normal** cuando el número de pruebas es grande.
- La **Poisson** se aproxima a la **Normal** si \( \lambda \) es grande.

# UNIDAD 5: DISTRIBUCIÓN DE FUNCIONES DE VARIABLES ALEATORIAS

## Distribución Conjunta de Variables Aleatorias
La **distribución conjunta** de dos variables aleatorias \( X \) e \( Y \) describe la probabilidad de que ambas variables tomen ciertos valores simultáneamente.

### Distribuciones Marginales
La **distribución marginal** de una variable se obtiene sumando (o integrando) la distribución conjunta sobre los valores de la otra variable.

### Variables Aleatorias Independientes
Dos variables \( X \) e \( Y \) son **independientes** si:

\[
P(X = x, Y = y) = P(X = x) P(Y = y)
\]

## Esperanza de Sumas y Productos
- **Esperanza de la Suma**: Si \( X \) e \( Y \) son variables aleatorias:

  \[
  E(X + Y) = E(X) + E(Y)
  \]

- **Esperanza del Producto**: Si \( X \) e \( Y \) son independientes:

  \[
  E(XY) = E(X) E(Y)
  \]

## Covarianza y Correlación
- **Covarianza**: Mide cómo varían conjuntamente dos variables aleatorias:

  \[
  \text{Cov}(X, Y) = E[(X - E(X))(Y - E(Y))]
  \]

- **Correlación**: Es una medida adimensional de la relación lineal entre \( X \) e \( Y \):

  \[
  \rho_{X,Y} = \frac{\text{Cov}(X, Y)}{\sigma_X \sigma_Y}
  \]

## Varianza de la Suma
Para variables aleatorias \( X \) e \( Y \):

\[
\text{Var}(X + Y) = \text{Var}(X) + \text{Var}(Y) + 2\text{Cov}(X, Y)
\]

Si \( X \) e \( Y \) son independientes, la covarianza es cero.

## Teorema Central del Límite (TCL)
El **Teorema Central del Límite** establece que la suma de un número grande de variables aleatorias independientes y con distribuciones idénticas se aproxima a una **distribución normal**, independientemente de la distribución original de las variables.

### Aplicaciones a la Estimación de Errores
El TCL es fundamental para la **estimación de errores** y para entender cómo las fluctuaciones aleatorias en múltiples medidas se distribuyen normalmente.

# UNIDAD 6: INTRODUCCIÓN A LA INFERENCIA ESTADÍSTICA

## Objetivo de la Inferencia Estadística
La **inferencia estadística** se encarga de sacar conclusiones sobre una población a partir de una muestra. Esto incluye **estimación de parámetros** y **pruebas de hipótesis**.

## Réplicas Independientes de un Experimento Aleatorio
Se considera que las muestras son **réplicas independientes** si los resultados de un experimento no afectan los resultados de otro.

## Método de Montecarlo
El **método de Montecarlo** es una técnica de simulación para obtener aproximaciones mediante **muestreo aleatorio** repetido. Se usa para simular réplicas de una variable aleatoria y estimar probabilidades o integrales.

## Identificación del Modelo
La **identificación del modelo** es el proceso de determinar cuál es la **distribución** que describe mejor los datos observados, usando gráficos y pruebas estadísticas.

# UNIDAD 7: ESTIMACIÓN

## Estimación Puntual
La **estimación puntual** consiste en obtener un valor único como una estimación del parámetro de la población.

## Métodos de los Momentos
Los **métodos de los momentos** utilizan los momentos muestrales para estimar los **momentos de la población** y, por ende, los parámetros de la distribución.

## Estimación de \( s^2, s \) y del Cociente Señal/Ruido
- **\( s^2 \)**: Estimador de la **varianza** de la población.
- **\( s \)**: Desviación estándar muestral.
- **Cociente Señal/Ruido** (\( SNR \)): Relación entre la **media** y la **desviación estándar**, una medida de la calidad de la señal.

## Estimación por Intervalos
La **estimación por intervalos** proporciona un **intervalo de confianza** para un parámetro, indicando un rango probable en el que se encuentra el parámetro.

### Intervalo de Confianza
- **Para la Media**: Si la muestra es grande, se usa:

  \[
  \bar{x} \pm z_{\alpha/2} \frac{s}{\sqrt{n}}
  \]

  donde \( z_{\alpha/2} \) es el valor crítico de la **distribución normal estándar**.

# UNIDAD 8: PRUEBAS DE HIPÓTESIS

## Introducción
Las **pruebas de hipótesis** son procedimientos estadísticos para decidir si una afirmación sobre un parámetro de la población es consistente con los datos muestrales.

## Tipos de Hipótesis
- **Hipótesis Nula (\( H_0 \))**: Afirmación que se pone a prueba, usualmente representando el estado "sin efecto" o "sin diferencia".
- **Hipótesis Alternativa (\( H_1 \))**: Afirmación que se acepta si los datos proporcionan suficiente evidencia contra \( H_0 \).

### Definición y Metodología
1. **Planteamiento**: Definir \( H_0 \) y \( H_1 \).
2. **Nivel de Significancia (\( \alpha \))**: Probabilidad de rechazar \( H_0 \) cuando es verdadera (error tipo I).
3. **Estadístico de Prueba**: Cálculo basado en la muestra para tomar la decisión.
4. **Región Crítica**: Conjunto de valores para los cuales se rechaza \( H_0 \).

## Tipos de Errores
- **Error Tipo I (\( \alpha \))**: Rechazar \( H_0 \) cuando es verdadera.
- **Error Tipo II (\( \beta \))**: No rechazar \( H_0 \) cuando es falsa.

## Pruebas para una Población

### Test para la Media
- **Cuando \( \sigma \) es conocido**: Se usa la distribución \( Z \):

  \[
  Z = \frac{\bar{X} - \mu_0}{\sigma / \sqrt{n}}
  \]

- **Cuando \( \sigma \) es desconocido**: Se usa la distribución \( t \).

### Test para una Proporción
La prueba se basa en la distribución normal si la muestra es suficientemente grande:

\[
Z = \frac{\hat{p} - p_0}{\sqrt{\frac{p_0 (1 - p_0)}{n}}}
\]

## Pruebas para Dos Poblaciones

### Diferencia de Medias
- **Muestras Independientes**: 
  - **Varianzas Iguales**: Se usa el estadístico \( t \) agrupado.
  - **Varianzas Desiguales**: Se usa la versión ajustada de \( t \).

- **Muestras Dependientes (Pareadas)**: Se realiza la prueba sobre las diferencias \( d_i \).

### Diferencia de Proporciones
Se usa el estadístico \( Z \) para probar si hay diferencia significativa entre dos proporciones:

\[
Z = \frac{\hat{p}_1 - \hat{p}_2}{\sqrt{\hat{p}(1-\hat{p}) \left( \frac{1}{n_1} + \frac{1}{n_2} \right)}}
\]

donde \( \hat{p} \) es la proporción combinada.

# UNIDAD 9: REGRESIÓN LINEAL SIMPLE

## El Modelo de Regresión Lineal Simple
El **modelo de regresión lineal simple** describe la relación entre una **variable dependiente** (\( Y \)) y una **variable independiente** (\( X \)) mediante una línea recta:

\[
Y = \beta_0 + \beta_1 X + \epsilon
\]

donde:
- \( \beta_0 \) es el **intercepto**.
- \( \beta_1 \) es la **pendiente**.
- \( \epsilon \) es el **término de error** (aleatorio).

## Hipótesis del Modelo
- **Linealidad**: La relación entre \( X \) e \( Y \) es lineal.
- **Independencia**: Los errores \( \epsilon \) son independientes.
- **Normalidad**: Los errores \( \epsilon \) tienen una distribución normal con media cero.
- **Homocedasticidad**: La varianza de \( \epsilon \) es constante.

## Estimación por el Método de Mínimos Cuadrados
El **Método de Mínimos Cuadrados** minimiza la suma de los cuadrados de las diferencias entre los valores observados y los valores predichos por la línea de regresión. Los estimadores son:

\[
\hat{\beta}_1 = \frac{\sum (X_i - \bar{X})(Y_i - \bar{Y})}{\sum (X_i - \bar{X})^2}
\]

\[
\hat{\beta}_0 = \bar{Y} - \hat{\beta}_1 \bar{X}
\]

## Bondad del Modelo
- **Coeficiente de Determinación (\( R^2 \))**: Mide la proporción de la variabilidad de \( Y \) explicada por el modelo. Varía entre 0 y 1.

\[
R^2 = 1 - \frac{\sum (Y_i - \hat{Y}_i)^2}{\sum (Y_i - \bar{Y})^2}
\]

## Validez del Modelo
Se utilizan **residuos** y **pruebas de significancia** para validar el modelo. Un **análisis de residuos** puede indicar si las suposiciones del modelo son adecuadas.

## Modelos Más Complejos
- **Regresión Polinomial**: Cuando la relación entre \( X \) e \( Y \) no es lineal, se puede usar un **polinomio** de grado mayor.
- **Modelos Multivariados**: Incorporan más variables independientes.

### Ejemplos
Un ejemplo común en ingeniería es la predicción de la resistencia de un material basada en su temperatura de tratamiento.

# UNIDAD 10: CONTROL DE CALIDAD

## Introducción
El **control de calidad** se enfoca en monitorear y asegurar que un proceso de producción esté bajo control y cumpla con los estándares establecidos.

## Proceso Bajo Control
Un **proceso bajo control** es aquel en el que las variaciones observadas están únicamente asociadas a causas comunes (no controlables) y no a causas especiales (controlables).

## Intervalos de Tolerancia
Los **intervalos de tolerancia** representan el rango de valores aceptables para una característica de calidad. Si el proceso produce dentro de estos límites, se considera aceptable.

## Capacidad de un Proceso
La **capacidad de un proceso** se refiere a la habilidad del proceso para producir productos dentro de los límites de tolerancia. Se mide mediante:

\[
C_p = \frac{USL - LSL}{6\sigma}
\]

donde \( USL \) y \( LSL \) son los **límites superior e inferior de especificación** y \( \sigma \) es la **desviación estándar** del proceso.

## Gráficos de Control
- **Gráficos de Medias (\( \bar{X} \)) y Desviaciones (\( R \))**: Se utilizan para monitorear la variabilidad de un proceso.
- **Gráficos de Control**: Sirven para identificar si el proceso está bajo control o si existen causas especiales de variabilidad.

### Interpretación
- Si los puntos en el gráfico se encuentran dentro de los límites de control y no muestran patrones sistemáticos, el proceso se considera bajo control.


# UNIDAD 11: INTRODUCCIÓN AL DISEÑO DE EXPERIMENTOS

## Introducción
El **diseño de experimentos (DOE)** es una metodología para planificar experimentos de manera eficiente, de modo que se obtenga la máxima información posible con el mínimo número de pruebas.

## Análisis de la Varianza (ANOVA)
El **Análisis de la Varianza (ANOVA)** es una técnica utilizada para comparar **medias** de varios grupos y determinar si existen diferencias significativas entre ellas.

### Contraste de Igualdad de Medias
En **ANOVA**, se contrasta la hipótesis nula de que todas las medias son iguales contra la alternativa de que al menos una media es diferente.

## Comparaciones Múltiples
Cuando se rechaza la hipótesis nula en ANOVA, se pueden realizar **comparaciones múltiples** para determinar qué grupos difieren específicamente.

## Introducción al Diseño de Experimentos
- **Diseño Completamente Aleatorizado**: Todos los tratamientos se asignan de forma aleatoria.
- **Diseños Bloqueados**: Se utiliza cuando existen **factores de bloqueo** que podrían influir en la variable de respuesta.

El diseño de experimentos se utiliza para **optimizar** procesos en ingeniería y para determinar **factores significativos** que afectan la producción o la calidad del producto.
