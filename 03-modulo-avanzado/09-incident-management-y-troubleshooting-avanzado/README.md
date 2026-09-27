# Incident Management y Troubleshooting Avanzado

> Módulo: Avanzado · Curso 9 de 12 · Duración estimada: 30-40 horas · Estado: ✅ Completo

## Objetivo

Todo lo que has construido en los dos cursos anteriores (telemetría, SLOs, alertas de burn rate, tolerancia a fallos) existe para un momento concreto: cuando algo se rompe en producción y hay que decidir, con información incompleta y presión, qué hacer en los próximos cinco minutos. Este curso trata de ese momento y de lo que viene después.

Vas a aprender a **gestionar** un incidente, no solo a resolverlo: declararlo con la severidad correcta, asumir el rol de Incident Commander, abrir un war room, mantener un timeline en tiempo real, comunicar a gente que no es técnica cada pocos minutos, escalar cuando toca y, sobre todo, **mitigar primero y arreglar después**. Después harás el análisis de causa raíz con método (5 porqués, diagrama de causa-efecto, reconstrucción del timeline desde logs y métricas) y escribirás un postmortem sin culpables con acciones correctivas que de verdad se puedan seguir. Ya escribiste un postmortem en el Módulo Intermedio; aquí lo harás sobre un incidente que has vivido de verdad, bajo el reloj.

La segunda mitad es **troubleshooting sistemático**: formular hipótesis, biseccionar, preguntar "qué cambió", y saber qué herramienta usar en cada capa (Linux, red, Kubernetes, Azure). En el laboratorio, un mentor o un compañero (o un script que eliges a ciegas) romperá tu sistema sin avisar de una de siete formas distintas, y tú tendrás que actuar como IC y como responder a la vez, dos veces, para medir si mejoras.

**Antes de empezar** necesitas el servicio `pedidos` del curso de SRE Avanzado (con `postgres` y `proveedor`), su telemetría y sus SLOs, y el clúster `kind` con la aplicación desplegada.

### Al terminar este curso deberías poder

- Clasificar un incidente con una matriz de severidades y explicar qué cambia en respuesta y comunicación en cada nivel.
- Actuar como Incident Commander: declarar, asignar roles, mantener el foco en la mitigación y cerrar el incidente.
- Abrir y mantener un war room y un timeline en tiempo real con marcas de tiempo y decisiones.
- Comunicar a stakeholders técnicos y no técnicos con plantillas, cadencia fija y una página de estado.
- Escalar según una matriz de escalado y explicar cuándo escalar es una obligación y no un fracaso.
- Distinguir mitigación de corrección, aplicar la primera bajo presión y planificar la segunda.
- Hacer un análisis de causa raíz con 5 porqués y diagrama de causa-efecto sin caer en la "causa única".
- Reconstruir un timeline a partir de logs, métricas y trazas y contrastarlo con el registrado en vivo.
- Escribir un postmortem sin culpables con acciones correctivas SMART y hacer su seguimiento.
- Aplicar un método de troubleshooting (hipótesis, bisección, qué cambió) con las herramientas adecuadas por capa en Linux, red, Kubernetes y Azure.

## Prerrequisitos

- Cursos 7 y 8 del Módulo Avanzado (Observabilidad Avanzada y SRE Avanzado) con su repositorio operativo.
- Módulo Intermedio: Administración de Linux, Networking Intermedio y Troubleshooting, Administración de Azure, Fundamentos de DevOps y SRE (postmortem).
- Módulo Avanzado: Kubernetes Avanzado (troubleshooting de pods y servicios), Networking Cloud Avanzado (NSG, DNS privado), Seguridad Cloud e IAM (certificados en Key Vault).
- Un mentor o compañero dispuesto a inyectar averías, o disciplina para usar el script ciego.
- VM `lab-so`, `kind`, Docker Compose y cuenta de Azure con presupuesto (solo para el escenario opcional de NSG).

## Temario

Incident severity · Incident Commander · War rooms · Escalation · Mitigation · Communication · Stakeholder management · Root Cause Analysis · Postmortems · Timeline reconstruction · Corrective actions · Troubleshooting sistemático.

**Práctica:** ejecutar una simulación completa de un incidente de producción.

## Recursos en español

### Microsoft Learn en español — Alertas de Azure Monitor, grupos de acciones, Service Health y respuesta a incidentes
- **URL:** https://learn.microsoft.com/es-es/azure/ (Supervisión > Azure Monitor > "Alertas" y "Grupos de acciones"; Azure Service Health; en Training, el módulo "Respuesta a incidentes" de la ruta "Mejora de la confiabilidad mediante prácticas de operaciones modernas")
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Documentación oficial y módulo de aprendizaje
- **Duración aproximada:** 2-3 h
- **Cubre:** Incident severity (niveles Sev0-Sev4 de las alertas de Azure), Communication (grupos de acciones, notificaciones), Escalation, Service Health como fuente de incidentes del proveedor.
- **Nivel:** Intermedio
- **Acceso:** Libre; cuenta Microsoft gratuita para guardar progreso
- **Por qué lo recomiendo:** Es el material en español más completo sobre cómo una alerta se convierte en una notificación a una persona (grupos de acciones, reglas de procesamiento, supresión) y sobre cómo Microsoft comunica sus propios incidentes en Service Health. El módulo de respuesta a incidentes cubre roles, comunicación y postmortem sin culpables en una hora, y es el único material de este curso que puedes leer entero en español.

