________________________________________
Capítulo 7: Redes Básicas en Linux
Laboratorio 7.1: Configuración de Interfaz
•	Objetivo: Identificar las interfaces de red físicas y lógicas, y entender la asignación de direccionamiento IP.
•	Tiempo estimado: 10 minutos.
•	Comandos relacionados: ip addr, ip link, nmcli (opcional).
Desarrollo paso a paso:
1.	Listar interfaces: Ejecutar ip addr show para ver todas las tarjetas de red.
2.	Identificación: Localizar la interfaz de bucle invertido (lo) y la interfaz principal (usualmente eth0, ens33 o enp0s3).
3.	Análisis de datos: Anotar la dirección IPv4 (marcada como inet), la máscara de subred (en formato CIDR, ej. /24) y la dirección MAC (link/ether).
•	Resultado esperado: El alumno debe identificar claramente cuál es su IP privada actual y confirmar que el estado de la interfaz es UP.
________________________________________
Laboratorio 7.2: Pruebas de Conectividad
•	Objetivo: Diagnosticar la comunicación en la red local y hacia el exterior.
•	Tiempo estimado: 15 minutos.
•	Comandos relacionados: ping, traceroute, ip route.
Desarrollo paso a paso:
1.	Identificar la Puerta de Enlace (Gateway): Ejecutar ip route | grep default para saber a qué IP enviar los paquetes de salida.
2.	Prueba local: Hacer ping -c 4 [IP_Gateway] para verificar la salud del cableado/enlace local.
3.	Traza de ruta: Usar traceroute google.com (o tracepath) para observar los saltos por los que pasa el paquete antes de llegar al destino.
•	Resultado esperado: Confirmar latencias bajas en el primer salto y verificar en qué punto de la red externa se pierden paquetes si hay un fallo.
________________________________________
Laboratorio 7.3: Resolución de Nombres (DNS)
•	Objetivo: Entender cómo el sistema traduce nombres de dominio en direcciones IP.
•	Tiempo estimado: 15 minutos.
•	Comandos relacionados: dig, nslookup, host, cat.
Desarrollo paso a paso:
1.	Consulta directa: Obtener los registros A de un dominio: dig google.com o nslookup google.com
2.	Verificar configuración local: Revisar qué servidores DNS está consultando el sistema: cat /etc/resolv.conf
3.	Análisis de jerarquía: Observar el archivo /etc/hosts para entender que Linux busca nombres localmente antes de preguntar al DNS.
•	Resultado esperado: El alumno comprenderá que sin una entrada válida en resolv.conf, la navegación por nombre fallará aunque el ping a una IP funcione.
________________________________________
Laboratorio 7.4: Puertos y Servicios
•	Objetivo: Auditar qué servicios están "escuchando" conexiones en el servidor.
•	Tiempo estimado: 15 minutos.
•	Comandos relacionados: ss, netstat, lsof.
Desarrollo paso a paso:
1.	Listado de sockets activos: Ejecutar el comando moderno para ver puertos TCP/UDP: ss -tulpn (Explicar: t=tcp, u=udp, l=listen, p=process, n=numeric).
2.	Identificación de servicios: Localizar servicios comunes (ej. puerto 22 para SSH o 80 para HTTP si se instaló en el Cap 6).
3.	Relación Proceso-Puerto: Identificar qué PID (Process ID) es dueño de cada puerto abierto.
•	Resultado esperado: Una lista detallada que permite al administrador saber si hay servicios innecesarios o peligrosos abiertos al exterior.
________________________________________
Laboratorio 7.5: Transferencia de Archivos (Seguridad)
•	Objetivo: Mover datos entre hosts de forma cifrada.
•	Tiempo estimado: 20 minutos.
•	Comandos relacionados: scp, sftp.
Desarrollo paso a paso:
1.	Simulación de red: Si no hay otra VM, se puede practicar hacia el propio localhost.
2.	Copia remota (SCP): Enviar un archivo de prueba al directorio /tmp de otra máquina: scp archivo_prueba.txt usuario@ip_remota:/tmp/
3.	Gestión interactiva (SFTP): Iniciar una sesión para navegar por el sistema remoto: sftp usuario@ip_remota (Dentro de sftp, practicar ls, get para descargar y put para subir).
•	Resultado esperado: El archivo debe aparecer en el destino con los mismos permisos y contenido que el original.
________________________________________
 
