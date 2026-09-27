# Administración de Linux

> Módulo: Intermedio · Curso 1 de 11 · Duración estimada: 30-40 horas · Estado: ✅ Completo

## Objetivo

En Linux Básico aprendiste a vivir en la terminal. Ahora vas a aprender a **ser responsable de una máquina**: que arranque lo que tiene que arrancar, que los usuarios tengan exactamente los permisos que necesitan y ni uno más, que el disco no se llene sin que te enteres, que los servicios se recuperen solos, que puedas explicar por qué algo falló leyendo los logs y que la máquina siga siendo tuya aunque esté expuesta a Internet.

Todo lo que harás aquí lo harás después a escala en la nube: una VM de Azure es una máquina Linux exactamente igual que tu `lab-so`; un contenedor Docker es un proceso Linux con permisos y límites; un nodo de Kubernetes es un servidor Linux que alguien tiene que entender cuando el clúster se comporta raro. Los errores más caros que verás en tu carrera ("el disco de la base de datos se llenó", "el servicio no arrancó tras el reinicio", "el cron de backup lleva tres meses fallando en silencio", "alguien dejó el SSH con contraseña abierto a Internet") son errores de administración básica de Linux.

El curso gira alrededor de un laboratorio largo en el que administras `lab-so` como si fuera el servidor de producción de una pequeña empresa: usuarios reales, un servicio propio bajo systemd, tareas programadas, un disco nuevo con LVM, SSH endurecido, firewall y tres averías que tendrás que diagnosticar con método.

**Antes de empezar** necesitas la VM `lab-so` con `nginx`, `openssh-server` y `ufw` del Módulo Básico y acceso por clave SSH desde tu anfitrión. Si la VM no está en buen estado, crea una nueva Ubuntu Server LTS: se tarda 15 minutos y es buena práctica.

### Al terminar este curso deberías poder

- Gestionar usuarios y grupos de forma completa (creación, caducidad, bloqueo, `sudoers` por archivo) y explicar `setuid`, `setgid`, `sticky bit`, `umask` y ACLs con casos reales.
- Listar, inspeccionar, priorizar y matar procesos con `ps`, `top`/`htop`, `nice`, `kill` y explicar qué es una señal, un proceso zombi y un proceso huérfano.
- Escribir una unidad de servicio de systemd para un script propio, con reinicio automático, dependencias y usuario dedicado, y programarla con un timer.
- Leer y filtrar logs con `journalctl` (por unidad, prioridad, tiempo, arranque) y saber qué sigue yendo a `/var/log`.
- Usar `apt` más allá de `install`: repositorios, prioridades, `hold`, versiones, `unattended-upgrades`, y saber qué hace cada archivo bajo `/etc/apt`.
- Endurecer SSH (solo clave, sin root, `AllowUsers`, `Fail2ban` opcional) sin quedarte fuera de la máquina.
- Programar tareas con `cron` y con timers de systemd y explicar cuándo usar cada uno.
- Añadir un disco a una VM, particionarlo, crear un volumen LVM, formatearlo, montarlo de forma persistente en `fstab` y ampliarlo en caliente.
- Diagnosticar consumo de CPU, memoria, swap y disco con `top`, `vmstat`, `free`, `df`, `du`, `iostat` y saber qué cifra mirar en cada caso.
- Configurar red con `netplan`, inspeccionarla con `ip` y `ss`, y controlar el firewall con `ufw`.
- Resolver con método tres averías clásicas: disco lleno, servicio que no arranca y problema de permisos.

## Prerrequisitos

- Módulo Básico completo, en especial Linux Básico (curso 5) y Networking Básico (curso 6).
- VM `lab-so` (Ubuntu Server LTS recomendado) con 2 GB de RAM mínimo, acceso SSH por clave desde el anfitrión y posibilidad de añadirle un segundo disco virtual (VirtualBox, Hyper-V y UTM lo permiten).
- Una instantánea (snapshot) de la VM antes de empezar. Vas a romper cosas a propósito.

## Temario

Usuarios y grupos · Ownership · Permisos avanzados · Procesos · systemd · Servicios · Logs · journalctl · Package managers · SSH · Cron · Variables de entorno · Storage · Filesystems · Mounts · CPU y memoria · Troubleshooting · Networking en Linux.

**Práctica:** administrar una VM Linux como un servidor real.

## Recursos en español

### Introducción a Linux (LF-UPV-101x), capítulos de administración — The Linux Foundation y UPV, en edX
- **URL:** https://www.edx.org/learn/linux/the-linux-foundation-introduccion-a-linux (ficha: https://training.linuxfoundation.org/training/introduccion-a-linux-lf-upv-101x/)
- **Autor / organización:** The Linux Foundation, adaptado por la Universitat Politècnica de València
- **Idioma:** Español
- **Tipo:** Curso online autoguiado (MOOC)
- **Duración aproximada:** 10-12 h para los capítulos que quedaron pendientes en Linux Básico: procesos, sistemas de archivos y almacenamiento, gestión de paquetes, red, servicios del sistema, seguridad local
- **Cubre:** Procesos, storage, filesystems, mounts, package managers, usuarios y grupos, networking en Linux.
- **Nivel:** Introductorio-intermedio
- **Acceso:** Gratuito en modo "auditar"; el certificado es de pago y no es necesario. Requiere cuenta gratuita en edX.
- **Por qué lo recomiendo:** Ya lo conoces del Módulo Básico. Termínalo: los capítulos de procesos, almacenamiento y red son exactamente la teoría que necesitas antes de tocar `systemd`, LVM y `netplan` en el laboratorio.

