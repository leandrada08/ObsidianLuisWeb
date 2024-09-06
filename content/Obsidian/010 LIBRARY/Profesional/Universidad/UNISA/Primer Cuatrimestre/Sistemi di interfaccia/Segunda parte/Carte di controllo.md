---
cards-deck: Profesional::Universidad::UNISA::Sistemi di interfaccia::Controllo di qualita
---




## Introduccion
### Motivaciones  
- El monitoria y control de calidad son esenciales para la eficiencia y competitividad
- Se deben medir y monitorear procesos para:
	- Determinar capacidad de cumplir requisitos
	- Observar estabilidad y continuidad en el tiempo
	- Mejorar continuamente



### Japoneses
- El objetivo anterior era el beneficio, y el objetivo siguiente es la calidad. 
- *Ademas los japones cambiaron el concepto de verificar la calidad por el de gestionar esta misma*
![[Pasted image 20240123203108.png|300]]
- El nuevo objetivo es, por lo tanto, la calidad, y *al tener como objetivo la calidad, han logrado resultados económicos extraordinarios*.
- **Como mantener mi calidad?**
	- *Diseño el proceso para asegurarme de que el resultado esté siempre en un rango que identifica para mí las especificaciones que quiero para el producto*.
	- *Ajustar el proceso de la mejor manera* 
		- *La calidad se obtiene verificando de manera continua y frecuente todos los resultados de la producción o descartando todos los que estén fuera de la banda que constituye la calidad.* 
		- Los japoneses impusieron la primera forma, mientras que loa alemanes usan la segunda.
			- Hay muchos desechos en el segundo caso en comparación con el primero y, por lo tanto, aumentan los costos.

> Los japoneses fueron los primeros en garantizar la garantía del producto, como en el caso de los automóviles.
> Esa garantía no les cuesta nada. 
> Hoy en día, hay un aplanamiento en las tecnologías japonesas, pero aún no hemos llegado a su nivel.


### Calidad
#### Gestion de la calidad
Gestión de la calidad implica gestionar un proceso con calidad, y aquí entra en juego la verificación y el control, por supuesto.
Ya que diseñamos *sistemas de medición automáticos que producen información sobre el producto y algunas fases del proceso, debemos conocer cómo se deben utilizar estos datos para ser objeto de control y verificación*, y para que alguien intervenga en caso de necesidad o si se sale de control. 
- Debe quedar claro para aquellos que están presentes en el proceso o lo monitorean, incluso a distancia, cómo está evolucionando el proceso/sistema con técnicas consolidadas y para comprenderlo rápidamente.
- *Algunos parámetros que son indicadores de calidad para ese producto se refieren a parámetros estadísticos*, operando sobre un alto número de productos, por supuesto. 
- En este caso, *el control al que nos referimos es el control del proceso a través del monitoreo de algunas magnitudes de la línea de producción para obtener el control del proceso.*


**Cuando el proceso está bajo control, esto garantiza que la producción/producto cumple con las especificaciones**. Al controlar proactivamente el proceso e interceptar la deriva de los parámetros, intervenimos en el proceso para mantenerlo bajo control. *Al hacer luego un control sobre el producto, la mayoría de ellos cumplirá con las especificaciones de proyecto.*
- *El modelo es fundamental para comprender cómo evolucionan los parámetros*. Siempre se parte de un modelo analítico; de lo contrario, se pueden utilizar datos experimentales para obtener este modelo experimentalmente mediante un procedimiento de ajuste o con **Machine Learning**. 
	 - Necesito entender *si algo está saliendo mal y cuáles son las causas* que causan un mal funcionamiento y cómo puedo intervenir. 
	 - Es evidente que *el proceso debe diseñarse con un enfoque virtuoso*, es decir, *partir del modelo analítico para obtener el diseño y la implementación del proceso*. 
	 - Entonces, *partiendo del modelo*, *sabemos todo*: dónde generar el feedback si la salida no es la esperada, porque el modelo es siempre la base del diseño. 
	 - Si el *proyecto no se basa en un modelo analítico, se recurre al método experimental: usar datos del proceso para retroceder* y, si existe, a un modelo para obtener ecuaciones y relaciones de causa y efecto. Si estas relaciones no son claras, *se utiliza el machine learning, especialmente útil con una gran cantidad de datos*. Aqui se usa AI
	 - Sin un modelo, no puedo intervenir, aunque sepamos la causa, porque no se puede asegurar que esa es la causa.

En sistemas de calidad debemos garantizar que los procesos esten siempre sujetos a mediciones de parametros caracteristicos y que estos sean analizados para entender, en primer lugar, si el proceso que hemos montado es capaz de manteenr esos objetivos de produccion, fijados inicialmente.
- Por lo tanto es obligatorio realizar un analisis preliminar, destinado simplemente a comprobar si el proceso establecido es capaz de satisfacer los objetivos fijados. Esto se realiza antes de iniciar la produccion de los objetos
#### ¿Qué significa calidad?  
- La calidad referida a un proceso de producción implica *obtener un producto como resultado de un proceso con la máxima estabilidad de los parámetros que lo caracterizan*. El parámetro siempre se mantiene en un intervalo específico según las especificaciones. *Un producto obtenido siempre con las mismas características indica un proceso de alta calidad*. 
- *Si me doy cuenta que hay un parámetro en deriva, puedo intervenir antes de que se produzca una violación de los límites*. Estamos hablando de la regulación de parámetros de proceso como la temperatura, la velocidad de un taladro, de una cinta y muchos otros parámetros que caracterizan el proceso de producción y sobre los cuales es necesario saber actuar e intervenir.

