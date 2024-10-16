
## Introduccion
- Las empresas alojan sus sistemas de ML en **centros de datos** con hardware especializado como **TPU** (Google) y **GPU** (NVIDIA), que proporcionan gran capacidad de cómputo. Sin embargo, estos grandes sistemas tienen desventajas en cuanto a interactividad y latencia.
  ![[Captura de pantalla 2024-10-09 a las 11.42.11 a. m..png]]

- Bigger is not always better
![[Captura de pantalla 2024-10-09 a las 11.44.09 a. m..png]]

- **Interactividad**: Poder ejecutar ML directamente en dispositivos como smartphones mejora la capacidad de respuesta y elimina la latencia asociada a los centros de datos.
- **Bajo consumo de energía**: Los centros de datos consumen grandes cantidades de energía, mientras que dispositivos pequeños, como smartphones, tienen un consumo energético mucho menor.
- **Latencia baja**: Procesar ML directamente en el dispositivo, como en un smartphone o un reloj inteligente, reduce el tiempo de espera en comparación con enviar los datos a la nube.



## Area de aplicacion de TinyML
TinyML está destinado a **impulsar la próxima generación de dispositivos inteligentes** en hogares y ubicaciones remotas, permitiendo monitoreo remoto en sectores industriales y ecológicos. Actualmente, se descarta el 99% de los datos de sensores, lo que ofrece una oportunidad para **analizar datos inexplorados** usando TinyML, proporcionando estadísticas inteligentes en dispositivos de bajo consumo.

#### Áreas de aplicación emergentes

1. **Mantenimiento predictivo industrial**
   - **TinyML** ya está mejorando la monitorización en el sector industrial, permitiendo un mantenimiento predictivo en dispositivos como turbinas eólicas.
   - Ejemplo: **Ping Services**, una startup australiana, ha desarrollado un dispositivo IoT que se adhiere magnéticamente a las turbinas eólicas, analizando datos en el borde para detectar problemas antes de que ocurran. Esto reduce tiempos de inactividad y mejora la calidad del servicio.

2. **Agricultura**
   - **Cassava**, un cultivo esencial para más de 500 millones de africanos, es atacado por diversas enfermedades. La app **Nuru**, desarrollada por el equipo de **PlantVillage**, utiliza ML en teléfonos móviles con **TensorFlow Lite** para ayudar a los agricultores a identificar enfermedades en tiempo real sin conexión a internet. 
   - La próxima generación de este sistema utilizará TinyML y sensores distribuidos para un **mejor seguimiento** en zonas remotas.

3. **Salud**
   - **Solar Scare Mosquito**: Un proyecto que utiliza pequeñas plataformas IoT para interrumpir el ciclo de reproducción de mosquitos, combatiendo la propagación de enfermedades como la malaria, dengue y Zika.
   - El sistema usa sensores de lluvia y acústicos para conservar batería, lo que le permite operar indefinidamente con energía solar. Estos dispositivos, asequibles y auto-suficientes, pueden ser desplegados ampliamente para **prevenir epidemias**.

4. **Conservación de la fauna**
   - **En tierra**: En la línea ferroviaria Siliguri-Jalapaiguri en India, un sistema basado en ML con sensores acústicos y térmicos alimentados por energía solar ha sido implementado para prevenir colisiones fatales con elefantes.
   - **En el mar**: Sistemas similares se están utilizando cerca de Seattle y Vancouver para prevenir colisiones con ballenas en vías marítimas, mejorando la **monitorización en tiempo real**.



## Habilitando TinyML a través de sistemas embebidos y ML

TinyML surge de la combinación de **sistemas embebidos** y **aprendizaje automático (ML)**, donde dispositivos pequeños pueden procesar y analizar datos de manera eficiente. 
![[Captura de pantalla 2024-10-09 a las 12.02.47 p. m..png|500]]
### Step for TinyMl
![[Captura de pantalla 2024-10-09 a las 12.03.57 p. m..png|600]]
- **Entrada**: Captura de datos, como señales de audio en el caso de "OK Google", a través de un **sensor acústico** (micrófono).
- **Procesamiento**: El ML procesa la señal para identificar el comando.
- **Salida**: Respuesta física, como encender una luz o dar una respuesta audible.

#### Entradas en sistemas TinyML
- Los dispositivos TinyML dependen de **sensores** para capturar datos:
  - **Sensores acústicos**: Captan señales de audio como en "OK Google".
  - **Sensores biométricos**: Monitorean parámetros como glucosa o señales cardíacas (ej. dispositivos ECG).
  - **Sensores de imagen**: Cámaras que pueden integrarse con microcontroladores para captura y procesamiento de visión.
  - **Otros sensores**: Sensores de movimiento, ambientales, entre otros.

#### Procesamiento en TinyML
- **Procesadores grandes** como GPU o TPU son usados tradicionalmente para ML, pero TinyML busca hacer este procesamiento en **procesadores pequeños** como microcontroladores (MCU). 
![[Captura de pantalla 2024-10-09 a las 12.06.40 p. m..png|500]]
![[Captura de pantalla 2024-10-09 a las 12.07.32 p. m..png|400]]
- Ejemplo de un MCU en una bola de golf

##### Ventajas de las MCU en TinyML
1. **Tamaño pequeño**: MCU como el Kinetis KL03 son tan pequeños que pueden estar integrados en cualquier dispositivo.
2. **Bajo consumo energético**: Los MCU pueden operar con menos de 1 mW, lo que les permite funcionar con baterías de tipo botón.
3. **Costo bajo**: Se proyecta que el costo de las MCU será inferior a $0.50 debido a su creciente demanda.
4. **Omnipresencia**: Los MCU ya están en todas partes y seguirán aumentando, siendo la base de los dispositivos TinyML.
![[Captura de pantalla 2024-10-09 a las 12.10.10 p. m..png|500]]
#### Salidas en sistemas TinyML
- Los dispositivos TinyML pueden generar dos tipos de salidas:
  - **Salidas físicas**: Como activar motores, luces o sonidos (ej. respuestas de "OK Google").
  - **Salidas digitales**: Mostrar información útil en pantallas basadas en el análisis de los datos de entrada.

#### Conclusión: El futuro de TinyML
- **MCU como componente fundamental**: Las MCU serán la base de los dispositivos TinyML debido a su tamaño, bajo consumo energético, costo y ubicuidad.
- **Aplicaciones emergentes**: A medida que la demanda de MCU crece, la combinación de estos procesadores con ML desbloqueará nuevas aplicaciones inteligentes y eficientes.
- **Próximo paso**: En los próximos videos se explorará cómo ejecutar modelos de ML en estos pequeños procesadores.


