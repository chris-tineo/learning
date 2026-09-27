# Kubernetes Avanzado

> Módulo: Avanzado · Curso 1 de 12 · Duración estimada: 45-60 horas · Estado: ✅ Completo

## Objetivo

En el Módulo Intermedio empaquetaste la aplicación del curso de Docker en una imagen, la publicaste en un registro, la desplegaste con un pipeline y la vigilaste con Azure Monitor. Todo eso funcionaba con un contenedor, en una máquina. Kubernetes es lo que pasa cuando necesitas que funcionen cincuenta contenedores, en veinte máquinas, que se reinicien solos cuando fallan, que se actualicen sin cortar el servicio y que crezcan cuando llega tráfico. Es la plataforma estándar de la industria para operar contenedores, y AKS, EKS y GKE son la misma cosa con distinta factura.

Este curso no es "kubectl para principiantes". Vas a desplegar la aplicación del curso de Docker de forma **completa**: con réplicas, actualizaciones progresivas y vuelta atrás, configuración y secretos, entrada HTTP con TLS, una base de datos con almacenamiento persistente, sondas de salud, límites de recursos, autoescalado y reglas de dónde puede o no puede ejecutarse cada cosa. Y, sobre todo, vas a **romperlo a propósito** una y otra vez para aprender a leer lo que Kubernetes te cuenta cuando algo va mal. Esa batería de troubleshooting es lo que distingue a quien ha hecho un tutorial de quien puede estar de guardia.

El laboratorio principal se hace en un clúster local de varios nodos (kind sobre Docker, minikube multinodo o k3s en dos VMs). No cuesta nada y puedes destruirlo y recrearlo en un minuto. Al final hay una sección opcional y acotada en **AKS** con un solo nodo para que veas qué cambia cuando el clúster lo gestiona Azure. El Proyecto Final sí usará AKS, así que lo que aprendas aquí lo vas a necesitar.

**Antes de empezar** necesitas la aplicación del curso de Docker con su imagen publicada y accesible (por ejemplo en GitHub Container Registry), Docker funcionando en tu equipo o en la VM `lab-so`, y soltura con YAML y la terminal. Si la imagen es privada, prepara un token de solo lectura: lo usarás para crear un Secret de tipo `docker-registry`.

### Al terminar este curso deberías poder

- Explicar la arquitectura de Kubernetes: qué hace cada componente del control plane (API server, etcd, scheduler, controller manager) y de los nodos (kubelet, kube-proxy, runtime), y qué pasa por dentro cuando ejecutas `kubectl apply`.
- Desplegar una aplicación con Deployment y ReplicaSet, hacer un rolling update, observarlo y revertirlo con `kubectl rollout`.
- Exponerla con Services de tipo ClusterIP, NodePort y LoadBalancer y explicar cuándo se usa cada uno y cómo funciona el DNS interno.
- Inyectar configuración con ConfigMaps y Secrets como variables de entorno y como archivos montados, y explicar qué protege realmente un Secret y qué no.
- Publicar la aplicación por HTTP/HTTPS con un Ingress y el controlador ingress-nginx, con certificado TLS.
- Desplegar PostgreSQL como StatefulSet con PersistentVolumeClaim y explicar la relación entre PV, PVC y StorageClass.
- Configurar readiness, liveness y startup probes, requests y limits, y explicar las clases de QoS y por qué un Pod es expulsado o reiniciado.
- Autoescalar con HPA a partir de métricas de CPU y controlar dónde se programan los Pods con nodeSelector, affinity/anti-affinity, taints y tolerations.
- Diagnosticar los fallos más habituales (CrashLoopBackOff, ImagePullBackOff, Pending, probes mal configuradas, Service sin endpoints, DNS) con `kubectl describe`, `logs`, `events`, `exec` y `port-forward`, siguiendo un método.
- Crear y destruir un clúster AKS mínimo con Azure CLI y explicar las diferencias con el clúster local (LoadBalancer real, StorageClass de Azure Disk, coste).

## Prerrequisitos

- Módulo Intermedio completo, en especial: Docker y Contenedores (la aplicación e imagen que vas a desplegar), Administración de Linux, Networking Intermedio, CI/CD y Administración de Azure.
- Docker Desktop o Docker Engine en el anfitrión, o en la VM `lab-so` con al menos 8 GB de RAM asignados si el clúster va dentro de la VM. Alternativa: dos VMs Ubuntu para k3s (servidor y agente).
- `kubectl` instalado en tu equipo y un editor con soporte de YAML (VS Code con la extensión de Kubernetes va bien).
- Cuenta de Azure con presupuesto y alertas activos (solo para la parte opcional de AKS).

## Temario

Arquitectura de Kubernetes · Control Plane · Worker Nodes · Pods · Deployments · ReplicaSets · StatefulSets · DaemonSets · Services · ConfigMaps · Secrets · Ingress · Persistent Volumes · Persistent Volume Claims · Readiness probes · Liveness probes · Resource requests · Resource limits · Autoscaling · Scheduling · Affinity · Taints · Tolerations · Troubleshooting.
**Práctica:** desplegar y operar una aplicación completa en Kubernetes.

## Recursos en español

### Documentación de Kubernetes en español — kubernetes.io/es
- **URL:** https://kubernetes.io/es/docs/ · Conceptos: https://kubernetes.io/es/docs/concepts/ · Tareas: https://kubernetes.io/es/docs/tasks/ · Tutoriales: https://kubernetes.io/es/docs/tutorials/
- **Autor / organización:** Proyecto Kubernetes (CNCF), traducción de la comunidad hispanohablante
- **Idioma:** Español (traducción parcial; las páginas que faltan enlazan a la versión en inglés)
- **Tipo:** Documentación oficial
- **Duración aproximada:** 6-8 h de lectura repartidas a lo largo del curso
- **Cubre:** Arquitectura, Pods, Deployments, ReplicaSets, Services, ConfigMaps, Secrets, volúmenes, scheduling.
- **Nivel:** Intermedio-avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la misma documentación oficial, en español donde existe. Úsala para las páginas de conceptos; para tareas concretas y para todo lo que no esté traducido, salta a la versión en inglés sin miedo. Aprender a leer kubernetes.io es parte del curso.

