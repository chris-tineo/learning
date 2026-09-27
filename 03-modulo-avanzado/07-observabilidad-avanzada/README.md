# Observabilidad Avanzada

> Módulo: Avanzado · Curso 7 de 12 · Duración estimada: 35-45 horas · Estado: ✅ Completo

## Objetivo

En Monitoreo y Observabilidad (Módulo Intermedio) aprendiste a mirar una aplicación desde fuera: Azure Monitor, Application Insights, unas cuantas consultas KQL y una alerta cuando algo se pasa de un umbral. Eso sirve para saber **que** algo va mal. Este curso trata de saber **por qué**, y de saberlo a las tres de la mañana, con un sistema distribuido en el que la petición del usuario atraviesa dos o tres servicios, una base de datos y un proveedor externo.

Vas a instrumentar la aplicación del curso de Docker con **OpenTelemetry**, el estándar abierto que hoy usan tanto Prometheus y Grafana como Azure Monitor, y vas a montar las dos tuberías que verás en cualquier empresa: una **abierta** (Prometheus, Grafana, Loki, Tempo en Docker Compose) y una **gestionada** (Application Insights). La misma telemetría, exportada desde un único OpenTelemetry Collector, llega a las dos. Así entenderás que la herramienta es intercambiable y lo que importa es el **diseño de la telemetría**: qué medir, con qué etiquetas, con qué cardinalidad, con qué muestreo.

La segunda mitad del curso es sobre **alertas**. Casi todos los equipos que conozco están enterrados en ruido: alertas que nadie lee, umbrales que saltan cada noche, canales de Teams silenciados. Aprenderás a alertar sobre síntomas y sobre el consumo del presupuesto de error (burn rate multiventana, según el SRE Workbook), a agrupar y silenciar con criterio y a exigir que cada alerta lleve un runbook. Terminarás investigando un incidente inyectado a ciegas en tu propio sistema, usando solo la telemetría, y documentando el camino desde la alerta hasta la causa. Ese ejercicio es el puente hacia SRE Avanzado e Incident Management.

**Antes de empezar** necesitas la aplicación del curso de Docker funcionando en local (imagen construida, `docker compose` a mano), tu cuenta de Azure con presupuesto y alertas, y haber hecho el curso de Monitoreo y Observabilidad del Módulo Intermedio (KQL introductorio y App Insights).

### Al terminar este curso deberías poder

- Explicar las tres señales (logs, métricas, trazas), qué pregunta responde cada una y cómo se correlacionan mediante el trace id.
- Instrumentar un servicio Python con el SDK de OpenTelemetry, auto-instrumentación de Flask/FastAPI y `requests`, y propagar el contexto entre dos servicios.
- Desplegar y configurar un OpenTelemetry Collector con receivers, processors y exporters hacia varios destinos a la vez.
- Diseñar métricas RED para servicios y USE para recursos, elegir etiquetas con cardinalidad controlada y justificar una estrategia de muestreo.
- Escribir PromQL básico e intermedio: `rate`, `histogram_quantile`, agregaciones por etiqueta, ratios de error, `increase`, `offset`.
- Construir un dashboard operacional en Grafana con variables, umbrales, anotaciones y enlaces a trazas y logs.
- Escribir KQL avanzado en Application Insights: `join`, `summarize ... by bin()`, `percentiles`, `render`, `let` y funciones.
- Diseñar alertas basadas en síntomas y en SLO con burn rate multiventana y multi-burn-rate, y explicar por qué superan a las de umbral.
- Reducir el ruido de alertas con agrupación, inhibición, silencios, severidades y runbooks enlazados.
- Investigar un incidente desconocido siguiendo la telemetría desde la alerta hasta la causa y documentar el razonamiento.

## Prerrequisitos

- Módulo Intermedio completo, en especial Docker y Contenedores (la aplicación que vas a instrumentar), Monitoreo y Observabilidad (Azure Monitor, App Insights, KQL introductorio) y Fundamentos de DevOps y SRE (postmortem, conceptos de SLI/SLO).
- Módulo Avanzado: Kubernetes Avanzado y Helm (el ejercicio final puede correr en `kind`, aunque el laboratorio principal usa Docker Compose).
- Equipo con Docker y Docker Compose, al menos 8 GB de RAM libres para el stack local (Prometheus, Grafana, Loki, Tempo, Collector y dos servicios).
- Cuenta de Azure con presupuesto activo y un recurso de Application Insights (basado en workspace) que puedas crear y borrar.
- Python 3.10 o superior y `pip`.

## Temario

Logs · Metrics · Distributed Tracing · Correlation · OpenTelemetry · Prometheus · Grafana · Azure Monitor · Application Insights · Advanced KQL · Alert engineering · Noise reduction · Dashboards operacionales · Service health · Telemetry design.

**Práctica:** investigar un incidente basándose principalmente en telemetría.

## Recursos en español

### Documentación de OpenTelemetry en español — CNCF
- **URL:** https://opentelemetry.io/es/docs/ · Qué es OpenTelemetry: https://opentelemetry.io/es/docs/what-is-opentelemetry/ · Componentes: https://opentelemetry.io/es/docs/concepts/components/ · Introducción para desarrolladores: https://opentelemetry.io/es/docs/getting-started/dev/
- **Autor / organización:** Proyecto OpenTelemetry (CNCF), traducción de la comunidad
- **Idioma:** Español (traducción parcial; las páginas no traducidas redirigen al inglés)
- **Tipo:** Documentación oficial
- **Duración aproximada:** 2 h para conceptos, componentes y la introducción para desarrolladores
- **Cubre:** OpenTelemetry, señales, correlación, Collector, diseño de telemetría.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la única documentación oficial de observabilidad moderna con una traducción al español cuidada. Léela para fijar vocabulario (traza, span, contexto, recurso, atributo) y pasa después a la versión inglesa para el SDK de Python, que no está traducida.

