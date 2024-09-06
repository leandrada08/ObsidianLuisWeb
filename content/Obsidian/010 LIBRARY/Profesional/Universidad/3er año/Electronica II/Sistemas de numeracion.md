## Sistemas de numeracion digitales
- Utilizaremos de valor posicional
- El digito mas significativo sera a la izquierda
	- El menos a la derecha

#### Numero de cuentas en cualquier base
$$N=\sum_{i+-p}^{q-1}{ai.b^i}$$
para b $\in$ N y $0<ai<b-1$ y ai $\in$ enteros
ai son los coeficientes de cada lugar y q el lugar

### Sistemas de usaremos
- Binomial
- Hexadecimal
- Decimal

## Conversiones
### Decimal -> Binomial
Se divide repetidamente el numero en 2 y se va escribienbo el resto
### Decimal -> Hexadecimal
Se divide repetidamente el numero en 16 y se va escribiendo el resto
### Hexadecimal -> binario
Se convierte cada digito hexadecimal en su equivalente binario
### Binario -> Hexadecimal
Se separa en grupo de 4 bit y se convierte en su equivalente

## Operaciones binarias
### Suma y resta
Se suma y se resta bit a bit, con las siguiente observaciones
*Observacion:* 1+1=10;0-0=0;10-1=1
### Multiplicacion
Se multiplica bit a bir, cualquier multiplicaciones es 0 menos 1x1=1

## Representacion de numeros signados
### Complemento a 1
Cambiar todos los 1 por 0
### Complemento a 2
En el complemento a 2, el bit más significativo (el bit más a la izquierda) se utiliza para indicar el signo del número: 0 para números positivos y 1 para números negativos. Los demás bits representan el valor absoluto del número.
La representacion sin signo equivalente de numeros negativos viene dad por $2^N-|a|$
Ejemplo: -9 su en 5 bit equivalente es $2^5-|-9|=23$


## Codigo
Se representa numeros, letras o palabras mediante un grupo especial de simbolos
### Ponderados
Cada codigo tiene asignado un peso, la suma de los pesos nos da el numero
### No ponderados
Se sigue otra reggla
#### BCD
Se representa cada numero digital con su equivalente binario
![[Pasted image 20230225184152.png]]
#### Gray
Codigo sin peso, usado para evitar errores cuando mandamos numeros binarios
#### Bytes
Consiste en 8 bits que puede representar cualquier tipo de dato informatico
#### ASCII
Codigo de 7 bit con el cual se representa todos los caracteres del teclado
#### Codigo Hamming



## Definiciones
- **Rango:** Diferencia entre el mayor número positivo y el menor número negativo representables.
- **Precisión:** Número total de valores distintos representables, que se determina por la cantidad de bits usados en la representación.
- **Resolución:** Distancia mínima entre dos valores consecutivos representables.
- **Exactitud:** Cercanía entre el valor real y su representación, determinada por la magnitud de la diferencia entre ambos.
- **Rango Dinámico:** Cociente entre el máximo valor absoluto representable y el mínimo valor absoluto (distinto de cero) representable.

## Escalado
Al implementar algoritmos usando aritmética de precisión finita, a veces es importante evitar el desbordamiento (overflow) ya que añade un error que es igual al rango dinámico completo del número.
### Reduccion
- Para evitar el desbordamiento, los números se reducen (scaled-down).
- Cuando un número tiene bits de signo redundantes, puede reducirse descartándolos.
	- Tambien se puede usar en caso de saber que nuestro valor final es solo entero o solo fraccionario, se puede quitar los bits sin importancias
- Esta reducción de bits no afectará el valor del número.
Ej:El número -2 como número signado en complemento a dos de 8 bits es 8’b11111110. En este caso contiene seis bits de signo redundantes que pueden descartarse, pudiendo representarlo sólo con 2 bits como 2’b10.
### Extension de signo
- En diseños digitales a veces también se requiere extender el signo de un número de N bits a un número de M bits para M > N.
	- Para operaciones como suma y resta
- Esta extension de signo se realizar debido a la necesidad de alinear la coma
	- Esto se realiza por si tenemos un numero negativo, si no expandimos el signo, no mantenemos la coherencia de las operaciones
- El signo se extiendo M>N bits.
- El valor del número no cambia pero si su representación equivalente.
Ej:El número -2 como número binario de 4 bits es 4’b1110. Extendiéndolo a un número de 8 bits es 8’b11111110.