### Documentación de Grafana Loki (consulta de logs para reconstruir timelines) — Grafana Labs
- **URL:** https://grafana.com/docs/loki/latest/ · Fuente de datos en Grafana: https://grafana.com/docs/grafana/latest/datasources/loki/
- **Autor / organización:** Grafana Labs
- **Idioma:** Inglés (se incluye aquí porque es la herramienta con la que reconstruirás los timelines en la Parte E; no hay equivalente en español)
- **Tipo:** Documentación oficial
- **Duración aproximada:** 1 h (LogQL: selectores, filtros, `line_format`, agregaciones por tiempo)
- **Cubre:** Timeline reconstruction, Root Cause Analysis.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Reconstruir un incidente exige buscar en logs por rango de tiempo, `trace_id` y servicio, y contar eventos por minuto. LogQL hace todo eso y lo aprendes en una hora si ya conoces PromQL.

## Recursos en inglés

### SRE Book: "Managing Incidents", "Emergency Response", "Postmortem Culture: Learning from Failure" y "Effective Troubleshooting" — Google
- **URL:** Índice: https://sre.google/sre-book/table-of-contents/ (los cuatro capítulos están en la parte III, "Practices")
- **Autor / organización:** Google SRE
- **Idioma:** Inglés
- **Tipo:** Libro online gratuito (capítulos)
- **Duración aproximada:** 4 h
- **Cubre:** Incident Commander, War rooms, Escalation, Mitigation, Communication, Postmortems, Corrective actions, Troubleshooting sistemático.
- **Nivel:** Avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** "Managing Incidents" describe el modelo de roles (IC, operaciones, comunicación, planificación) que este curso adopta y muestra el mismo incidente gestionado bien y mal. "Effective Troubleshooting" es el capítulo que convierte el troubleshooting en método (triaje, examen, diagnóstico, prueba, tratamiento) y advierte de los sesgos que más tiempo hacen perder. "Postmortem Culture" fija el estándar de postmortem sin culpables. Léelos antes del primer simulacro.

### SRE Workbook: "Incident Response", "Postmortem Culture" y "On-Call" — Google
- **URL:** Índice: https://sre.google/workbook/table-of-contents/ · On-Call: https://sre.google/workbook/on-call/ · Actualizaciones de los libros: https://sre.google/resources/book-update/
- **Autor / organización:** Google SRE
- **Idioma:** Inglés
- **Tipo:** Libro online gratuito (capítulos)
- **Duración aproximada:** 3 h
- **Cubre:** Incident severity, Incident Commander, Stakeholder management, Postmortems (con un ejemplo completo y su revisión), Escalation, carga de guardia.
- **Nivel:** Avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** "Incident Response" cuenta varios incidentes reales (incluido uno de PagerDuty, fuera de Google) con lo que salió bien y mal, y da una lista de prácticas concretas: declarar pronto, cadencia de comunicación, handoff. "Postmortem Culture" del Workbook incluye un postmortem de ejemplo con comentarios de por qué es bueno o malo, ideal para calibrar el tuyo.

### Prometheus Alerting overview y Alertmanager — Prometheus Authors
- **URL:** https://prometheus.io/docs/alerting/latest/overview/ · Alertmanager: https://prometheus.io/docs/alerting/latest/alertmanager/
- **Autor / organización:** Proyecto Prometheus (CNCF)
- **Idioma:** Inglés
- **Tipo:** Documentación oficial
- **Duración aproximada:** 45 min
- **Cubre:** El tramo alerta → notificación → responder: severidades como etiquetas, agrupación, silencios durante el incidente.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Durante un incidente, la gestión de las alertas (silenciar las derivadas, no la raíz; anotar el silencio con el identificador del incidente) es parte del trabajo del IC. Ya conoces la herramienta; aquí la usas bajo presión.

### Grafana Tempo y Loki: trazas y logs para el análisis posterior — Grafana Labs
- **URL:** https://grafana.com/docs/tempo/latest/ · https://grafana.com/docs/loki/latest/
- **Autor / organización:** Grafana Labs
- **Idioma:** Inglés
- **Tipo:** Documentación oficial
- **Duración aproximada:** 1 h de consulta
- **Cubre:** Timeline reconstruction, Root Cause Analysis.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** La reconstrucción del timeline de la Parte E se hace con búsquedas por rango temporal en Loki y trazas concretas en Tempo (la primera petición fallida, la última correcta). Ten a mano la sintaxis de búsqueda de ambos.

## Documentación oficial

