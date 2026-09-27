# DevSecOps

> Módulo: Avanzado · Curso 11 de 12 · Duración estimada: 30-40 horas · Estado: ✅ Completo

## Objetivo

En el curso de Seguridad Cloud e IAM aprendiste a proteger lo que ya está desplegado: identidades, secretos, red, políticas. Este curso mueve la seguridad al principio: al repositorio, al pipeline y al artefacto. La idea de DevSecOps es sencilla de enunciar y difícil de hacer bien: **cada cambio pasa automáticamente por controles de seguridad antes de llegar a producción, y esos controles bloquean lo que es inaceptable sin convertir el pipeline en un muro que todo el mundo salta**.

Vas a trabajar sobre lo que ya tienes: el repositorio de la aplicación del curso de Docker (código Python, Dockerfile, manifiestos de Kubernetes o chart de Helm) y el repositorio de Terraform. Sobre ellos añadirás, uno a uno, los controles que hoy se consideran estándar: escaneo de secretos, análisis estático (SAST), análisis de dependencias, escaneo de imágenes de contenedor, escaneo de infraestructura como código, pruebas dinámicas básicas (DAST), inventario de componentes (SBOM), firma y verificación de artefactos (cadena de suministro), políticas como código y endurecimiento del propio pipeline. Al final introducirás a propósito cinco problemas típicos y demostrarás que el pipeline los detecta y los bloquea.

Casi todas las herramientas del curso son de código abierto y gratuitas (gitleaks, Semgrep, Bandit, pip-audit, Trivy, Grype, Syft, Checkov, Conftest, ZAP, Cosign, Scorecard). Las funciones nativas de GitHub (CodeQL, secret scanning, push protection, Dependabot) son gratuitas para repositorios **públicos**; para privados se explica la alternativa abierta. Azure DevOps se menciona donde cambia algo; la mecánica es la misma.

**Antes de empezar** necesitas el pipeline de GitHub Actions del curso de CI/CD funcionando (build de imagen, push a un registro, despliegue a un destino barato), el Terraform del curso de Terraform Avanzado, y la disciplina de Seguridad Cloud e IAM: nada de credenciales en código.

### Al terminar este curso deberías poder

- Explicar qué aporta cada tipo de control (secret scanning, SAST, dependency scanning, container scanning, IaC scanning, DAST, SBOM) y en qué fase del pipeline encaja cada uno.
- Configurar escaneo de secretos en tres capas: pre-commit local, CI y protección nativa de la plataforma (push protection).
- Integrar SAST (CodeQL o Semgrep y Bandit), análisis de dependencias (Dependabot, pip-audit, Trivy) y escaneo de imágenes (Trivy o Grype) en GitHub Actions con umbrales de severidad.
- Escanear Terraform y manifiestos de Kubernetes con Checkov o Trivy config y escribir políticas propias con OPA/Conftest.
- Ejecutar un DAST básico con OWASP ZAP contra la aplicación desplegada en staging e interpretar sus alertas.
- Generar un SBOM en CycloneDX o SPDX, publicarlo con el artefacto y explicar para qué sirve cuando aparece la próxima vulnerabilidad tipo Log4Shell.
- Firmar imágenes con Cosign en modo keyless y verificar la firma antes de desplegar; explicar SLSA, procedencia y la puntuación de OpenSSF Scorecard.
- Definir una política de gestión de vulnerabilidades (severidades, SLA de corrección, excepciones documentadas con caducidad) y traducirla a security gates en el pipeline.
- Endurecer el pipeline: permisos mínimos del `GITHUB_TOKEN`, acciones fijadas por SHA, environments con aprobación, OIDC hacia Azure sin secretos, protección de ramas y elección de runners.
- Demostrar con evidencias que el pipeline bloquea un secreto en código, una dependencia vulnerable, una imagen base antigua, un Storage público en Terraform y una acción sin fijar.

## Prerrequisitos

- Módulo Intermedio completo, en especial Docker, CI/CD, Terraform y Git y GitHub Intermedio (protección de ramas, PRs).
- Módulo Avanzado: Kubernetes Avanzado y Helm (manifiestos a escanear), Seguridad Cloud e IAM (Key Vault, identidades, Azure Policy), Terraform Avanzado (pipelines de Terraform).
- Repositorio público en GitHub para la aplicación (recomendado para tener CodeQL, secret scanning y Dependabot gratis) y repositorio de Terraform. Si tus repos son privados, el curso indica la alternativa en cada paso.
- Cuenta de Azure con presupuesto activo; destino de despliegue barato del curso de CI/CD (App Service F1/B1, Container Apps con consumo mínimo o la VM `lab-so`).

## Temario

Security in CI/CD · SAST · DAST · Dependency scanning · Container scanning · Secret scanning · SBOM · Supply chain security · Vulnerability management · Security gates · Policy as Code · Secure pipelines.

**Práctica:** incorporar controles automáticos de seguridad dentro de un pipeline.

## Recursos en español

