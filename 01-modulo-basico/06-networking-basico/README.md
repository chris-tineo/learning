# Networking Básico

> Módulo: Básico · Curso 6 de 9 · Duración estimada: 15-20 horas · Estado: ✅ Completo

## Objetivo

En la nube, casi todo problema que no es de permisos es de red. "La aplicación no responde", "la base de datos no conecta", "el certificado falla", "desde la oficina sí pero desde casa no": detrás hay una IP, una máscara, una ruta, un puerto, un DNS o un firewall. Cuando llegues a Azure vas a dibujar redes virtuales, subredes, reglas de seguridad y balanceadores, y todo eso son los mismos conceptos que en la red de tu casa.

Este curso enseña **cómo viajan los datos de una máquina a otra** y te da un método para averiguar dónde se rompe el camino cuando algo falla. Verás qué es una red, cómo se identifican las máquinas (IP, MAC), cómo se nombran (DNS), cómo reciben configuración (DHCP), cómo se dividen las redes (máscaras, subredes), cómo se conectan entre sí (switches, routers, NAT) y cómo hablan las aplicaciones (TCP, UDP, puertos, HTTP/HTTPS). Y sobre todo practicarás con las herramientas que ya conoces de Windows y Linux (`ping`, `traceroute`, `nslookup`, `ipconfig`, `ip`) hasta que diagnosticar conectividad sea un reflejo.

**Antes de empezar** necesitas Windows Básico y Linux Básico: ya sabes usar `ipconfig`, `ping`, `tracert` y `nslookup` en Windows, y tienes la VM `lab-so` con SSH funcionando. Este curso les da el fundamento teórico y añade la práctica entre dos máquinas.

### Al terminar este curso deberías poder

- Explicar qué es una red, y distinguir LAN, WAN e Internet.
- Explicar qué es una dirección IPv4, qué es la máscara de subred y cómo se determina si dos IPs están en la misma red.
- Distinguir direcciones IP públicas y privadas, y explicar qué es NAT y por qué existe.
- Explicar la función de la puerta de enlace (gateway), de un switch y de un router, y en qué capa trabaja cada uno.
- Explicar qué es una dirección MAC y en qué se diferencia de una IP.
- Explicar cómo funciona DNS (resolución de nombres) y DHCP (asignación automática de direcciones), y qué pasa cuando fallan.
- Diferenciar TCP y UDP y explicar qué es un puerto, con ejemplos (80, 443, 22, 53, 3389).
- Explicar el modelo cliente-servidor y qué ocurre, paso a paso, cuando escribes una URL en el navegador (DNS → TCP → HTTP/HTTPS).
- Explicar qué hace un firewall y leer una regla sencilla (origen, destino, puerto, permitir/denegar).
- Hacer subnetting introductorio: calcular red, broadcast, rango de hosts y número de hosts de una red `/24`, `/25`, `/26`, `/27`, `/28`.
- Diagnosticar por capas un fallo de conectividad con `ping`, `traceroute`/`tracert`, `nslookup`/`dig`, `ipconfig`/`ip` y `ss`, y decir en qué punto se rompe.

## Prerrequisitos

- Curso 4: Windows Básico.
- Curso 5: Linux Básico (VM `lab-so` con SSH).
- Un anfitrión Windows (o macOS/Linux) y la VM Linux en la misma red (adaptador puente en VirtualBox, o red interna/NAT con dos VMs).
- Opcional: una segunda VM Linux (Ubuntu Server, 1 GB de RAM) para los ejercicios entre máquinas. Si no, se usan anfitrión + VM.

## Temario

- Qué es una red.
- LAN.
- WAN.
- Internet.
- IPv4.
- Direcciones IP públicas y privadas.
- Máscara.
- Gateway.
- MAC Address.
- DNS.
- DHCP.
- TCP.
- UDP.
- Puertos.
- Switches.
- Routers.
- Firewalls.
- NAT.
- Modelo cliente-servidor.
- HTTP y HTTPS.
- Routing introductorio.
- Subnetting introductorio.

**Herramientas:** `ping`, `traceroute`, `tracert`, `nslookup`, `ipconfig`, `ip`.

## Recursos en español