### El manual del Administrador de Debian (traducción al español) — Raphaël Hertzog y Roland Mas
- **URL:** https://debian-handbook.info/browse/es-ES/stable/ (portada del proyecto: https://debian-handbook.info/)
- **Autor / organización:** Raphaël Hertzog y Roland Mas, desarrolladores de Debian; traducción comunitaria
- **Idioma:** Español (la versión en inglés está más actualizada)
- **Tipo:** Libro libre (HTML y PDF)
- **Duración aproximada:** 6-8 h para los capítulos 8 (configuración básica: red, usuarios, montaje), 9 (servicios Unix: systemd, SSH, cron, logs) y 14 (seguridad: firewall, `sudo`)
- **Cubre:** Usuarios y grupos, systemd, servicios, logs, package managers (`apt` en profundidad), SSH, cron, mounts, networking, firewall.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Ubuntu es Debian por debajo: `apt`, `dpkg`, `/etc/network`, `systemd` y `ufw` (sobre `iptables`/`nftables`) se explican aquí con la profundidad de quien mantiene la distribución. Lee la traducción en español para los conceptos y salta a la edición inglesa cuando un detalle parezca antiguo.

### Artículos de freeCodeCamp en español (systemd, cron, permisos especiales) — freeCodeCamp
- **URL:** https://www.freecodecamp.org/espanol/news/ (busca "systemd", "cron", "chmod", "LVM")
- **Autor / organización:** freeCodeCamp (comunidad, traducciones revisadas)
- **Idioma:** Español
- **Tipo:** Artículos
- **Duración aproximada:** 10-20 min por artículo
- **Cubre:** Servicios, cron, permisos avanzados, storage, a nivel de repaso puntual.
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Complementario, para leer una explicación en español de un tema concreto antes de ir al `man`. No sustituye a la documentación oficial.

## Recursos en inglés

### Ubuntu Server documentation — Canonical
- **URL:** https://documentation.ubuntu.com/server/ (espejo: https://ubuntu.com/server/docs/) · Guías prácticas: https://ubuntu.com/server/docs/how-to/
- **Autor / organización:** Canonical (Ubuntu)
- **Idioma:** Inglés
- **Tipo:** Documentación oficial (tutorial, how-to, explicación y referencia)
- **Duración aproximada:** 6-8 h para las guías de gestión de usuarios, OpenSSH, configuración de red con netplan, gestión de software, almacenamiento (LVM) y logs
- **Cubre:** Todo el temario aplicado a Ubuntu Server, que es lo que corre en tu VM y en la mayoría de VMs de Azure.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la fuente de verdad para tu VM. Se organiza al estilo Diátaxis (tutorial, how-to, explicación, referencia): cuando quieras hacer algo, ve a "How-to"; cuando quieras entenderlo, a "Explanation". Acostúmbrate a este tipo de documentación porque es el estándar de la industria.

### Linux Upskill Challenge — Steve Brorens (snori74) y comunidad, mantenido por Livia Lima
- **URL:** https://linuxupskillchallenge.org/ (repositorio: https://github.com/livialima/linuxupskillchallenge)
- **Autor / organización:** Proyecto comunitario de código abierto (licencia libre), nacido en Reddit
- **Idioma:** Inglés
- **Tipo:** Curso práctico de 20 lecciones diarias sobre un servidor real
- **Duración aproximada:** 20 días a 1-2 h/día (puedes hacerlo en 12-15 h concentradas)
- **Cubre:** Usuarios, `sudo`, permisos, procesos, logs, `apt`, SSH endurecido, cron, storage, `ufw`, troubleshooting. Es casi exactamente el temario del curso.
- **Nivel:** Intermedio
- **Acceso:** Libre, sin registro
- **Por qué lo recomiendo:** Es el mejor curso gratuito de administración de servidores Linux orientado a "gente que empieza en operaciones". Cada día es una tarea concreta sobre tu propio servidor (usa tu `lab-so`; no necesitas alquilar nada) con explicación, ejercicios y extensiones. Es el complemento perfecto del laboratorio: haz sus días en paralelo con las partes correspondientes.

### Linux Journey, nivel Journeyman — proyecto Linux Journey mantenido por LabEx
- **URL:** https://labex.io/linuxjourney (repositorio: https://github.com/labex-labs/linuxjourney)
- **Autor / organización:** Proyecto de código abierto Linux Journey (Cindy Quach), mantenido por LabEx
- **Idioma:** Inglés
- **Tipo:** Lecciones cortas con cuestionario
- **Duración aproximada:** 5-6 h para Journeyman: Devices, The Filesystem, Boot the System, Kernel, Init (systemd), Process Utilization, Logging
- **Cubre:** Procesos, systemd, logs, storage, filesystems, mounts, CPU y memoria.
- **Nivel:** Intermedio
- **Acceso:** Libre, sin registro
- **Por qué lo recomiendo:** Ya usaste el nivel Grasshopper. Journeyman explica en lecciones de 5 minutos qué hay debajo: cómo arranca el sistema, qué es un inodo, qué hace `init`, cómo se mide la carga. Es la teoría corta que hace que el laboratorio tenga sentido.