### Seguridad en DevOps (Secure DevOps) — Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/devops/operate/security-in-devops
- **Autor / organización:** Microsoft
- **Idioma:** Español (cambia `es-es` por `en-us` para el original)
- **Tipo:** Documentación / guía conceptual
- **Duración aproximada:** 45 min
- **Cubre:** Security in CI/CD, shift-left, qué controles añadir en cada fase, cultura DevSecOps.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la visión de conjunto en pocas páginas y en español. Léelo el primer día para tener el mapa antes de meterte en herramientas concretas.

### Ruta AZ-400: Implementación de seguridad y validación de bases de código para el cumplimiento — Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/training/paths/az-400-implement-security-validate-code-bases-compliance/
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Ruta de aprendizaje
- **Duración aproximada:** 3-4 h
- **Cubre:** SAST, DAST, dependency scanning, secret scanning, gestión de vulnerabilidades, seguridad en pipelines de Azure DevOps y GitHub.
- **Nivel:** Intermedio-avanzado
- **Acceso:** Libre; cuenta Microsoft gratuita para guardar progreso
- **Por qué lo recomiendo:** Es el módulo de la certificación de DevOps de Microsoft dedicado a este tema. Explica los mismos controles del laboratorio con vocabulario de empresa y cubre el lado Azure DevOps que aquí solo mencionamos.

### Módulos de seguridad de GitHub: GitHub Advanced Security, code scanning y Dependabot — Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/training/modules/introduction-to-github-advanced-security/ · Code scanning: https://learn.microsoft.com/es-es/training/modules/configure-code-scanning/ · Dependabot: https://learn.microsoft.com/es-es/training/modules/configure-dependabot-security-updates-on-github-repo/
- **Autor / organización:** Microsoft y GitHub
- **Idioma:** Español
- **Tipo:** Módulos de aprendizaje con ejercicios
- **Duración aproximada:** 2-3 h
- **Cubre:** Secret scanning, SAST con CodeQL, dependency scanning con Dependabot, alertas y actualizaciones automáticas.
- **Nivel:** Intermedio
- **Acceso:** Libre; cuenta Microsoft y cuenta de GitHub gratuitas
- **Por qué lo recomiendo:** Cubren exactamente las funciones nativas que activarás en las Partes A, B y C, con capturas del portal de GitHub. Si tu repo es privado, sirven para entender qué te falta y qué sustituyes con herramientas abiertas.

## Recursos en inglés

### OWASP DevSecOps Guideline — OWASP
- **URL:** https://owasp.org/www-project-devsecops-guideline/ · Fuente en GitHub: https://github.com/OWASP/DevSecOpsGuideline
- **Autor / organización:** OWASP Foundation
- **Idioma:** Inglés
- **Tipo:** Guía abierta
- **Duración aproximada:** 3 h
- **Cubre:** Todo el temario: pre-commit, secret scanning, SAST, SCA, container scanning, IaC scanning, DAST, gobernanza, gestión de vulnerabilidades, panel central.
- **Nivel:** Intermedio-avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es el único documento que ordena todos los controles del curso en una sola tubería, independiente de proveedor. Su capítulo de gobernanza es la base de la política de vulnerabilidades de la Parte D.

### OWASP Top 10:2025, CI/CD Security Cheat Sheet y Top 10 CI/CD Security Risks — OWASP
- **URL:** https://owasp.org/Top10/2025/ · Cheat sheet CI/CD: https://cheatsheetseries.owasp.org/cheatsheets/CI_CD_Security_Cheat_Sheet.html · Cheat sheet GitHub Actions: https://cheatsheetseries.owasp.org/cheatsheets/GitHub_Actions_Security_Cheat_Sheet.html · Top 10 CI/CD Security Risks: https://owasp.org/www-project-top-10-ci-cd-security-risks/
- **Autor / organización:** OWASP Foundation
- **Idioma:** Inglés (el Top 10 tiene traducciones enlazadas desde la propia página)
- **Tipo:** Documentación de referencia
- **Duración aproximada:** 3 h
- **Cubre:** Riesgos de aplicación que buscan SAST y DAST; riesgos específicos del pipeline (flujo insuficiente, secretos, dependencias, integridad de artefactos, permisos excesivos).
- **Nivel:** Intermedio-avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** El Top 10 clásico te dice qué buscan los escáneres; el Top 10 de CI/CD te dice cómo atacan tu pipeline. La cheat sheet de GitHub Actions es una lista de comprobación directa para la Parte F.

### GitHub Docs: Code security y seguridad de GitHub Actions — GitHub
- **URL:** https://docs.github.com/en/code-security · Code scanning: https://docs.github.com/en/code-security/code-scanning · Secret scanning: https://docs.github.com/en/code-security/secret-scanning · Dependabot: https://docs.github.com/en/code-security/dependabot · Supply chain: https://docs.github.com/en/code-security/supply-chain-security · Uso seguro de Actions: https://docs.github.com/en/actions/reference/security/secure-use · OIDC en Azure: https://docs.github.com/en/actions/how-tos/secure-your-work/security-harden-deployments/oidc-in-azure
- **Autor / organización:** GitHub
- **Idioma:** Inglés (existe versión en español cambiando `/en/` por `/es/`, a veces con retraso)
- **Tipo:** Documentación oficial
- **Duración aproximada:** 4 h
- **Cubre:** Secret scanning y push protection, SAST con CodeQL, Dependabot, SBOM, attestations, permisos del `GITHUB_TOKEN`, fijado de acciones por SHA, `pull_request_target`, environments, OIDC.
- **Nivel:** Intermedio-avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** La página "Secure use reference" de Actions es de lectura obligatoria: cada recomendación que contiene se traduce en un paso de la Parte F. La de OIDC en Azure es la receta exacta para desplegar sin secretos.

