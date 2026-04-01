markdown
# Capítulo 3: Gestión de Usuarios, Grupos y Permisos

## Laboratorio 3.1: Creación de Cuentas y Grupos
- **Objetivo**: Aprender a gestionar el ciclo de vida de usuarios y grupos desde la línea de comandos.
- **Tiempo estimado**: 15 minutos.
- **Comandos relacionados**: `groupadd`, `useradd`, `usermod`, `id`, `grep`.

### Desarrollo paso a paso:
1. Crear el grupo colaborativo:
   ```bash
   sudo groupadd proyecto_it
Crear tres usuarios nuevos (user1, user2, user3) asignándoles el grupo secundario en un solo paso:

bash
sudo useradd -m -G proyecto_it user1
sudo useradd -m -G proyecto_it user2
sudo useradd -m -G proyecto_it user3
Nota: -m crea el home y -G asigna el grupo suplementario.

Asignar contraseñas (opcional para pruebas de login):

bash
sudo passwd user1
(repetir para los demás).

Verificación:

bash
id user1
Resultado esperado: El comando debe mostrar el UID del usuario y confirmar que pertenece al GID de proyecto_it.

Laboratorio 3.2: Permisos Octales y Simbólicos
Objetivo: Dominar las dos nomenclaturas de chmod para asegurar scripts.

Tiempo estimado: 10 minutos.

Comandos relacionados: chmod, ls -l, touch.

Desarrollo paso a paso:
Preparar el archivo:

bash
touch script_test.sh
Método Simbólico: Configurar: Dueño (ejecución), Grupo (lectura), Otros (nada).

bash
chmod u=x,g=r,o= script_test.sh
Verificar con ls -l resultando en --x r-- ---.

Método Octal: Aplicar la misma restricción (740 para dueño total, lectura grupo).

bash
chmod 740 script_test.sh
Verificación:

bash
ls -l script_test.sh
Resultado esperado: La salida debe ser -rwxr-----. El dueño puede leer/escribir/ejecutar, el grupo solo leer.

Laboratorio 3.3: Colaboración en Directorios (Permisos Especiales)
Objetivo: Configurar un entorno de trabajo compartido seguro.

Tiempo estimado: 20 minutos.

Comandos relacionados: mkdir, chgrp, chmod.

Desarrollo paso a paso:
Crear el directorio de trabajo:

bash
sudo mkdir /opt/shared_it
Cambiar el grupo propietario al grupo del proyecto:

bash
sudo chgrp proyecto_it /opt/shared_it
Configurar permisos de colaboración:

bash
sudo chmod 770 /opt/shared_it
(Dueño y Grupo: todo; Otros: nada).

Aplicar el SGID (Bit especial):

bash
sudo chmod g+s /opt/shared_it
Esto asegura que todo archivo nuevo creado dentro pertenezca automáticamente al grupo proyecto_it.

Resultado esperado: Al crear un archivo dentro como user1, el grupo del archivo será proyecto_it y no el grupo primario del usuario.

Laboratorio 3.4: Cambio de Propiedad
Objetivo: Transferir la responsabilidad de archivos entre cuentas.

Tiempo estimado: 10 minutos.

Comandos relacionados: chown, chgrp, sudo.

Desarrollo paso a paso:
Crear un archivo como root:

bash
sudo touch /tmp/reporte_admin.txt
Transferir la propiedad al usuario regular:

bash
sudo chown user1 /tmp/reporte_admin.txt
Cambiar el grupo específicamente:

bash
sudo chgrp proyecto_it /tmp/reporte_admin.txt
Verificación:

bash
ls -l /tmp/reporte_admin.txt
Resultado esperado: La tercera y cuarta columna de la salida de ls deben mostrar user1 proyecto_it.

Laboratorio 3.5: Elevación de Privilegios (Sudoers)
Objetivo: Delegar poder administrativo limitado (Principio de menor privilegio).

Tiempo estimado: 15 minutos.

Comandos relacionados: visudo, sudo, whoami.

Desarrollo paso a paso:
Abrir el editor de sudoers de forma segura:

bash
sudo visudo
Añadir la regla para user1 (permitirle reiniciar servicios sin ser root total). Al final del archivo, agregar:

bash
user1 ALL=(ALL) /usr/bin/systemctl restart nginx
Probar el comando como user1:

bash
sudo -u user1 sudo systemctl restart nginx
Resultado esperado: El sistema permitirá a user1 ejecutar esa línea específica, pero si intenta sudo cat /etc/shadow, recibirá un mensaje de "permiso denegado".

text

Puedes descargar el archivo haciendo clic en el siguiente botón:
Deseo que me pongas todo en UN SOLO ARCHIVO descargable
No puedo generar archivos directamente para descargar, pero puedo ofrecerte el contenido completo en un solo bloque de código Markdown. Solo tienes que copiarlo, pegarlo en un editor de texto y guardarlo con extensión .md.

Aquí está todo el contenido unificado:

markdown
# Capítulo 3: Gestión de Usuarios, Grupos y Permisos

## Laboratorio 3.1: Creación de Cuentas y Grupos
- **Objetivo**: Aprender a gestionar el ciclo de vida de usuarios y grupos desde la línea de comandos.
- **Tiempo estimado**: 15 minutos.
- **Comandos relacionados**: `groupadd`, `useradd`, `usermod`, `id`, `grep`.

### Desarrollo paso a paso:
1. Crear el grupo colaborativo:
   ```bash
   sudo groupadd proyecto_it