### Produccion de datos  
La producción de datos debe servir principalmente para:
- **Verificar** *que el sistema sea capaz de cumplir* con los objetivos en términos de calidad.(Capacidad de proceso)
- **Gestionar** la calidad del proceso *haciendo que los parámetros de este sean lo más constantes posible*.(Carta de control)
- **Mejorar** *el proceso trabajando en los fenómenos que determinan la mayor variabilidad de los datos*, por ejemplo, con machine learning. *Encontrando correlaciones*, se puede pasar a un nivel de calidad superior. Por lo tanto, quien produce los datos tiene un poder enorme porque en ellos está el conocimiento que se puede utilizar en todas las fases que estamos mencionando.
Evidentemente, el conocimiento del proceso es necesario para saber cuales de todas las cantidades posibles hay que monitorizar y por tanto elegir aquellas que son las variables realmente importante para controlar el proceso. Tambien es necesario saber dónde hacer la medición y dónde colocarlos. Cuanto más aumentan los parámetros a medir y, por lo tanto, la cantidad de sensores, mayor será el costo del proceso. 
- ¿A quién van estos datos? ¿Al departamento de producción, al centro de calidad? 
	- Es todo un conjunto de decisiones que deben tomarse y que conducen a una mayor o menor calidad del proceso. Establecidos los parámetros que deben monitorearse y dónde deben tomarse, esencialmente, a dónde va el sistema de medición y las herramientas para tomar los datos. Luego, para qué pueden servir y cuáles son las fases.





### Tipos de controles temporalmente que pueden ser efectuado:
1. **Antes del proceso** antes de poner en producción y consumir materias primas, tenemos la fase inicial de testing donde el proceso lo iniciamos para *verificar que la configuración inicial(Que son las configuraciones iniciales? Entradas,condiciones de la maquina, ambiente) no lleva fuera de especificación*. En los primeros datos se recogen en la fase de puesta en marcha del proceso. Cuando lo controlamos no es seguro que permanezca y como la calidad consiste en la estabilidad del nivel de los parámetros se deben monitorizar siempre y luego pasamos a la siguiente fase.
2. **Durante el proceso:** La segunda fase consiste en el *monitoreo continuo con frecuencias y tamaños de muestra que afectan a los parámetros estadísticos del control*, por supuesto.
3. **Sobre los productos acabados:** No es que la gestión de la calidad no implique la verificación del producto acabado, sino que también forma parte de esta operación final a efectuar. Son varias las fases del proceso donde se puede intervenir en tiempo y lugar.


#### Control preventivo(antes decontrol preventivo se realiza para *evitar errores gruesos*, por ejemplo, es necesario controlar:
- *Las entradas del proceso*.
- *La optimización de las condiciones de la máquina.*
- *La estabilidad ambienta*l: antes de iniciar la producción. Por ejemplo, control de la temperatura ambiente y otras verificaciones preliminares que dependen del proceso, por ejemplo, si hay UPS si el proceso es sensible a los cortes de energía.




#### Control durante el proceso  
Un control en 
- *Monitoreo de la deriva térmica y mecánica*.
- Inspección en línea de las herramientas más delicadas.
- *Computación suave y técnicas de IA para manejar automáticamente eventos inesperados*.
- *Monitoreo del estado del proceso a través de modelos.*
- Subida de las mediciones en línea y actualizaciones del estado para garantizar la trazabilidad.
--- 
**Efectos sistemáticos:** pueden provocar la salida de las especificaciones y se pueden detectar con cierta antelación. Una deriva antes de que salga del intervalo es más difícil de notar de antemano y estabilizarla con un cambio de signo.
La subida de datos garantiza preservar la gestión del proceso incluso de forma remota
> Diferencia entre efectos sistematicos y variabildiad natural

--- 
Para realizar un seguimiento online del estado de desgaste de las herramientas es evidentemente necesario saber cuales son las causas del desgaste de las herramiento, lo que solo es posbile con un modelo de las herramientas en mano.

#### Control post proceso
El monitoreo post proceso puede ser efectuado de varias maneras.
- Fuera de línea o en línea.
	- Se puede hacer un control post proceso de manera online, en la linea y fuera de las linea
- Trabajando en individuos o tomando muestras (análisis de muestra) → estudio de la población si muestreo al 100%.


## Control Estadístico del Proceso (SPC)  
**El control estadistico es:** Estimar, a través del análisis de parámetros estadísticos, el estado de nuestro proceso, ya sea que este bajo control o fuera de control.


Los esfuerzos para acercar la calidad de los productos al nivel considerado ideal por los clientes a menudo resultan en vano si no se conocen las causas que introducen variabilidad en los procesos. *Si no se pueden identificar con precisión las causas indeseadas que amenazan la estabilidad de un proceso, nunca será posible evitar su repetición*. 

El Control Estadístico de Procesos es la metodología que permite reconocer la presencia de fuentes de perturbación en el momento en que ocurren.
- La variabilidad en las entradas implica que, por lo general, es imposible predecir el valor de una característica de una sola unidad de producto.
	- *Los métodos estadísticos*, sin embargo, *hacen posible describir el resultado y el proceso mismo, naturalmente no de manera determinista, sino probabilística*. 
	- El Control Estadístico de Procesos (SPC) no *considera* las unidades individuales de producto, sino *el proceso en su conjunto*.
	- Las medidas en las unidades de producto, cuando se realizan, no tienen el propósito de separar las unidades buenas de las no conformes, sino de asegurar si la salida del proceso cumple con lo previsto. 






### Tipo de variaciones de procesos  
##### Variabilidad natural
En cada proces una variabilidad intrínseca que no depende de causas externas, denominada *variabilidad natural*, originada por una serie de fluctuaciones internas al proceso, resultado de numerosas pequeñas causas que operan de manera casual (llamadas causas comunes o aleatorias). Estas causas residen en el sistema de producción y no pueden atribuirse, por ejemplo, a máquinas, empleados o proveedores específicos; en este caso, la causa última reside y *debe buscarse en el sistema de producción, que debe modificarse, y no en un aspecto específico del proceso*. 
**Un proceso productivo cuya fuente de variabilidad se atribuye exclusivamente a este tipo de causas es un proceso predecible, que puede describirse mediante leyes estadísticas. Se habla en este caso de un proceso "bajo control estadístico".**
##### Variacion extraordinaria
Sin embargo, sobre la variabilidad del proceso pueden intervenir factores externos que alteran la variabilidad natural y generan una variabilidad impredecible que perturba el funcionamiento del proceso. Estos factores, llamados *causas especiales de variación*, determinan la parte excepcional de la variabilidad del proceso y representan grandes fluctuaciones en los datos, que *no se pueden atribuir al proceso objeto de análisis*. Estas fluctuaciones son el resultado de cambios en el proceso, que pueden indicar la aparición de problemas o, por el contrario, el surgimiento de novedades interesantes para explorar. 
*Un proceso cuya variabilidad se ve afectada tanto por causas comunes como por causas especiales de variación tiene un comportamiento impredecible, por lo que se hablará de un proceso "fuera de control estadístico".* 





