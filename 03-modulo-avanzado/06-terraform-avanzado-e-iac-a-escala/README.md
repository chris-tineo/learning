# Terraform Avanzado e IaC a Escala

> Módulo: Avanzado · Curso 6 de 12 · Duración estimada: 35-45 horas · Estado: ✅ Completo

## Objetivo

En el curso de Terraform del Módulo Intermedio escribiste un proyecto que desplegaba unos cuantos recursos en Azure con un backend remoto. Funcionaba, pero era un solo directorio, un solo estado, un solo entorno y una sola persona (tú) ejecutando `apply` desde su portátil. Así no se opera una plataforma. En una empresa hay decenas de equipos, tres o cuatro entornos, cientos de stacks, y nadie debería ejecutar `apply` a mano contra producción.

Este curso te enseña a pasar de "un proyecto Terraform" a "una plataforma de infraestructura como código": módulos reutilizables con contrato claro, versionados, documentados y probados; un repositorio de entornos que compone esos módulos sin duplicar código; un estado por entorno con bloqueo; pipelines que formatean, validan, analizan, planifican en el Pull Request y aplican con aprobación; gobernanza con nombres, etiquetas y políticas; dependencias explícitas entre stacks; y detección de deriva programada. Aprenderás también a tomar las decisiones que dividen a los equipos (workspaces frente a directorios, monorepo frente a multirepo, cuánto abstraer un módulo) con criterio y no por moda.

Nada de esto requiere recursos caros: las VNets, subredes, NSGs, tablas de rutas, workspaces de Log Analytics y cuentas de almacenamiento pequeñas cuestan céntimos o nada. Lo que se practica aquí es la ingeniería alrededor del código.

**Antes de empezar** necesitas el curso de Terraform del Módulo Intermedio, CI/CD con GitHub Actions, y la federación OIDC del curso de Seguridad Cloud e IAM (el pipeline no usará secretos).

### Al terminar este curso deberías poder

- Diseñar un módulo Terraform con un contrato claro (variables validadas, salidas, versiones), estructura estándar, ejemplos y documentación generada con `terraform-docs`.
- Escribir pruebas con `terraform test` (con `command = plan`, con proveedores simulados y con `apply` real acotado) y explicar qué aporta Terratest.
- Componer módulos en un repositorio de entornos con estructura dev/stage/prod, sin duplicar lógica, con estado remoto y bloqueo por entorno en Azure Storage autenticado por identidad.
- Argumentar cuándo usar `terraform workspaces` y cuándo directorios por entorno, y qué problemas trae cada opción.
- Usar `for_each`, `dynamic`, `moved`, `import`, `precondition`/`postcondition` y `check` para refactorizar e importar sin destruir recursos.
- Fijar versiones de Terraform, proveedores y módulos con restricciones y archivo de bloqueo, y actualizarlas de forma controlada.
- Construir un pipeline de GitHub Actions con `fmt`, `validate`, `tflint`, `checkov`, `plan` comentado en el PR y `apply` con aprobación en un entorno protegido.
- Implantar gobernanza: convenciones de nombres, etiquetas obligatorias validadas en código y Azure Policy como red de seguridad.
- Gestionar dependencias entre stacks (outputs vía estado remoto y vía data sources) y detectar deriva con un pipeline programado.
- Explicar cómo se traslada todo esto a AWS y GCP y qué cambia con Azure Verified Modules o Terragrunt.

## Prerrequisitos

- Módulo Intermedio: Terraform (azurerm, backend remoto en Azure Storage, módulos básicos), CI/CD (GitHub Actions, entornos), Git y GitHub Intermedio (PRs, protección de ramas, tags y releases), Bash y Python.
- Módulo Avanzado, curso 5: Seguridad Cloud e IAM (Service Principal con OIDC, RBAC, Azure Policy).
- Terraform 1.9 o superior, Azure CLI, `terraform-docs`, `tflint` y `checkov` instalados en tu equipo.

## Temario

- Diseño de módulos.
- Module composition.
- Remote State.
- State locking.
- Multiple environments.
- Repository structures.
- Pipelines para Terraform.
- Validation.
- Linting.
- Testing.
- Versioning.
- Providers a escala.
- Dependency management.
- Governance.

**Práctica:** crear una plataforma modular reutilizable para varios ambientes.

## Recursos en español

### Documentación de Terraform en Azure: autenticación (es-es) — Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/azure/developer/terraform/authenticate-to-azure · Índice de la documentación de Terraform en Azure (inglés): https://learn.microsoft.com/en-us/azure/developer/terraform/
- **Autor / organización:** Microsoft
- **Idioma:** Español (la página de autenticación) e inglés (el índice)
- **Tipo:** Documentación oficial
- **Duración aproximada:** 90 min para autenticación (OIDC, Managed Identity, Service Principal), el artículo de almacenar el estado en Azure Storage y el de pruebas y buenas prácticas del índice
- **Cubre:** Remote State, State locking, Pipelines, Providers a escala
- **Nivel:** Intermedio-avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la referencia oficial de Microsoft para el backend `azurerm` (bloqueo por concesión de blob, autenticación con Entra ID en vez de clave de cuenta) y para autenticar Terraform sin secretos en pipelines. Léelo antes de diseñar los backends por entorno.

