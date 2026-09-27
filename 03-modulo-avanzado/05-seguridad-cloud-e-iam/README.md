# Seguridad Cloud e IAM

> Módulo: Avanzado · Curso 5 de 12 · Duración estimada: 35-45 horas · Estado: ✅ Completo

## Objetivo

Repasa mentalmente todo lo que has desplegado en la ruta: cadenas de conexión en variables de entorno, claves de cuentas de almacenamiento en `terraform.tfvars`, un Service Principal con secreto guardado en GitHub, contraseñas de base de datos en un `docker-compose.yml`, una clave SSH que quizá compartiste entre varias VMs. Cada uno de esos elementos es una credencial embebida: algo que, si se filtra, da acceso a tu infraestructura sin que nadie tenga que "entrar" en ningún sitio. La mayoría de las brechas reales en la nube empiezan así, no con un exploit sofisticado.

Este curso te enseña a construir un entorno donde **no haya secretos que robar**: las aplicaciones se identifican con Managed Identity, los pipelines se autentican con federación OIDC sin secreto de cliente, los secretos que no pueden evitarse viven en Key Vault y se leen por identidad, cada identidad tiene exactamente los permisos que necesita (RBAC, roles personalizados, grupos), la plataforma impide por política lo que no debe existir (Azure Policy), la postura de seguridad se mide de forma continua (Defender for Cloud) y las máquinas Linux están endurecidas. Todo bajo el marco Zero Trust: verificar explícitamente, privilegio mínimo, asumir la brecha.

Termina con un ejercicio incómodo y muy útil: buscar credenciales en tu propio historial de Git con `gitleaks`. Casi todo el mundo encuentra algo.

**Antes de empezar** necesitas el curso de Networking Cloud Avanzado (Private Endpoints, NSG), Docker (la aplicación del curso de Docker), CI/CD (GitHub Actions) y Terraform.

### Al terminar este curso deberías poder

- Explicar los tres principios de Zero Trust y aplicarlos a una decisión concreta de identidad, red o datos.
- Distinguir usuario, grupo, Service Principal, Managed Identity (de sistema y de usuario) y App Registration en Entra ID, y elegir la identidad correcta para cada carga de trabajo.
- Diseñar asignaciones RBAC con privilegio mínimo: roles integrados, rol personalizado, ámbito adecuado y grupos en vez de usuarios.
- Configurar una aplicación en Azure para leer secretos y certificados de Key Vault por identidad, sin cadena de conexión ni clave en configuración.
- Autenticar GitHub Actions contra Azure con federación OIDC (sin secreto de cliente almacenado) y explicar el flujo de tokens.
- Explicar qué aportan PIM y Conditional Access, qué licencia requieren y cómo se aproximan sus beneficios sin ellas.
- Escribir y asignar una iniciativa de Azure Policy con efecto `deny` y leer el estado de cumplimiento.
- Interpretar el Secure Score y las recomendaciones de Microsoft Defender for Cloud en su plan gratuito.
- Aplicar una línea base de hardening a una VM Linux (SSH, `fail2ban`, actualizaciones automáticas, `auditd`) y situarla frente a CIS Benchmark.
- Usar autenticación basada en identidad hacia Storage (y PostgreSQL si el coste lo permite) y auditar tu propio código en busca de credenciales con `gitleaks`.

## Prerrequisitos

- Módulo Intermedio completo, especialmente Administración de Azure (Entra ID, RBAC y Key Vault introductorios), Docker, CI/CD y Terraform.
- Módulo Avanzado, curso 4: Networking Cloud Avanzado (Private Endpoints, NSG, service endpoints).
- La aplicación del curso de Docker (API Python con `/health` y `/version`) en su repositorio, con su imagen publicada en un registro.
- Eres administrador global de tu propio inquilino de Entra ID (lo eres si creaste la cuenta de Azure tú mismo). Entra ID Free es suficiente.

## Temario

- Entra ID.
- RBAC.
- Least privilege.
- Managed Identities.
- Service Principals.
- Key Vault.
- Secrets.
- Certificates.
- Zero Trust.
- Azure Policy.
- Security posture.
- Hardening.
- Privileged access.
- Network security.
- Identity-based authentication.

**Práctica:** diseñar un entorno sin credenciales embebidas y con privilegios mínimos.

## Recursos en español

### Administrar la identidad y el acceso en Microsoft Entra ID y Protección de la identidad y el acceso en Azure (rutas AZ-500) — Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/training/paths/manage-identity-and-access/ · https://learn.microsoft.com/es-es/training/paths/secure-identity-access/ · Curso completo AZ-500T00 (índice de todas sus rutas): https://learn.microsoft.com/es-es/training/courses/az-500t00
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Rutas de aprendizaje con ejercicios
- **Duración aproximada:** 8-10 h las dos rutas; desde el índice del curso AZ-500T00 haz además las rutas de protección de la plataforma (Azure Policy, Defender for Cloud) y de datos y aplicaciones (Key Vault): 6-8 h más
- **Cubre:** Entra ID, RBAC, Managed Identities, Service Principals, PIM, Conditional Access, Key Vault, Azure Policy, Defender for Cloud
- **Nivel:** Avanzado
- **Acceso:** Libre; cuenta Microsoft gratuita para guardar progreso
- **Por qué lo recomiendo:** Es el material oficial de la certificación de seguridad de Azure y el recurso principal del curso. Los ejercicios sobre PIM y Conditional Access requieren licencia P2: léelos y entiende la configuración, no la repliques.

