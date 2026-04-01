# Laboratorio 2.1: Exploración de la Jerarquía del Sistema (FHS)

## 1. Objetivo del Laboratorio
Al finalizar esta práctica, el estudiante comprenderá la organización estándar del sistema de archivos en Linux (FHS), identificando dónde se guardan los programas, las configuraciones, los archivos temporales y los datos de usuario.

## 2. Tiempo Estimado
20 a 25 minutos.

## 3. Comandos Relacionados y Recursos
- **Comandos:** `cd`, `ls -F`, `pwd`, `file`.
- **Conceptos clave:** Rutas absolutas vs. relativas.
- **Recursos:** Terminal con permisos de usuario estándar.

---

## 4. Desarrollo del Laboratorio Paso a Paso

### Paso 1: Ubicación Inicial y Salto al Raíz
Todo en Linux comienza en la raíz `/`.
- **Comando:** `cd /` y luego `ls -F`
- **Resultado esperado:** Verás una lista de carpetas con una barra diagonal al final (ej: `bin/`, `etc/`, `home/`). El símbolo `/` es el "tronco" del árbol.

### Paso 2: Diferenciar Binarios de Usuario y de Sistema
Históricamente, los comandos se dividían por importancia.
- **Acción:** Explora `/bin` y `/sbin`.
- **Comando:** `ls /bin | head` y luego `ls /sbin | head`
- **Resultado esperado:** En `/bin` verás comandos comunes (`ls`, `cp`). En `/sbin` verás comandos de administración (system binaries) como `fdisk` o `reboot`.

### Paso 3: El Almacén de Configuraciones (`/etc`)
Este es el directorio más importante para un administrador.
- **Comando:** `cd /etc` y luego `ls -d *.conf`
- **Resultado esperado:** Una lista de archivos que terminan en `.conf`. Aquí es donde se "tunea" el comportamiento de Linux y sus servicios.

### Paso 4: Identificar tipos de archivos con `file`
En Linux, la extensión (como `.exe` o `.txt`) no define al archivo.
- **Comando:** `file /bin/ls` y luego `file /etc/passwd`
- **Resultado esperado:** El sistema te dirá que el primero es un "ELF 64-bit executable" (un programa) y el segundo es "ASCII text" (un archivo de texto), independientemente de que no tengan extensión.

### Paso 5: Archivos Variables y Temporales
¿Dónde crecen los archivos (logs) y dónde se borran solos?
- **Acción:** Navega a `/var/log` y luego a `/tmp`.
- **Comando:** `ls /var/log`
- **Resultado esperado:** Verás archivos de registro del sistema. Luego, en `/tmp`, verás archivos que probablemente desaparezcan al reiniciar.

### Paso 6: El Directorio Personal (`~`)
- **Comando:** `cd ~` y luego `pwd`
- **Resultado esperado:** El sistema te llevará a tu "hogar" (ej: `/home/fernando`). Es el único lugar, aparte de `/tmp`, donde un usuario normal tiene permiso total de escritura por defecto.

---

## Resumen para el estudiante:
El alumno debe memorizar este mapa mental:
- **/etc:** Configuración.
- **/bin / /usr/bin:** Programas.
- **/var:** Datos que cambian (logs).
- **/home:** Archivos personales.
- **/root:** El hogar del superusuario (restringido).

---

# Laboratorio 2.2: Manipulación de Archivos y Uso de Comodines

## 1. Objetivo del Laboratorio
Al finalizar esta práctica, el estudiante podrá crear estructuras de directorios multinivel, copiar, mover y renombrar archivos de forma masiva utilizando caracteres comodín (`*`, `?`, `[]`) y entenderá la importancia de la gestión organizada del sistema de archivos.

## 2. Tiempo Estimado
25 a 30 minutos.

## 3. Comandos Relacionados y Recursos
- **Comandos:** `mkdir`, `touch`, `cp`, `mv`, `rm`, `ls`.
- **Comodines:** `*` (todo), `?` (un carácter), `[a-z]` (rangos).
- **Recursos:** Terminal en el directorio personal (`/home/usuario`).

---

## 4. Desarrollo del Laboratorio Paso a Paso

### Paso 1: Crear una estructura de proyecto
Vamos a crear varias carpetas a la vez para organizar un "proyecto ficticio".
- **Comando:** `mkdir -p proyecto/{datos,scripts,backups}`
- **Resultado esperado:** Se crea una carpeta llamada `proyecto` y, dentro de ella, tres subcarpetas. El parámetro `-p` asegura que se creen los niveles intermedios.

