- Una red inalambrica es la conexion de nodos por medio de ondas electromagneticas, sin necesidad de una red cableada o alambrica.

## Bluetooth
Bluetooth utiliza una técnica llamada Frequency Hopping Spread Spectrum (FHSS), que permite la transmisión de datos en una banda de frecuencia amplia dividiéndola en canales más estrechos y cambiando rápidamente de un canal a otro. El objetivo de utilizar el salto de canales y la elección de los mejores canales en Bluetooth es garantizar una comunicación confiable y robusta, incluso en entornos con múltiples dispositivos Bluetooth y otras fuentes de interferencia inalámbrica.
1. Selección de canales: Bluetooth utiliza una tabla de salto de frecuencia predefinida que determina qué canales se utilizarán durante la comunicación. La especificación Bluetooth clásica utiliza 79 canales disponibles numerados del 0 al 78. Estos canales cubren toda la banda ISM de 2.4 GHz.
2. Secuencia de salto de canales: Los dispositivos Bluetooth siguen una secuencia de salto de canales común para establecer la comunicación. Esta secuencia es pseudoaleatoria y se genera utilizando un algoritmo específico. A medida que los dispositivos se comunican, ambos siguen la misma secuencia de salto de canales para estar sincronizados.
3. Salto de canales: Durante la transmisión de datos, los dispositivos Bluetooth cambian rápidamente de un canal a otro según la secuencia de salto. Este cambio de canal se realiza en intervalos de tiempo muy cortos, generalmente en el orden de microsegundos. El salto de canal es casi instantáneo y ayuda a evitar interferencias constantes en un canal específico.
4. Adaptación de salto de frecuencia (AFH): El algoritmo de adaptación de salto de frecuencia (AFH) es utilizado por Bluetooth para evitar interferencias en canales específicos. El AFH supervisa constantemente los canales y evalúa el nivel de interferencia en cada uno. Basándose en esta información, el AFH ajusta dinámicamente la secuencia de salto de canales para evitar aquellos canales con alta interferencia.
5. Calidad de la señal: Durante la comunicación, los dispositivos Bluetooth también realizan mediciones de calidad de señal en los canales disponibles. Esto permite evaluar la potencia de la señal, la relación señal-ruido y otros parámetros para determinar la idoneidad de cada canal. En base a estas mediciones, los dispositivos pueden seleccionar los canales con la mejor calidad de señal para transmitir datos.
### Especificaciones

|Lugar|Rango de frecuencias(GHz)|Canales|
|---|---|---|
|Casi todo el mundo|2400-2493.5|f=2402+kMHz, k=0,...,78|
|Francia|2446.5-2493.5|f=2454+kMHz|

