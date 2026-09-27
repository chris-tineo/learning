# Terraform

> Módulo: Intermedio · Curso 8 de 11 · Duración estimada: 25-35 horas · Estado: ✅ Completo

## Objetivo

En Introducción a Cloud Computing y en Administración de Azure creaste recursos con el portal y con Azure CLI. Funciona, pero no escala: nadie recuerda qué se hizo, no se puede revisar en un pull request, y reproducirlo en otro entorno es copiar a mano. **Infraestructura como código (IaC)** resuelve eso: describes en archivos de texto el estado que quieres y una herramienta lo compara con lo que existe y hace solo los cambios necesarios. **Terraform** es la herramienta de IaC más usada en el mercado y funciona igual con Azure, AWS, GCP y cientos de proveedores más.

En este curso vas a desplegar en Azure, sin tocar el portal para crear nada, una infraestructura pequeña pero completa: grupo de recursos, red virtual, subred, grupo de seguridad, IP pública, interfaz de red, una VM Linux B1s que instala nginx con cloud-init y una cuenta de almacenamiento. Aprenderás el lenguaje HCL, el ciclo `init`, `plan`, `apply`, `destroy`, las variables por entorno, los outputs, los locals, los data sources, las dependencias, el **state** (el concepto más importante y más incomprendido de Terraform), su traslado a un backend remoto en Azure Storage con bloqueo, y a empaquetar tu primer módulo reutilizable.

El estado y los módulos vuelven con más profundidad en Terraform Avanzado (Módulo Avanzado). Aquí lo importante es que al terminar puedas leer cualquier configuración de Terraform y entender qué va a pasar antes de ejecutar `apply`.

**Antes de empezar** necesitas Azure CLI autenticada, tu clave SSH pública y la cuenta de Azure con presupuesto activo. Todo se hace desde la terminal de tu equipo o de `lab-so`.

### Al terminar este curso deberías poder

- Explicar qué es infraestructura como código, qué es el modelo declarativo y qué ventajas tiene frente a scripts imperativos con Azure CLI.
- Leer y escribir HCL: bloques `terraform`, `provider`, `resource`, `variable`, `output`, `locals`, `data` y `module`, con tipos, validaciones y expresiones.
- Explicar qué hace cada fase del ciclo `terraform init`, `fmt`, `validate`, `plan`, `apply` y `destroy`, y leer un plan distinguiendo crear, modificar en sitio, reemplazar y destruir.
- Parametrizar una configuración con variables y archivos `.tfvars` por entorno, y exponer resultados con outputs.
- Usar data sources para leer información existente (cliente actual, suscripción, imagen de VM) y explicar la diferencia con un resource.
- Explicar las dependencias implícitas y explícitas y cómo Terraform construye el grafo de ejecución.
- Explicar qué es el state, por qué es sensible, qué pasa si se pierde o se corrompe, y migrarlo a un backend remoto en Azure Storage con bloqueo.
- Crear un módulo propio con inputs y outputs y consumirlo desde la configuración raíz.
- Importar al state un recurso creado fuera de Terraform y detectar *drift* (cambios hechos a mano).
- Destruir todo lo creado y verificar que no queda coste.

## Prerrequisitos

- Curso 5: Administración de Azure (VNet, subred, NSG, IP pública, NIC, VM, Storage Account, RBAC; Azure CLI autenticada).
- Curso 1: Administración de Linux (cloud-init y systemd te resultarán familiares) y curso 4: Git y GitHub Intermedio (la configuración vive en un repositorio).
- Curso 7: CI/CD (no es imprescindible, pero al final se comenta cómo encajaría Terraform en un pipeline).
- Terraform instalado en tu equipo o en `lab-so` (binario oficial de HashiCorp; se instala en el laboratorio).
- Clave SSH pública (`~/.ssh/id_ed25519.pub`).

## Temario

- Infrastructure as Code.
- HCL.
- Providers.
- Resources.
- Variables.
- Outputs.
- Locals.
- Data sources.
- Dependencies.
- State.
- Remote state introductorio.
- Modules básicos.
- terraform init.
- terraform plan.
- terraform apply.
- terraform destroy.

## Recursos en español

