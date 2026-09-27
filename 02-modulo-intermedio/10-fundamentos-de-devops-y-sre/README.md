# Fundamentos de DevOps y SRE

> Módulo: Intermedio · Curso 10 de 11 · Duración estimada: 15-20 horas · Estado: ✅ Completo

## Objetivo

Llevas nueve cursos construyendo piezas: un servidor Linux administrado, una red que sabes diagnosticar, scripts que automatizan, un repositorio con ramas y Pull Requests, una suscripción de Azure, una aplicación en contenedor, un pipeline que la despliega, infraestructura en Terraform y telemetría que te dice si algo va mal. Este curso responde a la pregunta que une todo eso: **cómo se organiza un equipo para entregar software rápido sin romper producción, y qué hace cuando producción se rompe de todas formas**.

DevOps es una forma de trabajar (cultura, automatización, medición, ownership de extremo a extremo) que nació para acabar con el muro entre "los que programan" y "los que operan". SRE (Site Reliability Engineering) es la implementación concreta que Google publicó de esa idea: tratar la operación como un problema de ingeniería, medir la fiabilidad con SLI y SLO, gastar un presupuesto de error de forma consciente, eliminar el trabajo manual repetitivo (toil) y aprender de los incidentes con postmortems sin culpables.

Aquí no vas a desplegar nada nuevo. Vas a **analizar un incidente ficticio pero muy realista** ocurrido sobre la aplicación del curso de Docker, reconstruir qué pasó minuto a minuto, medir cuánto presupuesto de error se quemó, escribir el postmortem, identificar el toil que agravó la caída, proponer acciones correctivas con dueño y plazo y definir los SLI/SLO/SLA de la aplicación. Es exactamente el trabajo que hace un SRE la mañana siguiente a una caída.

**Antes de empezar** debes tener frescos los cursos de Docker, CI/CD y Monitoreo y Observabilidad: el incidente mezcla un despliegue con GitHub Actions, un contenedor en Azure y telemetría en Application Insights. Si no recuerdas qué es una revisión de Azure Container Apps o una alerta de Azure Monitor, repásalo antes.

### Al terminar este curso deberías poder

- Explicar con tus palabras qué es DevOps, qué es SRE y en qué se relacionan (SRE como una forma de implementar DevOps), sin recitar definiciones de marketing.
- Describir los pilares culturales de DevOps (colaboración, ownership, feedback loops, automatización, mejora continua) y reconocerlos o echarlos en falta en una situación concreta.
- Situar Infrastructure as Code, CI/CD y observabilidad como prácticas que sostienen DevOps, conectándolas con lo que ya hiciste en los cursos 7, 8 y 9.
- Definir SLI, SLO, SLA y error budget, distinguirlos con ejemplos y calcular el presupuesto de error de un SLO mensual en minutos y en peticiones.
- Explicar qué es toil, por qué es dañino y cómo identificarlo en un proceso operativo real.
- Reconstruir el timeline de un incidente a partir de logs, chats y gráficas, y separar detección, diagnóstico, mitigación y resolución.
- Escribir un postmortem blameless: causas contribuyentes (no "culpables"), impacto medido, qué funcionó, qué no, y acciones correctivas priorizadas con owner y plazo.
- Redactar un documento de SLI/SLO/SLA para una aplicación pequeña usando una plantilla.
- Comparar cómo gestionaría el mismo incidente un equipo de operaciones tradicional y uno DevOps/SRE, y justificar las diferencias.
- Nombrar las cuatro métricas DORA y explicar qué mide cada una.

## Prerrequisitos

- Cursos 6 (Docker y Contenedores), 7 (CI/CD) y 9 (Monitoreo y Observabilidad) del Módulo Intermedio. Recomendable el curso 1 (Administración de Linux) para entender los logs.
- Saber leer un workflow de GitHub Actions y una consulta KQL sencilla.
- Tu repositorio de entregas y un editor de Markdown. No se necesita Azure ni la VM para este laboratorio (es análisis y redacción), aunque puedes usar la app del curso de Docker para comprobar hipótesis si quieres.

## Temario

Qué es DevOps · Qué es SRE · Cultura DevOps · Automation · Ownership · Feedback loops · Infrastructure as Code · CI/CD · Reliability · Toil · Incidentes · SLA · SLI · SLO · Error budgets introductorios · Postmortems.

**Práctica:** analizar un incidente ficticio y proponer mejoras.

## Recursos en español

### Introducción a DevOps y Presentación de los pilares de DevOps (Microsoft Learn)
- **URL:** "Introducción a DevOps": https://learn.microsoft.com/es-es/training/modules/introduction-to-devops/ · "Presentación de los pilares de DevOps: cultura y producto ajustado": https://learn.microsoft.com/es-es/training/modules/introduce-foundation-pillars-devops/ (forma parte de la ruta "Introducción a DevOps Dojo": https://learn.microsoft.com/es-es/training/paths/devops-dojo-white-belt-foundation/)
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Módulos de aprendizaje
- **Duración aproximada:** 1,5-2 h en total
- **Cubre:** Qué es DevOps ("personas, procesos y productos para entregar valor de forma continua"), cultura DevOps, ownership, feedback loops, automatización, producto ajustado (lean).
- **Nivel:** Introductorio
- **Acceso:** Libre; cuenta Microsoft gratuita para guardar progreso
- **Por qué lo recomiendo:** Es la definición oficial de Microsoft, en español, con los 4 pilares y las 8 capacidades de DevOps y los ejemplos de "mentalidad DevOps". Es el punto de partida del curso: te da vocabulario compartido antes de entrar en SRE.

