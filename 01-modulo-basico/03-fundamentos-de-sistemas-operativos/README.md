# Fundamentos de Sistemas Operativos

> Módulo: Básico · Curso 3 de 9 · Duración estimada: 10-15 horas · Estado: ✅ Completo

## Objetivo

Todo lo que vas a operar en esta ruta corre sobre un sistema operativo: los servidores Windows y Linux, las máquinas virtuales de Azure, los contenedores de Docker (que comparten el kernel de Linux del host), los nodos de Kubernetes. Cuando un servicio "no arranca", un proceso "se come la CPU", un disco "se llena" o un usuario "no tiene permisos", estás ante un problema de sistema operativo.

Este curso explica **qué hace un sistema operativo, cómo se sitúa entre el hardware y las aplicaciones, y qué conceptos comparten Windows y Linux** aunque los llamen de forma distinta: kernel, procesos, hilos, memoria, sistema de archivos, usuarios, grupos, permisos, servicios y drivers. También introduce la virtualización, porque vas a crear tu primera máquina virtual.

La idea es que, al terminar, puedas abrir cualquier equipo Windows o Linux y responder cuatro preguntas: qué está ejecutándose, cuánta memoria y disco se usa, qué servicios hay y quién puede hacer qué. Los cursos siguientes (Windows Básico y Linux Básico) profundizan en cada sistema; este pone los cimientos comunes.

**Antes de empezar** necesitas los dos cursos anteriores (saber qué es la CPU, la RAM y el disco) y un equipo en el que puedas instalar software de virtualización.

### Al terminar este curso deberías poder

- Explicar qué es un sistema operativo y qué es el kernel, y qué diferencia hay entre ambos.
- Explicar qué es un proceso, qué es un hilo y cómo el sistema operativo reparte la CPU entre muchos procesos.
- Explicar cómo gestiona la memoria un sistema operativo (memoria física, memoria virtual, swap/archivo de paginación) a nivel conceptual.
- Explicar qué es un sistema de archivos y qué hace (nombres, directorios, permisos, metadatos), y nombrar los más comunes en Windows y Linux.
- Explicar el modelo de usuarios, grupos y permisos y por qué existe.
- Explicar qué es un servicio (daemon) y en qué se diferencia de una aplicación normal.
- Explicar qué es un driver y por qué el sistema operativo los necesita.
- Distinguir CLI de GUI y explicar por qué en servidores y en la nube domina la CLI.
- Crear una máquina virtual Linux en tu equipo y explicar qué es un hipervisor.
- Inspeccionar procesos, memoria, almacenamiento, servicios y permisos tanto en Windows como en Linux con herramientas básicas.

## Prerrequisitos

- Curso 1: Historia de la Computación (sabes qué es Unix y de dónde vienen Windows y Linux).
- Curso 2: Fundamentos de Hardware (sabes qué son CPU, núcleos, RAM, disco).
- Un equipo con al menos 8 GB de RAM y 30 GB de disco libre, con permisos de administrador para instalar VirtualBox (o Hyper-V/UTM). Si no cumples esto, avisa al mentor antes de empezar el laboratorio.

## Temario

- Qué es un sistema operativo.
- Kernel.
- Procesos.
- Threads.
- Memoria.
- Sistema de archivos.
- Usuarios.
- Grupos.
- Permisos.
- Servicios.
- Drivers.
- Aplicaciones.
- CLI frente a GUI.
- Windows frente a Linux.
- Conceptos básicos de virtualización.

## Recursos en español

