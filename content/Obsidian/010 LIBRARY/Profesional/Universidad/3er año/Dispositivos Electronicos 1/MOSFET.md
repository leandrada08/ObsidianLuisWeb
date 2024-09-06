



## Mosfet
**Transistor de efecto de campo** (FET)
**METAL-OXIDO-SEMICONDUCTOR**(MOS)
- El silicio tiene 4 electrones libre que completan sus uniones, sin tener cargas libres, pero si se le coloca un elemento con 3 electrones libres, logran tener un hueco y si se le agrega un elemento con 5 electrones libres, logra tener un electron libre
- Es muy importante la pureza del silicio, por eso el esfuerzo en su fabricacion
## Mosfet Canal N Enriquecimiento
## Estructura fisica
![[Pasted image 20230225203320.png]]
- *Vgs* Regula el canal
- *Vds* produce la corriente entre drenador y fuente
### Modos de operacion
![[Pasted image 20230225203644.png]]
#### Corte
- *Vgs<Vth* --> No circula carga por el canal
- El mosfet se comporta como una resistencia de valor infinito
- Idealmente Vth=0 pero en la realidad tiene un valor positivo
#### Ohmica
- *Vgs>Vth* y *Vgs-Vds>Vth* 
	- La segunda condicion significa que hay mas cargas disponible que las exigidas por Vds
El dispositivo entre drenador y fuente se comporta como un resistor cuyo valor es controlado por *Vgs*
$$Rds=\frac{1}{\beta(Vgs-Vth)}$$
Si consideramos la regulacion del canal, la corriente que circula es: $Ids=\beta(Vgs-Vth).Vds-\frac{\beta.Vds^2}{2}$
Donde el segundo termino correponde a la regulacion del canal
#### Saturacion
- *Vgs>Vth* y *Vgs-Vds<Vth*
	- La segunda condicion significa que hay menos cargas disponible que las exigidas por Vds
Por el circuito circula una corriente constante, se comporta como una resistencia de bajo valor.
$$Ids=\frac{\beta}{2}.(Vgs-Vth)^2$$
## Modulacion de canal
Cuando hay una gran exigencia de carga por Vds por la corriente generada, entoces el canal se comienza a cerrar, es por esto que ocurre la saturacion, pero, al cerrarse el canal se busca corriente constante pero como hay electrones muy exitados por Vds, estos logran saltar el canal, generando que la corriente si aumento, a esto lo compensanmos con el factor $\beta$ introducidos en las ecuaciones


## EAMTA
- El silicio tiene 4 electrones libre que completan sus uniones, sin tener cargas libres, pero si se le coloca un elemento con 3 electrones libres, logran tener un hueco y si se le agrega un elemento con 5 electrones libres, logra tener un electron libre
- Es muy importante la pureza del silicio, por eso el esfuerzo en su fabricacion
### Observaciones que difieren a lo que me enseniaron
- La conexion de los semiconductores genera una zona de deplexion
![[Pasted image 20230309125209.png]]
- Analisis de la foto
	- En esta foto podemos ver como el verdadero canal no es lo amarillo, ya que el semiconductor es de tipo p, lo amarillo seria como una continuacion de lo naranja que es la zona de deplexion de las uniones de los diodos, cuando se le aplica una tension lo suficientemente grande, ciertos enlances se rompen generando caminos discontinuos como vemos en rojo, que al ser discontinuos estos generan resistencia, lo ponemos ver como un diodo que esta en conduccion, el cual tiene una grande concentracion de portadores en la frontera de la zona de deflexion pero estos conjuntos de portadores es discontinuo *(introducir foto del celular)*
	- El canal formado es muy chico y hay que verlos como varias resistencias, formadas por las pocas cargas que si lograron acercarse oponiendose a la difusion
	- Cuando nuestra tension de compuerta es muy grande con respecto a la de drain, se puede ver estas pequenias resistencias como un canal uniforme
	- Cuando la tension de drain es muy grande, en cada uno de estos canales cae una tension mas grande haciendo que se estrangule el canal 