### Red Hat Enterprise Linux 9: Configuring basic system settings — Red Hat
- **URL:** https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/9/html-single/configuring_basic_system_settings/index · Capítulo de usuarios y grupos: https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/9/html/configuring_basic_system_settings/managing-users-and-groups_configuring-basic-system-settings · Capítulo de systemd: https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/9/html/configuring_basic_system_settings/managing-systemd_configuring-basic-system-settings · Índice de guías RHEL 9: https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/9
- **Autor / organización:** Red Hat
- **Idioma:** Inglés
- **Tipo:** Documentación oficial
- **Duración aproximada:** 3-4 h (usuarios y grupos, systemd, y las guías "Managing file systems" y "Configuring and managing logical volumes" del índice para la parte de storage)
- **Cubre:** Usuarios y grupos, systemd, servicios, storage, filesystems, LVM.
- **Nivel:** Intermedio
- **Acceso:** Libre (la documentación es pública; RHEL como sistema requiere suscripción, no la necesitas)
- **Por qué lo recomiendo:** La otra gran familia de Linux. La documentación de Red Hat sobre `systemd` y LVM es la más clara que existe y aplica casi literalmente a Ubuntu (cambia `dnf` por `apt` y `nmcli` por `netplan`). Saber leer las dos familias te hace empleable en cualquier empresa.

## Documentación oficial

- **Ubuntu Server — User management:** https://ubuntu.com/server/docs/how-to/security/user-management/
- **Ubuntu Server — OpenSSH server:** https://ubuntu.com/server/docs/how-to/security/openssh-server/
- **Ubuntu Server — Configuring networks (netplan, `ip`):** https://ubuntu.com/server/docs/explanation/networking/configuring-networks/
- **Netplan (referencia YAML y ejemplos):** https://netplan.io
- **systemd (documentación del proyecto):** https://systemd.io · En la VM: `man systemd.unit`, `man systemd.service`, `man systemd.timer`, `man journalctl`
- **Linux man-pages (man7.org):** https://man7.org/linux/man-pages/ · En la VM: `man 5 sudoers`, `man setfacl`, `man 7 signal`, `man 5 fstab`, `man lvm`, `man 5 crontab`, `man ufw`
- **El manual del Administrador de Debian:** https://debian-handbook.info/browse/es-ES/stable/
- **Documentación del kernel de Linux (referencia):** https://docs.kernel.org/

## Ruta recomendada de estudio

1. **Hacer** una instantánea de `lab-so` y **leer** el capítulo 8 del manual de Debian (configuración básica) (90 min). Repasa `/etc/passwd`, `/etc/group`, `/etc/shadow` y `sudo`.
2. **Hacer** Linux Journey Journeyman: Process Utilization y Init (systemd) (60 min) y **leer** el capítulo de systemd de Red Hat (60 min). Después, la Parte A y B del laboratorio.
3. **Empezar** el Linux Upskill Challenge por el día 1 y avanzar un día por sesión durante el resto del curso. Sus días de `sudo`, SSH, `apt`, cron, logs y `ufw` coinciden con partes del laboratorio: hazlos juntos.
4. **Leer** en Ubuntu Server docs las guías de OpenSSH server y user management (60 min) y **hacer** la Parte C (systemd) y D (paquetes y entorno) del laboratorio.
5. **Hacer** los capítulos de edX de procesos, red y seguridad local (3-4 h, en varios días) y **hacer** la Parte E (SSH endurecido).
6. **Hacer** Linux Journey Journeyman: Devices y The Filesystem (60 min), **leer** las guías de Red Hat sobre file systems y LVM (90 min) y **hacer** la Parte F (storage).
7. **Leer** Ubuntu Server "Configuring networks" y la documentación de netplan (45 min) y **hacer** la Parte G (CPU, memoria y red).
8. **Hacer** la Parte H (averías) sin mirar la solución hasta haber escrito tu diagnóstico.
9. **Responder la evaluación** y **revisar el checklist**.

Si vas justo de tiempo: haz obligatoriamente los puntos 1, 2, 4, 6 y 8. El Linux Upskill Challenge puede quedar a medias y terminarse durante el siguiente curso.

## Laboratorio

### Objetivo

Convertir `lab-so` en el servidor de una pequeña empresa ficticia ("Acme Logística"): usuarios con permisos exactos, un servicio propio gestionado por systemd, tareas programadas, un segundo disco gestionado con LVM, SSH endurecido, firewall activo, monitorización básica de recursos y tres averías diagnosticadas y resueltas con método y evidencias.

### Requisitos

- VM `lab-so` Ubuntu Server LTS con acceso por clave SSH y snapshot previo.
- Capacidad de añadir un disco virtual de 5 GB a la VM (VirtualBox: Configuración → Almacenamiento → Añadir disco duro; Hyper-V: Configuración → Controlador SCSI → Disco duro; UTM: Unidades → Nueva).
- Documenta todo en `laboratorio-linux-admin.md`: comandos, salidas relevantes como texto, y explicaciones propias. Las capturas son complementarias y deben mostrar tu usuario y `hostname`.
- Trabaja siempre por SSH desde el anfitrión. Mantén **una segunda sesión SSH abierta** cuando toques `sshd_config` o `ufw`: si te equivocas, la sesión vieja sigue viva.

### Instrucciones

**Parte A — Usuarios, grupos y permisos avanzados (2-3 h)**