### Paso 2: Generación masiva de archivos de prueba
Usaremos una técnica de "expansión de llaves" para crear archivos rápidamente.
- **Comando:** `touch proyecto/datos/archivo{1..10}.txt` y `touch proyecto/datos/nota_{a,b,c}.log`
- **Resultado esperado:** Al hacer `ls proyecto/datos`, verás 13 archivos nuevos creados en un solo segundo.

### Paso 3: Copia selectiva con el comodín `*`
Queremos copiar todos los archivos `.txt` a la carpeta de backups.
- **Comando:** `cp proyecto/datos/*.txt proyecto/backups/`
- **Resultado esperado:** Solo los 10 archivos `.txt` se copiarán; los archivos `.log` se quedarán solo en la carpeta original.

### Paso 4: Movimiento preciso con el comodín `?`
El comodín `?` representa exactamente un carácter. Vamos a mover los archivos de un solo dígito (1 al 9) a una nueva ubicación.
- **Acción:** `mkdir proyecto/datos/un_digito`
- **Comando:** `mv proyecto/datos/archivo?.txt proyecto/datos/un_digito/`
- **Resultado esperado:** Los archivos del 1 al 9 se mueven, pero `archivo10.txt` permanece en su sitio porque tiene dos caracteres después de la palabra "archivo".

### Paso 5: Uso de rangos `[]` y renombrado
Vamos a borrar las notas que no sean importantes usando rangos.
- **Comando:** `rm proyecto/datos/nota_[ab].log`
- **Resultado esperado:** Se eliminarán `nota_a.log` y `nota_b.log`, pero `nota_c.log` sobrevivirá.

### Paso 6: Renombrar directorios
El comando `mv` también sirve para cambiar nombres.
- **Comando:** `mv proyecto/backups proyecto/respaldos_finales`
- **Resultado esperado:** La carpeta cambia de nombre instantáneamente.

---

## Resumen para el estudiante:
El estudiante debe aprender que:
1. `*` es para "cualquier cantidad de caracteres".
2. `?` es para "exactamente un carácter".
3. `touch` no solo crea archivos, sino que actualiza su fecha de acceso.
4. ¡Cuidado! El comando `rm` en Linux no tiene "Papelera de reciclaje"; lo que se borra, se va para siempre.

---

# Laboratorio 2.3: Búsqueda Eficiente de Archivos (Find y Locate)

## 1. Objetivo del Laboratorio
Al finalizar esta práctica, el estudiante podrá localizar archivos en todo el sistema utilizando `locate` (búsqueda en base de datos) y `find` (búsqueda en tiempo real con criterios avanzados como tamaño, tiempo y tipo), entendiendo cuándo es mejor usar cada una.

## 2. Tiempo Estimado
20 a 25 minutos.

## 3. Comandos Relacionados y Recursos
- **Comandos:** `find`, `locate`, `updatedb`, `which`, `whereis`.
- **Recursos:** Terminal estándar. Para el paso de `updatedb`, se requiere acceso a `sudo`.

---

## 4. Desarrollo del Laboratorio Paso a Paso

### Paso 1: Búsqueda instantánea con `locate`
`locate` es extremadamente rápido porque busca en una base de datos, no en el disco directamente.
- **Comando:** `locate passwd`
- **Resultado esperado:** Una lista larga de todos los archivos y rutas que contienen la palabra "passwd".
- **Nota:** Si acabas de crear un archivo y `locate` no lo encuentra, es porque la base de datos no se ha actualizado.

### Paso 2: Actualizar la base de datos de búsqueda
Si el archivo es muy nuevo, debemos forzar al sistema a "indexarlo".
- **Comando:** `sudo updatedb`
- **Resultado esperado:** El comando tardará unos segundos en silencio. Ahora, cualquier archivo nuevo podrá ser encontrado con `locate`.

### Paso 3: Búsqueda en tiempo real con `find` por nombre
`find` es más lento pero mucho más potente. Vamos a buscar en el directorio `/etc`.
- **Comando:** `find /etc -name "*.conf"`
- **Resultado esperado:** Una lista de todos los archivos de configuración en `/etc`. El uso de comillas `""` es importante para que el Shell no intente expandir el asterisco antes de tiempo.

### Paso 4: Búsqueda por tiempo de modificación
Imagina que un archivo de configuración cambió hace poco y no sabes cuál fue.
- **Comando:** `find /etc -mmin -10`
- **Resultado esperado:** Mostrará los archivos en `/etc` que fueron modificados en los últimos 10 minutos. (Si no sale nada, es porque no ha habido cambios recientes).

### Paso 5: Búsqueda por tamaño de archivo
Vamos a buscar archivos grandes en el sistema (mayores a 50MB) para liberar espacio.
- **Comando:** `find /var -size +50M`
- **Resultado esperado:** Una lista de archivos (probablemente logs o bases de datos) que ocupan más de 50 Megabytes.

