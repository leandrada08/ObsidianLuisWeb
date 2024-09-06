
## Criterio de estabilidad de Routh
Este criterio permite analizar la estabilidad de un sistema sin tener que obtener los polinomios, cuando se aplica el criterio a un sistema de control, la informacion sobre la estabilidad absoluta se obtiene directamente de los coeficientes de la ecuacion caracteristica
### Procedicimiento
1. Escribo la ecuacion caracteristica, busco que el *polinomio este completo*
	-  Verifico que $an\neq 0$ 
2. Analiso el valor de los coeficientes de la ecuacion caracteristicas
	- Una condicion necesaria pero no suficiente para la estabilidad es que *todos los coeficientes sean positivos*
3. Se completa el arreglo de Routh 
	- La condicion necesaria y suficiente para la estabilidad de un sistema es que los coeficientes de la ecuacion caracteristica sean todos positivos y que todos los terminos de la primera columna del arreglo de Routh sean positivo
#### Observaciones
- Para polinomios de orden menor o igual a 2, las condiciones necesarias son suficientes
- Se lo utiliza cuando tenemos un parametro variable para calcular los valores de este parametro que hacen estable al sistema

### Arreglo de routh
![[Pasted image 20221108110828.png]]
#### Obs
Si algun coeficiente de la primera columna es 0, se lo toma como positivo

### Criterio de routh para la estabilidad relativa
En este caso remplazamos la varibales s por $s=s'-\sigma$ , de esta manera, el numero de coeficientes negativo en el arreglo de routh seria igual a las raices localizadas en el semi plano derecho

### Aplicacion del criterio de routh a sistema de control
Solo nos sirve para saber si nuestro sistema es estable y para analizar como cambiara nuestra estabilidad si cambiamos uno de los parametros
