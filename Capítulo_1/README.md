## Laboratorio 1.1: Identificación y Exploración del Sistema

## 1. Objetivo del Laboratorio
Al finalizar esta práctica, el estudiante será capaz de identificar la distribución de Linux que está utilizando, la versión del kernel instalada, la arquitectura del hardware y el tiempo que el sistema lleva encendido, utilizando comandos estándar de la terminal.

## 2. Tiempo Estimado
15 a 20 minutos.

## 3. Comandos Relacionados y Recursos
- Comandos: uname, cat, uptime, hostnamectl, clear.
- Archivos de sistema: /etc/os-release, /proc/version.
- Recursos: Una terminal con acceso de usuario estándar (no requiere root para la mayoría de los pasos).
________________________________________

### Desarrollo del Laboratorio Paso a Paso
   
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

# Laboratorio 1.2: Exploración de Licencias y Software Libre

## 1. Objetivo del Laboratorio
Al finalizar esta práctica, el estudiante podrá identificar qué programas de su sistema son Software Libre, bajo qué licencias específicas operan (GPL, BSD, MIT, etc.) y comprenderá la diferencia práctica entre *Software Libre* y *Código Abierto* mediante la inspección de paquetes instalados.

## 2. Tiempo Estimado
20 a 25 minutos.

## 3. Comandos Relacionados y Recursos

- **Comandos:** `dpkg` (Debian/Ubuntu), `rpm` (RHEL/Fedora), `ls`, `grep`, `less`
- **Directorios de sistema:**
  - `/usr/share/doc/`
  - `/usr/share/common-licenses/`
- **Recursos:** Terminal y opcional conexión a internet

---

## 4. Desarrollo del Laboratorio Paso a Paso

### Paso 1: Localizar el repositorio de licencias

```bash
ls /usr/share/common-licenses/
```

**Resultado esperado:**  
Lista de archivos como `GPL-3`, `Apache-2.0`, `BSD`, `Artistic`.

---

### Paso 2: Identificar la licencia de un comando esencial (bash)

**Debian/Ubuntu:**
```bash
cat /usr/share/doc/bash/copyright | less
```

**RHEL/Fedora:**
```bash
rpm -qi bash | grep License
```

**Resultado esperado:**  
Licencia **GPLv3**.

---

### Paso 3: Investigar una herramienta de red (curl)

```bash
cat /usr/share/doc/curl/copyright | head -n 20
```

**Resultado esperado:**  
Licencia tipo **MIT/X o curl license**.

---

### Paso 4: Listar licencias de múltiples paquetes

**Debian/Ubuntu:**
```bash
dpkg-query -W -f='${Package}: ${Maintainer}\n' | head -n 15
```

**RHEL/Fedora:**
```bash
rpm -qa --queryformat '%{NAME}: %{LICENSE}\n' | head -n 15
```

**Resultado esperado:**  
Lista de paquetes con autor o licencia.

---

### Paso 5: Copyleft vs Licencias permisivas

```bash
ls /usr/share/doc/
```

Buscar paquetes como:
- `openssh-client`
- `util-linux`

**Resultado esperado:**  
- GPL → obliga a compartir cambios (Copyleft)  
- BSD/MIT → permiten uso en software propietario  

---

## Resumen para el estudiante

Linux es un ecosistema colaborativo donde miles de autores comparten software bajo distintas licencias con reglas claras.

---

# Laboratorio 1.3: Navegación por la Ayuda y Documentación

## 1. Objetivo del Laboratorio
El estudiante podrá consultar documentación oficial, buscar opciones específicas y diferenciar entre fuentes de ayuda.

## 2. Tiempo Estimado
15 a 20 minutos.

## 3. Comandos Relacionados y Recursos

- **Comandos:** `man`, `info`, `--help`, `whatis`, `apropos`
- **Recurso:** Terminal (sin necesidad de internet)

---

## 4. Desarrollo del Laboratorio Paso a Paso

### Paso 1: Búsqueda con apropos

```bash
apropos "copy files"
```

**Resultado esperado:**  
Lista de comandos como `cp (1)`.

---

### Paso 2: Ayuda rápida

```bash
mkdir --help
```

**Resultado esperado:**  
Opciones básicas del comando.

---

