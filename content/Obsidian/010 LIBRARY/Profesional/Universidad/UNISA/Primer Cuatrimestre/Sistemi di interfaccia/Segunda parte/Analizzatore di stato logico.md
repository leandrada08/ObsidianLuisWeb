---
cards-deck: Profesional::Universidad::UNISA::Sistemi di interfaccia::Analizzatore di stato logico
---


## Introduccion
- **SUT:** Es el sistema bajo prueba, el dispositivo a analizar y que genera las señales digitales de entrada.
- **Fuente:** Es un generador de señales digitales utilizado para probar el analizador, no para analizar un SUT.
### Porque es necesario un analizador de estado logico?
- En circuitos digitales, *conocer los valores exactos de las tensiones no es crucial*; se busca determinar si caen en niveles lógicos alto (H) o bajo (L).
	- Por ejemplo un osciloscopio tiene 8 bit de resolucion, cuando un analizador de estado logico solo necesita 1 bit de solucion
- El *osciloscopio tiene limitaciones* para probar circuitos digitales debido a la *estabilidad de la imagen* y la *dificultad para extraer información lógica*.
- En sistemas digitales complejos, especialmente con microprocesadores, interesa conocer el valor lógico de *múltiples nodos simultáneamente*.
- El osciloscopio no es el instrumento más adecuado; se desarrollaron instrumentos como el analizador de estados lógicos (Logic Analyzer) para manejar información digital.

#### Cuando usar un osciloscopio
- Medicion analogica de pocas señales
- Se debe concoer amplitud, potencia, corriente y fase de una señal
- Tambien para efectuar medidas de tiempo de salida, para caracterizar la estabilidad, tiempo de setup o hold, retardo de propagacion
- Tambien nos sirve para encontrar anomalias transitorias como glitch, impulsos runt, transitorios de metaestabilidad

#### Cuando usar un analizador de estado logico
- Verificacion y debugging de funcionamiento de sitemas digitales.
- Visualizar muchas señales conteporaneamente e analizar sus relaciones temporales
- Algunos analizadores pueden resolver poblemas de glitch e violaciones del tiempo de hold e setup
- Detectar e analizar violaciones de timing e transistorios sobre el bus.
- Seguir la ejecucion de software embebido

## Analizador de estado logico
Los analizadores de estado logico:
- Tienen entre 34 y 136 canales.
- No miden detalles analogicos, detectan niveles de umbrales logicos

### Funcionamiento basico del analizar de estado logico
- Cuando el ingreso supera un tension dada, el nivel es alto o 1
- Cuando el ingreso es inferior a una tension dada, el nivel es bajo o 0
- El display da una forma de onda en funcion del tiempo similar a un diagrama temporal en un reporte tecnico o una simulacion
- Las señales estan relacionadas con el tiempo, por lo cual es posible analizar tiempo de hold, setup o longitud del impulso

#### Otras funcionamidades avanzadas
- Trigger sostificado que permite especificar condiciones de adquisicion
- Sonda de alta densidad y adaptibilidad que simplifican la conexion al sistema en prueba
- Capacidad de analidad que traduce los datos adquiridos en instrucciones del proceso y las relaciona con el codigo.

### Uso del analizador de estado logico
El uso del analizador de estado logico se divide en:
- Conexion
- Configuracion
- Adquisicion
- Analisis y visualizacion
![[Pasted image 20240207103202.png|400]]

#### Conexion
**SONDA:** Con esta se pueden conectar muchos pines a la vez y definir los niveles de umbrales de tension
Existen distintos tipos de sondas:
- *Para uso generar:* Se separan en cables para utiliza en punto a punto
- *De alta densidad:* Multicanal, se requieren conectar a un conector en una placa de circuito impreso.
- *De alta densidad a presion:* Son usadas en dispositivos sin conectores.
![[Pasted image 20240207103801.png|300]]
![[Pasted image 20240207103804.png|300]]

##### Observaciones
- La capacidad de la sonda tiende a aplanar la señal de salida, este aplanamiento ralentiza el transitorio en un tiempo $\Delta t$
![[Pasted image 20240207104053.png|300]]
- Esto puede evitar mediciones en el SUT a altas velocidades
- *Se debe usar adaptadores para compensar la carga*


#### Configuracion
##### Seleccion de la modalidad del clock
- En el dominio del tiempo
- En el dominio de datos

##### Seleccion del Trigger
- Se eligen las condiciones booleanas para la activacion del trigger
- Hay muchas elecciones de trigger que pueden generar distintos tipos de eventos, estos los veremos mas adelante


#### Adquisicion
##### Estado y tiempo
Es importante obtener informacion sobre los estados y el timing relacionado
- Si un analizador logico no tiene la capacidad de adquirir datos de timinng e de estados logicos de manera contemporaneo, sera dificil encontrar problemas en el sistema.
	- Algunos instrumentos necesitan de 2 sondas separadas para la adquisicion de informacion de timing y de estado, como se muestra en la figura acontinuacion.
		- Este tipo de dispositivo puede afeecta el valor de impedancia, por lo cual afecta la muestra
![[Pasted image 20240207112647.png|400]]
- Es mejor adquirir ambas informaciones en una misma sonda como se muestra en la siguiente figura
![[Pasted image 20240207112835.png|400]]

##### Memoria
Se analiza mas adelante
## ESTRUCTURA GENERAL DE UN ANALIZADOR DE ESTADOS LÓGICOS
- Conceptualmente, la estructura general de un analizador de estados lógicos es bastante simple, aunque su implementación resulta bastante compleja, especialmente debido a las altas prestaciones requeridas por las partes individuales que lo componen. Además, el uso de este instrumento no es inmediato, ya que requiere que el operador tenga un conocimiento adecuado tanto de las características del instrumento como, sobre todo, de la parte hardware y posiblemente del software del sistema bajo prueba.
- Un analizador de estados lógicos debe ser capaz de *capturar la actividad eléctrica de un número bastante elevado de nodos del circuito bajo prueba y transformar esta actividad en los dos estados lógicos, alto y bajo*(POD y clock). Mediante una cuidadosa selección, estos estados lógicos deben poder ser almacenados en una memoria interna(Memoria y trigger), desde donde pueden ser recuperados posteriormente para visualizarlos de la manera más adecuada para facilitar el análisis a realizar(Display).
- La estructura general de un analizador de estados lógicos se muestra en el diagrama de bloques de la figura 6.1.

