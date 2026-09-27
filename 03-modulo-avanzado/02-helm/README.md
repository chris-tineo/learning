# Helm

> Módulo: Avanzado · Curso 2 de 12 · Duración estimada: 20-30 horas · Estado: ✅ Completo

## Objetivo

Al terminar Kubernetes Avanzado tienes una carpeta `k8s/` con una docena de manifiestos que funcionan. Ahora imagina que necesitas desplegar la misma aplicación en desarrollo, en pruebas y en producción, con distintas réplicas, distintos hosts, distintos límites y con o sin base de datos. La opción "copiar la carpeta tres veces y editar a mano" dura hasta el primer cambio que olvidas replicar. Helm resuelve exactamente eso: convierte tus manifiestos en un **chart**, una plantilla parametrizada con valores por entorno, versionada, empaquetada y publicable en un registro como si fuera una imagen de contenedor.

Helm es además la forma en la que vas a instalar casi todo lo demás en Kubernetes: ingress-nginx, metrics-server, Prometheus, Grafana, cert-manager, External Secrets. Todos se distribuyen como charts. Saber leer un chart ajeno (qué valores acepta, qué genera, de qué depende) es tan importante como saber escribir el tuyo.

En este curso convertirás los manifiestos del curso anterior en un chart configurable, con valores para `dev` y `prod`, plantillas con funciones y condicionales, PostgreSQL como dependencia, pruebas, versionado semántico, publicación en GitHub Container Registry como artefacto OCI y despliegue desde el pipeline de GitHub Actions que construiste en el Módulo Intermedio. La parte de AKS y Azure Container Registry es opcional y acotada.

**Antes de empezar** necesitas el clúster local del curso anterior (kind, minikube o k3s) con la aplicación del curso de Docker funcionando desde `k8s/`, y tu repositorio con el pipeline de GitHub Actions. Si borraste el clúster, recréalo con tu `kind-config.yaml`: tarda un minuto.

### Al terminar este curso deberías poder

- Explicar qué problema resuelve Helm, qué es un chart, una release y un repositorio, y cómo Helm guarda el estado de cada release dentro del clúster.
- Leer un chart ajeno: `Chart.yaml`, `values.yaml`, `templates/`, `_helpers.tpl`, `NOTES.txt`, y averiguar con `helm show` y `helm template` qué va a instalar antes de instalarlo.
- Convertir manifiestos de Kubernetes en plantillas Go con valores, funciones (`default`, `quote`, `toYaml`, `include`, `required`, `tpl`), condicionales y bucles.
- Mantener valores por entorno (`values-dev.yaml`, `values-prod.yaml`) y validar el chart con `helm lint` y `helm template` antes de tocar el clúster.
- Declarar dependencias (por ejemplo PostgreSQL) en `Chart.yaml`, resolverlas con `helm dependency update`, activarlas o desactivarlas por entorno y saber qué hacer cuando el chart de un tercero cambia de licencia o de distribución.
- Instalar, actualizar, consultar el historial y revertir releases con `helm install/upgrade/history/rollback` y explicar qué hace cada uno en el clúster.
- Versionar el chart y la aplicación con SemVer, empaquetarlo y publicarlo en un registro OCI (GitHub Container Registry) y, opcionalmente, en Azure Container Registry.
- Escribir y ejecutar pruebas de release con `helm test`.
- Desplegar el chart desde un pipeline de GitHub Actions con un runner self-hosted hacia el clúster local, explicando los riesgos de seguridad de ese runner.

## Prerrequisitos

- Curso 1 del Módulo Avanzado: Kubernetes Avanzado (manifiestos en `k8s/` funcionando).
- Módulo Intermedio: CI/CD (pipeline en GitHub Actions), Docker y Contenedores (imagen publicada en GitHub Container Registry o similar), Git y GitHub Intermedio.
- Clúster local operativo y `kubectl` configurado. Cuenta de Azure solo para la parte opcional.

## Temario

Charts · Templates · Values · Releases · Dependencies · Repositories · Versioning · Upgrade · Rollback · Reutilización de deployments.
**Práctica:** convertir una aplicación Kubernetes en un Helm Chart configurable.

## Recursos en español

### Documentación de Helm en español — helm.sh/es
- **URL:** https://helm.sh/es/docs/
- **Autor / organización:** Proyecto Helm (CNCF), traducción de la comunidad
- **Idioma:** Español (traducción de la documentación de Helm 3; parcial, y puede ir por detrás de la versión en inglés)
- **Tipo:** Documentación oficial
- **Duración aproximada:** 3-4 h (Inicio rápido, Uso de Helm, Charts, Guía de plantillas)
- **Cubre:** Charts, templates, values, releases, repositorios, dependencias, upgrade y rollback.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la documentación oficial en tu idioma. Úsala para la primera lectura de conceptos y de la guía de plantillas; cuando algo no cuadre con lo que ves en tu terminal, consulta la versión en inglés, que es la canónica y la que está al día con Helm 4.