### Instrumentos de control estadistico de procesos  
Puede hacer uso de varios instrumentos:
#### Recopilación de Datos
*Cerca de cada punto de medición*, había un recolector que debía ser llenado por el operador *indicando si la medida era correcta o no* (por ejemplo, una hoja de Excel) *o si estaba dentro de un cierto intervalo*. Hoy en día, aún existe, pero puede ser digital o haber una base de datos en lugar de una hoja de papel, reproduciendo de manera físicamente diferente la misma forma de recopilar datos. No proporciona una información estadística directa, pero puede deducirse (por ejemplo, luego calculo la media).
#### Histograma
Si debo mantener un parámetro bajo control, *elaborar un histograma basado en una muestra nos permite entender claramente la tendencia de ese parámetro*. Proporciona información para intervenir. Es de capital importancia interpretar los datos de salida del proceso productivo analizado para capturar su dispersión y comprender, por lo tanto, la variabilidad. Una vez que se han recopilado los datos, es necesario contar con una herramienta para interpretarlos correctamente. *El histograma es una herramienta gráfica que brinda una visión completa y sintética de los datos recopilados, proporcionando también una indicación de su dispersión*.
#### Diagrama de Pareto
El análisis de Pareto es una poderosa técnica de apoyo a la acción de resolución de problemas, utilizada con frecuencia en el ámbito del SPC. *Es una metodología gráfica que permite identificar objetivamente*, más que sensaciones debido a la urgencia del momento, *las prioridades de intervención en la solución de problemas, destacando*, entre una serie de causas, *aquellas que afectan más al fenómeno en cuestión*. El objetivo es desarrollar una mentalidad capaz de comprender cuáles son las pocas cosas más importantes, para concentrarse solo en ellas.
![[Pasted image 20240123203134.png]]
- El principio detrás de este análisis establece que, entre todas las posibles causas, pocas de ellas son responsables de la mayoría de los problemas encontrados. Si registramos los problemas que ocurren según el tipo o la causa que los ha provocado, podemos descubrir pronto que la mayoría de ellos (y el costo consiguiente) se atribuye solo a una o pocas causas entre las muchas identificadas. 
- El diagrama de Pareto es una representación gráfica simple del principio mencionado anteriormente, generalmente representado como un diagrama de barras, en el cual en el eje horizontal se muestran los tipos de defectos y en el eje vertical su incidencia porcentual.
- Muestra cuál clase de valores tiene la mayor frecuencia relativa y, descendiendo, las otras clases de valores. Es como la mitad de un histograma. Si el valor que ocurre con mayor frecuencia es el que deseamos, se puede considerar si el proceso está bajo control o no.
#### Análisis de Correlación
*Cuando se consideran conjuntamente dos o más variables cuantitativas, es posible examinar el tipo y la intensidad de las relaciones que existen entre ellas*. Se recurre al análisis de correlación cuando se desea medir la intensidad de la asociación entre dos variables que varían conjuntamente, sin que exista una relación directa de causa y efecto entre ellas.
Esta análisis busca destacar posibles relaciones de causa y efecto. Normalmente, *no se utiliza como herramienta de monitoreo, sino más bien para una fase de análisis del proceso*. *Por ejemplo, cuando no se tiene un modelo disponible.* Es útil si los parámetros son pocos y no se requiere el uso de machine learning. Por ejemplo, se puede realizar un diagrama de desgaste versus velocidad para entender qué resultados se obtienen y comprender si hay una correlación y cómo esta actúa. Se puede determinar si la relación es determinística o no, o incluso si no hay correlación.
#### Carta de control
Sirve para estudiar el proceso y detectar anomalias. Se grafican limites de contrl y valores estadisticos. Permiten predeicr desviaciones y tomar acciones.






## Carta de Control  
Con el fin de obtener niveles de calidad aceptables, puede ser crucial emprender *una acción de monitoreo de la variabilidad* (la fluctuación de los valores medidos alrededor de la media) del proceso productivo; una variabilidad excesiva conduciría a que el producto no cumpla con sus características funcionales.
![[Pasted image 20240208184713.png|400]]
- Las cartas de control son gráficos de un proceso en el tiempo que permiten detectar anomalías y desviaciones mediante límites estadísticos.
- Ayudan a identificar si un proceso está fuera de control y reconocer sus causas para tomar acciones correctivas, evitando errores tipicos de exceso de intervención(interpretar como causa comun una extraordinaria) o falta de intervención(interpretar como causa extraordinaria una comun). 
- *Se establece un valor objetivo, límites de alarma y límites de especificación*. Superar los límites de alarma requiere vigilancia, superar los de especificación requiere acción inmediata.
- La elección de los límites implica un equilibrio entre el riesgo de rechazar productos buenos (error tipo I) y aceptar productos malos (error tipo II).

El parámetro puede ser:
- Un valor medido (carta de control x), donde la variable se mide y se representa típicamente en valor medio o esperado. 
- El rango de pertenencia del parámetro que se está monitoreando. No se extrae la media en un cierto intervalo, sino el rango (distancia entre el máximo y el mínimo)
- La sigma, es decir, el valor que se obtiene de ese conjunto de valores medidos (es decir, su dispersión).

Hay indices que permiten entender si lo que esta sucediente es fruto de un proceso bajo control o fuera de control. Por ejemplo:
- Si los puntos se mueven en zig-zag, estoy observando un proceso fuera de control
- Si los puntos son aleatorios, dando una distribucion gaussiana dentro de la banda de calidad que queremos obtener, estoy observando un proceso bajo contrl

La carta de control se pueden diferenciar en carta de variables o de atributos, las que analizamos y analizaremos son de variables, donde se señale un valor numerico de los parametros. Las cartas de atributos son aquellas donde en lugar de marcar el valor numerico, se le da un adjetico al producto(cumple, no cumple, parcialmente, etc)


