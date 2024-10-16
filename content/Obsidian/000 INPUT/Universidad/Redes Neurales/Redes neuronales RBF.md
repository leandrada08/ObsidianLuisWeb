


## **Redes Neuronales RBF (Radial Basis Function)**

Las **redes neuronales RBF (Radial Basis Function)** son un tipo especial de red neuronal que se utiliza ampliamente en tareas de **clasificación**, **regresión** y **aproximación de funciones no lineales**. Estas redes destacan por usar **funciones de base radial** como funciones de activación, lo que las hace especialmente útiles para problemas donde la relación entre los datos no es lineal.
![[Captura de pantalla 2024-10-11 a las 5.24.53 p. m..png|300]]
### **Estructura de las Redes RBF**

Una red neuronal RBF tiene una estructura en **tres capas**:

1. **Capa de Entrada**: Donde se reciben los datos de entrada (features o características del problema).
2. **Capa Oculta (Nodos RBF)**: Esta capa contiene nodos que aplican una **función de base radial**. Cada nodo tiene un **centro** y un **radio**. La activación de los nodos depende de la **distancia** entre la entrada y el centro del nodo.
3. **Capa de Salida**: La salida se calcula como una **combinación ponderada** de las activaciones de los nodos de la capa oculta. Los pesos en esta capa determinan cuánto contribuye cada nodo RBF a la salida final.

### **Funcionamiento de una Red RBF**

El proceso de inferencia en una red RBF ocurre en tres pasos principales:

#### **1. Cálculo de la Activación en los Nodos Ocultos (Función de Activación Radial)**
![[Captura de pantalla 2024-10-11 a las 5.22.24 p. m..png|400]]
En las redes RBF, los nodos ocultos aplican una **función de activación radial** que evalúa la **distancia** entre la **entrada** y el **centro del nodo**. La función más común para calcular esta activación es la **función gaussiana**, aunque también se utilizan otras funciones radiales, como las de tipo multicuadrática o inversa.

- **Función Gaussiana**: Es la función más utilizada y tiene la forma:

  $$
  \phi(x, c) = \exp\left(-\frac{\|x - c\|^2}{2\sigma^2}\right)
  $$

  Donde:
  - $x$ es el vector de entrada.
  - $c$ es el **centro** del nodo.
  - $\sigma$ es el **radio** del nodo, que controla la "anchura" de la función.
  - $\|x - c\|$ es la **distancia euclidiana** entre la entrada y el centro del nodo.

La activación de cada nodo es alta cuando la entrada está **cerca del centro** del nodo y disminuye a medida que la entrada se aleja del centro.

#### **2. Multiplicación por los Pesos**

Una vez que se calculan las activaciones de los nodos en la capa oculta, estas se **multiplican por los pesos** correspondientes en la capa de salida. Cada nodo tiene un peso asociado, que indica cuánto contribuye su activación a la salida final.

- **Pesos en la capa de salida**: Los pesos son ajustados durante el proceso de **aprendizaje** y determinan la influencia de cada nodo en la predicción final.

#### **3. Cálculo de la Salida Final**

La salida de la red se obtiene sumando las activaciones ponderadas de todos los nodos en la capa oculta, y usualmente se le añade un **bias** para mejorar la precisión del modelo. Para una red RBF, la salida se expresa como:

$$
y(x) = \sum_{i=1}^{N} w_i \cdot \phi(x, c_i) + b
$$

Donde:
- $N$ es el número de nodos en la capa oculta.
- $w_i$ es el peso asociado al nodo $i$.
- $\phi(x, c_i)$ es la activación del nodo $i$ para la entrada $x$.
- $b$ es el **bias**.

Dependiendo del tipo de problema, la salida puede ser **binaria** (en problemas de clasificación) o **continua** (en problemas de regresión).

---

### **Componentes Clave de los Nodos RBF**

Cada nodo en una red RBF tiene tres parámetros principales:

#### **1. Centro del Nodo (c)**

El **centro** de un nodo RBF es el punto en el espacio de características donde la activación del nodo es máxima. Los nodos RBF están distribuidos en el espacio de entrada, y cada uno tiene su propio centro. La activación de un nodo es **alta cuando la entrada está cerca de su centro** y baja cuando la entrada está lejos.

- Los **centros** pueden ser **fijos** o **ajustarse durante el entrenamiento**. En algunos casos, se utilizan algoritmos como **K-means** para inicializar los centros de los nodos.

#### **2. Radio o Dispersión (σ)**