### Terraform Best Practices (traducción al español) — Anton Babenko y colaboradores
- **URL:** https://www.terraform-best-practices.com/ (selecciona "Español" en el menú de idiomas; repositorio con todas las traducciones: https://github.com/antonbabenko/terraform-best-practices)
- **Autor / organización:** Anton Babenko (mantenedor de los módulos Terraform de AWS más usados) y traductores voluntarios
- **Idioma:** Español (traducción de la comunidad; el original es inglés)
- **Tipo:** Libro electrónico gratuito
- **Duración aproximada:** 2-3 h
- **Cubre:** Diseño de módulos, estructura de repositorios, composición, nombres, ejemplos
- **Nivel:** Intermedio-avanzado
- **Acceso:** Libre (licencia Apache 2)
- **Por qué lo recomiendo:** Es el texto más citado sobre estructura de código Terraform: módulos de recurso frente a módulos de infraestructura frente a composición, cuándo un módulo es demasiado pequeño o demasiado grande, y ejemplos de estructuras pequeñas, medianas y grandes. Está centrado en AWS, pero todo aplica a Azure: traduce mentalmente `aws_vpc` por `azurerm_virtual_network`.

## Recursos en inglés

### Terraform documentation: modules, tests, style guide — HashiCorp Developer
- **URL:** Crear módulos: https://developer.hashicorp.com/terraform/language/modules/develop · Estructura estándar: https://developer.hashicorp.com/terraform/language/modules/develop/structure · Publicar y versionar: https://developer.hashicorp.com/terraform/language/modules/develop/publish · Tests: https://developer.hashicorp.com/terraform/language/tests · Mocks: https://developer.hashicorp.com/terraform/language/tests/mocking · Comando `terraform test`: https://developer.hashicorp.com/terraform/cli/commands/test · Guía de estilo: https://developer.hashicorp.com/terraform/language/style · Índice del lenguaje: https://developer.hashicorp.com/terraform/docs
- **Autor / organización:** HashiCorp
- **Idioma:** Inglés
- **Tipo:** Documentación oficial
- **Duración aproximada:** 5-6 h para las páginas indicadas más, desde el índice, las de `backend` `azurerm`, `workspaces`, `moved`, `import`, `validation`, `precondition`/`postcondition`, `check`, restricciones de versión y archivo de bloqueo de dependencias
- **Cubre:** Todo el temario salvo pipelines y gobernanza
- **Nivel:** Avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la fuente de verdad y el recurso principal del curso. La guía de estilo es corta y te da las convenciones que seguirás en los módulos; la página de tests y la de mocks explican el marco de pruebas nativo que sustituye a gran parte de lo que antes exigía Terratest.

### Write Terraform tests (tutorial) — HashiCorp Developer
- **URL:** https://developer.hashicorp.com/terraform/tutorials/configuration-language/test
- **Autor / organización:** HashiCorp
- **Idioma:** Inglés
- **Tipo:** Tutorial guiado
- **Duración aproximada:** 60-90 min
- **Cubre:** Testing, Validation
- **Nivel:** Avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la forma más rápida de escribir tu primer `.tftest.hcl` correcto: `run` con `plan` y con `apply`, `assert`, variables por prueba y proveedores auxiliares. Hazlo con AWS o con Azure según el ejemplo; lo importante es el patrón.

### How to manage multiple environments with Terraform (serie) — Gruntwork
- **URL:** https://www.gruntwork.io/blog/how-to-manage-multiple-environments-with-terraform (artículo introductorio; enlaza a las tres partes: workspaces, ramas, Terragrunt)
- **Autor / organización:** Yevgeniy Brikman (Gruntwork, autor de "Terraform: Up & Running")
- **Idioma:** Inglés
- **Tipo:** Serie de artículos
- **Duración aproximada:** 90 min
- **Cubre:** Multiple environments, Repository structures, Module composition
- **Nivel:** Avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es el análisis más claro de los tres enfoques para gestionar entornos, con sus costes de aislamiento, versionado y duplicación. Te da el criterio que la evaluación te pedirá defender. Terragrunt es una herramienta de la propia Gruntwork: lee la tercera parte con ese sesgo en mente y decide tú.

