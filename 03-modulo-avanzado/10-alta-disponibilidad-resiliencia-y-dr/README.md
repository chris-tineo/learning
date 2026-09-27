# Alta Disponibilidad, Resiliencia y Disaster Recovery

> Módulo: Avanzado · Curso 10 de 12 · Duración estimada: 30-40 horas · Estado: ✅ Completo

## Objetivo

Hasta ahora has aprendido a construir plataformas que funcionan. Este curso trata de lo que pasa cuando dejan de funcionar: un disco que muere, una zona de disponibilidad que se cae, una región entera que desaparece durante horas, o alguien que ejecuta `DROP TABLE` en producción. La diferencia entre un incidente molesto y una empresa cerrada no está en la tecnología que compras, sino en dos preguntas que el negocio debe responder antes del desastre: **¿cuánto tiempo podemos estar parados?** (RTO) y **¿cuántos datos podemos perder?** (RPO). Todo lo demás (zonas, réplicas, backups, regiones secundarias, failover de DNS) son herramientas para cumplir esas dos cifras al menor coste posible.

En este curso vas a diseñar alta disponibilidad dentro de una región, diseñar recuperación ante desastres entre regiones, elegir el nivel de redundancia de cada dato y, sobre todo, **probar** que la recuperación funciona. Un plan de DR que nunca se ha ejecutado no es un plan, es una esperanza. El laboratorio termina simulando la pérdida de la región primaria de la aplicación del curso de Docker con su base de datos, levantándola en otra región con Terraform y midiendo el RTO y el RPO reales frente a los que prometiste.

Los conceptos son los mismos en Azure, AWS y GCP: cambian los nombres de los servicios (Azure Backup / AWS Backup, Traffic Manager / Route 53, región emparejada / región secundaria) pero no la lógica de decisión. Al terminar, esta forma de pensar te servirá para el Proyecto Final, donde tendrás que definir RTO, RPO, backup, failover y DR para tu propia plataforma.

**Antes de empezar** debes tener la aplicación del curso de Docker desplegable con Terraform (módulos del curso Terraform Avanzado), tu clúster local o AKS del curso de Kubernetes, y el hábito de coste: presupuesto activo, tamaños mínimos, borrado al final.

### Al terminar este curso deberías poder

- Explicar la diferencia entre alta disponibilidad, tolerancia a fallos, resiliencia, backup y disaster recovery, y por qué cada una protege frente a un tipo de fallo distinto.
- Definir RTO y RPO por componente a partir de un análisis de impacto en el negocio (BIA) y justificar el coste que implica cada cifra.
- Diseñar una arquitectura HA en una región usando zonas de disponibilidad, varias instancias detrás de un balanceador y una base de datos con réplica zonal.
- Comparar los patrones multi-región activo-pasivo (frío, tibio, caliente) y activo-activo, y elegir uno en función de RTO, RPO, coste y complejidad.
- Elegir el nivel de redundancia de Azure Storage (LRS, ZRS, GRS, GZRS, RA-GRS, RA-GZRS) para cada tipo de dato y demostrar una lectura real desde el endpoint secundario.
- Configurar backups y restauración point-in-time de PostgreSQL (servicio gestionado o `pg_dump`/`pg_basebackup` a Storage) y de una VM con Azure Backup, incluyendo la limpieza correcta del Recovery Services Vault.
- Explicar qué hace Azure Site Recovery, cuándo compensa frente a redesplegar con IaC y cuánto cuesta.
- Implementar failover de DNS con Traffic Manager o con Azure DNS y TTL bajo, y explicar sus límites.
- Ejecutar una prueba de DR completa, medir RTO y RPO reales y documentarla con un plan de DR, un runbook de failover y un informe de prueba.
- Situar el DR dentro de un marco de continuidad de negocio (BC) y explicar qué partes no son técnicas.

## Prerrequisitos

- Módulo Intermedio completo, en especial Docker (la aplicación), Terraform (despliegue), Administración de Azure y Monitoreo.
- Módulo Avanzado: Arquitectura Cloud Avanzada (multi-región conceptual, ADR), Terraform Avanzado (módulos por entorno), SRE Avanzado (SLO, riesgo) e Incident Management (runbooks, timeline).
- Cuenta de Azure con presupuesto y alertas activos. Azure CLI y Terraform instalados. Cliente `psql` en tu equipo o en `lab-so`.
- Repositorio de la aplicación del curso de Docker con su Terraform parametrizado por región.

## Temario

High Availability · Fault tolerance · Availability Zones · Multi-region · Redundancia · Replicación · Backups · Restore · RTO · RPO · Active-active · Active-passive · Failover · DR Plans · DR Testing · Business Continuity.

**Práctica:** diseñar y probar un plan de recuperación ante desastre.

## Recursos en español

### ¿Qué es Azure Backup? e Información general de los almacenes de Recovery Services — Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/azure/backup/backup-overview · Almacenes: https://learn.microsoft.com/es-es/azure/backup/backup-azure-recovery-services-vault-overview
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Documentación oficial
- **Duración aproximada:** 1 h
- **Cubre:** Backups, Restore, redundancia del almacén, soft delete, qué cargas protege Azure Backup.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la referencia del servicio que usarás en la Parte D. Léelo antes de crear el vault para entender por qué borrarlo después no es un `az group delete` y ya.

