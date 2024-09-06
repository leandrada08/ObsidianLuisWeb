# Introduccion Matlab
- Cuando realizamos una instruccion automaticamente se muestra el resultado de esta instruccion
- Para que no se muestre el resultado de la instruccion debemos poner **;**
## Funciones utiles
- clc
	- Limpia la pantalla "command window"
- min(Vector)
	- Nos calcula el minimo del vector
- min(min(matrix))
	- Minimo de una matrix
- mean(vector)
	- Media del vector
- std(V3)
	- desviacion estandar de un vector
- help funcion
	- Nos explica para que sirve la funcion
- length(vector)
	- longitud de un vector
- size(matrix)
	- Tamanio de la matrix, nos da el numero de fila y de columna
- plot(vector)
	- Me grafica el vector
- y=sin(vector)
	- Me define un vector con los valores del seno con los elementos del vector
- plot(vectorx,vectory)
	- Me hace una grafica donde vectorx es el eje x y el vectory es el eje y
- figure(n)
	- Defino la grafica n
- hold on
	- Mantengo la ultima figura y dibujo encima de ella
- poly(\[raiz1 raiz2\])
	- Te arma un polinomio basado en las raices
- tf(VectorNumerador,VectorDenominador)
	- Te arma una funcion transferencia
- conv(Vector1,Vector2)
	- Realiza la convolucion entre 2 vectores
- roots(Vector)
	- Busca las raices del vector ingresado
- step(FuncionTransferencia)
	- Respues al escalon unitario
- impulse(FuncionTransferencia)
	- Nos da la respues al impulso
		- Esta respuesta es la respuesta natural

## Definicion de variables
### Variable simple
Se lo hace sin definir que tipo de variable es. ej:
A=3+4i
Como se ve en este ejemplo, la variable que definamos puede ser real o compleja

### Vector
Para definir vectores de fila se lo hace
	V=\[1 2 3 4\]
Para vectores columnas
	V=\[1:2:3:4]
	V=\[1 2 3 4]'
Tambien se puede crear definiendo el principio y el final y los saltos que da
	V= 1:1:10
		En este caso el primer elemento es 1, el salto es de 1 y el final es 10
	
#### Extraccion de elemento
Se estrae con parentesis **()**
	V(2)
Si es una matrix
	V(fila,columna)
	V(3,2)
	Si tenemos una matrix y no definimos fila y columna, cuenta los elementos por columna
	V(10)

### Matrix
Se la define separando los vectores de una fila con espacio y separando filas con **;**


## Armar un codigo ejecutable
Hay que crear un archivo M-file, luego cuando lo corremos se ejecuta en la consola, luego podemos llamarlo desde la consola con el nombre del archivo

## Funciones Matlab PDS 
- Funcion interesante en matlab:
	- Filtro $h=fir1(n,\frac{fc}{(Fs/2)})$
		- Genera un filtro de orden n
	- Barrido en frecuencia $freqz(numerador,denominar,puntos)$
		- Hace un barrido de frecuencia de lo indicado
		- Esto nos devuelve frecuencia normalizada
			- Para calcular la verdadera frecuencia de corte
	- Figura con varias grafiacas $subplot(filas,columnas,LugarGrafica)$
	- Delta: $\delta (n-no)$ con n1<n<n2<
		- [x,n]=impseq(n0,n1,n2)
	- Escalon unitario : $u(n-no)$  con n1<n<n2<
		- [x,n]=stepseq(no,n1,n2)
	- Pasar de continua a discreta una senial
		- arreglo=c2d(SenialContinua, PeriodoMuestreo,'t') 
		- Consultar porque 't'
		- Esta funcion usa la transformada de tusti
	- Extraer numerador y denominador de una funcion de transferencia
		- {num,dend}=tfdata(sysd,'v')
	- Consultar sobre una funcion
		- help Funcion

#### Filtros butherworth en MATLAB 
$[a,b]=butter(N,\omega p,'s')$ 

#### Realizar filtro digital en matlab sin pasar por el analogico
$[a,b]=butter(2,Fc/(Fs/2))$

- Referir en la grafica la frecuencia a la frecuencia de corte
	- $plot(\frac{f.fs/2}{max(f),abs(h)}$

## Simulink
Se puede entrar desde la pestania superior o introduciendo en la barra de comandos simulink, luego entro a diagrama de bloque y comienzo a construir mi circuito




## MatLab Vision
### Introduccion
- Para abrir la ventana de desarrollo
	- Esto abre un tipo .fig
``` Python
guide 
```
- En esta ventana grafica tenemos varias herramientas para agregar a esta interfaz grafica
	- Texto
	- Ventanas de plot
	- Botones
- Cada uno de estos objetos tendran sus caracteristicas, que cuando apretamos doble click sobre alguno lo vemos
- Esta interfaz grafica esta basada en programacion orientada a objeto
	- Durante la ejecusion podemos modificar ciertas caracteristicas de este objeto modificando ciertos cuadros donde colcoaremos estas caracteristica
	- Luego, los botones estan asociados a metodos, que tambien pueden ser seleccionados cuando apretamos click derechos sobre ellos y vamos a la pestaña de ““view callback”
- Todas estas cosas que hacemos en nuestra ventana grafica, se escriben en nuestro archivo de codigo del tipo *.m*
- Dentro de este archivo de codigo, debemos especificar nuestras funciones de entrada y como manipulamos estas



## Observacion
- Cuando hacemos k.\*matriz de esta manera se multiplica k por cada valor de la matriz