### Conceptos básicos de redes (Networking Basics) — Cisco Networking Academy
- **URL:** https://www.netacad.com/es/courses/networking-basics
- **Autor / organización:** Cisco Networking Academy
- **Idioma:** Español (también en inglés)
- **Tipo:** Curso online autoguiado con simulaciones en Packet Tracer
- **Duración aproximada:** 22 h (puedes hacerlo en 12-15 h si ya dominas Windows y Linux; los módulos de configuración de routers domésticos se pueden leer por encima)
- **Cubre:** Todo el temario: redes, LAN/WAN, IPv4, máscaras, públicas/privadas, gateway, MAC, DNS, DHCP, TCP/UDP, puertos, switches, routers, NAT, cliente-servidor, HTTP, routing y subnetting introductorio.
- **Nivel:** Introductorio
- **Acceso:** Gratuito, requiere cuenta gratuita en netacad.com (la misma de los cursos anteriores). Da una insignia digital.
- **Por qué lo recomiendo:** Es el recurso principal del curso. Cisco es la referencia mundial en formación de redes y este curso es la puerta de entrada gratuita a su itinerario. Incluye laboratorios con Packet Tracer (simulador gratuito de redes), que te permite "cablear" redes y ver los paquetes viajar sin hardware.

### Curso de Redes Informáticas desde Cero — Contando Bits (Kike Gandía)
- **URL:** https://www.youtube.com/playlist?list=PLG1hKOHdoXkvFy_6g4_zf7mgq4kEu8V9H
- **Autor / organización:** Contando Bits, canal de Kike Gandía (ingeniero de ciberseguridad)
- **Idioma:** Español
- **Tipo:** Lista de reproducción de vídeos
- **Duración aproximada:** 3-4 h en total (vídeos de 10-20 min)
- **Cubre:** Qué es una red, historia de Internet, modelo OSI/TCP-IP, IP, máscaras, DNS, DHCP, TCP/UDP, puertos, NAT, dispositivos de red.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Explicaciones en español claras y con animaciones, sin errores conceptuales relevantes, y orientadas a entender cómo viaja un paquete. Es el complemento en vídeo del curso de Cisco; míralo para tener la visión general antes de entrar en la teoría.

### Configuración de la conectividad de red IP — Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/training/modules/configure-ip-network-connectivity/
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Módulo de aprendizaje
- **Duración aproximada:** 45-60 min (ya lo viste en Windows Básico; aquí interesan las unidades de IPv4, subredes, direcciones públicas/privadas y DHCP)
- **Cubre:** IPv4, máscara, subredes, públicas/privadas, DHCP, herramientas de diagnóstico en Windows.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la explicación oficial de Microsoft de los conceptos de direccionamiento, la misma que usarás luego en las redes virtuales de Azure. Sirve de puente entre este curso y el de Cloud.

### Introducción a los servicios básicos de red de Azure — Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/training/paths/intro-to-azure-network-foundation-services/
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Ruta de aprendizaje
- **Duración aproximada:** 1-2 h (solo lectura conceptual; no hace falta cuenta de Azure para leerla)
- **Cubre:** IP públicas y privadas, subredes, DNS, NAT y paquetes, en el contexto de Azure.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Complementario y opcional. Sirve para ver, ya al final del curso, cómo todo lo aprendido se traduce literalmente a la nube (subredes, DNS privado, NAT Gateway). No hagas los ejercicios prácticos todavía: eso llega en el curso 8.

### Wikipedia en español: Modelo TCP/IP, TCP, Dirección IP, Máscara de red
- **URL:** https://es.wikipedia.org/wiki/Modelo_TCP/IP · https://es.wikipedia.org/wiki/Protocolo_de_control_de_transmisi%C3%B3n
- **Autor / organización:** Wikipedia en español
- **Idioma:** Español
- **Tipo:** Artículos de referencia
- **Duración aproximada:** 15-20 min cada uno, lectura selectiva
- **Cubre:** Modelo por capas, TCP frente a UDP.
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Referencia rápida en español para repasar definiciones. No es la fuente principal.

## Recursos en inglés

### Networking Fundamentals (Module 1) — Practical Networking (Ed Harmoush)
- **URL:** https://www.youtube.com/playlist?list=PLIFyRwBY_4bRLmKfP1KnZA6rZbRHtxmXi · Web con índice: https://www.practicalnetworking.net/index/networking-fundamentals-how-data-moves-through-the-internet/
- **Autor / organización:** Ed Harmoush, ingeniero de redes (Practical Networking)
- **Idioma:** Inglés (subtítulos)
- **Tipo:** Serie de vídeos
- **Duración aproximada:** ~3 h
- **Cubre:** Hosts, IP, redes, switches, routers, modelo OSI con perspectiva práctica, ARP y MAC, cómo dos hosts se comunican en la misma red y en redes distintas, DNS, DHCP, TCP/UDP, HTTP/HTTPS/TLS.
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la serie que mejor explica **cómo se mueve realmente un paquete** de un host a otro, con diagramas paso a paso. Es la explicación que hace "clic" con el gateway, la MAC y la tabla de rutas. Complementa perfectamente a Cisco, que es más enciclopédico.