### Aspectos básicos de Terraform en Azure · Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/training/paths/terraform-fundamentals/
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Ruta de aprendizaje (varios módulos con ejercicios)
- **Duración aproximada:** 4-6 h
- **Cubre:** IaC, sintaxis declarativa de HCL, providers, variables, outputs, funciones, bucles, módulos, flujo `init`/`plan`/`apply`.
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre; cuenta Microsoft gratuita para guardar progreso. Los ejercicios se hacen en tu suscripción (recursos pequeños; bórralos al terminar cada módulo)
- **Por qué lo recomiendo:** Es el material oficial en español y cubre el temario casi completo con el enfoque de Azure. Es el recurso principal en español; lo complementas con los tutoriales de HashiCorp para el detalle del lenguaje.

### Documentación de Terraform en Azure · Microsoft Learn
- **URL:** Introducción: https://learn.microsoft.com/es-es/azure/developer/terraform/overview · Instalación y configuración: https://learn.microsoft.com/es-es/azure/developer/terraform/quickstart-configure · Autenticación en Azure: https://learn.microsoft.com/es-es/azure/developer/terraform/authenticate-to-azure
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Documentación oficial
- **Duración aproximada:** 1 h para las tres páginas
- **Cubre:** Providers de Azure (azurerm, azapi, azuread), instalación, autenticación con Azure CLI y con service principal.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Explica en español las decisiones que tomarás en los primeros diez minutos del laboratorio: qué provider usar y cómo autenticarte. La página de autenticación es la que consultarás cuando el `plan` falle con un error de credenciales.

### Curso completo de Terraform · Pelado Nerd
- **URL:** Vídeo: https://www.youtube.com/watch?v=_84CxYRv9Ik · Lista de reproducción: https://www.youtube.com/playlist?list=PLZyYSwe8s1lzEkCf_uIAS5yIDjU0xq_zB · Repositorio con los archivos: https://github.com/pablokbs/peladonerd
- **Autor / organización:** Pablo Fredrikson (Pelado Nerd), ingeniero SRE y divulgador en español
- **Idioma:** Español
- **Tipo:** Vídeo largo + lista de vídeos cortos + repositorio
- **Duración aproximada:** 2-3 h
- **Cubre:** IaC, HCL, providers, resources, variables, outputs, state, módulos, ciclo de vida.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Explica Terraform con claridad y sin marketing, desde la experiencia de alguien que lo opera a diario. Los ejemplos usan otros proveedores, pero los conceptos son idénticos: fíjate en cómo lee los planes y cómo trata el state.

## Recursos en inglés

### Get Started: Terraform on Azure · HashiCorp Developer
- **URL:** https://developer.hashicorp.com/terraform/tutorials/azure-get-started (incluye "Build infrastructure": https://developer.hashicorp.com/terraform/tutorials/azure-get-started/azure-build y "Store remote state": https://developer.hashicorp.com/terraform/tutorials/azure-get-started/azure-remote)
- **Autor / organización:** HashiCorp
- **Idioma:** Inglés
- **Tipo:** Serie de tutoriales paso a paso
- **Duración aproximada:** 3-4 h
- **Cubre:** Instalación, primer recurso en Azure, cambios, destrucción, variables, outputs, state remoto.
- **Nivel:** Introductorio
- **Acceso:** Libre (el tutorial de state remoto menciona HCP Terraform; en este curso usarás Azure Storage en su lugar)
- **Por qué lo recomiendo:** Son los tutoriales oficiales del fabricante, cortos y exactos. Hazlos con la terminal abierta: son la base sobre la que se construye el laboratorio.

### Terraform Language Documentation · HashiCorp Developer
- **URL:** https://developer.hashicorp.com/terraform/language · Módulos: https://developer.hashicorp.com/terraform/language/modules · Estructura estándar de un módulo: https://developer.hashicorp.com/terraform/language/modules/develop/structure · Backend azurerm: https://developer.hashicorp.com/terraform/language/backend/azurerm · Import: https://developer.hashicorp.com/terraform/language/import
- **Autor / organización:** HashiCorp
- **Idioma:** Inglés
- **Tipo:** Documentación oficial del lenguaje
- **Duración aproximada:** 3 h de lectura selectiva; consulta continua
- **Cubre:** Todo el temario: sintaxis, variables, outputs, locals, data sources, dependencias, state, backends, módulos.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la referencia del lenguaje. Cuando algo del laboratorio no te cuadre, la respuesta está aquí, no en un blog.

