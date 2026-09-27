# CI/CD

> Módulo: Intermedio · Curso 7 de 11 · Duración estimada: 25-35 horas · Estado: ✅ Completo

## Objetivo

Hasta ahora has construido cosas a mano: una VM, una imagen Docker, un repositorio. En este curso vas a dejar de hacerlo a mano. **CI/CD** (integración continua y entrega/despliegue continuo) es la práctica de que cada cambio de código se compruebe, se empaquete y se despliegue de forma automática, repetible y auditable. Es el corazón operativo de DevOps: sin pipelines no hay despliegues frecuentes, ni rollbacks rápidos, ni confianza para tocar producción un viernes.

Vas a tomar **la aplicación del curso de Docker** (`api-curso`, la API Flask con `/health` y la raíz `/` que devuelve versión y hostname) y construir para ella un pipeline completo en **GitHub Actions**: lint y tests en cada push y en cada pull request, construcción de la imagen, publicación en GitHub Container Registry, despliegue automático a un entorno de *staging* en Azure App Service y despliegue a *producción* con aprobación manual. Después romperás producción a propósito y volverás a la versión anterior con un rollback por tag. Por último leerás y ejecutarás un pipeline equivalente en **Azure DevOps Pipelines**, la otra herramienta que vas a encontrar en empresas que trabajan con Microsoft.

**Antes de empezar** necesitas el repositorio público `api-curso` del curso de Docker (la API Flask con su `Dockerfile` en `app/`), la cuenta de Azure con presupuesto activo y la VM `lab-so` con Docker instalado para la alternativa sin coste.

### Al terminar este curso deberías poder

- Explicar con tus palabras la diferencia entre integración continua, entrega continua y despliegue continuo, y qué problema resuelve cada una.
- Leer y escribir un workflow de GitHub Actions: eventos, jobs, steps, runners, `needs`, `permissions`, expresiones `${{ }}` y contextos.
- Distinguir triggers (`push`, `pull_request`, `workflow_dispatch`, tags) y elegir el adecuado para CI, para staging y para producción.
- Construir un job de CI para Python con lint (`ruff`), tests (`pytest`), matriz y artefactos, y publicar la imagen Docker en GitHub Container Registry con etiquetas por SHA y por versión semántica.
- Configurar entornos con aprobaciones, secretos y variables por entorno, y explicar por qué un secreto nunca debe aparecer en un log.
- Autenticar un pipeline contra Azure con OpenID Connect (sin contraseñas guardadas) y desplegar un contenedor en Azure App Service.
- Ejecutar un rollback redeplegando una versión anterior identificada por tag, y explicar por qué las imágenes inmutables lo hacen posible.
- Traducir un pipeline de GitHub Actions a Azure Pipelines (stages, jobs, tasks, pool, variable groups) y viceversa.

## Prerrequisitos

- Curso 4: Git y GitHub Intermedio (ramas, pull requests, tags, releases, branch protection).
- Curso 6: Docker y Contenedores (la aplicación del curso, su `Dockerfile` y la publicación en un registro).
- Curso 5: Administración de Azure (Azure CLI, grupos de recursos, RBAC, identidades).
- Curso 3: Bash y Python para Automatización (para entender los tests con `pytest` y los scripts del pipeline).
- Repositorio **público** en GitHub con la aplicación (público para que Actions y GHCR sean gratuitos sin límite; en privado tienes 2.000 minutos/mes gratuitos, suficientes pero contados).
- Cuenta de Azure con presupuesto y alertas activos.

## Temario

- Continuous Integration.
- Continuous Delivery.
- Continuous Deployment.
- Pipelines.
- Jobs.
- Stages.
- Agents/Runners.
- Builds.
- Artifacts.
- Environments.
- Variables.
- Secrets.
- Triggers.
- Approvals.
- Rollbacks.
- GitHub Actions.
- Azure DevOps Pipelines.

## Recursos en español

