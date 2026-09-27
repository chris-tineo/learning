# Administración de Azure

> Módulo: Intermedio · Curso 5 de 11 · Duración estimada: 40-60 horas (4-6 semanas) · Estado: ✅ Completo

## Objetivo

En Introducción a Cloud Computing creaste una VM y una cuenta de almacenamiento y las borraste. Eso es "usar" Azure. Este curso es sobre **administrar** Azure: organizar una suscripción en grupos de recursos con etiquetas y bloqueos, diseñar una red virtual con subredes y grupos de seguridad, desplegar máquinas que no tienen IP pública y se alcanzan a través de un host de salto, repartir tráfico con un balanceador, resolver nombres con Azure DNS, dar identidad a las máquinas para que lean secretos y escriban en almacenamiento sin contraseñas, controlar quién puede hacer qué con Entra ID y RBAC, vigilar todo con Azure Monitor y Log Analytics, y saber en todo momento cuánto cuesta.

Es el curso más largo del módulo y el que más se parece al trabajo diario de un administrador de nube o de un ingeniero de plataforma. Los conceptos son los mismos en AWS (cuentas, VPC, IAM, CloudWatch) y en GCP (proyectos, VPC, IAM, Cloud Monitoring); cambian los nombres, y al final del laboratorio harás la tabla de equivalencias.

Hay una regla que atraviesa todo el curso: **cada cosa que hagas en el portal, la repites con Azure CLI y la guardas en un script**. El portal sirve para entender; la CLI y, más adelante, Terraform, sirven para trabajar. Y otra: **el laboratorio se hace con coste casi cero**, apagando lo que no se usa y borrando todo al final.

**Antes de empezar** necesitas la cuenta de Azure con presupuesto y alertas del curso 8 del Módulo Básico, Administración de Linux (para operar las VMs) y Networking Intermedio (subnetting, DNS, balanceo, TLS).

### Al terminar este curso deberías poder

- Explicar la jerarquía inquilino → grupos de administración → suscripciones → grupos de recursos → recursos y decidir cómo organizar un entorno pequeño con etiquetas, convención de nombres y bloqueos.
- Diseñar y crear una red virtual con subredes, grupos de seguridad de red con reglas mínimas y una VM sin IP pública accesible por un host de salto.
- Desplegar VMs Linux con Azure CLI (tamaño, imagen, disco, identidad, cloud-init) y explicar qué se factura en cada estado de la VM.
- Poner un balanceador de carga delante de servidores web, explicar sondas de estado y reglas, y conocer su coste y sus alternativas.
- Crear zonas DNS públicas y privadas en Azure y resolver nombres de VMs dentro de la red virtual.
- Explicar qué es una identidad administrada y usarla desde una VM para leer un secreto de Key Vault y escribir en Blob Storage sin credenciales.
- Crear usuarios y grupos en Microsoft Entra ID y asignar roles RBAC con mínimo privilegio en el ámbito correcto, comprobándolo con el usuario de prueba.
- Configurar Log Analytics, el agente de Azure Monitor, consultas KQL básicas y una alerta de métrica con notificación.
- Crear presupuestos por grupo de recursos, analizar costes por etiqueta y dejar la suscripción sin recursos huérfanos.
- Escribir un script de Azure CLI que construya y destruya el entorno completo.

## Prerrequisitos

- Curso 8 del Módulo Básico: Introducción a Cloud Computing (cuenta de Azure con presupuesto y alertas, portal, Cloud Shell).
- Cursos 1 y 2 del Módulo Intermedio: Administración de Linux y Networking Intermedio.
- Curso 3: Bash y Python para Automatización (el script del laboratorio es Bash).
- Azure CLI instalada en tu equipo o en la VM `lab-so` (o Cloud Shell). Tu clave SSH pública.
- Cuenta de Azure: si tiene menos de 12 meses, las 750 h/mes de B1s son gratuitas; si no, el laboratorio cuesta unos pocos dólares (ver estimación en el laboratorio).

## Temario

Subscriptions · Resource Groups · Virtual Machines · Storage Accounts · VNets · Subnets · NSG · Load Balancers · Azure DNS · Managed Identities · Entra ID · RBAC · Key Vault · Azure Monitor · Log Analytics · Cost Management · Resource locks · Tags.

**Práctica:** construir y administrar un pequeño entorno empresarial.

## Recursos en español

### Rutas de aprendizaje AZ-104: Administrador de Azure — Microsoft Learn
- **URL:** Requisitos previos: https://learn.microsoft.com/es-es/training/paths/az-104-administrator-prerequisites/ · Identidades y gobernanza: https://learn.microsoft.com/es-es/training/paths/az-104-manage-identities-governance/ · Almacenamiento: https://learn.microsoft.com/es-es/training/paths/az-104-manage-storage/ · Cómputo: https://learn.microsoft.com/es-es/training/paths/az-104-manage-compute-resources/ · Redes virtuales: https://learn.microsoft.com/es-es/training/paths/az-104-manage-virtual-networks/ · Supervisión y copia de seguridad: https://learn.microsoft.com/es-es/training/paths/az-104-monitor-backup-resources/
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Seis rutas de aprendizaje con ejercicios (algunos en sandbox gratuito, otros sobre tu suscripción)
- **Duración aproximada:** 25-30 h en total. Para este curso: toda la de identidades y gobernanza, la de redes virtuales (salta VPN, ExpressRoute y Virtual WAN, que son del Módulo Avanzado), la de almacenamiento (cuentas, blobs, seguridad; salta Azure Files y File Sync), la de cómputo (VMs; salta App Service y contenedores, que se ven en cursos posteriores) y de la de supervisión los módulos de Azure Monitor, Log Analytics y alertas (Backup y Site Recovery se retoman en HA/DR)
- **Cubre:** Todo el temario.
- **Nivel:** Intermedio
- **Acceso:** Libre; cuenta Microsoft gratuita
- **Por qué lo recomiendo:** Es el material oficial de la certificación AZ-104 y coincide con el temario del curso casi punto por punto. Es el recurso principal. Si al terminar el curso quieres certificarte, habrás cubierto la mayor parte.

