# Git y GitHub Intermedio

> Módulo: Intermedio · Curso 4 de 11 · Duración estimada: 15-20 horas · Estado: ✅ Completo

## Objetivo

En Fundamentos de Git aprendiste a trabajar **solo**: commits, ramas sencillas, un remoto. En un equipo real todo eso se complica: varias personas tocan el mismo repositorio a la vez, nadie fusiona a `main` sin que otro revise, los conflictos aparecen, las versiones se etiquetan y se publican, y hay reglas que impiden que un despiste borre el historial. Este curso te enseña a **trabajar en equipo sobre un repositorio compartido** con la disciplina que se usa en cualquier empresa: ramas cortas, Pull Requests con revisión, conflictos resueltos con calma, historial limpio con rebase, tags y releases, y protección de ramas.

Todo lo que viene después en la ruta pasa por aquí. Los pipelines de CI/CD se disparan con Pull Requests y tags; Terraform y Kubernetes se revisan en PRs; los runbooks viven en repositorios con CODEOWNERS; una release mal etiquetada acaba en un despliegue equivocado. Si el equipo no tiene un flujo de Git claro, la automatización solo acelera el caos.

La parte central del curso es un laboratorio en el que simulas a **dos desarrolladores** (o trabajas con un compañero de la ruta) sobre el mismo repositorio: cada uno con su clon, su identidad y sus ramas, provocando y resolviendo los problemas típicos.

**Antes de empezar** debes manejar con soltura lo del curso Fundamentos de Git: `add`, `commit`, `push`, `pull`, ramas básicas, `.gitignore`, autenticación SSH con GitHub.

### Al terminar este curso deberías poder

- Explicar qué es un Pull Request, qué añade sobre un `git merge` local y por qué es la unidad de trabajo en equipo.
- Hacer una revisión de código útil: comentarios en línea, sugerencias aplicables, aprobación o solicitud de cambios, y responder a una revisión sin tomártelo como algo personal.
- Provocar, entender y resolver un conflicto de fusión desde la terminal y desde la web de GitHub, sabiendo qué significan los marcadores `<<<<<<<`, `=======` y `>>>>>>>`.
- Distinguir `merge`, `squash merge` y `rebase`, saber qué historial produce cada uno y cuándo elegir uno u otro.
- Usar `git rebase` para actualizar una rama y `git rebase -i` para limpiar commits antes de abrir un PR, y enunciar la regla de oro: nunca reescribas historia compartida.
- Crear tags anotados con versionado semántico y publicar una Release en GitHub con notas.
- Configurar protección de la rama `main` (PR obligatorio, revisiones requeridas, sin force-push), CODEOWNERS y plantillas de PR e issues, y explicar qué problema evita cada regla.
- Comparar trunk-based development, GitHub Flow y Gitflow y elegir una estrategia para un equipo concreto justificando la decisión.
- Configurar identidades de Git distintas por repositorio y explicar por qué importa que cada commit lleve el autor correcto.

## Prerrequisitos

- Módulo Básico completo, en especial el curso 7: Fundamentos de Git.
- Cuenta de GitHub con clave SSH configurada y tu repositorio de entregas funcionando desde la terminal.
- Git 2.30 o superior (`git --version`) en tu equipo o en la VM `lab-so`. Un editor (VS Code recomendado).
- Opcional pero muy recomendable: un compañero de la ruta con quien hacer el laboratorio a dos manos. Si no lo tienes, el laboratorio explica cómo simular al segundo desarrollador tú solo.

## Temario

Branches · Merge · Rebase introductorio · Pull Requests · Code Review · Conflictos · Tags · Releases · Branch protection · Estrategias de branching · Trabajo colaborativo.

**Práctica:** simular el trabajo de varios desarrolladores sobre un mismo repositorio.

## Recursos en español