### Versionado Semántico 2.0.0 — semver.org en español
- **URL:** https://semver.org/lang/es/
- **Autor / organización:** Tom Preston-Werner y comunidad (especificación abierta)
- **Idioma:** Español
- **Tipo:** Especificación
- **Duración aproximada:** 20 min
- **Cubre:** Versioning (versión del chart y de la aplicación).
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Helm exige SemVer en `version` y lo recomienda en `appVersion`. Es corta y hay que leerla una vez con calma: MAJOR.MINOR.PATCH, qué obliga a subir cada número y qué son las etiquetas de prelanzamiento.

### Inicio rápido: desarrollo en AKS con Helm — Microsoft Learn
- **URL:** https://learn.microsoft.com/en-us/azure/aks/quickstart-helm (para la versión en español cambia `en-us` por `es-es`) · Helm en Azure Container Registry: https://learn.microsoft.com/en-us/azure/container-registry/container-registry-helm-repos
- **Autor / organización:** Microsoft
- **Idioma:** Inglés (disponible en español)
- **Tipo:** Guía de inicio rápido y documentación
- **Duración aproximada:** 45 min
- **Cubre:** Repositories (OCI en ACR), instalación de un chart en AKS.
- **Nivel:** Intermedio
- **Acceso:** Libre (los recursos de Azure que crea tienen coste; ver parte opcional del laboratorio)
- **Por qué lo recomiendo:** Es la referencia oficial para la parte opcional del laboratorio y para el Proyecto Final: publicar charts en ACR y desplegarlos en AKS. Léela aunque no la ejecutes.

## Recursos en inglés

### Helm Documentation — helm.sh/docs
- **URL:** https://helm.sh/docs/ · Quickstart: https://helm.sh/docs/intro/quickstart/ · Using Helm: https://helm.sh/docs/intro/using_helm/ · Charts: https://helm.sh/docs/topics/charts/ · Chart Template Guide: https://helm.sh/docs/chart_template_guide/ · Best Practices: https://helm.sh/docs/chart_best_practices/ · Tips and Tricks: https://helm.sh/docs/howto/charts_tips_and_tricks/ · Registries (OCI): https://helm.sh/docs/topics/registries/ · Chart Tests: https://helm.sh/docs/topics/chart_tests/ · `helm dependency`: https://helm.sh/docs/helm/helm_dependency/
- **Autor / organización:** Proyecto Helm (CNCF)
- **Idioma:** Inglés
- **Tipo:** Documentación oficial
- **Duración aproximada:** 6-8 h en total a lo largo del curso
- **Cubre:** Todo el temario.
- **Nivel:** Intermedio-avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es el recurso principal del curso. La "Chart Template Guide" es un tutorial completo que hay que hacer con la terminal abierta, no leer. "Best Practices" y "Tips and Tricks" son las páginas que distinguen un chart que funciona de un chart que otros pueden usar.

### Artifact Hub — CNCF
- **URL:** https://artifacthub.io/
- **Autor / organización:** CNCF
- **Idioma:** Inglés
- **Tipo:** Catálogo de charts y otros artefactos cloud native
- **Duración aproximada:** Consulta puntual
- **Cubre:** Repositories, Dependencies (buscar charts de terceros, ver sus valores, su versión y su procedencia).
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es donde se buscan charts. Aprende a leer la ficha de un chart (mantenedor, firma, valores, changelog) antes de instalar nada de terceros en un clúster. Verás que muchos charts tienen varios publicadores: elegir bien es parte del oficio.

### Bitnami Helm Charts — Bitnami (Broadcom)
- **URL:** https://github.com/bitnami/charts (chart de PostgreSQL en `bitnami/postgresql`; instalación por OCI: `oci://registry-1.docker.io/bitnamicharts/postgresql`)
- **Autor / organización:** Bitnami (Broadcom)
- **Idioma:** Inglés
- **Tipo:** Repositorio de charts + documentación (README de cada chart)
- **Duración aproximada:** 45 min para leer el README de PostgreSQL y sus valores
- **Cubre:** Dependencies, Values (un chart de terceros bien hecho que usarás como dependencia).
- **Nivel:** Intermedio-avanzado
- **Acceso:** Libre (Apache 2.0). **Atención:** desde 2025 Bitnami distribuye sus imágenes de contenedor como "Bitnami Secure Images"; las imágenes antiguas basadas en Debian se han movido al registro `bitnamilegacy` de Docker Hub y las gratuitas actuales tienen etiquetas limitadas. El chart sigue siendo libre, pero la imagen que referencia por defecto puede no estar disponible con el tag esperado. El laboratorio explica cómo comprobarlo y qué alternativas hay.
- **Por qué lo recomiendo:** Es el chart de referencia por calidad de plantillas y de `values.yaml`. Aunque acabes usando otra imagen, leer cómo está hecho te enseña más que cualquier tutorial. Y su cambio de distribución es una lección real: las dependencias de terceros cambian y hay que tenerlas controladas.

