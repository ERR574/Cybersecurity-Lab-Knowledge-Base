# Lab 08: Implementación de SIEM Centralizado (Wazuh)
## 1. Objetivo del Laboratorio
Establecer una arquitectura Cliente-Servidor para la recolección, centralización y análisis de telemetría de seguridad en tiempo real. El objetivo es trasladar los eventos locales detectados previamente (como las conexiones de Opera GX capturadas con Sysmon) hacia un panel de control profesional.

## 2. Infraestructura Utilizada
- Servidor (SIEM): Laptop Lenovo T490 ejecutando Ubuntu nativo (IP: 192.168.1.239).
- Endpoint (Agente): Laptop Lenovo IdeaPad Gaming ejecutando Windows 11 (IP: 192.168.1.82).
- Software: Wazuh Indexer, Manager & Dashboard v4.7.5.

## 3. Proceso de Implementación
Fase A: Instalación del Servidor (T490)
- Se ejecutó el script de instalación de Wazuh en el entorno Ubuntu.
- Se verificó el inicio correcto de los servicios críticos: wazuh-manager, filebeat y wazuh-dashboard.
- Se generaron credenciales de administrador para el acceso seguro vía interfaz web (https://localhost).

Fase B: Despliegue del Agente (IdeaPad)
- Se configuró el paquete de instalación desde el Dashboard, definiendo al servidor 192.168.1.239 como el receptor de logs.
- Se utilizó PowerShell (Admin) para descargar e instalar el agente de forma remota:
- Comando utilizado: Invoke-WebRequest -Uri https://packages.wazuh.com/....
- 
Se inició el servicio WazuhSvc, confirmando la conexión exitosa con el servidor central.

4. Resultados y Evidencia
-Conectividad: El agente IdeaPad-Gaming aparece con estado Active en el Dashboard centralizado.
- Ingesta de Datos: El SIEM comenzó a recibir telemetría inmediata, incluyendo eventos de inicio de sesión de Windows (Windows logon success).
- Mapeo de Amenazas: Los eventos recibidos se categorizan automáticamente bajo el framework MITRE ATT&CK, identificando tácticas de Persistence y Privilege Escalation.

5. Conclusión Técnica
La implementación exitosa de este laboratorio permite la visibilidad total sobre el endpoint. La integración de Sysmon con Wazuh asegura que cualquier actividad sospechosa en la red o en los procesos (como el uso de navegadores para exfiltración o ataques de fuerza bruta) sea alertada y centralizada para su posterior investigación.