### Automatización del flujo de trabajo con Acciones de GitHub, partes 1 y 2 · Microsoft Learn
- **URL:** Parte 1: https://learn.microsoft.com/es-es/training/paths/github-actions/ · Parte 2: https://learn.microsoft.com/es-es/training/paths/github-actions-2/ · Módulo introductorio suelto: https://learn.microsoft.com/es-es/training/modules/introduction-to-github-actions/
- **Autor / organización:** Microsoft (en colaboración con GitHub)
- **Idioma:** Español
- **Tipo:** Rutas de aprendizaje con ejercicios guiados en tu propio repositorio de GitHub
- **Duración aproximada:** 6-8 h en total (parte 1: ~3 h; parte 2: ~4 h)
- **Cubre:** Workflows, eventos, jobs, runners, CI, artefactos, secretos, entornos, despliegue a Azure, publicación de paquetes.
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre; cuenta Microsoft gratuita para guardar progreso y cuenta de GitHub para los ejercicios
- **Por qué lo recomiendo:** Es el material oficial en español y sigue casi exactamente el orden de este curso. Los ejercicios se hacen en un repositorio tuyo, no en un sandbox, así que lo que aprendes te lo llevas. Es el recurso principal.

### Ruta de aprendizaje: creación de aplicaciones con Azure DevOps · Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/training/paths/build-applications-with-azure-devops/ · Módulo corto de contexto: https://learn.microsoft.com/es-es/training/modules/explore-azure-pipelines/
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Ruta de aprendizaje con proyecto guiado (equipo ficticio "Tailspin")
- **Duración aproximada:** 3-4 h para los módulos de introducción a Azure Pipelines y creación de un pipeline de compilación; el resto es opcional
- **Cubre:** Azure DevOps Pipelines, stages, jobs, agentes, artefactos, variables.
- **Nivel:** Introductorio
- **Acceso:** Libre; requiere organización gratuita de Azure DevOps (ver nota sobre paralelismo en el laboratorio)
- **Por qué lo recomiendo:** Te enseña la misma idea con la otra herramienta del mercado. Léelo comparando cada concepto con su equivalente de GitHub Actions: esa traducción mental es lo que te van a pedir en una entrevista.

### Aprende GitHub Actions desde cero · midudev
- **URL:** https://www.youtube.com/watch?v=-8haKKGc55Y
- **Autor / organización:** Miguel Ángel Durán (midudev), ingeniero de software y divulgador en español
- **Idioma:** Español
- **Tipo:** Vídeo
- **Duración aproximada:** ~1 h (comprueba la duración en la propia página)
- **Cubre:** Workflows, eventos, jobs, steps, acciones del Marketplace, secretos, un CI real para un proyecto.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Publicado en 2024 y muy práctico: ver a alguien escribir un workflow desde cero y equivocarse en directo ayuda a fijar la sintaxis YAML. Complementa, no sustituye, a Microsoft Learn y a la documentación de GitHub.

## Recursos en inglés

### GitHub Actions documentation: Quickstart, Understanding GitHub Actions y Workflow syntax · GitHub Docs
- **URL:** Portal: https://docs.github.com/en/actions · Quickstart: https://docs.github.com/en/actions/get-started/quickstart · Sintaxis de workflows: https://docs.github.com/actions/using-workflows/workflow-syntax-for-github-actions · Entornos: https://docs.github.com/actions/deployment/targeting-different-environments/using-environments-for-deployment
- **Autor / organización:** GitHub
- **Idioma:** Inglés
- **Tipo:** Documentación oficial
- **Duración aproximada:** 2-3 h de lectura inicial; consulta continua después
- **Cubre:** Todo el temario relativo a GitHub Actions: triggers, jobs, runners, artefactos, entornos, aprobaciones, secretos y variables.
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la fuente de verdad. La página de sintaxis la tendrás abierta durante todo el laboratorio: cada clave YAML que uses debería poder localizarla ahí.

### GitHub Skills: Hello GitHub Actions y Publish packages · GitHub
- **URL:** https://github.com/skills/hello-github-actions · https://github.com/skills/publish-packages
- **Autor / organización:** GitHub
- **Idioma:** Inglés
- **Tipo:** Cursos interactivos dentro de un repositorio que se copia a tu cuenta
- **Duración aproximada:** 30 min cada uno
- **Cubre:** Primer workflow, jobs y steps; construcción y publicación de una imagen Docker en GitHub Packages.
- **Nivel:** Introductorio
- **Acceso:** Libre, cuenta de GitHub
- **Por qué lo recomiendo:** Un bot te va guiando paso a paso y corrige tu trabajo en tiempo real. Son el calentamiento perfecto antes del laboratorio. Crea los repositorios como públicos para no gastar minutos.

### Continuous Integration · Martin Fowler
- **URL:** https://martinfowler.com/articles/continuousIntegration.html
- **Autor / organización:** Martin Fowler (Thoughtworks)
- **Idioma:** Inglés
- **Tipo:** Artículo largo
- **Duración aproximada:** 60-90 min
- **Cubre:** Qué es de verdad la integración continua, prácticas que la componen y errores habituales.
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es el texto que definió el término. Te va a servir para no confundir "tener un pipeline" con "hacer integración continua": integrar a diario en la rama principal, build autotestado, arreglar la build rota de inmediato.