### Computer Networks (#28) y The Internet (#29) — Crash Course Computer Science
- **URL:** https://www.youtube.com/watch?v=3QhU9jd03a0 · https://www.youtube.com/watch?v=AEaKrq3SpW8
- **Autor / organización:** CrashCourse (PBS Digital Studios)
- **Idioma:** Inglés (subtítulos)
- **Tipo:** Vídeos
- **Duración aproximada:** 12 min cada uno
- **Cubre:** LAN, Ethernet, MAC, switches, routers, conmutación de paquetes, IP, TCP/UDP, DNS, capas.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Dos vídeos para tener el mapa completo en 25 minutos antes de entrar en detalle. Ideal como primer paso del curso.

### Computers and the Internet: The Internet — Khan Academy
- **URL:** Vídeo "IP addresses and DNS" (con Vint Cerf): https://www.khanacademy.org/computing/computers-and-internet/xcae6f4a7ff015e7d:the-internet/xcae6f4a7ff015e7d:addressing-the-internet/v/the-internet-ip-addresses-and-dns · Artículo "IP packets": https://www.khanacademy.org/computing/computers-and-internet/xcae6f4a7ff015e7d:the-internet/xcae6f4a7ff015e7d:routing-with-redundancy/a/ip-packets · Artículo "Internet routing protocol": https://www.khanacademy.org/computing/computers-and-internet/xcae6f4a7ff015e7d:the-internet/xcae6f4a7ff015e7d:routing-with-redundancy/a/internet-routing
- **Autor / organización:** Khan Academy (vídeos de Code.org)
- **Idioma:** Inglés
- **Tipo:** Vídeos, artículos y ejercicios con corrección automática
- **Duración aproximada:** 1,5-2 h para la unidad "The Internet"
- **Cubre:** IP, DNS, paquetes, routing, TCP/UDP, HTTP, capas.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Tiene ejercicios de práctica con corrección (por ejemplo, sobre direcciones IP y paquetes), que ningún otro recurso de la lista ofrece. Úsalo para comprobar que entiendes antes del laboratorio.

### Cloudflare Learning Center: DNS — Cloudflare
- **URL:** https://www.cloudflare.com/learning/dns/what-is-dns/ · https://www.cloudflare.com/learning/dns/dns-server-types/ · https://www.cloudflare.com/learning/dns/dns-records/ (existe versión en español del Learning Center en https://www.cloudflare.com/es-la/learning/ ; muchos artículos están traducidos)
- **Autor / organización:** Cloudflare
- **Idioma:** Inglés (parcialmente en español)
- **Tipo:** Artículos explicativos
- **Duración aproximada:** 30-45 min
- **Cubre:** DNS en detalle: resolutor, servidores raíz, TLD, autoritativos, tipos de registro (A, AAAA, CNAME, MX, NS).
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Cloudflare opera uno de los mayores DNS del mundo (1.1.1.1) y sus explicaciones son las más claras que existen sobre DNS. Lo que aprendas aquí lo usarás en Azure DNS y en cada troubleshooting de tu carrera.

### Professor Messer's CompTIA Network+ N10-009 Training Course — Professor Messer
- **URL:** https://www.professormesser.com/network-plus/n10-009/n10-009-video/n10-009-training-course/
- **Autor / organización:** Professor Messer (James Messer)
- **Idioma:** Inglés
- **Tipo:** Curso en vídeo (87 vídeos, ~13 h)
- **Duración aproximada:** Para este curso, secciones 1.x "Networking Concepts" (~4 h)
- **Cubre:** Modelo OSI, dispositivos, IPv4, subnetting, puertos y protocolos, DNS, DHCP, NAT, routing.
- **Nivel:** Introductorio-intermedio (nivel certificación Network+)
- **Acceso:** Libre (vídeos gratuitos; notas y exámenes de práctica de pago, no necesarios)
- **Por qué lo recomiendo:** Complementario, para quien quiera profundizar o plantearse Network+ más adelante. Su vídeo de subnetting es una de las mejores explicaciones que existen del tema.