### Curso de Kubernetes de novato a pro — Pelado Nerd (Pablo Fredrikson)
- **URL:** https://www.youtube.com/watch?v=DCoBcpOA7W4 · Lista de reproducción con el resto de vídeos gratuitos: https://www.youtube.com/playlist?list=PLrb1e2Mp6N_uJSNsV-7SqLFaBdImJsI5x · Repositorio con los manifiestos: https://github.com/pablokbs/peladonerd
- **Autor / organización:** Pablo Fredrikson (Pelado Nerd), SRE, divulgador en español
- **Idioma:** Español
- **Tipo:** Vídeo largo (curso completo) + repositorio
- **Duración aproximada:** ~3 h el vídeo principal
- **Cubre:** Arquitectura, Pods, Deployments, Services, ConfigMaps, Secrets, Ingress, volúmenes, probes, requests/limits, HPA, taints y tolerations, troubleshooting básico.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es el mejor curso en español de Kubernetes hecho por alguien que lo opera en producción. Explica cada objeto y lo despliega en directo con manifiestos que puedes clonar. Publicado en 2021: los conceptos y la API siguen vigentes; si algún comando cambia, manda la documentación oficial.

### Inicio rápido de AKS — Microsoft Learn
- **URL:** Portal (español): https://learn.microsoft.com/es-es/azure/aks/learn/quick-kubernetes-deploy-portal · Azure CLI: https://learn.microsoft.com/en-us/azure/aks/learn/quick-kubernetes-deploy-cli (para la versión en español cambia `en-us` por `es-es` en la URL)
- **Autor / organización:** Microsoft
- **Idioma:** Español e inglés
- **Tipo:** Guía de inicio rápido
- **Duración aproximada:** 30 min
- **Cubre:** Creación de un clúster gestionado, `az aks get-credentials`, despliegue de una aplicación de ejemplo.
- **Nivel:** Intermedio
- **Acceso:** Libre (el clúster que crea tiene coste; en el laboratorio se ajusta a un nodo B-series y se borra al terminar)
- **Por qué lo recomiendo:** Es la guía oficial exacta para la parte opcional del laboratorio. Léela, pero sigue los tamaños y el orden que marca el laboratorio para no gastar más de lo previsto.

## Recursos en inglés

### Introduction to Kubernetes (LFS158) — The Linux Foundation
- **URL:** https://training.linuxfoundation.org/training/introduction-to-kubernetes/
- **Autor / organización:** The Linux Foundation / CNCF
- **Idioma:** Inglés
- **Tipo:** Curso online autoguiado
- **Duración aproximada:** 15-20 h (para este curso, los capítulos de arquitectura, instalación con minikube, objetos de Kubernetes, Services, volúmenes, ConfigMaps/Secrets e Ingress: ~10 h)
- **Cubre:** Arquitectura, control plane y nodos, Pods, Deployments, Services, volúmenes, ConfigMaps, Secrets, Ingress, introducción a escalado y scheduling.
- **Nivel:** Intermedio
- **Acceso:** Gratuito, requiere cuenta gratuita en el portal de formación de la Linux Foundation. El certificado de pago no es necesario.
- **Por qué lo recomiendo:** Es el curso gratuito oficial de la organización que aloja Kubernetes, con la misma estructura que su documentación. Es el recurso teórico principal: da la base ordenada que los vídeos no dan.

### Kubernetes Tutorial for Beginners [FULL COURSE in 4 Hours] — TechWorld with Nana
- **URL:** Canal: https://www.youtube.com/c/techworldwithnana (busca el vídeo por su título; también está enlazado en https://dev.to/techworld_with_nana/full-kubernetes-course-free-24hp )
- **Autor / organización:** Nana Janashia (TechWorld with Nana), CNCF Ambassador
- **Idioma:** Inglés (subtítulos)
- **Tipo:** Vídeo largo
- **Duración aproximada:** ~4 h
- **Cubre:** Arquitectura, Pods, Deployments, Services, Ingress, ConfigMaps, Secrets, volúmenes, StatefulSets, namespaces, y una introducción a Helm que reutilizarás en el curso siguiente.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Los diagramas de Nana sobre cómo se relacionan Service, Pod, Ingress y volúmenes son los más claros que existen en vídeo. Verlo antes de LFS158 hace que la lectura sea mucho más fluida.

### Killercoda: Kubernetes Playgrounds — Killercoda
- **URL:** https://killercoda.com/playgrounds/scenario/kubernetes · Todos los playgrounds: https://killercoda.com/playgrounds
- **Autor / organización:** Killercoda (Kim Wüstkamp, creador de killer.sh)
- **Idioma:** Inglés
- **Tipo:** Entornos de Kubernetes reales en el navegador
- **Duración aproximada:** Sesiones de 60 min (límite del plan gratuito)
- **Cubre:** Práctica libre de todo el temario en un clúster de dos nodos ya creado, con la versión de Kubernetes que usan los exámenes CKA/CKAD.
- **Nivel:** Intermedio-avanzado
- **Acceso:** Gratuito, requiere cuenta gratuita (GitHub, Google o correo)
- **Por qué lo recomiendo:** Para practicar cuando no tengas tu clúster a mano, y para probar cosas que no quieres hacer en el tuyo (romper el kubelet, drenar nodos). Los escenarios gratuitos de la comunidad son un buen repaso antes de la evaluación.

### Kube by Example — Red Hat
- **URL:** https://kubebyexample.com/
- **Autor / organización:** Red Hat Developer
- **Idioma:** Inglés
- **Tipo:** Lecciones cortas con ejemplos ejecutables
- **Duración aproximada:** 3-4 h para los ejemplos de Pods, labels, Deployments, Services, health checks, variables de entorno, volúmenes, Secrets, logging y nodos
- **Cubre:** Los objetos del temario, uno por lección, con el YAML mínimo de cada uno.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Cuando quieras el ejemplo más pequeño posible de un objeto para partir de él, aquí está. Es el complemento perfecto de la documentación oficial, que a veces da ejemplos demasiado completos.