### Ruta AZ-104: Supervisión y copia de seguridad de recursos de Azure — Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/training/paths/az-104-monitor-backup-resources/ · Módulo clave: https://learn.microsoft.com/es-es/training/modules/protect-virtual-machines-with-azure-backup/ · Diseño de backup y DR (nivel AZ-305): https://learn.microsoft.com/es-es/training/modules/design-solution-for-backup-disaster-recovery/
- **Autor / organización:** Microsoft
- **Idioma:** Español (cambia `es-es` por `en-us` para la versión original)
- **Tipo:** Ruta de aprendizaje con ejercicios
- **Duración aproximada:** 3-4 h (solo los módulos de backup y DR)
- **Cubre:** Backups, Restore, Azure Backup, Site Recovery, criterios de diseño de RTO/RPO.
- **Nivel:** Intermedio
- **Acceso:** Libre; cuenta Microsoft gratuita para guardar progreso
- **Por qué lo recomiendo:** El módulo de diseño (AZ-305) obliga a razonar RTO/RPO frente a coste, que es exactamente el ejercicio de la Parte A. El de AZ-104 te da la mecánica del vault, políticas y restauración.

### Pilar de confiabilidad del Azure Well-Architected Framework — Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/azure/well-architected/reliability/ · Módulo de training: https://learn.microsoft.com/es-es/training/modules/azure-well-architected-reliability/
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Documentación oficial y módulo de aprendizaje
- **Duración aproximada:** 3 h (principios, lista de comprobación, redundancia, estrategia de pruebas, recuperación ante desastres)
- **Cubre:** High Availability, Fault tolerance, Redundancia, DR Plans, DR Testing, métricas de confiabilidad.
- **Nivel:** Avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es el marco con el que Microsoft revisa arquitecturas reales. Los artículos de "estrategia de pruebas" y "recuperación ante desastres" son la base de tu plan de DR; la lista de comprobación es lo que usará el mentor para revisar tu diseño.

### Redundancia de Azure Storage — Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/azure/storage/common/storage-redundancy
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Documentación oficial
- **Duración aproximada:** 45 min
- **Cubre:** Redundancia, Replicación, LRS/ZRS/GRS/GZRS/RA-GRS/RA-GZRS, RPO de la replicación asíncrona, failover de cuenta.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** La tabla de durabilidad y las secciones sobre qué cubre cada opción (fallo de disco, de zona, de región) son la mejor explicación práctica de "redundancia" que existe. La Parte C del laboratorio la pone a prueba leyendo del secundario.

## Recursos en inglés

### Azure reliability documentation: regions, availability zones, region pairs and BCDR concepts — Microsoft Learn
- **URL:** https://learn.microsoft.com/en-us/azure/reliability/overview · Regiones: https://learn.microsoft.com/en-us/azure/reliability/regions-overview · Zonas: https://learn.microsoft.com/en-us/azure/reliability/availability-zones-overview · Pares de regiones: https://learn.microsoft.com/en-us/azure/reliability/regions-paired · Conceptos HA/DR/BC: https://learn.microsoft.com/en-us/azure/reliability/concept-business-continuity-high-availability-disaster-recovery
- **Autor / organización:** Microsoft
- **Idioma:** Inglés
- **Tipo:** Documentación oficial
- **Duración aproximada:** 2 h
- **Cubre:** Availability Zones, Multi-region, Redundancia, Business Continuity, diferencias entre HA y DR.
- **Nivel:** Intermedio-avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** Aclara dos malentendidos frecuentes: que desplegar en una región emparejada no te da DR automáticamente, y que muchas regiones nuevas no tienen par. Léelo antes de elegir tus dos regiones.

### Develop a disaster recovery plan for multi-region deployments y Multi-region App Service architectures — Azure Well-Architected Framework y Architecture Center
- **URL:** https://learn.microsoft.com/en-us/azure/well-architected/design-guides/disaster-recovery · Zonas y regiones: https://learn.microsoft.com/en-us/azure/well-architected/design-guides/regions-availability-zones · App Service multi-región: https://learn.microsoft.com/en-us/azure/architecture/web-apps/guides/multi-region-app-service/multi-region-app-service · Catálogo de patrones: https://learn.microsoft.com/en-us/azure/architecture/patterns
- **Autor / organización:** Microsoft
- **Idioma:** Inglés
- **Tipo:** Guías de diseño
- **Duración aproximada:** 3 h
- **Cubre:** Active-active, Active-passive, Failover, DR Plans, patrones de resiliencia (retry, circuit breaker, bulkhead, queue-based load leveling).
- **Nivel:** Avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** La guía de DR es el documento que más se parece a lo que tendrás que escribir en el laboratorio. La arquitectura multi-región de App Service muestra las tres variantes (activo-pasivo con standby frío, tibio y caliente) con sus costes relativos.

### Data Integrity: What You Read Is What You Wrote (SRE Book, capítulo 26) — Google
- **URL:** https://sre.google/sre-book/data-integrity/
- **Autor / organización:** Google SRE
- **Idioma:** Inglés
- **Tipo:** Capítulo de libro (gratuito online)
- **Duración aproximada:** 1,5 h
- **Cubre:** Backups frente a restores, defensa en profundidad (soft delete, backups, replicación), por qué "nadie quiere backups, todos quieren restores".
- **Nivel:** Avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** Cambia la perspectiva: el objetivo no es hacer copias, es poder recuperar datos dentro del RPO y el RTO. Sus 24 combinaciones de fallo y su insistencia en probar restauraciones justifican la Parte E del laboratorio.

### Reliability Pillar y Disaster Recovery of Workloads on AWS — AWS Well-Architected (comparación)
- **URL:** https://docs.aws.amazon.com/wellarchitected/latest/reliability-pillar/welcome.html · Opciones de DR: https://docs.aws.amazon.com/whitepapers/latest/disaster-recovery-workloads-on-aws/disaster-recovery-options-in-the-cloud.html · Equivalente en GCP: https://cloud.google.com/architecture/dr-scenarios-planning-guide
- **Autor / organización:** Amazon Web Services y Google Cloud
- **Idioma:** Inglés
- **Tipo:** Documentación oficial
- **Duración aproximada:** 1,5 h (solo las secciones de DR)
- **Cubre:** RTO, RPO, las cuatro estrategias clásicas (backup and restore, pilot light, warm standby, multi-site active-active) y cómo se traducen entre proveedores.
- **Nivel:** Avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** La clasificación de AWS (backup/restore, pilot light, warm standby, active-active) es el vocabulario que oirás en entrevistas y en equipos multi-cloud. Úsala para nombrar tu diseño aunque lo implementes en Azure.

