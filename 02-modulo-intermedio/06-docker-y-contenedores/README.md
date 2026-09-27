# Docker y Contenedores

> Módulo: Intermedio · Curso 6 de 11 · Duración estimada: 20-30 horas · Estado: ✅ Completo

## Objetivo

Hasta ahora has desplegado software "a mano": entras en la VM, instalas paquetes, editas configuración, arrancas un servicio. Funciona, pero no se repite igual dos veces, y lo que va bien en tu VM falla en la del compañero. Los contenedores resuelven eso: empaquetas la aplicación **con todo lo que necesita** en una imagen inmutable, la publicas en un registro y la ejecutas igual en tu portátil, en una VM de Azure o en un clúster de Kubernetes.

En este curso aprenderás qué es realmente un contenedor (un proceso aislado con namespaces y cgroups, no una VM pequeña), cómo se construyen imágenes por capas con un Dockerfile bien hecho, cómo se ejecutan, se conectan en red, guardan datos y se configuran con variables de entorno, cómo se orquestan varias con Docker Compose, cómo se publican en Docker Hub y en Azure Container Registry, y cómo se diagnostican cuando fallan.

Aquí nace también **la aplicación del curso de Docker**: una pequeña API web en Python con un endpoint `/health` y otro que devuelve versión y nombre de host. La containerizas en este curso y la reutilizarás en CI/CD (para construirla y desplegarla automáticamente), en Kubernetes y en Helm. Trátala como tu primer "producto".

**Antes de empezar** necesitas Administración de Linux (procesos, systemd, permisos, redes en Linux), Bash y Python básicos, Git intermedio (la app vive en un repositorio) y la cuenta de Azure del curso anterior para la parte de ACR.

### Al terminar este curso deberías poder

- Explicar la diferencia entre un contenedor y una máquina virtual, qué comparten los contenedores con el host y qué aíslan (namespaces, cgroups, sistema de archivos por capas).
- Distinguir imagen, capa, contenedor y registro, y leer `docker history` e `docker inspect` para saber de qué está hecha una imagen.
- Escribir un Dockerfile con buenas prácticas: imagen base pequeña, orden de instrucciones que aproveche la caché, `.dockerignore`, usuario no root, `HEALTHCHECK`, y multi-stage cuando aporte.
- Ejecutar contenedores con puertos, variables de entorno, límites de recursos y políticas de reinicio, y operarlos con `logs`, `exec`, `stats` e `inspect`.
- Persistir datos con volúmenes y bind mounts sabiendo cuándo usar cada uno y qué pasa con los permisos.
- Conectar contenedores por nombre en una red bridge propia y explicar cómo funciona el DNS interno de Docker.
- Describir una aplicación de varios servicios (API, base de datos, proxy inverso) en Docker Compose y operarla como una unidad.
- Publicar una imagen etiquetada en Docker Hub y en Azure Container Registry, conociendo el coste del registro y borrándolo al terminar.
- Diagnosticar los fallos típicos: contenedor que muere al arrancar, puerto ocupado, permisos en volúmenes, imagen enorme.

## Prerrequisitos

- Cursos 1, 3 y 4 del Módulo Intermedio: Administración de Linux, Bash y Python, Git y GitHub Intermedio.
- Curso 5: Administración de Azure (para ACR; si aún no lo has terminado, basta con saber crear y borrar grupos de recursos).
- VM `lab-so` (Ubuntu LTS) con al menos 2 GB de RAM y 15 GB libres, acceso SSH y `nginx` instalado. Alternativa: WSL2 con Ubuntu. En la propia VM no hace falta Docker Desktop.
- Cuenta gratuita en Docker Hub (se crea en el laboratorio).

## Temario

Containers frente a VMs · Images · Containers · Layers · Dockerfile · Registries · Docker Hub · Azure Container Registry · Volumes · Bind mounts · Networking · Environment variables · Docker Compose · Logs · Troubleshooting.

**Práctica:** containerizar una aplicación sencilla.

## Recursos en español

### Curso Docker Completo — Pelado Nerd (Pablo Fredrikson)
- **URL:** Vídeo: https://youtu.be/CV_Uf3Dq-EU · Repositorio con los materiales de todos sus vídeos: https://github.com/pablokbs/peladonerd
- **Autor / organización:** Pablo Fredrikson (Pelado Nerd), ingeniero SRE y divulgador en español
- **Idioma:** Español
- **Tipo:** Vídeo largo (curso completo) + repositorio
- **Duración aproximada:** ~2 h
- **Cubre:** Contenedores frente a VMs, imágenes, contenedores, capas, Dockerfile, volúmenes, redes, variables de entorno, Compose, registros.
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es el curso de Docker en español con más criterio de operaciones: lo explica alguien que lo usa en producción y va directo a lo que importa. Publicado en 2021: los comandos siguen siendo válidos (usa `docker compose` con espacio en lugar de `docker-compose` con guion, que es la sintaxis moderna). Es el recurso principal en español.