### Registro del provider azurerm · Terraform Registry
- **URL:** https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs
- **Autor / organización:** HashiCorp y Microsoft
- **Idioma:** Inglés
- **Tipo:** Documentación de referencia de cada recurso y data source
- **Duración aproximada:** Consulta continua
- **Cubre:** Cada `azurerm_*` que uses: argumentos obligatorios y opcionales, atributos exportados, ejemplo y sección de import.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** No memorices recursos: aprende a leer esta documentación. La regla del curso es "antes de escribir un recurso, abre su página en el Registry".

### Terraform Associate: guía de estudio oficial · HashiCorp Developer
- **URL:** https://learn.hashicorp.com/tutorials/terraform/associate-study-003 (redirige a la guía vigente en developer.hashicorp.com; la certificación se ha renumerado, sigue la versión que muestre la página)
- **Autor / organización:** HashiCorp
- **Idioma:** Inglés
- **Tipo:** Guía de estudio con enlaces a tutoriales y documentación
- **Duración aproximada:** 1 h para leerla; los enlaces suman muchas más
- **Cubre:** Todo el temario y algo más (workspaces, HCP Terraform).
- **Nivel:** Intermedio
- **Acceso:** Libre (el examen es de pago y **no** es necesario)
- **Por qué lo recomiendo:** Es un mapa de lo que un profesional debe saber de Terraform. Úsala al final del curso como autoevaluación: lo que no entiendas de la lista, vuélvelo a estudiar.

## Documentación oficial

- **Terraform (portal):** https://developer.hashicorp.com/terraform/docs · Lenguaje: https://developer.hashicorp.com/terraform/language
- **Tutoriales Terraform en Azure:** https://developer.hashicorp.com/terraform/tutorials/azure-get-started
- **Provider azurerm (Registry):** https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs
- **Backend azurerm (state remoto):** https://developer.hashicorp.com/terraform/language/backend/azurerm · Guía de Microsoft: https://learn.microsoft.com/en-us/azure/developer/terraform/store-state-in-azure-storage
- **Módulos:** https://developer.hashicorp.com/terraform/language/modules · Crear módulos: https://developer.hashicorp.com/terraform/language/modules/develop · Estructura estándar: https://developer.hashicorp.com/terraform/language/modules/develop/structure
- **Import:** https://developer.hashicorp.com/terraform/language/import · Comando `terraform import`: https://developer.hashicorp.com/terraform/cli/commands/import
- **Microsoft Learn: Terraform en Azure (es-es):** https://learn.microsoft.com/es-es/azure/developer/terraform/overview
- **Azure: custom data y cloud-init en VMs:** https://learn.microsoft.com/en-us/azure/virtual-machines/custom-data · Tutorial cloud-init: https://learn.microsoft.com/en-us/azure/virtual-machines/linux/tutorial-automate-vm-deployment
- **Azure Verified Modules (solo referencia, no se usan en el laboratorio):** https://azure.github.io/Azure-Verified-Modules/ · Ejemplo, módulo de VM: https://registry.terraform.io/modules/Azure/avm-res-compute-virtualmachine/azurerm/latest

## Ruta recomendada de estudio