### Sistemas Operativos (material de clase) — OCW Universidad Carlos III de Madrid
- **URL:** https://ocw.uc3m.es/course/view.php?id=228 · Material de clase: https://ocw.uc3m.es/mod/page/view.php?id=2793
- **Autor / organización:** Universidad Carlos III de Madrid, OpenCourseWare
- **Idioma:** Español
- **Tipo:** Apuntes y transparencias universitarias
- **Duración aproximada:** 2-3 h de lectura selectiva (solo los temas de introducción, procesos e hilos, gestión de memoria y sistemas de archivos)
- **Cubre:** Qué es un SO, kernel, procesos, threads, memoria, sistema de archivos.
- **Nivel:** Introductorio-intermedio (es material de grado universitario; lee solo las partes conceptuales, salta el código en C)
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es el material en español más riguroso y gratuito sobre los conceptos del curso. No hace falta hacer el curso universitario completo: usa las transparencias de introducción, procesos, memoria y archivos como texto de referencia.

### Sistemas Operativos (curso y apuntes) — OCW Universidad de La Laguna
- **URL:** https://campusvirtual.ull.es/ocw/course/view.php?id=105
- **Autor / organización:** Universidad de La Laguna, OpenCourseWare
- **Idioma:** Español
- **Tipo:** Apuntes en PDF y material de curso
- **Duración aproximada:** 1-2 h de lectura selectiva
- **Cubre:** Servicios que ofrece un SO, procesos, hilos, memoria, archivos.
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Alternativa a UC3M si prefieres apuntes en formato texto continuo (PDF). Elige uno de los dos OCW, no hagas los dos.

### Los sistemas operativos, ¿qué son? — Universitat Politècnica de València (Polimedia)
- **URL:** http://www.upv.es/visor/media/83b764f2-1f92-744b-a65d-718739636dd4/c
- **Autor / organización:** Universitat Politècnica de València
- **Idioma:** Español
- **Tipo:** Vídeo docente corto
- **Duración aproximada:** 10 min
- **Cubre:** Qué es un sistema operativo, funciones principales.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Vídeo universitario, breve y correcto para arrancar el curso en español. Los vídeos Polimedia de la UPV son de docencia real, sin publicidad.

### Virtualización con Hyper-V en Windows Server y Windows — Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/windows-server/virtualization/hyper-v/overview
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Documentación oficial
- **Duración aproximada:** 15 min
- **Cubre:** Conceptos básicos de virtualización (hipervisor, máquinas virtuales) desde el punto de vista de Microsoft.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Explica qué es un hipervisor con el producto que trae Windows de serie (Hyper-V, disponible en Windows 10/11 Pro). Es el mismo motor que usa Azure por debajo, así que lo que aprendes aquí lo verás en el curso 8.

## Recursos en inglés

### Operating Systems: Crash Course Computer Science #18 (y episodios 19-20) — CrashCourse / PBS
- **URL:** https://www.youtube.com/watch?v=26QPDBe-NB8
- **Autor / organización:** CrashCourse (PBS Digital Studios)
- **Idioma:** Inglés (subtítulos)
- **Tipo:** Vídeo
- **Duración aproximada:** 13 min (ep. 18); los episodios 19 "Memory & Storage" y 20 "Files & File Systems" añaden ~25 min y están en la misma serie en el canal CrashCourse
- **Cubre:** Qué es un SO, kernel, multitarea, procesos, memoria virtual, historia Unix/DOS; memoria y almacenamiento; sistemas de archivos.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** En 13 minutos explica qué problema resuelve un sistema operativo y por qué existe la multitarea y la memoria virtual. Es el mejor punto de partida en inglés.

### Operating Systems: Three Easy Pieces (OSTEP) — Remzi y Andrea Arpaci-Dusseau, University of Wisconsin
- **URL:** https://pages.cs.wisc.edu/~remzi/OSTEP/
- **Autor / organización:** Remzi H. Arpaci-Dusseau y Andrea C. Arpaci-Dusseau (University of Wisconsin-Madison)
- **Idioma:** Inglés
- **Tipo:** Libro de texto universitario, gratuito en PDF por capítulos
- **Duración aproximada:** 2-3 h para los capítulos recomendados: 2 (Introduction to Operating Systems), 4 (The Abstraction: The Process), 13 (The Abstraction: Address Spaces), 39 (Interlude: Files and Directories)
- **Cubre:** Kernel, procesos, memoria, sistema de archivos, en profundidad.
- **Nivel:** Intermedio (es un libro universitario, pero los capítulos indicados son conceptuales y muy bien escritos)
- **Acceso:** Libre (el PDF es y será siempre gratuito; existe versión impresa de pago, no necesaria)
- **Por qué lo recomiendo:** Es el libro de sistemas operativos más usado en universidades de todo el mundo y es gratuito. Los cuatro capítulos indicados dan la base conceptual que te servirá durante toda la carrera. Si el inglés te cuesta, léelos con calma y con un diccionario: merece la pena.

