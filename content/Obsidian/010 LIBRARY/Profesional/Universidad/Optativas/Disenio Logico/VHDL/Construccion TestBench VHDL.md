## Atributos
Se utilizan para obtener informacion sobre el tamanio, el alcance y la indexacion de una matriz, tambien se puede usar para seniales. Es buena practica usarlo para que nuestro codigo sea generico
### Atributos de arreglo
Sea "A" un arreglo

|Atributo|Descripcion|
|---|---|
|A’left|Devuelvela posición de mas a la izquierda de un tipo o subtipo|
|A’right|Devuelve la posición de mas a la derecha de un tipo o subtipo|
|A’high|Devuelve la posición superior de un tipo o subtipo|
|A’low|Devuelve la cota inferior de un tipo o subtipo|
|A’length|Devuelve el número de elementos de un arreglo|
|A’ascending|Devuelve un valor booleano verdadero si el rango de un tipo o subtipo es declarado en forma ascendente.|
Atributos de arreglos Relativos a rangos

|Atributo|Descripcion|
|---|---|
|A’range|Devuelve el rango un arreglo|
|A’reverse_range|Devuelve el rango en reverso de un arreglo|

![[Pasted image 20230425133807.png|500]]

### Atributos de seniales
Sea "S" una senial

|Atributo|Descripcion|
|---|---|
|S’event|Verdadero si hay un evento en S en el ciclo actual de la simulación, false en caso contrario (Chequea un cambio en la señal S)|
|S’active|Verdadero si hay una transacción S en el ciclo actual de la simulación, falso en caso contrario ( Chequea alguna actividad en la señal S aunque no haya cambio de valor)|
|S’last_event|El intervalo de tiempo desde el último evento en S|
|S’last_active|El intervalo de tiempo desde la última actividad en S aunque no haya cambio de valor|
|S’last_value| El valor de S justo antes del último evento en S|
|S’stable| Verdadero si S se mantiene estable en un Intervalo de tiempo|


## Declaracion secuencial Assert
Permite chequear en una simulacion si la condiciones esperadas se cumplen en un modelo.
``` VHDL
assert <boolean_expression>
    report <string_expresion>
        severity <severity_level>;
```
Se chequea que la expresion booleana se cumpla, en caso de no hacer se envia un mensaje(string_expresion) con el nivel de severidad
### Niveles de severidad
- Note: Mensaje al diseniador
- Warning: Situaciones inusuales
- Error: Errores y requieren acciones correctivas
- Failure: Reportan inconsistencias

![[Pasted image 20230425133845.png|500]]

## Verificacion
![[Introduccion a VHDL#Flujo de disenio FPGA]]

### Test bench
Un test bench es un módulo VHDL que se utiliza para probar y simular el comportamiento de un modelo VHDL. Básicamente, un test bench proporciona un entorno de prueba controlado en el que se pueden aplicar estímulos al modelo y se pueden verificar las respuestas esperadas. El proceso de generación de estímulos puede ser tan simple como enviar una señal constante al modelo, o tan complejo como simular el comportamiento de un sistema completo.
- Genera estimulos para simulacion
- Aplica los estimulos al circuito y recoge las salidas
- Compara las respuestas con valores esperados
- Debe ser creado por un ingeniero diferente al creador del circuito
![[Pasted image 20230425134018.png|500]]
#### Partes de un test bench
- Entidad
    - Declaracion vacia
- Arquitectura
    - Componente
    - Seniales locales
    - Instanciacion del component
    - Declaracion de estimulos
    - Chekeo de valores

### wait
Se usa en los procesos para realizar asignaciones.
``` VHDL
wait for time; --Espero el tiempo "time" para realizar la accion
wait until condition; --Espero que se cumpla la condicion para realizar la accion
wait on signal_list; -- Espero que la seniales se modifique para realizar la accion
wait; -- Espero indefinidamente
```

**Insertar Ejemplos**


#### Observaciones
- Evitar cambiar el dato en simultaneo con un clock
- Evitar condiciones de carrera


#### Generacion de datos
*Absoluta en tiempo:* Formas de onda de señal que se especifican para cambiar en tiempos de simulación en relación con el tiempo anterior, de manera acumulada en el tiempo
![[Pasted image 20230425134137.png|400]]
*Relativa en tiempo:* Formas de onda de señal que se especifican para cambiar en tiempos de simulación absolutos desde el momento en que comienza la simulación
![[Pasted image 20230425134145.png|400]]