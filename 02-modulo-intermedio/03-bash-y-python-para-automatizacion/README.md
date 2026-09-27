# Bash y Python para Automatización

> Módulo: Intermedio · Curso 3 de 11 · Duración estimada: 30-40 horas · Estado: ✅ Completo

## Objetivo

Hasta ahora has administrado máquinas escribiendo comandos uno a uno. Eso no escala: en cuanto tengas tres servidores, un backup diario y una comprobación de salud cada media hora, o lo automatizas o se te olvida. Este curso te enseña a **convertir lo que ya sabes hacer a mano en scripts fiables**: que fallen de forma visible, que registren lo que hacen, que acepten parámetros, que se puedan ejecutar desde `cron`, desde un timer de systemd o desde un pipeline de CI/CD sin que nadie los mire.

Aprenderás dos herramientas con papeles distintos. **Bash** para pegar comandos del sistema: backups, rotaciones, comprobaciones, despliegues sencillos; es lo que corre en cualquier servidor Linux y dentro de casi todos los pipelines. **Python** para todo lo que implique datos estructurados: leer JSON de una API o de `az`, parsear logs, generar informes, hablar con servicios HTTP; es el lenguaje de la automatización en Cloud, DevOps y SRE, y el que usarás en los cursos de IA de esta ruta.

El criterio para elegir entre ambos es simple y lo practicarás: si el script es "ejecutar comandos y comprobar códigos de salida" y cabe en 100 líneas, Bash; si hay que parsear, estructurar o hablar con una API, Python. Y una regla de oro para los dos: **un script que no gestiona errores no es una automatización, es una bomba de relojería.**

**Antes de empezar** necesitas la VM `lab-so` del curso de Administración de Linux (con `nginx`, systemd, timers y el volumen `/srv/datos`) y tu repositorio de entregas en Git. La Azure CLI se usa en un único ejercicio de solo lectura, sin coste.

### Al terminar este curso deberías poder

- Escribir scripts Bash con variables, condiciones, bucles, funciones, arrays, parámetros (`$1`, `getopts`), lectura de archivos y códigos de salida correctos.
- Aplicar `set -euo pipefail`, `trap`, comillas correctas, `[[ ]]`, `local` y `shellcheck` para que un script Bash falle pronto, limpie tras de sí y no tenga sorpresas.
- Escribir un script de backup con rotación, logging, bloqueo, verificación de integridad y ejecución programada, y un script de comprobación de salud que envíe un resumen.
- Explicar qué son `stdin`, `stdout`, `stderr` y los códigos de salida, y usarlos para encadenar scripts entre sí y con systemd.
- Crear y usar entornos virtuales de Python (`venv`) y gestionar dependencias con `pip` y `requirements.txt`.
- Leer, transformar y escribir JSON en Python, incluida la salida de comandos del sistema (`ip -j`, `az -o json`).
- Consumir una API HTTP con `requests`: cabeceras, parámetros, códigos de estado, tiempo de espera, errores y límites de peticiones.
- Parsear logs de nginx con expresiones regulares y generar un informe en Markdown y JSON.
- Estructurar un script Python con `argparse`, `logging`, funciones pequeñas, manejo de excepciones y una prueba mínima.
- Llamar a la Azure CLI desde Python en modo solo lectura y decidir cuándo usar la CLI y cuándo un SDK.

## Prerrequisitos

- Curso 1 del Módulo Intermedio: Administración de Linux (systemd, timers, `journalctl`, permisos).
- Fundamentos de Git del Módulo Básico (los scripts se entregan versionados).
- VM `lab-so` con `python3`, `python3-venv`, `python3-pip`, `shellcheck`, `jq` y `git` (`sudo apt install -y python3-venv python3-pip shellcheck jq git`).
- Azure CLI instalada en la VM o en el anfitrión, con `az login` funcionando (solo lectura en este curso).
- Un editor cómodo: `nano` o `vim` en la VM, o VS Code en el anfitrión editando por SSH (extensión Remote-SSH, gratuita).

## Temario

Variables · Condiciones · Loops · Funciones · Parámetros · Archivos · Variables de entorno · Manejo de errores · JSON · HTTP · APIs · Automatización de tareas administrativas.

**Práctica:** automatizar tareas repetitivas de administración de sistemas.

## Recursos en español

### Curso de Bash y Terminal desde cero, parte de scripting — MoureDev (Brais Moure)
- **URL:** https://www.youtube.com/watch?v=ABgLEKFhlZE · Repositorio con apuntes y ejercicios: https://github.com/mouredev/hello-bash-shell
- **Autor / organización:** Brais Moure (MoureDev), ingeniero de software y divulgador en español
- **Idioma:** Español
- **Tipo:** Vídeo largo + repositorio
- **Duración aproximada:** ~3 h de la segunda mitad del vídeo (variables, condicionales, bucles, funciones, parámetros, lectura de archivos, scripts)
- **Cubre:** Variables, condiciones, loops, funciones, parámetros, archivos, variables de entorno.
- **Nivel:** Introductorio
- **Acceso:** Libre (la versión con extras en mouredev.pro es de pago y no es necesaria)
- **Por qué lo recomiendo:** Ya viste la primera mitad en Linux Básico. La segunda mitad es la introducción al scripting más clara que hay en español, con ejercicios en el repositorio. Después de verla, pasa al libro de Shotts y a ShellCheck para aprender a hacerlo **bien**, no solo a hacerlo.