### CloudNativePG — operador de PostgreSQL para Kubernetes (alternativa)
- **URL:** https://github.com/cloudnative-pg/cloudnative-pg · Charts oficiales: https://github.com/cloudnative-pg/charts
- **Autor / organización:** Comunidad CloudNativePG (proyecto CNCF)
- **Idioma:** Inglés
- **Tipo:** Proyecto de código abierto con charts de Helm
- **Duración aproximada:** 30 min (solo para conocerlo)
- **Cubre:** Dependencies (alternativa al chart de Bitnami para PostgreSQL).
- **Nivel:** Avanzado
- **Acceso:** Libre (Apache 2.0)
- **Por qué lo recomiendo:** Es la forma "moderna" de ejecutar PostgreSQL en Kubernetes (un operador en vez de un StatefulSet a mano) y la alternativa recomendada si el chart de Bitnami te da problemas de imagen. No es necesario dominarlo ahora; basta con instalarlo una vez si eliges esa ruta en la Parte D.

### Working with the Container registry (GitHub Packages) — GitHub Docs
- **URL:** https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry · Runners self-hosted: https://docs.github.com/en/actions/concepts/runners/self-hosted-runners y https://docs.github.com/en/actions/how-tos/manage-runners/self-hosted-runners/add-runners
- **Autor / organización:** GitHub
- **Idioma:** Inglés
- **Tipo:** Documentación oficial
- **Duración aproximada:** 45 min
- **Cubre:** Repositories (publicar el chart como artefacto OCI en `ghcr.io`), despliegue desde el pipeline.
- **Nivel:** Intermedio
- **Acceso:** Libre (GHCR es gratuito para paquetes públicos; los privados tienen cuota gratuita limitada)
- **Por qué lo recomiendo:** GHCR acepta charts de Helm como artefactos OCI con el mismo login que usas para las imágenes. Es la forma gratuita y sencilla de tener tu propio "repositorio de charts" sin montar nada.

### Kubernetes Tutorial for Beginners (sección de Helm) — TechWorld with Nana
- **URL:** Canal: https://www.youtube.com/c/techworldwithnana (el curso completo de Kubernetes que usaste en el curso anterior incluye un bloque dedicado a Helm)
- **Autor / organización:** Nana Janashia (TechWorld with Nana)
- **Idioma:** Inglés (subtítulos)
- **Tipo:** Vídeo
- **Duración aproximada:** 20-30 min el bloque de Helm
- **Cubre:** Charts, Templates, Values, Releases, Repositories a nivel conceptual.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Para entender en veinte minutos qué es un chart y por qué existe antes de meterte en la guía de plantillas. Vídeo introductorio; el detalle está en la documentación.

## Documentación oficial

- **Helm — Documentación:** https://helm.sh/docs/ (índice) y en español https://helm.sh/es/docs/
- **Helm — Chart Template Guide** (hazla completa): https://helm.sh/docs/chart_template_guide/
- **Helm — Chart Best Practices:** https://helm.sh/docs/chart_best_practices/
- **Helm — Charts Tips and Tricks** (checksum de ConfigMaps, `required`, `tpl`, hooks): https://helm.sh/docs/howto/charts_tips_and_tricks/
- **Helm — Use OCI-based registries:** https://helm.sh/docs/topics/registries/
- **Helm — Chart Tests:** https://helm.sh/docs/topics/chart_tests/
- **Helm — Chart dependencies (`helm dependency`):** https://helm.sh/docs/helm/helm_dependency/
- **SemVer 2.0.0:** https://semver.org/ (español: https://semver.org/lang/es/)
- **GitHub — Container registry:** https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry
- **Microsoft Learn — Helm en AKS:** https://learn.microsoft.com/en-us/azure/aks/quickstart-helm · **Charts en ACR:** https://learn.microsoft.com/en-us/azure/container-registry/container-registry-helm-repos

## Ruta recomendada de estudio

1. **Ver** el bloque de Helm del curso de TechWorld with Nana (30 min) para tener el mapa: chart, release, values, repositorio.
2. **Leer** Quickstart y Using Helm (español o inglés) e **instalar** Helm (1 h). Instala un chart ajeno (Parte A) y mira qué ha creado en el clúster y dónde guarda Helm la release.
3. **Hacer** la Chart Template Guide completa, capítulo a capítulo, con `helm template` abierto en la terminal (3-4 h). No la leas: escribe cada ejemplo. Es la parte teórica principal del curso.
4. **Leer** Charts (estructura, `Chart.yaml`, dependencias) y SemVer (1 h). **Hacer** las Partes B y C del laboratorio.
5. **Leer** Best Practices y Tips and Tricks (1 h) y revisa tu chart contra ellas: nombres, labels estándar, `required`, checksum de ConfigMaps.
6. **Leer** el README del chart de PostgreSQL de Bitnami y la página `helm dependency` (45 min). **Hacer** la Parte D.
7. **Hacer** las Partes E, F y G (ciclo de vida, versionado y publicación OCI, pruebas), leyendo Registries y Chart Tests cuando llegues a cada una (3-4 h).
8. **Leer** la documentación de runners self-hosted de GitHub (30 min) y **hacer** la Parte H.
9. **Leer** el inicio rápido de Helm en AKS y la página de ACR (30 min). Si decides hacer la parte opcional, **hacer** la Parte I en una sola sesión.
10. **Responder la evaluación** y **revisar el checklist**.