![[Pasted image 20240117112537.png|400]]
Este esquema se ha simplificado intencionalmente para ilustrar solo las funciones esenciales realizadas por los diversos bloques presentes en estos instrumentos. Cada uno de estos bloques puede tener varias modalidades de funcionamiento; también son posibles diferentes tipos de interacciones, tanto entre los bloques del instrumento como con el circuito externo, que no se muestra en la figura 6.1.


### Bloque de Adquisición de Estados Lógicos
**Las líneas de entrada de un analizador de estados lógicos se agrupan físicamente en estructuras llamadas pods**. El bloque de adquisicion debe:
- *Convertir las señales de voltaje presentes en las líneas de entrada en niveles lógicos*
	- Tiene que elegir entre *diferentes posibilidades de rangos* dependiendo la situacion operativa
		- TTL o ECL predefinido
		- Pero si tenemos componentes CMOS genericos debemos definir nosotros
	- Osea que debe definir los umbrales relativos
	- *Es posible fijar distintos rangos para distintintos PODs*
- Este bloque tambien *contiene reloj y cualificadores*
#### POD
- *Numero limitado de lineas(8 o 16)*
	- *Se referencias cada entrada con el numero del pod y su orden adentro*
- Tiene una linea de referencia a massa la cual sirve para varias el rango para cada pod
- Al igual que cualificadores
	



### Generador de Clock
La función principal de la señal de reloj consiste en *controlar la adquisición del estado lógico presente en las líneas de entrada*. En general, el reloj se obtiene mediante una función predeterminada de cierto número de señales, tanto internas como externas al instrumento; por lo tanto, se adquiere un nuevo estado lógico solo cuando estas señales se encuentran en una condición predefinida.

El clock se puede dividir dependiendo el funcionamiento de un analizador de estados lógicos en dos modos fundamentales:
- En el dominio del tiempo.
- En el dominio de datos o estados.


#### En el dominio del tiempo
*El reloj es una señal periódica generada internamente en el instrumento* y, suponiendo que se cumplan algunas condiciones, la adquisición de un nuevo estado lógico y, eventualmente, su almacenamiento ocurre en cada periodo de reloj. Dado que el periodo de reloj es conocido, *los datos almacenados permiten obtener la evolución temporal de los estados lógicos* presentes en el circuito bajo prueba.
En el *dominio del tiempo, el funcionamiento del analizador es*, por lo tanto, *muy similar al de un osciloscopio digital de múltiples trazas*; sin embargo, hay una diferencia sustancial: en el eje y del analizador no se muestran los valores de voltaje, sino solo niveles lógicos.
A menudo, este *modo de funcionamiento se denomina asíncrono, ya que la adquisición de los estados lógicos de entrada ocurre a una frecuencia fija, independientemente del funcionamiento del sistema bajo prueba.*
En la figura 6.2 se muestra de manera cualitativa la evolución temporal de algunas señales de entrada y la señal de reloj generada internamente en el instrumento. Como se muestra en la figura 6.2, cada pulso de reloj provoca la adquisición de los valores lógicos presentes en las líneas de entrada.
![[Pasted image 20240117112729.png|400]]

#### En el dominio de datos
En el funcionamiento en el dominio de los datos, quizás de mayor interés para el análisis de sistemas a microprocesador,**las señales que activan la adquisición son externas al instrumento** y, por lo general, **son suministradas por el mismo sistema bajo prueba**. El caso más típico se presenta cuando *la adquisición es comandada por un flanco de una señal externa*, para la cual no se requiere ninguna condición de periodicidad. En principio, esta señal puede ser cualquiera, pero a menudo es una señal de control generada por el sistema en examen.

A menudo, *este modo de funcionamiento del analizador de estados se denomina síncrono*, ya que *hay una sincronización entre el funcionamiento del sistema bajo prueba y la adquisición de datos* por parte del instrumento.
![[Pasted image 20240117112736.png|400]]
En la figura 6.3 se muestra de manera cualitativa las evoluciones de algunas señales de entrada y la orden externa y no periódica del reloj. En la figura, se supone activo cada flanco de la orden de reloj; también se muestran los valores lógicos adquiridos.

#### Dominio de datos vs dominio de tiempo
- Reloj interno (asíncrono): Es útil cuando se requiere analizar la evolución temporal de las señales o detectar problemas de temporización. Al ser periódico permite obtener el comportamiento en el tiempo.
- Reloj externo (síncrono): Es recomendable para analizar sistemas con un reloj o señal de control claramente definidos, como microprocesadores. Sincroniza la adquisición con el sistema bajo prueba.
- Para analizar buses paralelos de alta velocidad, es mejor un reloj interno a una frecuencia superior a la del bus. Permite detectar glitches y problemas de temporización.
- En sistemas asíncronos complejos conviene el reloj interno para obtener el diagrama temporal de las señales.
- Si se quiere relacionar señales síncronas con asíncronas, se puede usar el reloj externo para las síncronas y otro interno para las asíncronas.
- Para analizar solo secuencias específicas de un sistema síncrono, el reloj externo permite concentrarse en esos eventos.
En resumen, el reloj interno es mejor para análisis temporal, y el externo cuando se quiere sincronía con un sistema con señal de reloj clara. La elección depende del tipo de sistema y del análisis a realizar.

### Memoria de Adquisición de Estados Lógicos
La memoria es el corazon del instrumento, aqui se destinan todos los datos.
- La memoria de este instrumento tiene la capcidad de memorizar a la frecuencia de muestreo del instrumento
- El numero de canales e la profundida de la memoria son fundamentales a la hora de elegir un analizador de estado logico
	- El numero de canales de nuestro analizador logico esta directamente asociado al numero de señales que quiero adquirir. Ademas son necesarias otras señales como el clock, activiacion, etc.
	- La duracion de nuestra adquisicion determina la profundida de memoria necessaria del analizador de estado logico y es muy importante en la adquisicion de timing
		- El tiempo total de adqisicion disminuye con el aumente de la frecuencia de muestro
		- Aumentar el muestreo(mas tiempo) aumenta la probabilidad de capturar un error y la causa
Grafica de memoria:
![[Pasted image 20240207113502.png]]


