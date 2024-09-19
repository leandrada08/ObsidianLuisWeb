
# Ingles
## What is Software Testing
It is the process focused on finding defects in a system.
*Static Testing (Verification):* 
- The code is not executed
- It verifies standard compliance
*Dynamic Testing (Test):*
- The code is executed
- It verifies requirement compliance

## Coding Guidelines
It is the set of conventions on how to write code. They increase readability and reduce errors.
- NASA SEL-94-003: Format from NASA’s Jet Propulsion Laboratory

### MISRA 2004
- C90 Code

## Verification
It can be performed by automatic tools (Linter)
- Verify prototype compliance
- Eliminate ambiguous situations
It can also be done by another person
- Improves software quality
- Improves the quality of the programmer
- Enhances teamwork

### Clang-Format
A tool to adjust and/or verify the format of C source code.

### Cppcheck

### Git Hooks
Functions that Git allows you to define, which are executed when making a commit or push. In these, you can install scripts that review or change the code format.
This tool also saves the configuration in a file within the same repository.

## Testing
Tests are dynamic checks. There are tests for:
- Unit
- Module
- System

### Unit Tests
They test a C file. Only the *external functions* are tested.
- All functions used from other files utilized by the code are replaced by Stub or Mock functions.
![[Pasted image 20230522113435.png|200]]

### Module Tests
They test the entire set of files that make up a module. The functions provided by other modules must be replaced with stubs or mocks.
- Similar to unit tests but include possible coupling issues between the module components.
- The same tools used for unit tests are employed.

### Test Structure
![[Pasted image 20230522114641.png|500]]
- Test procedures are each individual test. Every time we do one, we go through the same process:
	1. Set known values
	2. Call the function under test
	3. Verify the results 
### Testing Framework
All frameworks, regardless of language, use exactly the same 3 components.

### Ceedling: The Tool We Will Work With
It is a framework that works together with *Unity and CMock*.
It automates testing tasks:
- Automatically generates mocks (CMock)
- Executes tests (Unity)
- Collects results
It also automates the creation of the Makefile.

#### Unity
It is a library for unit and module testing of C code. It allows you to write tests very quickly and in a highly conceptual manner.

#### CMock
It is a library for generating Stub or Mock functions.
*Mock:* A replacement for the functions/objects used in a test. These simulate the behavior of objects or components of the system that are not yet available or are difficult to configure in the test environment. They help to isolate and independently test the behavior of a specific part of the system.
*Stub:* They do nothing and only allow the test to compile.

## Test-Driven Programming
### How We Program
- We obtain a subset of requirements
- We define one or more functions
- We write each function
- We write a program to test the function
- We keep the function
- We discard the test program
#### What's Wrong?
Often, when implementing a new feature, we break another one. If we save the tests "alongside" the function, every time something changes, we can verify that what used to work still does.
- These tests are part of the documentation.
- Testing frameworks simplify the process.
### What If We Change?
If we write the tests first and then the program:
- We guarantee compliance with the requirements.
- We force proper requirement analysis.

## Test Driven Development
- Improves the quality of developed software
- Design focused on needs
- Simpler design
- Higher productivity
- Less time spent debugging errors.

### The Three Rules of TDD
- You can't write any production code unless it’s to make a failing unit test pass.
- You can't write more than one failing unit test at a time, and a compilation failure is also considered a failure.
- You can't write more production code than strictly necessary to make the failing unit test pass.

## Observations
- After passing the tests, refactor them.


# Español
## Que es el testing de software
Es el proceso centrado en el objetivo de encontrar defectos en un sistemas
*Prueba Estaticas(verificacion):* 
- El codigo no es ejecutado
- Verifica el cumplimiento del estandar
*Prueba dinamica(Test):*
- El codigo es ejecutado
- Verifica el cumplimiento de los requisitos

## Coding Gidelines
Es el conjunto de convenciones sobre como escribir el codigo. Aumentan la legibilidad y disminuyen los error.
- NASA SEL-94-003: Formato del laboratorio de propulsion jeet de la nasa

### MISRA 2004
- Codigo C90


