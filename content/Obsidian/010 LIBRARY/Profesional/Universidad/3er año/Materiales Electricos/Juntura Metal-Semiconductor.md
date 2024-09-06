

## Introduccion

Cuando se une un metal con un semiconductor, la unión puede ser rectificante o ohmica. La dirección de la corriente eléctrica que fluye a través de la unión depende de la posición relativa de los niveles de Fermi en el metal (EFM) y en el semiconductor (EFS).

Las posibles configuraciones son las siguientes:

- Metal-semiconductor Tipo N (| EFM |>|EFS |): La unión es rectificante, permitiendo la circulación de corriente en una sola dirección.
- Metal-semiconductor Tipo N (| EFM |<|EFS |): La unión es ohmica, permitiendo la circulación de corriente en ambas direcciones.
- Metal-semiconductor Tipo P (| EFM |>|EFS |): La unión es rectificante con polaridad opuesta a la anterior.
- Metal-semiconductor Tipo P (| EFM |<|EFS |): La unión es ohmica en este caso.

### Diagramas de Bandas y Funciones de Trabajo:

La función trabajo, Φ, del metal es la energía necesaria para extraer un electrón del mismo. La afinidad electrónica, χ, del semiconductor es la energía requerida para extraer un electrón de la banda de conducción. Cuando se juntan estos materiales, los electrones en el semiconductor pueden pasar al metal si su energía es mayor. Esto deja iones positivos en la frontera del semiconductor, creando una zona de depleción y una barrera de potencial.

### Equilibrio Termodinámico y Potencial de Juntura:

En equilibrio, los niveles de Fermi de ambos materiales deben igualarse. La diferencia de los niveles de Fermi antes de la unión resulta en una barrera de potencial, Vj0, que se expresa en voltios.

### Comportamiento Electroestático

El comportamiento electroestático de la unión metal-semiconductor es similar al de una unión p-n de Bruk. Esto significa que la unión puede ser modelada como un dispositivo de portadores mayoritarios, donde el flujo de corriente está dominado por los portadores mayoritarios en el material.

### Diferencias con una Juntura PN:

En una juntura metal-semiconductor rectificante, la zona de depleción se forma solo en el lado del semiconductor. El semiconductor inyecta electrones al conductor en polarización directa, y la carga se distribuye rápidamente en el conductor, evitando la difusión en el metal. Esto mejora los tiempos de conmutación de los diodos, conocidos como diodos Schottky.

### Explicacion didactica del tipo de union


1. **Unión Rectificante**: Cuando la función de trabajo del metal es mayor que la afinidad electrónica del semiconductor (Φ > χ), significa que los electrones en el semiconductor tienen un nivel de energía más alto en comparación con los electrones en el metal. En esta situación, algunos electrones del semiconductor pueden pasar espontáneamente al metal, dejando iones positivos en la frontera del semiconductor. Esta transferencia de electrones crea una zona de depleción en el semiconductor y da lugar a la formación de una barrera de potencial. La barrera de potencial bloquea el flujo de electrones en una dirección específica, lo que hace que la unión sea rectificante, actuando como un diodo.

2.  **Unión Ohmica**: En contraste, si la función de trabajo del metal es menor que la afinidad electrónica del semiconductor (Φ < χ), los electrones en el metal tienen un nivel de energía más bajo que los electrones en el semiconductor. En este caso, los electrones del metal pueden pasar fácilmente a la banda de conducción del semiconductor sin enfrentar una barrera de energía significativa. No se forma una zona de depleción ni una barrera de potencial notable, lo que permite el flujo libre de electrones en ambas direcciones. Esta unión se comporta como un contacto ohmico, sin restringir la corriente en ninguna dirección.

## Tipos de uniones
### Metal-semiconductor tipo N Rectificante
En este caso, el nivel de Fermi en el metal (EFM) es mayor que el nivel de Fermi en el semiconductor (EFS). Esto resulta en una unión rectificante que permite la circulación de corriente del semiconductor al metal.
![[Pasted image 20240521100823.png]]
![[Pasted image 20240522105111.png]]
### Metal-semiconductor Tipo N ohmica

