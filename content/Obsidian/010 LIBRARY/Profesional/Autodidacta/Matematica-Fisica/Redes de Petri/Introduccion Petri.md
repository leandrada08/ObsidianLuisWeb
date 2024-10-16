# Introducción Redes de Petri

Los controladores lógicos programables (PLCs) son computadoras diseñadas para trabajar en ambientes industriales. En el año 1968, la división hidronomática de General Motors trabajó en un proyecto para desarrollar un sistema digital programable que permitiera flexibilizar las líneas de producción de automóviles y librarse del mantenimiento que requerían los paneles de relés. Además, la programación del computador industrial debía ser hecha en forma gráfica, simulando los diagramas escalera de los relés, con la finalidad de que la lógica fuera transparente a los técnicos e ingenieros de planta. La diferencia entre los PLC y los micros, es que estos primeros están hechos para trabajar en lugares hostiles. Ciertos procesos productivos industriales corresponden a sistemas dinámicos de eventos discretos (DEDS), los cuales pueden ser maniobrados y/o supervisados por uno o varios controladores de eventos discretos. A nivel industrial, el controlador de eventos discretos (DEC) se implementa usualmente con PLCs. Existen varios métodos formales para definir algoritmos de control, entre ellos, la teoría de autómatas finitos, la lógica temporal, el lenguaje Z, etc. Sin embargo, estas técnicas no son utilizadas ni aceptadas por fabricantes de PLC para la programación de sus productos. Los fabricantes han estandarizado sus lenguajes en la norma IEC 61131-3 [21], pero dicha norma sólo describe los lenguajes, no las metodologías de diseño. Se ha adoptado el Grafcet como aproximación en la norma IEC 60848 [19], pero ésta carece de partes esenciales en el diseño de algoritmos para controladores, tal como el levantamiento de requerimientos, los criterios de aceptación, el proceso de validación del algoritmo, etc. En el área de las ciencias de la computación, surgen en 1962 las Redes de Petri (PN) en la tesis de disertación de Carl Petri. Las PN son un formalismo matemático para el modelado del flujo asincrónico de información.
El éxito de las redes de Petri se debe básicamente a la simplicidad de su mecanismo básico, si bien, la representación de grandes sistemas es costosa.
Numerosos autores han extendidos el modelo básico:
- Rede de Petri temporizadas
	- Introducen el tiempo para modelar el comportamiento temporal de los sistemas dinamicos
- Redes de Petri estocásticas
	- Se especifica el comportamiento temporal con variables aleatorias exponenciales
- Redes de Petri coloreadas
	- A los testigos se le añade atributos que se denominan color. Permite modelar sistemas concurrentes descritos mediante flujos de datos
## Comparación con diagrama de transición

|Diagrama de estado | Redes de Petri|
|----------------------|----------------|
|Se vuelve complejo cuando se trata de sistemas recurrentes | Facilidad para analizar y modelar sistemas recurrentes, permitiendo ver la dependencia entre los elementos, refinar el modelo y obtener una composición modular|
|No se pueden implementar sistemas a partir del modelo | Capacidad de implementar el sistema a partir del modelo|
|No se puede validad un sistema | Capacidad de validad el sistema contra patologías (bloqueos, inestabilidades, ilimitaciones, etc)|
|No permite un análisis completo del comportamiento | Análisis de comportamiento temporal, velocidad, frecuencia, utilización de recursos, etc. Sin necesidad de simulación o ejecución de pruebas|
|| Posibilidad de análisis y animación mediante simuladores basados en eventos discretos|

## Ejemplo
Al Pulsar M ambos carros se desplazan a la derecha. El regreso lo hacen simultaneamente cuando ambos carros se encuentren en el extremo derecho.
![[Pasted image 20230223185917.png]]
### Con 2 carros
#### Con Diagrama de Estado
![[Pasted image 20230223185821.png]]
#### Con Red de Petri
![[Pasted image 20230223185757.png]]

### Problema para diagrama de estado
- Para N carros necesitamos $2^{N+1}-1$ estados
- Mientras que en petri por cada carros que agregamos solo tenemos que agregar 2 lugares y 1 transicion

### Con 3 carros
#### Diagrama de estado
![[Pasted image 20230223190106.png]]
#### Redes de Petri
![[Pasted image 20230223190631.png]]




