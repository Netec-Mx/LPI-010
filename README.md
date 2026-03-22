<img src="images/neteclogo (2).png" alt="logo" width="300"/>



# Nombre del curso



## Plataforma de laboratorios



Te damos la bienvenida a la **plataforma de laboratorios** del curso **nombre**. Aquí podrás explorar diferentes tecnologías a través de prácticas guiadas. ¡Desarrolla tus habilidades y lleva tus conocimientos al siguiente nivel!



## Lista de laboratorios



Cada uno de estos laboratorios está diseñado para ofrecerte una experiencia práctica. Haz clic en los enlaces para comenzar.



### [Práctica 1. Nombre de la práctica](CHAPTER_01/ch01-investment-portfolio/README.md) 

  - **Descripción**: xxx.

  - ⏱️ **Duración estimada**: xx min.



### [Práctica 2. Nombre de la práctica](CHAPTER_02/ch02-cashback-schema-design/README.md)

  - **Descripción**: xxx.

  - ⏱️ **Duración estimada**: xx min.



### [Práctica 3. Nombre de la práctica](CHAPTER_03/ch03-cashback-dgs-service/README.md)

  - **Descripción**: xxx.

  - ⏱️**Duración estimada**: xx min.



### [Práctica 3. Nombre de la práctica](CHAPTER_04/ch04-smart-savings-goals/README.md)

  - **Descripción**: xxx.

  - ⏱️**Duración estimada**: xx min.



### [Práctica 3. Nombre de la práctica](CHAPTER_05/ch05-p2p-lending-federation/README.md)

  - **Descripción**: xxx.

  - ⏱️**Duración estimada**: xx min.



### [Práctica 3. Nombre de la práctica](CHAPTER_06/ch06-fraud-detection-subscriptions/README.md)

  - **Descripción**: xxx.

  - ⏱️**Duración estimada**: xx min.



### [Práctica 3. Nombre de la práctica](CHAPTER_07/ch07-expense-analytics-caching/README.md)

  - **Descripción**: xxx.

  - ⏱️**Duración estimada**: xx min.



### [Práctica 3. Nombre de la práctica](CHAPTER_08/ch08-carbon-footprint-governance/README.md)

  - **Descripción**: xxx.

  - ⏱️**Duración estimada**: xx min.



---