### Trivy Documentation — Aqua Security
- **URL:** https://trivy.dev/docs/latest/ · Acción para GitHub: https://github.com/aquasecurity/trivy-action
- **Autor / organización:** Aqua Security (proyecto de código abierto)
- **Idioma:** Inglés
- **Tipo:** Documentación oficial
- **Duración aproximada:** 2 h
- **Cubre:** Container scanning, dependency scanning (`trivy fs`), IaC scanning (`trivy config`), secret scanning, SBOM, filtros de severidad, `.trivyignore`.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Una sola herramienta cubre cuatro controles del temario, lo que simplifica el pipeline. Aprende bien sus salidas (tabla, JSON, SARIF) porque son las que subirás a la pestaña Security de GitHub.

### Checkov Documentation y Conftest / Open Policy Agent — Prisma Cloud (Palo Alto) y OPA
- **URL:** https://www.checkov.io/ · Conftest: https://www.conftest.dev/ · Lenguaje Rego: https://www.openpolicyagent.org/docs/policy-language
- **Autor / organización:** Checkov es un proyecto abierto mantenido por Prisma Cloud; Conftest y OPA son proyectos de la CNCF
- **Idioma:** Inglés
- **Tipo:** Documentación oficial
- **Duración aproximada:** 3 h
- **Cubre:** IaC scanning con reglas predefinidas (Terraform, Kubernetes, Dockerfile), supresiones justificadas, Policy as Code con reglas propias en Rego.
- **Nivel:** Avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** Checkov te da cientos de comprobaciones listas; Conftest te obliga a escribir la regla que tu empresa necesita y nadie ha escrito. Necesitas las dos habilidades.

### Sigstore Cosign, SLSA y OpenSSF Scorecard — Sigstore, SLSA y OpenSSF (Linux Foundation)
- **URL:** Cosign (firma keyless): https://docs.sigstore.dev/cosign/signing/overview/ · Instalador para Actions: https://github.com/sigstore/cosign-installer · SLSA: https://slsa.dev/spec/v1.1/levels · Scorecard: https://scorecard.dev/ · Acción de Scorecard: https://github.com/ossf/scorecard-action
- **Autor / organización:** Proyectos de la OpenSSF y la Linux Foundation
- **Idioma:** Inglés
- **Tipo:** Documentación oficial y especificación
- **Duración aproximada:** 3 h
- **Cubre:** Supply chain security: firma y verificación de imágenes, identidad OIDC en la firma, niveles SLSA, procedencia de builds, puntuación de prácticas del repositorio.
- **Nivel:** Avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** La firma keyless con Cosign desde GitHub Actions es hoy la forma más práctica de garantizar que la imagen que despliegas es la que construyó tu pipeline. SLSA te da el marco para explicar a un auditor qué nivel has alcanzado y Scorecard te da una nota objetiva de tu repositorio.

### Secure Software Development Framework (SSDF), NIST SP 800-218 y Snyk Learn — NIST y Snyk
- **URL:** https://csrc.nist.gov/pubs/sp/800/218/final · Snyk Learn: https://learn.snyk.io/
- **Autor / organización:** NIST (gobierno de EE. UU.) y Snyk
- **Idioma:** Inglés
- **Tipo:** Marco normativo (PDF gratuito) y lecciones cortas interactivas
- **Duración aproximada:** 1,5 h del SSDF (secciones PW y RV) más 2-3 h de lecciones elegidas en Snyk Learn (secretos en código, dependencias vulnerables, seguridad de contenedores, seguridad de IaC)
- **Cubre:** Vulnerability management, prácticas del ciclo de vida seguro, ejemplos guiados de cada tipo de vulnerabilidad.
- **Nivel:** Intermedio-avanzado
- **Acceso:** SSDF libre; Snyk Learn gratuito con **cuenta gratuita** (no requiere tarjeta)
- **Por qué lo recomiendo:** El SSDF es lo que citan los contratos y las auditorías cuando piden "desarrollo seguro"; conviene saber mapear tus controles a sus prácticas. Snyk Learn es la mejor práctica guiada gratuita para entender por qué cada hallazgo importa; usa solo las lecciones, no necesitas su producto.

## Documentación oficial

