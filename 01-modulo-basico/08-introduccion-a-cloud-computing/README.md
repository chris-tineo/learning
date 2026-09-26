# Introducción a Cloud Computing

> Módulo: Básico · Curso 8 de 9 · Duración estimada: 10-15 horas · Estado: ✅ Completo

## Objetivo

Este es el curso en el que, por fin, tocas la nube. Todo lo anterior (hardware, sistemas operativos, Windows, Linux, redes, Git) era el suelo sobre el que se apoya. Ahora vas a entender **qué es realmente Cloud Computing, qué se compra, cómo se paga y quién es responsable de qué**, y vas a crear tus primeros recursos en Microsoft Azure: un grupo de recursos, una cuenta de almacenamiento y una máquina virtual Linux a la que entrarás por SSH exactamente igual que a tu VM local.

Los conceptos se explican de forma que sirvan también para AWS y GCP: regiones, zonas de disponibilidad, IaaS/PaaS/SaaS, modelo de responsabilidad compartida, elasticidad, pago por uso. Los nombres cambian entre proveedores; las ideas no.

Este curso también te enseña la primera regla de supervivencia en la nube: **controlar el coste**. Antes de crear nada configurarás un presupuesto con alertas, y al terminar borrarás todo lo que creaste.

**Antes de empezar** necesitas Networking Básico (IP, subred, puerto, SSH) y Linux Básico (administrar una VM). Necesitas también una **tarjeta de crédito o débito no prepagada** para crear la cuenta gratuita de Azure: se usa para verificar identidad y no se cobra nada mientras no cambies a pago por uso y no superes los límites gratuitos. Lo veremos paso a paso.

### Al terminar este curso deberías poder

- Definir Cloud Computing con tus palabras y explicar en qué se diferencia de un centro de datos propio (on-premises).
- Distinguir IaaS, PaaS y SaaS con ejemplos de Azure y decir quién gestiona qué en cada modelo (responsabilidad compartida).
- Distinguir nube pública, privada e híbrida y dar un caso de uso de cada una.
- Explicar qué son las regiones, los pares de regiones y las zonas de disponibilidad, y por qué importan para la disponibilidad.
- Nombrar las categorías básicas de servicios (cómputo, almacenamiento, red, bases de datos, identidad) y un servicio de Azure de cada una.
- Explicar elasticidad, escalabilidad (vertical y horizontal) y alta disponibilidad a nivel introductorio.
- Explicar el modelo de pago por uso, qué factores influyen en el coste y cómo estimarlo con la calculadora de precios.
- Crear una cuenta gratuita de Azure de forma segura, con presupuesto y alertas configurados antes de gastar nada.
- Crear, etiquetar, inspeccionar y eliminar un grupo de recursos, una cuenta de almacenamiento y una máquina virtual Linux desde el portal y desde Azure Cloud Shell.
- Conectarte por SSH a una VM de Azure y explicar qué componentes se crearon con ella (disco, NIC, IP pública, NSG).

## Prerrequisitos

- Curso 5: Linux Básico y curso 6: Networking Básico.
- Curso 7: Fundamentos de Git (la entrega se hace por Git).
- Tarjeta de crédito o débito no prepagada a tu nombre y un número de teléfono para la verificación.
- Cuenta Microsoft (la misma que usas en Microsoft Learn sirve).

## Temario

- Qué es Cloud Computing.
- On-premises frente a Cloud.
- IaaS.
- PaaS.
- SaaS.
- Public Cloud.
- Private Cloud.
- Hybrid Cloud.
- Regiones.
- Availability Zones.
- Compute.
- Storage.
- Networking.
- Bases de datos.
- Identidad.
- Shared Responsibility Model.
- Elasticidad.
- Escalabilidad.
- High Availability introductoria.
- Pay-as-you-go.
- Introducción a Azure.

## Recursos en español

