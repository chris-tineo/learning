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
7. Fundamentos de Git *(pendiente)*
8. Introducción a Cloud Computing *(pendiente)*
9. Inteligencia Artificial Básica *(pendiente)*

### Módulo Intermedio
1. Administración de Linux
2. Networking Intermedio y Troubleshooting
3. Bash y Python para Automatización
4. Git y GitHub Intermedio
5. Administración de Azure
6. Docker y Contenedores
7. CI/CD
8. Terraform
9. Monitoreo y Observabilidad
10. Fundamentos de DevOps y SRE
11. Inteligencia Artificial aplicada a Cloud, DevOps y SRE

### Módulo Avanzado
1. Kubernetes Avanzado
2. Helm
3. Arquitectura Cloud Avanzada
4. Networking Cloud Avanzado
5. Seguridad Cloud e IAM
6. Terraform Avanzado e IaC a Escala
7. Observabilidad Avanzada
8. SRE Avanzado
9. Incident Management y Troubleshooting Avanzado
10. Alta Disponibilidad, Resiliencia y Disaster Recovery
11. DevSecOps
12. Inteligencia Artificial Avanzada para DevOps y SRE

### Proyecto Final
Despliegue en Azure de una aplicación automatizada, segura, escalable, monitoreada, resiliente, recuperable ante desastre y con un componente de IA operativo. Ver [`04-proyecto-final/README.md`](04-proyecto-final/README.md).

## Estado de elaboración

Los cursos se redactan **curso por curso o en grupos pequeños** para mantener la calidad y verificar cada recurso. El estado de cada uno está en el README de su módulo.

| Estado | Significado |
|---|---|
| ✅ Completo | Guía completa, recursos verificados, laboratorio, evaluación y checklist |
| 🚧 En elaboración | Se está redactando |
| ⬜ Pendiente | Solo existe el temario fijo |

## Convenciones del repositorio

- Un directorio por curso: `NN-modulo/NN-nombre-del-curso/README.md`.
- Todos los cursos siguen la misma plantilla: [`plantillas/plantilla-curso.md`](plantillas/plantilla-curso.md).
- Los estudiantes entregan usando [`plantillas/plantilla-entrega.md`](plantillas/plantilla-entrega.md) en su **propio repositorio de entregas** (ver guía de uso).
- Los recursos enlazados son gratuitos. Cuando un recurso exige crear una cuenta o una tarjeta de crédito, se indica de forma explícita.
- La plataforma Cloud principal es Azure, pero los conceptos se explican de forma transferible a AWS y GCP.