### What is the Linux kernel? y What is virtualization? — Red Hat
- **URL:** https://www.redhat.com/en/topics/linux/what-is-the-linux-kernel · https://www.redhat.com/en/topics/virtualization/what-is-virtualization
- **Autor / organización:** Red Hat
- **Idioma:** Inglés
- **Tipo:** Artículos explicativos
- **Duración aproximada:** 10 min cada uno
- **Cubre:** Kernel (gestión de memoria, procesos, drivers, llamadas al sistema); virtualización e hipervisores.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Red Hat es el segundo mayor contribuidor al kernel de Linux; sus explicaciones son cortas, correctas y orientadas a quien va a administrar sistemas. El artículo del kernel resume sus "cuatro trabajos" en una página.

### How to run an Ubuntu Desktop virtual machine using VirtualBox 7 — Ubuntu (Canonical)
- **URL:** https://ubuntu.com/tutorials/how-to-run-ubuntu-desktop-on-a-virtual-machine-using-virtualbox
- **Autor / organización:** Canonical (Ubuntu)
- **Idioma:** Inglés
- **Tipo:** Tutorial oficial paso a paso
- **Duración aproximada:** 30-45 min (incluida la instalación)
- **Cubre:** Conceptos básicos de virtualización llevados a la práctica: crear una VM e instalar Linux.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es el tutorial oficial de Ubuntu para exactamente lo que harás en el laboratorio. Las capturas pueden ir una versión por detrás de la última Ubuntu, pero los pasos son los mismos.

### Process Explorer — Microsoft Learn (Sysinternals)
- **URL:** https://learn.microsoft.com/en-us/sysinternals/downloads/process-explorer
- **Autor / organización:** Microsoft (Sysinternals, Mark Russinovich)
- **Idioma:** Inglés
- **Tipo:** Documentación oficial de herramienta gratuita
- **Duración aproximada:** 15 min de lectura + uso en el laboratorio
- **Cubre:** Procesos, hilos, memoria y árbol de procesos en Windows.
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre (la herramienta es gratuita, sin instalación)
- **Por qué lo recomiendo:** Es el "Administrador de tareas avanzado" que usan los administradores de Windows. Te permite ver el árbol de procesos padre-hijo, los hilos y la memoria de cada proceso, que es exactamente lo que el curso explica en teoría.

### Linux man pages online — man7.org
- **URL:** https://man7.org/linux/man-pages/ · Páginas usadas en el laboratorio: `ps` https://man7.org/linux/man-pages/man1/ps.1.html · `free` https://man7.org/linux/man-pages/man1/free.1.html · `df` https://man7.org/linux/man-pages/man1/df.1.html
- **Autor / organización:** Michael Kerrisk (mantenedor del proyecto Linux man-pages)
- **Idioma:** Inglés
- **Tipo:** Documentación oficial (páginas de manual)
- **Duración aproximada:** Consulta puntual
- **Cubre:** Referencia de comandos para procesos, memoria y almacenamiento.
- **Nivel:** Todos
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la documentación oficial de los comandos de Linux, la misma que obtienes con `man ps` en la terminal. Acostumbrarte a consultarla ahora te ahorrará muchas búsquedas después.

## Documentación oficial