### Vídeos temáticos de Docker: Compose, Networking, Multi Stage Builds y Registry — Pelado Nerd
- **URL:** Docker Compose: https://youtu.be/eoFxMaeB9H4 · Networking: https://youtu.be/BNHNMoSJz4g · Multi Stage Builds: https://youtu.be/62r32R75iZs · Docker Registry: https://youtu.be/stVspIUHP4Q (todos enlazados desde el repositorio anterior, carpeta `docker/`)
- **Autor / organización:** Pablo Fredrikson (Pelado Nerd)
- **Idioma:** Español
- **Tipo:** Vídeos cortos (15-30 min) con código en el repositorio
- **Duración aproximada:** 1,5 h en total
- **Cubre:** Docker Compose, networking, Dockerfile multi-stage, registros privados.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Profundizan justo en las cuatro partes del laboratorio que más cuesta entender leyendo. Míralos después de la documentación oficial de cada tema, no antes.

### Artículos de freeCodeCamp en español sobre Docker
- **URL:** https://www.freecodecamp.org/espanol/news/ (busca "Docker": guía para principiantes, Dockerfile, Docker Compose)
- **Autor / organización:** freeCodeCamp (comunidad, traducciones revisadas)
- **Idioma:** Español
- **Tipo:** Artículos
- **Duración aproximada:** 15-30 min por artículo
- **Cubre:** Conceptos, Dockerfile, Compose.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Complementario, para releer en español un concepto que no haya quedado claro. La documentación oficial en inglés siempre manda sobre estos artículos.

## Recursos en inglés

### Docker Docs: Get started y Docker concepts — Docker
- **URL:** https://docs.docker.com/get-started/ · Qué es un contenedor: https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-a-container/ · Capas de una imagen: https://docs.docker.com/get-started/docker-concepts/building-images/understanding-image-layers/ · Escribir un Dockerfile: https://docs.docker.com/get-started/docker-concepts/building-images/writing-a-dockerfile/ · Persistir datos: https://docs.docker.com/get-started/docker-concepts/running-containers/persisting-container-data/ · Aplicaciones multicontenedor: https://docs.docker.com/get-started/docker-concepts/running-containers/multi-container-applications/ · Visión general: https://docs.docker.com/get-started/docker-overview/
- **Autor / organización:** Docker, Inc.
- **Idioma:** Inglés
- **Tipo:** Documentación oficial con guías paso a paso y vídeos cortos
- **Duración aproximada:** 4-5 h para toda la sección "Docker concepts" (The basics, Building images, Running containers)
- **Cubre:** Todo el temario salvo ACR.
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre (los ejercicios asumen Docker Desktop; en la VM funcionan igual con Docker Engine)
- **Por qué lo recomiendo:** Es el material oficial de introducción y está muy bien secuenciado: cada concepto tiene explicación, un vídeo de 5 minutos y un ejercicio. Es el recurso principal del curso.

### Docker Docs: manuales de Engine, Build y Compose — Docker
- **URL:** Instalar Docker Engine en Ubuntu: https://docs.docker.com/engine/install/ubuntu/ · Buenas prácticas de construcción: https://docs.docker.com/build/building/best-practices/ · Multi-stage: https://docs.docker.com/build/building/multi-stage/ · Volúmenes: https://docs.docker.com/engine/storage/volumes/ · Redes: https://docs.docker.com/engine/network/ · Compose: https://docs.docker.com/compose/
- **Autor / organización:** Docker, Inc.
- **Idioma:** Inglés
- **Tipo:** Documentación oficial de referencia
- **Duración aproximada:** 4-6 h para las páginas listadas aquí y en "Documentación oficial"
- **Cubre:** Dockerfile, capas, volúmenes, bind mounts, redes, variables de entorno, Compose, logs, troubleshooting.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Cuando "Docker concepts" te ha dado la idea, aquí está el detalle exacto: cada opción de `docker run`, cada instrucción de Dockerfile, cada clave de Compose. La página de buenas prácticas de construcción es lectura obligatoria antes de escribir tu Dockerfile.

### Play with Docker — Docker (comunidad)
- **URL:** https://labs.play-with-docker.com/
- **Autor / organización:** Docker (proyecto de código abierto mantenido por la comunidad)
- **Idioma:** Inglés
- **Tipo:** Entorno Docker en el navegador, sesiones de 4 horas
- **Duración aproximada:** Uso libre
- **Cubre:** Práctica de cualquier parte del temario sin instalar nada.
- **Nivel:** Todos
- **Acceso:** Libre; requiere cuenta de Docker Hub
- **Por qué lo recomiendo:** Para probar un comando o una red de varios nodos sin tocar tu VM. Útil también si tu equipo es poco potente. No sustituye al laboratorio en `lab-so`.

### Repositorios oficiales: getting-started y awesome-compose — Docker
- **URL:** https://github.com/docker/getting-started · https://github.com/docker/awesome-compose
- **Autor / organización:** Docker, Inc.
- **Idioma:** Inglés
- **Tipo:** Código de ejemplo
- **Duración aproximada:** 1-2 h para leer tres o cuatro ejemplos de `awesome-compose` (por ejemplo `nginx-flask-mongo`, `nginx-golang-postgres`, `react-express-mysql`)
- **Cubre:** Dockerfile, Compose, redes, volúmenes en aplicaciones reales de varios servicios.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** `awesome-compose` es la mejor colección de archivos Compose bien hechos: cuando dudes de cómo estructurar el tuyo, mira cómo lo hace un ejemplo parecido. Lee, no copies: el laboratorio exige que entiendas cada línea.

