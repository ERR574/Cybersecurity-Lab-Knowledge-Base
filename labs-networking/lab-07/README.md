# Lab 07: Análisis del TCP Three-Way Handshake y Enumeración de Servicios

## Objetivo
Confirmar la existencia de un servicio activo y analizar el proceso de establecimiento y finalización de una sesión TCP.

## Herramientas
- **Víctima (Windows):** `python -m http.server 8000` (Servidor señuelo).
- **Atacante (Ubuntu):** `nmap -p 8000 -A` (Escaneo agresivo de servicios).
- **Analizador:** Wireshark.

## Hallazgos en Wireshark
Al filtrar por `tcp.port == 8000`, se identificó el flujo completo de la comunicación:
1. **[SYN]:** Petición de conexión desde la T490.
2. **[SYN, ACK]:** Aceptación de la conexión por parte de la IdeaPad (confirmando que el puerto está ABIERTO).
3. **[ACK]:** Establecimiento formal de la sesión.
4. **Data Transfer:** Nmap envió peticiones HTTP GET para identificar el servicio como "Python http.server".
5. **[FIN, ACK]:** Cierre ordenado de la conexión tras la enumeración.

## Reflexión SOC
Como analista, detectar un `SYN` seguido de un `SYN-ACK` me confirma que el atacante tuvo éxito al encontrar una puerta abierta. Si solo viera `SYN` seguido de `RST` (Reset), sabría que el intento fue fallido.
