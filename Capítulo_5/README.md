________________________________________
Capítulo 5: Sistema Operativo Linux
Laboratorio 5.1: Monitoreo de Procesos (Señales)
•	Objetivo: Identificar procesos costosos y aprender a finalizarlos de forma controlada o forzada.
•	Tiempo estimado: 15 minutos.
•	Comandos relacionados: top, htop, kill, pkill.
Desarrollo paso a paso:
1.	Ejecución de monitor: Abrir top (o htop si está instalado).
2.	Identificación: Presionar M (en top) para ordenar por uso de Memoria o P para CPU. Identificar el PID del proceso más alto.
3.	Simulación de proceso: En otra terminal, ejecutar un comando infinito: sleep 1000 &.
4.	Envío de señal SIGTERM (15): Intentar cerrar el proceso amablemente: kill -15 [PID_del_sleep]
5.	Envío de señal SIGKILL (9): Si un proceso no responde, forzar el cierre: kill -9 [PID]
•	Resultado esperado: El alumno debe ver cómo el proceso desaparece de la lista de top tras enviar la señal.
________________________________________
Laboratorio 5.2: Verificación de Logs (Journaling)
•	Objetivo: Navegar por los registros del sistema para auditoría y resolución de problemas.
•	Tiempo estimado: 15 minutos.
•	Comandos relacionados: journalctl, tail, less.
Desarrollo paso a paso:
1.	Lectura de logs en tiempo real: Ejecutar tail -f /var/log/syslog (o /var/log/messages en RHEL) y observar cómo se generan eventos.
2.	Filtrado por arranque: Usar journalctl para ver solo los mensajes desde el último inicio: journalctl -b
3.	Filtrado por prioridad: Ver solo errores críticos: journalctl -p err
4.	Resultado esperado: El alumno identificará servicios que fallaron durante el arranque o advertencias del kernel.
________________________________________
Laboratorio 5.3: Uso de Memoria y Disco
•	Objetivo: Interpretar estadísticas de hardware para prevenir caídas por falta de recursos.
•	Tiempo estimado: 10 minutos.
•	Comandos relacionados: free, df, du.
Desarrollo paso a paso:
1.	Estado de Memoria: Ejecutar free -h y analizar la columna "available" vs "free". Identificar si se está usando la partición SWAP.
2.	Estado de Discos: Ejecutar df -h para ver el porcentaje de ocupación de las particiones montadas.
3.	Localización de archivos pesados: Usar du para ver qué carpeta de /var consume más espacio: sudo du -sh /var/* | sort -h
•	Resultado esperado: Comprensión de la diferencia entre memoria física y virtual, y ocupación de bloques en disco.
________________________________________
Laboratorio 5.4: Compresión y Archivado (Backups)
•	Objetivo: Empaquetar y comprimir datos respetando los permisos de los archivos.
•	Tiempo estimado: 20 minutos.
•	Comandos relacionados: tar, gzip, ls -lh.
Desarrollo paso a paso:
1.	Crear el archivo tar (archivar): sudo tar -cvf backup_etc.tar /etc
2.	Comprimir con gzip: gzip backup_etc.tar
3.	Verificación de reducción de tamaño: Comparar el tamaño de la carpeta original con el .tar.gz: ls -lh backup_etc.tar.gz
4.	Listar contenido sin extraer: tar -tvf backup_etc.tar.gz
•	Resultado esperado: Un único archivo comprimido que contiene toda la configuración del sistema.
________________________________________
Laboratorio 5.5: Programación de Tareas (Crontab)
•	Objetivo: Automatizar procesos repetitivos mediante el demonio cron.
•	Tiempo estimado: 20 minutos.
•	Comandos relacionados: crontab -e, crontab -l, tail.
Desarrollo paso a paso:
1.	Abrir el editor de tareas: crontab -e (elegir el editor preferido si se solicita).
2.	Programar la tarea: Añadir la siguiente línea al final del archivo: */5 * * * * echo "Sistema Activo - $(date)" >> /tmp/monitor.log (Explicar: Minuto, Hora, Día, Mes, Día de la semana).
3.	Guardar y salir.
4.	Verificación: Esperar el ciclo (o ajustar a * * * * * para ver resultados cada minuto) y revisar el log: cat /tmp/monitor.log
•	Resultado esperado: El archivo /tmp/monitor.log se actualizará automáticamente con la frase y la fecha cada 5 minutos.
________________________________________
Resumen de comandos para el examen LPIC-1 (Cap 5):
Categoría	Comando
Procesos	top, kill, ps, uptime
Recursos	free, df, du, iostat
Compresión	tar, gzip, bzip2, xz
Automatización	crontab, at

 