________________________________________
Capítulo 1: Introducción a Linux y Software Libre
•	Laboratorio 1.1: Identificación del Sistema: Explorar el archivo /etc/os-release y usar uname -a para determinar la distribución y versión del kernel.
•	Laboratorio 1.2: Comparativa de Licencias: Investigar y listar tres herramientas de software libre instaladas en el sistema y bajo qué licencia operan (GPL, BSD, MIT).
•	Laboratorio 1.3: Navegación por la Ayuda: Utilizar man, info y el parámetro --help para descubrir cómo cambiar la fecha del sistema.
•	Laboratorio 1.4: Exploración del Shell: Identificar qué shell se está utilizando (echo $SHELL) y practicar el uso del historial de comandos (history).
•	Laboratorio 1.5: Interfaz de Usuario: Alternar entre diferentes terminales virtuales (TTY) y ejecutar comandos simples en cada una.
Capítulo 2: Conceptos del Sistema de Archivos y Comandos Básicos
•	Laboratorio 2.1: Estructura Jerárquica: Navegar por /bin, /etc, /var y /home explicando brevemente qué tipo de archivos residen en cada uno.
•	Laboratorio 2.2: Manipulación de Archivos: Crear una estructura de directorios anidados con mkdir -p y realizar copias y movimientos de archivos masivos usando comodines (*, ?).
•	Laboratorio 2.3: Búsqueda Eficiente: Utilizar find para localizar archivos modificados en los últimos 10 minutos y locate para buscar binarios específicos.
•	Laboratorio 2.4: Atajos de Navegación: Practicar el uso de rutas relativas vs. absolutas para moverse entre el directorio personal y archivos de configuración global.
•	Laboratorio 2.5: Enlaces Físicos y Simbólicos: Crear un enlace simbólico a un archivo de configuración y verificar qué sucede si el archivo original se elimina o se mueve.
Capítulo 3: Gestión de Usuarios, Grupos y Permisos
•	Laboratorio 3.1: Creación de Cuentas: Añadir tres usuarios nuevos y asignarlos a un grupo común llamado proyecto_it.
•	Laboratorio 3.2: Permisos Octales y Simbólicos: Modificar permisos de un script para que sea ejecutable solo por el dueño y de lectura para el grupo, usando ambos métodos (chmod 740 y chmod u+x,g+r).
•	Laboratorio 3.3: Colaboración en Directorios: Configurar un directorio compartido donde todos los miembros de un grupo puedan escribir, pero los demás no tengan acceso.
•	Laboratorio 3.4: Cambio de Propiedad: Utilizar chown y chgrp para transferir la propiedad de un archivo de un usuario administrador a un usuario regular.
•	Laboratorio 3.5: Elevación de Privilegios: Configurar un usuario para que pueda ejecutar comandos específicos usando sudo sin necesidad de ser root total.
Capítulo 4: Herramientas de Usuario y Redirección
•	Laboratorio 4.1: Tuberías (Pipes): Listar todos los procesos del sistema y filtrar solo aquellos que pertenezcan a un usuario específico usando grep.
•	Laboratorio 4.2: Redirección de Salida: Guardar la lista de archivos de /etc en un archivo de texto y añadir (append) la fecha actual al final de ese mismo archivo.
•	Laboratorio 4.3: Redirección de Errores: Intentar leer un archivo sin permisos y redirigir el mensaje de error a un archivo llamado errores.log mientras la salida normal va a /dev/null.
•	Laboratorio 4.4: Editor Vi/Vim: Crear un archivo de configuración desde cero, practicar el guardado, la salida sin guardar y la búsqueda de palabras dentro del editor.
•	Laboratorio 4.5: Procesamiento de Texto: Utilizar cut, sort y uniq para extraer y ordenar alfabéticamente los nombres de usuario del archivo /etc/passwd.
Capítulo 5: Sistema Operativo Linux
•	Laboratorio 5.1: Monitoreo de Procesos: Utilizar top o htop para identificar el proceso que consume más memoria y practicar el envío de señales (SIGTERM/SIGKILL).
•	Laboratorio 5.2: Verificación de Logs: Consultar el archivo /var/log/syslog o usar journalctl para identificar eventos ocurridos durante el último arranque.
•	Laboratorio 5.3: Uso de Memoria y Disco: Ejecutar free -h y df -h para analizar el espacio disponible y la memoria swap.
•	Laboratorio 5.4: Compresión y Archivado: Crear un backup del directorio /etc usando tar y comprimirlo con gzip, verificando luego su integridad.
•	Laboratorio 5.5: Programación de Tareas: Crear una tarea sencilla en el crontab que escriba "Sistema Activo" en un log cada 5 minutos.
Capítulo 6: Gestión de Software y Paquetes
•	Laboratorio 6.1: Instalación y Remoción: Instalar un servidor web sencillo (como Nginx o Apache) usando el gestor de paquetes (apt o dnf) y luego eliminarlo completamente.
•	Laboratorio 6.2: Actualización del Sistema: Sincronizar los repositorios y listar qué paquetes tienen actualizaciones pendientes sin instalarlas.
•	Laboratorio 6.3: Búsqueda de Dependencias: Consultar qué paquetes son necesarios para que una herramienta específica funcione antes de instalarla.
•	Laboratorio 6.4: Gestión de Repositorios: Añadir un repositorio externo (PPA o archivo .repo) para instalar una versión más reciente de una herramienta de desarrollo.
•	Laboratorio 6.5: Paquetes Binarios: Descargar un paquete .deb o .rpm manualmente e instalarlo usando herramientas de bajo nivel como dpkg o rpm.
Capítulo 7: Redes Básicas en Linux
•	Laboratorio 7.1: Configuración de Interfaz: Visualizar la dirección IP y la máscara de subred usando ip addr e identificar la interfaz activa.
•	Laboratorio 7.2: Pruebas de Conectividad: Usar ping para verificar la conexión con la puerta de enlace y traceroute para ver los saltos hacia un servidor externo.
•	Laboratorio 7.3: Resolución de Nombres: Utilizar dig o nslookup para encontrar la dirección IP de un dominio y verificar el contenido de /etc/resolv.conf.
•	Laboratorio 7.4: Puertos y Servicios: Usar ss -tulpn o netstat para listar qué puertos están abiertos y qué procesos los están escuchando.
•	Laboratorio 7.5: Transferencia de Archivos: Copiar un archivo de una máquina a otra (o entre directorios simulando red) utilizando scp o sftp.




## 📬 **Contacto y más información**



Si tienes alguna pregunta o necesitas más detalles, no dudes en [contactarnos](mailto:soporte@netec.com). También puedes encontrar más recursos en nuestra [página](https://netec.com).



---



¡Gracias por visitar nuestra plataforma! No olvides revisar todos los laboratorios y comenzar tu viaje de aprendizaje hoy mismo.