### Azure Master Class v2, Module 4: Resiliency — John Savill's Technical Training
- **URL:** https://www.youtube.com/watch?v=iX87AomIqTw · Repositorio con materiales: https://github.com/johnthebrit/AzureMasterClass
- **Autor / organización:** John Savill
- **Idioma:** Inglés (subtítulos automáticos)
- **Tipo:** Vídeo largo
- **Duración aproximada:** ~2,5 h
- **Cubre:** Zonas, pares de regiones, replicación síncrona y asíncrona, Azure Backup, Site Recovery, Traffic Manager y Front Door, diseño multi-región.
- **Nivel:** Intermedio-avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** Dibuja en pizarra la diferencia entre replicación síncrona (zonal) y asíncrona (regional) y por qué la segunda siempre implica RPO mayor que cero. Es la mejor explicación visual de todo el temario en una sola sesión.

### Backup and Restore (PostgreSQL Documentation, capítulo 25) — PostgreSQL Global Development Group
- **URL:** https://www.postgresql.org/docs/current/backup.html · `pg_dump`: https://www.postgresql.org/docs/current/app-pgdump.html · `pg_basebackup`: https://www.postgresql.org/docs/current/app-pgbasebackup.html · Archivado continuo y PITR: https://www.postgresql.org/docs/current/continuous-archiving.html
- **Autor / organización:** PostgreSQL Global Development Group
- **Idioma:** Inglés
- **Tipo:** Documentación oficial
- **Duración aproximada:** 2 h
- **Cubre:** Backups, Restore, point-in-time recovery, diferencia entre volcado lógico y copia física.
- **Nivel:** Intermedio-avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** Aunque uses el servicio gestionado, necesitas entender qué hay debajo (snapshots más WAL) para razonar el RPO. Si usas PostgreSQL en VM, es tu manual de operación.

## Documentación oficial

- **Azure Backup:** portal de documentación https://learn.microsoft.com/en-us/azure/backup/ · Backup de VM en el portal: https://learn.microsoft.com/en-us/azure/backup/quick-backup-vm-portal · Backup de VM con CLI: https://learn.microsoft.com/en-us/azure/backup/quick-backup-vm-cli · Restaurar VM o discos: https://learn.microsoft.com/en-us/azure/backup/backup-azure-arm-restore-vms · Soft delete: https://learn.microsoft.com/en-us/azure/backup/backup-azure-security-feature-cloud · **Eliminar un Recovery Services Vault (léelo antes de crear el vault):** https://learn.microsoft.com/en-us/azure/backup/backup-azure-delete-vault
- **Azure Site Recovery:** https://learn.microsoft.com/en-us/azure/site-recovery/site-recovery-overview · Módulo introductorio: https://learn.microsoft.com/en-us/training/modules/intro-to-azure-site-recovery/
- **Azure Storage:** redundancia https://learn.microsoft.com/en-us/azure/storage/common/storage-redundancy · Diseño de aplicaciones con RA-GRS: https://learn.microsoft.com/en-us/azure/storage/common/geo-redundant-design · Guía de DR y failover de cuenta: https://learn.microsoft.com/en-us/azure/storage/common/storage-disaster-recovery-guidance
- **Azure Database for PostgreSQL flexible server:** información general https://learn.microsoft.com/en-us/azure/postgresql/flexible-server/overview · Backup y restore (PITR): https://learn.microsoft.com/en-us/azure/postgresql/backup-restore/concepts-backup-restore · Continuidad de negocio: https://learn.microsoft.com/en-us/azure/postgresql/backup-restore/concepts-business-continuity · Alta disponibilidad zonal: https://learn.microsoft.com/en-us/azure/postgresql/flexible-server/concepts-high-availability · Restore por CLI: https://learn.microsoft.com/en-us/azure/postgresql/samples/sample-point-in-time-restore
- **Cómputo HA:** Virtual Machine Scale Sets con zonas https://learn.microsoft.com/en-us/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-use-availability-zones · Azure Load Balancer: https://learn.microsoft.com/en-us/azure/load-balancer/load-balancer-overview
- **Failover de DNS:** Traffic Manager https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview · Cómo funciona: https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-how-it-works · Enrutamiento por prioridad: https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-configure-priority-routing-method · Azure DNS: https://learn.microsoft.com/en-us/azure/dns/dns-overview
- **Marco de continuidad de negocio:** Cloud Adoption Framework, BCDR https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/landing-zone/design-area/management-business-continuity-disaster-recovery · NIST SP 800-34 Rev. 1, Contingency Planning Guide (BIA, planes de contingencia): https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-34r1.pdf
- **Precios (consúltalos antes de cada parte del laboratorio):** Azure Backup https://azure.microsoft.com/en-us/pricing/details/backup/ · Site Recovery https://azure.microsoft.com/en-us/pricing/details/site-recovery/ · Traffic Manager https://azure.microsoft.com/en-us/pricing/details/traffic-manager/ · PostgreSQL https://azure.microsoft.com/en-us/pricing/details/postgresql/ · Calculadora: https://azure.microsoft.com/es-es/pricing/calculator/

## Ruta recomendada de estudio