- **SRE Book, índice:** https://sre.google/sre-book/table-of-contents/ · **SRE Workbook, índice:** https://sre.google/workbook/table-of-contents/
- **Microsoft Learn, Azure (español):** https://learn.microsoft.com/es-es/azure/ (Azure Monitor: alertas y grupos de acciones; Service Health; Azure Kubernetes Service: solución de problemas)
- **Prometheus Alertmanager:** https://prometheus.io/docs/alerting/latest/alertmanager/
- **Grafana Loki y Tempo:** https://grafana.com/docs/loki/latest/ · https://grafana.com/docs/tempo/latest/
- **Kubernetes, depuración de pods y servicios:** en kubernetes.io, sección "Tasks" > "Monitoring, Logging, and Debugging" (páginas "Debug Pods" y "Debug Services"), que ya usaste en Kubernetes Avanzado.
- **Páginas de manual en la VM:** `man ss`, `man dig`, `man journalctl`, `man openssl-x509`, `man df`, `man strace`.

## Ruta recomendada de estudio

1. **Leer** "Managing Incidents" y "Emergency Response" del SRE Book (1,5 h). Anota los tres errores del incidente mal gestionado y qué rol los habría evitado.
2. **Leer** "Incident Response" del Workbook (1 h). Fíjate en la cadencia de comunicación y en la regla de "declara pronto, degrada la severidad después".
3. **Hacer** el módulo de respuesta a incidentes de Microsoft Learn en español (1 h) y **leer** las páginas de alertas y grupos de acciones de Azure Monitor (1 h).
4. **Hacer la Parte A del laboratorio** (matrices, roles, plantillas, runbooks, escenarios). No hagas ningún simulacro sin esto preparado: gestionar un incidente sin plantillas es improvisar.
5. **Leer** "Effective Troubleshooting" del SRE Book (1 h) y **hacer la Parte B** (guía por capas ampliada y ensayo de herramientas).
6. **Hacer la Parte C**: primer simulacro completo, con mentor o compañero si es posible (2-3 h, cronometrado).
7. **Leer** "Postmortem Culture" en el SRE Book y en el Workbook, incluido el postmortem de ejemplo (2 h). **Hacer las Partes D y E** (RCA y reconstrucción) y **la Parte F** (postmortem).
8. **Hacer la Parte G**: segundo simulacro con otro escenario, y comparación de tiempos.
9. **Hacer la Parte H** (seguimiento de acciones y limpieza).
10. **Responder la evaluación** y **revisar el checklist**.

Si vas justo de tiempo: los puntos 1, 4, 6, 7 y 8 son obligatorios.

## Laboratorio

### Objetivo

Preparar el marco de gestión de incidentes del servicio `pedidos` (severidades, roles, escalado, plantillas, runbooks), ejecutar dos simulaciones completas de incidente de producción con avería inyectada a ciegas actuando como Incident Commander y responder, y cerrar cada una con RCA, reconstrucción del timeline y postmortem con acciones correctivas SMART y seguimiento.

### Requisitos

- Servicio `pedidos` del curso 8 desplegado en `kind` (con `postgres` y `proveedor`) y, para algunos escenarios, en la VM `lab-so` con Docker Compose. La telemetría (Prometheus, Grafana, Loki, Tempo, Alertmanager) operativa.
- Un mentor o compañero que ejecute la avería, o el script ciego `escenarios/aleatorio.sh` que escribirás en la Parte A.
- Un canal de war room: un chat (Teams, Discord, Slack gratuito) o, si estás solo, un documento vivo `war-room.md` con marcas de tiempo.
- Documenta en `laboratorio-incidentes.md`; cada incidente en su carpeta `incidentes/INC-<n>/`.

> **Sobre el coste.** Seis de los siete escenarios se ejecutan en local. El séptimo (NSG modificado) es opcional y requiere una VM B1s en Azure con la aplicación en Compose; una tarde cuesta céntimos si la desasignas al terminar, y debes borrar el grupo `rg-lab-inc` al acabar el curso. Si Application Insights sigue vivo del curso 7, vigila la ingesta.

### Matriz de severidades

| Sev | Impacto en usuarios | Ejemplos en `pedidos` | Respuesta | Comunicación |
|---|---|---|---|---|
| 1 | Servicio caído o datos corruptos para la mayoría de usuarios; SLO agotándose en horas | `/pedido` devuelve 5xx > 50 %; pedidos escritos con datos erróneos | IC inmediato, war room, todos los roles, 24x7 | Actualización cada 15 min, status page, dirección informada |
| 2 | Degradación grave para muchos usuarios o caída total de una función secundaria | p99 > 5 s; precios degradados por proveedor caído más de 30 min | IC, war room, roles según necesidad | Cada 30 min, status page |
| 3 | Degradación menor o impacto en pocos usuarios; sin riesgo inmediato de SLO | Errores intermitentes < 2 %; una réplica reiniciando | Responder de guardia, sin war room obligatorio | Al inicio y al cierre, canal del equipo |
| 4 | Sin impacto en usuarios; riesgo latente | Certificado que caduca en 7 días; disco al 80 % | Ticket, horario laboral | Ninguna externa |

