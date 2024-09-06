## Introduccion
-   Editores de código(Generalistas): Enfocados a multiples lenguajes. Se pueden potencial con extensiones o plugins. Por lo general son gratuitos.  Tenemos Pycharm VSCode, Atom, etc.
-   IDE (entornos de desarrollo integrado): Enfocado a un solo lenguaje y seguimiento a un solo proyecto. Por lo general son de pago 💸


## Editor de codigo VSCode 

### Agregar extensiones para VSCode.

-   Hay muchas extensiones para VSCode que hacen trabajar con datos más cómodo. ☁️
-   Se pueden instalar todas las extensiones directamente desde VSCode 😄.
-   Es recomendable activar la sincronización automática en la nube, para que siempre puedas tener tu entorno de trabajo en cualquier lugar. Lo puedes contectar con tu cuenta de GitHub 🤖
-   Hay extension para Python que incluye muchas funcionalidades 🔥.
-   MagicPython sirve mucho para darle formato a Python y que sea más legible.
-   Las extensiones de Icon sirven para diferenciar tipos de archivos. 📁
-   Rainbow Brackets sirve para cambiar los colores de los paréntesis y no tener errores 🌈.
-   Remote Development te descarga múltiples extensiones que te sirven trabajar de manera remota. 🌎

### Uso de VSCode notebooks.

-   Esto es un nuevo estilo de Notebook, integrado dentro de VSCode 🤯.
-   Puedes abrir VSCode en una carpeta específica para ver todos los archivos dentro (y solo esos). Menos distracción que tener todo abierto con WSL. 😆
-   Podemos correr los archivos `.py` directamente en la terminal dando click en ▶️.
-   Con las extensiones que instalamos, podemos darle formato de manera automática a nuestro código 🐍.
-   Dentro de los Jupyter Notebook en VSCode podemos usar todas estas extensiones 💕. La extensión de los Notebooks es `.ipynb`. Podemos exportar los notebooks a texto plano!.

## Entorno de desarrollo con Anaconda.

### ¿Qué son los ambientes virtuales?

-   En la vida real, no vas a trabajar en un solo trabajo, si no en varios, y cada uno tendrá diferentes dependencias y requerimientos 🤔.
-   Cuando se actualizan o se cambia la configuración de las dependencias de un ambiente que tiene varios proyectos asociados puede haber errores 🛑.
-   Para poder separar proyectos, lo que hacemos es crear ambientes virtuales diferentes para cada proyecto. 🧠 Entonces la configuración y actualizaciones son para cada proyecto.
-   **Ambiente virtual**: Proyecto que puede tener sus propias dependencias, independientemente de las dependencias que tengan los demás proyectos (Scott Robinson y la gente de Real Python).

### Introduccion de conda

-   Conda: Programa diseñado para gestión de paquetes, dependencias y entorno para cualquier lenguaje: Python, R, Ruby, Lua, Scala, Java, JavaScript, etc. Además, es multiplataforma. 🖥️

#### Instalar Conda a través de la terminal.
-   Para instalar conda debes instalar anaconda (versión completa, metapaquete de ciencia de datos) o miniconda (versión mínima). 🐍
![[Pasted image 20240202094751.png|300]]
	