1. **Leer** los conceptos de HA/DR/BC, regiones, zonas y pares de regiones de la documentación de confiabilidad de Azure (2 h). Anota qué regiones tienen zonas y cuál es (o no es) tu par de región.
2. **Ver** el módulo de Resiliency de John Savill (2,5 h), con papel: dibuja replicación síncrona y asíncrona y escribe al lado qué RPO permite cada una.
3. **Leer** el pilar de confiabilidad del Well-Architected Framework: principios, lista de comprobación, redundancia, estrategia de pruebas y recuperación ante desastres (3 h). Haz el módulo de training asociado.
4. **Leer** el capítulo Data Integrity del SRE Book (1,5 h). Escribe tres frases propias sobre por qué "backup" y "restore" no son lo mismo.
5. **Leer** las opciones de DR de AWS y la guía de GCP (1,5 h) y prepara una tabla de equivalencias Azure / AWS / GCP para los cuatro patrones.
6. **Hacer** el módulo de diseño de backup y DR (AZ-305) y el de protección de VMs con Azure Backup (3 h). Aquí ya debes poder redactar RTO/RPO justificados.
7. **Leer** la redundancia de Azure Storage y el diseño con RA-GRS (1,5 h), y la documentación de backup/restore de PostgreSQL flexible o el capítulo 25 de PostgreSQL según la opción que vayas a usar (2 h).
8. **Leer** Traffic Manager (overview, cómo funciona, enrutamiento por prioridad) y la página de borrado del Recovery Services Vault (1 h).
9. **Hacer el laboratorio** (18-24 h en varias sesiones; la Parte E requiere una sesión larga sin interrupciones).
10. **Responder la evaluación** y **revisar el checklist**.

## Laboratorio

### Objetivo

Diseñar, implementar en pequeño y **probar** un plan de recuperación ante desastre para la aplicación del curso de Docker con su base de datos PostgreSQL y sus adjuntos en Storage: definir RTO y RPO por componente, diseñar HA en una región y DR multi-región, elegir redundancia de datos, hacer backups y restauraciones reales, configurar failover de DNS, simular la pérdida de la región primaria, levantar en la secundaria, medir RTO y RPO reales y documentarlo todo con las plantillas de este curso.

### Escenario de negocio

**TurnoYa** es un SaaS pequeño de gestión de citas para clínicas dentales. La aplicación del curso de Docker es su API (`/health`, `/version`); la base de datos PostgreSQL guarda pacientes, agendas y citas; una cuenta de Storage guarda adjuntos (radiografías en PDF). Datos que te da el negocio:

- 40 clínicas, horario de uso 08:00-20:00 de lunes a sábado. Fuera de ese horario el uso es marginal.
- Una hora sin sistema en horario de clínica cuesta unos 1.500 EUR en citas perdidas y llamadas manuales. Más de un día sin servicio provoca cancelaciones de contrato.
- Perder citas creadas en la última hora es "muy molesto pero recuperable llamando"; perder más de un día de citas es inaceptable por contrato.
- Los adjuntos se suben una vez y casi nunca cambian; perder los de las últimas 24 h es aceptable (la clínica los vuelve a subir).
- Presupuesto de infraestructura actual: 400 EUR/mes. El negocio acepta subirlo hasta un 30 % por resiliencia, no más.

Con esto tienes que decidir RTO y RPO por componente. No hay una respuesta única; hay respuestas justificadas y respuestas sin justificar.

### Requisitos

- Repositorio de la aplicación con Terraform parametrizado por región (variables `location`, `location_secondary`, sufijo de nombres) y backend remoto en una cuenta de Storage **fuera** de los grupos de recursos que vas a destruir.
- Azure CLI, Terraform, `psql` y `pg_dump` (paquete `postgresql-client` en Ubuntu).
- Dos regiones elegidas: primaria con zonas de disponibilidad y secundaria (su par si existe, o la más cercana con zonas).
- Documentación en `laboratorio-dr.md` más los cuatro documentos de las plantillas.

> **Sobre el coste.** Estimación total del laboratorio si lo haces en 4-5 días y borras cada bloque al terminarlo: **entre 3 y 10 USD**. Desglose orientativo: Storage RA-GRS con pocos MB (céntimos), 2 VMs B1s en zonas más Standard Load Balancer durante 2-3 h (menos de 1 USD), PostgreSQL flexible Burstable B1ms unos días (0,5 USD/día aprox.; si aún estás dentro de los 12 meses gratuitos de la cuenta, B1ms 750 h/mes puede estar cubierto, compruébalo en Cost Management), Azure Backup de una VM pequeña unos días (1-2 USD), Traffic Manager (céntimos), despliegue en la región secundaria durante la prueba (1-2 USD). Lo que **sigue cobrando** si lo olvidas: el Recovery Services Vault con datos, el servidor PostgreSQL, IPs públicas estáticas, discos huérfanos y el Load Balancer Standard. Cada parte termina con su limpieza; no las pospongas. Site Recovery, Front Door, Application Gateway y App Service Premium con redundancia de zona se tratan solo a nivel conceptual.

### Instrucciones

**Parte A — BIA, RTO y RPO por componente (3 h, sin gastar)**

1. Rellena la plantilla **BIA simplificado** (al final del laboratorio) para TurnoYa: procesos de negocio (reservar cita, consultar agenda, subir adjunto, facturar), impacto por hora de parada, dependencias técnicas de cada proceso.
2. Define **RTO y RPO por componente** (API, PostgreSQL, Storage de adjuntos, DNS, pipeline/Terraform, secretos) en una tabla. Para cada cifra escribe una frase de justificación que cite un dato del escenario y una estimación de coste mensual de cumplirla. Ejemplo de razonamiento (no de respuesta): "RPO PostgreSQL 15 min porque perder una hora de citas es molesto pero un día es inaceptable; la replicación asíncrona de backups cada 5 min lo cubre por X EUR/mes".
3. Escribe un **ADR** (formato del curso de Arquitectura) con la decisión de estrategia de DR: backup/restore, pilot light, warm standby o active-active, y por qué, dentro del límite del 30 % de presupuesto extra. Incluye la tabla de equivalencias Azure / AWS / GCP de la ruta de estudio.

