##### Modelos comunes de distorsión
  - **Distorsión radial**: Aumenta con la distancia al centro de la imagen (debido a la simetría radial de la lente).
    - **Centro de distorsión**: $(u_c, v_c)$, donde la distorsión es nula.
    - **Componentes**:
      - **Radial**: A lo largo de la línea que une $(u_d, v_d)$ y $(u_c, v_c)$.
      - **Tangencial**: Ortogonal a la dirección radial.

![[Pasted image 20240530212006.png]]

- **Ecuaciones del modelo**:
  - **Distorsión radial y tangencial** aproximadas con funciones polinomiales del radio $r$.
![[Pasted image 20240530212136.png]]

 Se define el radio $r$ como $r = \sqrt{(u_d - u_c)^2 + (v_d - v_c)^2}$.

- **Parámetros del modelo**: Incluyen $(u_c, v_c)$, los coeficientes de distorsión radial $k_1, k_2, \ldots$, y los coeficientes de distorsión tangencial $b_1, b_2, \ldots$.



##### Semplificaciones del modelo de distorsión
  - **Modelo con un solo coeficiente radial**:
    $$
    \begin{cases}
    u_d = u + k_1 r^2 (u - u_c) \\
    v_d = v + k_1 r^2 (v - v_c)
    \end{cases}
    $$
  - **Modelo con el centro de distorsión fijado en el punto principal**:
    $$
    \begin{cases}
    u_d = u + k_1 r^2 (u - u_0) \\
    v_d = v + k_1 r^2 (v - v_0)
    \end{cases}
    $$
    - **Número de parámetros**: Solo $k_1$.

##### Tipos de distorsión
![[Pasted image 20240530212527.png]]
  - **Distorsión de barril** ("barrel distortion"): $k_1 > 0$.
  - **Distorsión de cojín** ("pincushion distortion"): $k_1 < 0$.
  
- **Parámetros del modelo de cámara**:
  - **Modelo pin-hole lineal**: 11 parámetros ($f_k, f_v, u_0, v_0, \psi, \phi, \theta, t_x, t_y, t_z$).
  - **Modelo de distorsión**: Generalmente, se añaden 3 parámetros ($u_c, v_c, k_1$) o solo 1 parámetro ($k_1$), dependiendo del nivel de precisión requerido y la aplicación específica.