# Networking Intermedio y Troubleshooting

> Módulo: Intermedio · Curso 2 de 11 · Duración estimada: 30-40 horas · Estado: ✅ Completo

## Objetivo

En Networking Básico aprendiste cómo viajan los paquetes y a diagnosticar por capas con `ping`, `traceroute` y `nslookup`. Este curso te lleva al nivel en el que trabaja un equipo de operaciones: **entender lo que hay entre el cliente y la aplicación** (DNS con forwarders, rutas estáticas, NAT, TLS, un reverse proxy, un balanceador, un firewall) y **demostrar con herramientas dónde se rompe** cuando alguien dice "la web no va".

La diferencia entre un técnico junior y uno intermedio en redes no es saber más comandos, es tener **método**: reproducir el síntoma, formular una hipótesis por capa, elegir la herramienta que la confirma o la descarta, y no tocar nada hasta saber qué está roto. Aquí practicarás ese método con ocho averías construidas a propósito en un laboratorio de dos VMs que tú mismo montas: un router con DNS y NAT, y un servidor con nginx haciendo de reverse proxy TLS delante de dos backends balanceados. Al terminar, `curl -v`, `dig`, `ss`, `tcpdump`, `nc` y `openssl s_client` serán reflejos, no comandos que buscas.

Todo esto es transferible tal cual a la nube: una VNet de Azure con subredes, tablas de rutas, NSG, Azure DNS privado, un Load Balancer y una Application Gateway son exactamente los conceptos que vas a tocar con tus manos aquí, solo que allí los configura una API.

**Antes de empezar** necesitas la VM `lab-so` del curso anterior (con `nginx`, SSH endurecido y `ufw`) y crear una segunda VM Ubuntu Server (`lab-net`, 1 GB de RAM basta). Ambas en VirtualBox, Hyper-V o UTM con soporte de redes internas.

### Al terminar este curso deberías poder

- Diseñar el direccionamiento de varias redes con CIDR y explicar qué hace una tabla de rutas al decidir por dónde sale cada paquete (`ip route get`).
- Configurar rutas estáticas y reenvío IP en Linux y explicar la diferencia entre un host, un router y un gateway por defecto.
- Explicar la resolución DNS completa (stub, recursivo, forwarder, autoritativo, caché, TTL) y montar un servidor DNS pequeño con `dnsmasq`.
- Configurar NAT (masquerade y DNAT) con `nftables` o `iptables` entre dos redes internas y explicar qué ve cada extremo.
- Explicar el handshake TLS, qué es un certificado, una CA, la cadena de confianza y el SNI, y analizar un servidor con `openssl s_client`.
- Montar nginx como reverse proxy con TLS delante de una aplicación y como balanceador con `upstream`, y leer sus logs.
- Distinguir proxy directo, reverse proxy, balanceador de capa 4 y de capa 7, y NAT, y decir qué IP ve cada componente.
- Capturar tráfico con `tcpdump` (filtros, `-w`, `-r`, `-A`) y leer un handshake TCP, una consulta DNS, un `ClientHello` TLS y una petición HTTP en claro.
- Usar con criterio `curl`, `dig`, `ss`, `netstat`, `nc`, `openssl`, `traceroute` y `tcpdump` para confirmar o descartar hipótesis.
- Diagnosticar con método y documentar al menos ocho averías de conectividad, indicando capa, punto de rotura, causa raíz y verificación.

## Prerrequisitos

- Curso 1 del Módulo Intermedio: Administración de Linux (systemd, `netplan`, `ufw`, `journalctl`).
- Networking Básico del Módulo Básico (IP, máscaras, subnetting introductorio, DNS, TCP/UDP, puertos).
- Dos VMs Ubuntu Server LTS locales: `lab-so` (existente) y `lab-net` (nueva). Hipervisor con **redes internas** (VirtualBox "Red interna", Hyper-V "Conmutador privado", UTM "Emulated VLAN"/host-only).
- Snapshot de ambas VMs antes de empezar.

## Temario

CIDR · Subnetting · Routing · Route tables · DNS en profundidad · NAT · TLS · HTTP/HTTPS · Proxies · Reverse proxies · Load balancing · Firewalls · Análisis de conectividad.

**Herramientas:** curl, dig, ss, netstat, tcpdump, nc, openssl, traceroute.

**Práctica:** diagnosticar fallos de conectividad construidos deliberadamente.

## Recursos en español

### Centro de aprendizaje de Cloudflare (en español) — Cloudflare
- **URL:** https://www.cloudflare.com/es-la/learning/ (secciones DNS, SSL/TLS, Rendimiento: "¿Qué es el equilibrio de carga?", "¿Qué es un proxy inverso?", CDN)
- **Autor / organización:** Cloudflare
- **Idioma:** Español (traducción de la versión inglesa)
- **Tipo:** Artículos explicativos con diagramas
- **Duración aproximada:** 3-4 h para: qué es DNS, tipos de servidores DNS, registros DNS, qué es TLS/SSL, cómo funciona el handshake TLS, qué es un certificado, qué es un proxy inverso, qué es el equilibrio de carga, qué es NAT
- **Cubre:** DNS en profundidad, TLS, HTTP/HTTPS, proxies, reverse proxies, load balancing, NAT.
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la mejor explicación conceptual gratuita de los servicios que hay entre el navegador y la aplicación, escrita por una empresa que opera una parte importante de Internet. Léela antes de montar cada pieza del laboratorio para saber qué estás construyendo. Cuando una traducción suene rara, cambia `es-la` por `learning` en la URL y lee el original.

