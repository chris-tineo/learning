# Monitoreo y Observabilidad

> Módulo: Intermedio · Curso 9 de 11 · Duración estimada: 20-30 horas · Estado: ✅ Completo

## Objetivo

Ya sabes desplegar: una VM con Terraform, un contenedor con un pipeline. La pregunta que viene después es la que define a un equipo de operaciones: **¿cómo sabes que funciona, y cómo averiguas por qué no funciona a las tres de la mañana sin entrar en el servidor?** Ese es el tema de este curso. **Monitorizar** es vigilar lo que ya sabes que puede fallar (CPU alta, disco lleno, errores 500) y avisar cuando pasa. **Observabilidad** es poder hacerle preguntas nuevas al sistema, a partir de las señales que emite (métricas, logs y trazas), para entender fallos que nadie había previsto.

Vas a trabajar sobre la aplicación que ya tienes desplegada en Azure App Service desde el curso de CI/CD (o, como alternativa, sobre la VM del curso de Terraform). La instrumentarás con **OpenTelemetry** a través del distro de **Azure Monitor** para Python, enviarás su telemetría a **Application Insights** respaldado por un **Log Analytics workspace**, escribirás tus primeras consultas en **KQL**, montarás un panel, configurarás alertas de métrica y de log con aviso por correo, y activarás un health check. Después introducirás a propósito un fallo intermitente y una latencia artificial, los desplegarás con tu pipeline y tendrás que encontrarlos **solo con la telemetría**, sin leer el código ni entrar en el servidor. Eso es exactamente lo que hace un SRE.

Los conceptos (las tres señales, umbrales, alertas, SLI) son los mismos con Prometheus y Grafana, que verás en Observabilidad Avanzada; aquí la herramienta es Azure Monitor porque es la que trae la plataforma que ya usas y la que te van a pedir en cualquier empresa con Azure. Ojo con el coste: la telemetría se paga por gigabyte ingerido. Aprenderás a controlarlo desde el primer minuto.

**Antes de empezar** necesitas `api-curso` (la aplicación del curso de Docker) desplegada con el pipeline del curso de CI/CD (repositorio, imagen en GHCR, web app en App Service) o, al menos, poder redesplegarla en 10 minutos con lo que ya tienes.

### Al terminar este curso deberías poder

- Explicar con tus palabras la diferencia entre monitoring y observability y por qué la segunda importa en sistemas distribuidos.
- Distinguir métricas, logs y trazas, dar un ejemplo de cada una de tu aplicación y decir qué pregunta responde cada señal.
- Explicar qué son Azure Monitor, Log Analytics y Application Insights, cómo se relacionan y qué cuesta cada uno.
- Instrumentar una aplicación Python con el distro de OpenTelemetry de Azure Monitor y verificar que llegan peticiones, dependencias, excepciones y logs.
- Escribir consultas KQL introductorias (`where`, `summarize`, `count`, `percentiles`, `render`, `join` sencillo) sobre las tablas de Application Insights.
- Construir un panel y un workbook con las métricas y consultas que importan para tu servicio.
- Crear alertas de métrica y de búsqueda de logs con umbrales razonados y un action group por correo, y explicar qué es un umbral demasiado sensible.
- Configurar un health check y explicar qué debe comprobar `/health` y qué no.
- Diagnosticar un problema real de una aplicación (errores intermitentes, latencia) usando solo telemetría y documentar el diagnóstico.
- Controlar la ingesta y el coste de Log Analytics (límite diario, retención, muestreo) y limpiar los recursos al terminar.

## Prerrequisitos

- Curso 7: CI/CD (la aplicación desplegada en App Service y su pipeline para redesplegar cambios).
- Curso 5: Administración de Azure (ya viste Azure Monitor y Log Analytics de forma introductoria; aquí se profundiza).
- Curso 3: Bash y Python para Automatización (vas a tocar el código de la aplicación).
- Curso 8: Terraform (solo si eliges la VM como alternativa de destino).
- Cuenta de Azure con presupuesto y alertas activos.

## Temario

- Monitoring frente a Observability.
- Metrics.
- Logs.
- Traces.
- Dashboards.
- Alertas.
- Thresholds.
- Health checks.
- Azure Monitor.
- Log Analytics.
- Application Insights.
- KQL introductorio.

## Recursos en español