1. Crea los grupos `ops`, `dev` y `finanzas`. Crea los usuarios `ana` (ops), `luis` (dev), `marta` (finanzas) y una cuenta de servicio `svc-informes` sin shell interactivo (`--shell /usr/sbin/nologin`, sin contraseña). Para `luis`, fija caducidad de contraseña a 90 días (`chage -M 90`) y fecha de expiración de cuenta dentro de 6 meses (`chage -E`). Muestra `chage -l luis` y explica cada línea. Bloquea y desbloquea a `marta` con `usermod -L`/`-U` y comprueba con `passwd -S marta` qué cambia en `/etc/shadow`.
2. `sudo` fino: crea `/etc/sudoers.d/ops` con `visudo -f` para que el grupo `ops` pueda ejecutar **solo** `systemctl restart nginx`, `systemctl status nginx` y `journalctl -u nginx` sin contraseña. Prueba como `ana`: `sudo systemctl restart nginx` funciona y `sudo apt update` no. Explica por qué se usa `visudo` y `sudoers.d` en vez de editar `/etc/sudoers`, y qué pasa si dejas un error de sintaxis.
3. Directorio compartido con `setgid`: crea `/srv/acme/dev` con grupo `dev` y permisos `2770`. Como `luis`, crea un archivo dentro y comprueba con `ls -l` que el grupo del archivo es `dev` y no el grupo primario de `luis`. Quita el `setgid` (`chmod g-s`), repite y explica la diferencia.
4. `sticky bit`: crea `/srv/acme/compartido` con `1777`. Como `ana`, crea `nota-ana.txt`; como `luis`, intenta borrarlo. Compara con `/tmp` (`ls -ld /tmp`). Explica para qué existe el sticky bit.
5. `setuid`: `ls -l /usr/bin/passwd /usr/bin/sudo /usr/bin/su`. Explica qué significa la `s` en la posición del propietario y por qué `passwd` la necesita (pista: `/etc/shadow`). Busca todos los binarios setuid del sistema con `find / -perm -4000 -type f 2>/dev/null` y explica por qué un auditor de seguridad revisa esa lista.
6. `umask`: ejecuta `umask`, crea un archivo y un directorio y explica cómo se calculan sus permisos a partir de `0666`/`0777` y la máscara. Cambia temporalmente a `umask 077`, repite y explica en qué caso querrías eso por defecto. Localiza dónde se fija la `umask` en Ubuntu (`/etc/login.defs`, `/etc/profile`, `~/.bashrc`).
7. ACLs: instala `acl` si hace falta. En `/srv/acme/finanzas` (grupo `finanzas`, `770`) da a `ana` (que **no** es de finanzas) permiso de solo lectura con `setfacl -m u:ana:rx`. Comprueba con `getfacl`, con `ls -l` (fíjate en el `+`) y probando como `ana` y como `luis`. Añade una ACL por defecto (`-d`) para que los archivos nuevos hereden la regla y demuéstralo. Explica cuándo una ACL resuelve algo que `ugo/rwx` no puede.

**Parte B — Procesos y señales (60-90 min)**

8. Lanza en segundo plano `sleep 3000 &` y `yes > /dev/null &`. Con `ps -ef --forest`, `ps -o pid,ppid,ni,pri,stat,cmd -p <pid>`, `top` (teclas `P`, `M`, `k`, `r`) y `htop` (instálalo) localiza ambos procesos, su PID, PPID, estado y consumo de CPU. Explica qué significan los estados `R`, `S`, `D`, `Z`, `T`.
9. Señales: envía a `sleep` `kill -STOP`, `kill -CONT`, `kill -TERM` y observa `STAT` tras cada una. Para `yes`, prueba `kill -TERM` y después `kill -KILL`. Lee `man 7 signal` y explica la diferencia entre `SIGTERM`, `SIGKILL`, `SIGHUP` y `SIGINT`, y por qué `kill -9` debe ser el último recurso. ¿Qué señal envía `systemctl stop` por defecto y cuánto espera?
10. Prioridades: lanza `nice -n 15 yes > /dev/null &` y otro `yes` sin `nice`. Compara en `top` el `%CPU` y `NI` de ambos. Cambia la prioridad en caliente con `renice`. Explica qué es el `load average` de `uptime` y qué valor sería preocupante en tu VM (mira `nproc`).
11. Zombis y huérfanos: ejecuta `bash -c 'sleep 30 & exec sleep 60'` en una terminal, y desde otra mira con `ps -ef --forest` quién es el padre de cada proceso pasados 30 s. Explica qué es un proceso huérfano, quién lo adopta y qué es un zombi (puedes provocar uno con un pequeño script Python o C si quieres ir más allá). Termina matando todos tus `yes` y `sleep` con `pkill` y verifica.

**Parte C — Tu propio servicio con systemd, timers y logs (2-3 h)**