### Pro Git, 2.ª edición (capítulos 3, 5, 6 y 7) — Scott Chacon y Ben Straub
- **URL:** https://git-scm.com/book/es/v2 · Secciones clave del capítulo 3: "Reorganizar el Trabajo Realizado" https://git-scm.com/book/es/v2/Ramificaciones-en-Git-Reorganizar-el-Trabajo-Realizado y "Flujos de Trabajo Ramificados" https://git-scm.com/book/es/v2/Ramificaciones-en-Git-Flujos-de-Trabajo-Ramificados
- **Autor / organización:** Scott Chacon y Ben Straub; licencia Creative Commons; alojado en la web oficial de Git
- **Idioma:** Español
- **Tipo:** Libro online
- **Duración aproximada:** 5-6 h: capítulo 3 completo (ramas, fusión, gestión de ramas, remotas, rebase), capítulo 5 (Git en entornos distribuidos: flujos de trabajo, contribuir a un proyecto, mantener un proyecto), capítulo 6 (GitHub: Pull Requests) y del capítulo 7 las secciones de guardado rápido (`stash`) y reescritura de la historia
- **Cubre:** Branches, merge, rebase, conflictos, tags, trabajo colaborativo, estrategias de branching.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Sigue siendo el texto de referencia. El capítulo 3 explica el rebase mejor que ningún vídeo, y el capítulo 5 describe los flujos de trabajo (centralizado, gestor de integraciones, dictador y tenientes) que están detrás de todo lo que hace GitHub. Ojo: la interfaz de GitHub que muestra el capítulo 6 está anticuada; los conceptos no.

### Colaborar con Git y Estrategias de rama — Microsoft Learn
- **URL:** Módulo "Colaborar con Git": https://learn.microsoft.com/es-es/training/modules/collaborate-with-git/ · Módulo "Diseñar e implementar estrategias y flujos de trabajo de rama": https://learn.microsoft.com/es-es/training/modules/manage-git-branches-workflows/ · Ruta "Fundamentos de GitHub, parte 1 de 2": https://learn.microsoft.com/es-es/training/paths/github-foundations/
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Módulos de aprendizaje con ejercicios guiados
- **Duración aproximada:** 3-4 h en total
- **Cubre:** Pull Requests, revisión, conflictos, ramas de característica, estrategias de branching (trunk-based, feature branch, Gitflow), protección de ramas, releases.
- **Nivel:** Intermedio
- **Acceso:** Libre; cuenta Microsoft gratuita para guardar progreso
- **Por qué lo recomiendo:** El módulo de estrategias de rama es el que mejor resume, en español, los criterios para elegir un flujo. La ruta de Fundamentos de GitHub repasa la plataforma (issues, PRs, releases, protección) desde la interfaz actual. Es material de la certificación GitHub Foundations, por si te interesa después.

### Curso de Git y GitHub desde cero (parte de colaboración) — MoureDev (Brais Moure)
- **URL:** Repositorio: https://github.com/mouredev/hello-git · Vídeo: https://www.youtube.com/watch?v=3GymExBkKjE
- **Autor / organización:** Brais Moure (MoureDev)
- **Idioma:** Español
- **Tipo:** Curso en vídeo + repositorio con apuntes
- **Duración aproximada:** ~2 h (la parte final del curso: fork, Pull Requests, revisión, conflictos, tags, GitHub Actions introductorio)
- **Cubre:** Pull Requests, conflictos, tags, trabajo colaborativo.
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** En el Módulo Básico viste las primeras 3 horas; ahora toca el resto. Ver a alguien abrir un PR, recibir comentarios y resolver un conflicto en directo quita mucho miedo antes de hacerlo tú.

### Learn Git Branching (niveles de rebase, cherry-pick y remotos avanzados) — Peter Cottle
- **URL:** https://learngitbranching.js.org/?locale=es_ES
- **Autor / organización:** Peter Cottle (código abierto)
- **Idioma:** Español (interfaz)
- **Tipo:** Tutorial interactivo con visualización del grafo
- **Duración aproximada:** 2-3 h para "Acelerando" (rebase, cherry-pick, rebase interactivo), "Moviéndose por el árbol" y la pestaña "Remoto" completa
- **Cubre:** Branches, merge, rebase, tags (`git tag`, `git describe`), remotos.
- **Nivel:** Intermedio
- **Acceso:** Libre, sin registro
- **Por qué lo recomiendo:** Es la única forma de **ver** lo que hace un rebase con los commits. Haz estos niveles antes del laboratorio y el rebase interactivo dejará de parecer magia.