### Azure Verified Modules (Terraform) — Microsoft
- **URL:** https://azure.github.io/Azure-Verified-Modules/ · Inicio rápido Terraform: https://azure.github.io/Azure-Verified-Modules/usage/quickstart/terraform/ · Índice de módulos Terraform: https://azure.github.io/Azure-Verified-Modules/indexes/terraform/ · Especificaciones que deben cumplir: https://azure.github.io/Azure-Verified-Modules/specs/tf/
- **Autor / organización:** Microsoft
- **Idioma:** Inglés
- **Tipo:** Catálogo de módulos y especificación
- **Duración aproximada:** 90 min para el inicio rápido, la especificación y leer el código de un módulo de recurso (por ejemplo, el de VNet)
- **Cubre:** Diseño de módulos, Versioning, Testing, Governance
- **Nivel:** Avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** Son los módulos oficiales de Microsoft para Azure y, sobre todo, su **especificación** es una lista concreta de lo que hace a un módulo "de calidad de producción" (interfaces comunes, tests, ejemplos, versionado semántico, documentación). En el laboratorio compararás tus módulos con ella y decidirás cuándo escribir el tuyo y cuándo consumir uno de AVM.

### terraform-docs, TFLint (ruleset azurerm) y Checkov — documentación de herramientas
- **URL:** terraform-docs: https://terraform-docs.io/user-guide/ (repositorio: https://github.com/terraform-docs/terraform-docs) · TFLint ruleset para azurerm: https://github.com/terraform-linters/tflint-ruleset-azurerm (el repositorio principal de TFLint se enlaza desde su README) · Checkov: https://www.checkov.io/ · Inicio rápido: https://www.checkov.io/1.Welcome/Quick%20Start.html · Análisis de Terraform: https://www.checkov.io/7.Scan%20Examples/Terraform.html · Análisis del plan: https://www.checkov.io/7.Scan%20Examples/Terraform%20Plan%20Scanning.html
- **Autor / organización:** Proyectos de código abierto terraform-docs y TFLint; Checkov (Prisma Cloud / Palo Alto Networks, código abierto)
- **Idioma:** Inglés
- **Tipo:** Documentación de herramientas
- **Duración aproximada:** 2 h para instalar las tres, configurarlas (`.terraform-docs.yml`, `.tflint.hcl`, `.checkov.yml`) y entender su salida
- **Cubre:** Validation, Linting, Governance, Pipelines
- **Nivel:** Intermedio
- **Acceso:** Libre (las tres son de código abierto; Checkov tiene una plataforma de pago que no necesitas)
- **Por qué lo recomiendo:** Son las tres herramientas que casi todos los pipelines de Terraform ejecutan antes del `plan`. `terraform-docs` genera el README de cada módulo a partir del código, TFLint detecta errores que `validate` no ve (tamaños de VM inexistentes, SKUs inválidos) y Checkov aplica cientos de comprobaciones de seguridad y cumplimiento sobre el código y sobre el plan.

## Documentación oficial

- **Terraform (índice):** https://developer.hashicorp.com/terraform/docs · Módulos: https://developer.hashicorp.com/terraform/language/modules · Tests: https://developer.hashicorp.com/terraform/language/tests · Estilo: https://developer.hashicorp.com/terraform/language/style
- **Terraform en Azure (Microsoft Learn):** índice en inglés https://learn.microsoft.com/en-us/azure/developer/terraform/ · Autenticación (es-es): https://learn.microsoft.com/es-es/azure/developer/terraform/authenticate-to-azure · Inicio rápido con el proveedor AzAPI (es-es): https://learn.microsoft.com/es-es/azure/developer/terraform/get-started-azapi-resource
- **Azure Verified Modules:** https://azure.github.io/Azure-Verified-Modules/ · Repositorio: https://github.com/Azure/terraform-azure-modules
- **Terraform Registry:** documentación del proveedor `azurerm` (ya la usas) y búsqueda de módulos AVM (`Azure/avm-res-*`).
- **terraform-docs:** https://terraform-docs.io/user-guide/ · Configuración: https://terraform-docs.io/user-guide/configuration/settings/
- **TFLint ruleset azurerm:** https://github.com/terraform-linters/tflint-ruleset-azurerm
- **Checkov:** https://www.checkov.io/ · Detección de credenciales en código: https://www.checkov.io/2.Basics/Scanning%20Credentials%20and%20Secrets.html
- **GitHub Actions:** la documentación de docs.github.com sobre entornos con revisores obligatorios, `permissions` del token, eventos `pull_request` y `schedule`, y la acción `hashicorp/setup-terraform` en el GitHub Marketplace (todo ya visto en CI/CD y Seguridad).

## Ruta recomendada de estudio

