

### Introducción

- **Obsidian** es una aplicación para tomar notas que permite organizar información en un formato de texto plano.
- **Obsidian Publish** es un servicio de pago (8 USD al mes) que permite publicar tus notas en la web.

### Alternativa Gratuita: Quartz 4.0

- **Quartz 4.0** es un proyecto que ofrece una manera gratuita de publicar tus notas en la web.
- Aprovecha el formato de texto plano de las notas en Obsidian para evitar depender de servicios pagos.

#### Proceso para Publicar Notas Usando Quartz 4.0

1. **Instalar Node.js**
   - Node.js es un entorno de ejecución para JavaScript.
   - Descárgalo e instálalo desde su [sitio oficial](https://nodejs.org).

2. **Clonar el Proyecto Quartz**
   - Abre la terminal o consola de tu sistema.
   - Clona el repositorio de Quartz a tu máquina local y navega al directorio del proyecto.
``` Bash
git clone https://github.com/jackyzha0/quartz.git
cd quartz
npm i
npx quartz create
```

3. **Instalar Dependencias**
   - Dentro del directorio del proyecto, instala las dependencias necesarias usando npm o yarn.

4. **Añadir tus Notas**
   - Coloca tu bóveda de Obsidian (con todas sus carpetas y archivos) en el directorio del proyecto Quartz.

5. **Construir y Desplegar el Servidor Local**
   - Ejecuta el siguiente comando en la terminal: 
```bash
       npx quartz build --serve
```
   - El comando configurará el servidor local y desplegará tus notas en `localhost:8080`.

6. **Publicar en la Nube**
   - Puedes utilizar servicios gratuitos como GitHub Pages, Bitbucket, o cualquier otro proveedor que ofrezca hosting gratuito para desplegar tu servidor en la web.

7. **Mantèn actualizada tu web**
	- Una vez que ya tengas creada tu web en github page y tu codigo repositorio ya este creado, lo unico que deberas hacer para mantener actualizada tu web es el siguiente comando en la carpeta de quartz
``` bash
npx quartz sync
```
## Referencias
### Enlaces externos
- **Documentación del proyecto Quartz:** https://quartz.jzhao.xyz
### Notas relacionadas
- **Nota:**[[Obsidian]]
	- **Relacion-Reflexion:** Esta buena esta funcionalidad para poder estudiar o repasar si tenemos nuestro vault en todos lador
- **Nota:** [[Metodo Cornell]]
	- **Relacion-Reflexion:** Si aplicamos este metodo en nuestros apuntes, teniendo nuestras notas en la web podremos estudiar en cualquier lugar haciendo active recall