### Introducción a la infraestructura en la nube (serie AZ-900, partes 1 a 3) — Microsoft Learn
- **URL:** Parte 1, "Descripción de los conceptos de la nube": https://learn.microsoft.com/es-es/training/paths/microsoft-azure-fundamentals-describe-cloud-concepts/ · Parte 2, "Descripción de la arquitectura y los servicios de Azure": https://learn.microsoft.com/es-es/training/paths/azure-fundamentals-describe-azure-architecture-services/ · Parte 3, "Descripción de la administración y gobernanza de Azure": https://learn.microsoft.com/es-es/training/paths/describe-azure-management-governance/
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Tres rutas de aprendizaje con ejercicios en sandbox (no gastan tu crédito)
- **Duración aproximada:** 6-8 h en total (Parte 1: ~1,5 h; Parte 2: ~3 h; Parte 3: ~2 h)
- **Cubre:** Todo el temario: qué es la nube, modelos de servicio y de implementación, responsabilidad compartida, regiones y zonas, cómputo, almacenamiento, red, bases de datos, identidad, escalabilidad, alta disponibilidad, costes, gobernanza.
- **Nivel:** Introductorio
- **Acceso:** Libre; cuenta Microsoft gratuita para el sandbox
- **Por qué lo recomiendo:** Es el material oficial de Microsoft para la certificación AZ-900 (Azure Fundamentals) y es exactamente el temario del curso, en español y con ejercicios en un sandbox que no cuesta nada. Es el recurso principal. Si al terminar quieres presentarte a la certificación, tendrás la base.

### ¿Qué es la informática en la nube? y Diccionario de la nube — Microsoft Azure
- **URL:** https://azure.microsoft.com/es-es/resources/cloud-computing-dictionary/what-is-cloud-computing (diccionario completo: https://azure.microsoft.com/es-es/resources/cloud-computing-dictionary)
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Artículos de referencia
- **Duración aproximada:** 30 min para las entradas: qué es la nube, tipos de nube, IaaS/PaaS/SaaS, qué es Azure, qué es una máquina virtual
- **Cubre:** Definiciones del temario.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Definiciones oficiales, cortas y en español, para tener el vocabulario claro antes de la ruta de aprendizaje. Ya lo viste en el curso de Historia.

### Cuenta gratuita de Azure: qué incluye y cómo evitar cargos — Microsoft
- **URL:** Página de la cuenta gratuita: https://azure.microsoft.com/es-es/pricing/purchase-options/azure-account · "Evitar cargos con su cuenta gratuita de Azure": https://learn.microsoft.com/es-es/azure/cost-management-billing/manage/avoid-charges-free-account · "Creación de servicios gratuitos con una cuenta gratuita": https://learn.microsoft.com/es-es/azure/cost-management-billing/manage/create-free-services
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Documentación oficial
- **Duración aproximada:** 30 min
- **Cubre:** Pago por uso, límites gratuitos, crédito inicial.
- **Nivel:** Introductorio
- **Acceso:** Libre (la cuenta requiere **tarjeta de crédito o débito no prepagada** para verificación; ver nota en el laboratorio)
- **Por qué lo recomiendo:** Lectura **obligatoria antes de crear la cuenta**. Explica qué es gratis, durante cuánto tiempo, qué pasa a los 30 días y cómo no pagar nada por accidente.

### Curso Completo AZ-900 Azure Fundamentals 2025 en Español (3 partes) — YouTube
- **URL:** Parte 1, Conceptos de Cloud: https://www.youtube.com/watch?v=pGqSIXHcVZ4 · Parte 3, Gobernanza, Seguridad y Administración: https://www.youtube.com/watch?v=aYmClk0rIvE (la parte 2 está enlazada desde cualquiera de los dos vídeos)
- **Autor / organización:** Canal de formación en Azure en español (verifica el autor en la propia página del vídeo)
- **Idioma:** Español
- **Tipo:** Vídeos largos
- **Duración aproximada:** 4-6 h en total
- **Cubre:** Todo el temario, siguiendo la estructura del AZ-900.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Complementario a Microsoft Learn para quien prefiere escuchar la explicación. Publicado en 2025 y alineado con el temario actual. Si encuentras discrepancias con Microsoft Learn, manda Microsoft Learn.

## Recursos en inglés

### AZ-900 Azure Fundamentals Certification Course — John Savill's Technical Training
- **URL:** Repositorio con el vídeo, el handout en PDF y los enlaces: https://github.com/johnthebrit/AZ900CertCourse (canal de YouTube: John Savill's Technical Training)
- **Autor / organización:** John Savill (Principal Cloud Solution Architect en Microsoft, divulgador independiente)
- **Idioma:** Inglés (subtítulos)
- **Tipo:** Curso en vídeo (una única sesión larga, actualizada periódicamente) + handout en PDF
- **Duración aproximada:** ~3 h el vídeo principal
- **Cubre:** Todo el temario con diagramas dibujados a mano en directo.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** John Savill es la referencia mundial en formación gratuita de Azure. Explica los conceptos dibujando, sin diapositivas de marketing, y entra en el "por qué" de cada servicio. Es el mejor complemento en inglés a Microsoft Learn. Su canal tiene además la serie "Azure Master Class", útil más adelante.