1. **Leer** la guía de estilo de Terraform y la estructura estándar de módulos (60 min). Anota las convenciones que aplicarás (nombres, orden de bloques, `variables.tf`/`outputs.tf`, descripciones obligatorias).
2. **Leer** "Crear módulos" y "Publicar y versionar" de HashiCorp y el libro Terraform Best Practices en español (3 h). Al terminar debes saber distinguir módulo de recurso, módulo de infraestructura y composición, y explicar por qué un módulo que envuelve un solo recurso suele ser un error.
3. **Leer** la especificación Terraform de Azure Verified Modules y el código de un módulo AVM de VNet (90 min). Compara con lo que leíste: qué exige AVM que Best Practices no menciona.
4. **Hacer** el tutorial "Write Terraform tests" y **leer** la página de tests y la de mocks (2,5 h).
5. **Leer** la serie de Gruntwork sobre entornos (90 min) y, desde el índice de Terraform, las páginas de `workspaces`, backend `azurerm`, `moved`, `import`, `validation`, condiciones y restricciones de versión (2 h). Escribe un borrador de tu criterio workspaces frente a directorios.
6. **Leer** la autenticación de Terraform en Azure (OIDC) y el artículo de almacenar el estado en Azure Storage (60 min).
7. **Instalar y probar** `terraform-docs`, `tflint` (con el ruleset azurerm) y `checkov` sobre tu proyecto del Módulo Intermedio (2 h). Anota qué encuentran: será tu primera evidencia de "deuda" en código propio.
8. **Hacer el laboratorio** (18-24 h en varias sesiones).
9. **Responder la evaluación** y **revisar el checklist**.

Si vas justo de tiempo: haz obligatoriamente los puntos 1, 2, 4, 5 y 8.

## Laboratorio

### Objetivo

Construir la plataforma de infraestructura como código de "Nortesur Logística": un repositorio de módulos versionado (`network`, `compute`, `storage`, `monitoring`) documentado y probado, y un repositorio de entornos que compone esos módulos para `dev`, `stage` y `prod` con estado y bloqueo por entorno, pipeline con validaciones, análisis, plan en PR y apply aprobado, gobernanza en código y por política, dependencias entre stacks y detección de deriva nocturna.

### Requisitos

- Dos repositorios nuevos en GitHub (públicos, para tener Actions y entornos con revisores gratis): `terraform-azure-modules-<usuario>` y `terraform-live-<usuario>`.
- El Service Principal con federación OIDC del curso anterior, o uno nuevo con credenciales federadas para cada repositorio y entorno.
- Terraform ≥ 1.9, Azure CLI, `terraform-docs`, `tflint`, `checkov`, `gh` (GitHub CLI).
- Documenta en `laboratorio-terraform.md`. El código va en los repositorios; la entrega los enlaza y copia lo esencial.

> **Sobre el coste.** Estimación total: **menos de 3 USD**. VNets, subredes, NSGs, tablas de rutas, grupos de recursos, asignaciones de roles, políticas y grupos de acciones son gratuitos. Cuenta de almacenamiento del estado (Standard_LRS, unos MB): céntimos. Log Analytics: 5 GB/mes gratuitos. El módulo `compute` despliega una VM B1s **solo en `dev`** y solo mientras haces las pruebas (~0,01 USD/h; gratis si conservas las 750 h/mes). Las cuentas de almacenamiento del módulo `storage` en tres entornos: céntimos. Los pipelines corren en GitHub Actions gratis en repositorios públicos. Termina con `terraform destroy` por entorno (de `prod` a `dev`) y `az group delete` de todo lo que quede, incluido el grupo del estado si no lo reutilizas en el Proyecto Final.

### Instrucciones

**Parte A — Decisiones de plataforma (2 h, sin código)**

1. Escribe tres ADRs (formato del curso de Arquitectura): (1) multirepo módulos/live frente a monorepo; (2) directorios por entorno frente a `terraform workspaces` (con la tabla aislamiento / versionado / duplicación / riesgo de aplicar al entorno equivocado / soporte en backend `azurerm`); (3) un estado por stack y entorno frente a un estado por entorno. En cada ADR incluye "qué me haría cambiar de opinión".
2. Define las convenciones de gobernanza en `GOVERNANCE.md`: nombres (`<tipo>-<carga>-<entorno>-<región>-<nn>`, con las abreviaturas del Cloud Adoption Framework), etiquetas obligatorias (`entorno`, `propietario`, `curso`, `coste-centro`), regiones permitidas, tamaños de VM permitidos por entorno, y quién puede aplicar en qué entorno.
3. Tabla de equivalencias: backend `azurerm` con bloqueo por concesión de blob ↔ S3 + DynamoDB (o S3 con bloqueo nativo) ↔ GCS; Managed Identity/OIDC ↔ IAM role con OIDC ↔ Workload Identity Federation; Azure Policy ↔ SCP/Config ↔ Organization Policy; Azure Verified Modules ↔ módulos oficiales `terraform-aws-modules` ↔ `terraform-google-modules`.

**Parte B — Repositorio de módulos (6-8 h)**