## Recursos en inglés

### GitHub Skills: Review pull requests, Resolve merge conflicts, Release-based workflow — GitHub
- **URL:** https://github.com/skills/review-pull-requests · https://github.com/skills/resolve-merge-conflicts · https://github.com/skills/release-based-workflow
- **Autor / organización:** GitHub
- **Idioma:** Inglés
- **Tipo:** Cursos interactivos dentro de tu propia cuenta de GitHub (un bot te guía en issues)
- **Duración aproximada:** 45-60 min cada uno
- **Cubre:** Code review (comentarios, sugerencias, aprobación), conflictos, tags, releases, flujo basado en releases.
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre, requiere cuenta de GitHub
- **Por qué lo recomiendo:** Son cursos oficiales y se hacen **haciendo**: copias el repositorio del curso, sigues las instrucciones y el bot comprueba cada paso. Es el calentamiento perfecto para el laboratorio.

### GitHub Docs: Pull requests, protected branches, releases y plantillas — GitHub
- **URL:** Pull request reviews: https://docs.github.com/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/about-pull-request-reviews · Protected branches: https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches · Rulesets: https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets · CODEOWNERS: https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners · Releases: https://docs.github.com/en/repositories/releasing-projects-on-github/about-releases · GitHub flow: https://docs.github.com/en/get-started/using-github/github-flow
- **Autor / organización:** GitHub
- **Idioma:** Inglés (GitHub Docs tiene traducción automática al español en el selector de idioma; la versión inglesa es la que manda)
- **Tipo:** Documentación oficial
- **Duración aproximada:** 2-3 h para las páginas indicadas
- **Cubre:** Pull Requests, code review, branch protection, releases, plantillas, GitHub Flow.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la fuente de verdad de todo lo que configurarás en el laboratorio. GitHub cambia la interfaz a menudo; la documentación siempre va por delante de los vídeos.

### Comparing Git workflows y Trunk-based development — Atlassian
- **URL:** https://www.atlassian.com/git/tutorials/comparing-workflows (incluye Feature Branch y Gitflow) · https://www.atlassian.com/continuous-delivery/continuous-integration/trunk-based-development
- **Autor / organización:** Atlassian
- **Idioma:** Inglés
- **Tipo:** Artículos-tutorial con diagramas
- **Duración aproximada:** 60-90 min
- **Cubre:** Estrategias de branching.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la comparación más citada de flujos de trabajo con Git, con diagramas claros de cada uno. Fíjate en que los propios autores señalan que Gitflow ha quedado como flujo heredado frente a los flujos basados en trunk para equipos con CI/CD.

### Trunk Based Development — Paul Hammant
- **URL:** https://trunkbaseddevelopment.com/
- **Autor / organización:** Paul Hammant (consultor de entrega continua; el sitio es de código abierto)
- **Idioma:** Inglés
- **Tipo:** Sitio de referencia
- **Duración aproximada:** 60 min para la introducción, "Short-Lived Feature Branches", "Branch for Release" y "Feature Flags"
- **Cubre:** Estrategias de branching, relación con CI/CD.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Explica el "por qué" del trunk-based development y responde a las objeciones habituales. Es la estrategia que usarás en el resto de la ruta y en el Proyecto Final, así que conviene entender sus reglas de verdad y no solo el nombre.

## Documentación oficial

