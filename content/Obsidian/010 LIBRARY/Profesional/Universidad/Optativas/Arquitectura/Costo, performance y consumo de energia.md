
## Costo 
- $CostoDelChip=CostoOblea/(ChipsOblea*yield)$
- $ChipsOblea=AreaOblea/AreaChip$
- Factor de produccion($yield$)=$ChipsSinDefectos/TotalChips$
Al reducir el area del chip
- Aumenta la cantidad de chips
- Aumenta el yield
--> Disminuye el costo del chip
- El costo del chip es proporcional al cubo de su area
- El area se reduce mejorando el proceso de fabricacion
*Siempre escuchamos que definen la tecnologia con una unidad de longitud(10nm), pero que significa este tamanio?*
- En un principio era el ancho de la compuerta
- Ahora es un numero que indica la capacidad de la fabrica, ya que no indican el ancho del transistor.
- La escala entre 2 tecnologias consecutivas(feature size) es 0.7x
	- Permite que el area se reduzca a la mitad(por el cuadrado)


### Costos y tiempos de disenio
Desde escritorio hasta que sale al mercado es entre 3-5 anios.
- Empezar un disenio hoy, pensando en el proceso de fabricaion que habra dentro de dos anios
	- Esto se maneja gracias a la ley de Moore
		- Esta ley es una ley *autocumplida*
		- Muchas veces se predijo el final de esta ley pero nunca pasa


### Un enfoque dominantes actualmente
#### Chiplets
Varios chips conectados entre si, dentro de un mismo empaquetado, al estilo lego.
- Se pueden combinar chips de distintos procesos 
- Al hacerlo modular lo podemos adaptar a la necesidad
**Ventaja:**
- Mejoran el yield, y la cantidad de chips por oblea lo cual hace que baje el costo
- Permite reutilizacion
**Desventaja:**
- Las interconexiones son propietarias
- Aumentan el area total
- Aniaden mas complejidad


#### Waferscale
Hicieron el chip mas grande del mundo en 2019
- Usa toda la oblea, sin cortes ni empaquetados
- Hecho en 16nm
- Este chip tenia 400000 nucleo y 18GB de memoria SRAM(cache)
Lo volvieron hacer en 2021
- Ahora con el mismo tamanio tenia 850000 nucleos y 40GB de memoria SRAM(cache)
La idea tiene como 40 anios pero recien se aplico ahora
- Este procesdaor tiene una unica funcion, es especifico para IA
- Promete una mejora de performance sin precedentes
**Desafios:**
- Yield
- Disipacion de energia(entre 15-50kW)
- Alrededor 2.5M de dolares
- No hay software generico para este


## Performance
### Performance vs feature size
Disminuir el feature size tambien hace que los transistores sean mas rapido.
Hay otrass cosas que tambien mejoran la performance(como la arquitectura)
### Que es la Performance
Nos permite elegir inteligentemente, por sobre las modas del marketing. Clave para comprender las razones de diferentes estructura de CPU. El concepto es aplicable a cualquier area, basicamente se basa en elegir lo mejor para lo que nosotros necesitamos


### Performance en computadoras. Latencia y productividad 
Lo unico importante es el **TIEMPO**
#### Definiciones
##### Latencia(tiempo de respuesta)
Tiempo total en la realizacion de una tarea
##### Productividad
Cantidad de tareas que puedo hacer por unidad de tiempo





#### Latencia vs Productividad
*Que se mejora si cambiamos el CPU de una maquina por otro mas rapido?*
- La latencia mejora seguro
- Tambien puede llegar a mejorar la productividad
- Normalmente mejoran ambas cosas
Si agregamos una computadora en un trabajo?
- En este caso mejora la productividad
- Tambien puede mejorar la latencia si tengo una cola de espera de trabajo
	- Esto es si vemos un enfoque muy general


#### Que tiempo medimos? 
Tiempo total(elapsed time)
- Cuenta todo
- En general no es bueno para comparar
	- Porque tiene una variabilidad muy grande
Tiempo del CPU
- No cuenta I/O ni el tiempo que se usa para correr programas
- Por lo tanto tampoco es buena metrica
*Tiempo de CPU del usuario*
Tiempo para ejecutar las intrucciones de mi programa
Este es buena metrica y sera en el que nos enfocaremos
<!--ID: 1679786910861-->




#### Calculo de performance
$$Performance=\frac{1}{tiempoDeEjecucion}$$
Comparacion de performance$$\frac{PerformanceX}{PerformanceY}=\frac{tiempoY}{tiempoX}$$



#### Ciclos de reloj
El ciclo de un reloj es el tiempo entre sus pulsos $T[\frac{seg}{ciclos}]$
La frecuencia de reloj es la cantidad de ciclos por segundos $1/T$


#### Calculo del tiempo de ejecucion 
Lo podemos escribir en ciclos de reloj, en vez de segundos.$$[\frac{seg}{programa}]=[\frac{ciclos}{programa}]*[\frac{segundos}{ciclo}]$$
Podemos desconponer el primer termino en:$$[\frac{ciclos}{programa}]=[\frac{instrucciones}{programa}]*[\frac{CiclosProm}{Instruccion}]$$
$$[\frac{seg}{programa}]=[\frac{instrucciones}{programa}]*[\frac{ciclosProm}{Instruccion}]*[\frac{segundos}{ciclo}]$$
Entonces:**t=CI.CPI.T**
- CPI: Ciclos promedios por instrucciones 
- CI: Cantidad de instrucciones dimanicas que se ejecutan(no que se escriben)
- T: Periodo
<!--ID: 1679786910866-->