### Guía de estudio SC-900: Fundamentos de seguridad, cumplimiento e identidad — Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/credentials/certifications/resources/study-guides/sc-900 (desde la guía se enlazan las rutas de aprendizaje gratuitas del examen)
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Guía de estudio con enlaces a rutas de aprendizaje
- **Duración aproximada:** 3-4 h para las rutas de conceptos de seguridad e identidad (Zero Trust, defensa en profundidad, responsabilidad compartida, autenticación y autorización)
- **Cubre:** Zero Trust, Entra ID, conceptos de identidad
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la base conceptual, en español, para el marco Zero Trust y el vocabulario de identidad antes de entrar en la implementación de AZ-500. Si ya tienes clara la diferencia entre autenticación y autorización y los tres principios de Zero Trust, léelo en una hora.

### Documentación de Azure Key Vault (es-es) — Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/azure/key-vault/ · Conceptos básicos: https://learn.microsoft.com/es-es/azure/key-vault/general/basic-concepts · Claves, secretos y certificados: https://learn.microsoft.com/es-es/azure/key-vault/general/about-keys-secrets-certificates · Seguridad: https://learn.microsoft.com/es-es/azure/key-vault/general/security-features · Guía del desarrollador: https://learn.microsoft.com/es-es/azure/key-vault/general/developers-guide · Registro: https://learn.microsoft.com/es-es/azure/key-vault/general/logging
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Documentación oficial
- **Duración aproximada:** 2 h de lectura
- **Cubre:** Key Vault, Secrets, Certificates, RBAC sobre Key Vault, red, auditoría
- **Nivel:** Intermedio-avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** Key Vault es el centro del laboratorio. La guía del desarrollador explica cómo lo usan las aplicaciones con `DefaultAzureCredential`, y la página de seguridad explica el modelo de permisos RBAC frente a las antiguas directivas de acceso, soft delete y protección contra purga.

### Preparación para AZ-500: administrar la identidad y el acceso (Exam Readiness Zone) — Microsoft Learn
- **URL:** https://learn.microsoft.com/es-ES/shows/exam-readiness-zone/preparing-for-az-500-manage-identity-and-access-1-of-4 (serie de 4 episodios enlazados)
- **Autor / organización:** Microsoft
- **Idioma:** Página en español; vídeos en inglés con subtítulos
- **Tipo:** Vídeos cortos
- **Duración aproximada:** 4 episodios de 25-35 min
- **Cubre:** Repaso de identidad, plataforma, datos y operaciones de seguridad
- **Nivel:** Avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** Repaso final antes de la evaluación; cada episodio plantea preguntas de escenario que se parecen a las de este curso.

## Recursos en inglés

### Zero Trust Guidance Center y Zero Trust security in Azure — Microsoft Learn
- **URL:** https://learn.microsoft.com/en-us/security/zero-trust/ · Zero Trust en Azure: https://learn.microsoft.com/en-us/azure/security/fundamentals/zero-trust · Marco de adopción: https://learn.microsoft.com/en-us/security/zero-trust/adopt/zero-trust-adoption-overview
- **Autor / organización:** Microsoft
- **Idioma:** Inglés
- **Tipo:** Guías de arquitectura y adopción
- **Duración aproximada:** 90 min para la introducción, los pilares y la página de Azure
- **Cubre:** Zero Trust, identidad, red, datos, infraestructura
- **Nivel:** Intermedio-avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la fuente del marco que ordena todo el curso. Lee los principios y el pilar de identidad e infraestructura, y usa su lenguaje para justificar cada decisión de la entrega ("verifica explícitamente", "privilegio mínimo", "asume la brecha").

### Microsoft cloud security benchmark — Microsoft Learn
- **URL:** https://learn.microsoft.com/en-us/security/benchmark/azure/introduction · Índice: https://learn.microsoft.com/en-us/security/benchmark/azure/ · Líneas base por servicio: https://learn.microsoft.com/en-us/security/benchmark/azure/security-baselines-overview · Cómo lo evalúa Defender for Cloud: https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-regulatory-compliance
- **Autor / organización:** Microsoft
- **Idioma:** Inglés
- **Tipo:** Marco de controles de seguridad
- **Duración aproximada:** 2 h para los dominios de identidad (IM), acceso privilegiado (PA), seguridad de red (NS) y postura (PV)
- **Nivel:** Avanzado
- **Cubre:** Security posture, Privileged access, Network security, Identity
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es el catálogo de controles que Defender for Cloud usa para calcular el Secure Score, con la correspondencia a CIS, NIST y PCI. Cuando una recomendación del portal no te diga por qué importa, busca el control aquí. Las líneas base por servicio (Key Vault, Storage, Container Apps) son la lista de comprobación del laboratorio.

### Configuring OpenID Connect in Azure — GitHub Docs
- **URL:** https://docs.github.com/en/actions/security-for-github-actions/security-hardening-your-deployments/configuring-openid-connect-in-azure
- **Autor / organización:** GitHub
- **Idioma:** Inglés
- **Tipo:** Documentación oficial
- **Duración aproximada:** 30 min
- **Cubre:** Service Principals, federación OIDC, `azure/login`
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la guía exacta de la Parte D del laboratorio. Presta atención al apartado de `subject` (repositorio, rama, entorno): es lo que impide que otro repositorio use tu identidad.

