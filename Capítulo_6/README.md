# Capítulo 6: Gestión de Software y Paquetes
## Objetivos
Al finalizar la práctica, serás capaz de:

6.1 Instalación y Remoción: Dominar el ciclo de vida de las aplicaciones (instalar, desinstalar y purgar) mediante gestores de paquetes de alto nivel.

6.2 Actualización del Sistema: Sincronizar los índices locales con los repositorios remotos y planificar actualizaciones de seguridad sin afectar la estabilidad.

6.3 Gestión de Dependencias: Comprender la jerarquía de librerías compartidas y cómo el sistema resuelve los requisitos de software automáticamente.

6.4 Repositorios Externos (PPA): Ampliar las fuentes de software oficiales para obtener versiones de desarrollo o herramientas no disponibles por defecto.

6.5 Instalación de Bajo Nivel: Gestionar archivos binarios locales (.deb o .rpm) y resolver manualmente conflictos de dependencias mediante dpkg o rpm.
<br/><br/>

## Tiempo estimado
- xxx minutos.
<br/><br/>

## Objetivo visual 

La imagen muestra...
![diagrama1](../images/img1.png)
<br/><br/>

## Tabla de Ayuda

Durante esta práctica...

| Nº | Comando                                               | Descripción                                                                                |Ejemplo de uso               |

| 1  | | | |
<br/><br/>

## Instrucciones 
<br/><br/>
## Laboratorio 6.1: Instalación y Remoción de Software

- **Objetivo**: Dominar el ciclo de vida básico de un servicio de red mediante gestores de alto nivel.
- **Tiempo estimado**: 15 minutos.
- **Comandos relacionados**: `apt install`, `apt remove`, `apt purge`, `systemctl`.

### Desarrollo paso a paso:

1.  **Instalación**: Instalar el servidor web Nginx tras actualizar los índices.
    ```bash
    sudo apt update && sudo apt install nginx -y
    ```
2.  **Verificación de ejecución**: Comprobar que el servicio está activo y corriendo.
    ```bash
    systemctl status nginx
    ```
3.  **Remoción simple**: Eliminar el binario pero mantener los archivos de configuración en el sistema.
    ```bash
    sudo apt remove nginx
    ```
4.  **Limpieza total (Purge)**: Eliminar configuraciones y dependencias que ya no son necesarias.
    ```bash
    sudo apt purge nginx && sudo apt autoremove
    ```

**Resultado esperado**: Al ejecutar `nginx -v`, el sistema debe devolver el mensaje "command not found".

---

## Laboratorio 6.2: Actualización del Sistema y Listado

- **Objetivo**: Mantener el sistema seguro y conocer qué cambios están pendientes sin aplicarlos.
- **Tiempo estimado**: 10 minutos.
- **Comandos relacionados**: `apt update`, `apt list --upgradable`.

### Desarrollo paso a paso:

1.  **Sincronización**: Actualizar el índice local de paquetes consultando los repositorios remotos.
    ```bash
    sudo apt update
    ```
2.  **Simulación de actualización**: Listar qué paquetes tienen versiones nuevas disponibles en los repositorios.
    ```bash
    apt list --upgradable
    ```
3.  **Simulación de instalación**: Ver qué ocurriría si actualizáramos (modo *dry-run*), sin realizar cambios reales.
    ```bash
    apt upgrade -s
    ```

**Resultado esperado**: Una lista detallada de paquetes que requieren actualización, permitiendo planificar una ventana de mantenimiento.

---

## Laboratorio 6.3: Búsqueda de Dependencias

- **Objetivo**: Entender la jerarquía de software y qué librerías requiere un paquete para funcionar correctamente.
- **Tiempo estimado**: 10 minutos.
- **Comandos relacionados**: `apt-cache depends`, `apt-rdepends`.

### Desarrollo paso a paso:

1.  **Consulta de dependencias directas**: Verificar qué componentes necesita el paquete `vim` para instalarse.
    ```bash
    apt-cache depends vim
    ```
2.  **Consulta inversa**: Ver qué otros paquetes instalados en el sistema dependen de una librería específica (ej. `libc6`).
    ```bash
    apt-cache rdepends libc6
    ```

**Resultado esperado**: Identificar que un paquete no es un archivo aislado, sino que depende de múltiples librerías compartidas.

---

## Laboratorio 6.4: Gestión de Repositorios Externos (PPA)

- **Objetivo**: Ampliar las fuentes de software para obtener versiones más recientes no disponibles en los repositorios oficiales.
- **Tiempo estimado**: 15 minutos.
- **Comandos relacionados**: `add-apt-repository`, `/etc/apt/sources.list`.

### Desarrollo paso a paso:

1.  **Agregar repositorio**: Añadir el PPA oficial de PHP para obtener versiones de desarrollo o más recientes.
    ```bash
    sudo add-apt-repository ppa:ondrej/php
    ```
2.  **Actualizar índices**: Sincronizar de nuevo tras haber añadido la nueva fuente.
    ```bash
    sudo apt update
    ```
3.  **Verificación de origen**: Ver de qué repositorio proviene la versión de PHP disponible.
    ```bash
    apt-cache policy php
    ```

**Resultado esperado**: El sistema mostrará múltiples fuentes para el mismo paquete, priorizando generalmente la del nuevo repositorio.

---

## Laboratorio 6.5: Instalación de Paquetes Binarios (Bajo Nivel)

- **Objetivo**: Instalar software cuando no está en repositorios oficiales, manejando archivos locales `.deb`.
- **Tiempo estimado**: 20 minutos.
- **Comandos relacionados**: `wget`, `dpkg -i`, `apt --fix-broken install`.

### Desarrollo paso a paso:

1.  **Descarga manual**: Descargar el paquete de una herramienta (ej. `gdebi-core`).
    ```bash
    apt download gdebi-core
    ```
2.  **Instalación con dpkg**: Intentar instalar el archivo binario descargado manualmente.
    ```bash
    sudo dpkg -i gdebi-core_*.deb
    ```
3.  **Resolución de errores**: Si `dpkg` falla por falta de dependencias, usar `apt` para repararlas automáticamente.
    ```bash
    sudo apt install -f
    ```

**Resultado esperado**: El software queda instalado correctamente tras gestionar manualmente el binario y resolver sus dependencias.

---

## Resumen de repaso de comandos

| Tarea | Debian/Ubuntu (Alto nivel) | Red Hat/CentOS (Alto nivel) |
| :--- | :--- | :--- |
| **Instalar** | `apt install` | `dnf install` |
| **Actualizar índices** | `apt update` | `dnf check-update` |
| **Buscar** | `apt search` | `dnf search` |
| **Bajo Nivel** | `dpkg -i paquete.deb` | `rpm -ivh paquete.rpm` |