## Verificacion
Puede ser realizadas por herramientas automaticas(Linter)
- Verifican cumplimiento de los prototipos
- Eliminan situaciones ambiguas
Tambien pueden ser realizadas por otra persona
- Mejora la calidad del software
- Mejora la calidad del programador
- Mejora el trabajo en equipo

### Clang-Format
Herramienta para ajustar y/o verificar el formato del codigo fuente en C.

### Cppcheck

### Los hook de Git
Funciones que git permite definir que se ejecutan al realizar un commit o push. En estos se puede instalar scripts que revisen o cambien el formato el codigo.
Esta herramienta tambien guarda la configuracion en un archivo dentro del mismo repositorio.

## Testing
Los test son pruebas dinamicas. Existen pruebas:
- Unitarias
- Modulo
- Sistema


### Pruebas unitarias
Prueban un archivo C. Se prueban unicamente las *funciones externas*
- Toas las funciones utilizados de otros archivos utilizados por el codigo se reemplazan por funciones Stub o Mock.
![[Pasted image 20230522113435.png|200]]

### Prueba de Modulos
Prueban todo el conjunto de archivos que conforman un modulo. Se debe reemplazar las funciones provistas por otros modulos por stubs o mocks
- Parecidas a las pruebas unitarias pero incluyen los posibles problemas de acoplamiento entre los componentes del modulo.
- Se utilizan las mismas herramientas que para los test unitarios.

### Estructura de los test
![[Pasted image 20230522114641.png|500]]
- Test procedures son cada prueba. Cada vez que hacemos una realizamos el mismo proceso
	1. Fija valores conocidos
	2. Llama a la funcion bajo prueba
	3. Verifica los resultados 
### Framework de testing
Todos los framework de todos los lenguajes usan exactamente los mismo 3 componentes.

### Ceedling: Herramienta con la que trabajaremos
Es un framework que trabaja en conjunto con *unity y cmock*.
Aumatiza las tareas de testing:
- Genera automaticamente los mock(cmock)
- Ejecuta los test(unity)
- Recopila los resultados
Automatiza tambien la creacion del makefile

#### Unity
Es una libreria para testint de codigo C a nivel de unidades y modulo. Permite escribir test muy rapidamente y en una forma muy conceptual.

#### CMock
Es una libreria para generar funciones de Stub o de Mock
*Mock:* Reemplazo de las funciones/objetos que se utilizan en una prueba. Estos simulan el comportamiento de objetos o componentes del sistema que aun no estan disponibles o que son dificiles de configurar en el entorno de pruebas. Nos sirven para aislar y probar de manera independiente el comportameitno de una determinada parte del sistema.
*Stub:* No hacen nada y solo permiten la compilacion del test.



## Programacion guiada por prueba
### Como programamos
- Obtenemos un sub-conjunto de requerimiento
- Definimos una o mas funciones
- Escribimos cada una de las funciones
- Escribimos un programa que pruebe la funcion
- Conservamos la funcion
- Tiramos el programa de prueba
#### Que esta mal?
Muchas veces al implementar una nueva funcionalidad rompemos otra, si guardamos las pruebas "junto" con la funcion, cada vez que algo cambia podemos verificar que lo que antes andaba sigue funcionando. 
- Estas pruebas son parte de la documentacion.
- Los frameworks de testing simplifican el proceso.
### Y si cambiamos?
Si escribimos primero los test y despues el programa:
- Garantizamos el cumplimiento de los requisitos
- Obligamos a realiza un correcto analisis de requisitos.

## Test Driven Development
- Mejora la calidad del software desarrollado
- Diseño enfocado a las necesidades
- Diseño mas simple
- Mayor productividad
- Menor tiemmpo invertido en depuracion de errores.

### Las tres reglas de TDD
- No puede escribir ningun codigo de produccion a menos que sea para hacer pasar una prueba unitaria que falla
- No escriba mas que una prueba unitaria que falle y una falla de compilacion es tambien una falla
- No escriba mas codigo de produccion estrictamente necesario para hacer pasar la prueba unitaria que falla.



## Observaciones
- Despues de cumplir las pruebas, refactorizarlas