*Cuando se cumplen ciertas condiciones(TRIGGER)*, los valores lógicos adquiridos se almacenan en una memoria interna, que está organizada como un búfer circular (first-in-first-out *FIFO*); cuando *la memoria está llena, la adquisición de un nuevo estado resulta en la pérdida del estado almacenado más antiguo*. El nivel lógico de cada línea de datos de entrada se expresa mediante un solo bit, por lo que la longitud de...
![[Pasted image 20240207115334.png|400]]
- La frecuencia del reloj de muestreo define intervalos regulares en los cuales se adquiere el estado lógico de las señales.
- Las transiciones (flancos) que ocurren en las señales se capturan en uno de estos instantes de muestreo.
- Pero la transición puede haber ocurrido en cualquier momento dentro del intervalo entre dos muestreos consecutivos.
- Cuanto más corto sea el intervalo de muestreo (mayor frecuencia de reloj), mejor será la resolución temporal para detectar transiciones rápidas.
- Los buses y sistemas modernos operan a velocidades muy altas, por lo que requieren analizadores con resoluciones temporales muy finas (intervalos de muestreo muy pequeños) para poder capturar adecuadamente sus señales.
- En instrumentos mas actuales captura informacion sobre un intervalo mas amplio cerca del punto del trigger
#### Qualificadores
No todos los modelos de analizadores de estados lógicos están equipados con qualificadores. Conceptualmente, el qualificador realiza una función muy simple: **cuando está activo, habilita la adquisición del estado lógico de entrada, que es comandado por la señal de reloj**. La función realizada por el qualificador puede representarse mediante el esquema de la figura 6.4, en la cual se supone que el qualificador está activo a un nivel lógico alto. 
Existen, por supuesto, otras soluciones de circuito que permiten diferentes condiciones de activación del qualificador. *Este comando también se puede obtener a partir de una única señal externa o combinando lógicamente varias señales externas con modalidades especificadas por el operador*.
![[Pasted image 20240117112846.png|400]]

#### El Evento de Trigger

El generador de trigger **permite obtener una alta capacidad de selección de datos para almacenar**. En la figura 6.5 se muestra una esquematización simplificada de la función principal realizada por este bloque.
Numerosas condiciones pueden activar el trigger de un analizador de estado logico. Aqui hay una lista de elecciones de trigger:
- *Palabra:* Se especifica una palabra en codigo binario o hexa
- *Campo:* Un evento que ocurre entre 2 valores
- *Contadores:* Se detectan eventos guiado por un contador programado
- *Señales:* Una señal externa como un reset del sistema.
- *Glitch:* Guiados por glitch
- *Timer:* Se especifica un intervalo de tiempo entre 2 eventos o una duracion de un unico evento 
![[Pasted image 20240117115358.png|400]]

- **Cuando los datos adquiridos toman una configuración lógica bien específica (patrón)**, fijada durante la preparación del instrumento, **se genera un evento de trigger y se realiza una acción de almacenamiento**, también especificada durante la preparación.
- La organización del almacenamiento es muy similar a la de los osciloscopios digitales. Dado que la memoria funciona como un búfer circular, aparte de un transitorio inicial, *siempre se almacenan N estados lógicos*; sin embargo, *se puede fijar el número M de estados lógicos que deben almacenarse después del evento de trigger*. Por lo general, se tienen las siguientes tres opciones:
	- **M=N:** En memoria *se conservan N estados lógicos sucesivos al evento de trigger* (condición de post-trigger). Esta opción *se denomina START, RIGHT, o con nombres similares*; el significado de los términos es obvio teniendo en cuenta que el evento de trigger provoca, desde un punto de vista lógico, el inicio del almacenamiento.
	- **M=0:** En memoria *se conservan N estados lógicos todos anteriores al evento de trigger (condición de pre-trigger)*. Esta opción *se llama STOP, END, LEFT o similares*; el evento de trigger provoca el fin del almacenamiento.
	- **M=N/2:** En memoria *se conservan N/2 estados lógicos que preceden y N/2 que siguen al evento de trigger*. Esta opción *se suele llamar CENTER*. En algunos modelos más recientes de analizador, es posible dividir la memoria de manera que el número de estados previos al evento de trigger sea diferente al de los estados posteriores (M$\neq$N/2).

![[Pasted image 20240207115351.png|400]]
![[Pasted image 20240117115402.png|400]]

## Instrumentos integrados para buscar fallos analogicos-digitales
A la hora de buscaar errores hay que tener en cuenta tambien el dominio analogico.
- En sistema actuales tan rapidos, la caracteristicas analogicas de señales digitales tienen un impacto mayor sobre el sistema
- Las aberraciones de las señales pueden tener fuentes de problemas analogicos
	- Desacoplamiento de impedancias, efectos en las lineas de trasmision y otros
- Tambien pueden tener otrigen digital como la violacion de setup o hold
- Una vez que descubrimos la aberracion de la señal con un analizador, es tarea del osciloscopio en tiempo real adquirir abudante informacion sobre este error en el tiempo
	- Suele ser mas rapido esto con osciloscopio
	- Es por esto que una correcta solucion de problemas requiere instrumentos y metodos que puedan operar en ambos dominios

## Actividad de Visualización

Los datos conservados en la memoria de adquisición pueden visualizarse e analizarse utilizando diferentes modos. Esta informacion peude ser visualizada en formato de onda de tiempo o tambien en terminos de instrucciones relacionadas con el codigo fuente.

### Lista de Valores Lógicos Codificados:
   En esta modalidad, los datos adquiridos se presentan de forma codificada y se agrupan según un criterio definido por el operador durante la configuración del instrumento. En la pantalla aparece una lista de valores lógicos, agrupados y codificados en binario, octal, hexadecimal, u otro formato según la configuración del instrumento.
   El seguimiento de las instrucciones en tiempo real permite entender las transiciones del bus y establecer cuales instrucciones son leidas atravez del mismo.
![[Pasted image 20240207122849.png|400]]
![[Pasted image 20240207122519.png|400]]


### Formas de Onda de Evolución Lógica:
   En esta modalidad, se presentan en la pantalla las formas de onda que representan la evolución lógica de las tensiones en las líneas de entrada. Si la adquisición de datos se realiza en el dominio del tiempo, esta representación proporciona la evolución temporal de la actividad lógica de las señales de entrada. Cuando el instrumento opera en el dominio de los datos, las formas de onda representan solo la sucesión de estados lógicos; cualquier vínculo temporal entre los diferentes estados visualizados se establece basándose en el conocimiento que va más allá de los datos adquiridos.
   - Se podria decir que esta visualizacion es analoga a la de un display de un osciloscopio
   - Tambien se agregan impulsos del clock de muestreo. 
Es importante destacar que, incluso cuando el eje de las abscisas está calibrado en unidades temporales, la forma de onda visualizada en la pantalla representa siempre y solo la evolución de los valores lógicos de las tensiones de entrada y no los valores reales asumidos por esas tensiones, como ocurre en un osciloscopio normal.
![[Pasted image 20240207122458.png|400]]
![[Pasted image 20240207122519.png|400]]
- Comunemnte se usa la forma de onda para:
	- Diagnostico de problemas de timing en el hardware del SUT
	- Comparar el correcto funcionamiento respeecto a un resultado mostrado en una simulacion o en un documento tecnico
	- Medida de caracteristicas de timing del hardware
		- Condiciones de accesos multiples
		- Retardo de propagacion
		- Ausencia o presencia de impulsos