### Hello Python: curso de Python desde cero — MoureDev (Brais Moure)
- **URL:** https://github.com/mouredev/Hello-Python (los vídeos están enlazados desde el README)
- **Autor / organización:** Brais Moure (MoureDev)
- **Idioma:** Español
- **Tipo:** Repositorio con código comentado + vídeos en YouTube
- **Duración aproximada:** Para este curso, las lecciones de fundamentos (~8 h): variables, tipos, condicionales, bucles, listas y diccionarios, funciones, excepciones, archivos, módulos, y la lección de peticiones HTTP/APIs. El resto (frontend, backend, IA) no hace falta ahora.
- **Cubre:** Variables, condiciones, loops, funciones, parámetros, archivos, manejo de errores, JSON, HTTP y APIs.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es el curso de Python en español más seguido, actualizado y con el código de cada lección en el repositorio para que lo ejecutes y lo modifiques. Es tu recurso principal si nunca has programado en Python. Si ya lo has hecho, salta directamente al tutorial oficial.

### Documentación oficial de Python en español (tutorial y biblioteca estándar) — Python Software Foundation, traducción de la comunidad python-docs-es
- **URL:** https://python-docs-es.readthedocs.io/ (proyecto de traducción: https://github.com/python/python-docs-es)
- **Autor / organización:** Python Software Foundation; traducción coordinada por la comunidad hispanohablante de Python
- **Idioma:** Español
- **Tipo:** Documentación oficial (tutorial, referencia de la biblioteca)
- **Duración aproximada:** 6-8 h para el tutorial (capítulos 3 a 10: introducción informal, control de flujo, estructuras de datos, módulos, entrada y salida, errores y excepciones, breve recorrido por la biblioteca) y consulta de `json`, `argparse`, `subprocess`, `logging`, `pathlib`, `re`, `venv`
- **Cubre:** Todo el temario de Python: variables, condiciones, loops, funciones, parámetros, archivos, manejo de errores, JSON.
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la documentación oficial traducida por la propia comunidad de Python en español. El tutorial es la referencia del curso; los módulos `json`, `argparse`, `subprocess` y `logging` los vas a usar en el laboratorio y aquí están descritos con precisión. Cuando una IA te proponga una función, compruébala aquí.

## Recursos en inglés

### The Linux Command Line, Parte 4: Writing Shell Scripts — William Shotts
- **URL:** https://linuxcommand.org/tlcl.php (PDF gratuito, licencia Creative Commons)
- **Autor / organización:** William Shotts
- **Idioma:** Inglés
- **Tipo:** Libro (PDF)
- **Duración aproximada:** 6-8 h para los capítulos 24 a 36 (escribir el primer script, diseño top-down, control de flujo con `if`, `read`, `while`/`until`, `case`, `for`, parámetros posicionales, arrays, troubleshooting, expansiones)
- **Cubre:** Variables, condiciones, loops, funciones, parámetros, archivos, manejo de errores en Bash.
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Ya lo conoces de Linux Básico. La Parte 4 es el mejor texto gratuito para aprender a escribir Bash con cabeza: explica **por qué** las comillas importan, qué son los códigos de salida y cómo depurar. El capítulo de troubleshooting de scripts es lectura obligatoria antes del laboratorio.

### ShellCheck — Vidar Holen (koalaman)
- **URL:** https://www.shellcheck.net (versión web) · Repositorio y wiki de cada aviso: https://github.com/koalaman/shellcheck
- **Autor / organización:** Vidar Holen y colaboradores (código abierto, GPLv3)
- **Idioma:** Inglés
- **Tipo:** Herramienta (analizador estático) con wiki explicativa
- **Duración aproximada:** Uso continuo; 30 min para leer los avisos más comunes (SC2086 comillas, SC2046, SC2164 `cd` sin comprobar, SC2181)
- **Cubre:** Manejo de errores y buenas prácticas en Bash.
- **Nivel:** Todos
- **Acceso:** Libre (en la VM: `sudo apt install shellcheck`)
- **Por qué lo recomiendo:** Es el corrector ortográfico de Bash. Cada aviso enlaza a una página de la wiki que explica el problema y la solución con ejemplos: aprenderás más Bash leyendo esas páginas que en muchos cursos. Regla del laboratorio: **ningún script se entrega con avisos de ShellCheck sin justificar.** En CI/CD lo integrarás como paso del pipeline.

