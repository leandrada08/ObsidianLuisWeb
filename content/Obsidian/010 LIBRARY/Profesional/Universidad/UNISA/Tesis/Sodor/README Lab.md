Sobre la Colección de Procesadores Sodor
====================================

**Nota: Este repositorio se ha actualizado para utilizarse con el [Chipyard](https://github.com/ucb-bar/chipyard) SoC Generator.**
**Para la antigua versión autónoma de Sodor (que ya no se mantiene), consulta https://github.com/ucb-bar/riscv-sodor/tree/sodor-old.**

Diagramas: [Sodor Github wiki](https://github.com/ucb-bar/riscv-sodor/wiki)

Más documentación: [Librecores Sodor wiki](https://github.com/librecores/riscv-sodor/wiki)

Desarrollo descendente: [Librecores Sodor](https://github.com/librecores/riscv-sodor)


Este repositorio se ha creado para demostrar una serie de simples tuberías de enteros [RISC-V](http://riscv.org) escritas en [Chisel](http://chisel.eecs.berkeley.edu):

* 1 etapa (básicamente un simulador de ISA)
* 2 etapas (demuestra el pipelining en Chisel)
* 3 etapas (utiliza memoria secuencial; compatible con las versiones Harvard y Princeton)
* 5 etapas (puede alternar entre completamente bypassed o completamente interlocked)
* Implementación microcodificada basada en "bus"

Todos los núcleos implementan la ISA base de usuario de enteros RISC-V de 32 bits (RV32I) versión 2.0. Ninguno de los núcleos admite memoria virtual y, por lo tanto, solo implementan el Modo M (Machine-level) de la ISA privilegiada v1.10.

Todos los procesadores se comunican con una memoria de almohadilla simple (asíncrona, de un solo ciclo), sin memoria externa de respaldo (la excepción es la de 3 etapas, su memoria de almohadilla es síncrona). Los programas se cargan a través de JTAG o TSI, almohadillas de 3 puertos de memoria (instrucción, datos, depuración).

Este repositorio está configurado para utilizar el archivo Verilog generado por Chisel3, que se alimenta a Verilator junto con un arnés de prueba en C++ para generar y ejecutar los emuladores Sodor.

Este repositorio funciona muy bien como laboratorio de pregrado (y ha sido utilizado por la clase CS152 de Berkeley durante 3 semestres y contando). Consulta doc/ para un ejemplo, así como para algunos diagramas del procesador. Sin embargo, ten cuidado, algunos de esos documentos pueden quedar obsoletos a medida que evoluciona la ISA privilegiada.



Obtención del repositorio y construcción de los emuladores de procesador
=====================================================

Este repositorio **NO** es un repositorio independiente que se ejecuta por sí mismo. Sigue las instrucciones en https://chipyard.readthedocs.io/en/latest/ para configurar Chipyard y simular los núcleos Sodor.

FAQ
===

*¿Cuál es el objetivo de estos núcleos?*

En primer lugar, proporcionar un conjunto de núcleos fáciles de entender que los usuarios puedan modificar y utilizar fácilmente. Sodor es útil tanto como una introducción rápida a la [ISA RISC-V](http://riscv.org) como al lenguaje de construcción de hardware [Chisel3](http://chisel.eecs.berkeley.edu).

*¿Hay algún diagrama de estos núcleos?*

Puedes encontrar diagramas de algunos de los procesadores en la [Sodor Github wiki](https://github.com/ucb-bar/riscv-sodor/wiki), en doc/, o en doc/lab1.pdf. Una descripción más completa de la implementación de microcódigo se encuentra en el [sitio web de CS152](http://inst.eecs.berkeley.edu/~cs152/sp12/handouts/microcode.pdf).


*¿Cómo genero código Verilog para usar en una FPGA?*

Chisel3 produce Verilog por defecto, que se puede generar con el siguiente comando:
```bash
cd emulator/rv32_1stage
make generated-src/Top.v
```

*¡Quiero ayudar! ¿A dónde debo ir?*

Puedes participar en la conversación de Sodor en [gitter](https://gitter.im/librecores/riscv-sodor). El desarrollo descendente también está teniendo lugar en [Librecores](https://github.com/librecores/riscv-sodor). Los hitos importantes se fusionarán aquí. ¡Échale un vistazo! También aceptamos solicitudes de extracción aquí.

TODAVÍA POR HACER
-----------------

Aquí tienes una lista informal de cosas que sería bueno hacer. ¡Siéntete libre de contribuir!

* Reducir el recuento de puertos en la memoria de almohadilla compartiendo uno de los puertos de la CPU con el puerto HTIF.
* Proporcionar un arnés de prueba Verilog y poner la de 3 etapas en una FPGA.
* Agregar soporte para las pruebas de ISA ma_addr, ma_fetch. Esto requiere detectar excepciones de dirección mal alineada.
* Limpiar en gran medida el archivo common/csr.scala, para que sea más claro y comprensible.
* Refactorizar la lógica de parada, kill, fencei y excepción de las 5 etapas para que sea más comprensible.
* Actualizar el código de microcódigo para manejar adecuadamente las instrucciones ilegales (rv32mi-p-illegal) y manejar adecuadamente las excepciones generadas por el archivo CSR (rv32mi-p-csr).