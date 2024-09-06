---
cards-deck: Profesional::Universidad::UNISA::Segundo Cuatrimestre::Nanoeletronica
---

## Definiciones
### Transductor y sensor
**Transductores:** Un transductor es un dispositivo que convierte una forma de energía en otra.
**Sensores:** Un sensor es un tipo específico de transductor que detecta o mide una magnitud física y produce una señal eléctrica proporcional a esa magnitud. 
**Diferencia:**
Mientras que un transductor puede convertir una forma de energía en otra, un sensor específicamente detecta una magnitud física y convierte esta detección en una señal eléctrica para su uso en sistemas electrónicos.
#### Ejemplos:
_Ejemplos de Transductores:_
1. **Micrófono:** Convierte las ondas sonoras en señales eléctricas que pueden ser amplificadas o grabadas. 
2. **Altavoz:** Realiza la operación inversa del micrófono, convirtiendo señales eléctricas en ondas sonoras audibles.
3. **Celda Fotovoltaica:** Transforma la luz solar en electricidad mediante el efecto fotovoltaico.
_Ejemplos de Sensores:_
1. **Sensor de Temperatura:** Detecta la temperatura del entorno y produce una señal eléctrica proporcional a ella, comúnmente utilizando termistores o termopares.
2. **Sensor de Presión:** Mide la presión de un fluido o gas y produce una señal eléctrica correspondiente, utilizando tecnologías como sensores piezoeléctricos o sensores de membrana.
3. **Sensor de Proximidad:** Detecta la presencia o proximidad de objetos cercanos sin contacto físico directo, utilizando tecnologías como infrarrojos, ultrasonido o capacitivos.
### Actuador
Un actuador es un dispositivo electromecánico que convierte una señal de control eléctrica, hidráulica o neumática en movimiento físico. Es decir, recibe una señal de entrada y realiza una acción física correspondiente en el mundo real.





## Sistema completo
### Sistema de control completo
- El sensor y el actuador son partes fundamentales para sistemas de control, en control esta en la salida de este sistema de contrl mientras que el sensor esta en la entrada



### Objetivos de nuestros sensores
- Los objetivos que seguimos es:
	- Bajo costo
	- Bajo consumo
	- Registro de informacion en poco tiempo
	- Gran especial de cobertura e remotamente
	- Miniaturizacion e integracion con circuitos de procesado en un chip(smart sensor)
	- Edge computing e inteligencia artificial integrada

- IoT: Objects equipped with sensors, processor and actuator communicate 