### Python for Everybody (PY4E) — Charles Severance (Dr. Chuck), Universidad de Michigan
- **URL:** https://www.py4e.com/ (libro, vídeos, ejercicios; el código fuente está en https://github.com/csev/py4e)
- **Autor / organización:** Charles Severance, Universidad de Michigan
- **Idioma:** Inglés (el libro tiene traducciones a varios idiomas, español incluido, enlazadas desde la propia web)
- **Tipo:** Libro libre + vídeos + ejercicios autocorregidos
- **Duración aproximada:** 8-10 h para los capítulos 1 a 9 (variables, condicionales, funciones, iteración, cadenas, archivos, listas, diccionarios) y los capítulos 11 (expresiones regulares), 12 (programas en red) y 13 (servicios web: JSON y APIs)
- **Cubre:** Variables, condiciones, loops, funciones, archivos, JSON, HTTP, APIs, expresiones regulares.
- **Nivel:** Introductorio
- **Acceso:** Libre, sin registro (el registro opcional permite guardar ejercicios)
- **Por qué lo recomiendo:** Es el curso de Python más usado del mundo para gente que no viene de programación, y sus capítulos de expresiones regulares y servicios web son exactamente lo que necesitas para el parser de logs y el cliente de API del laboratorio. Complementa a MoureDev con ejercicios corregidos.

### Requests: HTTP for Humans (documentación) — Python Software Foundation / Kenneth Reitz
- **URL:** https://requests.readthedocs.io/en/latest/ (repositorio: https://github.com/psf/requests)
- **Autor / organización:** Proyecto `requests`, bajo la Python Software Foundation
- **Idioma:** Inglés
- **Tipo:** Documentación oficial de biblioteca
- **Duración aproximada:** 60-90 min para Quickstart y Advanced Usage (sesiones, tiempo de espera, reintentos, cabeceras, autenticación, códigos de estado, `raise_for_status`)
- **Cubre:** HTTP, APIs, manejo de errores en peticiones.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** `requests` es la biblioteca HTTP estándar de facto en Python y la que usarás en el laboratorio, en el curso de IA aplicada y en cualquier script que hable con una API. Lee especialmente la parte de tiempos de espera y errores: un script que llama a una API sin `timeout` se puede quedar colgado para siempre.

## Documentación oficial

- **Python (sitio oficial):** https://www.python.org · Documentación en español: https://python-docs-es.readthedocs.io/ (tutorial y módulos `json`, `argparse`, `subprocess`, `logging`, `pathlib`, `re`, `venv`, `unittest`)
- **Requests:** https://requests.readthedocs.io/en/latest/
- **Bash:** en la VM, `man bash` (secciones "Parameter Expansion", "Conditional Expressions", "SHELL BUILTIN COMMANDS", con `help set`, `help trap`, `help getopts`) · Índice de manuales: https://man7.org/linux/man-pages/
- **ShellCheck (wiki de avisos):** https://github.com/koalaman/shellcheck
- **Azure CLI (referencia de comandos, `--query` con JMESPath, formatos de salida):** https://learn.microsoft.com/cli/azure/ · Documentación de Azure en español: https://learn.microsoft.com/es-es/azure/
- **GitHub Docs (sección REST API: puntos de conexión, límites de peticiones sin autenticar, autenticación):** https://docs.github.com
- **The Linux Command Line (Parte 4):** https://linuxcommand.org/tlcl.php

## Ruta recomendada de estudio

1. **Ver** la parte de scripting del curso de Bash de MoureDev (3 h, en dos sesiones) escribiendo cada ejemplo en la VM.
2. **Leer** The Linux Command Line, capítulos 24 a 30 (3 h) y **hacer** la Parte A y B del laboratorio (ejercicios Bash cortos). Pasa cada script por `shellcheck` y lee la wiki de cada aviso.
3. **Leer** The Linux Command Line, capítulos 31 a 36 (2 h), en especial el de troubleshooting, y **hacer** la Parte C (backup) y D (healthcheck).
4. **Hacer** las lecciones de fundamentos de Hello-Python o los capítulos 1 a 9 de PY4E (8 h, en varios días). Si ya sabes Python, **leer** el tutorial oficial en español, capítulos 3 a 8, en su lugar (4 h).
5. **Hacer** la Parte E (entorno virtual y JSON) leyendo la documentación de `json`, `subprocess` y `argparse`.
6. **Leer** el Quickstart de `requests` y el capítulo 13 de PY4E (90 min) y **hacer** la Parte F (API de GitHub).
7. **Leer** el capítulo 11 de PY4E (expresiones regulares) y la documentación de `re` (60 min) y **hacer** la Parte G (informe de nginx).
8. **Leer** en la documentación de Azure CLI la página de formatos de salida y consultas `--query` (30 min) y **hacer** la Parte H (inventario de Azure).
9. **Hacer** la Parte I (pruebas, programación y cierre).
10. **Responder la evaluación** y **revisar el checklist**.

Si vas justo de tiempo: obligatorios los puntos 2, 3, 4 (una de las dos opciones), 6 y 7. La Parte H se puede posponer al curso de Administración de Azure.

## Laboratorio

### Objetivo

Construir una pequeña caja de herramientas de automatización para `lab-so`, versionada en Git: dos scripts Bash de producción (backup con rotación y comprobación de salud con resumen) y cuatro utilidades Python (inventario del sistema desde JSON, cliente de la API de GitHub, informe de logs de nginx e inventario de Azure en solo lectura), todas con manejo de errores, parámetros, logging y una prueba mínima, y programadas con systemd donde tenga sentido.

