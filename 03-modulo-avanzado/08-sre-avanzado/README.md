# SRE Avanzado

> Módulo: Avanzado · Curso 8 de 12 · Duración estimada: 35-45 horas · Estado: ✅ Completo

## Objetivo

En Fundamentos de DevOps y SRE aprendiste el vocabulario: SLI, SLO, error budget, toil, postmortem. En Observabilidad Avanzada construiste la telemetría que lo hace medible. Este curso junta las dos cosas y te pide lo que se le pide a un SRE de verdad: **definir el modelo de confiabilidad completo de un servicio** y defenderlo con datos.

No es un curso de leer a Google. Vas a tomar la aplicación del curso de Docker (ya con `api` e `inventario` instrumentados), añadirle las dependencias que tiene cualquier servicio real (una base de datos y un proveedor externo que a veces falla) y responder con números a las preguntas que hace el negocio: ¿cómo de fiable es?, ¿cómo de fiable debería ser?, ¿cuánto nos cuesta el siguiente nueve?, ¿qué hacemos cuando fallamos más de lo prometido?, ¿hasta cuántos usuarios aguanta?, ¿qué pasa si se cae la base de datos? Cada respuesta se apoya en telemetría real que tú generas, no en suposiciones.

La segunda parte es ingeniería: harás que el servicio **falle bien**. Timeouts, reintentos con backoff y jitter, circuit breaker, un feature flag para degradar funcionalidad, y un experimento de caos controlado con hipótesis escrita antes de romper nada. Terminarás con un conjunto de documentos (especificaciones de SLI, documento de SLO, política de error budget, análisis de riesgos, fichas de experimento) que son exactamente los que se piden en una entrevista de SRE y los que usarás en el Proyecto Final.

**Antes de empezar** necesitas el repositorio del curso anterior funcionando (Compose con Collector, Prometheus, Grafana y Application Insights) y las alertas de burn rate ya implementadas.

### Al terminar este curso deberías poder

- Especificar un SLI con precisión: qué eventos cuentan, qué se considera "bueno", dónde se mide y con qué consulta exacta (PromQL o KQL).
- Elegir objetivos y ventanas de SLO justificados con datos históricos y explicar la diferencia entre SLO, SLA y objetivo interno.
- Calcular el error budget de un servicio, redactar su política y explicar qué decisiones cambia cuando se agota.
- Implementar y calibrar alertas de burn rate ligadas a un SLO real y verificar su comportamiento con tráfico.
- Inventariar el toil de una operación, priorizarlo y eliminar una tarea con automatización real.
- Hacer capacity planning básico: modelo de crecimiento, prueba de carga hasta saturación con k6 o hey e interpretación de percentiles y tail latency.
- Implementar en Python timeouts, reintentos con backoff exponencial y jitter, circuit breaker y feature flags de degradación, y demostrar su efecto con telemetría.
- Elaborar una matriz de riesgos y un análisis de modos de fallo (FMEA simplificado) de un servicio y sus dependencias.
- Diseñar, ejecutar y documentar un experimento de caos controlado con hipótesis, radio de impacto y criterio de aborto.
- Explicar los patrones de confiabilidad principales (bulkhead, circuit breaker, load shedding, cache de respaldo, colas) y cuándo aplican.

## Prerrequisitos

- Curso 7 del Módulo Avanzado, Observabilidad Avanzada: `api` e `inventario` instrumentados, stack local y alertas de burn rate funcionando.
- Módulo Intermedio: Fundamentos de DevOps y SRE, Docker, Bash y Python para Automatización.
- Módulo Avanzado: Kubernetes Avanzado (el experimento de caos usa `kind`), Helm opcional.
- Docker Compose y `kind` en tu equipo; Python 3.10+; `k6` o `hey` instalados.
- Cuenta de Azure solo para mantener Application Insights del curso anterior (opcional; todo el laboratorio funciona en local).

## Temario

SLI · SLO · SLA · Error Budgets · Reliability engineering · Toil reduction · Capacity planning · Performance · Graceful degradation · Fault tolerance · Reliability patterns · Automation · Risk · Engineering for failure.

**Práctica:** definir el modelo de confiabilidad de un servicio.

## Recursos en español