### Demo de OpenTelemetry (documentación en español) — CNCF
- **URL:** https://opentelemetry.io/es/docs/demo/ · Características de telemetría: https://opentelemetry.io/es/docs/demo/telemetry-features/
- **Autor / organización:** Proyecto OpenTelemetry (CNCF)
- **Idioma:** Español
- **Tipo:** Documentación de una aplicación de referencia (microservicios con Docker Compose)
- **Duración aproximada:** 1 h de lectura; 2 h si la despliegas
- **Cubre:** Distributed Tracing, Correlation, Collector, escenarios de fallo inyectado (feature flags de caos).
- **Nivel:** Intermedio-avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es el "sistema de ejemplo" oficial: una tienda con una docena de servicios ya instrumentados. No hace falta desplegarla entera (pide bastante RAM), pero su documentación de escenarios de fallo es una mina de ideas para el ejercicio final, y ver cómo instrumentan cada lenguaje te dará referencias cuando te atasques con Python.

### Microsoft Learn en español — Azure Monitor, Application Insights y KQL
- **URL:** Portal de documentación de Azure en español: https://learn.microsoft.com/es-es/azure/ (entra en "Supervisión" > Azure Monitor; para las páginas de OpenTelemetry y KQL usa las URL en inglés de la sección siguiente cambiando `en-us` por `es-es`)
- **Autor / organización:** Microsoft
- **Idioma:** Español (traducción automática revisada en la mayoría de páginas)
- **Tipo:** Documentación oficial
- **Duración aproximada:** 3-4 h repartidas en el curso
- **Cubre:** Azure Monitor, Application Insights, Advanced KQL, alertas, Service health.
- **Nivel:** Intermedio
- **Acceso:** Libre; cuenta Microsoft gratuita para guardar progreso en los módulos de aprendizaje
- **Por qué lo recomiendo:** Ya conoces este portal del Módulo Intermedio. Todo el material de Azure Monitor y del lenguaje Kusto existe en español; el truco de cambiar `en-us` por `es-es` en cualquier URL de Microsoft Learn funciona siempre (si la página no está traducida, te devuelve la inglesa). En la ruta de estudio te indico qué páginas leer.

## Recursos en inglés

### OpenTelemetry Python: Getting Started, zero-code instrumentation e instrumentation libraries — CNCF
- **URL:** https://opentelemetry.io/docs/languages/python/ · Getting started (Flask): https://opentelemetry.io/docs/languages/python/getting-started/ · Instrumentación sin código: https://opentelemetry.io/docs/languages/python/automatic · Librerías de instrumentación: https://opentelemetry.io/docs/languages/python/libraries/
- **Autor / organización:** Proyecto OpenTelemetry (CNCF)
- **Idioma:** Inglés
- **Tipo:** Documentación oficial con tutorial paso a paso
- **Duración aproximada:** 3 h (leer y reproducir el tutorial)
- **Cubre:** OpenTelemetry, Logs, Metrics, Distributed Tracing, Correlation en Python.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** El tutorial oficial instrumenta precisamente una aplicación Flask, así que es casi la Parte B del laboratorio. Lee también la página de librerías de instrumentación: ahí está cómo se instrumentan `requests`, FastAPI, `psycopg2` o `logging`, que necesitarás para las trazas distribuidas.

### OpenTelemetry Collector: quick start, configuración y arquitectura — CNCF
- **URL:** https://opentelemetry.io/docs/collector/ · Quick start: https://opentelemetry.io/docs/collector/quick-start/ · Configuración: https://opentelemetry.io/docs/collector/configuration/ · Arquitectura: https://opentelemetry.io/docs/collector/architecture/
- **Autor / organización:** Proyecto OpenTelemetry (CNCF)
- **Idioma:** Inglés
- **Tipo:** Documentación oficial
- **Duración aproximada:** 2 h
- **Cubre:** Collector (receivers, processors, exporters, pipelines), Telemetry design (batching, sampling, filtrado de atributos).
- **Nivel:** Intermedio-avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** El Collector es la pieza que hace que el resto del curso sea intercambiable: una sola tubería de salida desde la app y N destinos. La página de configuración es la referencia que tendrás abierta toda la Parte C.

### Prometheus: Querying basics, examples, functions y Alerting — Prometheus Authors
- **URL:** https://prometheus.io/docs/prometheus/latest/querying/basics/ · Ejemplos: https://prometheus.io/docs/prometheus/latest/querying/examples/ · Funciones: https://prometheus.io/docs/prometheus/latest/querying/functions/ · Reglas de alerta: https://prometheus.io/docs/prometheus/latest/configuration/alerting_rules/ · Alertmanager: https://prometheus.io/docs/alerting/latest/alertmanager/ · Tutorial de alertas: https://prometheus.io/docs/tutorials/alerting_based_on_metrics/
- **Autor / organización:** Proyecto Prometheus (CNCF)
- **Idioma:** Inglés
- **Tipo:** Documentación oficial
- **Duración aproximada:** 4 h
- **Cubre:** Prometheus, Metrics, PromQL, Alert engineering, Noise reduction (agrupación, inhibición, silencios).
- **Nivel:** Intermedio-avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** PromQL se aprende escribiendo consultas contra datos reales, y la página de ejemplos es la mejor chuleta que existe. La documentación de Alertmanager explica con precisión los tres mecanismos de reducción de ruido que usarás en la Parte G.

