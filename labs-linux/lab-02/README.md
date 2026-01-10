# Laboratorio 02: Superficie de Exposición (Sockets)

### Ejecución
Se analizó el estado de los puertos activos:
`ss -tunlp`

### Hallazgos
Se identificó que al levantar un servidor temporal con Python (`python3 -m http.server 8080`), el sistema abrió un socket en estado **LISTEN** en el puerto 8080.

---

##  Conclusiones
Este laboratorio establece la base de la **"Normalidad"**(Base-Line).Entender cómo se ve un login exitoso y qué puertos deben estar abiertos por defecto me permite identificar anomalías en el futuro.