- **Git, referencia de comandos:** https://git-scm.com/docs (lee `git-merge`, `git-rebase`, `git-tag`, `git-stash`, `git-cherry-pick`, `git-log` con `--graph`)
- **gitattributes:** https://git-scm.com/docs/gitattributes (finales de línea, archivos binarios, `linguist`)
- **GitHub Docs, quickstart de revisión de PRs:** https://docs.github.com/en/pull-requests/get-started/reviewing-pull-requests-quickstart
- **GitHub Docs, comentar en un PR (sugerencias aplicables):** https://docs.github.com/en/pull-requests/how-tos/review-pull-requests/commenting-on-a-pull-request
- **GitHub Docs, aprobar un PR con revisiones requeridas:** https://docs.github.com/en/pull-requests/how-tos/review-pull-requests/approving-a-pull-request-with-required-reviews
- **GitHub Docs, resolver conflictos (web y terminal):** https://docs.github.com/en/pull-requests/how-tos/merge-and-close-pull-requests/resolving-a-merge-conflict-on-github · https://docs.github.com/en/pull-requests/how-tos/merge-and-close-pull-requests/resolving-a-merge-conflict-using-the-command-line
- **GitHub Docs, squash de commits en PRs:** https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/configuring-commit-squashing-for-pull-requests
- **GitHub Docs, gestionar una regla de protección de rama:** https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/managing-a-branch-protection-rule · Convertir a rulesets: https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/converting-branch-protections-to-rulesets
- **GitHub Docs, releases:** https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository
- **GitHub Docs, plantillas de PR e issues:** https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/about-issue-and-pull-request-templates · https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/creating-a-pull-request-template-for-your-repository · https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository
- **GitHub Docs, flujos de trabajo con Git:** https://docs.github.com/en/get-started/git-basics/git-workflows
- **Glosario de GitHub:** https://docs.github.com/en/get-started/learning-about-github/github-glossary

## Ruta recomendada de estudio

1. **Leer** Pro Git capítulo 3 completo, con la terminal abierta reproduciendo los ejemplos (2 h). Céntrate en "Reorganizar el Trabajo Realizado" hasta entender el dibujo del rebase y "Los Peligros de Hacer Rebase".
2. **Hacer** en Learn Git Branching los niveles de "Acelerando" (rebase, rebase interactivo) y toda la pestaña "Remoto" (2-3 h, en varias sesiones).
3. **Hacer** GitHub Skills "Review pull requests" y "Resolve merge conflicts" (1,5-2 h). Anota qué botones usas: los repetirás en el laboratorio.
4. **Leer** en GitHub Docs "About pull request reviews", el quickstart de revisión y "Commenting on a pull request" (45 min). Aprende a hacer una sugerencia aplicable (bloque ```suggestion```).
5. **Ver** la parte de colaboración del curso de MoureDev (2 h, opcional si el punto 3 te ha quedado claro).
6. **Leer** Pro Git capítulo 5 (flujos de trabajo distribuidos) y capítulo 6 (1,5 h). Fíjate en la idea de "rama de tema" corta.
7. **Leer** Atlassian "Comparing workflows" y trunkbaseddevelopment.com (1,5 h) y **hacer** el módulo de Microsoft Learn de estrategias de rama (1 h). Al terminar debes poder dibujar los tres flujos y decir qué tamaño de equipo y qué ritmo de despliegue encaja con cada uno.
8. **Leer** "About protected branches", "About rulesets", "About code owners" y "About releases" (1 h). **Hacer** GitHub Skills "Release-based workflow" (1 h).
9. **Hacer el laboratorio** (8-10 h, en tres o cuatro sesiones: preparación y PRs, conflictos y rebase, releases y gobernanza, decisión de estrategia).
10. **Responder la evaluación** y **revisar el checklist**.

Si vas justo de tiempo: obligatorios los puntos 1, 3, 4, 7, 8 y 9.

## Laboratorio

### Objetivo

Simular un equipo de dos desarrolladores trabajando sobre el mismo repositorio de GitHub durante "tres sprints": abrir Pull Requests con revisión real, provocar y resolver conflictos, limpiar el historial con rebase interactivo, publicar dos releases etiquetadas y dejar el repositorio gobernado con protección de rama, CODEOWNERS y plantillas. Al final decides y justificas qué estrategia de branching usaría ese equipo.

### Requisitos

- Cuenta de GitHub con SSH. Repositorio nuevo **público** llamado `lab-git-equipo` (en el plan gratuito de GitHub la protección de ramas solo está disponible en repositorios públicos).
- Dos "desarrolladores": **Ana** y **Luis**. Opción A (recomendada): tú eres Ana y un compañero de la ruta o el mentor es Luis, con su propia cuenta y acceso de colaborador al repositorio. Opción B (en solitario): tú haces los dos papeles con **dos clones locales** en carpetas distintas (`~/lab-git/ana` y `~/lab-git/luis`), cada uno con su identidad local de Git. En la opción B habrá pasos (aprobar tu propio PR) que GitHub no permite: se indica qué hacer en cada caso.
- Documenta todo en `laboratorio-git.md`: comandos, salidas relevantes (`git log --oneline --graph --all` después de cada parte) y capturas de GitHub con tu usuario visible.