### Documentación de Azure en español — Microsoft Learn
- **URL:** Portal: https://learn.microsoft.com/es-es/azure/ · ¿Qué es Azure RBAC?: https://learn.microsoft.com/es-es/azure/role-based-access-control/overview · Roles integrados: https://learn.microsoft.com/es-es/azure/role-based-access-control/built-in-roles · Bloqueo de recursos: https://learn.microsoft.com/es-es/azure/azure-resource-manager/management/lock-resources · ¿Qué es Azure Resource Manager?: https://learn.microsoft.com/es-es/azure/azure-resource-manager/management/overview
- **Autor / organización:** Microsoft
- **Idioma:** Español (traducción oficial; si una frase suena rara, cambia `es-es` por `en-us` en la URL)
- **Tipo:** Documentación oficial
- **Duración aproximada:** Consulta continua; 2-3 h para las páginas indicadas
- **Cubre:** Resource Groups, RBAC, Resource locks, Tags, ARM.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** La sección "Documentación oficial" de este curso lista las páginas concretas de cada servicio. Estas cuatro son las que conviene leer enteras antes de tocar nada: explican el modelo de control (ARM, ámbitos, roles, bloqueos) sobre el que se apoya todo lo demás.

### Preparación para AZ-104 (Exam Readiness Zone) — Microsoft Learn
- **URL:** Episodio 1 de 5, identidades y gobernanza: https://learn.microsoft.com/es-es/shows/exam-readiness-zone/preparing-for-az-104-manage-azure-identities-and-governance-1-of-5 (los otros cuatro episodios están enlazados desde la misma página)
- **Autor / organización:** Microsoft
- **Idioma:** Vídeo en inglés con página y subtítulos en español
- **Tipo:** Serie de vídeos de repaso
- **Duración aproximada:** 5 vídeos de 30-45 min
- **Cubre:** Todo el temario, organizado por áreas del examen.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Resume cada área en media hora con los puntos que suelen confundirse (ámbitos de RBAC, tipos de bloqueo, SKUs). Úsalo como repaso al final de cada bloque, no como primera explicación.

## Recursos en inglés

### AZ-104 Azure Administrator Study Cram y materiales — John Savill's Technical Training
- **URL:** Repositorio con el vídeo, la lista de reproducción de estudio y la pizarra en PDF/PNG: https://github.com/johnthebrit/CertificationMaterials · Lista de reproducción AZ-104: https://youtube.com/playlist?list=PLlVtbbG169nGlGPWs9xaLKT1KfwqREHbs
- **Autor / organización:** John Savill (Microsoft; divulgador independiente)
- **Idioma:** Inglés (subtítulos automáticos)
- **Tipo:** Vídeo largo de repaso + lista de vídeos por tema + pizarra
- **Duración aproximada:** ~4 h el Study Cram; la lista de reproducción tiene vídeos de 20-60 min por servicio
- **Cubre:** Todo el temario, con especial profundidad en redes, identidad y gobernanza.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** John Savill dibuja la arquitectura completa de una suscripción bien organizada y explica el "por qué" de cada pieza. Sus vídeos individuales de la lista (Managed Identities, NSGs, Load Balancer, Azure Monitor) son el mejor complemento cuando un tema de Microsoft Learn no termina de encajar.

### Azure CLI: documentación y referencia — Microsoft Learn
- **URL:** Portal: https://learn.microsoft.com/en-us/cli/azure/ · Primeros pasos: https://learn.microsoft.com/en-us/cli/azure/get-started-with-azure-cli · Instalación en Linux: https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-linux · Consultas con `--query` (JMESPath): https://learn.microsoft.com/en-us/cli/azure/use-azure-cli-successfully-query · Autenticación con identidad administrada: https://learn.microsoft.com/en-us/cli/azure/authenticate-azure-cli-managed-identity · Referencia A-Z de comandos: https://learn.microsoft.com/en-us/cli/azure/reference-index
- **Autor / organización:** Microsoft
- **Idioma:** Inglés (existe versión `es-es`)
- **Tipo:** Documentación oficial
- **Duración aproximada:** 2 h de lectura inicial; consulta constante durante el laboratorio
- **Cubre:** Todo el temario desde la línea de comandos.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** El laboratorio exige repetir todo por CLI y guardarlo en un script. Aprende a usar `az <grupo> <comando> --help`, `--query` y `--output table` desde el primer día; te ahorrará horas y es la base de la automatización que viene en Terraform y CI/CD.

### Tutorial: usar una identidad administrada desde una VM Linux para acceder a recursos, y Key Vault desde una VM — Microsoft Learn
- **URL:** Identidad administrada en VM Linux (obtiene un token y llama a ARM): https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/tutorial-linux-managed-identities-vm-access · Key Vault desde una VM con Python: https://learn.microsoft.com/en-us/azure/key-vault/general/tutorial-python-virtual-machine
- **Autor / organización:** Microsoft
- **Idioma:** Inglés (existe versión `es-es`)
- **Tipo:** Tutoriales paso a paso
- **Duración aproximada:** 60-90 min
- **Cubre:** Managed Identities, Key Vault, RBAC.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Son los dos tutoriales oficiales que están detrás de la parte de identidad del laboratorio. El primero enseña a pedir un token al servicio de metadatos (IMDS) con `curl`, que es lo que hace por dentro cualquier SDK; el segundo lo usa desde Python, que reutilizarás en el curso de IA aplicada.

### Guía de estudio AZ-104 y Cloud Adoption Framework (solo referencia) — Microsoft Learn
- **URL:** Guía de estudio del examen: https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-104 · Cloud Adoption Framework: https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/overview
- **Autor / organización:** Microsoft
- **Idioma:** Inglés
- **Tipo:** Guía de estudio y marco de referencia
- **Duración aproximada:** 30 min la guía; el CAF solo para hojear la metodología "Ready" (zonas de aterrizaje) y "Govern"
- **Cubre:** Mapa del temario; organización de suscripciones y gobernanza a escala.
- **Nivel:** Intermedio (la guía) y avanzado (el CAF)
- **Acceso:** Libre
- **Por qué lo recomiendo:** La guía de estudio es la lista de habilidades oficial: úsala como checklist de lo que sabes y no sabes. El CAF es lo que las empresas grandes usan para organizar decenas de suscripciones; aquí solo hace falta saber que existe y qué es una zona de aterrizaje. Se retoma en Arquitectura Cloud Avanzada.