### CIS Benchmarks (Ubuntu Linux) — Center for Internet Security, y guía CIS de Ubuntu — Canonical
- **URL:** https://www.cisecurity.org/cis-benchmarks · Ubuntu: https://www.cisecurity.org/benchmark/ubuntu_linux · Documentación de Ubuntu sobre perfiles CIS: https://documentation.ubuntu.com/security/compliance/usg/cis-benchmarks/
- **Autor / organización:** Center for Internet Security; Canonical
- **Idioma:** Inglés
- **Tipo:** Estándar de configuración (PDF) y documentación
- **Duración aproximada:** 90 min para leer la estructura del benchmark y las secciones de SSH, auditoría y actualizaciones
- **Cubre:** Hardening
- **Nivel:** Avanzado
- **Acceso:** El PDF del benchmark es gratuito para uso no comercial pero **requiere cuenta gratuita** en CIS. La herramienta `usg` de Ubuntu requiere Ubuntu Pro (gratuito para uso personal en hasta 5 máquinas, con cuenta de Ubuntu One)
- **Por qué lo recomiendo:** Es el estándar de facto de hardening de sistemas. No vas a aplicar sus 300 controles; vas a entender cómo está organizado (niveles 1 y 2, controles automatizados y manuales) y a mapear tu línea base contra él.

### Gitleaks — Zachary Rice y comunidad
- **URL:** https://github.com/gitleaks/gitleaks · Web: https://gitleaks.io/ · Acción para GitHub: https://github.com/gitleaks/gitleaks-action
- **Autor / organización:** Proyecto de código abierto Gitleaks
- **Idioma:** Inglés
- **Tipo:** Herramienta y documentación
- **Duración aproximada:** 30 min para instalar y aprender `gitleaks git` y `gitleaks dir`
- **Cubre:** Secrets (detección de credenciales en repositorios)
- **Nivel:** Intermedio
- **Acceso:** Libre (licencia MIT). La acción de GitHub es gratuita para repositorios personales; las organizaciones necesitan licencia
- **Por qué lo recomiendo:** Es el escáner de secretos de código abierto más usado y lo que ejecutarás en la Parte G sobre todos tus repositorios. Lo volverás a ver en DevSecOps integrado en pipelines.

## Documentación oficial

- **Portal de documentación de Azure (es-es):** https://learn.microsoft.com/es-es/azure/ (busca aquí las páginas de Managed Identities, RBAC de Azure, roles personalizados, Azure Policy, Defender for Cloud, Container Apps, App Service, Storage y PostgreSQL flexible que necesites en el laboratorio; la navegación del portal es estable, las URLs profundas cambian)
- **Key Vault (es-es):** https://learn.microsoft.com/es-es/azure/key-vault/
- **Zero Trust:** https://learn.microsoft.com/en-us/security/zero-trust/ · En Azure: https://learn.microsoft.com/en-us/azure/security/fundamentals/zero-trust
- **Microsoft cloud security benchmark:** https://learn.microsoft.com/en-us/security/benchmark/azure/
- **Responsabilidad compartida:** https://learn.microsoft.com/en-us/azure/security/fundamentals/shared-responsibility (ya visto en el Módulo Básico; vuelve a él para el hardening: en IaaS el SO es tuyo)
- **Autenticación de Terraform en Azure (es-es):** https://learn.microsoft.com/es-es/azure/developer/terraform/authenticate-to-azure (incluye OIDC y Managed Identity para Terraform)
- **GitHub Docs, OIDC en Azure:** https://docs.github.com/en/actions/security-for-github-actions/security-hardening-your-deployments/configuring-openid-connect-in-azure
- **CIS Benchmarks:** https://www.cisecurity.org/cis-benchmarks
- **Gitleaks:** https://github.com/gitleaks/gitleaks
- **Terraform:** proveedores `azurerm` (recursos `azurerm_key_vault`, `azurerm_key_vault_secret`, `azurerm_key_vault_certificate`, `azurerm_role_assignment`, `azurerm_role_definition`, `azurerm_user_assigned_identity`, `azurerm_container_app`, `azurerm_policy_set_definition`, `azurerm_resource_group_policy_assignment`) y `azuread` (`azuread_group`, `azuread_application`, `azuread_service_principal`, `azuread_application_federated_identity_credential`) en el Terraform Registry.

## Ruta recomendada de estudio

1. **Leer** los principios de Zero Trust y la página de Zero Trust en Azure (60 min). Escribe con tus palabras qué significa cada principio para una API que lee un secreto.
2. **Hacer** la ruta SC-900 de conceptos de seguridad e identidad si no tienes claros autenticación, autorización, identidad federada y defensa en profundidad (2-3 h; si los tienes claros, 45 min de repaso).
3. **Hacer** la ruta "Administrar la identidad y el acceso en Microsoft Entra ID" (4-5 h): usuarios, grupos, Service Principals, Managed Identities, RBAC, PIM, Conditional Access. Toma nota de qué necesita licencia P1/P2.
4. **Leer** la documentación de Key Vault: conceptos básicos, objetos, seguridad y guía del desarrollador (2 h). Debes poder explicar RBAC frente a directivas de acceso, soft delete, purge protection y `DefaultAzureCredential`.
5. **Leer** la guía de OIDC de GitHub Docs y la de autenticación de Terraform en Azure (60 min). Dibuja el flujo de tokens: GitHub emite un JWT, Entra lo valida contra la credencial federada, devuelve un token de acceso.
6. **Hacer** desde el índice AZ-500T00 las rutas de protección de plataforma (Azure Policy, Defender for Cloud, seguridad de red) (4-5 h).
7. **Leer** los dominios IM, PA, NS y PV del Microsoft cloud security benchmark (2 h) y la estructura del CIS Benchmark de Ubuntu (60 min).
8. **Instalar** `gitleaks` y ejecutarlo contra un repositorio de prueba con un secreto falso para entender su salida (30 min).
9. **Hacer el laboratorio** (18-24 h en varias sesiones).
10. **Ver** la serie Exam Readiness AZ-500, **responder la evaluación** y **revisar el checklist**.

Si vas justo de tiempo: haz obligatoriamente los puntos 1, 3, 4, 5 y 9.