Si vas justo de tiempo: haz obligatoriamente los puntos 2, 3, 4, 7 y 8.

## Laboratorio

### Objetivo

Convertir los manifiestos de `k8s/` en un chart `api` configurable por entorno, con PostgreSQL como dependencia opcional, pruebas, versionado semántico, publicación en GitHub Container Registry y despliegue automático desde GitHub Actions al clúster local.

### Requisitos

- Clúster local del curso anterior en marcha (`kubectl get nodes` responde) con ingress-nginx y metrics-server instalados.
- `helm` instalado (versión 3.x o 4.x; anota cuál con `helm version`. Helm 4 mantiene la compatibilidad con los charts `apiVersion: v2` de Helm 3 y los comandos de este laboratorio funcionan en ambas).
- Repositorio Git de la aplicación con el pipeline del Módulo Intermedio y permiso para publicar paquetes en GHCR (un token clásico con `write:packages` o el `GITHUB_TOKEN` del propio workflow).
- Convención: el chart vive en `charts/api/` dentro del repositorio de la aplicación. Documenta en `laboratorio-helm.md`.

> **Sobre el coste.** Las Partes A a H son locales y gratuitas (GHCR es gratuito para paquetes públicos). La Parte I es opcional: un Azure Container Registry `Basic` cuesta unos 0,17 USD por día y el AKS de un nodo B2s en nivel Free unos 1-2 USD por día. En una sesión de 2-3 horas con borrado del grupo de recursos al final, céntimos. Presupuesto y alerta activos antes de empezar.

### Instrucciones

**Parte A — Helm, releases y un chart ajeno (60 min)**

1. Instala Helm siguiendo el Quickstart. Ejecuta `helm version`, `helm env` y `helm list -A`. Si instalaste ingress-nginx o metrics-server con `kubectl apply` en el curso anterior, no aparecerán: Helm solo conoce lo que instala él. Explica qué es una release y dónde guarda Helm su estado (`kubectl get secrets -A -l owner=helm`).
2. Instala un chart ajeno para ver el flujo completo: `helm repo add metrics-server https://kubernetes-sigs.github.io/metrics-server/`, `helm repo update`, y después `helm install metrics-server metrics-server/metrics-server -n kube-system --set args="{--kubelet-insecure-tls}"` (si ya tienes metrics-server por manifiesto del curso anterior, bórralo antes con `kubectl delete -f components.yaml` o instala el chart en un namespace de prueba con `--dry-run`; no lo tengas dos veces). Antes de instalar, inspecciona: `helm search repo metrics-server --versions`, `helm show chart`, `helm show values` y `helm template`. Explica qué te dice cada uno, qué es el `index.yaml` de un repositorio clásico y por qué nunca deberías instalar un chart sin haber visto su `values.yaml`.
3. Busca en Artifact Hub el chart de `ingress-nginx` y el de `postgresql`. Para cada uno anota: quién lo publica, cuántos publicadores distintos hay, versión del chart y de la app, si está firmado o verificado. Explica cómo decidirías cuál usar en una empresa.
4. `helm create api` en `charts/` y estudia lo generado: `Chart.yaml`, `values.yaml`, `templates/` (deployment, service, ingress, hpa, serviceaccount, `_helpers.tpl`, `NOTES.txt`, `tests/`), `.helmignore`. Ejecuta `helm template api charts/api | less` y relaciona cada bloque de YAML con la plantilla que lo produce. Explica qué es `.Release`, `.Chart`, `.Values` y qué hace `include "api.fullname"`.

**Parte B — Convertir los manifiestos en plantillas (2-3 h)**

5. Sustituye las plantillas generadas por las tuyas partiendo de `k8s/`, un objeto por archivo, en este orden y comprobando con `helm template` tras cada uno:
   - `deployment.yaml`: imagen como `{{ .Values.image.repository }}:{{ .Values.image.tag | default .Chart.AppVersion }}`, `replicaCount`, `resources` con `toYaml | nindent`, probes parametrizadas, `envFrom` hacia el ConfigMap y el Secret, y la anotación `checksum/config` sobre el ConfigMap (Tips and Tricks) para que un cambio de configuración provoque un rollout.
   - `configmap.yaml` y `secret.yaml`: los valores vienen de `.Values.config` (un mapa que recorres con `range`) y `.Values.secrets`. En el Secret usa `stringData` para no codificar a mano, y marca la contraseña como obligatoria con `required "Debes definir secrets.databasePassword" .Values.secrets.databasePassword`.
   - `service.yaml`: tipo y puerto parametrizados.
   - `ingress.yaml`: envuelto en `{{- if .Values.ingress.enabled }}`, con host, `ingressClassName`, anotaciones y TLS desde valores.
   - `hpa.yaml`: solo si `autoscaling.enabled`; cuando está activo, el `replicas` del Deployment no debe renderizarse (mira cómo lo hace el chart generado).
   - `postgres.yaml` (Service headless + StatefulSet + PVC) **solo temporalmente**: en la Parte D lo sustituirás por una dependencia. Envuélvelo en `{{- if .Values.postgresqlLocal.enabled }}`.
