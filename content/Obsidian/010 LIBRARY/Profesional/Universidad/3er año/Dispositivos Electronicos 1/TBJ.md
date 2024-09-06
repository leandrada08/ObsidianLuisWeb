# TBJ
Transistor bipolar de juntura
- Para lograrlo se unen 3 semiconductores
## Tipos
- *NPN*
- *PNP*

## Estructura fisica
![[Pasted image 20230227191049.png|500]]

## Modelos
### Modelo de Eber&Moll
![[Pasted image 20230227191151.png]]
- Donde : $Icc=Is(e^{Vbe/Vt}-1)$

### Modelo en zona activa directa
- Modelo valido cuando el dispositivo esta polarizado en zona activa directa
![[Pasted image 20230227191257.png]]
#### Limitaciones del modelo
- No contempla max de tension,corriente y potencia

### Modelo de pequenia senial
![[Pasted image 20230227191415.png]]
Donde:
- $gm=Icp/Vt$
- $R\pi=\beta.Vt/Icp$
- $R0=Va/Icp$
- $R\mu=Ro.\beta$

## Principio de funcionamiento
![[Pasted image 20230227192623.png|500]]
- Zona N pequenia para que llegue la mayor cantidad de portadores del emisor al colector
1. Los electrones del emisor se recombinan con los huecos de la base
	-  Solo se pueden recombinar hasta el numero de huecos de la base
2. La corriente de base reabastece de huecos buscando la nuetralidad electrica
3. Este reabastecimiento no es suficiente
4. Al no reabastecer con la misma velocidad que se recombinan, se almacenan cargas, que por la tension entre colector y emisor, estas saltan entre estos y otros pasan por base y luego para colector. Hay una mezcla de corriente de difusion y de carga

## Respuesta en frecuencia
![[Pasted image 20230227192843.png]]