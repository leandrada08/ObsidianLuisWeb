



## Transformaciones 2D
![[Pasted image 20240410111024.png]]
### Traslacion
La traslación es una transformación básica que puede ser especialmente interesante, ya que puede ocurrir a lo largo de una dirección paralela al plano del sensor. Esto significa que simplemente veríamos un punto moverse hacia adelante y hacia atrás en el plano de la imagen. 
Si un punto $x$ se mueve, después de un cierto tiempo, por una cantidad $t$, su efecto en el espacio de la imagen es un desplazamiento similar. En un sistema de coordenadas homogéneas, el punto $x'$ resultante se convierte en $x' = x + tx$ e $y' = y + ty$. En coordenadas homogéneas aumentadas, $\bar{x}' = (x', y', 1)$.
*La traslación es simplemente la suma vectorial entre el vector que identifica $x$ y $t$.* 


Al considerar los vectores aumentados, debemos vincular los dos vectores con una matriz $2 \times 3$ para obtener un vector $x'$ en coordenadas absolutas. Para obtener el punto $\bar{x}'$, debemos multiplicar por una matriz $3 \times 3$. Esta representación en coordenadas absolutas nos permite conservar la linealidad de la trasformación en el espacio homogéneo. En la matriz $3 \times 3$ están fijados 7 elementos (0 y 1), y solo los elementos de la tercera columna permanecen libres: $tx$ y $ty$.
![[Pasted image 20240410110159.png]]
- La matrix $I$ es la matriz identidad de 2x2
- El vector $0^T$ es un vector de 0 de 1x2
- La t es un vector columna de la traslacion

### Roto-Traslacion
La siguiente transformación es la roto-traslación, que podemos ver como una combinación de una transformación de traslación más una rotación. Estamos rotando el cuerpo rígido en un ángulo $\theta$ y luego moviéndolo hacia adelante. Todos los puntos del objeto están experimentando lo que se llama una transformación euclidiana, es decir, una roto-traslación.
Primero rotamos el objeto mediante la matriz de rotación $R$ y luego lo trasladamos hacia adelante.
La matriz $R$ es una matriz ortonormal, por lo que cambia ambas coordenadas del punto del objeto en el plano. El determinante de $R$ es 1, siendo ortonormal, y el producto de $R$ y su transpuesta $R^{T}$ será la matriz identidad. Al pasar a coordenadas homogéneas, todavía tendremos una matriz 3D, en la cual hay tres parámetros de libertad sobre 9: $tx$, $ty$ y $\theta$. De este vector de traslación, se podría extraer una medida.
![[Pasted image 20240410110326.png]]

### Cambio de escala
Otra transformación es la similitud, donde además de la rotación puede haber un cambio de escala mediante un factor $s$. Simplemente se modifican los elementos de la submatriz $R$, que se convierte en $sR$, donde aparecen los elementos $a$ y $b$. En este caso se pierde la ortonormalidad (ya que $a^{2} + b^{2}$ será diferente de 1). Esta transformación mantiene invariable el ángulo de rotación. La traslación mantiene todas las dimensiones (ángulos y lados), la rotación mantiene las mismas formas pero modifica la orientación. La transformación de similitud, sin embargo, también modifica las dimensiones debido al factor de escala $s$.
![[Pasted image 20240410110433.png]]
### Affine
Una transformación afín modifica la forma de la primitiva geométrica, dejando inalterado solo el paralelismo y las líneas rectas.
![[Pasted image 20240410110552.png]]
### Proyeccion
  
La transformación de proyección es una operación crucial en la geometría de la visión por computadora y la computación gráfica. Se utiliza para proyectar puntos tridimensionales en un espacio real a un plano de imagen bidimensional, simulando así la forma en que una cámara captura una escena tridimensional en una imagen bidimensional.

