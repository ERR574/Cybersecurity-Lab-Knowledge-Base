# Lab 06: Detección de Reconocimiento de Red (Nmap + Wireshark)

## Objetivo
Identificar y analizar un escaneo de puertos activo en la red local, observando el comportamiento desde la perspectiva del atacante y del defensor.

## Stack Tecnológico
* **Atacante:** Ubuntu 22.04 (Lenovo T490) con **Nmap 7.94SVN**.
* **Víctima:** Windows 11 (Lenovo IdeaPad Gaming) con **Wireshark**.

## Análisis del Incidente

### 1. Perspectiva del Atacante (T490)
Se ejecutó un escaneo rápido sobre la IP `192.168.1.xx`. 
- **Comando:** `sudo nmap -F 192.168.1.xx`.
- **Resultado:** Los 100 puertos escaneados aparecieron como **"filtered"**. Esto indica que el firewall de la víctima está descartando los paquetes sin responder.

### 2. Perspectiva del Defensor (IdeaPad)
En Wireshark se filtró el tráfico proveniente de la IP del atacante (`192.168.1.xxx`).
- **Patrón Detectado:** Una ráfaga masiva de paquetes **TCP [SYN]** dirigidos a múltiples puertos en un intervalo de milisegundos.
- **Evidencia Forense:** La captura muestra intentos de conexión a puertos críticos como el `3306` (MySQL), `445` (SMB) y `8080` (HTTP-Proxy).

## Conclusión
El firewall de Windows está cumpliendo su función de "sigilo" al no responder a las peticiones, lo que obliga al atacante a usar técnicas más agresivas o ruidosas que son fácilmente detectables mediante análisis de tráfico.