### Introducción a la Ingeniería de confiabilidad de sitios (SRE) y Administración de la confiabilidad del sitio (Microsoft Learn)
- **URL:** https://learn.microsoft.com/es-es/training/modules/intro-to-site-reliability-engineering/ · https://learn.microsoft.com/es-es/training/modules/manage-site-reliability/ · Complementario sobre supervisión: https://learn.microsoft.com/es-es/training/modules/improve-reliability-monitoring/
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Módulos de aprendizaje
- **Duración aproximada:** 2-2,5 h en total
- **Cubre:** Qué es SRE, reliability, SLI/SLO/SLA, error budgets, toil, incidentes, postmortems, cómo empezar con SRE en un equipo pequeño.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la versión resumida y en español de las ideas del libro de Google, escrita para equipos que usan Azure. Ideal para entender el vocabulario SRE antes de leer los capítulos originales en inglés.

### ¿Qué es DevOps? (Atlassian y Microsoft Learn)
- **URL:** Atlassian: https://www.atlassian.com/es/devops · Microsoft Learn: https://learn.microsoft.com/es-es/devops/what-is-devops
- **Autor / organización:** Atlassian; Microsoft
- **Idioma:** Español
- **Tipo:** Guías de referencia
- **Duración aproximada:** 45 min entre ambas (lee también las subpáginas de Atlassian sobre cultura y prácticas)
- **Cubre:** Qué es DevOps, cultura, ciclo de vida, prácticas (CI/CD, IaC, monitorización), equipos.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Dos empresas distintas explican lo mismo con palabras distintas. Compáralas: verás que DevOps no es una herramienta ni un puesto de trabajo, sino una forma de organizar el trabajo. La guía de Atlassian tiene además una sección de gestión de incidentes que usarás más adelante.

### Informe DORA 2025, "State of AI-assisted Software Development" (DORA / Google Cloud)
- **URL:** https://dora.dev/dora-report-2025/ (descarga; disponible en español) · Página de Google Cloud en español: https://cloud.google.com/devops/state-of-devops?hl=es-419
- **Autor / organización:** DORA (DevOps Research and Assessment), equipo de investigación de Google Cloud
- **Idioma:** Español (traducción oficial) e inglés
- **Tipo:** Informe de investigación anual
- **Duración aproximada:** 1-1,5 h para el resumen ejecutivo y los capítulos sobre métricas y capacidades
- **Cubre:** Métricas de entrega y estabilidad (las "cuatro claves" DORA), capacidades que distinguen a los equipos de alto rendimiento, cultura, y desde 2024 el efecto de la IA en el desarrollo.
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre (puede pedir un formulario con correo para la descarga)
- **Por qué lo recomiendo:** Es la investigación con más datos del sector sobre qué funciona en DevOps. Le da base empírica a lo que el resto de recursos afirma. Lee el resumen y la sección de métricas; el resto es opcional.

## Recursos en inglés

### Site Reliability Engineering, "el libro de SRE" (Google)
- **URL:** Índice: https://sre.google/sre-book/table-of-contents/ · Capítulo "Eliminating Toil": https://sre.google/sre-book/eliminating-toil/ · Apéndice "Example Postmortem": https://sre.google/sre-book/example-postmortem/ · Todos los libros: https://sre.google/books/
- **Autor / organización:** Google (Betsy Beyer, Chris Jones, Jennifer Petoff, Niall Richard Murphy, editores)
- **Idioma:** Inglés
- **Tipo:** Libro completo en línea, gratuito
- **Duración aproximada:** Para este curso, capítulos 1 (Introduction), 3 (Embracing Risk), 4 (Service Level Objectives), 5 (Eliminating Toil), 14 (Managing Incidents) y 15 (Postmortem Culture: Learning from Failure), más el apéndice con el postmortem de ejemplo: 5-6 h
- **Cubre:** Qué es SRE, reliability, SLI/SLO/SLA, error budgets, toil, incidentes, postmortems.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es el texto fundacional de la disciplina y sigue siendo la mejor explicación de por qué "100 % de disponibilidad" es el objetivo equivocado. Los seis capítulos indicados son el corazón teórico del curso. No leas el libro entero ahora: el resto se retoma en SRE Avanzado.

### The Site Reliability Workbook (Google)
- **URL:** Índice: https://sre.google/workbook/table-of-contents/ · "Implementing SLOs": https://sre.google/workbook/implementing-slos/ · "Alerting on SLOs": https://sre.google/workbook/alerting-on-slos/ · "Eliminating Toil": https://sre.google/workbook/eliminating-toil/ · "Postmortem Culture" (con análisis de un postmortem real): https://sre.google/workbook/postmortem-analysis/
- **Autor / organización:** Google
- **Idioma:** Inglés
- **Tipo:** Libro completo en línea, gratuito
- **Duración aproximada:** Para este curso, capítulos 1 (How SRE Relates to DevOps), 2 (Implementing SLOs) y 10 (Postmortem Culture): 3 h. El de alertas sobre SLO es opcional.
- **Cubre:** Relación DevOps/SRE, receta paso a paso para definir SLI y SLO, error budget policy, postmortems con ejemplos buenos y malos.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es el "cómo" del libro anterior. El capítulo 2 es la guía que seguirás para escribir el documento de SLO del laboratorio, y el capítulo 10 compara un postmortem mal escrito con uno bien escrito: léelo antes de redactar el tuyo.

