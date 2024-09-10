


# Sentencias Verilog
## Introducción
- **Selectores**
	- Que tipo de selectores existen en Verilog?
- **Loop**
	- Que tipos de loop existen en verilog?



## Selectores
### Case
- La sentencia case evalúa una expresión y en función de su valor ejecuta la sentencia o grupo de sentencias agrupadas en el primer caso en que coincida.
- En caso de no cubrir todos los posibles valores de la expresión a avaluar, es necesario el uso de un caso por defecto (default).
	- Si no ponemos el dafault y no cubrimos todos los casos se generara memoria, ya que debera almacenar un valor viejo en ese caso
- La sentencia case reconoce tanto al valor z como x como valores lógicos. Se puede usar el símbolo ? para representar un valor indiferente (“don’t care”).
	- En caso de simulacion hace falta el default aunque esten todos los valores logicos posibles(para cubrir el desconocido e alta impendacia),  en caso de sintesis lo podemos sacar si tenemos todos los casos asignados
- Existen dos variantes de case:
	- casez: Considera los valores en z como indiferentes (“don’t care”).
	- casex: Considera los valores en x y z como indiferentes (“don’t care”).
- Estamos usando asignacion bloqueante para que el circuito sea puramente combinacional

``` systemverilog
always @(*) begin
    case (sel)
        2'b00: out = in1; // Caso 00
            // Acciones a realizar cuando señal_de_control es 00
        2'b01: out = in2; // Caso 01
            // Acciones a realizar cuando señal_de_control es 01
        2'b10: out = in3; // Caso 10
            // Acciones a realizar cuando señal_de_control es 10
        2'b11: out = in4; // Caso 11
            // Acciones a realizar cuando señal_de_control es 11
        default: out = 16'bx; // Se coloca el default para los casos de X e alta impedancia, en este caso le asignamos un X a la salida
    endcase
end
```
#### Ejemplo de unidad de control con case
![[Pasted image 20231012131008.png]]
- En este caso analizamos un opCode para saber que funcion llamaremo, si la de operar, leer en memoria o escribir
### If
- Evalúa la expresión y realiza una tarea o asignación en caso de ser True o False.
- Soporta múltiples condiciones.
- En caso de tener varias condiciones hace falta colocar el begin y end, encaso de una condicion simple no

![[Pasted image 20231013134119.png]]

### Sentencias Case vs if
- Un If o un Case nos infiere un multiplexor
- La diferencia entre usar If o Case
	- Si usamos un case, nos genera un multiplexor de la cantidad de entradas como de casos y de 1 salida
	- Si usamos if, nos genera una arbol de multiplexores


## Loop
Se utilizan para ejecutar un bloque de sentencias múltiples veces.
- **for:** Es sintetizable y el *más comúnmente usado* en RTL.
- **while:** Es sintetizable pero *no se recomienda* su uso en RTL.
- **repeat:** Es sintetizable pero *no se recomienda* su uso en RTL.
- **forever:** No es sintetizable, *sólo se usa en simulaciones*.
### Usando FOR para describir hardware
- En este ejemplo se usa para describir un registro de desplazamiento
![[Pasted image 20231012190535.png]]