### Microsoft Learn en español — Ingeniería de confiabilidad de sitios y pilar de confiabilidad de Well-Architected
- **URL:** https://learn.microsoft.com/es-es/azure/ (desde el buscador del portal: módulo "Introducción a la ingeniería de confiabilidad de sitios (SRE)" en Training, y "Azure Well-Architected Framework" > pilar "Confiabilidad")
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Módulo de aprendizaje y documentación de arquitectura
- **Duración aproximada:** 1 h el módulo; 2-3 h las páginas del pilar de confiabilidad (principios de diseño, análisis de modos de fallo, objetivos de confiabilidad, autorreparación)
- **Cubre:** SLI, SLO, SLA, Error Budgets, Reliability engineering, Risk, Fault tolerance, Reliability patterns.
- **Nivel:** Intermedio-avanzado
- **Acceso:** Libre; cuenta Microsoft gratuita para guardar progreso
- **Por qué lo recomiendo:** El módulo de SRE es una introducción corta y bien traducida que sirve para repasar vocabulario antes de entrar en el Workbook. El pilar de confiabilidad de Well-Architected es lo mejor en español sobre análisis de modos de fallo y objetivos de confiabilidad aplicados a Azure, y es la referencia que usarás en la Parte H (FMEA) y en el Proyecto Final.

### Documentación de OpenTelemetry en español (repaso de señales para definir SLIs) — CNCF
- **URL:** https://opentelemetry.io/es/docs/concepts/components/
- **Autor / organización:** Proyecto OpenTelemetry (CNCF)
- **Idioma:** Español
- **Tipo:** Documentación oficial
- **Duración aproximada:** 30 min
- **Cubre:** Base para especificar dónde se mide cada SLI (servidor, cliente, balanceador, sondeo sintético).
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Un SLI mal especificado casi siempre nace de no tener claro en qué punto de la cadena se mide. Repasar los componentes y los puntos de instrumentación antes de la Parte B evita ese error.

## Recursos en inglés

### SRE Workbook: "Implementing SLOs", "SLO Engineering Case Studies", "Example SLO Document" y "Alerting on SLOs" — Google
- **URL:** https://sre.google/workbook/implementing-slos/ · https://sre.google/workbook/slo-engineering-case-studies/ · https://sre.google/workbook/slo-document/ · https://sre.google/workbook/alerting-on-slos/ · Índice completo: https://sre.google/workbook/table-of-contents/
- **Autor / organización:** Google SRE
- **Idioma:** Inglés
- **Tipo:** Libro online gratuito (capítulos)
- **Duración aproximada:** 5-6 h de lectura atenta
- **Cubre:** SLI, SLO, SLA, Error Budgets (política y documento de SLO), alertas de burn rate.
- **Nivel:** Avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** "Implementing SLOs" es el capítulo central del curso: cómo elegir SLIs, cómo especificarlos, cómo usar datos históricos para fijar objetivos, cómo escribir la política de error budget. El documento de SLO de ejemplo es una plantilla real que adaptarás. Los casos de Evernote y Home Depot muestran cómo se hace en empresas que no son Google. Del índice, lee también "Eliminating Toil" y "Managing Load" para las Partes E y F.

### SRE Book: capítulos sobre riesgo, SLOs, toil, capacidad y fallos en cascada — Google
- **URL:** Índice: https://sre.google/sre-book/table-of-contents/ (lee "Embracing Risk", "Service Level Objectives", "Eliminating Toil", "Addressing Cascading Failures" y "Handling Overload") · Introducción: https://sre.google/sre-book/introduction/ · Recuperación de sobrecarga operativa: https://sre.google/sre-book/operational-overload/
- **Autor / organización:** Google SRE
- **Idioma:** Inglés
- **Tipo:** Libro online gratuito (capítulos)
- **Duración aproximada:** 5-6 h
- **Cubre:** Error Budgets, Risk, Toil reduction, Capacity planning, Fault tolerance, Graceful degradation, Reliability patterns, Engineering for failure.
- **Nivel:** Avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** "Addressing Cascading Failures" y "Handling Overload" son los dos capítulos que explican por qué los reintentos ingenuos tumban sistemas y qué son load shedding, degradación y límites de reintento: la Parte G implementa sus recomendaciones. "Embracing Risk" es la justificación económica de todo el curso: la fiabilidad tiene un coste y el objetivo no es el 100 %.

### Prometheus: reglas de grabación y de alerta — Prometheus Authors
- **URL:** https://prometheus.io/docs/prometheus/latest/configuration/alerting_rules/ · Funciones PromQL: https://prometheus.io/docs/prometheus/latest/querying/functions/ · Ejemplos: https://prometheus.io/docs/prometheus/latest/querying/examples/
- **Autor / organización:** Proyecto Prometheus (CNCF)
- **Idioma:** Inglés
- **Tipo:** Documentación oficial
- **Duración aproximada:** 1 h de consulta
- **Cubre:** Implementación de SLIs como reglas de grabación y alertas de burn rate.
- **Nivel:** Intermedio-avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** Los SLIs viven como reglas de grabación; esta es la referencia para escribirlas bien (nombres `nivel:metrica:operacion`, intervalos de evaluación). Ya la usaste en el curso anterior; aquí la exprimes.