### Introduction to Kubernetes on Azure — Microsoft Learn
- **URL:** https://learn.microsoft.com/en-us/training/paths/intro-to-kubernetes-on-azure/ (para la versión en español cambia `en-us` por `es-es`)
- **Autor / organización:** Microsoft
- **Idioma:** Inglés (disponible en español)
- **Tipo:** Ruta de aprendizaje con módulos y ejercicios
- **Duración aproximada:** 4-5 h
- **Cubre:** Orquestación con Kubernetes, qué añade AKS sobre Kubernetes, despliegue y escalado en AKS.
- **Nivel:** Intermedio
- **Acceso:** Libre, cuenta Microsoft gratuita para guardar progreso. Los ejercicios que crean un clúster real tienen coste: hazlos solo en la parte opcional del laboratorio o léelos sin ejecutarlos.
- **Por qué lo recomiendo:** Es el puente entre el Kubernetes "puro" del clúster local y el AKS del Proyecto Final. Te explica qué partes del control plane gestiona Azure y qué sigue siendo tu responsabilidad.

## Documentación oficial

- **Kubernetes — Documentación (inglés):** https://kubernetes.io/docs/home/ · Concepts: https://kubernetes.io/docs/concepts/ · Tasks: https://kubernetes.io/docs/tasks/ · Tutorials: https://kubernetes.io/docs/tutorials/ · Learn Kubernetes Basics (tutorial interactivo): https://kubernetes.io/docs/tutorials/kubernetes-basics/
- **kubectl Quick Reference (chuleta oficial):** https://kubernetes.io/docs/reference/kubectl/quick-reference
- **Kubernetes — Monitoring, Logging and Debugging:** https://kubernetes.io/docs/tasks/debug/ · Debug Pods: https://kubernetes.io/docs/tasks/debug/debug-application/debug-pods/ · Debug Services: https://kubernetes.io/docs/tasks/debug/debug-application/debug-service/ · Debug Running Pods (`kubectl debug`, contenedores efímeros): https://kubernetes.io/docs/tasks/debug/debug-application/debug-running-pod/
- **kind:** https://kind.sigs.k8s.io/ · Quick Start: https://kind.sigs.k8s.io/docs/user/quick-start/ · Configuración multinodo: https://kind.sigs.k8s.io/docs/user/configuration/ · Ingress en kind: https://kind.sigs.k8s.io/docs/user/ingress/ · LoadBalancer en kind: https://kind.sigs.k8s.io/docs/user/loadbalancer/
- **minikube — Using Multi-Node Clusters:** https://minikube.sigs.k8s.io/docs/tutorials/multi_node/
- **k3s — Quick-Start Guide:** https://docs.k3s.io/quick-start
- **ingress-nginx — Installation Guide:** https://kubernetes.github.io/ingress-nginx/deploy/
- **metrics-server:** https://github.com/kubernetes-sigs/metrics-server
- **Kubernetes The Hard Way** (referencia opcional, no lo hagas en este curso): https://github.com/kelseyhightower/kubernetes-the-hard-way
- **AKS — Storage concepts (StorageClasses de Azure):** https://learn.microsoft.com/en-us/azure/aks/concepts-storage · **Niveles de precio Free y Standard:** https://learn.microsoft.com/en-us/azure/aks/free-standard-pricing-tiers · **AKS en el Azure Architecture Center (por dónde empezar):** https://learn.microsoft.com/en-us/azure/architecture/reference-architectures/containers/aks-start-here

## Ruta recomendada de estudio

1. **Ver** las primeras dos horas del curso de TechWorld with Nana (arquitectura, Pods, Services, Deployments, ConfigMaps/Secrets) sin tocar la terminal, solo para tener el mapa (2 h).
2. **Crear** el clúster local (Parte A del laboratorio) y **hacer** el tutorial interactivo "Learn Kubernetes Basics" de kubernetes.io, pero ejecutándolo en tu clúster en vez de en el navegador (2 h). Al terminar debes poder crear un Deployment, exponerlo y escalarlo con `kubectl`.
3. **Hacer** LFS158, capítulos de arquitectura, componentes del control plane y nodos, y modelo de objetos (3-4 h). Dibuja a mano el recorrido de `kubectl apply -f deployment.yaml` desde tu terminal hasta que el contenedor arranca en un nodo. Ese dibujo va en la entrega.
4. **Leer** en kubernetes.io Concepts: Workloads (Pods, Deployment, ReplicaSet, StatefulSet, DaemonSet) y Services, Load Balancing and Networking (Service, Ingress, DNS) (3 h). **Hacer** las Partes B, C y D del laboratorio.
5. **Ver** los bloques de volúmenes, StatefulSets y probes del curso de Pelado Nerd (1 h) y **leer** Concepts: Storage (Volumes, Persistent Volumes, StorageClasses) y Configuration (ConfigMaps, Secrets). **Hacer** la Parte E.
6. **Leer** Concepts: Configuration → Resource Management for Pods and Containers, Tasks → Configure Liveness, Readiness and Startup Probes y Horizontal Pod Autoscaling (2 h). **Hacer** la Parte F.
7. **Leer** Concepts: Scheduling, Preemption and Eviction (Assigning Pods to Nodes, Taints and Tolerations) (1,5 h). **Hacer** la Parte G.
8. **Leer** entera la sección "Monitoring, Logging and Debugging" → Troubleshooting Applications (1 h) y anota el método. **Hacer** la Parte H, que es la más importante del curso.
9. **Hacer** la ruta "Introduction to Kubernetes on Azure" leyendo los ejercicios sin ejecutarlos (2 h) y, si decides hacer la parte opcional, la **Parte I** en una sola sesión con el temporizador puesto.
10. **Practicar** en Killercoda o Kube by Example los objetos que te hayan costado más (2-3 h, opcional).
11. **Responder la evaluación** y **revisar el checklist**.