### Especificaciones OCI (solo referencia) — Open Container Initiative
- **URL:** Formato de imagen: https://github.com/opencontainers/image-spec · Runtime: https://github.com/opencontainers/runtime-spec · Distribución (registros): https://github.com/opencontainers/distribution-spec
- **Autor / organización:** Open Container Initiative (Linux Foundation)
- **Idioma:** Inglés
- **Tipo:** Especificaciones técnicas
- **Duración aproximada:** 30 min para leer los README y hojear el `image-spec`
- **Cubre:** Images, layers, registries: qué es realmente una imagen por dentro.
- **Nivel:** Avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** Solo para entender que "imagen Docker" es en realidad "imagen OCI": un manifiesto JSON, una configuración y capas comprimidas, y por eso la misma imagen funciona con Docker, Podman, containerd y Kubernetes. No hace falta leerlas enteras.

## Documentación oficial

- **Instalación:** Docker Engine en Ubuntu (repositorio oficial de Docker, no snap) https://docs.docker.com/engine/install/ubuntu/ · pasos posteriores (grupo `docker`, arranque) https://docs.docker.com/engine/install/linux-postinstall/
- **Imágenes y Dockerfile:** referencia de Dockerfile https://docs.docker.com/reference/dockerfile/ · buenas prácticas https://docs.docker.com/build/building/best-practices/ · multi-stage https://docs.docker.com/build/building/multi-stage/ · caché de construcción https://docs.docker.com/build/cache/ · contexto y `.dockerignore` https://docs.docker.com/build/concepts/context/
- **Contenedores:** referencia de `docker run` https://docs.docker.com/engine/containers/run/ · políticas de reinicio https://docs.docker.com/engine/containers/start-containers-automatically/ · logs https://docs.docker.com/engine/logging/ · referencia de la CLI https://docs.docker.com/reference/
- **Almacenamiento:** visión general https://docs.docker.com/engine/storage/ · volúmenes https://docs.docker.com/engine/storage/volumes/ · bind mounts https://docs.docker.com/engine/storage/bind-mounts/
- **Redes:** visión general https://docs.docker.com/engine/network/ · driver bridge https://docs.docker.com/engine/network/drivers/bridge/
- **Compose:** manual https://docs.docker.com/compose/ · primeros pasos https://docs.docker.com/compose/gettingstarted/ · modelo de aplicación https://docs.docker.com/compose/intro/compose-application-model/ · variables de entorno https://docs.docker.com/compose/how-tos/environment-variables/ · redes en Compose https://docs.docker.com/compose/how-tos/networking/ · orden de arranque https://docs.docker.com/compose/how-tos/startup-order/ · referencia del archivo Compose https://docs.docker.com/reference/compose-file/
- **Registros:** Docker Hub https://docs.docker.com/docker-hub/ · inicio rápido https://docs.docker.com/docker-hub/quickstart/ · repositorios https://docs.docker.com/docker-hub/repos/ · límites de descarga https://docs.docker.com/docker-hub/usage/ · Azure Container Registry: busca "Container Registry" en el portal de documentación de Azure https://learn.microsoft.com/es-es/azure/ y usa la referencia de `az acr` en https://learn.microsoft.com/en-us/cli/azure/reference-index
- **Seguridad y diagnóstico:** seguridad de Engine https://docs.docker.com/engine/security/ · modo rootless https://docs.docker.com/engine/security/rootless/ · troubleshooting del daemon https://docs.docker.com/engine/daemon/troubleshoot/
- **Azure Container Instances** (opcional, para ejecutar la imagen en la nube unos minutos): https://learn.microsoft.com/es-es/azure/container-instances/container-instances-overview

## Ruta recomendada de estudio

1. **Leer** "Docker overview" y "What is a container?" y hacer los ejercicios de "The basics" en Docker concepts (1,5 h). Debes poder explicar contenedor frente a VM sin decir "es una VM ligera".
2. **Hacer** la Parte A del laboratorio (instalar Docker Engine en `lab-so`) siguiendo la documentación oficial de instalación (1 h).
3. **Ver** el Curso Docker Completo de Pelado Nerd con la VM abierta, repitiendo los comandos (2 h).
4. **Hacer** "Building images" de Docker concepts (capas, Dockerfile, caché, multi-stage, publicar) y **leer** las buenas prácticas de construcción y la página de `.dockerignore` (3 h). **Hacer las Partes B y C.**
5. **Hacer** "Running containers" de Docker concepts (puertos, variables, persistencia, multicontenedor) y **leer** volúmenes, bind mounts y redes bridge (2,5 h). **Hacer las Partes D y E.**
6. **Ver** los vídeos de Networking y Multi Stage de Pelado Nerd (45 min) para afianzar.
7. **Leer** el manual de Compose (modelo de aplicación, variables, redes, orden de arranque) y dos ejemplos de `awesome-compose` (2 h). **Ver** el vídeo de Compose (30 min). **Hacer la Parte F.**
8. **Leer** Docker Hub quickstart y límites de descarga, y la referencia de `az acr` (45 min). **Ver** el vídeo de Registry (20 min). **Hacer la Parte G.**
9. **Leer** logging, troubleshooting del daemon y seguridad de Engine (1 h). **Hacer las Partes H e I.**
10. **Responder la evaluación** y **revisar el checklist**.