### Aspectos básicos de Azure Monitor · Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/training/paths/monitor-usage-performance-availability-resources-azure-monitor/ · Módulo de conjunto de herramientas: https://learn.microsoft.com/es-es/training/modules/describe-monitoring-tools-azure/
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Ruta de aprendizaje (6 módulos) con ejercicios
- **Duración aproximada:** 4-5 h
- **Cubre:** Azure Monitor, métricas, registros, Log Analytics, alertas, Application Insights, análisis de infraestructura con consultas.
- **Nivel:** Introductorio
- **Acceso:** Libre; cuenta Microsoft gratuita para guardar progreso. Algunos ejercicios usan tu suscripción: haz los de sandbox y deja los de pago para el laboratorio
- **Por qué lo recomiendo:** Es el material oficial en español que recorre todas las piezas de Azure Monitor en orden. Es el recurso principal; el laboratorio da por hecho que lo has terminado.

### Supervisión del rendimiento de la aplicación (Application Insights) · Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/training/modules/monitor-app-performance/ · Ruta completa AZ-204 de la que forma parte: https://learn.microsoft.com/es-es/training/paths/az-204-instrument-solutions-support-monitoring-logging/
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Módulo de aprendizaje
- **Duración aproximada:** 1-1,5 h
- **Cubre:** Application Insights, instrumentación, métricas de aplicación, disponibilidad, mapa de aplicación.
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es el módulo que explica qué hace Application Insights por ti y qué tienes que hacer tú (instrumentar). Está orientado a desarrolladores, que es justo la perspectiva que te falta para hablar con ellos.

### Escritura de la primera consulta con el lenguaje de consulta Kusto · Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/training/modules/write-first-query-kusto-query-language/
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Módulo de aprendizaje con consultas sobre un clúster de ejemplo gratuito
- **Duración aproximada:** 1 h
- **Cubre:** KQL introductorio: `take`, `project`, `count`, `where`, `sort`, `summarize`.
- **Nivel:** Introductorio
- **Acceso:** Libre; el clúster de ejemplo `help` no cuesta nada
- **Por qué lo recomiendo:** KQL es el mismo lenguaje en Log Analytics, Application Insights, Sentinel y Azure Data Explorer. Aprenderlo con datos de meteorología es más fácil que con tus logs, y después lo aplicas igual.

### AZ-104: Supervisión y copia de seguridad de recursos de Azure · Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/training/paths/az-104-monitor-backup-resources/
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Ruta de aprendizaje
- **Duración aproximada:** 2 h para los módulos de supervisión (salta los de copia de seguridad por ahora)
- **Cubre:** Azure Monitor, alertas, Log Analytics desde el punto de vista del administrador.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Complementario. Repite parte de la ruta principal desde la óptica de la certificación AZ-104; útil si te planteas certificarte y como repaso rápido antes de la evaluación.

## Recursos en inglés

### Monitoring Distributed Systems (SRE Book, capítulo 6) · Google
- **URL:** https://sre.google/sre-book/monitoring-distributed-systems/ (índice del libro: https://sre.google/sre-book/table-of-contents/)
- **Autor / organización:** Rob Ewaschuk, Google SRE
- **Idioma:** Inglés
- **Tipo:** Capítulo de libro (gratuito online)
- **Duración aproximada:** 45-60 min
- **Cubre:** Por qué monitorizar, las cuatro señales de oro (latencia, tráfico, errores, saturación), síntomas frente a causas, alertas que despiertan a alguien frente a las que no.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es el texto de referencia sobre qué merece una alerta y qué no. Las cuatro señales de oro son el criterio con el que diseñarás las alertas del laboratorio y los SLI del curso de DevOps y SRE.

### Observability primer y conceptos · OpenTelemetry
- **URL:** https://opentelemetry.io/docs/concepts/observability-primer/ · Conceptos: https://opentelemetry.io/docs/concepts/ · Python, primeros pasos: https://opentelemetry.io/docs/languages/python/getting-started/
- **Autor / organización:** Proyecto OpenTelemetry (CNCF)
- **Idioma:** Inglés
- **Tipo:** Documentación oficial
- **Duración aproximada:** 45 min para primer y conceptos; 45 min para el tutorial de Python (opcional)
- **Cubre:** Observabilidad, señales (trazas, métricas, logs), spans, instrumentación, propagación de contexto.
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** OpenTelemetry es el estándar abierto que usan hoy Azure Monitor, Grafana, Datadog y todos los demás. Entender sus conceptos te independiza de la herramienta. El distro de Azure que usarás en el laboratorio es OpenTelemetry con un exportador.

