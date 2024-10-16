## Introducción

La clasificación de imágenes es un problema de visión por computadora donde se busca identificar qué hay en una imagen. Básicamente, se trata de tomar una imagen y etiquetarla con una categoría, como "gato", "perro" o "taza". A pesar de ser algo simple para los humanos, para un algoritmo es bastante complicado debido a la enorme cantidad de posibles variaciones.

#### **Ejemplo**  
Imagina que le damos una imagen de un gato a un programa de computadora. La computadora ve la imagen como una gran matriz de números que representan los colores de cada punto (píxel). Estos números van desde 0 hasta 255, dependiendo de cuán brillante es cada color (rojo, verde, azul). La tarea de la computadora es convertir todos esos números en una etiqueta, como "gato".

#### **Desafíos**  
¿Por qué es difícil? Porque hay muchas formas en que una imagen puede variar:

- **Punto de vista**: El objeto puede ser visto desde distintos ángulos.
- **Tamaño**: Un gato puede verse muy grande o muy pequeño en la imagen.
- **Forma**: Los objetos pueden cambiar de forma, como un perro sentado o corriendo.
- **Oclusión**: Parte del objeto puede estar oculta por otra cosa.
- **Iluminación**: La luz puede hacer que los colores de la imagen cambien.
- **Entorno**: El fondo puede distraer y mezclar los colores del objeto.
- **Variación entre objetos similares**: Por ejemplo, hay muchas razas de perros, y todas lucen diferentes.

Un buen clasificador tiene que ser capaz de ignorar estas variaciones y aún así reconocer correctamente el objeto.

