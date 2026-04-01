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
