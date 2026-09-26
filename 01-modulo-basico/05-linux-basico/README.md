# Linux Básico

> Módulo: Básico · Curso 5 de 9 · Duración estimada: 20-30 horas · Estado: ✅ Completo

## Objetivo

Linux es el sistema operativo de la nube. La gran mayoría de las máquinas virtuales de Azure, AWS y GCP corren Linux; todos los contenedores Docker y todos los nodos de Kubernetes se apoyan en el kernel de Linux; casi todas las herramientas DevOps (Git, Terraform, Ansible, los agentes de CI/CD) nacieron en Linux. Si hay un curso de este módulo que no puedes saltarte ni hacer a medias, es este.

En este curso aprenderás a **vivir en la terminal**: moverte por el sistema de archivos, crear y manipular archivos, buscar dentro de ellos, entender quién puede hacer qué (usuarios, grupos, permisos), instalar software, arrancar y parar servicios y conectarte a otra máquina por SSH. No es un curso de "comandos para memorizar": es un curso para que la terminal deje de darte miedo y se convierta en tu herramienta principal.

Todo lo que viste en Windows Básico tiene aquí su equivalente, y ya conoces los conceptos de Fundamentos de Sistemas Operativos. Lo nuevo es la forma de trabajar: pequeña herramienta + tubería + archivos de texto. Es la filosofía Unix que viste en el curso de Historia.

**Antes de empezar** necesitas la VM `lab-so` de Ubuntu que creaste en el curso 3 (o crear una nueva). Todo el curso se hace dentro de ella, en la terminal.

### Al terminar este curso deberías poder

- Explicar qué es Linux, qué es una distribución y en qué se diferencian las familias principales (Debian/Ubuntu, Red Hat/Fedora, SUSE, Arch).
- Moverte por el sistema de archivos con rutas absolutas y relativas y explicar para qué sirven `/etc`, `/home`, `/var`, `/usr`, `/bin`, `/tmp`, `/root` y `/proc`.
- Crear, copiar, mover, renombrar y borrar archivos y directorios desde la terminal, con seguridad.
- Ver y buscar contenido en archivos con `cat`, `less`, `grep` y `find`, y encadenar comandos con tuberías y redirecciones.
- Explicar el modelo de permisos `rwx` para propietario, grupo y otros, leer la salida de `ls -l` y cambiar permisos y propietarios con `chmod` y `chown`.
- Crear usuarios y grupos, asignar pertenencia y explicar qué es `sudo` y por qué no se trabaja como `root`.
- Instalar, actualizar y eliminar paquetes con `apt` y explicar qué es un repositorio.
- Consultar, iniciar, parar y habilitar servicios con `systemctl` y leer sus logs con `journalctl`.
- Conectarte a una máquina Linux remota por SSH con contraseña y con clave, y copiar archivos con `scp`.
- Leer una página de manual (`man`) y la ayuda (`--help`) para aprender un comando que no conoces.

## Prerrequisitos

- Curso 3: Fundamentos de Sistemas Operativos (con la VM `lab-so` creada).
- Curso 4: Windows Básico (para las equivalencias; si vienes de macOS/Linux puedes haberlo hecho en paralelo).
- VM Ubuntu LTS (Desktop o Server) funcionando en VirtualBox, Hyper-V o UTM. Alternativa aceptable para casi todo el curso: WSL2 con Ubuntu en Windows 10/11, excepto la parte de SSH entre máquinas, que se adapta como se indica.

## Temario

- Qué es Linux.
- Distribuciones.
- Terminal.
- Estructura del sistema de archivos.
- Paths absolutos y relativos.
- pwd.
- ls.
- cd.
- mkdir.
- touch.
- cp.
- mv.
- rm.
- cat.
- less.
- grep.
- find.
- sudo.
- Usuarios.
- Grupos.
- Permisos.
- Instalación de paquetes.
- Servicios básicos.
- SSH introductorio.

## Recursos en español