**Parte B — Alta disponibilidad en una región (4-5 h, recursos vivos 2-3 h como máximo)**

4. Diseña en un diagrama la arquitectura HA regional: zonas 1, 2 y 3; al menos dos instancias de la API repartidas en zonas detrás de un balanceador; PostgreSQL flexible con alta disponibilidad zonal (réplica síncrona en otra zona, conceptual por coste, se activa con `--high-availability ZoneRedundant`); Storage ZRS o superior. Explica qué fallo tolera cada elemento y cuál **no** (una región completa).
5. Prueba real y acotada: crea con Terraform (o Azure CLI si prefieres) un grupo `rg-dr-ha` con un **Virtual Machine Scale Set** en modo flexible, 2 instancias `Standard_B1s` en `zones = ["1","2"]`, con `cloud-init` que instale Docker y arranque la imagen de la aplicación del curso de Docker en el puerto 80, detrás de un **Azure Load Balancer Standard** con sonda de estado a `/health`. Comprueba con `curl` repetido a la IP del balanceador que el `hostname` que devuelve `/version` alterna entre las dos instancias.
6. Simula el fallo de una zona: `az vm deallocate` (o `az vmss ... deallocate --instance-ids`) sobre la instancia de la zona 1. Repite el `curl` en bucle durante el apagado: anota cuántas peticiones fallaron y durante cuántos segundos hasta que la sonda retiró el backend. Ese número es tu **RTO real de un fallo zonal**. Relaciónalo con el intervalo y el umbral de la sonda y propón valores mejores.
7. Explica por escrito la alternativa PaaS: App Service con varias instancias y redundancia de zona (solo en planes Premium v3 o superiores, consulta la documentación de hosting plans y su coste) frente a VMSS; y qué aporta Application Gateway o Front Door frente a un Load Balancer (capa 7, WAF, coste fijo mensual alto). Borra `rg-dr-ha` al terminar esta parte y verifica con `az resource list`.

**Parte C — Redundancia y replicación de datos (3-4 h)**

8. Crea en la región primaria una cuenta de Storage `stturnoya<sufijo>` con SKU `Standard_RAGRS` y un contenedor `adjuntos`. Sube 3-4 archivos PDF de prueba. Consulta `az storage account show --name <cuenta> --expand geoReplicationStats --query geoReplicationStats` y anota `lastSyncTime`: la diferencia con la hora actual es tu **RPO real de Storage** en ese momento.
9. Lee **desde el endpoint secundario**: obtén `secondaryEndpoints.blob` con `az storage account show`, y descarga un blob con `az storage blob download --blob-endpoint https://<cuenta>-secondary.blob.core.windows.net ...` (o con `curl` y una SAS de lectura). Documenta que el secundario es de **solo lectura** intentando subir algo por ese endpoint y capturando el error. Explica qué cambiaría con GZRS/RA-GZRS y cuánto cuesta cada SKU para 100 GB (calculadora).
10. Base de datos, elige una opción y justifícala frente a la otra en dos párrafos:
    - **Opción gestionada (recomendada si el coste lo permite):** `az postgres flexible-server create` con `--sku-name Standard_B1ms --tier Burstable --storage-size 32 --backup-retention 7 --version 16` en la región primaria (añade `--geo-redundant-backup Enabled` solo si quieres probar geo-restore; duplica el coste del almacenamiento de backup). Crea la base `turnoya`, la tabla `citas` y carga 200 filas con un script Python o SQL. Anota la hora exacta, inserta 20 filas más, borra "por error" la tabla. Restaura con `az postgres flexible-server restore --restore-time "<hora antes del borrado>" --name <servidor>-restaurado ...`. Mide cuánto tarda (RTO del restore) y cuenta filas recuperadas (RPO real). Borra el servidor restaurado.
    - **Opción en VM:** PostgreSQL en una VM B1s (o en `lab-so` para la parte lógica): `pg_dump -Fc turnoya > turnoya.dump`, súbelo a un contenedor `backups` de la cuenta RA-GRS con `az storage blob upload`, programa el volcado cada 15 min con `cron` o un timer de `systemd`, y documenta cómo `pg_basebackup` más archivado de WAL permitiría PITR con RPO de segundos. Restaura el dump en una base vacía con `pg_restore` y mide el tiempo.
11. Escribe la sección **"Matriz de redundancia"** de tu plan: para cada dato (base de datos, adjuntos, estado de Terraform, imágenes de contenedor, secretos) indica dónde vive, cómo se replica, RPO teórico, RPO medido y qué fallo cubre.

**Parte D — Azure Backup de una VM y Site Recovery (3-4 h)**

12. Crea una VM `vm-turnoya-01` B1s (Ubuntu, disco Standard SSD de 30 GB) en `rg-dr-backup`, con un archivo `/home/azureuser/marca-$(date +%F-%H%M).txt` dentro. Crea un **Recovery Services Vault** en el mismo grupo con redundancia **LRS** (por defecto es GRS: cámbialo antes de proteger nada, y explica por qué en producción probablemente lo dejarías en GRS). Activa la protección de la VM con la política por defecto y lanza un **backup bajo demanda** (`az backup protection backup-now`). Anota cuánto tarda el primer backup (puede ser 20-40 min) y cuál es el coste mensual por instancia protegida según la página de precios.
13. Borra el archivo de marca en la VM y **restaura**: primero como discos a una cuenta de Storage temporal (`az backup restore restore-disks`) y después como VM nueva (`vm-turnoya-restaurada`), o usa la restauración a nivel de archivo desde el portal. Verifica que el archivo existe en la VM restaurada. Anota el tiempo total: es tu **RTO de restaurar una VM** desde backup.
14. **Limpieza del vault, en este orden y documentando cada paso** (sigue la página oficial de eliminación del vault): deshabilitar soft delete en las propiedades de seguridad del vault, detener la protección de la VM **con eliminación de datos** (`az backup protection disable --delete-backup-data true`), comprobar que no quedan elementos ni contenedores registrados, y entonces borrar el vault y el grupo. Explica qué habría pasado si hubieras intentado `az group delete` directamente y por qué el soft delete existe (ransomware, borrados accidentales).
15. Azure Site Recovery, **solo lectura y cálculo**: explica qué replica (discos de VM entre regiones con RPO de minutos), qué no replica (PaaS, Storage, bases gestionadas), qué es un plan de recuperación y qué es un failover de prueba. Calcula el coste de proteger tus 2 VMs de la Parte B durante un año (precio por instancia protegida más almacenamiento replicado) y compáralo con redesplegar con Terraform más restaurar datos. Decide para TurnoYa y justifícalo.