### Grafana fundamentals (tutorial), Loki y Tempo — Grafana Labs
- **URL:** Tutorial: https://grafana.com/tutorials/grafana-fundamentals/ · Índice de tutoriales: https://grafana.com/tutorials/ · Fundamentos y primer dashboard: https://grafana.com/docs/grafana/latest/fundamentals/ · Loki: https://grafana.com/docs/loki/latest/ · Tempo: https://grafana.com/docs/tempo/latest/ · Ejemplo Tempo con Docker: https://grafana.com/docs/tempo/latest/docker-example/
- **Autor / organización:** Grafana Labs
- **Idioma:** Inglés
- **Tipo:** Tutorial interactivo y documentación oficial
- **Duración aproximada:** 1,5 h el tutorial; 2 h la documentación de Loki y Tempo que necesitas
- **Cubre:** Grafana, Dashboards operacionales, Logs (Loki), Distributed Tracing (Tempo), Correlation (saltar de log a traza y de traza a métricas).
- **Nivel:** Intermedio
- **Acceso:** Libre (el tutorial se hace en tu propio Docker; no requiere cuenta de Grafana Cloud)
- **Por qué lo recomiendo:** El tutorial usa una aplicación de ejemplo con Prometheus y Loki y termina creando una alerta, lo que sirve de calentamiento para la Parte E. Loki y Tempo son las piezas ligeras que hacen viable tener logs y trazas en tu portátil. En https://learn.grafana.com/ hay además una ruta gratuita "Grafana Fundamentals" con laboratorios guiados, si prefieres ese formato.

### SRE Book, capítulo "Monitoring Distributed Systems", y SRE Workbook, capítulos "Alerting on SLOs" e "Implementing SLOs" — Google
- **URL:** https://sre.google/sre-book/monitoring-distributed-systems/ · https://sre.google/workbook/alerting-on-slos/ · https://sre.google/workbook/implementing-slos/ · Workbook "Monitoring": https://sre.google/workbook/monitoring/
- **Autor / organización:** Google SRE
- **Idioma:** Inglés
- **Tipo:** Libros online gratuitos (capítulos)
- **Duración aproximada:** 3-4 h de lectura atenta
- **Cubre:** Alert engineering, Noise reduction, Telemetry design (cuatro señales de oro, síntomas frente a causas), burn rate multiventana.
- **Nivel:** Avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** "Alerting on SLOs" es el capítulo que cambia cómo piensas las alertas: recorre seis diseños, desde el umbral simple hasta el multiventana multi-burn-rate, y explica con números por qué cada uno mejora al anterior. Lo implementarás tal cual en la Parte G. "Monitoring Distributed Systems" es corto y contiene las reglas que deberías poder recitar sobre qué merece despertar a alguien.

### Enable OpenTelemetry in Application Insights (Azure Monitor OpenTelemetry Distro para Python) — Microsoft Learn
- **URL:** https://learn.microsoft.com/en-us/azure/azure-monitor/app/opentelemetry-enable · Configuración (muestreo, atributos, exportador): https://learn.microsoft.com/en-us/azure/azure-monitor/app/opentelemetry-configuration · Referencia de la librería Python: https://learn.microsoft.com/en-us/python/api/overview/azure/monitor-opentelemetry-readme?view=azure-python
- **Autor / organización:** Microsoft
- **Idioma:** Inglés (en español cambiando `en-us` por `es-es`)
- **Tipo:** Documentación oficial
- **Duración aproximada:** 1,5 h
- **Cubre:** Azure Monitor, Application Insights, OpenTelemetry, Telemetry design (sampling en Azure).
- **Nivel:** Intermedio
- **Acceso:** Libre (el recurso de Application Insights en Azure entra en los 5 GB/mes gratuitos de Log Analytics si controlas el volumen)
- **Por qué lo recomiendo:** Explica las dos formas de enviar OpenTelemetry a Azure: la distro en el propio proceso Python (`configure_azure_monitor`) y el exporter desde el Collector. En el laboratorio usas la segunda para que la app no sepa nada de Azure, pero debes entender las dos.

## Documentación oficial

- **OpenTelemetry (Python):** https://opentelemetry.io/docs/languages/python/ y API: https://opentelemetry.io/docs/languages/python/api/
- **OpenTelemetry Collector:** https://opentelemetry.io/docs/collector/configuration/ (receivers OTLP y Prometheus, processors `batch`, `memory_limiter`, `attributes`, `tail_sampling`; exporters `prometheus`, `otlp`, `loki`, `azuremonitor`)
- **Prometheus, consultas:** https://prometheus.io/docs/prometheus/latest/querying/ · Almacenamiento y retención: https://prometheus.io/docs/prometheus/latest/storage/
- **Prometheus, alertas:** https://prometheus.io/docs/alerting/latest/overview/ · Configuración de Alertmanager (rutas, agrupación, inhibición): https://prometheus.io/docs/alerting/latest/configuration/
- **Grafana:** https://grafana.com/docs/grafana/latest/fundamentals/ · Fuente de datos Tempo: https://grafana.com/docs/grafana/latest/datasources/tempo/ · Fuente de datos Loki: https://grafana.com/docs/grafana/latest/datasources/loki/
- **Azure Monitor y Application Insights con OpenTelemetry:** https://learn.microsoft.com/en-us/azure/azure-monitor/app/opentelemetry-enable
- **SRE Workbook, plantilla de documento SLO** (la usarás en SRE Avanzado): https://sre.google/workbook/slo-document/

## Ruta recomendada de estudio