El **radio** de un nodo ($\sigma$) determina la **amplitud** o el alcance de la función radial. Es decir, indica **cuán lejos puede estar una entrada del centro del nodo para que aún se active**. 

- Un **radio grande** significa que el nodo responderá a entradas que están lejos de su centro, generando una activación más difusa.
- Un **radio pequeño** significa que el nodo solo activará fuertemente para entradas muy cercanas al centro.

#### **3. Peso del Nodo (w)**

El **peso** asociado a un nodo RBF controla **cuánto contribuye la activación de ese nodo a la salida final**. Los pesos se ajustan durante el **aprendizaje supervisado** o **no supervisado** y determinan la influencia de cada nodo en el resultado de la red.

---

### **Entrenamiento en Redes RBF**

El proceso de entrenamiento de una red RBF implica ajustar tanto los **pesos** de la capa de salida como los **centros** y, en algunos casos, los **radios** de los nodos en la capa oculta.

#### **1. Ajuste de los Pesos**

El ajuste de los **pesos** se realiza de manera similar a las redes neuronales tradicionales, donde se utiliza un algoritmo de **aprendizaje supervisado** como el **gradiente descendente**. Los pesos se actualizan en función del **error** entre la salida de la red y el valor objetivo, minimizando la **función de error**.

#### **2. Ajuste de los Centros y Radios**

Los **centros** y **radios** de los nodos pueden ajustarse durante el entrenamiento utilizando diferentes estrategias:

- **Centros fijos**: A menudo, los centros se determinan antes del entrenamiento, usando métodos como **K-means**, y se mantienen fijos.
- **Centros ajustables**: En algunos casos, los centros se ajustan durante el entrenamiento utilizando algoritmos de **optimización**, como el **gradiente descendente**.
- **Ajuste de los radios**: El radio ($\sigma$) puede ajustarse dinámicamente para optimizar el área de influencia de cada nodo.

---

### **Ventajas de las Redes RBF**

1. **Localidad de las funciones de activación**:
   - Las funciones de activación radial son **locales**, lo que significa que cada nodo responde principalmente a entradas cercanas a su centro. Esto es diferente de otras funciones de activación como ReLU o sigmoide, que tienen un comportamiento más global.
  
2. **Capacidad de modelar relaciones no lineales**:
   - Las redes RBF son excelentes para **aproximar funciones no lineales** y modelar relaciones complejas entre los datos de entrada y la salida.

3. **Interpolación suave**:
   - Gracias a la naturaleza suave de las funciones gaussianas, las redes RBF pueden **interpolar datos** de manera continua y sin picos bruscos, lo que es útil para tareas de regresión e interpolación.

---

### **Aplicaciones de las Redes RBF**

#### **1. Clasificación**

En tareas de **clasificación**, las redes RBF son útiles porque pueden separar clases no lineales al posicionar los nodos RBF estratégicamente en el espacio de entrada. Los nodos cercanos a los datos de una clase específica activan más fuertemente, ayudando a la red a hacer distinciones precisas.

- **Ejemplo**: Reconocimiento de patrones, detección de fraudes, clasificación de imágenes.

#### **2. Interpolación de funciones**

Las RBF son muy utilizadas en la **interpolación de funciones**, donde el objetivo es estimar valores intermedios basados en un conjunto de puntos conocidos. Debido a su naturaleza radial, estas redes pueden generar **superficies suaves** que pasan por puntos de datos conocidos.

- **Ejemplo**: Modelado de superficies en gráficos 3D o estimación de valores en simulaciones.

#### **3. Aproximación de funciones**

Las redes RBF también se utilizan para **aproximar funciones desconocidas**. Esto es útil en problemas donde no se conoce la relación exacta entre las entradas y la salida, pero se desea encontrar una aproximación.

- **Ejemplo**: Predicción de series temporales, modelado de fenómenos físicos como el flujo de aire o simulación de datos.

---

### **Comparación con otras redes neuronales**

- **RBF vs Redes Multicapa (MLP)**:
  - Las redes RBF tienen una **capa oculta con nodos locales**, mientras que las redes multicapa tradicionales (MLP) tienen capas ocultas donde cada neurona afecta globalmente la salida.
  - Las RBF suelen ser más rápidas de entrenar cuando el número de nodos es bajo, pero pueden requerir más nodos para tareas complejas, lo que aumenta el coste computacional.

- **RBF vs Máquinas de Soporte Vectorial (SVM)**:
  - Las SVM también pueden usar funciones de base radial como kernel, pero las RBF son más flexibles porque pueden ajustar tanto los centros como los pesos, mientras que en SVM solo se ajustan los pesos en el espacio transformado.

---