12. Crea el script `/opt/acme/bin/informe-sistema.sh` (propietario `svc-informes`, `750`) que escriba en `/var/lib/acme/informes/informe-$(date +%F_%H%M).txt` la fecha, `uptime`, `df -h /`, `free -m` y los 5 procesos con más memoria, y que registre una línea con `logger -t informe-sistema` al empezar y al terminar. Crea `/var/lib/acme/informes` con propietario `svc-informes`. Pruébalo con `sudo -u svc-informes /opt/acme/bin/informe-sistema.sh`.
13. Escribe la unidad `/etc/systemd/system/informe-sistema.service` de tipo `oneshot` que ejecute el script como `User=svc-informes`, con `After=network-online.target` y `Nice=10`. Luego `systemctl daemon-reload`, `systemctl start informe-sistema`, `systemctl status informe-sistema` y `journalctl -u informe-sistema`. Explica cada directiva de las secciones `[Unit]`, `[Service]` e `[Install]`.
14. Timer: crea `informe-sistema.timer` que dispare el servicio cada 15 minutos (`OnCalendar=*:0/15`) con `Persistent=true`. Habilítalo (`systemctl enable --now informe-sistema.timer`), comprueba con `systemctl list-timers` cuándo será la próxima ejecución y espera a ver el primer informe. Compara con la alternativa en `cron`: crea también una entrada en el crontab de `svc-informes` (`sudo crontab -u svc-informes -e`) que ejecute el script a las 07:30 de lunes a viernes, y explica la sintaxis de los cinco campos. Escribe en 8-10 líneas cuándo elegirías cron y cuándo un timer (dependencias, logs, `Persistent`, aleatoriedad, entorno).
15. Servicio de larga duración con reinicio: crea `/opt/acme/bin/latido.sh` (un bucle `while true` que escribe `latido $(date +%T)` con `logger -t latido` cada 10 s) y la unidad `latido.service` de tipo `simple` con `Restart=on-failure`, `RestartSec=5`. Arráncalo, mata el proceso con `kill -9 <pid>` y demuestra con `journalctl -u latido -f` y `systemctl status latido` que systemd lo reinicia y cuenta los reinicios. Cambia a `Restart=always` y explica la diferencia. Habilítalo en el arranque y reinicia la VM para comprobar.
16. `journalctl` en serio. Ejecuta y explica: `journalctl -b`, `journalctl -b -1` (arranque anterior; si no hay, activa persistencia con `mkdir -p /var/log/journal` y `systemctl restart systemd-journald`), `journalctl -p err -b`, `journalctl -u ssh --since "1 hour ago"`, `journalctl _UID=$(id -u svc-informes)`, `journalctl -k | tail`, `journalctl --disk-usage`, `journalctl --vacuum-time=7d`. Explica qué hay todavía en `/var/log` (`auth.log`, `syslog`, `nginx/`, `apt/`) y qué relación tiene `rsyslog` con el journal en Ubuntu. Localiza `logrotate` (`/etc/logrotate.d/`) y explica qué pasaría sin él.

**Parte D — Paquetes en profundidad, variables de entorno y perfiles (60-90 min)**

17. `apt` avanzado. Ejecuta y explica: `cat /etc/apt/sources.list.d/*` (o `sources.list`), `apt-cache policy nginx`, `apt list --installed | wc -l`, `apt-mark hold nginx` (y luego `unhold`), `apt-mark showhold`, `apt changelog nginx | head -20`, `apt install --only-upgrade`, `apt autoremove --dry-run`, `dpkg -S /usr/sbin/nginx`, `dpkg -V nginx`. Revisa `/etc/apt/apt.conf.d/50unattended-upgrades` y `20auto-upgrades`: ¿tu VM aplica parches de seguridad sola? Explica ventajas y riesgos de hacerlo en un servidor.
18. Variables de entorno y perfiles. Ejecuta `env | sort`, `echo $PATH`, `printenv HOME`, `export ACME_ENV=lab`, abre otra shell y comprueba si la ve. Explica la cadena de arranque de una shell de login frente a una no-login (`/etc/profile`, `/etc/profile.d/`, `~/.profile`, `~/.bashrc`, `/etc/environment`). Crea `/etc/profile.d/acme.sh` que exporte `ACME_ENV=lab` para todos los usuarios y demuéstralo entrando como `ana`. Añade una variable de entorno a tu servicio `latido` con `Environment=` y con `EnvironmentFile=` y muéstrala en el log. Explica por qué las credenciales nunca deben ir en variables de entorno visibles en `ps` o en el repositorio (esto vuelve en Docker y Kubernetes).

**Parte E — SSH endurecido (60 min)**

19. Con dos sesiones SSH abiertas, edita `/etc/ssh/sshd_config` (o un archivo en `sshd_config.d/`) para: `PermitRootLogin no`, `PasswordAuthentication no`, `PubkeyAuthentication yes`, `AllowUsers <tu-usuario> ana`, `MaxAuthTries 3`, `X11Forwarding no`. Valida con `sshd -t`, recarga con `systemctl reload ssh` y comprueba: tu usuario entra con clave; `luis` recibe "Permission denied" aunque conozca su contraseña; una conexión con `-o PubkeyAuthentication=no` falla. Mira en `journalctl -u ssh` cómo se registra cada intento y explica qué buscaría un atacante en esas líneas.
20. Opcional: instala `fail2ban`, activa la cárcel `sshd` y prueba tres intentos fallidos desde el anfitrión (con un usuario inexistente). Muestra `fail2ban-client status sshd` y desbanéate. Explica qué protege y qué no.
21. Copia la clave pública de tu anfitrión a `ana` (`~ana/.ssh/authorized_keys` con permisos correctos) y demuestra que `ana` entra por clave. Explica en 5 líneas por qué en Azure las VMs Linux se crean con clave y sin contraseña por defecto.

**Parte F — Storage: disco nuevo, LVM, fstab (2 h)**