## Documentación oficial

El networking básico se apoya en estándares (RFC) y en la documentación de los sistemas operativos:

- **RFC 1918 — Address Allocation for Private Internets** (qué rangos son privados): https://www.rfc-editor.org/rfc/rfc1918 (léelo: son 9 páginas y es el documento que define 10.0.0.0/8, 172.16.0.0/12 y 192.168.0.0/16).
- **Ubuntu Server — Configuring networks (comando `ip`):** https://ubuntu.com/server/docs/explanation/networking/configuring-networks/
- **Linux man pages:** `ip` (https://man7.org/linux/man-pages/man8/ip.8.html), `ss`, `ping`, `traceroute`, `dig`, `nslookup` en https://man7.org/linux/man-pages/
- **Microsoft Learn — Referencia de comandos de Windows:** https://learn.microsoft.com/es-es/windows-server/administration/windows-commands/windows-commands (`ipconfig`, `ping`, `tracert`, `nslookup`, `route`, `netstat`, `arp`)
- **Microsoft Learn — Fundamentos de redes de Azure (documentación):** https://learn.microsoft.com/es-es/azure/networking/fundamentals/ (solo lectura conceptual por ahora)
- **Wireshark — User's Guide:** https://www.wireshark.org/docs/wsug_html_chunked/ (herramienta opcional del laboratorio)
- **Cisco Packet Tracer (descarga y curso introductorio gratuito):** https://www.netacad.com/courses/getting-started-cisco-packet-tracer?courseLang=en-US

## Ruta recomendada de estudio

1. **Ver** Crash Course #28 y #29 (25 min). Mapa general.
2. **Ver** los primeros vídeos de Contando Bits (qué es una red, IP, máscara, DNS, DHCP, TCP/UDP, puertos, NAT) (2 h). Anota las dudas.
3. **Inscribirte** en "Conceptos básicos de redes" de Cisco y **hacer** los módulos de comunicación en red, componentes, IPv4, direccionamiento, DHCP, DNS, protocolos de transporte y aplicación (8-10 h, repartidas en una o dos semanas). Haz todos los laboratorios de Packet Tracer que aparecen: instala Packet Tracer con el curso gratuito "Getting Started with Cisco Packet Tracer".
4. **Ver** Practical Networking, lecciones 1 a 4 (hosts, dispositivos, OSI, cómo se comunican dos hosts en la misma red y en redes distintas) (90 min). Este es el bloque que hace que gateway, MAC y ARP cobren sentido. Después las lecciones sobre DNS, DHCP, TCP/UDP y HTTP/HTTPS (60 min).
5. **Leer** Cloudflare "What is DNS?", "DNS server types" y "DNS records" (45 min).
6. **Leer** la RFC 1918 (30 min) y las unidades de IPv4, subredes y públicas/privadas del módulo de Microsoft Learn (30 min).
7. **Practicar subnetting** a mano (60-90 min): con la sección de subnetting del curso de Cisco o el vídeo de Professor Messer, y comprueba tus resultados con una calculadora de subredes solo **después** de calcular. Objetivo mínimo: redes `/24` a `/28`.
8. **Hacer** los ejercicios de la unidad "The Internet" de Khan Academy (60 min) para comprobar la comprensión.
9. **Hacer el laboratorio** (5-7 h).
10. Opcional: **leer** la ruta "Introducción a los servicios básicos de red de Azure" (1-2 h) para ver cómo se traduce todo a la nube.
11. **Responder la evaluación** y **revisar el checklist**.

## Laboratorio

### Objetivo

Analizar la red real en la que están tu anfitrión y tu VM (direcciones, máscara, gateway, MAC, DNS, DHCP, rutas, puertos abiertos), hacer subnetting sobre ella, seguir el camino de un paquete hasta Internet y diagnosticar cuatro averías provocadas hasta identificar en qué capa y en qué punto se rompe la comunicación.

### Requisitos

- Anfitrión (Windows recomendado; vale macOS/Linux) y VM `lab-so` con `nginx` y `ssh` del curso anterior, ambas en la **misma red** (adaptador puente en VirtualBox).
- En la VM: `sudo apt install -y traceroute dnsutils net-tools` (para `traceroute`, `dig`, `netstat`; `ip` y `ss` ya vienen).
- Opcional: Wireshark en el anfitrión (gratuito) para la parte F.
- Packet Tracer instalado (gratuito vía NetAcad) para la parte E.
- Documenta todo en `laboratorio-redes.md`, con comandos y salidas como texto.

### Instrucciones

**Parte A — Radiografía de tu red (60 min)**

1. En el **anfitrión Windows**: `ipconfig /all`, `route print -4`, `arp -a`, `netstat -ano | findstr LISTENING`. En la **VM Linux**: `ip -br a`, `ip a`, `ip r`, `ip neigh`, `resolvectl status` (o `cat /etc/resolv.conf`), `ss -tulnp`. Con macOS: `ifconfig`, `netstat -rn`, `arp -a`, `scutil --dns`, `lsof -iTCP -sTCP:LISTEN`.
2. Rellena esta tabla para las dos máquinas:

   | Dato | Anfitrión | VM |
   |---|---|---|
   | Dirección IPv4 | | |
   | Máscara (decimal y /CIDR) | | |
   | Dirección de red | | |
   | Dirección de broadcast | | |
   | Puerta de enlace | | |
   | Dirección MAC | | |
   | ¿Asignada por DHCP? Servidor DHCP y caducidad | | |
   | Servidores DNS | | |
   | ¿Privada o pública? ¿Qué rango RFC 1918? | | |
   | Puertos TCP en escucha (mín. 3) y qué servicio es cada uno | | |

3. Responde: ¿están anfitrión y VM en la misma red? Demuéstralo aplicando la máscara (escribe la operación en binario para un octeto). ¿Qué IP pública tiene tu red hacia Internet? (Consúltala en un servicio como https://www.cloudflare.com/learning/dns/glossary/what-is-my-ip-address/ o con `curl ifconfig.me` desde la VM). ¿Por qué es distinta de tu IP privada? Explica NAT con tu caso.
4. Tabla ARP/vecinos: localiza la MAC de tu gateway y la de la otra máquina. Explica para qué sirve ARP y por qué la MAC del gateway aparece en tu tabla aunque tú "hables" con Internet.
5. Tabla de rutas: explica la ruta por defecto (`0.0.0.0/0` o `default`) y la ruta de tu red local. ¿Qué pasa con un paquete a `192.168.50.7` si tu red es `192.168.1.0/24`? ¿Y a una IP de tu red?

**Parte B — Subnetting sobre tu red (60-90 min)**

6. Toma la red de tu casa (por ejemplo `192.168.1.0/24`) y divídela **a mano**, mostrando el cálculo, en:
   - 2 subredes `/25`: para cada una, dirección de red, primer host, último host, broadcast, número de hosts útiles.
   - 4 subredes `/26`.
   - 8 subredes `/27`.
   - Después: ¿cuál es la máscara más pequeña (más hosts) que permite 4 subredes con al menos 50 hosts cada una? ¿Y 6 subredes con 20 hosts?
7. Diseña el direccionamiento de una oficina ficticia con la red `10.20.0.0/16`: subred de servidores (máximo 30 hosts), subred de empleados (250 hosts), subred de invitados Wi-Fi (100 hosts), subred de impresoras (10 hosts). Indica máscara, rango y gateway propuesto para cada una y justifica el tamaño. Solo después verifica con una calculadora online (por ejemplo https://subnetplus.com/es/calculator.html) y anota si te equivocaste en algo y por qué.
8. Explica con tus palabras por qué existen las direcciones privadas y NAT, y qué habría pasado sin ellas con IPv4.

**Parte C — Servicios: DNS, DHCP, TCP/UDP, HTTP (60 min)**

9. DNS paso a paso desde la VM (`dig`) y desde Windows (`nslookup`):
   - `dig learn.microsoft.com` y `nslookup learn.microsoft.com`: identifica la sección ANSWER, el tipo de registro, el TTL y qué servidor respondió.
   - `dig learn.microsoft.com CNAME`, `dig microsoft.com MX`, `dig microsoft.com NS`, `dig -x 1.1.1.1`. Explica cada tipo de registro y qué es una resolución inversa.
   - `dig +trace learn.microsoft.com`: identifica los servidores raíz, los TLD (`.com`) y el autoritativo. Relaciónalo con lo leído en Cloudflare.
   - Consulta el mismo nombre en dos resolutores distintos: `dig @1.1.1.1 ...` y `dig @8.8.8.8 ...`. ¿Cambia algo? ¿Por qué podría cambiar?
10. DHCP: en Windows, `ipconfig /release` seguido de `ipconfig /renew` (perderás la red unos segundos). Observa en `ipconfig /all` la nueva concesión. En la VM: `sudo journalctl -u systemd-networkd -n 50` o `journalctl | grep -i dhcp | tail -20`. Explica el proceso DORA (Discover, Offer, Request, Acknowledge) con lo que ves en los logs.
11. TCP, UDP y puertos:
    - Desde la VM: `ss -tulnp`. Clasifica cada puerto en TCP o UDP y di qué servicio hay detrás (22, 53, 80...).
    - Desde el anfitrión, comprueba con `Test-NetConnection <ip-vm> -Port 80` y `-Port 22` y `-Port 3389`. Explica qué significa "TcpTestSucceeded: True/False" en cada caso y por qué 3389 falla.
    - Desde la VM hacia el anfitrión: `nc -zv <ip-anfitrion> 445` y `nc -zv <ip-anfitrion> 3389` (instala `netcat-openbsd` si hace falta). ¿Qué puertos responde Windows y qué servicios son?
    - Explica por qué DNS usa UDP 53 principalmente y por qué HTTP usa TCP 80/443. ¿Qué servicio conocido usa UDP y no le importa perder paquetes?
12. HTTP y HTTPS:
    - `curl -v http://<ip-vm>` desde el anfitrión (o desde la VM `curl -v http://localhost`): identifica la línea de petición (`GET / HTTP/1.1`), las cabeceras y el código de respuesta (`200 OK`).
    - `curl -v https://learn.microsoft.com -o /dev/null 2>&1 | head -40`: identifica el handshake TLS, el certificado y su emisor. Explica en 5 líneas qué añade HTTPS a HTTP y qué papel juega el certificado.
    - `curl -I http://<ip-vm>/noexiste`: ¿qué código devuelve y qué significa?

**Parte D — El camino de un paquete (45 min)**

13. Desde la VM: `traceroute -n 1.1.1.1` y `traceroute -n learn.microsoft.com`. Desde Windows: `tracert -d 1.1.1.1`. Para cada traza identifica: tu gateway (salto 1), en qué salto dejas tu red privada (primera IP pública), cuántos saltos hay, dónde aparecen `*` y por qué eso no siempre es un fallo, y la latencia aproximada de cada tramo.
14. Escribe el recorrido completo de "escribo `https://learn.microsoft.com` en el navegador y aparece la página" en 10-15 pasos ordenados, mencionando: caché DNS, resolutor, raíz/TLD/autoritativo, ARP al gateway, NAT, routing, handshake TCP, handshake TLS, petición HTTP, respuesta. Puedes apoyarte en la lección de Practical Networking, pero escríbelo con tus palabras.

**Parte E — Packet Tracer (60-90 min)**

15. En Packet Tracer construye: 2 PCs y un servidor conectados a un switch, el switch a un router, y el router a un segundo switch con otro PC (dos redes: `192.168.10.0/24` y `192.168.20.0/24`). Configura IPs estáticas, máscaras y gateways. Activa DHCP en el router para la red 10 y DNS en el servidor con un registro `web.local` apuntando al propio servidor con servicio HTTP activado.
16. Comprueba con `ping` entre PCs de distinta red, abre `http://web.local` desde el navegador de un PC y usa el **modo simulación** para ver el paquete DNS (UDP) y después el HTTP (TCP) viajando. Captura al menos dos pantallas del modo simulación y explica qué muestran las capas de un paquete cuando lo abres (MAC origen/destino cambia en cada salto; IP origen/destino no).
17. Rompe algo a propósito (gateway incorrecto en un PC, o cable desconectado) y documenta qué síntoma da `ping` y cómo lo detectaste.

**Parte F — Cuatro averías provocadas (90 min)**

Para cada avería sigue el mismo método y documéntalo en una tabla: síntoma → hipótesis → comandos por capas (`ip`/`ipconfig` → `ping` gateway → `ping` IP externa → `nslookup`/`dig` → `Test-NetConnection`/`nc` puerto → `curl`) → punto de rotura → corrección → verificación.

18. **Avería 1 (capa 3, red):** en la VM, cambia temporalmente la IP a una de **otra** red, por ejemplo `sudo ip addr flush dev <iface> && sudo ip addr add 192.168.77.10/24 dev <iface>`. Intenta `ping` al gateway y a la otra máquina. Diagnostica. Restaura con `sudo netplan apply` o reiniciando la interfaz (`sudo dhclient <iface>` o reinicio de la VM).
19. **Avería 2 (ruta):** en la VM, borra la ruta por defecto: `sudo ip route del default`. Comprueba que `ping <ip-anfitrion>` funciona pero `ping 1.1.1.1` no. Diagnostica con `ip r` y explica. Restaura con `sudo ip route add default via <gateway>`.
20. **Avería 3 (DNS):** en la VM, apunta el resolutor a una IP que no responde (`sudo resolvectl dns <iface> 10.255.255.1` o editando `/etc/resolv.conf` temporalmente). Comprueba que `ping 1.1.1.1` funciona pero `ping learn.microsoft.com` y `curl` fallan. Demuestra con `dig @1.1.1.1 learn.microsoft.com` que Internet sí funciona. Restaura (`sudo resolvectl revert <iface>`).
21. **Avería 4 (puerto/firewall):** en la VM, activa el firewall permitiendo solo SSH: `sudo ufw allow 22/tcp && sudo ufw enable`. Desde el anfitrión: `ping` a la VM funciona, `ssh` funciona, `Test-NetConnection -Port 80` falla y el navegador no carga la web. Diagnostica y explica por qué "hay red" pero "no hay servicio". Mira `sudo ufw status verbose` y lee la regla. Corrige con `sudo ufw allow 80/tcp` y verifica. Deja el firewall activo con 22 y 80 permitidos.

**Parte G — Opcional: Wireshark (45 min)**

22. En el anfitrión, captura tráfico mientras haces `ping <ip-vm>`, `nslookup learn.microsoft.com` y `curl http://<ip-vm>`. Filtra con `icmp`, `dns`, `http` y `tcp.port == 80`. Identifica el handshake TCP (SYN, SYN-ACK, ACK), la consulta y respuesta DNS y la petición HTTP. Captura pantalla y explica.

### Resultado esperado

`laboratorio-redes.md` con las partes A-F (G opcional), la tabla de red, los cálculos de subnetting a mano, las salidas de `dig`/`nslookup`/`traceroute`/`ss`/`curl` explicadas, el archivo `.pkt` de Packet Tracer, la descripción paso a paso del viaje de un paquete y la tabla de diagnóstico de las cuatro averías.

### Criterios de validación

- [ ] Parte A: la tabla está completa y es coherente; la comprobación de "misma red" muestra la operación con la máscara; NAT está explicado con la IP pública real del estudiante.
- [ ] Parte B: los cálculos de subnetting están hechos a mano y son correctos (se acepta un error corregido y explicado); el diseño de la oficina cumple los tamaños con justificación.
- [ ] Parte C: se identifican correctamente tipos de registro DNS, TTL, resolutor; DORA se explica con evidencia de logs; TCP/UDP y puertos están bien clasificados; el análisis de `curl -v` identifica petición, respuesta, código y handshake TLS.
- [ ] Parte D: la traza está interpretada (gateway, salida a pública, `*`) y el recorrido del paquete tiene los pasos clave en orden correcto.
- [ ] Parte E: el `.pkt` funciona (ping entre redes y web por nombre) y las capturas del modo simulación están explicadas correctamente (MAC cambia por salto, IP no).
- [ ] Parte F: cada avería se localiza en la capa y punto correctos con los comandos que lo demuestran, y se restaura; el método es el mismo en las cuatro.
- [ ] El estudiante puede, ante una avería nueva planteada por el mentor en una llamada, decir qué comandos ejecutaría y en qué orden, sin consultar apuntes.

## Entrega

En tu repositorio de entregas, carpeta `01-modulo-basico/06-networking-basico/`:

1. `laboratorio-redes.md`.
2. `oficina.pkt` (Packet Tracer) y capturas del modo simulación en `capturas/`.
3. `subnetting.md` con los cálculos a mano (puede ser foto de papel legible + transcripción).
4. `ENTREGA.md` con evaluación, checklist y uso de IA.

## Evaluación

1. **Conceptual.** Explica la diferencia entre una dirección MAC y una dirección IP: quién las asigna, dónde se usan y por qué hacen falta las dos. ¿Por qué la MAC de destino cambia en cada salto y la IP de destino no?
2. **Técnica.** Dadas `192.168.4.130/26` y `192.168.4.190/26`, ¿están en la misma red? Muestra el cálculo. ¿Y `192.168.4.130/25` con `192.168.4.190/25`?
3. **Técnica.** Para la red `172.16.8.0/22`: dirección de red, broadcast, primer y último host, número de hosts útiles. ¿En cuántas `/24` se puede dividir?
4. **Conceptual.** ¿Qué es la puerta de enlace y cuándo la usa un host? Si un PC tiene IP y máscara correctas pero gateway incorrecto, ¿qué funciona y qué no?
5. **Conceptual.** Explica NAT con el ejemplo de tu casa: tres dispositivos navegando a la vez con una sola IP pública. ¿Cómo sabe el router a quién devolver cada respuesta?
6. **Situacional.** Un usuario dice "no tengo Internet". `ipconfig` muestra `169.254.10.5`. ¿Qué ha pasado, qué protocolo ha fallado y qué dos causas comprobarías primero?
7. **Situacional.** `ping 8.8.8.8` funciona, `ping google.com` falla con "no se puede resolver". Explica qué está roto, qué comando lo confirma y dos formas de arreglarlo (una temporal, otra definitiva).
8. **Situacional.** `ping` al servidor web funciona, pero el navegador no carga la página y `Test-NetConnection -Port 443` devuelve False. ¿En qué capa está el problema y cuáles son las tres causas más probables?
9. **Conceptual.** Diferencias entre TCP y UDP: da dos ejemplos de servicios que usan cada uno y explica por qué esa elección tiene sentido. ¿Qué es el handshake de tres vías?
10. **Conceptual.** ¿Qué hace DNS paso a paso cuando escribes un nombre que nadie en tu red ha consultado antes? Nombra los cuatro tipos de servidor implicados y explica qué es el TTL y por qué importa cuando cambias la IP de un servidor.
11. **Técnica.** Lee esta regla de firewall: "Permitir TCP desde 10.0.1.0/24 hacia 10.0.2.15 puerto 5432; denegar el resto". ¿Qué servicio se protege probablemente? ¿Puede un host `10.0.1.77` conectarse? ¿Y `10.0.3.5`? ¿Puede `10.0.1.77` hacer `ping` a `10.0.2.15`?
12. **Conceptual.** ¿Qué diferencia hay entre un switch y un router? ¿En qué capa trabaja cada uno y qué tabla consulta cada uno para decidir por dónde enviar una trama o un paquete?
13. **Troubleshooting.** `tracert` a un servidor se detiene en el salto 3 con `*` y no llega, pero el servidor responde a `ping` y la web carga. Explica cómo es posible.
14. **Conceptual.** ¿Qué añade HTTPS respecto a HTTP y qué papel tiene el certificado? Si el navegador avisa "certificado no válido", nombra dos causas posibles.
15. **Reflexión.** Describe tu método de diagnóstico por capas en 6-8 pasos genéricos y explica por qué empiezas siempre por lo más cercano (tu propia configuración) y no por "Internet está caído".

## Checklist final

Antes de continuar, deberías poder:

- [ ] Definir red, LAN, WAN e Internet, y explicar qué es una dirección IPv4 y una máscara.
- [ ] Decidir si dos IPs están en la misma red aplicando la máscara, y calcular red, broadcast y rango de hosts para `/24` a `/28`.
- [ ] Explicar direcciones privadas (RFC 1918), públicas y NAT.
- [ ] Explicar gateway, switch, router, MAC y ARP y en qué capa actúa cada uno.
- [ ] Explicar DNS (tipos de servidor, registros, TTL) y DHCP (DORA), y reconocer sus fallos.
- [ ] Distinguir TCP y UDP, explicar qué es un puerto y nombrar los puertos de SSH, DNS, HTTP, HTTPS y RDP.
- [ ] Describir el modelo cliente-servidor y el viaje completo de una petición HTTPS.
- [ ] Leer una regla de firewall sencilla y explicar por qué "hay red pero no hay servicio".
- [ ] Usar `ipconfig`/`ip`, `ping`, `tracert`/`traceroute`, `nslookup`/`dig`, `ss` y `Test-NetConnection`/`nc` para diagnosticar por capas.
- [ ] Construir y simular una red pequeña con dos subredes en Packet Tracer.
- [ ] Tener la VM con `ufw` activo permitiendo 22 y 80 para los cursos siguientes.

---

*Recursos verificados el 2026-09-26 mediante búsqueda web (existencia y vigencia de las URLs). Si un enlace falla, abre un issue en este repositorio.*