### Continuous Delivery (canal de Dave Farley) · YouTube
- **URL:** Canal: https://www.youtube.com/channel/UCCfqyGl3nq_V0bo64CjZh8g · Vídeo de arranque, "The Foundations of Continuous Delivery": https://www.youtube.com/watch?v=kgYhZOzb6EM
- **Autor / organización:** Dave Farley, coautor del libro "Continuous Delivery"
- **Idioma:** Inglés (subtítulos automáticos)
- **Tipo:** Vídeos cortos (15-25 min)
- **Duración aproximada:** 1-2 h para los vídeos fundamentales (foundations, deployment pipeline, trunk-based development)
- **Cubre:** Continuous Delivery y Continuous Deployment como conceptos, pipelines de despliegue, por qué desplegar pequeño y a menudo.
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es el "por qué" de todo el curso, contado por quien ayudó a inventarlo. Sin herramientas, solo ideas que valen para cualquier tecnología.

## Documentación oficial

- **GitHub Actions (portal):** https://docs.github.com/en/actions
- **GitHub Actions: sintaxis de workflows:** https://docs.github.com/actions/using-workflows/workflow-syntax-for-github-actions
- **GitHub Actions: entornos y aprobaciones:** https://docs.github.com/actions/deployment/targeting-different-environments/using-environments-for-deployment
- **GitHub Actions: secretos:** https://docs.github.com/actions/security-guides/using-secrets-in-github-actions
- **GitHub Actions: matrices de jobs:** https://docs.github.com/actions/using-jobs/using-a-matrix-for-your-jobs
- **GitHub Actions: publicar imágenes Docker:** https://docs.github.com/actions/guides/publishing-docker-images
- **GitHub Packages: Container registry (ghcr.io):** https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry
- **GitHub Actions: facturación y minutos gratuitos:** https://docs.github.com/billing/managing-billing-for-github-actions/about-billing-for-github-actions
- **Azure: autenticar GitHub Actions con OpenID Connect:** https://learn.microsoft.com/en-us/azure/developer/github/connect-from-azure-openid-connect · Acción `azure/login`: https://github.com/Azure/login
- **Azure App Service con contenedores:** inicio rápido: https://learn.microsoft.com/en-us/azure/app-service/quickstart-custom-container · configurar contenedor (puerto, variables): https://learn.microsoft.com/en-us/azure/app-service/configure-custom-container · CI/CD desde GitHub Actions: https://learn.microsoft.com/en-us/azure/app-service/deploy-container-github-action
- **Azure Container Apps (alternativa): GitHub Actions:** https://learn.microsoft.com/en-us/azure/container-apps/github-actions · Facturación y cuota gratuita: https://learn.microsoft.com/en-us/azure/container-apps/billing
- **Azure Pipelines (portal):** https://learn.microsoft.com/en-us/azure/devops/pipelines/?view=azure-devops · Qué es: https://learn.microsoft.com/en-us/azure/devops/pipelines/get-started/what-is-azure-pipelines?view=azure-devops · Primer pipeline: https://learn.microsoft.com/en-us/azure/devops/pipelines/create-first-pipeline?view=azure-devops · Esquema YAML: https://learn.microsoft.com/en-us/azure/devops/pipelines/yaml-schema/?view=azure-pipelines
- **Azure Pipelines: paralelismo gratuito y formulario de solicitud:** https://learn.microsoft.com/en-us/azure/devops/pipelines/licensing/concurrent-jobs?view=azure-devops · Formulario: https://aka.ms/azpipelines-parallelism-request

## Ruta recomendada de estudio