### Proceso carta de control  
1. **En una fase preliminar que se realiza** se debe establecer el nivel objetivo del parámetro, seria ideal, el valor de este parámetro debería ser siempre igual al objetivo y se traza la "línea".
2. **Establecer una tolerancia con respecto a este valor ideal** obviamente, la igualdad nunca es perfecta→se establece un umbral porcentual donde el valor debe mantenerse para considerar el proceso bajo control *$$[LímiteSuperiorDeAlarma; LímiteInferiorDeAlarma]$$*.
3. *Si el valor supera este primer umbral de alarma, se genera una alarma, pero el producto aún es conforme*. Se espera que la desviación sea temporal (pero si persiste, se debe intervenir para devolverlo bajo control) porque esta es una condición de fuera de control.
4. Si el parámetro supera el límite superior específico→ ¡intervención inmediata! Estamos produciendo productos defectuosos. Por lo general, son ± 2 sigma.$$[LímiteSuperiorEspecífico; LímiteInferiorEspecífico]$$



### Tipos de errores y eleccion de umbrales  
¿Cuál es la influencia en el monitoreo de la elección de los umbrales?
Dado que estamos hablando de paricos, cada parámetro tiene su nivel de confianza. Existe el riesgo, de todos modos, de cometer errores al tomar decisiones sobre parámetros estadísticos:
1. **Error tipo 1, tipo alfa:** *rechazar un producto conforme*. Esto significa que he establecido umbrales tan estrechos que, incluso si hay una oscilación aleatoria del valor del producto, salgo inmediatamente fuera de ellos con la menor oscilación.
2. **Error tipo 2, beta:** *aceptar un producto no conforme*. Aceptar uno de los dos errores según la filosofía empresarial. Compromiso óptimo entre los dos tipos de errores.
Estos son los riesgos que tenemos al exagerar uno u otro error según cómo movemos los umbrales. 
- Los alemanes optaron por elegir umbrales muy estrechos. Los japonenes, ayq eu tienen un proceso que ya es muy eficiente en terminos de calidad, eligen umbrales flexibles, ya que en cualquier caso el error ya seria muy limitado.

### Tamaño de la muestra para una carta de control  
Definimos una ventana de tiempo dentro de la cual vamos a actualizar el mapa con las posteriores adquisiciones de un parametro(Especia de buffer FIFO) trigger 100%. Siempre queremos tener visualizadas las ultimas N acquisiciones de un parametro especifico, tipicamente representando el valor medio o promedio.
Otro parámetro que puede influir en el riesgo de cometer uno de los dos errores es el tamaño de la muestra, es decir, cuántos valores se observan estadísticamente y cuántos se promedian y se desvían estándar. 
- Sabemos que el tamaño de la muestra determina la confiabilidad de la estimación que estamos haciendo y afecta la estimación de parámetros como la varianza. Mientras mayor sea el tamaño de la muestsr, mas confiables seran los datos estimados pero esto extiende el tiempo de produccion del resultado
	- Pero aumentar el tamaño de la muestra aumenta el tiempo para producir un solo valor y esto puede reducir, si aumentamos demasiado el tamaño de la muestra, la frecuencia de muestreo: ¿cada cuánto saco el valor de este parámetro? Puedo sacar este valor con un intervalo de tiempo mayor entre uno y otro porque he aumentado demasiado el tamaño de la muestra.
- La frecuencia de muestreo permite detectar si una desviación es aleatoria o sistemática. Frecuencias bajas no permiten distinguir esto. 
*Tambien se puede utilizar un sitema adaptativo:* si supero un umbral durante cierto tiempo, aumento la frecuencia de muestreo y reduzco el tamaño de la muestra porque estoy interesado en entender si el evento que me causa esa sobreexposición es aleatorio o sistemático.






## Capacidad del proceso  
La primera fase, la de eleccion de los umbrales, se conoce comunemte como periodo azul, en la que se definen los umbrales azules.
- Una vez que el proceso esta en marcha, observamos si nuestro proceso es capaz de sostener estos umbrales de calidad.
- De la observacion del proceso surgiran umbrales rojos.
Los umbrales rojos deben compararse con los azules para comprender si el proceso es capaz de resistir estos umbrales o no. La capacidad del proceso viene dada por la diferencia entre los umbrales azules y rojos. El primero elegido en base a un analisis preliminar y el segundo es el que surgio de un analisis estadistico durante el proceso.
- Si el primer rango es menor que el segundo, entonces la capacidad es menor que 1 y el proceso no puede garantizar la calidad deseada.
$$CP = \frac{LSC_{estimado}-LIC_{estimado}}{LSC_{obtenido} - LIC_{obtenido}}$$
- Si CP<1, el proceso no puede soportar los rangos inicialmente establecidos.
- Si CP>=1 indica que el proceso es capaz de cumplir las especificaciones
![[Pasted image 20240124124419.png|500]]
![[Pasted image 20240208194123.png|500]]



## Conclusion
- Las cartas de control son un medio poderoso para mantener un proceso bajo control estadístico, indicando las acciones correctivas que deben tomarse para eliminar las causas de la variabilidad indeseada, las causas atribuibles. 
- Sin embargo, las cartas de control no tienen en cuenta las especificaciones a las que debe adherirse el proceso, como tolerancias de trabajo u otras características requeridas en el producto final del proceso.
	- Por ejemplo, imaginemos que las especificaciones dicen que el peso de un producto debe estar entre 90 y 110 gramos. Si el proceso produce los productos con un peso promedio de 70 gramos, y la variabilidad es mínima (proceso estable), las cartas de control no encontrarían nada extraño, pero el proceso no cumpliría las especificaciones
- Su uso no es suficiente para comprender la capacidad real de un proceso y cómo puede mejorarse. Con este fin, se definen los índices de capacidad del proceso, que relacionan el rendimiento o el potencial del proceso con el cumplimiento de las especificaciones establecidas.
	- Además, permiten resumir de manera muy concisa los datos de un proceso productivo, con la ventaja, en comparación con los índices estadísticos como la media y la dispersión, de ser cantidades adimensionales y, por lo tanto, fácilmente interpretables y comparables entre sí. Con el estudio de la capacidad potencial de un proceso, se busca verificar la capacidad de mantener una determinada característica dentro de los límites de especificación predeterminados. La capacidad del proceso evalúa el rendimiento cualitativo de un proceso en función de una comparación entre la amplitud de la dispersión del proceso y la amplitud del intervalo de tolerancia. El análisis de la capacidad del proceso abarca diferentes funciones; puede usarse para:

- cuantificar la variabilidad en un proceso productivo;
- verificar el rendimiento requerido para nuevas herramientas;
- predecir el rendimiento del proceso;
- determinar los intervalos de muestreo;
- ayudar en la selección o modificación de un proceso;
- planificar las tolerancias para que el producto final permanezca dentro de las especificaciones.