- **Linux — The Linux Kernel documentation:** https://docs.kernel.org/ (referencia; por ahora basta saber que existe y ojear el índice).
- **Linux — man pages:** https://man7.org/linux/man-pages/ (y `man <comando>` en tu VM).
- **Windows — Documentación del cliente Windows:** https://learn.microsoft.com/es-es/windows/resources/ (punto de entrada a la documentación de Windows para profesionales de TI).
- **Windows — Sysinternals:** https://learn.microsoft.com/en-us/sysinternals/ (herramientas oficiales gratuitas de diagnóstico).
- **Windows — Hyper-V:** https://learn.microsoft.com/es-es/windows-server/virtualization/hyper-v/overview
- **Ubuntu — Tutorial oficial de VM con VirtualBox:** https://ubuntu.com/tutorials/how-to-run-ubuntu-desktop-on-a-virtual-machine-using-virtualbox

## Ruta recomendada de estudio

1. **Ver** el vídeo de la UPV "Los sistemas operativos, ¿qué son?" (10 min) y después Crash Course #18 "Operating Systems" (13 min). Ya tienes el mapa: el SO es un programa con privilegios especiales que gestiona hardware y ejecuta otros programas.
2. **Leer** el artículo de Red Hat "What is the Linux kernel?" (10 min). Apunta los cuatro trabajos del kernel: memoria, procesos, drivers, llamadas al sistema y seguridad.
3. **Leer** OSTEP capítulo 2 (Introduction) y capítulo 4 (The Process) (60-90 min). Es la parte más teórica del curso; tómate tu tiempo. Objetivo: entender qué es un proceso, qué estados tiene y cómo el SO "virtualiza" la CPU para que muchos procesos parezcan correr a la vez.
4. **Ver** Crash Course #19 "Memory & Storage" y **leer** OSTEP capítulo 13 (Address Spaces) (45 min). Objetivo: entender la diferencia entre memoria física y memoria virtual, y qué es el swap.
5. **Ver** Crash Course #20 "Files & File Systems" y **leer** OSTEP capítulo 39 (Files and Directories) (60 min). Objetivo: qué es un sistema de archivos, qué son los permisos y por qué existen usuarios y grupos.
6. **Leer** las transparencias de introducción, procesos y memoria del OCW de la UC3M (o los apuntes de la ULL) para tener el vocabulario en español (60-90 min). Compara los términos: kernel/núcleo, process/proceso, thread/hilo, file system/sistema de archivos, service/servicio o demonio.
7. **Leer** Red Hat "What is virtualization?" y la página de Hyper-V de Microsoft Learn (25 min). Objetivo: qué es un hipervisor y qué diferencia hay entre virtualizar y emular.
8. **Hacer el laboratorio** (4-6 h, repartidas en dos o tres sesiones). La parte B incluye instalar tu primera VM Linux siguiendo el tutorial oficial de Ubuntu.
9. **Responder la evaluación** y **revisar el checklist**.

## Laboratorio

### Objetivo

Inspeccionar un sistema operativo Windows (o macOS) y un sistema operativo Linux "desde dentro": procesos, hilos, memoria, almacenamiento, servicios, usuarios y permisos. Crear la primera máquina virtual Linux, que reutilizarás en el curso de Linux Básico. Resolver un problema sencillo (un proceso que consume toda la CPU).

### Requisitos

- Equipo anfitrión Windows 10/11, macOS o Linux con 8 GB de RAM (mínimo) y 30 GB libres.
- Software de virtualización:
  - **Windows / Linux / macOS con Intel:** VirtualBox 7 (gratuito): https://www.virtualbox.org/
  - **Windows 10/11 Pro/Enterprise:** alternativamente Hyper-V (incluido en Windows).
  - **macOS con Apple Silicon (M1/M2/M3/M4):** UTM (gratuito) con una imagen de Ubuntu Server para ARM64. VirtualBox no funciona bien en Apple Silicon.
- Imagen ISO de **Ubuntu Desktop LTS** (versión LTS más reciente) descargada de https://ubuntu.com/download/desktop. Si tu equipo es justo de recursos, usa **Ubuntu Server LTS** (sin escritorio, solo terminal), que consume mucho menos.
- Tiempo: 4-6 h.