### Instrucciones

**Parte A — Preparación del equipo (45-60 min)**

1. Crea el repositorio `lab-git-equipo` en GitHub con README y licencia MIT. Clónalo dos veces (o una vez cada desarrollador):
   ```bash
   git clone git@github.com:<usuario>/lab-git-equipo.git ~/lab-git/ana
   git clone git@github.com:<usuario>/lab-git-equipo.git ~/lab-git/luis
   cd ~/lab-git/ana  && git config user.name "Ana Dev"  && git config user.email "ana@example.com"
   cd ~/lab-git/luis && git config user.name "Luis Ops" && git config user.email "luis@example.com"
   ```
   Comprueba con `git config --show-origin user.name` en cada clon de dónde sale cada valor (local frente a global). Explica por qué una empresa exige que el correo del commit sea el corporativo y qué pasa con el "verified" de GitHub cuando el correo no está asociado a la cuenta.
2. Como Ana, crea la estructura inicial del proyecto (un pequeño kit de operaciones): `scripts/backup.sh` (un script Bash sencillo que comprime un directorio con fecha), `docs/runbook.md` (con secciones "Propósito", "Pasos", "Rollback") y `CHANGELOG.md` con una sección `## [Unreleased]`. Haz commit y push a `main`. Luis hace `git pull` y comprueba que lo tiene.
3. Protege `main` (Settings → Branches o Rulesets): requerir Pull Request antes de fusionar, **1 aprobación** requerida, descartar aprobaciones obsoletas cuando se suben commits nuevos, bloquear force-push y borrado. Intenta hacer `git push` directo a `main` desde el clon de Luis con un cambio trivial y captura el rechazo. Explica qué protege cada casilla que marcaste.

**Parte B — Sprint 1: Pull Requests con revisión (90 min)**

4. Ana crea la rama `feature/backup-retencion` y añade al script una variable `RETENCION_DIAS` y un `find ... -mtime +$RETENCION_DIAS -delete`. Tres commits pequeños con mensajes en imperativo. Push y abre un PR hacia `main` con título claro y descripción: qué cambia, por qué, cómo probarlo.
5. Luis revisa el PR **en GitHub**: al menos dos comentarios en línea (uno pidiendo un cambio, otro preguntando algo), una **sugerencia aplicable** (bloque de sugerencia que Ana pueda aceptar con un clic) y termina con "Request changes". Captura.
6. Ana responde: acepta la sugerencia desde la web (fíjate en que eso crea un commit en la rama), corrige lo que Luis pidió con un commit nuevo desde su clon, y marca las conversaciones como resueltas. Luis vuelve a revisar y **aprueba**. Fusiona con **Squash and merge** y borra la rama. En la opción B (solitario): GitHub no deja aprobar tu propio PR; documenta el bloqueo con captura, pide al mentor o a un compañero que apruebe, o baja temporalmente a 0 aprobaciones **explicando por qué en producción eso sería inaceptable** y vuelve a subirlo a 1 después.
7. Ambos clones: `git switch main && git pull && git log --oneline --graph`. Observa que en `main` hay **un solo commit** por el PR aunque la rama tenía cuatro o cinco. Explica qué hace squash merge y qué se pierde y qué se gana frente a un merge normal. Borra la rama local (`git branch -d`) y limpia referencias remotas (`git fetch --prune`).

**Parte C — Sprint 2: conflictos y rebase (2 h)**