### Paso 3: Manual con man

```bash
man ls
```

Acciones:
- `/human-readable`
- Enter
- `q` para salir

---

### Paso 4: Navegación con info

```bash
info coreutils 'ls invocation'
```

Acciones:
- Flechas para navegar
- `H` para ayuda
- `q` para salir

---

### Paso 5: Descripción rápida

```bash
whatis rm
```

Resultado esperado:
```
rm (1) - remove files or directories
```

---

## Resumen para el estudiante

Jerarquía de ayuda en Linux:

1. `--help` → rápido  
2. `man` → estándar  
3. `info` → detallado  

---

# Laboratorio 1.4: Exploración del Shell y Gestión del Historial

## 1. Objetivo del Laboratorio
El estudiante podrá identificar el shell, entender variables de entorno y usar el historial eficientemente.

## 2. Tiempo Estimado
15 a 20 minutos.

## 3. Comandos Relacionados y Recursos

- **Comandos:** `echo`, `history`, `env`, `type`, `alias`
- **Atajos:**
  - `Tab`
  - `Ctrl + R`
  - Flechas ↑ ↓
- **Recurso:** Terminal Linux (Bash recomendado)

---

## 4. Desarrollo del Laboratorio Paso a Paso

### Paso 1: Identificar el shell

```bash
echo $SHELL
```

**Resultado esperado:**  
Ejemplo: `/bin/bash`

---

### Paso 2: Autocompletado

Acción:
```
hostn + Tab
```

**Resultado esperado:**  
Se completa a `hostname`.

---

### Paso 3: Historial de comandos

```bash
history
```

Ejecutar comando anterior:
```bash
!n
```

---

### Paso 4: Búsqueda inversa

Acción:
```
Ctrl + R
```

Buscar:
```
uname
```

---

### Paso 5: Crear alias

```bash
alias ll='ls -lah'
```

Uso:
```bash
ll
```

---

## Resumen para el estudiante

El shell es un entorno programable.  
El uso de `Tab` y `Ctrl+R` incrementa significativamente la productividad.


---

# Laboratorio 1.5: Interfaz de Usuario y Terminales Virtuales (TTY)

## 1. Objetivo del Laboratorio
Al finalizar esta práctica, el estudiante comprenderá el concepto de TTY (TeleTypewriter), sabrá cómo conmutar entre diferentes consolas virtuales del sistema y entenderá la diferencia entre una sesión de terminal en modo texto y el entorno de escritorio gráfico.

## 2. Tiempo Estimado
15 a 20 minutos.

## 3. Comandos Relacionados y Recursos

- **Comandos:** `tty`, `who`, `w`, `chvt` (opcional)
- **Teclas de acceso rápido:** `Ctrl + Alt + F1` hasta `F7`
- **Recursos:** Máquina física o virtual (puede requerir tecla `Fn`)

---

## 4. Desarrollo del Laboratorio Paso a Paso

### Paso 1: Identificar la terminal actual

```bash
tty
```

**Resultado esperado:**  
- `/dev/pts/0` → pseudo-terminal (entorno gráfico)  
- `/dev/tty1` → terminal en modo texto  

---

### Paso 2: Ver usuarios conectados

```bash
who
```

o

```bash
w
```

**Resultado esperado:**  
Lista de usuarios, terminales y actividad.

---

### Paso 3: Cambiar a una TTY (modo texto)

**Acción:**
```
Ctrl + Alt + F3
```

*(Probar también F4, F5 o F6 si es necesario)*

**Resultado esperado:**  
Pantalla de login tipo:

```
localhost login:
```

---

### Paso 4: Iniciar sesión en la TTY

**Acción:**
- Ingresar usuario y contraseña

```bash
tty
```

**Resultado esperado:**  
Salida como `/dev/tty3`

---

### Paso 5: Regresar al entorno gráfico

**Acción:**
```
Ctrl + Alt + F1
```
o
```
Ctrl + Alt + F2
```

**Resultado esperado:**  
Regreso al entorno gráfico.

---

## Resumen para el estudiante

Si el entorno gráfico falla, se puede acceder a una TTY con `Ctrl + Alt + F3`, iniciar sesión y administrar procesos manualmente. Linux opera en múltiples capas independientes.
