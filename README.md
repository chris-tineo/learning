# Ruta de formación — Cloud, DevOps, SRE e Inteligencia Artificial

Ruta de aprendizaje **autodidacta**, pensada para personas que empiezan con conocimientos técnicos muy básicos y quieren llegar a diseñar, desplegar, automatizar, proteger, observar y operar una plataforma Cloud moderna (principalmente en **Microsoft Azure**), aplicando además Inteligencia Artificial al trabajo diario de Cloud, DevOps y SRE.

Todo el contenido vive en este repositorio. No hay clases en vivo ni cursos grabados propios: cada curso es una **guía de autoaprendizaje** que ordena recursos gratuitos públicos (documentación oficial, Microsoft Learn, vídeos, cursos abiertos), añade un laboratorio práctico, una entrega, una evaluación y un checklist. El instructor actúa como **mentor**: resuelve dudas, revisa entregas y desbloquea.

> Empieza por [`00-guia-de-uso/README.md`](00-guia-de-uso/README.md). Explica cómo estudiar, cómo entregar y cómo usar la IA sin sustituir la comprensión técnica.

## Estructura

| Módulo | Cursos | Carpeta |
|---|---|---|
| Básico | 9 | [`01-modulo-basico/`](01-modulo-basico/README.md) |
| Intermedio | 11 | [`02-modulo-intermedio/`](02-modulo-intermedio/README.md) |
| Avanzado | 12 | [`03-modulo-avanzado/`](03-modulo-avanzado/README.md) |
| Proyecto Final (obligatorio) | 1 | [`04-proyecto-final/`](04-proyecto-final/README.md) |

Orientación aproximada de cada curso: **30 % teoría, 60 % práctica, 10 % evaluación**.

No todos los cursos duran lo mismo. Historia de la Computación se completa en pocos días; Linux, Azure, Terraform o Kubernetes pueden requerir varias semanas.

## Índice completo

### Módulo Básico
1. [Historia de la Computación](01-modulo-basico/01-historia-de-la-computacion/README.md)
2. [Fundamentos de Hardware](01-modulo-basico/02-fundamentos-de-hardware/README.md)
3. [Fundamentos de Sistemas Operativos](01-modulo-basico/03-fundamentos-de-sistemas-operativos/README.md)
4. [Windows Básico](01-modulo-basico/04-windows-basico/README.md)
5. [Linux Básico](01-modulo-basico/05-linux-basico/README.md)
6. [Networking Básico](01-modulo-basico/06-networking-basico/README.md)
7. [Fundamentos de Git](01-modulo-basico/07-fundamentos-de-git/README.md)
8. [Introducción a Cloud Computing](01-modulo-basico/08-introduccion-a-cloud-computing/README.md)
9. [Inteligencia Artificial Básica](01-modulo-basico/09-inteligencia-artificial-basica/README.md)

### Módulo Intermedio
1. [Administración de Linux](02-modulo-intermedio/01-administracion-de-linux/README.md)
2. [Networking Intermedio y Troubleshooting](02-modulo-intermedio/02-networking-intermedio-y-troubleshooting/README.md)
3. [Bash y Python para Automatización](02-modulo-intermedio/03-bash-y-python-para-automatizacion/README.md)
4. [Git y GitHub Intermedio](02-modulo-intermedio/04-git-y-github-intermedio/README.md)
5. [Administración de Azure](02-modulo-intermedio/05-administracion-de-azure/README.md)
6. [Docker y Contenedores](02-modulo-intermedio/06-docker-y-contenedores/README.md)
7. [CI/CD](02-modulo-intermedio/07-ci-cd/README.md)
8. [Terraform](02-modulo-intermedio/08-terraform/README.md)
9. [Monitoreo y Observabilidad](02-modulo-intermedio/09-monitoreo-y-observabilidad/README.md)
10. [Fundamentos de DevOps y SRE](02-modulo-intermedio/10-fundamentos-de-devops-y-sre/README.md)
11. [Inteligencia Artificial aplicada a Cloud, DevOps y SRE](02-modulo-intermedio/11-ia-aplicada-a-cloud-devops-y-sre/README.md)

### Módulo Avanzado
1. [Kubernetes Avanzado](03-modulo-avanzado/01-kubernetes-avanzado/README.md)
2. [Helm](03-modulo-avanzado/02-helm/README.md)
3. [Arquitectura Cloud Avanzada](03-modulo-avanzado/03-arquitectura-cloud-avanzada/README.md)
4. [Networking Cloud Avanzado](03-modulo-avanzado/04-networking-cloud-avanzado/README.md)
5. [Seguridad Cloud e IAM](03-modulo-avanzado/05-seguridad-cloud-e-iam/README.md)
6. [Terraform Avanzado e IaC a Escala](03-modulo-avanzado/06-terraform-avanzado-e-iac-a-escala/README.md)
7. [Observabilidad Avanzada](03-modulo-avanzado/07-observabilidad-avanzada/README.md)
8. [SRE Avanzado](03-modulo-avanzado/08-sre-avanzado/README.md)
9. [Incident Management y Troubleshooting Avanzado](03-modulo-avanzado/09-incident-management-y-troubleshooting-avanzado/README.md)
10. [Alta Disponibilidad, Resiliencia y Disaster Recovery](03-modulo-avanzado/10-alta-disponibilidad-resiliencia-y-dr/README.md)
11. [DevSecOps](03-modulo-avanzado/11-devsecops/README.md)
12. [Inteligencia Artificial Avanzada para DevOps y SRE](03-modulo-avanzado/12-ia-avanzada-para-devops-y-sre/README.md)

### Proyecto Final
Despliegue en Azure de una aplicación automatizada, segura, escalable, monitoreada, resiliente, recuperable ante desastre y con un componente de IA operativo. Ver [`04-proyecto-final/README.md`](04-proyecto-final/README.md).

## Estado de elaboración

Los 32 cursos y la guía del Proyecto Final están redactados (estado ✅ en los índices de cada módulo). Cada curso indica al pie la fecha y el método de verificación de sus recursos. Los enlaces se revisan periódicamente; si encuentras uno roto o un recurso que ha dejado de ser gratuito, abre un issue.

| Estado | Significado |
|---|---|
| ✅ Completo | Guía completa, recursos verificados, laboratorio, evaluación y checklist |
| 🚧 En revisión | Se está actualizando |
| ⬜ Pendiente | Solo existe el temario fijo |

## Convenciones del repositorio

- Un directorio por curso: `NN-modulo/NN-nombre-del-curso/README.md`.
- Todos los cursos siguen la misma plantilla: [`plantillas/plantilla-curso.md`](plantillas/plantilla-curso.md).
- Los estudiantes entregan usando [`plantillas/plantilla-entrega.md`](plantillas/plantilla-entrega.md) en su **propio repositorio de entregas** (ver guía de uso).
- Los recursos enlazados son gratuitos. Cuando un recurso exige crear una cuenta o una tarjeta de crédito, se indica de forma explícita.
- La plataforma Cloud principal es Azure, pero los conceptos se explican de forma transferible a AWS y GCP.
