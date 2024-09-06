**Nombre:** Luis Elian Andrada
**Mail:** leandrada08@gmail.com
**DNI:** 43362912

## Ejercicio 1
![[Pasted image 20240312113551.png]]
- Suponiendo que la flecha entre el nodo 1 y 7 esta en sentido contrario
- Suponiendo que la salida se da por el nodo 2

#### Apartado 1,2,3

| Lazos               | Periodo iteracion | Relacion de lazo |
| ------------------- | ----------------- | ---------------- |
| 1→2→3→4→5→6→7       | 6                 | 1                |
| 1→2→5→6→7           | 4                 | 2                |
| 1→2→3→8→9→10→7      | 6                 | 1,2              |
| 1→2→5→8→9→10→7      | 6                 | 3                |
| 1→2→3→11→12→13→10→7 | 7                 | 1,4              |
| 1→2→5→8→12→13→10→7  | 7                 | 3,5              |

#### Apartado 4

IPB=3,5

#### Apartado 5

Camino critico=7T

#### Apartado 6

- Al maximo camino critico que podemos llegar esta indicado con el IPB, por lo cual no podriamos llegar a un camino de critico de 3, si a uno de 3,5 o 4

- Diagrama con camino critico de 4:
![[Pasted image 20240312114252.png]]



## Ejercicios 4
- Aplicar la tecnica unfolding al filtro IIF

![[Pasted image 20240313152357.png]]
### Apartado 1
#### De 3 etapas
- j=0 → $(j+w)\%J=(0+1)\%3=1$ →$(0+1)/J=0$
- j=1 → $(j+w)\%J=(1+1)\%3=2$ →$(1+1)/J=0$
- j=2 → $(j+w)\%J=(2+1)\%3=0$ →$(2+1)/J=1$ 
![[Pasted image 20240313154223.png]]


#### De 4 etapas
- j=0 → $(j+w)\%J=(0+1)\%4=1$ →$(0+1)/J=0$
- j=1 → $(j+w)\%J=(1+1)\%4=2$ →$(1+1)/J=0$
- j=2 → $(j+w)\%J=(2+1)\%4=3$ →$(2+1)/J=0$ 
- j=2 → $(j+w)\%J=(3+1)\%4=0$ →$(3+1)/J=1$ 

![[Pasted image 20240318105425.png|300]]



### Apartado 2
- [ ] Identicar los lazos en la estructura unfolded y calcular sus IPBs asumiendo que los multiplicadores y sumadores toman 3 y 2 unidades de tiempo, respectivamente.
	- Se hacen infinitos estos lazos, como simplificar el analisis