### Requisitos

- `lab-so` con lo indicado en prerrequisitos. Si el volumen `/srv/datos` del curso anterior no existe, usa `/var/backups/acme`.
- Repositorio Git `automatizacion/` dentro de tu carpeta de entrega, con esta estructura:
  ```
  automatizacion/
  ├── bash/         # ejercicios, backup.sh, healthcheck.sh
  ├── python/       # inventario.py, github_info.py, nginx_report.py, azure_inventario.py
  ├── systemd/      # unidades y timers
  ├── tests/        # pruebas mínimas
  ├── datos/        # JSON de ejemplo (sin secretos)
  ├── requirements.txt
  └── README.md     # cómo usar cada herramienta
  ```
- `.gitignore` con `.venv/`, `*.log`, `*.tar.gz`, `datos/privado/`. **Nunca** subas tokens, IDs de suscripción completos ni la salida cruda de `az account show`.
- Documenta en `laboratorio-automatizacion.md` las decisiones, las pruebas y los fallos que encontraste.

> **Sobre el coste.** El único ejercicio con Azure (Parte H) usa solo comandos de lectura (`az group list`, `az resource list`, `az vm list`). No crea recursos y no cuesta nada. Si tu suscripción está vacía, crea antes un grupo de recursos vacío con etiquetas para tener algo que listar y bórralo al terminar (`az group delete`); un grupo vacío no cuesta nada.

### Instrucciones

**Parte A — Bash: fundamentos con ejercicios cortos (2 h)**

1. Escribe en `bash/01-basicos.sh` un script que reciba un nombre de directorio como parámetro (`$1`), compruebe que existe (`[[ -d ]]`) y que es legible, y muestre: número de archivos, número de subdirectorios, el archivo más grande y el más reciente. Sin parámetro debe imprimir el uso por `stderr` y salir con código `2`. Explica en un comentario qué son `$0`, `$1`, `$#`, `$@`, `$?` y por qué `"$@"` lleva comillas.
2. `bash/02-usuarios-csv.sh`: dado un CSV `datos/usuarios.csv` (`usuario,grupo,shell`), recórrelo con `while IFS=, read -r usuario grupo shell` y para cada línea cree el grupo si no existe y el usuario con su shell. Debe aceptar `--dry-run` (imprime lo que haría sin hacerlo) y saltar las líneas de comentario y la cabecera. Usa una función `log()` con fecha, `local` en las variables de función y comprueba el código de salida de `useradd`. Pruébalo en `dry-run`, luego de verdad, y borra los usuarios creados al final.
3. `bash/03-arrays-case.sh`: un menú con `case` que acepte `start|stop|status|logs` y un nombre de servicio, con un array de servicios permitidos (`nginx ssh latido`) y rechazo de cualquier otro. Añade `getopts` para una opción `-n <líneas>` que controle cuántas líneas de `journalctl` muestra `logs`.
4. Pasa los tres scripts por `shellcheck` hasta que no quede ningún aviso. Para cada aviso que hayas tenido, copia en el laboratorio el código SC, qué significaba y cómo lo arreglaste. Lee el capítulo de troubleshooting de Shotts y explica con ejemplos propios: expansión sin comillas, `[ ]` frente a `[[ ]]`, `=` frente a `==` frente a `-eq`, y por qué `cd dir && cmd` es más seguro que `cd dir; cmd`.

**Parte B — Bash: manejo de errores de verdad (60-90 min)**

5. Escribe `bash/04-errores.sh` con `set -euo pipefail` y demuestra cada opción con un ejemplo que falle sin ella: `-e` (comando que falla en medio), `-u` (variable no definida, típico `rm -rf "$DIR/"` con `DIR` vacía), `-o pipefail` (`grep` sin coincidencias en una tubería). Documenta la salida y el `$?` en cada caso.
6. Añade `trap 'limpiar' EXIT` y `trap 'error_handler $LINENO' ERR` con funciones que borren un directorio temporal creado con `mktemp -d` y que registren la línea que falló. Provoca un fallo y demuestra que la limpieza se ejecuta igual. Explica la diferencia entre `EXIT`, `ERR`, `INT` y `TERM`, y qué relación tiene `TERM` con `systemctl stop` (lo viste en el curso anterior).
7. Explica en 8-10 líneas, con ejemplos, `stdout` frente a `stderr` (`>&2`), `2>&1`, `|&`, `tee`, `exec > >(tee -a log)` y por qué los mensajes de error nunca deben ir a `stdout` en un script que otro script va a consumir.

**Parte C — Backup con rotación, logging y systemd (3 h)**