1. **Leer** la documentación de OpenTelemetry en español: qué es, componentes e introducción para desarrolladores (2 h). Dibuja a mano la relación app → SDK → exporter OTLP → Collector → backends.
2. **Releer** "Monitoring Distributed Systems" del SRE Book (45 min). Anota las cuatro señales de oro y la regla de "síntomas frente a causas": las vas a necesitar para justificar cada métrica y cada alerta.
3. **Hacer** el Getting Started de OpenTelemetry Python en un directorio de pruebas, sin tocar todavía tu aplicación (1,5 h). Luego **leer** la página de instrumentation libraries y localizar las de Flask o FastAPI, `requests` y `logging`.
4. **Leer** el quick start y la página de configuración del Collector (1,5 h). Debes poder explicar qué es un pipeline y por qué configurar un receiver no lo activa.
5. **Hacer las Partes A, B y C del laboratorio** (8-10 h). Aquí es donde se aprende: no avances a PromQL hasta ver una traza de dos servicios en Tempo con su log correlado en Loki.
6. **Leer** Querying basics y examples de Prometheus con tu Prometheus abierto en otra pestaña, probando cada ejemplo sobre tus métricas (2 h). **Hacer la Parte D.**
7. **Hacer** el tutorial Grafana fundamentals (1,5 h) y después **la Parte E** con tus propios datos.
8. **Leer** la documentación de OpenTelemetry en Application Insights (1 h) y las páginas de KQL que indica la Parte F (en Microsoft Learn, en español). **Hacer la Parte F.**
9. **Leer** "Alerting on SLOs" del Workbook completo, con papel y lápiz para reproducir las tablas de burn rate (2 h). **Leer** la página de Alertmanager (45 min). **Hacer la Parte G.**
10. **Hacer la Parte H** (el incidente inyectado) en una sesión sin interrupciones de 2-3 h, cronometrada, y **la Parte I** de limpieza.
11. **Responder la evaluación** y **revisar el checklist**.

Si vas justo de tiempo: los puntos 3, 4, 5, 9 y 10 son obligatorios. El resto es refuerzo, pero sin ellos el ejercicio final se hace a ciegas.

## Laboratorio

### Objetivo

Convertir la aplicación del curso de Docker en un pequeño sistema distribuido observable de extremo a extremo: dos servicios Python instrumentados con OpenTelemetry, un Collector que exporta a un stack local (Prometheus, Grafana, Loki, Tempo) y a Application Insights, métricas RED y USE, dashboards operacionales, alertas basadas en síntomas y en burn rate con reducción de ruido, y un incidente inyectado a ciegas que resolverás usando solo la telemetría.

### Requisitos

- Repositorio de la aplicación del curso de Docker (Flask o FastAPI, con `/health` y `/version`), Docker y Docker Compose.
- Python 3.10+ en tu equipo para desarrollo local. Editor con soporte de YAML.
- Cuenta de Azure. Recurso de Application Insights basado en workspace en un grupo `rg-lab-obs`.
- Un script de carga sencillo (puede ser `hey`, `k6` o un bucle de `curl` en Bash; `hey` y `k6` los usarás también en SRE Avanzado).
- Documenta todo en `laboratorio-observabilidad.md`. El código va en archivos, no en capturas.

> **Sobre el coste.** Todo el stack abierto corre en tu equipo: coste cero. En Azure solo creas un Application Insights basado en workspace: la ingesta en Log Analytics tiene 5 GB/mes gratuitos y la retención de 31 días es gratuita. Con dos servicios y unas horas de carga moderada no llegarás ni a 200 MB, pero activa el **muestreo** en el Collector antes de conectar Azure y revisa "Uso y costos estimados" en el recurso al terminar. No dejes generadores de carga corriendo en segundo plano. Al final, `az group delete`.

### Instrucciones

**Parte A — Diseño de telemetría (60-90 min)**

1. Añade a la aplicación del curso de Docker un **segundo servicio** llamado `inventario` (misma base: Python, mismo framework) con dos endpoints: `GET /stock/<id>` que devuelve un JSON con stock ficticio tras dormir un tiempo configurable por variable de entorno (`LATENCIA_MS`, por defecto 20), y `/health`. Añade al primer servicio (llámalo `api`) un endpoint `GET /pedido/<id>` que llame por HTTP a `inventario` con `requests` y devuelva el resultado combinado. Ya tienes un sistema distribuido.
2. Antes de instrumentar nada, escribe `diseno-telemetria.md` con una tabla por servicio: **qué medir** (las cuatro señales de oro: latencia, tráfico, errores, saturación), **con qué tipo de métrica** (counter, histogram, gauge), **con qué etiquetas** (`service`, `route`, `method`, `status_code`) y **qué etiquetas están prohibidas** por cardinalidad (id de pedido, id de usuario, IP de cliente, timestamps). Estima la cardinalidad resultante: número de series = producto de los valores posibles de cada etiqueta. Justifica por qué `route` debe ser la plantilla (`/pedido/{id}`) y no la URL real.
3. Define la **convención de logs**: JSON estructurado, campos obligatorios (`timestamp`, `level`, `service`, `message`, `trace_id`, `span_id`) y qué nunca debe ir en un log (secretos, datos personales). Define la **estrategia de muestreo** inicial: 100 % de trazas en local, muestreo por ratio en Azure (por ejemplo 20 %) y por qué las métricas nunca se muestrean.

**Parte B — Instrumentación con OpenTelemetry (3-4 h)**