## Laboratorio

### Objetivo

Rediseñar la plataforma de "Nortesur Logística" para que funcione **sin ninguna credencial embebida**: la aplicación del curso de Docker se ejecuta en Azure Container Apps con identidades administradas, lee sus secretos y su certificado de Key Vault y accede a Storage por identidad; el pipeline de GitHub Actions despliega con federación OIDC; el acceso humano se organiza con grupos, roles integrados y un rol personalizado; Azure Policy impide configuraciones prohibidas; Defender for Cloud mide la postura; la VM Linux queda endurecida; y tú auditas tu propio historial de Git en busca de secretos.

### Requisitos

- Azure CLI, Terraform, Docker, Git y `gitleaks` instalados. Python 3 con `azure-identity`, `azure-keyvault-secrets` y `azure-storage-blob` para la aplicación.
- La aplicación del curso de Docker en su repositorio, con pipeline de GitHub Actions del curso de CI/CD.
- Una VM Linux para el hardening: `lab-so` o una B1s en Azure (la reutilizas de la Parte F).
- Documenta en `laboratorio-seguridad.md`. Las capturas del portal deben mostrar tu usuario; oculta IDs de inquilino y suscripción completos.

> **Sobre el coste.** Estimación total si limpias al final: **2-6 USD**. Container Apps tiene una concesión mensual gratuita (180.000 vCPU-segundos y 2 millones de peticiones) que cubre el laboratorio con escala a cero. Key Vault cobra por operación (~0,03 USD por cada 10.000; céntimos). Entra ID Free, RBAC, Azure Policy, Defender for Cloud en su plan gratuito (CSPM básico) y GitHub Actions en repositorio público son gratuitos. Azure Container Registry Basic cuesta ~0,17 USD/día: úsalo solo los días del laboratorio o publica la imagen en GitHub Container Registry (gratuito para imágenes públicas). Log Analytics: los primeros 5 GB/mes son gratuitos. VM B1s ~0,01 USD/h (gratis si conservas las 750 h/mes). **Cuidado con:** activar planes de pago de Defender for Cloud (tienen 30 días de prueba y después cobran por recurso: no los actives, o desactívalos el mismo día), la prueba de Entra ID P2 (gratuita 30 días, pero no la necesitas), y PostgreSQL flexible (B1ms ~13 USD/mes; solo si tu cuenta conserva las 750 h gratuitas de 12 meses, y bórralo el mismo día). Termina con `az group delete` y comprobación en Cost Management.

### Instrucciones

**Parte A — Inventario de credenciales y modelo de amenazas (2 h, sin desplegar)**

1. Recorre tus entregas de los cursos de Administración de Azure, Docker, CI/CD, Terraform y Monitoreo y lista en una tabla **todas** las credenciales que usaste: tipo (clave de cuenta, cadena de conexión, secreto de SP, contraseña, token, clave SSH), dónde vivía (archivo, variable de entorno, secreto de GitHub, portal), quién podía leerla, cuánto tiempo era válida y qué podría hacer un atacante con ella. Sé honesto: esta tabla es la línea base del curso.
2. Para cada fila, propone el sustituto sin credencial (Managed Identity, OIDC, Key Vault por identidad, autenticación de Entra ID al servicio de datos) o, si no existe, cómo lo guardarías y rotarías. Anota cuáles resolverás en este laboratorio.
3. Escribe el modelo Zero Trust de Nortesur en una página: para identidad, dispositivos (tu equipo), red, aplicación y datos, di qué significa "verificar explícitamente", "privilegio mínimo" y "asumir la brecha", y qué control concreto de este laboratorio implementa cada celda. Añade la tabla de equivalencias Azure ↔ AWS ↔ GCP: Entra ID (IAM Identity Center / Cloud Identity), Managed Identity (IAM role for EC2/ECS / service account adjunta), Key Vault (Secrets Manager + KMS / Secret Manager + Cloud KMS), Azure Policy (Organizations SCP + Config rules / Organization Policy), Defender for Cloud (Security Hub / Security Command Center), PIM (IAM Identity Center permission sets temporales / Privileged Access Manager).

**Parte B — Key Vault y RBAC sobre datos (2-3 h)**

4. Proyecto Terraform `nortesur-seguridad/` con backend remoto, grupo `rg-nortesur-seg`, etiquetas obligatorias (`curso`, `propietario`, `entorno`). Crea `azurerm_key_vault` con `rbac_authorization_enabled = true` (el laboratorio no usa directivas de acceso), `soft_delete_retention_days = 7`, `purge_protection_enabled = false` (solo porque vas a destruirlo; explica por qué en producción iría a `true`), `sku_name = "standard"`. Asígnate el rol `Key Vault Administrator` sobre el vault con `azurerm_role_assignment` (usa `data.azurerm_client_config`). Explica por qué ser `Owner` de la suscripción **no** te da permiso para leer secretos con el modelo RBAC (plano de control frente a plano de datos).
5. Crea un secreto `api-token` (valor generado con `random_password`, marcado `sensitive`) y un certificado autofirmado `cert-api` con `azurerm_key_vault_certificate` (política con `exportable = true`, RSA 2048, 12 meses). Comprueba con `az keyvault secret show` y `az keyvault certificate show`. Explica la diferencia entre clave, secreto y certificado en Key Vault, qué son las versiones y por qué las aplicaciones deben referenciar el secreto sin versión (o con ella, según el caso de rotación).
6. Activa el registro de auditoría del vault hacia un Log Analytics workspace (`azurerm_monitor_diagnostic_setting`, categoría `AuditEvent`). Al final del laboratorio consultarás con KQL quién leyó qué secreto.