# Italiano

## Introduzione

### Motivazioni  #tarjeta-anki 
- Il monitoraggio e il controllo della qualità sono essenziali per l'efficienza e la competitività.
- I processi devono essere misurati e monitorati per:
	- Determinare la capacità di soddisfare i requisiti.
	- Osservare la stabilità e la continuità nel tempo.
	- Migliorare continuamente.
### Giapponesi
- L'obiettivo precedente era il profitto, e l'obiettivo successivo è la qualità.
- Il nuovo obiettivo è quindi la qualità, e avendo come obiettivo la qualità, hanno ottenuto risultati economici straordinari.
- Come mantenere la mia qualità?
	- Progettare il processo per garantire che il risultato sia sempre in un intervallo che identifica per me le specifiche che voglio per il prodotto.
	- Regolare il processo nel migliore dei modi, ma la qualità si ottiene verificando continuamente e frequentemente tutti i risultati della produzione e scartando tutti quelli al di fuori della banda che costituisce la qualità.
	- Ci sono molti scarti nel secondo caso rispetto al primo e, di conseguenza, i costi aumentano.
^1707419253998

>I giapponesi sono stati i primi a garantire la garanzia del prodotto, come nel caso delle automobili. Tale garanzia non costa loro nulla. Oggi c'è una piattaforma nelle tecnologie giapponesi, ma non abbiamo ancora raggiunto il loro livello.

### Qualità
#### Gestione della qualità
La gestione della qualità implica gestire un processo con qualità, e qui entra in gioco la verifica e il controllo, naturalmente.
Poiché progettiamo **sistemi di misurazione automatici che producono informazioni sul prodotto e su alcune fasi del processo, dobbiamo sapere come utilizzare questi dati per essere oggetto di controllo e verifica**, e affinché qualcuno intervenga in caso di necessità o se esce dal controllo.
- Deve essere chiaro per coloro che sono presenti nel processo o lo monitorano, anche a distanza, come sta evolvendo il processo/sistema con tecniche consolidate e per comprenderlo rapidamente.
- Alcuni parametri che sono indicatori di qualità per quel prodotto si riferiscono a parametri statistici, operando su un alto numero di prodotti, naturalmente.
- In questo caso, il controllo a cui ci riferiamo è il controllo del processo attraverso il monitoraggio di alcune grandezze della linea di produzione per ottenere il controllo del processo.

Quando il processo è sotto controllo, questo garantisce che la produzione/prodotto soddisfi le specifiche. Controllando proattivamente il processo e intercettando la deriva dei parametri, interveniamo nel processo per mantenerlo sotto controllo. Effettuando poi un controllo sul prodotto, la maggior parte di essi rispetterà le specifiche di progetto.

- Il modello è fondamentale per comprendere come evolvono i parametri. Si parte sempre da un modello analitico; in caso contrario, possono essere utilizzati dati sperimentali per ottenere questo modello sperimentalmente mediante un procedimento di adattamento o con **Machine Learning**.
	- Ho bisogno di capire se qualcosa sta andando storto e quali sono le cause che causano un malfunzionamento e come posso intervenire.
	- È evidente che il processo deve essere progettato con un approccio virtuoso, cioè partendo dal modello analitico per ottenere la progettazione e l'implementazione del processo.
	- Quindi, partendo dal modello, sappiamo tutto: dove generare il feedback se l'uscita non è quella prevista, perché il modello è sempre la base della progettazione.
	- Se il progetto non si basa su un modello analitico, si ricorre al metodo sperimentale: utilizzare dati del processo per retrocedere e, se esiste, a un modello per ottenere equazioni e relazioni di causa ed effetto. Se queste relazioni non sono chiare, si utilizza il machine learning, particolarmente utile con un gran numero di dati.

#### Cosa significa qualità? #tarjeta-anki 
- La qualità riferita a un processo di produzione implica *ottenere un prodotto come risultato di un processo con la massima stabilità dei parametri che lo caratterizzano*. Il parametro è sempre mantenuto all'interno di un intervallo specifico secondo le specifiche. *Un prodotto ottenuto sempre con le stesse caratteristiche indica un processo di alta qualità*. 
- *Se mi accorgo che c'è un parametro in deriva, posso intervenire prima che si verifichi una violazione dei limiti*. Stiamo parlando della regolazione dei parametri di processo come la temperatura, la velocità di un trapano, di una cinghia e molti altri parametri che caratterizzano il processo di produzione e su cui è necessario sapere agire ed intervenire.
^1707419254006


e un parametro in deriva, posso intervenire prima che si verifichi una violazione dei limiti. Stiamo parlando della regolazione dei parametri di processo come la temperatura, la velocità di un trapano, di una cinghia e molti altri parametri che caratterizzano il processo di produzione e su cui è necessario sapere come agire e intervenire.

### Produzione di dati  #tarjeta-anki 
La produzione di dati deve servire principalmente per:
- **Verificare** *che il sistema sia in grado di soddisfare* gli obiettivi in termini di qualità. (Capacità di processo)
- **Gestire** la qualità del processo *rendendo i parametri il più costanti possibile*. (Carta di controllo)
- **Migliorare** *il processo lavorando sui fenomeni che determinano la maggiore variabilità dei dati*, ad esempio, con il machine learning. *Trovarne correlazioni* può portare a un livello di qualità superiore. Pertanto, chi produce i dati ha un'enorme potenza perché in essi risiede la conoscenza che può essere utilizzata in tutte le fasi che stiamo menzionando.
Evidentemente, la conoscenza del processo è necessaria per sapere quali tra tutte le possibili grandezze monitorare e quindi scegliere quelle che sono le variabili veramente importanti da controllare nel processo. È anche necessario sapere dove fare le misurazioni e dove posizionarle. Più aumentano i parametri da misurare e quindi la quantità di sensori, maggiore sarà il costo del processo.
- A chi vanno questi dati? Al dipartimento di produzione, al centro di qualità?
	- È tutto un insieme di decisioni che devono essere prese e che portano a una maggiore o minore qualità del processo. Una volta stabiliti i parametri da monitorare e dove devono essere presi, fondamentalmente, si determina dove va il sistema di misurazione e gli strumenti per raccogliere i dati. Poi, per cosa possono servire e quali sono le fasi.
^1707419254011