4. Instala en ambos servicios el SDK y los paquetes de instrumentación: `opentelemetry-sdk`, `opentelemetry-exporter-otlp`, `opentelemetry-instrumentation-flask` (o `-fastapi`), `opentelemetry-instrumentation-requests` y `opentelemetry-instrumentation-logging`. Fija versiones en `requirements.txt`.
5. Instrumenta primero **sin tocar código** con `opentelemetry-instrument --traces_exporter console --metrics_exporter console python app.py` (o con `opentelemetry-bootstrap -a install`). Haz una petición a `/pedido/1` y captura la salida de consola de **ambos** servicios. Localiza en las dos trazas el mismo `trace_id` y explica cómo ha viajado: busca la cabecera `traceparent` con `curl -v` entre servicios (W3C Trace Context).
6. Pasa a exportar por **OTLP** hacia el Collector (variables `OTEL_EXPORTER_OTLP_ENDPOINT`, `OTEL_SERVICE_NAME`, `OTEL_RESOURCE_ATTRIBUTES=service.version=...,deployment.environment=lab`). Explica por qué la app no debe conocer Prometheus ni Azure.
7. Añade **instrumentación manual** donde la automática no llega: un span hijo `calcular_precio` dentro de `/pedido/<id>` con un atributo `pedido.items` y un evento si el stock es cero; un **histograma** propio `pedido_importe_eur` y un **counter** `pedidos_total{resultado="ok|sin_stock|error"}` con la API de métricas de OpenTelemetry.
8. Configura el `logging` de Python en JSON con `trace_id` y `span_id` inyectados por la instrumentación de logging. Comprueba con una petición que el log de `api` y el de `inventario` comparten `trace_id`. Guarda esa evidencia: es la definición práctica de **correlación**.
9. Añade a `inventario` tres interruptores por variable de entorno que usarás en la Parte H y en los dos cursos siguientes: `LATENCIA_MS` (ya existe), `TASA_ERROR` (probabilidad de responder 500, 0.0 a 1.0) y `FUGA_MEMORIA=1` (en cada petición añade unos KB a una lista global que nunca se libera). Documenta que existen pero **no anotes** cómo se activan en el informe del incidente hasta la Parte H.

**Parte C — Collector y stack local (3-4 h)**

10. Crea `docker-compose.yml` con estos servicios: `api`, `inventario`, `otel-collector` (imagen `otel/opentelemetry-collector-contrib`), `prometheus`, `grafana`, `loki`, `tempo`. Añade `node-exporter` (o `cadvisor`) para las métricas USE de recursos. Monta los archivos de configuración desde una carpeta `config/`.
11. Escribe `config/otel-collector.yaml` con un receiver `otlp` (gRPC y HTTP), processors `memory_limiter` y `batch`, y exporters: `prometheus` (expone las métricas para que Prometheus las recoja), `otlp` hacia Tempo y el exporter de logs hacia Loki (según la versión de tu Collector puede ser `otlphttp` apuntando al endpoint OTLP de Loki; consulta la documentación de Loki de tu versión). Declara los tres pipelines (`traces`, `metrics`, `logs`) en `service`. Esqueleto orientativo:
    ```yaml
    receivers:
      otlp:
        protocols: { grpc: {}, http: {} }
    processors:
      memory_limiter: { check_interval: 1s, limit_mib: 400 }
      batch: {}
    exporters:
      prometheus: { endpoint: "0.0.0.0:8889" }
      otlp/tempo: { endpoint: "tempo:4317", tls: { insecure: true } }
    service:
      pipelines:
        traces:  { receivers: [otlp], processors: [memory_limiter, batch], exporters: [otlp/tempo] }
        metrics: { receivers: [otlp], processors: [memory_limiter, batch], exporters: [prometheus] }
    ```
    Completa el pipeline de logs tú. Cuando algo no arranque, lee los logs del Collector: son muy explícitos sobre qué componente está mal.
12. Configura `prometheus.yml` con `scrape_configs` para el Collector y para `node-exporter`, intervalo 15 s. En Grafana añade las tres fuentes de datos (Prometheus, Loki, Tempo) y configura en Tempo los enlaces **trace to logs** (por `trace_id`) y en Loki el **derived field** que convierte el `trace_id` del log en un enlace a la traza.
13. Genera carga durante 10 minutos (`hey -z 10m -q 5 http://localhost:8000/pedido/1` o equivalente) y comprueba el circuito completo: en Grafana Explore, busca un log con error en Loki, salta a su traza en Tempo, ve los dos spans (uno por servicio) y desde la traza vuelve a las métricas. Captura los tres saltos. Si alguno falla, arréglalo antes de seguir: sin correlación no hay observabilidad, solo tres silos.

**Parte D — Métricas RED/USE y PromQL (2 h)**

14. Escribe y explica, en `promql.md`, estas consultas sobre tus datos (adapta los nombres de métrica a los que genera tu instrumentación; míralos en `http://localhost:8889/metrics`):
    - **Rate**: peticiones por segundo por servicio y ruta (`sum by (service, route) (rate(http_server_request_duration_seconds_count[5m]))` o el nombre equivalente).
    - **Errors**: ratio de errores 5xx sobre el total, por servicio, en porcentaje.
    - **Duration**: p50, p95 y p99 con `histogram_quantile` sobre `rate(..._bucket[5m])`, por ruta. Explica por qué no se puede "promediar percentiles" y qué pasa si los buckets del histograma están mal elegidos.
    - **USE** sobre `node-exporter`: utilización de CPU (`1 - rate(node_cpu_seconds_total{mode="idle"}[5m])`), saturación de memoria y errores de red. Explica la diferencia entre utilización y saturación con un ejemplo de tu máquina.
    - Una consulta con `increase` para pedidos totales en la última hora, otra con `offset 1h` para comparar con la hora anterior, y una con `topk(3, ...)`.