## Documentación oficial

Todas las URLs admiten `es-es` en lugar de `en-us`.

- **Gobernanza:** grupos de administración https://learn.microsoft.com/es-es/azure/governance/management-groups/overview · etiquetas https://learn.microsoft.com/es-es/azure/azure-resource-manager/management/tag-resources · bloqueos https://learn.microsoft.com/es-es/azure/azure-resource-manager/management/lock-resources · grupos de recursos por CLI https://learn.microsoft.com/es-es/azure/azure-resource-manager/management/manage-resource-groups-cli · reglas de nombres https://learn.microsoft.com/es-es/azure/azure-resource-manager/management/resource-name-rules · límites de suscripción https://learn.microsoft.com/es-es/azure/azure-resource-manager/management/azure-subscription-service-limits · Azure Policy (solo lectura) https://learn.microsoft.com/es-es/azure/governance/policy/overview
- **Red:** VNet https://learn.microsoft.com/es-es/azure/virtual-network/virtual-networks-overview · inicio rápido VNet https://learn.microsoft.com/es-es/azure/virtual-network/quickstart-create-virtual-network · NSG https://learn.microsoft.com/es-es/azure/virtual-network/network-security-groups-overview · filtrar tráfico con NSG https://learn.microsoft.com/es-es/azure/virtual-network/tutorial-filter-network-traffic · IPs públicas y SKUs https://learn.microsoft.com/es-es/azure/virtual-network/ip-services/public-ip-addresses · Bastion (para entender por qué no lo usamos) https://learn.microsoft.com/es-es/azure/bastion/bastion-overview
- **Cómputo:** VM Linux por CLI https://learn.microsoft.com/es-es/azure/virtual-machines/linux/quick-create-cli · administrar VMs por CLI https://learn.microsoft.com/es-es/azure/virtual-machines/linux/tutorial-manage-vm · estados y facturación https://learn.microsoft.com/es-es/azure/virtual-machines/states-billing · familia B https://learn.microsoft.com/es-es/azure/virtual-machines/sizes/general-purpose/b-family
- **Load Balancer:** qué es https://learn.microsoft.com/es-es/azure/load-balancer/load-balancer-overview · SKUs (Basic retirado en septiembre de 2025) https://learn.microsoft.com/es-es/azure/load-balancer/skus · inicio rápido Standard por CLI https://learn.microsoft.com/es-es/azure/load-balancer/quickstart-load-balancer-standard-public-cli
- **DNS:** Azure DNS https://learn.microsoft.com/es-es/azure/dns/dns-overview · zonas privadas https://learn.microsoft.com/es-es/azure/dns/private-dns-overview · zona pública por CLI https://learn.microsoft.com/es-es/azure/dns/dns-getstarted-cli · zona privada por CLI https://learn.microsoft.com/es-es/azure/dns/private-dns-getstarted-cli
- **Almacenamiento:** cuentas https://learn.microsoft.com/es-es/azure/storage/common/storage-account-overview · crear cuenta https://learn.microsoft.com/es-es/azure/storage/common/storage-account-create · autorizar blobs con Entra ID https://learn.microsoft.com/es-es/azure/storage/blobs/authorize-access-azure-active-directory · asignar rol de datos https://learn.microsoft.com/es-es/azure/storage/blobs/assign-azure-role-data-access · blobs por CLI https://learn.microsoft.com/es-es/azure/storage/blobs/storage-quickstart-blobs-cli
- **Identidad:** qué es Entra ID https://learn.microsoft.com/es-es/entra/fundamentals/what-is-entra · crear usuarios https://learn.microsoft.com/es-es/entra/fundamentals/how-to-create-delete-users · grupos https://learn.microsoft.com/es-es/entra/fundamentals/how-to-manage-groups · identidades administradas https://learn.microsoft.com/es-es/entra/identity/managed-identities-azure-resources/overview · configurarlas en VMs https://learn.microsoft.com/es-es/entra/identity/managed-identities-azure-resources/how-to-configure-managed-identities
- **RBAC:** asignar roles por CLI https://learn.microsoft.com/es-es/azure/role-based-access-control/role-assignments-cli · por portal https://learn.microsoft.com/es-es/azure/role-based-access-control/role-assignments-portal · buenas prácticas https://learn.microsoft.com/es-es/azure/role-based-access-control/best-practices · roles de Azure frente a roles de Entra https://learn.microsoft.com/es-es/azure/role-based-access-control/rbac-and-directory-admin-roles
- **Key Vault:** qué es https://learn.microsoft.com/es-es/azure/key-vault/general/overview · conceptos https://learn.microsoft.com/es-es/azure/key-vault/general/basic-concepts · RBAC en Key Vault https://learn.microsoft.com/es-es/azure/key-vault/general/rbac-guide · secretos por CLI https://learn.microsoft.com/es-es/azure/key-vault/secrets/quick-create-cli
- **Monitor:** qué es Azure Monitor https://learn.microsoft.com/es-es/azure/azure-monitor/fundamentals/overview · agente de Azure Monitor https://learn.microsoft.com/es-es/azure/azure-monitor/agents/azure-monitor-agent-overview · instalar y gestionar el agente https://learn.microsoft.com/es-es/azure/azure-monitor/agents/azure-monitor-agent-manage · reglas de recopilación (DCR) https://learn.microsoft.com/es-es/azure/azure-monitor/data-collection/data-collection-rule-overview · recopilar datos de VMs https://learn.microsoft.com/es-es/azure/azure-monitor/vm/data-collection · crear área de trabajo https://learn.microsoft.com/es-es/azure/azure-monitor/logs/quick-create-workspace · primeras consultas KQL https://learn.microsoft.com/es-es/azure/azure-monitor/logs/get-started-queries · alertas https://learn.microsoft.com/es-es/azure/azure-monitor/alerts/alerts-overview · tutorial alerta de métrica https://learn.microsoft.com/es-es/azure/azure-monitor/alerts/tutorial-metric-alert · costes de Log Analytics https://learn.microsoft.com/es-es/azure/azure-monitor/logs/cost-logs
- **Costes:** análisis de costes https://learn.microsoft.com/es-es/azure/cost-management-billing/costs/quick-acm-cost-analysis · presupuestos https://learn.microsoft.com/es-es/azure/cost-management-billing/costs/tutorial-acm-create-budgets · herencia de etiquetas https://learn.microsoft.com/es-es/azure/cost-management-billing/costs/enable-tag-inheritance · evitar cargos en cuenta gratuita https://learn.microsoft.com/es-es/azure/cost-management-billing/manage/avoid-charges-free-account · calculadora https://azure.microsoft.com/es-es/pricing/calculator/