- **Secret scanning:** gitleaks https://github.com/gitleaks/gitleaks (incluye configuración de pre-commit y acción de GitHub) · pre-commit: https://pre-commit.com/ · GitHub push protection: https://docs.github.com/en/code-security/secret-scanning/introduction/about-push-protection
- **SAST:** CodeQL https://docs.github.com/en/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning · Acción CodeQL: https://github.com/github/codeql-action · Semgrep: https://semgrep.dev/docs · Bandit: https://bandit.readthedocs.io/ · Subir SARIF a GitHub: https://docs.github.com/en/code-security/code-scanning/integrating-with-code-scanning/uploading-a-sarif-file-to-github
- **Dependencias:** Dependabot alerts https://docs.github.com/en/code-security/dependabot/dependabot-alerts/about-dependabot-alerts · Mantener acciones actualizadas con Dependabot: https://docs.github.com/en/code-security/dependabot/working-with-dependabot/keeping-your-actions-up-to-date-with-dependabot · pip-audit: https://github.com/pypa/pip-audit
- **Contenedores e IaC:** Trivy https://trivy.dev/docs/latest/ · Grype: https://github.com/anchore/grype · Checkov: https://www.checkov.io/ · hadolint (Dockerfile): https://github.com/hadolint/hadolint · Buenas prácticas de Dockerfile: https://docs.docker.com/build/building/best-practices/ · Pod Security Standards: https://kubernetes.io/docs/concepts/security/pod-security-standards/
- **DAST:** ZAP baseline scan https://www.zaproxy.org/docs/docker/baseline-scan/ · Acción: https://github.com/zaproxy/action-baseline
- **SBOM y supply chain:** Syft https://github.com/anchore/syft · Acción SBOM: https://github.com/anchore/sbom-action · CycloneDX: https://cyclonedx.org/ · SPDX: https://spdx.dev/ · Exportar SBOM desde GitHub: https://docs.github.com/en/code-security/supply-chain-security/understanding-your-software-supply-chain/exporting-a-software-bill-of-materials-for-your-repository · Attestations de GitHub: https://docs.github.com/en/actions/how-tos/secure-your-work/use-artifact-attestations/use-artifact-attestations · Cosign: https://docs.sigstore.dev/cosign/signing/overview/
- **Pipeline seguro:** permisos del `GITHUB_TOKEN` https://docs.github.com/en/actions/how-tos/write-workflows/choose-what-workflows-do/control-permissions-for-github_token · Environments: https://docs.github.com/en/actions/how-tos/deploy/configure-and-manage-deployments/manage-environments · Rulesets: https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets · OIDC en Azure desde GitHub: https://docs.github.com/en/actions/how-tos/secure-your-work/security-harden-deployments/oidc-in-azure · Lado Azure: https://learn.microsoft.com/en-us/azure/developer/github/connect-from-azure-openid-connect · Acción `azure/login`: https://github.com/Azure/login · zizmor (auditor de workflows): https://github.com/zizmorcore/zizmor
- **Azure:** Azure Policy https://learn.microsoft.com/es-es/azure/governance/policy/overview · Asignar política con CLI: https://learn.microsoft.com/en-us/azure/governance/policy/assign-policy-azurecli · Defender for Cloud, seguridad DevOps: https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-devops-introduction · Defender for Containers: https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-containers-introduction · GHAS para Azure DevOps: https://learn.microsoft.com/en-us/azure/devops/repos/security/github-advanced-security-code-scanning
- **Priorización de vulnerabilidades:** CVSS v4 https://www.first.org/cvss/v4.0/specification-document · EPSS: https://www.first.org/epss/ · Catálogo KEV de CISA: https://www.cisa.gov/known-exploited-vulnerabilities-catalog

## Ruta recomendada de estudio

1. **Leer** "Seguridad en DevOps" de Microsoft Learn y el índice de la OWASP DevSecOps Guideline (1,5 h). Dibuja tu pipeline actual y marca dónde encajaría cada control.
2. **Leer** el Top 10 CI/CD Security Risks y la cheat sheet de GitHub Actions (1,5 h). Audita a mano tu workflow actual contra la cheat sheet y anota los incumplimientos: serán la Parte F.
3. **Hacer** los tres módulos de GitHub en Microsoft Learn (2-3 h) y activar en tu repo secret scanning, push protection, Dependabot y CodeQL default setup (si es público).
4. **Leer** la documentación de gitleaks y pre-commit (45 min) y la "Secure use reference" de Actions (1 h).
5. **Hacer** la ruta AZ-400 de seguridad y cumplimiento (3-4 h). Anota las diferencias con Azure DevOps para tu tabla de equivalencias.
6. **Leer** Trivy (escaneo de imagen, fs, config, SBOM, severidades, ignore) y Checkov (Terraform, Kubernetes, supresiones) (3 h).
7. **Leer** Cosign keyless, niveles SLSA y Scorecard (2 h). Debes poder explicar qué demuestra una firma keyless y qué no.
8. **Leer** las secciones PW y RV del SSDF y hacer 3-4 lecciones de Snyk Learn (2-3 h). Redacta el borrador de la política de vulnerabilidades.
9. **Hacer el laboratorio** (16-22 h en varias sesiones; la Parte G se hace al final, con todo lo anterior activo).
10. **Responder la evaluación** y **revisar el checklist**.

## Laboratorio

### Objetivo