**Parte C — La aplicación sin credenciales: Managed Identities (4-5 h)**

7. Amplía la aplicación del curso de Docker con dos endpoints: `/secret-check`, que lee `api-token` de Key Vault con `DefaultAzureCredential` + `SecretClient` y devuelve solo su longitud y los 4 últimos caracteres del hash SHA-256 (nunca el valor); y `/docs-count`, que lista los blobs de un contenedor de una cuenta de almacenamiento con `BlobServiceClient(account_url, credential=DefaultAzureCredential())` y devuelve la cantidad. La URL del vault y de la cuenta llegan por variables de entorno `KEY_VAULT_URL` y `STORAGE_URL`: son identificadores, no secretos. Explica el orden de credenciales que prueba `DefaultAzureCredential` y por qué el mismo código funciona en tu portátil (con `az login`) y en Azure (con Managed Identity).
8. Construye y publica la imagen con una etiqueta nueva. Registro: ACR Basic con `admin_enabled = false` (Terraform) o GHCR público. Si usas ACR, crea una `azurerm_user_assigned_identity` `id-nortesur-acr` con rol `AcrPull` sobre el registro: es la identidad **de usuario** que usará Container Apps para descargar la imagen sin usuario ni contraseña de registro.
9. Despliega con Terraform un `azurerm_container_app_environment` (con el Log Analytics de la Parte B) y un `azurerm_container_app` con: `identity { type = "SystemAssigned, UserAssigned" }` incluyendo `id-nortesur-acr`; bloque `registry` que use la identidad de usuario (`identity = azurerm_user_assigned_identity.acr.id`); escala mínima 0 y máxima 1; ingress externo en el puerto de la aplicación. Asigna a la identidad **de sistema** de la app el rol `Key Vault Secrets User` sobre el vault y `Storage Blob Data Reader` sobre una cuenta de almacenamiento `stnortesurdocs<sufijo>` (con `shared_access_key_enabled = false`: las claves de cuenta quedan deshabilitadas, no solo sin usar). Sube dos blobs con tu propia identidad (`az storage blob upload --auth-mode login`).
10. Prueba: `curl https://<fqdn>/secret-check` y `curl https://<fqdn>/docs-count`. Revisa en el portal, en la Container App, que **no hay ningún secreto ni clave** en su configuración, solo las dos URLs. Explica por qué se usan dos identidades (la de sistema muere con la app y es ideal para permisos de esa app; la de usuario sobrevive y se comparte, por ejemplo, entre varias apps que descargan del mismo registro) y cuándo elegirías una u otra.
11. Añade, como segunda forma de consumir secretos, un secreto de Container Apps que referencie Key Vault por identidad (`secret { name = "api-token", key_vault_secret_id = ..., identity = "System" }`) e inyéctalo como variable de entorno `API_TOKEN`. Explica la diferencia entre que la plataforma inyecte el secreto y que la aplicación lo lea con el SDK (rotación, superficie de exposición, dependencia del código). Menciona el equivalente en App Service (referencias `@Microsoft.KeyVault(...)`).
12. En Log Analytics, consulta `AzureDiagnostics | where ResourceType == "VAULTS" | project TimeGenerated, OperationName, identity_claim_oid_g, CallerIPAddress, ResultSignature` y confirma que el `SecretGet` lo hizo el object ID de la identidad de la app. Guarda la consulta y el resultado.

**Parte D — Pipeline sin secreto: Service Principal con OIDC (2-3 h)**

13. Con el proveedor `azuread` crea `azuread_application` `sp-nortesur-deploy`, su `azuread_service_principal` y una `azuread_application_federated_identity_credential` con `issuer = "https://token.actions.githubusercontent.com"`, `audiences = ["api://AzureADTokenExchange"]` y `subject = "repo:<usuario>/<repo>:environment:prod"`. Asigna al SP el rol `Contributor` **solo sobre `rg-nortesur-seg`** y, además, `AcrPush` sobre el registro si construyes allí. Explica por qué el `subject` con `environment:prod` es más seguro que uno con `ref:refs/heads/main` y qué pasaría si pusieras un `subject` demasiado amplio.
14. Modifica el workflow del curso de CI/CD: `permissions: { id-token: write, contents: read }`, paso `azure/login` con `client-id`, `tenant-id` y `subscription-id` (guárdalos como *variables* del repositorio, no como secretos: son identificadores públicos; explica por qué no obstante muchos equipos los guardan como secretos), entorno `prod` con revisor obligatorio (gratuito en repositorios públicos), y despliegue con `az containerapp update --image ...`. Ejecuta el pipeline, aprueba y comprueba el nuevo `/version`.
15. Elimina el secreto de cliente del SP del curso de CI/CD (`az ad app credential delete`) y el secreto de GitHub que lo guardaba. Actualiza la tabla de la Parte A marcando esa fila como resuelta. Explica el flujo completo de tokens con un diagrama de secuencia.

**Parte E — Acceso humano: grupos, roles, rol personalizado, PIM y Conditional Access (3 h)**