**Parte E — Prueba de DR completa (6-8 h en una sesión)**

16. Prepara el **runbook de failover** con la plantilla de este curso, antes de tocar nada. Debe incluir: criterio de declaración de desastre y quién lo decide, pasos numerados con comando exacto y responsable, puntos de verificación, plan de vuelta atrás (failback) y comunicación.
17. Configura el failover de DNS. Opción barata y automática: perfil de **Traffic Manager** con enrutamiento por **prioridad**, endpoint 1 la IP pública (o FQDN) de la región primaria y endpoint 2 la de la secundaria (crea de momento solo el primario; el secundario se añade en el paso 20), sonda HTTP a `/health` cada 30 s, TTL de 60 s. Opción manual: registro A en una zona de **Azure DNS** con TTL 60 que cambiarás a mano. Explica el límite de ambas: el TTL y las cachés de los resolvedores intermedios hacen que el failover de DNS nunca sea instantáneo.
18. Despliega la **región primaria** completa con Terraform: `rg-turnoya-pri` con la API (una VM B1s con Docker es suficiente aquí, la HA ya la probaste), la base PostgreSQL (opción elegida en la Parte C) y la cuenta de Storage RA-GRS con los adjuntos. Carga datos, anota la hora y el número de filas, y activa el backup periódico (retención del servicio gestionado, o el `cron` de `pg_dump` cada 15 min hacia la cuenta RA-GRS). Comprueba que `curl http://<perfil>.trafficmanager.net/health` responde.
19. **Declara el desastre.** Anota la hora exacta `T0`. Simula la pérdida de la región: `az group delete --name rg-turnoya-pri --yes --no-wait` (o, si quieres conservar la posibilidad de failback rápido, `az vm deallocate` de la API y `az postgres flexible-server stop`; documenta cuál elegiste y por qué la eliminación es la simulación más honesta). La sonda de Traffic Manager debe marcar el endpoint como degradado en 1-2 minutos: anótalo.
20. Ejecuta el runbook: `terraform apply` con `location = <secundaria>` y sufijo `-sec` para levantar API, servidor PostgreSQL vacío y lo necesario; restaura los datos desde la copia más reciente (geo-restore del flexible server si activaste geo-backup, o `pg_restore` del último dump leído **desde el endpoint secundario** de la cuenta RA-GRS, porque la primaria "ya no existe"); apunta los adjuntos a la misma cuenta RA-GRS (solo lectura hasta iniciar un failover de cuenta, que **no** vas a ejecutar por coste y tiempo: explícalo); añade el endpoint secundario a Traffic Manager o cambia el registro A. Anota la hora en que `curl http://<perfil>.trafficmanager.net/health` devuelve 200 desde la secundaria: `T1`.
21. Mide: **RTO real = T1 - T0**. **RPO real** = hora de la última cita presente en la base restaurada frente a la última insertada antes de `T0` (compara con el número de filas). Compara ambos con los objetivos de la Parte A. Si no los cumples, no maquilles la tabla: escribe qué cambiarías (frecuencia de backup, warm standby, automatizar el runbook) y cuánto costaría.
22. Rellena el **informe de prueba de DR** con la plantilla: cronología con horas, desviaciones respecto al runbook, problemas encontrados, RTO/RPO objetivo frente a real, acciones correctivas con responsable y fecha. Actualiza el runbook con lo aprendido (un runbook que no cambia tras una prueba es sospechoso).
23. **Limpieza total:** `terraform destroy` en la secundaria, borrado de los grupos restantes, del perfil de Traffic Manager y de la zona DNS si la creaste. Conserva solo la cuenta del backend de Terraform. Al día siguiente captura Cost Management filtrado por los grupos del curso y anota el gasto real frente a la estimación.

**Parte F — Plan de DR y continuidad de negocio (2-3 h)**

24. Escribe el **DR plan** completo con la plantilla, integrando: alcance, BIA, RTO/RPO, arquitectura primaria y secundaria (diagramas), matriz de redundancia, estrategia de backup y retención, runbook de failover y failback, calendario de pruebas (mínimo semestral), roles y contactos, criterios de mejora.
25. Añade una sección **"Continuidad de negocio más allá de la tecnología"**: qué hace el personal de las clínicas durante el RTO (agenda en papel, teléfono), quién comunica a los clientes, qué pasa si el desastre coincide con vacaciones del único ingeniero, y qué exige el RGPD/normativa sanitaria sobre disponibilidad e integridad de datos. Apóyate en el marco del CAF y de NIST SP 800-34 para la estructura, no para copiar texto.

### Plantillas

Copia estas cuatro plantillas a tu carpeta de entrega y rellénalas. Amplía secciones si lo necesitas; no borres ninguna.

**Plantilla 1: BIA simplificado (`bia.md`)**