### Paso 6: Localizar binarios con `which` y `whereis`
¿Dónde está realmente el programa que ejecuto?
- **Comando:** `which ls` y luego `whereis ls`
- **Resultado esperado:** `which` te da la ruta del ejecutable (`/usr/bin/ls`), mientras que `whereis` te da además la ruta del manual y del código fuente si estuviera disponible.

---

## Resumen para el estudiante:
El estudiante debe concluir que:
1. `locate`: Es para búsquedas rápidas por nombre en todo el sistema.
2. `find`: Es para búsquedas quirúrgicas (por tamaño, fecha, permisos, etc.).
3. `which`: Para saber qué versión de un comando se está ejecutando.

---

# Laboratorio 2.4: Atajos de Navegación y Rutas (Absolutas vs. Relativas)

## 1. Objetivo del Laboratorio
Al finalizar esta práctica, el estudiante podrá diferenciar entre rutas absolutas y relativas, y dominará el uso de atajos de navegación (`.`, `..`, `~`, `-`) para desplazarse por el sistema de archivos con el mínimo de pulsaciones de teclado.

## 2. Tiempo Estimado
15 a 20 minutos.

## 3. Comandos Relacionados y Recursos
- **Comandos:** `cd`, `pwd`, `ls`.
- **Símbolos especiales:** `/` (raíz), `.` (directorio actual), `..` (directorio superior), `~` (home), `-` (directorio anterior).
- **Recursos:** Terminal estándar.

---

## 4. Desarrollo del Laboratorio Paso a Paso

### Paso 1: Entender la Ruta Absoluta
Una ruta absoluta siempre empieza desde la raíz `/`. Es como una dirección postal completa.
- **Comando:** `cd /etc/network` (o `/etc/ssh` si la anterior no existe).
- **Verificación:** Ejecuta `pwd`.
- **Resultado esperado:** El sistema muestra la ruta completa desde el origen. No importa dónde estés, este comando siempre te llevará al mismo lugar.

### Paso 2: Entender la Ruta Relativa
Una ruta relativa depende de dónde estés parado "ahora".
- **Acción:** Asegúrate de estar en `/etc`.
- **Comando:** `cd ssh` (sin la barra inicial `/`).
- **Resultado esperado:** Entrarás a `/etc/ssh`.
- **Prueba de error:** Si intentas hacer `cd ssh` desde tu carpeta personal, fallará, porque la ruta relativa busca "hacia adelante" desde tu posición actual.

### Paso 3: Subir niveles con `..`
- **Comando:** `cd ..`
- **Resultado esperado:** Subirás un nivel (si estabas en `/etc/ssh`, ahora estarás en `/etc`).
- **Acción avanzada:** `cd ../..`
- **Resultado:** Subirás dos niveles de golpe.

### Paso 4: El atajo del "Hogar" (`~`)
No importa qué tan profundo estés en el sistema, siempre puedes volver a casa.
- **Comando:** `cd ~` o simplemente `cd`
- **Resultado esperado:** Volverás a `/home/tu_usuario`.

### Paso 5: El "Salto Atrás" (`-`)
Este es el comando "volver" del navegador, pero para la terminal.
- **Acción:** Ve a `/var/log`. Luego ve a `/etc`.
- **Comando:** `cd -`
- **Resultado esperado:** Volverás automáticamente a `/var/log`. Si lo repites, volverás a `/etc`. Es ideal para alternar entre dos carpetas lejanas.

### Paso 6: Referencia al directorio actual (`.`)
- **Comando:** `ls .`
- **Resultado esperado:** Lista el contenido de donde estás. (Útil más adelante para ejecutar scripts locales con `./script.sh`).

---

## Resumen para el estudiante:
El alumno debe integrar estas reglas de oro:
1. Si empieza con `/`, es una **Ruta Absoluta**.
2. Si no empieza con `/`, es una **Ruta Relativa**.
3. `..` es para ir hacia atrás.
4. `cd` (solo) es el botón de "pánico" para volver a casa.

---

# Laboratorio 2.5: Enlaces Físicos (Hard Links) y Simbólicos (Soft Links)

## 1. Objetivos del Laboratorio
- Diferenciar el comportamiento de los enlaces físicos frente a los simbólicos.
- Comprender el papel del Inodo en la estructura del sistema de archivos.
- Analizar qué sucede con los enlaces cuando el archivo original es movido o eliminado.

---

## 2. Preparación del Entorno
Antes de comenzar, los alumnos deben situarse en su directorio personal y crear una carpeta de trabajo:

```bash
mkdir ~/lab_enlaces && cd ~/lab_enlaces
echo "Contenido original del archivo A" > archivoA.txt