### Otros modos
Los datos almacenados también pueden visualizarse en otros modos, que no están disponibles en todos los modelos de este tipo de instrumentos. Estas modalidades suelen permitir obtener una indicación global del funcionamiento del sistema bajo prueba, de la cual se puede deducir directamente la corrección o incorrección del mismo. También se puede deducir la necesidad de análisis adicionales, generalmente realizados utilizando los modos de visualización antes descritos o la adquisición de estados lógicos adicionales.

Por ejemplo, es posible representar en el eje de las ordenadas los valores codificados de los datos adquiridos relacionados con un cierto grupo de líneas de entrada, mientras que en el eje de las abscisas se muestra la sucesión temporal de estos estados.

Es importante destacar que estos modos de visualización proporcionan información valiosa para analizar el funcionamiento del sistema bajo prueba y detectar posibles actividades no previstas.

### Medicion automatica
Se realizan con operaciones de “arrastras y soltar”. Ofecen la posibilidad de seguir la medicion sobre datos adquiridos por el analizador de estado logico.
- Ofrece la posibilidad de medidas analogicas seguidas con un osciloscopio como la frcuencia, periodo, longitud de los inpulsos, duty cycle, etc.
- Las mediciones automáticas proporcionan resultados rápidos y exhaustivos, ya que dan rápidamente resultados de intervalos de muestreo muy amplios


### 6.4.1 Opciones para Simplificar el Análisis de los Datos Presentados

Un analizador de estados lógicos a menudo presenta opciones que permiten simplificar el análisis del funcionamiento del sistema bajo prueba, algunas de las cuales se presentan en los siguientes ejemplos.

**Ejemplo: Programa Aplicativo para un Sistema a Microprocesador**
Normalmente, un programa aplicativo para un sistema a microprocesador está formado por un conjunto de módulos fuente. Esto permite escribir y ensamblar por separado las diferentes partes del programa, que luego se reunirán y cargarán en la memoria del sistema mediante el cargador. Este enfoque ofrece ventajas como:

- La corrección de un error en un módulo fuente solo requiere el reensamblaje del módulo afectado en lugar de todo el programa.
- Los diferentes módulos fuente pueden ser escritos por diferentes programadores, acelerando así la escritura del programa.
- Es posible evitar la inserción de subrutinas de uso común en el programa fuente. Basta con que estas estén disponibles como módulos objeto en una biblioteca que se cargará en memoria, junto con otros módulos necesarios, mediante el cargador.

La posición que ocupan los diferentes módulos objeto proporcionados por el ensamblador en memoria no puede ser definida por el programador, ya que este no conoce la extensión de los otros módulos ni el orden en que se depositarán en memoria. Por lo tanto, el programador solo dispone de un listado en el que la dirección inicial de la subrutina de interés no coincide con la dirección real de memoria en la que se coloca esa subrutina.

La efectiva colocación de los diferentes módulos del programa la realiza el cargador en la fase de enlace, durante la cual los diferentes módulos se conectan entre sí para obtener el programa completo. La dirección real de memoria en la que comienza una subrutina específica depende de la colocación de todos los demás módulos del programa.

Por ejemplo, la dirección de la primera ubicación de la subrutina RADIX podría ser 435EH, mientras que en el listado disponible dicha subrutina comienza en la dirección 0000H. Sin embargo, el instrumento permite establecer una correspondencia simple entre las direcciones disponibles en el listado y las reales. Para esto, se asocia una etiqueta, como RADIX, a la dirección 435EH. Los siguientes direcciones después de RADIX y menores que una dirección que se puede especificar se visualizan de la siguiente manera:

- RADIX + 0000H
- RADIX + 0001H

De esta manera, se indican explícitamente tanto la subrutina examinada como el desplazamiento relativo a la dirección de referencia, que coincide con la dirección indicada en el listado disponible.

Esto facilita considerablemente el análisis de los datos presentados por el instrumento.

**Ejemplo: Opción para Visualización de Operaciones de Escritura y Lectura**
Otra opción que facilita el análisis de un sistema a microprocesador es la siguiente. Supongamos que se tiene la señal digital RIW que controla las operaciones de escritura y lectura de datos en una memoria RAM. Cuando se realiza una lectura, la señal RIW está en nivel lógico alto, mientras que en una operación de escritura asume el nivel lógico bajo; en la pantalla del analizador se presentan entonces dos valores lógicos 1 y 0 asumidos en estas dos situaciones. Para permitir que el operador asocie directamente un valor lógico a la actividad ejecutada, evitando así interpretaciones incorrectas de los resultados, el instrumento puede configurarse de modo que, en lugar de los valores 0 y 1, se visualicen las indicaciones WRITE y READ.


## 6.5 Detección de Glitches

Como se ilustró anteriormente, cuando el analizador funciona en el dominio del tiempo, los datos se adquieren en instantes equidistantes por una cantidad que puede elegirse entre un conjunto finito de valores. Un evento de naturaleza impulsiva (glitch) que se manifiesta entre dos instantes de muestreo sucesivos, es decir, dentro de un período de clock, no puede ser adquirido. En un circuito electrónico digital que contiene elementos de memoria, este impulso de voltaje puede alterar, a menudo de manera impredecible, el estado del circuito.

El instrumento puede revelar la presencia de un glitch solo cuando opera en el dominio del tiempo. En los instrumentos menos recientes, a menudo esta capacidad de detección requiere el uso de dos líneas distintas para cada entrada en la que se debe verificar la aparición de glitches; por lo tanto, se reduce a la mitad el número de entradas que el instrumento puede manejar.

Existen varios circuitos electrónicos que permiten detectar la presencia de impulsos de voltaje dentro de un intervalo de muestreo. Generalmente, un glitch se detecta comprobando si, dentro de un período de clock, ocurre tanto un flanco de subida como un flanco de bajada, independientemente del orden en que ocurran estos flancos.

El esquema de principio de un detector de glitch se muestra en la fig. 6.7. 
![[Pasted image 20240117115749.png]]

Este circuito se restablece y habilita con cada pulso de clock utilizando comandos no mostrados en el esquema. Los dos latches de la fig. 6.7 son sensibles uno a los flancos de subida y el otro a los flancos de bajada. La salida de la puerta AND asume un nivel lógico alto solo cuando ambos latches han sido activados, es decir, solo cuando se ha producido un glitch.

