# Sistema de control



## Definiciones generales
### Sistema ki 
Un sistema es un conjunto de elementos en interracion dinamica organizados en funcion de un objetivo
#### Partes de un sistema
- Elementos
- Interaccion
- Organizacion
- Finalidad
#### Clasificacion de sistemas
-  En función del tiempo: en estático o dinámico.
-  En función del tipo de variables: en continuos, de eventos discretos o mixto.
- En función de la certeza de las variables: en determinista o estocástico.
- En función de la distribución de los componenetes: en paralelo o secuenciales.



El sistema existe en un entorno y puede sividirse en subsistema
![[Pasted image 20220823103930.png]]



### Modelo
Se entiende por modelo de un sistema a una representación abstracta y consistente dentro de un marco experimental o analítico que representa al sistema real simplificado (dentro de ciertos límites) en un lapso de tiempo en la extension espacial propia del sistema
#### Modelo Analitico:
Es el modelo teorico obtenido a partir de leyes
#### Modelo Experimental
Es el modelo obtenido en base a mediciones y suele ser un prototipo a pequenia escala


### Ingenieria de sistemas
Es el conjunto de conocimientos y de técnicas que permiten aplicar el saber cientifico a la utilización de la materia y de las fuentes de
energía, mediante invenciones o construcciones útiles para el hombre


### Teoría de Sistemas
Se entiende como TEORIA de SISTEMAS a la disciplina que trata sobre las propiedades generales y leyes de los sistemas


### Sistemas de Control
Teoría de Sistemas de Control es la disciplina que trata sobre las
propiedades generales y leyes de los sistemas sometidos a acciones de control


### Accion de Control
Se llama Acción de Control a las correcciones necesarias sobre
variables accesibles de un sistema a controlar con la finalidad que
alcance un objetivo deseado
#### Variables accesibles:
Son las variables que podemos controlar, tambien llamadas VARIABLES MANIPULABLE
#### Variables Controladas
Son las variables de salidas que requerimos darle un valor especifcado

### Definicion de un sistema de control ki 
Un Sistema de Control es aquel sistema en el que alguno de los
elementos posee o presenta una dada inteligencia que permite
alcanzar un objetivo que es, matemáticamente, mantener
determinadas variables del sistema dentro de valores especificados


### Subsistema de un sistema de control ki 
- **Sensores:** Uno o mas elemento de medicion, en nuestro caso, mide la salida y ve nos devuelve una respuesta en la entrada en base a esa medicion
-  **ACTUADORES:** Uno o mas sistema de accion. En nuestro caso, actua sobre la variable de entrada
-  “**CONTROLADOR:** Elemento de inteligencia y correcion del sistema.
- **PLANTA:** Parte de un equipo, tal vez un conjunto de los elementos de una maquina que funcionan juntos y cuyo objetivo es efectural una operacion en particular. En nuestra materia se le llamara planta al objeto fisico que se va a controlar


### Funcionamiento de un sistema de control
Operativamente los sensores sirven para chequear el estado de funcionamiento del sistema y envían esa información al controlador. El controlador analiza los valores recibidos desde los sensores, los compara con los valores deseados y elabora una acción que se envía al sistema de actuación. Finalmente el sistema de actuación acciona sobre el proceso hasta alcanzar el objetivo adecuadamente.


### Definicion de cibernetica
Cibernética es la ciencia que estudia los sistemas de construcción,
control y manejo de máquinas a partir de las analogías entre éstas y el
sistema nervioso del ser humano y de los animales


### Definicion de automatica
Automática es la disciplina que trata de métodos y procedimientos
cuya finalidad es la sustitución del operador humano por un
operador artificial en la ejecución de una tarea física y mental
previamente programada
#### Automatismo:
acción de implantar la automática en la industria.
#### Automata:
instrumento, aparato o estructura que encierra dentro de si los mecanísmos necesarios para realizar ciertas acciones programadas.


### Categoria de variables en un sistema de control: ki 
- Variables controladas: Cantidad o condicion que se mide y controla
- Variables manipuladas: Cantidad o condicion que se modificada por el controlador para afectar el valor de la  variable controlada
- Perturbaciones: variables de entrada que no podemos controlar