### Instrucciones

**Parte A — Radiografía del anfitrión (60-90 min)**

Crea `radiografia-so.md`. En tu equipo anfitrión:

1. **Procesos e hilos.** Abre el Administrador de tareas (Windows: `Ctrl+Shift+Esc`, pestaña Detalles; activa las columnas "Subprocesos" y "PID") o el Monitor de Actividad (macOS). Anota: cuántos procesos hay en total, cuál usa más memoria, cuál más CPU, y cuántos hilos tiene el proceso de tu navegador. En Windows, descarga Process Explorer (sin instalación) y muestra el **árbol de procesos** de tu navegador: qué proceso es el padre y cuántos hijos tiene. Captura.
2. **Memoria.** En la pestaña Rendimiento → Memoria: anota memoria total, en uso, disponible y el tamaño del archivo de paginación / memoria comprimida. Explica con tus palabras qué es la memoria "en uso" frente a "comprometida" o "caché".
3. **Almacenamiento y sistema de archivos.** Anota los discos/volúmenes, su sistema de archivos (NTFS, APFS, ext4...), capacidad y espacio libre. Windows: Administración de discos o `Get-Volume` en PowerShell. macOS: Utilidad de Discos o `diskutil list`.
4. **Servicios.** Windows: abre `services.msc`, cuenta cuántos servicios están "En ejecución" y elige tres (por ejemplo, Windows Update, Spooler de impresión, DHCP Client). Para cada uno escribe: qué hace, con qué cuenta se ejecuta y qué tipo de inicio tiene. macOS: `launchctl list | head -30` y elige tres.
5. **Usuarios, grupos y permisos.** Windows: `whoami /groups` en CMD, y en el Explorador mira los permisos (Propiedades → Seguridad) de `C:\Windows\System32` y de una carpeta de tu perfil de usuario. Anota quién puede escribir en cada una. macOS/Linux: `id` y `ls -ld /usr/bin ~/Documents`.
6. **Drivers.** Windows: Administrador de dispositivos; localiza tu tarjeta de red y anota el proveedor y la versión del driver. macOS: Informe del sistema → Extensiones. Explica en dos líneas para qué necesita el SO ese driver.

**Parte B — Tu primera máquina virtual Linux (90-120 min)**

7. Instala VirtualBox (o Hyper-V/UTM) y crea una VM siguiendo el tutorial oficial de Ubuntu. Configuración recomendada: 2 vCPU, 4 GB de RAM (2 GB si usas Ubuntu Server), 25 GB de disco dinámico. Usuario: tu nombre. Nombre de la máquina: `lab-so`.
8. Una vez dentro de Ubuntu, abre una terminal y ejecuta y **captura** cada bloque, explicando debajo con tus palabras qué muestra cada comando (consulta `man` o man7.org cuando no lo entiendas):
   ```bash
   uname -a                      # kernel: nombre, versión, arquitectura
   cat /etc/os-release           # distribución
   ps -e --forest | head -40     # árbol de procesos
   ps -eo pid,ppid,user,nlwp,%cpu,%mem,comm --sort=-%mem | head -15   # top 15 por memoria, con número de hilos (nlwp)
   free -h                       # memoria y swap
   df -hT                        # sistemas de archivos montados, tipo y uso
   lsblk                         # discos y particiones
   systemctl list-units --type=service --state=running | head -30      # servicios en ejecución
   systemctl status ssh 2>/dev/null || systemctl status systemd-resolved   # detalle de un servicio
   id                            # tu usuario y grupos
   ls -ld / /etc /home/$USER /root   # permisos de directorios clave
   ls -l /etc/passwd /etc/shadow      # ¿quién puede leer las contraseñas?
   lsmod | head -15              # módulos del kernel (drivers) cargados
   ```
9. Responde en el documento: ¿qué proceso tiene PID 1 y qué hace? ¿Cuánta swap hay y por qué puede ser 0 en una VM recién instalada? ¿Qué sistema de archivos usa la raíz `/`? ¿Por qué `/etc/shadow` no es legible por tu usuario y `/etc/passwd` sí?