Si vas justo de tiempo: obligatorios los puntos 1, 2, 4, 5, 7, 8 y 9. Los vídeos son refuerzo.

## Laboratorio

### Objetivo

Crear **la aplicación del curso de Docker** (una API Python con `/health` y `/`), containerizarla con un Dockerfile de calidad, operarla (logs, exec, capas, volúmenes, redes, variables), componerla con Redis y nginx en Docker Compose, publicarla en Docker Hub y en Azure Container Registry, y practicar el diagnóstico de los cuatro fallos más comunes. Todo en la VM `lab-so`.

### Requisitos

- VM `lab-so` con Ubuntu LTS, acceso SSH desde el anfitrión, `nginx` instalado (lo usaremos para provocar un conflicto de puerto) y salida a Internet.
- Cuenta de Docker Hub (gratuita, plan Personal) y cuenta de Azure.
- Repositorio Git **nuevo** `api-curso` en tu GitHub (público) donde vivirá la aplicación: lo reutilizarás en CI/CD, Kubernetes y Helm. Trabaja con ramas y PRs como en el curso anterior.
- Documenta en `laboratorio-docker.md` cada comando y su salida relevante.

> **Sobre el coste.** Todo el laboratorio es gratuito salvo la Parte G en Azure: Azure Container Registry **Basic** cuesta alrededor de 0,17 USD por día (unos 5 USD/mes) más almacenamiento por encima de 10 GB; créalo, úsalo y **bórralo el mismo día**: coste esperado inferior a 0,50 USD. Si además ejecutas la imagen en Azure Container Instances unos minutos, son céntimos. Docker Hub Personal es gratuito (repositorios públicos ilimitados, un privado, con límite de descargas por hora).

### Instrucciones

**Parte A — Instalar Docker Engine (45 min)**

1. En `lab-so`, sigue **exactamente** la guía oficial "Install Docker Engine on Ubuntu" con el método del repositorio `apt` (no uses `snap install docker` ni el paquete `docker.io` de Ubuntu: explica por qué la guía lo desaconseja). Instala `docker-ce`, `docker-ce-cli`, `containerd.io`, `docker-buildx-plugin` y `docker-compose-plugin`.
2. Pasos posteriores: añade tu usuario al grupo `docker` (`sudo usermod -aG docker $USER`, cierra sesión y vuelve), comprueba `docker version`, `docker info | head -30` y `docker run --rm hello-world`. Explica qué implica en seguridad pertenecer al grupo `docker` (equivale a root en el host) y qué es el modo rootless.
3. Explora la arquitectura: `systemctl status docker containerd`, `ps -ef | grep -E "dockerd|containerd"`, `ls -l /var/run/docker.sock`. Explica cliente, daemon, containerd, runc, y por qué `docker` sin sudo funciona ahora.

**Parte B — La aplicación del curso (45 min)**

4. Crea el repositorio `api-curso` con esta estructura y **este código** (cópialo tal cual; lo entenderás línea a línea en la Parte C):
   ```
   api-curso/
   ├── app/
   │   ├── app.py
   │   ├── requirements.txt
   │   ├── Dockerfile
   │   └── .dockerignore
   ├── nginx/
   │   └── default.conf
   ├── compose.yaml
   ├── .env.example
   └── README.md
   ```
   `app/app.py`:
   ```python
   import os
   import socket

   from flask import Flask, jsonify

   app = Flask(__name__)
   APP_VERSION = os.getenv("APP_VERSION", "0.1.0")
   APP_ENV = os.getenv("APP_ENV", "dev")
   REDIS_HOST = os.getenv("REDIS_HOST")


   def contar_visita():
       """Incrementa un contador en Redis si está configurado; si no, devuelve None."""
       if not REDIS_HOST:
           return None
       try:
           import redis
           r = redis.Redis(host=REDIS_HOST, port=int(os.getenv("REDIS_PORT", "6379")),
                           socket_connect_timeout=1)
           return r.incr("visitas")
       except Exception as exc:  # noqa: BLE001
           return f"redis no disponible: {exc.__class__.__name__}"


   @app.get("/")
   def raiz():
       return jsonify(app="api-curso", version=APP_VERSION, env=APP_ENV,
                      hostname=socket.gethostname(), visitas=contar_visita())


   @app.get("/health")
   def health():
       return jsonify(status="ok"), 200


   if __name__ == "__main__":
       app.run(host="0.0.0.0", port=8000)
   ```
   `app/requirements.txt`:
   ```
   flask>=3,<4
   gunicorn>=22,<24
   redis>=5,<7
   ```
5. Pruébala **sin Docker** en la VM: `python3 -m venv .venv && source .venv/bin/activate && pip install -r app/requirements.txt && python app/app.py`, y desde otra terminal `curl -s localhost:8000/ ; curl -s -i localhost:8000/health`. Anota qué devuelve `hostname` (el de la VM). Esto es lo que vas a meter en un contenedor. Para el venv y añade `.venv/` al `.gitignore`.

**Parte C — Dockerfile con buenas prácticas, construir y ejecutar (2 h)**

