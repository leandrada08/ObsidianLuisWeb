---
cards-deck: Profesional::Universidad::UNISA::Sistemi di interfaccia::Multirampa
---


## Conceptos
La *resolución absoluta* de un convertidor ADC se refiere a la *precisión con la que puede convertir una señal analógica en una representación digital*. Esta resolución *se expresa normalmente en bits y se refiere a la cantidad de valores distintos que el convertidor puede generar*. Por ejemplo, un convertidor de 8 bits tiene una resolución absoluta de 256 niveles.

La *resolución relativa* de un convertidor ADC se refiere a la *precisión con la que puede detectar cambios pequeños en una señal analógica*. Esta resolución *se expresa normalmente en bits y se refiere a la capacidad del convertidor para detectar cambios en una señal dada*. Por ejemplo, un convertidor con una resolución relativa de 8 bits puede detectar cambios de 1 parte en 256 en una señal dada. $$\frac{\Delta V}{V_{in}}$$
## ADC a rampa analogica
Lo que caracteriza a este tipo de ADC es que la tensión de referencia varía linealmente según una pendiente. 
- Esto es posible gracias a la presencia de un generador de rampa analógica, que consta de un generador ideal de corriente conectado a un transistor y un condensador. 
- De hecho, si el transistor está apagado, toda la corriente va a las placas del condensador, que se carga con una pendiente lineal creciente. Mientras tanto, cuando el transistor está saturado, el condensador se descarga, creando una verdadera rampa.

Existen dos formas ligeramente diferentes de implementar el circuito, dependiendo de si la pendiente de la rampa es positiva o negativa.

### Pendiente Negativa
El generador de rampa está conectado a la entrada de dos comparadores. En particular, está conectado a la entrada inversa del comparador $C_{o1}$ y a la entrada no inversa del comparador $C_{o2}$. $C_{o1}$ *compara el valor instantáneo* de la rampa de tensión VR salida del generador con la tensión analógica desconocida a convertir $V_X$, mientras que $C_{o2}$ la compara con Gnd (0 voltios). *El resultado de la comparación de Co1 es un nivel lógico alto (H) si $V_X$ ≥ $V_R$ o bajo (L) si $V_X < V_R$.*
![[Pasted image 20240125100805.png]]

En cuanto a $C_{o2}$, produce un nivel lógico alto (H) si $V_R ≥ 0 V$, o bajo (L) si $V_R < 0 V$.
Las salidas de los dos comparadores convergen en la entrada de una puerta XNOR que actualiza su salida según la tabla de verdad
![[Pasted image 20240125100757.png]]

El valor lógico obtenido se ingresa a un bloque de circuito que controla la conmutación de un interruptor y está conectado a su vez a un oscilador local. Específicamente, dependiendo de si el valor lógico es alto (H) o bajo (L), el interruptor se cierra o se abre, permitiendo o impidiendo el paso de la onda sinusoidal generada por el oscilador local.

En serie con él se coloca un contador, habilitado inicialmente junto con el generador de rampa mediante una señal de reinicio enviada por un circuito de sincronización. El contador cuenta los periodos de esta señal hasta la nueva apertura del interruptor.

En la figura siguiente se muestra la evolución temporal de la tensión en el circuito.
![[Pasted image 20240125100907.png]]

Se puede observar que en el estado inicial del circuito, la salida de $C_{o1}$ es baja (L) porque la rampa parte de un valor de $V_R > V_X$. Sin embargo, la salida de $C_{o2}$ es alta porque $V_R > 0V$. El interruptor está abierto y el contador se reinicia mediante el circuito de sincronización.

Desde el instante inicial hasta tstart, el interruptor permanece abierto y el circuito permanece "congelado" en el estado inicial. Posteriormente, a tstart, se cumple la condición: $V_X ≥ V_R$ y esto hace cambiar la salida de $C_{o1}$ (de L a H). El interruptor permite entonces el paso de la señal generada por el oscilador hacia el contador, que comienza a contar los periodos. Esto persiste mientras $V_R$ permanece positivo, después de lo cual la salida de $C_{o2}$ se vuelve baja e inhibe, a través de la XNOR, el interruptor y, por lo tanto, el contador.

El resultado es un código n0 (número de pulsos de reloj contados), proporcional a la tensión presente en la entrada. Esto se puede deducir fácilmente mediante una proporción basada en la evolución temporal de la tensión; de hecho, se cumple que:
$\frac{V_X}{R}=\frac{\Delta T_x}{\Delta T}$ donde $R$ es el máximo valor asumido por la rampa (correspondiente al rango de entrada del ADC), $\Delta T_x$ es el intervalo de tiempo en el que $0 < VR < VX$, y $T$ es el intervalo de tiempo total de conversión. De esto se deduce que $V_X = \frac{R}{\Delta T}.\Delta T_x$, donde $\frac{R}{\Delta T}$ es la pendiente de la rampa.

### Pendiente Positiva
![[Pasted image 20240125102045.png]]
En el caso de una pendiente positiva, la salida del generador de rampa se conecta a ambos terminales no inversores de los comparadores, que la comparan respectivamente con la tensión de entrada desconocida $v_x$ y con Gnd (0 V). *La salida del comparador 1 es alta si la tensión de entrada es menor que la tensión de referencia, mientras que es baja en el caso complementario. La salida del comparador 2 es alta si la tensión de referencia es mayor que cero, y baja en el caso complementario*.

El valor lógico en la salida del primer comparador entra en un flip-flop, que guarda el valor lógico recibido y lo coloca (negado) en la entrada de una puerta AND, cuyas otras entradas son respectivamente una señal de reloj y la salida del segundo comparador. La puerta AND multiplica los tres señales de entrada, permitiendo o no el paso de la señal de reloj dependiendo del valor lógico de las otras dos entradas. Si el valor lógico es adecuado, la señal de reloj puede pasar hasta un contador de n bits que cuenta los pulsos de reloj.


En la figura se representa la evolución temporal de la tensión en el circuito. Ambas salidas de los comparadores son inicialmente bajas (L).
![[Pasted image 20240125102354.png]]

El proceso comienza con la señal SOC (Start Of Conversion) que pone a cero el contador binario y pone en marcha el generador de rampa desde un nivel de tensión ligeramente negativo. Esto evita problemas relacionados con los desplazamientos de los comparadores.

Cuando la rampa de tensión cruza el cero, la salida del comparador 2 cambia al nivel alto, permitiendo que el contador cuente los pulsos de reloj. La salida del contador se actualiza hasta que la rampa supera el nivel de la tensión desconocida $v_x$. De hecho, la salida del comparador 1 también cambia, asumiendo un valor lógico alto, e inhibiendo así, a través de la puerta AND, el conteo del contador.

Se puede demostrar, de la misma manera que se hizo para la pendiente negativa, que el número $N$ de pulsos de reloj contados por el contador es directamente proporcional a la tensión de entrada: $V_x = K \cdot N \cdot T_C$, donde $K$ es la pendiente de la rampa en voltios por segundo.

Esto destaca que el circuito (ya sea para pendiente positiva o negativa) es un convertidor de voltaje a tiempo, es decir, realiza una transformación lineal de la tensión inicial en un intervalo de tiempo determinado.

Debido a esta propiedad del circuito, el tiempo de conversión y, por lo tanto, la velocidad de conversión, dependen de la tensión de entrada y de la pendiente de la rampa. En el peor caso, *el tiempo de conversión depende de un máximo de $2^n$ pulsos de reloj*.

La precisión (y, por lo tanto, la exactitud) del sistema depende principalmente de tres factores:
1. linealidad de la rampa (no idealidad del generador de rampa);
2. estabilidad del oscilador (si está presente);
3. comportamiento de los comparadores (puede modificar los umbrales de disparo).

Este circuito también tiene una baja rechazo de ruido en comparación con los ADC normales que contienen integradores, por lo que el ruido superpuesto a la señal puede provocar conmutaciones espurias de los comparadores y el resultado de la medición puede verse afectado por errores.

Un parámetro fundamental de ambas implementaciones del circuito es el número máximo de recuentos realizado por el contador (respectivamente $N_0$ y $N$ para pendiente negativa y positiva). Esto ocurre cuando el circuito ya en el estado inicial se encuentra en la condición $v_x = v_r$, y es importante porque está estrechamente relacionado con la resolución del dispositivo. De hecho, corresponde al número de niveles de cuantización previstos para el rango de entrada del ADC, suponiendo que sea unipolar. En particular, para el circuito de pendiente negativa, la resolución $\Delta$ es:
$\Delta = \frac{R}{N_0}$
donde $N_0 = \frac{\Delta T}{T_0}$ y $T_0$ es el período de la señal sinusoidal producida por el oscilador. Por lo tanto, se puede mejorar restringiendo el rango de entrada del ADC, aumentando la frecuencia del oscilador local o aumentando la duración del intervalo de tiempo. Esta última elección tiene como consecuencia el aumento del tiempo de conversión del dispositivo y, por lo tanto, la disminución de la velocidad de conversión del mismo.