### Incident management: postmortems (Atlassian)
- **URL:** Cómo hacer un postmortem sin culpables: https://www.atlassian.com/incident-management/postmortem/blameless · Proceso de postmortem: https://www.atlassian.com/incident-management/postmortem · Plantillas: https://www.atlassian.com/incident-management/postmortem/templates · Los 5 porqués: https://www.atlassian.com/incident-management/postmortem/5-whys · Capítulo del handbook: https://www.atlassian.com/incident-management/handbook/postmortems
- **Autor / organización:** Atlassian
- **Idioma:** Inglés
- **Tipo:** Guías prácticas
- **Duración aproximada:** 1 h
- **Cubre:** Incidentes, postmortems, cultura sin culpa, análisis de causas contribuyentes.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Más corto y directo que Google, y con una plantilla y un método (los 5 porqués) que puedes aplicar directamente al incidente del laboratorio. Es la visión de una empresa que no es Google, lo que demuestra que estas prácticas son del sector.

### What is DevOps? REALLY understand it | DevOps vs SRE (TechWorld with Nana)
- **URL:** https://www.youtube.com/watch?v=0yWAtQ6wYNM
- **Autor / organización:** Nana Janashia (TechWorld with Nana)
- **Idioma:** Inglés (subtítulos)
- **Tipo:** Vídeo
- **Duración aproximada:** 20 min
- **Cubre:** Qué es DevOps frente a lo que dice el marketing, qué hace un ingeniero DevOps, DevOps frente a SRE.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Publicado en 2022, sigue siendo la explicación en vídeo más clara y honesta de "qué es realmente DevOps" y de cómo se diferencia de SRE. Bueno para el primer día del curso.

### Accelerate State of DevOps Report 2024 (DORA)
- **URL:** https://dora.dev/research/2024/dora-report/ · Todas las publicaciones: https://dora.dev/research/publications/
- **Autor / organización:** DORA (Google Cloud)
- **Idioma:** Inglés
- **Tipo:** Informe de investigación
- **Duración aproximada:** 45 min para el resumen y la sección de métricas
- **Cubre:** Las cuatro métricas DORA (frecuencia de despliegue, lead time de cambios, tasa de fallo de cambios, tiempo de recuperación) y cómo se relacionan con la cultura y la plataforma.
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Complementario al informe de 2025. Las cuatro métricas se explican con más detalle y las usarás para puntuar al equipo del incidente en la parte F del laboratorio.

## Documentación oficial

DevOps y SRE son disciplinas, no productos, pero tienen fuentes de referencia estables:

- **Google SRE, portal de libros y recursos:** https://sre.google/ · Libros gratuitos: https://sre.google/books/
- **Microsoft Learn, documentación de SRE:** https://learn.microsoft.com/es-es/azure/site-reliability-engineering/ · Lista de libros de SRE recomendados: https://learn.microsoft.com/es-es/azure/site-reliability-engineering/resources/books
- **Azure Well-Architected Framework, cultura DevOps (pilar de excelencia operativa):** https://learn.microsoft.com/es-es/azure/well-architected/operational-excellence/devops-culture
- **DORA, investigación y publicaciones:** https://dora.dev/research/publications/
- **Atlassian, gestión de incidentes:** https://www.atlassian.com/incident-management/postmortem

## Ruta recomendada de estudio

1. **Ver** el vídeo de TechWorld with Nana (20 min). Anota en una línea qué es DevOps y en otra qué es SRE.
2. **Hacer** los dos módulos de DevOps de Microsoft Learn (2 h). Al terminar debes poder nombrar los pilares y dar un ejemplo propio de cada uno.
3. **Leer** las guías "¿Qué es DevOps?" de Atlassian y de Microsoft (45 min) y escribir un párrafo con tu propia definición.
4. **Leer** el capítulo 1 del SRE Workbook, "How SRE Relates to DevOps" (30 min). Aquí encaja todo lo anterior.
5. **Hacer** los módulos de SRE de Microsoft Learn (2-2,5 h). Vocabulario: SLI, SLO, SLA, error budget, toil, postmortem.
6. **Leer** los capítulos 1, 3 y 4 del libro de SRE (2 h). Céntrate en "Embracing Risk" y en la tabla de disponibilidad del apéndice: calcula a mano cuántos minutos al mes permiten 99 %, 99,9 % y 99,99 %.
7. **Leer** el capítulo 2 del Workbook, "Implementing SLOs" (1 h). Es la receta que aplicarás en la parte G del laboratorio.
8. **Leer** los capítulos de toil de ambos libros (1 h) y apunta tres ejemplos de toil de tus propios laboratorios anteriores.
9. **Leer** los capítulos 14 y 15 del libro de SRE, el apéndice "Example Postmortem" y el capítulo 10 del Workbook (2 h). Después lee las guías de postmortem de Atlassian (1 h).
10. **Leer** el resumen y la sección de métricas de los informes DORA 2024 y 2025 (1,5 h).
11. **Hacer el laboratorio** (6-8 h, en dos o tres sesiones).
12. **Responder la evaluación** y **revisar el checklist**.