8. Escribe `bash/backup.sh` que:
   - Acepte `--origen <ruta>` (repetible), `--destino <dir>` (por defecto `/srv/datos/backups`), `--conservar <n>` (por defecto 7), `--dry-run` y `--help`, con `getopts` o un bucle `while [[ $# -gt 0 ]]; do case "$1" ...`.
   - Use `set -euo pipefail`, `trap` para limpieza y errores, y `flock` sobre un archivo de bloqueo para que no corran dos copias a la vez (demuéstralo lanzándolo dos veces).
   - Cree `backup-<hostname>-<AAAAMMDD-HHMMSS>.tar.gz` con `tar` de `/etc`, `/var/www` y `/var/lib/acme` (o lo que tengas), excluyendo `*.tmp` y `*.sock`, y escriba un `.sha256` junto al archivo.
   - Verifique el archivo (`tar -tzf` y `sha256sum -c`) antes de dar por buena la copia.
   - Rote: conserve solo las `n` copias más recientes (cuidado con `ls | xargs rm`: usa `find -printf` o un array ordenado, y `shellcheck` te dirá por qué).
   - Registre cada paso con fecha en `/var/log/acme/backup.log` y en el journal (`logger -t backup`), y termine con código `0` solo si todo fue bien; si falla, código distinto de cero y una línea `ERROR` clara.
   - Pase `shellcheck` sin avisos.
9. Pruebas obligatorias, documentadas con salidas: ejecución normal; `--dry-run`; destino sin permisos de escritura (debe fallar limpiamente y dejar el log); disco "lleno" (usa un `tmpfs` pequeño: `sudo mount -t tmpfs -o size=5M tmpfs /mnt/pequeno` y apunta ahí el destino); ejecución simultánea (`flock`); rotación (crea 10 copias con `--conservar 3` y demuestra que quedan 3). Restaura un archivo concreto de una copia con `tar -xzf ... ruta/al/archivo` y compáralo con el original.
10. Crea `systemd/backup.service` (`oneshot`, `User=root`, `Nice=10`, `IOSchedulingClass=idle`) y `systemd/backup.timer` (`OnCalendar=*-*-* 02:30`, `Persistent=true`, `RandomizedDelaySec=15m`). Instala, habilita, fuerza una ejecución (`systemctl start backup`) y muestra `journalctl -u backup` y `systemctl list-timers`. Explica qué pasaría si el script fallara: ¿cómo te enterarías? (pista: `systemctl --failed`, `OnFailure=`, y el healthcheck de la siguiente parte).

**Parte D — Comprobación de salud con resumen (2 h)**

11. Escribe `bash/healthcheck.sh` que compruebe y puntúe como `OK`/`WARN`/`CRIT`: servicios systemd esperados activos (lista en un array o en un archivo de configuración `datos/servicios.txt`), uso de disco de `/` y `/srv/datos` (umbrales `80`/`90` %), memoria disponible (`free`), carga media frente a `nproc`, respuesta HTTP `200` de `http://localhost` con `curl -fsS -m 5 -o /dev/null -w '%{http_code}'`, puertos esperados en escucha (`ss -tln`), fecha del último backup correcto (leyendo el log de la Parte C; `CRIT` si tiene más de 26 horas) y timers activos.
12. El script genera un resumen en Markdown (`/var/log/acme/healthcheck-<fecha>.md`) con una tabla comprobación/estado/valor/umbral, imprime la misma tabla por `stdout`, envía una línea por comprobación al journal con la prioridad correcta (`logger -p user.warning` / `user.err`) y sale con `0` si todo es `OK`, `1` si hay `WARN`, `2` si hay `CRIT`. **Envío del resumen:** si existe la variable de entorno `HEALTHCHECK_WEBHOOK` (cárgala con `EnvironmentFile=` desde `/etc/acme/healthcheck.env`, permisos `600`), envía el resumen con `curl -X POST` a ese webhook (sirve cualquier servicio gratuito de notificaciones tipo Discord, Slack, Telegram o ntfy, o un `python3 -m http.server` propio para probar); si no existe, deja constancia y no falla. Nunca escribas la URL del webhook en el script ni en Git.
13. Provoca un `WARN` (para `latido`) y un `CRIT` (llena `/mnt/pequeno` o para `nginx`), ejecuta el script y muestra el resumen y el código de salida en cada caso. Prográmalo con `systemd/healthcheck.timer` cada 30 minutos y explica cómo systemd refleja el código de salida `2` en `systemctl status` y `systemctl --failed`.

**Parte E — Python: entorno virtual y JSON (2 h)**

14. En `automatizacion/`, crea el entorno virtual: `python3 -m venv .venv && source .venv/bin/activate`, `pip install requests`, `pip freeze > requirements.txt`. Explica qué hay dentro de `.venv/`, por qué no se sube a Git, qué hace `activate` con `PATH` y por qué **no** se instalan paquetes con `pip` fuera de un `venv` en Ubuntu moderno (prueba `pip install requests` sin activar y lee el error `externally-managed-environment`).
15. `python/inventario.py`: ejecuta con `subprocess.run([...], capture_output=True, text=True, check=True)` los comandos `ip -j addr show`, `ip -j route show`, `lsblk -J` y `ps -eo pid,user,%mem,%cpu,comm --no-headers`, convierte cada salida a estructuras Python (`json.loads` para las tres primeras; para `ps`, parsea tú las columnas y construye una lista de diccionarios) y genera `datos/inventario-<hostname>.json` con: interfaces e IPs, ruta por defecto, discos y puntos de montaje, y los 5 procesos con más memoria. Acepta `--salida <archivo>` y `--pretty`. Maneja con `try/except` el caso de que un comando no exista (`FileNotFoundError`) o falle (`subprocess.CalledProcessError`) y termina con un código de salida distinto de cero y un mensaje en `stderr`. Compara el resultado con `jq` en la terminal (`jq '.interfaces[].ip' datos/inventario-*.json`).
16. Guarda en `datos/az-group-list.json` la salida de `az group list -o json` (o un JSON de ejemplo con la misma forma si aún no quieres tocar Azure) y escribe una función `resumir_grupos(ruta)` que devuelva por región el número de grupos y la lista de los que no tienen la etiqueta `propietario`. Úsala desde `inventario.py` con `--azure-json <ruta>`. Esto prepara la Parte H y te enseña a trabajar con datos guardados sin depender de la red.