## ADC a Doppia Rampa
### Introduccion
![[Pasted image 20240125112646.png]]
*Los ADC a doble rampa son una arquitectura que utiliza un método de conversión indirecta, conocido como conversión voltaje-tiempo*. El corazon de este dispositivo es el integrador con el compadorador. Resuelven los problemas del convertidor de rampa única y se utilizan en sistemas de adquisición de datos de alta precisión. En la figura se muestra el esquema general del dispositivo físico.
Problemas que resuelve:
- Mayor resolución y precisión: Al utilizar una rampa de referencia interna conocida y estable en la segunda etapa, se elimina el límite de resolución que impone la propia rampa del convertidor de 1 rampa.
- Mejor rechazo a ruido y deriva: Larampa de referencia interna también hace que el convertidor sea menos sensible al ruido y a la deriva del oscilador, mejorando la calidad de la conversión.
- Rango dinámico más amplio: En el convertidor de 1 rampa el rango dinámico está limitado por la linearidad de la rampa. En el de 2 rampas se puede ampliar utilizando una referencia estable sin perder linearidad.
- Velocidad de conversión: El de 2 rampas es más lento, pero gracias a su mayor resolución no necesita ser tan rápido para una misma precisión. Esto simplifica el diseño.

### Funcionamiento 
El ciclo de *conversión consta de dos intervalos* de integración distintos: *run-up y run-down*.
- La tension de referencia $V_R$ debe tener una polaridad que necesariamente debe ser opuesta a la de $V_X$
#### Fase Run-Up
1. En el instante $t_0$, la lógica de control *reinicia el contador* y al mismo tiempo *cambia el selector S a la posición 1*, *conectando $V_X$ a la entrada* de un integrador (RC). Tambien *la lógica de control ordena el cierre del interruptor I*, de modo que la *sinusoide producida por el oscilador de referencia pase a través del interruptor y habilite el conteo del contador*.
2. La tensión $V_X$ se integra durante un intervalo de tiempo finito, obteniendo así: $$Vo(t) = -\frac{V_x}{R_1C} \cdot (t - t_0)$$
	- Donde *$t_0$ es el instante inicial de la conversión*. 
	- *La tensión $V_o$ varía en el tiempo con una tendencia lineal decreciente y proporcional a $V_X$.*
		- $V_0$ es la salida del integrador
3. Este dispositivo *cuenta los períodos $T_O$ de la sinusoide hasta un valor límite, fijado por diseño* o en la fase de configuración, luego indica desbordamiento. 
4. Esto es detectado por la lógica de control *que abre el interruptor I*, bloqueando la señal sinusoidal y *cambia el selector S a la posición 2*. 
5. Así termina la fase de run-up después de un tiempo $T_U = N_U \cdot T_O$, donde $N_U$ es el número de períodos detectados por el contador. ($T_U$ tiene un valor típico de 100 a 200 ms)


#### Fase Run-Down
La operación de integración se realiza en la tensión $-V_R$, constante y negativa ($V_R > 0 V$). 
- Dado que $VR$ es negativa, esto provoca una disminución de la carga acumulada en el condensador $C$, y como resultado, la tensión $V?o$ asume una tendencia temporal constante y linealmente creciente. 
- Este comportamiento se manifiesta a partir del valor $V_{OM}$ previamente asumido por la tensión Vo durante la fase de run-up.

1. En el mismo instante de $V_{OM}$, la lógica de control *cierra nuevamente el interruptor I*, *permitiendo un nuevo conteo $N_D$* de los períodos de la señal producida por el oscilador.
2. *Cuando la tensión $V_0$ supera 0 V*, el comparador de cero cambia de estado. Esto es detectado por *la lógica de control que abre el interruptor I*, inhibiendo el contador y *transfiriendo el resultado del segundo conteo a la salida*. 
3. Así termina también la fase de run-down.

![[Pasted image 20240125170203.png]]
- La rampa de bajada sera siempre la misma porque depende de la tension de referencia y de la contante de integracion, las cuales son fijadas por nosotros, esto hace que tarde o temprano $V_0$ llegue a 0
- Para la segunda fase, la tensión de salida del integrador es: $$Vo(t) = -\frac{V_X \cdot T_U}{R_1 \cdot C} + \frac{V_R \cdot (t - t_1)}{R_1 \cdot C}$$
	- Donde $t_1$ es el instante de transición entre las fases de run-up y run-down.

### Desarrollo matematico
- Denotando que durante la segunda fase de integración la tensión vuelve a cero, se puede escribir: $V_o(T_u+T_d)=0$
- Entonces:
$$-\frac{V_x}{R1 \cdot C} \cdot T_U=- \frac{V_R}{R_1 \cdot C} \cdot T_D$$


- Entonces, obtemos que: $$T_D = \frac{T_U}{V_R} \cdot V_x$$
	- Donde $T_D$ es el intervalo de tiempo de la fase de run-down.

- *Se destaca la proporcionalidad directa entre $V_x$ y $T_D$.* El circuito es, por lo tanto, un convertidor de voltaje a tiempo, es decir, *realiza una transformación lineal de la tensión de entrada en un intervalo de tiempo*. Además, dado que $T_U$ y $T_D$ son conocidos en base al numero de conteo $N_U$ y $N_D$, se puede sustituir su valor en la fórmula y se obtiene:$$V_x=\frac{N_D}{N_U} \cdot V_R = K \cdot N_D$$
	- Con $K = \frac{V_R}{N_U}$, pendiente de la rampa en la fase de run-up. 
		- Nuestra variable independiente es $N_D$ y nuestra variable dependiente es $V_X$
		- **La pendiente es la resolucion**
- Esta pendiente(pendiente de fase run-down) es conocida y seleccionada por nosotros
- *Otra manera de ver este analisis es con la igualdad de la integrales*:
![[Pasted image 20240209113328.png]]
- Tau en el primer y segundo mientro estan simplificados.
	- La unica condicion de estabilidad de reloj que tenemos para que esta relacion sea siempre cierta es que sea estable en el corto plazo. Es decir, establecemos que Tau permanece estable durante el intervalo de medicion; si hay una pequeña variacion entre una medicion y otra esto no afecta la relacion, lo importante es que la estabilidad sea tal que dentro del tiempo de medicion la variabilidad de la frecuencia sea despreciable
	- Si la frecuencia cambia de un año a otro siempre encontraremos el mismo valor, en todo caso la incertitumbre cambiara

### Parametros
#### Resolucion absoluta
En esta arquitectura, la resolución $\Delta$ se define de la siguiente manera:
$$\Delta = \frac{R}{2^B} = \frac{V_R}{N_U}$$


##### Aumento de la resolucion
Puede mejorarse:
- Disminuyendo el voltaje de referencia $V_R$,
	- Esto podria generar problemas ya que el comparador de nuestro circuito tiene histeresis, si disminuimos el voltaje de referencia la recta de bajada se aplanara por lo cual sera mucho mas susceptible a esta histeresis
- Aumentando el número de periodos de la fase de run-up. 
	- Aumentando la duración del intervalo de tiempo de run-up $T_U$
	- Aumentando la frecuencia de oscilación de la señal sinusoidal producida por el oscilador de referencia. 
	- Otro problema con esta solucion que podemos generar que el Op sature
		- Para solucionar dicho problema deberiamos limitar nuestro valor de entrada lo cual no es lo ideal

>Esto se puede hacer dentro de ciertos límites; de hecho, aumentar demasiado la frecuencia de oscilación corre el riesgo de caer en una situación de inestabilidad del oscilador. También se necesita un contador adecuado, que pueda seguir rápidamente los períodos de la señal y con un cierto grado de precisión. Sin embargo, permite una alta resolución, generalmente superior a 18 bits.

#### Resolucion relativa
- El numero que varia segun varia el voltaje es ND
- Las mediciones en un intervalo de tiempo que se traducen en un tren de pulsos, la resolucion sera de un pulso
	- Donde se cuenta el numero de pulsos en nuestro circuito? En ND
$$\frac{\Delta V}{V_X}=1/N_D$$
#### Tiempo, velocidad e inmunidad al ruido
El tiempo y la velocidad de conversión dependen del intervalo de tiempo de run-up y run-down, del tiempo de espera entre las dos fases y del tiempo necesario para restablecer el circuito una vez concluido un ciclo.
- *Por lo tanto, es un dispositivo lento pero muy preciso*. De hecho, no depende de los parámetros del circuito, sino solo de $V_R$ y de los conteos del contador.
- Además, debido a la presencia del integrador, *el circuito tiene una notable capacidad de rechazo de ruido generado por la tensión de alimentación*.
Finalmente, la ausencia del DAC confiere al circuito una relativa simplicidad circuital.


