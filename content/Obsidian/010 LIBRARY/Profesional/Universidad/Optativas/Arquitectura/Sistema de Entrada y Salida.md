## Esquema basico del Sistema de I/O
![[Pasted image 20230531082951.png|500]]
Es muy complejo este sistema ya que se le pueden conectar muchisimo dispositivos, con caracteristicas y comportamiento muy diferentes, conectados a uno o mas buses.

## Responsabilidades del SO
El SO es la interface entre el hardware de I/O y el programa de usuario que requiere una operacion de I/O
- Sus responsabilidades surgen de 3 caracteristicas:
	- El sistema de I/O es compartido por multiples programas usando el procesador(*Multiprogramacion*)
	- El sistema de I/O usa generalmente *interrupciones* para comunicar informacion de la operacion de I/O
	- El control de bajo nivel de los dispositivos de I/O es complejo
- El SO debera proveer:
	- *Proteccion* de recursos de I/O compartido
	- *Abstracion* en el uso de dispositivos de I/O
	- *Manejo de interrucion* generadas por los dispositivos de I/O
	- *Acceso equitativo* de los recursos de I/O compartidos
	- *Organizacion* de los accesos a los recursos de I/O compartidos

### Driver de dispositivos
El SO provee todas las caracteristicas anteriores incorporando porciones de software que sirven de interfaz con cada dispositivvo especifico. Estos pedazos de software son conocidos como "drivers".
El driver se encarga de copiar datos desde el espacio de direcciones del programa de usuario al espacio de direcciones del SO.

### Requisitos de comunicacion
El SO debe ser capaz de comunicarse con el sistema de I/O y al mismo tiempo evitar que los programas de usuarios se comuniquen directamente con el sistema de I/O
Tres tipos de comunicacion:
- SO ->sistema I/O:ser capaz de enviar comandos
- Dispositivo de I/O ->SO: Notificar que se a completado una operacion
- Dispositivo I/O -> Memoria principal: transferir los datos