### Application Insights con OpenTelemetry · Microsoft Learn
- **URL:** Introducción: https://learn.microsoft.com/en-us/azure/azure-monitor/app/app-insights-overview · Habilitar OpenTelemetry (Python): https://learn.microsoft.com/en-us/azure/azure-monitor/app/opentelemetry-enable · Configuración (muestreo, variables): https://learn.microsoft.com/en-us/azure/azure-monitor/app/opentelemetry-configuration · Paquete `azure-monitor-opentelemetry`: https://learn.microsoft.com/en-us/python/api/overview/azure/monitor-opentelemetry-readme?view=azure-python
- **Autor / organización:** Microsoft
- **Idioma:** Inglés (la introducción existe en es-es cambiando `en-us` por `es-es`)
- **Tipo:** Documentación oficial
- **Duración aproximada:** 1,5 h
- **Cubre:** Application Insights, instrumentación de Python (Flask, FastAPI, Django, requests, logging), muestreo, conexión con Log Analytics.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la guía exacta de la parte B del laboratorio. Sigue el tutorial de Python para tu framework y, si algo no llega a Application Insights, la respuesta está en la página de configuración.

### Observability, a 3-Year Retrospective · Charity Majors (Honeycomb)
- **URL:** https://www.honeycomb.io/blog/observability-a-3-year-retrospective
- **Autor / organización:** Charity Majors, cofundadora de Honeycomb
- **Idioma:** Inglés
- **Tipo:** Artículo
- **Duración aproximada:** 20-30 min
- **Cubre:** Monitoring frente a observability, "unknown unknowns", eventos de alta cardinalidad, por qué los dashboards no bastan.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la persona que popularizó el término en la industria explicando qué quiso decir y qué no. Léelo con espíritu crítico: es una opinión fundada, no documentación, pero te dará el vocabulario para la primera pregunta de la evaluación.

### Kusto Detective Agency · Microsoft (opcional)
- **URL:** https://detective.kusto.io/
- **Autor / organización:** Microsoft (equipo de Azure Data Explorer)
- **Idioma:** Inglés
- **Tipo:** Juego de retos con KQL sobre datos reales
- **Duración aproximada:** 1-2 h por caso; hazlo en ratos libres
- **Cubre:** KQL de introductorio a avanzado.
- **Nivel:** Introductorio a avanzado
- **Acceso:** Libre; requiere cuenta Microsoft y crear un clúster gratuito de Kusto (sin tarjeta, sin coste)
- **Por qué lo recomiendo:** Es la forma más entretenida de coger soltura con KQL. Los dos o tres primeros casos son suficientes para este curso; el resto es para quien se enganche.

## Documentación oficial

- **Azure Monitor (introducción):** https://learn.microsoft.com/en-us/azure/azure-monitor/fundamentals/overview · Primeros pasos (es-es): https://learn.microsoft.com/es-es/azure/azure-monitor/fundamentals/getting-started
- **Log Analytics:** workspace: https://learn.microsoft.com/en-us/azure/azure-monitor/logs/log-analytics-workspace-overview · herramienta Log Analytics: https://learn.microsoft.com/en-us/azure/azure-monitor/logs/log-analytics-overview · límite diario: https://learn.microsoft.com/en-us/azure/azure-monitor/logs/daily-cap
- **Coste de Azure Monitor:** coste y uso: https://learn.microsoft.com/en-us/azure/azure-monitor/fundamentals/cost-usage · cálculo de costes de logs: https://learn.microsoft.com/en-us/azure/azure-monitor/logs/cost-logs · optimización: https://learn.microsoft.com/en-us/azure/azure-monitor/fundamentals/best-practices-cost · precios: https://azure.microsoft.com/en-us/pricing/details/monitor/
- **Application Insights:** crear recurso basado en workspace: https://learn.microsoft.com/en-us/azure/azure-monitor/app/create-workspace-resource · métricas: https://learn.microsoft.com/en-us/azure/azure-monitor/app/metrics-overview · OpenTelemetry Python: https://learn.microsoft.com/en-us/azure/azure-monitor/app/opentelemetry-enable
- **KQL:** referencia rápida: https://learn.microsoft.com/en-us/kusto/query/kql-quick-reference · tutorial de operadores comunes: https://learn.microsoft.com/en-us/kusto/query/tutorials/learn-common-operators · portal: https://learn.microsoft.com/en-us/kusto/query/
- **Alertas:** introducción: https://learn.microsoft.com/en-us/azure/azure-monitor/alerts/alerts-overview · alerta de métrica: https://learn.microsoft.com/en-us/azure/azure-monitor/alerts/alerts-create-metric-alert-rule · alerta de búsqueda de logs: https://learn.microsoft.com/en-us/azure/azure-monitor/alerts/alerts-create-log-alert-rule · action groups: https://learn.microsoft.com/en-us/azure/azure-monitor/alerts/action-groups
- **Workbooks:** https://learn.microsoft.com/en-us/azure/azure-monitor/visualize/workbooks-overview · crear: https://learn.microsoft.com/en-us/azure/azure-monitor/visualize/workbooks-create-workbook
- **App Service:** health check: https://learn.microsoft.com/en-us/azure/app-service/monitor-instances-health-check · supervisión de App Service: https://learn.microsoft.com/en-us/azure/app-service/monitor-app-service
- **Google SRE Book:** https://sre.google/sre-book/table-of-contents/ · **OpenTelemetry:** https://opentelemetry.io/docs/