- Cuando el transistor es muy pequenio, la corriente en saturacion sigue creyendo como si no estaria en saturacion, es por eso que si queremos usar el transistor en difusion(para fuente de corriente) necesitamos que sea muy grande este transistor para que la corriente en saturacion no se modifique
- Que pasa cuando lo hago mas ancho?(Dimension que sale de la pantalla)
	- En este caso mientras mas ancho es el mosfet mas corriente circula ya que es como poner en paralelo las resistencias del canal, entonces esta corriente se hace despreciable
	- Esto tambien hace que el capacitor aumente su valor

# Nanoelectronica



## Mosfet autoallineato
- Si chiama autoallineato perche il source e il drain sono allineato con il polisilicio delle gate, ma questo no sucede
- Il source/drain si fa con PCVD
- Il ossido di campo con LCPVD
- **Cosa é un vuoto spinto?**

### NMOS passi di processo(anni 70)
- Pulizia del wafer
	- Si usa trelina, acetone e alcohol → perche?
- Crecita dell´ossido di campo
- Definizione della regione attiva
	- Deposizione del fotoresist
	- Exposizione con la prima caschera
	- Rimozione del fotoresist
	- Attacco e rimozion dell’ossido
	- rimozione del fotoresist residuo
- Crescita dell´ossido di gate
- Machera 2:Definizione del gate e impiantazione
	- Crecita del silicio policritalino ed impiantazne delle regioni di source e drain
	- Deposiz
	- ….
- Impiantazione di atomi di fosforo
- Machera 3: Deposizione dei metalli
	- Deposizione di un ossidn drogato fosfoto
	- Fusione del PSG per smussare gli spigoli
	- Sposizione del fotoresist
- Maschera 4: Definizionde delle aree dei contatti
	- Deposizione del fotoresist
	- Esposizioned el fotoresist
	- Rimozione del fotoresist


- Soluzione al problema del …. → Attaco seco → ma questo é molto costozo

## 4. Introducción a MOSFETs (Transistores de Efecto de Campo Metal-Óxido-Semiconductor)

### Principios Básicos
Los MOSFETs son dispositivos fundamentales en la electrónica moderna, utilizados para amplificar y conmutar señales eléctricas. La estructura básica de un MOSFET incluye un canal de semiconductor (generalmente silicio) entre una fuente y un drenaje, controlado por un gate separado del canal por una capa de óxido. El profesor enfatizó que los MOSFETs son cruciales debido a su capacidad para operar con bajos voltajes y corrientes, lo que es esencial en aplicaciones de alta densidad y bajo consumo energético.

### Proceso de Fabricación de MOSFETs

#### Depósito de Silicio Policristalino y Oxidación Térmica
El proceso de fabricación comienza con la deposición de una capa de silicio policristalino y la oxidación térmica para formar el óxido de gate. El profesor mencionó que es esencial remover el óxido existente antes de crecer el nuevo óxido para evitar problemas tecnológicos y garantizar un contacto eléctrico eficiente.

#### Definición de Regiones de Gate e Implantación
La definición de las regiones de gate y de implantación se realiza mediante exposición con una segunda máscara. Esto permite la implantación precisa de dopantes en las áreas designadas. El profesor señaló que la tecnología actual no permite una implantación selectiva perfecta, por lo que se debe implantar en toda la región del dispositivo.

#### Capacidad Parásita
La capacidad parásita es un problema significativo en la construcción de MOSFETs, ya que puede afectar la conmutación del transistor. Sin embargo, el profesor argumentó que es preferible tener una capacidad controlable que no tener ninguna, ya que la capacidad puede deberse a la formación de biodispositivos que dependen de la polarización.

### Técnicas de Depósito y Limpieza
El profesor también discutió las técnicas de deposición de materiales y limpieza, como la deposición química de vapor (CVD) a baja temperatura y alta velocidad de crecimiento, y la limpieza con sustancias químicas como HCl. Estas técnicas son cruciales para crear materiales con propiedades específicas y garantizar la pureza del dispositivo.

### Avances Tecnológicos y Desafíos
Los avances en la tecnología de MOSFET han permitido la creación de dispositivos más rápidos y eficientes. El profesor recordó los desafíos iniciales en el uso de ordenadores y cómo la tecnología ha avanzado significativamente, facilitando la interacción user-friendly y aumentando la velocidad y capacidad de los dispositivos.