## Ruta recomendada de estudio

El curso se hace en **cinco bloques**, cada uno de teoría (Microsoft Learn) seguida de su parte del laboratorio. No intentes leer todo primero.

1. **Bloque 1, gobernanza (semana 1).** Ruta "Requisitos previos" (1 h) y ruta "Identidades y gobernanza": módulos de suscripciones, grupos de recursos, etiquetas, bloqueos y Azure Policy (3 h). Leer las cuatro páginas de la ficha de documentación en español (1 h). Ver la primera hora del Study Cram de John Savill (jerarquía y gobernanza). **Hacer la Parte A del laboratorio.**
2. **Bloque 2, red y cómputo (semanas 1-2).** Ruta "Redes virtuales": VNets, subredes, NSGs, IPs públicas, DNS y Load Balancer (5 h; salta VPN, ExpressRoute y Virtual WAN). Ruta "Cómputo": máquinas virtuales, discos, tamaños, disponibilidad (3 h). Leer "estados y facturación" y "SKUs de Load Balancer". **Hacer las Partes B, C, D y E.**
3. **Bloque 3, almacenamiento e identidad (semanas 2-3).** Ruta "Almacenamiento": cuentas, blobs, seguridad y acceso con Entra ID (3 h). Ruta "Identidades y gobernanza": módulos de Entra ID, usuarios y grupos, RBAC (3 h). Leer "¿Qué es Azure RBAC?", "roles integrados", "identidades administradas" y "RBAC en Key Vault". Hacer el tutorial de identidad administrada en VM Linux (1 h). **Hacer las Partes F, G y H.**
4. **Bloque 4, monitorización (semana 3-4).** Ruta "Supervisión": Azure Monitor, Log Analytics, agente, alertas (3 h; salta Backup y Site Recovery). Leer "agente de Azure Monitor", "reglas de recopilación", "primeras consultas KQL" y "costes de Log Analytics" (1,5 h). **Hacer la Parte I.**
5. **Bloque 5, costes, limpieza y consolidación (semana 4).** Leer análisis de costes, presupuestos y herencia de etiquetas (1 h). **Hacer las Partes J y K.** Ver los cinco vídeos de Exam Readiness Zone como repaso (3 h) y repasar la guía de estudio AZ-104 marcando lo que sabes hacer sin mirar.
6. **Responder la evaluación** y **revisar el checklist**.

Si vas justo de tiempo: la ruta de identidades y gobernanza, la de redes (sin VPN) y las Partes A a C, F a H y J del laboratorio son obligatorias; el Load Balancer y DNS público pueden hacerse a nivel conceptual.

## Laboratorio

### Objetivo

Construir y administrar el entorno de una pequeña empresa ficticia (**Acme**) en tu suscripción: tres grupos de recursos por función con etiquetas y bloqueos, una red con dos subredes y NSGs, un host de salto y un servidor web sin IP pública, un balanceador (o su alternativa), DNS privado, almacenamiento y Key Vault accedidos por identidad administrada, un usuario de operaciones con permisos mínimos, monitorización con alerta y presupuesto por grupo. Todo por portal la primera vez y por CLI en un script reproducible. Al final, destruir el entorno y demostrar que no queda coste.

### Requisitos

- Azure CLI 2.60 o superior (`az version`), sesión iniciada (`az login`) y suscripción seleccionada (`az account show`).
- Clave SSH pública. Terminal Bash (equipo, `lab-so` o Cloud Shell).
- Presupuesto de suscripción del curso 8 activo. Crearás otro por grupo de recursos.
- Documenta en `laboratorio-azure.md` y guarda todos los comandos en `lab-azure.sh` (con variables al principio y `set -euo pipefail`). Las capturas del portal deben mostrar tu usuario o suscripción.

> **Sobre el coste.** Estimación si trabajas unas 30 horas repartidas en 3-4 semanas y **desasignas las VMs al terminar cada sesión**: dos VMs B1s (~0,01 USD/h cada una; gratuitas 750 h/mes si tu cuenta tiene menos de 12 meses), dos discos Standard HDD de 30 GB (~1,5 USD/mes cada uno, prorrateado), una IP pública Standard estática (~3,65 USD/mes, prorrateado; **cobra aunque la VM esté apagada**), zona DNS privada (~0,50 USD/mes), Load Balancer Standard (~0,025 USD/h: úsalo solo unas horas y bórralo el mismo día), Log Analytics (primeros 5 GB/mes gratis; una VM genera megabytes), una alerta de métrica (~0,10 USD/mes), Key Vault y Storage (céntimos). Total esperado: **3-8 USD** en todo el curso; si dejas las VMs encendidas un mes, 15-20 USD. Lo que **no** usamos por caro: Azure Bastion (~0,19 USD/h), VPN Gateway, Application Gateway, Front Door. Regla: presupuesto por grupo antes de crear nada, `az vm deallocate` al acabar cada sesión, `az group delete` al final.

### Instrucciones

**Parte A — Gobernanza: suscripción, grupos, etiquetas, bloqueos (2 h)**

