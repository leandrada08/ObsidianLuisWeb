Los filtros ideales, son no causales por lo tanto no se pueden aplicar en la realidad, por lo que realizamos aproximaciones, las aproximaciones se restriguen a funciones racionales, se aproxima con la siguente funcion
$$M(w)=\frac{k0}{\sqrt{1+f(w^2)}}$$

## Filtro Butterworth
Butterworth propone que la funcion f(w^2) sea: $f(w^2)=(w/wc)^{2n}$
Por lo que la respuesta en frecuencia tiene la forma $|H(w)|=\frac{K0}{\sqrt{1+(w/wc)^{2n}}}$
- wc es la frecuencia de corte
- K0 ganancia de camino directo
### Parametros para el disenio
Los parametros para el disenio de un filtro Butteworth son n y wc:

#### 1. Ap=3dB
- Wc=Wp
![[Pasted image 20221121113016.png]]
#### 2. Si Ap distinto de 3dB
![[Pasted image 20221121113012.png]]
wp=wc
- Para hacer coincidir la wc con la banda de paso o con la banda de bloque se hace la siguiente conversion
$$wc'=\frac{wp}{(10^{Ap/10}-1)^{1/2n}}$$
$$wc'=\frac{wb}{(10^{Ap/10}-1)^{1/2n}}$$

#### Obtencion de H(s)
Para obtener H(s) con la respuesta en frecuencia, usamos la siguiente relacion: $s^2=-w^2$
- Para hacerlo de manera mas practica, voy a tablas
#### Ubicacion de los polos en el Plano S de filtros Butter
![[Pasted image 20221121112402.png]]


## Transformaciones espectrales analogicas
### Disenio de filtro pasa bajo
Primero obtenemos un filtro con frecuencia de corte wc=1, para transformar este filtro al deseado tenemos que aplicar la sustitucion de $s=\frac{s}{wo.wc'}$ 
### Disenio de filtro pasa alto
Tenemos que hacer la sustitucion de s=wo/s pero cuando diseniamos el filtro pasa bajo prototipo tenemos que hacer que $wb=2.\pi.fc/fb$
### Disenio de filtro pasa banda
Tenemos que hacer la sustitucion aclarada en la imagen pero cuando diseniamos el filtro pasa bajo prototipo tenemos que hacer que $wb=\frac{ws2-ws1}{wp2-wp1}$
![[Pasted image 20221121113759.png]]
### Disenio de filtro rechaza banda
Tenemos que hace la sustitucion aclarada en la imagen pero cuando diseniamos el filtro pasa bajo prototipo tenemos que hacer que $wb=\frac{wp2-wp1}{ws2-ws1}$
![[Pasted image 20221123173339.png]]