4. Estructura `terraform-azure-modules-<usuario>/modules/{network,compute,storage,monitoring}/` con, en cada módulo: `main.tf`, `variables.tf`, `outputs.tf`, `versions.tf` (con `required_version = ">= 1.9"` y `azurerm ~> 4.0` o la mayor vigente), `README.md` generado, `examples/basic/`, `tests/*.tftest.hcl` y `CHANGELOG.md`. Añade en la raíz `.terraform-docs.yml`, `.tflint.hcl` (con el plugin `azurerm`), `.checkov.yml` y `.pre-commit-config.yaml` opcional.
5. Módulo `network`: VNet con `address_space` validado (debe ser un prefijo privado RFC 1918, usa `cidrhost`/`can` en `validation`), mapa de subredes con `for_each` (`{ nombre = { prefix, service_endpoints, nsg_rules } }`), NSG por subred con las reglas en un bloque `dynamic "security_rule"`, tabla de rutas opcional, y salidas `vnet_id`, `subnet_ids` (mapa) y `nsg_ids`. Añade una `precondition` en la VNet que exija las etiquetas obligatorias de `GOVERNANCE.md` (`alltrue([for t in var.required_tags : contains(keys(var.tags), t)])`) con mensaje de error claro.
6. Módulo `compute`: VM Linux con NIC, sin contraseña (`disable_password_authentication = true`), clave SSH por variable, tamaño validado contra una lista permitida (`B1s`, `B2s`), IP pública opcional (`count`), `custom_data` opcional, identidad administrada de sistema activada, y `postcondition` que compruebe que la NIC quedó en la subred esperada. Salidas: `vm_id`, `private_ip`, `principal_id`.
7. Módulo `storage`: cuenta con nombre validado (3-24 caracteres, minúsculas y números: `regex`), `min_tls_version = "TLS1_2"`, `allow_nested_items_to_be_public = false`, `shared_access_key_enabled` como variable con valor por defecto `false`, contenedores con `for_each`, opción de Private Endpoint (variable `private_endpoint_subnet_id`, `null` por defecto). Salidas: `id`, `primary_blob_endpoint`, `name`.
8. Módulo `monitoring`: Log Analytics workspace (retención 30 días, `daily_quota_gb = 0.5` para protegerte de la ingesta), grupo de acciones por correo, y `azurerm_monitor_diagnostic_setting` para un mapa de recursos que recibe por variable (`for_each` sobre `{ nombre = id }`). Salidas: `workspace_id`, `action_group_id`.
9. Documentación y calidad: ejecuta `terraform fmt -recursive`, `terraform validate` en cada módulo y ejemplo, `tflint --recursive`, `checkov -d modules/` y `terraform-docs markdown table --output-file README.md modules/<m>` para los cuatro. Corrige lo que salga o suprime con justificación escrita (`#checkov:skip=CKV_AZURE_xx: motivo`). Guarda la salida antes y después.
10. Tests. Para cada módulo escribe al menos: una prueba `command = plan` que compruebe que una entrada inválida falla (`expect_failures = [var.address_space]`), una que verifique con `assert` un valor calculado (por ejemplo, que se crean tantas subredes como entradas del mapa), y una con `mock_provider "azurerm"` que no necesite credenciales. Para `network` y `storage` añade una prueba `command = apply` real sobre `examples/basic` (recursos gratuitos o de céntimos) que se destruye sola al terminar. Ejecuta `terraform test` y guarda la salida. Explica qué prueba cada tipo y qué no puede probar. Lee la introducción de Terratest (Gruntwork) y escribe en cinco líneas cuándo compensaría escribir pruebas en Go.
11. Versionado: etiqueta el repositorio `v0.1.0`, haz un cambio compatible en `network` (nueva variable opcional) y etiqueta `v0.2.0`, y un cambio incompatible (renombra una salida) y etiqueta `v1.0.0` con nota en `CHANGELOG.md`. Explica el versionado semántico aplicado a módulos y por qué los consumidores deben fijar `?ref=v1.0.0` en la `source` de Git y no una rama.
12. Pipeline del repositorio de módulos (`.github/workflows/ci.yml`): en cada PR, `fmt -check`, `validate`, `tflint`, `checkov`, `terraform-docs` en modo comprobación (falla si el README no está regenerado) y `terraform test` con los mocks; las pruebas con `apply` real solo en `main` con OIDC. Sin secretos en el repositorio.

**Parte C — Repositorio live: entornos, estado y composición (5-6 h)**

