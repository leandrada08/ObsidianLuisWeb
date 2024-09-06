
## Unión y Niveles de Energía de Fermi
Cuando un material tipo P (exceso de huecos) se une a un material tipo N (exceso de electrones), los niveles de energía de Fermi se alinean. Esto causa una difusión de electrones del lado N al lado P y de huecos del lado P al lado N, buscando un equilibrio.
![[Pasted image 20240517102427.png]]
## Formación de la Zona de Depleción
Al difundir electrones y huecos, se neutralizan mutuamente creando una zona sin portadores móviles conocida como zona de depleción. Esta zona actúa como una barrera potencial debido a las cargas fijas de los iones donadores (N) y aceptadores (P) que permanecen.
![[Pasted image 20240517102515.png]]
### Corriente de Huecos y Electrones
1. **Por Difusión:** Huecos y electrones se mueven debido a diferencias en sus concentraciones. Los huecos se difunden del P al N y los electrones del N al P.
2. **Por Campo Eléctrico:** En la zona de depleción, el campo eléctrico creado por la barrera potencial empuja los huecos hacia el P y los electrones hacia el N.

### Ley de la Juntura
La ley de la juntura establece un equilibrio entre las corrientes de difusion y campo en la union
- $J_{Dp}=J_{Ep}$
- $J_{Dn}=J_{En}$

## Juntura PN usando bandas
![[Pasted image 20240517102936.png]]
### Explicación de la Juntura Usando Bandas de Energía
En equilibrio, la banda de conducción del N está más baja que la del P, y la banda de valencia del P está más alta que la del N. La alineación de los niveles de Fermi crea una curvatura en las bandas de energía en la zona de depleción, formando la barrera potencial.
![[Pasted image 20240517103317.png]]
- Si la expresamos esta energia en Volt
 ![[Pasted image 20240517103437.png]]
![[Pasted image 20240517103603.png]]


## Polarizaciones
### Modificación de la Barrera con la Polarización Directa
Reduciendo la barrera potencial, permitiendo que los portadores mayoritarios (electrones en N y huecos en P) crucen fácilmente la juntura, facilitando la corriente.
![[Pasted image 20240517103651.png|300]]
![[Pasted image 20240517104008.png|300]]
### Modificacion de la Barrera con la Polarizacion Inversa
Aumentando la barrera potencial, haciendo más difícil que los portadores minoritarios (electrones en P y huecos en N) crucen la juntura, impidiendo la corriente significativa.
![[Pasted image 20240517103717.png|300]]
![[Pasted image 20240517104026.png|300]]
### Observaciones
#### Rectificación de la Juntura PN
La juntura rectifica debido a la barrera potencial que solo permite flujo de corriente en una dirección:
1. **Sentido Directo:** La barrera disminuye y los portadores mayoritarios pueden cruzar.
2. **Sentido Inverso:** La barrera aumenta y los portadores minoritarios no pueden cruzar fácilmente.

#### Corriente en Sentido Directo e Inverso
1. **Directo:** Con la reducción de la barrera, los electrones del N se mueven al P y los huecos del P al N, permitiendo una corriente significativa.
2. **Inverso:** El incremento de la barrera impide que los portadores minoritarios crucen, resultando en una corriente insignificante.

#### Peso de Portadores Mayoritarios vs. Minoritarios
En condiciones normales de operación:
- **Mayoritarios:** Determinan la conducción en polarización directa. Son cruciales para el flujo de corriente significativo.
- **Minoritarios:** En polarización inversa, su movimiento es muy restringido por la barrera elevada, contribuyendo a una corriente muy pequeña (corriente de saturación inversa).



