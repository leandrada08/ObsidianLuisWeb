La programacion orientada a objeto trabaja con un paradigma basado en objetos que pueden tener caracteristicas y hacer cosas. Los datos y las funciones que los manipulan son internos de cada objeto e inaccesibles al resto.
*Ventaja:* 
- Facilita la comprension del programa y del problema.
- Mas modular.
- Los objetos son reusables.


## Cosas que nos permite la POO.
**Abstraccion:** Permite separar la implementacion de la interfaz de uso de un componente.
**Modularidad:** Permite modificar las caracteristicas de algunos componentes sin afectar al resto
**Encapsulamiento:** Permite ocultar la informacion interna de un componente al resto sistema
**Relaciones:** Permite definir vinculaciones entre los componentes que colaboran para resolver una parte del problema.
**Herencia:** Permite crear un componente especializado a partir uno generico.
**Polimorfismo:** Permite que dos componentes especializados que parten de un mismo ancestro realicen una misma operacion en forma diferente.

## Caracteristicas de los objetos
**Identidad:** Permite diferenciar uno de otro, aun cuando sus atributos sean igual
**Estado:** El estado de un objeto esta definido por el valor de sus atributos.
**Comportamiento:** Esta definido por las acciones que  se pueden realizar sobre el objeto.
### Atributos y metodos
- Los atributos almacenan los datos de un objeto.
- Los metodo, son funciones o procedimientos que implementan las acciones definidas para objeto.
- La unica forma de manipular la informacion de un objeto es a travez de sus metodos.
### Interaccion de los objetos
- Conceptualmente los objetos se comunican intercambiando mensajes.
- Generalmente esto se traduce en un objeto que ejecuta un metodo de otro objeto.
- Los dinstintos mensajes que pueden recibir un objeto se denominan protocolo
	- Es equivalente a una API del objeto.
### Clases de objeto.
Es habitual que en un software existan varios objetos que comparte estructura y comportamiento. Es por esto que nosotros programamos clases de objetos y cuando vamos a usarlo definimos un objeto de esa clase. Cada objeto es una instancia de una clase y comparte la estructura y comportamiento con los otros objetos de la misma clase

## Implementacion en C
- Cada archivo .c es equivalente a un paquete donde se define una o mas clases
- El archivo .h declara los metodos publicos de las clases.
	- Para cada clase se declara un puntero a una estructura anonima para representar a un objeto en particular.
- La definicion de los miembros de la estructura es privada al archivo .c y almacena los atributos de cada objeto.
- Los metodos son funciones que 

## Visibilidad de metodo y atributos
*Private:* solo puede ser accedido internamente por el propio objeto
*Protected:* Solo puede ser accedido por el objeto o por un decenciente
*Pachage:* solo puede ser accedido por objetos del mismo paquete
*Public:* puede ser accedido desde cualquier parte del sistema