##### Cosas que influyen el tiempo
- Si uno modifica el algoritmo(modifica CI y posiblemente CPI)
- El lenguaje de programacion(modifica CI y posiblemente CPI)
- El copilador(modifica CI y posiblemente CPI)
- El ISA (modifica CI y posiblemente CPI)
- La organizacion del HW(modifica CPI y posiblemente T)
- La tecnologia(T)
*Si cambio solo el procesador, mismo ISA y mismo programa*
--> Se mantiene constante CI
*La cantidad de intrucciones se mantiene igual si es el mismo programa, mismo ISA e igual compilador*


##### CPI
$$CPI=\frac{TotalDeCiclos}{CI}$$
$$CPI=sumatoria(CPIi*Fi)$$
- CPIi: es cantidad de ciclos de la instruccion i
- $Fi=\frac{instri}{CI}$
- El CPI nos permite analizar donde se consume el tiempo de CPU
![[Pasted image 20230321200423.png]]


#### MIPS:el triundo del marketing(no sirve)
![[Pasted image 20230321201123.png]]
Millones de Intrucciones Por Segundo
*Ejecutar muchas intrucciones no significa performance*
Porque?
*Para un mismo programa tenemos distintas cantidades de intrucciones dependiendo del ISA y del compilador*


#### Benchmarks: necesidad 
Una verdadera metrica
Surgen conjuntos estandar de programas utilizados para comparar
*Cual es el mejor benchmark?*
Depende para lo que queremos hacer.
Uso gamer casero uno de grafica
Uso de oficina uno de oficina
<!--ID: 1679786910872-->



##### Un benchmark exitoso:SPEC
Busca crear una lista standar de programas, realizar tests y reportes.
Hay para distintos usos y tipos
![[Pasted image 20230321201942.png]]
- Es gratuito
- Simple de ejecutar
- Conjunto de programas reales
- Resumino en un unico valor
- Frecuenteme revisado y respaldado



#### Ejemplo de como modifica la performance el SW
![[Pasted image 20230321202335.png]]



### Ley de Amdahl 
Es una limitacion a la mejora de performance
- Es una falacia mejorar un aspecto de la computadora y esperar que la totalidad se mejore de igual forma
	- No sirve cambiar el micro pensando que seguira mejorando
![[Pasted image 20230321202735.png]]
![[Pasted image 20230321202823.png]]
- f es la frecuencia con la que se hace la tarea que mejoramos
- p es cuanto mejoramos esta tarea
- A es la acelaracion de tiempo
<!--ID: 1679786910878-->



## Consumo de energia
En tecnologia [[CMOS]], cada transicion logica disipa energia(ver energia dinamica):
$$P=N*A*C*V^2*f$$
- N es la cantidad de transistores
- A es el factor de actividad, la probabilidad promedio de que un transistor transicion
- C es la capacitancia de carga promedio
- V es la tension de alimentacion
- f es la frencuencia de reloj
Para bajar la energia:
- Bajar f
	- No es deseable porque sera mas lento
	- Ademas terminara gastanto la misma cantidad para iguales tareas
- Bajar V
	- Aumenta el delay
	- Menor toleracia al ruido
- Bajemos N
	- Empeora el trabajo
- Disminuir C
	- Se hace constantemente-depende de la tecnologia
### Consumo de energia y ley de moore
![[Pasted image 20230322195358.png]]
Achicar los transistores diminuye el consumo, pero tiene una limitacion y es muy costosa.
### Ley de Dennard scaling
Disminuir el area 0.7 produce:
- Se reducia la tension de los transistores, la capacitancia y los retardos de propagacion
- Esto implica que se podia aumentar la frecuencia, manteniendo el consumo de energia constante
#### Fin de dennard scaling
Esto paso en 2006, porque:
- Cuando los transistores se hicieron muy pequenios, perdio validez
- Aparecian corriente de perdida, tensiones de umbral.
--> Para mantener la ley de moore se aumento el consumo de energia
![[Pasted image 20230322222404.png]]
Entonces tuvieron que bajar la frecuencia para que la energia no suba exponencialmente.
A esto lo llamaron *The power wall*(La pared de consumo de energia). Para solucionar esto cambiaron el paradigma, esto posibilito la aparicion de:
- Cloud computing: Mega servidores, grandes instalaciones(nubes)
- IoT: Sistemas embebidos conectados a internet
##### Falacia de la carga de trabajo
El consumo de energia no es lineal con la carga de trabajo. Si una notebook no hace nada, solo duraria el doble la bateria.
##### Otras implicancias 
En servidores la disipacion de calor limite la cantidad de equipos que pueden colocarse en la sala. La disipacion de calor aumenta la cantida de fallas y la tarifa electrica suele ser muy alta
En dispositivos portatiles son muy grandes(respecto al equipo) y muy peligrosas