15. Activa `TASA_ERROR=0.2` en `inventario`, reinicia solo ese contenedor, genera carga y observa cómo cambia cada consulta. Anota cuánto tarda cada una en reflejar el cambio y por qué (ventana de `rate`, intervalo de scrape).

**Parte E — Dashboards operacionales en Grafana (2 h)**

16. Construye un dashboard `Servicio: pedidos` con: fila RED por servicio (tres paneles: tasa, errores, latencia p95/p99), fila USE del host, fila de logs (panel de Loki filtrado por `level=error`) y un panel de trazas recientes con errores. Añade una **variable** `service` (query sobre `label_values(service)`) que filtre todos los paneles y una variable `intervalo`.
17. Configura **umbrales** visuales (verde/ámbar/rojo) en latencia y errores coherentes con un objetivo que definas (por ejemplo p95 < 300 ms, errores < 1 %). Añade **anotaciones**: una manual marcando cuándo activaste `TASA_ERROR` y otra automática desde una consulta de Loki que marque cada despliegue (haz que la app escriba un log `evento=arranque` al iniciar).
18. Exporta el dashboard como JSON a `grafana/dashboards/pedidos.json` y provisiónalo desde Compose (carpeta de provisioning) para que no dependa de clics. Escribe en el informe qué preguntas responde ese dashboard en los primeros 30 segundos de un incidente y qué **no** debe tener (paneles decorativos, promedios de latencia, más de una pantalla).

**Parte F — Azure Monitor, Application Insights y KQL avanzado (2-3 h)**

19. Crea `rg-lab-obs` y un Application Insights basado en workspace (`az monitor app-insights component create ... --workspace ...`; instala la extensión de CLI si te la pide). Copia la cadena de conexión a un archivo `.env` **que no subas al repositorio**.
20. Añade al Collector el exporter `azuremonitor` con la cadena de conexión y un processor `probabilistic_sampler` (o el muestreo equivalente) al 20 % **solo en el pipeline de trazas hacia Azure**. Añádelo a los pipelines de trazas y logs. Explica cómo el Collector permite muestrear distinto para cada destino. Genera carga 15 minutos y comprueba en el portal: Mapa de aplicación (deben aparecer `api`, `inventario` y la dependencia entre ellos), Transacciones de extremo a extremo y Live Metrics.
21. En Logs (KQL), escribe y guarda en `kql.md`:
    - `requests | summarize peticiones=count(), errores=countif(success == false) by bin(timestamp, 5m), cloud_RoleName | render timechart`.
    - Percentiles de duración por operación: `requests | summarize percentiles(duration, 50, 95, 99) by operation_Name`.
    - Un `join` entre `requests` y `dependencies` por `operation_Id` para ver, por cada petición lenta de `api`, cuánto tardó la llamada a `inventario`; calcula la diferencia como "tiempo propio".
    - Un `join` entre `requests` y `traces` (logs) por `operation_Id` para listar los mensajes de error de una petición fallida.
    - Una consulta con `let` que defina un umbral y devuelva el porcentaje de peticiones que lo superan por hora, con `render columnchart`.
    - Una consulta que responda a "¿qué versión (`application_Version` o el atributo `service.version` que propagaste) tiene más errores?".
22. Compara en una tabla la misma pregunta en PromQL y en KQL (tasa de errores por servicio en 5 minutos). Explica qué modelo de datos hay detrás de cada uno (series temporales frente a tablas de eventos) y qué es fácil en uno y difícil en el otro.
23. Revisa **Service Health** en el portal de Azure: activa una alerta de Service Health para tu suscripción y región (incidentes de servicio y mantenimiento planificado) hacia tu correo. Explica en tres líneas por qué en un incidente lo primero que se mira es si el proveedor tiene un problema conocido y cómo se distingue "es Azure" de "somos nosotros" con tu telemetría.

**Parte G — Ingeniería de alertas y reducción de ruido (3 h)**

24. Añade `alertmanager` al Compose y `rule_files` a Prometheus. Escribe `config/reglas.yml` con **reglas de grabación** para el SLI de disponibilidad (ratio de éxito) y el SLI de latencia (proporción de peticiones bajo 300 ms), a ventanas de 5m, 30m, 1h, 2h, 6h, 1d y 3d, tal y como propone el Workbook.
25. Implementa las alertas **multiventana multi-burn-rate** para un SLO de disponibilidad del 99,5 % en 30 días: página (`severity: page`) con burn rate 14,4 en 1 h y 5 min; ticket (`severity: ticket`) con burn rate 3 en 1 d y 2 h. Ejemplo de la primera, adáptalo a tus métricas:
    ```yaml
    - alert: ErrorBudgetBurnRapido
      expr: (sli:errores:ratio_rate1h > (14.4 * 0.005)) and (sli:errores:ratio_rate5m > (14.4 * 0.005))
      for: 2m
      labels: { severity: page, service: api }
      annotations:
        summary: "api consume el presupuesto de error 14x más rápido de lo sostenible"
        runbook_url: "https://github.com/<tu-usuario>/learning-entregas-<usuario>/blob/main/03-modulo-avanzado/07-observabilidad-avanzada/runbooks/error-budget.md"
    ```
    Calcula a mano cuánto presupuesto consume cada alerta antes de disparar y en cuánto tiempo agotaría el mes. Escribe también una alerta de **síntoma** (p99 de `/pedido` > 1 s durante 5 min) y una de **causa** (`inventario` caído según `up`), y explica cuál de las dos debería paginar y por qué la otra es informativa.
