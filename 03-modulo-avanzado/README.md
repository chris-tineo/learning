# Módulo Avanzado

Doce cursos orientados a diseñar y operar plataformas Cloud de nivel empresarial: Kubernetes y Helm, arquitectura y networking Cloud avanzados, seguridad e IAM, Terraform a escala, observabilidad avanzada, SRE, gestión de incidentes, alta disponibilidad y DR, DevSecOps e IA avanzada aplicada a la operación.

| # | Curso | Estado |
|---|---|---|
| 1 | Kubernetes Avanzado | ⬜ Pendiente |
| 2 | Helm | ⬜ Pendiente |
| 3 | Arquitectura Cloud Avanzada | ⬜ Pendiente |
| 4 | Networking Cloud Avanzado | ⬜ Pendiente |
| 5 | Seguridad Cloud e IAM | ⬜ Pendiente |
| 6 | Terraform Avanzado e IaC a Escala | ⬜ Pendiente |
| 7 | Observabilidad Avanzada | ⬜ Pendiente |
| 8 | SRE Avanzado | ⬜ Pendiente |
| 9 | Incident Management y Troubleshooting Avanzado | ⬜ Pendiente |
| 10 | Alta Disponibilidad, Resiliencia y Disaster Recovery | ⬜ Pendiente |
| 11 | DevSecOps | ⬜ Pendiente |
| 12 | Inteligencia Artificial Avanzada para DevOps y SRE | ⬜ Pendiente |

**Prerrequisito:** haber completado los Módulos Básico e Intermedio.

## Temarios fijos

### 1. Kubernetes Avanzado
Arquitectura de Kubernetes · Control Plane · Worker Nodes · Pods · Deployments · ReplicaSets · StatefulSets · DaemonSets · Services · ConfigMaps · Secrets · Ingress · Persistent Volumes · Persistent Volume Claims · Readiness probes · Liveness probes · Resource requests · Resource limits · Autoscaling · Scheduling · Affinity · Taints · Tolerations · Troubleshooting.
**Práctica:** desplegar y operar una aplicación completa en Kubernetes.

### 2. Helm
Charts · Templates · Values · Releases · Dependencies · Repositories · Versioning · Upgrade · Rollback · Reutilización de deployments.
**Práctica:** convertir una aplicación Kubernetes en un Helm Chart configurable.

### 3. Arquitectura Cloud Avanzada
Landing Zones · Management Groups · Subscriptions · Governance · Hub-Spoke · Shared Services · Multi-environment · Multi-region · Resiliencia · Escalabilidad · Availability · Cost optimization · Architecture decision records · Cloud design patterns.
**Práctica:** diseñar una arquitectura empresarial completa en Azure.

### 4. Networking Cloud Avanzado
VNet Peering · Hub-Spoke networking · Private Endpoints · Private Link · Private DNS · DNS forwarding · VPN · ExpressRoute · Azure Load Balancer · Application Gateway · WAF · Front Door · Routing · UDR · Network appliances · Hybrid networking · Troubleshooting complejo.
**Práctica:** resolver un escenario empresarial de conectividad privada e híbrida.

### 5. Seguridad Cloud e IAM
Entra ID · RBAC · Least privilege · Managed Identities · Service Principals · Key Vault · Secrets · Certificates · Zero Trust · Azure Policy · Security posture · Hardening · Privileged access · Network security · Identity-based authentication.
**Práctica:** diseñar un entorno sin credenciales embebidas y con privilegios mínimos.

### 6. Terraform Avanzado e IaC a Escala
Diseño de módulos · Module composition · Remote State · State locking · Multiple environments · Repository structures · Pipelines para Terraform · Validation · Linting · Testing · Versioning · Providers a escala · Dependency management · Governance.
**Práctica:** crear una plataforma modular reutilizable para varios ambientes.

### 7. Observabilidad Avanzada
Logs · Metrics · Distributed Tracing · Correlation · OpenTelemetry · Prometheus · Grafana · Azure Monitor · Application Insights · Advanced KQL · Alert engineering · Noise reduction · Dashboards operacionales · Service health · Telemetry design.
**Práctica:** investigar un incidente basándose principalmente en telemetría.

### 8. SRE Avanzado
SLI · SLO · SLA · Error Budgets · Reliability engineering · Toil reduction · Capacity planning · Performance · Graceful degradation · Fault tolerance · Reliability patterns · Automation · Risk · Engineering for failure.
**Práctica:** definir el modelo de confiabilidad de un servicio.

### 9. Incident Management y Troubleshooting Avanzado
Incident severity · Incident Commander · War rooms · Escalation · Mitigation · Communication · Stakeholder management · Root Cause Analysis · Postmortems · Timeline reconstruction · Corrective actions · Troubleshooting sistemático.
**Práctica:** ejecutar una simulación completa de un incidente de producción.

### 10. Alta Disponibilidad, Resiliencia y Disaster Recovery
High Availability · Fault tolerance · Availability Zones · Multi-region · Redundancia · Replicación · Backups · Restore · RTO · RPO · Active-active · Active-passive · Failover · DR Plans · DR Testing · Business Continuity.
**Práctica:** diseñar y probar un plan de recuperación ante desastre.

### 11. DevSecOps
Security in CI/CD · SAST · DAST · Dependency scanning · Container scanning · Secret scanning · SBOM · Supply chain security · Vulnerability management · Security gates · Policy as Code · Secure pipelines.
**Práctica:** incorporar controles automáticos de seguridad dentro de un pipeline.

### 12. Inteligencia Artificial Avanzada para DevOps y SRE
**Objetivo:** no convertir al alumno en investigador de IA, sino permitirle comprender y operar soluciones modernas de IA dentro de un entorno Cloud/SRE.
Transformers a nivel conceptual · Attention · Tokenization · Context windows · Embeddings · Vector databases · Semantic Search · RAG · Tool Calling · Function Calling · Agents · Agentic workflows · Modelos grandes y pequeños · Hosted models · Local models · Fine-tuning y cuándo utilizarlo · Evaluación · Guardrails · Prompt injection · Seguridad · Gestión de secretos · Autorización · Observabilidad de IA · Latencia · Tokens · Costos · Arquitecturas de IA en Azure · Operación de workloads de IA.
**Aplicación a SRE y DevOps:** asistentes de troubleshooting · consulta de documentación interna · análisis de logs · análisis de incidentes · generación de runbooks · automatización asistida · tool calling hacia APIs de infraestructura · sistemas de IA con acceso controlado a herramientas.
**Práctica:** construir un pequeño asistente técnico que consulte documentación y pueda utilizar herramientas de manera controlada.