1. **Leer** el artículo de Martin Fowler sobre Continuous Integration (60-90 min). Anota las prácticas que enumera: las usarás para evaluar tu propio pipeline al final.
2. **Ver** "The Foundations of Continuous Delivery" de Dave Farley (20 min). Escribe con tus palabras la diferencia entre CI, Continuous Delivery y Continuous Deployment.
3. **Hacer** GitHub Skills "Hello GitHub Actions" (30 min) y **leer** Quickstart y "Understanding GitHub Actions" de la documentación (45 min).
4. **Hacer** la parte 1 de "Automatización del flujo de trabajo con Acciones de GitHub" de Microsoft Learn (3 h).
5. **Ver** el vídeo de midudev (1 h) con la página de sintaxis de workflows abierta al lado.
6. **Hacer** GitHub Skills "Publish packages" (30 min) y **leer** la documentación del Container registry y "Publishing Docker images" (30 min).
7. **Hacer** la parte 2 de la ruta de Microsoft Learn (4 h): entornos, secretos, despliegue a Azure.
8. **Leer** la documentación de entornos y aprobaciones, secretos y OpenID Connect con Azure (1 h). Este bloque es el que separa un pipeline de juguete de uno profesional.
9. **Hacer el laboratorio**, partes A a D (12-16 h, en varias sesiones).
10. **Hacer** los módulos de introducción de "Creación de aplicaciones con Azure DevOps" (2-3 h) y las partes E y F del laboratorio.
11. **Responder la evaluación** y **revisar el checklist**.

Si vas justo de tiempo: haz obligatoriamente los puntos 1, 3, 4, 7, 8 y 9. El resto es refuerzo.

## Laboratorio

### Objetivo

Construir un pipeline completo para la aplicación del curso de Docker: CI en cada push y PR, publicación de la imagen en GitHub Container Registry, despliegue automático a *staging* y con aprobación a *producción* en Azure App Service, rollback por tag, y una versión mínima equivalente en Azure DevOps Pipelines.

### Requisitos

- Repositorio público `api-curso` del curso de Docker: `app/app.py` (Flask; `GET /` devuelve versión y hostname, `GET /health`), `app/requirements.txt`, `app/Dockerfile` (puerto 8000, gunicorn) y `compose.yaml`. En este curso añadirás `tests/`, `requirements-dev.txt` (con `pytest` y `ruff`) y un `ARG APP_VERSION` al Dockerfile.
- Azure CLI autenticada (`az login`) y suscripción con presupuesto.
- VM `lab-so` con Docker (solo para la alternativa sin coste de la parte C).
- Convención: documenta en `laboratorio-cicd.md` cada paso, con enlaces a las ejecuciones (runs) de Actions y capturas donde se vea tu usuario.

> **Sobre el coste.** GitHub Actions y GHCR son gratuitos en repositorios públicos. En Azure, el plan **F1 (Free) de App Service para Linux** admite contenedores personalizados y cuesta 0 (con límites: 60 minutos de CPU al día, sin "always on", arranque en frío). Si en tu región F1 no acepta contenedores o se queda sin cuota, usa **B1** (unos 13 USD/mes, es decir, céntimos por unas horas) y bórralo al terminar. Azure Container Apps con plan de consumo también entra en su cuota gratuita mensual, pero tiene más piezas; aquí se deja como alternativa documentada. Azure DevOps es gratuito hasta 5 usuarios. Regla de siempre: **`az group delete` al terminar y comprobar Cost Management al día siguiente**.

### Instrucciones

**Parte A: CI, tests y artefactos (3-4 h)**

1. Prepara la aplicación. En `app/Dockerfile` sustituye `ENV ... APP_VERSION=0.1.0` por `ARG APP_VERSION=dev` seguido de `ENV APP_VERSION=$APP_VERSION`, para que el pipeline fije la versión en el build. Crea `requirements-dev.txt` en la raíz (con `pytest` y `ruff`) y `tests/test_app.py` con al menos tres tests usando el cliente de pruebas de Flask: `/health` responde 200, `/` devuelve las claves `version` y `hostname`, y `version` coincide con la variable de entorno `APP_VERSION` cuando la defines en el test (piensa cómo). Ejecuta `ruff check .` y `pytest` en local hasta que pasen.
2. Crea `.github/workflows/ci.yml`. Empieza solo con el job de CI y ve ampliándolo:
   ```yaml
   name: ci-cd
   on:
     push:
       branches: ["**"]
       tags: ["v*"]
     pull_request:
       branches: [main]
     workflow_dispatch:
   jobs:
     lint-test:
       runs-on: ubuntu-latest
       strategy:
         matrix:
           python-version: ["3.11", "3.12"]
       steps:
         - uses: actions/checkout@v4
         - uses: actions/setup-python@v5
           with:
             python-version: ${{ matrix.python-version }}
         - run: pip install -r app/requirements.txt -r requirements-dev.txt
         - run: ruff check .
         - run: pytest --junitxml=reporte-${{ matrix.python-version }}.xml
         - uses: actions/upload-artifact@v4
           if: always()
           with:
             name: reporte-pytest-${{ matrix.python-version }}
             path: reporte-*.xml
   ```
   Comprueba en el Marketplace la versión mayor vigente de cada acción (`actions/checkout`, `actions/setup-python`, `actions/upload-artifact`) y fíjala. Explica en el documento qué es un runner `ubuntu-latest`, qué hace `strategy.matrix` (¿cuántos jobs se lanzan?), para qué sirve `if: always()` y dónde ves y descargas el artefacto.