6. En `_helpers.tpl` define `api.name`, `api.fullname`, `api.labels` (con las labels recomendadas `app.kubernetes.io/name`, `instance`, `version`, `managed-by`, `helm.sh/chart`) y `api.selectorLabels`. Explica por qué las labels del `selector` deben ser un subconjunto estable y no incluir la versión.
7. Usa al menos una vez cada función: `default`, `quote`, `toYaml`, `nindent`, `include`, `required`, `tpl` (por ejemplo para que el host del Ingress pueda contener `{{ .Release.Namespace }}`), y un `range` sobre una lista de variables de entorno extra (`extraEnv`). Anota en el laboratorio un ejemplo de cada una con su salida.
8. Escribe `NOTES.txt` para que al instalar diga cómo probar `/health` según el tipo de Service e Ingress configurado (con condicionales). Escribe también el `README.md` del chart con la tabla de valores.

**Parte C — Valores por entorno, lint y template (60-90 min)**

9. Crea `values.yaml` con valores por defecto seguros (1 réplica, sin Ingress, sin HPA, recursos pequeños), `values-dev.yaml` (2 réplicas, Ingress `api-dev.curso.local`, TLS autofirmado, sin HPA, PostgreSQL activado) y `values-prod.yaml` (3 réplicas, Ingress `api.curso.local`, HPA 2-6, anti-affinity preferida, recursos mayores, PostgreSQL desactivado porque en producción sería un servicio gestionado). Explica la regla de precedencia: `values.yaml` < `-f values-dev.yaml` < `--set`.
10. `helm lint charts/api` y `helm lint charts/api -f charts/api/values-prod.yaml`. Provoca y corrige al menos tres errores: una indentación mal hecha con `nindent`, un valor obligatorio ausente (`required`) y una clave que no existe en `values.yaml`. Anota los mensajes.
11. `helm template api charts/api -f charts/api/values-dev.yaml > /tmp/dev.yaml` y lo mismo para prod. Compara con `diff` y comprueba que la diferencia es exactamente la que esperas. Ejecuta también `helm install api charts/api -f ... --dry-run --debug` y explica qué añade `--dry-run` frente a `template` (contacta con el clúster, valida contra la API).
12. Opcional recomendado: escribe `values.schema.json` con los tipos y valores obligatorios y comprueba que `helm lint` e `install` fallan cuando pasas un valor incorrecto (por ejemplo `replicaCount: "dos"`).

**Parte D — PostgreSQL como dependencia (90 min)**

13. Borra la plantilla `postgres.yaml` temporal. En `Chart.yaml` declara la dependencia:
    ```yaml
    dependencies:
      - name: postgresql
        version: "<versión que veas en Artifact Hub>"
        repository: oci://registry-1.docker.io/bitnamicharts
        condition: postgresql.enabled
    ```
    Ejecuta `helm dependency update charts/api`, mira `Chart.lock` y `charts/postgresql-*.tgz`, y explica qué hace cada archivo y cuál debe ir en Git (el lock sí, el `.tgz` normalmente no: añádelo a `.gitignore` y regenera con `helm dependency build`).
14. En `values-dev.yaml` configura la dependencia bajo la clave `postgresql:` (`enabled: true`, `auth.postgresPassword` o `auth.existingSecret`, `primary.persistence.size: 1Gi`). Conecta la API a `<release>-postgresql` por DNS. Instala en un namespace `dev` (`helm install api charts/api -n dev --create-namespace -f charts/api/values-dev.yaml`).
15. **Si el Pod de PostgreSQL queda en `ImagePullBackOff`**, no es culpa tuya: comprueba con `kubectl describe` qué imagen y tag intenta descargar. Por el cambio de distribución de Bitnami, puede que la imagen por defecto ya no se publique con ese tag. Documenta el diagnóstico y elige una salida, justificándola: (a) sobrescribir `postgresql.image.registry/repository/tag` para apuntar al registro `bitnamilegacy` (imágenes antiguas, sin actualizaciones de seguridad, aceptable solo en laboratorio), (b) usar una imagen `latest` gratuita si existe, o (c) sustituir la dependencia por CloudNativePG (instala el operador con su chart y describe un `Cluster` mínimo en una plantilla condicional). Sea cual sea, la lección es la misma: **una dependencia de terceros es una decisión que hay que revisar**. Si la imagen se descarga sin problemas, documenta igualmente qué harías si mañana dejara de hacerlo.
16. Comprueba que `helm install ... -f values-prod.yaml` en un namespace `prod` **no** despliega PostgreSQL (la `condition` funciona) y que la API recibe la `DATABASE_URL` de un valor externo.