Regla: si dudas entre dos severidades, declara la más alta y rebaja después. Subir de severidad tarde es lo que sale caro.

### Matriz de escalado

| Situación | Escalar a | Plazo |
|---|---|---|
| Sev 1 o 2 declarado | Responsable de guardia secundario y responsable del servicio | Inmediato |
| Sin hipótesis viable tras 30 min (Sev 1) o 60 min (Sev 2) | Especialista de la capa sospechosa (BD, red, plataforma) | Al cumplirse el plazo |
| Mitigación requiere cambio con riesgo (rollback de datos, cambio de red) | Responsable del servicio para aprobar | Antes de ejecutar |
| Posible causa en el proveedor cloud | Abrir caso de soporte y consultar Service Health | En cuanto se sospeche |
| Impacto en clientes con SLA o datos personales | Dirección técnica y legal/comunicación | Inmediato |

### Roles

- **Incident Commander (IC):** dirige, decide, asigna; no teclea en producción. Mantiene la severidad, el foco en mitigar y la cadencia de comunicación.
- **Operaciones (responder):** investiga y ejecuta cambios; informa al IC antes de cualquier acción con riesgo.
- **Comunicaciones:** redacta y envía las actualizaciones, mantiene la status page, filtra preguntas de stakeholders para que no lleguen al responder.
- **Escriba:** mantiene el timeline con marca de tiempo de cada hecho, hipótesis, decisión y acción; guarda enlaces a consultas y capturas.

En el laboratorio ejercerás los cuatro. Márcalo en el timeline: `[IC]`, `[OPS]`, `[COM]`, `[ESC]`. Esa etiqueta te obliga a cambiar de sombrero conscientemente.

### Instrucciones

**Parte A — Preparación del marco (3-4 h)**

1. Crea `marco/` con: `severidades.md` y `escalado.md` (adapta las matrices anteriores a tu empresa ficticia, con nombres de roles y contactos inventados), `roles.md`, y las cinco plantillas de la sección "Plantillas" como archivos separados.
2. Prepara una **status page** mínima: un `status.md` publicado en GitHub Pages de tu repositorio de entregas (o un archivo HTML estático servido por nginx en `lab-so`) con estados "Operativo", "Degradado", "Incidente" por componente. Lo actualizarás a mano durante el simulacro.
3. Revisa que cada alerta de los cursos 7 y 8 enlaza a un **runbook** con: síntoma, cómo confirmar, primeras comprobaciones por capa, mitigaciones conocidas, cuándo escalar. Añade un runbook genérico `runbooks/incidente-desconocido.md` con los primeros 10 minutos de cualquier incidente (confirmar impacto, declarar, revisar Service Health, revisar últimos cambios, abrir war room).
4. Escribe los **siete escenarios** en `escenarios/`, cada uno como script `NN-nombre.sh` idempotente con `--romper` y `--restaurar`, más un `aleatorio.sh` que elige uno al azar, lo ejecuta con `--romper`, guarda el nombre cifrado o en un archivo que no leerás (`echo "$n" > /tmp/.escenario`) y no imprime nada. Escenarios:
   - `01-disco-lleno`: en la VM donde corre Compose, `fallocate -l <casi todo el espacio libre> /var/lib/docker/relleno.img` (o en el volumen de `postgres`), de modo que la base de datos o los logs dejen de escribir.
   - `02-certificado-expirado`: pon nginx con TLS delante de `api` (si no lo tienes ya) y sustituye el certificado por uno autofirmado generado con fecha pasada (`faketime '2024-01-01 00:00:00' openssl req -x509 -newkey rsa:2048 -days 30 ...`) y recarga nginx.
   - `03-cambio-dns`: en `kind`, edita el ConfigMap de CoreDNS para que `postgres.<ns>.svc.cluster.local` resuelva a una IP inexistente (plugin `hosts` o `rewrite`); en Compose, cambia la variable `DB_HOST` a un nombre parecido pero incorrecto y recrea solo `api`.
   - `04-limite-conexiones-bd`: `ALTER SYSTEM SET max_connections = 5;` y reinicio de `postgres`, o un script Python que abre y mantiene 95 conexiones ociosas.
   - `05-despliegue-roto`: aplica un ConfigMap o `values.yaml` con `DB_PORT=5433` (o un timeout de 1 ms) y haz `rollout` de `api`. Debe pasar los probes de arranque y fallar en uso.
   - `06-fuga-memoria`: `FUGA_MEMORIA=1` en `inventario` con límite de memoria de 128 MB, para que entre en ciclo de OOMKilled.
   - `07-nsg-modificado` (opcional, Azure): con la app en una VM B1s en `rg-lab-inc`, añade una regla de denegación con prioridad 100 al NSG para el puerto de `api` o para el tráfico saliente hacia el puerto 5432 si `postgres` está en otra VM o en Azure Database. Restaurar borra la regla.
   Prueba cada script con `--romper` y `--restaurar` **ahora**, cuando no hay presión, y anota qué síntomas produce para ti mismo en un archivo `escenarios/SOLUCIONES.md` que **no abrirás** durante los simulacros (pídele al mentor que lo guarde él, o cífralo con `gpg -c`).