En esta configuración, el nivel de Fermi en el metal (EFM) es menor que el nivel de Fermi en el semiconductor (EFS). La unión ohmica permite la circulación bidireccional de corriente.
![[Pasted image 20240522105121.png]]
![[Pasted image 20240522105128.png]]
### Metal-semiconductor Tipo P ohmica
En este caso, el nivel de Fermi en el metal (EFM) es menor que el nivel de Fermi en el semiconductor de tipo P (EFS). La unión ohmica también permite la circulación de corriente en ambas direcciones.
![[Pasted image 20240522105339.png]]
![[Pasted image 20240522105350.png]]
### Metal-semiconductor Tipo P rectificante

Aquí, el nivel de Fermi en el metal (EFM) es mayor que el nivel de Fermi en el semiconductor de tipo P (EFS). La unión rectificante permite la circulación de corriente del metal al semiconductor.
![[Pasted image 20240522105315.png]]
![[Pasted image 20240522105323.png]]
## Caracteriscas tension-corriente
Las ecuaciones de corriente para la unión metal-semiconductor son similares a las de una unión p-n de semiconductores. Sin embargo, se deben considerar constantes de Richardson efectivas y la influencia de la función de trabajo del metal.
- $I_s$ es mayor que en una union PN
- $V_{\gamma}$ es menor que el de una juntura PN  
![[Pasted image 20240522104243.png]]

La constante de Richardson efectiva, a menudo denotada como $A^*$ o $Ar$, se utiliza para calcular la densidad de corriente de saturación inversa (J0) en una unión metal-semiconductor. La ecuación que relaciona J0 con A* es la siguiente:

$$J0 = Ae^{(-qΦ/kT)}$$

donde:

- J0 es la densidad de corriente de saturación inversa,
- A* es la constante de Richardson efectiva,
- q es la carga del electrón,
- Φ es la función de trabajo del metal,
- k es la constante de Boltzmann, y
- T es la temperatura en Kelvin.

Ahora, veamos la influencia de la función de trabajo del metal (Φ):

- **Mayor función de trabajo (Φ)**: Una función de trabajo más alta del metal resulta en un valor más pequeño de A*. Esto significa que la densidad de corriente de saturación inversa (J0) también será más baja. En otras palabras, una función de trabajo más alta crea una barrera de potencial más alta para que los electrones la crucen, lo que reduce la cantidad de corriente inversa que puede fluir a través de la unión.
- **Menor función de trabajo (Φ)**: Por el contrario, una función de trabajo más baja del metal conduce a un valor más alto de A*. Esto resulta en una mayor densidad de corriente de saturación inversa (J0). Una función de trabajo más baja reduce la barrera de potencial para el flujo de electrones, haciendo que sea más fácil para ellos cruzar la unión en la dirección inversa.
### Ecuación de Poisson

La ecuación de Poisson describe la relación entre la densidad de carga, el campo eléctrico y el potencial en la unión. Es fundamental para calcular las características electroestáticas de la unión.

La ecuación de Poisson en su forma más general es:

$$∇²V = -ρ/ε$$

donde:

- ∇² es el operador laplaciano, que representa la segunda derivada espacial,
- V es el potencial eléctrico,
- ρ es la densidad de carga, y
- ε es la permitividad dieléctrica del material.

Ahora, veamos por qué esta ecuación describe la relación entre la densidad de carga, el campo eléctrico y el potencial en la unión metal-semiconductor:

1. **Densidad de Carga (ρ)**: La densidad de carga en una unión metal-semiconductor puede variar en diferentes regiones de la unión. En la zona de depleción, por ejemplo, hay una acumulación de carga positiva debido a la escasez de electrones. La ecuación de Poisson relaciona directamente la densidad de carga con el potencial eléctrico (V). Un cambio en la densidad de carga en una región afectará el potencial eléctrico en esa área.
    
2. **Campo Eléctrico (E)**: El campo eléctrico es el gradiente negativo del potencial eléctrico, es decir, E = -∇V. La ecuación de Poisson nos permite calcular el campo eléctrico resultante de una distribución de carga dada. En el contexto de la unión metal-semiconductor, el campo eléctrico juega un papel crucial en el movimiento de electrones y en la formación de la barrera de potencial.
    
3. **Potencial Eléctrico (V)**: El potencial eléctrico en una unión metal-semiconductor no es constante, especialmente en la región de la zona de depleción. La ecuación de Poisson nos ayuda a determinar cómo el potencial varía en función de la distribución de carga. El potencial eléctrico es importante porque afecta el movimiento de los portadores de carga y, por lo tanto, la corriente a través de la unión.