Si vas justo de tiempo: haz obligatoriamente los puntos 2, 3, 4, 6 y 8. El resto es refuerzo, salvo la Parte I, que es opcional en cualquier caso.

## Laboratorio

### Objetivo

Desplegar y operar la aplicación del curso de Docker en un clúster Kubernetes local de tres nodos como si fuera un servicio de producción pequeño: réplicas, actualizaciones sin corte, configuración externa, entrada HTTPS, base de datos con almacenamiento persistente, salud, límites, autoescalado y reglas de ubicación. Después, romperlo de forma controlada y diagnosticarlo con método.

### Requisitos

- Docker en funcionamiento y `kind` (recomendado), o `minikube` con soporte multinodo, o dos VMs Ubuntu para `k3s`. Las instrucciones usan kind; si eliges otra opción, anota las diferencias.
- `kubectl`, `curl`, `openssl` y opcionalmente `k9s` (interfaz de terminal, ayuda a ver todo a la vez) y `hey` o `ab` para generar carga.
- La imagen de la aplicación del curso de Docker publicada, con al menos **dos tags** (por ejemplo `1.0.0` y `1.1.0`, la segunda con algún cambio visible en el endpoint de versión). Si no la tienes con dos versiones, publica una segunda ahora desde tu pipeline.
- Convención: todos los manifiestos van en una carpeta `k8s/` de tu repositorio de la aplicación (o de entregas), un archivo por objeto, en el namespace `curso`. Documenta en `laboratorio-k8s.md` los comandos, las salidas relevantes y lo que aprendiste en cada parte.

> **Sobre el coste.** Las Partes A a H se ejecutan en local y no cuestan nada. La Parte I (AKS) es opcional: un clúster de **un nodo `Standard_B2s`** en nivel Free cuesta aproximadamente 1-2 USD por día completo (nodo, disco del sistema, Load Balancer estándar e IP pública). Hecha en una sesión de 2-3 horas y borrando el grupo de recursos al final, se queda en céntimos. Si dejas el clúster encendido una semana por descubierto, son unos 10 USD. Presupuesto y alerta activos antes de empezar, `az group delete` al terminar.

### Instrucciones

**Parte A — Clúster local de tres nodos (60-90 min)**

1. Instala `kind` y `kubectl` siguiendo el Quick Start de kind. Crea `k8s/kind-config.yaml` con un `control-plane` y dos `worker`, y en el control-plane añade `extraPortMappings` para los puertos 80 y 443 del anfitrión (lo necesita el Ingress; está explicado en la página "Ingress" de kind). Crea el clúster: `kind create cluster --name curso --config k8s/kind-config.yaml`.
2. Explora: `kubectl cluster-info`, `kubectl get nodes -o wide`, `kubectl get pods -A`, `kubectl get componentstatuses 2>/dev/null || kubectl get --raw='/readyz?verbose'`. Identifica en `kube-system` los Pods del API server, etcd, scheduler, controller manager, kube-proxy, CoreDNS y el CNI (kindnet). Explica con tus palabras qué hace cada uno y en qué nodo corre.
3. Mira "por dentro" un nodo: `docker exec -it curso-worker bash` y dentro `ps aux | grep -E 'kubelet|containerd'`, `crictl ps` (o `ctr -n k8s.io containers ls`). Relaciona lo que ves con lo que aprendiste en Docker: el kubelet habla con containerd, no con Docker. Sal del nodo.
4. Crea el namespace `curso`, hazlo el namespace por defecto de tu contexto (`kubectl config set-context --current --namespace=curso`) y explica para qué sirven los namespaces y qué **no** aíslan (pista: red, a menos que haya NetworkPolicies).
5. Si tu imagen es privada, crea un Secret `docker-registry` con un token de solo lectura y anota cómo se referencia desde `imagePullSecrets`. Si es pública, documenta la decisión.

**Parte B — Deployment, ReplicaSet, rolling update y rollback (90 min)**

6. Escribe `k8s/deployment.yaml`: Deployment `api` con 3 réplicas, la imagen con el tag `1.0.0`, el puerto del contenedor y labels `app=api` y `version=1.0.0`. Aplícalo y observa: `kubectl get deploy,rs,pods -l app=api -o wide`. Explica la cadena Deployment → ReplicaSet → Pod y por qué el nombre del Pod lleva dos sufijos.
7. Borra un Pod a mano (`kubectl delete pod <nombre>`) y observa con `kubectl get pods -w` quién lo recrea y cuánto tarda. Escala a 5 y a 2 con `kubectl scale`. Comprueba en qué nodos caen los Pods y por qué se reparten.
8. Rolling update: cambia el tag a `1.1.0` en el manifiesto (no con `kubectl set image`, queremos que el YAML sea la fuente de verdad), aplica y sigue el proceso en dos terminales: `kubectl rollout status deploy/api` y `kubectl get rs -w`. Explica `maxSurge` y `maxUnavailable` con lo que has visto y cambia la estrategia a `Recreate` para comparar (y vuelve a `RollingUpdate`).
9. Simula un despliegue roto: aplica una versión con un tag que no existe (`9.9.9`). Observa que el rollout se queda a medias y que las réplicas antiguas siguen sirviendo. `kubectl rollout history deploy/api`, `kubectl rollout undo deploy/api`, y comprueba que vuelves a `1.1.0`. Explica por qué el rollback funcionó sin cortar el servicio y qué guarda cada revisión (mira `revisionHistoryLimit`).

**Parte C — Services, DNS, ConfigMaps y Secrets (90 min)**