### Azure Monitor OpenTelemetry y KQL para SLIs — Microsoft Learn
- **URL:** https://learn.microsoft.com/en-us/azure/azure-monitor/app/opentelemetry-enable (en español cambiando `en-us` por `es-es`)
- **Autor / organización:** Microsoft
- **Idioma:** Inglés y español
- **Tipo:** Documentación oficial
- **Duración aproximada:** 45 min
- **Cubre:** Medición de los mismos SLIs en Application Insights (tablas `requests` y `dependencies`) para compararlos con Prometheus.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Un SLI debe dar el mismo número se mida donde se mida. Definir cada SLI en PromQL y en KQL y comparar los resultados es el ejercicio que más errores de especificación destapa.

### Grafana Learn (GROT Academy) y documentación de k6 — Grafana Labs
- **URL:** https://learn.grafana.com/ (rutas gratuitas de Grafana; la documentación de k6 se enlaza desde el menú "Docs" de grafana.com)
- **Autor / organización:** Grafana Labs
- **Idioma:** Inglés
- **Tipo:** Rutas de aprendizaje y documentación de herramienta
- **Duración aproximada:** 1-2 h para lo que necesitas de k6 (script básico, `stages`, `thresholds`, salida de percentiles)
- **Cubre:** Capacity planning, Performance (pruebas de carga y percentiles).
- **Nivel:** Intermedio
- **Acceso:** Libre; el binario de k6 es open source y no necesita cuenta de Grafana Cloud
- **Por qué lo recomiendo:** k6 es la herramienta de carga más usada en equipos SRE y sus `thresholds` te permiten escribir el SLO como criterio de paso o fallo de la prueba. Si prefieres algo más simple, `hey` (una sola línea de comando) es suficiente para la Parte F.

## Documentación oficial

- **SRE Workbook, índice:** https://sre.google/workbook/table-of-contents/ · **SRE Book, índice:** https://sre.google/sre-book/table-of-contents/ · Actualizaciones de ambos libros: https://sre.google/resources/book-update/
- **Documento de SLO de ejemplo (plantilla de referencia):** https://sre.google/workbook/slo-document/
- **Prometheus, reglas de alerta y grabación:** https://prometheus.io/docs/prometheus/latest/configuration/alerting_rules/
- **Application Insights con OpenTelemetry:** https://learn.microsoft.com/en-us/azure/azure-monitor/app/opentelemetry-enable
- **Librerías Python que usarás** (busca cada una en PyPI y lee su README antes de instalarla): `tenacity` (reintentos con backoff y jitter), `pybreaker` (circuit breaker), `httpx` o `requests` (timeouts), `psycopg` (PostgreSQL).
- **Herramientas de carga:** `k6` (Grafana Labs) o `hey` (herramienta de línea de comandos en Go). Ambas se instalan desde su repositorio oficial de GitHub o desde el gestor de paquetes de tu sistema.

## Ruta recomendada de estudio

1. **Hacer** el módulo de introducción a SRE de Microsoft Learn en español (1 h) como repaso de vocabulario.
2. **Leer** "Embracing Risk" y "Service Level Objectives" del SRE Book (2 h). Anota la frase que resume por qué el 100 % es el objetivo equivocado.
3. **Leer** "Implementing SLOs" del Workbook completo (2 h) y después el documento de SLO de ejemplo (30 min). Compara la estructura del documento con la plantilla de este README.
4. **Hacer las Partes A, B y C del laboratorio** (8-10 h). No fijes ningún objetivo sin haber mirado antes los datos.
5. **Releer** "Alerting on SLOs" (1 h) y **hacer la Parte D**.
6. **Leer** "Eliminating Toil" en el SRE Book y en el Workbook (1,5 h) y **hacer la Parte E**.
7. **Leer** "Managing Load" del Workbook y las páginas de k6 o hey que necesites (1,5 h). **Hacer la Parte F.**
8. **Leer** "Addressing Cascading Failures" y "Handling Overload" del SRE Book (2 h). Son densos: haz un esquema de los mecanismos que describen. **Hacer la Parte G.**
9. **Leer** las páginas de análisis de modos de fallo del pilar de confiabilidad de Well-Architected (1 h). **Hacer las Partes H e I.**
10. **Hacer la Parte J** (caos), en una sesión seguida y con la ficha escrita antes de ejecutar nada. **Limpieza.**
11. **Responder la evaluación** y **revisar el checklist**.

Si vas justo de tiempo: los puntos 3, 4, 5, 8 y 10 son obligatorios.

## Laboratorio

### Objetivo

Definir e implementar el modelo de confiabilidad completo del servicio `pedidos` (la aplicación del curso de Docker con `api`, `inventario`, una base de datos PostgreSQL y un proveedor externo simulado): SLIs medibles, SLOs justificados con datos, SLA interno, política de error budget con alertas de burn rate, plan de reducción de toil con una automatización real, capacity planning con prueba de carga, tolerancia a fallos y degradación implementadas en código, análisis de riesgo y un experimento de caos documentado.

