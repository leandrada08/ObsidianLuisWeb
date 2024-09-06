
## Corriente Limitada por Carga Espacial (SCLC)

La corriente limitada por carga espacial es un fenómeno que ocurre en materiales aislantes o semiconductores de baja conductividad cuando se inyectan portadores de carga desde los electrodos y se forman regiones de carga espacial en el material. Este fenómeno es una desviación de la Ley de Ohm y se estudia en el contexto de la conducción en tubos de vacío y aislantes.
### Acumulación de Carga Espacial

La acumulación de carga espacial ocurre cuando los portadores de carga (electrones o huecos) se acumulan en una región del material, creando una densidad de carga que afecta el campo eléctrico interno del material.

#### ¿Cómo ocurre la acumulación de carga espacial?

1. **Inyección de Portadores**:
   - Cuando se aplica un voltaje entre dos electrodos (cátodo y ánodo), los portadores de carga (electrones en el caso de materiales tipo $n$) son inyectados desde el cátodo hacia el material.
   - En un aislante o semiconductor de baja conductividad, estos portadores tienen una movilidad limitada.

2. **Movimiento de Portadores**:
   - Los electrones inyectados se mueven bajo la influencia del campo eléctrico aplicado.
   - Sin embargo, en un aislante, la movilidad de los portadores es muy baja y los electrones tienden a acumularse cerca del cátodo.

3. **Formación de una Región de Carga Espacial**:
   - La acumulación de estos electrones crea una región de carga negativa en el material.
   - Esta región de carga espacial modifica el campo eléctrico interno del material.

#### ¿Por qué es relevante en un aislante?

En un aislante, la corriente eléctrica no sigue la Ley de Ohm (donde la corriente es proporcional al voltaje aplicado). En su lugar, la corriente está limitada por la capacidad del material para transportar los portadores inyectados. La SCLC se convierte en el mecanismo dominante para el transporte de carga debido a:

- **Baja Densidad de Portadores Intrínsecos**: En un aislante, la densidad de portadores libres (electrones y huecos) es extremadamente baja en equilibrio térmico.
- **Inyección de Portadores Externos**: La corriente depende principalmente de los portadores inyectados desde los electrodos.
- **Formación de Campo Eléctrico Interno**: La carga espacial acumulada crea un campo eléctrico que afecta el movimiento adicional de portadores.



### Corriente Limitada por Carga Espacial (SCLC) en un Aislante

#### Formación de la Región de Carga Espacial

- **Inicialmente, sin carga inyectada**: En un aislante puro, no hay portadores libres. La corriente es cero porque no hay electrones o huecos que puedan moverse a través del material.
- **Aplicación de un potencial**: Cuando se aplica un potencial entre el cátodo y el ánodo, los electrones son inyectados desde el cátodo al aislante.
- **Acumulación de carga**: Debido a la baja movilidad en el aislante, los electrones inyectados no pueden moverse rápidamente a través del material y se acumulan cerca del cátodo, formando una región de carga espacial.

#### 2. Efecto de la Región de Carga Espacial en el Campo Eléctrico Interno

- **Campo Eléctrico Inicial**: Sin carga espacial, el campo eléctrico en el aislante es uniforme y determinado solo por el voltaje aplicado y la distancia entre los electrodos.
- **Campo Modificado**: La acumulación de carga espacial cerca del cátodo crea un campo eléctrico adicional dentro del material. Este campo no es uniforme y es más fuerte cerca del cátodo donde se acumula la carga.

#### 3. Impacto en la Corriente

- **Modificación del Potencial**: La región de carga espacial crea una barrera de potencial que los nuevos electrones inyectados deben superar.
- **Corriente Inicial**: Al principio, la corriente es baja porque los electrones inyectados tienen que superar esta barrera adicional.
- **Corriente Limitada por Carga Espacial**: Una vez que se inyectan suficientes electrones y se establece un campo eléctrico interno significativo, la corriente aumenta. Sin embargo, esta corriente está limitada por la densidad de carga espacial y la movilidad de los portadores.

### Modelo Ideal del Aislante
   - En un aislante perfecto, sin trampas y con una concentración de portadores libres despreciable en equilibrio, todos los portadores inyectados permanecen libres en la banda de conducción.
   - La densidad de corriente ($J$) se puede expresar como:
     $$
     J = \rho v=\frac{Q}{t}
     $$
     donde $\rho$ es la concentración de carga libre inyectada y $v$ es la velocidad de deriva media de los electrones libres.

- **Tiempo de Tránsito y Velocidad de Deriva**: El tiempo de tránsito ($t$) de los electrones entre el cátodo y el ánodo se relaciona con la distancia ($L$) entre los electrodos y la velocidad de deriva:$$
     t = \frac{L}{v}=\frac{L^2}{\mu V}
     $$