**Parte E — Ciclo de vida: upgrade, history, rollback (60 min)**

17. Con la release `api` en `dev`: `helm list -n dev`, `helm status api -n dev`, `helm get values api -n dev`, `helm get manifest api -n dev | head -50`. Explica la diferencia entre `get values` (lo que pasaste) y `get values --all` (lo efectivo).
18. Actualiza la imagen a tu segundo tag con `helm upgrade api charts/api -n dev -f charts/api/values-dev.yaml --set image.tag=1.1.0` y sigue el rollout con `kubectl rollout status`. Cambia un valor del ConfigMap y actualiza: comprueba que la anotación `checksum/config` fuerza el reinicio de los Pods. Ejecuta `helm history api -n dev`.
19. Rompe algo a propósito (un tag inexistente) con `helm upgrade ... --atomic --timeout 2m` y observa que Helm revierte solo. Repite sin `--atomic`, observa la release en estado `failed`/`pending` y usa `helm rollback api <revisión> -n dev`. Explica qué es una revisión, qué guarda Helm de cada una y por qué un rollback de Helm no revierte los datos de la base de datos.
20. `helm uninstall api -n dev --keep-history` y `helm history`: ¿qué queda? Reinstala. Explica también qué pasa con los PVC de la dependencia al desinstalar y por qué (los StatefulSets no borran sus PVC).

**Parte F — Versionado, empaquetado y publicación OCI (60-90 min)**

21. Sube `version` en `Chart.yaml` a `0.2.0` y `appVersion` a la versión de tu imagen. Escribe en `laboratorio-helm.md` la regla que vas a seguir: cuándo sube cada número del chart y por qué `version` y `appVersion` evolucionan por separado (un cambio de plantilla sin cambio de app, y al revés). Añade un `CHANGELOG.md` al chart.
22. `helm package charts/api` genera `api-0.2.0.tgz`. Inspecciónalo con `tar tzf`. Explica qué incluye y qué excluye `.helmignore`.
23. Publica en GHCR: `echo $GHCR_TOKEN | helm registry login ghcr.io -u <usuario> --password-stdin` y `helm push api-0.2.0.tgz oci://ghcr.io/<usuario>/charts`. En GitHub, localiza el paquete, hazlo público (o déjalo privado y anota cómo autenticarías el clúster) y enlázalo al repositorio. Comprueba desde otra máquina o desde el runner: `helm show chart oci://ghcr.io/<usuario>/charts/api --version 0.2.0` y `helm install api-oci oci://ghcr.io/<usuario>/charts/api --version 0.2.0 -n test --create-namespace -f charts/api/values-dev.yaml`. Explica qué tienen en común una imagen y un chart en un registro OCI.

**Parte G — helm test (30-45 min)**

24. En `templates/tests/test-health.yaml` define un Pod con la anotación `helm.sh/hook: test` que haga `wget -qO- http://<fullname>:<puerto>/health` y falle si no responde 200. Ejecuta `helm test api -n dev` y guarda la salida. Rompe el Service (cambia el puerto en un `--set`) y comprueba que el test falla. Explica para qué sirve `helm test` en un pipeline y qué **no** sustituye (pruebas de integración serias, monitorización).

**Parte H — Despliegue desde GitHub Actions con runner self-hosted (2-3 h)**

25. Registra un **runner self-hosted** en tu repositorio siguiendo la documentación de GitHub, en la máquina que tiene acceso al clúster (tu equipo o la VM `lab-so` si el clúster corre allí). Etiquétalo `lab-k8s`. Comprueba que aparece "Idle" en Settings → Actions → Runners. Lee la advertencia de GitHub sobre runners self-hosted en repositorios públicos y explícala con tus palabras: qué puede hacer un fork malicioso y por qué en tu caso el repo debería ser privado o el runner limitarse a ramas protegidas.
26. Amplía el pipeline del Módulo Intermedio con tres trabajos:
    - `chart-lint` (runner de GitHub, en cada PR): `helm lint` con los tres archivos de valores y `helm template` de dev y prod guardados como artefactos.
    - `chart-publish` (runner de GitHub, al crear un tag `chart-v*`): `helm package` y `helm push` a GHCR autenticándose con `GITHUB_TOKEN` (permiso `packages: write`).
    - `deploy-dev` (runner `lab-k8s`, al hacer push a `main` tras construir la imagen): `helm upgrade --install api oci://ghcr.io/<usuario>/charts/api --version <x> -n dev -f charts/api/values-dev.yaml --set image.tag=${{ github.sha }} --atomic --timeout 5m` seguido de `helm test api -n dev`. La contraseña de la base de datos viene de un secreto del repositorio vía `--set`, nunca del YAML.