### Introducción a Linux (LF-UPV-101x) — The Linux Foundation y Universitat Politècnica de València, en edX
- **URL:** https://www.edx.org/learn/linux/the-linux-foundation-introduccion-a-linux (ficha en Linux Foundation: https://training.linuxfoundation.org/training/introduccion-a-linux-lf-upv-101x/)
- **Autor / organización:** The Linux Foundation, traducido y adaptado por la Universitat Politècnica de València
- **Idioma:** Español
- **Tipo:** Curso online autoguiado (MOOC)
- **Duración aproximada:** 14 semanas a 5-7 h/semana según edX; para los capítulos que cubre este curso (introducción, distribuciones, sistema de archivos, línea de comandos, usuarios, permisos, procesos básicos) calcula 12-15 h. El resto se retoma en Administración de Linux (Módulo Intermedio).
- **Cubre:** Todo el temario excepto SSH en profundidad.
- **Nivel:** Introductorio
- **Acceso:** **Gratuito en modo "auditar"** (todo el contenido). El certificado verificado es de pago (unos 69 USD) y **no es necesario**. Requiere cuenta gratuita en edX. Al inscribirte elige explícitamente la opción gratuita, no la de certificado.
- **Por qué lo recomiendo:** Es la versión en español del curso de Linux más seguido del mundo (más de un millón de inscritos en inglés), hecho por la organización que gobierna Linux. Es el recurso principal del curso: estructurado, riguroso y con ejercicios. La parte gráfica (escritorio GNOME) puedes leerla por encima: aquí lo que importa es la terminal.

### Curso de Bash y Terminal desde cero — MoureDev (Brais Moure)
- **URL:** https://www.youtube.com/watch?v=ABgLEKFhlZE · Repositorio con apuntes y ejercicios: https://github.com/mouredev/hello-bash-shell
- **Autor / organización:** Brais Moure (MoureDev), ingeniero de software y divulgador en español
- **Idioma:** Español
- **Tipo:** Vídeo largo (curso completo) + repositorio de apuntes
- **Duración aproximada:** 6 h en total; para este curso interesan las primeras ~3 h (terminal, navegación, archivos, permisos, usuarios). La parte de scripting se retoma en el Módulo Intermedio.
- **Cubre:** Terminal, estructura del sistema de archivos, rutas, `pwd`/`ls`/`cd`/`mkdir`/`touch`/`cp`/`mv`/`rm`/`cat`/`less`/`grep`/`find`, permisos, usuarios, `sudo`.
- **Nivel:** Introductorio
- **Acceso:** Libre (el vídeo y el repositorio son gratuitos; la versión con extras en mouredev.pro es de pago y no es necesaria)
- **Por qué lo recomiendo:** Publicado en 2025, muy actualizado, con ritmo de clase y ejercicios en el repositorio. Es la mejor opción en español para "ver" la terminal en uso mientras lees la documentación. Usa la terminal Warp en las demostraciones, pero todo lo que enseña funciona igual en la terminal normal de Ubuntu.

### NDG Linux Unhatched — Cisco Networking Academy
- **URL:** https://www.netacad.com/courses/linux-unhatched?courseLang=en-US (en la página del curso puedes cambiar el idioma a español si está disponible en tu región; el curso existe en español)
- **Autor / organización:** Network Development Group (NDG) a través de Cisco Networking Academy
- **Idioma:** Español e inglés
- **Tipo:** Curso online con **terminal Linux real en el navegador**
- **Duración aproximada:** 8 h
- **Cubre:** Terminal, sistema de archivos, comandos básicos, permisos, instalación de paquetes.
- **Nivel:** Introductorio
- **Acceso:** Gratuito, requiere cuenta gratuita en netacad.com (la misma del curso de hardware)
- **Por qué lo recomiendo:** Complementario a edX. Su gran ventaja es que trae una terminal Linux dentro del navegador con ejercicios corregidos automáticamente: puedes practicar en cualquier momento sin arrancar la VM. Si el curso de edX te resulta muy largo, este es la alternativa corta.

### Hoja de trucos y artículos de freeCodeCamp en español (permisos, comandos)
- **URL:** https://www.freecodecamp.org/espanol/news/ (busca "permisos de Linux", "comandos de Linux")
- **Autor / organización:** freeCodeCamp (comunidad, traducciones revisadas)
- **Idioma:** Español
- **Tipo:** Artículos
- **Duración aproximada:** 10-15 min por artículo
- **Cubre:** Permisos, comandos básicos, `chmod`, `grep`, `find`.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Complementario, para repasar un tema concreto con ejemplos en español. Prefiere siempre la página `man` como fuente de verdad.

## Recursos en inglés

### The Linux command line for beginners — Ubuntu (Canonical)
- **URL:** https://ubuntu.com/tutorials/command-line-for-beginners (versión actualizada en la documentación oficial: https://documentation.ubuntu.com/desktop/en/latest/tutorial/the-linux-command-line-for-beginners/)
- **Autor / organización:** Canonical (Ubuntu)
- **Idioma:** Inglés
- **Tipo:** Tutorial oficial paso a paso
- **Duración aproximada:** 60-90 min
- **Cubre:** Terminal, historia de la línea de comandos, rutas, `pwd`/`ls`/`cd`/`mkdir`/`cp`/`mv`/`rm`, redirecciones y tuberías, `sudo`, buenas prácticas de seguridad.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es el tutorial oficial de Ubuntu para empezar con la terminal. Corto, claro, con ejercicios que puedes copiar tal cual en tu VM. Es el primer recurso en inglés que debes hacer.