En la fig. 6.8 se muestran las formas de onda de la señal de entrada, del clock y de la traza visualizada tanto en presencia como en ausencia del control de glitch.

![[Pasted image 20240117115806.png]]

Como se puede observar en el último diagrama temporal de la fig. 6.8, la indicación de la presencia de un glitch ocurre convencionalmente en correspondencia con los pulsos de clock utilizando, por ejemplo, un segmento discontinuo o un asterisco u otro elemento distintivo. Es decir, no se proporciona ninguna indicación sobre las características del glitch (instante en que ocurre, duración, amplitud, ...); solo se indica su manifestación dentro de un período específico de clock.

Es importante tener en cuenta que los dispositivos utilizados en un detector de glitch, al tener que ser sensibles a tiempos de transición muy reducidos, deben estar fabricados con componentes muy rápidos.

A veces, para simplificar la estructura del instrumento y contener su costo, que suele ser bastante elevado, solo algunas líneas de entrada están equipadas con detectores de glitch. Además, las líneas en las que se debe realizar el control de glitches deben especificarse durante la fase de preparación del instrumento.

# Italiano

### Funzionamento di base dell'analizzatore di stato logico
- Quando l'ingresso supera una tensione data, il livello è alto o 1
- Quando l'ingresso è inferiore a una tensione data, il livello è basso o 0
- Il display fornisce una forma d'onda in funzione del tempo simile a un diagramma temporale in un report tecnico o una simulazione
- I segnali sono correlati al tempo, quindi è possibile analizzare il tempo di hold, il setup o la lunghezza dell'impulso
#### Altre funzionalità avanzate
- Trigger sofisticato che permette di specificare condizioni di acquisizione
- Sonda ad alta densità e adattabilità che semplificano la connessione al sistema in prova
- Capacità di analisi che traduce i dati acquisiti in istruzioni del processo e le relaziona al codice.


### Uso dell'analizzatore di stato logic #tarjeta-anki 
L'uso dell'analizzatore di stato logico si divide in:
- Connessione
- Configurazione
- Acquisizione
- Analisi e visualizzazione
![[Pasted image 20240207103202.png|400]]
#### Connessione
**SONDA:** Con questa si possono connettere molti pin contemporaneamente e definire i livelli di soglia di tensione
Ci sono diversi tipi di sonde:
- *Per uso generale:* Si separano in cavi per utilizzo punto a punto
- *Ad alta densità:* Multicanale, devono essere collegati a un connettore su una scheda di circuito stampato.
- *Ad alta densità a pressione:* Usate in dispositivi senza connettori.
![[Pasted image 20240207103801.png|300]]
![[Pasted image 20240207103804.png|300]]
##### Osservazioni
- La capacità della sonda tende ad appiattire il segnale di uscita, questo appiattimento rallenta il transitorio di un tempo $\Delta t$
![[Pasted image 20240207104053.png|300]]
- Ciò può impedire misurazioni sul SUT ad alte velocità
- *È necessario utilizzare adattatori per compensare il carico*
#### Configurazione
##### Selezione della modalità del clock
- Nel dominio del tempo
- Nel dominio dei dati
##### Selezione del Trigger
- Vengono scelte le condizioni booleane per l'attivazione del trigger
- Ci sono molte scelte di trigger che possono generare diversi tipi di eventi, li vedremo più avanti
#### Acquisizione
##### Stato e tempo
È importante ottenere informazioni sugli stati e sul timing correlato
- Se un analizzatore logico non ha la capacità di acquisire contemporaneamente dati di timing e di stati logici, sarà difficile individuare problemi nel sistema.
	- Alcuni strumenti richiedono 2 sonde separate per l'acquisizione di informazioni di timing e di stato, come mostrato nella figura seguente.
		- Questo tipo di dispositivo può influenzare il valore dell'impedenza, quindi influenzare il campione
![[Pasted image 20240207112647.png|400]]
- È meglio acquisire entrambe le informazioni in una stessa sonda come mostrato nella seguente figura
![[Pasted image 20240207112835.png|400]]
##### Memoria
Sarà analizzata più avanti.
^1707321132132




## 6.1 Perché è necessario un analizzatore di stato logico #tarjeta-anki  
- Nei circuiti digitali, conoscere i valori esatti delle tensioni non è cruciale; si cerca di determinare se cadono nei livelli logici alto (H) o basso (L).
- L'oscilloscopio ha limitazioni nel testare circuiti digitali a causa della stabilità dell'immagine e della difficoltà nell'estrazione di informazioni logiche.
- Nei sistemi digitali complessi, specialmente con microprocessori, è interessante conoscere il valore logico di nodi multipli contemporaneamente.
- L'oscilloscopio non è lo strumento più adatto; sono stati sviluppati strumenti come l'analizzatore di stati logici (Logic Analyzer) per gestire informazioni digitali.
#### Quando utilizzare un oscilloscopio
- Misurazione analogica di pochi segnali
- Deve conoscere l'ampiezza, la potenza, la corrente e la fase di un segnale
- Anche per effettuare misurazioni di tempo di uscita, per caratterizzare la stabilità, il tempo di setup o hold, il ritardo di propagazione
- Ci serve anche per trovare anomalie transitorie come glitch, impulsi runt, transitori di meta-stabilità
#### Quando utilizzare un analizzatore di stato logico
- Verifica e debugging del funzionamento di sistemi digitali.
- Visualizzare molti segnali contemporaneamente e analizzare le loro relazioni temporali
- Alcuni analizzatori possono risolvere problemi di glitch e violazioni del tempo di hold e setup
- Rilevare e analizzare violazioni di timing e transitori sul bus.
- Seguire l'esecuzione del software incorporato
^1707321132144



## 6.2 Evoluzione degli Analizzatori di Stato Logico 

- I primi analizzatori si concentravano sull'hardware, con clock periodici per acquisire dati ad alte frequenze (fino a GHz), costosi ma efficienti.
- La diffusione dei microprocessori ha cambiato le esigenze, richiedendo la verifica dell'hardware e del software.
- Gli analizzatori adatti per i microprocessori devono catturare l'attività logica di molti nodi contemporaneamente.
- Con l'aumento della velocità dei circuiti, alcuni analizzatori consentono di catturare segnali con clock di diverse centinaia di MHz.
In sintesi, gli analizzatori di stati logici si sono evoluti per adattarsi alle mutevoli esigenze dei circuiti digitali, essenziali per la verifica dell'hardware e del software in sistemi complessi, specialmente con microprocessori.


