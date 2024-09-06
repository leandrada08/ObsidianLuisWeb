## Introduccion
La conversion de señales analogicas en su correspondiante digital, efectura las siguientes acciones:
1. Muestreo
2. Mantener
3. Cuantizacion
4. Codificacion

![[Pasted image 20240124172556.png]]
El primero de estos circuitos es el de muestreo, toma de la señal de entrada un secuancia de muestras distantes en el tiempo de un valor Ts(periodo). El segundo es el circuito de retención, o hold circuit, cuya función es almacenar temporalmente el nivel de las muestras que salen del muestreador. El tercero es el circuito cuantizador, que realiza la discretización en amplitud de los niveles de voltaje de las muestras de entrada. Por lo general, no hay un circuito real de codificación. La codificación se confía al circuito cuantizador, que asigna a cada muestra discretizada un código de salida apropiado, compuesto por números binarios.

### Muestreo
![[Pasted image 20240124173440.png]]
El muestreo es la operación que consiste en adquirir de la señal de entrada una secuencia de muestras. La señal muestreada es una secuencia de impulsos de voltaje espaciados en el tiempo por un intervalo constante Ts, conocido como período de muestreo. La amplitud de las muestras depende de la señal de entrada v(t) según la relación: $v_s(tk) = v(tk)$, donde tk es el instante genérico de muestreo. El ritmo con el que las muestras se presentan en la salida se llama velocidad de muestreo o frecuencia de muestreo, Rs. La velocidad de muestreo está relacionada con el tiempo de muestreo por la relación: Rs=1/Ts. Por lo tanto, se mide en Sample/s o en Hertz.
El circuito de muestreo se puede pensar como un interruptor electrónico S en serie con la línea de entrada, controlado por un circuito oscilador de cuarzo. El cierre de S ocurre en correspondencia con el flanco de subida de la señal de reloj. De la señal de entrada v(t), solo la porción correspondiente a los instantes de muestreo pasa por S y continúa a lo largo de la cadena de adquisición. Todo lo demás es bloqueado por el mismo interruptor. El parámetro más importante en un proceso de conversión A-D es la frecuencia de muestreo. De hecho, de ella depende la posibilidad de reconstruir la señal original v(t) a partir de sus muestras vs(t). En particular, esto depende de la relación entre Rs y la frecuencia máxima de la señal de entrada v(t) según el Teorema de Shannon(criterio de nyquiz)

#### Teorema de Shannon:
La reconstrucción sin ambigüedades de la señal original v(t) a partir de su versión muestreada vs(t) es posible si: Rs > 2 * fmax, donde fmax representa la frecuencia más alta de la señal de interés.
En el caso de un muestreo que viole la condición establecida por el Teorema de Shannon (Rs < 2.fmax), se observa que las repeticiones periódicas de V(f), la transformada de Fourier de la señal de interés, se superponen unas a otras y el espectro final Vs(f) aparece de manera confusa, siendo imposible recuperar V(f) mediante filtrado. En este caso, se habla de Aliasing.


### RETENCIÓN
![[Pasted image 20240124174153.png]]
La retención es la operación que consiste en mantener los niveles de voltaje vs(t) de las muestras adquiridas durante el período de muestreo Ts, es decir, hasta la llegada de la siguiente muestra.
Desde el bloque de retención, sale una señal constante a tramos v_H(t).
El circuito de retención está compuesto por una resistencia Rh en serie con la línea de entrada, colocada aguas arriba del interruptor S, que suele estar formado por un MOSFET, que tiene una pequeña resistencia de entrada intrínseca R.
Gobierna la conexión del condensador a la entrada analógica.
En el source y el drain del transistor están conectados dos buffers (operacionales en configuración de seguidores de voltaje), que tienen una impedancia de entrada alta, baja impedancia de salida y voltaje de salida igual al voltaje de entrada.
Esto sirve para mantener la impedancia de entrada total alta y asegurar que casi toda la corriente en la salida del selector S sea absorbida por el condensador Ch.
Este circuito se llama *Track and Hold* (o Sample and Hold) y permite las funciones de muestreo y retención.
El funcionamiento del circuito se lleva a cabo en dos fases:
1. Fase de carga;
2. Fase de retención.