**Parte C — Mini troubleshooting: un proceso descontrolado (30 min)**

10. En la VM Linux, en una terminal, lanza un proceso que consuma CPU sin parar:
    ```bash
    yes > /dev/null &
    ```
11. En **otra** terminal, encuéntralo con `top` (o `htop` si lo instalas con `sudo apt install htop`): identifica el PID, el porcentaje de CPU, el usuario y el estado. Captura.
12. Mátalo primero de forma "educada" y luego comprueba que ha muerto:
    ```bash
    kill <PID>
    ps -p <PID>
    ```
    Si no muriera, usa `kill -9 <PID>` y explica la diferencia entre ambas señales (busca `SIGTERM` y `SIGKILL` en `man 7 signal`).
13. Repite el ejercicio en el anfitrión Windows: abre un navegador con 10-15 pestañas de vídeo, localiza en el Administrador de tareas o Process Explorer el proceso que más CPU consume y termínalo desde ahí ("Finalizar tarea"). Captura y explica qué diferencia hay entre finalizar el proceso padre del navegador y uno de sus hijos.

**Parte D — Windows frente a Linux (30 min)**

14. Completa esta tabla de equivalencias con lo que has visto (añade al menos 3 filas propias):

    | Concepto | Windows | Linux |
    |---|---|---|
    | Ver procesos | Administrador de tareas / Process Explorer / `tasklist` | `ps`, `top`, `htop` |
    | Ver memoria | | |
    | Ver discos y sistema de archivos | | |
    | Listar servicios | | |
    | Detalle de un servicio | | |
    | Usuario actual y grupos | | |
    | Permisos de un archivo/directorio | | |
    | Terminar un proceso | | |
    | Drivers cargados | | |
    | Sistema de archivos habitual | | |
    | Usuario administrador | | |
    | Shell / terminal | | |

15. Escribe 150-250 palabras respondiendo: ¿por qué en servidores y en la nube se administra casi todo por CLI y no por GUI? Da al menos tres razones basadas en lo que has hecho en el laboratorio.

### Resultado esperado

- Una VM Ubuntu funcional llamada `lab-so` (la usarás en el curso 5).
- `radiografia-so.md` con las cuatro partes, capturas y explicaciones propias.

### Criterios de validación

- [ ] Parte A: hay datos reales del anfitrión (procesos, hilos, memoria, discos, 3 servicios, permisos de dos carpetas, un driver), con capturas donde se vea el nombre del equipo o del usuario.
- [ ] Parte B: la VM existe, todos los comandos están ejecutados y capturados, y cada uno tiene una explicación propia y correcta. Las cuatro preguntas están respondidas correctamente (PID 1 = systemd/init; motivo de swap 0; tipo de FS; permisos de `/etc/shadow`).
- [ ] Parte C: se identificó el PID correcto, se terminó el proceso y se explica correctamente la diferencia entre `SIGTERM` y `SIGKILL` y entre padre e hijos en Windows.
- [ ] Parte D: la tabla está completa y correcta, y el texto sobre CLI da tres razones fundamentadas.
- [ ] El estudiante puede, si se le pide en una llamada, abrir la VM y localizar un proceso por nombre y ver su memoria sin buscar los comandos.

## Entrega

En tu repositorio de entregas, carpeta `01-modulo-basico/03-fundamentos-de-sistemas-operativos/`:

1. `radiografia-so.md` con las partes A, B, C y D.
2. Carpeta `capturas/` con todas las imágenes.
3. `ENTREGA.md` con la evaluación, el checklist y la declaración de uso de IA.

Las explicaciones de cada comando deben ser tuyas. Copiar la descripción de la página `man` no cuenta como explicación.

## Evaluación

