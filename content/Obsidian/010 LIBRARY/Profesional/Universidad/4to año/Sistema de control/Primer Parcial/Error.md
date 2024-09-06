## Error de estado estacionario
Para analizar el error de estado estacionario pasaremos redibujaremos el sistema como se muestra a continuacion
![[Pasted image 20221011195757.png|300]]![[Pasted image 20221011195801.png|290]]
De esta manera nos quedara la funcion de transferencia como $$(i)\frac{E(s)}{R(s)}=\frac{1}{1+G(s).H(s)}$$
Para encontrar el error de estado estacionario aplicaremos el teorema del valor final, entonces el error sera: $$e=\lim_{x \to infinito}{e(t)}=\lim_{s \to 0}{s.E(s)}=\lim_{s \to 0}{\frac{s.R(s)}{1+G(s).H(s)}}$$Para simplificar el analisis de este error definiremos varias cosas
### Analisis de funcion de transferencia de lazo abierto
La funcion de transferecia de lazo abierto se la define como $G(s).H(s)$ y se la puede escribir de manera generica como :$$G(s).H(s)=\frac{k.(a1.s+1).(a2.s+1).....(an.s+1)}{s^n.(b1.s+1).(b2.s+1).....(bm.s+1)}$$
Podemos ver en la ecuacion (i) que este producto de $G(s).H(s)$ queda en el denominador y es lo que define el valor del error, por lo que cuando analicemos el error, solo nos hara falta analizar el valor final de este producto, para simplificar aun mas el analisis, definiremos los tipos de sistemas.
#### Tipo de sistema:
Se dira que nuestro sistema es del orden de la cantidad de polos que tiene en el origen
Ej:
- n=0 entonces sistema de tipo 0
- n=1 entonces sistema de tipo 1

### Determinacion del error dependiendo del tipo de sistema y del tipo de entrada
![[Pasted image 20221011195609.png]]

### Calculo de las constante de error
Para calcular la constante de error tenemos que aplicar el teorema de valor final a la funcion de transferencia de lazo cerrado G(s).H(s).