### Introducción a los servicios básicos de red de Azure — Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/training/paths/intro-to-azure-network-foundation-services/ · Documentación: https://learn.microsoft.com/es-es/azure/networking/fundamentals/
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Ruta de aprendizaje y documentación
- **Duración aproximada:** 2-3 h (módulos de Virtual Network, DNS, NSG, Load Balancer)
- **Cubre:** Cómo se llaman en Azure los conceptos del curso: VNet y subredes (CIDR), tablas de rutas definidas por el usuario, Azure DNS y resolución privada, NSG (firewall), Load Balancer (capa 4) y Application Gateway (capa 7, reverse proxy), NAT Gateway.
- **Nivel:** Introductorio
- **Acceso:** Libre; cuenta Microsoft gratuita para guardar progreso
- **Por qué lo recomiendo:** Ya lo viste por encima en Networking Básico. Ahora lo lees con otra cabeza: cada concepto que montes en las VMs tiene aquí su equivalente gestionado. Es la base de la tabla de equivalencias del laboratorio. No crees recursos en Azure en este curso: aquí se trabaja en local.

## Recursos en inglés

### Practical Networking (series TLS, NAT, Routing) — Ed Harmoush
- **URL:** https://www.practicalnetworking.net/index/networking-fundamentals-how-data-moves-through-the-internet/ (índice de fundamentos; desde el menú "Series" del sitio llega a las series "Practical TLS" y "NAT", y a las lecciones de routing)
- **Autor / organización:** Ed Harmoush, ingeniero de redes y formador
- **Idioma:** Inglés (subtítulos en los vídeos)
- **Tipo:** Artículos y vídeos
- **Duración aproximada:** 4-5 h: la serie de fundamentos completa si no la terminaste, la serie de NAT (tipos de NAT, qué ve cada lado) y los vídeos introductorios gratuitos de la serie TLS (handshake, certificados, cadena de confianza)
- **Cubre:** Routing, route tables, NAT, TLS, HTTP/HTTPS.
- **Nivel:** Intermedio
- **Acceso:** Libre (el curso completo "Practical TLS" es de pago; las lecciones introductorias y todos los artículos son gratuitos y son suficientes para este curso)
- **Por qué lo recomiendo:** Nadie explica mejor "qué hay dentro de cada paquete en cada salto". Su explicación del handshake TLS y de por qué el certificado se valida como se valida es la que deberías tener en la cabeza cuando lances `openssl s_client`.

### CompTIA Network+ N10-009 Training Course, secciones de troubleshooting — Professor Messer
- **URL:** https://www.professormesser.com/network-plus/n10-009/n10-009-video/n10-009-training-course/
- **Autor / organización:** James "Professor" Messer
- **Idioma:** Inglés (subtítulos)
- **Tipo:** Curso en vídeo (lecciones de 5-15 min)
- **Duración aproximada:** 4-5 h: sección 1 (routing, NAT, DNS, DHCP), sección 3 (network services) y toda la sección 5 (troubleshooting: metodología, herramientas de software, problemas comunes)
- **Cubre:** Routing, route tables, DNS, NAT, firewalls, análisis de conectividad, metodología de troubleshooting, herramientas (`ping`, `traceroute`, `dig`, `nmap`, `tcpdump`, `netstat`/`ss`).
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** La sección de troubleshooting enseña el método formal (identificar el problema, hipótesis, probar, plan, verificar, documentar) que vas a aplicar en las ocho averías. Es el mismo método que usarás en incidentes reales y en el curso de Incident Management del Módulo Avanzado.

### Cloudflare Learning Center: DNS (en inglés) — Cloudflare
- **URL:** https://www.cloudflare.com/learning/dns/what-is-dns/ · Tipos de servidor: https://www.cloudflare.com/learning/dns/dns-server-types/ · Registros: https://www.cloudflare.com/learning/dns/dns-records/
- **Autor / organización:** Cloudflare
- **Idioma:** Inglés
- **Tipo:** Artículos
- **Duración aproximada:** 60 min
- **Cubre:** DNS en profundidad: resolutor recursivo, raíz, TLD, autoritativo, caché, TTL, tipos de registro.
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Son las tres páginas que tienes que haber leído antes de montar `dnsmasq` y de interpretar `dig +trace`. Ya las conoces del Módulo Básico: reléelas fijándote en la diferencia entre resolutor, forwarder y autoritativo, que es justo lo que vas a construir.

### NGINX documentation — NGINX (F5)
- **URL:** https://nginx.org/ (menú "documentation": Beginner's Guide, "Using nginx as HTTP load balancer", "Configuring HTTPS servers", referencia de `ngx_http_proxy_module` y `ngx_http_upstream_module`) · Guías de administración: https://docs.nginx.com/
- **Autor / organización:** NGINX, Inc. (F5)
- **Idioma:** Inglés
- **Tipo:** Documentación oficial
- **Duración aproximada:** 2-3 h para la guía de principiantes, el balanceador HTTP, HTTPS y las directivas `proxy_pass`, `proxy_set_header`, `upstream`, `server` (con `max_fails`, `fail_timeout`, `weight`)
- **Cubre:** Reverse proxies, load balancing, HTTP/HTTPS, TLS en el servidor.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** nginx es el reverse proxy y balanceador más usado del mundo y el ingress más común en Kubernetes. Lo que configures aquí a mano es lo que después configurarás por YAML. Lee la referencia de cada directiva que uses: la documentación de nginx es corta, exacta y sin relleno.

