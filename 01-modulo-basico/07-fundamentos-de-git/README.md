# Fundamentos de Git

> Módulo: Básico · Curso 7 de 9 · Duración estimada: 8-12 horas · Estado: ✅ Completo

## Objetivo

En Cloud, DevOps y SRE **todo vive en Git**: el código de las aplicaciones, la infraestructura (Terraform), los pipelines (YAML), la configuración de Kubernetes, los runbooks, la documentación. Un cambio en producción empieza siendo un commit. Si no dominas Git, no puedes trabajar en un equipo moderno, y buena parte de la ruta (Terraform, CI/CD, Kubernetes, el Proyecto Final) se entrega en repositorios Git.

Este curso te enseña **lo esencial para trabajar solo con Git de forma segura**: qué es el control de versiones, cómo se estructura un repositorio, el ciclo working directory → staging → commit, cómo publicar y sincronizar con un repositorio remoto en GitHub, qué son las ramas y para qué sirve `.gitignore`. El trabajo colaborativo (Pull Requests, conflictos, rebase) llega en el Módulo Intermedio.

Hasta ahora has entregado tus laboratorios subiendo archivos por la web de GitHub. A partir de este curso, **tu repositorio de entregas se gestiona con Git desde la terminal**, y ese será precisamente el laboratorio.

**Antes de empezar** debes manejar la terminal (Linux Básico) y tener una cuenta de GitHub. Git funciona igual en Windows, macOS y Linux; los ejemplos usan Bash (en Windows, Git Bash o la VM Linux).

### Al terminar este curso deberías poder

- Explicar qué es el control de versiones, qué problema resuelve y por qué Git es distribuido.
- Explicar los tres estados de un archivo (modificado, preparado, confirmado) y las tres zonas (working directory, staging area, repositorio).
- Crear un repositorio, configurar tu identidad y hacer commits con mensajes útiles.
- Leer `git status`, `git log` y `git diff` y saber en qué estado está tu repositorio en cada momento.
- Clonar un repositorio remoto, publicar cambios con `push` y traer cambios con `pull`, entendiendo qué es `origin`.
- Crear una rama, cambiar entre ramas, hacer commits en ella y fusionarla en la principal en un caso sin conflictos.
- Escribir un `.gitignore` y explicar qué **no** debe entrar nunca en un repositorio (secretos, binarios, archivos temporales).
- Deshacer errores habituales: quitar un archivo del staging, descartar cambios locales, corregir el último mensaje de commit.
- Explicar qué es GitHub, qué añade sobre Git y qué es un README.
- Autenticarte con GitHub desde la terminal de forma segura (SSH o token), nunca con tu contraseña.

## Prerrequisitos

- Curso 5: Linux Básico (terminal, SSH con claves).
- Cuenta de GitHub (gratuita).
- Git instalado: en la VM Linux `sudo apt install git`; en Windows, Git for Windows (incluye Git Bash) con `winget install Git.Git`; en macOS viene con las herramientas de Xcode o `brew install git`.
- Un editor de texto: se recomienda Visual Studio Code (gratuito, con integración de Git).

## Temario

- Control de versiones.
- Repositorios.
- Working directory.
- Staging.
- Commits.
- Clone.
- Pull.
- Push.
- Branches básicas.
- .gitignore.
- Repositorios remotos.
- Introducción a GitHub.

## Recursos en español

### Pro Git, 2.ª edición (capítulos 1-3) — Scott Chacon y Ben Straub
- **URL:** https://git-scm.com/book/es/v2
- **Autor / organización:** Scott Chacon y Ben Straub; publicado por Apress y liberado bajo Creative Commons; alojado en la web oficial de Git
- **Idioma:** Español (traducción comunitaria completa)
- **Tipo:** Libro online / PDF
- **Duración aproximada:** 3-4 h para los capítulos 1 (Inicio), 2 (Fundamentos de Git) y 3 (Ramificaciones, solo las secciones "Qué es una rama" y "Procedimientos básicos para ramificar y fusionar")
- **Cubre:** Control de versiones, repositorios, las tres zonas, commits, `.gitignore`, remotos, ramas básicas.
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es **el** libro de Git, escrito por gente de GitHub, gratuito y en español, y vive en la web oficial. El capítulo 2 es la mejor explicación que existe del ciclo working directory → staging → commit. Es el texto de referencia del curso.

