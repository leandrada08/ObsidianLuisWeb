### **Apunte sobre Entornos Virtuales en Python**

#### 1. **¿Qué es un entorno virtual?**
Un **entorno virtual** en Python es un espacio aislado donde puedes instalar versiones específicas de paquetes y bibliotecas sin que afecten a otros proyectos o al sistema global de Python. Es como un "contenedor" en el que puedes trabajar en un proyecto sin interferir con otros, lo cual es especialmente útil si diferentes proyectos requieren distintas versiones de los mismos paquetes.

#### 2. **¿Para qué sirve un entorno virtual?**
- **Aislamiento**: Cada proyecto tiene sus propias dependencias (bibliotecas y versiones) sin afectar el sistema operativo ni otros proyectos.
- **Evitación de conflictos**: Si trabajas en múltiples proyectos que requieren diferentes versiones de los mismos paquetes, los entornos virtuales previenen conflictos.
- **Facilidad para compartir**: Puedes compartir un archivo (`requirements.txt`) con las dependencias del entorno, permitiendo que otras personas reproduzcan el entorno en sus máquinas de manera fácil.

#### 3. **Cómo crear un entorno virtual**
Para crear un entorno virtual, debes tener instalada una versión de Python 3. Luego, en la terminal:

```bash
python3 -m venv nombre_del_entorno
```

- Esto creará una carpeta llamada `nombre_del_entorno` (puedes llamarlo `.venv` para mantenerlo oculto y organizado) en la que se almacenará el entorno virtual.

#### 4. **Cómo activar un entorno virtual**
Una vez creado, debes **activar** el entorno virtual para empezar a usarlo. Esto cambia tu entorno de trabajo para que uses las bibliotecas y el intérprete de Python del entorno virtual.

- En **macOS** y **Linux**:
  ```bash
  source nombre_del_entorno/bin/activate
  ```


- **Indicador**: Verás el nombre del entorno virtual a la izquierda del prompt de la terminal, lo que indica que el entorno está activado. Por ejemplo:
  ```
  (nombre_del_entorno) $
  ```

#### 5. **Instalar paquetes dentro del entorno virtual**
Una vez activado el entorno, cualquier paquete que instales con `pip` será instalado solo dentro de ese entorno virtual.

```bash
pip install nombre_paquete
```

Para ver los paquetes instalados en el entorno, usa:

```bash
pip list
```

#### 6. **Cómo salir (desactivar) el entorno virtual**
Cuando termines de trabajar en el proyecto, puedes **desactivar** el entorno virtual con el siguiente comando:

```bash
deactivate
```

- Esto te devuelve al entorno de Python global del sistema. El prompt de la terminal ya no mostrará el nombre del entorno.

#### 7. **Recrear un entorno virtual en otro equipo**
Si deseas compartir el entorno con otros o recrearlo en otro equipo, puedes generar un archivo `requirements.txt` con las dependencias del entorno:

```bash
pip freeze > requirements.txt
```

En otro equipo, simplemente clona el proyecto, activa un nuevo entorno virtual y usa el archivo `requirements.txt` para instalar las dependencias:

```bash
pip install -r requirements.txt
```

#### 8. **Eliminar un entorno virtual**
Para **eliminar un entorno virtual**, solo necesitas borrar la carpeta que contiene el entorno (`nombre_del_entorno` o `.venv`).

#### 9. **Consejos útiles para manejar entornos virtuales**
- **Nombra el entorno `.venv`**: Es común llamar al entorno virtual `.venv` y colocarlo en la raíz del proyecto para mantener el proyecto organizado y fácil de reconocer.
- **Añadir `.venv` a `.gitignore`**: Si estás usando Git, asegúrate de agregar el entorno virtual a tu archivo `.gitignore` para no subirlo al repositorio:
  ```bash
  .venv/
  ```
- **VSCode y otros editores**: Si usas editores como VSCode, selecciona el intérprete del entorno virtual para asegurarte de que tu editor lo utilice para ejecutar el código.

#### Resumen de Comandos:
1. **Crear un entorno virtual**:
   ```bash
   python3 -m venv nombre_del_entorno
   ```

2. **Activar el entorno virtual**:
   - macOS/Linux:
     ```bash
     source nombre_del_entorno/bin/activate
     ```
   - Windows:
     ```bash
     nombre_del_entorno\Scripts\activate
     ```

3. **Desactivar el entorno virtual**:
   ```bash
   deactivate
   ```

4. **Instalar paquetes en el entorno virtual**:
   ```bash
   pip install nombre_paquete
   ```

5. **Crear archivo de dependencias (`requirements.txt`)**:
   ```bash
   pip freeze > requirements.txt
   ```

6. **Instalar dependencias desde un archivo**:
   ```bash
   pip install -r requirements.txt
   ```

Con este apunte ya deberías tener una comprensión clara de los entornos virtuales y cómo manejarlos. ¡Estás listo para trabajar con ellos en tus proyectos!