1. Explora la jerarquía: `az account show`, `az account list --output table`, `az account management-group list` (si no tienes permiso, explica qué es un grupo de administración y para qué lo usaría Acme con varias suscripciones). En el portal, Entra ID → Información general: anota inquilino y dominio `*.onmicrosoft.com`. Explica la diferencia entre inquilino (identidad) y suscripción (facturación y recursos).
2. Define en `laboratorio-azure.md` la **convención de nombres y etiquetas** de Acme (basada en las reglas de nombres de Azure): `rg-acme-<función>-<entorno>`, `vnet-acme-<entorno>`, `snet-<rol>`, `nsg-<rol>`, `vm-<rol>-<nn>`, `st<acme><sufijo>`, `kv-acme-<sufijo>`, `log-acme-<entorno>`. Etiquetas obligatorias: `env`, `owner`, `cost-center`, `course=azure-admin`.
3. Crea tres grupos en tu región (portal para el primero, CLI para el resto):
   ```bash
   LOC=<tu-region>; OWNER=<tu-usuario>
   for RG in rg-acme-net-dev rg-acme-app-dev rg-acme-shared-dev; do
     az group create -n $RG -l $LOC --tags env=dev owner=$OWNER cost-center=ops course=azure-admin
   done
   az group list --query "[?tags.course=='azure-admin'].{rg:name, env:tags.env}" -o table
   ```
   Explica por qué separar red, aplicación y servicios compartidos, y qué alternativa habría (un grupo por entorno).
4. Bloqueo: `az lock create -n lock-shared -g rg-acme-shared-dev --lock-type CanNotDelete`. Intenta `az group delete -n rg-acme-shared-dev --yes` y captura el error. Explica `CanNotDelete` frente a `ReadOnly` y un efecto secundario sorprendente de `ReadOnly` (por ejemplo, sobre cuentas de almacenamiento o listados de claves).
5. Presupuesto: en Cost Management crea un presupuesto de **5 USD/mes** con ámbito el grupo `rg-acme-app-dev` y alertas al 50 %, 80 % y 100 %. Captura. Repite por CLI con `az consumption budget create` (o documenta si tu suscripción no lo admite) y explica por qué el presupuesto no detiene el gasto.

**Parte B — Red: VNet, subredes, NSGs (2-3 h)**

6. Diseña la red en papel antes de crearla: `vnet-acme-dev` 10.10.0.0/16, `snet-web` 10.10.1.0/24, `snet-mgmt` 10.10.2.0/24. Explica cuántas IPs útiles tiene cada subred y por qué Azure reserva 5 por subred.
7. Crea VNet y subredes (portal primero, luego CLI en `rg-acme-net-dev`):
   ```bash
   az network vnet create -g rg-acme-net-dev -n vnet-acme-dev --address-prefix 10.10.0.0/16 \
     --subnet-name snet-web --subnet-prefix 10.10.1.0/24 --tags env=dev owner=$OWNER course=azure-admin
   az network vnet subnet create -g rg-acme-net-dev --vnet-name vnet-acme-dev -n snet-mgmt --address-prefix 10.10.2.0/24
   ```
8. Crea dos NSGs y asócialos a las subredes: `nsg-web` permite TCP 80 desde `Internet` (prioridad 200) y TCP 22 solo desde `10.10.2.0/24` (210); `nsg-mgmt` permite TCP 22 solo desde **tu IP pública** (`curl -s ifconfig.me`) (200). Lista las reglas por defecto (`az network nsg rule list --include-default`) y explica `AllowVnetInBound`, `AllowAzureLoadBalancerInBound` y `DenyAllInBound`. Explica NSG en subred frente a NSG en NIC y en qué orden se evalúan.

**Parte C — Cómputo: host de salto y servidor web (3 h)**

9. Crea la IP pública Standard estática `pip-jump-dev` y la VM de salto en `rg-acme-app-dev`, subred `snet-mgmt`, tamaño `Standard_B1s`, Ubuntu LTS, disco `Standard_LRS`, autenticación por clave, identidad administrada asignada por el sistema:
   ```bash
   SUBNET_MGMT=$(az network vnet subnet show -g rg-acme-net-dev --vnet-name vnet-acme-dev -n snet-mgmt --query id -o tsv)
   az network public-ip create -g rg-acme-app-dev -n pip-jump-dev --sku Standard --allocation-method Static
   az vm create -g rg-acme-app-dev -n vm-jump-01 --image Ubuntu2404 --size Standard_B1s \
     --subnet $SUBNET_MGMT --public-ip-address pip-jump-dev --nsg "" --storage-sku Standard_LRS \
     --admin-username azureuser --ssh-key-values ~/.ssh/id_ed25519.pub --assign-identity [system] \
     --tags env=dev owner=$OWNER course=azure-admin
   ```
   Si `Ubuntu2404` no existe como alias en tu CLI, usa `az vm image list --publisher Canonical --output table` para elegir. Explica por qué `--nsg ""` (el NSG ya está en la subred) y qué crea `az vm create` además de la VM.
10. Crea `vm-web-01` en `snet-web` **sin IP pública** (`--public-ip-address ""`), con identidad administrada y un `cloud-init.yaml` que instale nginx y escriba en `/var/www/html/index.html` el nombre de host (`--custom-data cloud-init.yaml`). Explica qué es cloud-init y por qué es preferible a entrar por SSH a instalar cosas.
11. Accede a `vm-web-01` a través del host de salto con `ssh -J azureuser@<ip-jump> azureuser@10.10.1.4` (o configura `ProxyJump` en `~/.ssh/config`). Dentro: `curl localhost`, `curl -s -H Metadata:true "http://169.254.169.254/metadata/instance/compute?api-version=2021-02-01" | python3 -m json.tool | head -30`. Desde tu equipo, `curl http://10.10.1.4` no puede funcionar: explica por qué. Comprueba desde `vm-jump-01` que sí.
12. Estados y facturación: `az vm deallocate`, `az vm get-instance-view --query instanceView.statuses[1].displayStatus`, `az vm start`. Comprueba que la IP pública **no** cambió (estática) y explica qué sigue costando con la VM desasignada (disco, IP). **Hábito del curso: desasigna ambas VMs al acabar cada sesión.** Añade al script una función `apagar_todo`.

**Parte D — Load Balancer (1-2 h, acotado en coste)**