## Ruta recomendada de estudio

1. **Leer** el capítulo "Monitoring Distributed Systems" del SRE Book (60 min). Anota las cuatro señales de oro y la distinción entre síntoma y causa.
2. **Leer** el Observability primer de OpenTelemetry y el artículo de Charity Majors (60 min). Escribe con tus palabras la diferencia entre monitoring y observability y qué es una "unknown unknown".
3. **Hacer** la ruta "Aspectos básicos de Azure Monitor" (4-5 h). Deja los ejercicios que creen recursos de pago para el laboratorio.
4. **Hacer** "Escritura de la primera consulta con KQL" (1 h) y **hojear** la referencia rápida de KQL.
5. **Hacer** el módulo "Supervisión del rendimiento de la aplicación" (1,5 h) y **leer** la introducción de Application Insights y la página de OpenTelemetry para Python (1 h).
6. **Leer** las páginas de coste de Azure Monitor y de límite diario (45 min). No crees el workspace hasta haberlas leído.
7. **Hacer el laboratorio**, partes A a E (8-10 h, en varias sesiones).
8. **Leer** la documentación de alertas y de health check (45 min) y **hacer** las partes F y G.
9. **Hacer** la parte H (diagnóstico) sin mirar el código: esa es la prueba de fuego del curso.
10. **Opcional:** dos casos de Kusto Detective Agency y la ruta AZ-104 de supervisión como repaso.
11. **Responder la evaluación** y **revisar el checklist**.

Si vas justo de tiempo: haz obligatoriamente los puntos 1, 3, 4, 6, 7, 8 y 9.

## Laboratorio

### Objetivo

Dotar de observabilidad completa a la aplicación desplegada en el curso de CI/CD: telemetría con OpenTelemetry y Application Insights sobre un Log Analytics workspace con la ingesta controlada, consultas KQL, panel y workbook, alertas de métrica y de log con correo, health check, y un ejercicio de diagnóstico a ciegas de un fallo introducido a propósito.

### Requisitos

- `api-curso` desplegada en App Service (`app-<usuario>-staging`) con el pipeline del curso de CI/CD operativo. Si borraste `rg-cicd`, vuelve a crear el plan y la web app con los comandos de aquel laboratorio (10 min).
- Alternativa: la VM del curso de Terraform ejecutando la aplicación con Docker; la instrumentación es idéntica, cambian el health check (usa una prueba de disponibilidad) y las métricas de plataforma (las de la VM).
- Azure CLI autenticada y acceso al repositorio de la aplicación.
- Convención: documenta en `laboratorio-observabilidad.md`; guarda cada consulta KQL en `consultas.kql` con un comentario `//` que diga qué responde.

> **Sobre el coste.** Log Analytics cobra por GB ingerido (unos 2-3 USD/GB en el plan de pago por uso) y por retención más allá de la incluida; los primeros GB al mes suelen estar cubiertos por la asignación gratuita de la cuenta (comprueba la cifra vigente en la página de precios: históricamente 5 GB/mes). Una aplicación de laboratorio con unos cientos de peticiones genera **megabytes**, no gigabytes. Las alertas de métrica cuestan céntimos por serie al mes; las alertas de búsqueda de logs, del orden de 1-2 USD al mes por regla según la frecuencia; el health check de App Service es gratuito; las pruebas de disponibilidad estándar se cobran por ejecución (céntimos). Aun así: **límite diario en el workspace desde el minuto uno**, borrado de reglas y recursos al terminar, y comprobación en Cost Management al día siguiente.