27. Ejecuta el flujo completo: cambio en la app → imagen nueva → despliegue en `dev` → `helm history` muestra la revisión con el SHA. Provoca un fallo (por ejemplo, una probe rota en `values-dev.yaml`) y comprueba que `--atomic` revierte y el trabajo falla en rojo. Captura ambos casos.
28. Explica en el laboratorio qué ventajas y qué riesgos tiene que el pipeline despliegue directamente (push) frente a que el clúster tire de los cambios (pull, GitOps con Argo CD o Flux). No implementes GitOps ahora; lo verás más adelante.

**Parte I — Opcional y acotada: ACR y AKS (2-3 h, con coste)**

29. Con presupuesto y alerta activos: `az group create --name rg-helm-lab ...`, `az acr create --name <acrunico> --resource-group rg-helm-lab --sku Basic`, `az acr login --name <acrunico>` y `helm push api-0.2.0.tgz oci://<acrunico>.azurecr.io/helm`. Lista con `az acr repository list` y `az acr manifest list-metadata`. Compara con GHCR.
30. Crea el AKS mínimo del curso anterior (`--tier free --node-count 1 --node-vm-size Standard_B2s`) con `--attach-acr <acrunico>` para que el clúster pueda leer del registro sin secretos (identidad gestionada). Instala tu chart desde ACR con `values-prod.yaml` pero con `replicaCount: 1` y sin HPA, y observa el `LoadBalancer` con IP pública y la StorageClass de Azure Disk si activas PostgreSQL. Ejecuta `helm test`.
31. **Borra todo**: `az group delete --name rg-helm-lab --yes --no-wait`, comprueba que el grupo `MC_...` desaparece y captura el coste en Cost Management al día siguiente.

**Parte J — Limpieza (10 min)**

32. Desinstala las releases de prueba (`helm uninstall` en `test`, y `dev`/`prod` si no vas a seguir usándolas), elimina el runner si estaba en tu equipo personal o déjalo apagado, y conserva el chart en Git: lo reutilizarás en los cursos de DevSecOps y en el Proyecto Final.

### Resultado esperado

- `charts/api/` completo: `Chart.yaml` con dependencia condicional, `Chart.lock`, `values.yaml`, `values-dev.yaml`, `values-prod.yaml`, `values.schema.json` (opcional), `templates/` con `_helpers.tpl`, `NOTES.txt`, `tests/`, `README.md` y `CHANGELOG.md`.
- Chart publicado en `oci://ghcr.io/<usuario>/charts/api` con al menos una versión.
- Pipeline con los trabajos `chart-lint`, `chart-publish` y `deploy-dev` funcionando, con una ejecución verde y una roja capturadas.
- `laboratorio-helm.md` con las partes A-J, salidas de `helm template`, `lint`, `history`, `rollback`, `test`, y las decisiones sobre la dependencia de PostgreSQL.

### Criterios de validación

- [ ] Parte A: se explica qué es una release y dónde guarda Helm su estado; el análisis de Artifact Hub distingue publicadores y versiones.
- [ ] Parte B: `helm template` genera manifiestos equivalentes a los de `k8s/`; se usan las funciones pedidas y los helpers con labels estándar; el checksum del ConfigMap provoca rollout.
- [ ] Parte C: `helm lint` pasa con los tres archivos de valores; el `diff` dev/prod es el esperado; los tres errores provocados están documentados.
- [ ] Parte D: la dependencia se resuelve con `Chart.lock` en Git, se activa en dev y se desactiva en prod; el problema de la imagen de Bitnami (real o hipotético) está diagnosticado y la decisión justificada.
- [ ] Parte E: `history` muestra las revisiones; el rollback manual y el `--atomic` están capturados; se explica qué no revierte un rollback.
- [ ] Parte F: `version` y `appVersion` siguen SemVer con la regla escrita; el chart se instala desde `oci://ghcr.io/...`.
- [ ] Parte G: `helm test` pasa con la release sana y falla con el Service roto.
- [ ] Parte H: el pipeline despliega en `dev` desde el runner self-hosted con `--atomic` y `helm test`; hay una ejecución verde y una roja; la explicación de los riesgos del runner es correcta.
- [ ] Parte I (si se hace): el chart está en ACR, el AKS lo instaló con `--attach-acr` sin secretos y el grupo de recursos está borrado con captura de coste.
- [ ] El estudiante puede, en una llamada con el mentor, leer el `values.yaml` de un chart que no ha visto y explicar qué desplegaría con `helm template`.

## Entrega

En tu repositorio de entregas, carpeta `03-modulo-avanzado/02-helm/`:

1. `laboratorio-helm.md`.
2. Enlace al repositorio de la aplicación con `charts/api/` y el workflow, o copia de ambos (sin secretos: la contraseña de la base de datos no puede aparecer en ningún archivo de valores versionado).
3. Enlace al paquete publicado en GHCR (o captura si es privado).
4. `capturas/` de las ejecuciones del pipeline (verde y roja), `helm history` y `helm test`.
5. `ENTREGA.md` con evaluación, checklist y uso de IA.

Nota sobre IA: pídele que te explique un error de plantilla (`nil pointer evaluating`, `wrong type for value`) o que revise tu `_helpers.tpl`. No le pidas que convierta tus manifiestos: el ejercicio es precisamente ese, y la IA suele generar charts que no pasan `helm lint`.

## Evaluación

1. **Conceptual.** Explica con tus palabras chart, release, revisión y repositorio, y qué relación hay entre ellos. ¿Dónde guarda Helm el estado de una release y qué pasa si borras ese Secret?
2. **Técnica.** Un compañero tiene tres carpetas `k8s-dev/`, `k8s-test/`, `k8s-prod/` casi idénticas. Explícale qué gana convirtiéndolas en un chart con tres archivos de valores y qué riesgo nuevo aparece (un cambio de plantilla afecta a los tres entornos).
3. **Técnica.** Escribe el fragmento de plantilla que renderiza `resources` solo si está definido en los valores, con la indentación correcta, y explica la diferencia entre `indent` y `nindent`.
4. **Troubleshooting.** `helm template` falla con `nil pointer evaluating interface {}.tag`. ¿Qué significa, dónde está el error y cómo lo harías robusto con `default`?
5. **Situacional.** Cambias una clave del ConfigMap y haces `helm upgrade`, pero los Pods no se reinician y la app sigue con la configuración vieja. ¿Por qué ocurre y cómo lo resuelve la anotación de checksum?
6. **Conceptual.** ¿Qué diferencia hay entre `helm template`, `helm install --dry-run` y `helm lint`? ¿Cuál detecta un `apiVersion` que tu clúster no soporta?
7. **Técnica.** Explica `Chart.yaml` → `dependencies`, `Chart.lock` y `charts/*.tgz`: qué hace cada uno, cuál va en Git y qué comando regenera el resto. ¿Para qué sirve `condition`?
8. **Situacional.** El chart de un tercero que usas como dependencia cambia su modelo de distribución y la imagen por defecto deja de descargarse. Describe tres salidas posibles con sus ventajas y riesgos, y qué harías para detectarlo antes de que llegue a producción.
9. **Técnica.** Tienes `version: 1.4.2` y `appVersion: 2.0.0`. Cambias solo el `values.yaml` por defecto para añadir una anotación al Ingress. ¿Qué número subes y a cuánto? ¿Y si además la nueva imagen de la app es la 2.1.0? ¿Y si cambias el nombre de una clave de valores que rompe a quien la usaba?
10. **Troubleshooting.** `helm upgrade` termina en `UPGRADE FAILED: another operation (install/upgrade/rollback) is in progress`. ¿Qué ha pasado y qué dos formas hay de salir de ahí?
11. **Conceptual.** ¿Qué revierte y qué no revierte `helm rollback`? Pon un ejemplo con la base de datos del laboratorio. ¿Qué añade `--atomic`?
12. **Técnica.** Explica el flujo `helm registry login` → `helm package` → `helm push` → `helm install oci://...`. ¿Qué tiene en común con `docker push`? ¿Qué diferencia hay con un repositorio de charts clásico basado en `index.yaml`?
13. **Situacional.** Tu runner self-hosted está en tu portátil y el repositorio es público. Un desconocido abre un PR que modifica el workflow. ¿Qué puede pasar y qué tres medidas tomarías?
14. **Reflexión.** ¿Qué parte de tu chart te costó más parametrizar y por qué? ¿Qué valores dejaste fijos a propósito y con qué criterio?

## Checklist final

Antes de continuar, deberías poder:

- [ ] Explicar chart, release, revisión y repositorio, y dónde guarda Helm su estado.
- [ ] Inspeccionar un chart ajeno con `helm show` y `helm template` antes de instalarlo.
- [ ] Escribir plantillas con valores, funciones, condicionales, bucles y helpers con labels estándar.
- [ ] Mantener valores por entorno y validar con `helm lint` y `helm template`.
- [ ] Declarar, resolver y condicionar dependencias, y reaccionar cuando una dependencia de terceros cambia.
- [ ] Instalar, actualizar, consultar el historial y revertir releases, y explicar qué no revierte un rollback.
- [ ] Versionar chart y aplicación con SemVer, empaquetar y publicar en un registro OCI.
- [ ] Escribir y ejecutar `helm test`.
- [ ] Desplegar el chart desde GitHub Actions con un runner self-hosted y explicar sus riesgos.
- [ ] Tener el chart `api` en Git y publicado, listo para el Proyecto Final.

---

*Recursos verificados el 2026-09-27 mediante búsqueda web (existencia y vigencia de las URLs). Si un enlace falla, abre un issue en este repositorio.*