### Requisitos

- Repositorio del curso 7 con `api`, `inventario`, Collector, Prometheus, Grafana, Alertmanager.
- `kind` para la Parte J (o `minikube`/`k3s`); manifiestos o chart de Helm de la aplicación de los cursos 1 y 2 de este módulo.
- `k6` o `hey`; Python con `tenacity`, `pybreaker`, `psycopg`.
- Documenta en `laboratorio-sre.md`. Los documentos de confiabilidad van en `confiabilidad/`.

> **Sobre el coste.** Todo corre en local. Si mantienes Application Insights del curso anterior, vigila la ingesta durante las pruebas de carga (el muestreo del Collector debe estar activo) y bórralo al terminar si no lo vas a usar en el curso 9. Coste esperado: cero.

### Instrucciones

**Parte A — El servicio y sus dependencias (2 h)**

1. Añade a Compose un contenedor `postgres` (imagen oficial, `mem_limit` 256 MB) y haz que `api` guarde cada pedido en una tabla `pedidos` y lea de ella en `GET /pedido/<id>`. Añade un tercer servicio `proveedor` (Python, 30 líneas) que simule un servicio externo de precios con `GET /precio/<id>`, con `LATENCIA_MS`, `TASA_ERROR` y un modo `CAIDO=1` que rechace conexiones. `api` lo llama en cada pedido.
2. Dibuja el **diagrama de dependencias** (Mermaid o imagen): usuario → `api` → {`inventario`, `postgres`, `proveedor`}. Marca cada dependencia como **crítica** (sin ella no hay respuesta correcta) o **degradable** (sin ella se puede responder algo útil). Justifica: el precio del proveedor puede sustituirse por el último conocido; el stock no.
3. Verifica que la instrumentación del curso 7 cubre las nuevas llamadas (spans de `psycopg` y de `requests` al proveedor). Si no, añade la instrumentation library correspondiente.

**Parte B — Especificación de SLIs (3 h)**

4. Escribe en `confiabilidad/sli-*.md`, uno por SLI, usando la **plantilla de especificación de SLI** de más abajo, cuatro SLIs del servicio `pedidos`:
   - **Disponibilidad**: proporción de peticiones a `/pedido/*` con respuesta distinta de 5xx, medida en el servidor `api`.
   - **Latencia**: proporción de peticiones correctas a `/pedido/*` servidas en menos de 300 ms.
   - **Corrección**: proporción de pedidos leídos cuyo contenido coincide con lo escrito (implementa un **sondeo sintético**: un script cada minuto crea un pedido, lo lee y compara; publica una métrica `sonda_correccion_total{resultado}`).
   - **Frescura**: proporción de respuestas de precio con antigüedad menor de 5 minutos (añade al `api` la marca de tiempo del precio y una métrica de antigüedad).
5. Para cada SLI escribe la **consulta exacta** en PromQL (regla de grabación `sli:disponibilidad:ratio_rate5m`, etc.) y la equivalente en KQL sobre `requests`/`dependencies`/`customMetrics`. Ejecuta ambas sobre el mismo intervalo y compara los valores: documenta las diferencias y de dónde salen (muestreo, punto de medición, redondeo de bins).
6. Discute por escrito dos decisiones de especificación: ¿cuenta un 404 como error? ¿cuenta una petición que tarda 10 s pero devuelve 200 como "disponible"? No hay respuesta única; lo que se evalúa es que la justifiques desde el punto de vista del usuario.

**Parte C — Datos históricos, SLOs y SLA interno (3-4 h)**

7. Genera tráfico realista durante al menos **24 horas** con un generador en segundo plano de baja intensidad (2-5 peticiones/s, con variación horaria si puedes) y con fallos "naturales" pequeños programados (`TASA_ERROR=0.002` en `proveedor`, picos de `LATENCIA_MS` ocasionales mediante un cron). Si no puedes tener el equipo encendido 24 h, haz 4 sesiones de 2-3 h en días distintos y anótalo.
8. Analiza los datos: para cada SLI calcula el valor conseguido en ventanas de 1 h, 6 h y en el total. Usa PromQL (`avg_over_time`, `quantile_over_time`) o exporta a CSV y analiza con Python. Representa en Grafana la distribución.
9. Escribe `confiabilidad/slo-pedidos.md` con la **plantilla de documento de SLO**: para cada SLI un objetivo y una ventana **justificados por los datos** (regla práctica del Workbook: el objetivo debe ser un poco más exigente que lo que ya consigues sin esfuerzo, no un deseo) y un párrafo de "por qué no un nueve más" con su coste estimado. Ventana recomendada: 28 o 30 días móviles; justifica si eliges otra.
10. Define un **SLA interno** (lo que el equipo de plataforma promete al equipo de producto) más laxo que el SLO y explica la relación: el SLO es la alarma interna, el SLA la promesa con consecuencias. Indica qué consecuencia tendría incumplirlo en tu empresa ficticia.