8. Conflicto provocado. Ana crea `feature/runbook-rollback` y edita la línea del título de la sección "Rollback" de `docs/runbook.md` y añade pasos. Luis, **desde `main` actualizado**, crea `fix/runbook-typos` y edita **la misma línea** del título. Luis abre PR primero, se aprueba y se fusiona. Ana abre su PR: GitHub avisa de conflicto. Resuélvelo **desde la terminal**:
   ```bash
   git switch feature/runbook-rollback
   git fetch origin
   git merge origin/main        # o git rebase origin/main; anota cuál eliges y por qué
   git status                   # localiza el archivo en conflicto
   ```
   Abre el archivo, explica los marcadores `<<<<<<< HEAD`, `=======`, `>>>>>>>`, decide la versión final (probablemente una mezcla de ambas), `git add`, completa el merge o el rebase, push y comprueba que el PR ya se puede fusionar. Anota la diferencia entre "ours" y "theirs" en un merge y en un rebase (se invierten: explica por qué).
9. Segundo conflicto, esta vez resuelto **desde la web de GitHub** con el editor de conflictos (provoca uno similar en `CHANGELOG.md`). Compara ambas experiencias: cuándo vale la web y cuándo hace falta la terminal (conflictos en varios archivos, binarios, necesidad de ejecutar pruebas).
10. Rebase para actualizar. Luis crea `feature/backup-logs` con dos commits. Mientras, Ana fusiona otro PR pequeño a `main`. Luis ejecuta `git fetch && git rebase origin/main` y observa con `git log --oneline --graph --all` que sus commits ahora están **encima** del nuevo `main`, con hashes nuevos. Explica por qué cambian los hashes y por qué ahora necesita `git push --force-with-lease` (y por qué **nunca** `--force` a secas ni sobre `main`).
11. Rebase interactivo para limpiar. Antes de abrir el PR, Luis tiene cuatro commits tipo "wip", "arreglo", "otro arreglo", "ahora sí". Ejecuta `git rebase -i origin/main`, usa `squash` o `fixup` para dejar **un commit** con un buen mensaje, y `reword` para mejorarlo. Push con `--force-with-lease`, abre PR, revisión, aprobación, esta vez fusiona con **Rebase and merge** y compara el historial resultante con el del squash del Sprint 1.
12. Regla de oro. Escribe en `laboratorio-git.md` un párrafo titulado "Cuándo NO hacer rebase" con al menos tres situaciones concretas y qué harías en su lugar.

**Parte D — Sprint 3: tags y releases (60 min)**

13. Ana actualiza `CHANGELOG.md` moviendo lo de `[Unreleased]` a `## [1.0.0] - <fecha>` mediante PR. Tras fusionar, en `main` actualizado:
    ```bash
    git tag -a v1.0.0 -m "Primera versión estable del kit de operaciones"
    git push origin v1.0.0
    git tag -n1 && git show v1.0.0 --stat
    ```
    Explica la diferencia entre un tag ligero y uno anotado, y qué significa cada número de `MAJOR.MINOR.PATCH` en versionado semántico.
14. En GitHub crea una **Release** a partir de `v1.0.0`: usa "Generate release notes", edita las notas para que un usuario las entienda, adjunta `scripts/backup.sh` como asset. Captura.
15. Luis arregla un bug pequeño mediante PR. Decide entre `v1.0.1` y `v1.1.0` justificándolo, etiqueta, publica una segunda release y comprueba `git describe --tags` en un clon. Explica cómo un pipeline de CI/CD podría dispararse "cuando se publica un tag `v*`" (lo harás en el curso 7).

**Parte E — Gobernanza del repositorio (60-90 min)**

16. Crea `.github/CODEOWNERS` asignando `scripts/` a Ana y `docs/` a Luis (en la opción B, usa tu usuario y el del mentor o compañero). Activa en la protección de `main` "Require review from Code Owners". Abre un PR que toque `scripts/` y comprueba que GitHub solicita automáticamente la revisión al propietario. Explica qué problema organizativo resuelve CODEOWNERS.
17. Crea `.github/pull_request_template.md` con secciones: "Qué cambia", "Por qué", "Cómo se ha probado", "Checklist" (casillas: he actualizado el CHANGELOG, he probado el script, no he incluido secretos). Crea dos plantillas de issue en `.github/ISSUE_TEMPLATE/` (informe de bug y solicitud de cambio, en formato YAML de formularios). Abre un PR y un issue para comprobar que se aplican.
18. Opcional: añade `.gitattributes` con `* text=auto` y `*.sh text eol=lf`, y explica qué problema evita cuando en el equipo hay gente en Windows. Ejecuta `git add --renormalize .` y observa si algo cambia.
19. Revisa la pestaña "Insights → Network" o `git log --oneline --graph --all --decorate` y pega el grafo final en `laboratorio-git.md`, señalando dónde hubo squash, dónde rebase y dónde están los tags.