**Parte B — Método y guía de troubleshooting por capa (2-3 h)**

5. Copia la **guía de troubleshooting por capa** de más abajo a `marco/troubleshooting.md` y amplíala con al menos tres comandos por capa que hayas usado tú en cursos anteriores, con un ejemplo de salida "sana" de tu sistema (captúrala ahora: durante el incidente compararás contra ella).
6. Escribe con tus palabras el **método** en una página: (1) confirmar y acotar el síntoma (¿quién, desde cuándo, qué porcentaje?); (2) preguntar "qué cambió" (despliegues, configuración, certificados, cuotas, proveedor) mirando anotaciones de Grafana, historial de `kubectl rollout`, `git log` y el registro de actividad de Azure; (3) formular una hipótesis falsable y la prueba más barata que la descarta; (4) **biseccionar** por capa (cliente → borde → aplicación → dependencias → infraestructura) o por tiempo (última versión buena); (5) mitigar en cuanto haya una acción segura aunque no se conozca la causa; (6) anotar cada hipótesis descartada en el timeline para no repetirla.
7. Ensayo en frío: ejecuta `03-cambio-dns --romper` sabiendo lo que es y cronométrate siguiendo solo el método y la guía. Anota qué comando confirmó la causa. Restaura.

**Parte C — Simulacro 1: el incidente (2-3 h, cronometrado)**

8. Arranca carga estable (`hey` o k6 a baja intensidad) y abre Grafana, Alertmanager y el war room. Pide al mentor o compañero que ejecute un escenario sin decirte cuál, en un momento de los próximos 30 minutos; si estás solo, `bash escenarios/aleatorio.sh` y aparta la vista.
9. Cuando llegue la primera señal (alerta, dashboard, "queja" del generador de carga), **declara** el incidente con la plantilla de declaración: hora, severidad provisional, impacto observado, IC (tú), canal. Publica la primera actualización en la status page antes de investigar más de 5 minutos.
10. Trabaja con las cuatro etiquetas de rol en el timeline. Cada 15 minutos (Sev 1-2) publica una **actualización de estado** con la plantilla, aunque no haya novedades ("seguimos investigando; próxima actualización a las HH:MM"). Aplica la matriz de escalado: si a los 30 minutos no tienes hipótesis viable, "escala" (escríbelo en el timeline, y si tienes mentor, llámale de verdad).
11. **Mitiga primero**: rollback, reinicio, escalar réplicas, activar `DEGRADAR_PRECIOS`, redirigir tráfico, ampliar disco. Anota qué mitigación elegiste, por qué era segura y cuánto tardó en verse en el SLI. Solo después busca la causa y **arregla** (`--restaurar` equivale a la corrección definitiva, pero tú debes haber identificado qué hay que restaurar antes de ejecutarlo).
12. Declara el cierre cuando el SLI vuelva a su valor normal durante 10 minutos, publica la actualización final y anota la hora. Guarda: `incidentes/INC-1/declaracion.md`, `timeline.md`, `comunicaciones.md` (todas las actualizaciones), capturas de dashboards en el momento de detección y de recuperación.

**Parte D — Análisis de causa raíz (2 h)**

13. En `incidentes/INC-1/rca.md`, aplica **5 porqués** partiendo del síntoma hasta llegar a causas de proceso u organizativas, no solo técnicas (ejemplo: "el certificado caducó" → "nadie lo renovó" → "no había alerta de caducidad" → "el SLI/FMEA del curso 8 no cubría certificados" → "no revisamos el FMEA al añadir TLS"). Para cada porqué, la evidencia (log, métrica, comando).
14. Dibuja un **diagrama de causa-efecto** (Ishikawa, en Mermaid o a mano) con categorías: personas, proceso, herramientas, configuración, dependencias externas, entorno. Coloca factores contribuyentes, no una única causa. Escribe un párrafo sobre por qué "causa raíz" en singular es una simplificación y qué factores, de haber estado presentes, habrían evitado o acortado el incidente.

**Parte E — Reconstrucción del timeline (2 h)**

15. Sin mirar tu `timeline.md`, reconstruye el incidente **solo desde la telemetría**: en Loki, primer log de error y último log correcto por servicio; en Prometheus, el instante en que el SLI cruzó el umbral (`changes()`, `min_over_time`); en Alertmanager, cuándo disparó cada alerta y cuándo se resolvió; en Tempo, la primera traza fallida; anotaciones de despliegue; para el escenario 7, el registro de actividad de Azure. Escribe `timeline-reconstruido.md`.
16. Compara ambos timelines en una tabla: hora del hecho según telemetría, hora en que tú lo detectaste, hora en que lo anotaste. Calcula **tiempo de detección** (fallo → alerta), **tiempo de reconocimiento** (alerta → declaración), **tiempo de mitigación** y **tiempo de resolución**. Señala los hechos que no anotaste en vivo y los que anotaste con hora equivocada. Ese hueco es la razón por la que existe el rol de escriba.