Esta transformación se describe típicamente mediante una matriz de 9 elementos, de los cuales 8 son parámetros libres. Estos parámetros controlan cómo se mapean los puntos tridimensionales al plano de imagen. Es importante destacar que, a diferencia de las transformaciones anteriores, la transformación de proyección es lineal solo para las coordenadas homogéneas. Esto significa que las coordenadas homogéneas resultantes del punto proyectado se pueden obtener mediante una operación matricial lineal.

En esta transformación, la información de profundidad se pierde, ya que solo se conservan las coordenadas bidimensionales en el plano de imagen. Por lo tanto, no se puede reconstruir completamente la escena tridimensional a partir de la imagen proyectada sin información adicional.

El modelo de la cámara, que describe cómo la cámara captura una escena, se representa mediante una matriz 3D de 9 elementos. Estos elementos de la matriz controlan varios aspectos de la proyección, como la posición y orientación de la cámara, así como las propiedades ópticas de la lente. A menudo, esta matriz no se proporciona directamente y debe determinarse experimentalmente utilizando técnicas de calibración de cámara.

Los enlaces debidos a la traslación serán dados por los primeros dos elementos de la tercera columna, los de la rotación, por la submatriz 2x2 (en la esquina superior derecha), y así sucesivamente. El fabricante no proporciona esta matriz, por lo que es necesario obtenerla experimentalmente. Por lo tanto, obtener el modelo será igual a querer identificar esos nueve elementos de la matriz en cuestión.
![[Pasted image 20240410110954.png]]
![[Pasted image 20240410111002.png]]
## Transformaciones 3D
En el espacio 3D, se mantienen las mismas ideas, pero aumentando el número de parámetros libres y las dimensiones de las matrices. Por ejemplo, para la traslación, los elementos libres serán solo tx, ty y tz, presentes en la cuarta columna. En el espacio 3D, para contemplar todas las rotaciones, necesitamos los tres ángulos de Euler, por lo que las coordenadas independientes son seis (tx, ty, tz y los tres ángulos). El espacio 3D esquematiza la escena real.

### Rotacion 3D
Imagina que tienes un sistema de coordenadas tridimensional con ejes x, y, y z. Quieres rotarlo desde un punto de origen O a otro punto C, donde está ubicada una cámara. El objetivo es comprender qué combinación de rotación y traslación se necesita para ir de O a C. Por ahora, nos enfocaremos solo en la rotación.

Digamos que inicialmente los puntos O y C coinciden, por lo que ignoraremos la traslación y nos centraremos solo en la rotación. Una razón común para rotar el sistema de coordenadas es alinear un eje del sistema con algún aspecto importante de la escena, como el eje de simetría de una lente de la cámara.

Ahora, supongamos que tienes un punto (x, y, z) en el sistema de coordenadas original y deseas transformarlo en el punto (x2, y2, z2) en el sistema de coordenadas rotado. El primer ángulo que consideramos es φ, que representa la rotación alrededor del eje z. Esta rotación ocurre en el plano xy. Para describir esta rotación en un espacio bidimensional, utilizamos una matriz 2x2, pero dado que estamos trabajando en 3D, necesitamos una matriz 3x3. La matriz de rotación 2D se encuentra en la parte superior izquierda de la matriz 3x3. La tercera fila y columna de la matriz permanecen sin cambios, ya que no se altera la tercera dimensión.

La segunda rotación, alrededor del eje x2, se realiza con el ángulo θ. Esta rotación afecta al plano y2-z2. Como la componente x del punto no cambia, la primera fila y columna de la matriz de rotación son (1, 0, 0). Luego, agregamos la matriz de rotación 2D anteriormente establecida, pero esta vez cambiamos φ por θ.

Finalmente, realizamos una última rotación alrededor del nuevo eje z3, con un ángulo Ψ. La matriz resultante de esta rotación completa es idéntica a la primera, pero con el ángulo modificado. La rotación completa se obtiene multiplicando las matrices en el orden en que se realizaron: RΨ, Rφ y Rθ. Con estos ángulos variando dentro de ciertos rangos, podemos definir completamente cualquier rotación en el espacio tridimensional.