3. Rompe el CI a propósito: crea una rama `feature/rompe-lint`, añade una variable sin usar, abre un **pull request** hacia `main` y captura el check en rojo. Arréglalo en la misma rama y captura el check en verde. En Settings → Branches (o Rulesets) exige que `lint-test` pase antes de fusionar en `main`. Explica la relación entre este check, la branch protection del curso de Git y la definición de integración continua de Fowler.

**Parte B: build y publicación de la imagen en GHCR (2-3 h)**

4. Añade un job `build-push` que dependa de `lint-test` y no se ejecute en pull requests:
   ```yaml
     build-push:
       needs: lint-test
       if: github.event_name != 'pull_request'
       runs-on: ubuntu-latest
       permissions:
         contents: read
         packages: write
       outputs:
         version: ${{ steps.meta.outputs.version }}
       steps:
         - uses: actions/checkout@v4
         - uses: docker/login-action@v3
           with:
             registry: ghcr.io
             username: ${{ github.actor }}
             password: ${{ secrets.GITHUB_TOKEN }}
         - id: meta
           uses: docker/metadata-action@v5
           with:
             images: ghcr.io/${{ github.repository }}
             tags: |
               type=sha
               type=semver,pattern={{version}}
               type=raw,value=latest,enable={{is_default_branch}},priority=50
         - uses: docker/build-push-action@v6
           with:
             context: ./app
             push: true
             tags: ${{ steps.meta.outputs.tags }}
             labels: ${{ steps.meta.outputs.labels }}
             build-args: APP_VERSION=${{ steps.meta.outputs.version }}
   ```
   Haz push a `main` y comprueba en tu perfil → Packages que la imagen existe con las etiquetas `sha-xxxxxxx` y `latest`. Cambia la visibilidad del paquete a **público** (Package settings) para que App Service pueda descargarla sin credenciales. Explica: qué es `GITHUB_TOKEN` y por qué no has creado ningún secreto, qué hace `permissions: packages: write`, qué valor toma la salida `version` en un push a `main` y en un tag (mira las prioridades en la documentación de `metadata-action`), y por qué la etiqueta `latest` es cómoda pero peligrosa para desplegar.
5. Crea un tag de versión: `git tag v1.0.0 && git push origin v1.0.0`. Verifica que aparece la imagen `:1.0.0` y que `docker run --rm -p 8000:8000 ghcr.io/<usuario>/<repo>:1.0.0` en `lab-so` responde en `/` con `"version": "1.0.0"`. Opcional: añade un step de escaneo de vulnerabilidades de la imagen con una acción del Marketplace (por ejemplo, la de Trivy de Aqua Security) en modo informativo (sin hacer fallar el job) y comenta tres hallazgos.

**Parte C: CD a Azure App Service con entornos y aprobaciones (5-6 h)**

6. Crea la infraestructura de destino con Azure CLI (anota cada salida):
   ```bash
   az group create -n rg-cicd -l <tu-region> --tags curso=cicd propietario=<usuario>
   az appservice plan create -n plan-cicd -g rg-cicd --is-linux --sku F1
   for ENV in staging prod; do
     az webapp create -n app-<usuario>-$ENV -g rg-cicd -p plan-cicd \
       --container-image-name ghcr.io/<usuario>/<repo>:1.0.0
     az webapp config appsettings set -n app-<usuario>-$ENV -g rg-cicd --settings WEBSITES_PORT=8000
   done
   ```
   (En CLIs antiguas el parámetro es `--deployment-container-image-name`.) Espera unos minutos y comprueba `curl https://app-<usuario>-staging.azurewebsites.net/`. Si F1 rechaza el contenedor en tu región, repite con `--sku B1` y anótalo. Explica qué es un App Service plan, por qué las dos apps comparten uno y qué hace `WEBSITES_PORT`.