10. Crea `k8s/service.yaml` con un Service **ClusterIP** `api` que seleccione `app=api`. Desde un Pod de utilidad (`kubectl run -it --rm debug --image=busybox:1.36 -- sh`) ejecuta `nslookup api`, `nslookup api.curso.svc.cluster.local` y `wget -qO- http://api:<puerto>/health` varias veces. Explica el nombre DNS completo, quién lo resuelve (CoreDNS) y cómo `kube-proxy` reparte las peticiones entre los Pods (`kubectl get endpoints api` o `kubectl get endpointslices`).
11. Cambia el tipo a **NodePort** y accede desde el anfitrión a `http://localhost:<nodePort>` (en kind necesitarás mapear el puerto o usar `docker inspect` para la IP del nodo; documenta cómo lo resolviste). Cambia a **LoadBalancer** y observa que `EXTERNAL-IP` se queda en `<pending>`. Explica por qué en un clúster local no hay balanceador y qué lo proporciona en AKS/EKS/GKE. Opcional: instala la solución que describe la página "LoadBalancer" de kind y comprueba que la IP aparece. Vuelve a ClusterIP para el resto del laboratorio.
12. Crea `k8s/configmap.yaml` con al menos `APP_ENV=laboratorio` y `LOG_LEVEL=info`, y un archivo de configuración pequeño (por ejemplo `settings.json`). Inyéctalo en el Deployment de dos formas: las claves como variables de entorno (`envFrom`) y el archivo montado como volumen en `/etc/api/`. Verifica con `kubectl exec deploy/api -- env` y `kubectl exec deploy/api -- cat /etc/api/settings.json`. Cambia un valor del ConfigMap y comprueba qué se actualiza solo (el archivo montado, con retardo) y qué no (las variables de entorno) y por qué.
13. Crea un Secret `api-secrets` con una clave `DATABASE_PASSWORD` (`kubectl create secret generic ... --from-literal`), móntalo como variable de entorno y como archivo. Ejecuta `kubectl get secret api-secrets -o yaml` y decodifica el valor con `base64 -d`. Explica qué protege un Secret (RBAC, no aparece en `describe`, no se escribe en logs) y qué **no** (está en base64, cualquiera con permiso de lectura lo ve, y en etcd va en claro salvo que se cifre en reposo). Anota qué harías en producción (Key Vault con el CSI driver o External Secrets), pero no lo implementes ahora.

**Parte D — Ingress con TLS (60 min)**

14. Instala ingress-nginx con el manifiesto para kind que indica su guía de instalación y espera a que el controlador esté `Ready`. Explica qué es un Ingress Controller y por qué el objeto `Ingress` no hace nada sin él.
15. Genera un certificado autofirmado con `openssl req -x509 -newkey rsa:2048 -nodes -keyout tls.key -out tls.crt -days 30 -subj "/CN=api.curso.local"` y crea el Secret TLS (`kubectl create secret tls api-tls --cert=tls.crt --key=tls.key`). Escribe `k8s/ingress.yaml` con host `api.curso.local`, ruta `/` hacia el Service `api`, `ingressClassName: nginx` y la sección `tls`.
16. Añade `127.0.0.1 api.curso.local` a tu `/etc/hosts` (o `C:\Windows\System32\drivers\etc\hosts`). Prueba `curl -k https://api.curso.local/health` y `curl -kv https://api.curso.local/` (fíjate en el certificado que devuelve). Prueba también con HTTP y explica la redirección. Mira los logs del controlador (`kubectl logs -n ingress-nginx deploy/ingress-nginx-controller`) y localiza tus peticiones.

**Parte E — StatefulSet con PostgreSQL, PVC y DaemonSet (90-120 min)**

17. Lista las StorageClasses del clúster (`kubectl get sc`). En kind hay una `standard` (local-path, `rancher.io/local-path`) marcada como default. Explica la diferencia entre StorageClass, PersistentVolume y PersistentVolumeClaim y qué significa `volumeBindingMode: WaitForFirstConsumer`.
18. Escribe `k8s/postgres.yaml`: un Service **headless** `postgres` (`clusterIP: None`) y un StatefulSet `postgres` con 1 réplica, imagen `postgres:16`, variables `POSTGRES_PASSWORD` desde el Secret de la Parte C, y un `volumeClaimTemplates` de 1 Gi montado en `/var/lib/postgresql/data`. Aplica y observa `kubectl get sts,pods,pvc,pv`. Explica por qué el Pod se llama `postgres-0` y qué DNS tiene (`postgres-0.postgres.curso.svc.cluster.local`).
19. Prueba la persistencia: `kubectl exec -it postgres-0 -- psql -U postgres -c "CREATE TABLE prueba(id serial, nota text); INSERT INTO prueba(nota) VALUES ('sobrevivi');"`. Borra el Pod (`kubectl delete pod postgres-0`), espera a que vuelva y comprueba que la fila sigue ahí. Borra el StatefulSet **sin** borrar el PVC y vuelve a crearlo: los datos siguen. Explica qué pasaría si borras el PVC y qué política (`reclaimPolicy`) tiene el PV.
20. Si tu API acepta una `DATABASE_URL`, apúntala a `postgres://postgres:<pass>@postgres-0.postgres:5432/postgres` desde el Secret y comprueba desde la API que conecta. Si tu API no usa base de datos, no pasa nada: el objetivo es operar el StatefulSet. Opcionalmente añade un endpoint `/db` que haga `SELECT 1` y publica una nueva imagen.
21. DaemonSet: escribe `k8s/log-agent.yaml`, un DaemonSet `log-agent` con una imagen `busybox:1.36` que ejecute `tail -F` sobre `/var/log/containers/*.log` (monta `/var/log` del nodo con `hostPath`, solo lectura). Comprueba que hay exactamente un Pod por nodo worker y ninguno en el control-plane; añade la `toleration` para `node-role.kubernetes.io/control-plane` y observa que ahora también corre allí. Explica para qué se usan los DaemonSets en la práctica (agentes de logs, métricas, seguridad, CNI).

**Parte F — Probes, recursos, QoS y HPA (120 min)**