### Introducción al control de versiones con Git (ruta de aprendizaje) — Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/training/paths/intro-to-vc-git/
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Ruta de aprendizaje con ejercicios en un sandbox (terminal en el navegador)
- **Duración aproximada:** 2 h
- **Cubre:** Control de versiones, repositorios, commits, historial, deshacer cambios, colaboración básica.
- **Nivel:** Introductorio
- **Acceso:** Libre; el sandbox requiere cuenta Microsoft gratuita
- **Por qué lo recomiendo:** Permite practicar los comandos en un entorno guiado con comprobaciones, sin miedo a romper nada. Es el mejor primer contacto práctico. Además, Microsoft Learn será tu plataforma principal en Azure, así que conviene acostumbrarse a su formato.

### Curso de Git y GitHub desde cero — MoureDev (Brais Moure)
- **URL:** Repositorio del curso con enlaces a los vídeos, apuntes y ejercicios: https://github.com/mouredev/hello-git · Vídeo principal en YouTube: https://www.youtube.com/watch?v=3GymExBkKjE
- **Autor / organización:** Brais Moure (MoureDev)
- **Idioma:** Español
- **Tipo:** Curso en vídeo + repositorio con apuntes y ejercicios
- **Duración aproximada:** ~5 h en total; para este curso interesan las primeras ~3 h (instalación, configuración, repositorio, commits, historial, `.gitignore`, ramas, remotos, GitHub). Pull Requests y colaboración se retoman en el Módulo Intermedio.
- **Cubre:** Todo el temario.
- **Nivel:** Introductorio
- **Acceso:** Libre (el vídeo y el repositorio son gratuitos; la versión en mouredev.pro con extras es de pago y no es necesaria)
- **Por qué lo recomiendo:** Es el curso en vídeo en español más completo y claro sobre Git, con un repositorio que sirve de chuleta. Ideal para ver los comandos en acción mientras lees Pro Git.

### Learn Git Branching (en español) — Peter Cottle
- **URL:** https://learngitbranching.js.org/?locale=es_ES
- **Autor / organización:** Peter Cottle (proyecto de código abierto)
- **Idioma:** Español (interfaz traducida)
- **Tipo:** Tutorial interactivo con visualización del grafo de commits
- **Duración aproximada:** 60-90 min para "Introducción a Git" (niveles 1-4) y "Remoto: Push y Pull" (niveles 1-4)
- **Cubre:** Commits, ramas, merge, remotos, push, pull, de forma visual.
- **Nivel:** Introductorio (los primeros niveles); el resto es intermedio-avanzado
- **Acceso:** Libre, sin registro
- **Por qué lo recomiendo:** Es la herramienta que hace que las ramas "se vean". Cada comando dibuja el grafo. Haz solo los niveles indicados; los de rebase y cherry-pick son del Módulo Intermedio.

## Recursos en inglés

### Introduction to GitHub — GitHub Skills
- **URL:** https://github.com/skills/introduction-to-github (catálogo completo: https://learn.github.com/skills)
- **Autor / organización:** GitHub
- **Idioma:** Inglés
- **Tipo:** Curso interactivo dentro de un repositorio propio (GitHub Actions te va guiando en Issues)
- **Duración aproximada:** 1 h
- **Cubre:** Repositorios, ramas, commits, Pull Requests básicos, README de perfil, todo desde la web de GitHub.
- **Nivel:** Introductorio
- **Acceso:** Libre, requiere cuenta de GitHub
- **Por qué lo recomiendo:** Es el curso oficial de GitHub y se hace **dentro** de GitHub: copias el repositorio del curso a tu cuenta y un bot te va dando instrucciones en Issues. Te acostumbra a la interfaz que usarás toda la ruta. Como resultado, creas el README de tu perfil.

### Hello World y Get started — GitHub Docs
- **URL:** https://docs.github.com/en/get-started/start-your-journey/hello-world (portal: https://docs.github.com/en/get-started)
- **Autor / organización:** GitHub
- **Idioma:** Inglés (GitHub Docs ofrece traducción al español en el selector de idioma, con calidad variable)
- **Tipo:** Documentación oficial / tutorial
- **Duración aproximada:** 30 min
- **Cubre:** Introducción a GitHub: repositorio, rama, commit, Pull Request desde la interfaz web.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la guía oficial de primeros pasos en GitHub. Corta y exacta. Sirve como referencia de la parte "GitHub" del temario, separada de la parte "Git".

