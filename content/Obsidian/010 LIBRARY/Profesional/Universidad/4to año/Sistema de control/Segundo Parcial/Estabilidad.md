# Estabilidad


## Metodos apra analizar la estabilidad
- Lugar geometrico de las raices(LGR)
- Routh-Hurwitz
- Respuesta en frecuencia
	- Bode
		- Barckhouse(estabilidad relativa)
		- Margen de ganancia y de fase
	- Nyquist


## Definiciones basicas
### Estabilidad Absoluta
Un sistema es:
- Estable: Si la salida termina por regresr a su estado de equilibrio cuando el sistema esta sujeto a una condicion inial
- Criticamente estable: Si las oscilaciones de la salida continuan de forma indefinida
- Inestible: Si es sistema es caotico
### Estalibilidad relativa
Esta estabilidad hace referencia al analisis transitorio con referencia a otro valor, se analiza que tanto se extingue el transitorio con referencia a la otra senial
### Error de estado estacionar
Es la diferencia entre la salida del sistema y la entrada cuando t tiende a infinito


## Estabilidad absoluta
### Inestabilidad absoluta
Polo/s en el semi plano derecho serian los dominante y estos harian que la respuesta transitoria aumentara de forma monotoma. Por lo tanto la estabilidad de un sistema se determinara a partir de la ubicion de los polos en lazo cerrado en el plano s, estos deben estar todos en el semiplano izquierdo. Para determinar si los polos se encuentran en el semiplano izquierod sin buscar los polos del polinomio se usa el **Criterio de Routh**