## Automatizacion y clasificacion de los sistemas de control
### Diferencia entre sistema de control y automatizacion
1) Mientras en la automatización el trayecto de actuación se repite una y otra vez, en un sistema de control automático NO NECESARIAMENTE se recorre el mismo trayecto de actuación.
2) La automatización por si sola no contempla la capacidad de cambiar sus acciones en función del entorno o situación. Por el contrario un sistema de control automático esta dotado de la capacidad inteligente de tomar decisiones según la situación que se presente.

### Caracteristicas de un sistema de control
- Estabiliza el sistema ante perturbaciones.
- Hace que el sistema evolucione en el tiempo atendiendo consignas.
- Consigue un comportamento óptimo con respecto a algún índice de calidad.
- Logra un comportamiento robusto.
- Consigue un comportamiento global fiable y tolerante a fallos.
- Tiene capacidad de adaptarse a cambios en la dinámica del proceso.
- Dispone de capacidad de aprendizaje ante dadas circunstancias.


### Sistema de control manual y automatico ki 
Si el ser humano es uno o mas de los elementos del sistema “Sistema de Control Manual”. En el caso de que el humano no participe del sistema de control y su función “Sistema de Control Automático”.



### Control de seguimiento y control regulatorio ki 
El término “**control regulador**” se utiliza para referirse a los sistemas diseñados para eliminar la acción de las perturbaciones y mantener asi el producto según lo especificado por la referencia.
Cuando resulta que la “perturbación” más importante es la referenciase dice entonces que es “**control de seguimiento**"


### Control a lazo abierto ki 
Los sistema en los cuales la salida no tiene efecto sobre la accion de control se denominan *sistemas de contro de lazo abierto*. La presicion del sistema depende de la calibracion. Ante la presencia de perturbaciones, estos sistemas no realizan la tarea deseada.Su accionar se fundamenta en que se asumen 2 items:
-  Se considera que la planta es perfectamente conocida (modelo exacto).
-  se considera que las perturbaciones seran mínimas o nulas.
Si se cumplen las 2 condiciones citadas (situación muy difícil), una vez ajustado el controlador, la variable de salida se mantendrá en el valor deseado.


### Control Realimentado o Feedback ki 
En el control “Feedback” o “Realimentado se mide la variable de salida o variable controlada, esta medición es llevada a la entrada para compararla con el valor deseado o entrada; la diferencia entre ambas (error) es utilizad por un dispositivo (controlador), que toma la mejor decisión a los fines de mantener las variables controladas en el valor adecuado. En la practica usaremos indistintamente los terminos *control realimentado o de lazo cerrado*




### Control Precalculada o Feedforward
Consiste en medir las perturbaciones y anularlas (compensarlas) antes de que la variable controlada se desvíe del valor deseado, sólo compensa la perturbación medida dejando las otras sin atender (es un sistema a lazo abierto para las restantes perturbaciones), es por ello que se lo utiliza acompaniado de una lazo de realimentacion


### Control Analogico y Digital
#### Control analogico
Las variables son continuas en el tiempo y los sistemas se modelan con ecuaciones diferenciales ordinarias.
#### Control digital
Las variables son discontinuas o discretas en el tiempo y los sistemas se representan mediante ecuaciones de diferencias.
#### Las ventajas más significativas de los controladores digitales frente a los analógicos son:
 - Los controladores digitales pueden realizar cálculos muy complejos a una velocidad muy alta y con el grado de exactitud que se necesite, con un coste relativamente reducido
- Los controladores digitales son mucho más versátiles, simplemente cambiando el programa de aplicación, se pueden modificar absolutamente las operaciones a realizar.


### Tipos de procesos
#### Procesos localizados
Se puede llevar a cabo en pequenias areas de operacion
#### Procesos distribuidos
Desarrollados en areas geograficas extensas


### Control de procesos localizados
En un comienzo se utilizaba un controlador para cada subproceso, luego se comenzo a utilizar una computadora para que controle todos los procesos a la vez, se la llamo **Control centralizado, CCS** o **Control Digital Directo, DDC**, esta tenia un incoveniente cuando ocurria un problema con esta computadora, por lo que se hizo un sistema controladores individuales para cada proceso y una computadora que controle todos los controladores, a este control se lo llamo **Control Computarizado Distribuido, DCC** o **Control Descentralizado, DCS**


