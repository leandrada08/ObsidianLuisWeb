## Introduccion al problema
- Un ISA establece el “contrato” entre el software y el hardware por debajo.
- Los programa de usuario solicitan servicios al SO a traves de llamadas al sistemas
Hasta aquí, todas las técnicas vistas en Arquitectura de Computadoras hacen que una computadora funcione completamente bien. Pero, es posible que aunque los programas funcionen correctamente, se filtre información mediante ataques tipo side channel
## Ataques de tipo side-channel
Ataques basados en mediciones físicas indirectas de un sistema informático.
- No buscan debilidades inherentes del sistema, sino canales que no deberían ser usados para transmitir información.
- La operación "normal" de un sistema produce ciertas variables físicas secundarias que pueden ser medidas, y de esa manera deducir información sobre el sistema mismo.
- En 2018 descubrieron que la arquitectura de los micros tienen muchas vulnerabilidades al igual que el cache y la jerarquia de memoria


## Ataques de ejecucion transitoria
- Durante un breve período de tiempo se ejecutan instrucciones que modifican algún estado de la microarquitectura. 
- Esas instrucciones son eventualmente descartadas a nivel arquitectura, pero los rastros que dejan no, dando lugar a posibles side channels
### Ataque de ejecucion transitoria tipo *Meltdown*
Relacionados con romper barreras de aislamiento. Ocasionados por excepciones , de cualquier tipo. Saltean políticas de seguridad basadas en hardware
- Normalmente , las excepciones son tratadas al terminarse las instrucciones ( commit
	- Hay una ventana de ejecución transitoria desde que se produce una excepción, hasta que se la atiende.
	- Con ejecución especulativa, las instrucciones no generan excepciones hasta que dejan de ser especulativas.
#### Analisis con codigo
``` C
if ( cualquier condición que haga fallar la predicción de saltos ){
	trusted_value = kernel_mem [untrusted_offset];
	tmp = user_mem [(trusted_value) & mask];
	}
```
- La instrucción Ld que se ejecuta especulativamente intenta acceder a una dirección de memoria no permitida.
	- Genera una excepción, pero al ser especulativa, no se le da importancia.
	- A pesar de eso, se trae igual el dato especulativamente para ganar tiempo, aunque se sabe que será descartado posteriormente.
	- Sin embargo, mientras tanto, ese dato se utiliza como índice para una segunda instrucción Ld y acceder a otra dirección de memoria conocida, que también será descartada.
- En resumen, ambos valores de memoria serán descartados y no serán accesibles. Entonces, ¿cuál es el problema?
	- El problema radica en que deja rastros en las cachés, ya que los datos fueron cargados.
- Posteriormente, se miden los tiempos de acceso a esa memoria conocida.
	- El acceso que demore menos tiempo será atribuido al dato traído especulativamente, generando una vulnerabilidad de seguridad.



### Ataque de ejecucion transitoria tipo *Spectre*
- Todos los relacionados con ejecutar código de manera especulativa.
- Ocasionados por fallas en la predicción del flujo de datos o de control.
- Saltean políticas de seguridad basadas en software.