22. Añade al Deployment `api` una **readinessProbe** HTTP a `/health`, una **livenessProbe** HTTP a `/health` con `periodSeconds: 10` y `failureThreshold: 3`, y una **startupProbe** con `failureThreshold: 30`. Explica qué decide cada una (recibir tráfico, ser reiniciado, dar tiempo al arranque) y qué pasa si solo pones liveness en una app que tarda en arrancar.
23. Provoca fallos: (a) cambia la readiness a una ruta que no existe y observa que los Pods están `Running` pero `0/1 READY` y que `kubectl get endpoints api` se queda vacío; (b) cambia la liveness a una ruta inexistente y observa los `RESTARTS` subir y el evento `Liveness probe failed` en `kubectl describe`; (c) pon un `initialDelaySeconds` demasiado corto y una app que "tarda" (puedes simularlo con un `command` que haga `sleep 20` antes de arrancar). Documenta cada síntoma y cómo lo distinguirías en una guardia. Restaura la configuración correcta.
24. Añade `resources.requests` (por ejemplo `cpu: 100m`, `memory: 64Mi`) y `resources.limits` (`cpu: 250m`, `memory: 128Mi`). Consulta `kubectl get pod <pod> -o jsonpath='{.status.qosClass}'` y explica las tres clases de QoS (Guaranteed, Burstable, BestEffort) y cuál te ha salido. Baja el `limits.memory` a un valor absurdo (`20Mi`) y observa `OOMKilled` en `kubectl describe`. Pide `requests.cpu: 10` (diez CPUs) y observa el Pod en `Pending` con el evento `Insufficient cpu`. Restaura valores sanos.
25. Instala metrics-server (en kind necesita el argumento `--kubelet-insecure-tls`; edita el Deployment tras aplicar el `components.yaml` o usa un `kubectl patch`). Comprueba `kubectl top nodes` y `kubectl top pods`.
26. Crea un HPA para `api`: `kubectl autoscale deploy/api --cpu-percent=50 --min=2 --max=6` (o escribe `k8s/hpa.yaml` con `autoscaling/v2`). Genera carga desde un Pod (`kubectl run -it --rm carga --image=busybox:1.36 -- sh -c 'while true; do wget -qO- http://api:<puerto>/ >/dev/null; done'`) o con `hey` desde el anfitrión a través del Ingress. Observa `kubectl get hpa -w` durante varios minutos: cuándo escala hacia arriba, cuánto tarda en bajar cuando paras la carga y por qué (ventana de estabilización). Explica por qué el HPA necesita `requests.cpu` para funcionar.

**Parte G — Scheduling: nodeSelector, affinity, taints y tolerations (60-90 min)**

27. Etiqueta los nodos: `kubectl label node curso-worker tipo=frontend` y `kubectl label node curso-worker2 tipo=backend`. Añade al Deployment `api` un `nodeSelector: {tipo: frontend}` y comprueba que todos los Pods se mueven a ese nodo. Escala a 6: ¿qué pasa si el nodo se queda sin recursos? Retira el `nodeSelector`.
28. Sustitúyelo por `podAntiAffinity` con `requiredDuringSchedulingIgnoredDuringExecution` sobre `app=api` y `topologyKey: kubernetes.io/hostname`. Con 2 workers y 3 réplicas, una se queda `Pending`: explica por qué y arréglalo cambiando a `preferredDuringScheduling...`. Añade al StatefulSet `postgres` una `nodeAffinity` preferida hacia `tipo=backend` y comprueba dónde cae.
29. Taints: `kubectl taint node curso-worker2 dedicado=bd:NoSchedule`. Borra los Pods de `api` y observa que ninguno vuelve a ese nodo. Añade a `postgres` la `toleration` correspondiente y comprueba que sí puede. Prueba `NoExecute` y observa la expulsión inmediata de los Pods sin toleration. Explica la diferencia entre taint/toleration (el nodo rechaza) y affinity (el Pod elige) y cuándo usarías cada una en AKS (node pools de sistema y de usuario, nodos con GPU, nodos spot). Quita los taints al terminar.

**Parte H — Batería de troubleshooting (120-150 min, la parte más importante)**

Para cada caso: reproduce el fallo con un manifiesto propio en `k8s/roto/`, escribe **antes de mirar** qué crees que verás, diagnostica solo con `kubectl get`, `describe`, `logs` (incluido `--previous`), `get events --sort-by=.lastTimestamp`, `exec`, `port-forward` y `kubectl debug`, anota el comando que te dio la pista definitiva, arregla y explica la causa raíz. Sigue siempre el mismo orden: ¿está el Pod programado? ¿arranca el contenedor? ¿pasa las probes? ¿tiene endpoints el Service? ¿resuelve el DNS? ¿llega el Ingress?

30. **CrashLoopBackOff:** un Deployment cuya imagen ejecuta un comando que sale con error (`command: ["sh","-c","echo fallo; exit 1"]`) y otro con la aplicación real pero una variable de entorno obligatoria ausente. Distingue ambos con `logs --previous`.
31. **ImagePullBackOff / ErrImagePull:** un tag inexistente, un nombre de registro mal escrito y una imagen privada sin `imagePullSecrets`. Los tres se parecen en `get pods` y se distinguen en `describe`.
32. **Pending:** por `requests` imposibles, por `nodeSelector` hacia una etiqueta que no existe y por un PVC cuya StorageClass no existe. Lee los eventos del Pod y del PVC.
33. **Probes mal configuradas:** readiness al puerto equivocado (Pod nunca `Ready`, Service sin endpoints) y liveness demasiado agresiva (reinicios en bucle de una app sana).
34. **Service sin endpoints:** un `selector` con una errata (`app: apy`) y un `targetPort` que no coincide con el puerto del contenedor. Usa `kubectl get endpoints` y `kubectl describe svc` y explica por qué `curl` da "connection refused" en un caso y cuelga en otro.
35. **DNS interno:** desde un Pod de utilidad, resuelve un Service en otro namespace con y sin el sufijo completo; provoca un fallo escalando CoreDNS a 0 réplicas (`kubectl -n kube-system scale deploy/coredns --replicas=0`), observa qué deja de funcionar y qué no (las conexiones por IP siguen), y restáuralo. Lee `kubectl -n kube-system logs deploy/coredns`.
36. **Ingress que devuelve 404 o 503:** un `host` que no coincide con el que pones en `curl`, un `ingressClassName` erróneo y un Service de backend con nombre equivocado. Aprende a leer el log del controlador.
37. Escribe al final una **guía de troubleshooting de una página** (`troubleshooting.md`) con tu método, los síntomas y el comando que resuelve cada uno. Esta guía la reutilizarás en Incident Management y en el Proyecto Final.