### tcpdump y libpcap (página del proyecto y manual) — The Tcpdump Group
- **URL:** https://www.tcpdump.org/ (manual `tcpdump(1)` y `pcap-filter(7)` en la sección de documentación; en la VM: `man tcpdump`, `man pcap-filter`)
- **Autor / organización:** The Tcpdump Group
- **Idioma:** Inglés
- **Tipo:** Documentación oficial y páginas de manual
- **Duración aproximada:** 60-90 min: sintaxis de filtros (`host`, `net`, `port`, `and`/`or`/`not`), opciones `-i`, `-n`/`-nn`, `-c`, `-w`/`-r`, `-A`/`-X`, `-v`, y la sección de ejemplos del manual
- **Cubre:** Análisis de conectividad, captura y lectura de tráfico.
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** `tcpdump` es la herramienta que zanja discusiones: "el paquete llegó o no llegó". Está en cualquier servidor Linux, incluidos los nodos de Kubernetes y las VMs de Azure donde no puedes instalar Wireshark. Aprende la sintaxis de filtros del manual y luego abre las capturas en Wireshark si quieres la vista gráfica.

## Documentación oficial

- **nginx:** https://nginx.org/ · https://docs.nginx.com/
- **tcpdump / libpcap:** https://www.tcpdump.org/
- **OpenSSL (proyecto y documentación de `openssl s_client`, `req`, `x509`):** https://openssl-library.org/ · En la VM: `man openssl-s_client`, `man openssl-req`, `man openssl-x509`
- **dnsmasq (documentación y ejemplo de configuración):** http://thekelleys.org.uk/dnsmasq/doc.html · En la VM: `man dnsmasq` y `/usr/share/doc/dnsmasq/examples/`
- **Netplan (rutas estáticas, DNS, interfaces):** https://netplan.io
- **Ubuntu Server — Configuring networks:** https://ubuntu.com/server/docs/explanation/networking/configuring-networks/
- **nftables / iptables:** en la VM, `man nft`, `man iptables`, `man ufw` (páginas de manual de las herramientas instaladas) · Índice de manuales: https://man7.org/linux/man-pages/
- **RFC 1918 (direcciones privadas):** https://www.rfc-editor.org/rfc/rfc1918
- **Wireshark User's Guide (opcional):** https://www.wireshark.org/docs/wsug_html_chunked/
- **Azure — Fundamentos de redes (para la tabla de equivalencias):** https://learn.microsoft.com/es-es/azure/networking/fundamentals/

## Ruta recomendada de estudio

1. **Leer** en Cloudflare (es-la o inglés) las páginas de DNS (qué es, tipos de servidor, registros) y de NAT (60 min). **Ver** en Professor Messer las lecciones de routing, NAT y DNS de la sección 1 (60 min).
2. **Hacer** la Parte A del laboratorio (diseño de direccionamiento y montaje de las dos VMs). Sin esto no hay curso.
3. **Ver** la serie de NAT de Practical Networking (45 min) y **hacer** la Parte B (rutas estáticas y NAT).
4. **Leer** la documentación de `dnsmasq` (30 min) y **hacer** la Parte C (DNS).
5. **Leer** en Cloudflare TLS (qué es, handshake, certificado) y **ver** las lecciones introductorias de Practical TLS (90 min). **Leer** en nginx "Configuring HTTPS servers" y la guía de principiantes (45 min). **Hacer** la Parte D (reverse proxy y TLS).
6. **Leer** en nginx "Using nginx as HTTP load balancer" y `ngx_http_upstream_module` (30 min), y en Cloudflare "qué es un proxy inverso" y "qué es el equilibrio de carga" (30 min). **Hacer** la Parte E (balanceo).
7. **Leer** el manual de `tcpdump` (filtros y ejemplos) (60 min) y **hacer** la Parte F (captura).
8. **Ver** completa la sección 5 de Professor Messer (troubleshooting) (90 min) y **hacer** la Parte G (averías). Escribe tu diagnóstico antes de mirar la causa.
9. **Hacer** la Parte H (equivalencias con Azure) leyendo la ruta de Microsoft Learn en paralelo (2 h).
10. **Responder la evaluación** y **revisar el checklist**.

Si vas justo de tiempo: obligatorios los puntos 2, 3, 4, 5 y 8. La Parte F puede reducirse a las tres capturas mínimas.

## Laboratorio

### Objetivo

Construir con dos VMs una pequeña infraestructura de red realista (router con DNS, NAT y forwarders; servidor web con reverse proxy TLS y balanceo hacia dos backends en otra red), verificar cada pieza con las herramientas del curso, capturar y leer el tráfico, y diagnosticar con método ocho averías provocadas deliberadamente.

### Requisitos

- `lab-so` (existente) y `lab-net` (nueva, Ubuntu Server LTS, 1 GB RAM, 10 GB disco, usuario con clave SSH copiada desde el anfitrión).
- En ambas VMs: `sudo apt install -y dnsutils tcpdump netcat-openbsd traceroute net-tools nftables openssl curl`. En `lab-net` además `dnsmasq`. En `lab-so` ya está `nginx`.
- Redes del hipervisor (nombres de VirtualBox; adapta a Hyper-V/UTM):
  - `lab-so`: adaptador 1 **NAT** (para `apt`; se desconectará en la Parte B), adaptador 2 **Red interna `acme-a`**.
  - `lab-net`: adaptador 1 **NAT**, adaptador 2 **Red interna `acme-a`**, adaptador 3 **Red interna `acme-b`**.
  - Para llegar por SSH desde el anfitrión a las VMs conserva el reenvío de puertos del adaptador NAT (por ejemplo 2222 → `lab-so`:22 y 2223 → `lab-net`:22) o añade un adaptador solo-anfitrión. Documenta lo que elijas.