### Linux Journey (nivel Grasshopper) — LabEx (proyecto original de Cindy Quach)
- **URL:** https://labex.io/linuxjourney
- **Autor / organización:** Proyecto de código abierto Linux Journey, mantenido por LabEx
- **Idioma:** Inglés
- **Tipo:** Lecciones cortas con cuestionarios y terminal en el navegador
- **Duración aproximada:** 4-6 h para el nivel Grasshopper (Command Line, Text-Fu, Users and Groups, Permissions, Processes, Packages)
- **Cubre:** Terminal, sistema de archivos, `grep`, `find`, usuarios, grupos, permisos, paquetes, procesos.
- **Nivel:** Introductorio
- **Acceso:** Libre, sin registro
- **Por qué lo recomiendo:** Lecciones de 5 minutos, una por comando o concepto, con cuestionario al final. Ideal para repasar en ratos cortos y para comprobar si has entendido cada tema antes de pasar al siguiente.

### The Linux Command Line (libro) — William Shotts
- **URL:** https://linuxcommand.org/tlcl.php (PDF gratuito, licencia Creative Commons)
- **Autor / organización:** William Shotts
- **Idioma:** Inglés (existe traducción parcial al español en la misma web)
- **Tipo:** Libro (PDF, ~550 páginas)
- **Duración aproximada:** Para este curso, capítulos 1 a 10 (~4 h de lectura)
- **Cubre:** Todo el temario en profundidad: shell, navegación, manipulación de archivos, comandos, redirecciones, permisos, procesos.
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es "el libro" de la línea de comandos Linux. Gratuito y muy bien escrito. No hace falta leerlo entero ahora: los capítulos 1-10 son el texto de referencia del curso; el resto (scripting) lo usarás en el Módulo Intermedio.

### OverTheWire: Bandit (niveles 0 a 12) — OverTheWire
- **URL:** https://overthewire.org/wargames/bandit/
- **Autor / organización:** Comunidad OverTheWire
- **Idioma:** Inglés
- **Tipo:** Juego de retos por SSH
- **Duración aproximada:** 3-5 h para los niveles 0-12
- **Cubre:** SSH, `ls`, `cat`, `find`, `grep`, permisos, archivos ocultos, redirecciones. Practica exactamente lo que enseña el curso, en un servidor real.
- **Nivel:** Introductorio (los primeros 12 niveles)
- **Acceso:** Libre, sin registro. Solo necesitas un cliente SSH.
- **Por qué lo recomiendo:** Es la mejor práctica gamificada que existe para la terminal: cada nivel te obliga a leer `man`, buscar y pensar. Se usa en la parte D del laboratorio. **No busques las soluciones en Internet**: el valor está en atascarse y salir.

### Linux man pages online — man7.org
- **URL:** https://man7.org/linux/man-pages/
- **Autor / organización:** Michael Kerrisk (proyecto Linux man-pages)
- **Idioma:** Inglés
- **Tipo:** Documentación oficial
- **Duración aproximada:** Consulta puntual
- **Cubre:** Todos los comandos del temario.
- **Nivel:** Todos
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la fuente de verdad. La regla del curso: antes de buscar un comando en Google, `man <comando>` o `<comando> --help`.

## Documentación oficial

- **Ubuntu Server — User management:** https://ubuntu.com/server/docs/how-to/security/user-management/ (usuarios, grupos, `sudo`, por qué `root` está deshabilitado en Ubuntu)
- **Ubuntu Server — OpenSSH server:** https://ubuntu.com/server/docs/how-to/security/openssh-server/ (instalar y configurar SSH)
- **Ubuntu Server — Networking (configuración de red, comando `ip`):** https://ubuntu.com/server/docs/explanation/networking/configuring-networks/
- **Ubuntu Desktop — The Linux command line for beginners:** https://documentation.ubuntu.com/desktop/en/latest/tutorial/the-linux-command-line-for-beginners/
- **Linux man-pages:** https://man7.org/linux/man-pages/ (y `man` en la VM)
- **The Debian Administrator's Handbook** (Debian y Ubuntu comparten base; libro libre): https://debian-handbook.info/ — referencia para quien quiera profundizar; no es lectura obligatoria.
- **Documentación del kernel de Linux:** https://docs.kernel.org/ (referencia)

## Ruta recomendada de estudio

