Capítulo 4: Herramientas de Usuario y Redirección
Laboratorio 4.1: Tuberías (Pipes)
•	Objetivo: Combinar comandos independientes para procesar datos en tiempo real.
•	Tiempo estimado: 10 minutos.
•	Comandos relacionados: ps, grep, |.
Desarrollo paso a paso:
1.	Listar procesos: Ejecutar ps aux para ver la cantidad masiva de datos.
2.	Filtrar por usuario: Conectar la salida a grep para buscar solo los procesos del usuario user1 (creado en el lab anterior). ps aux | grep user1
3.	Refinamiento: Filtrar procesos pero excluir la propia línea del comando grep: ps aux | grep user1 | grep -v grep
•	Resultado esperado: Una lista limpia que solo muestra los procesos ejecutados por el usuario específico.
________________________________________
Laboratorio 4.2: Redirección de Salida (> y >>)
•	Objetivo: Aprender a capturar la salida de los comandos en archivos físicos.
•	Tiempo estimado: 10 minutos.
•	Comandos relacionados: ls, date, cat.
Desarrollo paso a paso:
1.	Sobrescribir archivo: Guardar el contenido de /etc en un archivo nuevo. ls /etc > lista_etc.txt
2.	Añadir información (Append): Sin borrar lo anterior, agregar la estampa de tiempo al final. date >> lista_etc.txt
3.	Verificación: Leer las últimas líneas del archivo. tail -n 5 lista_etc.txt
•	Resultado esperado: El archivo contiene la lista de archivos de /etc y, en la última línea, la fecha y hora actual.
________________________________________
Laboratorio 4.3: Redirección de Errores (File Descriptors)
•	Objetivo: Gestionar de forma separada la salida estándar (stdout) y el error estándar (stderr).
•	Tiempo estimado: 15 minutos.
•	Comandos relacionados: find o cat, 2>, >.
Desarrollo paso a paso:
1.	Forzar un error: Intentar leer un archivo protegido (como /etc/shadow) siendo un usuario normal. cat /etc/shadow (Verás el mensaje "Permiso denegado").
2.	Redirigir el error: Enviar el error a un log y "descartar" la salida normal. cat /etc/shadow > /dev/null 2> errores.log
3.	Verificación: Comprobar que la pantalla quedó limpia y el archivo tiene el mensaje. cat errores.log
•	Resultado esperado: La terminal no muestra nada, pero errores.log contiene el texto "cat: /etc/shadow: Permiso denegado".
________________________________________
Laboratorio 4.4: Editor Vi/Vim (Modos de operación)
•	Objetivo: Sobrevivir y dominar las funciones básicas del editor estándar de Linux.
•	Tiempo estimado: 25 minutos.
•	Recursos: Editor vim instalado.
Desarrollo paso a paso:
1.	Crear y entrar: vim configuracion.conf
2.	Modo Inserción: Presionar i, escribir "Puerto=8080" y "Protocolo=TCP". Presionar ESC para volver al modo comando.
3.	Búsqueda: Escribir /Puerto y presionar Enter para saltar a esa palabra.
4.	Guardar y Salir: Escribir :wq y Enter.
5.	Práctica de pánico: Entrar de nuevo, borrar todo con dG y salir sin guardar con :q!.
•	Resultado esperado: El alumno debe ser capaz de editar archivos de configuración sin bloquearse en el editor.
________________________________________
Laboratorio 4.5: Procesamiento de Texto (Filtros)
•	Objetivo: Extraer información específica de bases de datos de texto del sistema.
•	Tiempo estimado: 20 minutos.
•	Comandos relacionados: cut, sort, uniq.
Desarrollo paso a paso:
1.	Extraer la primera columna: El archivo /etc/passwd usa : como delimitador. cut -d: -f1 /etc/passwd
2.	Ordenar alfabéticamente: cut -d: -f1 /etc/passwd | sort
3.	Contar y limpiar (Opcional): Si hubiera duplicados, se usaría uniq. Para este lab, contaremos cuántos usuarios hay: cut -d: -f1 /etc/passwd | sort | wc -l
•	Resultado esperado: Una lista ordenada A-Z de todos los nombres de usuario registrados en el sistema.
________________________________________
 