Si vas justo de tiempo: haz obligatoriamente los puntos 2, 5, 7, 9 y 11.

## Laboratorio

### Objetivo

Analizar de principio a fin un incidente ficticio de producción sobre la aplicación del curso de Docker: reconstruir el timeline, medir el impacto sobre el SLO, clasificar las causas contribuyentes, escribir un postmortem blameless, identificar el toil, proponer acciones correctivas priorizadas y definir los SLI/SLO/SLA de la aplicación. Cierra con un ejercicio de cultura comparando la gestión "ops tradicional" con la DevOps/SRE.

### Requisitos

- Haber leído al menos los capítulos de SLO, toil y postmortem indicados en la ruta.
- Editor de Markdown y calculadora. Opcional: una hoja de cálculo para el timeline.
- Todo se entrega como archivos Markdown en tu repositorio. No hay que desplegar nada.

> **Regla del laboratorio.** El material del incidente que sigue es la única fuente. No inventes datos que no estén aquí; si algo no se sabe, dilo en el postmortem ("no hay evidencia de..."). Eso también es SRE.

### El incidente: INC-2026-0914, caída de `api-pedidos` en producción

**Contexto.** Nubia Logística es una empresa ficticia de 40 personas. Su API de pedidos, `api-pedidos`, es la aplicación del curso de Docker (FastAPI, endpoints `/health` y `/version`) a la que el equipo añadió un endpoint `POST /pedidos` que escribe en una base de datos PostgreSQL gestionada. Corre en **Azure Container Apps** en la región West Europe, con una única revisión activa, y se despliega con **GitHub Actions** al hacer merge en `main`: el workflow construye la imagen, la sube a Azure Container Registry con la etiqueta de versión y ejecuta `az containerapp update`. La telemetría va a **Application Insights**. El equipo lo forman tres desarrolladores (Ana, Diego, Sofía), un administrador de sistemas (Luis, que hace guardia esta semana), una responsable de soporte (Marta) y el responsable técnico (Carlos). Tráfico habitual un lunes por la mañana: unas 40 peticiones por minuto a `/pedidos`.

**El cambio.** La PR #212 de Ana renombra la variable de entorno `DB_HOST` (junto con `DB_USER`, `DB_PASSWORD`, `DB_NAME`) por una única `DATABASE_URL` con la cadena de conexión completa, porque la biblioteca de acceso a datos lo recomienda. Los tests unitarios pasan (usan una base de datos SQLite en memoria y no leen variables). La descripción de la PR dice "Refactor: simplificar configuración de BD". Diego la aprueba en 6 minutos. Nadie actualiza el workflow `deploy.yml`, que sigue definiendo `DB_HOST`, `DB_USER`, `DB_PASSWORD` y `DB_NAME` en `--set-env-vars`. El código lee `os.environ["DATABASE_URL"]` **dentro** del handler de `/pedidos`, no al arrancar, así que el proceso arranca sin error y `/health` (que solo devuelve `{"status": "ok"}`) responde 200.

**Timeline (hora local, lunes 14 de septiembre de 2026).**

| Hora | Qué pasa | Fuente |
|---|---|---|
| 09:58 | Merge de PR #212 en `main`. | GitHub |
| 10:05 | Workflow `deploy.yml`: build y tests en verde (2 min 40 s), push de la imagen `api-pedidos:1.4.0`. | GitHub Actions |
| 10:12 | `az containerapp update` termina. Nueva revisión `api-pedidos--1-4-0` recibe el 100 % del tráfico. El paso "smoke test" del workflow hace `curl /health` y obtiene 200: el workflow termina en verde. | GitHub Actions, Azure |
| 10:12-10:31 | `POST /pedidos` responde 500 en el 96 % de los casos (`KeyError: 'DATABASE_URL'` en los logs). `/health` y `/version` responden 200. Ninguna alerta se dispara: la única alerta configurada es "CPU > 80 % durante 5 min", y la CPU baja (las peticiones fallan en milisegundos). | App Insights |
| 10:31 | Marta (soporte) en el canal `#soporte`: "Tres clientes dicen que no pueden crear pedidos desde hace un rato, ¿alguien sabe algo?". | Chat |
| 10:34 | Luis (guardia) responde: "Miro". Abre App Insights, ve el pico de excepciones. Crea el canal `#inc-pedidos`. | Chat, App Insights |
| 10:38 | Luis reinicia la revisión desde el portal ("por si acaso"). Sin efecto. | Azure Activity Log |
| 10:41 | Ana entra en el canal: "Es mi cambio de esta mañana. La app ahora lee `DATABASE_URL` y el workflow no la define. Hay que añadirla." | Chat |
| 10:43 | Carlos: "Añadidla a mano en el portal ahora y luego arreglamos el workflow." Luis: "¿Hacemos rollback mejor?" Carlos: "Con la variable es más rápido." | Chat |
| 10:46 | Luis añade `DATABASE_URL` en el portal copiando los valores de las cuatro variables antiguas. Se equivoca en el formato (omite el puerto). Nueva revisión. Los errores cambian a `connection refused`. | Azure, App Insights |
| 10:52 | Carlos: "Rollback. Ya." Luis: "¿Cuál era la imagen anterior?". Busca en ACR: hay etiquetas `1.3.1`, `1.3.2`, `1.4.0` y varias `latest`. Diego confirma por el historial de releases que producción tenía `1.3.2`. | Chat, ACR |
| 10:56 | Luis ejecuta `az containerapp update --image ...:1.3.2` desde su portátil (tuvo que instalar la extensión de la CLI, no la tenía). | Chat, Activity Log |
| 10:59 | La tasa de 500 vuelve al 0,1 % habitual. Luis: "Recuperado". Marta avisa a los clientes. | App Insights, Chat |
| 11:20 | PR #214 (Ana): añade `DATABASE_URL` al workflow y elimina las cuatro variables antiguas. | GitHub |
| 14:05 | Despliegue de `1.4.1` con la PR #214, en horario de bajo tráfico, tras comprobar a mano con `curl` un `POST /pedidos` de prueba. Sin incidencias. | GitHub Actions |