1. **Ver** la primera hora del curso de MoureDev (terminal, navegación, archivos) con la VM abierta, repitiendo cada comando (60-90 min).
2. **Hacer** el tutorial oficial de Ubuntu "The Linux command line for beginners" completo, escribiendo cada comando (90 min). Al terminar deberías manejar rutas, `ls`, `cd`, `mkdir`, `cp`, `mv`, `rm`, redirecciones y tuberías básicas.
3. **Inscribirte gratis** en "Introducción a Linux" (edX, LF-UPV-101x) y **hacer** los capítulos de introducción, distribuciones, filosofía de Linux, estructura del sistema de archivos y línea de comandos (6-8 h, repartidas en varios días). Salta o lee por encima los capítulos de escritorio gráfico y aplicaciones.
4. **Leer** The Linux Command Line, capítulos 1-6 (2 h). Es el repaso escrito de lo anterior con más profundidad; céntrate en el capítulo 6 (redirecciones) y practica `>`, `>>`, `2>`, `|`.
5. **Hacer** Linux Journey, Grasshopper: "Text-Fu" (`cat`, `less`, `grep`, `find`, `head`, `tail`, `sort`, `wc`) (60 min).
6. **Hacer** los capítulos de usuarios, grupos y permisos de edX y **leer** "User management" de Ubuntu Server y el capítulo 9 (Permissions) de The Linux Command Line (3 h). Este es el bloque conceptual más importante del curso.
7. **Ver** las secciones de permisos, usuarios y `sudo` del curso de MoureDev (45 min) y **hacer** Linux Journey "Users and Groups" y "Permissions" (45 min).
8. **Leer** el capítulo de paquetes de edX y **hacer** Linux Journey "Packages" (60 min). Practica `apt update`, `apt search`, `apt install`, `apt remove`, `apt show`.
9. **Leer** "OpenSSH server" de Ubuntu Server (30 min). En SSH vas a **practicar** más que leer: se hace en el laboratorio.
10. **Hacer el laboratorio** (8-12 h, en varias sesiones). La parte D (Bandit) puedes ir haciéndola en paralelo desde el punto 5.
11. **Responder la evaluación** y **revisar el checklist**.

Si vas justo de tiempo: haz obligatoriamente los puntos 2, 3, 6, 9 y 10. El resto es refuerzo.

## Laboratorio

### Objetivo

Administrar tu VM Linux como un pequeño servidor de una empresa ficticia: organizar un árbol de directorios de trabajo, crear usuarios y grupos con permisos correctos, instalar y operar un servicio, habilitar acceso remoto por SSH con claves y demostrar que puedes encontrar información dentro del sistema usando solo la terminal.

### Requisitos

- VM Ubuntu LTS `lab-so` (o nueva) con al menos 2 GB de RAM y red configurada (NAT con reenvío de puertos o adaptador puente en VirtualBox).
- Tu equipo anfitrión con un cliente SSH: Windows 10/11 trae `ssh` y `scp` en PowerShell/CMD; macOS y Linux también.
- Toda la práctica se hace en la **terminal**. Si usas Ubuntu Desktop, no uses el explorador de archivos gráfico para ninguna tarea del laboratorio.
- Convención: documenta en `laboratorio-linux.md` cada comando ejecutado y su salida relevante (copiada como texto). Las capturas son complementarias.

### Instrucciones

**Parte A — Orientación y sistema de archivos (60-90 min)**

1. Identifica tu sistema: `cat /etc/os-release`, `uname -r`, `hostnamectl`, `whoami`, `id`, `echo $SHELL`, `echo $HOME`. Explica qué distribución, versión, kernel y shell tienes.
2. Recorre el árbol y explica **con tus palabras** para qué sirve cada directorio, mirando su contenido: `ls -la /`, `ls /etc | head`, `ls /home`, `ls /var/log`, `ls /usr/bin | wc -l`, `ls /tmp`, `sudo ls /root`, `ls /proc | head`. Responde: ¿por qué `ls /root` sin `sudo` falla? ¿Qué es `/proc` si no ocupa espacio en disco?
3. Rutas. Desde `/var/log`, escribe la ruta **relativa** a `/etc/hostname` y compruébala con `cat`. Desde tu `$HOME`, escribe la ruta absoluta y la relativa a `Documentos` (o `Documents`). Explica la diferencia entre `.`, `..`, `~` y `/`.
4. Crea con **un solo comando** `mkdir` esta estructura dentro de tu home (pista: `-p` y llaves `{}`):
   ```
   empresa/
   ├── proyectos/{alfa,beta,gamma}
   ├── documentos/{contratos,facturas}
   ├── scripts
   └── backups
   ```
   Verifica con `find empresa -type d` o `tree` (instálalo si no está: `sudo apt install tree`).