22. Añade un disco virtual de 5 GB a la VM apagada, arranca y localízalo con `lsblk`, `sudo fdisk -l` y `ls -l /dev/disk/by-id/`. Anota el nombre (`/dev/sdb` o `/dev/vdb`). Explica por qué **no** debes fiarte del nombre `/dev/sdX` para montar de forma persistente.
23. Particiona con `sudo fdisk /dev/sdb` (o `parted`): tabla GPT y **una** partición de 3 GB de tipo Linux LVM (deja 2 GB libres a propósito). Verifica con `lsblk` y `sudo partprobe`.
24. LVM: `pvcreate /dev/sdb1`, `vgcreate vg-acme /dev/sdb1`, `lvcreate -n lv-datos -L 2G vg-acme`. Muestra `pvs`, `vgs`, `lvs` y `lsblk` y dibuja (texto o imagen) la pila disco → partición → PV → VG → LV → filesystem → punto de montaje. Explica qué problema resuelve LVM frente a particiones clásicas.
25. Formatea con `mkfs.ext4 /dev/vg-acme/lv-datos`, crea `/srv/datos`, monta a mano, escribe un archivo, desmonta. Obtén el UUID con `blkid` y añade una línea a `/etc/fstab` con UUID, `ext4`, opciones `defaults,nofail`. Prueba con `sudo mount -a` y `findmnt /srv/datos` **antes** de reiniciar, reinicia y comprueba. Explica cada campo de `fstab` y por qué `nofail` puede salvarte de una VM que no arranca.
26. Ampliación en caliente: `lvextend -L +500M -r /dev/vg-acme/lv-datos` con el sistema montado y comprueba con `df -h /srv/datos`. Después crea una segunda partición con el espacio libre, añádela al VG (`pvcreate`, `vgextend`) y amplía el LV al 100 % del espacio libre (`lvextend -l +100%FREE -r`). Explica qué harías en Azure para lo mismo (ampliar el disco gestionado y luego `growpart`/LVM dentro de la VM).
27. Mueve `/var/lib/acme/informes` al nuevo volumen (copia con `rsync -a`, cambia la ruta en el script o usa un bind mount o un enlace simbólico) y explica la opción elegida. Comprueba `df -h`, `df -i` (inodos) y `du -sh /srv/datos/*`.

**Parte G — CPU, memoria y red (60-90 min)**

28. Genera carga con `stress-ng` (instálalo) durante 60 s: `stress-ng --cpu 2 --vm 1 --vm-bytes 512M --timeout 60`. Mientras, en otra sesión: `top` (fíjate en `%Cpu(s)`, `us`, `sy`, `wa`, `load average`), `vmstat 2` (columnas `r`, `b`, `si`, `so`, `us`, `sy`, `wa`), `free -h` (explica `available` frente a `free` y `buff/cache`), `cat /proc/loadavg`, `cat /proc/meminfo | head`. Explica qué cifra mirarías primero si un usuario dice "el servidor va lento". ¿Tu VM tiene swap? Mira `swapon --show`; si no, crea un archivo de swap de 1 GB, actívalo y añádelo a `fstab`, y explica cuándo el swap es útil y cuándo es una señal de alarma.
29. Red con `ip` y `ss`: `ip -br a`, `ip -br l`, `ip r`, `ip -s link show <iface>` (errores y descartes), `ss -tulnp`, `ss -tnp state established`, `ss -s`. Identifica cada puerto en escucha y su proceso. Añade una IP secundaria temporal a la interfaz (`ip addr add 192.168.200.10/24 dev <iface>`), compruébala y quítala.
30. `netplan`: lee `/etc/netplan/*.yaml`, explica cada clave, y configura una IP estática (en la misma red que ya tienes, elegida fuera del rango DHCP) con gateway y DNS explícitos usando `netplan try` (te devuelve la configuración anterior si pierdes la conexión). Aplica, verifica con `ip a`, `ip r`, `resolvectl status` y vuelve a DHCP o deja la estática, según prefieras, documentándolo.
31. `ufw`: `ufw status verbose`, `ufw status numbered`. Añade una regla que permita el puerto 8080/tcp **solo** desde la IP de tu anfitrión, una que deniegue explícitamente 23/tcp con registro (`ufw deny log 23/tcp`), y comprueba desde el anfitrión con `nc -zv`. Genera un intento al 23 y encuéntralo en `journalctl -k` o `/var/log/ufw.log`. Mira las reglas reales con `sudo iptables -L -n | head -40` (o `nft list ruleset`) y explica que `ufw` es una capa sobre netfilter. Elimina la regla del 8080 por número.

**Parte H — Tres averías con método (2 h)**

Para cada avería documenta en una tabla: síntoma → hipótesis → comandos y salidas → causa raíz → corrección → verificación → cómo lo habrías detectado antes (alerta, log, métrica). Haz un snapshot antes de cada una.