# Juntura PN polarizacion directa
## Corrientes y concentracion
![[Pasted image 20240517110811.png]]
### Inyección de Huecos y Electrones en la Unión
![[Pasted image 20240517110838.png]]
1. **Inyección de Huecos ( $p_n(x_n)$ ):**
   - Huecos son inyectados desde la región P a la región N.
   - La concentración de huecos inyectados decae exponencialmente desde la frontera de la región N hacia dentro.
   - $p_n(x)$ = $p_{n0} e^{(V - V_0) / V_T}=p_{n0} ( e^{(V/V_T)} - 1 ) e^{(-x / L_p)}$ (donde $V$ es el voltaje aplicado).

2. **Inyección de Electrones ( $n_p(-x_p)$ ):**
   - Electrones son inyectados desde la región N a la región P.
   - La concentración de electrones inyectados decae exponencialmente desde la frontera de la región P hacia dentro.
   - $n_p(x)$ = $n_{p0} e^{(V - V_0) / V_T}=n_{p0} ( e^{(V/V_T)} - 1 ) e^{(-x / L_n)}$.


- $L_n$ y $L_p$ son las longitudes de difusión de electrones y huecos respectivamente.
- $n_{p0}$ y $p_{n0}$ son las concentraciones de equilibrio de electrones en la región P y de huecos en la región N respectivamente.

### Corriente de Difusión de Huecos y Electrones
![[Pasted image 20240517112214.png]]
1. **Corriente de Difusión de Huecos:**
   - La corriente de huecos ($J_p$) se debe a su difusión en la región N.
   - $J_p = q D_p \frac{dp_n(x)}{dx}$.

2. **Corriente de Difusión de Electrones:**
   - La corriente de electrones ($J_n$) se debe a su difusión en la región P.
   - $J_n = q D_n \frac{dn_p(x)}{dx}$.

Donde:
- $q$ es la carga del electrón.
- $D_p$ y $D_n$ son los coeficientes de difusión de huecos y electrones respectivamente.