**Parte D — Error budget, política y alertas (2-3 h)**

11. Calcula el error budget de cada SLO en minutos de indisponibilidad total y en número de peticiones fallidas para tu tráfico medido. Crea un panel en Grafana "Presupuesto de error restante (30 d)" con la fórmula `1 - (1 - sli_30d) / (1 - objetivo)`.
12. Escribe `confiabilidad/politica-error-budget.md` con la **plantilla de política de error budget**: quién la aprueba, umbrales (por ejemplo, con menos del 50 % restante se prioriza fiabilidad en la planificación; agotado, se congelan despliegues de funcionalidad salvo correcciones), excepciones, cómo se levanta la congelación y qué pasa con los incidentes por causas externas.
13. Revisa las alertas de burn rate del curso 7 para que apunten a los SLOs reales de este curso (objetivo, ventana y nombres de regla). Comprueba con `TASA_ERROR` que las alertas se disparan cuando toca y anota los tiempos. Añade una alerta de **presupuesto casi agotado** (menos del 20 % restante) de severidad `ticket`.

**Parte E — Toil: inventario y automatización (3 h)**

14. Haz un **inventario del toil** de tu propia ruta: lista todas las tareas manuales, repetitivas y sin valor duradero que has hecho desde el Módulo Intermedio (crear y borrar grupos de recursos, regenerar `.env`, reiniciar contenedores, comprobar costes, rotar cadenas de conexión, actualizar dashboards a mano, lanzar carga...). Para cada una: frecuencia, minutos por vez, si es automatizable, riesgo de hacerla mal. Calcula horas al mes.
15. Elige la de mayor coste × automatizabilidad y **automatízala de verdad** en `automatizacion/`: un script Python o Bash idempotente, con manejo de errores, salida clara y un `README` de uso. Ejemplos válidos: crear y destruir el entorno de laboratorio de Azure con comprobación de coste; un comprobador que valida que todas las alertas tienen `runbook_url` y que las URLs responden; un generador de informe semanal de SLO en Markdown a partir de Prometheus. Mide el tiempo antes y después.
16. Escribe un **plan de reducción de toil** para las tres siguientes tareas, con esfuerzo estimado y retorno en horas al mes.

**Parte F — Capacity planning y performance (3 h)**

17. Escribe un script de k6 (o una serie de ejecuciones de `hey`) que aumente la carga por escalones (10, 25, 50, 100, 200 usuarios virtuales, 2 minutos cada uno) contra `/pedido/<id>`. Con `thresholds` de k6 codifica tu SLO de latencia (p95 < 300 ms) y de errores (< 0,5 %).
18. Ejecuta y encuentra el **punto de saturación**: el escalón en el que el p95 se dispara o los errores superan el umbral. Captura la curva de latencia frente a carga en Grafana y localiza con métricas USE qué recurso saturó primero (CPU de `api`, conexiones de `postgres`, hilos del servidor). Repite con el doble de CPU asignada al contenedor o dos réplicas de `api` tras un balanceador (Compose `deploy.replicas` con nginx, o el clúster `kind`) y compara.
19. Analiza **tail latency**: representa p50, p95, p99 y p99,9 en el escalón anterior a saturación. Explica por qué la mediana engaña y qué peticiones caen en la cola (busca dos o tres trazas de la cola en Tempo y di qué las hizo lentas).
20. **Modelo de crecimiento**: supón que el tráfico crece un 8 % mensual desde tu carga actual de referencia. Calcula en qué mes alcanzas el 70 % del punto de saturación (tu umbral de ampliación) y qué acción de capacidad propondrías con antelación. Preséntalo en una tabla de 12 meses.

**Parte G — Graceful degradation y fault tolerance (4 h)**

21. Implementa en `api`, medible con telemetría antes y después:
    - **Timeouts** explícitos en todas las llamadas salientes (`inventario`, `proveedor`, `postgres`). Justifica cada valor a partir de los percentiles medidos.
    - **Reintentos con backoff exponencial y jitter** con `tenacity` solo para `proveedor` y solo en errores transitorios (conexión, 503), con un máximo de 2 reintentos y **presupuesto de reintentos** (no más del 10 % de peticiones adicionales). Explica por qué reintentar en `inventario` con `TASA_ERROR` alta sería peor.
    - **Circuit breaker** con `pybreaker` alrededor de `proveedor`: se abre tras 5 fallos, medio abierto a los 30 s. Publica el estado del breaker como métrica.
    - **Feature flag** `DEGRADAR_PRECIOS` (variable de entorno o archivo recargable) que, activo o con el breaker abierto, devuelve el último precio conocido de una cache local con una cabecera `X-Degradado: precios-cacheados` y sigue respondiendo 200.