7. Configura la identidad para el pipeline con **OpenID Connect**, siguiendo la documentación oficial: crea un registro de aplicación (o una identidad administrada asignada por el usuario), asígnale el rol **Contributor** con ámbito **solo `rg-cicd`**, y añade dos credenciales federadas con `subject` `repo:<usuario>/<repo>:environment:staging` y `repo:<usuario>/<repo>:environment:production`. Guarda en el repositorio los **secretos** `AZURE_CLIENT_ID`, `AZURE_TENANT_ID` y `AZURE_SUBSCRIPTION_ID`. Explica por qué OIDC es mejor que guardar una contraseña de service principal, y por qué el ámbito del rol es el grupo de recursos y no la suscripción.
8. En Settings → Environments crea `staging` (sin reglas) y `production` con **Required reviewers** (tú mismo) y restricción de despliegue solo desde tags `v*`. En cada entorno define la **variable** `WEBAPP_NAME` con el nombre de su web app. Escribe el job `deploy-staging` con estas piezas, consultando la documentación de cada acción: `needs: build-push`; `if: github.ref == 'refs/heads/main'`; `environment` con `name: staging` y `url: https://${{ vars.WEBAPP_NAME }}.azurewebsites.net`; `permissions` con `id-token: write` y `contents: read`; un step `azure/login@v2` con `client-id`, `tenant-id` y `subscription-id` desde `secrets`; un step `azure/webapps-deploy@v3` con `app-name: ${{ vars.WEBAPP_NAME }}` e `images: ghcr.io/${{ github.repository }}:${{ needs.build-push.outputs.version }}`; y un último step de **smoke test** que espere unos segundos y haga `curl -fsS https://${{ vars.WEBAPP_NAME }}.azurewebsites.net/health`. Haz un cambio pequeño en la app, push a `main`, y comprueba que staging muestra el nuevo `sha-` en `/`. Explica la diferencia entre `secrets` y `vars`, qué es `id-token: write` y por qué el smoke test con `curl -f` convierte "desplegado" en "desplegado y funcionando".
9. **Escribe tú** el job `deploy-production`: añade a `workflow_dispatch` un `inputs.image_tag` opcional (lee la sintaxis en la documentación), haz que el job se ejecute solo con tags `v*` o manualmente, usa `environment: production`, y despliega `inputs.image_tag` si viene informado o, si no, la versión del build. Crea el tag `v1.1.0`, observa cómo el job queda **esperando aprobación**, apruébalo y captura la pantalla de revisión. Explica qué protege una aprobación y qué no (pista: no revisa el código, revisa el momento).
10. **Alternativa sin coste (leer obligatorio, hacer opcional):** instala un **runner autoalojado** en `lab-so` (Settings → Actions → Runners) y crea un job `deploy-vm` con `runs-on: self-hosted` que haga `docker pull` y `docker run -d -p 80:8000` de la imagen. Explica por qué un runner hospedado no puede llegar a tu VM doméstica y qué riesgos tiene un runner autoalojado en un repositorio público. Si lo haces, desregistra el runner al terminar.

**Parte D: triggers, rollback y seguridad del pipeline (3 h)**

11. Introduce un fallo en `main`: haz que `/health` devuelva 500 y crea el tag `v1.2.0`. Aprueba producción y comprueba que el smoke test **falla** y el job queda en rojo (y la app rota; míralo con `curl -i`). Ahora ejecuta el workflow manualmente (`Run workflow` con `image_tag` = `1.1.0`), aprueba, y verifica en `/` que producción volvió a `1.1.0`. Mide el tiempo desde que detectaste el fallo hasta la recuperación. Explica por qué el rollback es solo "volver a desplegar una imagen que ya existía" y qué habría pasado si tus imágenes se etiquetaran solo con `latest`.
12. Arregla `/health`, publica `v1.2.1` y despliega. Completa una tabla con los cuatro triggers usados (push a rama, pull request, tag, manual) indicando qué jobs se ejecutan con cada uno y por qué.

13. Seguridad del pipeline. Intenta imprimir un secreto en un step (`echo ${{ secrets.AZURE_CLIENT_ID }}`) y observa el enmascarado en el log. Bórralo después. Revisa que todos los `uses:` están fijados a versión mayor y explica qué ganarías fijándolos a un SHA de commit. Añade al principio del workflow `permissions: contents: read` a nivel de workflow y verifica que los jobs siguen funcionando con los permisos que declaran. Contrasta tu pipeline con la lista de prácticas de Fowler: ¿cuáles cumples y cuáles no?

**Parte E: el mismo pipeline en Azure DevOps Pipelines (2-3 h)**