#### 1: SO --> I/O
*I/O mapeada en memoria*
- Se asignan area del espacio de memoria a dispositivos de I/O
- Se usa este metodo porque permite usar el mismo mecanismo de proteccion que ya se implemento para Memoria Virtual
#### 2:I/O --> SO
*Polling*
-  Cada dispositivo de I/O se asocia a un registro de estado (mapeado en memoria o
-  El dispositivo pone información en este registro.
-  El SO periódicamente revisa este registro para ver si hay datos listos, o si ocurrió un error.
-  Si los datos están listos, leerlos y continuar.
-  Si no, permanecer en el lazo e intentar nuevamente más
*Interrupciones*
- El procesador esta ocupado en sus asuntos hasta que un dispositivo esta listo y requiere su atencino mediante una interrupcion.
- El procesador guarda el estado y salta a la rutina de servicio de interrupcion correspondiente.
- Al temrinar, continua con lo que estaba haciendo

*Cual se usa:*
- Eventos frecuentes y regulares, con polling
- En otro caso, interrupciones.

#### 3:I/O --> Memoria
Se usa un *Controlador DMA* para delegar esta tarea
- Externo al procesador, toma posesion del bus de memoria y genera todas las señales correspondientes para hacer la transferencia
- Transfiere datos de a bloques, sin intervencion del procesador.
- El procesador envia la direccion incial del bloque a transferir, el dispositivo en cuestion, la longitud del bloque, y un comando para que empiece
- Al temrinar, genera un interrupcion al procesador
Comunmente al controlador DMA se le agrea funciones adiciones y se convierte en un *IOP(input Output Processor)*
- El procesador emite una instruccion al IOP donde le indica cual es el dispositivo objetivo, y cual es la direccion donde estan el resto de los comandos
- El IOP busca sus propios comandos y realiza todas las transferencias a memorias necesarias, siempre en segundo plano
- Al terminar todas las transferencias, interrumpe al procesador principal
Este modelo es bastante usado, por ejemplo en la placa de video1

## Consideraciones de Diseño de I/O
Ademas de la *performance*, hay que tener en cuenta la *escabilidad*, *toleracia a fallos*(si falla un dispositivo, fallan todos), confiabilidad y disponibilidad.
### Performance
Depende de multiples factores, por lo que no es facil de medir. Por lo que usamos brerckmans dependendiendo las especificaciones y usos de las computadoras
- Bases de Datos y transacciones: www.tpc.org
- Sistemas web: SPECWeb
- Supercomputadoras : ExaFLOPs
Metricas comunes:
- Productividad: Ancho de banda
- Latencia: Tiempo de respuesta
![[Costo, performance y consumo de energia#Performance en computadoras. Latencia y productividad#Definiciones]]
Para la productividad lo mejor es que la cola nunca este vacia, para que nunca se detenga y para la latencia la cola deberia estar vacio, asi el servidor puede responder inmediatamente. Por lo que hay un compromiso, se intenta que ningun recursos compartido este ocupado mas del 70-80% del tiempo
![[Pasted image 20230531094549.png]]
La productividad de I/O puede mejorarse sin sacrificazr latencia

### Confiabilidad y Disponibilidad
*Confiabilidad:* Tiempo hasta que se produce una caida del serivicio.
- MTTF(Mean Time To Failure), medida en años
*Disponibilidad:* Porcentaje de tiempo que el servicio esta disponible.
- MTTR(Mean Time To Repair), medida en horas.
- D=MTTF/(MTTF+MTTR)

- La disponibilidad se mejora agregando hardware

# Dispositivos I/O
## Discos Magnéticos
En general, son el ultimo nivel de la jerarquia de memoria
- Almacenamiento no volatil de larga duracion
- Grandes, baratos y lentos
### Detalles constructivos
Placas rotarias rigidas recubiertas de una superficie magnetica, los discos mas grandes actuales tienen 10 placas, cada placa puede almacenar datos en ambos lados
- Un cabezal para lectura/escritura por superficie
- Un brazo mecanico que mueve todos los cabezales juntos, radialmente
### Distribucion de los datos en un disco
![[Pasted image 20230602083746.png]]
- *Pista:* Cada anillo concentrico de la figura
- *Sectores:* Division minima de las pistas, en 2011 se estandarizo en 4k
- Las pistas de todas las superficies conforman un cilindro

### Operacion de lectura/escritura
- *Seek time:* Tiempo de posicionamiento de los cabezales (3-4 ms)
- *Latencia rotacional:* Tiempo de espera que el disco rote hasta el dato(aprox 6ms)
- *Tiempo de transferencia:* Tiempo de escritura o lectura(40us)
- *Retardo de controlador:* entre 100 y 200 us
$$AMAT(Disco)=seekTime+Latencia+Transferencia+RetardoControlador$$
Para bajar el tiempo, se pone varios discos en paralelo y para aumentar la confiabilidad se copia los datos en varios discos. Esto se llama *RAID*


## Memoria FLASH
Celdas de memoria agrupadas en paginas, a su vez agrupadas en bloques de hasta 256 paginas. Se escribe de a paginas completar y se borra de a bloque completo. La escritura de una pagina demora aprox. 200us
- Flash, SSD, Microcontroladores,etc.
- Impulsada principalmente por la economia de escala.
### Funcionamiento
Tiene una compuerta flotante que no esta conectada, para escribir un nuevo valor, se aplica una tension alta en esta compeurta flotante
- Permite almacenar electrones durante mucho tiempo
- La aplicacion sucesivas de estas altas tensiones termina deteriorando la compuerta
- Por lo tanto, la cantidad de escritura que se realizan en una memoria de esta tipo esta limitada

## SSD vs Magneticos
*Ventajas de los SSD:* 
- No tiene componenetes mecanicas
	- Enorme reduccion en AMAT
	- Mejor resistencia a golpes e impactos
- Menor consumo de energia
- Menor tiempo de transferencia
	- Mas rapida en lectura, similar en escritura
*Desventajas de los SSD*
- Cantidad limitada de escritura
- Mayores latencia a medida que aumenta su capacidad
- Mas caros.

*Observaciones:*
Se supone que el precio por GB se igualaran en 2033.

### Conclusion
Los HDD no pueden competir en performance con los SSD pero si en otras metricas, generalmente relacionadas a la capacidad
- Los que si corren riesgo de dasaparecer son los HDD premiun
- Hay HDD de 20TB y se proyectan de 100TB para 2025
Nueva tecnologias para HDD en pleno desarrollo:
- Nuevos metodos de grabacion, para incrementar la densidad
- Aumentar la cantidad de platos de discos
La limitacion de la vida util de los SSD hace poco probable que desaparezcan los HDD

## Tendencias actuales
- Hay una brecha de performance entre *memoria e I/O*
	- Los ssd son 1000 veces mas lentos que la ram.
- Nuevas aplicaciones requieren nuevas capacidades de I/O: Machine Learning y computacion cientifica.
- **La evolucion de una tecnologia suele mejorar el ancho de banda, y solonuevas tecnologias mejoran la latencia.**
### Memorias RAM no Volatiles
![[Pasted image 20230602094558.png]]
Llamadas NVDIMM-N. Las primeras se conectan al bus PCle, las mas nuevas directamente al bus de memoria.
Rquiere nuevo modelos de programacion ya que casi toda la jerarquia de memorias vista es volatil.
### Intel Optane Memory

### CXL
Es un bus, introduce el concepto de "memory pooling", mediante el cual permite acceder a modulos de DRAM remontamente a traves de la red.
- Ampliaria a DDR, permitiendo aumentar notablemente la capacidad, sin aumentar tanto la latencia
- Permitiria manejar identicamente distintas tecnologias de memorias, como distintos DDR< LPDDR, HBM y NVM.

#### Jerarquia de memoria propuesta
![[Pasted image 20230602095515.png|500]]

### UltraRAM