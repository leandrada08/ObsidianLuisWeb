### **¿Por qué considerar la ética en IA?**
La IA tiene un enorme potencial, pero también puede tener efectos negativos si no se usa de manera responsable. Por eso, es importante hacerte preguntas como:
- **¿Qué estoy construyendo?**
- **¿Cuál es el objetivo?**

No siempre la IA es la mejor solución. Hay que comparar entre usar **programación tradicional** o **aprendizaje automático (IA)** según la situación:

### **Programación tradicional vs. IA**
1. **Programación tradicional**: Es ideal cuando hay **menos datos** y las reglas son **simples**. Es:
   - Más rápida de construir.
   - Más fácil de explicar y depurar.
   - Consistente.
   Pero **no escala bien**, **no se adapta** automáticamente y **no sirve para tareas complejas** que necesitan muchas reglas.
   
2. **IA (Aprendizaje automático)**: Es mejor para problemas complejos y puede **adaptarse y mejorar con el tiempo**. Sin embargo:
   - **Requiere muchos datos** y tiempo para entrenarse.
   - Es más difícil de **interpretar y depurar** (Problema de Caja Negra).
   - **Más lenta** de desarrollar.

### **Decidiendo cuándo usar IA**
Antes de usar IA, pregúntate:
- **¿Cuál es el problema?**
- **¿Por qué necesita ser resuelto?**
- **¿Podría resolverse con programación tradicional?**
- **¿La IA agregaría un valor único?**

Por ejemplo, en el caso del diagnóstico de la **retinopatía diabética**, la IA ofrece un valor único al detectar patrones en imágenes que los especialistas podrían no notar.

### **IA para el bien social**
Además de resolver problemas técnicos, es importante pensar en el impacto social de lo que estás creando. La **IA para el bien social** busca usar la IA para enfrentar grandes desafíos, como la pobreza o la conservación del medio ambiente.

El **TinyML**, al ser **eficiente en memoria y energía**, abre nuevas posibilidades para aplicar IA en lugares o dispositivos donde antes no era posible, como **sensores en el bosque** para proteger la fauna o en **artículos cotidianos**.

### **Evitar el sobreajuste (overfitting)**
El **sobreajuste** es cuando una red neuronal se especializa tanto en el conjunto de datos de entrenamiento que falla con nuevos datos. Técnicas como **dropout regularization** ayudan a evitarlo apagando algunas neuronas durante el entrenamiento para evitar que ciertas partes de la red se especialicen demasiado.

En resumen:
- **Evalúa cuidadosamente si la IA es la solución adecuada** para el problema.
- **Considera el impacto social de lo que desarrollas**.
- **Usa técnicas como el dropout** para evitar que tu modelo se sobreajuste y funcione mejor en situaciones reales.

Este enfoque te ayudará a diseñar sistemas de IA que no solo sean eficaces, sino también responsables y éticos.


Susan Kennedy en esta clase introduce un concepto clave del diseño ético en IA: **centrarse en los usuarios y sus valores** durante la fase de diseño. Aquí te lo explico de manera sencilla:

### **¿Para quién estoy diseñando la tecnología?**
En cualquier proyecto de IA, es importante identificar a los **stakeholders** o partes interesadas:
- **Usuarios directos**: quienes van a usar la tecnología (ej. médicos que usan un sistema de IA para diagnosticar enfermedades).
- **Usuarios indirectos**: personas que se ven afectadas por la tecnología aunque no la usen directamente (ej. los pacientes que reciben los diagnósticos).

### **Identificar los valores de los usuarios**
Es importante entender qué valores tienen estos stakeholders. Por ejemplo:
- Los **médicos** podrían valorar la **precisión** de la IA y que no les requiera mucha capacitación.
- Los **pacientes** valoran la **privacidad** y poder confiar en el diagnóstico de su médico.

### **Tensiones de valores**
A veces, los valores de diferentes stakeholders pueden entrar en conflicto, y esto crea lo que se llama "tensiones de valores". Ejemplos:
- Un médico quiere usar una IA muy precisa, pero esa IA no puede explicar cómo llega a los diagnósticos, lo que podría generar desconfianza en los pacientes.
- La recolección de datos para investigación podría ser valiosa para el médico, pero los pacientes pueden sentir que su **privacidad** está en riesgo.