### Introduction to Git — Microsoft Learn
- **URL:** https://learn.microsoft.com/en-us/training/modules/intro-to-git/
- **Autor / organización:** Microsoft
- **Idioma:** Inglés
- **Tipo:** Módulo de aprendizaje con sandbox
- **Duración aproximada:** 45 min
- **Cubre:** Control de versiones, crear y configurar un repositorio, hacer y seguir cambios.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Versión en inglés del módulo de la ruta en español, útil para fijar la terminología (staging, commit, working tree, remote) tal como aparece en toda la documentación.

### Git Reference Documentation (gittutorial, git-init, git-add, git-commit, git-log, git-push...) — Proyecto Git
- **URL:** https://git-scm.com/docs (tutorial oficial: https://git-scm.com/docs/gittutorial ; glosario: https://git-scm.com/docs/gitglossary)
- **Autor / organización:** Proyecto Git
- **Idioma:** Inglés
- **Tipo:** Documentación oficial de referencia (las mismas páginas que `git help <comando>`)
- **Duración aproximada:** Consulta puntual; `gittutorial` son 30 min
- **Cubre:** Todos los comandos.
- **Nivel:** Todos
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la fuente de verdad. Como con `man` en Linux: antes de buscar un comando de Git en un blog, `git help <comando>` o esta web.

## Documentación oficial

- **Git — Documentación de referencia:** https://git-scm.com/docs
- **Git — Pro Git (libro oficial, español):** https://git-scm.com/book/es/v2
- **Git — Descarga e instalación:** https://git-scm.com/downloads
- **GitHub Docs — Get started:** https://docs.github.com/en/get-started
- **GitHub Docs — Recursos de aprendizaje de Git y GitHub:** https://docs.github.com/en/get-started/start-your-journey/git-and-github-learning-resources
- **GitHub Docs — Autenticación (SSH y tokens):** https://docs.github.com/en/authentication (léela cuando llegues a la parte C del laboratorio; explica por qué GitHub no acepta contraseñas por línea de comandos y cómo configurar claves SSH, que ya sabes crear del curso de Linux)
- **gitignore.io / plantillas de GitHub:** https://github.com/github/gitignore (colección oficial de `.gitignore` por lenguaje y herramienta)

## Ruta recomendada de estudio

1. **Leer** Pro Git, capítulo 1 completo (45 min): qué es el control de versiones, historia de Git, las tres zonas, instalación y configuración inicial (`git config --global user.name / user.email`). Configura tu identidad en tu equipo y en la VM.
2. **Hacer** la ruta "Introducción al control de versiones con Git" de Microsoft Learn (2 h) en el sandbox. Objetivo: repetir el ciclo editar → `git add` → `git commit` hasta que sea automático, y leer `git status` sin dudar.
3. **Leer** Pro Git, capítulo 2 completo (90 min), con un repositorio de prueba abierto y ejecutando cada comando: `git init`, `git status`, `git add`, `git diff`, `git diff --staged`, `git commit`, `git log` (con `--oneline`, `--graph`, `-p`), `git rm`, `git mv`, `.gitignore`, deshacer cosas, remotos.
4. **Ver** las secciones del curso de MoureDev sobre configuración, repositorio, commits, historial y `.gitignore` (60-90 min).
5. **Hacer** GitHub Skills "Introduction to GitHub" (1 h) y **leer** GitHub Docs "Hello World" (20 min). Ya tienes claro qué añade GitHub sobre Git.
6. **Leer** Pro Git, capítulo 3, secciones "Qué es una rama" y "Procedimientos básicos para ramificar y fusionar" (45 min), y **hacer** Learn Git Branching, "Introducción a Git" niveles 1-4 y "Remoto: Push y Pull" niveles 1-4 (60-90 min).
7. **Ver** las secciones de ramas, remotos y GitHub del curso de MoureDev (45 min).
8. **Leer** GitHub Docs sobre autenticación por SSH (20 min). Vas a reutilizar la clave `ed25519` que creaste en Linux Básico o crear una nueva.
9. **Hacer el laboratorio** (3-4 h).
10. **Responder la evaluación** y **revisar el checklist**.

## Laboratorio

### Objetivo