#### FASE DE CARGA
![[Pasted image 20240124174431.png]]
La fase de carga comienza con el cierre del interruptor S en un instante de muestreo genérico $tk$. En este momento, el circuito tiene el voltaje de entrada $v(tk)$ diferente al de salida $v_H(tk)$. El circuito permanece en este estado hasta que S se abre, en el instante $t'_k$, después de un intervalo de tiempo $ΔTc$. En este intervalo de tiempo, se manifiesta un transitorio de carga exponencial del condensador $C_H$ hasta $t'_k$.
La evolución del voltaje $v_H(t)$ durante $ΔTc$ se puede aproximar así:
$$v_H(t) = v_H(t_k) + [v(t'_k) – v_H(t_k)] * (1 – e^{-ΔTc/τc})$$
donde $τc = R_H * C_H$ es la constante de tiempo del circuito.
La duración de $ΔTc$ es un parámetro importante para los ADC. A medida que $ΔTc$ aumenta, la discrepancia entre el nivel $v_H(t'_k)$ alcanzado por $v_H(t)$ y el nivel de la señal de entrada v(t) en el instante de apertura $t'_k$ disminuye. Mejora así la estimación de la muestra de la señal de entrada v(t) en $t'_k$, a expensas del tiempo de conversión de cada muestra, es decir, Ts.
También se observa que la elección de un valor de ΔTc que no sea lo suficientemente grande como para permitir que $v_H(t)$ alcance $v(t'_k)$ resulta en un error de amplitud $e = v(t'_k) – vH(t'_k)$ que depende de ΔTc según la relación: $ΔTc = -τc * ln(er)$ con $er = e/ ΔV$.

#### FASE DE RETENCIÓN
![[Pasted image 20240124174449.png]]
La fase de retención comienza con la apertura de S en el instante $t'_k$ y dura un intervalo $ΔT_H$ hasta el cierre de S.
Cuando S está abierto, el condensador retiene la carga eléctrica acumulada durante la fase de carga y mantiene constante el voltaje en sus extremos $v_H(t'_k)$. En este intervalo de tiempo, tiene lugar la conversión del nivel de la señal en un valor numérico por medio del siguiente bloque de conversión. Esto ocurre en un tiempo $Tad < ΔT_H$, es decir, antes de que S se cierre nuevamente para adquirir la siguiente muestra.
Debido a la resistencia no infinita del interruptor, se genera una corriente de descarga $i_H$ que provoca la descarga del condensador $C_H$ a través de la resistencia. Así, el voltaje en los extremos de CH disminuye con el tiempo según un perfil exponencial decreciente.
Se puede obtener de la gráfica temporal que:
$$ΔV = v_H(t'_k) * (1 - e^{-ΔT_H/τ_H})$$, con $τ_H = R_H * C_H$, la constante de tiempo del circuito.
La disminución de v_H(t) provoca un error en la adquisición de los niveles de las muestras, cuyo valor máximo posible es: emax = ΔV. Este depende de τH y de ΔTH según la relación: ΔTH = - τH * ln(1 – er), con $er = emax/vH(t'_k)$.
El circuito de retención afecta el ancho de banda del ADC, ya que, durante la toma de muestras, actúa como un filtro pasa bajo en serie con la cadena de medición. Su función de transferencia, por lo tanto, afecta la del ADC.
En la elección de CH y Rh, es importante tener en cuenta las especificaciones del ADC en términos de ancho de banda. En particular, al elegir CH, se realiza un compromiso: un valor grande de CH limitaría la excursión ΔV en la fase de retención, mientras que un valor pequeño aceleraría la carga del condensador y aumentaría el ancho de banda del ADC.
### CUANTIZACIÓN
![[Pasted image 20240124175302.png]]
La cuantización en el dominio de las amplitudes es la operación mediante la cual la señal muestreada v_H(t) presente en la salida del circuito track and hold se transforma en una secuencia de niveles de voltaje vO(t), uno por cada muestra.
En cada intervalo de duración Ts, el dispositivo aproxima el nivel de voltaje asumido por v_H(t) al nivel de salida vO más cercano, obtenido dividiendo el rango R de valores de entrada del dispositivo en N intervalos de amplitud: Q = R/N = R/2^B, donde Q es el paso de cuantización y B es el número de bits del dispositivo.
10
La característica más importante de un circuito de cuantización es su transcaracterística, que determina su rendimiento y posibles ineficiencias. Se define como la función que asocia a cada nivel de voltaje asumido por el voltaje analógico en la entrada del ADC en un cierto intervalo de retención ΔTh, un voltaje vo adecuado perten




## ADC: CONVERTIDOR ANALÓGICO A DIGITAL
En los sistemas electrónicos modernos, las actividades de medición, cálculo y control ocurren en el dominio digital, a partir de señales analógicas convertidas a digital mediante uno o más ADC.
En la mayoría de los casos, el rendimiento del sistema de adquisición depende del ADC utilizado, especialmente de sus parámetros, como la velocidad de muestreo, la resolución y la precisión de la medición.
Idealmente, se desearía tener ADC con velocidad de muestreo, resolución y precisión infinitas. En la realidad, sin embargo, el rendimiento de los ADC es alto para ciertos parámetros y modesto para otros. Esto también se debe a la presencia de errores y otras no idealidades que hacen que el funcionamiento sea diferente al deseado.

### NO IDEALIDADES DE UN ADC
Las no idealidades de un ADC son defectos del dispositivo que hacen que su funcionamiento sea diferente al ideal esperado. En particular, pueden generar errores en la determinación del nivel de voltaje de salida del mismo ADC.
Para detectar y corregir estos errores, es útil considerar la caracterización de un ADC. Esta consiste en la determinación y descripción de su comportamiento estático y dinámico.
El comportamiento estático es la forma en que el dispositivo se comporta en relación con señales de entrada constantes o variables lentamente en el tiempo.
La principal información que se desea determinar a nivel estático es la transcaracterística del ADC. Esto se logra mediante el conocimiento de los niveles de transición.
15
Idealmente, se definen como aquellos niveles de voltaje de entrada en los cuales el voltaje de salida del ADC cambia de un código a otro. Sin embargo, en los ADC reales, debido al ruido generado internamente, no hay una transición de nivel nítida, sino una conmutación aleatoria de un código a otro. Por lo tanto, habrá errores en la asociación de un código de salida a un voltaje analógico de entrada específico.
Los errores se pueden dividir en dos tipos: errores estáticos y errores dinámicos.
Los errores estáticos se manifiestan en señales constantes o lentamente variables y son los errores más evidentes y compensables mediante bloques circuitales adecuados. Los errores dinámicos, por otro lado, se manifiestan en relación con señales de entrada variables en el tiempo y están principalmente relacionados con la no idealidad de la función de transferencia del dispositivo.
#### ERRORES ESTÁTICOS
Los errores estáticos se pueden dividir en:
1) error de cuantización;
2) error de offset;
3) error de ganancia;
4) error de no linealidad;