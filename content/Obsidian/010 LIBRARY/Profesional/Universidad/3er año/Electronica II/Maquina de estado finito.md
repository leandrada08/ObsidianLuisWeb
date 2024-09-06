

## Introducción a las Máquinas de Estado Finito

Las máquinas de estado finito (FSM, por sus siglas en inglés) son dispositivos fundamentales en la electrónica digital que modelan sistemas secuenciales. Estas máquinas representan una parte clave en el diseño y control de sistemas digitales, ya que permiten definir el comportamiento de un sistema en función de su estado actual y las entradas presentes.

## Elementos Básicos de una Máquina de Estado

Las máquinas de estado finito constan de los siguientes elementos:

1. **Estados (States)**: Representan las condiciones o situaciones en las que se encuentra la máquina en un momento dado. Cada estado tiene un comportamiento específico asociado.

2. **Transiciones (Transitions)**: Definen las condiciones bajo las cuales la máquina cambia de un estado a otro. Las transiciones están controladas por entradas y el estado actual.

3. **Entradas (Inputs)**: Son las señales externas que afectan el comportamiento de la máquina.

4. **Salidas (Outputs)**: Representan la información que la máquina produce en función de su estado y las entradas.

## Tipos de Máquinas de Estado

Existen dos tipos principales de máquinas de estado:

1. **Máquinas de Estado de Moore**: En este tipo de FSM, las salidas dependen únicamente del estado actual. En otras palabras, la salida se determina solo por el estado en el que se encuentra la máquina.

2. **Máquinas de Estado de Mealy**: En este tipo de FSM, las salidas dependen del estado actual y de las entradas actuales. Por lo tanto, las salidas pueden cambiar en función tanto del estado como de las entradas.

## Diseño de Máquinas de Estado

El diseño de una máquina de estado finito implica los siguientes pasos:

1. **Identificación de Estados y Comportamiento**: Determinar los estados necesarios para el sistema y definir el comportamiento de cada estado en función de las entradas y las salidas.

2. **Creación de Diagrama de Estados**: Representar gráficamente los estados y las transiciones en un diagrama de estados. Esto ayuda a visualizar el funcionamiento de la máquina.

3. **Especificación de Transiciones y Salidas**: Detallar las condiciones bajo las cuales la máquina cambia de estado y las salidas asociadas a cada transición.

4. **Implementación**: Crear circuitos lógicos que implementen las transiciones y generen las salidas requeridas.

5. **Simulación y Verificación**: Utilizar herramientas de simulación para verificar el diseño y asegurarse de que la máquina funcione correctamente.

## Aplicaciones de Máquinas de Estado Finito

Las máquinas de estado finito se utilizan en una amplia variedad de aplicaciones, incluyendo:

- Control de secuencias en sistemas de automatización.
- Procesamiento de datos en microprocesadores y microcontroladores.
- Control de dispositivos electrónicos, como impresoras y sistemas de control de tráfico.
- Implementación de protocolos de comunicación.
- Diseño de máquinas de juego y sistemas de control de tráfico de red.

Las máquinas de estado finito son un concepto esencial en la electrónica digital y se utilizan ampliamente para controlar el comportamiento de sistemas digitales secuenciales. Su diseño y comprensión son cruciales para cualquier ingeniero electrónico.



## Observaciones
La maquina de estado finito es un modelo matematico que define un sistema sencuencial sincronico. Esta definido por una quintupla
1. {X}--> Alfabeto de entrada
2. {Z}--> Alfabeto de salida
3. {S}--> Conjunto de estados
4. {Su+1}-->Estado siguiente
5. {Zu}--> Salida actual
	- *En Mealy* su salida depende de la entrada y del estado actual
	- *En Moore* su salida depende exclusivamente de su estado actual
#### Modelo de Mealy
![[Pasted image 20230321090513.png|600]]
#### Modelo de Moore
![[Pasted image 20230321090543.png|600]]
#### Observaciones entre ambos modelos
Los estados en ambos modelos no tienen porque ser iguales, siempre se da que: $$|[S]mealy<o=[S]moore$$
- Cada estado se desdobla cuando pasa a de Mealy a Moore  en tantos estados como salidas posibles tenga este estado en Mealy