13. Crea la infraestructura del estado con un pequeño stack aparte `bootstrap/` (estado local, se ejecuta una vez): grupo `rg-tfstate-nortesur`, cuenta `sttfstatenortesur<sufijo>` con `shared_access_key_enabled = false`, versionado de blobs activado, contenedor `tfstate`, y asignación `Storage Blob Data Contributor` a tu usuario y al SP del pipeline. Explica por qué el bootstrap tiene estado local y cómo lo protegerías.
14. Estructura `terraform-live-<usuario>/envs/{dev,stage,prod}/{network,platform}/` y `envs/global/monitoring/`. Cada stack tiene `backend.tf` con `use_azuread_auth = true` y una `key` propia (`dev/network.tfstate`, `dev/platform.tfstate`, ...), `main.tf` que llama a los módulos por `source = "git::https://github.com/<usuario>/terraform-azure-modules-<usuario>.git//modules/network?ref=v1.0.0"`, `terraform.tfvars` con lo que cambia por entorno (prefijos, tamaños, cuántas subredes) y `locals.tf` con nombres y etiquetas calculados a partir de `var.environment`. Explica qué se repite entre entornos y por qué se acepta esa repetición (y cómo Terragrunt la eliminaría).
15. `dev/network` despliega la VNet con dos subredes; `dev/platform` despliega `storage` y, con una variable `deploy_vm = true` solo en `dev`, una VM del módulo `compute` en una de las subredes. `platform` obtiene los IDs de subred de `network` de **dos formas** y compara: `data "terraform_remote_state"` sobre el backend `azurerm` (`use_azuread_auth`) y `data "azurerm_subnet"` por nombre. Explica en tu documento las ventajas de cada una (acoplamiento, permisos necesarios sobre el estado, qué pasa si el stack de red renombra una salida).
16. `global/monitoring` despliega el workspace y recibe los IDs de las cuentas de almacenamiento de los tres entornos para sus diagnósticos. Despliega `stage` y `prod` (sin VM). Comprueba el bloqueo: lanza `terraform apply` en `prod/network` en una terminal, y en otra `terraform plan` sobre el mismo stack: debe fallar con error de estado bloqueado. Muestra la concesión del blob en el portal. Explica qué haría `terraform force-unlock` y cuándo es peligroso.
17. Refactorización sin destruir: en `dev/platform`, cambia el nombre local del recurso del módulo `storage` en tu código y usa un bloque `moved` para que el `plan` muestre 0 cambios destructivos. Después crea a mano con la CLI una cuenta de almacenamiento "heredada" y adóptala con un bloque `import` más `terraform plan -generate-config-out=imported.tf`; ajusta el código generado. Guarda los planes que demuestran que nada se destruye.
18. Versiones a escala: ejecuta `terraform providers lock -platform=linux_amd64 -platform=darwin_arm64 -platform=windows_amd64` en cada stack y explica qué contiene `.terraform.lock.hcl`, por qué se versiona y qué diferencia hay entre `~> 4.0`, `>= 4.0, < 5.0` y `= 4.12.0`. Sube el proveedor una versión menor en `dev` y describe el procedimiento para promoverlo a `stage` y `prod`.

**Parte D — Pipeline del repositorio live (3-4 h)**

19. `.github/workflows/plan.yml`: en `pull_request`, para cada stack cambiado (detecta el directorio con `git diff --name-only`), `fmt -check`, `validate`, `tflint`, `checkov` sobre el plan en JSON (`terraform show -json plan.tfplan > plan.json` y `checkov -f plan.json`), y `terraform plan -no-color -out plan.tfplan`; publica el plan como comentario del PR con `gh pr comment --body-file plan.md` (recorta a 60 KB y sube el completo como artefacto). Autenticación con OIDC, `permissions: { id-token: write, contents: read, pull-requests: write }`.
20. `.github/workflows/apply.yml`: en `push` a `main`, un job por entorno en orden `dev` → `stage` → `prod`, cada uno con `environment: <env>`; `stage` y `prod` con revisor obligatorio. El job hace `plan -out` y `apply plan.tfplan` (aplica exactamente lo planificado). Crea un PR real que añada una subred en `dev` y en `prod`, revisa el comentario del plan, fusiona, aprueba `prod` y verifica. Guarda capturas del comentario y de la aprobación.
21. Gobernanza como red de seguridad: asigna en la suscripción (o en un grupo de administración si lo creaste en Arquitectura) la iniciativa de Azure Policy del curso anterior en modo `Audit`, y una asignación `Deny` de "Require a tag" `propietario` sobre `rg-nortesur-prod`. Crea un PR que quite la etiqueta en `prod`: la `precondition` del módulo debe fallar en `plan`; comenta la `precondition` temporalmente y observa cómo falla el `apply` con `RequestDisallowedByPolicy`. Explica la diferencia entre la validación en código (rápida, del equipo) y la política (última barrera, de la organización).
22. Detección de deriva: `.github/workflows/drift.yml` con `schedule` nocturno que ejecuta `terraform plan -detailed-exitcode -lock=false` en cada stack; con código de salida 2 abre un issue con `gh issue create` (o actualiza el existente) con el resumen del plan. Prueba: cambia a mano una etiqueta en el portal en `stage`, lanza el workflow con `workflow_dispatch` y comprueba el issue. Explica por qué la deriva se **detecta** de noche pero **no se corrige** automáticamente, y en qué casos sí automatizarías el `apply`.