**Fragmento del chat en `#inc-pedidos` (10:43-10:47).**

```
[10:43] Carlos: Añadidla a mano en el portal ahora y luego arreglamos el workflow.
[10:43] Luis:   ¿Hacemos rollback mejor? La 1.3.2 funcionaba.
[10:43] Carlos: Con la variable es más rápido. Son 30 segundos.
[10:44] Ana:    El formato es postgresql://usuario:password@host:5432/nombre
[10:46] Luis:   Puesta. Nueva revisión desplegando.
[10:47] Luis:   Sigue fallando pero con otro error, "connection refused"...
[10:47] Ana:    ¿Has puesto el :5432? Sin puerto intenta otro por defecto en esta lib.
```

**Gráficas (descritas).**

- *Gráfica 1, tasa de respuestas 5xx en `POST /pedidos`, 09:30-11:30.* Línea plana en 0,1 % hasta las 10:12; salto vertical al 96 % y meseta hasta las 10:59; caída vertical al 0,1 %. Entre 10:46 y 10:52 la meseta sigue al 96 % (cambió el tipo de error, no la tasa).
- *Gráfica 2, peticiones por minuto a `POST /pedidos`.* Alrededor de 40/min antes y después. Durante la caída baja a unas 25/min a partir de las 10:25: los clientes dejan de reintentar.
- *Gráfica 3, disponibilidad de `/health`.* 100 % durante todo el periodo. La prueba de disponibilidad de App Insights (cada 5 min contra `/health`) nunca falló.
- *Gráfica 4, CPU del contenedor.* Entre 3 % y 8 % todo el tiempo. La alerta de CPU > 80 % nunca se acercó a dispararse.

**Datos para el cálculo de impacto.**

- Duración del impacto en usuarios: de 10:12 a 10:59, **47 minutos**.
- Peticiones a `/pedidos` durante el incidente: aproximadamente 1 550 (media de 33/min), de las que 1 490 fallaron.
- SLO vigente (definido de palabra, nunca escrito): "99,9 % de disponibilidad mensual de la API de pedidos", entendido por el equipo como porcentaje de peticiones a `/pedidos` sin error 5xx en una ventana de 30 días.
- Peticiones mensuales típicas a `/pedidos`: 1 700 000.
- Antes de este incidente, en el mes en curso ya se habían consumido 12 minutos de caída total equivalente (el día 3, un fallo de la base de datos con unas 500 peticiones fallidas).
- SLA contractual con los clientes: 99,5 % mensual, con crédito del 10 % de la factura si se incumple.

### Instrucciones

Documenta todo en `analisis-incidente.md`, salvo lo que se indique en archivos propios.

**Parte A: Reconstrucción del timeline (60 min)**

1. Reescribe el timeline en una tabla con columnas: hora, evento, tipo (cambio / detección / diagnóstico / decisión / mitigación / comunicación / resolución), actor, fuente de evidencia. Añade una fila para cada mensaje relevante del chat.
2. Calcula y explica: tiempo hasta detección (desde 10:12 hasta que alguien del equipo supo que había un problema), tiempo hasta diagnóstico (hasta que se identificó la causa), tiempo hasta mitigación (hasta que los usuarios dejaron de sufrir) y tiempo total. Indica qué fase fue la más larga y por qué.
3. Señala en el timeline los tres momentos en los que una decisión distinta habría acortado el incidente y explica qué información faltaba para tomarla.

**Parte B: Impacto sobre el SLO y el SLA (45 min)**

4. Calcula el **error budget mensual** del SLO de 99,9 % de dos formas: en tiempo (minutos de indisponibilidad total equivalente en 30 días) y en peticiones (número de peticiones fallidas permitidas sobre 1 700 000). Muestra las operaciones.
5. Calcula cuánto presupuesto quedaba antes del incidente (resta lo consumido el día 3, en las dos unidades) y cuánto consumió este incidente. Para la medida en tiempo, considera que el incidente afectó al 96 % de las peticiones durante 47 minutos y convierte a "minutos de caída total equivalente". ¿Queda presupuesto? ¿En cuánto se ha excedido o cuánto sobra? Expresa el resultado también en porcentaje del presupuesto.
6. Comprueba si se ha incumplido el **SLA** del 99,5 %. Explica por qué es posible agotar el error budget del SLO sin incumplir el SLA y por qué es deseable que sea así (SLO más estricto que SLA).
7. Explica qué habría medido de forma distinta un SLI basado en `/health` frente a uno basado en `/pedidos`, y qué te dice eso sobre elegir SLI "desde el punto de vista del usuario".