1. **Leer** la introducción de "Terraform en Azure" de Microsoft Learn y la página de autenticación (45 min). Anota qué providers existen para Azure y por qué en este curso se usa `azurerm`.
2. **Hacer** los tutoriales "Get Started: Terraform on Azure" de HashiCorp hasta "Destroy infrastructure" incluido (2-3 h). Al terminar debes saber qué hacen `init`, `plan`, `apply` y `destroy` y haber visto un `terraform.tfstate` por dentro.
3. **Ver** la primera hora del curso de Pelado Nerd (60 min), prestando atención a cómo lee un plan.
4. **Hacer** los módulos de la ruta "Aspectos básicos de Terraform en Azure" sobre sintaxis, variables, outputs y funciones (3 h). Borra los recursos de cada ejercicio.
5. **Leer** en la documentación del lenguaje las páginas de variables, outputs, locals, data sources y `depends_on` (90 min). Abre en paralelo la página de `azurerm_linux_virtual_machine` en el Registry y localiza cada tipo de bloque.
6. **Hacer el laboratorio**, partes A a C (6-8 h).
7. **Leer** la documentación del backend `azurerm` y la guía de Microsoft sobre state en Azure Storage (45 min) y **hacer** la parte D (2 h).
8. **Leer** "Creating modules" y "Standard module structure" (45 min) y **hacer** el módulo de la ruta de Microsoft Learn (60 min); después la parte E del laboratorio (2-3 h).
9. **Leer** la página de import (20 min) y **hacer** las partes F y G (1-2 h).
10. **Leer** la guía de estudio de Terraform Associate como autoevaluación (1 h) y **hojear** Azure Verified Modules para ver cómo es un módulo profesional (20 min).
11. **Responder la evaluación** y **revisar el checklist**.

Si vas justo de tiempo: haz obligatoriamente los puntos 2, 5, 6, 7 y 8. El resto es refuerzo.

## Laboratorio

### Objetivo

Desplegar en Azure, solo con Terraform, una VM Linux con nginx y su red completa más una cuenta de almacenamiento; parametrizarlo por entorno; mover el state a Azure Storage con bloqueo; extraer la VM a un módulo propio; importar un recurso existente; y destruirlo todo verificando el coste.

### Requisitos

- Terraform 1.9 o superior instalado (`terraform version`). Sigue la guía oficial de instalación para tu sistema operativo.
- Azure CLI autenticada (`az login`, `az account show`).
- Clave SSH pública y un repositorio Git nuevo `terraform-lab` (público o privado) en tu cuenta de GitHub.
- Convención: documenta en `laboratorio-terraform.md` cada comando y la parte relevante de su salida (los planes son largos: pega el resumen `Plan: X to add, Y to change, Z to destroy` y los fragmentos que expliques).

> **Sobre el coste.** La infraestructura completa cuesta, con precios orientativos: VM B1s unos 0,01 USD/h (o gratuita si tu cuenta aún tiene las 750 h/mes de los 12 primeros meses), disco de SO Standard SSD de 30 GB unos 2,5 USD/mes, IP pública estándar estática unos 3,6 USD/mes, cuenta de almacenamiento LRS céntimos. Una sesión de 4 h de laboratorio con todo encendido cuesta **menos de 0,10 USD**. La cuenta de almacenamiento del state cuesta céntimos al mes. Lo que sí cobra aunque la VM esté parada: el disco y la IP pública. Por eso el laboratorio termina con `terraform destroy` y `az group delete`, y con la verificación en Cost Management al día siguiente.

### Instrucciones

**Parte A: instalación, provider y primer recurso (1-2 h)**

1. Instala Terraform y verifica `terraform version`. En el repositorio `terraform-lab` crea `providers.tf`:
   ```hcl
   terraform {
     required_version = ">= 1.9"
     required_providers {
       azurerm = {
         source  = "hashicorp/azurerm"
         version = "~> 5.0"
       }
       random = {
         source  = "hashicorp/random"
         version = "~> 3.6"
       }
     }
   }
   provider "azurerm" {
     features {}
     subscription_id = var.subscription_id
   }
   ```
   Comprueba en el Registry cuál es la versión mayor vigente de `azurerm` y ajusta la restricción si hace falta. Explica qué significa `~> 5.0`, para qué sirve `features {}` y por qué el provider exige `subscription_id`.
