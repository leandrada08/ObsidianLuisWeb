

## Que es Google Colab?
Google Colab es una herramienta que te permite escribir, ejecutar y compartir código dentro de Google Drive. Funciona como un notebook de Jupyter almacenado en la nube, lo que significa que puedes ejecutar código Python sin necesidad de instalar nada en tu equipo. Cada notebook está compuesto por celdas que pueden contener código, texto, imágenes y más. 

Colab es una herramienta basada en la nube que te permite trabajar en notebooks, y se guardan en tu cuenta de Google Drive 😃. No requiere configuración y tiene un trabajo a nivel de archivo (el notebook es la base)
- Los notebooks en Colab también permiten agregar contexto alrededor del código mediante celdas de texto, que se formatean utilizando Markdown. Esto facilita agregar títulos, listas y fórmulas matemáticas. Para compartir tus notebooks, puedes hacerlo a través de Google Drive o exportarlos a GitHub, ya que se almacenan en formato compatible con Jupyter Notebook.
- Tiene uso de gratuito de GPUs y TPUs para correr modelos grandes. ☁️

## Como funciona Colab?
Colab se conecta a un entorno de ejecución basado en la nube, lo que te permite aprovechar cualquier funcionalidad de Python, incluyendo bibliotecas como Altair para crear visualizaciones interactivas. Además, puedes usar atajos como Mayús+Intro para ejecutar celdas de manera más rápida.
-   Las variables son persistentes (se conservan) entre celdas de código!. 🔥
Google Colab es compatible con varios proyectos interesantes en la web, como el proyecto Seedbank, donde puedes encontrar ejemplos prácticos de aprendizaje profundo, como la transferencia de estilo neuronal.


## Como usar Colab?


### **Creación de un nuevo Colab**
Puedes crear un nuevo notebook de Colab desde Google Drive, simplemente seleccionando "Nuevo" y luego buscando "Colaboratory" en el menú "Más". Una vez que el notebook está listo, puedes escribir código Python directamente en las celdas de código.
-   Para llamar a la **línea de comandos**, debemos usar primero un signo de admiración `!` y luego un comando válido, por ejemplo `!pwd` o `!pip install session-info`.
    

### Ciencia de datos en Google colab
Google Colab incluye varias herramientas:
-   Podemos subir archivos a Colab para trabajar con ellos (también tienen datos de muestra) 🔢. Dándole click podemos previsualizar e incluso filtrar la tabla que hayamos subido.
-   Podemos montar nuestro Google Drive en nuestro Notebook, con lo que podremos trabajar con datos que estén en nuestro Drive. 🤓 Es lo más recomendable ya que los archivos no se eliminan al terminar la sesión.
-   Ya incluye multiples librerías (las mas usadas) como Matplotlib, Numpu, Pandas, Scipy, Seaborn, etc. 💫
-   Google Colaboratory tiene **code snipets**, para que puedas utilizarlo y agilizar tu trabajo 🤯.
-   Para abrir la paleta de comandos usamos Ctrl + shift + p. Es útil conocer los shortcuts más útiles para ser más ágil.




### **Uso de Colab para Aprender Aprendizaje Automático**
- **Tutoriales de código**: Usaremos Colab para trabajar con fragmentos de código que representan distintos algoritmos y conceptos de aprendizaje automático. Aprenderás a modificar el código directamente en Colab.
  
- **Cuestionarios y evaluaciones**: Para afianzar los conceptos, habrá cuestionarios que te permitirán completar algunos ejercicios prácticos, ayudándote a entender mejor los fundamentos.

- **Entrenamiento de redes neuronales en la nube**: Colab te permitirá utilizar el poder de la nube para entrenar modelos de aprendizaje automático mucho más rápido, especialmente utilizando GPU. Esto acelerará el proceso de aprendizaje, ya que entrenar modelos en una computadora portátil podría tomar demasiado tiempo.

### **Análisis de Algoritmos y Visualización**
Colab también nos ayudará a visualizar cómo los algoritmos aprenden, permitiendo observar características clave del proceso de entrenamiento. Exploraremos aspectos como el impacto de la tasa de aprendizaje o la función de pérdida, lo que te permitirá comprender las implicaciones de los ajustes en los hiperparámetros.


### Consejos Colab

1. **Duración de la instancia**: Cada instancia de Colab permanecerá activa mientras interactúes con ella al menos una vez cada 90 minutos.
2. **Límite de tiempo**: Las instancias solo duran un máximo de 12 horas, así que asegúrate de descargar todos los archivos que necesites para evitar perderlos.
3. **Acceso a archivos**: Puedes acceder a los archivos en la máquina virtual de Colab haciendo clic en el ícono de la carpeta en el lado izquierdo de la pantalla.
4. **Directorio por defecto**: Todos tus archivos se guardan en `/content` por defecto.
5. **Ejecución de comandos bash**: Aunque Colab utiliza Python por defecto, puedes ejecutar cualquier comando de bash agregando un signo de exclamación (!) al inicio. Ejemplo: `!unzip archivo.zip -d carpeta_destino`.
6. **Descargar archivos**: Para descargar un archivo, haz clic en los tres puntos al lado del nombre del archivo y selecciona "Descargar".
7. **Subir archivos**: Para subir un archivo, haz clic en el ícono de la hoja con una flecha hacia arriba debajo de la sección "Archivos".
8. **Guardar cambios permanentes**: Si quieres guardar cambios en un Colab, selecciona "Archivo -> Guardar una copia en Drive" para crear una copia con tus modificaciones.
9. **Acelerar entrenamiento de redes neuronales**: Para acelerar el entrenamiento, activa una instancia con GPU. Ve a "Entorno de ejecución -> Cambiar tipo de entorno de ejecución" y selecciona "GPU" bajo "Acelerador de hardware".




## Referencias
### Notas relacionadas
- **Nota:**[[Reglas de Markdown]]
	- **Relacion-Reflexion:**