## Funciones de tick
En términos generales, una función de tick es una función que se llama en intervalos regulares (conocidos como ticks o interrupciones de temporización) por un temporizador de hardware o por una tarea de software que se ejecuta en segundo plano. El intervalo de tiempo entre las llamadas a la función de tick se determina en función de la aplicación y de las necesidades del sistema.
La función de tick típicamente se utiliza para actualizar el estado del sistema y realizar tareas como:
-   Actualizar las lecturas de sensores y actuadores
-   Actualizar la pantalla o la interfaz de usuario
-   Realizar cálculos y decisiones basadas en el tiempo
-   Enviar o recibir datos a través de una red o una interfaz de comunicación
-   Controlar el flujo del programa
-   Generar señales de temporización
### Explicacion didactica
Imagina que estás programando un sistema embebido en C, como por ejemplo un dispositivo de control de temperatura en un horno. Una parte importante de este sistema es la capacidad de medir la temperatura y ajustar el calor para mantenerla dentro de un rango deseado. Para hacer esto, necesitas una forma de actualizar la lectura de la temperatura y ajustar el calor en momentos específicos en el tiempo.
Aquí es donde entran las funciones de tick. Puedes programar una función de tick que se llame cada cierto intervalo de tiempo (por ejemplo, cada 100 milisegundos) y que actualice la lectura de la temperatura, verifique si está dentro del rango deseado y ajuste el calor si es necesario. Al hacerlo, puedes garantizar que el sistema se actualice y se comporte de manera consistente y predecible.
Además de actualizar la temperatura, las funciones de tick también se pueden utilizar para realizar otras tareas importantes en momentos específicos en el tiempo, como actualizar la pantalla, realizar cálculos y tomar decisiones basadas en el tiempo, enviar o recibir datos a través de una red, controlar el flujo del programa y generar señales de temporización.





## Lista enlazada
Una lista enlazada doble es una estructura de datos que consta de nodos, donde cada nodo contiene un valor y punteros al siguiente y al elemento anterior en la lista. Los punteros al siguiente y al anterior permiten que la lista sea recorrida en ambas direcciones.
Para crear una lista enlazada doble, primero debemos definir una estructura que represente un nodo de la lista. Podemos definir la estructura de la siguiente manera:
``` C
typedef struct Node {
    int value;
    struct Node* next;
    struct Node* prev;
} Node;
```
En esta estructura, `value` es el valor que contiene el nodo y `next` y `prev` son punteros a los nodos siguientes y anteriores en la lista, respectivamente.

Una vez que tenemos la estructura del nodo, podemos crear una función para insertar un nuevo nodo en la lista. La función debe recibir un puntero a la cabeza de la lista y un valor, y debe devolver un puntero al nuevo nodo insertado:
```C
Node* insert(Node* head, int value) {
    Node* newNode = (Node*) malloc(sizeof(Node));
    newNode->value = value;
    newNode->next = head;
    newNode->prev = NULL;
    if (head != NULL) {
        head->prev = newNode;
    }
    return newNode;
}

```