1. **Conceptual.** ¿Qué diferencia hay entre "sistema operativo" y "kernel"? Da un ejemplo de algo que forma parte del sistema operativo pero no del kernel.
2. **Conceptual.** Explica qué es un proceso y qué es un hilo. ¿Por qué un navegador moderno usa muchos procesos en vez de uno solo con muchos hilos? Relaciónalo con lo que viste en el árbol de procesos.
3. **Conceptual.** Tu VM tiene 4 GB de RAM y ves 40 procesos que, sumados, "usan" más de 4 GB según la columna de memoria virtual. ¿Cómo es posible? Explica memoria física, memoria virtual y swap.
4. **Situacional.** Un servidor Linux muestra `free -h` con casi toda la memoria en "used" pero mucha en "buff/cache" y el sistema va bien. Un compañero quiere añadir RAM urgentemente. ¿Qué le explicas?
5. **Técnica.** ¿Qué hace el proceso con PID 1 en Linux y por qué es especial? ¿Qué pasa si muere?
6. **Conceptual.** ¿Para qué sirve un sistema de archivos además de "guardar archivos"? Nombra dos sistemas de archivos de Windows y dos de Linux y una diferencia entre NTFS y ext4.
7. **Situacional.** Un usuario dice que "no puede guardar un archivo en `C:\Program Files\MiApp\config.ini`" y otro dice que "no puede leer `/etc/shadow`". Explica ambos casos con el modelo de usuarios, grupos y permisos, y di si son errores o comportamientos correctos.
8. **Conceptual.** ¿Qué es un servicio (o demonio) y en qué se diferencia de una aplicación que abres tú? ¿Por qué el servidor web de una empresa debe ser un servicio y no una aplicación abierta en el escritorio de alguien?
9. **Troubleshooting.** Un proceso en Linux no muere con `kill <PID>` pero sí con `kill -9 <PID>`. Explica qué señal envía cada uno, por qué la primera puede ignorarse y qué riesgo tiene la segunda.
10. **Troubleshooting.** Después de instalar un dispositivo USB nuevo en Windows, aparece con un icono de advertencia en el Administrador de dispositivos y no funciona. ¿Qué componente del sistema operativo falta probablemente y qué harías?
11. **Conceptual.** ¿Qué es un hipervisor? ¿Qué diferencia hay entre el hipervisor que instalaste (VirtualBox/Hyper-V/UTM) y el que usa Azure para darte una máquina virtual? ¿Qué gana y qué pierde una VM frente a una máquina física?
12. **Situacional.** Tienes que administrar 200 servidores Linux en Azure. Explica, con tres argumentos concretos de este laboratorio, por qué lo harás por CLI y no por GUI.
13. **Reflexión.** Nombra dos conceptos que en Windows y Linux se llaman de forma distinta pero son lo mismo, y uno en el que los dos sistemas realmente funcionan de forma diferente.

## Checklist final

Antes de continuar, deberías poder:

- [ ] Explicar qué es un sistema operativo y qué es el kernel, y sus cuatro funciones principales.
- [ ] Explicar qué es un proceso, qué es un hilo y cómo se reparte la CPU entre procesos.
- [ ] Explicar memoria física, memoria virtual y swap a nivel conceptual.
- [ ] Explicar qué es un sistema de archivos y nombrar los habituales en Windows y Linux.
- [ ] Explicar el modelo de usuarios, grupos y permisos con un ejemplo de cada sistema.
- [ ] Explicar qué es un servicio/demonio y qué es un driver.
- [ ] Distinguir CLI de GUI y justificar por qué la CLI domina en servidores y nube.
- [ ] Crear una máquina virtual Linux en tu equipo y explicar qué es un hipervisor.
- [ ] Listar procesos, memoria, discos, servicios y permisos en Windows y en Linux con herramientas básicas.
- [ ] Localizar y terminar un proceso que consume toda la CPU en ambos sistemas.
- [ ] Tener la VM `lab-so` funcionando para el curso de Linux Básico.

---

*Recursos verificados el 2026-09-26 mediante búsqueda web (existencia y vigencia de las URLs). Si un enlace falla, abre un issue en este repositorio.*