**Parte C: Causas contribuyentes (45 min)**

8. Lista al menos **ocho causas contribuyentes** y clasifícalas en: cambio (código, configuración), proceso (revisión, despliegue, pruebas), detección (alertas, SLI, health checks), respuesta (runbooks, herramientas, decisiones, comunicación) y cultura/organización. Para cada una escribe una frase que empiece por "El sistema permitió que..." o "Faltaba...", nunca por un nombre de persona.
9. Aplica los 5 porqués a la causa que consideres más importante y muestra la cadena completa.
10. Escribe un párrafo sobre por qué "Ana no actualizó el workflow" o "Luis se equivocó al copiar la variable" son descripciones **correctas de hechos** pero **causas incorrectas** para un postmortem, y qué causa sistémica hay detrás de cada una.

**Parte D: Postmortem blameless (90 min)**

11. Escribe `postmortem-INC-2026-0914.md` usando la plantilla siguiente. Cada sección debe tener contenido propio derivado del material; el impacto debe incluir los números de la parte B.

```markdown
# Postmortem: <título corto y descriptivo>

- **Identificador:** INC-AAAA-NNNN
- **Fecha del incidente:** AAAA-MM-DD, HH:MM a HH:MM (zona horaria)
- **Autores:** <quién escribe el postmortem>
- **Estado:** Borrador | En revisión | Completo
- **Severidad:** SEV1 | SEV2 | SEV3 (define la escala en una línea)

## Resumen
<Tres a cinco frases: qué falló, a quién afectó, cuánto duró, cómo se resolvió.>

## Impacto
<Usuarios afectados, peticiones fallidas, minutos, error budget consumido (antes / después), impacto en SLA, impacto económico o reputacional si se conoce.>

## Detección
<Cómo se supo que había un problema. Quién lo detectó y con qué. Tiempo hasta detección. Qué debería haberlo detectado y no lo hizo.>

## Causas contribuyentes
<Lista clasificada. Sin nombres de personas como causa. "El sistema permitió que...">

## Disparador (trigger)
<El evento concreto que inició el incidente. Distinto de las causas.>

## Resolución y mitigación
<Qué se hizo, en qué orden, qué funcionó y qué no.>

## Timeline detallado
<Tabla con hora, evento, actor, fuente.>

## Qué funcionó bien
<Al menos tres cosas. Siempre hay algo.>

## Qué no funcionó / dónde tuvimos suerte
<Incluye "dónde tuvimos suerte": qué habría empeorado el incidente en otras condiciones.>

## Lecciones aprendidas
<Frases generales que valen para otros servicios.>

## Acciones correctivas
| # | Acción | Tipo (prevenir / detectar / mitigar / proceso) | Prioridad (P0-P2) | Owner (rol) | Plazo | Estado |
|---|---|---|---|---|---|---|

## Anexos
<Consultas KQL, fragmentos de logs, enlaces a PRs, capturas.>
```

12. Al final del postmortem añade una sección "Revisión blameless" en la que compruebes tu propio texto: busca cualquier frase que atribuya culpa a una persona y reescríbela. Deja la versión antes y después de al menos dos frases.

**Parte E: Toil (30 min)**

13. Identifica al menos **cinco tareas de toil** en el incidente y en el proceso de despliegue descrito (por ejemplo: buscar a mano qué imagen estaba en producción, instalar la CLI en el portátil durante la guardia, copiar valores de variables por el portal, comprobar con `curl` a mano tras desplegar...). Para cada una indica cuáles de las características del toil del libro de SRE cumple (manual, repetitiva, automatizable, táctica, sin valor duradero, crece con el servicio) y cómo la eliminarías o automatizarías.
14. Estima cuántos minutos del incidente se fueron en toil puro y argumenta qué duración habría tenido con esas tareas automatizadas.

**Parte F: Acciones correctivas priorizadas (45 min)**

15. Propón **cinco acciones correctivas** (pueden coincidir con las del postmortem, pero aquí se justifican con detalle). Para cada una: descripción concreta, qué causa contribuyente ataca, tipo (prevenir / detectar / mitigar / proceso), prioridad P0-P2 con justificación, owner por rol (no por nombre), plazo realista, cómo se verificará que está hecha y coste aproximado en horas. Al menos una debe ser de detección (alerta sobre el SLI real, no sobre CPU), una de mitigación (rollback en un comando, con runbook) y una de prevención (por ejemplo, validación de configuración al arrancar o un test de integración que arranque el contenedor con las variables del workflow).
16. Puntúa al equipo de Nubia Logística en las cuatro métricas DORA con lo que sabes (frecuencia de despliegue, lead time, tasa de fallo de cambios, tiempo de recuperación), explica qué dato te falta para cada una y qué medirías a partir de ahora.

**Parte G: SLI, SLO y SLA de `api-pedidos` (60 min)**

17. Escribe `slo-api-pedidos.md` con esta plantilla, siguiendo la receta del capítulo "Implementing SLOs" del Workbook. Define al menos dos SLI (disponibilidad y latencia) y un SLO para cada uno. Justifica cada número; no copies "99,9 %" sin explicar por qué no 99,5 % ni 99,99 %.