26. Configura Alertmanager: **agrupación** por `service` y `severity`, `group_wait` y `group_interval` razonables, una **ruta** que envíe `page` a un receiver "oncall" y `ticket` a otro "equipo" (pueden ser webhooks a un contenedor que solo imprime, o correo), y una regla de **inhibición**: si `InventarioCaido` está activa, silencia las alertas de latencia de `api`. Crea un **silencio** de 30 minutos con un comentario que incluya el motivo y el ticket, y captúralo.
27. Escribe los **runbooks** enlazados desde `runbook_url` en `runbooks/`: qué significa la alerta, cómo confirmar que es real (dashboard, consulta), primeras acciones de mitigación, cuándo escalar. Regla: si no puedes escribir qué hacer cuando salta, la alerta no debería existir.
28. Prueba de fuego: con `TASA_ERROR=0.05` la alerta rápida no debe disparar y la lenta sí, al cabo de un rato; con `TASA_ERROR=0.5` la rápida debe disparar en pocos minutos. Documenta tiempos observados frente a los teóricos.

**Parte H — Ejercicio final: incidente inyectado (2-3 h, cronometrado)**

29. Pide al mentor o a un compañero que ejecute, sin decirte cuál, uno de estos tres escenarios sobre tu Compose (o usa `bash escenario.sh $((RANDOM % 3))` sin mirar la salida): (a) `LATENCIA_MS=1500` en `inventario`; (b) `TASA_ERROR=0.15` en `inventario`; (c) `FUGA_MEMORIA=1` en `inventario` con un `mem_limit` de 256 MB en Compose para que acabe reiniciando. Que se inyecte mientras hay carga estable.
30. Desde ese momento eres el responder. Solo puedes usar Grafana, Prometheus, Alertmanager, Application Insights y los logs a través de Loki (nada de `docker exec` ni leer el script hasta el final). Registra en `incidente.md` un timeline con marca de tiempo: cuándo saltó la primera alerta y cuál, qué dashboard miraste, qué consulta escribiste, qué hipótesis formulaste, cómo la descartaste o confirmaste, hasta identificar servicio, síntoma y causa probable.
31. Cuando creas saber la causa, compruébala (ahora sí, `docker inspect` o el script) y escribe: tiempo hasta detección (alerta), tiempo hasta diagnóstico, qué señal fue decisiva (métrica, traza o log), qué te faltó en la telemetría y qué cambiarías (una métrica, una etiqueta, un panel, una alerta). Aplica al menos un cambio y repite el escenario para medir si mejora el tiempo de diagnóstico.

**Parte I — Limpieza (20 min)**

32. `docker compose down -v` (borra volúmenes de Prometheus, Loki y Tempo). En Azure, `az group delete --name rg-lab-obs --yes --no-wait`. Al día siguiente, captura Cost Management filtrado por `rg-lab-obs` y la pestaña "Uso y costos estimados" de Application Insights antes de borrarlo (o el uso del workspace), para confirmar que la ingesta quedó muy por debajo de los 5 GB gratuitos.

### Resultado esperado

- Repositorio con `api/`, `inventario/`, `docker-compose.yml`, `config/` (Collector, Prometheus, reglas, Alertmanager), `grafana/dashboards/pedidos.json`, `runbooks/`, `escenario.sh`.
- `diseno-telemetria.md`, `promql.md`, `kql.md`, `laboratorio-observabilidad.md` con las capturas de correlación, dashboards, Mapa de aplicación y alertas.
- `incidente.md` con el timeline del ejercicio final y la mejora aplicada.
- Ningún recurso vivo en Azure y coste de laboratorio en cero.

### Criterios de validación

- [ ] Parte A: la tabla de telemetría distingue tipos de métrica, etiquetas permitidas y prohibidas y calcula la cardinalidad; la estrategia de muestreo está justificada.
- [ ] Parte B: una petición a `/pedido/<id>` genera una traza con spans de ambos servicios y el mismo `trace_id` aparece en los logs de los dos; hay al menos un span, un histograma y un counter manuales.
- [ ] Parte C: el Collector tiene tres pipelines funcionando; desde un log en Loki se llega a la traza en Tempo y de ahí a las métricas, con capturas.
- [ ] Parte D: las consultas PromQL son propias, funcionan y las explicaciones de `rate`, `histogram_quantile` y utilización/saturación son correctas.
- [ ] Parte E: el dashboard está provisionado desde archivo, tiene variables, umbrales y anotaciones, y el estudiante sabe explicar qué pregunta responde cada panel.
- [ ] Parte F: el Mapa de aplicación muestra los dos servicios; las consultas KQL con `join`, `bin`, `percentiles`, `let` y `render` funcionan; la comparación PromQL/KQL es coherente; la alerta de Service Health existe.
- [ ] Parte G: las alertas multiventana están implementadas y probadas con tiempos medidos; hay agrupación, inhibición y un silencio documentado; cada alerta enlaza a un runbook escrito.
- [ ] Parte H: el timeline muestra hipótesis, consultas y descartes reales, identifica la causa correcta sin mirar el script y propone e implementa una mejora medible.
- [ ] El estudiante, en una llamada con el mentor, puede escribir en menos de 5 minutos una consulta PromQL y otra KQL que respondan a una pregunta nueva sobre sus datos.

## Entrega

En tu repositorio de entregas, carpeta `03-modulo-avanzado/07-observabilidad-avanzada/`:

1. Código y configuración: `api/`, `inventario/`, `docker-compose.yml`, `config/`, `grafana/`, `runbooks/`, `escenario.sh` (sin `.env` ni cadenas de conexión).
2. `diseno-telemetria.md`, `promql.md`, `kql.md`.
3. `laboratorio-observabilidad.md` y `capturas/` (con tu usuario o nombre de máquina visibles; oculta la cadena de conexión y el ID de suscripción).
4. `incidente.md`.
5. `ENTREGA.md` con evaluación, checklist y uso de IA.