6. Escribe `app/Dockerfile` (multi-stage: la etapa `builder` instala dependencias, la final solo copia lo instalado):
   ```dockerfile
   # syntax=docker/dockerfile:1
   FROM python:3.12-slim AS builder
   WORKDIR /app
   COPY requirements.txt .
   RUN pip install --no-cache-dir --prefix=/install -r requirements.txt

   FROM python:3.12-slim
   ENV PYTHONDONTWRITEBYTECODE=1 PYTHONUNBUFFERED=1 APP_VERSION=0.1.0
   RUN groupadd -r app && useradd -r -g app -d /app -s /sbin/nologin app
   WORKDIR /app
   COPY --from=builder /install /usr/local
   COPY app.py .
   USER app
   EXPOSE 8000
   HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
     CMD python -c "import urllib.request,sys; sys.exit(0 if urllib.request.urlopen('http://127.0.0.1:8000/health', timeout=2).status == 200 else 1)"
   CMD ["gunicorn", "--bind", "0.0.0.0:8000", "--workers", "2", "app:app"]
   ```
   y `app/.dockerignore` con `.venv`, `__pycache__/`, `*.pyc`, `.git`, `.env`, `*.md`. Explica **cada instrucción**: por qué `slim` y no `python:3.12` ni `alpine` (compatibilidad de wheels), por qué `requirements.txt` se copia antes que `app.py` (caché), qué hace `--no-cache-dir`, por qué un usuario no root, qué diferencia hay entre `EXPOSE` y `-p`, por qué `HEALTHCHECK` usa Python y no `curl`, y por qué `CMD` en forma exec y con gunicorn en vez de `python app.py`.
7. Construye y observa las capas:
   ```bash
   cd app && docker build -t api-curso:0.1.0 .
   docker images api-curso
   docker history api-curso:0.1.0
   docker image inspect api-curso:0.1.0 --format '{{json .Config}}' | python3 -m json.tool
   ```
   Cambia una línea de `app.py`, reconstruye y fíjate en qué pasos dicen `CACHED`. Cambia `requirements.txt` y observa la diferencia. Explica cómo funciona la caché de capas.
8. Ejecuta y opera:
   ```bash
   docker run -d --name api -p 8000:8000 -e APP_ENV=lab --memory 128m --cpus 0.5 --restart unless-stopped api-curso:0.1.0
   curl -s localhost:8000/ | python3 -m json.tool      # hostname = ID del contenedor
   docker ps; docker logs -f api                        # Ctrl+C para salir
   docker exec -it api sh -c 'id; ps -ef; env | sort; cat /etc/os-release'
   docker stats --no-stream api
   docker inspect api --format '{{.State.Health.Status}} {{.NetworkSettings.IPAddress}} {{.HostConfig.Memory}}'
   ```
   Explica: por qué el `hostname` ya no es el de la VM, qué usuario ejecuta gunicorn, por qué `ps -ef` dentro solo ve dos o tres procesos, qué muestra `docker stats` y dónde están esos límites en el host (`cgroups`: `cat /sys/fs/cgroup/system.slice/docker-<id>.scope/memory.max`).
9. Ciclo de vida: `docker stop api` (observa que tarda hasta 10 s: explica SIGTERM y SIGKILL), `docker start api`, `docker restart api`, `docker rm -f api`. Comprueba con `docker ps -a` qué queda. Ejecuta `docker run --rm -it api-curso:0.1.0 sh` y explica `--rm` e `-it`.

**Parte D — Volúmenes y bind mounts (1 h)**

10. Ejecuta Redis con un **volumen con nombre**: `docker volume create redis-data && docker run -d --name redis -v redis-data:/data redis:7-alpine redis-server --appendonly yes`. Escribe una clave (`docker exec redis redis-cli set curso docker`), borra el contenedor, crea otro con el mismo volumen y comprueba que la clave sigue. `docker volume inspect redis-data`: ¿dónde vive en el host? Explica por qué los datos deben ir en volúmenes y no en la capa de escritura del contenedor.
11. **Bind mount** para desarrollo: `docker run -d --name api-dev -p 8001:8000 -v "$PWD/app:/app:ro" api-curso:0.1.0`. Edita `app.py` en el host y explica por qué el contenedor no refleja el cambio hasta reiniciarlo (gunicorn ya cargó el código; qué opción lo recargaría). Compara volumen frente a bind mount: cuándo usar cada uno, portabilidad, permisos, rendimiento.
12. Permisos: crea en el host `mkdir datos && sudo chown root:root datos && chmod 755 datos`, ejecuta `docker run --rm -v "$PWD/datos:/datos" api-curso:0.1.0 sh -c 'touch /datos/prueba'` y explica el `Permission denied` (UID del usuario `app` dentro frente a propietario fuera). Da dos soluciones (ajustar propietario al UID, o usar `--user`) y explica por qué en un volumen con nombre esto no suele pasar.

**Parte E — Redes (1 h)**