### Shared responsibility in the cloud — Microsoft Learn
- **URL:** https://learn.microsoft.com/en-us/azure/security/fundamentals/shared-responsibility
- **Autor / organización:** Microsoft
- **Idioma:** Inglés
- **Tipo:** Documentación oficial
- **Duración aproximada:** 15 min
- **Cubre:** Shared Responsibility Model, con el diagrama de quién gestiona qué en on-premises, IaaS, PaaS y SaaS.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la página oficial del concepto más importante del curso. El diagrama que contiene deberías poder reproducirlo de memoria.

### Quickstart: Create a Linux virtual machine in the Azure portal — Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/azure/virtual-machines/linux/quick-create-portal (en inglés: cambia `es-es` por `en-us`)
- **Autor / organización:** Microsoft
- **Idioma:** Español e inglés
- **Tipo:** Guía de inicio rápido paso a paso
- **Duración aproximada:** 20 min
- **Cubre:** Compute, networking e identidad en la práctica (crear VM, clave SSH, NSG, IP pública).
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la guía oficial exacta para la parte central del laboratorio. Sigue sus pasos, pero con los tamaños y opciones que indica el laboratorio para no gastar.

### What is Azure Cloud Shell? — Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/azure/cloud-shell/overview · Módulo introductorio: https://learn.microsoft.com/es-es/training/modules/intro-to-azure-cloud-shell/
- **Autor / organización:** Microsoft
- **Idioma:** Español e inglés
- **Tipo:** Documentación y módulo de aprendizaje
- **Duración aproximada:** 30 min
- **Cubre:** Introducción a Azure desde la línea de comandos (Azure CLI y Azure PowerShell en el navegador).
- **Nivel:** Introductorio
- **Acceso:** Libre (Cloud Shell necesita una cuenta de almacenamiento pequeña; se explica en el laboratorio)
- **Por qué lo recomiendo:** Cloud Shell es la forma más rápida de usar la CLI de Azure sin instalar nada. En el laboratorio harás por CLI lo mismo que hiciste por portal, para empezar a ver que el portal es solo una interfaz sobre una API.

## Documentación oficial

- **Microsoft Learn — Documentación de Azure (portal):** https://learn.microsoft.com/es-es/azure/
- **Microsoft Learn — Serie AZ-900 (ver recursos en español):** partes 1, 2 y 3.
- **Azure — Cuenta gratuita:** https://azure.microsoft.com/es-es/pricing/purchase-options/azure-account
- **Microsoft Learn — Evitar cargos con la cuenta gratuita:** https://learn.microsoft.com/es-es/azure/cost-management-billing/manage/avoid-charges-free-account
- **Azure — Calculadora de precios:** https://azure.microsoft.com/es-es/pricing/calculator/ · Cómo usarla: https://learn.microsoft.com/es-es/azure/cost-management-billing/costs/pricing-calculator
- **Microsoft Learn — Tutorial: creación y administración de presupuestos:** https://learn.microsoft.com/es-es/azure/cost-management-billing/costs/tutorial-acm-create-budgets
- **Microsoft Learn — Tamaños de máquinas virtuales:** https://learn.microsoft.com/es-es/azure/virtual-machines/sizes/overview (ya lo usaste en Hardware)
- **Microsoft Learn — Tipos de disco:** https://learn.microsoft.com/es-es/azure/virtual-machines/disks-types
- **Microsoft Learn — Responsabilidad compartida:** https://learn.microsoft.com/en-us/azure/security/fundamentals/shared-responsibility
- **Microsoft Learn — Azure Cloud Shell:** https://learn.microsoft.com/es-es/azure/cloud-shell/overview
- **Guía de estudio oficial AZ-900** (para quien quiera certificarse después): https://learn.microsoft.com/es-es/credentials/certifications/resources/study-guides/az-900

## Ruta recomendada de estudio