16. Crea con `azuread_group` los grupos `gr-nortesur-lectores` y `gr-nortesur-operadores`. Crea un usuario de prueba `operador@<tu-inquilino>.onmicrosoft.com` (Entra ID Free lo permite) y añádelo a operadores. Asigna `Reader` sobre `rg-nortesur-seg` al grupo de lectores y, al de operadores, un **rol personalizado** `Operador de VM Nortesur` definido con `azurerm_role_definition`: `actions = ["Microsoft.Compute/virtualMachines/read", "Microsoft.Compute/virtualMachines/start/action", "Microsoft.Compute/virtualMachines/restart/action", "Microsoft.Compute/virtualMachines/deallocate/action", "Microsoft.Resources/subscriptions/resourceGroups/read"]`, `assignable_scopes` = el grupo de recursos. Explica `actions`, `notActions` y `dataActions`, y por qué se asigna a grupos y no a personas.
17. Despliega una VM B1s `vm-nortesur-hard` (sin IP pública si tienes el NVA del curso anterior; con IP pública restringida a tu IP si no) para las pruebas y el hardening. En una ventana privada, `az login` como `operador@...` y prueba: `az vm deallocate` (permitido), `az vm start` (permitido), `az vm delete` (denegado), `az keyvault secret show` (denegado), `az storage blob list --auth-mode login` (denegado). Guarda las salidas con los mensajes `AuthorizationFailed`. Comprueba en el registro de actividad quién hizo qué.
18. **PIM y Conditional Access (conceptual, requieren P2 y P1).** Lee la documentación y escribe: cómo configurarías el rol `Operador de VM Nortesur` como asignación *elegible* con activación de 4 horas, justificación y aprobación; qué política de Conditional Access exigirías (MFA para todos, bloqueo de autenticación legada, MFA reforzada para roles privilegiados, ubicación de confianza para el portal). Después implementa lo que sí puedes gratis: activa los **valores predeterminados de seguridad** de Entra ID (MFA para todos), registra MFA en tu cuenta y en la de `operador`, y explica qué pierdes respecto a Conditional Access.

**Parte F — Azure Policy, Defender for Cloud y seguridad de red (3-4 h)**

19. Crea con `azurerm_policy_set_definition` una iniciativa `Nortesur baseline` con tres definiciones integradas (búscalas por nombre con `az policy definition list --query "[?displayName=='...']"`): "Network interfaces should not have public IPs" (efecto `Deny`), "Require a tag on resources" con parámetro `tagName = propietario` (`Deny`) y "Allowed locations" con tu región (`Deny`). Asígnala **solo** a `rg-nortesur-seg` con `azurerm_resource_group_policy_assignment` (explica qué romperías si la asignaras a la suscripción mientras existe el NVA del curso anterior). Prueba: intenta crear una NIC con IP pública y un grupo de recursos sin etiqueta dentro del ámbito; guarda los errores `RequestDisallowedByPolicy`. Lanza `az policy state trigger-scan` y captura el estado de cumplimiento. Explica `Audit` frente a `Deny` frente a `DeployIfNotExists` y por qué en producción se empieza en `Audit`.
20. Abre Microsoft Defender for Cloud. Verifica que solo está activo el plan gratuito (Configuración del entorno → todos los planes en "Off" salvo la CSPM básica). Anota el Secure Score inicial, lista las 10 recomendaciones principales de tus recursos y corrige al menos tres con Terraform (típicas: cuenta de almacenamiento sin TLS 1.2 mínimo o con acceso público a blobs, Key Vault sin purge protection o sin registro, VM sin actualizaciones, NSG con SSH abierto). Captura el Secure Score al día siguiente y relaciona cada recomendación con su control del Microsoft cloud security benchmark.
21. Seguridad de red. Crea dos `azurerm_application_security_group` (`asg-web`, `asg-ops`), asocia la NIC de la VM a `asg-ops` y escribe reglas NSG que usen ASGs como origen y destino en vez de prefijos IP. Añade a la subred de la VM un service endpoint `Microsoft.Storage` y configura el firewall de `stnortesurdocs` con `default_action = "Deny"` y regla de red para esa subred; comprueba que `az storage blob list --auth-mode login` funciona desde la VM (identidad + red) y falla desde tu equipo aunque tengas el rol (red). Compara con el Private Endpoint del curso anterior y explica por qué la Container App (sin integración en VNet) deja de poder leer los blobs y qué harías en producción (integrar el entorno de Container Apps en una VNet y usar Private Endpoint). Documenta la decisión y revierte el firewall si quieres que `/docs-count` siga funcionando.

**Parte G — Hardening de la VM Linux (3 h)**

22. En `vm-nortesur-hard` (o `lab-so`) aplica y documenta con evidencia esta línea base: `sshd_config` con `PasswordAuthentication no`, `PermitRootLogin no`, `MaxAuthTries 3`, `AllowUsers <tu-usuario>` y reinicio del servicio; `fail2ban` con jail `sshd` (`maxretry = 3`, `bantime = 1h`) y una prueba de bloqueo desde otra máquina con clave incorrecta (`sudo fail2ban-client status sshd`); `unattended-upgrades` habilitado para actualizaciones de seguridad con `dpkg-reconfigure` y `unattended-upgrade --dry-run --debug`; `auditd` con reglas que vigilen `/etc/passwd`, `/etc/shadow`, `/etc/sudoers` y el uso de `sudo`, y una prueba con `ausearch -k <clave>`; `ufw` con política por defecto de denegar entrada y solo SSH permitido. Si es la VM de Azure, activa además la identidad administrada de la VM y usa `az login --identity` desde dentro para listar blobs: otra credencial menos.
23. Descarga el CIS Benchmark de Ubuntu (cuenta gratuita en CIS) y mapea cada medida de la línea base al control CIS correspondiente (número de sección, nivel 1 o 2, automatizado o manual). Elige cinco controles más del capítulo de SSH o de auditoría, evalúalos manualmente y decide si los aplicarías o no, con motivo. Ejecuta `lynis audit system` (paquete `lynis`, código abierto) y anota tu índice de endurecimiento antes y después. Explica qué es una imagen "golden" endurecida y cómo lo automatizarías (cloud-init, Ansible, Image Builder) en vez de hacerlo a mano en cada VM.

**Parte H — Caza de credenciales (2 h)**