Convertir tu repositorio de entregas en un repositorio Git gestionado desde la terminal, con historial limpio, `.gitignore` correcto, autenticación segura por SSH y una rama de trabajo fusionada; y crear un segundo repositorio desde cero con los scripts de la ruta.

### Requisitos

- Git instalado y configurado (`user.name`, `user.email`, `init.defaultBranch main`).
- Cuenta de GitHub con tu repositorio `learning-entregas-<usuario>` ya existente (creado por la web en cursos anteriores).
- Terminal Bash (Git Bash en Windows, o la VM Linux).
- Visual Studio Code u otro editor.

### Instrucciones

Documenta todo en `laboratorio-git.md`. Pega la salida de los comandos como texto.

**Parte A — Configuración e identidad (20 min)**

1. Ejecuta `git --version`, `git config --global user.name "Tu Nombre"`, `git config --global user.email "tu@correo"` (usa el mismo correo que en GitHub, o el correo `noreply` que GitHub te ofrece en Settings → Emails), `git config --global init.defaultBranch main`, `git config --global core.editor "code --wait"` (si usas VS Code). Muestra `git config --global --list`. Explica dónde se guarda esa configuración (`~/.gitconfig`) y qué diferencia hay entre `--global` y la configuración local de un repositorio.

**Parte B — Un repositorio desde cero (60 min)**

2. Crea la carpeta `scripts-ruta` e inicialízala con `git init`. Muestra `ls -la` y explica qué es la carpeta `.git` y por qué nunca se edita a mano.
3. Copia dentro `hola.sh` (del curso de Linux) y el `comandos.ps1` del curso de Windows. Ejecuta `git status` y explica el estado de los archivos ("untracked").
4. Añade **solo** `hola.sh` al staging (`git add hola.sh`), ejecuta `git status` y explica las dos secciones que aparecen. Haz el primer commit con un mensaje descriptivo (`git commit -m "Añadir script de saludo del curso de Linux"`). Muestra `git log`.
5. Añade `comandos.ps1` y haz un segundo commit. Edita `hola.sh` añadiendo una línea que muestre la fecha, y **sin** hacer `add` ejecuta `git diff`. Después haz `git add` y ejecuta `git diff` otra vez (nada) y `git diff --staged` (tu cambio). Explica la diferencia. Haz commit.
6. Crea un archivo `README.md` que explique qué contiene el repositorio. Crea también un archivo `notas-personales.txt` con texto cualquiera y un archivo `secreto.env` con `PASSWORD=1234`. Escribe un `.gitignore` que excluya `*.env`, `notas-personales.txt`, `*.log` y la carpeta `tmp/`. Ejecuta `git status` y comprueba que los archivos ignorados no aparecen. Haz commit de `README.md` y `.gitignore`. Explica por qué `secreto.env` **jamás** debe entrar en un repositorio y qué pasaría si lo subieras a GitHub aunque lo borraras en el siguiente commit.
7. Deshacer cosas, cada una con su comando y su explicación:
   - Edita `README.md`, añádelo al staging y **sácalo** del staging sin perder el cambio (`git restore --staged README.md`).
   - Descarta por completo ese cambio del working directory (`git restore README.md`). Comprueba con `git diff` que no queda nada.
   - Haz un commit con un mensaje con una falta de ortografía y corrígelo con `git commit --amend`. Muestra `git log --oneline` antes y después y explica por qué el hash del commit cambió.
   - Explica en 3 líneas por qué `--amend` solo debe usarse en commits que **no** has publicado todavía.
8. Muestra el historial completo con `git log --oneline --graph --decorate` y explica qué es `HEAD` y qué es `main`.

**Parte C — Remoto y GitHub (45 min)**

9. Autenticación por SSH: comprueba si tienes una clave (`ls ~/.ssh`); si no, créala con `ssh-keygen -t ed25519 -C "github"`. Añade la clave **pública** en GitHub → Settings → SSH and GPG keys. Comprueba con `ssh -T git@github.com` (debe saludarte por tu usuario). Explica por qué GitHub no permite autenticarse con contraseña desde la terminal y qué alternativa hay a SSH (token de acceso personal).
10. Crea en GitHub un repositorio **vacío** llamado `scripts-ruta` (sin README ni `.gitignore`, para no crear conflictos). Conecta tu repositorio local: `git remote add origin git@github.com:<usuario>/scripts-ruta.git`, `git remote -v`, `git push -u origin main`. Explica qué es `origin`, qué hace `-u` y qué es `origin/main` cuando ejecutas `git log --oneline --all`.
11. Edita `README.md` **desde la web de GitHub** (botón de editar, commit desde el navegador). En tu terminal ejecuta `git status` (no sabe nada), `git fetch` y `git status` otra vez (ahora dice que estás 1 commit por detrás), `git log --oneline --all --graph`. Después `git pull`. Explica la diferencia entre `fetch` y `pull` y qué habría pasado si hubieras hecho `push` con un cambio local sin haber hecho `pull` antes.

