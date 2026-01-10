# Lab 04: Visibilidad de Procesos y Comandos (Event ID 4688)

## Objetivo
Configurar Windows para obtener telemetría detallada de cada proceso creado en el sistema, incluyendo la línea de comandos ejecutada.

## Desafíos y Troubleshooting (Lo más divertido)
Este laboratorio presentó retos técnicos debido a las limitaciones de la edición Windows Home, los cuales se resolvieron de la siguiente manera:

1. **Error de Localización (auditpol):**
   - **Problema:** Los comandos en inglés (`Logon`, `Process Creation`) devolvían el error `0x00000057`.
   - **Solución:** Se identificó la subcategoría correcta en español o se utilizó la categoría superior `Seguimiento detallado` para activar el sensor.

2. **Falta de Interfaz GPO (secpol.msc):**
   - **Problema:** Al ser una versión Home, no existía la consola de directivas.
   - **Solución:** Se realizó una modificación directa en el **Registro de Windows** (`regedit`) creando la ruta `Policies\System\Audit` y habilitando el valor `ProcessCreationIncludeCmdLine_Output`.

3. **Persistencia de la Política:**
   - Se forzó la actualización de las directivas mediante el comando `gpupdate /force` desde una terminal con privilegios de administrador.

## Evidencias Capturadas
Tras la configuración, se realizaron pruebas de ejecución que generaron los siguientes eventos:

* **Ejecución de Calculadora:** Se capturó el **Event ID 4688** mostrando el binario `calc.exe`.
* **Interacción con PowerShell:** El log registró no solo la apertura de PowerShell, sino también los comandos específicos ingresados.
* **Enumeración de Privilegios:** Se ejecutó `whoami /priv` y el log mostró el argumento `/priv` dentro del campo "Process Command Line".

## Conclusión o lo que aprendí: 
Sin esta configuración, un atacante podría ejecutar scripts maliciosos o comandos de reconocimiento (`net user`, `ipconfig`, etc.) y el SOC solo vería que "se abrió una terminal", pero no qué se hizo en ella. 
Ahora, el sistema es capaz de registrar la **intención** del usuario a través de sus comandos, permitiendo una investigación forense real.