Convertir el pipeline de GitHub Actions de la aplicación del curso de Docker y el del repositorio de Terraform en pipelines con controles de seguridad automáticos: detección de secretos, SAST, dependencias, imagen, IaC, DAST, SBOM, firma y verificación, políticas como código y endurecimiento del propio pipeline, gobernados por una política de vulnerabilidades escrita por ti. Terminar demostrando, con cinco fallos introducidos a propósito, que el pipeline detecta y bloquea cada uno.

### Requisitos

- Repositorio `app` (aplicación del curso de Docker con `Dockerfile`, `requirements.txt`, tests, manifiestos K8s o chart de Helm y workflow de CI/CD) y repositorio `infra` (Terraform con backend remoto).
- Registro de contenedores: GitHub Container Registry (gratuito para repos públicos) o Azure Container Registry Basic (unos 5 USD/mes; bórralo al terminar si lo creas solo para esto).
- Destino de staging barato del curso de CI/CD para el DAST. Docker en tu equipo o en `lab-so` para probar herramientas en local antes de subirlas al pipeline.
- Documentación en `laboratorio-devsecops.md`.

> **Sobre el coste.** Todas las herramientas son gratuitas. GitHub Actions es gratuito en repos públicos y tiene 2.000 minutos/mes en privados: los escaneos añaden 5-10 minutos por ejecución, vigila el consumo. En Azure solo pagas el destino de staging que ya tenías (App Service F1 es gratis; B1 unos 13 USD/mes prorrateados) y, si lo creas, un ACR Basic. La asignación de Azure Policy no cuesta nada. Estimación total: **0-5 USD** si borras el staging y el ACR al terminar. Recuerda el contador de minutos de Actions en Settings → Billing.

### Instrucciones

Documenta cada control con: el fragmento del workflow, una ejecución **en verde** y una ejecución **en rojo** provocada por ti. Sin la ejecución en rojo no has demostrado que el control funciona.

**Parte A — Secret scanning en tres capas (2-3 h)**

1. Instala `pre-commit` y `gitleaks` en tu equipo. Crea `.pre-commit-config.yaml` con el hook de gitleaks en el repo `app` y en `infra`. Prueba: añade una línea `AZURE_STORAGE_KEY="<clave falsa con formato real>"` en un archivo, intenta `git commit` y captura el rechazo. Explica por qué el pre-commit es la capa más barata y por qué no basta (se puede saltar con `--no-verify`).
2. Añade un job `secrets` al workflow de CI con la acción de gitleaks escaneando **todo el historial** (`fetch-depth: 0`). Explica la diferencia entre encontrar un secreto en el commit actual y en el historial, y qué hay que hacer si aparece uno antiguo (rotar la credencial; reescribir el historial no lo "des-filtra").
3. Activa en GitHub secret scanning y **push protection** (Settings → Code security). Intenta hacer push de un token con formato reconocido (por ejemplo, un PAT de GitHub inventado con el prefijo correcto) y captura el bloqueo del servidor. Si tu repo es privado sin GitHub Advanced Security, documenta qué pierdes y cómo lo compensas con gitleaks.

**Parte B — SAST y dependencias (3-4 h)**

4. Activa **CodeQL** (default setup si el repo es público) y espera al primer análisis. Añade además un job con **Bandit** (`bandit -r app/ -f sarif -o bandit.sarif`) y sube el SARIF con `github/codeql-action/upload-sarif` para verlo en la pestaña Security. Opcional: **Semgrep** con el conjunto de reglas `p/python` en modo CI. Provoca un hallazgo real: añade `subprocess.run(cmd, shell=True)` con entrada de usuario o un `eval()` y comprueba que aparece; luego corrígelo.
5. Configura **Dependabot** (`.github/dependabot.yml`) para `pip`, `docker` y `github-actions`, con agrupación de actualizaciones menores. Activa Dependabot alerts y security updates. Añade en CI `pip-audit -r requirements.txt --strict` y `trivy fs --scanners vuln,misconfig,secret --severity HIGH,CRITICAL --exit-code 1 .`. Provoca fallo fijando una versión antigua de una dependencia con CVE conocida (por ejemplo, una versión de `requests` o `urllib3` de hace años) y captura el rojo; después actualiza y captura el verde.

**Parte C — Imagen, IaC y DAST (4-5 h)**

6. Tras el `docker build`, añade `trivy image --severity HIGH,CRITICAL --exit-code 1 --ignore-unfixed <imagen>` y, como comparación, `grype <imagen> --fail-on high`. Compara el número de hallazgos de ambos y explica por qué difieren (bases de datos distintas, detección de paquetes). Cambia la imagen base a una etiqueta antigua (por ejemplo `python:3.9-slim` de una fecha concreta o `python:3.8`) y captura el bloqueo. Vuelve a una base actual y mínima y añade `hadolint` sobre el Dockerfile.
7. En el repo `infra` añade `checkov -d . --framework terraform --soft-fail-on LOW,MEDIUM` y `trivy config .` En el repo `app`, `checkov -d k8s/` (o sobre el `helm template` renderizado). Corrige los hallazgos razonables (sin `runAsNonRoot`, sin límites de recursos, imagen con `latest`) y suprime con comentario justificado (`# checkov:skip=CKV_...: motivo`) los que no apliquen. Cuenta cuántos hallazgos había al principio y cuántos quedan.
8. **DAST:** despliega la aplicación en staging y añade un job `dast` con la acción ZAP baseline apuntando a la URL de staging, con `fail_action: true` para alertas de nivel medio o superior y un archivo de reglas para ignorar las que no apliquen. Interpreta el informe: qué alertas son cabeceras HTTP ausentes (fáciles de corregir en la app o en el proxy), cuáles son falsos positivos y cuáles requieren cambios de código. Corrige al menos dos cabeceras y vuelve a ejecutar.