### Tipi di controllo temporaneo che possono essere effettuati: #tarjeta-anki 
1. **Prima del processo:** prima di mettere in produzione e consumare materie prime, abbiamo la fase iniziale di testing dove avviamo il processo per verificare che la configurazione iniziale non porti fuori specifica. I primi dati vengono raccolti nella fase di avviamento del processo. Quando lo controlliamo, non è sicuro che rimanga e poiché la qualità consiste nella stabilità del livello dei parametri, devono essere monitorati sempre e poi passiamo alla fase successiva.
2. **Durante il processo:** La seconda fase consiste nel monitoraggio continuo con frequenze e dimensioni campionarie che influenzano i parametri statistici di controllo, naturalmente.
3. **Sui prodotti finiti:** Non è che la gestione della qualità non implichi il controllo del prodotto finito, ma fa parte anche di questa operazione finale da effettuare. Ci sono varie fasi del processo in cui è possibile intervenire nel tempo e nel luogo.
^1707419254016


#### Controllo preventivo (prima del processo) #tarjeta-anki 
Il controllo preventivo si effettua per *evitare errori grossolani*, ad esempio, è necessario controllare:
- Gli ingressi del processo.
- *L'ottimizzazione delle condizioni della macchina.*
- *La stabilità ambientale*: prima di avviare la produzione. Ad esempio, controllo della temperatura ambiente e altre verifiche preliminari che dipendono dal processo, ad esempio, se ci sono UPS se il processo è sensibile ai black-out.
^1707419254021


#### Controllo durante il processo  #tarjeta-anki 
Un controllo in:
- Monitoraggio della deriva termica e meccanica.
- Ispezione online degli strumenti più delicati.
- Calcolo morbido e tecniche di intelligenza artificiale per gestire automaticamente eventi imprevisti.
- Monitoraggio dello stato del processo attraverso modelli.
- Alzando le misurazioni online e gli aggiornamenti dello stato per garantire la tracciabilità.
**Effetti sistemici:** possono causare la fuoriuscita dalle specifiche e possono essere rilevati con una certa anticipo. Una deriva prima che escano dall'intervallo è più difficile da notare in anticipo e stabilizzare con un cambio di segno. La raccolta di dati garantisce di preservare la gestione del processo anche da remoto.
^1707419254026


#### Controllo post processo
Il monitoraggio post processo può essere effettuato:
- Offline o online.
- Lavorando sugli individui o prendendo campioni (analisi del campione) → studio della popolazione se il campionamento è al 100%.

## Controllo Statistico del Processo (SPC)   #tarjeta-anki 
**Scopo:** stimare, attraverso l'analisi di parametri statistici, la situazione del processo, determinare se è fuori o sotto controllo.
Gli sforzi per avvicinare la qualità dei prodotti al livello considerato ideale dai clienti spesso sono vani se non sono conosciute le cause che introducono variabilità nei processi. *Se non si possono identificare con precisione le cause indesiderate che minacciano la stabilità di un processo, non sarà mai possibile evitarne la ripetizione*. 
Il Controllo Statistico dei Processi è la metodologia che consente di riconoscere la presenza di fonti di disturbo nel momento in cui si verificano.
- La variabilità negli ingressi implica che, di solito, sia impossibile prevedere il valore di una caratteristica di una singola unità di prodotto.
	- *I metodi statistici*, tuttavia, *rendono possibile descrivere il risultato e il processo stesso, naturalmente non in modo deterministico, ma probabilistico*. 
	- Il Controllo Statistico dei Processi (SPC) non *considera* le singole unità di prodotto, ma *il processo nel suo complesso*.
	- Le misure sulle unità di prodotto, quando vengono effettuate, non hanno lo scopo di separare le unità buone da quelle non conformi, ma di assicurare se l'uscita del processo è conforme a quanto previsto. 
^1707419254029


### Tipi di variazioni dei processi  #tarjeta-anki 
##### Variabilità naturale
In ogni processo c'è una variabilità intrinseca che non dipende da cause esterne, chiamata *variabilità naturale*, originata da una serie di fluttuazioni interne al processo, risultato di numerose piccole cause che operano casualmente (chiamate cause comuni o casuali). Queste cause risiedono nel sistema di produzione e non possono essere attribuite, ad esempio, a macchine, dipendenti o fornitori specifici; in questo caso, la causa ultima risiede e deve essere cercata nel sistema di produzione, che deve essere modificato, e non in un aspetto specifico del processo. 
*Un processo produttivo la cui fonte di variabilità è attribuita esclusivamente a questo tipo di cause è un processo prevedibile, che può essere descritto mediante leggi statistiche. Si parla in questo caso di un processo "sotto controllo statistico".*
##### Variabilità straordinaria
Tuttavia, sulla variabilità del processo possono intervenire fattori esterni che alterano la variabilità naturale e generano una variabilità imprevedibile che disturba il funzionamento del processo. Questi fattori, chiamati *cause speciali di variazione*, determinano la parte eccezionale della variabilità del processo e rappresentano grandi fluttuazioni nei dati, che non possono essere attribuite al processo oggetto di analisi. Queste fluttuazioni sono il risultato di cambiamenti nel processo, che possono indicare l'emergere di problemi o, al contrario, il sorgere di novità interessanti da esplorare. 
*Un processo la cui variabilità è influenzata sia da cause comuni che da cause speciali di variazione ha un comportamento imprevedibile, quindi si parlerà di un processo "fuori controllo statistico".*
^1707419254034




