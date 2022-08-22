[[_TOC_]]

En virtud del cumplimiento del habilitador Nro. 76 cada aplicación web en producción debe garantizar que la información de usuario después del cierre de sesión sea eliminada.

| Información de usuario a eliminar |
| ----------- | 
| Almacenamiento local (Local storage) | 
| Almacenamiento de sesión (Session storage) | 
| Cookies| 

### Evidencia de cumplimiento por web

| Squad  | Responsable | Evidencia |
| ----------- | ---------------- | ---------------- | 
| Web Transaccional   | Chapter Frontend |  | 
| PAC (Plataforma de atención a cliente)   | Chapter Frontend |  | 
| Reporte web de estado de ahorros   | Squad Xperia |  | 
| Portal Fortel  | Squad Qamaleon |  | 
| Webs Públicas  | Squad Qamaleon |   | 

### Herramienta de captura de evidencia

1. Instalar awesome screenshot (Extensión para Google Chrome) [link de la extensión](https://chrome.google.com/webstore/detail/awesome-screenshot-and-sc/nlipoenfbbikpbjkfpfillcgkoblgpmj?hl=es)

2. Al momento de inicializar por primera vez la extensión, la misma va a solicitar el acceso con una cuenta de google. Por otro lado, también consultará el acceso a micrófono (No es necesario).

3. La herramienta se ubicará en la esquina superior derecha. Al darle clic ofrecerá las opciones de captura disponibles.

![Cap.PNG](/.attachments/Cap-2eb44a50-5fb0-4c38-a1f8-6eec41e73d51.PNG)

### Procedimiento de captura

1. Abrir la herramienta de desarrollador. Previo al login en la aplicación. Mostrar los datos de sesión (En Google Chrome: Pestaña Aplicación). Los datos a verificar son Almacenamiento Local, Almacenamiento de sesión y cookies.

2. Realizar el login luego mostrar los datos de sesión (En Google Chrome: Pestaña Aplicación). Los datos a verificar son Almacenamiento Local, Almacenamiento de sesión y cookies.

3. Realizar el logout finalmente mostrar los datos de sesión (En Google Chrome: Pestaña Aplicación). Los datos a verificar son Almacenamiento Local, Almacenamiento de sesión y cookies.