**Parte D — SBOM, firma y política de vulnerabilidades (4-5 h)**

9. Genera un **SBOM** de la imagen con Syft en CycloneDX (`syft <imagen> -o cyclonedx-json > sbom.cdx.json`) y en SPDX; súbelo como artifact del workflow y adjúntalo a la release cuando etiquetes una versión. Abre el JSON y localiza tres componentes con su versión y licencia. Explica cómo usarías el SBOM el día que se publique una vulnerabilidad crítica en una librería transitiva. Ejecuta `grype sbom:./sbom.cdx.json` para ver que se puede escanear el SBOM sin la imagen.
10. **Firma keyless con Cosign:** en el job de build, con `permissions: id-token: write` y `packages: write`, instala Cosign y firma por digest (`cosign sign --yes <registro>/<imagen>@<digest>`). En el job de despliegue, **verifica antes de desplegar** con `cosign verify --certificate-identity-regexp "https://github.com/<usuario>/<repo>/.github/workflows/.*" --certificate-oidc-issuer https://token.actions.githubusercontent.com <imagen>@<digest>`. Prueba a verificar una imagen que no firmó tu pipeline y captura el fallo. Explica qué garantiza la firma (quién construyó qué) y qué no (que el código sea seguro).
11. Añade la acción de **OpenSSF Scorecard** al repo público y anota tu puntuación inicial y las comprobaciones que fallan (Pinned-Dependencies, Token-Permissions, Branch-Protection suelen aparecer). Explica en un párrafo qué nivel **SLSA** alcanza tu build hoy y qué te faltaría para el siguiente nivel (procedencia firmada, build aislado). Opcional: genera procedencia con `actions/attest-build-provenance`.
12. Escribe `SECURITY-POLICY.md` con la **política de gestión de vulnerabilidades** (plantilla al final): clasificación de severidad (CVSS más contexto: explotabilidad EPSS, presencia en KEV, exposición a Internet), SLA de corrección por severidad, proceso de excepción con responsable, motivo y fecha de caducidad, y qué gates bloquean el pipeline. Traduce la política a los umbrales de Trivy, pip-audit, Checkov y ZAP, y a un `.trivyignore` con cada excepción comentada y con fecha.

**Parte E — Policy as Code (3 h)**

13. Escribe con **Conftest** al menos cuatro políticas Rego propias: el Dockerfile no puede usar `latest` ni ejecutar como root; los manifiestos de Kubernetes deben tener `resources.limits`, `readinessProbe` y no montar el socket de Docker; los workflows de Actions deben declarar `permissions` a nivel de job. Añade `conftest test` al CI con sus pruebas unitarias (`conftest verify`). Provoca un fallo de cada regla.
14. **Azure Policy en el despliegue:** asigna al grupo de recursos de staging la política integrada que impide cuentas de Storage con acceso público a blobs (efecto `Deny`) y la que exige transferencia segura. Modifica el Terraform para crear un Storage con `allow_nested_items_to_be_public = true` y ejecuta `terraform apply`: captura el rechazo de Azure Resource Manager por política. Explica la diferencia entre bloquear en el pipeline (Checkov) y bloquear en la plataforma (Azure Policy) y por qué necesitas ambos.

**Parte F — Pipeline seguro (3-4 h)**

15. Endurece el workflow siguiendo la referencia de uso seguro de Actions y la cheat sheet de OWASP: `permissions: {contents: read}` a nivel de workflow y permisos explícitos por job; todas las acciones fijadas por **SHA completo** con comentario de versión (usa Dependabot para mantenerlas); sin `pull_request_target` salvo justificación; secretos solo en `environments` con **required reviewers** para producción; sin `echo` de secretos ni `set-output` inseguro; `concurrency` para evitar despliegues solapados. Pasa `zizmor` sobre los workflows y corrige lo que señale.
16. Sustituye cualquier secreto de Azure del pipeline (client secret, publish profile) por **OIDC**: crea una identidad (app registration o managed identity de usuario) con credencial federada para `repo:<usuario>/<repo>:environment:staging`, asígnale solo el rol necesario sobre el grupo de staging y usa `azure/login` con `client-id`, `tenant-id` y `subscription-id` (que no son secretos). Borra el secreto antiguo y captura que el despliegue sigue funcionando. Explica qué gana esto frente a un secreto de larga duración.
17. Configura un **ruleset** en la rama principal: PR obligatoria con una revisión, checks requeridos (secrets, sast, deps, image, iac, conftest), sin force push, firmas de commit opcionales. Documenta la decisión sobre runners: hospedados por GitHub frente a self-hosted en tu VM (riesgo de ejecutar código de PRs de terceros en un runner propio). Añade a tu tabla de equivalencias cómo se hace cada cosa en Azure DevOps (service connections con workload identity federation, branch policies, environments con aprobaciones, GHAS para Azure DevOps).