2. Crea `variables.tf` con `subscription_id`, `location`, `environment` (con `validation` que solo admita `dev` o `prod`), `prefix`, `vm_size` (por defecto `Standard_B1s`), `admin_username`, `ssh_public_key_path`, `allowed_ssh_cidr` (tu IP pública en formato `x.x.x.x/32`) y `tags` (tipo `map(string)`). Crea `envs/dev.tfvars` con valores para dev. Crea `.gitignore` con `.terraform/`, `*.tfstate`, `*.tfstate.*`, `*.tfvars` no debería ignorarse aquí porque no contiene secretos, razona si lo mantienes versionado.
3. Crea `main.tf` con solo el grupo de recursos `azurerm_resource_group` (nombre `rg-${var.prefix}-${var.environment}`, etiquetas). Ejecuta en orden `terraform init`, `terraform fmt -check`, `terraform validate`, `terraform plan -var-file=envs/dev.tfvars -out=dev.tfplan`, `terraform apply dev.tfplan`. Explica qué apareció en `.terraform/`, qué es `.terraform.lock.hcl` (¿se versiona?) y qué contiene `terraform.tfstate` (ábrelo; localiza el `id` del grupo). Ejecuta `terraform state list` y `terraform show`.

**Parte B: red, VM con cloud-init y almacenamiento (3-4 h)**

4. Añade `locals.tf`:
   ```hcl
   locals {
     name        = "${var.prefix}-${var.environment}"
     common_tags = merge(var.tags, { environment = var.environment, managed_by = "terraform" })
   }
   ```
   y `data.tf` con `data "azurerm_client_config" "current" {}` y `data "azurerm_subscription" "current" {}`. Explica la diferencia entre una variable, un local y un data source.
5. En `main.tf` añade, leyendo cada recurso en el Registry antes de escribirlo: `azurerm_virtual_network` (10.20.0.0/16), `azurerm_subnet` (10.20.1.0/24), `azurerm_network_security_group` con dos reglas (SSH desde `var.allowed_ssh_cidr`, HTTP desde cualquier origen), `azurerm_public_ip` (Standard, Static), `azurerm_network_interface`, `azurerm_network_interface_security_group_association`, y `azurerm_linux_virtual_machine` con `size = var.vm_size`, `admin_ssh_key` leyendo `file(var.ssh_public_key_path)`, imagen Ubuntu LTS (`source_image_reference`, mira los valores vigentes en la documentación), disco de SO `Standard_LRS` o `StandardSSD_LRS`, y `custom_data = base64encode(file("${path.module}/cloud-init.yaml"))`. Añade `depends_on = [azurerm_network_interface_security_group_association.vm]` en la VM y explica por qué esta dependencia es explícita mientras que la de la NIC con la subred es implícita. Crea `cloud-init.yaml`:
   ```yaml
   #cloud-config
   package_update: true
   packages: [nginx]
   runcmd:
     - echo "<h1>Desplegado con Terraform en $(hostname)</h1>" > /var/www/html/index.html
     - systemctl enable --now nginx
   ```
6. Añade `random_string` (minúsculas y números, 6 caracteres) y `azurerm_storage_account` (`st${var.prefix}${var.environment}${random_string.sufijo.result}`, Standard, LRS) con un `azurerm_storage_container` privado `datos`. Explica por qué el nombre necesita el sufijo aleatorio y qué pasa con `random_string` en el state.
7. Crea `outputs.tf` con `public_ip`, `ssh_command` (cadena completa `ssh usuario@ip`), `web_url`, `storage_account_name` y `tenant_id` (desde el data source). Ejecuta `fmt`, `validate`, `plan` y `apply`. Anota el resumen del plan (¿cuántos recursos?), el tiempo de `apply`, y comprueba: `curl $(terraform output -raw web_url)` muestra la página de nginx (espera 1-2 min a cloud-init) y `ssh` entra con tu clave. Dentro de la VM, `cloud-init status` y `sudo cat /var/log/cloud-init-output.log | tail -20`.
8. Genera el grafo de dependencias con `terraform graph` (puedes pegarlo en un visor de Graphviz online) e identifica en él la dependencia explícita. Explica con tus palabras cómo decide Terraform el orden de creación y qué recursos puede crear en paralelo.

**Parte C: cambios, drift y entornos (1-2 h)**