**Parte F — Python: consumir una API HTTP con requests (2 h)**

17. `python/github_info.py`: con `argparse`, acepta `--owner`, `--repo`, `--usuario` (para listar repos públicos de un usuario) y `--json` (salida en JSON en vez de texto). Consulta sin autenticación `https://api.github.com/repos/<owner>/<repo>`, `.../releases/latest` y `https://api.github.com/users/<usuario>/repos?per_page=100&sort=updated`, y muestra: descripción, estrellas, licencia, fecha del último push, última versión publicada y sus notas resumidas, o la lista de repos con su lenguaje. Usa una `requests.Session()` con `headers={"Accept": "application/vnd.github+json", "User-Agent": "lab-automatizacion"}` y **siempre** `timeout=10`.
18. Manejo de errores obligatorio y demostrado con salidas: repo inexistente (`404`, mensaje claro, código de salida `1`); sin red (desconecta el adaptador de la VM o usa `--api-url http://10.255.255.1` para provocar `ConnectionError`/`Timeout`); límite de peticiones (`403` o `429` con cabeceras `X-RateLimit-Remaining` y `X-RateLimit-Reset`: muéstralas y explica cuánto permite la API sin autenticar). Consulta `https://api.github.com/rate_limit` y explica el resultado. Si el usuario define `GITHUB_TOKEN` en el entorno, úsalo como `Authorization: Bearer` y demuestra que el límite cambia; **el token nunca va en el código ni en Git**.
19. Explica en el laboratorio: qué es un código de estado y por qué `raise_for_status()` es tu amigo; qué diferencia hay entre `response.text`, `response.json()` y `response.content`; qué pasa si no pones `timeout`; qué es la paginación (cabecera `Link`) y cómo la implementarías.

**Parte G — Python: informe de logs de nginx (2-3 h)**

20. Genera tráfico realista en `lab-so`: un bucle con `curl` a `/`, a rutas inexistentes (404), con distintos `User-Agent`, y si conservas el laboratorio del curso anterior, tráfico HTTPS a `web.acme.lab`. Copia `/var/log/nginx/access.log` a `datos/access.log` (revisa que no contenga nada privado).
21. `python/nginx_report.py`: parsea el formato `combined` de nginx con una expresión regular (grupos con nombre: `ip`, `fecha`, `metodo`, `ruta`, `protocolo`, `estado`, `bytes`, `referer`, `agente`), tolera líneas malformadas (cuéntalas y no rompas), y produce: total de peticiones, peticiones por código de estado, top 10 IPs, top 10 rutas, top 5 rutas con 404, bytes totales, peticiones por hora, porcentaje de errores 4xx y 5xx. Opciones: `--log <ruta>`, `--top <n>`, `--desde <AAAA-MM-DD>`, `--formato md|json`, `--salida <archivo>`. Usa `collections.Counter`, `datetime.strptime`, `logging` (nivel configurable con `-v`) y funciones pequeñas con docstring. Ejecuta y guarda `informe-nginx.md` e `informe-nginx.json`.
22. Añade una regla sencilla de "sospecha": IPs con más de `N` 404 en una hora o con `User-Agent` vacío, listadas en una sección aparte. Explica qué harías con esa lista en un servidor real (y por qué no bloquear automáticamente sin revisar).

**Parte H — Python + Azure CLI en solo lectura (60-90 min)**

23. `python/azure_inventario.py`: comprueba primero que `az` existe (`shutil.which`) y que hay sesión (`az account show -o json`; si falla, mensaje claro y salida `1`, sin volcar la salida completa por pantalla). Después ejecuta `az group list -o json`, `az resource list -o json` y `az vm list -d -o json` mediante `subprocess.run`, parsea con `json.loads` y genera `informe-azure.md` con: grupos por región, recursos por tipo, grupos sin etiquetas `propietario`/`entorno`, VMs con su estado de energía y tamaño, y una sección "candidatos a borrar" (grupos sin recursos, VMs desasignadas). Añade `--offline datos/az-group-list.json` para funcionar con el JSON guardado en la Parte E, y `--query` opcional que pase una expresión JMESPath a `az` (lee la documentación de `--query`). Antes de escribir el archivo, enmascara el ID de suscripción (muestra solo los últimos 4 caracteres).
24. Explica en 8-10 líneas cuándo conviene llamar a la CLI desde Python (como aquí) y cuándo usar el SDK de Azure para Python, y por qué este script no puede costar dinero ni romper nada (solo verbos `list`/`show`). Si creaste un grupo de recursos para la prueba, bórralo y verifica.