**Parte G — Ejercicio final: cinco fallos a propósito (3-4 h)**

18. En una rama `demo-fallos`, introduce **los cinco problemas** en commits separados: (1) una clave con formato real en un archivo de configuración, (2) una dependencia con CVE crítica en `requirements.txt`, (3) una imagen base antigua en el Dockerfile, (4) un Storage con acceso público en Terraform, (5) una acción de terceros referenciada por etiqueta mutable (`@v3`) sin SHA. Abre una PR hacia la rama principal.
19. Para cada problema captura: qué control lo detectó (pre-commit, push protection, job de CI, Conftest, Checkov, Azure Policy), en qué fase, el mensaje de error y si el merge quedó **bloqueado** por el ruleset. Si algún fallo pasó, arréglalo y explica qué control faltaba. Corrige los cinco en la misma rama y muestra la PR en verde.
20. Cierra con una **tabla resumen del pipeline**: fase, control, herramienta, umbral, qué bloquea, tiempo que añade, coste. Y una reflexión de diez líneas: qué controles quitarías en un equipo de tres personas y cuáles no negociarías nunca.

### Plantilla: política de gestión de vulnerabilidades (`SECURITY-POLICY.md`)

```markdown
# Política de gestión de vulnerabilidades: <repositorio / servicio>
## 1. Alcance (código, dependencias, imágenes, IaC, pipeline, staging)
## 2. Clasificación
| Severidad | Criterio (CVSS base, EPSS, KEV, exposición, datos afectados) | Ejemplo |
|---|---|---|
## 3. SLA de corrección
| Severidad | Bloquea pipeline | Plazo máximo de corrección | Quién decide excepción |
|---|---|---|---|
| CRITICAL | Sí | 7 días | Responsable de seguridad |
## 4. Excepciones
| ID | Hallazgo (CVE/regla) | Motivo | Mitigación compensatoria | Aprobado por | Caduca el | Dónde está el ignore |
|---|---|---|---|---|---|---|
## 5. Security gates por fase (herramienta, umbral, comportamiento al fallar)
## 6. Revisión de la política (frecuencia, responsable, histórico de cambios)
```

### Resultado esperado

- Dos repositorios con pipelines endurecidos y todos los controles activos, cada uno con evidencia en verde y en rojo.
- `laboratorio-devsecops.md`, `SECURITY-POLICY.md`, políticas Rego con sus pruebas, `.trivyignore` y supresiones de Checkov justificadas, `dependabot.yml`, SBOM adjunto a una release, imagen firmada y verificada en el despliegue.
- PR `demo-fallos` con los cinco problemas detectados y bloqueados, y después corregidos.
- Tabla de equivalencias GitHub Actions / Azure DevOps y tabla resumen del pipeline.

### Criterios de validación

- [ ] Cada control tiene una ejecución en rojo provocada y una en verde; el estudiante explica qué detecta y qué no detecta cada herramienta.
- [ ] El secreto de prueba fue bloqueado en pre-commit, en CI y por push protection (o se documenta la alternativa en repos privados).
- [ ] Los hallazgos de SAST, dependencias, imagen e IaC aparecen en la pestaña Security (SARIF) o en los logs, y las supresiones tienen motivo y fecha.
- [ ] El SBOM está adjunto a una release y el estudiante localiza componentes concretos en él; la imagen se firma por digest y el despliegue falla si la firma no verifica.
- [ ] Las políticas Rego tienen pruebas y bloquean lo que dicen bloquear; Azure Policy rechaza el Storage público aunque Checkov se hubiera saltado.
- [ ] El workflow tiene permisos mínimos, acciones fijadas por SHA, environments con aprobación y despliegue por OIDC sin secretos de Azure; `zizmor` no reporta hallazgos altos.
- [ ] Los cinco fallos de la Parte G fueron detectados y el merge quedó bloqueado; la evidencia indica fase, control y mensaje.
- [ ] La política de vulnerabilidades es coherente con los umbrales configurados y contiene al menos una excepción real con caducidad.
- [ ] En conversación con el mentor, el estudiante puede justificar qué controles son imprescindibles en un equipo pequeño y por qué.

## Entrega

En tu repositorio de entregas, carpeta `03-modulo-avanzado/11-devsecops/`:

1. `laboratorio-devsecops.md` y carpeta `capturas/` (ejecuciones en rojo y en verde, bloqueo de push protection, PR bloqueada, rechazo de Azure Policy; oculta cualquier valor que parezca un secreto aunque sea falso).
2. Enlaces a los repositorios `app` e `infra` con los workflows, `SECURITY-POLICY.md`, políticas Rego y pruebas, `.trivyignore`, `dependabot.yml`, `.pre-commit-config.yaml`.
3. `sbom.cdx.json` de la release final y la salida de `cosign verify`.
4. Tablas de equivalencias y de resumen del pipeline.
5. `ENTREGA.md` con evaluación, checklist y uso de IA.

