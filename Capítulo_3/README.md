________________________________________
Capítulo 3: Gestión de Usuarios, Grupos y Permisos
Laboratorio 3.1: Creación de Cuentas y Grupos
•	Objetivo: Aprender a gestionar el ciclo de vida de usuarios y grupos desde la línea de comandos.
•	Tiempo estimado: 15 minutos.
•	Comandos relacionados: groupadd, useradd, usermod, id, grep.
Desarrollo paso a paso:
1.	Crear el grupo colaborativo: sudo groupadd proyecto_it
2.	Crear tres usuarios nuevos (user1, user2, user3) asignándoles el grupo secundario en un solo paso: sudo useradd -m -G proyecto_it user1 sudo useradd -m -G proyecto_it user2 sudo useradd -m -G proyecto_it user3 (Nota: -m crea el home y -G asigna el grupo suplementario).
3.	Asignar contraseñas (opcional para pruebas de login): sudo passwd user1 (repetir para los demás).
4.	Verificación: id user1 Resultado esperado: El comando debe mostrar el UID del usuario y confirmar que pertenece al GID de proyecto_it.
________________________________________
Laboratorio 3.2: Permisos Octales y Simbólicos
•	Objetivo: Dominar las dos nomenclaturas de chmod para asegurar scripts.
•	Tiempo estimado: 10 minutos.
•	Comandos relacionados: chmod, ls -l, touch.
Desarrollo paso a paso:
1.	Preparar el archivo: touch script_test.sh
2.	Método Simbólico: Configurar: Dueño (ejecución), Grupo (lectura), Otros (nada). chmod u=x,g=r,o= script_test.sh (Verificar con ls -l resultando en --x r-- ---).
3.	Método Octal: Aplicar la misma restricción (740 para dueño total, lectura grupo). chmod 740 script_test.sh
4.	Verificación: ls -l script_test.sh Resultado esperado: La salida debe ser -rwxr-----. El dueño puede leer/escribir/ejecutar, el grupo solo leer.
________________________________________
Laboratorio 3.3: Colaboración en Directorios (Permisos Especiales)
•	Objetivo: Configurar un entorno de trabajo compartido seguro.
•	Tiempo estimado: 20 minutos.
•	Comandos relacionados: mkdir, chgrp, chmod.
Desarrollo paso a paso:
1.	Crear el directorio de trabajo: sudo mkdir /opt/shared_it
2.	Cambiar el grupo propietario al grupo del proyecto: sudo chgrp proyecto_it /opt/shared_it
3.	Configurar permisos de colaboración: sudo chmod 770 /opt/shared_it (Dueño y Grupo: todo; Otros: nada).
4.	Aplicar el SGID (Bit especial): sudo chmod g+s /opt/shared_it (Esto asegura que todo archivo nuevo creado dentro pertenezca automáticamente al grupo proyecto_it).
5.	Resultado esperado: Al crear un archivo dentro como user1, el grupo del archivo será proyecto_it y no el grupo primario del usuario.
________________________________________
Laboratorio 3.4: Cambio de Propiedad
•	Objetivo: Transferir la responsabilidad de archivos entre cuentas.
•	Tiempo estimado: 10 minutos.
•	Comandos relacionados: chown, chgrp, sudo.
Desarrollo paso a paso:
1.	Crear un archivo como root: sudo touch /tmp/reporte_admin.txt
2.	Transferir la propiedad al usuario regular: sudo chown user1 /tmp/reporte_admin.txt
3.	Cambiar el grupo específicamente: sudo chgrp proyecto_it /tmp/reporte_admin.txt
4.	Verificación: ls -l /tmp/reporte_admin.txt Resultado esperado: La tercera y cuarta columna de la salida de ls deben mostrar user1 proyecto_it.
________________________________________
Laboratorio 3.5: Elevación de Privilegios (Sudoers)
•	Objetivo: Delegar poder administrativo limitado (Principio de menor privilegio).
•	Tiempo estimado: 15 minutos.
•	Comandos relacionados: visudo, sudo, whoami.
Desarrollo paso a paso:
1.	Abrir el editor de sudoers de forma segura: sudo visudo
2.	Añadir la regla para user1: (Permitirle reiniciar servicios sin ser root total). Al final del archivo, agregar: user1 ALL=(ALL) /usr/bin/systemctl restart nginx
3.	Probar el comando como user1: sudo -u user1 sudo systemctl restart nginx
4.	Resultado esperado: El sistema permitirá a user1 ejecutar esa línea específica, pero si intenta sudo cat /etc/shadow, recibirá un mensaje de "permiso denegado".
________________________________________
 