```markdown
# SLO de <servicio>

- **Propietario del servicio:** <rol>
- **Fecha / revisión:** AAAA-MM-DD, revisar cada <n> meses
- **Usuarios y recorrido crítico:** <quién usa el servicio y qué hace con él>

## SLI 1: <nombre, por ejemplo Disponibilidad de creación de pedidos>
- **Definición:** proporción de <eventos buenos> sobre <eventos válidos>. Ejemplo: peticiones a `POST /pedidos` con código distinto de 5xx sobre el total de peticiones a `POST /pedidos`.
- **Dónde se mide:** <App Insights, balanceador, cliente...> y por qué ahí.
- **Consulta o método de medida:** <KQL u otra>.
- **Exclusiones:** <mantenimientos anunciados, tráfico de pruebas...>

## SLO 1
- **Objetivo:** <99,x %> en ventana <móvil de 30 días | mes natural>.
- **Error budget resultante:** <minutos equivalentes y peticiones>.
- **Justificación del número:** <por qué este y no uno mayor o menor: coste, expectativas, historia>.

## SLI 2 / SLO 2: <Latencia>
<Misma estructura. Ejemplo de SLI: proporción de peticiones a POST /pedidos con duración < 500 ms.>

## Política de error budget
- Si el presupuesto restante baja del <x %> a mitad de ventana: <congelar despliegues no urgentes, priorizar fiabilidad...>
- Si el presupuesto se agota: <qué se para, quién decide, cómo se comunica>.
- Si sobra presupuesto de forma sistemática: <qué se puede permitir el equipo: más despliegues, experimentos>.

## Alertas derivadas
- <Alerta sobre el SLI, no sobre CPU: qué condición, qué ventana, a quién avisa.>

## Relación con el SLA
- **SLA contractual:** <99,x %, consecuencias>.
- **Margen SLO frente a SLA:** <por qué el SLO es más estricto>.
```

18. Añade una sección "Cómo lo habría cambiado": explica qué habría pasado en el incidente si este documento hubiera existido el 14 de septiembre (detección, decisión de rollback, comunicación).

**Parte H: Ejercicio de cultura: ops tradicional frente a DevOps/SRE (45 min)**

19. Escribe `cultura.md` con una tabla de al menos **diez filas** comparando cómo habría gestionado el mismo incidente un equipo "ops tradicional" (desarrollo y operaciones separados, despliegues por ticket, ventanas de cambio, operaciones responsable de producción y desarrollo de las funcionalidades) frente al equipo DevOps/SRE ideal. Filas mínimas: quién despliega, cómo llega el cambio a producción, quién está de guardia, cómo se detecta, quién decide el rollback, cómo se comunica, qué pasa después (culpa frente a postmortem), cómo se mide el éxito, cómo se prioriza el trabajo de fiabilidad, qué pasa con el toil.
20. Termina con dos párrafos: uno sobre qué tenía ya de DevOps el equipo de Nubia Logística (despliegue automático, dev en el canal del incidente, fix forward el mismo día) y otro sobre qué le faltaba de SRE (SLO escrito, alertas sobre SLI, runbook de rollback, política de error budget, postmortem). Sé concreto: cita momentos del timeline.

### Resultado esperado

- `analisis-incidente.md` con las partes A, B, C, E y F.
- `postmortem-INC-2026-0914.md` con la plantilla completa y la revisión blameless.
- `slo-api-pedidos.md` con al menos dos SLI, dos SLO, política de error budget y relación con el SLA.
- `cultura.md` con la tabla comparativa y los dos párrafos.

### Criterios de validación

- [ ] El timeline clasifica cada evento por tipo y los tiempos de detección (19 min), diagnóstico (29 min) y mitigación (47 min) están bien calculados y explicados.
- [ ] El error budget está calculado en minutos y en peticiones, con las operaciones visibles, y la conclusión (presupuesto agotado y excedido; SLA no incumplido) es correcta y está razonada.
- [ ] Hay al menos ocho causas contribuyentes clasificadas, ninguna nombra a una persona como causa y los 5 porqués llegan a una causa sistémica.
- [ ] El postmortem sigue la plantilla, el impacto tiene números, "qué funcionó bien" tiene al menos tres puntos y la revisión blameless muestra frases reescritas.
- [ ] Se identifican al menos cinco tareas de toil con sus características y una propuesta de automatización cada una.
- [ ] Las cinco acciones correctivas tienen tipo, prioridad justificada, owner por rol, plazo, verificación y coste, e incluyen al menos una de detección sobre el SLI, una de rollback y una de prevención.
- [ ] El documento de SLO justifica cada número, define la política de error budget y las alertas derivan del SLI, no de la CPU.
- [ ] La comparación cultural tiene al menos diez filas concretas y los párrafos finales citan momentos del timeline.
- [ ] El estudiante puede explicar oralmente al mentor la diferencia entre SLI, SLO, SLA y error budget con el ejemplo del incidente, sin apuntes.

## Entrega

En tu repositorio de entregas (por Git), carpeta `02-modulo-intermedio/10-fundamentos-de-devops-y-sre/`:

1. `analisis-incidente.md`.
2. `postmortem-INC-2026-0914.md`.
3. `slo-api-pedidos.md`.
4. `cultura.md`.
5. `ENTREGA.md` con evaluación, checklist y uso de IA.

