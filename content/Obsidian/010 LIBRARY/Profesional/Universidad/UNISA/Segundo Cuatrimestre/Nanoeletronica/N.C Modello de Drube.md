

## Modello de Drube

El **Modelo de Drude** es una teoría clásica que describe el comportamiento de los portadores de carga (electrones y huecos) en materiales conductores y semiconductores. Este modelo considera a los electrones como partículas clásicas que se mueven libremente entre colisiones con iones de la red cristalina o impurezas.
### 1. Energía Cinética Media

- **Portadores de Carga:** Electrones y huecos generados térmicamente o por irradiación.
- **Energía Cinética Media:**
  $$
  E_{\text{cin}} = \frac{3}{2} kT
  $$
  donde $k$ es la constante de Boltzmann y $T$ es la temperatura en Kelvin.
- **Velocidad Térmica Promedio:**
  $$
  v_{\text{th}} \approx 10^7 \, \text{cm/s}
  $$
- **En Equilibrio:** Desplazamiento y velocidad media son nulos:
  $$
  \mathbf{J} = nq \mathbf{v}_{\text{th}} = 0
  $$

### 2. Movimiento bajo Campo Eléctrico

- **Campo Eléctrico Externo:** 
  - **Electrones:** Movimiento en dirección opuesta al campo.
  - **Huecos:** Movimiento en la misma dirección del campo.

### 3. Colisiones y Camino Libre Medio

- **Centros de Colisión:** Impurezas y vibraciones reticulares.
- **Camino Libre Medio ($l$):**
  $$
  l \approx 10^{-5} \, \text{cm}
  $$
- **Tiempo Medio entre Colisiones ($\tau$):**
  $$
  \tau \approx 10^{-12} \, \text{s}
  $$

### 4. Ecuación del Movimiento

- **Fuerza sobre el Electrón:**
  $$
  \mathbf{F} = -q \mathbf{E}
  $$
- **Segunda Ley de Newton:**
  $$
  m \frac{d\mathbf{v}}{dt} = -q \mathbf{E}
  $$
- **Velocidad de Deriva Promedio:**
  $$
  \langle \mathbf{v} \rangle = \left( -\frac{q \tau}{m} \right) \mathbf{E}
  $$

### 5. Velocidad de Deriva

- **Difusión Isotrópica:** Media de $\mathbf{v}_{\text{th}}$ es nula.
- **Electrones:**
  $$
  \mathbf{v}_n = -\frac{q \tau_n}{m_n} \mathbf{E} = -\mu_n \mathbf{E}
  $$
  donde $\mu_n$ es la movilidad de los electrones.
- **Huecos:**
  $$
  \mathbf{v}_p = \frac{q \tau_p}{m_p} \mathbf{E} = \mu_p \mathbf{E}
  $$
  donde $\mu_p$ es la movilidad de los huecos.

### 6. Conductividad y Ley de Ohm

- **Densidad de Corriente para Electrones:**
  $$
  \mathbf{J}_n = -nq\mu_n \mathbf{E}
  $$
- **Densidad de Corriente para Huecos:**
  $$
  \mathbf{J}_p = pq\mu_p \mathbf{E}
  $$
- **Densidad de Corriente Total:**
  $$
  \mathbf{J} = \mathbf{J}_n + \mathbf{J}_p = \sigma \mathbf{E}
  $$
- **Conductividad ($\sigma$):**
  $$
  \sigma = q (n \mu_n + p \mu_p)
  $$
- **Resistividad ($\rho$):**
  $$
  \rho = \frac{1}{\sigma}
  $$