Nota sobre IA: es legítimo pedir a una IA que te explique un error del Collector o que revise una consulta que ya escribiste. No es legítimo pedirle "las reglas de burn rate" y pegarlas: en la revisión se te pedirá recalcular a mano cuánto presupuesto consume una alerta antes de disparar.

## Evaluación

1. **Conceptual.** Explica con tus palabras la diferencia entre logs, métricas y trazas, qué pregunta responde mejor cada una y por qué el `trace_id` es lo que convierte tres herramientas en un sistema de observabilidad.
2. **Conceptual.** ¿Qué papel juega el OpenTelemetry Collector? Da tres razones por las que es mejor que cada aplicación exporte directamente a Prometheus y a Azure.
3. **Técnica.** Tu compañero añade la etiqueta `user_id` a `http_requests_total` "para poder filtrar por cliente". Tienes 50 000 usuarios, 12 rutas, 5 códigos de estado y 2 servicios. Calcula cuántas series genera y explica qué le pasará a Prometheus y a la factura de Log Analytics. Propón la alternativa correcta.
4. **Técnica.** Escribe la consulta PromQL del p95 de latencia de la ruta `/pedido/{id}` en los últimos 5 minutos y explica por qué `avg(latencia)` es una métrica peligrosa para un servicio con tail latency.
5. **Situacional.** El dashboard muestra p99 de 4 s en `api` pero `inventario` tiene p99 de 40 ms y sin errores. Con la telemetría del laboratorio, describe en orden qué mirarías para saber dónde se pierde el tiempo (pista: tiempo propio del span frente a tiempo de la dependencia).
6. **Conceptual.** Explica el método RED y el método USE, a qué se aplica cada uno y por qué "utilización al 100 %" y "saturación" no son lo mismo.
7. **Técnica.** Escribe una consulta KQL que devuelva, por cada 15 minutos de la última hora, el número de peticiones, el porcentaje de errores y el p95 de duración, y la represente como gráfico temporal. ¿Qué operador de KQL no tiene equivalente directo en PromQL?
8. **Conceptual.** Explica la diferencia entre alertar sobre síntomas y sobre causas con un ejemplo de tu laboratorio. ¿Por qué el SRE Book recomienda que las páginas sean sobre síntomas?
9. **Técnica.** Un SLO de disponibilidad del 99,9 % a 30 días. Calcula el presupuesto de error en minutos y explica qué significa un burn rate de 14,4 en una hora: ¿cuánto presupuesto consume antes de que la alerta dispare y en cuánto tiempo agotaría el mes si siguiera así?
10. **Situacional.** El equipo recibe 400 alertas a la semana y responde a menos del 10 %. Propón un plan en cinco pasos usando severidades, agrupación, inhibición, silencios y runbooks, y di qué métrica seguirías para saber si el plan funciona.
11. **Troubleshooting.** El Collector arranca pero en Tempo no aparece ninguna traza y en Prometheus sí hay métricas. Nombra cuatro causas posibles (configuración de pipeline, red entre contenedores, TLS, muestreo) y el comando o consulta con el que comprobarías cada una.
12. **Troubleshooting.** En Application Insights aparecen las peticiones pero el Mapa de aplicación muestra `api` e `inventario` como dos nodos sin conexión. ¿Qué ha fallado en la propagación de contexto y cómo lo verificarías con `curl -v`?
13. **Situacional.** Tu jefe pide "una alerta si la CPU del nodo pasa del 80 %". Argumenta si esa alerta debería paginar a alguien, qué alerta propondrías en su lugar y en qué caso sí tiene sentido la de CPU.
14. **Conceptual.** ¿Qué es el muestreo de trazas, cuándo debes muestrear en la app (head) y cuándo en el Collector (tail), y por qué las métricas y los logs de error no deberían muestrearse?
15. **Reflexión.** En el incidente inyectado, ¿qué señal fue decisiva y cuál te despistó? ¿Qué cambio en la telemetría redujo más tu tiempo de diagnóstico y qué te llevas para el curso de SRE Avanzado?

## Checklist final

Antes de continuar, deberías poder:

- [ ] Explicar logs, métricas y trazas y cómo se correlacionan con el `trace_id`.
- [ ] Instrumentar un servicio Python con OpenTelemetry (automático y manual) y propagar contexto entre dos servicios.
- [ ] Configurar un Collector con varios pipelines y exportar a Prometheus/Tempo/Loki y a Application Insights a la vez.
- [ ] Diseñar métricas RED y USE con etiquetas de cardinalidad controlada y una estrategia de muestreo.
- [ ] Escribir PromQL con `rate`, `histogram_quantile`, agregaciones, `increase`, `offset` y `topk`.
- [ ] Construir y provisionar un dashboard operacional con variables, umbrales y anotaciones.
- [ ] Escribir KQL con `join`, `summarize by bin()`, `percentiles`, `let` y `render`.
- [ ] Implementar alertas de burn rate multiventana y explicar los números que hay detrás.
- [ ] Configurar agrupación, inhibición y silencios en Alertmanager y escribir un runbook por alerta.
- [ ] Distinguir un problema del proveedor (Service Health) de uno propio.
- [ ] Investigar un incidente desconocido usando solo la telemetría y documentar el razonamiento.
- [ ] Tener `api` e `inventario` con sus interruptores de fallo listos para SRE Avanzado e Incident Management.

---

*Recursos verificados el 2026-09-27 mediante búsqueda web (existencia y vigencia de las URLs). Si un enlace falla, abre un issue en este repositorio.*