14. Crea una organización gratuita en https://dev.azure.com y un proyecto `cicd-lab`. Conecta tu repositorio de GitHub (Pipelines → New pipeline → GitHub) y crea `azure-pipelines.yml` mínimo en el repo:
    ```yaml
    trigger:
      - main
    pool:
      vmImage: ubuntu-latest
    stages:
      - stage: CI
        jobs:
          - job: LintTest
            steps:
              - task: UsePythonVersion@0
                inputs:
                  versionSpec: "3.12"
              - script: pip install -r app/requirements.txt -r requirements-dev.txt
                displayName: Instalar dependencias
              - script: ruff check . && pytest
                displayName: Lint y tests
    ```
    Es muy probable que la primera ejecución falle con "No hosted parallelism has been purchased or granted": las organizaciones nuevas deben **solicitar el paralelismo gratuito** en https://aka.ms/azpipelines-parallelism-request (tarda 2-5 días laborables). Envía la solicitud y, mientras, o bien esperas, o bien registras un **agente autoalojado** en `lab-so` (Project settings → Agent pools) y cambias `pool` por el nombre de tu pool. Documenta cuál de las dos opciones seguiste.
15. Completa la tabla de equivalencias GitHub Actions ↔ Azure Pipelines con al menos 10 filas (workflow/pipeline, job, step, runner/agent, `needs`/`dependsOn`, environment, secret/variable group, artifact, trigger, approval, matrix, `workflow_dispatch`/ejecución manual). Añade una columna para GitLab CI a partir de una búsqueda rápida.

**Parte F: limpieza y verificación de coste (30 min)**

16. `az group delete -n rg-cicd --yes --no-wait`. Borra el registro de aplicación de OIDC (`az ad app delete`) o la identidad administrada. Desregistra runners y agentes autoalojados. Deja el repositorio, los workflows y la imagen en GHCR: los reutilizarás en Monitoreo, Kubernetes y Helm. Al día siguiente captura Cost Management → Análisis de costos filtrado por `rg-cicd` y anota la cifra (debería ser 0 con F1 o céntimos con B1).

### Resultado esperado

- Repositorio con `.github/workflows/ci.yml` (CI + build/push + staging + producción con aprobación + rollback manual) y `azure-pipelines.yml`.
- Imagen en GHCR con etiquetas `sha-*`, `1.0.0`, `1.1.0`, `1.2.0`, `1.2.1` y `latest`.
- `laboratorio-cicd.md` con enlaces a los runs relevantes (CI en rojo y en verde, aprobación de producción, fallo de smoke test, rollback), capturas y explicaciones propias.
- Grupo de recursos borrado y coste verificado.

### Criterios de validación

- [ ] El CI corre en push y en PR, con matriz, artefacto de resultados y el check exigido por la protección de `main`; existe un run en rojo y otro en verde del mismo PR.
- [ ] La imagen se publica en GHCR solo fuera de PRs, con etiquetas por SHA y semver; el estudiante explica `GITHUB_TOKEN` y `permissions`.
- [ ] La autenticación con Azure usa OIDC con credenciales federadas por entorno y rol con ámbito de grupo de recursos; no hay contraseñas en secretos.
- [ ] Staging se despliega automáticamente desde `main` y producción requiere aprobación y tag; el smoke test es parte del job.
- [ ] Hay un run donde el smoke test de producción falla y un run posterior de rollback por `workflow_dispatch` con `image_tag`, con el tiempo de recuperación anotado.
- [ ] La tabla de triggers y la tabla de equivalencias GitHub Actions ↔ Azure Pipelines son correctas.
- [ ] El pipeline de Azure DevOps existe y o bien se ejecutó, o bien está documentada la solicitud de paralelismo y el agente autoalojado.
- [ ] La sección de seguridad (enmascarado, versiones fijadas, permisos mínimos) está hecha y razonada.
- [ ] Todo lo de Azure está borrado y hay captura de coste del día siguiente.

## Entrega

En tu repositorio de entregas, carpeta `02-modulo-intermedio/07-ci-cd/`:

1. `laboratorio-cicd.md` con los enlaces a los runs y las explicaciones.
2. Copia de `ci.yml` y `azure-pipelines.yml` (como archivos, no capturas), y el enlace al repositorio de la aplicación.
3. `equivalencias.md` con las tablas de triggers y de herramientas.
4. Carpeta `capturas/` (checks del PR, paquete en GHCR, aprobación de producción, rollback, Cost Management). Oculta IDs de suscripción y de inquilino.
5. `ENTREGA.md` con evaluación, checklist y uso de IA.

Nota sobre IA: pedirle a una IA "un workflow de GitHub Actions para Python" te dará algo a medias y con acciones desactualizadas. Úsala para que te explique una clave YAML o un error del log, verifica cada acción en su repositorio del Marketplace y declara el uso.

