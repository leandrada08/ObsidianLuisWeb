

## Google Colab

### Introduccion Google Colab
-   Es una herramienta basada en la nube que te permite trabajar en notebooks, y se guardan en tu cuenta de Google Drive 😃.
    
-   **Nube vs local**: 
	- Ambas son útiles, pero se diferencian en la configuración de entornos, ya que en la nube ya están precargadas, y de local tienes que configurarlo manualmente. 
	- Es diferente el tiempo de ejecución y la escalabilidad: la nube tiene más poder porque puedes rentarlo!. 💸
    
-   **Google Colab**: Servicio en la nube basado en Jupyter Notebooks, no requiere configuración y tiene un trabajo a nivel de archivo (el notebook es la base). 
	- Tiene uso de gratuito de GPUs y TPUs para correr modelos grandes. ☁️
    
-   Puedes acceder a Google Colab desde tu drive o desde el navegador.

- [[Reglas de Markdown]]
    
-   Las variables son persistentes (se conservan) entre celdas de código!. 🔥
    
-   Para llamar a la **línea de comandos**, debemos usar primero un signo de admiración `!` y luego un comando válido, por ejemplo `!pwd` o `!pip install session-info`.
    

### Ciencia de datos en Google colab

Google Colab incluye varias herramientas:

-   Podemos subir archivos a Colab para trabajar con ellos (también tienen datos de muestra) 🔢. Dándole click podemos previsualizar e incluso filtrar la tabla que hayamos subido.
-   Podemos montar nuestro Google Drive en nuestro Notebook, con lo que podremos trabajar con datos que estén en nuestro Drive. 🤓 Es lo más recomendable ya que los archivos no se eliminan al terminar la sesión.
-   Ya incluye multiples librerías (las mas usadas) como Matplotlib, Numpu, Pandas, Scipy, Seaborn, etc. 💫
-   Google Colaboratory tiene **code snipets**, para que puedas utilizarlo y agilizar tu trabajo 🤯.
-   Para abrir la paleta de comandos usamos Ctrl + shift + p. Es útil conocer los shortcuts más útiles para ser más ágil.

## Deepnote.

-   Deepnote es un servicio en la nube basado en Jupyter Notebooks. No requiere configuración y tiene un trabajo a nivel de **proyecto**. Tiene colaboración en tiempo real, integración con múltiples Apps y tiene acceso a una terminal o línea de comandos integrada 😎.
-   Tiene también variables de entorno y permite publicar proyectos (para construir portafolio). 🎉
-   Podemos correr y agregar lo mismo que en Colab, pero además podemos subir archivos que se quedan siempre en el proyecto.
-   Permite previsualizar los archivos CSV de manera muy bonita 😄.
-   Parte de lo poderoso de Deepnote es que podemos integrar muchas cosas 🔥.
-   No solo podemos agregar celdas de código y de texto, si no que en la opción de _Bloque_ vienen muchos más tipos, como input, chart, dataframe sql, etc 🤯. Puede crear gráficas de manera automática sin código!
-   Para acceder a los atajos de teclado usamos _Ctrl + i_.
-   También es importante resaltar que tenemos una terminal integrada 🤖.



## Resumen rapido

Comando para ejecutar en consola
``` Comando
python3 name_codigo.py
```

Comando para ejecutar tipos notebook en jupyter
``` Comando
jupyter-notebook
```