### Instrucciones

**Parte A: workspace y Application Insights con la ingesta controlada (1 h)**

1. Crea el grupo `rg-observabilidad` y un **Log Analytics workspace** `law-<usuario>` (plan de pago por uso, retención 30 días). En Uso y costes estimados → Límite diario, fija **0,1 GB/día**. Explica qué pasa cuando se alcanza el límite (¿se pierden datos? ¿afecta a las alertas?) y por qué en producción se ajusta con cuidado.
2. Crea un recurso de **Application Insights** basado en workspace `appi-<usuario>` enlazado a `law-<usuario>`. Copia la **cadena de conexión** (no la clave de instrumentación: explica la diferencia). Explica la relación Azure Monitor → Log Analytics workspace → Application Insights y qué tablas del workspace va a rellenar la aplicación (`AppRequests`, `AppDependencies`, `AppExceptions`, `AppTraces`, `AppPerformanceCounters`).
3. Sin haber instrumentado nada todavía, abre Monitor → Métricas y selecciona la web app: mira `Requests`, `Http Server Errors`, `Response Time`, `CPU Time`. Explica qué son las **métricas de plataforma**, quién las emite (Azure, no tu código), por qué son gratuitas y qué no pueden decirte (pista: qué endpoint falla).

**Parte B: instrumentar la aplicación con OpenTelemetry (2-3 h)**

4. En el repositorio de la aplicación añade `azure-monitor-opentelemetry` a `app/requirements.txt` y, al arrancar la app, antes de crear rutas:
   ```python
   import logging, os
   from azure.monitor.opentelemetry import configure_azure_monitor

   if os.getenv("APPLICATIONINSIGHTS_CONNECTION_STRING"):
       configure_azure_monitor(logger_name="app")
   logger = logging.getLogger("app")
   logger.setLevel(logging.INFO)
   ```
   La aplicación es Flask, que el distro instrumenta solo (con FastAPI habría que añadir su instrumentación sobre el objeto `app`; mira la documentación). Ten en cuenta que gunicorn arranca varios workers: cada uno inicializa su propia telemetría. Añade en `/` un `logger.info("raiz solicitada", extra={"hostname": ...})` y en `/health` nada (los health checks generan ruido: razona si quieres excluirlos de la telemetría y cómo). Comprueba que `ruff` y `pytest` siguen pasando sin la variable de entorno definida.
5. Añade la cadena de conexión como **secreto** de repositorio `APPINSIGHTS_CONNECTION_STRING` y, en el job de despliegue de staging, un step con `az webapp config appsettings set` que fije `APPLICATIONINSIGHTS_CONNECTION_STRING` desde ese secreto (o hazlo una vez a mano con la CLI y documenta por qué preferirías que lo hiciera el pipeline). Haz push a `main` y espera al despliegue.
6. Genera tráfico desde tu equipo: un bucle de 200 peticiones a `/`, 50 a `/health` y 20 a una ruta inexistente `/no-existe`. Abre Application Insights → **Live Metrics** mientras corre el bucle y captura. Después (espera 2-5 min) revisa **Transaction search**, **Application map**, **Performance** y **Failures**. Explica qué señal (métrica, log, traza) estás viendo en cada pantalla y de dónde sale el hostname en las trazas.

**Parte C: primeras consultas KQL (2 h)**

7. En Application Insights → Logs ejecuta y guarda en `consultas.kql` al menos estas consultas, adaptando nombres:
   ```kusto
   // 1. Peticiones por código de respuesta en la última hora
   requests | where timestamp > ago(1h) | summarize total = count() by resultCode | order by total desc
   // 2. Latencia p50, p95 y p99 por operación
   requests | where timestamp > ago(1h) | summarize percentiles(duration, 50, 95, 99) by name
   // 3. Peticiones por minuto en gráfico de tiempo
   requests | where timestamp > ago(1h) | summarize count() by bin(timestamp, 1m) | render timechart
   // 4. Tasa de error (%) por operación
   requests | where timestamp > ago(1h) | summarize errores = countif(success == false), total = count() by name | extend tasa_error = round(100.0 * errores / total, 2)
   // 5. Tus logs de aplicación con su hostname
   traces | where timestamp > ago(1h) | project timestamp, message, severityLevel, customDimensions
   // 6. Excepciones con la petición que las provocó
   exceptions | join kind=inner (requests | project operation_Id, name, url) on operation_Id | project timestamp, type, outerMessage, name, url
   ```
   Explica cada operador que uses. Ejecuta la consulta 1 también desde el **workspace** (Log Analytics → tabla `AppRequests`) y anota qué cambia en los nombres de columnas.