13. Redes por defecto: `docker network ls`, `docker network inspect bridge`. Lanza dos contenedores en la red `bridge` por defecto e intenta que se resuelvan por nombre (`docker exec api ping -c1 redis` o `getent hosts redis`): falla. Explica por qué la red bridge por defecto no tiene DNS entre contenedores.
14. Red propia: `docker network create --driver bridge red-curso`, arranca `redis` y `api` con `--network red-curso` y la variable `-e REDIS_HOST=redis`. Comprueba `curl localhost:8000/` varias veces: el contador `visitas` aumenta. Desde `api`, `getent hosts redis` resuelve. Explica el DNS embebido de Docker (127.0.0.11), qué es una red bridge en el host (`ip a` muestra `br-xxxx` y `veth`), qué hace `-p` a nivel de `iptables`/`nftables` (`sudo iptables -t nat -L DOCKER -n`) y por qué Redis **no** necesita `-p` para que la API lo use.
15. Aislamiento: crea `red-otra`, pon un tercer contenedor y demuestra que no alcanza a `redis`. Explica cómo usarías esto para separar frontend y base de datos. Menciona `--network host` y `none` y cuándo tienen sentido.

**Parte F — Docker Compose: API + Redis + nginx (2 h)**

16. Escribe `compose.yaml` en la raíz del repositorio:
    ```yaml
    services:
      api:
        build: ./app
        image: api-curso:0.1.0
        environment:
          APP_ENV: ${APP_ENV:-compose}
          REDIS_HOST: redis
        expose:
          - "8000"
        depends_on:
          redis:
            condition: service_healthy
        restart: unless-stopped
      redis:
        image: redis:7-alpine
        command: ["redis-server", "--appendonly", "yes"]
        volumes:
          - redis-data:/data
        healthcheck:
          test: ["CMD", "redis-cli", "ping"]
          interval: 5s
          timeout: 3s
          retries: 5
      proxy:
        image: nginx:1.27-alpine
        ports:
          - "8080:80"
        volumes:
          - ./nginx/default.conf:/etc/nginx/conf.d/default.conf:ro
        depends_on:
          - api
    volumes:
      redis-data:
    ```
    y `nginx/default.conf`:
    ```nginx
    upstream api {
        server api:8000;
    }
    server {
        listen 80;
        location / {
            proxy_pass http://api;
            proxy_set_header Host $host;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        }
    }
    ```
    Crea `.env.example` con `APP_ENV=compose` y explica la diferencia entre `.env` (lo lee Compose para sustituir `${...}`), `environment:` y `env_file:` (llegan al contenedor). Añade `.env` al `.gitignore`.
17. `docker compose up -d --build`, `docker compose ps`, `docker compose logs -f api`, `curl -s localhost:8080/` (a través de nginx). Explica: la red que Compose creó (`docker network ls`), por qué `api` usa `expose` y no `ports`, qué hace `depends_on` con `condition: service_healthy` y qué **no** garantiza `depends_on` a secas.
18. Escala la API: `docker compose up -d --scale api=3 && docker compose restart proxy`; ejecuta `for i in $(seq 1 6); do curl -s localhost:8080/ | python3 -c 'import sys,json; print(json.load(sys.stdin)["hostname"])'; done` y observa que el `hostname` cambia: nginx reparte entre las tres réplicas. Explica cómo lo consigue (DNS de Docker devuelve varias IPs) y por qué es la misma idea que el Load Balancer del curso de Azure.
19. `docker compose down` y comprueba que el volumen `redis-data` sigue (`docker volume ls`); `docker compose down -v` lo borra. Explica cuándo usar cada uno. Haz commit de todo al repositorio mediante PR.

**Parte G — Registros: Docker Hub y Azure Container Registry (1,5 h)**

20. Docker Hub: crea la cuenta, un repositorio público `api-curso` y un **token de acceso** (no uses la contraseña). `docker login -u <usuario>`, etiqueta y publica:
    ```bash
    docker tag api-curso:0.1.0 <usuario>/api-curso:0.1.0
    docker tag api-curso:0.1.0 <usuario>/api-curso:latest
    docker push <usuario>/api-curso:0.1.0 && docker push <usuario>/api-curso:latest
    ```
    Comprueba en la web las capas y el `digest`. Explica el formato `registro/usuario/repo:tag`, por qué `latest` es solo una etiqueta más (y peligrosa en producción), y qué es un digest `sha256:...`. Borra la imagen local y haz `docker pull` por digest.
21. Azure Container Registry: `az group create -n rg-acr-lab -l <region> --tags course=docker`, `az acr create -g rg-acr-lab -n acrcurso<sufijo> --sku Basic`, `az acr login -n acrcurso<sufijo>`, etiqueta como `acrcurso<sufijo>.azurecr.io/api-curso:0.1.0`, `docker push`, `az acr repository show-tags -n acrcurso<sufijo> --repository api-curso`. Explica la diferencia entre un registro público y uno privado, cómo se autentica ACR (Entra ID, tokens, identidad administrada más adelante) y qué SKUs hay. **Opcional:** ejecuta la imagen 5 minutos en Azure Container Instances (`az container create ... --image acrcurso<sufijo>.azurecr.io/api-curso:0.1.0 --ports 8000 --ip-address Public` con credenciales de administrador de ACR habilitadas temporalmente), `curl` a su IP, y bórrala. **Borra el grupo `rg-acr-lab` el mismo día** y comprueba en Cost Management al día siguiente.

**Parte H — Troubleshooting provocado (1,5 h)**