```markdown
# Análisis de impacto en el negocio (BIA): <servicio>
| Proceso de negocio | Impacto/hora de parada (EUR y descripción) | Impacto por pérdida de datos | Dependencias técnicas | Ventana crítica | MTD (máximo tiempo tolerable) |
|---|---|---|---|---|---|
| Reservar cita | | | API, PostgreSQL, DNS | L-S 08:00-20:00 | |
## Componentes y objetivos derivados
| Componente | RTO objetivo | RPO objetivo | Justificación (cita un dato del escenario) | Coste mensual estimado de cumplirlo |
|---|---|---|---|---|
## Supuestos y límites
```

**Plantilla 2: Plan de recuperación ante desastres (`dr-plan.md`)**

```markdown
# Plan de DR: <servicio>  ·  Versión <x.y>  ·  Fecha  ·  Propietario
1. Alcance y escenarios cubiertos (fallo zonal, fallo regional, borrado lógico, ransomware) y NO cubiertos
2. Resumen del BIA y tabla RTO/RPO por componente
3. Arquitectura: región primaria, región secundaria, diagrama, estrategia (backup/restore, pilot light, warm standby, active-active) y ADR asociado
4. Matriz de redundancia de datos (dato, ubicación, replicación, RPO teórico, RPO medido, fallo que cubre)
5. Estrategia de backup: qué, frecuencia, retención, redundancia del almacén, cifrado, soft delete, pruebas de restauración
6. Detección y declaración de desastre (señales, umbrales, quién decide) y runbooks enlazados: failover, failback, restauración de datos
7. Roles y contactos (primario y suplente), cadena de escalado y comunicación (plantillas para clientes, dirección y equipo; canales alternativos)
8. Calendario de pruebas (revisión de mesa, parcial, completa) e histórico de resultados
9. Dependencias externas (DNS, identidad, correo, pipeline) y su propio DR; registro de cambios
```

**Plantilla 3: Runbook de failover (`runbook-failover.md`)**

```markdown
# Runbook: failover de <servicio> a <región secundaria>
- Cuándo ejecutarlo / cuándo NO (criterios objetivos)  ·  Quién autoriza  ·  RTO/RPO esperados  ·  Última prueba y resultado
## Precondiciones (checklist)
- [ ] Acceso a la suscripción con rol X  - [ ] Backend de Terraform accesible  - [ ] Último backup verificado a las __:__  - [ ] Comunicación inicial enviada
## Pasos
| # | Acción | Comando exacto | Responsable | Duración esperada | Verificación | Si falla |
|---|---|---|---|---|---|---|
| 1 | Declarar desastre y anotar T0 | | | | | |
## Vuelta atrás (failback) y limpieza
## Registro de ejecución (hora real de cada paso, desviaciones)
```

**Plantilla 4: Informe de prueba de DR (`informe-prueba-dr.md`)**

```markdown
# Informe de prueba de DR: <servicio>  ·  Fecha  ·  Tipo de prueba  ·  Participantes
## Objetivo y alcance de la prueba
## Cronología (hora, evento, quién, evidencia)
## Resultados
| Métrica | Objetivo | Real | Cumple | Comentario |
|---|---|---|---|---|
| RTO | | | | |
| RPO | | | | |
## Desviaciones respecto al runbook y problemas encontrados
## Acciones correctivas (acción, responsable, fecha, prioridad)
## Cambios aplicados al runbook y al plan de DR
## Coste de la prueba
```

### Resultado esperado

- `laboratorio-dr.md` con las seis partes, comandos, salidas, capturas y mediciones (RTO zonal, RPO de Storage, RTO/RPO de restore de PostgreSQL, RTO de restore de VM, RTO/RPO de la prueba completa).
- `bia.md`, `dr-plan.md`, `runbook-failover.md` (versión previa y versión corregida tras la prueba) e `informe-prueba-dr.md`.
- ADR de la estrategia de DR y diagramas (HA regional y multi-región).
- Código Terraform parametrizado por región y scripts de backup/restore.
- Ninguna cuenta de Storage, VM, servidor PostgreSQL, vault ni perfil de Traffic Manager vivo al terminar, salvo el backend de Terraform.

### Criterios de validación

- [ ] RTO y RPO por componente están justificados con datos del escenario y con una estimación de coste; el ADR elige una estrategia coherente con el 30 % de presupuesto extra.
- [ ] La prueba HA zonal muestra el número de peticiones fallidas y el tiempo hasta que la sonda retiró la instancia, y relaciona ese tiempo con la configuración de la sonda.
- [ ] Hay evidencia de lectura real desde el endpoint secundario RA-GRS, del error al escribir en él y del `lastSyncTime`.
- [ ] La restauración de PostgreSQL (PITR o `pg_restore`) se ejecutó de verdad, con tiempo medido y recuento de filas antes y después.
- [ ] El backup y la restauración de la VM funcionaron; el vault se eliminó siguiendo el procedimiento correcto y el estudiante explica el papel del soft delete.
- [ ] La prueba de DR tiene `T0` y `T1` reales, RTO y RPO medidos y comparados con los objetivos, sin maquillaje; el informe recoge desviaciones y acciones correctivas, y el runbook cambió tras la prueba.
- [ ] El plan de DR incluye continuidad de negocio no técnica y dependencias externas.
- [ ] La captura de Cost Management del día siguiente muestra un gasto acorde con la estimación y no quedan recursos vivos.
- [ ] En una conversación con el mentor, el estudiante puede defender por qué eligió backup/restore, pilot light o warm standby y qué haría distinto con el doble de presupuesto.

## Entrega

En tu repositorio de entregas, carpeta `03-modulo-avanzado/10-alta-disponibilidad-resiliencia-y-dr/`:

1. `laboratorio-dr.md` y carpeta `capturas/` (con usuario o suscripción visible; oculta claves y SAS).
2. `bia.md`, `dr-plan.md`, `runbook-failover.md`, `informe-prueba-dr.md` y el ADR.
3. `terraform/` (código parametrizado por región, sin estado ni secretos) y `scripts/` (backup, restore, bucle de `curl`).
4. `diagramas/` (HA regional y multi-región).
5. `ENTREGA.md` con evaluación, checklist y uso de IA.