8. Escribe **tres consultas propias** que respondan a preguntas que se te ocurran (por ejemplo, "¿qué hostname atendió más peticiones?", "¿a qué hora hubo más 404?"). Consulta la tabla `Usage` del workspace para ver cuántos MB has ingerido por tipo de dato y compáralo con el límite diario.

**Parte D: panel y workbook (1 h)**

9. Desde Métricas, ancla a un **dashboard** nuevo `Panel <usuario>` las gráficas de `Requests`, `Http Server Errors` y `Response Time` de la web app, y desde Logs ancla las consultas 3 y 4. Crea un **Workbook** con un parámetro de rango de tiempo, un texto de cabecera, la consulta de latencia p95 como gráfico y la tasa de error como tabla con formato condicional. Explica cuándo usarías dashboard y cuándo workbook, y por qué un panel lleno de gráficas no sustituye a una alerta.

**Parte E: alertas y umbrales (1,5 h)**

10. Crea un **action group** `ag-correo-<usuario>` con notificación por correo a tu dirección. Confirma el correo de prueba.
11. Crea una **alerta de métrica** sobre la web app: `Http Server Errors` mayor que 5 en 5 minutos, evaluada cada minuto, gravedad 2. Crea una **alerta de búsqueda de logs** sobre Application Insights con la consulta 4 adaptada: dispara cuando `tasa_error` de cualquier operación supere el 10 % con al menos 20 peticiones en la ventana de 5 minutos, evaluada cada 5 minutos. Razona cada umbral apoyándote en las cuatro señales de oro y en la distinción síntoma/causa del SRE Book. Explica la diferencia entre ambas alertas (qué detecta antes, qué cuesta más, cuál puede preguntar "qué endpoint").
12. Prueba las alertas: genera 30 peticiones a una ruta que devuelva 500 (la añadirás en la parte H; de momento usa `/no-existe` y observa que **no** dispara: explica por qué un 404 no es un error de servidor). Anota el tiempo entre el fallo y el correo cuando la pruebes de verdad en la parte H.

**Parte F: health check (30 min)**

13. En la web app, Supervisión → Health check: habilítalo con la ruta `/health`. Si tu plan (F1) no permite activarlo, crea en su lugar una **prueba de disponibilidad estándar** en Application Insights contra `/health` desde una sola ubicación cada 15 minutos (coste de céntimos; bórrala al final). Añade una alerta si el estado de salud cae por debajo de 100 (o si la disponibilidad falla). Explica qué debería comprobar `/health` en una aplicación con base de datos y cola, qué **no** debería hacer (llamadas lentas, dependencias externas no críticas) y qué hace App Service cuando una instancia falla el health check con dos o más instancias.

**Parte G: métricas de plataforma frente a métricas de aplicación (30 min)**

14. Completa una tabla con al menos 8 filas: cada fila una pregunta operativa ("¿la app está caída?", "¿qué endpoint es lento?", "¿cuánta CPU consume?", "¿qué error exacto ve el usuario?", "¿qué versión está desplegada?"...) y la señal y la herramienta con la que la respondes (métrica de plataforma, métrica de App Insights, log, traza, health check). Añade la columna de equivalente en AWS (CloudWatch, X-Ray) y GCP (Cloud Monitoring, Cloud Trace) a partir de una búsqueda rápida.

**Parte H: diagnóstico a ciegas (2-3 h)**