- Documenta todo en `laboratorio-redes-intermedio.md` con comandos y salidas como texto. Guarda los archivos de configuración y las capturas `.pcap` en la carpeta de la entrega.
- Snapshot de las dos VMs al terminar la Parte A ("topologia-base"). Vas a romperlas ocho veces.

### Instrucciones

**Parte A — Direccionamiento y topología (2 h)**

1. Diseña el plan de direcciones y dibújalo (texto ASCII o imagen):

   | Red | CIDR | Uso | Gateway |
   |---|---|---|---|
   | `acme-a` | `10.10.10.0/24` | Red de servidores (donde vive `lab-so`) | `10.10.10.1` (`lab-net`) |
   | `acme-b` | `10.10.20.0/24` | Red de backends (solo `lab-net` tiene pata aquí) | `10.10.20.1` (`lab-net`) |

   Asigna `lab-so` = `10.10.10.10`, `lab-net` = `10.10.10.1` y `10.10.20.1`. Antes de configurar nada responde por escrito: ¿cuántos hosts caben en cada red? ¿Pueden `10.10.10.10` y `10.10.20.1` hablarse sin un router? ¿Qué pasaría si `acme-b` fuera `10.10.10.128/25`? Divide `10.10.20.0/24` en cuatro `/26` y di qué rango usarías para "backends", "bases de datos", "monitorización" y "reserva".
2. Configura las interfaces con `netplan` en ambas VMs (IPs estáticas en las redes internas, DHCP en la NAT). En `lab-net` activa el reenvío: `sysctl -w net.ipv4.ip_forward=1` y hazlo persistente en `/etc/sysctl.d/99-router.conf`. Verifica con `ip -br a`, `ip r`, `sysctl net.ipv4.ip_forward`. Explica qué es una tabla de rutas leyendo la de cada VM línea a línea y usa `ip route get 10.10.20.1` y `ip route get 1.1.1.1` desde `lab-so` para explicar qué decide el kernel en cada caso.
3. Comprueba la conectividad de capa 2/3 dentro de `acme-a`: `ping 10.10.10.1` desde `lab-so`, `ip neigh` en ambas (ARP), `traceroute -n 10.10.20.1` desde `lab-so` (fallará: no hay ruta; anótalo, se arregla en la Parte B). Haz el snapshot "topologia-base".

**Parte B — Rutas estáticas y NAT (2 h)**

4. Ruta estática: en `lab-so`, `sudo ip route add 10.10.20.0/24 via 10.10.10.1`. Repite `traceroute -n 10.10.20.1` y `ping 10.10.20.1`. En `lab-net`, mientras haces el ping, ejecuta `sudo tcpdump -ni <iface-acme-a> icmp` y `sudo tcpdump -ni <iface-acme-b> icmp`: ¿en qué interfaz aparece el eco? ¿por qué? Haz la ruta persistente en el `netplan` de `lab-so` (`routes:`) y aplica con `netplan try`.
5. NAT de salida (masquerade): desconecta el cable del adaptador NAT de `lab-so` desde el hipervisor (o `sudo ip link set <iface-nat> down`). Comprueba que `lab-so` ya no tiene Internet (`ping 1.1.1.1`, `curl -m 5 https://nginx.org`). Pon la ruta por defecto de `lab-so` hacia `lab-net`: `sudo ip route replace default via 10.10.10.1`. Sigue sin funcionar: diagnostica con `tcpdump` en `lab-net` (verás las peticiones salir por el adaptador NAT con IP origen `10.10.10.10` y no volver). Explica por qué. En `lab-net` crea con `nft` una tabla `nat` con cadena `postrouting` y regla `oifname "<iface-nat>" masquerade` (o `iptables -t nat -A POSTROUTING -o <iface-nat> -j MASQUERADE`). Repite las pruebas y captura de nuevo: ahora la IP origen que sale es la de `lab-net`. Guarda la configuración (`nft list ruleset > /etc/nftables.conf`, `systemctl enable nftables`). Explica con tus capturas qué es SNAT/masquerade y compáralo con lo que hace tu router doméstico y con Azure NAT Gateway.
6. DNAT (redirección de puerto): en `lab-net` añade una regla `prerouting` que redirija `10.10.10.1:8080` hacia `10.10.20.1:8081` (`dnat to`). En `lab-net` levanta un servidor de prueba `python3 -m http.server 8081 --bind 10.10.20.1` en un directorio con un `index.html`. Desde `lab-so`: `curl http://10.10.10.1:8080` y `curl http://10.10.20.1:8081`. Con `tcpdump` en `lab-net` muestra los dos destinos. Explica la diferencia entre DNAT y un reverse proxy (¿quién termina la conexión TCP en cada caso?). Elimina la regla DNAT al terminar para no confundir la Parte E.
7. Reconecta el adaptador NAT de `lab-so` solo si necesitas instalar algo más; deja documentado el estado final de rutas (`ip r`) de las dos VMs. Ejecuta `netstat -rn` y compáralo con `ip r`: explica por qué `ss`/`ip` sustituyen a `netstat`/`ifconfig`/`route` y por qué aun así conviene reconocer la salida antigua.