### Control de procesos
El control de procesos se refiere a un sistema de control que supervisa algun proceso de producción industrial. Esto se consigue monitoreando y ajustando los parámetros de control. En el control de procesos industriales el control regulador es el predominante.


### Control de movimiento
El control de movimiento es un término ampliamente utilizado para describir el control de sistemas electromecánicos con elementos en movimiento. Lo que se persigue es un movimiento preciso de un objeto físico mediante un control a lazo cerrado de todo el sistema. El control de movimiento es fundamentalmente un control de seguimiento de la entrada o refencia ya que lo buscado es que la salida reproduzcla la entrada.


### Variables de estado
Podemos analizar un sistema con una ecuacion diferencial de orden N o por N ecuaciones diferenciales de orden 1, entonces, diremos que cada variable de cada una de estas ecuaciones son las variables de estados
Cada una de estas ecuaciones diferencias nos dice como se comporta cada elemento almacenador de energia, por lo tanto con el analisis por variables de estado podemos analizar el funcionamiento de cada elemento almacenador de energia y no solo con la salida



## Ingenieria de control moderna
### Teoria de control moderna
La tendencia moderna es mas compleja pero es mas precisa. Los sistemas complejos pueden tener multiples entradas y multiples salidas al igual que pueden ser variantes en el tiempo. Esta nueva aproximacion se basa en el concepto de estado.

### Estado
Conjunto de variables mas pequenias, de forma que el conocimiento de estas variables en t=t0 junto con el con el conocimiento de la entrada para t>t0 determina completamente el comportamiento del sistema para cualquier t>t0.

### Variables de estado
Son el menor numero de variable de un sistema dinamico necesarias para determinar un estado. Estas no necesitan ser fisicamente medibles o cantidades observables 

### Vector de estado
Vector que contiene a las variables de estado de un sistema dinamico

### Espacio de estado
Espacio cuya dimensiones son las variables de estado

### Ecuaciones en el espacio de estado
Tenemos 3 tipos de variables; variables de entrada, variables de salida y variables de estado. 
los sistemas dinamicos deben contener elementos que recuerden los valores, los integradores en un sistema de control en tiempo continuo sirven como dispositivo de memoria. Asi las salidas de los integradores sirven como variable de estado. El numero de variables de estado para definir completamente la dinamica del sistema es igual al numero de integradores que aparezcan en el mismo. Entonces el sistema se puede describir con las siguiente ecuaciones:
#### Ecuacion de estado x'(t)=f(x,u,t)
![[Pasted image 20221007191445.png|400]]
#### Ecuaciones de salida y(t)=f(x,u,t)
![[Pasted image 20221007191525.png|400]]
Donde x son las variables de estado y u las variables de entrada
#### Linealizando las anteriores ecuaciones
$x'(t)=A(t).x(t)+B(t).u(t)$
$y(t)=C(t).x(t)+D(t).u(t)$
Donde:
A(t) matriz de estado
B(t) matriz de entrada
C(t) matriz de salida
D(t) matriz de transmision directa
![[Pasted image 20221007191829.png|600]]

### Correlacion entre funciones de transferencia y ecuaciones en el espacio de estados
Sea la funcion de transferencia de un sistema: $$G(s)=\frac{Y(s)}{X(s)}$$
Trabajando en el espacio de estados llegamos a que: $$G(s)=C.(sI-A)^{-1}.B+D$$
O escrito de otra manera: $$G(s)=\frac{Q(s)}{|sI-A|}$$
Entonces podemos ver que los valores propios de A son identicos a los polos de G(s)

### Matriz de transferencia
Definida para un sistema de control con multiples entradas y salidas, sea la matrices de entrada y salidas respectivamente U(s) y Y(s), entonces: $$Y(s)=G(s).U(s)$$ Donde $G(s)=C.(sI-A)^{-1}.B+D$


#### Referencia
- [[Realimentacion]]
- [[Diagrama de bloque]]
- [[Funcion de transferencia]]
- [[Respuesta en el tiempo]]
- [[Lugar geometrico de las raices]]