**Parte F — Decisión de estrategia (45 min)**

20. Escribe `estrategia-branching.md` (1-2 páginas) para este escenario ficticio: "Equipo de 6 personas que mantiene una plataforma interna; despliegan a producción varias veces por semana con CI/CD; una vez al trimestre entregan una versión empaquetada a un cliente externo que la instala en su propio centro de datos y exige soporte de esa versión durante un año". Compara **trunk-based development**, **GitHub Flow** y **Gitflow**: dibuja los tres, indica ventajas e inconvenientes para el escenario, y **elige** una (o una combinación, por ejemplo trunk-based con ramas de release) justificando con los criterios: frecuencia de despliegue, necesidad de mantener versiones antiguas, tamaño del equipo, madurez del CI/CD, coste de los conflictos. Incluye qué reglas de protección y qué convención de nombres de rama y de commits aplicarías.
21. Termina con una tabla "Comando o acción ↔ GitHub ↔ GitLab o Azure Repos" con al menos 8 filas (Pull Request / Merge Request, branch protection / branch policies, CODEOWNERS, releases, plantillas) buscando los equivalentes. Verás en CI/CD que Azure DevOps usa otros nombres para lo mismo.

### Resultado esperado

- Repositorio `lab-git-equipo` público con: `main` protegido, al menos 6 PRs fusionados (con revisiones, una sugerencia aplicada y dos conflictos resueltos), dos tags anotados y dos releases con notas, CODEOWNERS, plantilla de PR y dos plantillas de issue.
- `laboratorio-git.md` con comandos, grafos y explicaciones propias de cada parte.
- `estrategia-branching.md` con la decisión justificada.

### Criterios de validación

- [ ] Los commits de Ana y Luis tienen autores distintos (`git log --format='%h %an %ae %s'`) y el push directo a `main` está bloqueado con captura.
- [ ] Hay al menos un PR con "Request changes", una sugerencia aplicada desde la web y una aprobación posterior; el squash dejó un solo commit en `main`.
- [ ] Los dos conflictos están resueltos (uno por terminal, otro por web) y la explicación de marcadores y de ours/theirs es correcta.
- [ ] El rebase interactivo redujo varios commits a uno; se usó `--force-with-lease` y el párrafo "Cuándo NO hacer rebase" es correcto.
- [ ] Existen `v1.0.0` y una segunda versión anotadas, con releases y notas legibles; la elección PATCH/MINOR está justificada.
- [ ] CODEOWNERS provoca solicitud automática de revisión; las plantillas de PR e issue se aplican.
- [ ] `estrategia-branching.md` compara los tres flujos con criterios y elige uno coherente con el escenario.
- [ ] En una llamada con el mentor, el estudiante resuelve en vivo un conflicto pequeño y explica qué haría si un compañero hubiera hecho force-push sobre `main`.

## Entrega

En tu repositorio de entregas, carpeta `02-modulo-intermedio/04-git-y-github-intermedio/`:

1. `laboratorio-git.md` con el enlace al repositorio `lab-git-equipo` y a los PRs y releases relevantes.
2. `estrategia-branching.md`.
3. `capturas/` (protección de rama, revisión con sugerencia, conflicto, releases, CODEOWNERS en acción).
4. `ENTREGA.md` con evaluación, checklist y uso de IA.

Desde este curso, entrega **mediante un Pull Request** en tu propio repositorio de entregas y pide al mentor la revisión. La entrega del curso es también su práctica.

## Evaluación