**Parte I — Pruebas, integración y cierre (60-90 min)**

25. Pruebas mínimas: `tests/test_nginx_report.py` con `unittest` que compruebe que la expresión regular parsea una línea válida y rechaza una malformada, y que `resumir_grupos()` cuenta bien con un JSON de ejemplo; `tests/test_bash.sh` que ejecute `bash -n` y `shellcheck` sobre todos los scripts de `bash/` y compruebe que `backup.sh --dry-run` devuelve `0` y `backup.sh --destino /ruta/inexistente` devuelve distinto de `0`. Ejecuta `python -m unittest discover tests` y `bash tests/test_bash.sh` y guarda las salidas. En el curso de CI/CD estos dos comandos serán tu pipeline.
26. Integra: haz que `healthcheck.sh` incluya en su resumen la primera línea del último `informe-nginx.md` (o ejecute `nginx_report.py` con el `venv`) y explica cómo se invoca un script Python con su entorno virtual desde Bash y desde una unidad de systemd (`ExecStart=/ruta/.venv/bin/python ...`).
27. Escribe el `README.md` de `automatizacion/` (uso de cada herramienta, ejemplos, variables de entorno esperadas, cómo instalar los timers) y haz commit de todo con mensajes claros. Comprueba con `git status` y `git log --stat` que no hay secretos, `.venv/` ni archivos `.tar.gz`. Deja los timers de backup y healthcheck activos en `lab-so`.

### Resultado esperado

- Repositorio `automatizacion/` completo, versionado y sin secretos, con los tres scripts de la Parte A, `04-errores.sh`, `backup.sh`, `healthcheck.sh`, `inventario.py`, `github_info.py`, `nginx_report.py`, `azure_inventario.py`, unidades y timers, pruebas, `requirements.txt` y `README.md`.
- `laboratorio-automatizacion.md` con las decisiones, las pruebas de fallo documentadas (salidas y códigos de salida), los avisos de ShellCheck corregidos y las explicaciones pedidas.
- `informe-nginx.md`, `informe-nginx.json`, `informe-azure.md` (con la suscripción enmascarada) e `inventario-<hostname>.json`.
- `lab-so` con `backup.timer` y `healthcheck.timer` activos.

### Criterios de validación

- [ ] Parte A: los tres scripts funcionan, validan parámetros, escriben errores por `stderr` con códigos de salida correctos y pasan `shellcheck` sin avisos; los avisos corregidos están explicados.
- [ ] Parte B: cada opción de `set -euo pipefail` está demostrada con un fallo real; el `trap` limpia también cuando el script falla.
- [ ] Parte C: `backup.sh` cumple todos los requisitos; las seis pruebas de fallo están documentadas; la rotación se hace sin `ls | xargs`; la restauración de un archivo funciona; el timer está activo.
- [ ] Parte D: el healthcheck puntúa correctamente, genera Markdown, registra en el journal con prioridades, devuelve `0/1/2` y envía (o documenta que no hay) el webhook sin exponer la URL.
- [ ] Parte E: el `venv` está bien explicado; `inventario.py` genera JSON válido a partir de `ip -j`, `lsblk -J` y `ps`, y maneja comandos ausentes o fallidos.
- [ ] Parte F: `github_info.py` usa `timeout`, `Session`, cabeceras, `raise_for_status` y maneja 404, sin red y límite de peticiones con evidencias; el token solo viene del entorno.
- [ ] Parte G: el parser tolera líneas malformadas, los informes MD y JSON son correctos y la sección de sospechosos está razonada.
- [ ] Parte H: el script es de solo lectura, funciona en modo `--offline`, enmascara la suscripción y el razonamiento CLI/SDK es correcto.
- [ ] Parte I: las pruebas pasan, la integración Bash → Python con `venv` está explicada y el repositorio no contiene secretos ni artefactos.
- [ ] En una llamada con el mentor, el estudiante explica línea a línea `backup.sh` o `nginx_report.py` a elección del mentor y modifica una función en directo.

## Entrega

En tu repositorio de entregas, carpeta `02-modulo-intermedio/03-bash-y-python-para-automatizacion/`:

1. `automatizacion/` completo (como subcarpeta o como submódulo/enlace a un repositorio propio; si es repositorio propio, debe ser público o compartido con el mentor).
2. `laboratorio-automatizacion.md`.
3. `informes/` con `informe-nginx.md`, `informe-nginx.json`, `informe-azure.md`, `inventario-<hostname>.json`.
4. `capturas/` (salidas de las pruebas de fallo, `systemctl list-timers`, `journalctl` del backup y del healthcheck).
5. `ENTREGA.md` con evaluación, checklist y uso de IA.

Nota sobre IA: en este curso la tentación es máxima. Puedes usar IA para que te explique un aviso de ShellCheck, una excepción de Python o una expresión regular, y para que revise un script **que tú ya escribiste**. Si generas un script con IA, decláralo y demuestra en la llamada con el mentor que entiendes cada línea. Los modelos suelen olvidar `timeout`, comillas y `set -euo pipefail`: si lo detectas, anótalo en la entrega.