Nota sobre IA: pedirle que te explique un hallazgo de CodeQL o una regla Rego es buen uso. Copiar una excepción de vulnerabilidad sugerida por una IA sin entender el riesgo es exactamente lo que este curso intenta evitar; cada excepción la firmas tú.

## Evaluación

1. **Conceptual.** Explica la diferencia entre SAST, DAST y análisis de dependencias con un ejemplo de vulnerabilidad que solo detectaría cada uno.
2. **Situacional.** Un desarrollador hizo push de una clave de Storage real hace tres semanas y acaba de borrarla en un commit nuevo. Enumera los pasos en orden de prioridad y explica por qué reescribir el historial no es el primero.
3. **Técnica.** Trivy marca 40 vulnerabilidades HIGH en tu imagen, 35 de ellas sin parche disponible (`--ignore-unfixed`). ¿Bloqueas el pipeline? Justifica tu decisión con la política de vulnerabilidades y explica qué harías con las 5 restantes.
4. **Conceptual.** ¿Qué demuestra una firma keyless de Cosign hecha desde GitHub Actions y qué no demuestra? ¿Qué añade la procedencia SLSA sobre la firma?
5. **Troubleshooting.** El job de despliegue falla en `cosign verify` con un error de identidad del certificado después de renombrar el repositorio. ¿Qué ha pasado y cómo lo arreglas sin bajar el nivel de seguridad?
6. **Situacional.** El equipo se queja de que el pipeline tarda 15 minutos más y falla por hallazgos MEDIUM en librerías transitivas. Propón tres cambios que reduzcan la fricción sin eliminar controles.
7. **Técnica.** Explica qué riesgo mitiga fijar acciones por SHA frente a por etiqueta, qué riesgo introduce (mantenimiento) y cómo lo resuelves con Dependabot.
8. **Conceptual.** ¿Por qué el `GITHUB_TOKEN` con permisos por defecto es un problema y qué combinación de `permissions` necesita un job que solo construye y escanea una imagen? ¿Y uno que firma con Cosign keyless?
9. **Situacional.** Auditoría pregunta "¿qué componentes con licencia GPL hay en producción y qué versión de `openssl` lleva cada imagen?". Explica cómo respondes en una hora usando lo construido en el curso.
10. **Técnica.** Checkov aprobó el Terraform pero Azure Policy rechazó el despliegue. Da dos causas plausibles y explica por qué la defensa en profundidad (pipeline más plataforma) es necesaria.
11. **Conceptual.** Diferencia entre Dependabot alerts, Dependabot security updates y Dependabot version updates. ¿Cuál activarías en un repo de Terraform y para qué ecosistema?
12. **Troubleshooting.** ZAP baseline reporta "Content Security Policy Header Not Set" y "Cookie without SameSite" en tu API. ¿Cuál aplica realmente a una API JSON sin sesiones? ¿Cómo lo documentas en el archivo de reglas sin ocultar hallazgos válidos?
13. **Situacional.** Te piden replicar el pipeline en Azure DevOps. Indica el equivalente de: environments con aprobación, OIDC con `azure/login`, rulesets, CodeQL y Dependabot.
14. **Reflexión.** De los cinco fallos que introdujiste, ¿cuál fue el más difícil de detectar y por qué? ¿Qué control añadirías al Proyecto Final que no estaba en este curso?

## Checklist final

Antes de continuar, deberías poder:

- [ ] Situar cada control (secretos, SAST, dependencias, imagen, IaC, DAST, SBOM, firma) en la fase correcta del pipeline y explicar qué detecta.
- [ ] Configurar gitleaks en pre-commit y en CI y activar push protection.
- [ ] Integrar CodeQL o Semgrep y Bandit, pip-audit y Trivy con umbrales y subir resultados SARIF.
- [ ] Escanear imágenes con Trivy o Grype y explicar por qué difieren sus resultados.
- [ ] Escanear Terraform y Kubernetes con Checkov o Trivy config y suprimir hallazgos con justificación.
- [ ] Ejecutar ZAP baseline contra staging e interpretar sus alertas.
- [ ] Generar y publicar un SBOM y usarlo para responder a una vulnerabilidad nueva.
- [ ] Firmar imágenes con Cosign keyless y verificar la firma antes de desplegar; explicar SLSA y Scorecard.
- [ ] Escribir una política de vulnerabilidades con SLA y excepciones con caducidad, y traducirla a security gates.
- [ ] Escribir y probar políticas Rego con Conftest y asignar una Azure Policy con efecto Deny.
- [ ] Endurecer un workflow: permisos mínimos, SHA pinning, environments, OIDC, rulesets.
- [ ] Demostrar con evidencias que el pipeline bloquea los cinco fallos clásicos.

---

*Recursos verificados el 2026-09-27 mediante búsqueda web (existencia y vigencia de las URLs). Si un enlace falla, abre un issue en este repositorio.*