24. Clona en un directorio temporal **todos** tus repositorios de la ruta (entregas, aplicación, Terraform, pipelines) y ejecuta en cada uno `gitleaks git -v --report-path gitleaks-<repo>.json` (todo el historial) y `gitleaks dir .` (estado actual). Revisa cada hallazgo: verdadero positivo o falso positivo, tipo, commit, si la credencial sigue siendo válida. Para cada verdadero positivo: **rota** la credencial primero (revoca la clave, regenera el secreto, cambia la contraseña) y después limpia el historial (`git filter-repo` o, si el repositorio es solo tuyo y pequeño, reescritura y `push --force` con el aviso al mentor) y añade un `.gitleaks.toml` con las exclusiones justificadas. Activa en GitHub, para tus repositorios públicos, el escaneo de secretos y la protección de inserción (gratuitos).
25. Documenta en `caza-de-credenciales.md`: número de hallazgos por repositorio, tipos, cuántos eran válidos, qué rotaste y qué aprendiste. **No incluyas los valores** ni fragmentos que permitan reconstruirlos. Añade `gitleaks` como paso previo al commit (hook `pre-commit`) en tu repositorio de entregas.

**Parte I — Opcional: identidad hacia PostgreSQL (1-2 h, solo si el coste lo permite)**

26. Si tu cuenta conserva las 750 h/mes gratuitas de Azure Database for PostgreSQL flexible (B1ms), crea un servidor con autenticación **solo de Entra ID** (`password_auth_enabled = false`), configúrate como administrador de Entra, conéctate con `psql` usando un token (`az account get-access-token --resource-type oss-rdbms`) en lugar de contraseña, crea un rol para la identidad administrada de la Container App (`pgaadauth_create_principal`) y haz que `/health` compruebe la conexión. Bórralo el mismo día. Si no, describe el flujo y compáralo con la autenticación de Entra ID a Azure SQL.

**Parte J — Limpieza (30 min)**

27. `terraform destroy`, `az group delete -n rg-nortesur-seg --yes`, elimina la App Registration del SP (`az ad app delete`), el usuario `operador` y los grupos si no los reutilizarás. Deja los valores predeterminados de seguridad activados. Al día siguiente captura Cost Management filtrado por `curso=seguridad-iam`.

### Resultado esperado

- `nortesur-seguridad/` con el Terraform completo (Key Vault, identidades, Container App, roles, política, VM, red) y el código de la aplicación ampliada con su Dockerfile y workflow.
- `laboratorio-seguridad.md` con el inventario de credenciales (antes y después), el modelo Zero Trust, equivalencias, evidencias de cada parte, consulta KQL de auditoría, mapeo CIS y decisiones.
- `caza-de-credenciales.md` sin valores sensibles.
- Ningún recurso vivo, ningún secreto de cliente en el SP, ninguna clave en GitHub, y captura de coste.

### Criterios de validación

- [ ] Parte A: el inventario es honesto y completo, y al final del curso cada fila está marcada como resuelta o con plan.
- [ ] Partes B y C: la aplicación responde en `/secret-check` y `/docs-count` sin ninguna clave ni cadena de conexión en su configuración; las claves de la cuenta de almacenamiento están deshabilitadas; la auditoría de Key Vault muestra el object ID de la identidad de la app; se explica correctamente sistema frente a usuario y plano de control frente a plano de datos.
- [ ] Parte D: el pipeline despliega con OIDC, el `subject` está acotado al entorno, y el secreto de cliente antiguo fue eliminado (evidencia).
- [ ] Parte E: el rol personalizado permite exactamente lo previsto y deniega el resto (salidas `AuthorizationFailed`); las asignaciones van a grupos; PIM y Conditional Access están correctamente descritos y se activaron los valores predeterminados de seguridad con MFA.
- [ ] Parte F: la iniciativa deniega las tres condiciones (errores capturados), el Secure Score mejoró con cambios en Terraform, y las reglas NSG usan ASGs; la comparación service endpoint / Private Endpoint / integración en VNet es correcta.
- [ ] Parte G: cada medida de hardening tiene evidencia de prueba (bloqueo de fail2ban, evento de auditd, dry-run de actualizaciones) y está mapeada a CIS.
- [ ] Parte H: `gitleaks` se ejecutó sobre todos los repositorios, los hallazgos están clasificados, las credenciales válidas se rotaron y no hay valores en la entrega.
- [ ] El estudiante puede explicar al mentor, sin notas, qué pasaría si se filtrara el código fuente completo de la aplicación y del Terraform (respuesta esperada: nada aprovechable).

## Entrega

En tu repositorio de entregas, carpeta `03-modulo-avanzado/05-seguridad-cloud-e-iam/`:

1. `nortesur-seguridad/` (Terraform, aplicación, Dockerfile, workflow), sin `tfstate` ni `.tfvars` sensibles.
2. `laboratorio-seguridad.md` con inventario, modelo Zero Trust, equivalencias, evidencias, KQL, mapeo CIS y decisiones.
3. `caza-de-credenciales.md` y `.gitleaks.toml`.
4. `capturas/` (oculta IDs completos de inquilino, suscripción y object IDs si lo prefieres; nunca valores de secretos).
5. `ENTREGA.md` con evaluación, checklist y uso de IA.

Nota sobre IA: nunca pegues en una herramienta de IA un secreto, un token, una salida de `gitleaks` con valores ni un `tfstate`. Úsala para entender mensajes `AuthorizationFailed`, definiciones de política o reglas de `auditd`, y verifica los nombres de roles y acciones contra la documentación: los modelos inventan permisos.

## Evaluación

