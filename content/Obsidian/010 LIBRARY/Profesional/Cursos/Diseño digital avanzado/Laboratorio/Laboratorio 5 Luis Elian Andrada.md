**Nombre:** Luis Elian Andrada
**DNI:** 43362912
## Simulacion
![[Pasted image 20240502103440.png]]

## Parte 1 
- El objetivo es evaluar la complejidad y el timing del sistema implementando las técnicas de reducción de complejidad Pipelining y Retiming.
- [x] En todos los casos obtener el reporte de Celdas y el peor camino crítico.
	- [x] Justificar los resultados en un informe.
### Analisis de Sintesis e implementacion de todos los casos
![[Pasted image 20240502120715.png]]
- Caso 1 → Implementacion de filtro con diseño basico y sin implementar tecnicas de Pipelining ni te Retiming
- Caso 2 → Se implementan tecnicas de Pipelinig manualmente
- Caso 3 → Se implementan tecnicas de Retiming automaticamente por la herramienta
- Caso 4 → Se fuerza a la herramienta a una sintetizacion del hardware sin ningun tipo de sintetizacion del hardware, en este caso no se aplica ni Pipelining ni Retiming
- Caso 5 → Al caso extremo anterior se le aplica tecnicas de Retiming automaticamente por la herramienta

#### Informe
En todos los casos la utilizacion de DSP es 0 ya que se fuerza a la herramienta a que sea de esta manera para poder hacer un mejor analisis de los recursos utilizados.
- Cuando hago referencia a al utilizacion de recursos logicos me refiero a la utilizacion de LUT
- Cuando hago referencia a la utilizacion de memoria me refiero a la utilizacion de FF

*Caso 1*:
- Se obtiene un camino critico bastante ajustado, casi en el limite del constrains
- Utilizacion de recursos logicos es demasiado baja, ya que en este caso se sintetiza el diseño para el caso particular.
- La utilizacion de memoria es la minima de todos los resultados, esto se debe a que los registros se colocan antes de hacer las operacion de multiplicacion y de suma por lo cual estos tienen menor tamaño que en los otros casos

*Caso 2:*
- Hay un camino critico bastante menor que en el caso 1 debido al pipelining
- Pero tambien se puede notar que aplicar pipelining aumento casi el doble la memoria
	- Esto se debe a que los registros agregados estan a la salida de los multiplicadores por lo cual tienen un tamaño mayor a la registros del caso 1
- Ademas tambien se puede notar un aumento minimo de los recursos logicos que podemos despreciar en este analisis y podemos decir que se debe a los registros agregados

*Caso 3:*
- Al aplicar Retiming al caso 1, los recursos logicos se mantienen iguales
- La memoria crescen un poco debido a que los registros son colocados en otros lados, donde seguramente el tamaño de los cables son mayores debido a operaciones matematicas
- Se ve una mejora bastante importante en el camino critico debido al retiming aplicado, a pesar de mejor demasiado el camino critico, los recursos utilizados no aumentaron mucho, por lo cual podriamos suponer que es una solucion optima y mejor que el pipelining aplicado manualmente

*Caso 4:*
- Se ve un aumento casi del 3 en recursos y un minimo aumento en la memoria
- Esto se debe a que se aplica el maximo de recursos necesarios, porque se forzo a la herramienta a hacerlo
	- Esto hacer que no se puedan eliminar logica usada en operaciones por 0 como pasa en el primer caso
- Este caso de analisis es muy interesante ya que en caso de querer hacer un filtro reutilizable para distintos parametros, se usara esta cantidad de logica la cual es la maxima para esta aplicacion
- Tambien podes ver que el camino critico aumenta demasiado debido a esta logica agregada

*Caso 5:*
- Este caso es muy interesante a que podemos ver que solo aplicando el retiming manual de la herramienta podemos cumplir con nuestras restricciones de tiempo y mejorar a la del primer caso con menos logica y hasta con pipeline
- Tambien se utiliza una cantidad de memoria mayor a la sin retiming debido a lo mismo que se explico en el caso 3





## Parte 2
- El objetivo es comparar la complejidad y el timing entre un filtro FIR Directo con paralelismo 4 y un filtro transpuesto Unfolding de orden 4.
- Pasos:
	- [x] Generar un proyecto nuevo.
	- [x] Diseñar e Implementar un filtro FIR paralelo.
	- [x] Diseñar e Implementar un filtro FIR transpuesto utilizando la técnica unfolding de orden 4.
	- [x] En ambos casos proponer un TestBench para verificar la conexiones.
	- [x] En base a los ejercicios anteriores armar un constraint que seleccione algunos pines de la FPGA y configurar el pin de clock.
	- [x] Sintetizar los diseños a 100MHz.
	- [x] Obtener los reportes de celdas y camino crítico para ambos casos.
	- [x] En caso de encontrar problemas de timing aplicar alguna de las técnicas vistas anteriormente para resolverlo (pipeline o retiming).
*Parametros:*
- Paralelismo de entrada 4.
- Paralelismo de salida 4.
- Resolución: X S(8,7), h S(8,7) e Y determinada por el diseñador.
- El filtro FIR paralelo debe incluir un Regressor para sincronizar las muestra de entrada.
- En el caso del filtro FIR directo, las muestras entran a los filtros en forma paralela (no se necesito el bloque shift register).
- Todos los filtros utilizan los mismos coeficientes.
	- coeff\[0] = 8’d0;
	- coeff\[1] = 8’d229;
	- coeff\[2] = 8’d0;
	- coeff\[3] = 8’d81;
	- coeff\[4] = 8’d127;
	- coeff\[5] = 8’d81;
	- coeff\[6] = 8’d0; 
	- oeff\[7] = 8’d229;


### Test Bench
#### Paralelo
![[Pasted image 20240509184612.png]]
#### Unfolding
![[Pasted image 20240509184806.png]]
### Implementacion con 100Mhz
#### Paralelo
![[Pasted image 20240509184039.png]]
#### Unfolding
![[Pasted image 20240509190403.png]]

### Reporte de celda y camino critico
#### Paralelo
![[Pasted image 20240509184119.png]]
![[Pasted image 20240509184150.png]]
#### Unfolding
![[Pasted image 20240509190515.png]]
![[Pasted image 20240509190433.png]]