22. Demuestra cada mecanismo con un experimento: `CAIDO=1` en `proveedor` con y sin breaker (compara latencia p99 y ratio de errores en Grafana); `TASA_ERROR=0.3` con y sin reintentos (compara tráfico recibido por `proveedor`: los reintentos lo multiplican). Captura las gráficas.
23. Documenta en `confiabilidad/patrones.md` qué **patrones de confiabilidad** has aplicado y cuáles no y por qué: bulkhead, circuit breaker, retry con backoff, timeout, cache de respaldo, load shedding, cola de trabajo, idempotencia. Para cada uno, una frase sobre en qué parte del sistema encajaría.

**Parte H — Análisis de riesgo (2 h)**

24. Construye la **matriz de riesgos** del servicio: al menos 10 riesgos (caída de `postgres`, latencia del proveedor, agotamiento de conexiones, despliegue roto, expiración de certificado, saturación por tráfico, error humano en configuración, caída de zona de Azure...), con probabilidad (1-5), impacto (1-5), puntuación, detección actual (alerta, dashboard, nada) y mitigación existente o propuesta.
25. Haz un **FMEA simplificado** para los tres componentes críticos: modo de fallo, efecto en el usuario, causa, controles de detección, controles de recuperación, gravedad, y acción recomendada. Cruza el resultado con tus SLIs: ¿hay algún modo de fallo que ninguno de tus SLIs detectaría? Si lo hay, ese es tu quinto SLI candidato.

**Parte I — Ficha del experimento de caos (1 h)**

26. Despliega la aplicación (con `postgres` y `proveedor`) en `kind` con los manifiestos o el chart de los cursos 1 y 2. Comprueba que el Collector recibe telemetría también desde el clúster (puedes correr el Collector como Deployment y apuntar Prometheus al clúster, o exponer por `port-forward`; documenta la decisión).
27. Rellena la **ficha de experimento de caos** de más abajo para tres experimentos **antes** de ejecutarlos: (1) matar el pod de `api` con carga activa; (2) cortar la red entre `api` y `postgres` (NetworkPolicy que deniegue el tráfico, o escalar `postgres` a 0); (3) saturar la CPU de `api` con un contenedor `stress` en el mismo pod o bajando el límite de CPU. La hipótesis debe ser cuantitativa ("el SLI de disponibilidad bajará como mucho al 99 % durante 30 s y volverá al 100 % sin intervención").

**Parte J — Ejecución del caos y cierre (2-3 h)**

28. Ejecuta los tres experimentos con carga activa y el dashboard abierto, uno a uno, respetando el criterio de aborto. Registra para cada uno: métricas antes, durante y después; si la hipótesis se cumplió; qué mecanismo de la Parte G actuó; qué no funcionó como esperabas.
29. Escribe las conclusiones: qué cambios harías en la aplicación, en los manifiestos (réplicas, `PodDisruptionBudget`, probes, límites), en las alertas o en los SLOs. Aplica al menos uno y repite el experimento afectado.
30. Limpieza: `kind delete cluster`, `docker compose down -v`. Si borras Application Insights, `az group delete --name rg-lab-obs --yes`. Si lo conservas para el curso 9, comprueba su ingesta y anótalo.

### Plantillas

Copia estas plantillas a `confiabilidad/` y rellénalas con tus datos.

**Especificación de SLI**

```markdown
# SLI: <nombre>
- Servicio / interfaz: <api /pedido/*>
- Tipo: <disponibilidad | latencia | corrección | frescura | throughput>
- Evento válido: <qué peticiones cuentan; exclusiones justificadas (p. ej. /health, 4xx)>
- Evento bueno: <condición exacta, p. ej. status != 5xx y duración < 300 ms>
- Punto de medición: <servidor api | balanceador | cliente | sondeo sintético> y por qué
- Fórmula: buenos / válidos
- Consulta PromQL: <regla de grabación completa>
- Consulta KQL: <consulta completa>
- Limitaciones conocidas: <muestreo, eventos no observados, sesgos>
- Propietario y fecha de revisión:
```

**Documento de SLO**

```markdown
# SLO del servicio <nombre>
## Contexto: quiénes son los usuarios, qué hace el servicio, dependencias críticas y degradables
## SLIs y objetivos
| SLI | Objetivo | Ventana | Valor histórico (28 d) | Justificación |
## Por qué no un objetivo más alto: coste técnico y organizativo del siguiente nueve
## Relación con el SLA interno: <promesa, medición, consecuencias>
## Exclusiones: <mantenimientos anunciados, fallos del proveedor cloud, abuso>
## Presupuesto de error resultante: <minutos y peticiones por ventana>
## Revisión: <cada cuánto, quién, qué datos>
```