**Parte F — Postmortem (2-3 h)**

17. Escribe `incidentes/INC-1/postmortem.md` con la plantilla, **sin culpables**: nada de "el operador olvidó" sino "el sistema permitía que se olvidara". Incluye impacto cuantificado con tus SLIs (minutos, peticiones fallidas, presupuesto de error consumido), detección, respuesta, lo que salió bien, lo que salió mal, dónde hubo suerte.
18. Define entre 3 y 6 **acciones correctivas SMART**: específicas, medibles, con responsable (aunque seas tú), realistas y con fecha. Clasifícalas: prevenir, detectar antes, mitigar más rápido, mejorar el proceso. Al menos una debe ser técnica y ejecutarse en este curso (por ejemplo, alerta de caducidad de certificado con 14 días de antelación; alerta de espacio en disco con predicción `predict_linear`; límite de conexiones en el pool de `api`). Regístralas como issues en tu repositorio de entregas con etiqueta `postmortem-INC-1`.
19. Sesión de revisión con el mentor (o autoevaluación con el postmortem de ejemplo del Workbook al lado): ¿está libre de culpa?, ¿las acciones atacan los porqués profundos o solo el síntoma?, ¿se entiende sin haber estado allí?

**Parte G — Simulacro 2 y comparación (3 h)**

20. Repite la Parte C con un escenario distinto (que el mentor lo garantice, o modifica `aleatorio.sh` para excluir el ya usado). Aplica lo aprendido: runbooks actualizados, la acción correctiva ya implementada, plantillas afinadas.
21. Haz RCA, reconstrucción y postmortem abreviados en `incidentes/INC-2/`. Compara en una tabla los cuatro tiempos de INC-1 e INC-2 y el número de hipótesis descartadas. Explica qué mejoró por el método y qué por conocer ya el sistema.

**Parte H — Seguimiento y limpieza (1 h)**

22. Revisa los issues de acciones correctivas: cierra los completados con enlace a la evidencia (commit, captura de la alerta nueva disparando), replanifica los demás con fecha y anota en `seguimiento.md` el porcentaje completado. Un postmortem sin seguimiento es un documento decorativo.
23. Restaura todos los escenarios (`--restaurar`), `kind delete cluster` si no lo necesitas, `docker compose down -v`, y en Azure `az group delete --name rg-lab-inc --yes --no-wait` si hiciste el escenario 7. Comprueba Cost Management al día siguiente.

### Guía de troubleshooting por capa

| Capa | Primeras preguntas | Herramientas |
|---|---|---|
| Linux (host o VM) | ¿CPU, memoria, disco, inodos, descriptores? ¿Qué proceso? ¿Qué cambió en el sistema? | `uptime`, `top`/`htop`, `free -h`, `df -h`, `df -i`, `dmesg -T \| tail`, `journalctl -p err --since "-1h"`, `ss -tulpn`, `lsof -p`, `strace -p`, `/proc/<pid>/status`, `systemctl status`, `last`, `apt list --installed` con fechas |
| Red y DNS | ¿Resuelve? ¿Llega? ¿Responde? ¿TLS válido? ¿Quién bloquea? | `dig +short`, `dig @<servidor>`, `getent hosts`, `ping`, `traceroute`/`mtr`, `nc -zv host puerto`, `curl -v --max-time 5`, `openssl s_client -connect host:443 -servername host \| openssl x509 -noout -dates`, `ss -s`, `iptables -L -n`/`nft list ruleset`, `tcpdump -i any port 5432 -c 20` |
| Contenedores y Kubernetes | ¿Pod Running y Ready? ¿Reinicios? ¿OOMKilled? ¿Eventos? ¿Endpoints del Service? ¿Qué cambió en el rollout? | `kubectl get pods -o wide`, `kubectl describe pod`, `kubectl logs --previous`, `kubectl get events --sort-by=.lastTimestamp`, `kubectl top pod`, `kubectl get endpoints`, `kubectl rollout history`, `kubectl diff`, `kubectl exec -- nslookup`, `kubectl debug`, `docker stats`, `docker inspect` |
| Aplicación y datos | ¿Qué dicen los SLIs? ¿Qué ruta falla? ¿Qué dependencia? ¿La base de datos acepta conexiones? | Dashboard RED, Tempo (primera traza fallida), Loki (`{service="api"} \|= "error"`), `psql -c "select count(*) from pg_stat_activity"`, `psql -c "show max_connections"`, logs de `postgres`, estado del circuit breaker |
| Azure | ¿Hay incidente del proveedor? ¿Qué cambió en la suscripción? ¿NSG, rutas, DNS privado, identidad, cuotas? | Service Health, Registro de actividad (`az monitor activity-log list --start-time`), `az network nsg rule list`, `az network watcher test-ip-flow`, `az network watcher test-connectivity`, `az vm boot-diagnostics get-boot-log`, métricas de plataforma en Azure Monitor, `az resource show` para comparar configuración |

Orden recomendado: confirmar síntoma en el SLI → Service Health y "qué cambió" → capa de aplicación (trazas) → dependencia señalada por la traza → capa de red o Kubernetes según el error → host. Biseccionar, no recorrer todo.