**Parte I — Opcional y acotada: lo mismo en AKS (2-3 h, con coste)**

38. Con presupuesto y alerta activos, crea el clúster mínimo:
    ```bash
    az group create --name rg-aks-lab --location <region> --tags curso=k8s-avanzado propietario=<usuario>
    az aks create --resource-group rg-aks-lab --name aks-lab --tier free --node-count 1 --node-vm-size Standard_B2s --generate-ssh-keys
    az aks get-credentials --resource-group rg-aks-lab --name aks-lab
    kubectl config get-contexts
    ```
    Anota el tiempo que tarda y qué recursos aparecen en el grupo `MC_rg-aks-lab_aks-lab_<region>` (VMSS, disco, Load Balancer, IP pública, NSG, VNet). Compáralo con lo que tenías en kind.
39. Aplica tus manifiestos de `k8s/` (sin el DaemonSet de logs ni el Ingress si no instalas el controlador). Observa: el Service `LoadBalancer` obtiene una **IP pública real** (¿quién la ha creado y cuánto cuesta?); `kubectl get sc` muestra las StorageClasses de Azure (`default`/`managed-csi`, `azurefile`, etc.) y el PVC de PostgreSQL crea un **Azure Disk** que puedes ver en el portal. Prueba `/health` desde Internet.
40. Compara `kubectl get pods -n kube-system` con el de kind: qué componentes del control plane **no** ves y por qué (los gestiona Azure), y qué agentes nuevos aparecen. Explica la responsabilidad compartida en AKS.
41. **Borra todo**: `az group delete --name rg-aks-lab --yes --no-wait`. Comprueba al cabo de unos minutos que el grupo `MC_...` también desapareció y que `az resource list --output table` está limpio. Al día siguiente, captura Cost Management con el coste real del laboratorio. Si no haces la Parte I, escribe igualmente las diferencias esperadas a partir de la documentación de AKS (StorageClasses, Load Balancer, niveles Free/Standard).

**Parte J — Limpieza y equivalencias (20 min)**

42. `kind delete cluster --name curso` (o conserva el clúster si vas a empezar Helm en breve: lo vas a necesitar). Completa una tabla de equivalencias con al menos 12 filas: concepto de Kubernetes ↔ qué lo proporciona en AKS ↔ en EKS ↔ en GKE (control plane gestionado, LoadBalancer, StorageClass por defecto, Ingress gestionado, identidad de Pods, registro de imágenes, autoescalado de nodos, etc.).

### Resultado esperado

- Carpeta `k8s/` con todos los manifiestos funcionales (un archivo por objeto) y la subcarpeta `k8s/roto/` con los casos de la Parte H.
- `laboratorio-k8s.md` con las partes A-J, comandos, salidas relevantes, capturas y explicaciones propias, incluido el dibujo del recorrido de `kubectl apply`.
- `troubleshooting.md` con tu guía de una página.
- Si hiciste la Parte I: captura de la IP pública funcionando, del Azure Disk creado por el PVC y del coste del día siguiente, con el grupo de recursos borrado.

### Criterios de validación

- [ ] Parte A: el clúster tiene tres nodos `Ready`; la explicación de los componentes del control plane y del nodo es correcta y menciona containerd, no Docker.
- [ ] Parte B: el rolling update y el rollback están documentados con `rollout status/history/undo` y la explicación de `maxSurge`/`maxUnavailable` coincide con lo observado.
- [ ] Parte C: se distingue correctamente ClusterIP/NodePort/LoadBalancer; se explica el DNS interno; el ConfigMap está inyectado de las dos formas y se explica qué se recarga y qué no; la explicación de lo que protege y no protege un Secret es precisa.
- [ ] Parte D: `curl -k https://api.curso.local/health` responde a través de ingress-nginx con el certificado autofirmado.
- [ ] Parte E: la fila `sobrevivi` sigue existiendo tras borrar el Pod y tras recrear el StatefulSet; el DaemonSet corre en todos los nodos tras añadir la toleration.
- [ ] Parte F: los tres fallos de probes están reproducidos y explicados; se identifican `OOMKilled` e `Insufficient cpu`; el HPA escala con carga y baja al retirarla, con las cifras anotadas.
- [ ] Parte G: se demuestra el `Pending` por anti-affinity requerida y su arreglo; se demuestra `NoSchedule` frente a `NoExecute`; la distinción taint/affinity es correcta.
- [ ] Parte H: los siete tipos de fallo están reproducidos con manifiestos propios, diagnosticados con el comando decisivo anotado y explicados por causa raíz; la guía `troubleshooting.md` es propia y utilizable.
- [ ] Parte I (si se hace): la IP pública del LoadBalancer y el Azure Disk están capturados, el grupo de recursos está borrado y el coste del día siguiente es coherente con la estimación.
- [ ] El estudiante puede, en una llamada con el mentor, diagnosticar en menos de 10 minutos un manifiesto roto que no ha visto antes.

## Entrega

En tu repositorio de entregas, carpeta `03-modulo-avanzado/01-kubernetes-avanzado/`:

1. `laboratorio-k8s.md`.
2. Carpeta `k8s/` con los manifiestos (y `k8s/roto/`). Sin secretos reales: los Secrets van con valores de ejemplo o generados con `kubectl create secret ... --dry-run=client -o yaml` y valores ficticios.
3. `troubleshooting.md`.
4. `capturas/` (con tu usuario, nombre de clúster o fecha visibles).
5. `ENTREGA.md` con evaluación, checklist y uso de IA.