**Política de error budget**

```markdown
# Política de error budget de <servicio>
- Propietarios y aprobadores:
- SLOs a los que aplica:
- Estados y acciones:
  - Presupuesto > 50 %: <cadencia normal de despliegues, experimentos permitidos>
  - 20-50 %: <prioridad a fiabilidad en la planificación, revisión semanal>
  - < 20 %: <alerta ticket, solo cambios de bajo riesgo>
  - Agotado: <congelación de funcionalidad hasta recuperar X %, postmortem obligatorio>
- Excepciones y quién puede concederlas:
- Cómo se levanta una congelación:
- Incidentes por causa externa: <cuentan o no, y por qué>
- Historial de decisiones:
```

**Ficha de experimento de caos**

```markdown
# Experimento: <nombre>
- Fecha, responsable, observadores:
- Estado estable (métricas de referencia y valores actuales):
- Hipótesis (cuantitativa):
- Método de inyección (comandos exactos):
- Radio de impacto (qué se puede ver afectado y qué no debe verse afectado):
- Criterio de aborto y procedimiento de vuelta atrás:
- Duración prevista:
- Resultado observado (métricas durante y después, capturas):
- ¿Hipótesis confirmada? Aprendizajes:
- Acciones derivadas (con responsable y fecha):
```

### Resultado esperado

- `confiabilidad/` con cuatro especificaciones de SLI, `slo-pedidos.md`, `politica-error-budget.md`, `patrones.md`, `riesgos.md` (matriz y FMEA) y tres fichas de caos completadas.
- Código de `api` con timeouts, reintentos, breaker y feature flag; `proveedor/` y `sonda/`; script de carga; `automatizacion/` con la tarea automatizada.
- Reglas de Prometheus actualizadas, panel de error budget y capturas de las pruebas de carga y de los experimentos.
- `laboratorio-sre.md` con el análisis de datos, la tabla de capacidad y las conclusiones.

### Criterios de validación

- [ ] Parte A: el diagrama distingue dependencias críticas y degradables con justificación; las nuevas llamadas aparecen en las trazas.
- [ ] Parte B: cada SLI tiene evento válido, evento bueno, punto de medición y consultas PromQL y KQL que devuelven valores coherentes; las decisiones de especificación están argumentadas desde el usuario.
- [ ] Parte C: los objetivos se derivan de datos reales (capturas y cálculo), la ventana está justificada y el SLA interno es más laxo que el SLO con relación explicada.
- [ ] Parte D: el error budget está calculado en minutos y peticiones, la política define acciones por umbral y las alertas de burn rate se han probado sobre los SLOs reales.
- [ ] Parte E: el inventario de toil tiene tiempos medidos, la automatización funciona, es idempotente y ahorra tiempo demostrable.
- [ ] Parte F: se ha encontrado el punto de saturación con evidencia de qué recurso saturó, se han analizado los percentiles y la tabla de crecimiento es correcta.
- [ ] Parte G: cada mecanismo tiene su experimento con gráficas de antes y después; el breaker y el flag mantienen el servicio respondiendo 200 degradado con el proveedor caído.
- [ ] Partes H e I: la matriz tiene al menos 10 riesgos puntuados; el FMEA cruza modos de fallo con SLIs; las hipótesis de caos son cuantitativas y anteriores a la ejecución.
- [ ] Parte J: los tres experimentos están documentados con métricas y al menos una acción derivada está implementada y comprobada.
- [ ] El estudiante puede defender ante el mentor, en 10 minutos y sin leer, por qué eligió cada objetivo de SLO y qué haría el primer día con el presupuesto agotado.

## Entrega

En tu repositorio de entregas, carpeta `03-modulo-avanzado/08-sre-avanzado/`:

1. `confiabilidad/` completa (SLIs, SLO, política, patrones, riesgos, fichas de caos).
2. Código: `api/`, `inventario/`, `proveedor/`, `sonda/`, `carga/` (script k6 o comandos hey), `automatizacion/`, `docker-compose.yml`, `config/`, manifiestos o chart para `kind`.
3. `laboratorio-sre.md` y `capturas/` (con usuario o nombre de máquina visibles).
4. `ENTREGA.md` con evaluación, checklist y uso de IA.

Nota sobre IA: pide a la IA que critique tus SLOs ("¿qué usuario se quejaría con este objetivo?") o que revise tu política, no que la redacte. En la revisión se te pedirá reproducir el cálculo del error budget y explicar el código del breaker línea por línea.

## Evaluación

