________________________________________
Capítulo 6: Gestión de Software y Paquetes
Laboratorio 6.1: Instalación y Remoción de Software
•	Objetivo: Dominar el ciclo de vida básico de un servicio de red mediante gestores de alto nivel.
•	Tiempo estimado: 15 minutos.
•	Comandos relacionados: apt install, apt remove, apt purge, systemctl.
Desarrollo paso a paso:
1.	Instalación: Instalar el servidor web Nginx. sudo apt update && sudo apt install nginx -y
2.	Verificación de ejecución: Comprobar que el servicio está activo. systemctl status nginx
3.	Remoción simple: Eliminar el binario pero mantener archivos de configuración. sudo apt remove nginx
4.	Limpieza total (Purge): Eliminar configuraciones y dependencias innecesarias. sudo apt purge nginx && sudo apt autoremove
•	Resultado esperado: El comando nginx -v debe devolver "command not found" al finalizar.
________________________________________
Laboratorio 6.2: Actualización del Sistema y Listado
•	Objetivo: Mantener el sistema seguro y conocer qué cambios están pendientes sin aplicarlos.
•	Tiempo estimado: 10 minutos.
•	Comandos relacionados: apt update, apt list --upgradable.
Desarrollo paso a paso:
1.	Sincronización: Actualizar el índice local de paquetes con los repositorios remotos. sudo apt update
2.	Simulación de actualización: Listar qué paquetes tienen versiones nuevas disponibles. apt list --upgradable
3.	Simulación de instalación: Ver qué pasaría si actualizáramos (sin hacerlo realmente). apt upgrade -s
•	Resultado esperado: Una lista detallada de paquetes que requieren actualización, permitiendo al administrador planificar una ventana de mantenimiento.
________________________________________
Laboratorio 6.3: Búsqueda de Dependencias
•	Objetivo: Entender la jerarquía de software y qué librerías requiere un paquete para funcionar.
•	Tiempo estimado: 10 minutos.
•	Comandos relacionados: apt-cache depends, apt-rdepends.
Desarrollo paso a paso:
1.	Consulta de dependencias directas: Verificar qué necesita el paquete vim para instalarse. apt-cache depends vim
2.	Consulta inversa: Ver qué paquetes del sistema dependen de una librería específica (ej. libc6). apt-cache rdepends libc6
3.	Resultado esperado: Identificar que un paquete no es un archivo aislado, sino que depende de librerías compartidas (como las vistas en el Cap 2).
________________________________________
Laboratorio 6.4: Gestión de Repositorios Externos (PPA)
•	Objetivo: Ampliar las fuentes de software para obtener versiones más recientes no disponibles en repositorios oficiales.
•	Tiempo estimado: 15 minutos.
•	Comandos relacionados: add-apt-repository, /etc/apt/sources.list.
Desarrollo paso a paso:
1.	Agregar repositorio: Añadir el PPA oficial de PHP para obtener versiones de desarrollo. sudo add-apt-repository ppa:ondrej/php
2.	Actualizar índices: Tras añadir la fuente, sincronizar de nuevo. sudo apt update
3.	Verificación de origen: Ver de qué repositorio proviene ahora una versión de PHP. apt-cache policy php
•	Resultado esperado: El sistema mostrará múltiples fuentes para el mismo paquete, priorizando la del nuevo repositorio.
________________________________________
Laboratorio 6.5: Instalación de Paquetes Binarios (Bajo Nivel)
•	Objetivo: Instalar software cuando no está en repositorios, manejando archivos locales .deb.
•	Tiempo estimado: 20 minutos.
•	Comandos relacionados: wget, dpkg -i, apt --fix-broken install.
Desarrollo paso a paso:
1.	Descarga manual: Descargar el paquete de una herramienta (ej. gdebi-core). apt download gdebi-core
2.	Instalación con dpkg: Intentar instalar el archivo descargado. sudo dpkg -i gdebi-core_*.deb
3.	Resolución de errores: Si dpkg falla por falta de dependencias (ya que no las descarga solo), usar apt para repararlo. sudo apt install -f
•	Resultado esperado: El software queda instalado correctamente tras gestionar manualmente el binario y sus dependencias.
________________________________________
Resumen de repaso de comandos
Tarea	Debian/Ubuntu (Alto nivel)	Red Hat/CentOS (Alto nivel)
Instalar	apt install	dnf install
Actualizar índices	apt update	dnf check-update
Buscar	apt search	dnf search
Bajo Nivel	dpkg -i paquete.deb	rpm -ivh paquete.rpm

 
