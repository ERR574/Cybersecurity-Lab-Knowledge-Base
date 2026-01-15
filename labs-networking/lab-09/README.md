# Lab-09 Implementacion de Wazuh y Sysmon
Implementación de un sistema de monitoreo de endpoints utilizando Wazuh y Sysmon para detectar la ejecución de procesos maliciosos basados en la jerarquía Padre-Hijo. 
El objetivo es identificar cuando un proceso legítimo (como PowerShell) invoca una consola de comandos (CMD), una técnica común en ataques de movimiento lateral.

## Arquitectura del Laboratorio
- SIEM Manager: Servidor Wazuh instalado en Lenovo T490 (Ubuntu/Linux).
- Endpoint: Lenovo IdeaPad Gaming (Windows 11) monitoreada mediante el agente de Wazuh.
- Telemetría: Microsoft Sysmon configurado para la captura de eventos detallados de procesos (EventID 1).
