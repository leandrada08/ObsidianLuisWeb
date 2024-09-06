
## Introducción
![[Pasted image 20240515104153.png]]
Para estudiar la conducción eléctrica en gases, consideremos un gas contenido en una ampolla de vidrio con dos electrodos en sus extremos conectados a un circuito externo. Este circuito consta de una fuente de tensión de corriente continua (CC) variable en serie con una resistencia limitadora de corriente "R". El electrodo positivo es el ánodo, mientras que el negativo es el cátodo. Los gases utilizados son típicamente gases nobles químicamente inertes, como el helio, neón, argón y xenón.

## Fenómenos Involucrados

### Excitación e ionizacion
La excitación eleva un electrón a un estado energético superior, mientras que la ionización implica extraer un electrón del átomo. El potencial crítico es la energía mínima para elevar un electrón al siguiente nivel, y el potencial de ionización es la energía necesaria para liberar completamente un electrón del átomo
- La energía absorbida es igual a la energía emitida cuando el electrón regresa a su estado estable de menor energía.
- La energía de excitación debe corresponder a la diferencia de energía entre los dos niveles.
- Los átomos pueden permanecer en estado excitado por un tiempo muy breve, inferior a 10^-8 segundos, antes de que el electrón retorne a su estado estable.
- Un electrón que se mueve en el seno de un gas con una energía cinética menor al Potencial crítico al chocar con un átomo, rebotará elásticamente, sin cambio apreciable en su energía, puesto que la masa del átomo es muy grande frente a la del electrón.

**Choque elastico:**
![[Pasted image 20240515104223.png|300]]
**Exitacion e ionizacion**![[Pasted image 20240515105202.png]]



### Excitación y Ionización Fotónica
Tanto la excitación como la ionización pueden ser inducidas por radiación fotónica ($hf$). 
- La excitación fotónica requiere un fotón con energía igual a la diferencia de energía entre niveles, mientras que la ionización fotónica necesita un fotón con energía superior a la de ionización y el exceso de energía se convierte en energía cinética del electrón liberado. 
- En ambos casos, el fotón incidente desaparece. Estos procesos requieren fotones de alta energía, typically en las regiones de ultravioleta, rayos X o rayos cósmicos.
![[Pasted image 20240515105433.png|250]]![[Pasted image 20240515105412.png|250]]
## Conducción Eléctrica
- **Recombinación:** La recombinación es el proceso inverso a la ionización, donde iones positivos se combinan con electrones para formar átomos neutros.

- **Recorrido Libre Medio:** El recorrido libre medio, también conocido como camino libre medio (clm), es la distancia promedio que recorre un electrón entre dos colisiones sucesivas.
	- La energía ganada por el electrón entre colisiones se calcula como:$$E = F\cdot clm = q\cdot E\cdot clm$$
		- Donde E es el valor del campo eléctrico.

### Potencial de Descarga y Presión del Gas
![[Pasted image 20240515104414.png|300]]
El potencial de descarga es el punto en el que se establece una corriente en el circuito debido a la ionización del gas. La presión del gas afecta el clm y, por lo tanto, la tensión necesaria para la descarga. A medida que aumenta la presión, el clm disminuye, mientras que a bajas presiones, el clm aumenta.
Si la presión se reduce mas se observa que para alcanzar la descarga disruptiva la intensidad de campo aumenta y esto es por que hay menos átomos por unidad de volumen y disminuye la probabilidad de que un electrón choque contra un átomo.
## Mecanismos de Conducción Eléctrica en Gases
![[Pasted image 20240515104447.png|500]]
![[Pasted image 20240515110835.png|500]]
### Inicio de la Descarga y Corriente de Townsend
El potencial de descarga es el punto en el que aparece corriente en el circuito debido a la ionización del gas y la creación de portadores de carga (iones y electrones). 
- Inicialmente, sin radiación ultravioleta (UV), el gas inerte dentro de la ampolla está compuesto por átomos neutros que no son afectados por el campo eléctrico creado por los electrodos.
- La radiación UV inicial ioniza los átomos, creando iones positivos y electrones. En la Región O, los electrones viajan al ánodo y los iones positivos al cátodo, completando el circuito. En la Región AB, la corriente aumenta a medida que más portadores participan en la conducción.


### Emisión Secundaria y Zona Automantenida
- Si se supera el potencial del punto "C" en la curva, el campo eléctrico es lo suficientemente intenso como para que los iones positivos, al chocar con el cátodo, puedan extraer un electrón, generando un electrón secundario. Estos electrones secundarios se suman a los existentes y pueden producir ionización por choque, aumentando el número de iones positivos y, en consecuencia, más electrones secundarios. Este es un proceso de realimentación positiva.

- En la Región CD, la tensión necesaria para mantener la corriente ahora es menor que en el punto C, y a esta tensión se le llama "Tensión de Descarga Disruptiva" o "Potencial de Ignición". La tensión disminuye hasta el punto "D", y es importante destacar que, incluso si se retira la fuente de radiación UV, la corriente persiste en esta región, por lo que se la denomina zona "automantenida" o "de descarga de Townsend".

### Luminiscencia Normal y Anormal

Después del punto "D", se observa luminiscencia en el gas. En la Región DE, conocida como zona de luminiscencia normal, la tensión permanece constante a medida que aumenta la corriente. En la Región EF, o zona de luminiscencia anormal, la tensión vuelve a aumentar para incrementar la densidad de corriente.
### Zona de Arco

Antes del punto "F", la temperatura del cátodo aumenta debido al intenso bombardeo de iones positivos. En el punto "F", la emisión de electrones es muy alta y se suma la emisión termoiónica. La Región FG es la zona de arco, donde la tensión necesaria para mantener la corriente disminuye debido a las altas temperaturas y densidades de corriente.