15. En una rama `feature/pedidos` añade a la aplicación un endpoint `GET /pedidos` que, sin que se note en el código a primera vista, falle el **20 %** de las veces con un 500 (excepción real, no un `return 500`) y en el resto de las veces duerma un tiempo aleatorio entre 0 y 2 segundos antes de responder. Escribe un test que no detecte el fallo (piensa por qué no lo detecta) para que el CI pase. Fusiona y crea el tag `v1.3.0`; despliega a staging con tu pipeline. Si trabajas con un compañero, mejor aún: que sea él quien introduzca el fallo sin decirte cuál es.
16. Cierra el editor. Lanza 300 peticiones a `/pedidos` y 100 a `/`. Con **solo el portal** (Failures, Performance, Transaction search, Live Metrics y tus consultas KQL) responde por escrito, con capturas: ¿qué endpoint falla? ¿con qué frecuencia exacta? ¿qué excepción y en qué línea de qué archivo? ¿cuál es su p50 y p95 frente a los de `/`? ¿desde cuándo ocurre y coincide con el despliegue de `v1.3.0`? ¿llegó el correo de la alerta de log, cuánto tardó, y disparó la alerta de métrica? Escribe un **informe de diagnóstico** de una página: síntoma, evidencia (consultas y capturas), causa probable, impacto, recomendación.
17. Recupera el servicio con el **rollback** del curso de CI/CD a `v1.2.1`, verifica en KQL que la tasa de error vuelve a 0 y que la alerta pasa a resuelta. Después arregla el endpoint de verdad y publica `v1.3.1`. Reflexiona: ¿qué te faltó en la telemetría para ir más rápido? ¿qué añadirías a la app (un log con el id de pedido, un atributo en el span, una métrica de negocio)?

**Parte I: limpieza y verificación de coste (30 min)**

18. Borra las reglas de alerta, la prueba de disponibilidad si la creaste, el action group, el dashboard y el workbook. Elimina la app setting `APPLICATIONINSIGHTS_CONNECTION_STRING` (o déjala si vas a seguir con la app; sin destino no cuesta). Borra `rg-observabilidad` con `az group delete` (el workspace queda 14 días en borrado suave: explica qué implica y cómo se purga). Consulta antes la tabla `Usage` una última vez y anota los MB totales ingeridos. Al día siguiente captura Cost Management filtrado por `rg-observabilidad` y anota la cifra.

### Resultado esperado

- Aplicación instrumentada (cambio en el repositorio y pipeline que inyecta la cadena de conexión), con telemetría visible en Application Insights.
- `consultas.kql` con al menos 9 consultas comentadas.
- `laboratorio-observabilidad.md` con capturas (Live Metrics, Application map, panel, workbook, alertas, correo recibido, Usage, Cost Management), la tabla de señales y el **informe de diagnóstico** de la parte H.
- Recursos borrados y coste verificado.

### Criterios de validación

- [ ] El workspace tiene límite diario y retención definidos antes de recibir datos; la explicación de la relación Monitor → workspace → Application Insights es correcta.
- [ ] La aplicación envía peticiones, excepciones y logs propios; el hostname aparece en la telemetría; los tests siguen pasando sin la variable de entorno.
- [ ] Las 9 consultas KQL funcionan, están comentadas y los operadores están explicados; hay una ejecución equivalente desde el workspace.
- [ ] Panel y workbook existen con las gráficas pedidas y el estudiante distingue su uso.
- [ ] Las dos alertas y el action group existen, los umbrales están razonados con las señales de oro, y hay un correo real recibido durante la parte H con el tiempo anotado.
- [ ] Health check (o prueba de disponibilidad) configurado y explicado, incluidas las limitaciones del plan.
- [ ] El informe de diagnóstico identifica endpoint, frecuencia, excepción, latencia y momento de inicio **solo con telemetría**, y el rollback está verificado con KQL.
- [ ] La tabla de señales tiene al menos 8 filas correctas con equivalentes en AWS y GCP.
- [ ] Todo borrado, MB ingeridos anotados y captura de coste del día siguiente.

## Entrega

En tu repositorio de entregas, carpeta `02-modulo-intermedio/09-monitoreo-y-observabilidad/`:

1. `laboratorio-observabilidad.md` (con el informe de diagnóstico como sección propia o como `informe-diagnostico.md`).
2. `consultas.kql`.
3. Enlace al commit o PR de instrumentación en el repositorio de la aplicación y al run del pipeline que desplegó `v1.3.0` y el rollback.
4. `senales.md` con la tabla de preguntas, señales y equivalencias.
5. Carpeta `capturas/` (oculta la cadena de conexión y los IDs de suscripción).
6. `ENTREGA.md` con evaluación, checklist y uso de IA.

Nota sobre IA: en la parte H está prohibido pedirle a una IA que te diga dónde está el fallo enseñándole el código. Sí puedes pedirle que te explique un operador de KQL o una pantalla del portal. Declara el uso.