1. **Leer** las entradas del diccionario de la nube de Azure indicadas (30 min).
2. **Hacer** la Parte 1 de la serie AZ-900, "Descripción de los conceptos de la nube" (1,5 h). Al terminar debes poder explicar IaaS/PaaS/SaaS, nube pública/privada/híbrida, responsabilidad compartida, elasticidad, escalabilidad, alta disponibilidad y pago por uso.
3. **Leer** "Shared responsibility in the cloud" (15 min) y reproduce el diagrama a mano.
4. **Ver** el curso AZ-900 de John Savill, al menos la primera hora y media (conceptos, arquitectura, cómputo, red, almacenamiento) (90 min).
5. **Hacer** la Parte 2 de la serie, "Descripción de la arquitectura y los servicios de Azure" (3 h). Incluye ejercicios en sandbox donde creas una VM y un blob sin gastar nada: hazlos todos.
6. **Hacer** la Parte 3, "Descripción de la administración y gobernanza de Azure" (2 h). Céntrate en costes (calculadora, Cost Management, etiquetas) y en la idea de gobernanza; el resto se retoma en el Módulo Intermedio.
7. **Leer** con atención la documentación de la cuenta gratuita y "Evitar cargos" (30 min). No crees la cuenta hasta haberla leído.
8. **Ver** el resto del vídeo de John Savill o la serie en español, según prefieras (90 min, opcional).
9. **Hacer el laboratorio** (4-6 h, en dos sesiones: una para cuenta + presupuesto + almacenamiento, otra para la VM + CLI + limpieza).
10. **Responder la evaluación** y **revisar el checklist**.

## Laboratorio

### Objetivo

Crear una cuenta gratuita de Azure con control de costes desde el minuto uno, desplegar y explorar los recursos básicos (grupo de recursos, cuenta de almacenamiento, máquina virtual Linux con su red), repetir parte del trabajo desde la CLI, estimar costes con la calculadora y **eliminar todo** verificando que no queda gasto.

### Requisitos

- Tarjeta de crédito o débito no prepagada y teléfono. Lee antes las condiciones oficiales de la cuenta gratuita.
- Cuenta Microsoft.
- Tu clave SSH pública (`~/.ssh/id_ed25519.pub`) del curso de Linux/Git.
- Navegador y terminal.

> **Sobre el coste.** Todo lo que se crea en este laboratorio entra en los servicios gratuitos de la cuenta nueva (VM B1s o B2ats 750 h/mes durante 12 meses, almacenamiento LRS 5 GB, etc.) o se cubre con el crédito inicial de 200 USD durante los 30 primeros días. Aun así, la regla es: **presupuesto y alerta primero, recursos después, borrado al final**. Si algo del laboratorio te genera un cargo, es una señal de que algo se dejó encendido: revisa Cost Management y avisa al mentor.

### Instrucciones

Documenta en `laboratorio-cloud.md`. Las capturas del portal deben mostrar tu nombre de usuario o el nombre de tu suscripción.

**Parte A — Cuenta y control de costes (45-60 min)**