### Plantillas

**Declaración de incidente**

```markdown
# INC-<n> · <título corto en lenguaje de usuario>
- Declarado: <AAAA-MM-DD HH:MM zona> por <nombre> (IC)
- Severidad provisional: Sev <1-4> · Motivo:
- Impacto observado: <quién, qué función, desde cuándo, porcentaje o SLI>
- Canal / war room: <enlace>
- Roles: IC <>, Operaciones <>, Comunicaciones <>, Escriba <>
- Próxima actualización: <HH:MM>
```

**Actualización de estado**

```markdown
[<HH:MM>] INC-<n> · Sev <n> · Estado: <Investigando | Identificado | Mitigando | Monitorizando | Resuelto>
Impacto actual: <una frase sin jerga>
Qué sabemos: <hechos confirmados>
Qué hacemos: <acción en curso>
Próxima actualización: <HH:MM> (o "al cierre")
```

**Postmortem**

```markdown
# Postmortem INC-<n> · <título>
- Fecha del incidente / fecha del postmortem / autores / revisores / estado
## Resumen (3 líneas, para dirección)
## Impacto: usuarios afectados, duración, SLIs (minutos, peticiones fallidas, presupuesto de error consumido)
## Detección: cómo se detectó, tiempo hasta alerta, tiempo hasta declaración
## Respuesta: severidad, roles, escalados, mitigación aplicada y su efecto
## Timeline (reconstruido y contrastado con el registrado en vivo)
## Análisis de causas: 5 porqués y factores contribuyentes (diagrama)
## Qué salió bien / qué salió mal / dónde tuvimos suerte
## Acciones correctivas (SMART)
| # | Acción | Tipo (prevenir/detectar/mitigar/proceso) | Responsable | Fecha | Issue | Estado |
## Lecciones y preguntas abiertas
```

La matriz de severidad, la matriz de escalado y la ficha de roles están más arriba; cópialas a `marco/` y adáptalas.

### Resultado esperado

- `marco/` con severidades, escalado, roles, troubleshooting por capa, método y plantillas.
- `runbooks/` actualizados y `escenarios/` con siete scripts probados (más `SOLUCIONES.md` cifrado o en poder del mentor).
- `incidentes/INC-1/` e `incidentes/INC-2/` con declaración, timeline en vivo, comunicaciones, RCA, timeline reconstruido, postmortem y capturas.
- Issues de acciones correctivas con seguimiento y al menos una implementada y verificada.
- `laboratorio-incidentes.md` con la comparación de tiempos entre simulacros.

### Criterios de validación

- [ ] Parte A: las matrices están adaptadas y son coherentes entre sí; cada alerta tiene runbook; los siete scripts rompen y restauran de forma idempotente.
- [ ] Parte B: la guía por capa incluye comandos propios con salidas sanas de referencia; el método está escrito con palabras propias y el ensayo en frío está cronometrado.
- [ ] Parte C: la declaración se hizo en los primeros 5 minutos tras la primera señal; hay actualizaciones con la cadencia de la severidad; el timeline tiene etiquetas de rol; se mitigó antes de arreglar y se justificó la seguridad de la mitigación; la causa identificada coincide con el escenario.
- [ ] Parte D: los 5 porqués llegan a causas de proceso con evidencia por paso; el diagrama tiene factores en varias categorías.
- [ ] Parte E: el timeline reconstruido cita consultas concretas; los cuatro tiempos están calculados y las discrepancias con el timeline en vivo, comentadas.
- [ ] Parte F: el postmortem no atribuye culpa a personas, cuantifica el impacto con SLIs y tiene entre 3 y 6 acciones SMART registradas como issues, una implementada y probada.
- [ ] Parte G: el segundo simulacro usa un escenario distinto y la comparación de tiempos distingue mejoras por método y por familiaridad.
- [ ] Parte H: el seguimiento de acciones está actualizado y todo el entorno restaurado y limpio.
- [ ] El estudiante puede, ante un tercer escenario propuesto verbalmente por el mentor, describir en 5 minutos la declaración, la primera comunicación, la mitigación y los tres primeros comandos que ejecutaría.

## Entrega

En tu repositorio de entregas, carpeta `03-modulo-avanzado/09-incident-management-y-troubleshooting-avanzado/`:

1. `marco/`, `runbooks/`, `escenarios/` (con `SOLUCIONES.md` cifrado o ausente).
2. `incidentes/INC-1/` e `incidentes/INC-2/` completos, con `capturas/` (usuario o máquina visibles; nada de secretos).
3. Enlaces a los issues de acciones correctivas y `seguimiento.md`.
4. `laboratorio-incidentes.md`.
5. `ENTREGA.md` con evaluación, checklist y uso de IA.

Nota sobre IA: durante los simulacros puedes usar IA como la usarías en producción, para interpretar un mensaje de error o recordar la sintaxis de un comando, y debes anotarlo en el timeline como cualquier otra consulta. No la uses para redactar el postmortem: se te pedirá defenderlo oralmente.