13. Lee "SKUs de Load Balancer": el SKU Basic fue retirado en septiembre de 2025 y no se puede crear. **Opción 1 (recomendada, ~0,10 USD):** crea un Load Balancer **Standard** público en `rg-acme-app-dev` con IP pública Standard nueva, backend pool con `vm-web-01`, sonda HTTP a `/` en el puerto 80 y regla 80 → 80. Comprueba `curl http://<ip-lb>` varias veces. Detén nginx en la VM (`sudo systemctl stop nginx`) y observa cuánto tarda la sonda en marcar el backend como no saludable y qué devuelve `curl`. **Bórralo el mismo día** (`az network lb delete` y la IP pública). **Opción 2 (gratuita):** si prefieres no crear el LB, configura nginx en `vm-jump-01` como proxy inverso con `upstream` hacia `vm-web-01` y explica en qué se parece y en qué no a un balanceador de capa 4.
14. En cualquiera de las dos opciones, explica: sonda de estado, regla de balanceo, SNAT de salida (por qué una VM sin IP pública detrás de un LB Standard **no** tiene salida a Internet sin regla de salida o NAT Gateway) y la diferencia entre Load Balancer (capa 4) y Application Gateway (capa 7, más caro, del Módulo Avanzado).

**Parte E — Azure DNS (1 h)**

15. Zona privada: crea `acme.internal` en `rg-acme-net-dev`, enlázala a la VNet con **registro automático** y comprueba desde `vm-jump-01` que `dig vm-web-01.acme.internal` y `dig vm-jump-01.acme.internal` resuelven a las IPs privadas. Muestra `resolvectl status` en la VM y explica quién responde (168.63.129.16) y qué es esa IP.
16. Zona pública (opcional, ~0,50 USD/mes prorrateado): crea `lab-acme-<tusufijo>.com` (no hace falta ser dueño del dominio para crear la zona), añade un registro A y consulta **directamente a los servidores de nombres de Azure** que te asigna la zona (`dig @ns1-XX.azure-dns.com www.lab-acme-<sufijo>.com`). Explica por qué la resolución "normal" no funciona (delegación en el registrador) y borra la zona.

**Parte F — Storage Account con identidad administrada (1,5 h)**

17. En `rg-acme-shared-dev` crea `stacme<sufijo>` (Standard_LRS, StorageV2, acceso público a blobs deshabilitado, `--allow-shared-key-access false` si tu CLI lo admite) con un contenedor `backups`. Explica qué deshabilita cada opción y por qué la clave de cuenta es un riesgo.
18. Asigna a la identidad de `vm-web-01` el rol **Storage Blob Data Contributor** con ámbito **el contenedor** (o la cuenta si tu CLI no permite el ámbito de contenedor):
    ```bash
    PRINCIPAL=$(az vm show -g rg-acme-app-dev -n vm-web-01 --query identity.principalId -o tsv)
    SCOPE=$(az storage account show -g rg-acme-shared-dev -n stacme<sufijo> --query id -o tsv)/blobServices/default/containers/backups
    az role assignment create --assignee-object-id $PRINCIPAL --assignee-principal-type ServicePrincipal \
      --role "Storage Blob Data Contributor" --scope $SCOPE
    ```
19. En `vm-web-01` instala Azure CLI desde el repositorio de Microsoft, ejecuta `az login --identity` y sube un archivo: `az storage blob upload --auth-mode login --account-name stacme<sufijo> -c backups -f /etc/hostname -n hostname-$(date +%F).txt`. Intenta listar **otro** contenedor o borrar la cuenta y explica por qué falla. Repite la subida sin CLI, pidiendo el token a IMDS con `curl` y llamando a la API REST de Blob (sigue el tutorial de identidad administrada). Explica qué ha pasado con las contraseñas en todo este proceso.

**Parte G — Entra ID y RBAC con mínimo privilegio (1,5 h)**

20. Crea el usuario `ana.ops@<tuinquilino>.onmicrosoft.com` y el grupo de seguridad `grp-acme-ops-dev` con Ana como miembro (portal y luego `az ad user create`, `az ad group create`, `az ad group member add`). Explica la diferencia entre un rol de Entra ID (por ejemplo, Administrador de usuarios) y un rol de Azure RBAC (por ejemplo, Colaborador).
21. Asigna al **grupo** el rol **Virtual Machine Contributor** con ámbito `rg-acme-app-dev` y **Reader** con ámbito `rg-acme-net-dev`. Nada en `rg-acme-shared-dev`. Explica por qué se asigna al grupo y no al usuario, y por qué no basta con "Contributor en la suscripción".
22. Abre una ventana privada, entra como Ana (cambia la contraseña inicial) y comprueba: puede iniciar y detener `vm-web-01`; **no** puede crear una VM nueva (le falta permiso sobre la red: explica qué acción concreta falla); no ve `rg-acme-shared-dev`; no puede borrar el grupo `rg-acme-app-dev`. Captura cada resultado. Revisa desde tu usuario el Registro de actividad y localiza las acciones de Ana.
23. Ejecuta `az role assignment list --all --assignee ana.ops@... --include-groups -o table` y `az role definition list --name "Virtual Machine Contributor" --query "[].permissions[].actions"` y comenta tres acciones que incluye y una que no.

**Parte H — Key Vault (1 h)**

24. Crea `kv-acme-<sufijo>` en `rg-acme-shared-dev` con modelo de permisos RBAC (`--enable-rbac-authorization true`). Asígnate **Key Vault Secrets Officer** sobre el vault y crea el secreto `db-password` con un valor generado (`openssl rand -base64 24`). Explica por qué no ves el secreto en el portal hasta tener el rol de datos aunque seas propietario de la suscripción.
25. Asigna a la identidad de `vm-web-01` **Key Vault Secrets User** sobre **ese secreto** (ámbito del recurso `.../secrets/db-password`) y léelo desde la VM: `az keyvault secret show --vault-name kv-acme-<sufijo> -n db-password --query value -o tsv`. Intenta crear otro secreto desde la VM y explica el error. Muestra en el portal el registro de acceso o los eventos de diagnóstico. Explica soft-delete y protección contra purga, y qué implica para el nombre del vault cuando lo borres.

**Parte I — Azure Monitor y Log Analytics (2-3 h)**