1. Crea la cuenta gratuita de Azure desde https://azure.microsoft.com/es-es/pricing/purchase-options/azure-account siguiendo la documentación oficial. Anota: fecha de creación (los 30 días del crédito cuentan desde aquí), nombre de la suscripción (por defecto "Azure subscription 1") y qué se te pidió para verificar identidad. Explica con tus palabras qué pasa a los 30 días y qué es el "límite de gasto" que trae la cuenta gratuita.
2. Entra en el portal (https://portal.azure.com). Localiza y captura: Suscripciones, Cost Management + Billing → Información general de la suscripción. Anota tu **ID de suscripción** (puedes ocultar parte en la captura) y tu **inquilino (tenant) de Entra ID**. Explica la relación cuenta → inquilino → suscripción → grupo de recursos → recurso.
3. Crea un **presupuesto** siguiendo el tutorial oficial de Cost Management: ámbito la suscripción, importe **10 USD** al mes, alertas al 50 %, 80 % y 100 % a tu correo. Captura. Explica por qué un presupuesto no impide el gasto y qué sí lo impediría (el límite de gasto de la cuenta gratuita, o borrar recursos).
4. Abre la **calculadora de precios** (https://azure.microsoft.com/es-es/pricing/calculator/) y estima el coste mensual, en tu región más cercana, de: una VM `B1s` Linux 730 h/mes con disco Standard SSD de 30 GB, una cuenta de almacenamiento con 10 GB en LRS y una VM `D2s_v5` 730 h/mes. Guarda la estimación (exportar o captura) y responde: ¿cuánto costaría dejar la `D2s_v5` encendida un año por descuido? ¿Cuánto te ahorras apagándola por la noche y fines de semana (~60 % del tiempo)?

**Parte B — Grupo de recursos y almacenamiento en el portal (45 min)**

5. Crea un grupo de recursos `rg-lab-cloud` en la región más cercana a ti (anota cuál y por qué la elegiste; mira en la Parte 2 de la serie AZ-900 qué es un par de regiones). Añade las etiquetas `curso=cloud-basico` y `propietario=<tu-usuario>`. Explica para qué sirve un grupo de recursos y para qué sirven las etiquetas en una empresa (coste, propietario, entorno).
6. Crea una **cuenta de almacenamiento** dentro del grupo: nombre único en minúsculas (por ejemplo `stlab<tusiniciales><4cifras>`), rendimiento Standard, redundancia **LRS** (la más barata; explica qué significa y qué otras opciones hay: ZRS, GRS). Crea un contenedor de blobs `documentos` con acceso privado y sube tu `linea-de-tiempo.md` del curso 1. Intenta abrir la URL del blob en una ventana privada del navegador: ¿qué obtienes y por qué? Genera una URL con SAS (firma de acceso compartido) de 1 hora y comprueba que ahora sí se puede leer. Explica el modelo de identidad/permiso que acabas de tocar.
7. En la cuenta de almacenamiento, abre Información general → pestaña de métricas o "Insights" y anota la capacidad usada. En Cost Management → Análisis de costos, filtra por el grupo `rg-lab-cloud`. Explica por qué puede tardar horas en aparecer el coste.

**Parte C — Máquina virtual Linux (60-90 min)**

8. Sigue la guía oficial de inicio rápido "Creación de una máquina virtual Linux en Azure Portal" con estos ajustes: grupo `rg-lab-cloud`, nombre `vm-lab-01`, imagen Ubuntu Server LTS, tamaño **B1s** (o el tamaño B que aparezca como gratuito en tu cuenta; si no aparece B1s, elige el más pequeño de la serie B), autenticación por **clave SSH pública** (pega la tuya, no generes una nueva), puertos de entrada permitidos: **solo SSH (22)**, disco Standard SSD, resto por defecto. Antes de pulsar "Crear", revisa la pestaña "Revisar y crear" y **anota el precio por hora** que muestra.
9. Cuando termine el despliegue, abre el grupo de recursos y lista **todos** los recursos que se crearon con la VM. Para cada uno (máquina virtual, disco, interfaz de red, IP pública, grupo de seguridad de red, red virtual) explica qué es y con qué concepto de los cursos de Hardware, SO y Redes se corresponde.
10. Copia la IP pública y conéctate por SSH desde tu equipo: `ssh azureuser@<ip-publica>` (o el usuario que hayas definido). Una vez dentro: `hostname`, `ip -br a` (fíjate en que la IP **privada** de la VM no es la pública: explica NAT/IP pública de Azure), `curl -s -H Metadata:true "http://169.254.169.254/metadata/instance?api-version=2021-02-01" | head -c 600` (el servicio de metadatos de Azure: explica qué te está diciendo), `df -h`, `free -h`, `lscpu | head -15`. Compara los recursos con los que estimaste en el curso de Hardware.
11. Instala nginx (`sudo apt update && sudo apt install -y nginx`) y comprueba desde tu equipo que `curl http://<ip-publica>` **no** responde. Ve al grupo de seguridad de red (NSG) en el portal, añade una regla de entrada que permita TCP 80 desde cualquier origen con prioridad 310, y comprueba que ahora responde. Explica qué es el NSG, en qué se parece a `ufw` y a un firewall de red, y por qué es mala idea abrir puertos "desde cualquier origen" en un servidor real.
12. **Detén** la VM desde el portal (Detener, no apagar desde dentro). Observa que el estado pasa a "Detenido (desasignado)". Explica la diferencia entre apagar desde el sistema operativo (sigue facturando cómputo) y desasignar desde Azure (deja de facturar cómputo pero sigue facturando el disco y la IP pública estática si la hay). Vuelve a iniciarla y comprueba si la IP pública cambió y por qué.

**Parte D — Lo mismo desde la línea de comandos (45 min)**

13. Abre **Azure Cloud Shell** desde el icono de terminal del portal (o https://shell.azure.com), elige Bash. La primera vez pedirá crear almacenamiento para tu perfil: acepta la opción más simple. Ejecuta y explica:
    ```bash
    az account show --output table
    az group list --output table
    az resource list --resource-group rg-lab-cloud --output table
    az vm list --resource-group rg-lab-cloud --show-details --output table
    az vm get-instance-view --resource-group rg-lab-cloud --name vm-lab-01 --query "instanceView.statuses[].displayStatus" --output tsv
    az storage account list --resource-group rg-lab-cloud --query "[].{nombre:name, sku:sku.name, region:location}" --output table
    ```
14. Crea desde la CLI un segundo grupo de recursos `rg-lab-cli` con etiquetas, y dentro una cuenta de almacenamiento LRS:
    ```bash
    az group create --name rg-lab-cli --location <tu-region> --tags curso=cloud-basico propietario=<tu-usuario>
    az storage account create --name stlabcli<sufijo> --resource-group rg-lab-cli --sku Standard_LRS --kind StorageV2
    ```
    Comprueba en el portal que aparecen. Explica en 5 líneas qué relación hay entre el portal, la CLI y la API de Azure Resource Manager, y por qué en la ruta acabarás usando la CLI y Terraform en vez del portal.
15. Detén la VM desde la CLI con desasignación: `az vm deallocate --resource-group rg-lab-cloud --name vm-lab-01` y verifica el estado con el comando del paso 13.

**Parte E — Limpieza y verificación de coste (30 min)**

16. Elimina los dos grupos de recursos: desde el portal `rg-lab-cloud` (observa que te pide escribir el nombre) y desde la CLI `az group delete --name rg-lab-cli --yes --no-wait`. Explica por qué borrar el grupo de recursos es la forma segura de "apagarlo todo".
17. Comprueba que no queda nada: `az resource list --output table` debe devolver vacío (salvo el almacenamiento de Cloud Shell, si lo creaste en su propio grupo; identifícalo y decide si lo conservas). Al día siguiente, entra en Cost Management → Análisis de costos y captura el coste acumulado del laboratorio. Debería ser cero o céntimos cubiertos por el crédito. Anota la cifra.
18. Escribe una sección "Responsabilidad compartida en mi laboratorio": para la VM (IaaS) y para la cuenta de almacenamiento (PaaS), lista qué gestionaba Microsoft y qué gestionabas tú, apoyándote en lo que hiciste (parches del SO, firewall, claves SSH, permisos del blob, hardware, red física, región).

### Resultado esperado

- Cuenta de Azure con presupuesto y alertas configurados.
- `laboratorio-cloud.md` con las cinco partes, capturas, la estimación de la calculadora y la verificación de coste del día siguiente.
- Ningún recurso de laboratorio vivo al terminar.

### Criterios de validación

- [ ] El presupuesto existe con las tres alertas, creado **antes** que los recursos (las capturas tienen fecha y hora).
- [ ] La jerarquía cuenta → inquilino → suscripción → grupo → recurso está explicada correctamente.
- [ ] La estimación de la calculadora es coherente y responde a las dos preguntas de coste.
- [ ] Los seis recursos que acompañan a la VM están identificados y relacionados con los conceptos de cursos anteriores.
- [ ] La prueba del NSG (puerto 80 cerrado → abierto) está documentada y la explicación de "detenido" frente a "desasignado" es correcta.
- [ ] Los comandos de la CLI están ejecutados y explicados; la relación portal/CLI/ARM está bien expresada.
- [ ] Todo está borrado y hay una captura de coste del día siguiente.
- [ ] La sección de responsabilidad compartida distingue correctamente IaaS (VM) de PaaS (almacenamiento).

## Entrega

En tu repositorio de entregas (por Git), carpeta `01-modulo-basico/08-introduccion-a-cloud-computing/`:

1. `laboratorio-cloud.md`.
2. `capturas/` (oculta el ID completo de suscripción y cualquier clave SAS; nunca subas claves de acceso de la cuenta de almacenamiento).
3. `estimacion-calculadora.*` (exportación o captura).
4. `ENTREGA.md` con evaluación, checklist y uso de IA.

## Evaluación

1. **Conceptual.** Define Cloud Computing con tus palabras. Un compañero dice "es tener servidores en el centro de datos de Microsoft en vez de en el nuestro". ¿Qué le falta a esa definición (piensa en elasticidad, pago por uso y autoservicio)?
2. **Conceptual.** Clasifica como IaaS, PaaS o SaaS: una VM de Azure, Azure SQL Database, Microsoft 365, Azure App Service, una cuenta de almacenamiento. Para cada uno di quién parchea el sistema operativo.
3. **Situacional.** Una empresa quiere mover su ERP a la nube pero por regulación algunos datos deben quedarse en su centro de datos. ¿Qué modelo de implementación encaja y qué implica para la red?
4. **Conceptual.** ¿Qué es una región, qué es un par de regiones y qué es una zona de disponibilidad? Si despliegas dos VMs en zonas distintas de la misma región, ¿de qué te proteges y de qué no?
5. **Conceptual.** Explica la diferencia entre escalar verticalmente y horizontalmente con el ejemplo de tu `vm-lab-01`. ¿Cuál requiere reinicio? ¿Cuál necesita un balanceador?
6. **Situacional.** Tu VM está "Detenida" desde el sistema operativo (`sudo shutdown`) desde hace un mes. Llega una factura de cómputo. Explica qué ha pasado y qué deberías haber hecho.
7. **Técnica.** Al crear la VM se crearon seis recursos. Si borras solo la VM, ¿qué queda y qué sigue costando dinero? ¿Cómo lo evitas?
8. **Situacional.** Necesitas que un servidor web sea accesible solo desde la oficina (IP pública 203.0.113.10) por HTTPS y por SSH solo desde tu casa. Describe las reglas del NSG.
9. **Conceptual.** Explica el modelo de responsabilidad compartida con tres ejemplos concretos de tu laboratorio: uno que siempre es de Microsoft, uno que siempre es tuyo y uno que depende del modelo de servicio.
10. **Técnica.** Estima con la calculadora el coste mensual de tres VMs `B2s` encendidas 8 horas al día, 22 días al mes. Explica qué factores cambiarían la cifra (región, sistema operativo con licencia, disco, tráfico de salida).
11. **Situacional.** Recibes una alerta del presupuesto al 80 % el día 10 del mes. Describe los tres pasos que darías en el portal para encontrar qué recurso está gastando y quién lo creó (pista: etiquetas, análisis de costos, registro de actividad).
12. **Conceptual.** ¿Qué es Azure Cloud Shell y por qué el portal, la CLI, PowerShell y Terraform acaban hablando con lo mismo? ¿Qué ventaja tiene la CLI sobre el portal para un equipo de operaciones?
13. **Conceptual.** Traduce a AWS y GCP (con ayuda de una búsqueda) estos conceptos de Azure: grupo de recursos, cuenta de almacenamiento con blobs, NSG, zona de disponibilidad. ¿Qué concepto de Azure no tiene equivalente exacto?
14. **Reflexión.** ¿Qué parte del laboratorio te resultó más parecida a lo que ya sabías (Linux, redes) y cuál fue realmente nueva? ¿Qué harías distinto para no gastar ni un céntimo?

## Checklist final

Antes de continuar, deberías poder:

- [ ] Definir Cloud Computing y contrastarlo con on-premises.
- [ ] Distinguir IaaS, PaaS y SaaS con ejemplos de Azure y decir quién gestiona qué.
- [ ] Distinguir nube pública, privada e híbrida.
- [ ] Explicar regiones, pares de regiones y zonas de disponibilidad.
- [ ] Nombrar un servicio de Azure de cómputo, almacenamiento, red, base de datos e identidad.
- [ ] Explicar elasticidad, escalabilidad vertical/horizontal y alta disponibilidad introductoria.
- [ ] Explicar pago por uso y estimar un coste con la calculadora.
- [ ] Crear presupuesto y alertas en Cost Management.
- [ ] Crear y borrar grupo de recursos, cuenta de almacenamiento y VM Linux desde el portal y la CLI.
- [ ] Conectarte por SSH a una VM de Azure y ajustar su NSG.
- [ ] Explicar detenido frente a desasignado y qué sigue costando dinero.
- [ ] Tener la cuenta de Azure limpia (sin recursos de laboratorio) y con presupuesto activo para los cursos siguientes.

---

*Recursos verificados el 2026-09-26 mediante búsqueda web (existencia y vigencia de las URLs). Las condiciones de la cuenta gratuita de Azure cambian con el tiempo: la página oficial manda sobre lo que aquí se describe. Si un enlace falla, abre un issue en este repositorio.*
