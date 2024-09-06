
# Cosas para aprender a futuro
- Se puede crear ambientes de trabajo para hacer analisis de distintas sintesis o implementaciones sin perder la anterior
	1. Ir a Desing runs → Apretar el boton *+*
	2. Definir si se requiere implementacion, sintesis o ambas
	3. Elegir el constrain y el tipo de estrategia de vivado a usar
	- Luego se genera otro entorno de trabajo y se debe seleccionar cual activar aprentando click derecho y activando
![[Pasted image 20240502104929.png]]


- Implementacion generica vs implementacion especifica → Analisis para proyecto
	- En la implementacin generica se usara muchisimo mas componentes que en las especificas
	- Esto se debe a que la herramienta no podra sintentizar el diseño en base a valores usados, por lo cual debera usar todos los componentes necesarios
	- Por ejemplo si tenemos un filtro con la mitad de los valors 0 y la mitad 1(que es muy probable por entropia), el resultado sera un filtro de la mitad de recursos que uno que tiene todos 1, que seria aproximadamente el que se deberia implementar en un filtro generico