## Evaluación

1. **Conceptual.** Explica qué hace cada opción de `set -euo pipefail` y da un ejemplo real de bug que cada una evita. ¿En qué caso `-e` te puede traicionar (piensa en `if`, `&&`, `||` y en tuberías)?
2. **Técnica.** ¿Qué imprime `for f in $(ls *.log); do echo "$f"; done` si un archivo se llama `mi log.log`? ¿Cómo se escribe bien y qué aviso daría ShellCheck?
3. **Situacional.** El backup nocturno lleva tres semanas fallando y nadie se ha enterado. Nombra tres mecanismos de tu laboratorio que lo habrían delatado y explica cómo encaja cada uno (código de salida, journal, healthcheck, `OnFailure`).
4. **Técnica.** Escribe el esqueleto de un script Bash con `trap` que cree un directorio temporal, lo borre siempre al salir (aunque falle) y registre la línea del error. Explica por qué `EXIT` y `ERR` son distintos.
5. **Conceptual.** Diferencia `stdout` y `stderr` y explica por qué `healthcheck.sh` imprime la tabla por `stdout` y los errores por `stderr`. ¿Qué pasaría si otro script hiciera `resultado=$(./healthcheck.sh)` y mezclaras ambos?
6. **Situacional.** Te piden "un script rápido" que lea la salida de `az vm list -o json`, agrupe las VMs por región y avise de las que llevan desasignadas más de 30 días. ¿Bash o Python? Justifica con tres razones y esboza la estructura.
7. **Técnica.** ¿Por qué `requests.get(url)` sin `timeout` es peligroso en un script programado? ¿Qué excepciones de `requests` capturarías y qué harías en cada una (404, 429, `ConnectionError`, `Timeout`)?
8. **Conceptual.** Explica qué es un entorno virtual de Python, qué problema resuelve y por qué Ubuntu bloquea `pip install` fuera de él. ¿Cómo se ejecuta un script con su `venv` desde una unidad de systemd?
9. **Técnica.** Escribe una expresión regular con grupos con nombre que capture IP, fecha, método, ruta y código de estado de una línea `combined` de nginx, y di qué harías con una línea que no coincide.
10. **Troubleshooting.** `nginx_report.py` funciona en tu terminal pero, lanzado desde el timer, falla con `ModuleNotFoundError: requests`. Explica la causa y dos soluciones.
11. **Situacional.** Alguien propone poner el `GITHUB_TOKEN` en la primera línea del script "para que funcione en el servidor". Explica los riesgos, dónde debería vivir el secreto en tu VM (archivo con permisos, `EnvironmentFile=`) y dónde en un pipeline de CI/CD o en Azure (secretos del repositorio, Key Vault).
12. **Técnica.** ¿Qué diferencia hay entre `subprocess.run(["az", "group", "list"], check=True)` y `subprocess.run("az group list", shell=True)`? ¿Cuál es más seguro cuando parte del comando viene del usuario y por qué?
13. **Conceptual.** ¿Por qué `azure_inventario.py` solo usa verbos `list`/`show`? Si tuviera que borrar los "candidatos a borrar", ¿qué salvaguardas añadirías (dry-run por defecto, confirmación, etiquetas de protección, bloqueo de recursos)?
14. **Reflexión.** ¿Qué tarea manual de los cursos anteriores automatizarías mañana con lo aprendido y con cuál de los dos lenguajes? ¿Qué error de tus scripts te enseñó más?

## Checklist final

Antes de continuar, deberías poder:

- [ ] Escribir un script Bash con parámetros, funciones, arrays, bucles sobre archivos y códigos de salida correctos.
- [ ] Explicar y usar `set -euo pipefail`, `trap`, comillas y `[[ ]]`, y dejar cualquier script sin avisos de ShellCheck.
- [ ] Escribir un backup con rotación, bloqueo, verificación y logging, y programarlo con un timer de systemd.
- [ ] Escribir una comprobación de salud que resuma en Markdown, registre en el journal y devuelva códigos `0/1/2`.
- [ ] Crear y usar un `venv`, congelar dependencias y ejecutar Python con su entorno desde Bash y systemd.
- [ ] Ejecutar comandos del sistema desde Python y convertir su salida (JSON o texto) en estructuras de datos.
- [ ] Consumir una API HTTP con `requests`, con `timeout`, cabeceras, códigos de estado, errores y límites de peticiones.
- [ ] Parsear un log con expresiones regulares y generar un informe en Markdown y JSON.
- [ ] Estructurar un script Python con `argparse`, `logging`, excepciones y una prueba `unittest`.
- [ ] Llamar a la Azure CLI desde Python en solo lectura y decidir entre CLI y SDK.
- [ ] Mantener los secretos fuera del código y del repositorio.
- [ ] Tener `lab-so` con backup y healthcheck programados para los cursos siguientes.

---

*Recursos verificados el 2026-09-27 mediante búsqueda web (existencia y vigencia de las URLs). Si un enlace falla, abre un issue en este repositorio.*