**Parte E — Revisión frente a Azure Verified Modules (1-2 h)**

23. Compara tu módulo `network` con el módulo AVM equivalente de VNet: interfaz (variables, mapas), tests, ejemplos, versionado, documentación, telemetría. Anota cinco cosas que AVM hace y tú no, y decide para cada una si la adoptas. Sustituye en `dev/network` tu módulo por el de AVM en una rama, mira el `plan`, y escribe la ADR "módulos propios frente a AVM" con tu criterio (control, curva de aprendizaje, dependencia de un tercero, ritmo de cambios).

**Parte F — Limpieza (30 min)**

24. `terraform destroy` en `prod`, `stage`, `dev` (primero `platform`, después `network`) y `global`. Decide si conservas `rg-tfstate-nortesur` para el Proyecto Final (recomendado; cuesta céntimos) o lo borras. Al día siguiente, captura Cost Management filtrado por `curso=terraform-avanzado`.

### Resultado esperado

- Repositorio de módulos con cuatro módulos documentados, probados, versionados (`v0.1.0`, `v0.2.0`, `v1.0.0`) y con CI verde.
- Repositorio live con `bootstrap/`, `envs/{dev,stage,prod}/{network,platform}`, `envs/global/monitoring`, tres workflows (plan, apply, drift) y al menos dos PRs fusionados con plan comentado y apply aprobado.
- `laboratorio-terraform.md` con ADRs, `GOVERNANCE.md`, equivalencias, evidencias (salidas de herramientas, tests, bloqueo, `moved`/`import`, deriva, política) y la revisión frente a AVM.
- Ningún recurso vivo salvo, si lo decides, el grupo del estado.

### Criterios de validación

- [ ] Parte A: las tres ADRs comparan alternativas con criterios explícitos y dicen qué haría cambiar la decisión.
- [ ] Parte B: cada módulo pasa `fmt`, `validate`, `tflint`, `checkov` y `terraform test`; los READMEs están generados; las validaciones y condiciones rechazan entradas incorrectas con mensajes claros; hay tres tags con versionado semántico justificado en el `CHANGELOG`.
- [ ] Parte C: hay un estado por stack y entorno con autenticación de Entra ID; se demostró el bloqueo; `moved` e `import` produjeron planes sin destrucción; las dos formas de dependencia entre stacks funcionan y están comparadas; los lockfiles están versionados.
- [ ] Parte D: el plan aparece como comentario en el PR; `prod` requirió aprobación; la `precondition` y la política bloquearon la etiqueta faltante en momentos distintos; el workflow de deriva abrió un issue con el cambio manual.
- [ ] Parte E: la comparación con AVM es concreta y la ADR toma una posición.
- [ ] Sin secretos en ningún repositorio (el pipeline usa OIDC) y sin `tfstate` en Git.
- [ ] El estudiante puede explicar al mentor, con su código delante, qué pasaría si dos personas ejecutaran `apply` en `prod` a la vez, y qué pasaría si alguien borrara el archivo de bloqueo de dependencias.

## Entrega

En tu repositorio de entregas, carpeta `03-modulo-avanzado/06-terraform-avanzado-e-iac-a-escala/`:

1. `laboratorio-terraform.md` con enlaces a los dos repositorios (y a los PRs), ADRs, `GOVERNANCE.md`, equivalencias, evidencias y revisión AVM.
2. `evidencias/` con salidas de `terraform test`, `tflint`, `checkov`, planes de `moved`/`import`, error de bloqueo, error de política, issue de deriva.
3. `capturas/` (comentario del plan en el PR, aprobación de entorno, concesión del blob, Cost Management).
4. `ENTREGA.md` con evaluación, checklist y uso de IA.

Nota sobre IA: es muy útil para explicarte un mensaje de `terraform test` o proponer una expresión de `validation`; comprueba siempre las funciones y argumentos contra la documentación de HashiCorp y del proveedor, porque los modelos mezclan versiones de Terraform y de `azurerm` con frecuencia. Declara su uso.

## Evaluación