Nota sobre IA: es legítimo pedirle que revise tu runbook o que te proponga escenarios de fallo que no habías considerado. No es legítimo que te escriba el informe de prueba: ese documento solo tiene valor si refleja lo que pasó de verdad en tu suscripción, con tus horas y tus errores.

## Evaluación

1. **Conceptual.** Explica con un ejemplo de TurnoYa la diferencia entre alta disponibilidad y recuperación ante desastres. ¿Puede un sistema tener HA excelente y DR inexistente? ¿Y al revés?
2. **Conceptual.** Define RTO y RPO con tus palabras y explica por qué la replicación asíncrona entre regiones nunca da RPO cero mientras que la síncrona entre zonas sí puede darlo. ¿Por qué no se replica síncronamente entre regiones?
3. **Situacional.** Dirección pide "RTO 5 minutos y RPO cero para todo". Prepara la respuesta: qué arquitectura haría falta, cuánto costaría aproximadamente frente a los 400 EUR/mes actuales y qué alternativa razonable propondrías.
4. **Técnica.** Tienes una cuenta de Storage RA-GRS con `lastSyncTime` hace 8 minutos y la región primaria acaba de caer. ¿Qué datos puedes leer, cuáles has perdido, qué implica iniciar un failover de cuenta y por qué es una decisión que no se debe tomar en el primer minuto?
5. **Troubleshooting.** Tras un `terraform apply` en la región secundaria, la API arranca pero devuelve 500: la cadena de conexión apunta al servidor PostgreSQL de la región primaria que ya no existe. ¿Qué fallo de diseño del plan de DR revela y cómo lo corriges en el código y en el runbook?
6. **Situacional.** Un desarrollador ejecutó `DELETE FROM citas` sin `WHERE` a las 11:42. Con PostgreSQL flexible y retención de 7 días, describe los pasos exactos para recuperar, qué RPO consigues y qué haces con las citas creadas entre 11:42 y el momento de la recuperación.
7. **Conceptual.** Clasifica tu diseño de la Parte E en la taxonomía de AWS (backup and restore, pilot light, warm standby, multi-site active-active). ¿Qué tendrías que añadir para subir un escalón y cuánto costaría al mes?
8. **Técnica.** Explica por qué borrar un Recovery Services Vault requiere deshabilitar soft delete y detener la protección con eliminación de datos. ¿Qué riesgo de seguridad mitiga esa fricción?
9. **Situacional.** Traffic Manager marcó la región primaria como degradada en 90 segundos, pero algunos clientes siguieron llegando a la IP antigua durante 20 minutos. Explica las causas posibles (TTL, cachés de resolvedores, clientes que ignoran TTL) y qué harías para reducir ese tiempo.
10. **Conceptual.** Azure Site Recovery frente a redesplegar con Terraform más restaurar datos: ventajas, inconvenientes y coste de cada opción para TurnoYa. ¿En qué tipo de empresa elegirías ASR sin dudar?
11. **Troubleshooting.** Durante la prueba de DR el `pg_restore` falla porque el dump se hizo con una versión mayor de PostgreSQL que la del servidor nuevo. ¿Cómo lo evitas en el runbook y qué te dice esto sobre las pruebas de restauración periódicas?
12. **Conceptual.** El SRE Book dice que a nadie le importan los backups, solo los restores. Explica las tres capas de defensa que propone (soft delete, backups, replicación) y qué capa te salvó de qué fallo en tu laboratorio.
13. **Situacional.** Tu prueba dio RTO real de 3 h 40 min frente a un objetivo de 4 h. El mentor dice que no basta con cumplir. ¿Qué tres acciones correctivas priorizarías para bajar el RTO a 1 h y cuál es la más barata?
14. **Reflexión.** ¿Qué parte de la continuidad de negocio de TurnoYa no se resuelve con tecnología? Describe qué tendría que hacer una recepcionista de clínica durante tu RTO y qué necesita de ti para poder hacerlo.

## Checklist final

Antes de continuar, deberías poder:

- [ ] Distinguir HA, tolerancia a fallos, resiliencia, backup y DR con ejemplos.
- [ ] Definir RTO y RPO por componente a partir de un BIA y justificar su coste.
- [ ] Diseñar HA regional con zonas, varias instancias, balanceador y base de datos con réplica zonal.
- [ ] Comparar activo-pasivo (frío, tibio, caliente) y activo-activo y nombrarlos en la taxonomía de AWS.
- [ ] Elegir la redundancia de Storage adecuada y leer desde el secundario de una cuenta RA-GRS.
- [ ] Restaurar PostgreSQL a un punto en el tiempo (servicio gestionado o `pg_dump`/`pg_restore`) y medir RTO y RPO.
- [ ] Hacer backup y restore de una VM con Azure Backup y eliminar el vault correctamente.
- [ ] Explicar qué hace Azure Site Recovery y cuándo compensa frente a IaC más restauración.
- [ ] Configurar failover de DNS con Traffic Manager o Azure DNS y explicar el efecto del TTL.
- [ ] Ejecutar una prueba de DR completa, medir RTO y RPO reales y escribir el informe con acciones correctivas.
- [ ] Redactar un plan de DR con su parte de continuidad de negocio no técnica.
- [ ] Dejar la suscripción limpia y con el gasto verificado en Cost Management.

---

*Recursos verificados el 2026-09-27 (existencia y vigencia de las URLs mediante búsqueda web y, cuando el cupo de búsqueda se agotó, mediante los repositorios oficiales de la documentación). Las páginas de Microsoft Learn se enlazan en `es-es` cuando se confirmó la traducción; en el resto se indica cómo cambiar el idioma. Si un enlace falla, abre un issue en este repositorio.*