5. Con `touch`, `cp`, `mv` y `rm`:
   - Crea 5 archivos `informe-01.txt` a `informe-05.txt` en `proyectos/alfa` con un solo comando (llaves).
   - Copia toda la carpeta `alfa` a `beta` conservando permisos y fechas (`cp -a`). Explica qué hace `-a`.
   - Renombra `informe-01.txt` a `informe-inicial.txt` en `alfa`.
   - Mueve `informe-05.txt` de `alfa` a `gamma`.
   - Borra `proyectos/beta` completa. Explica la diferencia entre `rm`, `rm -r`, `rm -rf` y por qué `rm -rf` con `sudo` es peligroso. Ejecuta `rm -i informe-02.txt` y explica qué añade `-i`.

**Parte B — Texto, búsqueda y tuberías (60-90 min)**

6. Genera datos reales para trabajar: `sudo cp /var/log/syslog empresa/backups/syslog.copia 2>/dev/null || sudo journalctl --no-pager -n 2000 > empresa/backups/syslog.copia` y `sudo chown $USER empresa/backups/syslog.copia`. También `cp /etc/passwd empresa/documentos/passwd.copia`.
7. Con `cat`, `less`, `head`, `tail`, `wc`:
   - ¿Cuántas líneas tiene `syslog.copia`? ¿Y `passwd.copia`?
   - Muestra las 5 primeras y las 5 últimas líneas de cada uno.
   - Abre `syslog.copia` con `less`, busca la palabra `error` con `/`, salta al final con `G`, vuelve al inicio con `g`, sal con `q`. Anota estas teclas.
8. Con `grep`:
   - Cuenta cuántas líneas contienen `error` sin distinguir mayúsculas (`-i`, `-c`).
   - Muestra las líneas de `passwd.copia` que **no** terminan en `nologin` ni en `false` (`-v`, `-E`). ¿Qué usuarios pueden iniciar sesión interactiva?
   - Busca de forma recursiva en `/etc` los archivos que contienen la palabra `PermitRootLogin` (`-r`, `-l`). Necesitarás `sudo` para algunos directorios: explica los errores "Permission denied" que aparecen y cómo los ocultarías con `2>/dev/null`.
9. Con `find`:
   - Todos los archivos `.conf` dentro de `/etc` modificados en los últimos 30 días.
   - Todos los archivos de tu home mayores de 1 MB.
   - Todos los archivos de `/usr/bin` cuyo nombre empiece por `ip`.
   - Todos los archivos con permiso de ejecución para "otros" dentro de `empresa` (`-perm`).
10. Tuberías y redirecciones. Construye y explica cada comando:
    - Los 10 procesos que más memoria consumen: `ps aux --sort=-%mem | head -11`.
    - El número de usuarios definidos en el sistema: `cut -d: -f1 /etc/passwd | wc -l`.
    - Los 5 tipos de shell más usados en `/etc/passwd`: `cut -d: -f7 /etc/passwd | sort | uniq -c | sort -rn | head -5`.
    - Guarda la salida del primer comando en `empresa/backups/top-memoria.txt` con `>` y añade la fecha al final con `date >>`. Explica la diferencia entre `>` y `>>`.
    - Ejecuta `ls /root /home 2> empresa/backups/errores.txt` y explica qué fue a pantalla y qué al archivo.

**Parte C — Usuarios, grupos, permisos y sudo (90-120 min)**

11. Lee `/etc/passwd`, `/etc/group` y (con `sudo`) `/etc/shadow`. Explica qué hay en cada uno y por qué `shadow` solo lo lee `root`. Comprueba con `ls -l /etc/passwd /etc/shadow /etc/group`.
12. Crea el grupo `desarrollo` y el grupo `finanzas`. Crea los usuarios `ana`, `luis` (grupo suplementario `desarrollo`) y `marta` (grupo suplementario `finanzas`) con `sudo adduser` (interactivo) o `useradd -m -s /bin/bash` + `passwd`. Añade pertenencias con `usermod -aG`. Verifica con `id ana`, `groups luis`, `getent group desarrollo`. Explica la diferencia entre grupo primario y suplementario y qué pasa si olvidas la `-a` en `usermod -G`.
13. Permisos sobre `empresa`:
    - `empresa/proyectos`: propietario tú, grupo `desarrollo`, permisos `rwxrwx---` (770). Que `ana` y `luis` puedan crear archivos y `marta` no pueda ni listar.
    - `empresa/documentos/facturas`: propietario tú, grupo `finanzas`, `rwxrwx---`. Que `marta` pueda entrar y `ana` no.
    - `empresa/documentos/contratos`: `rwxr-x---` con grupo `finanzas`: `marta` puede leer y listar pero **no** crear archivos.
    - `empresa/scripts`: `rwxr-xr-x` (755).
    Usa `chown`, `chgrp`/`chown :grupo` y `chmod` tanto en notación octal como simbólica (`g+w`, `o-rx`). Muestra `ls -l empresa empresa/documentos` y explica cada columna de una línea (tipo, permisos, enlaces, propietario, grupo, tamaño, fecha, nombre).
