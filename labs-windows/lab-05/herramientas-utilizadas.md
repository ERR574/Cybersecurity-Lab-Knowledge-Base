# **Herramientas y Programas Utilizados**
Para este laboratorio de detección y respuesta, el stack tecnológico fue:

- Sistema Operativo Host: Windows 10/11 Home Edition (Lenovo IdeaPad Gaming).

- Editor del Registro (regedit.exe): Utilizado para realizar cambios de configuración de bajo nivel en las políticas de auditoría del sistema, superando las limitaciones de la versión Home.

- Consola de Auditoría (auditpol.exe): Herramienta de línea de comandos fundamental para activar los "sensores" de seguridad de Windows (categorías de Inicio de sesión y Seguimiento detallado).

- PowerShell / CMD (Admin): Entorno de ejecución para la simulación de comandos de ataque y para forzar la actualización de políticas mediante gpupdate /force.

- Visor de Eventos (eventvwr.msc): Nuestra consola de monitoreo principal (SIEM local) donde se realizó el análisis, filtrado y búsqueda de los Event IDs 4625 y 4688.

- GitHub: Plataforma de documentación y control de versiones para el registro del portafolio profesional.