## 6.3 STRUTTURA GENERALE DI UN ANALIZZATORE DI STATI LOGICo #tarjeta-anki 
Concettualmente, la struttura generale di un analizzatore di stati logici è piuttosto semplice, anche se la sua implementazione è piuttosto complessa, specialmente a causa delle elevate prestazioni richieste dalle singole parti che lo compongono. **Inoltre, l'uso di questo strumento non è immediato, poiché richiede che l'operatore abbia una conoscenza adeguata sia delle caratteristiche dello strumento che, soprattutto, della parte hardware e possibilmente del software del sistema sotto esame.**
![[Pasted image 20240117112537.png]]
Un analizzatore di stati logici deve essere in grado di catturare l'attività elettrica di un numero abbastanza elevato di nodi del circuito sotto esame e trasformare questa attività nei due stati logici, alto e basso. Mediante una selezione attenta, questi stati logici devono poter essere memorizzati in una memoria interna, da dove possono essere recuperati successivamente per visualizzarli nel modo più adatto per facilitare l'analisi da eseguire.
La struttura generale di un analizzatore di stati logici è mostrata nel diagramma a blocchi della figura 6.1.
Questo schema è stato intenzionalmente semplificato per illustrare solo le funzioni essenziali svolte dai vari blocchi presenti in questi strumenti. Ciascuno di questi blocchi può avere diverse modalità di funzionamento; sono possibili anche diversi tipi di interazioni, sia tra i blocchi dello strumento che con il circuito esterno, che non viene mostrato nella figura 6.1.
^1707321132148




### 6.3.1 Blocco di Acquisizione di Stati Logic #tarjeta-anki 
**Le linee di ingresso di un analizzatore di stati logici sono fisicamente raggruppate in strutture chiamate pods**. Il blocco di acquisizione deve:
- Convertire i segnali di tensione presenti nelle linee di ingresso in livelli logici
  - Deve scegliere tra diverse possibilità di range a seconda della situazione operativa
    - TTL o ECL predefinito
    - Ma se abbiamo componenti CMOS generici dobbiamo definire noi
  - Quindi deve definire le soglie relative
  - È possibile fissare diversi range per diversi PODs
- Questo blocco contiene anche clock e qualificatori
#### POD
- Numero limitato di linee (8 o 16)
  - Ogni ingresso è referenziato con il numero del pod e il suo ordine interno
- Ha una linea di riferimento a massa che serve per variare il range per ogni pod
- Così come i qualificatori
^1707321132152




### 6.3.2 Generatore di Clk #tarjeta-anki 
La funzione principale del segnale di clock consiste nel *controllare l'acquisizione dello stato logico presente nelle linee di ingresso*. In generale, il clock viene ottenuto mediante una funzione predefinita di un certo numero di segnali, sia interni che esterni allo strumento; quindi, viene acquisito un nuovo stato logico solo quando questi segnali si trovano in una condizione predefinita.
Il clock può essere diviso a seconda del funzionamento di un analizzatore di stati logici in due modalità fondamentali:
- Nel dominio del tempo.
- Nel dominio dei dati o degli stati.
#### Nel dominio del tempo
*Il clock è un segnale periodico generato internamente nello strumento* e, supponendo che siano soddisfatte alcune condizioni, l'acquisizione di un nuovo stato logico e, eventualmente, il suo salvataggio avviene ad ogni periodo di clock. Poiché il periodo di clock è noto, *i dati memorizzati consentono di ottenere l'evoluzione temporale degli stati logici* presenti nel circuito in prova.
Nel *dominio del tempo, il funzionamento dell'analizzatore è* quindi *molto simile a quello di un oscilloscopio digitale a traccia multipla*; tuttavia, c'è una differenza sostanziale: sull'asse y dell'analizzatore non vengono visualizzati i valori di tensione, ma solo i livelli logici.
Spesso, questo *modo di funzionamento è chiamato asincrono, poiché l'acquisizione degli stati logici di ingresso avviene a una frequenza fissa, indipendentemente dal funzionamento del sistema in prova.*
Nella figura 6.2 è mostrata in modo qualitativo l'evoluzione temporale di alcuni segnali di ingresso e del segnale di clock generato internamente nello strumento. Come mostrato nella figura 6.2, ogni impulso di clock provoca l'acquisizione dei valori logici presenti nelle linee di ingresso.
![[Pasted image 20240117112729.png|400]]
#### Nel dominio dei dati
Nel funzionamento nel dominio dei dati, forse di maggiore interesse per l'analisi di sistemi a microprocessore,**i segnali che attivano l'acquisizione sono esterni allo strumento** e, in genere, **sono forniti dallo stesso sistema in prova**. Il caso più tipico si presenta quando *l'acquisizione è comandata da un fronte di un segnale esterno*, per il quale non è richiesta alcuna condizione di periodicità. In principio, questo segnale può essere qualsiasi, ma spesso è un segnale di controllo generato dal sistema in esame.
Spesso, *questo modo di funzionamento dell'analizzatore di stati è chiamato sincrono*, poiché *vi è una sincronizzazione tra il funzionamento del sistema in prova e l'acquisizione dei dati* da parte dello strumento.
![[Pasted image 20240117112736.png|400]]
Nella figura 6.3 è mostrata in modo qualitativo l'evoluzione di alcuni segnali di ingresso e l'ordine esterna e non periodica del clock. Nella figura, si suppone attivo ogni fronte dell'ordine di clock; vengono inoltre mostrati i valori logici acquisiti.
#### Dominio dei dati vs dominio del tempo
- Clock interno (asincrono): È utile quando è necessario analizzare l'evoluzione temporale dei segnali o rilevare problemi di temporizzazione. Essendo periodico, consente di ottenere il comportamento nel tempo.
- Clock esterno (sincrono): È consigliabile per analizzare sistemi con un clock o segnale di controllo chiaramente definiti, come i microprocessori. Sincronizza l'acquisizione con il sistema in prova.
- Per analizzare bus paralleli ad alta velocità, è meglio un clock interno a una frequenza superiore a quella del bus. Consente di rilevare glitch e problemi di temporizzazione.
- In sistemi asincroni complessi, conviene il clock interno per ottenere il diagramma temporale dei segnali.
- Se si vogliono relazionare segnali sincroni con asincroni, si può utilizzare il clock esterno per i sincroni e un altro interno per i asincroni.
- Per analizzare solo sequenze specifiche di un sistema sincrono, il clock esterno consente di concentrarsi su quegli eventi.
In sintesi, il clock interno è migliore per l'analisi temporale, e quello esterno quando si desidera la sincronia con un sistema con segnale di clock chiaro. La scelta dipende dal tipo di sistema e dall'analisi da effettuare.
^1707321132156








