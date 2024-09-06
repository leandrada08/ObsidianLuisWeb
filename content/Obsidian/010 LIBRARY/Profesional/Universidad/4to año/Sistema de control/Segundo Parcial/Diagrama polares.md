# Diagramas polares

El diagrama polar es el lugar geometrico de los vectores $|G(jw)|<G(jw)$ cuando w varia de cero a infinito, tambien se lo suele denominar diagrama de Nyquist. La ventaja de usar este diagrama es que podemos ver las caracteristicas de la respuesta en frecuencia de un sistema en el rango de frecuencia completo, la desventaja es que no indica de manera clara como afecta cada factor a este grafico

## Graficos comunes
#### Integral y derivativo
**Derivativo(jw)^{-1}:** Es el eje imaginario negativo $G(jw)=\frac{1}{w}<-90$
**Integral(jw):** Eje imaginario positivo
#### Factores de primero orden(1+jwT)^{-+1}:
Ambos factores en conjunto generan un circulo con centro 0,5 y de radio 0,5, si hablamos del factor negativo seria la parte inferior y el factor positivo la parte superior
![[Pasted image 20221126211035.png]]
#### Factores cuadrativos
**1er caso:** $\frac{1}{1+2\delta.(\frac{j.w}{wn})+(\frac{j.w}{wn})^2}$ 
Empieza 1<0 y termina de 0<180, la forma exacta varia con el factor de amortiguamiento pero en general la forma es parecida a la de la figura, el cruce con el eje imaginario nos da la frecuencia natural no amortiguada y el lugar mas alejado nos da la frecuencia de resonancia
![[Pasted image 20221126211456.png]]
**2do caso:** $1+2\delta.(\frac{j.w}{wn})+(\frac{j.w}{wn})^2$
![[Pasted image 20221126211556.png]]
#### Formas generales
**Sistema tipo 0:** El punto inicial del diagrama polar es finito y esta sobre el eje real positivo. La tangente en el diagrama polar en w=0 es perpendicular al eje real. En w infinito esta en el origen y la curva es tangente a uno de los ejes
**Sistema tipo 1:** En bajas frecuencias es asintotico a una linea paralela al eje imaginario negativo. En altas frecuencias la magnitud se vuelve cero, la curva converge hacia el origen y es tangente a uno de los ejes.
**Sistema tipo 2:** En bajas frecuencia es asintotico a una linea paralela al eje real negativo, en altas frecuencia se vuelve cero y la curva es tangente a uno de los ejes
![[Pasted image 20221126212107.png]]
![[Pasted image 20221126212117.png]]