1. **Conceptual.** Explica los tres principios de Zero Trust con un ejemplo de tu laboratorio para cada uno. ¿Qué principio incumple una cadena de conexión en una variable de entorno, aunque esté cifrada en reposo?
2. **Conceptual.** Diferencia Service Principal, Managed Identity de sistema, Managed Identity de usuario y App Registration. Para cada caso elige la identidad correcta: una Container App que lee Key Vault; tres apps que descargan del mismo ACR; GitHub Actions; una aplicación on-premises que llama a una API de Azure.
3. **Técnica.** Eres `Owner` de la suscripción y `az keyvault secret show` devuelve `Forbidden`. Explica por qué, qué rol necesitas y qué diferencia hay entre `actions` y `dataActions`.
4. **Situacional.** Un desarrollador pide `Contributor` en la suscripción "para poder desplegar". Diseña la alternativa con privilegio mínimo: ámbito, rol (integrado o personalizado), grupo, duración. ¿Qué cambiaría si tuvieras PIM?
5. **Técnica.** Describe el flujo OIDC de GitHub Actions a Azure paso a paso. ¿Qué comprueba Entra ID en el token? ¿Por qué ya no hay nada que rotar? ¿Qué riesgo introduce un `subject` como `repo:org/*`?
6. **Troubleshooting.** La Container App devuelve 500 en `/secret-check` con `DefaultAzureCredential failed to retrieve a token`. Da cuatro causas posibles (identidad no habilitada, rol no asignado o aún no propagado, URL incorrecta, firewall de Key Vault) y el comando o la consulta con que confirmarías cada una.
7. **Conceptual.** Compara que la plataforma inyecte un secreto de Key Vault como variable de entorno frente a que la aplicación lo lea con el SDK: rotación, exposición en volcados y logs, dependencia del código, latencia. ¿Cuándo usarías cada opción?
8. **Situacional.** Tienes que dar acceso de lectura a los blobs de Nortesur a un proveedor externo durante dos semanas. Compara: clave de cuenta, SAS, invitado B2B con rol RBAC, identidad del proveedor federada. ¿Cuál cumple mejor Zero Trust y qué desactivarías en la cuenta?
9. **Técnica.** Explica los efectos `Audit`, `Deny`, `DeployIfNotExists` y `Modify` de Azure Policy con un ejemplo cada uno. Tu iniciativa deniega IPs públicas en NICs: ¿qué pasa con las NICs que ya existían? ¿Cómo lo verías en el estado de cumplimiento?
10. **Situacional.** El Secure Score de Nortesur es 41 %. La dirección quiere "llegar al 80 % este mes". Explica qué mide realmente el Secure Score, por qué perseguir el número puede ser mala idea y cómo priorizarías las recomendaciones.
11. **Técnica.** Justifica cada medida de tu línea base de hardening (SSH sin contraseña, `fail2ban`, `unattended-upgrades`, `auditd`, `ufw`) frente a un ataque concreto, y di qué control CIS la cubre. ¿Qué medida de CIS nivel 2 decidiste **no** aplicar y por qué?
12. **Troubleshooting.** Desde la VM, `az storage blob list --auth-mode login` funciona, pero desde tu portátil, con el mismo usuario y rol, devuelve `AuthorizationFailure`. Explica la causa (red frente a identidad) y cómo distinguirías ambos tipos de error por el mensaje.
13. **Conceptual.** Service endpoint, Private Endpoint e integración de Container Apps en VNet: qué resuelve cada uno, qué cuesta y en qué orden los aplicarías para que la Container App lea blobs de una cuenta con acceso público deshabilitado.
14. **Situacional.** `gitleaks` encuentra una clave de cuenta de almacenamiento en un commit de hace ocho meses de un repositorio público. Ordena los pasos (rotar, revisar registros de acceso, limpiar historial, prevenir) y explica por qué limpiar el historial sin rotar no sirve de nada.
15. **Reflexión.** ¿Cuántas credenciales tenías en la Parte A y cuántas quedan? ¿Cuál fue más difícil de eliminar y qué harás distinto en el Proyecto Final desde el primer commit?

## Checklist final

Antes de continuar, deberías poder:

- [ ] Explicar Zero Trust y aplicarlo a decisiones de identidad, red y datos.
- [ ] Elegir entre Service Principal, Managed Identity de sistema y de usuario, y justificarlo.
- [ ] Diseñar RBAC con privilegio mínimo: ámbito, rol integrado o personalizado, grupos.
- [ ] Desplegar una aplicación que lee secretos, certificados y blobs por identidad, sin claves en configuración.
- [ ] Configurar OIDC entre GitHub Actions y Azure y eliminar los secretos de cliente.
- [ ] Explicar PIM y Conditional Access, su licencia y las alternativas gratuitas.
- [ ] Escribir y asignar una iniciativa de Azure Policy con `deny` y leer el cumplimiento.
- [ ] Interpretar el Secure Score y corregir recomendaciones con Terraform.
- [ ] Aplicar y probar una línea base de hardening en Linux y mapearla a CIS.
- [ ] Usar ASGs, service endpoints y Private Endpoints con criterio.
- [ ] Auditar tus repositorios con `gitleaks`, rotar credenciales y prevenir nuevas filtraciones.
- [ ] Tener la suscripción limpia y el coste del laboratorio documentado.

---

*Recursos verificados el 2026-09-27 (existencia y vigencia de las URLs mediante búsqueda web y, cuando el cupo de búsqueda se agotó, mediante los repositorios oficiales de la documentación). Las páginas de Microsoft Learn se enlazan en `es-es` cuando se confirmó la traducción; en el resto se indica cómo cambiar el idioma. Si un enlace falla, abre un issue en este repositorio.*