### Strumenti di controllo statistico dei processi #tarjeta-anki 
Si possono utilizzare vari strumenti:
#### Raccolta dati
*Vicino a ogni punto di misurazione*, c'era un raccoglitore che doveva essere compilato dall'operatore *indicando se la misura fosse corretta o meno* (ad esempio, un foglio di Excel) *o se fosse all'interno di un certo intervallo*. Oggi, esiste ancora, ma può essere digitale o può esserci un database al posto di un foglio di carta, riproducendo fisicamente in modo diverso la stessa forma di raccolta dati. Non fornisce informazioni statistiche dirette, ma possono essere dedotte (ad esempio, poi calcolo la media).
#### Istogramma
Se devo mantenere sotto controllo un parametro, *elaborare un istogramma basato su un campione ci permette di capire chiaramente la tendenza di quel parametro*. Fornisce informazioni per intervenire. È di capitale importanza interpretare i dati di uscita del processo produttivo analizzato per catturarne la dispersione e comprendere, quindi, la variabilità. Una volta che i dati sono stati raccolti, è necessario disporre di uno strumento per interpretarli correttamente. *L'istogramma è uno strumento grafico che fornisce una visione completa e sintetica dei dati raccolti, fornendo anche un'indicazione della loro dispersione*.
#### Diagramma di Pareto
L'analisi di Pareto è una potente tecnica di supporto all'azione di risoluzione dei problemi, spesso utilizzata nell'ambito dello SPC. *È una metodologia grafica che consente di identificare obiettivamente*, più che sensazioni dovute all'urgenza del momento, *le priorità di intervento nella soluzione dei problemi, evidenziando*, tra una serie di cause, *quelle che influenzano maggiormente il fenomeno in questione*. L'obiettivo è sviluppare una mentalità in grado di capire quali sono le poche cose più importanti, per concentrarsi solo su di esse.
![[Pasted image 20240123203134.png]]
- Il principio alla base di questa analisi stabilisce che, tra tutte le possibili cause, poche di esse sono responsabili della maggior parte dei problemi riscontrati. Se registriamo i problemi che si verificano in base al tipo o alla causa che li ha provocati, possiamo presto scoprire che la maggior parte di essi (e il costo conseguente) è attribuita solo a una o poche cause tra le molte identificate.
- Il diagramma di Pareto è una rappresentazione grafica semplice del principio sopra menzionato, generalmente rappresentato come un diagramma a barre, in cui sull'asse orizzontale vengono mostrati i tipi di difetti e sull'asse verticale la loro incidenza percentuale.
- Mostra quale classe di valori ha la maggiore frequenza relativa e, discendendo, le altre classi di valori. È come metà di un istogramma. Se il valore che si verifica con maggiore frequenza è quello desiderato, si può considerare se il processo è sotto controllo o meno.
#### Analisi di correlazione
*Quando si considerano congiuntamente due o più variabili quantitative, è possibile esaminare il tipo e l'intensità delle relazioni che esistono tra di loro*. Si ricorre all'analisi di correlazione quando si desidera misurare l'intensità dell'associazione tra due variabili che variano insieme, senza che esista una relazione diretta di causa ed effetto tra di esse.
Questo tipo di analisi cerca di evidenziare possibili relazioni di causa ed effetto. Normalmente, *non viene utilizzato come strumento di monitoraggio, ma piuttosto per una fase di analisi del processo*. Ad esempio, quando non si dispone di un modello disponibile. È utile se i parametri sono pochi e non è necessario l'uso del machine learning. Ad esempio, si può eseguire un diagramma di usura versus velocità per capire quali risultati si ottengono e comprendere se c'è una correlazione e come questa agisce. Si può determinare se la relazione è deterministica o meno, o anche se non c'è correlazione.
#### Scheda di controllo
Serve per studiare il processo e rilevare anomalie. Vengono graficati i limiti di controllo e i valori statistici. Consentono di prevedere deviazioni e intraprendere azioni.
^1707419254038


## Scheda di Controllo #tarjeta-anki 
Al fine di ottenere livelli di qualità accettabili, potrebbe essere cruciale intraprendere *un'azione di monitoraggio della variabilità* (fluttuazione dei valori misurati intorno alla media) del processo produttivo; un'eccessiva variabilità porterebbe il prodotto a non rispettare le sue caratteristiche funzionali.
![[Pasted image 20240208184713.png|400]]
- Le carte di controllo sono grafici di un processo nel tempo che consentono di rilevare anomalie e deviazioni attraverso limiti statistici.
- Aiutano a identificare se un processo è fuori controllo e riconoscerne le cause per intraprendere azioni correttive, evitando errori tipici di eccessiva intervenzione (interpretare come causa comune un evento straordinario) o mancanza di intervento (interpretare come causa straordinaria un evento comune).
- *Viene stabilito un valore obiettivo, limiti di allarme e limiti di specifica*. Superare i limiti di allarme richiede vigilanza, superare quelli di specifica richiede azione immediata.
- La scelta dei limiti implica un equilibrio tra il rischio di respingere prodotti buoni (errore di tipo I) e accettare prodotti difettosi (errore di tipo II).
Il parametro può essere:
- Un valore misurato (carta di controllo x), dove la variabile viene misurata e rappresentata tipicamente come valore medio o atteso.
- L'intervallo di appartenenza del parametro che viene monitorato. Non si estrae la media in un certo intervallo, ma l'intervallo stesso (distanza tra il massimo e il minimo).
- La sigma, cioè il valore ottenuto da quel insieme di valori misurati (cioè la sua dispersione).
Ci sono indicatori che permettono di capire se ciò che sta accadendo è il risultato di un processo sotto controllo o fuori controllo. Per esempio:
- Se i punti si muovono a zig-zag, sto osservando un processo fuori controllo.
- Se i punti sono casuali, dando una distribuzione gaussiana all'interno della banda di qualità che vogliamo ottenere, sto osservando un processo sotto controllo.
Le carte di controllo possono essere differenziate in carte di variabili o di attributi; quelle che analizziamo e analizzeremo sono di variabili, dove viene segnalato un valore numerico dei parametri. Le carte di attributi sono quelle in cui invece di segnare il valore numerico, viene dato un aggettivo al prodotto (conforme, non conforme, parzialmente, ecc.).
^1707419254042


### Processo della scheda di controllo #tarjeta-anki 
1. **In una fase preliminare che viene condotta**, è necessario stabilire il livello obiettivo del parametro; idealmente, il valore di questo parametro dovrebbe essere sempre uguale all'obiettivo e si traccia la "linea".
2. **Stabilire una tolleranza rispetto a questo valore ideale**; ovviamente, l'uguaglianza non è mai perfetta→si stabilisce una soglia percentuale entro cui il valore deve mantenersi per considerare il processo sotto controllo *$$[LimiteSuperioreDiAllarme; LimiteInferioreDiAllarme]$$*.
3. *Se il valore supera questa prima soglia di allarme, viene generato un allarme, ma il prodotto è ancora conforme*. Si attende che la deviazione sia temporanea (ma se persiste, è necessario intervenire per riportarla sotto controllo) perché questa è una condizione di fuori controllo.
4. Se il parametro supera il limite superiore specifico→ intervento immediato! Stiamo producendo prodotti difettosi. Di solito sono ± 2 sigma. $$[LimiteSuperioreSpecifico; LimiteInferioreSpecifico]$$
^1707419254046