### **Resolver tensiones de valores**
Para resolver estas tensiones, debemos preguntarnos:
1. **¿Es uno de los valores un derecho?** Si es un derecho (como la privacidad), tenemos que cumplir con las leyes que lo protegen.
2. **¿Qué valores priorizan los usuarios?** Si un médico valora la precisión de la IA, puede estar dispuesto a recibir más capacitación para usarla.
3. **¿Se pueden cumplir ambos valores?** A veces, se puede satisfacer el valor del paciente (como la privacidad) usando técnicas de anonimización de datos.

### **Considerar diferentes perspectivas**
Además de las tensiones de valores, es importante analizar la tecnología desde perspectivas diversas, como aquellas de grupos marginados o subrepresentados. Un ejemplo sería diseñar un **asistente de voz** que pueda entender diferentes acentos o formas de hablar, como el inglés vernáculo afroamericano o personas con discapacidades del habla.

### **Multiestabilidad de la tecnología**
La **multiestabilidad** se refiere a cómo una tecnología puede usarse de formas no previstas, algunas buenas y otras malas. Por ejemplo:
- Google decidió no vender su tecnología de reconocimiento facial porque podría usarse para vigilancia inapropiada.
- OpenAI inicialmente decidió no lanzar GPT-2 por miedo a que se usara para crear noticias falsas.

Algunas veces, se debe frenar el desarrollo de una tecnología si su mal uso es muy peligroso, pero en otras, podríamos ajustar su diseño para prevenir esos malos usos. Incluso, en algunos casos, podemos **aprovechar los usos no intencionados** si descubrimos que pueden tener beneficios positivos.

En esta clase, el profesor nos lleva a reflexionar sobre las **consecuencias del fallo de una IA** y cómo equilibrar la precisión y el recall, que son dos medidas clave en el rendimiento de los modelos de clasificación.

### **Diferencia entre precisión y recall**:
- **Precisión (precision)**: Es la capacidad del modelo para evitar **falsos positivos**. Es decir, cuando el modelo predice algo (por ejemplo, que hay un incendio o que un correo es spam), queremos asegurarnos de que sea correcto. Optimizar para alta precisión reduce los **falsos positivos** (errores de tipo I).
  
- **Recall**: Es la capacidad del modelo para evitar **falsos negativos**. Es decir, no queremos que el modelo ignore algo que en realidad sí es importante (por ejemplo, un incendio real o un correo importante marcado como spam). Optimizar para alto recall reduce los **falsos negativos** (errores de tipo II).

### **Errores de tipo I y II**:
- **Tipo I**: Falso positivo (por ejemplo, se activa una alarma de incendio cuando no hay incendio).
- **Tipo II**: Falso negativo (por ejemplo, no se activa la alarma cuando realmente hay un incendio).

### **Ejemplos prácticos**:
- **Filtro de spam**: Un error de tipo I sería que un correo importante termine en la carpeta de spam. Un error de tipo II sería que un correo spam llegue a la bandeja de entrada. En este caso, los **errores de tipo I son más dañinos** (perder un correo importante), por lo que queremos **más precisión**.
  
- **Detector de humo**: Un error de tipo I sería una falsa alarma (ruido molesto). Un error de tipo II sería no detectar un incendio real. En este caso, los **errores de tipo II son más dañinos** (no detectar un incendio), por lo que optimizamos para **alto recall**.

### **Cómo decidir entre precisión y recall**:
Debemos hacernos 4 preguntas para decidir si priorizamos precisión o recall:
1. ¿Quiénes son los **stakeholders** directos e indirectos?
2. ¿Cuáles son las consecuencias de los **errores de tipo I**?
3. ¿Cuáles son las consecuencias de los **errores de tipo II**?
4. Comparar ambos errores y decidir cuál es más dañino.

### **Ejemplo adicional**:
- **Sistema de vigilancia**: Si el sistema solo manda una alerta al usuario, los **errores de tipo II** (no detectar un intruso) son más peligrosos, así que optimizamos para alto recall. Pero si el sistema alerta a la policía automáticamente, un **error de tipo I** (falsa alarma) desperdicia recursos policiales, por lo que preferimos **más precisión**.

### **Conclusión**:
No hay una regla universal para elegir entre precisión y recall. Depende del contexto y de las consecuencias que los errores puedan tener para los usuarios directos e indirectos.