**Parte C — DNS en profundidad con dnsmasq (2 h)**

8. En `lab-net` configura `dnsmasq` (`/etc/dnsmasq.d/acme.conf`): `listen-address=10.10.10.1,127.0.0.1`, `bind-interfaces`, `domain=acme.lab`, `local=/acme.lab/`, `address=/web.acme.lab/10.10.10.10`, `host-record=router.acme.lab,10.10.10.1`, `host-record=backend.acme.lab,10.10.20.1`, `server=1.1.1.1`, `server=9.9.9.9`, `cache-size=1000`, `log-queries`. Si `systemd-resolved` ocupa el puerto 53 en `lab-net`, resuélvelo (deshabilita el stub listener o haz que `dnsmasq` escuche solo en `10.10.10.1`) y documenta cómo lo averiguaste (`ss -ulnp | grep :53`).
9. En `lab-so`, apunta el DNS a `10.10.10.1` en `netplan` (`nameservers: addresses: [10.10.10.1]`, `search: [acme.lab]`). Verifica con `resolvectl status`. Prueba: `dig web.acme.lab`, `dig web` (dominio de búsqueda), `dig -x 10.10.10.10`, `dig router.acme.lab`, `dig nginx.org`, `dig @1.1.1.1 web.acme.lab` (¿qué responde y por qué?). En `lab-net`, `journalctl -u dnsmasq -f` mientras consultas: identifica qué consultas se responden localmente, cuáles se reenvían a los forwarders y cuáles se sirven de caché (compara el TTL de dos `dig nginx.org` seguidos).
10. Explica con un diagrama la cadena completa cuando `lab-so` resuelve `learn.microsoft.com`: stub (`systemd-resolved`) → `dnsmasq` (forwarder con caché) → `1.1.1.1` (recursivo) → raíz → TLD → autoritativo. Confírmala con `dig +trace learn.microsoft.com` desde `lab-net` y explica por qué `+trace` no pasa por tu `dnsmasq`. ¿Qué diferencia hay entre un forwarder, un recursivo y un autoritativo? ¿Cuál es `dnsmasq` para `acme.lab` y cuál para `nginx.org`?
11. Añade un registro CNAME (`cname=www.acme.lab,web.acme.lab`) y un registro con TTL corto; recarga `dnsmasq` y comprueba con `dig` la sección ANSWER de cada uno. Explica cómo se haría lo mismo con una zona privada de Azure DNS enlazada a una VNet.

**Parte D — Reverse proxy con TLS (2-3 h)**

12. Backends: en `lab-net` crea dos directorios `/srv/backend1` y `/srv/backend2` con un `index.html` distinto cada uno ("backend 1 en lab-net" y "backend 2 en lab-net"), y dos unidades systemd (`backend1.service`, `backend2.service`) que ejecuten `python3 -m http.server 8081 --bind 10.10.20.1` y `... 8082 --bind 10.10.20.1` (reutiliza lo aprendido en el curso anterior). Comprueba desde `lab-so` con `curl http://backend.acme.lab:8081` y `nc -zv backend.acme.lab 8082`, y en `lab-net` con `ss -tlnp | grep 808`. Añade en `ufw` de `lab-net` las reglas mínimas para que solo `10.10.10.0/24` llegue a esos puertos.
13. Certificado autofirmado en `lab-so`: `sudo openssl req -x509 -newkey rsa:2048 -nodes -days 365 -keyout /etc/ssl/private/web.acme.lab.key -out /etc/ssl/certs/web.acme.lab.crt -subj "/CN=web.acme.lab" -addext "subjectAltName=DNS:web.acme.lab,DNS:www.acme.lab"`. Inspecciónalo con `openssl x509 -in ... -noout -text`: identifica emisor, sujeto, validez, SAN, clave pública, firma. Explica por qué "autofirmado" significa que emisor y sujeto coinciden y por qué un navegador desconfía de él aunque el cifrado sea perfectamente válido. Fija permisos `600` a la clave y explica por qué.
14. Configura en `lab-so` `/etc/nginx/sites-available/web.acme.lab` con: un `server` en `:80` que redirige (301) a HTTPS; un `server` en `:443 ssl` con `server_name web.acme.lab www.acme.lab`, el certificado y la clave, `ssl_protocols TLSv1.2 TLSv1.3`, y `location / { proxy_pass http://10.10.20.1:8081; proxy_set_header Host $host; proxy_set_header X-Forwarded-For $remote_addr; proxy_set_header X-Forwarded-Proto $scheme; }`. Añade `add_header X-Servido-Por $hostname always;`. Activa el sitio, `nginx -t`, recarga, abre 443 en `ufw`.
15. Pruebas desde `lab-so` y desde `lab-net` (que también resuelve `web.acme.lab` si su `/etc/hosts` o `dnsmasq` lo dice): `curl -I http://web.acme.lab` (301), `curl -k https://web.acme.lab` (contenido del backend 1), `curl https://web.acme.lab` (fallo de verificación: lee el error y explícalo), `curl --cacert /etc/ssl/certs/web.acme.lab.crt https://web.acme.lab` (funciona: explica por qué), `curl -kv https://web.acme.lab -o /dev/null 2>&1 | grep -iE "SSL connection|subject|issuer|expire|X-Servido"`, `curl -k --resolve web.acme.lab:443:10.10.10.10 https://web.acme.lab` (explica para qué sirve `--resolve` cuando el DNS aún no está listo). Mira en `lab-net` el `access.log` de `python3 -m http.server`: ¿qué IP origen ve el backend? ¿Cómo sabría el backend la IP real del cliente?
16. `openssl s_client -connect web.acme.lab:443 -servername web.acme.lab </dev/null`: identifica `Verify return code` (y qué significa 18), la cadena, el protocolo y la suite negociados. Repite con `-tls1_1` (debe fallar), `-tls1_3`, y `-servername otro.acme.lab` (¿cambia algo? explica el SNI). Con `-showcerts` extrae el certificado y compara su huella (`openssl x509 -fingerprint -sha256`) con la del archivo en disco. Explica en 8-10 líneas el handshake TLS 1.3 con lo que ves.