### Tipi di errori e scelta delle soglie #tarjeta-anki 
Qual è l'influenza sul monitoraggio della scelta delle soglie?
Dato che stiamo parlando di parametri, ogni parametro ha il suo livello di confidenza. Esiste comunque il rischio di commettere errori nel prendere decisioni sui parametri statistici:
1. **Errore di tipo 1, tipo alfa:** *rifiutare un prodotto conforme*. Ciò significa che ho stabilito soglie così strette che, anche se c'è un'oscillazione casuale del valore del prodotto, esco immediatamente al di fuori di esse con la minima oscillazione.
2. **Errore di tipo 2, beta:** *accettare un prodotto non conforme*. Accettare uno dei due errori secondo la filosofia aziendale. Compromesso ottimale tra i due tipi di errori.
Questi sono i rischi che abbiamo nel esagerare uno o l'altro errore a seconda di come spostiamo le soglie.
- Gli tedeschi hanno optato per scegliere soglie molto strette. I giapponesi, poiché hanno un processo già molto efficiente in termini di qualità, scelgono soglie flessibili, poiché in ogni caso l'errore sarebbe già molto limitato.
^1707419254050

Questi sono i rischi che corriamo esagerando uno o l'altro errore a seconda di come spostiamo le soglie.

### Dimensione del campione per una scheda di controllo #tarjeta-anki 
Definiamo una finestra temporale entro la quale aggiorneremo la mappa con le acquisizioni successive di un parametro (tipo di buffer FIFO) al 100% di trigger. Vogliamo sempre visualizzare le ultime N acquisizioni di un parametro specifico, tipicamente rappresentando il valore medio o medio.
Un altro parametro che può influenzare il rischio di commettere uno dei due errori è la dimensione del campione, cioè quanti valori vengono osservati statisticamente e quanti vengono mediati e deviati standard.
- Sappiamo che la dimensione del campione determina l'affidabilità dell'analisi che stiamo facendo e influenza la stima di parametri come la varianza. Maggiore è la dimensione del campione, più affidabili saranno i dati stimati, ma ciò prolunga il tempo di produzione del risultato.
	- Ma aumentare la dimensione del campione aumenta il tempo per produrre un singolo valore e questo può ridurre, se aumentiamo troppo la dimensione del campione, la frequenza di campionamento: ogni quanto prelevo il valore di questo parametro? Posso prelevare questo valore con un intervallo di tempo maggiore tra uno e l'altro perché ho aumentato troppo la dimensione del campione.
- La frequenza di campionamento consente di rilevare se una deviazione è casuale o sistematica. Le basse frequenze non consentono di distinguere questo.
*Si può anche utilizzare un sistema adattativo:* se supero una soglia per un certo periodo di tempo, aumento la frequenza di campionamento e riduco la dimensione del campione perché sono interessato a capire se l'evento che causa quella sovraesposizione è casuale o sistematico.
^1707419254054

## Capacità del processo #tarjeta-anki 
La prima fase, quella della scelta delle soglie, è comunemente conosciuta come periodo blu, in cui vengono definite le soglie blu.
- Una volta che il processo è avviato, osserviamo se il nostro processo è in grado di sostenere queste soglie di qualità.
- Dall'osservazione del processo emergono le soglie rosse.
Le soglie rosse devono essere confrontate con le blu per comprendere se il processo è in grado di resistere a queste soglie o meno. La capacità del processo è data dalla differenza tra le soglie blu e rosse. La prima è scelta sulla base di un'analisi preliminare e la seconda è quella che è emersa da un'analisi statistica durante il processo.
- Se il primo intervallo è inferiore al secondo, allora la capacità è inferiore a 1 e il processo non può garantire la qualità desiderata.
$$CP = \frac{LSC_{stimato}-LIC_{stimato}}{LSC_{ottenuto} - LIC_{ottenuto}}$$
- Se CP<1, il processo non può sostenere gli intervalli inizialmente stabiliti.
- Se CP>=1 indica che il processo è in grado di soddisfare le specifiche.
![[Pasted image 20240124124419.png|500]]
![[Pasted image 20240208194123.png|500]]
^1707419254057

## Conclusione
- Le schede di controllo sono un potente mezzo per mantenere un processo sotto controllo statistico, indicando le azioni correttive che devono essere intraprese per eliminare le cause della variabilità indesiderata, le cause attribuibili.
- Tuttavia, le schede di controllo non tengono conto delle specifiche a cui il processo deve aderire, come le tolleranze di lavoro o altre caratteristiche richieste nel prodotto finale del processo.
  - Ad esempio, immaginiamo che le specifiche dicano che il peso di un prodotto deve essere compreso tra 90 e 110 grammi. Se il processo produce i prodotti con un peso medio di 70 grammi e la variabilità è minima (processo stabile), le schede di controllo non troverebbero nulla di strano, ma il processo non rispetterebbe le specifiche.
- Il loro utilizzo non è sufficiente per comprendere la capacità reale di un processo e come può essere migliorato. A questo scopo, vengono definiti gli indici di capacità del processo, che collegano le prestazioni o il potenziale del processo al rispetto delle specifiche stabilite.
  - Inoltre, consentono di riassumere in modo molto conciso i dati di un processo produttivo, con il vantaggio, rispetto agli indici statistici come la media e la dispersione, di essere grandezze adimensionali e quindi facilmente interpretabili e confrontabili tra loro. Con lo studio della capacità potenziale di un processo, si cerca di verificare la capacità di mantenere una determinata caratteristica entro i limiti di specifica predefiniti. La capacità del processo valuta le prestazioni qualitative di un processo in base a un confronto tra l'ampiezza della dispersione del processo e l'ampiezza dell'intervallo di tolleranza. L'analisi della capacità del processo copre diverse funzioni; può essere utilizzato per:

- quantificare la variabilità in un processo produttivo;
- verificare le prestazioni richieste per nuovi strumenti;
- prevedere le prestazioni del processo;
- determinare gli intervalli di campionamento;
- aiutare nella selezione o modifica di un processo;
- pianificare le tolleranze in modo che il prodotto finale rimanga all'interno delle specifiche.
