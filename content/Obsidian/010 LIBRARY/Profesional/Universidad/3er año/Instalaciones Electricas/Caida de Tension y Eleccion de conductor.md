# Intalaciones Electricas

## Caida de tension y eleccion de conductor

---

### Criterios para elegir un cable 
Continuando lo visto en [[Metales conductores#Cables]] .
Los criterios para seleccionar un cable son:
- Tension nominal
- Calculo termico
- Caida de tension
- Cortocircuito



------------ 
### Como saber la verdadera corriente que puede circular por un cable 
 Hay que tener en cuenta que hay otros factores que afectan la resistencia del cable, entonces, para calcular la verdadera corriente de circulacion se lo haria con la formula $$Ia'=f1.f2.f3.....Ia$$
Donde el valor de estos factores sera dado por una tabla dependiendo el factor ambiental o constructivo que estemos analizando




------------ 
### Tension nominal 
Buscamos que la tension nominal del cable sea mayor a lo sumo(No recomendable) igual a la tension de servicio
Si estamos en una instalacion de baja tension, elegimos el cable respecto a una tension de 1.1kV
La asilacion debe ser mayor a 1000$\Omega$ Por cada Volt transmitido



------------
### Calculo termico 
La temperatura generada por la intensidad de corriente nominal(El valor eficaz de esta) debe ser menor a la especificada por el cable. En el caso de conductores sin envoltura de proteccion, la temperatura ambiente no debe superar 40C, la del conductor 70C y la de cortocircuito 160C



------------
### Caida de tension 
Los valores de caida de tension se los calcula desde el tablero hasta la carga mas alejada con la ecuacion $$\Delta Uadm=K. Inominal.Longitud.(R.cos(\phi)+X.sen(\phi))$$
esta tiene que ser menor a:
- 3% Uadm para iluminacion
- 5% Uadm para motores en regimen
- 15% Uadm para motores en arranque
K es igual a 2 para sistemas monofasicos y $\sqrt{3}$


------------
### [[Corriente de cortocircuito]] 
Aqui verificamos la maxima solicitud termina que puede efectuar el conductor, con la formula $$S>\frac{Icc.\sqrt{t}}{K}$$
determinamos el valor minimo de seccion transversal que necesitariamos para que esto se cumpla. Tomamos un 0.1s<t<5s. Basicamente necesitamos que las corriente de cortocircuito no rompan el cable antes que el interruptor electromagnetico accione.
En esta formula K vale:
- 115 si Cobre+PVC
- 76  si Aluminio+PVC
- 143 si Cobre+XLP
- 94 si Aluminio+XLP
<!--ID: 1658522493857-->

------------ 
#### Obs:
Se puede tener una menor caida de tension en los cables y una menor seccion trasversal del conductor realizando [[Correccion del factor de potencia]]



 