**Parte E — Balanceo con upstream (60-90 min)**

17. Cambia el `proxy_pass` para usar un bloque `upstream backends { server 10.10.20.1:8081; server 10.10.20.1:8082; }`. Recarga y ejecuta `for i in $(seq 1 10); do curl -sk https://web.acme.lab; done`: deberías ver alternancia (round robin). Añade `add_header X-Upstream $upstream_addr always;` y compruébalo con `curl -kI`. Prueba `weight=3` en uno, `least_conn`, e `ip_hash`, y explica cuándo usarías cada uno (piensa en sesiones).
18. Tolerancia a fallos: `systemctl stop backend2` en `lab-net` y repite el bucle. Anota cuántas peticiones fallan (502) antes de que nginx marque el servidor como caído; añade `max_fails=2 fail_timeout=10s` y `proxy_next_upstream error timeout http_502;` y repite. Lee `/var/log/nginx/error.log` y explica la línea "upstream prematurely closed" o "connect() failed". Vuelve a arrancar `backend2`. Explica la diferencia entre este balanceo de capa 7 y un balanceador de capa 4 (Azure Load Balancer) y por qué Application Gateway es "un nginx gestionado".

**Parte F — Capturar y leer tráfico con tcpdump (90 min)**

19. En `lab-net`, captura en la interfaz de `acme-a` mientras desde `lab-so` haces `curl http://backend.acme.lab:8081` (en claro, directamente al backend): `sudo tcpdump -ni <iface> -c 30 -w /tmp/http-claro.pcap host 10.10.10.10 and port 8081`. Léelo con `tcpdump -nr /tmp/http-claro.pcap` y con `-A`: identifica el handshake (`[S]`, `[S.]`, `[.]`), la petición `GET / HTTP/1.1` legible, la respuesta `200 OK` y el cierre (`[F.]`). Anota números de secuencia relativos y explica qué es cada flag.
20. Repite capturando en `lab-so` el tráfico a `443` mientras haces `curl -k https://web.acme.lab`: `sudo tcpdump -ni <iface-acme-a> -w /tmp/tls.pcap port 443`. Con `tcpdump -nr /tmp/tls.pcap -A | head -60` localiza el `ClientHello` y comprueba que el nombre `web.acme.lab` (SNI) viaja **en claro** y que el resto no es legible. Explica qué implica eso para la privacidad y qué es ECH/DoH a nivel conceptual (una búsqueda en Cloudflare basta).
21. Captura DNS en `lab-net`: `sudo tcpdump -ni <iface-acme-a> -c 10 port 53` mientras `lab-so` hace `dig web.acme.lab` y `dig nginx.org`. Identifica consulta y respuesta (`A?`, `A 10.10.10.10`), el ID de transacción y el puerto origen aleatorio. Explica por qué DNS usa UDP y cuándo cambia a TCP.
22. Filtros: escribe y explica cinco filtros `pcap-filter` útiles para un incidente (por ejemplo, "todo lo que no sea SSH", "solo SYN sin ACK hacia el puerto 443", "tráfico entre dos hosts concretos", "ICMP unreachable", "DNS que no venga de mi forwarder"). Opcional: copia los `.pcap` al anfitrión con `scp` y ábrelos en Wireshark; captura de pantalla de la vista "Follow TCP Stream" del tráfico en claro.

**Parte G — Ocho averías con método (3-4 h)**

Método obligatorio para cada avería, documentado en una tabla: síntoma reproducible (comando y salida) → hipótesis por capa (L1-L2 enlace/ARP, L3 IP/rutas/NAT, DNS, L4 puerto/firewall, L7 TLS/HTTP/proxy) → prueba que confirma o descarta cada hipótesis, con la herramienta elegida → punto de rotura y causa raíz → corrección mínima → verificación → qué log o métrica lo habría delatado antes.

Escribe primero un script `romper.sh` en el que cada avería es una función numerada (se ejecuta con `sudo ./romper.sh N` y no imprime nada), y `reparar.sh` con la corrección de cada una. Después ejecuta `sudo ./romper.sh $((RANDOM % 8 + 1))` **sin mirar el número**, diagnostica a ciegas, y solo al final comprueba con qué número lo rompiste. Repite hasta haber pasado por las ocho. Las averías (repártelas entre las dos VMs; si una función necesita ejecutarse en `lab-net`, hazlo por SSH desde el script o manualmente):