1. **Conceptual.** ¿Qué es un Pull Request y qué aporta frente a que cada persona haga `git merge` en su máquina y `push` a `main`? Nombra tres cosas que pasan en un PR y no en un merge local.
2. **Situacional.** Revisas el PR de un compañero y ves un error grave y varios detalles de estilo. ¿Cómo estructuras la revisión (qué va como comentario, qué como sugerencia, qué como "Request changes") para que sea útil y no desanime?
3. **Técnica.** Explica qué produce en el historial cada opción de fusión de GitHub: merge commit, squash and merge, rebase and merge. ¿Cuál elegirías para un equipo que quiere un `main` lineal y por qué?
4. **Troubleshooting.** Al hacer `git pull` aparece `CONFLICT (content): Merge conflict in docs/runbook.md`. Describe paso a paso qué haces, incluyendo cómo sabes qué parte es tuya y cuál del remoto, y cómo abortas si te arrepientes.
5. **Conceptual.** ¿Qué hace `git rebase main` estando en `feature/x`? ¿Por qué cambian los hashes de tus commits y qué consecuencia tiene si otra persona ya había descargado tu rama?
6. **Técnica.** Tienes cinco commits en tu rama con mensajes "wip". Escribe la secuencia de comandos para dejarlos en uno solo con buen mensaje y publicarlo de forma segura. ¿Qué diferencia hay entre `--force` y `--force-with-lease`?
7. **Situacional.** Un compañero hizo `git push --force` sobre `main` y desaparecieron dos commits de otra persona. ¿Cómo los recuperas (pista: `git reflog`, los clones de los demás) y qué regla de protección lo habría impedido?
8. **Conceptual.** ¿Qué diferencia hay entre un tag ligero y uno anotado? ¿Por qué las releases se hacen sobre tags anotados? Un cambio corrige un bug sin tocar la interfaz: ¿PATCH, MINOR o MAJOR?
9. **Técnica.** Explica qué hacen estas tres reglas de protección y qué riesgo evita cada una: requerir PR con 1 aprobación, descartar aprobaciones obsoletas al subir commits nuevos, bloquear force-push.
10. **Situacional.** Tu equipo despliega a producción diez veces al día con CI/CD y todos los cambios son pequeños. Un consultor propone Gitflow "porque es el estándar". Argumenta a favor o en contra con criterios concretos.
11. **Situacional.** Ahora el equipo debe mantener durante un año la versión 2.x instalada en un cliente mientras desarrolla la 3.x. ¿Cómo adaptas el flujo trunk-based (pista: ramas de release, cherry-pick de arreglos)?
12. **Conceptual.** ¿Para qué sirve CODEOWNERS y qué pasa si el propietario está de vacaciones y es el único revisor posible? ¿Cómo lo evitarías con equipos en lugar de personas?
13. **Troubleshooting.** Un PR muestra "This branch is out-of-date with the base branch" y el botón de merge está bloqueado. Da dos formas de resolverlo desde la terminal y explica qué historial produce cada una.
14. **Reflexión.** ¿Qué parte del laboratorio te resultó más incómoda (revisar, ser revisado, resolver conflictos, rebase) y qué harías para que en un equipo real esa parte fluyera mejor?

## Checklist final

Antes de continuar, deberías poder:

- [ ] Configurar identidades de Git por repositorio y explicar por qué importa el autor del commit.
- [ ] Abrir un Pull Request bien descrito y revisarlo con comentarios en línea, sugerencias y aprobación o solicitud de cambios.
- [ ] Provocar y resolver un conflicto desde la terminal y desde la web, entendiendo los marcadores.
- [ ] Explicar merge, squash y rebase y elegir el adecuado para un caso dado.
- [ ] Actualizar una rama con `rebase` y limpiar commits con `rebase -i`, publicando con `--force-with-lease`.
- [ ] Enunciar la regla de oro del rebase y recuperar commits perdidos con `reflog`.
- [ ] Crear tags anotados con versionado semántico y publicar releases con notas.
- [ ] Configurar protección de rama, CODEOWNERS y plantillas de PR e issues y explicar qué evita cada una.
- [ ] Comparar trunk-based, GitHub Flow y Gitflow y justificar una elección para un equipo concreto.
- [ ] Entregar tus trabajos de la ruta mediante Pull Requests revisados.

---

*Recursos verificados el 2026-09-27 mediante búsqueda web (existencia y vigencia de las URLs). Si un enlace falla, abre un issue en este repositorio.*