Crear tres usuarios nuevos (user1, user2, user3) asignándoles el grupo secundario en un solo paso:

bash
sudo useradd -m -G proyecto_it user1
sudo useradd -m -G proyecto_it user2
sudo useradd -m -G proyecto_it user3
Nota: -m crea el home y -G asigna el grupo suplementario.

Asignar contraseñas (opcional para pruebas de login):

bash
sudo passwd user1
(repetir para los demás).

Verificación:

bash
id user1
Resultado esperado: El comando debe mostrar el UID del usuario y confirmar que pertenece al GID de proyecto_it.

Laboratorio 3.2: Permisos Octales y Simbólicos
Objetivo: Dominar las dos nomenclaturas de chmod para asegurar scripts.

Tiempo estimado: 10 minutos.

Comandos relacionados: chmod, ls -l, touch.

Desarrollo paso a paso:
Preparar el archivo:

bash
touch script_test.sh
Método Simbólico: Configurar: Dueño (ejecución), Grupo (lectura), Otros (nada).

bash
chmod u=x,g=r,o= script_test.sh
Verificar con ls -l resultando en --x r-- ---.

Método Octal: Aplicar la misma restricción (740 para dueño total, lectura grupo).

bash
chmod 740 script_test.sh
Verificación:

bash
ls -l script_test.sh
Resultado esperado: La salida debe ser -rwxr-----. El dueño puede leer/escribir/ejecutar, el grupo solo leer.

Laboratorio 3.3: Colaboración en Directorios (Permisos Especiales)
Objetivo: Configurar un entorno de trabajo compartido seguro.

Tiempo estimado: 20 minutos.

Comandos relacionados: mkdir, chgrp, chmod.

Desarrollo paso a paso:
Crear el directorio de trabajo:

bash
sudo mkdir /opt/shared_it
Cambiar el grupo propietario al grupo del proyecto:

bash
sudo chgrp proyecto_it /opt/shared_it
Configurar permisos de colaboración:

bash
sudo chmod 770 /opt/shared_it
(Dueño y Grupo: todo; Otros: nada).

Aplicar el SGID (Bit especial):

bash
sudo chmod g+s /opt/shared_it
Esto asegura que todo archivo nuevo creado dentro pertenezca automáticamente al grupo proyecto_it.

Resultado esperado: Al crear un archivo dentro como user1, el grupo del archivo será proyecto_it y no el grupo primario del usuario.

Laboratorio 3.4: Cambio de Propiedad
Objetivo: Transferir la responsabilidad de archivos entre cuentas.

Tiempo estimado: 10 minutos.

Comandos relacionados: chown, chgrp, sudo.

Desarrollo paso a paso:
Crear un archivo como root:

bash
sudo touch /tmp/reporte_admin.txt
Transferir la propiedad al usuario regular:

bash
sudo chown user1 /tmp/reporte_admin.txt
Cambiar el grupo específicamente:

bash
sudo chgrp proyecto_it /tmp/reporte_admin.txt
Verificación:

bash
ls -l /tmp/reporte_admin.txt
Resultado esperado: La tercera y cuarta columna de la salida de ls deben mostrar user1 proyecto_it.

Laboratorio 3.5: Elevación de Privilegios (Sudoers)
Objetivo: Delegar poder administrativo limitado (Principio de menor privilegio).

Tiempo estimado: 15 minutos.

Comandos relacionados: visudo, sudo, whoami.

Desarrollo paso a paso:
Abrir el editor de sudoers de forma segura:

bash
sudo visudo
Añadir la regla para user1 (permitirle reiniciar servicios sin ser root total). Al final del archivo, agregar:

bash
user1 ALL=(ALL) /usr/bin/systemctl restart nginx
Probar el comando como user1:

bash
sudo -u user1 sudo systemctl restart nginx
Resultado esperado: El sistema permitirá a user1 ejecutar esa línea específica, pero si intenta sudo cat /etc/shadow, recibirá un mensaje de "permiso denegado".
