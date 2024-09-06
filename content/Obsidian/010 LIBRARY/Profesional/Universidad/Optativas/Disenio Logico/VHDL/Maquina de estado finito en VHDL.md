## Sistema general de sintesis
![[Pasted image 20230502081735.png|500]]
- Estado actual es la memoria: Proceso sincronizado
- Proximo estado es un sistema combinatorio: Proceso combinatorio
### Mealy y Moore
![[Pasted image 20230502082002.png|500]]
### Diagrama de flujo general de MEF en VHDL
1. Especificacion
	- Con palabras
	- Con diagramas de transicion 
2. Diagrama de estados
3. Definir un type enumerado de MEF
4. Definir seniales de MEF (estado actual y siguiente)
5. Escribir el codigo.

#### 3 y 4) Type enumerado: Parte declarativa
``` VHDL
-- Declarar los estados de la MEF como tipo numerado
type estado_MEF is(Estado1,Estado2,Estado3,Estado4);
.
.
.

-- Declaro seniales del tipo estado_MEF
signal estado_actual, estado_siguiente: estados_MEF;
```

#### 5) Proceso sincronico
Es la memoria de la MEF. Decide cuando la MEF cambia de estado
- Activo por flanco de clock
- En algun momento debemos usar la sintaxis "estado_actual<=estado_siguiente"

#### 5) Proceso combinacional
Asigna saldias dependiento del "estado_actual".
- Uso de "Case" para asignar salidas y "estado_siguiente"
- Evitar latch no deseados
- Se usa "if-then-else" para MEF Mealy. Genera la dependencia de la salida con el "estado_actual" y la entrada.

#### Observaciones
- Los Reset siempre deben ser asincronico

## Estilos de diseño
![[Pasted image 20230502084325.png|300]]
