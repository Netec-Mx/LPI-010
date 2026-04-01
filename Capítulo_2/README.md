Laboratorio 1.2: Exploración de Licencias y Software Libre
1. Objetivo del Laboratorio
Al finalizar esta práctica, el estudiante podrá identificar qué programas de su sistema son Software Libre, bajo qué licencias específicas operan (GPL, BSD, MIT, etc.) y comprenderá la diferencia práctica entre "Software Libre" y "Código Abierto" mediante la inspección de paquetes instalados.

2. Tiempo Estimado
20 a 25 minutos.

3. Comandos Relacionados y Recursos
Comandos: dpkg (Debian/Ubuntu), rpm (RHEL/Fedora), ls, grep, less.

Directorios de sistema: /usr/share/doc/, /usr/share/common-licenses/.

Recursos: Acceso a la terminal y, opcionalmente, conexión a internet.

4. Desarrollo del Laboratorio Paso a Paso
Paso 1: Localizar el repositorio de licencias
Las licencias "base" que reconoce el sistema suelen guardarse en un lugar centralizado.

Comando:

Bash

ls /usr/share/common-licenses/
Resultado esperado: Verás una lista de archivos como GPL-3, Apache-2.0, BSD, Artistic, etc. Estos son los textos legales completos.

Paso 2: Identificar la licencia de un comando esencial
Investigaremos el shell bash.

Comando (Debian/Ubuntu):

Bash

cat /usr/share/doc/bash/copyright | less
Comando (RHEL/Fedora):

Bash

rpm -qi bash | grep License
Resultado esperado: El sistema mostrará que bash está bajo la GPLv3. Esto garantiza que el código siempre sea libre.

Paso 3: Investigar una herramienta de red
Busquemos la licencia de curl.

Comando:

Bash

cat /usr/share/doc/curl/copyright | head -n 20
Resultado esperado: Notarás que la licencia es una variante de MIT/X o curl license. No todo el software libre usa la misma licencia.

Paso 4: Listar licencias de múltiples paquetes instalados
Generaremos un reporte de los primeros 15 paquetes.

Comando (Debian/Ubuntu):

Bash

dpkg-query -W -f='${Package}: ${Maintainer}\n' | head -n 15
Comando (RHEL/Fedora):

Bash

rpm -qa --queryformat '%{NAME}: %{LICENSE}\n' | head -n 15
Paso 5: El concepto de "Copyleft" vs "Permisivas"
Busca un paquete con licencia permisiva (ej. openssh-client o util-linux).

Comando sugerido:

Bash

ls /usr/share/doc/
# Luego revisa el archivo copyright de la carpeta elegida
Resultado esperado: Identificar que mientras la GPL (Copyleft) obliga a compartir los cambios, las licencias como BSD o MIT permiten mayor libertad de integración en software propietario.

Resumen para el estudiante: Linux es un ecosistema de miles de autores que comparten su trabajo bajo reglas claras que protegen o flexibilizan su uso.

Laboratorio 1.3: Navegación por la Ayuda y Documentación
1. Objetivo del Laboratorio
El estudiante será capaz de consultar la documentación técnica oficial (man, info, --help), buscar opciones específicas y diferenciar las fuentes de ayuda interna.

2. Tiempo Estimado
15 a 20 minutos.

3. Comandos Relacionados
man, info, --help, whatis, apropos.

4. Desarrollo del Laboratorio Paso a Paso
Paso 1: Búsqueda por palabras clave con apropos
Comando: apropos "copy files"

Resultado esperado: Una lista de comandos relacionados. El número entre paréntesis, ej: cp (1), indica la sección del manual (1 = comandos de usuario).

Paso 2: Uso de la ayuda rápida (--help)
Comando: mkdir --help

Resultado esperado: Una salida corta con las opciones básicas. Identifica la opción para crear directorios anidados (parental).

Paso 3: Exploración profunda con man (Manual)
Comando: man ls

Acción: Presiona /, escribe human-readable y pulsa Enter. El cursor saltará a la opción -h.

Salida: Presiona la tecla q.

Paso 4: Navegación avanzada con info
Comando: info coreutils 'ls invocation'

Acción: Usa las flechas para moverte y H para ver la ayuda de navegación. Presiona q para salir.

Paso 5: Definiciones rápidas con whatis
Comando: whatis rm

Resultado esperado: Una respuesta simple de una sola línea: rm (1) - remove files or directories.

Jerarquía de ayuda para el estudiante:

--help: Ayuda rápida/sintaxis.

man: Estándar de uso detallado.

info: Detalles técnicos profundos y estructurados.

Laboratorio 1.4: Exploración del Shell y Gestión del Historial
1. Objetivo del Laboratorio
Identificar el shell activo, entender variables de entorno básicas y dominar el historial de comandos para optimizar la productividad.

2. Tiempo Estimado
15 a 20 minutos.

3. Comandos y Atajos
Comandos: echo, history, env, type, alias.

Atajos: Tab, Ctrl+R, Flechas.

4. Desarrollo del Laboratorio Paso a Paso
Paso 1: Identificar el Shell activo
Comando: echo $SHELL

Resultado esperado: Una ruta como /bin/bash o /bin/zsh.

Paso 2: Uso del Autocompletado (Tecla Tab)
Acción: Escribe hostn y presiona Tab.

Resultado esperado: El shell completará a hostname. (Tab doble muestra todas las opciones disponibles).

Paso 3: Gestión del Historial de Comandos
Comando: history

Acción avanzada: Escribe !n (donde n es el número de un comando de la lista).

Resultado: El sistema ejecutará automáticamente ese comando previo.

Paso 4: Búsqueda inversa con Ctrl+R
Acción: Presiona Ctrl+R y escribe uname.

Resultado esperado: El shell mostrará el último comando que contenía esa palabra.

Paso 5: Creación de un Alias temporal
Comando: alias ll='ls -lah'

Acción: Ejecuta el nuevo comando escribiendo simplemente ll.

Resultado esperado: Se ejecutará ls -lah (lista detallada, archivos ocultos y tamaños legibles).

Resumen para el estudiante: El Shell es un entorno programable. Dominar el autocompletado (Tab) y la búsqueda en el historial (Ctrl+R) ahorra horas de trabajo a largo plazo.