32. **Disco lleno.** Provoca: `sudo fallocate -l 1500M /var/log/acme-relleno.bin` (ajusta el tamaño hasta dejar el disco raíz al 100 %; compruébalo con `df -h /`). Ahora intenta `sudo apt update`, crea un archivo como `ana`, reinicia `nginx` y mira `journalctl -u nginx`. Diagnostica como si no supieras la causa: `df -h`, `df -i`, `du -xh --max-depth=1 / 2>/dev/null | sort -h | tail`, `sudo find / -xdev -size +200M -type f 2>/dev/null`, `lsof +L1` (archivos borrados pero abiertos). Corrige, verifica y explica por qué borrar un archivo que un proceso tiene abierto no libera espacio y qué hacer en ese caso.
33. **Servicio que no arranca.** Provoca un error en `/etc/nginx/nginx.conf` (una directiva mal escrita) y otro en `latido.service` (`ExecStart` con una ruta inexistente). Reinicia ambos servicios. Diagnostica con `systemctl status`, `journalctl -xeu <unidad>`, `nginx -t`, `systemd-analyze verify /etc/systemd/system/latido.service`, `systemctl cat latido`. Corrige, `daemon-reload` cuando toque, verifica y explica la diferencia entre "el binario falla" y "la unidad está mal escrita" y cómo se distinguen en los logs.
34. **Permisos.** Provoca: `sudo chown root:root /var/lib/acme/informes && sudo chmod 700 /var/lib/acme/informes`, y `sudo chmod 600 /opt/acme/bin/informe-sistema.sh`. Espera al timer (o lanza el servicio a mano). Diagnostica a partir de `systemctl status informe-sistema` y `journalctl -u informe-sistema`: identifica los dos errores distintos ("Permission denied" al ejecutar frente a al escribir), usa `namei -l /var/lib/acme/informes/` para recorrer los permisos de toda la ruta y `sudo -u svc-informes` para reproducir. Corrige y verifica. Explica por qué `namei` es la herramienta que más tiempo te ahorrará en problemas de permisos.

**Parte I — Cierre (30 min)**

35. Deja `lab-so` así para los cursos siguientes: `nginx`, `ssh` (endurecido), `ufw` activo con 22 y 80 (y 443 si quieres), `informe-sistema.timer` y `latido.service` activos, el volumen LVM montado. Elimina `marta` y `luis` (conserva `ana` y `svc-informes`). Haz un snapshot final llamado `fin-admin-linux`.
36. Escribe una sección "Runbook de `lab-so`" (media página): cómo ver el estado de los servicios propios, dónde están los logs, cómo ampliar el disco, qué reglas de firewall hay y por qué, y qué harías primero ante cada uno de los tres síntomas de la Parte H. Este runbook lo reutilizarás en el curso de DevOps y SRE.

### Resultado esperado

- `laboratorio-linux-admin.md` con las nueve partes, comandos, salidas, explicaciones, el diagrama de la pila de almacenamiento y la tabla de las tres averías.
- Carpeta `systemd/` con `informe-sistema.service`, `informe-sistema.timer` y `latido.service`; carpeta `scripts/` con `informe-sistema.sh` y `latido.sh`; `sudoers-ops` (copia de `/etc/sudoers.d/ops`); `fstab` (copia de la línea añadida); `netplan.yaml` (con IPs, sin secretos).
- `runbook-lab-so.md`.
- La VM operativa y con snapshot final.

### Criterios de validación

- [ ] Parte A: `sudoers.d/ops` funciona exactamente como se pide; `setgid`, `sticky`, `setuid`, `umask` y la ACL están demostrados con salidas reales y explicados con precisión.
- [ ] Parte B: se distinguen correctamente las señales, los estados de proceso, `nice`/`renice`, y hay evidencia del huérfano adoptado.
- [ ] Parte C: el servicio `oneshot` y el timer funcionan; `latido` se reinicia solo tras `kill -9` y sobrevive al reinicio; la comparación cron/timer está razonada; los comandos de `journalctl` están explicados.
- [ ] Parte D: `hold`/`unhold` y `apt-cache policy` explicados; la cadena de perfiles de shell está correcta; la variable llega al servicio por `EnvironmentFile`.
- [ ] Parte E: `sshd -t` limpio; solo clave; `luis` no entra; `AllowUsers` aplicado; el estudiante no se quedó fuera (o documentó cómo recuperó el acceso).
- [ ] Parte F: `lsblk`, `pvs/vgs/lvs` y `fstab` con UUID coherentes; el montaje sobrevive al reinicio; la ampliación en caliente está demostrada con `df` antes y después.
- [ ] Parte G: las métricas de CPU/memoria están interpretadas (no solo pegadas); `netplan try` usado; reglas `ufw` correctas y relación con netfilter explicada.
- [ ] Parte H: las tres averías tienen causa raíz correcta, corrección verificada y una propuesta de detección temprana razonable.
- [ ] El runbook permite a otra persona operar la VM sin preguntarte.
- [ ] En una llamada con el mentor, el estudiante resuelve un reto de 10 minutos (por ejemplo, "crea un timer que ejecute X cada hora como el usuario Y" o "averigua por qué este servicio no arranca") sin buscar los comandos.

## Entrega

En tu repositorio de entregas, carpeta `02-modulo-intermedio/01-administracion-de-linux/`:

1. `laboratorio-linux-admin.md`.
2. `systemd/`, `scripts/`, `sudoers-ops`, `fstab`, `netplan.yaml` (sin contraseñas ni claves privadas).
3. `runbook-lab-so.md`.
4. `capturas/` (con usuario y `hostname` visibles).
5. `ENTREGA.md` con evaluación, checklist y uso de IA.

Nota sobre IA: pedir a una IA "una unidad de systemd para mi script" es legítimo, pero en `ENTREGA.md` debes poder explicar cada directiva y haber comprobado en `man systemd.service` que existe y hace lo que la IA dice. Los modelos inventan directivas con frecuencia.

## Evaluación

