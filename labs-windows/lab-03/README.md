# Lab 03: Detección de Fallos de Autenticación en Windows (EID 4625)

## Objetivo
Habilitar la auditoría de seguridad para capturar y analizar intentos de inicio de sesión fallidos, simulando un vector de ataque de fuerza bruta.

## Metodología y Desafíos Técnicos
Durante el despliegue en una máquina host con Windows Home, se identificaron las siguientes limitaciones:
1. **Ausencia de secpol.msc:** La consola de Directivas de Seguridad Local no está disponible en versiones Home.
2. **Conflicto de Localización:** El comando `auditpol` falló inicialmente al usar parámetros en inglés (`Logon`).

### Solución aplicada (Troubleshooting)
Se utilizó la interfaz de línea de comandos (CLI) con privilegios de administrador para forzar la auditoría mediante el nombre de subcategoría localizado:
`auditpol /set /subcategory:"Inicio de sesión" /failure:enable /success:enable`

##  Análisis de Evidencias
Al inspeccionar el **Event ID 4625**, se identificaron los siguientes campos críticos:
- **Nombre de cuenta:** Identificación del usuario objetivo.
- **Tipo de inicio de sesión (Logon Type):** (Ej: Tipo 2 - Interactivo).
- **Dirección de red de origen:** Origen del intento de acceso.

##  Conclusión
Este laboratorio demuestra que la visibilidad no siempre está activa por defecto. Un analista debe conocer las herramientas de bajo nivel (CLI) para asegurar la ingesta de logs independientemente de la edición del sistema operativo.