### 6.3.3 Memoria di Acquisizione degli Stati Logic #tarjeta-anki  
La memoria è il cuore dello strumento, qui vengono destinati tutti i dati.
- La memoria di questo strumento ha la capacità di memorizzare alla frequenza di campionamento dello strumento.
- Il numero di canali e la profondità della memoria sono fondamentali nella scelta di un analizzatore di stato logico.
   - Il numero di canali del nostro analizzatore logico è direttamente associato al numero di segnali che voglio acquisire. Inoltre, sono necessari altri segnali come il clock, l'attivazione, ecc.
   - La durata della nostra acquisizione determina la profondità di memoria necessaria dell'analizzatore di stato logico ed è molto importante nell'acquisizione di timing.
      - Il tempo totale di acquisizione diminuisce con l'aumento della frequenza di campionamento.
      - Aumentare il campionamento (più tempo) aumenta la probabilità di catturare un errore e la sua causa.
Grafico della memoria:
![[Pasted image 20240207113502.png]]
*Quando si verificano determinate condizioni (TRIGGER)*, i valori logici acquisiti vengono memorizzati in una memoria interna, organizzata come un buffer circolare (first-in-first-out *FIFO*); quando *la memoria è piena, l'acquisizione di un nuovo stato comporta la perdita dello stato più vecchio memorizzato*. Il livello logico di ciascuna linea di dati in ingresso è espresso mediante un singolo bit, quindi la lunghezza di...
![[Pasted image 20240207115334.png|400]]
- La frequenza del clock di campionamento definisce intervalli regolari in cui viene acquisito lo stato logico dei segnali.
- Le transizioni (flanci) che si verificano nei segnali vengono catturate in uno di questi istanti di campionamento.
- Tuttavia, la transizione potrebbe essere avvenuta in qualsiasi momento all'interno dell'intervallo tra due campionamenti consecutivi.
- Più breve è l'intervallo di campionamento (maggiore è la frequenza del clock), migliore è la risoluzione temporale per rilevare transizioni rapide.
- I bus e i sistemi moderni operano a velocità molto elevate, quindi richiedono analizzatori con risoluzioni temporali molto precise (intervalli di campionamento molto piccoli) per poter catturare adeguatamente i loro segnali.
- Negli strumenti più recenti, viene acquisita informazione su un intervallo più ampio vicino al punto di trigger.
#### Qualificatori
Non tutti i modelli di analizzatori di stato logico sono dotati di qualificatori. Concettualmente, il qualificatore svolge una funzione molto semplice: **quando è attivo, abilita l'acquisizione dello stato logico in ingresso, che è comandato dal segnale di clock**. La funzione eseguita dal qualificatore può essere rappresentata mediante lo schema della figura 6.4, in cui si suppone che il qualificatore sia attivo a un livello logico alto. 
Esistono, naturalmente, altre soluzioni di circuito che consentono diverse condizioni di attivazione del qualificatore. *Questo comando può anche essere ottenuto da un singolo segnale esterno o combinando logicamente vari segnali esterni con modalità specificate dall'operatore*.
![[Pasted image 20240117112846.png|400]]
#### L'Evento di Trigger
Il generatore di trigger **permette di ottenere un'ampia capacità di selezione dei dati da memorizzare**. Nella figura 6.5 è mostrata una schematizzazione semplificata della funzione principale svolta da questo blocco.
Numerose condizioni possono attivare il trigger di un analizzatore di stato logico. Ecco un elenco di scelte di trigger:
- *Parola:* Viene specificata una parola in codice binario o esadecimale.
- *Campo:* Un evento che si verifica tra 2 valori.
- *Contatori:* Vengono rilevati eventi guidati da un contatore programmato.
- *Segnali:* Un segnale esterno come un reset di sistema.
- *Glitch:* Guidati da glitch.
- *Timer:* Viene specificato un intervallo di tempo tra 2 eventi o una durata di un singolo evento.
![[Pasted image 20240117115358.png|400]]
- **Quando i dati acquisiti assumono una configurazione logica ben specifica (modello)**, fissata durante la preparazione dello strumento, **si genera un evento di trigger e si esegue un'azione di memorizzazione**, anch'essa specificata durante la preparazione.
- L'organizzazione della memorizzazione è molto simile a quella degli oscilloscopi digitali. Dato che la memoria funziona come un buffer circolare, a parte un transitorio iniziale, *vengono sempre memorizzati N stati logici*; tuttavia, *è possibile impostare il numero M di stati logici da memorizzare dopo l'evento di trigger*. Di solito, ci sono tre opzioni:
	- **M=N:** In memoria *vengono conservati N stati logici successivi all'evento di trigger* (condizione post-trigger). Questa opzione *viene chiamata START, RIGHT o con nomi simili*; il significato dei termini è ovvio considerando che l'evento di trigger provoca, dal punto di vista logico, l'inizio della memorizzazione.
	- **M=0:** In memoria *vengono conservati N stati logici tutti precedenti all'evento di trigger (condizione pre-trigger)*. Questa opzione *si chiama STOP, END, LEFT o simili*; l'evento di trigger provoca la fine della memorizzazione.
	- **M=N/2:** In memoria *vengono conservati N/2 stati logici che precedono e N/2 che seguono l'evento di trigger*. Questa opzione *solitamente si chiama CENTER*. In alcuni modelli più recenti di analizzatori, è possibile dividere la memoria in modo che il numero di stati precedenti all'evento di trigger sia diverso dal numero di stati successivi (M$\neq$N/2).
^1707321132161






## 6.4 Attività di Visualizzazion #tarjeta-anki 
I dati conservati nella memoria di acquisizione possono essere visualizzati e analizzati utilizzando diversi modi. Queste informazioni possono essere visualizzate in formato di forma d'onda temporale o anche in termini di istruzioni correlate al codice sorgente.
### Elenco dei Valori Logici Codificati:
   In questa modalità, i dati acquisiti vengono presentati in modo codificato e raggruppati secondo un criterio definito dall'operatore durante la configurazione dello strumento. Sullo schermo appare un elenco di valori logici, raggruppati e codificati in binario, ottale, esadecimale o in un altro formato, a seconda della configurazione dello strumento.
   Il tracciamento delle istruzioni in tempo reale consente di comprendere le transizioni del bus e stabilire quali istruzioni vengono lette attraverso di esso.