### Corriente Total
La corriente total $I$ en la juntura PN en polarización directa es la suma de las corrientes de difusión de huecos y electrones:
$$I = I_n + I_p$$
$$I = q A [ D_p \frac{p_{n0}}{L_p} ( e^{V/V_T} - 1 ) + D_n \frac{n_{p0}}{L_n} ( e^{V/V_T} - 1 )$$

Donde:
- $A$ es el área de la sección transversal de la juntura.


# Polarizacion inversa

### Perfiles de Concentración en la Polarización Inversa
En polarización inversa, los perfiles de concentración de portadores son:
- En la región N: $p_n(x) \approx 0$
- En la región P: $n_p(x) \approx 0$
Los portadores minoritarios tienen concentraciones muy bajas debido a la alta barrera de potencial.
![[Pasted image 20240517113521.png]]
### Ancho de la Zona de Depleción
El ancho de la zona de depleción $W$ se incrementa con el voltaje inverso:
$$W = \sqrt{\frac{2 \epsilon (V_0 + V)}{q} ( \frac{N_A + N_D}{N_A N_D} ) }$$
Donde $\epsilon$ es la permitividad del material semiconductor, $V_0$ es el potencial de barrera en equilibrio y $V$ es el voltaje aplicado inverso.
![[Pasted image 20240517113609.png]]


# Caracteristicas Electronica de la juntura

## Característica I-V
En polarización inversa, el voltaje aplicado incrementa la barrera de potencial, reduciendo la corriente a valores muy bajos, prácticamente constantes. La característica I-V en polarización inversa es:
$$I=I_S​(e^{\frac{V}{nV_T}}​−1)$$

Donde:

- 𝐼 es la corriente total.
- $𝐼_𝑆$​ es la corriente de saturación inversa.
- 𝑉 es el voltaje aplicado.
- 𝑛 es el factor de idealidad.
- $V_T$​ es el voltaje térmico

![[Pasted image 20240517113253.png]]
- $V_{Y}$ Tension umbral
- $I_S$ Corriente de saturacion inversa
### Tensión de Umbral
La tensión de umbral (o tensión de ruptura) es el voltaje inverso a partir del cual la corriente empieza a aumentar rápidamente debido a la ruptura del diodo. Esta tensión depende de las características del material y de la fabricación del diodo.

### Corriente de Saturación Inversa
La corriente de saturación inversa $I_S$ es la corriente que fluye a través de la juntura cuando está polarizada inversamente, y es debida a la generación térmica de portadores minoritarios:
$$I_S = q A ( D_p \frac{n_i^2}{N_D L_p} + D_n \frac{n_i^2}{N_A L_n} )$$

### Resistencia Dinámica
La resistencia dinámica en polarización inversa se define como:
$$r_d = ( \frac{dV}{dI} )_{\text{polarización inversa}} \approx \frac{kT}{q I_S}$$
Para $V \gg kT/q$, la resistencia dinámica es muy alta debido a la pequeña corriente de saturación inversa.

### Ruptura Inversa
![[Pasted image 20240517114102.png]]
La ruptura inversa ocurre cuando el voltaje inverso aplicado es suficientemente alto para causar un aumento abrupto de la corriente. Hay dos mecanismos principales:
1. **Ruptura por Avalancha:**
   - Ocurre cuando los portadores ganan suficiente energía del campo eléctrico para ionizar átomos al chocar con ellos, creando más electrones y huecos y llevando a una reacción en cadena.
   
2. **Ruptura Zener:**
   - Ocurre en diodos con una zona de depleción muy estrecha y altamente dopada. El fuerte campo eléctrico permite la ruptura del enlace covalente de los átomos, generando pares electrón-hueco.

3. *Ruptura por Perforación:* 
 - Ocurre en junturas cortas (Wny Wpson menores que Lpy Ln) Este fenómeno sucede cuando la zona de depleción se agranda hasta tocar los contactos metálicos. En esas condiciones el comportamiento de la juntura es prácticamente un cortocircuito.
## Funciones de Densidad de Carga, Campo Eléctrico y Potencial de Juntura
![[Pasted image 20240517113652.png]]
1. **Densidad de Carga ($\rho(x)$):**
   - En la región P: $\rho(x) = -q N_A$
   - En la región N: $\rho(x) = q N_D$

2. **Campo Eléctrico ($E(x)$):**
   - La máxima intensidad del campo eléctrico se encuentra en la frontera entre las regiones P y N.
   - $E(x) = -\frac{dV(x)}{dx}$
   - En polarización inversa, el campo eléctrico es mayor debido al incremento del ancho de la zona de depleción.

3. **Potencial de Juntura ($V(x)$):**
   - Se incrementa con la polarización inversa, incrementando la barrera potencial.
   - $V(x) = \int_0^x E(x') dx'$

### Modificación de Estas Funciones con la Polarización
![[Pasted image 20240517113720.png]]

#### Valores de Límites de Zona de Depleción
Los límites de la zona de depleción se extienden hacia ambas regiones cuando se aplica una polarización inversa:
- En la región P: $-x_p$ donde $x_p = \sqrt{\frac{2 \epsilon N_D (V_0 + V)}{q N_A (N_A + N_D)}}$
- En la región N: $x_n$ donde $x_n = \sqrt{\frac{2 \epsilon N_A (V_0 + V)}{q N_D (N_A + N_D)}}$

#### Capacidad de Juntura
- Dado que existe una carga Qj dependiente de la tensión asociada a la a zona de depleción
- Esto produce un efecto capacitivo
- Se puede considerar como un capacitor de placas paralelas que están separadas una distancia Xp+ Xn que llamamos Xm
La capacidad de la juntura $C$ en polarización inversa se comporta como una capacidad de barrera:
$$C = \frac{\epsilon A}{W}=\frac{C_{j0}}{\sqrt{(1-\frac{V_D}{V_{j0}})}}$$
Con $W$ aumentado por la polarización inversa, la capacidad disminuye.