### Fabricación de MOSFET

- **Ácido Acético:** No se puede usar como ácido menos agresivo porque corroe el mármol.
- **Problemas:**
    - **Banda Recíproca y Ataque Seco:** Mayor costo y menor eficiencia.
    - **Óxido del Gate:** Necesario remover óxido existente antes de nuevo crecimiento.

### Proceso de Fabricación

1. **Deposición de Silicio Policristalino y Oxidación Térmica:**
    - Crecimiento del óxido en el gate.
    - Exposición con segunda máscara para definir regiones de gate e implantación.
    - Remoción del resist y realización de implantación.
2. **Implantación Selectiva:**
    - No es posible actualmente; se implanta en toda la región.
3. **Capacidad Parásita:**
    - Problema en la conmutación del transistor.
    - Preferible una capacidad controlable a no tener ninguna.
    - Capacidad puede deberse a formación de biodispositivos por polarización.
4. **Implantación:**
    - Proceso controlable minimiza errores sistemáticos.

### Preguntas y Soluciones Propuestas

- **Strato Removible de Silicio:**
    - Para aumentar capacidad de sobreposición.
    - Implica costo adicional y proceso más complejo.
- **Contorno de Gate:**
    - Más grande para evitar problemas de alineamiento.



## Clase del 21/05 fin de contacto metal semicondcutor e inicio de mosfet : Transcripcion



"En la fabricación de MOSFET, no se puede utilizar ácido acético como un ácido menos agresivo, ya que corroería el mármol. El problema radica en la banda reciproca y en la técnica de ataque seco, que implica un costo mayor y una menor eficiencia en el proceso. La deposición de silicio policristalino y la oxidación térmica permiten crecer el óxido en todo el sitio de gate. Sin embargo, es necesario remover el óxido existente para evitar problemas en la tecnología.

La construcción de dispositivos MOSFET implica varios pasos, incluyendo la deposición de silicio policristalino, la exposición con una segunda máscara para definir las regiones de gate y de implantación, la remoción del resist y la implantación. La tecnología actual no permite una implantación selectiva, por lo que se debe implantar en todo el sitio.

La capacidad parásita es un problema en la construcción de dispositivos MOSFET, ya que puede afectar la commutación del transistor. Sin embargo, es mejor tener una capacidad controlable que no tener nada. La capacidad puede ser debida a la formación de biodispositivos que dependen de la polarización.

En cuanto a la implantación, es mejor tener un proceso controlable que no tener nada. La estadística nos enseña que la distribución de errores es gaussiana, por lo que es importante tener un proceso que minimice los errores sistemáticos.

Finalmente, se plantea la pregunta de si es posible crear un strato removible de silicio sobre el sitio de gate para alcanzar un margen en la implantación."


"En la fabricación de MOSFET, se puede crear un strato protector removible sobre el sitio de gate para aumentar la capacidad de sovrapposizione. Sin embargo, esto implica un costo adicional y un proceso más complicado.

El problema de la implantación selectiva se puede resolver creando un contorno de gate más grande para evitar problemas de allineamiento. La capacidad parásita es un problema en la construcción de dispositivos MOSFET, pero es mejor tener una capacidad controlable que no tener nada.

La tecnología ha avanzado mucho en los últimos años, permitiendo la creación de dispositivos más rápidos y eficientes. Recuerdo cuando era estudiante y utilizaba calculadoras y programaba en BASIC. Luego, con la llegada de los ordenadores personales, todo cambió. Me compré un ordenador en 1984 por 500.000 liras, que era una gran cantidad de dinero en ese momento.

La interacción user-friendly fue una revolución en la tecnología, permitiendo a las personas utilizar ordenadores sin necesidad de ser expertos en programación. La velocidad y la capacidad de los ordenadores han aumentado mucho en los últimos años, lo que ha cambiado la forma en que vivimos y trabajamos.

Recuerdo cuando era estudiante y utilizaba los terminales de la Universidad para programar, y cómo luego me convertí en un 'abusivo' de los recursos informáticos de la agraria. La tecnología ha avanzado mucho desde entonces, y ha cambiado la forma en que vivimos y trabajamos."