26. Crea el área de trabajo `log-acme-dev` en `rg-acme-shared-dev` (`az monitor log-analytics workspace create`). Explica el modelo de coste (5 GB/mes gratis, retención 31 días incluida) y por qué en una empresa se controla qué se ingiere.
27. Instala el **agente de Azure Monitor** en `vm-web-01` y crea una **regla de recopilación de datos** que envíe Syslog (facilidades `auth`, `daemon`, `syslog`) y contadores de rendimiento (CPU, memoria, disco) al área de trabajo. Hazlo primero desde el portal (Supervisión → Reglas de recopilación de datos o "Insights" de la VM) y anota el equivalente CLI (`az vm extension set --name AzureMonitorLinuxAgent --publisher Microsoft.Azure.Monitor` y `az monitor data-collection rule create` con un JSON). Comprueba con `az vm extension list`.
28. Tras 10-15 minutos, en Logs ejecuta y explica: `Heartbeat | summarize max(TimeGenerated) by Computer`, `Perf | where CounterName == "% Processor Time" | summarize avg(CounterValue) by bin(TimeGenerated, 5m)`, `Syslog | where Facility == "auth" | project TimeGenerated, SyslogMessage | take 20` (genera entradas entrando por SSH). Guarda las consultas en `consultas.kql`.
29. Crea un **grupo de acciones** con tu correo y una **alerta de métrica**: `Percentage CPU` de `vm-web-01` mayor de 80 % durante 5 minutos, gravedad 2. Provoca la carga desde la VM (`yes > /dev/null &` un par de veces, o `stress-ng --cpu 1 --timeout 10m` tras instalarlo), espera el correo, captura, y detén la carga (`kill %1 %2`). Anota cuánto tardó en dispararse y en resolverse, y explica ventana de agregación y frecuencia de evaluación. Crea también la alerta por CLI (`az monitor metrics alert create`).
30. Consulta el **Registro de actividad** de la suscripción por CLI: `az monitor activity-log list -g rg-acme-app-dev --offset 7d --query "[].{hora:eventTimestamp, quien:caller, que:operationName.localizedValue}" -o table`. Localiza las acciones de Ana y las tuyas.

**Parte J — Cost Management y limpieza total (1,5 h, más una comprobación al día siguiente)**

31. En Análisis de costes: agrupa por **etiqueta `env`** y por **grupo de recursos**; filtra por `course=azure-admin`; cambia la granularidad a diaria. Captura y anota qué recurso ha costado más y por qué (probablemente la IP pública o los discos, no las VMs). Explica por qué las etiquetas de los grupos no se heredan a los recursos salvo que actives la herencia.
32. Limpieza ordenada, en el script como función `destruir_todo`: quitar el bloqueo (`az lock delete`), borrar los tres grupos (`az group delete --yes --no-wait`), esperar y comprobar `az group list -o table` y `az resource list -o table`; purgar el Key Vault (`az keyvault purge`) o explicar por qué queda 90 días reservado; borrar el usuario Ana y el grupo; borrar el presupuesto. Comprueba que **no queda ninguna IP pública ni disco** huérfano (`az network public-ip list`, `az disk list`).
33. Al día siguiente, captura el coste acumulado del curso en Análisis de costes y anótalo junto a tu estimación inicial. Si difieren, explica por qué.

**Parte K — Script y equivalencias (1-2 h)**

34. Deja `lab-azure.sh` completo: variables al inicio, funciones `crear_gobernanza`, `crear_red`, `crear_computo`, `crear_dns`, `crear_storage_identidad`, `crear_rbac`, `crear_keyvault`, `crear_monitor`, `apagar_todo`, `destruir_todo`, y un `case "$1"` para ejecutar cada una. Ejecuta al menos `crear_gobernanza`, `crear_red` y `destruir_todo` de principio a fin en un grupo con sufijo distinto para demostrar que es reproducible, y pega la salida. Explica qué tiene de frágil un script así (orden, idempotencia, estado) y por qué el curso 8 lo sustituye por Terraform.
35. Completa una tabla **Azure ↔ AWS ↔ GCP** con al menos 12 filas: suscripción, grupo de recursos, VNet, subred, NSG, IP pública, VM, disco, Load Balancer, DNS, Storage Account/Blob, identidad administrada, Entra ID, RBAC, Key Vault, Log Analytics, alertas, presupuestos, bloqueos, etiquetas.

### Resultado esperado

- `laboratorio-azure.md` con las partes A-K, capturas, diseño de red, convención de nombres, pruebas del usuario Ana y análisis de costes de dos momentos (durante y al día siguiente de borrar).
- `lab-azure.sh` ejecutable y reproducible, `cloud-init.yaml`, `consultas.kql`, y el JSON de la regla de recopilación si lo usaste.
- La suscripción **sin recursos del laboratorio** y con presupuesto activo.

### Criterios de validación

- [ ] Los tres grupos tienen las cuatro etiquetas; el bloqueo impide el borrado (captura del error) y se explica `CanNotDelete` frente a `ReadOnly`.
- [ ] La red coincide con el diseño; los NSGs solo permiten 80 desde Internet a `snet-web`, 22 a `snet-web` desde `snet-mgmt` y 22 a `snet-mgmt` desde la IP del estudiante; las reglas por defecto están explicadas.
- [ ] `vm-web-01` no tiene IP pública y se alcanza por `ProxyJump`; nginx responde por IP privada y por nombre DNS privado; cloud-init está en un archivo.
- [ ] El Load Balancer (o la alternativa nginx) está probado, la sonda de estado documentada y el LB borrado el mismo día; SNAT de salida explicado.
- [ ] La subida al blob y la lectura del secreto se hacen con identidad administrada (sin claves ni contraseñas en ningún archivo) y los intentos fuera de ámbito fallan con el error documentado.
- [ ] Ana puede iniciar/detener la VM y no puede crear VMs ni ver el grupo compartido; las asignaciones son al grupo y con el ámbito mínimo; el Registro de actividad muestra sus acciones.
- [ ] El agente envía Heartbeat, Perf y Syslog; las tres consultas KQL funcionan; la alerta de CPU se disparó y se resolvió con evidencias (correo, portal).
- [ ] El análisis de costes está agrupado por etiqueta y por grupo; todo está borrado (incluidas IPs y discos) y hay captura de coste del día siguiente.
- [ ] `lab-azure.sh` crea y destruye al menos gobernanza y red de forma reproducible.
- [ ] En una llamada con el mentor, el estudiante explica su red dibujándola y responde a "¿qué pasaría si...?" (borrar la IP pública, quitar el rol a la identidad, apagar la VM desde dentro).