14. Prueba los permisos cambiando de usuario con `su - ana` (o `sudo -u ana bash`): intenta `ls`, `touch` y `cat` en cada carpeta y anota qué funciona y qué da "Permission denied". Repite como `marta`. Vuelve a tu usuario con `exit`.
15. Crea en `empresa/scripts/hola.sh` un script con:
    ```bash
    #!/bin/bash
    echo "Hola, soy $(whoami) en $(hostname) y hoy es $(date +%F)"
    ```
    Ejecuta `./hola.sh` (fallará) y explica por qué. Dale permiso con `chmod +x` y vuelve a ejecutarlo. Explica qué es la línea `#!/bin/bash`.
16. `sudo`. Ejecuta `sudo -l` y explica qué puedes hacer. Comprueba `cat /etc/sudoers` (con `sudo`) y `ls /etc/sudoers.d/`. Intenta como `ana` ejecutar `sudo apt update`: ¿qué pasa y por qué? Añade a `luis` al grupo `sudo` (`usermod -aG sudo luis`) y verifica que ahora puede. Explica por qué en Ubuntu no se usa la cuenta `root` directamente y qué diferencia hay entre `su`, `sudo` y `sudo -i`.

**Parte D — Paquetes y servicios (60-90 min)**

17. `apt`. Ejecuta y explica: `sudo apt update` (¿qué descarga?), `apt list --upgradable`, `apt search nginx`, `apt show nginx`, `sudo apt install nginx`, `apt policy nginx`, `dpkg -l | grep nginx`, `dpkg -L nginx | head`. Explica qué es un repositorio, qué hay en `/etc/apt/sources.list` o `/etc/apt/sources.list.d/`, y la diferencia entre `apt update` y `apt upgrade`.
18. Servicios. Con `nginx` instalado:
    - `systemctl status nginx`: ¿está activo? ¿habilitado en el arranque? ¿cuál es su PID principal?
    - Abre en el navegador de la VM `http://localhost` (o `curl localhost` en la terminal). ¿Qué ves?
    - `sudo systemctl stop nginx` y repite `curl localhost`. Anota el error.
    - `sudo systemctl start nginx`, `sudo systemctl disable nginx`, reinicia la VM y comprueba con `systemctl status nginx` que **no** arrancó. Explica la diferencia entre start/stop y enable/disable.
    - `sudo systemctl enable --now nginx` y comprueba.
    - `journalctl -u nginx --since "1 hour ago"`: localiza tus paradas y arranques. `sudo tail -5 /var/log/nginx/access.log`: localiza tus visitas con `curl`.
19. Edita la página por defecto de nginx (`/var/www/html/index.nginx-debian.html`) con `nano` para que muestre tu nombre y "Laboratorio Linux Básico". Comprueba con `curl localhost`. Explica por qué necesitaste `sudo` para editar ese archivo (mira `ls -l`).
20. Desinstala algo que no necesites y limpia: `sudo apt remove tree` (si lo instalaste), `sudo apt autoremove`. Explica qué hace `autoremove`.

**Parte E — SSH (60-90 min)**

21. Instala y arranca el servidor SSH en la VM siguiendo la documentación de Ubuntu: `sudo apt install openssh-server`, `sudo systemctl enable --now ssh`, `systemctl status ssh`. Averigua la IP de la VM con `ip -br a` (explica qué muestra la salida).
22. Configura la red de la VM para que el anfitrión la alcance: en VirtualBox, o bien adaptador **puente** (la VM recibe IP de tu red doméstica), o bien NAT con **reenvío de puertos** (anfitrión 2222 → VM 22). Documenta cuál elegiste y por qué. (Con WSL2 la IP de `ip -br a` es directamente accesible desde Windows.)
23. Desde el **anfitrión**, conéctate con contraseña: `ssh <tu-usuario>@<ip-vm>` (o `ssh -p 2222 <tu-usuario>@localhost`). Acepta la huella del servidor y explica qué es esa pregunta de "fingerprint" y qué archivo `known_hosts` se ha creado. Ejecuta `hostname`, `uptime` y `exit`.
24. Autenticación con clave:
    - En el anfitrión: `ssh-keygen -t ed25519 -C "laboratorio-linux"` (acepta la ruta por defecto, pon passphrase). Explica qué dos archivos se crearon y cuál **nunca** debe salir de tu equipo.
    - Copia la clave pública a la VM: `ssh-copy-id <usuario>@<ip>` (Linux/macOS) o, en Windows, `type $env:USERPROFILE\.ssh\id_ed25519.pub | ssh <usuario>@<ip> "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys"`.
    - Conéctate de nuevo: no debe pedir la contraseña del usuario (sí la passphrase de la clave). Revisa en la VM `ls -la ~/.ssh` y `cat ~/.ssh/authorized_keys`, y explica por qué `.ssh` debe ser `700` y `authorized_keys` `600`.
