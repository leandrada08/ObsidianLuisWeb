
## Introducción a el Descenso del Gradiente
En el aprendizaje automático, las **derivadas** se utilizan para encontrar cómo cambiar los parámetros del modelo (pesos y sesgos) para reducir una **función de pérdida** que mide el error de las predicciones. El **descenso del gradiente** es un algoritmo de optimización que utiliza estos conceptos para ajustar los parámetros de una red neuronal iterativamente con el objetivo de **minimizar la función de pérdida**.


## Algoritmo de Descenso del Gradiente
El **descenso del gradiente** es un algoritmo iterativo para encontrar los valores de los parámetros (pesos y sesgos) que minimizan la función de pérdida. Consiste en ajustar los parámetros siguiendo la dirección opuesta al gradiente:

$$
w_{ij} \leftarrow w_{ij} - \eta \cdot \frac{\partial \mathcal{L}}{\partial w_{ij}}
$$

Donde:
- $\eta$ es la **tasa de aprendizaje**: un valor positivo que determina la magnitud de cada actualización.
- $\frac{\partial \mathcal{L}}{\partial w_{ij}}$ es la **derivada parcial** de la función de pérdida respecto al peso $w_{ij}$.

### Tasa de Aprendizaje ($\eta$)
La **tasa de aprendizaje** es un hiperparámetro crítico que controla el **tamaño de los pasos** en la dirección opuesta al gradiente. Un valor de $\eta$ muy grande puede llevar a que el modelo **salte por encima** del valor mínimo de la pérdida, mientras que un valor muy pequeño puede hacer que el modelo **converja muy lentamente** o quede atrapado en un mínimo local.
![[Captura de pantalla 2024-10-01 a las 1.30.29 p. m..png]]
- **Oscilaciones**: Si la **tasa de aprendizaje** es muy alta, el descenso del gradiente puede oscilar y nunca converger. Si es demasiado baja, el proceso puede ser muy lento.


### Variantes comunes
- **Descenso por Gradiente Completo (Batch Gradient Descent)**
	- **Descripción**: Utiliza todo el conjunto de datos para calcular el gradiente de la pérdida y luego actualizar los parámetros.
	- **Ventajas**:
		- La actualización del gradiente es precisa y apunta a la verdadera dirección de descenso.
	- **Desventajas**:
		- Es computacionalmente costoso para grandes conjuntos de datos, ya que se requiere calcular el gradiente en cada muestra.
		- Puede llevar a convergencia lenta debido a la necesidad de procesar todos los datos en cada paso.
- **Descenso por Gradiente Estocástico (Stochastic Gradient Descent, SGD)**
	- **Descripción**: En lugar de usar todo el conjunto de datos, **SGD** actualiza los parámetros utilizando una sola muestra a la vez. Esto introduce ruido en la dirección de descenso, pero hace que las actualizaciones sean más rápidas.
	- **Ventajas**:
		- Es mucho más rápido y eficiente para grandes volúmenes de datos.
		- Introduce cierta **aleatoriedad** que puede ayudar a escapar de mínimos locales.
	- **Desventajas**:
		- La dirección del gradiente es ruidosa, lo cual puede dificultar la convergencia.
		- No garantiza un mínimo global, ya que las actualizaciones varían mucho.
- **Descenso por Gradiente Mini-Batch**
	- **Descripción**: Combina las ventajas del descenso por gradiente completo y del estocástico. Divide los datos en **mini-lotes** y realiza la actualización de los parámetros con base en estos lotes.
	- **Ventajas**:
		- Balancea precisión y eficiencia en la actualización de parámetros.
		- Aumenta la **eficiencia computacional** gracias al procesamiento paralelo en lotes.
	- **Desventajas**:
		- La selección del tamaño del mini-lote es crucial y puede afectar la velocidad de convergencia.

## Conceptos avanzados
### Optimizadores
Un **optimizador** es un algoritmo que se encarga de ajustar los **pesos** y **sesgos** de la red con el objetivo de **minimizar la función de pérdida**. En otras palabras, un optimizador define la manera en la que los parámetros se actualizan durante el entrenamiento para encontrar los valores que produzcan la menor pérdida posible.


El optimizador utiliza el **gradiente** de la función de pérdida para determinar la dirección y el tamaño de los ajustes necesarios. El más simple de estos algoritmos es el **Gradiente Descendente**, pero existen optimizadores avanzados que son más eficientes en cuanto a tiempo y convergencia como AdaGrand, AdaDelta, Momentum, Nesterov, ADAM, RMS prop.
![[Captura de pantalla 2024-10-03 a las 1.51.50 p. m..png]]
### Minimo local y minimo local
- **Mínimos Locales**: Dependiendo de la **topología de la función de pérdida**, el descenso del gradiente puede quedarse atrapado en **mínimos locales**. Técnicas como **SGD** o la **regularización** ayudan a evitar este problema.
- **Variantes Mejoradas**: Algoritmos como **Adam (Adaptive Moment Estimation)**, **RMSprop**, y **Momentum** son variantes del descenso del gradiente diseñadas para mejorar la **convergencia** y la **estabilidad** del entrenamiento.
![[Captura de pantalla 2024-10-01 a las 1.30.09 p. m..png]]
![[Captura de pantalla 2024-10-01 a las 1.32.29 p. m..png]]

