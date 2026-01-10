# Lab 05: Simulación y Detección de Reconocimiento Local (Threat Hunting)

## Objetivo
Actuar como Analista SOC de Nivel 1 para detectar una secuencia de comandos de reconocimiento (Discovery) ejecutados de forma automatizada en un host de Windows.

## Escenario de "Ataque"
Se simuló la actividad de un intruso que, tras obtener acceso inicial, busca entender su entorno mediante la ejecución encadenada de comandos en PowerShell:
`whoami; net user; ipconfig /all`

## Metodología de Investigación
Utilizando el **Visor de Eventos (Security Logs)**, se realizó un triage basado en los filtros configurados en el laboratorio anterior (ver laboratorios 3 y 4 de windows):
1. **Filtro Aplicado:** Event ID 4688 (Creación de procesos).
2. **Análisis de Correlación:** Se identificaron tres eventos consecutivos con la misma marca de tiempo (Timestamp), lo que confirma que no fue una interacción humana típica, sino un script o comando encadenado.
3. **Identificación de Procesos:**
   - **Proceso Padre:** `powershell.exe` (Origen de la ejecución).
   - **Procesos Hijos:** `whoami.exe`, `net.exe` y `ipconfig.exe`.
4. **Evidencia Forense:** Gracias a la activación de la "Línea de comandos", se pudo observar el argumento `user` para el binario `net.exe`, confirmando la intención de enumerar cuentas locales.

## Conclusión
Este ejercicio demuestra la importancia de la visibilidad detallada. Sin el registro de la línea de comandos, un analista vería procesos legítimos del sistema y podría pasarlos por alto.
La correlación temporal y el análisis del proceso padre son claves para identificar actividad maliciosa.
