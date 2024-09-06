
# **Bases de Bus**

## **¿Qué es un BUS?**

- Un **bus** es un conjunto de _cables_ utilizado para conectar múltiples dispositivos.
- Es una herramienta sistemática de la arquitectura para construir sistemas complejos.
- Están definidos por distintas capas:
    - Protocolo de transacciones.
    - Especificaciones de señales y tiempo.
    - Paquete de cables.

## **Características Esenciales de los Buses**

1. **Basados en Protocolos Estándar**:
    - Aseguran:
        - _Compatibilidad_: Funcionamiento sin inconvenientes con dispositivos de terceros.
        - _Efectividad_: Correcta realización de transacciones.
        - _Eficiencia_: Productividad (ancho de banda) o latencia (tiempo de respuesta).
2. **Organización Jerárquica**:
    - Posibilidad de conectar diversos estándares mediante _bridges_.
    - Mejora la eficiencia: buses más rápidos para dispositivos más rápidos.
    - Permite transferencias simultáneas.
    - Simplifica la lógica de dispositivos lentos.
3. **Tipos de Señales**:
    - Direcciones, datos y control.
4. **Arbitraje**:
    - Manejo de contenciones (cuando varios dispositivos intentan usar el bus).
    - Esquemas como Master/Slave.
    - Puede ser centralizado o distribuido con diferentes prioridades.
5. **Métricas Utilizadas**:
    - Ancho de banda y latencia.
    - Frecuencia (menos común).
    - Tolerancia a fallos.
    - Eficiencia energética.



## Topologias

### **Topologías principales de buses**:

1. **Topologia en Red Troncal**
    
    - En esta topología, todos los dispositivos de la red están conectados a un solo cable o **red troncal**.
    - El cable principal actúa como la columna vertebral de toda la red.
    - Los datos enviados por una computadora se transmiten a lo largo de todo el cable troncal en ambas direcciones desde la computadora emisora.
    - Se utiliza en redes Ethernet y es valorada por su simplicidad y menor costo de implementación
2. **Topología en Estrella**:
    
    - En esta topología, todos los dispositivos de la red están conectados a un dispositivo central, como un **conmutador** o un **router**.
    - El dispositivo central conecta indirectamente todos los ordenadores de la red.
    - Cada dispositivo se comunica directamente con el dispositivo central.
    - Es común en redes LAN y proporciona una mayor facilidad de administración.
3. **Topología en Anillo**:
    
    - En esta topología, los dispositivos están conectados en un círculo cerrado.
    - Cada dispositivo se comunica con los dispositivos adyacentes en el anillo.
    - La señal se propaga en una dirección continua a través del anillo.
    - Menos común en redes de computadoras, pero se utiliza en algunas redes de área local (LAN) y sistemas de control industrial.
4. **Topología en Malla**:
    
    - En esta topología, cada dispositivo está conectado directamente a todos los demás dispositivos.
    - Proporciona redundancia y alta confiabilidad.
    - Costosa de implementar debido a la gran cantidad de conexiones físicas.


### BUS para Computadoras
#### PCI EXPRES
**PCI Express** es una **interfaz serial de alta velocidad** utilizada para conectar dispositivos a la placa base de una computadora.
    - Es comúnmente utilizado para tarjetas gráficas, tarjetas de sonido, adaptadores de unidades de disco duro, SSDs, conexiones de hardware Wi-Fi y Ethernet.
- **Características Esenciales**:
    - **Protocolos Estándar**:
        - Aseguran **compatibilidad**, **efectividad** y **eficiencia** en las transacciones.
    - **Organización Jerárquica**:
        - Permite conectar diversos estándares mediante _bridges_.
        - Facilita transferencias simultáneas y simplifica la lógica de dispositivos lentos.
    - **Tipos de Señales**:
        - Incluye señales de direcciones, datos y control.
    - **Arbitraje**:
        - Maneja las contenciones (cuando varios dispositivos intentan usar el bus).
        - Puede ser centralizado o distribuido.

### BUS per ATE

#### STAR

Ogni componente, usualmente indicato come "periferica", é collegato da una linea autonoma alla unitá principale, denominata "controllore": ogni componente ha quindi un proprio bus indipendente da quello delle altre unitá
- Solitamente le linee di connessione sono previste per un flusso unidirezionale di informazioni e questo contribuisce ad aumentare la velocitá di trasmissione che costituisce la prestazione principale di questa struttura
- La struttura di tipo star garantisce elevate prestazioni al sistema in termini di velocitá, ma il costo é rilevante perche sono necessari due circuiti di interfaccia per ogni linea di collegamento(un'interfaccia per la periferica ed una per il controllore), questo fare che il numero di periferiche collegabili será limitato.
- In pratica questa struttura viene adottata solamente quando si ricercano le piú alte velocitá di trasmissione.

![[Pasted image 20231226160644.png]]

#### Daisy-chain
La struttura daisy-chain prevede l'uso di linee di connessione unidizerionali fra un componente e l'altro: la struttura si completa quando tutte le periferiche sono collegate da un bus che asuume la forma di un anello. Per la particolare struttura di questo bus ogni periferica collegata fra il trasmettitore del messaggio e la periferica di destinazione riceve e ritrasmette le informazioni sulla linea daisy-chain fino a quando il messagio non ha raggiunto il ricevitore previsto.
- Vantaggi
	- Numero ilimiti di perifeche collegabili
	- Costo limitato del sistema
- Problema
	- Sensibilita del sistema al mancato funzionamento di un componente
	- Lento

![[Pasted image 20231226160629.png]]

#### Party-line
Questa ha ottenuto la maggiori diffusione. In questo caso tutte le periferiche si trovano collegate "in parallelo" su di un unico bus costituito da linee di tipo bidirezionale. Le comunicazioni sono "broadcoat", dove tutte le periferiche acquisiscono i messaggi ricevuto e "point-to-point" dove solamente una periferica, quella di destinazione, recepisce il messaggio.
- Conferisce al sistema una buona velocita
- La circuiteria di interfaccia delle periferiche é alquanto complessa
	- Il numero massimo di periferiche utilizzabili é limitato
	- ![[Pasted image 20231226160626.png]]