25. Copia archivos: desde el anfitrión, `scp laboratorio-linux.md <usuario>@<ip>:~/empresa/documentos/` y en sentido contrario `scp <usuario>@<ip>:~/empresa/backups/top-memoria.txt .`. Comprueba con `ls`.
26. Endurecimiento mínimo: edita `/etc/ssh/sshd_config` (con `sudo nano`) y asegúrate de que `PermitRootLogin no`. Reinicia el servicio (`sudo systemctl restart ssh`) y comprueba con `journalctl -u ssh -n 20` que arrancó bien. Explica por qué esta opción importa en un servidor expuesto a Internet.

**Parte F — Bandit (3-5 h, en paralelo)**

27. Completa los niveles **0 a 12** de OverTheWire Bandit desde el anfitrión o la VM. Para cada nivel anota en `bandit.md`: el comando o comandos usados, qué `man` consultaste y qué aprendiste. **No** anotes las contraseñas. No busques soluciones: si te atascas más de 30 minutos en un nivel, pregunta al mentor.

**Parte G — Limpieza y equivalencias (30 min)**

28. Elimina los usuarios `ana`, `luis` y `marta` con sus homes (`deluser --remove-home`) y los grupos `desarrollo` y `finanzas`. Deja `nginx` y `ssh` instalados y habilitados (los usarás en cursos siguientes).
29. Completa una tabla **Windows ↔ Linux** con al menos 15 filas de lo que has hecho (crear usuario, ver grupos, cambiar permisos, listar servicios, ver logs, instalar software, ver IP, conectarse remotamente, buscar texto en archivos, etc.).

### Resultado esperado

- `laboratorio-linux.md` con las partes A-E y G, comandos y salidas, capturas de los puntos clave y explicaciones propias.
- `bandit.md` con las notas de los niveles 0-12.
- `hola.sh` y la tabla de equivalencias.
- La VM con `nginx` y `ssh` operativos y acceso por clave desde el anfitrión.

### Criterios de validación

- [ ] Parte A: la estructura se creó con un solo `mkdir`, las operaciones de archivos son correctas y la explicación de `rm -rf` es precisa.
- [ ] Parte B: cada `grep`, `find` y tubería está escrito por el estudiante, funciona y está explicado; se distingue correctamente `>`/`>>`/`2>`.
- [ ] Parte C: `ls -l` refleja exactamente los permisos pedidos; las pruebas con `ana`, `luis` y `marta` coinciden con lo esperado; la explicación de `sudo`/`su`/`root` es correcta; el script falla antes de `chmod +x` y funciona después.
- [ ] Parte D: se distingue start/stop de enable/disable con la prueba del reinicio; los logs de nginx (`journalctl` y `access.log`) muestran las acciones del estudiante.
- [ ] Parte E: la conexión por clave funciona sin contraseña de usuario; `PermitRootLogin no`; explicación correcta de clave pública/privada, `known_hosts`, `authorized_keys` y sus permisos.
- [ ] Parte F: los 13 niveles están documentados con comandos propios y aprendizaje por nivel (sin contraseñas).
- [ ] Parte G: la tabla tiene al menos 15 filas correctas.
- [ ] El estudiante puede, en una llamada con el mentor, resolver un pequeño reto en la terminal (por ejemplo, "encuentra qué archivos de /etc cambiaron hoy" o "dale al grupo X permiso de escritura en Y") sin buscar los comandos.

## Entrega

En tu repositorio de entregas, carpeta `01-modulo-basico/05-linux-basico/`:

1. `laboratorio-linux.md`.
2. `bandit.md`.
3. `hola.sh`.
4. Carpeta `capturas/`.
5. `ENTREGA.md` con evaluación, checklist y uso de IA.

Nota sobre IA: en este curso es especialmente tentador pedirle a una IA "el comando para X". Úsala para que te **explique** un comando o un error, no para que te lo dé hecho. Si lo haces, decláralo y demuestra en `ENTREGA.md` que entiendes cada flag.

## Evaluación