9. Cambia una etiqueta en `dev.tfvars` y añade una tercera regla al NSG (por ejemplo, HTTPS). Ejecuta `plan` y explica la diferencia entre `~ update in-place` y `-/+ destroy and then create replacement`. Cambia ahora el `admin_username` de la VM y observa en el plan qué tipo de cambio provoca (no apliques; revierte).
10. **Drift:** desde el portal, añade a mano la etiqueta `manual=true` al grupo de recursos y borra una regla del NSG. Ejecuta `plan`. Explica qué detecta Terraform, en qué dirección lo corrige (`apply` deja el mundo como dice el código) y por qué en un equipo con IaC "tocar el portal" es un problema.
11. Crea `envs/prod.tfvars` con otras etiquetas y `environment = "prod"`. Ejecuta solo `terraform plan -var-file=envs/prod.tfvars` y explica qué pasaría si hicieras `apply` con el **mismo state** (pista: Terraform cree que quieres renombrar, no duplicar). No apliques. Anota la solución que verás en el Módulo Avanzado (state separado por entorno: workspaces o un backend `key` por entorno).

**Parte D: state remoto en Azure Storage con bloqueo (2 h)**

12. El state contiene IDs, IPs y, a veces, secretos; guardarlo en tu portátil no sirve para un equipo. Crea **con Azure CLI** (no con Terraform: explica el problema del huevo y la gallina) un grupo `rg-tfstate-<usuario>`, una cuenta de almacenamiento `sttfstate<sufijo>` (LRS, versionado de blobs activado) y un contenedor `tfstate`. Asígnate el rol **Storage Blob Data Contributor** sobre la cuenta.
13. Añade a `providers.tf` el bloque `backend "azurerm" {}` vacío y crea `backend.hcl` con `resource_group_name`, `storage_account_name`, `container_name`, `key = "terraform-lab/dev.tfstate"` y `use_azuread_auth = true`. Ejecuta `terraform init -backend-config=backend.hcl -migrate-state` y confirma la migración. Comprueba en el portal que el blob existe y que `terraform.tfstate` local quedó vacío o desapareció. Explica por qué `use_azuread_auth` es preferible a usar la clave de la cuenta.
14. **Bloqueo:** abre dos terminales. En la primera lanza `terraform apply -var-file=envs/dev.tfvars` y quédate en la pregunta de confirmación; en la segunda ejecuta `terraform plan -var-file=envs/dev.tfvars`. Captura el error de bloqueo y mira en el portal el estado *lease* del blob. Cancela el primer `apply`. Explica qué evita el bloqueo y qué harías si un bloqueo se quedara colgado (`terraform force-unlock`, y cuándo **no** usarlo).

**Parte E: tu primer módulo (2-3 h)**

15. Crea `modules/vm-linux/` con `main.tf`, `variables.tf`, `outputs.tf` y `README.md` siguiendo la estructura estándar. Mueve al módulo la IP pública, la NIC, la asociación con el NSG y la VM. Inputs mínimos: `name`, `location`, `resource_group_name`, `subnet_id`, `nsg_id`, `vm_size`, `admin_username`, `ssh_public_key`, `custom_data`, `tags`. Outputs: `public_ip`, `private_ip`, `vm_id`. En la raíz sustituye esos recursos por un bloque `module "vm" { source = "./modules/vm-linux" ... }` y ajusta los outputs raíz.
16. Ejecuta `terraform init` (¿por qué hace falta otra vez?) y `plan`. Verás que Terraform quiere destruir y recrear la VM porque cambió de dirección en el state. Evítalo con bloques `moved` (por ejemplo, `moved { from = azurerm_linux_virtual_machine.vm  to = module.vm.azurerm_linux_virtual_machine.this }`) para cada recurso movido, hasta que el plan sea `0 to add, 0 to change, 0 to destroy`. Explica qué acabas de aprender sobre la relación entre direcciones de recursos y state.
17. Documenta el módulo en su `README.md` (para qué sirve, inputs, outputs, ejemplo de uso). Compara tu módulo con el de Azure Verified Modules para VM: enumera tres cosas que el módulo profesional hace y el tuyo no, y por qué para este curso es correcto que el tuyo sea pequeño.

**Parte F: importar un recurso existente (opcional, 1 h)**

18. Crea a mano con CLI una segunda cuenta de almacenamiento en `rg-<prefix>-dev` (`az storage account create ...`). Escribe en `import.tf` un bloque `import { to = azurerm_storage_account.importada  id = "<id completo del recurso>" }` y ejecuta `terraform plan -generate-config-out=importada.tf`. Revisa el archivo generado, límpialo de atributos innecesarios, ejecuta `apply` y verifica que un `plan` posterior no propone cambios. Explica cuándo se importa en la vida real (infraestructura que existía antes de adoptar IaC) y qué riesgos tiene.