1. **Conceptual.** Explica con un ejemplo de tu laboratorio la diferencia entre `setuid`, `setgid` en un directorio y `sticky bit`. ¿Por qué `/tmp` necesita el sticky bit y `/srv/acme/dev` el `setgid`?
2. **Técnica.** Un archivo se crea con permisos `640` aunque el usuario ejecutó `touch` sin más. ¿Qué `umask` tiene y dónde puede estar configurada? ¿Qué permisos tendría un directorio creado en la misma sesión?
3. **Situacional.** Un desarrollador necesita leer los logs de nginx pero no debe poder hacer nada más con `sudo`. Describe dos formas de conseguirlo (una con grupos/ACL, otra con `sudoers`) y cuándo elegirías cada una.
4. **Conceptual.** ¿Qué diferencia hay entre `SIGTERM` y `SIGKILL`? ¿Por qué un servicio bien escrito debe manejar `SIGTERM`? ¿Qué hace `systemctl stop` si el proceso no termina a tiempo?
5. **Troubleshooting.** `systemctl status miapp` muestra `activating (auto-restart)` y `Result: exit-code` repitiéndose cada 5 segundos. Escribe los tres comandos que ejecutarías, qué buscarías en cada salida y dos causas raíz probables.
6. **Conceptual.** Compara cron y timers de systemd en: registro de ejecuciones, comportamiento si la máquina estaba apagada a la hora programada, dependencias de red y facilidad de depuración. Da un caso para cada uno.
7. **Técnica.** Explica esta línea de `fstab`: `UUID=3f2a...  /srv/datos  ext4  defaults,nofail  0  2`. ¿Qué pasaría en el arranque si el disco no existiera con y sin `nofail`? ¿Por qué UUID y no `/dev/sdb1`?
8. **Situacional.** El disco raíz de un servidor está al 100 %. Has borrado un log de 3 GB pero `df` sigue mostrando 100 %. ¿Qué ha pasado y cómo liberas el espacio sin reiniciar?
9. **Técnica.** Dibuja o describe la pila de LVM de tu laboratorio y explica cómo ampliarías `/srv/datos` en 10 GB si el VG ya no tiene espacio libre, tanto en tu VM como en una VM de Azure.
10. **Conceptual.** `free -h` muestra 1,8 GB "used", 100 MB "free" y 1,5 GB "available" en una VM de 4 GB. ¿Hay problema de memoria? Explica `buff/cache` y `available`. ¿Qué columnas de `vmstat` confirmarían presión de memoria real?
11. **Situacional.** Cambias `sshd_config` para permitir solo clave y, sin querer, te desconectas antes de probar. Ya no puedes entrar. ¿Qué hábito lo habría evitado? ¿Cómo recuperarías el acceso en tu VM local y cómo en una VM de Azure (piensa en la consola serie o en restablecer la configuración desde el portal)?
12. **Técnica.** Escribe una unidad `.service` mínima para un script que debe ejecutarse como el usuario `svc-informes`, después de que haya red, reiniciarse si falla y arrancar con el sistema. Explica qué hace `systemctl enable` con el `WantedBy`.
13. **Troubleshooting.** Un servicio registra "Permission denied" al escribir en `/var/lib/app/data/salida.txt`. El archivo tiene `666`. ¿Qué otras causas hay y cómo las descubres con un solo comando sobre la ruta completa?
14. **Conceptual.** Explica qué hace `ufw` en relación con netfilter/`iptables`/`nftables`, y cómo se traduce una regla `ufw allow from 203.0.113.10 to any port 8080 proto tcp` a un NSG de Azure.
15. **Reflexión.** ¿Cuál de las tres averías te costó más y qué hábito o comando te llevas? ¿Qué añadirías al runbook si esta VM fuera un servidor real con clientes?

## Checklist final

Antes de continuar, deberías poder:

- [ ] Crear usuarios con caducidad, bloquearlos, y escribir reglas `sudoers` acotadas con `visudo`.
- [ ] Explicar y aplicar `setuid`, `setgid`, `sticky bit`, `umask` y ACLs.
- [ ] Inspeccionar procesos, enviar señales, cambiar prioridades e identificar zombis y huérfanos.
- [ ] Escribir una unidad `.service` y un `.timer` propios, y elegir entre cron y timer con criterio.
- [ ] Filtrar el journal por unidad, prioridad, tiempo y arranque, y saber qué queda en `/var/log`.
- [ ] Gestionar paquetes con `apt` más allá de `install` (`policy`, `hold`, `unattended-upgrades`).
- [ ] Explicar la cadena de perfiles de shell y pasar variables a un servicio de forma segura.
- [ ] Endurecer SSH sin quedarte fuera y leer los intentos de acceso en el journal.
- [ ] Añadir un disco, crear PV/VG/LV, formatear, montar por UUID en `fstab` y ampliar en caliente.
- [ ] Interpretar `top`, `vmstat`, `free` y `df`/`du` para decir dónde está el cuello de botella.
- [ ] Configurar red con `netplan try`, inspeccionar con `ip`/`ss` y controlar `ufw`.
- [ ] Diagnosticar con método un disco lleno, un servicio que no arranca y un problema de permisos.
- [ ] Tener `lab-so` operativa, endurecida y con snapshot para los cursos siguientes.

---

*Recursos verificados el 2026-09-27 mediante búsqueda web (existencia y vigencia de las URLs). Si un enlace falla, abre un issue en este repositorio.*