22. **Contenedor que muere al arrancar.** `docker run -d --name roto api-curso:0.1.0 gunicorn app:noexiste`. `docker ps` no lo muestra; `docker ps -a` sí. Diagnostica con `docker logs roto`, `docker inspect roto --format '{{.State.ExitCode}} {{.State.Error}}'` y explica el código de salida. Repite con `docker run -d --name roto2 -e REDIS_HOST=redis-inexistente ...` y comprueba que la API **no** muere (el código lo tolera): reflexiona sobre qué debe hacer una aplicación cuando falta una dependencia.
23. **Puerto ocupado.** `docker run -d --name web -p 80:80 nginx:alpine` con el nginx de la VM escuchando en 80. Lee el error, usa `sudo ss -ltnp | grep :80` para encontrar al culpable y resuélvelo de dos formas (otro puerto del host, o parar el servicio). Explica por qué el puerto del **contenedor** no choca con nada.
24. **Permisos en volúmenes.** Repite el caso del paso 12 pero con Compose: monta `./logs:/app/logs` y haz que la API intente escribir ahí. Documenta el error y la solución que elijas.
25. **Imagen enorme.** Construye una variante `Dockerfile.gordo` con `FROM python:3.12` (sin slim), sin `.dockerignore`, con `.venv` dentro del contexto y con `RUN apt-get update && apt-get install -y build-essential` en la imagen final. Compara `docker images` y `docker history` de ambas y explica de dónde salen los megas y cómo los quitó tu Dockerfile bueno (multi-stage, slim, `.dockerignore`, `--no-cache-dir`, no instalar compiladores en la imagen final).
26. Limpieza y espacio: `docker system df`, `docker image prune`, `docker container prune`, `docker system prune` (lee bien qué borra cada uno). Explica dónde viven las imágenes en el host (`docker info | grep "Docker Root Dir"`) y por qué en un servidor de CI el disco se llena.

**Parte I — Consolidación (30 min)**

27. Escribe en el `README.md` del repositorio `api-curso` cómo construir, ejecutar, configurar (variables) y probar la aplicación, y qué endpoints tiene. Este README lo leerán los cursos siguientes.
28. Tabla **Docker ↔ VM ↔ Azure**: al menos 10 filas relacionando conceptos (imagen ↔ plantilla de VM ↔ imagen de galería; volumen ↔ disco de datos ↔ disco administrado; red bridge ↔ vSwitch ↔ VNet; `-p` ↔ NAT ↔ IP pública/NSG; HEALTHCHECK ↔ sonda del LB; registro ↔ ISO ↔ ACR; límites cgroups ↔ tamaño de VM, etc.).

### Resultado esperado

- Repositorio `api-curso` público con la aplicación, `Dockerfile`, `.dockerignore`, `compose.yaml`, `nginx/default.conf`, `.env.example` y README, construido mediante PRs.
- Imagen `api-curso:0.1.0` publicada en Docker Hub (queda) y en ACR (borrado tras la prueba).
- `laboratorio-docker.md` con las partes A-I, salidas de comandos y explicaciones propias.
- `lab-so` con Docker Engine operativo para los cursos de CI/CD y Kubernetes.

### Criterios de validación

- [ ] Docker Engine instalado desde el repositorio oficial; el usuario opera sin `sudo` y explica la implicación de seguridad.
- [ ] La aplicación responde en `/` (versión, entorno, hostname, visitas) y en `/health`, primero sin Docker y después en contenedor.
- [ ] El Dockerfile cumple: multi-stage, imagen slim, orden que aprovecha caché, `.dockerignore`, usuario no root, `HEALTHCHECK`, `CMD` exec con gunicorn; cada instrucción está explicada y el comportamiento de la caché demostrado.
- [ ] `docker history`, `inspect`, `stats`, `logs` y `exec` están usados y explicados; los límites de recursos se localizan en cgroups.
- [ ] La persistencia con volumen sobrevive al borrado del contenedor; el bind mount y el problema de permisos están demostrados y resueltos.
- [ ] Dos contenedores se comunican por nombre en una red bridge propia y el aislamiento entre redes está probado; el DNS embebido y `-p` están explicados.
- [ ] Compose levanta API + Redis + nginx, el contador de visitas funciona a través del proxy y el escalado a 3 réplicas reparte peticiones.
- [ ] La imagen está en Docker Hub con tag y digest, y estuvo en ACR con el grupo borrado el mismo día (captura de coste al día siguiente).
- [ ] Los cuatro fallos provocados están diagnosticados con los comandos correctos y explicados.
- [ ] En una llamada con el mentor, el estudiante explica su Dockerfile línea a línea y diagnostica en vivo un contenedor que no arranca.

## Entrega

En tu repositorio de entregas, carpeta `02-modulo-intermedio/06-docker-y-contenedores/`, mediante Pull Request:

1. `laboratorio-docker.md` con enlaces al repositorio `api-curso`, a la imagen en Docker Hub y a los PRs.
2. `Dockerfile.gordo` y la comparación de tamaños.
3. `capturas/` (Docker Hub con las capas, ACR con la etiqueta, Cost Management del día siguiente).
4. `ENTREGA.md` con evaluación, checklist y uso de IA.

