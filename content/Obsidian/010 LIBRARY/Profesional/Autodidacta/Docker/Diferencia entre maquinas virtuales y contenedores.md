# **Máquinas Virtuales (VM):**

1. **Aislamiento:** Las VMs proporcionan un aislamiento completo, ya que ejecutan un sistema operativo completo independiente del host.
2. **Recurso Intensivo:** Las VMs pueden consumir más recursos, porque cada una tiene su propio sistema operativo y una cantidad significativa de recursos dedicados.
3. **Arranque Más Lento:** El arranque de una VM es más lento, puesto que implica iniciar un sistema operativo completo.
4. **Hypervisor:** Las VMs se ejecutan en un hipervisor, que gestiona y asigna recursos para cada máquina virtual.

# **Contenedores:**

1. **Aislamiento Ligero:** Los contenedores comparten el mismo kernel del sistema operativo del host, lo que proporciona un aislamiento más ligero.
2. **Eficiencia de Recursos:** Los contenedores son más eficientes en términos de recursos, ya que comparten el mismo sistema operativo y solo incluyen las bibliotecas y dependencias necesarias.
3. **Arranque Rápido:** Los contenedores tienen un arranque rápido, por el hecho de que no requieren iniciar un sistema operativo completo.
4. **Docker, Containerd, etc.:** Docker es una de las tecnologías de contenedores más populares, y otras implementaciones incluyen containerd, rkt, etc.

# **Servicios:**

1. **Abstracción de Recursos:** Los servicios proporcionan una capa de abstracción adicional, encapsulando funcionalidades específicas y ocultando detalles de implementación.
2. **Escalabilidad Horizontal:** Los servicios suelen diseñarse para escalar horizontalmente, agregando instancias según sea necesario.
3. **Arquitectura Distribuida:** Los servicios pueden formar parte de una arquitectura distribuida, donde se comunican entre sí para proporcionar funcionalidades complejas.
4. **Ejemplos:** Pueden ser servicios web, microservicios, funciones sin servidor (serverless), etc



# Virtualización



Permite atacar en simultáneo los tres problemas del desarrollo de software profesional.
Problemas de la virtualizacion
- PESO: En el orden de los GBs. Repiten archivos en común. Inicio lento.
- COSTO DE ADMINISTRACION: Necesita mantenimiento igual que cualquier otra computadora.
- MULTIPLES DE FORMATO: VDI, VMDK, VHD, raw, etc

Containerización
- El empleo de contenedores para construir y desplegar software.
- Flexibles
- Livianos
- Portables
- Bajo acoplamiento
- Escalables
- Seguros

Virtualizacion vs Containerización
- Virtualización: A diferencia de un contenedor, las máquinas virtuales ejecutan un sistema operativo completo, incluido su propio kernel.
- Containerización: Un contenedor es un silo aislado y ligero para ejecutar una aplicación en el sistema operativo host. Los contenedores se basan en el kernel del sistema operativo host (que puede considerarse la fontanería del sistema operativo), y solo puede contener aplicaciones y algunas API ligeras del sistema operativo y servicios que se ejecutan en modo de usuario.