![[Pasted image 20240207122849.png|400]]
![[Pasted image 20240207122519.png|400]]
### Forme d'Onda dell'Evoluzione Logica:
   In questa modalità, sullo schermo vengono presentate le forme d'onda che rappresentano l'evoluzione logica delle tensioni sulle linee di ingresso. Se l'acquisizione dei dati avviene nel dominio del tempo, questa rappresentazione fornisce l'evoluzione temporale dell'attività logica dei segnali di ingresso. Quando lo strumento opera nel dominio dei dati, le forme d'onda rappresentano solo la successione di stati logici; qualsiasi legame temporale tra i diversi stati visualizzati è stabilito basandosi sulla conoscenza che va oltre i dati acquisiti.
   - Si potrebbe dire che questa visualizzazione è analoga a quella di un display di un oscilloscopio
   - Vengono anche aggiunti impulsi del clock di campionamento.
È importante sottolineare che, anche quando l'asse delle ascisse è calibrato in unità temporali, la forma d'onda visualizzata sullo schermo rappresenta sempre e solo l'evoluzione dei valori logici delle tensioni di ingresso e non i valori reali assunti da tali tensioni, come avviene in un normale oscilloscopio.
![[Pasted image 20240207122458.png|400]]
![[Pasted image 20240207122519.png|400]]
- Comunemente si usa la forma d'onda per:
	- Diagnostica dei problemi di timing nell'hardware del SUT
	- Confrontare il corretto funzionamento rispetto a un risultato mostrato in una simulazione o in un documento tecnico
	- Misurare le caratteristiche temporali dell'hardware
		- Condizioni di accesso multiple
		- Ritardo di propagazione
		- Presenza o assenza di impulsi
### Altri Modi
I dati memorizzati possono anche essere visualizzati in altri modi, che non sono disponibili in tutti i modelli di questo tipo di strumenti. Queste modalità di solito consentono di ottenere un'indicazione globale del funzionamento del sistema in prova, dalla quale si può dedurre direttamente la correttezza o incorrettezza dello stesso. Si può anche dedurre la necessità di ulteriori analisi, generalmente effettuate utilizzando le modalità di visualizzazione precedentemente descritte o l'acquisizione di stati logici aggiuntivi.
Ad esempio, è possibile rappresentare sull'asse delle ordinate i valori codificati dei dati acquisiti relativi a un certo gruppo di linee di ingresso, mentre sull'asse delle ascisse viene mostrata la successione temporale di questi stati.
È importante sottolineare che questi modi di visualizzazione forniscono informazioni preziose per analizzare il funzionamento del sistema in prova e rilevare eventuali attività non previste.
### Misurazione Automatica
Vengono effettuate con operazioni di "trascina e rilascia". Offrono la possibilità di seguire la misurazione su dati acquisiti dall'analizzatore di stato logico.
- Offrono la possibilità di misure analogiche seguite con un oscilloscopio come la frequenza, il periodo, la lunghezza degli impulsi, il duty cycle, ecc.
- Le misurazioni automatiche forniscono risultati rapidi ed esaustivi, poiché forniscono rapidamente risultati di intervalli di campionamento molto ampi.
^1707321132167




### 6.4.1 Opzioni per Semplificare l'Analisi dei Dati Presentati

Un analizzatore di stati logici spesso presenta opzioni che consentono di semplificare l'analisi del funzionamento del sistema sotto esame, alcune delle quali sono presentate negli esempi seguenti.

**Esempio: Programma Applicativo per un Sistema a Microprocessore**
Normalmente, un programma applicativo per un sistema a microprocessore è formato da un insieme di moduli sorgente. Ciò consente di scrivere e assemblare separatamente le diverse parti del programma, che verranno poi unite e caricate in memoria del sistema mediante il linker. Questo approccio offre vantaggi come:

- La correzione di un errore in un modulo sorgente richiede solo la riesecuzione del modulo interessato anziché dell'intero programma.
- I diversi moduli sorgente possono essere scritti da diversi programmatori, accelerando così la scrittura del programma.
- È possibile evitare l'inserimento di subroutine di uso comune nel programma sorgente. È sufficiente che queste siano disponibili come moduli oggetto in una libreria che verrà caricata in memoria, insieme ad altri moduli necessari, tramite il linker.

La posizione occupata dai diversi moduli oggetto forniti dall'assemblatore in memoria non può essere definita dal programmatore, poiché questi non conosce l'estensione degli altri moduli né l'ordine in cui verranno depositati in memoria. Pertanto, il programmatore dispone solo di un elenco in cui l'indirizzo iniziale della subroutine di interesse non coincide con l'indirizzo reale di memoria in cui viene collocata quella subroutine.

La effettiva posizione dei diversi moduli del programma è eseguita dal linker nella fase di link, durante la quale i diversi moduli vengono collegati tra loro per ottenere il programma completo. L'indirizzo reale di memoria in cui inizia una specifica subroutine dipende dalla posizione di tutti gli altri moduli del programma.

Ad esempio, l'indirizzo della prima posizione della subroutine RADIX potrebbe essere 435EH, mentre nell'elenco disponibile tale subroutine inizia all'indirizzo 0000H. Tuttavia, lo strumento consente di stabilire una corrispondenza semplice tra gli indirizzi disponibili nell'elenco e quelli reali. A questo scopo, viene associata un'etichetta, come RADIX, all'indirizzo 435EH. Le direzioni successive a RADIX e inferiori a un indirizzo specificabile vengono visualizzate nel seguente modo:

- RADIX + 0000H
- RADIX + 0001H

In questo modo, sia la subroutine esaminata che lo spostamento relativo all'indirizzo di riferimento, che coincide con l'indirizzo indicato nell'elenco disponibile, vengono indicati esplicitamente.

Ciò semplifica notevolmente l'analisi dei dati presentati dallo strumento.

**Esempio: Opzione per la Visualizzazione delle Operazioni di Scrittura e Lettura**
Un'altra opzione che facilita l'analisi di un sistema a microprocessore è la seguente. Supponiamo di avere il segnale digitale RIW che controlla le operazioni di scrittura e lettura dei dati in una memoria RAM. Quando viene effettuata una lettura, il segnale RIW è a livello logico alto, mentre in un'operazione di scrittura assume il livello logico basso; sullo schermo dell'analizzatore vengono quindi presentati due valori logici 1 e 0 assunti in queste due situazioni. Per consentire all'operatore di associare direttamente un valore logico all'attività eseguita, evitando interpretazioni errate dei risultati, lo strumento può essere configurato in modo che, anziché i valori 0 e 1, vengano visualizzate le indicazioni WRITE e READ.