## Evaluación

1. **Conceptual.** ¿Por qué el Incident Commander no debe teclear en producción? Describe qué pasa en un incidente cuando la misma persona investiga, decide y comunica, y cómo lo mitigaste tú al hacer los cuatro roles.
2. **Situacional.** A las 03:10 salta la alerta de burn rate rápido de `api` con 8 % de errores. Declara el incidente: severidad, primera comunicación (redáctala) y las tres primeras comprobaciones, en orden y con justificación.
3. **Conceptual.** Explica la diferencia entre mitigación y corrección con dos ejemplos de tus simulacros. ¿Cuándo es aceptable cerrar un incidente sin conocer la causa?
4. **Situacional.** Llevas 40 minutos en un Sev 2 sin hipótesis viable. Según tu matriz, ¿qué haces? Un compañero dice que escalar "queda mal". Responde con argumentos.
5. **Técnica.** Los usuarios reportan "a veces falla". Con el método del curso, ¿cómo acotas el síntoma con tu telemetría (qué consultas) antes de tocar nada? ¿Qué es biseccionar por tiempo y qué comando o consulta te da la "última versión buena"?
6. **Troubleshooting.** `api` devuelve 500 en todas las peticiones; sus logs dicen `could not translate host name "postgres" to address`. Recorre las capas: qué comprobarías en Kubernetes, en DNS y en la configuración, y qué comando confirma cada hipótesis.
7. **Troubleshooting.** `curl -v https://pedidos.lab` falla con error de certificado. Escribe el comando que te dice las fechas del certificado servido y explica cómo la acción correctiva de tu postmortem habría evitado el incidente.
8. **Troubleshooting.** `inventario` entra en `CrashLoopBackOff` cada 4 minutos y `kubectl describe` muestra `OOMKilled`. ¿Es una mitigación válida subir el límite de memoria? ¿Qué mirarías en Prometheus para distinguir una fuga de un dimensionamiento insuficiente?
9. **Troubleshooting.** En Azure, la aplicación de la VM dejó de responder desde fuera pero por SSH funciona y `curl localhost` responde. Nombra las tres primeras cosas que mirarías en la suscripción y el comando de Azure CLI o la herramienta de Network Watcher para cada una.
10. **Conceptual.** ¿Qué hace que un postmortem sea "sin culpables"? Reescribe esta frase en ese estilo: "El incidente ocurrió porque Juan desplegó sin probar en staging".
11. **Técnica.** Da una acción correctiva mal formulada ("mejorar la monitorización") y conviértela en SMART para tu servicio, con la métrica que demostraría que se completó.
12. **Conceptual.** Explica la diferencia entre el timeline registrado en vivo y el reconstruido desde telemetría. ¿Qué tiempos (detección, reconocimiento, mitigación, resolución) se calculan con cada uno y por qué importa el rol de escriba?
13. **Situacional.** Durante un Sev 1, dirección pide "una llamada rápida para entender qué pasa" con el responder. ¿Qué haces como IC y qué rol absorbe esa petición? Redacta la respuesta de dos líneas.
14. **Conceptual.** ¿Por qué "5 porqués" puede llevar a una causa única engañosa y cómo lo compensa el diagrama de causa-efecto? Pon un ejemplo de factor contribuyente de tu INC-1 que no era "la causa".
15. **Reflexión.** Compara tus tiempos de INC-1 e INC-2. ¿Qué parte de la mejora atribuyes al método y cuál a conocer ya el sistema? ¿Qué hábito te llevas para el Proyecto Final?

## Checklist final

Antes de continuar, deberías poder:

- [ ] Clasificar un incidente con la matriz de severidades y saber cuándo subir o bajar de nivel.
- [ ] Declarar un incidente en menos de 5 minutos con la plantilla y asumir el rol de IC.
- [ ] Mantener un war room y un timeline con marcas de tiempo y etiquetas de rol.
- [ ] Comunicar a stakeholders con cadencia fija, plantilla y status page.
- [ ] Escalar según la matriz sin considerarlo un fracaso.
- [ ] Mitigar primero con una acción segura y planificar la corrección después.
- [ ] Hacer 5 porqués con evidencia y un diagrama de causa-efecto con factores contribuyentes.
- [ ] Reconstruir un timeline desde Loki, Prometheus, Tempo y Alertmanager y calcular los cuatro tiempos.
- [ ] Escribir un postmortem sin culpables con acciones SMART y hacer su seguimiento en issues.
- [ ] Aplicar el método (acotar, qué cambió, hipótesis, bisección, mitigar) con las herramientas de cada capa en Linux, red, Kubernetes y Azure.
- [ ] Explicar qué síntomas produce cada uno de los siete escenarios y cómo se confirma cada uno.
- [ ] Tener el marco (severidades, escalado, roles, plantillas, runbooks) listo para reutilizarlo en el Proyecto Final.

---

*Recursos verificados el 2026-09-27 mediante búsqueda web (existencia y vigencia de las URLs). Si un enlace falla, abre un issue en este repositorio.*