### Smart Sensor
![[Rete wireless#Smart Sensor (IEEE 1451.2)]]




### Ciclos de control
- **Bucle de retroalimentación de gestión de bajo nivel:** Este bucle de retroalimentación de gestión de bajo nivel se encarga de mantener el sistema en funcionamiento dentro de los parámetros deseados. Recibe como entrada el punto de ajuste proporcionado por los usuarios. Utiliza esta información para ajustar directamente los actuadores del sistema, asegurando que las condiciones medidas se mantengan lo más cerca posible del punto de ajuste deseado.
- **Bucle de retroalimentación de gestión de alto nivel:** Este bucle de retroalimentación de gestión de alto nivel implica decisiones más estratégicas tomadas por los usuarios basadas en la información recopilada por los sensores y las previsiones. Los usuarios utilizan esta información para tomar decisiones sobre la configuración y los puntos de ajuste del sistema. Por ejemplo, pueden ajustar los límites de operación del sistema o establecer puntos de ajuste basados en la información del sensor y las proyecciones futuras.




## Clasificacion de sensores

### Clasificacion general
- **Sensores de procesos:**
  - *Flujo:* Miden la velocidad o el volumen de un fluido que pasa por un punto específico.
  - *Nivel:* Detectan y miden el nivel de un líquido o material sólido dentro de un contenedor.
  - *Temperatura:* Registran la temperatura de un entorno o de un objeto específico.
  - *Presión:* Midenn la presión de un fluido o gas en un sistema.
  - *Vacío:* Detectan la ausencia de presión o la presión por debajo de la atmósfera estándar.
- **Sensores de posiciones:**
  - *GPS:* Utilizan señales de satélites para determinar la posición geográfica precisa.
  - *Potenciómetro:* Proporcionan una señal eléctrica proporcional a la posición mecánica de un componente.
  - *Radar:* Emplean ondas de radio para determinar la distancia y la velocidad de objetos distantes.
  - *Sonar:* Utilizan ondas sonoras para detectar objetos bajo el agua y calcular distancias.
  - *Altimetro:* Miden la altitud de un objeto en relación con un punto de referencia.
- **Sensores de movimiento:**
  - *Giroscopio:* Miden la velocidad angular y orientación de un objeto.
  - *Acelerómetro:* Detectan cambios en la velocidad o aceleración de un objeto.
  - *Velocímetro:* Midenn la velocidad de un objeto en movimiento.
- **Sensores ergónicos:**
  - *Táctiles:* Detectan y responden al contacto físico con un objeto.
  - *Ópticos:* Utilizan luz para detectar objetos, cambios de posición o condiciones.
  - *Acústicos:* Detectan y miden sonidos o vibraciones en el entorno.
- **Sensores químicos:**
  - *Espectrómetro de masas:* Identifican y cuantifican compuestos químicos basados en su masa molecular.
  - *pH:* Miden el nivel de acidez o alcalinidad de una solución.
  - *Conductividad:* Midenn la capacidad de una sustancia para conducir corriente eléctrica.
  - *Humo:* Detectan la presencia de partículas en suspensión en el aire.
  - *Oxígeno (O2):* Miden la concentración de oxígeno en un entorno.
  - *Hidrógeno (H2):* Detectan la presencia de hidrógeno en el aire.
  - *Dióxido de nitrógeno (NO2):* Midenn la concentración de dióxido de nitrógeno en el aire.

- **Sensores eléctricos:**
  - *Voltímetro:* Miden la diferencia de potencial eléctrico entre dos puntos.
  - *Amperímetro:* Midenn la intensidad de corriente eléctrica en un circuito.
  - *Detector de metales:* Detectan la presencia de objetos metálicos en un área determinada.
  - *Efecto Hall:* Detectan campos magnéticos mediante el efecto Hall.


### Clasificacion basadas en:
- **El tipo de medida o mecanismo de transducción:**
  - *Físicos:* Detectan y miden magnitudes físicas como temperatura, presión, flujo, etc.
  - *Químicos:* Responden a cambios en la composición química del entorno, como la concentración de ciertos compuestos.
  - *Biológicos:* Detectan y miden procesos biológicos, como la presencia de biomoléculas, células o microorganismos.
- **El estímulo:**
  - *Acústico:* Detectan y responden a ondas sonoras o vibraciones en el entorno.
  - *Eléctrico:* Convierten cambios en campos eléctricos o corrientes en señales eléctricas medibles.
  - *Óptico:* Utilizan la luz visible o invisible para detectar cambios en la intensidad, el color, la posición o la forma de los objetos.
  - *Magnético:* Detectan y responden a cambios en campos magnéticos en el entorno.
  - *Mecánico:* Responden a fuerzas mecánicas, movimientos o deformaciones en el entorno.


### Clasificaciones basadas en la energía requerida:
- **Activo/modulante:**
  - Estos sensores requieren una fuente de energía externa para operar. Utilizan esta energía para generar señales de salida que varían en función de la magnitud medida o para modular una señal de salida continua en respuesta a cambios en el entorno.
- **Pasivo/auto-generador:**
  - Estos sensores no requieren una fuente de energía externa para operar. Utilizan la energía del entorno o del fenómeno que están midiendo para generar señales de salida. Por ejemplo, los sensores termoeléctricos pueden generar una señal eléctrica en respuesta a cambios de temperatura sin necesidad de energía externa.


### Clasificaion basada en la referencia
- **Absoluta:**
  - Estos sensores proporcionan mediciones directas en relación con una referencia absoluta o fija. La salida del sensor se relaciona directamente con una escala de medición estándar, como la escala Kelvin en el caso de la temperatura.
    - Ejemplo:
      - **Termistor:** Su resistencia eléctrica se relaciona directamente con la temperatura absoluta en la escala Kelvin.
- **Relativa:**
  - Estos sensores proporcionan mediciones en relación con una referencia que puede variar o ser relativa. La salida del sensor se relaciona con un cambio en la magnitud medida en lugar de proporcionar una medida absoluta.
    - Ejemplo:
      - **Termopar:** Produce un voltaje eléctrico que es función del gradiente de temperatura a lo largo de los cables del termopar, sin proporcionar una medida directa de la temperatura absoluta.



### Clasificacion segun la manera de medir
1. **Sensor Directo:** Un sensor directo mide la magnitud física de interés directamente, sin necesidad de ningún tipo de conversión adicional.
2. **Sensor Indirecto:** Un sensor indirecto mide la magnitud física de interés mediante la detección de algún cambio secundario que está relacionado con la magnitud deseada. 




## Principales parámetros del sensor: #tarjeta-anki 
**Características estáticas:**
- **Función de transferencia o curva de respuesta:**
    - **Linealidad:** La relación entre la entrada y la salida del sensor es proporcional y constante.
    - **Histéresis:** La respuesta del sensor depende de su historia pasada, especialmente cuando la magnitud medida varía en ambas direcciones.
    - **Sensibilidad:** La capacidad del sensor para detectar cambios en la magnitud medida.
- **Resolución:**
      - **Sensibilidad:** La menor variación detectable en la magnitud medida.
      - **Relación señal-ruido (SNR):** La relación entre la señal deseada y el ruido de fondo.
    - **Precisión:** La cercanía entre el valor medido y el valor real.
    - **Errores sistemáticos:** Desviaciones predecibles entre la salida del sensor y el valor real debido a condiciones ambientales o diseño del sensor.
    - **Errores aleatorios (ruido):** Variaciones impredecibles en la salida del sensor debido a factores aleatorios.
    - **Repetibilidad:** La capacidad del sensor para producir el mismo resultado en mediciones repetidas bajo las mismas condiciones.
    - **Reproducibilidad:** La capacidad del sensor para producir resultados similares en mediciones repetidas realizadas en diferentes condiciones.
    - **Estabilidad:** La capacidad del sensor para mantener su calibración y rendimiento a lo largo del tiempo.
    - **Selectividad:** La capacidad del sensor para responder solo a la magnitud medida y no a otras variables.
^1719992515668

**Características dinámicas:**
- **Velocidad de procesamiento/respuesta:**
	- **Retardo de respuesta y error dinámico:** El tiempo que tarda el sensor en responder a cambios en la magnitud medida y el error asociado con este retardo.
- **Sensor de orden cero (ideal):**
	- **Función de transferencia independiente del tiempo:** La respuesta del sensor no depende del tiempo.
- **Sensor de primer orden:**
	  - La respuesta del sensor sigue una función exponencial, con una fase de transición gradual.
- **Sensor de segundo orden:**
	  - La respuesta del sensor es más compleja que la del sensor de primer orden, con una fase de transición más pronunciada.



## Sensor resistivo #tarjeta-anki 
Un sensor resistivo convierte la variación de un fenómeno no eléctrico en una variación de resistencia. La fórmula básica para la resistencia $R$ en función de la longitud $l$, el área $A$, y la resistividad $\rho$ del material es:
$$R = \frac{\rho l}{A}$$
Diferenciando esta ecuación, obtenemos:
$$\frac{dR}{R} = \frac{dl}{l} - \frac{dA}{A} + \frac{d\rho}{\rho}$$
### Sensor potenciométrico
- Consiste en un elemento resistivo provisto con un contacto deslizante, llamado cursor, utilizado como sensor de desplazamiento.
#### Ventajas
- **Simplicidad:** Los sensores potenciométricos suelen ser simples y fáciles de fabricar.
- **Costo:** En comparación con otros tipos de sensores, los potenciómetros pueden ser más económicos.
- **Buena resolución:** Pueden tener una alta resolución dependiendo del diseño y la calidad del potenciómetro.
- **Buena linealidad:** Suelen tener una respuesta lineal, lo que los hace adecuados para muchas aplicaciones de medición.
#### Desventajas
- **Desgaste:** El desgaste del contacto deslizante puede afectar la precisión y la vida útil del sensor con el tiempo.
- **Sensibilidad a la suciedad y la humedad:** La presencia de suciedad o humedad puede afectar negativamente el funcionamiento del potenciómetro.
- **Limitaciones de rango:** Algunos potenciómetros pueden tener un rango limitado de medición en comparación con otros tipos de sensores.
- **No apto para ambientes extremos:** No son ideales para entornos con alta temperatura, alta humedad, vibraciones intensas o exposición a productos químicos corrosivos.
### Termorresistor
También conocido como RTD (Resistance Temperature Detector), explota la característica de los metales para variar su conductividad con la temperatura.
#### Tipos de RTD:
1. **Bobinado de alambre (Wire wound):** Consiste en un alambre de platino enrollado alrededor de un núcleo cerámico o de vidrio.
2. **Elemento enrollado (Coiled element):** Utiliza un alambre de platino enrollado en forma de espiral.
3. **Película delgada (Thin film):** La resistencia de platino se deposita en un sustrato cerámico en forma de película delgada.
#### Método indirecto:
Se suministra una corriente y se mide el voltaje resultante.
#### Método directo:
Se utiliza un puente de Wheatstone para medir la resistencia del RTD.
#### RTD de platino
Los RTD típicamente muestran un aumento en la resistencia con el aumento de la temperatura.
### Termistor
Explota las propiedades eléctricas de los semiconductores para variar su conductividad con la temperatura.
- **NTC (Coeficiente de temperatura negativo):** La resistencia disminuye con el aumento de la temperatura.
- **PTC (Coeficiente de temperatura positivo):** La resistencia aumenta con el aumento de la temperatura.
#### Ventajas:
- Mayor sensibilidad y resolución en comparación con los RTD.
- Sensor integrable y económico.
#### Desventajas:
- Alta impedancia.
- Fuertemente no lineal en su respuesta a la temperatura.
### Sensores piezorresistivos
![[Pasted image 20240703094055.png]]
La piezorresistividad es el acoplamiento entre el estrés mecánico y la resistividad eléctrica.
- Se explota como mecanismo de transducción en varios sensores:
  - Acelerómetros
  - Galgas extensiométricas
  - Sensores de vibración y presión
Los sensores piezorresistivos se basan en una capa delgada de metal nanoestructurado depositada sobre un filamento de polímero no conductivo o sobre semiconductores dopados.
#### Principio de funcionamiento de la galga extensiométrica
Las galgas extensiométricas miden la deformación o tensión en un objeto mediante el cambio en la resistencia eléctrica cuando se someten a deformación mecánica.
### Sensor de presión orgánico para electrónica portátil 
Los sensores de presión orgánicos para la electrónica portátil detectan cambios en la presión aplicada a una superficie mediante la variación de la resistencia eléctrica de materiales orgánicos cuando se deforman bajo presión. Estos sensores son flexibles y se pueden integrar en dispositivos portátiles como teléfonos inteligentes y dispositivos de monitoreo de la salud.
### Otros sensores resistivos
- **Fotorresistor:** Su resistencia varía con la intensidad de la luz incidente.
- **Quimiorresistivo:** Su resistencia cambia en respuesta a cambios en la composición química del entorno.
- **Higroscópico:** Su resistencia varía con la humedad ambiental.
^1719992515673


## Sensores Capacitivos #tarjeta-anki 
Los sensores capacitivos se basan en la variación de la capacitancia, que depende de la constante dieléctrica del material entre las placas, el área de las placas y la distancia entre ellas. La fórmula básica para la capacitancia es:
$$C = \epsilon_r \epsilon_0 \frac{A}{d}$$
Donde:
- $\epsilon_r$ es la constante dieléctrica relativa del material.
- $\epsilon_0$ es la permitividad del vacío.
- $A$ es el área de las placas.
- $d$ es la distancia entre las placas.
#### Métodos para Variar la Capacitancia
1. **Variación de la Constante Dieléctrica**: Se puede construir un sensor capacitivo variando la constante dieléctrica del material entre las placas. Esto es útil en aplicaciones como la medición de nivel de líquidos o la pureza de estos, ya que diferentes líquidos o soluciones tienen diferentes constantes dieléctricas.
2. **Modificación de la Distancia entre Placas**: Cambiar la distancia $d$ entre las placas es una manera común de variar la capacitancia. En aplicaciones como sensores de presión, la distancia entre placas cambia con la presión aplicada, alterando la capacitancia.
3. **Modificación del Área de las Placas**: Aunque modificar el área de las placas $A$ es más complicado, a veces se emplea desplazando lateralmente las placas para cambiar el área frontal efectiva.
#### Configuración Diferencial
- **Configuración Lineal**: Utiliza dos capacitores con dos placas fijas y una placa intermedia que se mueve. La capacitancia varía de 0 a 2 veces el valor inicial, dependiendo de la posición de la placa móvil.
- **Configuración Hiperbólica**: Consta de tres placas en paralelo, donde la placa intermedia se mueve. La capacitancia varía desde la mitad del valor inicial hasta infinito.
### Ejemplos de Sensores Capacitivos
1. **Sensores de Nivel de Líquidos**: Miden el nivel de un líquido o su pureza al detectar cambios en la constante dieléctrica.
2. **Sensores de Humedad**: Detectan la humedad a través de cambios en la constante dieléctrica del aire o de un material absorbente.
3. **Estructuras Coplanares con Electrodos Integrados (IDE)**: Estos sensores miden cambios en la impedancia debidos a la variación en las líneas de campo, las cuales dependen de la frecuencia de la señal y del medio donde se encuentran los electrodos.
4. **Acelerómetros**: Funcionan con una masa móvil que actúa como una placa del capacitor. La aceleración provoca un cambio en la distancia entre la masa móvil y las placas fijas, alterando la capacitancia.
5. **Sensores de Presión**: La presión cambia la distancia entre las placas, variando la capacitancia.
6. **Micrófonos Capacitivos**: Detectan el sonido por la variación de la capacitancia debido al movimiento de una membrana en respuesta a las ondas sonoras.
7. **Micrófonos MEMS**: Similar a los micrófonos capacitivos, pero en una escala microelectromecánica, proporcionando mayor sensibilidad y precisión.
8. **Giroscopios MEMS**: Utilizan una masa conectada a una estructura interna que rota, midiendo los cambios en la capacitancia debido a la fuerza centrífuga.
### Fabricación de MEMS
Los dispositivos MEMS (Microelectromechanical Systems) se fabrican utilizando técnicas de micromecanizado que permiten la integración de componentes mecánicos y eléctricos en una escala microscópica. Estos dispositivos pueden incluir sensores capacitivos como acelerómetros, giroscopios y micrófonos, proporcionando alta precisión y funcionalidad en aplicaciones compactas.
### Consideraciones Adicionales
- **Estabilidad**: Los sensores capacitivos deben estar protegidos contra factores ambientales como temperatura, humedad y oxidación para mantener su precisión.
- **Linearidad**: Es importante diseñar los sensores para mantener una relación lineal entre la variable medida y la capacitancia, aunque en algunos casos se pueden usar métodos para linearizar las señales.
Estos sensores son ampliamente utilizados en diversas aplicaciones debido a su alta sensibilidad, capacidad de miniaturización y posibilidad de integración en sistemas complejos.
^1719992515678