- Q es la total inicial por unidad de superficie entre catodo y anodo $$Q\approx C_0V=\frac{\epsilon_{is}\epsilon_0}{L}V$$

3. **Característica Corriente-Tensión**:
   - La relación corriente-tensión se puede determinar a partir de la densidad de corriente y la concentración de carga:
     $$
     J = \frac{\epsilon \epsilon_0 \mu V^2}{L^3}
     $$
     donde $\epsilon$ es la permitividad del material, $\epsilon_0$ es la permitividad del vacío, $\mu$ es la movilidad de los portadores, $V$ es la tensión aplicada y $L$ es la distancia entre los electrodos.
### Aislante con portadores libres

4. **Ley de Langmuir-Child**:
   - En un tubo de vacío, los electrones inyectados se mueven sin colisiones y su velocidad de deriva está ligada a la diferencia de potencial entre las placas:$$v=(\frac{qV}{m})^{1/2}$$
     $$
     J = \frac{9}{8} \epsilon_0 \mu \frac{V^2}{L^3}
     $$
### Aislante con trampas

Las trampas son defectos en el material que pueden capturar y retener portadores de carga (electrones o huecos), afectando el transporte de carga. Las trampas pueden ser:

- **Trampas poco profundas**: Capturan y liberan electrones fácilmente. Cerca del nivel de fermi
- **Trampas profundas**: Retienen los electrones durante más tiempo y requieren más energía para liberarlos. Mucho menores al nivel de fermi

**Efecto de las Trampas en la SCLC:**

- **Reducción de la Densidad de Portadores Libres**: Las trampas capturan portadores libres, reduciendo la cantidad de electrones disponibles para la conducción.
- **Modificación del Campo Eléctrico Interno**: La captura y liberación de portadores por las trampas cambia la distribución de carga espacial y, por lo tanto, el campo eléctrico interno.
- **Movilidad Efectiva Reducida**: La presencia de trampas reduce la movilidad efectiva de los portadores porque los electrones atrapados no contribuyen al transporte de corriente:
  $$
  \mu_{\text{eff}} = \mu \Theta
  $$
  donde $\Theta$ es el factor de ocupación de las trampas.

**Region de Carga Espacial con Trampas:**

- **Región de Trampas Llena**: Al aplicar un potencial, las trampas cerca del cátodo se llenan primero. Una vez que las trampas están llenas, los electrones adicionales contribuyen a la corriente.
- **Corriente Dependiente de las Trampas**: La corriente en la región de trampas llenas será diferente a la corriente en la región sin trampas. En general, la presencia de trampas hace que la relación corriente-tensión sea más compleja y puede introducir no linealidades adicionales.

![[Pasted image 20240704052610.png]]
![[Pasted image 20240704052357.png]]





## Graficas

### Imagen 1
![[Pasted image 20240704050518.png]]
#### Izquierda
El diagrama de la izquierda muestra el alineamiento de bandas de energía en una interfaz metal-aislante:
- **$E_F$**: Nivel de Fermi en el metal.
- **$E_c$**: Banda de conducción del aislante.
Este diagrama ilustra cómo los niveles de energía cambian en la interfaz entre el metal y el aislante. En el metal, los electrones tienen un nivel de energía definido por el nivel de Fermi ($E_F$). Al pasar al aislante, se forma una barrera de potencial debido a la diferencia en las bandas de energía. Los electrones deben superar esta barrera para entrar en la banda de conducción del aislante.

#### Derecha
El diagrama de la derecha muestra la formación de una región de carga espacial en un semiconductor tipo $n$:

- **$E_c$**: Banda de conducción.
- **$E_F$**: Nivel de Fermi.
- **$E_v$**: Banda de valencia.
- **$n^+$**: Región altamente dopada tipo $n$.
- **$n$**: Región ligeramente dopada tipo $n$.

Este diagrama ilustra cómo los electrones inyectados desde la región $n^+$ crean una acumulación de carga en la región $n$, afectando el perfil de potencial y creando una región de carga espacial. La acumulación de electrones en la región $n$ causa una modificación en la posición de la banda de conducción y el nivel de Fermi.

### Imagen 2
![[Pasted image 20240704050532.png]]
Este diagrama muestra un dispositivo con un cátodo y un ánodo separados por un aislante:

El diagrama muestra cómo los electrones deben superar una barrera de potencial para moverse desde el cátodo, a través del aislante, hasta el ánodo. La forma de la barrera de potencial refleja la energía que los electrones deben superar para atravesar el aislante y llegar al ánodo. Este es un ejemplo típico de cómo se forma la corriente limitada por carga espacial en un dispositivo de este tipo.