**Parte G: destrucción y verificación de coste (30 min)**

19. Ejecuta `terraform plan -destroy -var-file=envs/dev.tfvars`, lee el plan completo y después `terraform destroy -var-file=envs/dev.tfvars`. Comprueba con `az resource list -g rg-<prefix>-dev -o table` que no queda nada y que el blob de state sigue existiendo pero con `resources: []`. Decide si conservas `rg-tfstate-<usuario>` para Terraform Avanzado (coste de céntimos) o lo borras con `az group delete`. Al día siguiente captura Cost Management filtrado por los dos grupos y anota la cifra.
20. Escribe una sección final "Terraform frente a lo que ya sabía": compara el laboratorio con lo que hiciste en Administración de Azure por portal y CLI (tiempo, reproducibilidad, revisión, errores) y completa la tabla de equivalencias: concepto de Terraform (provider, resource, state, module, plan) frente a Bicep/ARM (Azure), CloudFormation (AWS) y Pulumi.

### Resultado esperado

- Repositorio `terraform-lab` con `providers.tf`, `variables.tf`, `locals.tf`, `data.tf`, `main.tf`, `outputs.tf`, `cloud-init.yaml`, `envs/dev.tfvars`, `envs/prod.tfvars`, `backend.hcl`, `modules/vm-linux/` con README, bloques `moved` y, si hiciste la parte F, `import.tf` e `importada.tf`. Sin archivos `.tfstate` ni `.terraform/` versionados.
- `laboratorio-terraform.md` con los planes resumidos, salidas, capturas (nginx en el navegador, blob de state, error de bloqueo, Cost Management) y explicaciones propias.
- Ningún recurso de laboratorio vivo, salvo, si lo decides, el grupo del state.

### Criterios de validación

- [ ] `terraform fmt -check` y `terraform validate` pasan; el código está en Git sin state ni `.terraform/`.
- [ ] Variables con tipos y una validación, locals, dos data sources, outputs útiles y un `depends_on` explícito justificado.
- [ ] La VM arranca con nginx instalado por cloud-init y el NSG solo permite SSH desde la IP del estudiante.
- [ ] Están documentados y explicados: un cambio en sitio, un cambio con reemplazo, el drift detectado y el plan de `prod` con el mismo state.
- [ ] El state está en Azure Storage con autenticación de Entra ID; hay captura del error de bloqueo y explicación de `force-unlock`.
- [ ] El módulo `vm-linux` tiene la estructura estándar, README, y el plan tras el refactor con `moved` es de cero cambios.
- [ ] (Opcional) El import genera configuración y el plan posterior es de cero cambios.
- [ ] Todo destruido, blob de state vacío o grupo borrado, y captura de coste del día siguiente.
- [ ] El estudiante puede, en una llamada con el mentor, leer un plan desconocido y explicar qué va a pasar antes de aplicar.

## Entrega

En tu repositorio de entregas, carpeta `02-modulo-intermedio/08-terraform/`:

1. `laboratorio-terraform.md`.
2. Enlace al repositorio `terraform-lab` (o copia de los archivos `.tf`, `.tfvars`, `backend.hcl` y `cloud-init.yaml` como archivos, no como capturas).
3. `equivalencias.md` con la tabla Terraform / Bicep / CloudFormation / Pulumi y la comparación con portal y CLI.
4. Carpeta `capturas/` (oculta el ID de suscripción y de inquilino; **nunca** subas un `tfstate`).
5. `ENTREGA.md` con evaluación, checklist y uso de IA.

Nota sobre IA: los modelos inventan argumentos de recursos `azurerm_*` y mezclan versiones del provider. Úsala para que te explique un error de `plan` o un concepto, y contrasta cada argumento con el Registry. Declara el uso.

## Evaluación