1. **Conceptual.** ¿Qué distingue un módulo de recurso, un módulo de infraestructura y una composición? Clasifica tus cuatro módulos y tus stacks de `envs/`. ¿Por qué un módulo que envuelve un único `azurerm_resource_group` suele ser mala idea?
2. **Situacional.** Un equipo propone gestionar `dev`, `stage` y `prod` con `terraform workspaces` en un solo directorio "para no duplicar código". Expón tres riesgos concretos y en qué caso sí aceptarías workspaces.
3. **Técnica.** Explica cómo bloquea el estado el backend `azurerm`, qué ocurre si un `apply` muere a mitad, qué hace `force-unlock` y por qué el bootstrap del estado es un problema de "huevo y gallina".
4. **Técnica.** Escribe (en pseudocódigo HCL) una `validation` para que un mapa de subredes no tenga prefijos solapados, o explica por qué es difícil y qué comprobarías en su lugar con una `precondition` o un `check`.
5. **Troubleshooting.** Tras renombrar `module.storage` a `module.storage_docs`, el `plan` quiere destruir y recrear la cuenta con todos sus datos. ¿Qué bloque evita el desastre, cómo se escribe y qué habrías hecho en versiones antiguas de Terraform?
6. **Conceptual.** Diferencia `terraform validate`, `tflint`, `checkov`, `terraform test` con `plan`, con mocks y con `apply`. Da un error que solo detecta cada uno.
7. **Situacional.** El `plan` comentado en un PR de `prod` muestra `-/+ destroy and then create replacement` para una VM. Describe el proceso de revisión y decisión y qué mecanismos del pipeline y del código (`prevent_destroy`, aprobación, `create_before_destroy`) intervienen.
8. **Técnica.** `?ref=v1.0.0` frente a `?ref=main` en la `source` de un módulo: qué garantiza cada uno, cómo promoverías `v1.1.0` de `dev` a `prod`, y qué relación tiene con `.terraform.lock.hcl` (pista: ninguna directa; explica por qué).
9. **Situacional.** Tres stacks dependen de las salidas del stack de red. El equipo de red quiere renombrar la salida `subnet_ids` a `subnets`. Compara el impacto si los consumidores usan `terraform_remote_state` frente a `data "azurerm_subnet"`, y propone un plan de migración sin cortes.
10. **Conceptual.** Validación en código (`validation`, `precondition`), pipeline (`checkov`) y plataforma (Azure Policy): qué detecta cada capa, en qué momento y quién la controla. ¿Por qué hacen falta las tres?
11. **Troubleshooting.** El workflow de deriva abre un issue todas las noches por el mismo recurso aunque nadie lo toca: el `plan` muestra un cambio en una etiqueta que Azure añade automáticamente. Explica la causa y dos soluciones (`ignore_changes`, corregir el módulo) con sus contrapartidas.
12. **Situacional.** Un pipeline de `apply` a `prod` usa un secreto de cliente guardado en GitHub. ¿Qué cambiarías y por qué? ¿Qué permisos mínimos daría al SP y a qué ámbito? ¿Cómo separarías la identidad de `plan` (lectura) de la de `apply` (escritura)?
13. **Conceptual.** Módulos propios frente a Azure Verified Modules frente a Terragrunt: qué problema resuelve cada uno, qué coste organizativo tiene y qué elegirías para Nortesur con un equipo de plataforma de dos personas y con uno de veinte.
14. **Técnica.** Explica qué hace `terraform plan -detailed-exitcode` y por qué el workflow de deriva usa `-lock=false`. ¿Qué riesgo introduce ese flag y por qué es aceptable en ese caso concreto?
15. **Reflexión.** Compara tu proyecto del Módulo Intermedio con la plataforma de este curso: ¿qué tres cambios aportan más valor por esfuerzo? ¿Qué parte te parece sobreingeniería para un equipo pequeño y por qué la mantendrías o no en el Proyecto Final?

## Checklist final

Antes de continuar, deberías poder:

- [ ] Diseñar un módulo con contrato claro, estructura estándar, validaciones, ejemplos y README generado.
- [ ] Escribir y ejecutar pruebas con `terraform test` (plan, mocks y apply) y explicar qué cubre cada tipo.
- [ ] Versionar módulos con tags semánticos y consumirlos con referencias fijas.
- [ ] Montar un estado por stack y entorno en Azure Storage con bloqueo y autenticación de Entra ID.
- [ ] Defender con criterio directorios por entorno frente a workspaces.
- [ ] Refactorizar e importar sin destruir con `moved` e `import`.
- [ ] Fijar y actualizar versiones de Terraform, proveedores y módulos de forma controlada.
- [ ] Construir pipelines con `fmt`, `validate`, `tflint`, `checkov`, plan en PR y apply aprobado, sin secretos.
- [ ] Implantar gobernanza en código y por política, y explicar qué capa detecta qué.
- [ ] Gestionar dependencias entre stacks y detectar deriva de forma programada.
- [ ] Situar Azure Verified Modules y Terragrunt frente a módulos propios.
- [ ] Tener la suscripción limpia (salvo el estado, si lo conservas) y el coste documentado.

---

*Recursos verificados el 2026-09-27 (existencia y vigencia de las URLs mediante búsqueda web y, cuando el cupo de búsqueda se agotó, mediante los repositorios oficiales de la documentación). Las páginas de Microsoft Learn se enlazan en `es-es` cuando se confirmó la traducción; en el resto se indica cómo cambiar el idioma. Si un enlace falla, abre un issue en este repositorio.*