23. **Gateway.** `lab-so` pierde la ruta por defecto (`ip route del default`). Síntoma: la red interna funciona, Internet no.
24. **Ruta estática.** `lab-so` pierde la ruta a `10.10.20.0/24`. Síntoma: nginx devuelve 502 con ambos backends arriba.
25. **DNS interno.** `dnsmasq` parado. Síntoma: `curl https://web.acme.lab` falla por nombre pero `curl -k --resolve ...` funciona.
26. **DNS externo.** Forwarders de `dnsmasq` cambiados a una IP muerta. Síntoma: `acme.lab` resuelve, `nginx.org` no; `ping 1.1.1.1` funciona.
27. **Backend a medias.** `backend2` parado sin `max_fails` configurado. Síntoma: una de cada dos peticiones falla.
28. **Backend escuchando en la interfaz equivocada.** `backend1` arrancado con `--bind 127.0.0.1`. Síntoma: `ss -tlnp` en `lab-net` muestra el puerto abierto pero `nc -zv` desde `lab-so` da "connection refused".
29. **Firewall.** En `lab-net`, `ufw` deja de permitir `8081`/`8082` desde `10.10.10.0/24`. Síntoma: `nc -zv` se queda en timeout (no "refused"); explica la diferencia entre ambos síntomas y qué te dice cada uno.
30. **TLS.** Certificado regenerado con `CN=otro.acme.lab` sin SAN correcto. Síntoma: `curl --cacert` falla con "does not match", `openssl s_client` lo muestra en `subject`.
31. **Extra (NAT).** En `lab-net`, `ip_forward=0` o regla `masquerade` eliminada. Síntoma: `lab-so` alcanza `lab-net` pero nada más allá; `tcpdump` en `lab-net` muestra los paquetes entrando y no saliendo (o saliendo sin traducir).

**Parte H — Equivalencias con la nube y cierre (60 min)**

32. Completa una tabla con al menos 10 filas: componente de tu laboratorio → Azure → AWS → GCP → qué hace. Incluye: red interna `acme-a`/`acme-b` (VNet/subred), ruta estática (UDR / route table), `ip_forward` en `lab-net` (NVA / IP forwarding en la NIC), masquerade (NAT Gateway), `ufw` (NSG / Security Group / firewall rules), `dnsmasq` (Azure DNS zona privada / Route 53 privada / Cloud DNS), nginx reverse proxy TLS (Application Gateway / ALB / HTTPS Load Balancer), `upstream` capa 4 (Azure Load Balancer / NLB), certificado autofirmado (Key Vault + CA pública), `tcpdump` (Network Watcher packet capture / VPC Flow Logs).
33. Restaura las dos VMs al estado sano (`reparar.sh` completo), verifica el flujo entero (`dig`, `curl -k https://web.acme.lab` alternando backends, `openssl s_client`) y haz el snapshot "fin-redes-intermedio". Deja `lab-so` con el adaptador NAT reconectado y la ruta por defecto original (la usarás en los cursos siguientes); puedes apagar `lab-net`.

### Resultado esperado

- `laboratorio-redes-intermedio.md` con las ocho partes, el plan de direccionamiento, el diagrama de topología, las salidas explicadas y la tabla de las ocho averías (más la extra si la hiciste).
- Carpeta `config/` con: `netplan` de ambas VMs, `nftables.conf`, `acme.conf` de `dnsmasq`, el sitio de nginx, las unidades de los backends, `romper.sh` y `reparar.sh`.
- Carpeta `capturas-pcap/` con `http-claro.pcap`, `tls.pcap`, `dns.pcap` y las capturas de pantalla (Wireshark opcional).
- La tabla de equivalencias Azure/AWS/GCP.

### Criterios de validación

- [ ] Parte A: el plan de direcciones es correcto (hosts, subredes `/26`, respuesta razonada a los "qué pasaría si"); `ip route get` está explicado; el snapshot base existe.
- [ ] Parte B: la ruta estática es persistente; la captura demuestra el antes y el después del masquerade (IP origen distinta); DNAT y reverse proxy están correctamente diferenciados.
- [ ] Parte C: `dig` distingue respuestas locales, reenviadas y de caché con evidencia del log de `dnsmasq`; el diagrama de resolución es correcto; se explica por qué `+trace` salta el forwarder.
- [ ] Parte D: el certificado tiene SAN; la redirección 80→443 funciona; se explican los tres resultados de `curl` (con `-k`, sin nada, con `--cacert`); `s_client` está interpretado (verify code, protocolo, SNI).
- [ ] Parte E: la alternancia round robin y el comportamiento con un backend caído (antes y después de `max_fails`) están documentados con salidas reales.
- [ ] Parte F: en las capturas se identifican handshake TCP, petición HTTP en claro, `ClientHello` con SNI y consulta/respuesta DNS; los cinco filtros son correctos y útiles.
- [ ] Parte G: las ocho averías siguen el método, la capa y la causa raíz son correctas, y `romper.sh`/`reparar.sh` funcionan; hay evidencia de al menos tres diagnósticos "a ciegas".
- [ ] Parte H: la tabla tiene al menos 10 filas correctas.
- [ ] En una llamada con el mentor, el estudiante diagnostica en menos de 15 minutos una avería que el mentor le indique por número, explicando cada comando antes de ejecutarlo.

## Entrega

En tu repositorio de entregas, carpeta `02-modulo-intermedio/02-networking-intermedio-y-troubleshooting/`:

1. `laboratorio-redes-intermedio.md`.
2. `config/` (sin claves privadas: **no subas** `web.acme.lab.key`; el `.crt` sí puede ir).
3. `capturas-pcap/` y `capturas/`.
4. `equivalencias-cloud.md` (o dentro del laboratorio).
5. `ENTREGA.md` con evaluación, checklist y uso de IA.

Nota sobre IA: es buena idea pedirle a la IA que te explique una salida de `tcpdump` o de `openssl s_client` que no entiendes. No le pidas "la causa" de una avería antes de haber escrito tu propia hipótesis: el método es lo que se evalúa.

