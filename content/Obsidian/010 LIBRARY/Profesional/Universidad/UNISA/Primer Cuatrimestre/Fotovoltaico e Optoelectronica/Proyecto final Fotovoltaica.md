## Paneles solares para la agricultura
### Precedentes
Según un estudio realizado en Alemania (1) , los proyectos agrovoltaicos siguen siendo considerablemente más caros que las plantas fotovoltaicas montadas en el suelo, debido a los mayores costes del sistema de seguimiento, los módulos especiales y el diseño del sistema. Sin embargo, estos costes pueden compensarse con los beneficios que aporta la agrovolatica, como la reduccion del consumo de agua, el aumento del rendimiento de las plantas y los paneles y la contribucion a la transicion energetica sostenible. 
Los mayores costes se deben a:
- Mayor costes del sistema de seguimiento
- Condicionamiento de las condiciones del subsuelo para el uso agricola elegido
- Preparacion del suelo para la agricultura
- Mayor inversion en el sistema para una armonica coexistencia entre la agricultura y los paneles
	- Por ejemplos los cables deben colocarse a una profundida segura de al menos un metro apra garantizar una actividad agricola sin problemas.
### Deventajas
- Aumento del costo
- Se debe encontrar un suelo que sea optimo para la agricultura y para la generacoin de energia solar
- Los paneles solares limitan de luz a la plantacion

### Ventajas 
- Reducción en la emisión de gases de efecto invernadero en el sector agrícola. 
- Doble uso del terreno para agricultura y energía alivia la presión sobre los ecosistemas y la biodiversidad, que se ven afectados cuando se amplían las zonas de cultivo.
- Aumento en más del 30 % el valor económico de las explotaciones agrovoltaicas al mejorar la eficiencia y el rendimiento del terreno, tal y como podemos observar en la infografía. Esto es especialmente válido en zonas más cálidas, donde la sombra puede proteger los cultivos bajando su temperatura y evitando una evaporación excesiva.

### Costes
	En italia existe un incentivo para este tipo de tecnologia llamado fondos PNRR que pevee contribuciones para esta tecnologia de hasta un 40%.


Para estimar los costes, tomaremos el estudio hecho por el grupo aleman, el cual tomó como proyecto de referencia una planta de 850 kW montada en el suelo con un coste total medio de 572 euros/kW y una inversión necesaria de 486.200 euros/hectárea. Los costes estimados para un proyecto agrovoltaico son:

| Planta | Coste estimado[euros/kW] | Inversion[euros/hectarea] | Coste variable[euros hectarea] |
| ---- | ---- | ---- | ---- |
| Agrovoltaica vertical | 688 | 237.760 | 5000 |
| Agrovoltaica elevada | 1234 | 802.100 | 6000 |
- Estos costes estimados son considerando una capacidad de 345,8kW obtenidas con 4 hectareas
- Tambien son costos medios ya que estos varian por zona
- Los costos variables incluyen mantenimiento, seguro, administracion, operacionc, etc.

En otro informe publicado por el Instituto Fraunhofer de Sistemas de Energía Solar ISE de Alemania, el coste nivelado de la electricidad (LCOE) de los proyectos agrovoltaicos con un plazo de 20 años situados en Alemania se estimó entre 0,07 y 0,12 euros por kWh, con un valor medio de 0,093 euros por kWh.

La TIR de los proyectos agrovoltaicos analizados en el estudio aleman oscilan entre el 2.5% y el 5.5% lo que significa que tardariamos entre 18 y 40 años en recuperar la inversion inicial

Aunque hay que tener en cuenta que estas investigaciones fueron hechas antes  de la guerra cuando el costo de energia en europa era 1/3 del actual, por lo cual ahora el TIR aumentaria significativamente 


## Analisis economico de nuestro proyecto
### Hipotesis
Para analizar nuestro proyecto debemos hacer varias suposiciones:
- Tomaremos como referencia los costos estimados por el grupo aleman para una planta agrovoltaica vertical con una capacidad de 345,8 kW
	- Estos costos son:
		- Costes estimados 688 euros/kW
		- Inversion necesaria 237.760 euros/hectareas
- Tambien estimaremos una planta de 4 hectareas, que es el numero de hectareas que se estimo en el estudio de donde se obtuvieron los datos
- Tambien hay que tener en cuenta que esta capacidad es lograda con las 4 hectareas
- Supondremos que cada hectarea nos da 1000 euros de ganancia al año ya que cada una produce 1000kg de verdura,fruta y se vende en 1 euro/kg
- Tambien supondremos una eficiencia del 100% ya que en algunos cultivos es mayor pero en otros menor
### Analisis de costo
- Si tenemos 4 hectareas, entonces nuestra inversion inicial sera de:
$$Inversion Inicial=4*237.760=951.040$$
- Nuestro costo variable sera de:
	- Este costo hace referencia a lo gastado por año luego de la inversion inicial
$$CostoVariable=5000*4=20000euros$$

### Analisis de ganancias
#### Ganancias por generacion de luz
- El precio de la electricidad hoy en dia en italia es de aproximadamente 0,32 euros/kWh sin impuestos
- Suponiendo un factor de capacidad de 0,15(osea que producimos el 15% de la potencia nominal en promedio)
$$VentaLuz=Potencia*FactorCapacidad*PrecioLuz*24*365=145.400euros$$
- Este es el precio de ganancia en las 4 hectareas
#### Ganancias por cultivos
- Al tener 4 hectareas que producen 1000kg y se venden en 1euro/kg , tendremos una ganancia de:
$$VentaAgricola=1000*1*4=4000$$
- Entonces la venta agricola nos da 4000 euros

#### Ganancia total
$$GananciaTotal= 145400+4000=149400 euro$$
### Balance general

|Año|Ingresos (€)|Gastos (€)|Balance (€)|
|---|---|---|---|
|0|0|951,040|-951,040|
|1|149400 |20,000|129400|
|2|149400|20,000|129400|
|3|149400|20,000|129400|
|4|149400|20,000|129400|
|5|149400|20,000|129400|
|6|149400|20,000|129400|
|7|149400|20,000|129400|
|8|149400|20,000|129400|
|9|149400|20,000|129400|
|10|149400|20,000|129400|

Con una inversión inicial de 951,040 €, gastos variables anuales de 20,000 € y unos ingresos anuales de 149400 € se obtiene:
- Se alcanza el punto de equilibrio luego de 7 años
- La tasa interna de retorno es del 13.6%
- Hay que tener en cuanta que este modelo no es muy representativo ya que estamos en una situacion actual donde el precio de la electricidad es elevado y no estamos teniendo en cuenta ciertas cuestiones a la hora del analisis, es por eso que el valor del TIR nos da mayor.

## Referencia
1. [Microsoft Word - Linea Guida Agroftv_25_11_2021_VDS.docx (qualenergia.it)](https://www.qualenergia.it/wp-content/uploads/2022/01/linee-guida-agrovoltaico.pdf)