El código de la aplicación **no** se copia en la entrega: vive en `api-curso`. Nunca subas `.env` ni tokens de Docker Hub o de ACR.

## Evaluación

1. **Conceptual.** Explica qué es un contenedor sin usar la palabra "virtual". ¿Qué comparte con el host y qué aísla? ¿Por qué un contenedor de Ubuntu arranca en un segundo y una VM de Ubuntu en un minuto?
2. **Conceptual.** Diferencia imagen, capa y contenedor. Si diez contenedores usan la misma imagen, ¿cuánto disco ocupan sus capas de solo lectura? ¿Dónde van los archivos que escribe cada uno?
3. **Técnica.** Un Dockerfile copia todo el proyecto (`COPY . .`) y luego instala dependencias. Cada cambio en el código reinstala todo. Explica por qué y reescribe el orden para aprovechar la caché.
4. **Situacional.** Un compañero propone `FROM ubuntu:24.04` e instalar Python con `apt` para "tener más control". Argumenta a favor de `python:3.12-slim`: tamaño, superficie de ataque, actualizaciones, compatibilidad de wheels. ¿Cuándo tendría razón él?
5. **Técnica.** ¿Qué diferencia hay entre `EXPOSE 8000` y `-p 8000:8000`? ¿Y entre `CMD` y `ENTRYPOINT`? ¿Por qué `CMD ["gunicorn", ...]` (forma exec) recibe bien la señal de `docker stop` y `CMD gunicorn ...` (forma shell) puede no hacerlo?
6. **Troubleshooting.** `docker run -d` devuelve un ID pero `docker ps` no muestra nada. Enumera los tres comandos que ejecutas y qué buscas en cada salida. Da tres causas típicas.
7. **Conceptual.** Volumen con nombre frente a bind mount: cuándo usar cada uno y por qué un bind mount de código es cómodo en desarrollo y una mala idea en producción.
8. **Troubleshooting.** La API en un contenedor no root escribe en `/app/logs`, montado desde `./logs` del host, y recibe `Permission denied`. Explica la causa (UID/GID) y dos soluciones, con sus inconvenientes.
9. **Técnica.** Dos contenedores en la red bridge por defecto no se resuelven por nombre; en una red creada por ti, sí. Explica qué componente lo hace posible y qué IP tiene. ¿Por qué Redis no necesita `-p` para que la API lo use?
10. **Situacional.** En Compose, `api` arranca antes que la base de datos y falla al conectar, aunque tiene `depends_on`. Explica qué garantiza y qué no `depends_on`, y las dos formas de arreglarlo (healthcheck con `condition`, reintentos en la aplicación). ¿Cuál es más robusta y por qué?
11. **Conceptual.** ¿Por qué desplegar `miapp:latest` en producción es peligroso? ¿Qué es un digest y cómo garantiza que despliegas exactamente lo que probaste? Propón una convención de etiquetas para la aplicación del curso.
12. **Situacional.** Tu imagen pesa 1,2 GB y el pipeline tarda 10 minutos en subirla. Enumera cinco medidas para reducirla y estima cuál ahorra más.
13. **Técnica.** Explica qué hace `HEALTHCHECK`, qué estados puede tener un contenedor y cómo lo usará Compose (y después Kubernetes y el Load Balancer de Azure) para decidir si envía tráfico.
14. **Situacional.** Un servidor de CI se queda sin disco cada dos semanas. ¿Qué está pasando con Docker, cómo lo compruebas (`docker system df`) y qué limpieza programarías sin borrar lo que se usa?
15. **Reflexión.** ¿Qué te sorprendió más al meter la aplicación en un contenedor? ¿Qué parte de tu Dockerfile cambiarías si la aplicación fuera a producción mañana?

## Checklist final

Antes de continuar, deberías poder:

- [ ] Explicar contenedor frente a VM y qué son namespaces, cgroups y el sistema de archivos por capas.
- [ ] Instalar Docker Engine en Ubuntu desde el repositorio oficial y explicar la arquitectura cliente/daemon/containerd/runc.
- [ ] Escribir un Dockerfile con imagen slim, caché bien aprovechada, `.dockerignore`, usuario no root, `HEALTHCHECK` y multi-stage.
- [ ] Construir, etiquetar, ejecutar, inspeccionar (`history`, `inspect`, `stats`) y operar (`logs`, `exec`, `stop`, `rm`) contenedores.
- [ ] Persistir datos con volúmenes y bind mounts y resolver problemas de permisos.
- [ ] Conectar contenedores por nombre en redes bridge propias y explicar el DNS embebido y el mapeo de puertos.
- [ ] Describir y operar una aplicación de varios servicios con Docker Compose, con healthchecks, variables y escalado.
- [ ] Publicar imágenes en Docker Hub y en ACR con tags y digests, y borrar el registro de Azure al terminar.
- [ ] Diagnosticar un contenedor que muere, un puerto ocupado, un problema de permisos y una imagen enorme.
- [ ] Tener la aplicación del curso de Docker en un repositorio propio, lista para CI/CD, Kubernetes y Helm.

---

*Recursos verificados el 2026-09-27 mediante búsqueda web (existencia y vigencia de las URLs). Los precios de ACR y ACI son aproximados: la calculadora de Azure manda. Si un enlace falla, abre un issue en este repositorio.*