### ADC de Doble Rampa con Fase de Run-up de Duración Reducida
*Para reducir el tiempo de conversión* de un ADC de doble rampa sin degradar su resolución, se adoptan *soluciones circuitales con resistencias $R_U$ y $R_D$,* que representan las *resistencias de carga y descarga del condensador*. Siguiendo el procedimiento anterior, es fácil demostrar que *se cumple la relación*:$$V_X=-V_R \cdot \frac{R_U}{R_D} \cdot \frac{N_D}{N_U}$$
![[Pasted image 20240125174416.png]]
- Al elegir $R_U$ menor que $R_D$, se logra una reducción del tiempo de run-up. Sin embargo, *el resultado de la conversión también depende de la relación entre las dos resistencias $R_U$ y $R_D$: para no reducir la precisión del ADC, es necesario garantizar la precisión de esta relación*. De todas formas, existen tecnologías actualmente capaces de permitir la realización integrada de resistencias que presentan características adecuadas.
- La resolución $\Delta_V$ y el tiempo de conversión $T_{ADC}$ que se obtienen son:$$\Delta_V=\frac{|V_R|R_V}{N_UR_D}$$

- Recordando la proporcionalidad entre tensiones y duración, también se puede escribir:$$\Delta_V=\frac{|V_R|R_U}{N_UR_D}=\frac{|V_R|}{N_D}$$

- En este caso, al igual que en el anterior, la resolución del ADC solo depende de $T_S$ y $N$
	- *La reducción de la duración de la fase de run-up no tiene influencia en ella*. La resolución aumenta al aumentar el número máximo de conteos previstos en la fase de run-down y, por lo tanto, fijando el periodo de reloj $T$, al aumentar la duración de la fase de run-down misma.

- La duración de la conversión está dada por la relación:$$T_{ADC}=\frac{\Delta_V \cdot R_D}{|V_R| \cdot R_U}$$
- Lo cual confirma que, manteniendo constantes otros parámetros, el tiempo de conversión puede reducirse eligiendo $R_U/R_D < 1$.

## ADC multirampa
### Motivacion
- Para maximizar la resolución:
	- No se puede aumentar mucho Nu porque aumenta el tiempo de conversión 
	- Tampoco reducir mucho VR porque se reduce el rango dinámico
- Por tanto, la clave está en variar la relación Ru/RD. Es decir, elegir RD lo mayor posible, siempre sin que la pendiente resultante active la histéresis del comparador.
- De esta forma, manteniendo los demás parámetros fijos, variar Ru/RD permite ajustar la resolución al máximo valor posible para una Vx dada. 
	- Esto dará el mayor número de cuentas ND en la rampa descendente y por tanto la mejor incertidumbre relativa (siempre 1/ND).


### Introduccion
Además de los ADC de doble rampa, también existen los ADC de Multirampa (multislope).
- Aguas abajo siempre se utiliza el mismo circuito ya visto en el de doble rampa
![[Pasted image 20240125170307.png]]
La etapa de entrada se presenta como un conjunto de ramas circuitales en paralelo, algunos de los cuales están conectados al potencial de referencia $V_R > 0 V$, otros al potencial $-V_R$. Una rama adicional permite la conexión del instrumento al voltaje de entrada desconocido $V_x$.
Se prepare el integrador para generar 4 rampas de pendiente 4 rampas con pendientes de 1, 10, 100 y 1000, tanto positivas como negativas. Estas rampas se indican respectivamente como $\pm S_1, \pm S_{10}, \pm S_{100}$ y $\pm S_{1000}$, donde el signo coincide con el de la tensión de referencia 1000 utilizada.
En cada rama hay un interruptor y una resistencia: el interruptor tiene la función de conectar la rama a la entrada del integrador, mientras que *la resistencia sirve para modular la intensidad de la corriente enviada al integrador*, según la rampa de voltaje deseada. Al igual que con los ADC de doble rampa, la conversión se divide en fase run up y run down. En este caso hay dos fases de run-up y dos run-down.
En comparación con los ADC de doble rampa, la aproximación a cero no ocurre en una sola fase con una sola rampa, sino en M fases a través de M rampas, una por cada dígito de resolución deseado.
### Funcionamiento
#### Libro
![[Pasted image 20240125193320.png]]

Supongamos, por ejemplo, que el valor del voltaje $V_X$ es tal que, al aplicar una rampa de pendiente unitaria en la fase de run-down, se obtiene una cuenta igual a $N_D= 6437$.

1. Solo se *cierra el interruptor $I_V$* y, suponiendo que $V_X$ sea negativo, la tensión de salida del integrador asume valores positivos, como se indica en el diagrama temporal de la figura. Se ha supuesto que el tiempo necesario para abrir y cerrar los interruptores es despreciable.
 2. *En el instante $t_V$, se abre el interruptor $I_V$ y se cierra el interruptor $I'_D$,* dando inicio a la fase de run-down; como $v_0(t_u) > 0$, la tensión utilizada durante esta fase será positiva *(rampa $+S_{1000}$).* 
	 - Dado que la *velocidad de descarga de $v(t)$ es 1000 veces la de referencia, cada evento de conteo de reloj corresponde a 1000 eventos de reloj relativos a la rampa de pendiente unitaria*. 