## Evaluación

1. **Conceptual.** Explica con tus palabras monitoring frente a observability. Da un ejemplo del laboratorio de una pregunta que responde el monitoring y otra que solo responde la observabilidad.
2. **Conceptual.** Métricas, logs y trazas: define cada una, di qué tabla de Application Insights la contiene y qué pregunta de la parte H respondiste con cada una.
3. **Técnica.** ¿Qué relación hay entre Azure Monitor, un Log Analytics workspace y Application Insights? ¿Qué se paga en cada uno y qué hiciste para acotarlo?
4. **Situacional.** Un compañero propone activar el registro de todas las peticiones con cuerpo y cabeceras "para tener toda la información". Explica qué pasaría con el coste y el límite diario, y qué alternativa propones (muestreo, nivel de log, exclusión de health checks).
5. **Técnica.** Explica la consulta de tasa de error: qué hace `countif`, `summarize ... by`, `extend`, y por qué el `100.0` lleva decimal. ¿Cómo la modificarías para ver la tasa por minuto?
6. **Conceptual.** Las cuatro señales de oro: nómbralas y di qué métrica o consulta del laboratorio mide cada una. ¿Cuál no mediste y cómo lo harías?
7. **Situacional.** Una alerta de CPU > 80 % se dispara cada noche durante el backup y nadie la mira ya. Explica qué está mal (síntoma frente a causa, umbral, fatiga de alertas) y cómo la rediseñarías.
8. **Técnica.** Alerta de métrica frente a alerta de búsqueda de logs: diferencias en latencia de detección, coste y capacidad de expresar condiciones. ¿Cuál usarías para "el servicio está caído" y cuál para "el endpoint de pago falla más del 5 %"?
9. **Troubleshooting.** Instrumentaste la aplicación, la desplegaste, generaste tráfico y en Application Insights no aparece nada. Enumera cuatro comprobaciones en orden (variable de entorno, cadena de conexión, tiempo de ingesta, límite diario, salida a Internet de la app).
10. **Conceptual.** ¿Qué debe comprobar un endpoint `/health` y qué no? ¿Qué diferencia hay entre el health check de App Service y una prueba de disponibilidad externa? ¿Cuál detecta un problema de DNS público?
11. **Situacional.** Describe cómo encontraste el fallo de la parte H: qué pantalla o consulta miraste primero, qué descartaste, cómo confirmaste la causa. Si hubieras tenido dos réplicas de la app, ¿qué habrías mirado para saber si fallaban las dos?
12. **Técnica.** ¿Qué es OpenTelemetry y qué papel juega el distro de Azure Monitor? Si mañana la empresa cambia a Grafana, ¿qué parte de tu instrumentación cambiaría y cuál no?
13. **Conceptual.** Traduce a AWS y GCP: Log Analytics workspace, Application Insights, alerta de métrica, action group. ¿Qué concepto no tiene traducción directa?
14. **Reflexión.** ¿Qué te sorprendió más al ver tu aplicación "desde fuera"? ¿Qué cambiarías en la aplicación del curso de Docker para que fuera más observable desde el diseño?

## Checklist final

Antes de continuar, deberías poder:

- [ ] Explicar monitoring frente a observability y las tres señales con ejemplos propios.
- [ ] Explicar la relación Azure Monitor, Log Analytics y Application Insights y qué cuesta cada pieza.
- [ ] Crear un workspace con límite diario y retención razonados.
- [ ] Instrumentar una aplicación Python con el distro de OpenTelemetry de Azure Monitor y verificar la telemetría.
- [ ] Escribir consultas KQL con `where`, `summarize`, `percentiles`, `bin`, `render` y un `join` sencillo.
- [ ] Construir un panel y un workbook útiles y saber cuándo no bastan.
- [ ] Crear alertas de métrica y de log con umbrales razonados y un action group por correo.
- [ ] Configurar un health check y explicar qué debe comprobar.
- [ ] Diagnosticar un fallo intermitente y una latencia solo con telemetría y escribir el informe.
- [ ] Controlar la ingesta, limpiar los recursos y verificar el coste.
- [ ] Tener la aplicación instrumentada en el repositorio (la reutilizarás en Observabilidad Avanzada y en el Proyecto Final).

---

*Recursos verificados el 2026-09-27 mediante búsqueda web (existencia y vigencia de las URLs). Si un enlace falla, abre un issue en este repositorio.*