-   Para instalar conda:
    
    [Anaconda | Individual Edition](https://www.anaconda.com/products/individual)
    
    O bien hacer `wget -0 anaconda.sh https://repo.anaconda.com/archive/Anaconda3-2021.05-Linux-x86_64.sh`.
    
    Para instalar hacemos `bash anaconda.sh`. 🐍
    
-   Para abrir notebooks usamos `jupyter-notebook`o bien `jupyterlab`. Los notebooks que creas ahí también los puedes abrir en VSCode.
    
-   Para abrir VSCode en la carpeta en el que te encuentras, usas `code .`.
    

### Conda: crear y actualizar ambientes.

-   Conda tiene por defecto el ambiente `base` 😄
-   `conda env list` para ver todos tus ambientes existentes.
-   `conda create --name <nombre de="" ambiente=""> <paquete1>= <version1><paquete2>=</paquete2></version1></paquete1></nombre>` para crear un ambiente nuevo. 👀 Si no se especifica la versión, se toma la mas reciente.
-   `conda activjuate` para activar un ambiente.
-   `conda deactivate` para desactivar el ambiente actual.
-   `conda list` muestra todos los paquetes (y sus versiones) en tu ambiente. Para filtrar resultados (en ambientes grandes) `conda list pandas`.
-   `conda update <paquete></paquete>`para actualizar la versión mas reciente de un paquete.
-   `conda install <paquete>=</paquete>` para poner un paquete en una versión específica.

### Conda: Abrir VSCode Notebooks con tu ambiente creado.
**abrir tus notebooks desde VSCode con cualquier ambiente que hayas creado**.

Esto es muy sencillo y solo tiene una pequeña diferencia con la forma en la que abriste tu notebook en la clase de instalación de Conda. Sigue los pasos que te muestro a continuación para hacerlo.

1.  Abre Visual Studio Code desde tu terminal con el comando:

```bash
code .
```

**Recuerda que si usas WSL debes verificar en el cuadro verde de la parte inferior izquierda que efectivamente usas VSCode desde WSL**.

2.  Abre la notebook vacía que creaste anteriormente o crea una nueva llamada `Untitled.ipynb`.

![Notebook_abierta.png|500](https://static.platzi.com/media/user_upload/notebook_abierta-6ce05791-8423-4620-aff0-b2f7b7988f41.jpg)

3.  Asegura que tienes instalada la extensión de Python en VSCode que instalamos en una clase anterior.

**En caso de que uses WSL debe estar instalada en la versión de VSCode con WSL**.

![Extension_python.png|500](https://static.platzi.com/media/user_upload/extension_python-f7f76264-b121-4ca2-9588-2a431c815560.jpg)

4.  Regresa al notebook. En su esquina superior derecha aparecerá un botón que dice `Select Kernel`, `Not Started` o incluso puede aparecer en el botón que ya tienes un Kernel seleccionado. Da clic en él.

![Select_kernel.png|500](https://static.platzi.com/media/user_upload/select_kernel-134cc7c4-965e-4290-b586-f01fac5a9719.jpg)

5.  Al presionarlo aparecerán todas las opciones de Kernels/ambientes que están instalados en tu computadora. Elige el que prefieras. Para este ejemplo escogeré el ambiente `py39` que creamos en la clase anterior.

![Elegir_ambiente_py39.png|500](https://static.platzi.com/media/user_upload/elegir_ambiente_py39-129561ab-d095-409a-b059-599e9e11198b.jpg)

Al elegirlo notarás que aparece el nombre del ambiente en el botón que presionaste anteriormente en la parte superior derecha.

![Ambiente_seleccionado.png|500](https://static.platzi.com/media/user_upload/ambiente_seleccionado-ddad0cf6-0a1b-4ec4-8e77-5322c2a39f61.jpg)

Listo, has seleccionado un ambiente. De esta forma puedes cambiar de ambiente cuando lo necesites y abrir tus notebooks para trabajar con ellas en VSCode.

### ¿Qué hacer si no me aparecen los ambientes creados con Conda?

1.  Asegura tener instalada la extensión de Python. ¿Lo recuerdas? Porque con ello se instala todo lo necesario para que puedas escoger estos ambientes y usar Jupyter Notebooks.
    
2.  Si el problema todavía persiste recarga tu ventana de VSCode usando el comando `Ctrl + R` o `Command + R`.
    

**Si estás en WSL elige la versión de VSCode de WSL. Debe decir la versión de Linux que instalaste**.

![Reiniciar_vscode.png|500](https://static.platzi.com/media/user_upload/reiniciar_vscode-012271ad-415b-402f-9790-0fb52573e4da.jpg)

___

Ahora ya sabes cómo utilizar cualquier ambiente creado en Conda para usar tus Jupyter Notebooks. Entonces, avancemos a la siguiente clase para aprender a eliminar ambientes y librerías.

### Conda: Eliminar ambientes y librerías.

-   `conda remove <paquete></paquete>`para desinstalar un paquete en particular. 🗞️
-   `conda env remove --name <nombre>` para eliminar un ambiente completo 👀.
-   No se puede eliminar el ambiente en el que te encuentras 🤔. Necesitas desactivarlo primero.

### Conda: Comandos avanzados.

-   Para buscar paquetes:
	-   Podemos encontrar algún paquete que necesitemos en un _channel_ como _conda-forge._ 😯
	-   `conda install --channel <nombre del="" canal=""> <paquete></paquete></nombre>`**Para instalar un paquete especificando el channel de donde buscarlo.**
	-   `conda list --revision` **para listar las revisiones (modificaciones)** de tu ambiente; con esto puedes **volver en el tiempo** a un estado pasado de tu ambiente virtual.
		-   `conda install --revision <falg></falg>`para regresar a un estado pasado de tu ambiente. 🌲(falg es el numero de revision)
	-   `conda env export --no-build` Para compartir nuestro ambiente de conda y que otras personas puedan tener exactamente el mismo ambiente que tú.
		- Con este codigo compartimos los paquetes que tenemos instalados
	-   Con `conda env export --from-history --file <archivo>.yml` para compartir únicamente los paquetes que hayamos especificado explícitamente. 🔍. Esta es la mejor manera!(te genera un archivo .yml)
-   Para instalar un ambiente del cual recibimos un archivo `.yml` hacemos `conda env create --file <archivo>.yml` 🤯

## Acelerar la creación de ambientes virtuales con Mamba.

-   Mamba es una re-implementación de Conda (en C++) para la creación de ambientes virtuales. 🤖 Lo hace en paralelo, e incluye multiples optimizaciones que lo hacen más rápido.
-   Mamba funciona de la misma manera que conda en la línea de comandos. 🤔
-   `conda install --channel conda-forge mamba` para instalarlo.
-   Anaconda es muy tardado en multiples ocasiones (ya que es muy pesado). 😢

## Bonus: Divide y vencerás.

-   En proyectos grandes, es complicado mantener un ambiente virtual. 😵
-   Divide y vencerás es partir un problema difícil en partes pequeñas. Cada paquete se desarrolla a su propio ritmo (no siempre preocupándose de la compatibilidad con otros módulos). 🤯
-   Hay tres tipos de paquetes: Externos, Modelo y de Comunicación. Entonces podemos crear en multiples ambientes en un solo proyecto. 👀 Para esto, creamos una carpeta llamada `envs` y creamos tres documentos: external.yml, model.yml y comunicacion.yml.
-   `Snakemake` es un paquete que implementa muy bien este concepto. Es un motor de workflows 👀. Cada paso lo ejecuta con un ambiente específico.

[Snakemake - Snakemake 6.8.0 documentation](https://snakemake.readthedocs.io/en/stable/)

Un paquete que puede ser útil si tu ambiente está muy pesado es usar Mamba (puras serpientes jajajaja🤣)





# Complementos
### Instalar WSL: Usa Linux dentro de Windows.
¡Hola, te doy la bienvenida a esta clase! Estamos a punto de instalar **WSL (Windows Subsystem for Linux)**, una de las herramientas más poderosas que usarás en tu día a día en data science si utilizas Windows 10 o Windows 11. Esta herramienta te servirá para usar una línea de comandos de Linux desde Windows.

Para este punto de tu ruta de aprendizaje quizás ya tengas una terminal basada en Unix instalada en tu computadora. **Puedes saltarte esta clase de instalación si cumples alguno de los siguientes puntos:**

1.  Utilizas Linux como sistema operativo de forma nativa en tu computadora.
2.  Utilizaz macOS como tu sistema operativo.
3.  Ya cuentas con una terminal Linux con WSL en tu Windows.

Pero si utilizas Windows 10 u 11 y no tienes WSL y algún sistema de Linux instalado, sigue cada una de las instrucciones a detalle para instalarlo.

#### 1\. Instalar WSL y Ubuntu

**WSL** es la base con la que haremos que alguna distribución de Linux pueda correr dentro de nuestra computadora con Windows 10 u 11.

Una vez que se tenga instalada esta herramienta podrás instalar una gran variedad de distribuciones de Linux como Ubuntu o Debian. Para nuestro caso instalaremos **Ubuntu** que se instala por defecto al instalar WSL, pero puedes escoger alguna otra por la que tengas preferencia y ya sepas utilizar.

1.  Abre Windows PowerShell desde inicio en Widows. Para ello búscala y da clic derecho sobre **Ejecutar como Administrador**.

![Instalación de WSL _ Microsoft Learn — Mozilla Firefox 07_11_2022 03_32_44 p. m..png](https://static.platzi.com/media/user_upload/Instalaci%C3%B3n%20de%20WSL%20_%20Microsoft%20Learn%20%E2%80%94%20Mozilla%20Firefox%2007_11_2022%2003_32_44%20p.%20m.-c0a0736c-7c2f-458d-bcc6-f88a64f94bde.jpg)

2.  Dentro de Windows PowerShell escribe la siguiente instrucción y presiona la tecla **Enter**:
    
    wsl --install
    

![Seleccionar Administrador_ Windows PowerShell 07_11_2022 03_12_52 p. m..png](https://static.platzi.com/media/user_upload/Seleccionar%20Administrador_%20Windows%20PowerShell%2007_11_2022%2003_12_52%20p.%20m.-a60f5054-1b26-438f-9d1a-9478dc9075c0.jpg)

3.  Espera a que la barra de instalación llegue al 100% y presiona **Enter** nuevamente. Eso iniciará el proceso de instalación del sistema operativo Ubuntu.

![Seleccionar Administrador_ Windows PowerShell 07_11_2022 03_15_39 p. m..png](https://static.platzi.com/media/user_upload/Seleccionar%20Administrador_%20Windows%20PowerShell%2007_11_2022%2003_15_39%20p.%20m.-ce0cdf21-0a0d-4bc1-9b6f-4bf22070c3a0.jpg)

4.  Espera a que la barra de instalación de Ubuntu llegue al 100%.

![Seleccionar Administrador_ Windows PowerShell 07_11_2022 03_17_58 p. m..png](https://static.platzi.com/media/user_upload/Seleccionar%20Administrador_%20Windows%20PowerShell%2007_11_2022%2003_17_58%20p.%20m.-860c7daa-72e9-4ab9-aa66-784c7fb286e8.jpg)

5.  A finalizar la instación reinicia tu computadora para aplicar los cambios.
    
6.  Una vez que se haya reiniciado la computadora te llevará a configurar Ubuntu.
    

![Instalación de WSL _ Microsoft Learn — Mozilla Firefox 07_11_2022 03_20_26 p. m..png](https://static.platzi.com/media/user_upload/Instalaci%C3%B3n%20de%20WSL%20_%20Microsoft%20Learn%20%E2%80%94%20Mozilla%20Firefox%2007_11_2022%2003_20_26%20p.%20m.-4d1fbbdb-f513-4802-b999-dfd1263f21fc.jpg)

7.  Ingresa el **username** y **password** de tu preferencia. Recuerda muy bien tu password, ya que deberás usarla al utilizar el sistema operativo Ubuntu desde WSL.

![Instalación de WSL _ Microsoft Learn — Mozilla Firefox 07_11_2022 03_20_56 p. m..png](https://static.platzi.com/media/user_upload/Instalaci%C3%B3n%20de%20WSL%20_%20Microsoft%20Learn%20%E2%80%94%20Mozilla%20Firefox%2007_11_2022%2003_20_56%20p.%20m.-2dfb68e7-e772-4356-bf27-90979f565f06.jpg)

8.  Listo, ya tienes WSL y Ubuntu instalados en tu computadora con Windows. Para acceder nuevamente a Ubuntu en WSl abre la aplicación **Terminal** desde inicio de Windows.

![StackEdit — Mozilla Firefox 07_11_2022 03_52_34 p. m..png](https://static.platzi.com/media/user_upload/StackEdit%20%E2%80%94%20Mozilla%20Firefox%2007_11_2022%2003_52_34%20p.%20m.-6929eefa-6fc9-45a8-9f8f-08f490f76957.jpg)

9.  Dentro de **Terminal** da clic en la flecha hacia abajo y elige la opción de **Ubuntu**.

![Capturas 07_11_2022 03_54_02 p. m..png](https://static.platzi.com/media/user_upload/Capturas%2007_11_2022%2003_54_02%20p.%20m.-b0f7e6d9-b86e-4229-b0ac-4ac0d66d9789.jpg)  
![Fotos 07_11_2022 03_54_13 p. m..png](https://static.platzi.com/media/user_upload/Fotos%2007_11_2022%2003_54_13%20p.%20m.-8fc61f83-3c35-431a-9ce9-8270c5350961.jpg)

De igual forma te comparto la [documentación oficial de Microsoft](https://learn.microsoft.com/es-mx/windows/wsl/install) de este proceso y te invito a que dejes en los comentarios cualquier duda o inconveniente con el que te hayas topado al instalarlas para que podamos apoyarte.

#### 2\. Probar versión de Python 3

Al instalar Ubuntu tendremos una instalación de Python 3 disponible para utilizar. Probemos esta instalación:

1.  Abre **Windows Terminal** y dentro de las opciones escoge el Ubuntu que acabas de instalar.

![Fotos 07_11_2022 03_54_13 p. m..png](https://static.platzi.com/media/user_upload/Fotos%2007_11_2022%2003_54_13%20p.%20m.-8fc61f83-3c35-431a-9ce9-8270c5350961.jpg)

3.  Dentro de la terminal WSL con Ubuntu ejecuta el siguiente comando:

```bash
python3 --version
```

![Capturas 07_11_2022 03_56_26 p. m..png](https://static.platzi.com/media/user_upload/Capturas%2007_11_2022%2003_56_26%20p.%20m.-0cc32ffa-d4dd-474b-9cbd-ddf2aec97335.jpg)  
Como puedes observar en la imagen, esto te imprimirá en pantalla que cuentas con una versión de Python 3 lista para su uso.

#### 3\. Instalar pip3

Ahora es momento de instalar **pip3**, el manejador de paquetes y librerías más utilizado de Python. Con esta herramienta podrás instalar librerías de terceros como Pandas o Numpy que usarás en tu día a día en ciencia de datos.

1.  Ejecuta en tu terminal el siguiente comando para actualizar tu sistema operativo Ubuntu:

```bash
sudo apt update
```

![datormx@datormxPC_ ~ 07_11_2022 04_10_39 p. m..png](https://static.platzi.com/media/user_upload/datormx%40datormxPC_%20~%2007_11_2022%2004_10_39%20p.%20m.-0e6d76c1-98b4-4949-9d9c-ab16b649dd26.jpg)  
![datormx@datormxPC_ ~ 07_11_2022 04_10_55 p. m..png](https://static.platzi.com/media/user_upload/datormx%40datormxPC_%20~%2007_11_2022%2004_10_55%20p.%20m.-dfb23d2a-2adb-4d1c-9011-ad7587d047d3.jpg)

2.  Ejecuta en tu terminal el siguiente comando para instalar pip3:

```bash
sudo apt-get -y install python3-pip
```

![Fotos 07_11_2022 04_04_08 p. m..png](https://static.platzi.com/media/user_upload/Fotos%2007_11_2022%2004_04_08%20p.%20m.-5377b7d4-275f-4034-9d8c-08fa9a6b0665.jpg)  
![StackEdit — Mozilla Firefox 07_11_2022 04_17_14 p. m..png](https://static.platzi.com/media/user_upload/StackEdit%20%E2%80%94%20Mozilla%20Firefox%2007_11_2022%2004_17_14%20p.%20m.-f863be10-fb4f-42de-b83b-1722237348af.jpg)

3.  Prueba la instalación de pip3 una vez que haya terminado todo el proceso ejecutand el siguiente comando:

```bash
pip3 --version
```

![StackEdit — Mozilla Firefox 07_11_2022 04_18_29 p. m..png](https://static.platzi.com/media/user_upload/StackEdit%20%E2%80%94%20Mozilla%20Firefox%2007_11_2022%2004_18_29%20p.%20m.-03635dee-120f-438f-b80a-b423d86c7897.jpg)

Muy bien, con esto ya tienes instalado pip3 en tu terminal con Ubuntu.

#### 4\. Abrir VSCode desde WSL

Ahora que tienes tu sistema de Linux en Windows, Visual Studio Code lo abrirás de una forma un tanto distinta para que toda librería o configuración que instales en ese sistema funcione.

1.  Busca “Visual Studio Code” desde tu buscador de Windows y ábrelo dando clic en su ícono:

![buscar_vscode.png](https://static.platzi.com/media/user_upload/buscar_vscode-a86bb58b-6667-4566-a8ec-2bcdd9b776c6.jpg)

3.  Una vez abierto VSCode ve al panel izquierdo y da clic en el ícono de extensiones:

![extensiones.png](https://static.platzi.com/media/user_upload/extensiones-07c59cae-12a6-49e0-b4d7-b18b96ab41ae.jpg)

4.  Busca en el menú izquierdo la extensión **WSL** e instálala con el botón azul install:  
    ![datormx@datormxPC_ ~ 07_11_2022 04_26_19 p. m..png](https://static.platzi.com/media/user_upload/datormx%40datormxPC_%20~%2007_11_2022%2004_26_19%20p.%20m.-fcb6e290-38a6-4f29-b6ee-cb74c331cc09.jpg)
    
5.  Escribe el siguiente comando desde tu terminal para abrir VSCode en WSL:
    

```bash
code .
```

![vscode.png](https://static.platzi.com/media/user_upload/vscode-f72085e8-1e9f-4630-92f4-0e252d6b0783.jpg)

Este comando abrirá una versión de VSCode que correrá desde WSL con el sistema operativo Ubuntu. Esto puedes comprobarlo porque en la parte inferior izquierda de tu editor verás un recuadro verde que indica que estás en WSL y qué versión de Linux utilizas:

![vscode_wsl_indicacion.png](https://static.platzi.com/media/user_upload/vscode_wsl_indicacion-016c8a43-b561-46a9-9c46-807e9481da5b.jpg)

Excelente, ya está usando VSCode desde WSL. Recuerda que siempre debes abrir VSCode con el comando `code` desde tu terminal con WSL, de lo contrario te encontrarías utilizando la versión de tu sistema operativo Windows y no la de tu versión de Ubuntu Linux en WSL.
