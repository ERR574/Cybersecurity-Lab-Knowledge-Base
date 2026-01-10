# Lab 01: Análisis de Autenticación y Visibilidad en Linux

## Objetivo
Aprender a localizar e interpretar los registros de seguridad (logs) relacionados con la gestión de usuarios y el estado de la red.

## Parte 1: Auditoría de Logs (PAM & Auth)

### Ejecución
Se monitorizó en tiempo real el archivo de autenticación:
`sudo tail -f /var/log/auth.log`

### Observaciones Técnicas
Al intentar accesos fallidos o usar `sudo`, identifiqué los siguientes patrones:
- **Intento fallido:** `authentication failure; logname= user=...`
- **Uso de sudo:** `COMMAND=/usr/bin/whoami`