1. **Conceptual.** Explica infraestructura como código y el modelo declarativo con el ejemplo de tu NSG: ¿qué diferencia hay entre `az network nsg rule create` ejecutado dos veces y `terraform apply` ejecutado dos veces?
2. **Técnica.** Describe qué hace cada uno: `terraform init`, `fmt`, `validate`, `plan`, `apply`, `destroy`. ¿Cuál de ellos necesita credenciales de Azure y cuál no?
3. **Conceptual.** ¿Qué es el state, qué contiene y por qué es sensible? Un compañero borra `terraform.tfstate` por accidente con la infraestructura viva: ¿qué pasa en el siguiente `apply` y cómo lo recuperarías?
4. **Técnica.** Explica la diferencia entre `variable`, `local` y `data`, con un ejemplo de tu laboratorio de cada uno. ¿Cuándo un valor debería ser variable y cuándo local?
5. **Situacional.** Necesitas la misma infraestructura para `dev`, `test` y `prod` con tamaños distintos. Explica cómo lo harías con `.tfvars` y por qué necesitas states separados. ¿Qué pasaría con un solo state?
6. **Troubleshooting.** `terraform plan` muestra `-/+ destroy and then create replacement` para la VM cuando solo cambiaste una etiqueta. Da dos causas posibles y cómo las investigarías en el plan y en el Registry.
7. **Conceptual.** Explica dependencia implícita y explícita con los recursos de tu laboratorio. ¿Por qué abusar de `depends_on` es mala señal?
8. **Técnica.** Explica el bloqueo del state remoto: qué lo activa, qué error ves, cómo se libera. ¿Cuándo es peligroso `terraform force-unlock`?
9. **Situacional.** Alguien cambió a mano el tamaño de la VM en el portal de B1s a B2s. ¿Qué muestra `plan`? Si aplicas, ¿qué pasa? ¿Cómo harías que el cambio manual quedara reflejado en el código en vez de revertirlo?
10. **Conceptual.** ¿Qué es un módulo, qué lo diferencia de copiar y pegar bloques, y qué hace `moved`? ¿Por qué cambiar la dirección de un recurso sin `moved` provoca destrucción?
11. **Técnica.** Explica qué hacen `custom_data`, `base64encode` y `file()` en tu VM y qué verías en la VM si el cloud-init tuviera un error de YAML.
12. **Situacional.** Tu equipo quiere ejecutar Terraform desde el pipeline de GitHub Actions del curso anterior. ¿Dónde vivirían el state y las credenciales, qué pasos tendría el workflow (`fmt`, `validate`, `plan` en PR, `apply` con aprobación) y qué riesgos ves?
13. **Conceptual.** Traduce a Bicep y a CloudFormation los conceptos provider, resource, state y module. ¿Qué concepto de Terraform no tiene equivalente directo en Bicep y por qué?
14. **Reflexión.** ¿Qué te costó más: la sintaxis HCL, leer el Registry o entender el state? ¿Qué error del laboratorio te enseñó más y cómo lo resolviste?

## Checklist final

Antes de continuar, deberías poder:

- [ ] Explicar IaC y el modelo declarativo con un ejemplo propio.
- [ ] Escribir una configuración con provider, recursos, variables tipadas, locals, data sources y outputs.
- [ ] Ejecutar y explicar `init`, `fmt`, `validate`, `plan`, `apply` y `destroy`.
- [ ] Leer un plan y anticipar qué se crea, se modifica, se reemplaza o se destruye.
- [ ] Parametrizar por entorno con `.tfvars` y explicar por qué cada entorno necesita su state.
- [ ] Explicar qué es el state, por qué es sensible y cómo se protege.
- [ ] Configurar el backend `azurerm` con autenticación de Entra ID y explicar el bloqueo.
- [ ] Crear y consumir un módulo con la estructura estándar y usar `moved` en un refactor.
- [ ] Detectar drift e importar un recurso existente.
- [ ] Destruir todo, verificar el coste y dejar solo (si quieres) el grupo del state para Terraform Avanzado.

---

*Recursos verificados el 2026-09-27 (existencia y vigencia de las URLs mediante búsqueda web y, cuando el cupo de búsqueda se agotó, mediante los repositorios oficiales de la documentación). Las páginas de Microsoft Learn se enlazan en `es-es` cuando se confirmó la traducción; en el resto se indica cómo cambiar el idioma. Si un enlace falla, abre un issue en este repositorio.*
