________________________________________
### Laboratorio 1.1: Identificación y Exploración del Sistema
1. Objetivo del Laboratorio
Al finalizar esta práctica, el estudiante será capaz de identificar la distribución de Linux que está utilizando, la versión del kernel instalada, la arquitectura del hardware y el tiempo que el sistema lleva encendido, utilizando comandos estándar de la terminal.

3. Tiempo Estimado
15 a 20 minutos.

## Comandos Relacionados y Recursos
- Comandos: uname, cat, uptime, hostnamectl, clear.
- Archivos de sistema: /etc/os-release, /proc/version.
- Recursos: Una terminal con acceso de usuario estándar (no requiere root para la mayoría de los pasos).
________________________________________

## Desarrollo del Laboratorio Paso a Paso
   
### Paso 1: Limpiar el entorno
Antes de empezar, limpia la pantalla para trabajar con claridad.
-	Comando: clear
-	Resultado esperado: La terminal queda vacía y el cursor se posiciona en la parte superior izquierda.

### Paso 2: Identificar la Distribución
Linux no es un solo sistema, sino muchas distribuciones. Vamos a ver cuál tienes instalada consultando un archivo de texto estándar.
-	Comando: cat /etc/os-release
-	Resultado esperado: Verás varias líneas de texto. Busca las que dicen PRETTY_NAME, ID y VERSION. (Ejemplo: "Ubuntu 24.04 LTS" o "CentOS Stream 9").

### Paso 3: Consultar el Kernel y la Arquitectura
El kernel es el corazón del sistema operativo. Usaremos el comando uname con diferentes modificadores.

-	Comandos: 1. uname -s (Muestra el nombre del kernel: Linux). 2. uname -r (Muestra la versión exacta del kernel). 3. uname -m (Muestra la arquitectura, ej: x86_64). 4. uname -a (Muestra toda la información anterior en una sola línea).
- Resultado esperado: Una cadena de texto similar a Linux 6.x.x-generic x86_64.

### Paso 4: Resumen del Sistema con hostnamectl
Este comando moderno proporciona una vista de "pájaro" del sistema, incluyendo el nombre del equipo y el tipo de virtualización si existe.
-	Comando: hostnamectl
-	Resultado esperado: Una lista organizada que incluye el "Static hostname", "Icon name", "Chassis", "Operating System", "Kernel" y "Architecture".

### Paso 5: Verificar la Disponibilidad (Uptime)
Es útil saber cuánto tiempo ha estado funcionando el servidor sin reiniciarse.
-	Comando: uptime
-	Resultado esperado: Una línea que indica la hora actual, cuánto tiempo lleva encendido (up), cuántos usuarios hay conectados y el promedio de carga del sistema (load average).

### Paso 6: Explorar la versión según el proceso
El kernel también expone su información a través de un sistema de archivos virtual llamado /proc.
-	Comando: cat /proc/version
-	Resultado esperado: Una línea detallada que indica la versión del kernel y la versión de gcc (el compilador) utilizada para crearlo.
________________________________________
________________________________________