## Entrega

En tu repositorio de entregas, carpeta `02-modulo-intermedio/05-administracion-de-azure/`, mediante Pull Request:

1. `laboratorio-azure.md`.
2. `lab-azure.sh`, `cloud-init.yaml`, `consultas.kql` (y el JSON de la DCR si lo usaste). **Nunca** incluyas el valor del secreto, claves de cuenta, IDs completos de suscripción ni contraseñas: revisa el diff antes de hacer push.
3. `capturas/` con usuario o suscripción visible (oculta IDs y correos completos si lo prefieres).
4. `ENTREGA.md` con evaluación, checklist y uso de IA.

## Evaluación

1. **Conceptual.** Explica la jerarquía inquilino → grupo de administración → suscripción → grupo de recursos → recurso. ¿En qué nivel asignarías un rol a un equipo de finanzas que solo necesita ver costes de toda la empresa?
2. **Situacional.** Acme va a tener tres entornos (dev, test, prod) y dos equipos. Propón una organización de suscripciones y grupos de recursos, la convención de nombres y las etiquetas mínimas, y justifica dónde pondrías bloqueos `CanNotDelete`.
3. **Técnica.** Una VM en `snet-web` con NSG que permite 80 desde Internet no responde a `curl` desde tu casa. Da cuatro causas posibles en orden de comprobación (pista: IP pública, LB, NSG en NIC, servicio en la VM, `ufw`).
4. **Conceptual.** ¿Qué diferencia hay entre `az vm stop` y `az vm deallocate`? Enumera lo que sigue costando en cada caso. ¿Por qué una IP pública Standard estática cobra con la VM apagada?
5. **Situacional.** El equipo pide "un Bastion para entrar a las VMs". Explica qué es Azure Bastion, qué cuesta aproximadamente y qué alternativas razonables tiene una empresa pequeña (host de salto con NSG restringido, acceso Just-in-Time, VPN).
6. **Técnica.** Explica sonda de estado y regla de balanceo. Si la sonda apunta a `/health` y la aplicación devuelve 500 en ese endpoint pero sirve bien el resto, ¿qué verá el usuario? ¿Qué pasa con la salida a Internet de una VM sin IP pública detrás de un LB Standard?
7. **Conceptual.** ¿Qué es una identidad administrada y qué problema resuelve? Diferencia asignada por el sistema y asignada por el usuario, y da un caso para cada una.
8. **Troubleshooting.** Desde la VM, `az storage blob upload --auth-mode login` devuelve `AuthorizationPermissionMismatch`. Enumera las comprobaciones (rol, ámbito, propagación, identidad habilitada, `--auth-mode`) en orden.
9. **Conceptual.** Diferencia entre un rol de Microsoft Entra ID y un rol de Azure RBAC. ¿Puede el Administrador global de Entra borrar una VM por defecto? ¿Qué es la "elevación de acceso"?
10. **Situacional.** Un desarrollador pide Contributor en la suscripción "para no molestar cada vez". Propón una alternativa con mínimo privilegio (roles, ámbitos, grupos) y explica el riesgo de lo que pide.
11. **Técnica.** ¿Por qué un propietario de la suscripción no puede leer un secreto de un Key Vault con modelo RBAC sin un rol adicional? ¿Qué es la separación entre plano de control y plano de datos? Da otro servicio donde ocurre lo mismo.
12. **Técnica.** Escribe una consulta KQL que muestre, por VM, el promedio de CPU en intervalos de 15 minutos de las últimas 24 horas, y otra que cuente los inicios de sesión SSH fallidos del último día. Explica qué tabla usa cada una y de dónde salen esos datos.
13. **Situacional.** La alerta de CPU se dispara cada noche a las 03:00 durante 5 minutos por un backup y el equipo la ignora. ¿Qué ajustarías (umbral, ventana, frecuencia, supresión, gravedad) y qué riesgo tiene "subir el umbral hasta que deje de molestar"?
14. **Situacional.** El presupuesto del grupo `rg-acme-app-dev` avisa al 80 % el día 12. Describe cómo encuentras el recurso culpable con Análisis de costes (agrupar, filtrar, granularidad) y el Registro de actividad, y qué harías si fuera una IP pública huérfana.
15. **Reflexión.** ¿Qué parte del entorno fue más difícil de hacer por CLI que por portal y por qué? ¿Qué harías distinto si tuvieras que crear este entorno para cinco clientes distintos?

## Checklist final

Antes de continuar, deberías poder:

- [ ] Explicar la jerarquía de Azure y organizar grupos de recursos con nombres, etiquetas y bloqueos coherentes.
- [ ] Diseñar y crear una VNet con subredes y NSGs de mínimo privilegio, y explicar las reglas por defecto.
- [ ] Desplegar VMs Linux por CLI con cloud-init, con y sin IP pública, y acceder por host de salto.
- [ ] Explicar estados de una VM y qué se factura en cada uno; desasignar sin pensarlo al acabar.
- [ ] Explicar y probar un Load Balancer Standard (sonda, regla, SNAT) y conocer su coste y alternativas.
- [ ] Crear zonas DNS privadas y públicas en Azure y resolver nombres desde la VNet.
- [ ] Usar identidades administradas para acceder a Blob Storage y Key Vault sin credenciales.
- [ ] Crear usuarios y grupos en Entra ID y asignar roles RBAC con el ámbito mínimo, comprobándolo.
- [ ] Configurar Log Analytics, el agente, consultas KQL básicas y una alerta de métrica con notificación.
- [ ] Crear presupuestos por grupo, analizar costes por etiqueta y dejar la suscripción limpia.
- [ ] Reproducir el entorno con un script de Azure CLI y explicar sus límites frente a Terraform.

---

*Recursos verificados el 2026-09-27 (existencia y vigencia de las URLs mediante búsqueda web y, cuando el cupo de búsqueda se agotó, mediante los repositorios oficiales de la documentación). Los precios indicados son aproximados y cambian: la calculadora y las páginas de precios de Azure mandan. Si un enlace falla, abre un issue en este repositorio.*