#### Momentum

El concepto de momentum se introduce para hacer que el proceso de optimización sea más robusto y acelerar la convergencia. Momentum es una técnica que ayuda a suavizar la trayectoria hacia el mínimo, de manera similar a cómo funciona la inercia en la física.

**¿Cómo Funciona el Momentum?**
La idea es agregar un término que acumule el historial de gradientes previos, lo cual ayuda a “mantener el movimiento” en la misma dirección cuando el gradiente apunta consistentemente hacia ella. Esto resulta en un efecto más suave y rápido al acercarse al mínimo.
La actualización de los pesos utilizando momentum se realiza como sigue:
1.	Se calcula una velocidad (v) que es una combinación del gradiente actual y el gradiente acumulado:

$$v_{ij} = \gamma v_{ij} - \eta \frac{\partial \mathcal{L}}{\partial w_{ij}}
$$
	- Donde:
		- $v_{ij}$ es la velocidad de cambio del peso.
		- $\gamma$ es el factor de momentum, generalmente entre 0.9 y 0.99. Controla cuánto contribuye la velocidad pasada al nuevo ajuste.
		- $\eta$ es la tasa de aprendizaje.
2.	Los pesos se actualizan usando esta velocidad:
$$
w_{ij} \leftarrow w_{ij} + v_{ij}
$$

Momentum permite superar oscilaciones, especialmente en direcciones donde el gradiente cambia frecuentemente (como en los valles pronunciados), y ayuda a acelerar el descenso a lo largo de pendientes menos pronunciadas.

### Otras tecnicas
- Nesterov Momentum
	- Es una mejora sobre el momentum estandar. en lugar de calcular el gradiente en la posicion actual, se calcula "un paso adelante" usando la estimacion del momentum
- RMSProp
	- Divide el gradiente por la raiz cuadrada de una media exponencialmente ponderada de los cuadrados de los grandientes anteriores
- Adam
	- Combina las idea de momentum y RMP para acumular tanto el promedio de los gradiente como el promedio de los cuadrados de los gradientes



### **Intuición Geométrica del Descenso del Gradiente**
Podemos imaginar la **superficie de la función de pérdida** como una especie de terreno montañoso, donde queremos encontrar el punto más bajo (mínimo global). El gradiente descendente nos indica la dirección en la que debemos movernos para reducir la altura del terreno (la pérdida).

- El **gradiente** apunta siempre en la dirección de mayor crecimiento.
- Moviéndonos en la dirección **opuesta** al gradiente descendemos hacia el punto más bajo.
- Si la **pendiente** es más pronunciada, la magnitud del gradiente será mayor, y daremos pasos más grandes (si la tasa de aprendizaje es constante).

En un terreno complicado con múltiples mínimos locales, es posible que el descenso del gradiente encuentre un **mínimo local** en lugar del **mínimo global**.

### **Ejemplo Numérico Simplificado**
Supongamos que tenemos una función de pérdida simplificada:

$$
\mathcal{L}(w) = (w - 3)^2
$$

Queremos minimizar esta función. Calculemos la derivada con respecto a $w$:

$$
\frac{d\mathcal{L}}{dw} = 2(w - 3)
$$

Para aplicar el descenso del gradiente, debemos ajustar el valor de $w$:

$$
w \leftarrow w - \eta \cdot \frac{d\mathcal{L}}{dw}
$$

Por ejemplo, si $\eta = 0.1$ y empezamos con un valor inicial $w_0 = 0$:

- Paso 1: $\frac{d\mathcal{L}}{dw} = 2(0 - 3) = -6$
- Actualización: $w_1 = 0 - 0.1 \cdot (-6) = 0.6$

En el siguiente paso, se recalcula la derivada para el nuevo valor de $w$ y se repite el proceso, acercándonos gradualmente al valor $w = 3$, que minimiza la función de pérdida.

## Referencias
### Notas relacionadas
- **Nota:**[[Derivadas y extremos de funciones multi variables]]
	- **Relacion-Reflexion:** De esta nota podemos sacar varias conexiones, la primera es el gradiente, herramienta matematica principal que se utiliza en esta nota, basicamente nos mide la pendiente en cada direccion por lo cual podemos saber para donde movernos
		- Tambien, en esta nota vemos los extremos, que justamente es lo que estamos buscando aqui, un extreno global.
		- La duda que tengo es como se encuentra uno global y no el local