## Evaluación

1. **Conceptual.** Explica con tus palabras integración continua, entrega continua y despliegue continuo. Tu pipeline del laboratorio, ¿en cuál de las tres categorías cae para staging y en cuál para producción? Justifícalo.
2. **Conceptual.** Un equipo tiene un pipeline que compila y pasa tests en cada push, pero cada desarrollador trabaja dos semanas en su rama antes de fusionar. Según Fowler, ¿hacen integración continua? ¿Qué les falta?
3. **Técnica.** Explica qué hacen `needs`, `if`, `permissions` y `outputs` en el job `build-push`. ¿Qué pasaría si quitas `needs: lint-test`?
4. **Situacional.** Un pull request de un colaborador externo (fork) necesita ejecutar el CI. ¿Tiene acceso a tus secretos? ¿Por qué esa restricción es deseable?
5. **Técnica.** Tu imagen se publica con `sha-a1b2c3d`, `1.2.1` y `latest`. Explica qué garantiza cada etiqueta y cuál usarías para desplegar en producción y para el rollback.
6. **Troubleshooting.** El job `deploy-staging` falla en `azure/login` con "AADSTS70021: No matching federated identity record found". Nombra dos causas probables relacionadas con el `subject` de la credencial federada y cómo las comprobarías.
7. **Conceptual.** ¿Qué diferencia hay entre un secreto de repositorio, un secreto de entorno y una variable de entorno (`vars`)? Da un ejemplo de cada uno de tu laboratorio.
8. **Situacional.** Producción está rota a las 18:05 tras el despliegue de `v2.3.0`. Describe paso a paso cómo vuelves a `v2.2.1` con tu pipeline, cuánto tardarías y qué comprobarías después. ¿Qué pasa con la base de datos si `v2.3.0` cambió el esquema?
9. **Conceptual.** ¿Qué es un runner hospedado y uno autoalojado? Da un caso en que el autoalojado es imprescindible y dos riesgos de usarlo en un repositorio público.
10. **Troubleshooting.** El smoke test `curl -f .../health` falla justo después de `azure/webapps-deploy`, pero al minuto la app responde bien. ¿Qué está pasando y cómo harías el pipeline más robusto sin un `sleep` fijo?
11. **Conceptual.** ¿Qué protege una aprobación manual en el entorno `production` y qué no protege? ¿Qué añadirías (revisión de código, tests de integración, ventanas de despliegue) y en qué punto del pipeline?
12. **Técnica.** Traduce a Azure Pipelines: un job con matriz de dos versiones de Python que dependa de otro job y publique un artefacto. Indica las claves YAML equivalentes (`stage`, `job`, `dependsOn`, `strategy.matrix`, `publish`).
13. **Reflexión.** ¿Qué parte del pipeline te dio más problemas y qué aprendiste del log de ejecución para resolverla? ¿Qué añadirías al pipeline si la aplicación fuera real?

## Checklist final

Antes de continuar, deberías poder:

- [ ] Explicar CI, Continuous Delivery y Continuous Deployment con un ejemplo propio.
- [ ] Leer cualquier workflow de GitHub Actions e identificar triggers, jobs, steps, runners y dependencias.
- [ ] Escribir un job de CI para Python con lint, tests, matriz y artefactos.
- [ ] Publicar una imagen Docker en GHCR con etiquetas inmutables desde un pipeline.
- [ ] Configurar entornos con aprobaciones, secretos y variables por entorno.
- [ ] Autenticar un pipeline en Azure con OIDC y rol de ámbito mínimo.
- [ ] Desplegar un contenedor en App Service desde el pipeline y verificar con un smoke test.
- [ ] Hacer un rollback redeplegando un tag anterior y explicar por qué funciona.
- [ ] Leer y escribir un `azure-pipelines.yml` mínimo y traducir conceptos entre herramientas.
- [ ] Tener el repositorio con pipeline funcional (lo reutilizarás en Monitoreo, Kubernetes y Helm) y Azure limpio.

---

*Recursos verificados el 2026-09-27 (existencia y vigencia de las URLs mediante búsqueda web y, cuando el cupo de búsqueda se agotó, mediante los repositorios oficiales de la documentación). Las páginas de Microsoft Learn se enlazan en `es-es` cuando se confirmó la traducción; en el resto se indica cómo cambiar el idioma. Si un enlace falla, abre un issue en este repositorio.*