1. **Conceptual.** ¿Qué es una distribución de Linux? Nombra las tres familias principales, una distribución de cada una y una diferencia práctica entre ellas (por ejemplo, el gestor de paquetes).
2. **Conceptual.** Explica qué hay en `/etc`, `/var/log`, `/home`, `/usr/bin` y `/tmp`. Si un servicio "no arranca", ¿en cuál de estos directorios buscarías primero y por qué?
3. **Técnica.** Estás en `/home/ana/proyectos/alfa`. Escribe la ruta relativa y la absoluta a `/home/ana/backups/copia.txt`. ¿Qué hace `cd -`?
4. **Situacional.** Un compañero ejecutó `sudo rm -rf /var/log /` (con un espacio accidental antes de la última barra). Explica qué ha pasado y por qué `-f` empeoró las cosas. ¿Qué hábito habría evitado el desastre?
5. **Técnica.** Explica esta línea de `ls -l`: `-rwxr-x--- 1 luis desarrollo 4096 sep 20 10:15 deploy.sh`. ¿Quién puede ejecutar el script? ¿Quién puede modificarlo? ¿Qué número octal corresponde?
6. **Situacional.** `marta` pertenece al grupo `finanzas`, la carpeta `facturas` tiene `rwxrwx---` y grupo `finanzas`, pero `marta` recibe "Permission denied" al hacer `ls facturas`. Da dos causas posibles y cómo comprobarías cada una (pista: la carpeta padre; `id marta` frente a una sesión antigua).
7. **Conceptual.** ¿Qué diferencia hay entre `su`, `sudo comando` y `sudo -i`? ¿Por qué Ubuntu deshabilita el login de `root` y qué ventaja tiene `sudo` a la hora de auditar quién hizo qué?
8. **Técnica.** Escribe una tubería que muestre cuántas veces aparece cada dirección IP en `/var/log/nginx/access.log`, ordenadas de mayor a menor, y explica cada etapa.
9. **Técnica.** ¿Qué diferencia hay entre `grep -r "error" /var/log` y `find /var/log -name "*error*"`? Da un caso de uso para cada uno.
10. **Troubleshooting.** `sudo systemctl start nginx` devuelve "Job for nginx.service failed". Escribe los dos comandos que ejecutarías a continuación para averiguar por qué y qué buscarías en su salida.
11. **Conceptual.** Explica la diferencia entre `systemctl start`, `systemctl enable` y `systemctl enable --now`. Un servicio está "active (running)" pero "disabled": ¿qué pasará tras un reinicio?
12. **Conceptual.** ¿Qué hace `apt update` y qué hace `apt upgrade`? ¿Qué es un repositorio y por qué instalar desde el repositorio oficial es más seguro que descargar un `.deb` de una web cualquiera?
13. **Conceptual.** Explica la autenticación SSH por clave pública: qué archivo va en el cliente, cuál en el servidor, qué es la passphrase y por qué es más segura que la contraseña. ¿Qué significa el aviso "REMOTE HOST IDENTIFICATION HAS CHANGED"?
14. **Troubleshooting.** `ssh usuario@servidor` responde "Permission denied (publickey)". Nombra tres causas posibles relacionadas con claves y permisos de archivos, y cómo comprobarías cada una.
15. **Reflexión.** Del laboratorio, ¿qué tarea te costó más y qué `man` o `--help` te desbloqueó? ¿Qué hábito de la terminal te llevas para el resto de la ruta?

## Checklist final

Antes de continuar, deberías poder:

- [ ] Explicar qué es Linux y qué es una distribución, y nombrar las familias principales.
- [ ] Moverte por el sistema de archivos con rutas absolutas y relativas y explicar los directorios principales.
- [ ] Crear, copiar, mover y borrar archivos y directorios sin equivocarte, y explicar los riesgos de `rm -rf`.
- [ ] Buscar texto con `grep` y archivos con `find`, y combinar comandos con tuberías y redirecciones.
- [ ] Leer `ls -l` completo y cambiar permisos y propietarios con `chmod` y `chown` (octal y simbólico).
- [ ] Crear usuarios y grupos, gestionar pertenencias y explicar `sudo` frente a `root`.
- [ ] Instalar, actualizar y eliminar paquetes con `apt` y explicar qué es un repositorio.
- [ ] Gestionar servicios con `systemctl` y leer sus logs con `journalctl`.
- [ ] Conectarte por SSH con clave, copiar archivos con `scp` y explicar `known_hosts` y `authorized_keys`.
- [ ] Aprender un comando nuevo leyendo `man` o `--help`.
- [ ] Tener la VM con `nginx` y `ssh` operativos para los cursos siguientes.

---

*Recursos verificados el 2026-09-26 mediante búsqueda web (existencia y vigencia de las URLs). Si un enlace falla, abre un issue en este repositorio.*