**Parte D — Ramas (45 min)**

12. Crea una rama `mejora-hola` (`git switch -c mejora-hola`), edita `hola.sh` para que acepte un nombre como parámetro (`$1`) y haz dos commits en la rama. Ejecuta `git log --oneline --graph --all` y explica el dibujo.
13. Vuelve a `main` (`git switch main`), comprueba que `hola.sh` **no** tiene los cambios (`cat hola.sh`) y explica por qué. Crea en `main` un archivo `CHANGELOG.md` y haz commit (para que las ramas diverjan).
14. Fusiona `mejora-hola` en `main` (`git merge mejora-hola`). Explica qué tipo de fusión ocurrió (mira si hay un "merge commit") y muestra el grafo. Borra la rama ya fusionada (`git branch -d mejora-hola`) y haz `push`. Comprueba en GitHub que el historial y la red de commits ("Insights → Network") reflejan la fusión.
15. Publica una rama sin fusionar: crea `experimento`, haz un commit, `git push -u origin experimento`. Comprueba en GitHub que aparecen dos ramas. Explica para qué sirve trabajar en ramas aunque estés solo.

**Parte E — Migrar tu repositorio de entregas a Git (45-60 min)**

16. Clona tu repositorio de entregas: `git clone git@github.com:<usuario>/learning-entregas-<usuario>.git`. Muestra `git log --oneline | head` y `git remote -v`. Explica qué hizo `clone` (descargó todo el historial y configuró `origin`).
17. Añade al repositorio un `.gitignore` adecuado (archivos temporales del sistema como `.DS_Store` y `Thumbs.db`, `*.env`, `*.pem`, `*.key`, `.vscode/` si no quieres compartir tu configuración). Revisa que **ninguna** entrega anterior contenga secretos (contraseñas de los usuarios de laboratorio, claves privadas, tokens). Si los hay, elimínalos y avisa al mentor: veréis juntos cómo limpiar el historial.
18. Crea la carpeta `01-modulo-basico/07-fundamentos-de-git/`, mueve dentro `laboratorio-git.md` y `ENTREGA.md`, y haz commits **pequeños y con mensajes claros** (por ejemplo, uno para `.gitignore`, otro para el laboratorio, otro para la entrega). Haz `push`. A partir de ahora, todas las entregas se hacen así.
19. Reescribe el `README.md` de tu repositorio de entregas para que tenga: quién eres, en qué curso estás, un índice con enlaces a cada carpeta de entrega y una tabla con el estado de cada curso. Commit y push.

### Resultado esperado

- Repositorio `scripts-ruta` en GitHub con historial legible, `.gitignore`, una rama fusionada y otra publicada.
- Repositorio de entregas clonado en tu equipo, con `.gitignore`, sin secretos, con el README de índice y con la entrega de este curso hecha por Git.
- `laboratorio-git.md` con las cinco partes y las salidas de los comandos.

### Criterios de validación

- [ ] `git log --oneline --graph --all` de `scripts-ruta` muestra al menos 8 commits con mensajes descriptivos (no "cambios", "update", "asdf"), el merge de `mejora-hola` y la rama `experimento`.
- [ ] `.gitignore` funciona: `secreto.env` y `notas-personales.txt` no están en ningún commit (`git log --all -- secreto.env` vacío).
- [ ] Las explicaciones de `diff` frente a `diff --staged`, `fetch` frente a `pull`, `restore` frente a `restore --staged` y de por qué `--amend` cambia el hash son correctas y propias.
- [ ] La autenticación es por SSH (o token); `ssh -T git@github.com` funciona.
- [ ] El repositorio de entregas tiene `.gitignore`, README con índice, no contiene secretos y la entrega de este curso llegó por `push` desde la terminal.
- [ ] El estudiante puede, en una llamada, crear una rama, hacer un commit, fusionarla y publicarla sin consultar apuntes.

