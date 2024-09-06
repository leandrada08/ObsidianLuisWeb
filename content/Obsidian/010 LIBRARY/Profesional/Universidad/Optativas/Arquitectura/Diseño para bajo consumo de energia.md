
## Repaso
**Ecuacion consumo de energia dinamico:** $$P=N*A*C*V^2*f$$
- La evolucion tecnologica requiere menos consumo de energia

## Mejora del proceso de fabricacion
Mejoro tanto el proceso que las compuertas de los transistores tienen solo unos atomos de ancho y no son ideales. Esto genera que se produzca *corrientes de perdida.*
Pero tambien permite reducir el tamaño del chip, lo cual permite reducir el consumo de energia. *Esto permite poner chip en paralelo*
### Corrientes de perdida
Al disminuir el tamaño de transistor, la relacion entre corriente de perdida y corriente activa va aumentando esto hace que aumente el consumo estatico de energia.
- Como evito esto? Adapto
#### Adaptar proceso al producto
No todos los dispositivos necesitan altas frecuencias

### Chip en paralelo
Reemplazamos un bloque logico que hace una tarea, por dos bloques mas pequeños, que hacen media tarea cada uno
![[Pasted image 20230609081830.png|500]]
- La frecuencia de los bloques se puede reducir a la mitad, porque tienen que realizar la mitad de la tarea en la misma unidad de tiempo. 
- Mantenemos la productividad, duplicando el área.
- La reducción de frecuencia permite una reducción similar de la tensión, y por lo tanto la potencia se reduce a la cuarta parte.
Esta alternativa es bastante utilizada en sistemas embebidos.
Otra alternativa es mantener el consumo y mejorar la performance.
![[Pasted image 20230609081710.png|400]]

## Otras tecnicas

### Escalado dinamico de frecuencia
El procesador va modificando su frecuencia para reducir el consumo.
Tiene una frecuencia base de trabajo y cuando requiere mayor performance, se aumenta la frecuencia. Entonces los procesadores modernos vienen con una frecuencia base y una frecuencia maximo, la variacion de estas frecuencias se hace a pasos escalonados.

No todas las partes del procesador tienen que trabajar a la misma frecuencia.


### Escalado dinamico de tension
Se manejan multiples niveles de tension en un mismo procesador. Porciones del procesador fuera del camino critico reciben menos tension.

### Power Gating
Agregar transistores para apagar ciertos bloques de logica que no se usan todo el tiempo. Los transistores nuevos controlan la alimentacion del circuito, esto baja mucho el consumo estatica pero agregan retardos.
Otros procesadores modernos pueden apagar nucleos completos.

### Clock Gating
Ya que los registros consumen mucho y no se cambian mucho, se desabilita el clock
![[Pasted image 20230609085140.png|400]]

### Procesadores heterogeneos
Usar en un mismo chip dos nucleos: *uno gran de mayor performance y uno pequeño de menor consumo.*
- Ambos son *implementaciones diferentes del mismo ISA*.
Esta idea la aplico ARM pero a un nivel mayor, se combinan 8 nucleos y se flexibiliza a la hora de hacer combinaciones.

![[Pasted image 20230609092936.png]]
![[Pasted image 20230609092955.png]]