3. *El conteo se detiene cuando ocurre el cruce por cero de la tensión $v_s(t)$,* mientras que *la descarga, continua con esta pendiente hasta el siguiente evento del clock*(instante $t_D$’'), *donde recien se cierra $I''_D$*
4. En el instante $t'_D$, en el cual se detiene la descarga, *el conteo asume un valor de 6*, *mientras que la tensión de la rampa adquiere un valor negativo correspondiente a $7000 - 6437=563$*  conteos unitarios. 
	- La cifra más significativa del voltaje desconocido coincide así con el valor de la cuenta correspondiente a esta primera fase de la descarga.
5. En el instante $t'_D$, además de abrir el interruptor $I'_{D}$, también se cierra el interruptor $I''_{D}$, activando así la rampa $-S_{100}$. La tensión $v_s(t)$ comienza a aumentar con una velocidad igual a $1/100$ de la velocidad relativa al caso anterior. 
6. En esta segunda fase, *el conteo se detiene al ocurrir el cruce por cero de la tensión $v_s(t)$,* *mientras que la descarga se detiene en el próximo evento de reloj* (instante $t''_D$).
	- *El conteo alcanzado durante esta segunda fase es igual a 5, es decir, el complemento a 9 de la segunda cifra del voltaje desconocido*. Observando la rampa $-S_{100}$, cuando se detiene, el valor positivo asumido por $v_s(t'')$ corresponde a $600 - 563=37$ conteos unitarios.
7. *En el instante $t''_D$, se abre el interruptor $I''_D$ y se cierra el interruptor $I'''_D$, activando así la rampa $+S_{10}$.* El cruce por cero ocurre en correspondencia con el conteo 3, mientras que el valor negativo de $v_S(t)$ es igual a $40 - 17=3$ conteos unitarios.
8. Una vez activada la rampa de pendiente unitaria $-S_1$, se alcanza el cero de $v_s(t)$ en el conteo 3, que representa la cifra menos significativa del voltaje desconocido. La fase de run-down está completa.

- Se nota que el número de conteos correspondientes a rampas en posiciones pares con respecto a la primera $+S_{1000}$ proporciona
	- El complemento a 10 para la última cifra
	- El complemento a 9 para las demás cifras pares buscadas. 
- El número de conteos equivalentes obtenidos durante toda la fase de run-down es, por lo tanto: $$N_{Deq}=1000*6+100*(9-5)+10*3+1*(10-3)$$
- Mientras la duración efectiva de esta fase es: $$T_d=(7+6+4+3)*T=20T$$
	- Donde $T$ representa el periodo del reloj.

#### Catedra
- Se tienen las rampas ascendente (Ru) y descendente (RD) que optimizan la resolución como antes.
- En la rampa ascendente se integra la señal de entrada durante Nu * Tau.
- Luego en la rampa descendente en vez de usar solo RD, se usan varias resistencias para tener diferentes pendientes (RD/1000, RD/100, RD/10).
- Esto hace que se alcance el cero de tensión en muchas menos cuentas que si solo se usara RD.
- Ejemplo: para una entrada dada, con RD se necesitarían 6242 cuentas. Con RD/1000 llegan a 0 en solo 7 cuentas (N1).
- Al cambiar a RD/100 necesitan 8 cuentas más para llegar a 0 (N2).  
- Finalmente con RD/10 se necesitan 5 cuentas más (N3).
- En total solo N1+N2+N3=7+8+5=20 cuentas en lugar de las 6242 originales con solo RD.
	- Se opera matematicamente estas cuentas para conseguir el valor original
![[Pasted image 20240209125723.png]]
- Esto reduce drásticamente el tiempo de conversión manteniendo la misma resolución.
### Tiempo de conversion
- Una gran ventaja de este circuito en comparación con el ADC de doble rampa es una reducción del tiempo de conversión. Considerando dos ADC, uno multirampa y otro de doble rampa, ambos con la misma resolución $\delta$ y, por lo tanto, con un número máximo de conteos $N_0=10^{\delta}$ para el de doble rampa y un número de rampas $M=\delta$ para el multirampa, la relación de sus tiempos de conversión respectivos es:
$$\frac{T_{conv,dual}}{T_{conv,multi}} = \frac{10^{\delta} \cdot T_0}{10 \cdot T_0 \cdot \delta}=\frac{10^{\delta -1}}{\delta}$$
- Por lo tanto, el tiempo de conversión para un ADC de doble rampa es mucho mayor que el de un ADC multirampa.
![[Pasted image 20240209120223.png]]



## ADC con fase de Run-up Multirampa

### Motivaciones
- El objetivo es mejorar la resolución (número de dígitos) de un convertidor ADC multirampa, más allá de las 4 cifras decimales que se conseguían previamente.
- Un enfoque sería aumentar el tiempo de integración t1 en la rampa ascendente, ya que esto mejoraría la resolución. 
- Sin embargo, hay un problema: en la rampa ascendente se integra la tensión de entrada Vx. Si aumentamos mucho t1, la tensión de salida V_0 del integrador podría superar los límites de tensión soportados por el convertidor.
- Por tanto, lo que se explicará es una técnica alternativa para integrar Vx de forma diferente en la rampa ascendente, de modo que:
	1. Se pueda aumentar t1 para mejorar la resolución
	2. Pero manteniendo V_0 siempre por debajo de un valor máximo prefijado, independientemente del valor de Vx.
- La clave es modificar cómo se realiza la integración en la rampa ascendente. 
- Al final, esto permite resolver las limitaciones previas y obtener una resolución muy alta (8+ dígitos) sin exponer al convertidor a tensiones excesivas.






- Con los esquemas propuestos hasta ahora, para aumentar la resolución de un ADC, es decir, el número de dígitos con los que se representa la magnitud desconocida, es necesario aumentar el número de rampas utilizadas en la fase de run-down. Sin embargo, hay algunos límites en el funcionamiento de un integrador que hacen difícil la realización de convertidores capaces de determinar la tensión desconocida con más de 4 dígitos decimales. Un límite superior para la pendiente está impuesto por el slew-rate ($\frac{dv}{dt}$) propio de cada amplificador operacional. De hecho, *una vez fijada la pendiente máxima, no es posible reducir indefinidamente la pendiente mínima debido al ruido superpuesto a la señal útil*, lo que hace muy incierto determinar cuándo se produce el cruce por cero de la tensión. También existen valores máximos para la amplitud de la tensión, generalmente del orden de 100V.

### Introduccion
- *El uso de rampas de diferentes pendientes también en la fase de run-up permite ampliar tanto el rango de tensiones convertibles como la resolución*. Sin embargo, esto ocurre a expensas de un aumento, a veces de manera considerable, el tiempo de conversión.
- Para obtener más resolución también en la fase de run-up y mantener así la tensión de salida dentro de límites permitidos, el condensador del integrador se somete, además de la tensión desconocida $V_X$, a una tensión conocida $V_R$, agregando o quitando así una cantidad conocida de carga.
- El esquema de principio de esta estructura y el comportamiento temporal teórico de la tensión $v(t)$ se muestran en la fig.13.

![[Pasted image 20240125202233.png]]


### Funcionamiento
1. La tensión desconocida $V_X$ es negativa; permanece aplicada al ADC durante toda la duración de la fase de run-up, es decir, durante esta fase, el interruptor $I_X$ de la fig. siempre permanece cerrado. 
2. Se observa que si en el instante $t=0$ solo se cerrara el interruptor $I_X$, la tensión $v(t)$ aumentaría como la rampa punteada de la fig.13; en realidad, también se cierra el interruptor $I_-$ y, por lo tanto, la rampa aumenta con una pendiente $S_-$ mayor.
3. En el instante $T_p$, se detecta el signo de la tensión $v(t)$; como este resulta ser positivo, se abre el interruptor $I_-$ y se cierra el interruptor $I_+$. Dado que $V_R$ se ha elegido de valor absoluto mayor que $V_X$, cuando $I_+$ está cerrado, la tensión $v(t)$ comienza a descender con la pendiente $S_+$. 
4. En el instante $2T_P$, se vuelve a verificar el signo de $v(t)$: siendo aún positivo, el estado de los interruptores no se altera, por lo que esta tensión desciende aún más. 
5. Cuando en una verificación subsiguiente (instante 4$T_p$), la tensión $v(t)$ asume signo negativo, se abre $I_+$ y se cierra $I_-$, y la rampa vuelve a aumentar. 
6. Sin embargo, en el instante $5T_p$, $v(t)$ ha vuelto a ser positiva; por lo tanto, se abre $I_-$ y se cierra $I_+$, y la rampa vuelve a descender. 
7. Este proceso continúa examinando periódicamente el signo de $v(t)$ y controlando en consecuencia los dos interruptores.


### Matematica

- Se nota que las sucesivas cargas y descargas del condensador $C$ permiten mantener la tensión $v(t)$ dentro de los límites impuestos; esta propiedad permitiría asumir valores mucho más altos si solo se aplicara la tensión $V_X$. Además, la carga agregada o quitada al condensador $C$ a través de la f.e.m. $V_R$ es conocida. Si $N+$ y $N-$ representan el número de intervalos de tiempo de duración $T_P$ durante los cuales han permanecido aplicadas las rampas $S_+$ y $S_-$, respectivamente, al final de la fase de run-up se puede escribir: $$(1)V_s(T_U)=-\frac{V_x}{R_x \cdot C}(N_+ + N_-)T_P - \frac{V_R}{R_RC}(N_--N_+)T_P$$
Entonces:$$V_x=-V_R \cdot \frac{(N_--N_+)R_x}{(N_-+N_+)R_R}-v_0(T_U)\frac{1}{N_-+N_+}\frac{R_xC}{T_P}$$

- *El unico valor que viene determinado durante la fase de Run-up es la diferencia $N_--N_+$.* Todos los otros parametros se conocen a priori; esto tmbien se aplica a *la suma $N_-+N_+$ ya que la duracion de la fase de runup esta fijada*. 
	- El segundo termino de la ecuacion es la unica incognita neta y su valor absoluto no puede exceder un valor maximo conocido de antemano, ya que durante la fase de Run-up, los diferentes interruptores se manejan de manera que mantienen $v(t)$ dentro de limites predefinidos
- Por lo tanto esta ecuacion permite determinar el orden de magnitud de la tension, es decir, las cifras mas significativas del valor convertido. *Las cifras restantes se determinan en la siguientes fases de rundown, donde se estima el valor $v_0(t)$.*
- *Este enfoque* no solo *amplía el rango de tensiones convertibles* sino que también *aumenta la resolución*. *Es posible amplificar la tensión aplicada* al instrumento de manera conocida y, con una gestión adecuada de la fase de runup multirampa, determinar las cifras más significativas de la tensión incógnita, mientras que las restantes se determinan en la fase de rundown.
- La subdivisión entre las cifras determinadas en la fase de runup y en la de rundown se establece durante el diseño del ADC. Dificultosamente, en esta última fase se pueden determinar más de 4 cifras decimales; las cifras restantes deben determinarse durante la fase de runup. Sin embargo, al aumentar el número de cifras, se experimenta un aumento sustancial en el tiempo de conversión.

### Sistema completo
![[Pasted image 20240209192047.png|400]]
- Dependiendo del valor de Vx, cambia la relación entre número de pulsos en la fase creciente vs la fase decreciente:
	- *Si Vx está cerca del fondo de escala*, la mayoría de pulsos cuentan en la fase decreciente (alta pendiente negativa). *Sólo 1 pulso cuenta en la fase creciente*.
	- *Si Vx es muy pequeña* (cerca de la resolución), *los pulsos se reparten aproximadamente igual entre fases* creciente y decreciente. Se obtiene una oscilación casi simétrica.
- *Lo importante es que el número total de pulsos (fases crecientes + decrecientes) se fija en el diseño. Esto define el tiempo de medición*.   
	- Dentro de ese tiempo, lo que varía con Vx es la relación entre número de pulsos en fases crecientes vs decrecientes.
	- Esta relación es la que luego influirá en el cálculo de Vx a partir de los pulsos contados.
- Por tanto, el truco está en alternar integración positiva y negativa para extender tiempo sin saturar, a la vez que se registran los pulsos en cada fase para poder estimar Vx.
- Tras los N pulsos totales de integración con el selector alternando en la rampa ascendente, se llega a un valor final de tensión $V0$.

Partiendo desde la ecuacion (1) obtenida anteriormente, pero cambiando la notacion a las usada en la materia: $$(1)V_0=-\frac{V_x}{R_x \cdot C}(N_+ + N_-)\tau - \frac{V_R}{R_RC}(N_--N_+)\tau$$
- Podemos calcular este valor $V_0$ con la fase Run-Down. 
	- Viendolo de otra manera: Cuando termina la fase run-up, tenemos un valor $V_o$ es cual tiene que ser igual a la integral:$\frac{1}{R_D \cdot C}\cdot\int{Vr}=V_R \cdot \frac{N_d \cdot \tau}{R_D \cdot C}=V_0$
![[Pasted image 20240209192101.png|400]]

- Por lo cual la ecuacion anterior nos queda como: $$V_R \cdot \frac{N_d \cdot \tau}{R_D \cdot C}=-\frac{V_x}{R_x \cdot C}(N_+ + N_-)\tau - \frac{V_R}{R_RC}(N_--N_+)\tau$$
	- En este caso no ponemos el $N_U$ de la fase Run-Down ya que no existiria
	- $N_D$ es el valor de cuentas obtenido en la fase Run-Down
- Simplificando los tiempos e igualando las resistencias usadas, nos queda el valor:$$V_X=V_R \frac{(N_D+N^--N^+)}{N^-+N^+}$$

- A mayor número de pulsos totales, mejor resolución. Pero también mayor tiempo de conversión.
	- Si por ejemplo se eligen 10 pulsos, es como añadir 1 cifra extra de resolución. 
	- Con 100 pulsos se añaden 2 cifras extras.
	- Con 1000 pulsos se añaden 3 cifras extras.
- Siempre N- > N+ porque en la fase creciente se integra la suma de dos tensiones, mientras que en la decreciente se integra la resta. Por eso dura más la fase decreciente.

#### Resolucion
$$\Delta V\approx V_R \cdot \frac{1}{N^-+N^+}$$
#### Tiempo de run-up
$$\tau_{run-up}=(N^-+N^+) \cdot \tau$$





# Italiano

## Concepti
La *risoluzione assoluta* di un convertitore ADC si riferisce alla *precisione con cui può convertire un segnale analogico in una rappresentazione digitale*. Questa risoluzione *è normalmente espressa in bit e si riferisce alla quantità di valori distinti che il convertitore può generare*. Ad esempio, un convertitore a 8 bit ha una risoluzione assoluta di 256 livelli.

La *risoluzione relativa* di un convertitore ADC si riferisce alla *precisione con cui può rilevare piccole variazioni in un segnale analogico*. Questa risoluzione *è normalmente espressa in bit e si riferisce alla capacità del convertitore di rilevare cambiamenti in un segnale dato*. Ad esempio, un convertitore con una risoluzione relativa di 8 bit può rilevare cambiamenti di 1 parte su 256 in un segnale dato. $$\frac{\Delta V}{V_{in}}$$
## ADC a rampa analogica
Ciò che caratterizza questo tipo di ADC è che la tensione di riferimento varia linearmente secondo una pendenza.
- Questo è possibile grazie alla presenza di un generatore di rampa analogica, che consiste in un generatore ideale di corrente collegato a un transistor e a un condensatore.
- Infatti, se il transistor è spento, tutta la corrente va alle piastre del condensatore, che si carica con una pendenza lineare crescente. Nel frattempo, quando il transistor è saturato, il condensatore si scarica, creando una vera e propria rampa.

Esistono due forme leggermente diverse di implementare il circuito, a seconda che la pendenza della rampa sia positiva o negativa.

### Pendenza Negativa
Il generatore di rampa è collegato all'ingresso di due comparatori. In particolare, è collegato all'ingresso invertente del comparatore $C_{o1}$ e all'ingresso non invertente del comparatore $C_{o2}$. $C_{o1}$ *confronta il valore istantaneo* della rampa di tensione VR in uscita dal generatore con la tensione analogica sconosciuta da convertire $V_X$, mentre $C_{o2}$ la confronta con Gnd (0 volt). *Il risultato del confronto di Co1 è un livello logico alto (H) se $V_X$ ≥ $V_R$ o basso (L) se $V_X < V_R$.*
![[Pasted image 20240125100805.png]]

Per quanto riguarda $C_{o2}$, produce un livello logico alto (H) se $V_R ≥ 0 V$, o basso (L) se $V_R < 0 V$.
Le uscite dei due comparatori convergono all'ingresso di un portello XNOR che aggiorna la sua uscita in base alla tabella di verità
![[Pasted image 20240125100757.png]]

Il valore logico ottenuto viene inserito in un blocco di circuito che controlla lo switch e è a sua volta collegato a un oscillatore locale. Specificamente, a seconda che il valore logico sia alto (H) o basso (L), lo switch si apre o si chiude, permettendo o impedendo il passaggio dell'onda sinusoidale generata dall'oscillatore locale.

In serie con esso è posto un contatore, inizialmente abilitato insieme al generatore di rampa tramite un segnale di reset inviato da un circuito di sincronizzazione. Il contatore conta i periodi di questo segnale fino alla nuova apertura dello switch.

Nella figura seguente è mostrata l'evoluzione temporale della tensione nel circuito.
![[Pasted image 20240125100907.png]]

Si può osservare che nello stato iniziale del circuito, l'uscita di $C_{o1}$ è bassa (L) perché la rampa parte da un valore di $V_R > V_X$. Tuttavia, l'uscita di $C_{o2}$ è alta perché $V_R > 0V$. Lo switch è aperto e il contatore viene resettato dal circuito di sincronizzazione.

Dal momento iniziale fino a tstart, lo switch rimane aperto e il circuito rimane "bloccato" nello stato iniziale. Successivamente, a tstart, viene soddisfatta la condizione: $V_X ≥ V_R$ e ciò

 fa cambiare l'uscita di $C_{o1}$ (da L a H). Lo switch consente quindi il passaggio del segnale generato dall'oscillatore al contatore, che inizia a contare i periodi. Questo persiste mentre $V_R$ rimane positivo, dopodiché l'uscita di $C_{o2}$ diventa bassa e inibisce, tramite l'XNOR, lo switch e, di conseguenza, il contatore.

Il risultato è un codice n0 (numero di impulsi di clock contati), proporzionale alla tensione presente in ingresso. Questo può essere dedotto facilmente mediante una proporzione basata sull'evoluzione temporale della tensione; infatti, si verifica che:
$\frac{V_X}{R}=\frac{\Delta T_x}{\Delta T}$ dove $R$ è il massimo valore assunto dalla rampa (corrispondente all'intervallo di ingresso dell'ADC), $\Delta T_x$ è l'intervallo di tempo in cui $0 < VR < VX$, e $T$ è l'intervallo di tempo totale di conversione. Da ciò si deduce che $V_X = \frac{R}{\Delta T}.\Delta T_x$, dove $\frac{R}{\Delta T}$ è la pendenza della rampa.

### Pendenza Positiva
![[Pasted image 20240125102045.png]]
Nel caso di una pendenza positiva, l'uscita del generatore di rampa è collegata a entrambi i terminali non invertenti dei comparatori, che la confrontano rispettivamente con la tensione di ingresso sconosciuta $v_x$ e con Gnd (0 V). *L'uscita del comparatore 1 è alta se la tensione di ingresso è inferiore alla tensione di riferimento, mentre è bassa nel caso complementare. L'uscita del comparatore 2 è alta se la tensione di riferimento è maggiore di zero, e bassa nel caso complementare*.

Il valore logico in uscita dal primo comparatore entra in un flip-flop, che memorizza il valore logico ricevuto e lo inserisce (negato) all'ingresso di un portello AND, le cui altre entrate sono rispettivamente un segnale di clock e l'uscita del secondo comparatore. Il portello AND moltiplica i tre segnali di ingresso, permettendo o meno il passaggio del segnale di clock a seconda del valore logico degli altri due ingressi. Se il valore logico è adeguato, il segnale di clock può pass


## ADC a Doppia Rampa
### Introduzione
![[Pasted image 20240125112646.png]]
Gli ADC a doppia rampa sono un'architettura che utilizza un metodo di conversione indiretto, noto come conversione tensione-tempo. Il cuore di questo dispositivo è l'integratore con il comparatore. Risolvono i problemi del convertitore a rampa singola e vengono utilizzati nei sistemi di acquisizione dati ad alta precisione. Nella figura è mostrato lo schema generale del dispositivo fisico.
Problemi risolti:
- Maggiore risoluzione e precisione: utilizzando una rampa di riferimento interna nota e stabile nella seconda fase, si elimina il limite di risoluzione imposto dalla rampa del convertitore a 1 rampa.
- Migliore soppressione del rumore e deriva: anche la rampa di riferimento interna rende il convertitore meno sensibile al rumore e alla deriva dell'oscillatore, migliorando la qualità della conversione.
- Gamma dinamica più ampia: nel convertitore a 1 rampa, la gamma dinamica è limitata dalla linearità della rampa. Nel caso a 2 rampe, può essere estesa utilizzando un riferimento stabile senza perdere linearità.
- Velocità di conversione: quello a 2 rampe è più lento, ma grazie alla sua maggiore risoluzione non ha bisogno di essere così veloce per la stessa precisione. Questo semplifica il design.

### Funzionamento Doppia rampa #tarjeta-anki 
Il ciclo di conversione consta di due intervalli di integrazione distinti: run-up e run-down.
- La tensione di riferimento $V_R$ deve avere una polarità opposta a quella di $V_X$
#### Fase Run-Up
1. All'istante $t_0$, la logica di controllo *reimposta il contatore* e contemporaneamente *cambia il selettore S nella posizione 1*, *collegando $V_X$ all'ingresso* di un integratore (RC). Anche *la logica di controllo ordina la chiusura dell'interruttore I*, in modo che la *sinusoide prodotta dall'oscillatore di riferimento passi attraverso l'interruttore e abiliti il conteggio del contatore*.
2. La tensione $V_X$ si integra per un intervallo di tempo finito, ottenendo così: $$Vo(t) = -\frac{V_x}{R_1C} \cdot (t - t_0)$$
	- Dove *$t_0$ è l'istante iniziale della conversione*.
	- *La tensione $V_o$ varia nel tempo con una tendenza lineare decrescente e proporzionale a $V_X$.*
		- $V_0$ è l'uscita dell'integratore.
3. Questo dispositivo *conta i periodi $T_O$ della sinusoide fino a un valore limite, fissato per progetto* o nella fase di configurazione, poi indica il riporto.
4. Questo viene rilevato dalla logica di controllo *che apre l'interruttore I*, bloccando il segnale sinusoidale e *cambia il selettore S nella posizione 2*.
5. Così termina la fase di run-up dopo un tempo $T_U = N_U \cdot T_O$, dove $N_U$ è il numero di periodi rilevati dal contatore. ($T_U$ ha un valore tipico di 100 a 200 ms)
#### Fase Run-Down
L'operazione di integrazione avviene alla tensione $-V_R$, costante e negativa ($V_R > 0 V$).
- Dato che $V_R$ è negativa, questo provoca una diminuzione della carica accumulata sul condensatore $C$, e di conseguenza la tensione $V_o$ assume una tendenza temporale costante e lineare crescente.
- Questo comportamento si manifesta a partire dal valore $V_{OM}$ precedentemente assunto dalla tensione Vo durante la fase di run-up.
1. Allo stesso istante di $V_{OM}$, la logica di controllo *riapre l'interruttore I*, *consentendo un nuovo conteggio $N_D$* dei periodi del segnale prodotto dall'oscillatore.
2. *Quando la tensione $V_0$ supera 0 V*, il comparatore di zero cambia stato. Questo è rilevato da *la logica di controllo che apre l'interruttore I*, inibendo il contatore e *trasferendo il risultato del secondo conteggio all'uscita*.
3. Anche la fase di run-down termina.
^1707560286625

![[Pasted image 20240125170203.png]]
- La rampa di discesa sarà sempre la stessa perché dipende dalla tensione di riferimento e dalla costante di integrazione, che sono fissate da noi, questo fa sì che prima o poi $V_0$ raggiunga 0.
- Per la seconda fase, la tensione di uscita dell'integratore è: $$Vo(t) = -\frac{V_X \cdot T_U}{R_1 \cdot C} + \frac{V_R \cdot (t - t_1)}{R_1 \cdot C}$$
	- Dove $t_1$ è l'istante di transizione tra le fasi di run-up e run-down.


### Sviluppo matematico Doppia rampa #tarjeta-anki 
- Denotando che durante la seconda fase di integrazione la tensione ritorna a zero, si può scrivere: $V_o(T_u+T_d)=0$
- Quindi:
$$-\frac{V_x}{R1 \cdot C} \cdot T_U=- \frac{V_R}{R_1 \cdot C} \cdot T_D$$
^1707560286631


- Quindi, otteniamo che: $$T_D = \frac{T_U}{V_R} \cdot V_x$$
	- Dove $T_D$ è l'intervallo di tempo della fase di run-down.
- *Si sottolinea la proporzionalità diretta tra $V_x$ e $T_D$.* Il circuito è quindi un convertitore di tensione in tempo, cioè *realizza una trasformazione lineare della tensione di ingresso in un intervallo di tempo*. Inoltre, poiché $T_U$ e $T_D$ sono conosciuti in base al numero di conteggi $N_U$ e $N_D$, il loro valore può essere sostituito nella formula e si ottiene: $$V_x=\frac{N_D
}{N_U} \cdot V_R = K \cdot N_D$$
	- Con $K = \frac{V_R}{N_U}$, pendenza della rampa nella fase di run-up. 
		- La nostra variabile indipendente è $N_D$ e la nostra variabile dipendente è $V_X$
		- **La pendenza è la risoluzione**
- Questa pendenza (pendenza della fase run-down) è nota e selezionata da noi.
- *Un altro modo di vedere questa analisi è con l'uguaglianza delle integrazioni*:
![[Pasted image 20240209113328.png]]
- Tau nei primi e secondi membri sono semplificati.
	- L'unica condizione di stabilità dell'orologio che abbiamo affinché questa relazione sia sempre vera è che sia stabile nel breve termine. Cioè, stabiliamo che Tau rimane stabile durante l'intervallo di misurazione; se c'è una piccola variazione tra una misurazione e l'altra, ciò non influisce sulla relazione, l'importante è che la stabilità sia tale che nel tempo di misurazione la variabilità della frequenza sia trascurabile
	- Se la frequenza cambia da un anno all'altro, troveremo sempre lo stesso valore, in ogni caso l'incertezza cambierà




### Parametri Doppia Rampa #tarjeta-anki 
#### Risoluzione assoluta
In questa architettura, la risoluzione $\Delta$ è definita come segue:
$$\Delta = \frac{R}{2^B} = \frac{V_R}{N_U}$$
^1707560286635


##### Aumento della risoluzione
Può essere migliorato:
- Riducendo la tensione di riferimento $V_R$,
	- Questo potrebbe generare problemi poiché il comparatore del nostro circuito ha isteresi, se riduciamo la tensione di riferimento la retta di discesa diventa più suscettibile a questa isteresi
- Aumentando il numero di periodi della fase di run-up.
	- Aumentando la durata dell'intervallo di tempo di run-up $T_U$
	- Aumentando la frequenza di oscillazione del segnale sinusoidale prodotto dall'oscillatore di riferimento.
	- Un altro problema con questa soluzione è che potremmo far saturare l'Op
		- Per risolvere questo problema dovremmo limitare il nostro valore di ingresso, il che non è l'ideale



> Questo può essere fatto entro certi limiti; infatti, aumentare troppo la frequenza di oscillazione rischia di cadere in una situazione di instabilità dell'oscillatore. È anche necessario un contatore adeguato, che possa seguire rapidamente i periodi del segnale e con un certo grado di precisione. Tuttavia, consente una risoluzione elevata, generalmente superiore a 18 bit.

#### Risoluzione relativa
- Il numero che varia al variare della tensione è ND
- Le misurazioni in un intervallo di tempo che si traducono in un treno di impulsi, la risoluzione sarà di un impulso
	- Dove viene contato il numero di impulsi nel nostro circuito? In ND
$$\frac{\Delta V}{V_X}=1/N_D$$


#### Tempo, velocità e immunità al rumore Doppia Rampa #tarjeta-anki 
Il tempo e la velocità di conversione dipendono dall'intervallo di tempo di run-up e run-down, dal tempo di attesa tra le due fasi e dal tempo necessario per ripristinare il circuito una volta concluso un ciclo.
- *Quindi, è un dispositivo lento ma molto preciso*. Infatti, non dipende dai parametri del circuito, ma solo da $V_R$ e dai conteggi del contatore.
- Inoltre, a causa della presenza dell'integratore, *il circuito ha una notevole capacità di soppressione del rumore generato dalla tensione di alimentazione*.
Infine, l'assenza del DAC conferisce al circuito una relativa semplicità circuital.
^1707560286639




### ADC a Doppia Rampa con Fase di Run-up di Durata Ridotta #tarjeta-anki 
*Per ridurre il tempo di conversione* di un ADC a doppia rampa senza degradare la sua risoluzione, si adottano *soluzioni circuitali con resistenze $R_U$ e $R_D$,* che rappresentano le *resistenze di carico e scarica del condensatore*. Seguendo la procedura precedente, è facile dimostrare che *si verifica la relazione*:$$V_X=-V_R \cdot \frac{R_U}{R_D} \cdot \frac{N_D}{N_U}$$
![[Pasted image 20240125174416.png]]
- Scegliendo $R_U$ minore di $R_D$, si ottiene una riduzione del tempo di run-up. Tuttavia, *il risultato della conversione dipende anche dalla relazione tra le due resistenze $R_U$ e $R_D$: per non ridurre la precisione dell'ADC, è necessario garantire la precisione di questa relazione*. Comunque, al giorno d'oggi esistono tecnologie capaci di permettere la realizzazione integrata di resistenze che presentano caratteristiche adeguate.
- La risoluzione $\Delta_V$ e il tempo di conversione $T_{ADC}$ ottenuti sono:$$\Delta_V=\frac{|V_R|R_V}{N_UR_D}$$
- Ricordando la proporzionalità tra tensioni e durata, si può scrivere anche:$$\Delta_V=\frac{|V_R|R_U}{N_UR_D}=\frac{|V_R|}{N_D}$$
- In questo caso, come nel precedente, la risoluzione dell'ADC dipende solo da $T_S$ e $N$
	- *La riduzione della durata della fase di run-up non ha influenza su di essa*. La risoluzione aumenta aumentando il numero massimo di conteggi previsti nella fase di run-down e, quindi, fissando il periodo di clock $T$, aumentando anche la durata della fase di run-down stessa.
- La durata della conversione è data dalla relazione:$$T_{ADC}=\frac{\Delta_V \cdot R_D}{|V_R| \cdot R_U}$$
- Il che conferma che, mantenendo costanti gli altri parametri, il tempo di conversione può essere ridotto scegliendo $R_U/R_D < 1$.
^1707560286642




## ADC multirampa
### Motivazione #tarjeta-anki 
- Per massimizzare la risoluzione:
	- Non è possibile aumentare molto Nu perché aumenta il tempo di conversione
	- Nemmeno ridurre molto VR perché si riduce il range dinamico
- Quindi, la chiave è nel variare la relazione Ru/RD. Cioè, scegliere RD il più grande possibile, sempre senza che la pendenza risultante attivi l'isteresi del comparatore.
- In questo modo, mantenendo fissi gli altri parametri, variare Ru/RD consente di regolare la risoluzione al valore massimo possibile per un dato Vx. 
	- Ciò darà il maggior numero di conteggi ND nella rampa discendente e quindi la migliore incertezza relativa (sempre 1/ND).
^1707560286647




### Introduzione
Oltre agli ADC a doppia rampa, esistono anche gli ADC multirampa (multislope).
- A valle viene sempre utilizzato lo stesso circuito già visto nel doppio rampa
![[Pasted image 20240125170307.png]]
Lo stadio di ingresso si presenta come un insieme di rami circuitali in parallelo, alcuni dei quali sono collegati al potenziale di riferimento $V_R > 0 V$, altri al potenziale $-V_R$. Un ramo aggiuntivo consente il collegamento dello strumento alla tensione di ingresso sconosciuta $V_x$.
Si prepara l'integratore per generare 4 rampe di pendenza 4 rampe con pendenze di 1, 10, 100 e 1000, sia positive che negative. Queste rampe sono indicate rispettivamente come $\pm S_1, \pm S_{10}, \pm S_{100}$ e $\pm S_{1000}$, dove il segno coincide con quello della tensione di riferimento 1000 utilizzata.
In ogni ramo c'è un interruttore e una resistenza: l'interruttore ha la funzione di collegare il ramo all'ingresso dell'integratore, mentre *la resistenza serve a modulare l'intensità della corrente inviata all'integratore*, secondo la rampa di tensione desiderata. Come nei ADC a doppia rampa, la conversione è divisa in fase run up e run down. In questo caso ci sono due fasi di run-up e due run-down.
Rispetto agli ADC a doppia rampa, l'approssimazione a zero non avviene in una sola fase con una sola rampa, ma in M fasi attraverso M rampe, una per ogni cifra di risoluzione desiderata.



### Funzionamento #tarjeta-anki 
#### Libro
![[Pasted image 20240125193320.png]]
Supponiamo, ad esempio, che il valore della tensione $V_X$ sia tale che, applicando una rampa di pendenza unitaria nella fase di run-down, si ottiene un conteggio pari a $N_D= 6437$.
1. Si *chiude solo l'interruttore $I_V$* e, supponendo che $V_X$ sia negativo, la tensione di uscita dell'integratore assume valori positivi, come indicato nel diagramma temporale della figura. Si è supposto che il tempo necessario per aprire e chiudere gli interruttori sia trascurabile.
 2. *All'istante $t_V$, si apre l'interruttore $I_V$ e si chiude l'interruttore $I'_D$,* dando inizio alla fase di run-down; poiché $v_0(t_u) > 0$, la tensione utilizzata durante questa fase sarà positiva *(rampa $+S_{1000}$).* 
	 - Dato che la *velocità di scarica di $v(t)$ è 1000 volte quella di riferimento, ogni evento di conteggio dell'orologio corrisponde a 1000 eventi di clock relativi a una rampa di pendenza unitaria*. 
3. *Il conteggio si interrompe quando avviene l'attraversamento dello zero della tensione $v_s(t)$,* mentre *lo scarico continua con questa pendenza fino al prossimo evento dell'orologio* (istante $t_D$'').
4. All'istante $t'_D$, in cui si interrompe lo scarico, *il conteggio assume un valore di 6*, *mentre la tensione della rampa acquisisce un valore negativo corrispondente a $7000 - 6437=563$* conteggi unitari. 
	- La cifra più significativa della tensione sconosciuta coincide così con il valore del conteggio corrispondente a questa prima fase dello scarico.
5. All'istante $t'_D$, oltre ad aprire l'interruttore $I'_{D}$, si chiude anche l'interruttore $I''_D$, attivando così la rampa $-S_{100}$. La tensione $v_s(t)$ inizia ad aumentare con una velocità pari a $1/100$ della velocità relativa al caso precedente. 
6. In questa seconda fase, *il conteggio si interrompe quando avviene l'attraversamento dello zero della tensione $v_s(t)$,* *mentre lo scarico si interrompe al prossimo evento dell'orologio* (istante $t''_D$).
	- *Il conteggio raggiunto durante questa seconda fase è pari a 4,* mentre *la tensione della rampa è pari a $700 - 600 = 100$.* *La seconda cifra significativa di $V_X$ coincide così con il valore del conteggio in questa seconda fase di scarico*.
7. Dopo lo scarico della rampa $-S_{100}$, si apre l'interruttore $I''_{D}$ e si chiude l'interruttore $I'''_{D}$, attivando la rampa $+S_{10}$.
8. Si ripetono le operazioni di conteggio e scarico; *nel frattempo, si ottengono i valori dei conteggi e delle tensioni corrispondenti a tutte le cifre significative di $V_X$, terminando con la fase di scarico della rampa $-S_{10}$,* che determina le ultime cifre di $V_X$. 
^1707560286650




#### Cifre di risoluzione 
Si definiscono $\Delta_1,\Delta_2$ le risoluzioni delle prime due cifre, la massima pendenza $S_M$ e la risoluzione della parte meno significativa $\Delta_M$ della tensione $V_X$. 
- Si ottengono le cifre significative e, quindi, la tensione $V_X$ utilizzando le relazioni:
$$\Delta_1=|V_R| \cdot \frac{R_V}{N_U R_D}$$
$$\Delta_2=\Delta_1 \cdot \frac{1}{10}$$
$$S_M=1000 \cdot S_{10}$$
$$\Delta_M=\Delta_1 \cdot \frac{1}{1000}$$
### Parametri
Il numero di cifre di risoluzione e la durata delle fasi di run-up e run-down dipendono dalle caratteristiche del contatore utilizzato. 
- È chiaro che, *mantenendo costanti gli altri parametri,* aumentare il numero di cifre di risoluzione comporta un aumento del tempo necessario per effettuare la conversione. 
- Anche in questo caso, quindi, è necessario un compromesso tra la precisione desiderata e il tempo massimo di conversione ammissibile. 
- Per avere una maggiore flessibilità nella scelta del numero di cifre di risoluzione, *gli ADC multislope sono spesso realizzati in modo che il numero di cifre possa essere selezionato in base alla misura da effettuare.*

### Confronto tra ADC a Doppia Rampa e Multirampa
- Gli ADC a doppia rampa, rispetto agli ADC a multirampa, *hanno una maggiore semplicità circuitali e minore complessità implementativa*.
- Gli ADC a doppia rampa sono in grado di *ridurre il tempo di conversione attraverso la riduzione della durata della fase di run-up*, mentre *l'aumento della risoluzione è ottenuto solo aumentando il tempo di integrazione nella fase di run-down*.
- Gli ADC a multirampa, d'altra parte, *permettono di variare il numero di cifre di risoluzione in modo indipendente dal tempo di conversione*. Tuttavia, la loro implementazione è più complessa, in quanto richiede una maggiore complessità circuitali e software.








## ADC con fase di Run-up Multirampa

### Motivazioni
- L'obiettivo è migliorare la risoluzione (numero di cifre) di un convertitore ADC multirampa, oltre le 4 cifre decimali ottenute in precedenza.
- Un approccio sarebbe aumentare il tempo di integrazione t1 nella rampa ascendente, poiché ciò migliorerebbe la risoluzione.
- Tuttavia, c'è un problema: nella rampa ascendente viene integrata la tensione di ingresso Vx. Se aumentiamo troppo t1, la tensione di uscita V_0 dell'integratore potrebbe superare i limiti di tensione supportati dal convertitore.
- Quindi, verrà spiegata una tecnica alternativa per integrare Vx in modo diverso nella rampa ascendente, in modo che:
	1. Si possa aumentare t1 per migliorare la risoluzione
	2. Ma mantenendo V_0 sempre al di sotto di un valore massimo prefissato, indipendentemente dal valore di Vx.
- La chiave è modificare il modo in cui avviene l'integrazione nella rampa ascendente.
- Alla fine, ciò consente di superare le limitazioni precedenti e ottenere una risoluzione molto elevata (8+ cifre) senza esporre il convertitore a tensioni eccessive.

### Introduzione
- L'uso di rampe con pendenze diverse anche nella fase di run-up consente di ampliare sia il range di tensioni convertibili che la risoluzione. Tuttavia, ciò avviene a spese di un aumento, a volte considerevole, del tempo di conversione.
- Per ottenere una maggiore risoluzione anche nella fase di run-up e mantenere così la tensione di uscita entro limiti consentiti, il condensatore dell'integratore viene sottoposto, oltre alla tensione sconosciuta $V_X$, anche a una tensione conosciuta $V_R$, aggiungendo o rimuovendo così una quantità nota di carica.
- Lo schema di principio di questa struttura e il comportamento temporale teorico della tensione $v(t)$ sono mostrati nella fig.13.


### Funzionamento Multirampa run-up #tarjeta-anki 
1. La tensione sconosciuta $V_X$ è negativa; rimane applicata all'ADC per tutta la durata della fase di run-up, cioè durante questa fase, l'interruttore $I_X$ della fig. rimane sempre chiuso.
2. Si osserva che se all'istante $t=0$ si chiudesse solo l'interruttore $I_X$, la tensione $v(t)$ aumenterebbe come la rampa tratteggiata della fig.13; in realtà, anche l'interruttore $I_-$ viene chiuso e, quindi, la rampa aumenta con una pendenza $S_-$ maggiore.
3. All'istante $T_p$, viene rilevato il segno della tensione $v(t)$; poiché questo risulta essere positivo, si apre l'interruttore $I_-$ e si chiude l'interruttore $I_+$. Dato che $V_R$ è stata scelta con un valore assoluto maggiore di $V_X$, quando $I_+$ è chiuso, la tensione $v(t)$ inizia a diminuire con la pendenza $S_+$.
4. All'istante $2T_P$, il segno di $v(t)$ viene nuovamente verificato: essendo ancora positivo, lo stato degli interruttori non viene alterato, quindi questa tensione diminuisce ulteriormente.
5. Quando in un controllo successivo (istante $4T_p$), la tensione $v(t)$ assume segno negativo, si apre $I_+$ e si chiude $I_-$, e la rampa aumenta nuovamente.
6. Tuttavia, all'istante $5T_p$, $v(t)$ è di nuovo diventata positiva; quindi, si apre $I_-$ e si chiude $I_+$, e la rampa diminuisce nuovamente.
7. Questo processo continua esaminando periodicamente il segno di $v(t)$ e controllando di conseguenza i due interruttori.
### Matematica
- Si nota che le successive cariche e scariche del condensatore $C$ consentono di mantenere la tensione $v(t)$ entro i limiti imposti; questa proprietà consentirebbe di assumere valori molto più alti se fosse applicata solo la tensione $V_X$. Inoltre, la carica aggiunta o rimossa al condensatore $C$ attraverso la f.e.m. $V_R$ è nota. Se $N^+$ e $N^-$ rappresentano il numero di intervalli di tempo della durata $T_P$ durante i quali sono state applicate le rampe $S_+$ e $S_-$, rispettivamente, alla fine della fase di run-up si può scrivere:
$$(1)V_s(T_U)=-\frac{V_x}{R_x \cdot C}(N_+ + N_-)T_P - \frac{V_R}{R_RC}(N_--N_+)T_P$$
Quindi:$$V_x=-V_R \cdot \frac{(N_--N_+)R_x}{(N_-+N_+)R_R}-v_0(T_U)\frac{1}{N_-+N_+}\frac{R_xC}{T_P}$$
^1707560286654

- L'unico valore che viene determinato durante la fase di Run-up è la differenza $N_--N_+$. Tutti gli altri parametri sono noti a priori; questo si applica anche alla somma $N_-+N_+$ poiché la durata della fase di run-up è fissata.
	- Il secondo termine dell'equazione è l'unica incognita netta e il suo valore assoluto non può superare un valore massimo noto in anticipo, poiché durante la fase di Run-up, gli interruttori diversi sono gestiti in modo da mantenere $v(t)$ entro limiti predefiniti.
- Pertanto, questa equazione consente di determinare l'ordine di grandezza della tensione, cioè le cifre più significative del valore convertito. Le cifre rimanenti sono determinate nelle fasi successive di rundown, dove viene stimato il valore $v_0(t)$.
- Questo approccio non solo amplia il range di tensioni convertibili ma aumenta anche la risoluzione. È possibile amplificare la tensione applicata allo strumento in modo noto e, con una gestione adeguata della fase di run-up multirampa, determinare le cifre più significative della tensione incognita, mentre le rimanenti vengono determinate nella fase di rundown.
- La suddivisione tra le cifre determinate nella fase di run-up e in quella di rundown viene stabilita durante la progettazione dell'ADC. Difficilmente, in quest'ultima fase possono essere determinate più di 4 cifre decimali; le cifre restanti devono essere determinate durante la fase di run-up. Tuttavia, aumentando il numero di cifre, si sperimenta un aumento sostanziale del tempo di conversione.




#### Risoluzione
$$\Delta V\approx V_R \cdot \frac{1}{N^-+N^+}$$
#### Tempo di run-up
$$\tau_{run-up}=(N^-+N^+) \cdot \tau$$



### Sistema completo #tarjeta-anki 
- A seconda del valore di Vx, cambia la relazione tra il numero di impulsi nella fase crescente rispetto a quella decrescente:
	- Se Vx è vicino al fondo scala, la maggior parte degli impulsi conta nella fase decrescente (alta pendenza negativa). Solo 1 impulso conta nella fase crescente.
	- Se Vx è molto piccola (vicina alla risoluzione), gli impulsi sono distribuiti approssimativamente ugualmente tra le fasi crescente e decrescente. Si ottiene un'oscillazione quasi simmetrica.
- L'importante è che il numero totale di impulsi (fasi crescenti + decrescenti) sia fisso nel design. Questo definisce il tempo di misurazione.
	- All'interno di quel tempo, ciò che varia con Vx è la relazione tra il numero di impulsi nelle fasi crescenti rispetto a quelle decrescenti.
	- Questa relazione influenzerà poi il calcolo di Vx a partire dagli impulsi contati.
- Quindi, il trucco sta nell'alternare l'integrazione positiva e negativa per estendere il tempo senza saturare, contemporaneamente registrando gli impulsi in ciascuna fase per poter stimare Vx.
- Dopo N impulsi totali di integrazione con il selettore che alterna nella rampa ascendente, si arriva a un valore finale di tensione V0.
Partendo dall'equazione (1) ottenuta in precedenza, ma cambiando la notazione a quella usata nella materia:
$$(1)V_0=-\frac{V_x}{R_x \cdot C}(N_+ + N_-)\tau - \frac{V_R}{R_RC}(N_--N_+)\tau$$
- Possiamo calcolare questo valore V0 con la fase di Run-Down.
	- Guardandolo in un altro modo: quando termina la fase di run-up, abbiamo un valore V_o che deve essere uguale all'integrale: $\frac{1}{R_D \cdot C}\cdot\int{Vr}=V_R \cdot \frac{N_d \cdot \tau}{R_D \cdot C}=V_0$
- Quindi l'equazione precedente diventa: $$V_R \cdot \frac{N_d \cdot \tau}{R_D \cdot C}=-\frac{V_x}{R_x \cdot C}(N_+ + N_-)\tau - \frac{V_R}{R_RC}(N_--N_+)\tau$$
	- In questo caso non includiamo il $N_U$ della fase di Run-Down poiché non esisterebbe
	- $N_D$ è il valore dei conteggi ottenuto nella fase di Run-Down
- Semplificando i tempi e uguagliando le resistenze usate, otteniamo il valore: $$V_X=V_R \frac{(N_D+N^--N^+)}{N^-+N^+}$$
^1707560286657

- Maggiore è il numero totale di impulsi, migliore è la risoluzione. Ma anche maggiore è il tempo di conversione.
	- Se ad esempio si scelgono 10 impulsi, è come aggiungere 1 cifra extra di risoluzione.
	- Con 100 impulsi si aggiungono 2 cifre extra.
	- Con 1000 impulsi si aggiungono 3 cifre extra.
- Sempre N- > N+ perché nella fase crescente si integra la somma di due tensioni, mentre nella fase decrescente si integra la differenza. Per questo motivo la fase decrescente dura più a lungo.