## Entrega

En tu repositorio de entregas, carpeta `01-modulo-basico/07-fundamentos-de-git/`, **subida con Git desde la terminal**:

1. `laboratorio-git.md`.
2. Enlace al repositorio `scripts-ruta` en GitHub (dentro de `ENTREGA.md`).
3. `ENTREGA.md` con evaluación, checklist y uso de IA.

El mentor revisará directamente el historial de ambos repositorios en GitHub.

## Evaluación

1. **Conceptual.** ¿Qué problema resuelve el control de versiones que no resuelve "guardar copias con fecha en una carpeta"? Da tres ventajas concretas.
2. **Conceptual.** ¿Qué significa que Git sea **distribuido**? Si GitHub desapareciera mañana, ¿perderías tu historial? ¿Y si se rompe tu disco duro sin haber hecho `push`?
3. **Técnica.** Explica las tres zonas de Git y dibuja (en texto) el camino de un archivo desde que lo editas hasta que está en GitHub, nombrando el comando de cada paso.
4. **Situacional.** `git status` te dice "Changes not staged for commit" para `config.yaml` y "Changes to be committed" para `main.tf`. Si haces `git commit -m "x"` ahora, ¿qué entra en el commit? ¿Qué comando te muestra exactamente lo que va a entrar?
5. **Técnica.** ¿Qué diferencia hay entre `git fetch` y `git pull`? ¿Cuándo preferirías `fetch`?
6. **Situacional.** Haces `git push` y Git responde "rejected: fetch first" o "non-fast-forward". ¿Qué ha pasado y qué debes hacer? ¿Por qué **no** debes usar `--force` para "arreglarlo"?
7. **Conceptual.** ¿Qué es una rama en Git (a nivel técnico, qué guarda realmente)? ¿Por qué crear una rama es instantáneo aunque el repositorio sea enorme?
8. **Situacional.** Estás en la rama `feature-x`, editas un archivo y sin hacer commit ejecutas `git switch main`. Nombra dos cosas que pueden pasar y qué harías para evitar problemas.
9. **Técnica.** Escribe un `.gitignore` razonable para un proyecto que tendrá Terraform (`.terraform/`, `*.tfstate`), Python (`__pycache__/`, `.venv/`) y variables de entorno. Explica por qué el `tfstate` no debe subirse (pista: contiene datos sensibles).
10. **Situacional.** Un compañero subió por error un archivo con una contraseña, lo borró en el siguiente commit y dice que "ya está arreglado". Explícale por qué no lo está y qué dos cosas hay que hacer.
11. **Técnica.** ¿Qué hace `git commit --amend`? ¿Por qué es peligroso si el commit ya está en GitHub y otra persona lo ha descargado?
12. **Conceptual.** ¿Qué es GitHub y qué añade sobre Git? Nombra tres cosas que existen en GitHub y no en Git.
13. **Conceptual.** ¿Por qué GitHub no acepta tu contraseña desde la terminal? Explica las dos alternativas y cuál usaste.
14. **Reflexión.** Escribe tres reglas personales para tus mensajes de commit a partir de ahora y justifica cada una pensando en alguien que lea tu historial dentro de seis meses.

## Checklist final

Antes de continuar, deberías poder:

- [ ] Explicar qué es el control de versiones y por qué Git es distribuido.
- [ ] Explicar working directory, staging area y repositorio, y los estados de un archivo.
- [ ] Inicializar un repositorio, configurar tu identidad y hacer commits con mensajes claros.
- [ ] Interpretar `git status`, `git log` y `git diff` (con y sin `--staged`).
- [ ] Clonar, hacer `push` y `pull`, y explicar `origin` y `origin/main`.
- [ ] Crear, cambiar, fusionar y borrar ramas en un caso sin conflictos.
- [ ] Escribir un `.gitignore` y explicar qué nunca debe entrar en un repositorio.
- [ ] Deshacer los errores habituales con `restore`, `restore --staged` y `--amend` (sabiendo cuándo no usarlo).
- [ ] Autenticarte con GitHub por SSH.
- [ ] Gestionar tu repositorio de entregas por Git desde la terminal.

---

*Recursos verificados el 2026-09-26 mediante búsqueda web (existencia y vigencia de las URLs). Si un enlace falla, abre un issue en este repositorio.*