Nota sobre IA: puedes usarla para que te explique un concepto o revise la redacción, pero el análisis, los cálculos y las decisiones deben ser tuyos y coherentes con el material del incidente. Un postmortem generado por IA se nota: es genérico, no cita el timeline y no comete los errores de cálculo que después corriges. Si la usaste, decláralo.

## Evaluación

1. **Conceptual.** Define DevOps y SRE con tus palabras y explica la frase del Workbook "class SRE implements interface DevOps". ¿Puede haber DevOps sin SRE? ¿Y SRE sin cultura DevOps?
2. **Conceptual.** Nombra los pilares culturales de DevOps y da, para cada uno, un ejemplo de algo que hiciste en los cursos 7, 8 o 9 que lo encarna y algo del incidente de Nubia Logística que lo contradice.
3. **Técnica.** Un servicio tiene SLO de 99,95 % mensual sobre peticiones y recibe 4 000 000 de peticiones al mes. ¿Cuántas peticiones fallidas caben en el presupuesto? Si un incidente hace fallar el 50 % de las peticiones durante 30 minutos a 90 peticiones/min, ¿qué porcentaje del presupuesto consume?
4. **Conceptual.** Explica la diferencia entre SLI, SLO y SLA con el ejemplo de `api-pedidos`. ¿Por qué el SLO debe ser más estricto que el SLA? ¿Qué pasaría si fueran iguales?
5. **Situacional.** El equipo propone como SLI "porcentaje de tiempo que `/health` devuelve 200". Explica por qué este incidente demuestra que es un mal SLI y propone dos mejores.
6. **Situacional.** A mitad de mes el error budget está al 10 %. Un desarrollador quiere desplegar una funcionalidad importante para un cliente. ¿Qué dice una política de error budget razonable? ¿Quién decide? ¿Qué alternativa existe a "no desplegar nada"?
7. **Conceptual.** Define toil con las características del libro de SRE y explica por qué "trabajo manual" no siempre es toil y por qué el toil crece con el éxito del servicio. Da un ejemplo del incidente y otro de tus propios laboratorios.
8. **Situacional.** En la reunión de postmortem, Carlos dice: "La causa fue que Ana no avisó del cambio de configuración; que la próxima vez avise". Explica por qué esta conclusión es un problema, qué causa sistémica hay detrás y qué acción correctiva propondrías en su lugar.
9. **Troubleshooting.** Durante el incidente, el reinicio de la revisión (10:38) no sirvió y el hotfix por portal (10:46) empeoró el diagnóstico. ¿Qué información habría necesitado Luis a las 10:34 para ir directo al rollback? Describe el runbook de rollback en cinco pasos concretos con comandos de Azure CLI.
10. **Técnica.** Propón una alerta de Azure Monitor sobre el SLI de disponibilidad de `/pedidos` (condición, ventana de evaluación, umbral, severidad, destinatario) y explica por qué una alerta de CPU no habría servido y por qué una alerta con umbral "1 error" tampoco.
11. **Conceptual.** Explica las cuatro métricas DORA y por qué un equipo que despliega diez veces al día puede ser más estable que uno que despliega una vez al mes. ¿Qué métrica DORA salió peor en el incidente?
12. **Situacional.** Tu jefe propone "prohibir los despliegues los lunes por la mañana y añadir una aprobación del comité de cambios" como acción correctiva. Argumenta a favor y en contra desde la perspectiva DevOps/SRE y propone una alternativa que reduzca el riesgo sin frenar la entrega (pista: despliegues progresivos, validación automática, rollback automático).
13. **Conceptual.** ¿Qué papel juegan Infrastructure as Code y CI/CD en la fiabilidad? Explica cómo el hecho de que la configuración de producción viviera en el workflow (y no en el portal) fue a la vez una fortaleza y una debilidad en este incidente.
14. **Reflexión.** ¿Qué parte del análisis te costó más: los cálculos, escribir sin culpar o priorizar acciones? ¿Qué harás distinto en tu próximo laboratorio de esta ruta sabiendo lo que sabes ahora sobre toil y detección?

## Checklist final

Antes de continuar, deberías poder:

- [ ] Explicar qué es DevOps, qué es SRE y cómo se relacionan.
- [ ] Nombrar los pilares culturales de DevOps y reconocerlos en una situación real.
- [ ] Definir SLI, SLO, SLA y error budget y calcular un presupuesto de error en minutos y en peticiones.
- [ ] Explicar por qué el SLO debe medirse desde el punto de vista del usuario y ser más estricto que el SLA.
- [ ] Definir toil y detectarlo en un proceso operativo.
- [ ] Reconstruir el timeline de un incidente separando detección, diagnóstico y mitigación.
- [ ] Escribir un postmortem blameless con causas contribuyentes y acciones con owner y plazo.
- [ ] Redactar un documento de SLO con política de error budget para un servicio pequeño.
- [ ] Nombrar las cuatro métricas DORA y explicar qué mide cada una.
- [ ] Comparar la gestión de un incidente en un equipo ops tradicional y en uno DevOps/SRE.

---

*Recursos verificados el 2026-09-27 mediante búsqueda web (existencia y vigencia de las URLs). Si un enlace falla, abre un issue en este repositorio.*