Nota sobre IA: es muy útil para explicarte un evento de `kubectl describe` que no entiendes o para revisar un manifiesto que ya escribiste. No le pidas los manifiestos hechos: el valor de este curso está en que los errores de la Parte H los hayas provocado, visto y arreglado tú.

## Evaluación

1. **Conceptual.** Describe el recorrido de `kubectl apply -f deployment.yaml` hasta que el contenedor arranca: qué componentes intervienen, en qué orden, y qué guarda etcd. ¿Qué pasaría si el scheduler estuviera caído?
2. **Conceptual.** ¿Qué relación hay entre Deployment, ReplicaSet y Pod? ¿Por qué tras varios rolling updates hay varios ReplicaSets con 0 réplicas y para qué sirven?
3. **Situacional.** Un despliegue de la versión 2.3.0 lleva 20 minutos "en curso": 2 Pods nuevos en `CrashLoopBackOff` y 3 antiguos sirviendo. ¿Están los usuarios afectados? ¿Qué comando ejecutas primero y cuál después para volver a un estado sano?
4. **Técnica.** Un Service `api` de tipo ClusterIP tiene `port: 80` y `targetPort: 8080`. Un Pod en otro namespace `pagos` quiere llamarlo. Escribe la URL completa que debería usar y explica qué resuelve cada parte del nombre.
5. **Troubleshooting.** `kubectl get endpoints api` devuelve `<none>` aunque hay 3 Pods `Running` y `1/1 READY`. Da dos causas posibles y cómo confirmarías cada una.
6. **Conceptual.** ¿Qué diferencia práctica hay entre inyectar un ConfigMap como variables de entorno y montarlo como volumen? ¿Cuál se actualiza sin reiniciar el Pod? ¿Qué harías para forzar el reinicio al cambiar el ConfigMap?
7. **Situacional.** Un compañero dice "los Secrets de Kubernetes son seguros porque están cifrados en base64". Corrígele y explica qué medidas hacen falta de verdad (permisos RBAC, cifrado en reposo en etcd, gestor externo como Key Vault).
8. **Técnica.** ¿Por qué PostgreSQL va en un StatefulSet y la API en un Deployment? Nombra tres garantías que da el StatefulSet y explica qué le pasa al PVC cuando borras el StatefulSet.
9. **Troubleshooting.** Un Pod lleva 5 minutos en `Pending`. Escribe el comando que ejecutarías y tres mensajes distintos que podrías encontrar en los eventos, con la solución de cada uno.
10. **Conceptual.** Explica readiness, liveness y startup probe con un ejemplo de fallo que cada una detecta y otro que **no** detecta. ¿Qué daño puede hacer una liveness probe demasiado agresiva?
11. **Técnica.** Un Pod tiene `requests: cpu 100m, memory 128Mi` y `limits: cpu 500m, memory 128Mi`. ¿Qué clase de QoS tiene? ¿Qué le pasa si consume 600m de CPU? ¿Y si consume 200Mi de memoria? ¿Cuál de los dos es más grave para el proceso?
12. **Situacional.** El HPA está configurado al 50 % de CPU con mínimo 2 y máximo 10, pero nunca escala aunque la app va lenta. Da tres causas posibles (piensa en metrics-server, requests y el tipo de cuello de botella).
13. **Técnica.** Necesitas que la base de datos corra solo en el node pool `bd` y que ninguna otra carga caiga allí. Escribe qué configuras en los nodos y qué en el StatefulSet, y explica por qué con solo `nodeAffinity` no bastaría.
14. **Conceptual.** ¿Qué gestiona Azure y qué gestionas tú en un clúster AKS? Nombra dos cosas que en kind hiciste a mano y en AKS aparecieron solas, y qué coste tienen.
15. **Reflexión.** De los siete tipos de fallo de la Parte H, ¿cuál te costó más diagnosticar y qué señal deberías haber mirado antes? ¿Cómo cambiarías tu guía de troubleshooting después de la experiencia?

## Checklist final

Antes de continuar, deberías poder:

- [ ] Explicar la arquitectura de Kubernetes y el recorrido de un `kubectl apply`.
- [ ] Crear y destruir un clúster local multinodo y moverte entre contextos y namespaces.
- [ ] Desplegar con Deployment, hacer rolling update y rollback, y explicar `maxSurge`/`maxUnavailable`.
- [ ] Exponer con Service ClusterIP/NodePort/LoadBalancer y explicar el DNS interno y los endpoints.
- [ ] Inyectar ConfigMaps y Secrets de las dos formas y explicar sus límites de seguridad.
- [ ] Publicar por HTTPS con Ingress e ingress-nginx.
- [ ] Desplegar un StatefulSet con PVC y explicar PV/PVC/StorageClass.
- [ ] Configurar probes, requests y limits, explicar QoS, OOMKilled y Pending por recursos.
- [ ] Configurar un HPA y demostrar que escala con carga.
- [ ] Usar nodeSelector, affinity/anti-affinity, taints y tolerations con criterio.
- [ ] Diagnosticar CrashLoopBackOff, ImagePullBackOff, Pending, probes, Service sin endpoints, DNS e Ingress con un método propio.
- [ ] Crear y borrar un AKS mínimo y explicar sus diferencias con el clúster local (o explicarlas a partir de la documentación).
- [ ] Tener los manifiestos en `k8s/` listos para convertirlos en un chart de Helm en el siguiente curso.

---

*Recursos verificados el 2026-09-27 (existencia y vigencia de las URLs mediante búsqueda web y, cuando el cupo de búsqueda se agotó, mediante los repositorios oficiales de la documentación). Las páginas de Microsoft Learn se enlazan en `es-es` cuando se confirmó la traducción; en el resto se indica cómo cambiar el idioma. Si un enlace falla, abre un issue en este repositorio.*