1. **Conceptual.** Explica la diferencia entre SLI, SLO y SLA con el servicio `pedidos`. ¿Por qué el SLO debe ser más estricto que el SLA?
2. **Técnica.** Especifica el SLI de latencia de `/pedido/*`: evento válido, evento bueno, punto de medición y consulta PromQL. ¿Por qué excluir las peticiones fallidas del SLI de latencia?
3. **Situacional.** El equipo de producto pide un SLO de disponibilidad del 99,99 %. Tus datos de 28 días muestran un 99,7 % sin ningún incidente grave. Argumenta con números y con el diagrama de dependencias qué respuesta das y qué haría falta para llegar.
4. **Técnica.** Con un SLO del 99,5 % en 30 días y 3 peticiones/s de media, calcula el error budget en minutos de caída total y en peticiones fallidas. Si ayer hubo una caída de 40 minutos, ¿qué porcentaje del presupuesto queda?
5. **Situacional.** El presupuesto de error se agotó el día 12 por un fallo del proveedor externo. Según tu política, ¿se congelan los despliegues? Defiende tu decisión y explica qué cambia si la causa hubiera sido un despliegue propio.
6. **Conceptual.** Define toil con los criterios del SRE Book y da dos ejemplos de tu inventario que lo son y uno que parece toil pero no lo es. ¿Por qué Google limita el toil al 50 % del tiempo?
7. **Técnica.** En tu prueba de carga, el p95 se mantiene plano hasta 100 usuarios y salta de 250 ms a 2 s en 150. ¿Qué te dice eso sobre el sistema? ¿Qué métricas USE mirarías para saber qué saturó y qué dos acciones de capacidad propondrías?
8. **Conceptual.** ¿Por qué los reintentos sin backoff ni jitter pueden convertir un fallo parcial en una caída total? Explica el mecanismo de fallo en cascada y qué tres controles lo frenan.
9. **Técnica.** Describe los tres estados de un circuit breaker y qué pasa con la petición del usuario en cada uno en tu implementación. ¿Qué métrica publicaste para saber en qué estado está?
10. **Situacional.** `proveedor` está caído desde hace 10 minutos. Con el feature flag `DEGRADAR_PRECIOS` la API responde 200 con precios de hace 15 minutos. ¿Es una respuesta "buena" para tu SLI de disponibilidad? ¿Y para el de frescura? ¿Qué le dirías al equipo de negocio?
11. **Conceptual.** Explica bulkhead, load shedding e idempotencia y di en qué punto del servicio `pedidos` aplicaría cada uno.
12. **Técnica.** Tu FMEA detecta que la expiración del certificado TLS no la detecta ningún SLI ni alerta. Propón el SLI o la alerta, dónde se mide y con qué antelación debe avisar.
13. **Situacional.** Antes de un experimento de caos, el mentor te pregunta el radio de impacto y el criterio de aborto. Escribe ambos para "cortar la red a postgres" y explica por qué un experimento sin hipótesis previa no es ingeniería.
14. **Troubleshooting.** Tras matar el pod de `api` en `kind`, la disponibilidad cayó al 0 % durante 25 segundos en vez de los 3 esperados. Nombra tres causas posibles relacionadas con réplicas, probes y `terminationGracePeriodSeconds`, y cómo comprobarías cada una.
15. **Reflexión.** ¿Qué documento de `confiabilidad/` te costó más escribir y por qué? ¿Qué decisión tomaste con datos que antes habrías tomado por intuición?

## Checklist final

Antes de continuar, deberías poder:

- [ ] Especificar un SLI con evento válido, evento bueno, punto de medición y consulta exacta en PromQL y KQL.
- [ ] Fijar un SLO y su ventana a partir de datos históricos y explicar por qué no un nueve más.
- [ ] Distinguir SLO, SLA interno y objetivo, y explicar sus consecuencias.
- [ ] Calcular un error budget y aplicar una política escrita cuando se consume.
- [ ] Implementar y calibrar alertas de burn rate sobre SLOs reales.
- [ ] Inventariar toil, priorizarlo y automatizar una tarea de forma idempotente.
- [ ] Encontrar el punto de saturación de un servicio con k6 o hey y proyectar capacidad a 12 meses.
- [ ] Interpretar p50/p95/p99/p99,9 y explicar tail latency con trazas.
- [ ] Implementar timeouts, reintentos con backoff y jitter, circuit breaker y feature flag de degradación en Python y medir su efecto.
- [ ] Construir una matriz de riesgos y un FMEA simplificado y cruzarlos con los SLIs.
- [ ] Diseñar y ejecutar un experimento de caos con hipótesis, radio de impacto y criterio de aborto.
- [ ] Tener el servicio `pedidos` con `postgres` y `proveedor` listo para las simulaciones de Incident Management.

---

*Recursos verificados el 2026-09-27 mediante búsqueda web (existencia y vigencia de las URLs). Si un enlace falla, abre un issue en este repositorio.*