## Evaluación

1. **Conceptual.** Explica qué hace el kernel cuando `lab-so` quiere enviar un paquete a `10.10.20.1`, a `10.10.10.1` y a `1.1.1.1`, leyendo su tabla de rutas. ¿Qué es la "ruta más específica" y por qué gana?
2. **Técnica.** Divide `172.16.40.0/22` en subredes para: 400 servidores, 120 backends, 50 sistemas de monitorización y 2 enlaces punto a punto. Justifica las máscaras y di cuánto espacio te sobra.
3. **Situacional.** Un backend en la red `acme-b` ve todas las peticiones con IP origen `10.10.10.10` y el equipo de seguridad pide la IP real de los clientes. Explica por qué pasa y dos formas de resolverlo (cabecera y protocolo/NAT).
4. **Conceptual.** Diferencia entre SNAT/masquerade, DNAT y un reverse proxy: quién cambia qué campo del paquete, quién termina la conexión TCP y qué ve el servidor destino en cada caso.
5. **Troubleshooting.** `curl https://web.acme.lab` tarda 30 segundos y falla con "Connection timed out", pero `curl -k --resolve web.acme.lab:443:10.10.10.10 https://web.acme.lab` funciona al instante. ¿Qué capa falla? ¿Con qué dos comandos lo confirmas?
6. **Conceptual.** Explica la diferencia entre un stub resolver, un forwarder con caché, un resolutor recursivo y un servidor autoritativo, usando tu laboratorio. ¿Por qué el TTL baja entre dos `dig` seguidos contra `dnsmasq` y no contra el autoritativo?
7. **Técnica.** Explica el `Verify return code: 18 (self-signed certificate)` de `openssl s_client`. ¿Qué tendrías que hacer para que fuera `0 (ok)` en tu laboratorio y qué se hace en producción (CA pública, ACME/Let's Encrypt, Key Vault)?
8. **Conceptual.** ¿Qué información viaja en claro en una conexión HTTPS y qué no? Menciona SNI, la IP destino y el DNS. ¿Qué cambia con DNS sobre HTTPS?
9. **Troubleshooting.** `nc -zv backend.acme.lab 8081` devuelve "Connection refused" desde `lab-so`, pero en `lab-net` `ss -tlnp` muestra el puerto 8081 escuchando. Da la causa más probable y cómo la confirmas con `ss`. ¿Qué habría cambiado en el síntoma si fuera el firewall?
10. **Situacional.** Tras un despliegue, una de cada tres peticiones a la web devuelve 502. Describe tu diagnóstico paso a paso (nginx `error.log`, `upstream`, `ss` en los backends, `curl` directo a cada backend) y qué cambiarías en la configuración de `upstream` para que el usuario no lo note.
11. **Técnica.** Escribe el filtro de `tcpdump` para capturar solo los intentos de conexión (SYN sin ACK) hacia el puerto 443 de `10.10.10.10` que no vengan de `10.10.10.1`, y explica cómo distinguirías en la captura un puerto cerrado (RST) de uno filtrado (silencio).
12. **Conceptual.** Compara round robin, `least_conn` e `ip_hash` y di cuál elegirías para una aplicación con sesión en memoria, para una API sin estado y para backends de distinta capacidad.
13. **Situacional.** Debes exponer la web en Azure con TLS, dos backends en una subred privada y sin que los backends tengan IP pública. Nombra los recursos de Azure equivalentes a cada pieza de tu laboratorio y di cuáles cobran por hora aunque no haya tráfico.
14. **Reflexión.** ¿Cuál de las averías te llevó más tiempo y qué hipótesis descartaste tarde? ¿Qué añadirías al método para no repetirlo?

## Checklist final

Antes de continuar, deberías poder:

- [ ] Diseñar direccionamiento con CIDR y leer y explicar una tabla de rutas con `ip r` e `ip route get`.
- [ ] Configurar rutas estáticas persistentes y reenvío IP en Linux.
- [ ] Explicar la cadena de resolución DNS y montar un `dnsmasq` con registros locales y forwarders.
- [ ] Configurar masquerade y DNAT con `nftables`/`iptables` y demostrar con `tcpdump` qué cambia.
- [ ] Generar un certificado autofirmado con SAN y explicar por qué no es confiable pese a cifrar bien.
- [ ] Configurar nginx como reverse proxy TLS y como balanceador con `upstream`, `max_fails` y cabeceras `X-Forwarded-*`.
- [ ] Interpretar `openssl s_client` (verify code, protocolo, cadena, SNI) y `curl -v`.
- [ ] Capturar con `tcpdump` usando filtros y leer handshake TCP, HTTP en claro, `ClientHello` y DNS.
- [ ] Distinguir "timeout" de "connection refused" y saber qué capa señala cada uno.
- [ ] Diagnosticar una avería de red desconocida con método en menos de 15 minutos y documentarla.
- [ ] Traducir cada pieza del laboratorio a su equivalente en Azure, AWS y GCP.
- [ ] Tener `lab-so` restaurada y con snapshot para los cursos siguientes.

---

*Recursos verificados el 2026-09-27 (existencia y vigencia de las URLs mediante búsqueda web y, cuando el cupo de búsqueda se agotó, mediante los repositorios oficiales de la documentación). Las páginas de Microsoft Learn se enlazan en `es-es` cuando se confirmó la traducción; en el resto se indica cómo cambiar el idioma. Si un enlace falla, abre un issue en este repositorio.*