### Laboratorio 1.2: Exploración de Licencias y Software Libre
1. Objetivo del Laboratorio
Al finalizar esta práctica, el estudiante podrá identificar qué programas de su sistema son Software Libre, bajo qué licencias específicas operan (GPL, BSD, MIT, etc.) y comprenderá la diferencia práctica entre "Software Libre" y "Código Abierto" mediante la inspección de paquetes instalados.
2. Tiempo Estimado
20 a 25 minutos.
3. Comandos Relacionados y Recursos
•	Comandos: dpkg (en sistemas Debian/Ubuntu) o rpm (en sistemas RHEL/Fedora), ls, grep, less.
•	Directorios de sistema: /usr/share/doc/, /usr/share/common-licenses/.
•	Recursos: Acceso a la terminal y, opcionalmente, una conexión a internet para consultar términos de licencias específicas.
________________________________________
4. Desarrollo del Laboratorio Paso a Paso
Paso 1: Localizar el repositorio de licencias
En Linux, las licencias de los paquetes instalados suelen guardarse en un lugar centralizado. Vamos a explorar qué licencias "base" reconoce tu sistema.
•	Comando: ls /usr/share/common-licenses/
•	Resultado esperado: Verás una lista de archivos como GPL-3, Apache-2.0, BSD, Artistic, etc. Estos son los textos legales completos de las licencias más comunes.
Paso 2: Identificar la licencia de un comando esencial
Vamos a investigar bajo qué licencia se distribuye el shell bash, que es el que estás usando ahora mismo.
•	Comando (Debian/Ubuntu): cat /usr/share/doc/bash/copyright | less
•	Comando (RHEL/Fedora): rpm -qi bash | grep License
•	Resultado esperado: El sistema mostrará que bash está bajo la GPLv3 (GNU General Public License versión 3). Esto garantiza que el código siempre sea libre.
Paso 3: Investigar una herramienta de red
Busquemos la licencia de curl, una herramienta fundamental para transferir datos.
•	Comando: cat /usr/share/doc/curl/copyright | head -n 20
•	Resultado esperado: Notarás que la licencia de curl es diferente (normalmente una variante de MIT/X o curl license). Es un buen momento para observar que no todo el software libre usa la misma licencia.
Paso 4: Listar licencias de múltiples paquetes instalados
Vamos a generar un reporte rápido de las licencias de varios paquetes del sistema para ver la diversidad.
•	Comando (Debian/Ubuntu): dpkg-query -W -f='${Package}: ${Maintainer}\n' | head -n 15
•	Comando (RHEL/Fedora): rpm -qa --queryformat '%{NAME}: %{LICENSE}\n' | head -n 15
•	Resultado esperado: Una lista de programas junto con su autor o licencia. Esto demuestra la naturaleza colaborativa de Linux.
Paso 5: El concepto de "Copyleft" vs "Permisivas"
Busca en el directorio de documentación un paquete que use una licencia permisiva como BSD.
•	Comando sugerido: ls /usr/share/doc/ y busca una carpeta de un servicio como openssh-client o util-linux. Revisa su archivo copyright.
•	Resultado esperado: Identificar las diferencias clave: mientras la GPL (Copyleft) obliga a compartir los cambios, las licencias como BSD o MIT permiten mayor libertad de integración en software propietario.
________________________________________
Resumen para el estudiante:
Al terminar, el alumno debe notar que Linux es un ecosistema de miles de autores que comparten su trabajo bajo reglas claras.
________________________________________
Laboratorio 1.3: Navegación por la Ayuda y Documentación (Man, Info y Help)
1. Objetivo del Laboratorio
Al finalizar esta práctica, el estudiante será capaz de consultar la documentación técnica oficial de cualquier comando, buscar opciones específicas dentro de las páginas de manual y diferenciar entre las distintas fuentes de ayuda interna del sistema.
2. Tiempo Estimado
15 a 20 minutos.
3. Comandos Relacionados y Recursos
•	Comandos: man, info, --help, whatis, apropos.
•	Recursos: Una terminal estándar. No se requiere acceso a internet, ya que la documentación está precargada en el sistema.
________________________________________
4. Desarrollo del Laboratorio Paso a Paso
Paso 1: Búsqueda por palabras clave con apropos
A veces sabemos qué queremos hacer (ej: "copiar"), pero no recordamos el comando.
•	Comando: apropos "copy files"
•	Resultado esperado: Una lista de comandos relacionados con la copia de archivos, donde aparecerá cp (1). El número entre paréntesis indica la sección del manual (1 es para comandos de usuario).
Paso 2: Uso de la ayuda rápida (--help)
Muchos comandos tienen una ayuda integrada muy veloz para recordar la sintaxis.
•	Comando: mkdir --help
•	Resultado esperado: Una salida corta en la terminal que explica las opciones básicas del comando para crear directorios. Busca la opción para crear directorios de forma "parental" o anidada.
Paso 3: Exploración profunda con man (Manual)
Vamos a entrar en el manual del comando ls.
•	Comando: man ls
•	Resultado esperado: Se abrirá una interfaz a pantalla completa.
•	Acción: Presiona la tecla / y escribe human-readable, luego presiona Enter.
•	Resultado: El cursor saltará a la opción -h.
•	Salida: Presiona la tecla q para salir del manual.
Paso 4: Navegación avanzada con info
El comando info ofrece una estructura de hipervínculos más detallada que man.
•	Comando: info coreutils 'ls invocation'
•	Resultado esperado: Una documentación tipo libro con menús.
•	Acción: Usa las flechas para moverte y la tecla H para ver una lista de comandos de navegación dentro de info. Presiona q para salir.
Paso 5: Definiciones rápidas con whatis
Si solo quieres una descripción de una línea sin leer todo el manual.
•	Comando: whatis rm
•	Resultado esperado: Una respuesta simple como: rm (1) - remove files or directories.
________________________________________
Resumen para el estudiante:
El estudiante debe comprender que en Linux la ayuda siempre está presente. La jerarquía suele ser:
1.	--help para algo rápido.
2.	man para el estándar de uso.
3.	info para detalles técnicos profundos.
________________________________________
Laboratorio 1.4: Exploración del Shell y Gestión del Historial
1. Objetivo del Laboratorio
Al finalizar esta práctica, el estudiante podrá identificar el shell que está utilizando, entender el concepto de variables de entorno básicas y dominar el uso del historial de comandos para evitar escribir tareas repetitivas.
2. Tiempo Estimado
15 a 20 minutos.
3. Comandos Relacionados y Recursos
•	Comandos: echo, history, env, type, alias.
•	Teclas de acceso rápido: Tab, Ctrl+R, Flechas Arriba/Abajo.
•	Recursos: Una terminal de Linux (preferiblemente Bash).
________________________________________
4. Desarrollo del Laboratorio Paso a Paso
Paso 1: Identificar el Shell activo
Existen diferentes tipos de shell (sh, bash, zsh, fish). Vamos a confirmar cuál tienes asignado.
•	Comando: echo $SHELL
•	Resultado esperado: Una ruta como /bin/bash o /bin/zsh. El símbolo $ indica que estamos consultando una variable de entorno.
Paso 2: Uso del Autocompletado (La tecla Tab)
El autocompletado es la herramienta de productividad #1 en Linux.
•	Acción: Escribe hostn y presiona la tecla Tab una vez.
•	Resultado esperado: El shell completará automáticamente el comando a hostname. Si presionas Tab dos veces rápidamente, te mostrará todas las opciones que empiezan por esas letras.
Paso 3: Gestión del Historial de Comandos
El sistema recuerda lo que has escrito anteriormente.
•	Comando: history
•	Resultado esperado: Una lista numerada de los últimos comandos ejecutados.
•	Acción avanzada: Escribe !n (donde n es el número de un comando en tu lista de history).
•	Resultado: El shell ejecutará automáticamente ese comando de nuevo.
Paso 4: Búsqueda inversa con Ctrl+R
En lugar de buscar en una lista larga, buscaremos un comando que usamos hace tiempo.
•	Acción: Presiona Ctrl+R y empieza a escribir uname.
•	Resultado esperado: El shell te mostrará el último comando que contenía esa palabra. Presiona Enter para ejecutarlo o las flechas para editarlo.
Paso 5: Creación de un Alias temporal
Los alias son "apodos" para comandos largos o frecuentes.
•	Comando: alias ll='ls -lah'
•	Acción: Ejecuta el nuevo comando escribiendo simplemente ll.
•	Resultado esperado: Se ejecutará ls -lah, que muestra todos los archivos (incluidos ocultos) en formato de lista detallada y con tamaños fáciles de leer.
________________________________________
Resumen para el estudiante:
El estudiante debe notar que el Shell no es solo una línea de comandos, sino un entorno programable. La combinación de Tab para completar y Ctrl+R para buscar en el historial ahorra horas de trabajo a largo plazo.
________________________________________
Laboratorio 1.5: Interfaz de Usuario y Terminales Virtuales (TTY)
1. Objetivo del Laboratorio
Al finalizar esta práctica, el estudiante comprenderá el concepto de TTY (TeleTypewriter), sabrá cómo conmutar entre diferentes consolas virtuales del sistema y entenderá la diferencia entre una sesión de terminal en modo texto y el entorno de escritorio gráfico.
2. Tiempo Estimado
15 a 20 minutos.
3. Comandos Relacionados y Recursos
•	Comandos: tty, who, w, chvt (opcional).
•	Teclas de acceso rápido: Ctrl + Alt + F1 hasta F7.
•	Recursos: Una máquina física con Linux o una máquina virtual (en algunas máquinas virtuales, las teclas de función pueden requerir la tecla Fn).
________________________________________
4. Desarrollo del Laboratorio Paso a Paso
Paso 1: Identificar la terminal actual
Antes de movernos, debemos saber dónde estamos parados.
•	Comando: tty
•	Resultado esperado: Una salida como /dev/pts/0 (esto indica que estás en una "pseudo-terminal" dentro de un entorno gráfico) o /dev/tty1 (si estás en modo texto puro).
Paso 2: Ver quién está conectado
Linux es multiusuario. Vamos a ver cuántas sesiones hay abiertas.
•	Comando: who o simplemente w
•	Resultado esperado: Una lista de usuarios, la terminal que usan y la hora de inicio de sesión. El comando w además te muestra qué están haciendo.
Paso 3: Cambiar a una Terminal Virtual (Modo Texto)
Vamos a salir momentáneamente del entorno gráfico para entrar a una consola pura de comandos.
•	Acción: Presiona simultáneamente Ctrl + Alt + F3. (Si no funciona, intenta con F4, F5 o F6).
•	Resultado esperado: La pantalla se pondrá negra y aparecerá un prompt de login: localhost login:. ¡No te asustes! Has accedido a una TTY diferente.
Paso 4: Iniciar sesión en la TTY
•	Acción: Introduce tu nombre de usuario y contraseña (recuerda que al escribir la contraseña no se verán asteriscos ni puntos por seguridad).
•	Comando una vez dentro: tty
•	Resultado esperado: Ahora la salida será /dev/tty3 (o el número de F que hayas presionado). Estás trabajando directamente sobre el sistema sin intermediarios gráficos.
Paso 5: Regresar al Entorno Gráfico
Normalmente, el entorno gráfico (X11 o Wayland) corre en la TTY1 o TTY2 (o a veces la TTY7 en sistemas antiguos).
•	Acción: Presiona Ctrl + Alt + F2 o Ctrl + Alt + F1.
•	Resultado esperado: Volverás a ver tu escritorio, ventanas y ratón tal como los dejaste.
________________________________________
Resumen para el estudiante:
El estudiante debe aprender que si el entorno gráfico se "congela", siempre puede saltar a una TTY con Ctrl+Alt+F3, iniciar sesión y matar el proceso que causa el problema. Linux es un sistema de múltiples capas.
________________________________________
 

