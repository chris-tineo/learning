# Networking Cloud Avanzado

> Módulo: Avanzado · Curso 4 de 12 · Duración estimada: 30-40 horas · Estado: ✅ Completo

## Objetivo

En el Módulo Intermedio aprendiste a crear una VNet, una subred y un NSG, y a diagnosticar conectividad con `dig`, `tcpdump` y `traceroute`. En Arquitectura Cloud Avanzada dibujaste una landing zone con topología hub-spoke. Este curso es donde esa topología deja de ser un dibujo: vas a construirla con Terraform, a forzar el tráfico entre spokes a través de un cortafuegos que tú controlas, a hacer que un servicio PaaS (una cuenta de almacenamiento) solo sea alcanzable por IP privada, a resolver nombres privados desde una red "on-premises" (tu VM local) a través de un túnel VPN, y a romperlo todo a propósito para diagnosticarlo con Network Watcher.

El networking es la parte de la nube donde los errores son más silenciosos: no hay un log que diga "la UDR apunta a una IP que no existe" o "la resolución DNS está devolviendo la IP pública". Los paquetes simplemente desaparecen. Por eso el 60 % de este curso es práctica y la última parte del laboratorio es una batería de averías que tú mismo provocas.

Sobre el coste: los servicios de red empresariales de Azure (Azure Firewall, VPN Gateway, ExpressRoute, Application Gateway, Front Door) cuestan desde decenas hasta miles de dólares al mes. En este curso los estudias a fondo a nivel conceptual, comparas precios reales en la calculadora y los sustituyes en el laboratorio por equivalentes baratos y didácticos: una VM Linux con `iptables` como network appliance, `dnsmasq` como forwarder DNS y WireGuard como VPN site-to-site. Aprenderás lo mismo (y entenderás mejor qué hace el servicio gestionado por dentro) gastando unos pocos dólares.

**Antes de empezar** necesitas el curso de Terraform del Módulo Intermedio (azurerm, backend remoto) y Networking Intermedio (subnetting, routing, DNS, `tcpdump`). La VM local `lab-so` hará de "oficina on-premises".

### Al terminar este curso deberías poder

- Diseñar una topología hub-spoke con peering, explicar por qué el peering no es transitivo y qué implica para el direccionamiento y el enrutamiento.
- Escribir rutas definidas por el usuario (UDR) que fuercen el tráfico spoke-to-spoke y el de salida a Internet por una network virtual appliance (NVA), y explicar el orden en que Azure evalúa rutas de sistema, BGP y UDR.
- Configurar una VM Linux como NVA (IP forwarding, `iptables`, NAT) y justificar cuándo compensa frente a Azure Firewall.
- Exponer un servicio PaaS solo por red privada con Private Endpoint, Private DNS Zone y enlaces de VNet, y comprobar la resolución desde dentro y desde fuera de Azure.
- Explicar el flujo de resolución DNS en Azure (168.63.129.16, zonas privadas, servidores DNS personalizados, forwarders) y montar un forwarder para redes híbridas.
- Colocar un Azure Load Balancer Standard interno delante de dos VMs y distinguir cuándo usar Load Balancer, Application Gateway, Front Door o Traffic Manager.
- Comparar VPN Gateway, ExpressRoute y Virtual WAN (topología, ancho de banda, latencia, coste, tiempo de despliegue) y elegir con criterio para un escenario dado.
- Montar una VPN site-to-site con WireGuard entre tu red local y Azure y enrutar tráfico híbrido hacia los spokes.
- Diagnosticar fallos de red complejos (peering asimétrico, UDR mal apuntada, NSG que bloquea, DNS que resuelve a la IP pública) con Network Watcher, rutas efectivas y capturas de paquetes.
- Traducir cada servicio de red de Azure a su equivalente en AWS y GCP.

## Prerrequisitos

- Módulo Intermedio completo, en especial Networking Intermedio (subnetting, routing, DNS, `tcpdump`, `dig`), Administración de Azure (VNets, NSG, Load Balancer básico) y Terraform (azurerm, backend remoto, módulos básicos).
- Módulo Avanzado, curso 3: Arquitectura Cloud Avanzada (has diseñado un hub-spoke sobre papel).
- VM local `lab-so` operativa con acceso SSH desde el anfitrión y salida a Internet.
- Cuenta de Azure con presupuesto y alertas, Azure CLI y Terraform instalados en tu equipo.

## Temario

- VNet Peering.
- Hub-Spoke networking.
- Private Endpoints.
- Private Link.
- Private DNS.
- DNS forwarding.
- VPN.
- ExpressRoute.
- Azure Load Balancer.
- Application Gateway.
- WAF.
- Front Door.
- Routing.
- UDR.
- Network appliances.
- Hybrid networking.
- Troubleshooting complejo.

**Práctica:** resolver un escenario empresarial de conectividad privada e híbrida.

## Recursos en español

### Diseño e implementación de soluciones de red de Microsoft Azure (ruta AZ-700) — Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/training/paths/design-implement-microsoft-azure-networking-solutions-az-700/ · Guía de estudio del examen: https://learn.microsoft.com/es-es/credentials/certifications/resources/study-guides/az-700
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Ruta de aprendizaje con módulos y ejercicios
- **Duración aproximada:** 14-18 h completa; para este curso interesan los módulos de VNets y peering, enrutamiento, conectividad híbrida (VPN, ExpressRoute, Virtual WAN), balanceo de carga, Private Link y DNS privado, y supervisión de red (10-12 h)
- **Cubre:** Todo el temario
- **Nivel:** Avanzado
- **Acceso:** Libre; cuenta Microsoft gratuita para guardar progreso
- **Por qué lo recomiendo:** Es el material oficial de la certificación de ingeniería de redes de Azure y el único recurso en español que recorre el temario completo con diagramas actualizados. Es el recurso principal del curso. Los ejercicios que despliegan VPN Gateway o Application Gateway léelos sin ejecutarlos en tu suscripción: aquí se sustituyen por alternativas baratas.

### Arquitectura de la infraestructura de red en Azure — Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/training/paths/architect-network-infrastructure/
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Ruta de aprendizaje
- **Duración aproximada:** 4-5 h
- **Cubre:** Hub-spoke, peering, conectividad híbrida, balanceo, Private Link, con enfoque de arquitecto (cuándo usar qué)
- **Nivel:** Intermedio-avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la vista de diseño que complementa la vista de implementación de AZ-700. Se lee rápido y te da el vocabulario para justificar decisiones en la entrega.

### Enrutamiento del tráfico de redes virtuales y Emparejamiento de VNets — Microsoft Learn (documentación)
- **URL:** Enrutamiento: https://learn.microsoft.com/es-es/azure/virtual-network/virtual-networks-udr-overview · Peering: https://learn.microsoft.com/es-es/azure/virtual-network/virtual-network-peering-overview · Escenario UDR + gateway + NVA: https://learn.microsoft.com/es-es/azure/virtual-network/virtual-network-scenario-udr-gw-nva
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Documentación oficial
- **Duración aproximada:** 90 min de lectura atenta
- **Cubre:** Routing, UDR, network appliances, VNet peering
- **Nivel:** Avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** La página de enrutamiento es la más importante del curso: explica las rutas de sistema, cómo Azure elige entre rutas de sistema, BGP y UDR, y los tipos de siguiente salto. Léela antes de tocar una tabla de rutas y vuelve a ella en cada avería.

### Preparación para AZ-700 (Exam Readiness Zone) — Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/shows/exam-readiness-zone/preparing-for-az-700-design-and-implement-core-networking-infrastructure-1-of-5 (serie de 5 episodios enlazados desde esa página)
- **Autor / organización:** Microsoft
- **Idioma:** Página en español; los vídeos están en inglés con subtítulos
- **Tipo:** Vídeos cortos
- **Duración aproximada:** 5 episodios de 25-35 min
- **Cubre:** Repaso de todo el temario en formato "qué debes saber"
- **Nivel:** Intermedio-avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** Repaso rápido antes de la evaluación. Cada episodio termina con preguntas del estilo del examen que sirven para comprobar si has entendido los conceptos.

## Recursos en inglés

### Azure Master Class v3, Part 6: Networking — John Savill's Technical Training
- **URL:** https://www.youtube.com/watch?v=nDtCSQyG_I8
- **Autor / organización:** John Savill
- **Idioma:** Inglés (subtítulos automáticos)
- **Tipo:** Vídeo largo con pizarra
- **Duración aproximada:** 2 h 50 min
- **Cubre:** VNets, peering, NSG, UDR, NVAs, conectividad híbrida (VPN, ExpressRoute, Virtual WAN), Private Link, service endpoints, DNS, balanceadores
- **Nivel:** Avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la mejor explicación gratuita de "por qué" funciona así la red de Azure: dibuja cómo viaja un paquete, qué hace el host físico, por qué el peering no es transitivo y cómo se encadenan UDR y NVA. Verlo antes del laboratorio te ahorrará horas de depuración.

### Hub-spoke network topology in Azure — Azure Architecture Center
- **URL:** https://learn.microsoft.com/en-us/azure/architecture/networking/architecture/hub-spoke · Private Link en hub-spoke: https://learn.microsoft.com/en-us/azure/architecture/networking/guide/private-link-hub-spoke-network · Topología tradicional (Cloud Adoption Framework): https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/traditional-azure-networking-topology
- **Autor / organización:** Microsoft
- **Idioma:** Inglés
- **Tipo:** Arquitecturas de referencia
- **Duración aproximada:** 60-90 min
- **Cubre:** Hub-spoke, shared services, NVAs, Private Endpoints y DNS en hub-spoke
- **Nivel:** Avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la referencia que vas a implementar en el laboratorio, con las decisiones de diseño explicadas (dónde va el DNS, dónde van los Private Endpoints, por qué el cortafuegos vive en el hub). La guía de Private Link en hub-spoke resuelve la duda más frecuente: en qué VNet se crea la zona DNS privada y a cuáles se enlaza.

### Create a hub and spoke hybrid network topology in Azure using Terraform — Microsoft Learn
- **URL:** https://learn.microsoft.com/en-us/azure/developer/terraform/hub-spoke-introduction (serie de varios artículos)
- **Autor / organización:** Microsoft
- **Idioma:** Inglés
- **Tipo:** Tutorial paso a paso con código
- **Duración aproximada:** 2 h de lectura; no ejecutes su despliegue completo (incluye VPN Gateway, que cuesta dinero)
- **Cubre:** Hub-spoke con Terraform, NVA, UDR, peering, híbrido
- **Nivel:** Avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** Código Terraform oficial de una topología muy parecida a la del laboratorio. Úsalo como referencia de sintaxis (peering, tablas de rutas, NVA), no como plantilla para copiar: el laboratorio te pide una variante más barata y con decisiones propias.

### Azure Private Endpoint DNS integration — Microsoft Learn
- **URL:** https://learn.microsoft.com/en-us/azure/private-link/private-endpoint-dns-integration · Qué es un Private Endpoint: https://learn.microsoft.com/en-us/azure/private-link/private-endpoint-overview · DNS a escala (CAF): https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/private-link-and-dns-integration-at-scale
- **Autor / organización:** Microsoft
- **Idioma:** Inglés
- **Tipo:** Documentación oficial
- **Duración aproximada:** 60 min
- **Cubre:** Private Endpoints, Private Link, Private DNS, DNS forwarding
- **Nivel:** Avanzado
- **Acceso:** Libre
- **Por qué lo recomiendo:** Contiene los escenarios de DNS (solo Azure, redes emparejadas, on-premises con forwarder) que reproduces en el laboratorio y la tabla de nombres de zona `privatelink.*` por servicio. El 90 % de los problemas con Private Endpoints son problemas de DNS, y esta página los explica todos.

### WireGuard: Quick Start e instalación — WireGuard
- **URL:** https://www.wireguard.com/quickstart/ · Instalación: https://www.wireguard.com/install/
- **Autor / organización:** Proyecto WireGuard (Jason A. Donenfeld)
- **Idioma:** Inglés
- **Tipo:** Documentación oficial
- **Duración aproximada:** 30 min
- **Cubre:** VPN, hybrid networking (la simulación site-to-site del laboratorio)
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** WireGuard cabe en una página de documentación y en un archivo de configuración de diez líneas. Es la forma más didáctica de entender qué hace un túnel VPN (claves, peers, AllowedIPs, enrutamiento) antes de pagar por un VPN Gateway gestionado.

## Documentación oficial

- **Enrutamiento del tráfico de red virtual (es-es):** https://learn.microsoft.com/es-es/azure/virtual-network/virtual-networks-udr-overview
- **Emparejamiento de redes virtuales (es-es):** https://learn.microsoft.com/es-es/azure/virtual-network/virtual-network-peering-overview
- **Qué es Azure Virtual Network (es-es):** https://learn.microsoft.com/es-es/azure/virtual-network/virtual-networks-overview
- **Private Link (índice, en-us):** https://learn.microsoft.com/en-us/azure/private-link/ · DNS: https://learn.microsoft.com/en-us/azure/private-link/private-endpoint-dns-integration
- **Network Watcher (índice, en-us):** https://learn.microsoft.com/en-us/azure/network-watcher/ · Módulo introductorio: https://learn.microsoft.com/en-us/training/modules/intro-to-azure-network-watcher/ · Referencia CLI `az network watcher`: https://learn.microsoft.com/en-us/cli/azure/network/watcher?view=azure-cli-latest
- **Hub-spoke (Architecture Center):** https://learn.microsoft.com/en-us/azure/architecture/networking/architecture/hub-spoke · Guía de diseño de red: https://learn.microsoft.com/en-us/azure/networking/design-guide/hub-spoke
- **Portal de documentación de Azure (es-es):** https://learn.microsoft.com/es-es/azure/ (busca aquí Load Balancer, Application Gateway, Front Door, VPN Gateway, ExpressRoute, Azure DNS y DNS Private Resolver; en este curso se estudian por la ruta AZ-700 y se comparan por precio)
- **Calculadora de precios:** https://azure.microsoft.com/es-es/pricing/calculator/ (la usarás para la tabla comparativa de la Parte A)
- **WireGuard:** https://www.wireguard.com/quickstart/
- **Terraform azurerm:** la documentación del proveedor en el Terraform Registry (ya la usaste en el Módulo Intermedio): recursos `azurerm_virtual_network_peering`, `azurerm_route_table`, `azurerm_route`, `azurerm_subnet_route_table_association`, `azurerm_network_interface` (`enable_ip_forwarding`), `azurerm_private_endpoint`, `azurerm_private_dns_zone`, `azurerm_private_dns_zone_virtual_network_link`, `azurerm_lb`, `azurerm_lb_backend_address_pool`, `azurerm_lb_probe`, `azurerm_lb_rule`, `azurerm_network_watcher`.

## Ruta recomendada de estudio

1. **Ver** el vídeo de John Savill completo, tomando notas de tres cosas: cómo se encadenan rutas de sistema, UDR y NVA; por qué el peering no es transitivo; y el flujo de resolución DNS con Private Link (3 h, en dos sesiones).
2. **Leer** la página de enrutamiento y la de peering de la documentación en español (90 min). Al terminar debes saber responder: ¿qué ruta gana si una UDR y una ruta de sistema coinciden en prefijo? ¿Qué hace `allow_forwarded_traffic` en un peering?
3. **Hacer** los módulos de la ruta AZ-700 sobre VNets, peering y enrutamiento (3 h). Puedes hacer sus ejercicios en sandbox si lo ofrecen; no despliegues gateways en tu suscripción.
4. **Leer** la arquitectura hub-spoke del Architecture Center y la guía de Private Link en hub-spoke (90 min). Dibuja tu propia versión del diagrama con las IPs que usarás en el laboratorio.
5. **Hacer** los módulos AZ-700 de Private Link y DNS privado, y **leer** la página de integración DNS de Private Endpoints (2,5 h). Este es el bloque conceptual más importante después del enrutamiento.
6. **Hacer** los módulos AZ-700 de conectividad híbrida (VPN, ExpressRoute, Virtual WAN) y de balanceo de carga (Load Balancer, Application Gateway, Front Door, Traffic Manager) (4 h). Aquí llegan los servicios caros: apréndelos para decidir, no para desplegar.
7. **Leer** el Quick Start de WireGuard (30 min) y **hacer** una prueba rápida de túnel entre `lab-so` y tu anfitrión, o entre dos VMs locales, antes de hacerlo hacia Azure (60 min).
8. **Leer** el tutorial hub-spoke con Terraform de Microsoft como referencia de sintaxis (60 min).
9. **Hacer el laboratorio** (16-22 h en varias sesiones; cada sesión termina con las VMs desasignadas o todo destruido).
10. **Ver** la serie Exam Readiness AZ-700 como repaso, **responder la evaluación** y **revisar el checklist**.

Si vas justo de tiempo: haz obligatoriamente los puntos 1, 2, 5, 9 y 10.

## Laboratorio

### Objetivo

Resolver el escenario de conectividad de una empresa ficticia, "Nortesur Logística": una plataforma en Azure con un hub de servicios compartidos y dos spokes (uno para la web interna, otro para aplicaciones), donde todo el tráfico entre spokes y hacia Internet pasa por un cortafuegos central, el almacenamiento solo es accesible por red privada, la oficina (tu VM local) se conecta por VPN y resuelve los nombres privados de Azure, y el equipo de operaciones (tú) es capaz de diagnosticar cualquier avería de red con herramientas de la plataforma. Todo desplegado con Terraform, salvo lo que se rompe a mano para practicar.

### Requisitos

- Terraform y Azure CLI actualizados; backend remoto en Azure Storage (reutiliza el del curso de Terraform).
- Tu clave SSH pública. Tu IP pública actual (`curl -s ifconfig.me`) para restringir el acceso SSH en el NSG.
- VM local `lab-so` con `wireguard-tools`, `dnsutils` y `curl`.
- Documenta en `laboratorio-networking.md`: cada decisión, cada comando de diagnóstico y su salida como texto. Las capturas del portal deben mostrar tu usuario.

> **Sobre el coste.** Estimación para el laboratorio completo si desasignas las VMs entre sesiones y destruyes al final: **3-8 USD**. Precios orientativos (septiembre de 2026, región East US; comprueba en la calculadora): 4 VMs B1s a ~0,01 USD/h cada una (gratis si tu cuenta conserva las 750 h/mes de los 12 meses gratuitos); 2 IPs públicas Standard estáticas a ~0,005 USD/h cada una (siguen cobrando con la VM desasignada); Load Balancer Standard ~0,025 USD/h más ~0,005 USD/GB (unos 18 USD/mes si lo olvidas encendido); Private Endpoint ~0,01 USD/h más tráfico; zona DNS privada 0,50 USD/mes; peering ~0,01 USD/GB en cada sentido dentro de la región (lo que muevas en el laboratorio son céntimos); Network Watcher: los diagnósticos (IP flow verify, next hop, connection troubleshoot) son gratuitos hasta 1.000 comprobaciones al mes y las capturas de paquetes hasta 100 al mes (pagas el almacenamiento donde se guardan; los flow logs y Connection Monitor sí se cobran y no se usan aquí). **No despliegues** VPN Gateway (~29 USD/mes el SKU Basic, ~140 USD/mes VpnGw1, 30-45 min de creación), Azure Firewall (~290 USD/mes Basic, ~900 USD/mes Standard), Front Door (~35 USD/mes base Standard), ExpressRoute ni Application Gateway con WAF (~320 USD/mes): se tratan a nivel conceptual. La única excepción opcional es Application Gateway Basic en la Parte D, si aceptas el coste de una sesión y lo borras antes de cerrar la terminal. Termina cada sesión con `az vm deallocate` de las 4 VMs y el laboratorio con `terraform destroy` y `az group delete`.

### Instrucciones

Plan de direccionamiento (úsalo tal cual o justifica tus cambios):

| Red | Prefijo | Subredes | Contenido |
|---|---|---|---|
| `vnet-hub` | 10.0.0.0/16 | `snet-nva` 10.0.1.0/24 | `vm-nva` (10.0.1.4, IP pública, IP forwarding): cortafuegos, NAT, DNS forwarder, extremo VPN |
| `vnet-spoke-web` | 10.1.0.0/16 | `snet-web` 10.1.1.0/24 · `snet-pe` 10.1.2.0/24 | `vm-web-1`, `vm-web-2` (nginx) detrás de `lb-web-int` (frontend 10.1.1.100); Private Endpoint del almacenamiento |
| `vnet-spoke-app` | 10.2.0.0/16 | `snet-app` 10.2.1.0/24 | `vm-app` (cliente de pruebas, sin IP pública) |
| Túnel WireGuard | 10.99.0.0/24 | | `vm-nva` 10.99.0.1 · `lab-so` 10.99.0.2 |

**Parte A — Diseño y comparativa de precios (2-3 h, sin desplegar nada)**

1. Dibuja el diagrama de la topología con las IPs de la tabla, las tablas de rutas que asociarás a cada subred y las zonas DNS. Marca con un color el camino que sigue un paquete de `vm-app` a `vm-web-1` y con otro el de `lab-so` a la cuenta de almacenamiento.
2. Construye en la calculadora de precios una tabla comparativa mensual en tu región, con una fila por servicio: Azure Firewall Basic y Standard, tu NVA (B1s + IP pública), VPN Gateway Basic y VpnGw1, ExpressRoute (circuito 50 Mbps medido, sin contar al operador), Virtual WAN (hub básico), Load Balancer Standard, Application Gateway Standard_v2 y WAF_v2, Application Gateway Basic, Front Door Standard, Traffic Manager, Azure DNS Private Resolver (1 endpoint de entrada + 1 de salida), NAT Gateway. Añade columnas "qué resuelve", "qué pierdo con la alternativa barata" y "cuándo lo elegiría en producción".
3. Escribe una página de "decisiones de red" (formato ADR, como en Arquitectura Cloud Avanzada): NVA frente a Azure Firewall, WireGuard frente a VPN Gateway, `dnsmasq` frente a DNS Private Resolver, Load Balancer frente a Application Gateway para la web interna. En cada una, di qué elegirías en producción y por qué en el laboratorio eliges otra cosa.
4. Tabla de equivalencias Azure ↔ AWS ↔ GCP para: VNet peering, hub-spoke (Transit Gateway, VPC Network Peering / Network Connectivity Center), UDR (route tables), Private Endpoint (PrivateLink, Private Service Connect), Private DNS Zone (Route 53 private hosted zone, Cloud DNS private zone), VPN Gateway, ExpressRoute (Direct Connect, Cloud Interconnect), Load Balancer, Application Gateway/WAF, Front Door, Network Watcher (VPC Reachability Analyzer, Network Intelligence Center).

**Parte B — Hub-spoke, NVA y enrutamiento con Terraform (4-5 h)**

5. Crea el proyecto Terraform `nortesur-red/` con backend remoto y archivos separados (`network.tf`, `nva.tf`, `spokes.tf`, `routes.tf`, `lb.tf`, `private-endpoint.tf`, `outputs.tf`). Todo en un solo grupo de recursos `rg-nortesur-red` con etiquetas `curso=networking-avanzado` y `propietario=<tu-usuario>`.
6. Declara las tres VNets y sus subredes, y los **cuatro** recursos de peering (hub→spoke-web, spoke-web→hub, hub→spoke-app, spoke-app→hub) con `allow_forwarded_traffic = true` en todos y `allow_virtual_network_access = true`. Explica en un comentario por qué hacen falta dos recursos por pareja y qué pasaría con el tráfico reenviado por el NVA si `allow_forwarded_traffic` fuera `false` en el lado del spoke.
7. Crea `vm-nva` (Ubuntu LTS, B1s, IP pública Standard estática, NIC con `enable_ip_forwarding = true`) y un NSG `nsg-nva` que solo permita TCP 22 desde tu IP pública, UDP 51820 desde cualquier origen (WireGuard) y todo el tráfico desde `10.0.0.0/8`. Con `custom_data` (cloud-init) deja la VM lista al arrancar:
   ```yaml
   #cloud-config
   package_update: true
   packages: [iptables-persistent, dnsmasq, wireguard-tools, tcpdump]
   write_files:
     - path: /etc/sysctl.d/99-forward.conf
       content: "net.ipv4.ip_forward=1\n"
   runcmd:
     - sysctl --system
     - iptables -t nat -A POSTROUTING -o eth0 -s 10.0.0.0/8 -j MASQUERADE
     - iptables -A FORWARD -j LOG --log-prefix "NVA-FWD " --log-level 6
     - netfilter-persistent save
   ```
   Explica cada línea: qué hace el `MASQUERADE` (el NVA es también la salida a Internet de los spokes, como haría Azure Firewall), por qué hace falta activar el forwarding en dos sitios (NIC de Azure y kernel) y por qué se registra la cadena FORWARD.
8. Crea las VMs `vm-web-1`, `vm-web-2` y `vm-app` (B1s, **sin IP pública**, misma clave SSH). En las web, cloud-init instala `nginx` y escribe `hostname` en `index.html`. Añade `depends_on` hacia el NVA y las asociaciones de rutas: sin IP pública y con la ruta por defecto hacia el NVA, estas VMs solo tienen Internet a través de él. Explica qué es el "acceso saliente predeterminado" de Azure, por qué ya no puedes contar con él en VNets nuevas y qué alternativas existen (NAT Gateway, Load Balancer con reglas de salida, IP pública, NVA).
9. Enrutamiento. Crea `rt-spoke-web` (asociada a `snet-web` y `snet-pe`) y `rt-spoke-app` (asociada a `snet-app`) con estas rutas y `next_hop_type = "VirtualAppliance"`, `next_hop_in_ip_address = "10.0.1.4"`: `0.0.0.0/0`, el prefijo del otro spoke y `10.99.0.0/24` (la VPN). Añade a las tablas `disable_bgp_route_propagation = true` y explica cuándo importa. **No** asocies ninguna tabla a `snet-nva`. Explica por qué no hace falta una ruta explícita spoke-a-spoke si ya existe `0.0.0.0/0` hacia el NVA, y por qué conviene ponerla igualmente (legibilidad, y qué pasaría si algún día quitas la ruta por defecto).
10. `terraform apply`. Entra al NVA por SSH y desde él a `vm-app` con `ssh -J azureuser@<ip-nva> azureuser@10.2.1.4`. Desde `vm-app`: `curl 10.1.1.4` y `curl 10.1.1.5` (las web), `curl -s ifconfig.me` (debe devolver la IP pública del NVA), `traceroute -n 10.1.1.4` (debe pasar por 10.0.1.4). En el NVA, `sudo journalctl -k | grep NVA-FWD | tail` para ver los paquetes reenviados y `sudo tcpdump -ni eth0 host 10.2.1.4` mientras haces un `curl` desde `vm-app`. Guarda las salidas.
11. Demuestra que el NVA es un cortafuegos: en el NVA, `sudo iptables -I FORWARD -s 10.2.0.0/16 -d 10.1.0.0/16 -p icmp -j DROP`. Desde `vm-app`, `ping 10.1.1.4` falla pero `curl 10.1.1.4` funciona. Quita la regla (`-D`). Explica cómo harías esto mismo con Azure Firewall (reglas de red y de aplicación) y qué gana la versión gestionada (alta disponibilidad, escalado, inteligencia de amenazas, sin parches).
12. Comprueba las **rutas efectivas** de la NIC de `vm-app`: `az network nic show-effective-route-table -g rg-nortesur-red -n <nic-vm-app> -o table`. Identifica las rutas de sistema (`Default`) que han quedado `Invalid` por tus UDR (`User`) y explica el orden de prioridad de Azure: prefijo más específico primero y, a igual prefijo, UDR > BGP > sistema.

**Parte C — Private Endpoint, Private DNS y forwarder (3-4 h)**

13. Crea una cuenta de almacenamiento `stnortesur<sufijo>` (Standard_LRS, `public_network_access_enabled = false`, `min_tls_version = "TLS1_2"`) con un contenedor `documentos`. Crea un `azurerm_private_endpoint` en `snet-pe` para el subrecurso `blob`, la zona `azurerm_private_dns_zone` `privatelink.blob.core.windows.net`, un `private_dns_zone_group` en el endpoint y **tres** `azurerm_private_dns_zone_virtual_network_link` (hub, spoke-web, spoke-app). Explica por qué la zona se enlaza a las tres VNets y qué pasaría si olvidas la del spoke-app (lo comprobarás en la Parte F).
14. Desde `vm-app`: `nslookup stnortesur<sufijo>.blob.core.windows.net` debe devolver un CNAME a `stnortesur<sufijo>.privatelink.blob.core.windows.net` y una IP `10.1.2.x`. `curl -sv https://stnortesur<sufijo>.blob.core.windows.net/documentos?restype=container&comp=list` debe conectar a la IP privada y devolver una respuesta HTTP del servicio (un error de autorización 403/404 es correcto: demuestra conectividad de red sin exponer datos). Desde tu equipo, el mismo `nslookup` devuelve la IP pública y el `curl` devuelve un error de acceso público deshabilitado. Explica la diferencia con un **service endpoint** (qué ve el servicio como origen, quién resuelve el nombre, qué se paga) y cuándo elegirías cada uno.
15. Forwarder DNS. En el NVA configura `dnsmasq` para escuchar en `10.0.1.4` y `10.99.0.1` y reenviar todo a `168.63.129.16` (el resolutor de Azure) con `/etc/dnsmasq.d/azure.conf`:
    ```
    listen-address=10.0.1.4,10.99.0.1,127.0.0.1
    bind-interfaces
    server=168.63.129.16
    cache-size=1000
    log-queries
    ```
    Reinicia el servicio y comprueba desde `vm-app`: `dig @10.0.1.4 stnortesur<sufijo>.blob.core.windows.net +short`. Explica qué es `168.63.129.16`, por qué solo responde desde dentro de Azure y por qué una red on-premises necesita un forwarder dentro de la VNet para resolver zonas privadas. Explica qué hace **Azure DNS Private Resolver** en su lugar (endpoints de entrada y salida, conjuntos de reglas), cuánto cuesta según tu tabla de la Parte A (más de 100 USD/mes por endpoint) y en qué situación lo elegirías igualmente.
16. Opcional: configura las VNets spoke con `dns_servers = ["10.0.1.4"]` en Terraform, reinicia `vm-app` y comprueba con `resolvectl status` que ahora resuelve a través del NVA. Observa las consultas en `journalctl -u dnsmasq -f`. Vuelve al DNS de Azure al terminar o déjalo y documenta el impacto (punto único de fallo).

**Parte D — Balanceo (2-3 h)**

17. Crea `lb-web-int`: `azurerm_lb` con `sku = "Standard"` y una `frontend_ip_configuration` privada estática `10.1.1.100` en `snet-web`, un backend pool con las NICs de las dos web, un probe HTTP a `/` en el 80 y una regla TCP 80→80 con `disable_outbound_snat = true`. Explica por qué un Load Balancer interno no da salida a Internet a sus backends y cómo lo resuelve tu NVA.
18. Desde `vm-app`, `for i in $(seq 10); do curl -s 10.1.1.100; done`: deberías ver alternar los hostnames. Para `nginx` en `vm-web-2` (`sudo systemctl stop nginx`) y repite: solo responde `vm-web-1`. Mira el estado del probe en el portal (Load Balancer → Insights o Métricas → Health Probe Status). Arranca `nginx` de nuevo.
19. Comparativa escrita, con tu tabla de precios: Load Balancer (capa 4, regional, interno/externo), Application Gateway (capa 7, TLS, rutas por URL, WAF), Front Door (capa 7 global, CDN, WAF, anycast) y Traffic Manager (DNS). Para el escenario de Nortesur, decide qué pondrías delante de la web interna, qué delante de una web pública europea y qué delante de una API global, y explica qué protege un **WAF** que no protege un NSG (OWASP Top 10, reglas administradas, modo detección frente a prevención).
20. **Opcional y acotado en coste:** si tu presupuesto lo permite, despliega un Application Gateway **Basic** (no v2 ni WAF) desde el portal en una subred nueva `snet-agw` 10.1.3.0/24 del spoke-web, con backend las dos web y un listener HTTP. Comprueba desde el NVA que balancea, captura la pantalla de la regla y el probe, y **bórralo en la misma sesión**. Anota el coste que aparece al día siguiente en Cost Management.

**Parte E — Híbrido: VPN site-to-site con WireGuard (2-3 h)**

21. Genera claves en ambos extremos (`wg genkey | tee privatekey | wg pubkey > publickey`). En el NVA, `/etc/wireguard/wg0.conf`:
    ```ini
    [Interface]
    Address = 10.99.0.1/24
    ListenPort = 51820
    PrivateKey = <privada-nva>
    [Peer]
    PublicKey = <publica-lab-so>
    AllowedIPs = 10.99.0.2/32
    ```
    En `lab-so`:
    ```ini
    [Interface]
    Address = 10.99.0.2/24
    PrivateKey = <privada-lab-so>
    DNS = 10.99.0.1
    [Peer]
    PublicKey = <publica-nva>
    Endpoint = <ip-publica-nva>:51820
    AllowedIPs = 10.0.0.0/16, 10.1.0.0/16, 10.2.0.0/16, 10.99.0.0/24
    PersistentKeepalive = 25
    ```
    `sudo systemctl enable --now wg-quick@wg0` en ambos. Explica quién inicia la conexión y por qué (NAT de tu casa), qué son `AllowedIPs` (a la vez lista de control y tabla de rutas) y qué hace `PersistentKeepalive`. **Nunca** subas las claves privadas a la entrega.
22. Desde `lab-so`: `ping 10.99.0.1`, `ping 10.2.1.4`, `curl 10.1.1.100` (la web balanceada, a través del túnel y del NVA), `dig stnortesur<sufijo>.blob.core.windows.net +short` (debe devolver la IP privada gracias al forwarder) y el `curl -sv https://stnortesur<sufijo>.blob.core.windows.net/...` de la Parte C. En el NVA, `sudo wg show` y `tcpdump -ni wg0`. Explica el camino completo de un paquete de `lab-so` a `vm-web-1` y de vuelta, incluyendo la ruta `10.99.0.0/24 → NVA` que pusiste en la Parte B (quítala un momento y explica por qué deja de funcionar).
23. Escribe la comparación WireGuard/VPN Gateway/ExpressRoute para Nortesur: cifrado, ancho de banda, SLA, alta disponibilidad (activo-activo, BGP), latencia, coste mensual y tiempo de puesta en marcha. Indica qué requisito de negocio te haría saltar de una opción a la siguiente.

**Parte F — Troubleshooting complejo con Network Watcher (3-4 h)**

24. Instala la extensión de Network Watcher en `vm-app` y `vm-web-1` (`az vm extension set --publisher Microsoft.Azure.NetworkWatcher --name NetworkWatcherAgentLinux --version 1.4 ...`). Verifica que existe el Network Watcher de tu región (`az network watcher list -o table`). Para cada avería siguiente: rompe **fuera de Terraform** (CLI o portal), reproduce el síntoma desde `vm-app` o `lab-so`, diagnostica con las herramientas indicadas, documenta la evidencia y repara con `terraform apply`, explicando qué cambio detectó el `plan`.
25. **Peering asimétrico.** Borra solo el lado spoke-app del peering: `az network vnet peering delete -g rg-nortesur-red --vnet-name vnet-spoke-app -n <nombre>`. Síntoma: `vm-app` no llega a nada. Diagnóstico: `az network vnet peering list --vnet-name vnet-hub -o table` (estado `Disconnected` en el lado hub), `az network watcher show-next-hop --source-resource vm-app --dest-ip 10.1.1.4` (siguiente salto `None`), rutas efectivas de `vm-app`.
26. **UDR mal apuntada.** `az network route-table route update -g rg-nortesur-red --route-table-name rt-spoke-app -n <ruta-spoke-web> --next-hop-ip-address 10.0.1.5`. Síntoma: `curl 10.1.1.4` se queda colgado. Diagnóstico: `show-next-hop` devuelve `VirtualAppliance 10.0.1.5`; `az network watcher test-connectivity --source-resource vm-app --dest-address 10.1.1.4 --dest-port 80` muestra dónde muere el salto; en el NVA `tcpdump` no ve nada. Explica por qué Azure acepta una ruta hacia una IP inexistente sin avisar.
27. **NSG que bloquea.** Añade a `nsg-web` una regla `Deny TCP 80 desde 10.2.0.0/16` con prioridad 100. Síntoma: `curl 10.1.1.4` falla desde `vm-app` pero `lab-so` (10.99.0.2) sí llega. Diagnóstico: `az network watcher test-ip-flow --vm vm-web-1 --direction Inbound --protocol TCP --local 10.1.1.4:80 --remote 10.2.1.4:50000` devuelve `Deny` y el nombre de la regla; compara con `--remote 10.99.0.2:50000`. Explica por qué el `test-ip-flow` no necesita agente y el `test-connectivity` sí.
28. **DNS que resuelve a la IP pública.** Borra el enlace de la zona privada con `vnet-spoke-app` (`az network private-dns link vnet delete ...`). Síntoma: desde `vm-app`, `nslookup` devuelve una IP pública y el `curl` devuelve un error de acceso público no permitido. Diagnóstico: compara `nslookup` desde `vm-web-1` (correcto) y `vm-app` (incorrecto), revisa los enlaces de la zona. Explica por qué este fallo no lo detecta ninguna herramienta de Network Watcher y qué comprobarías primero en un incidente real de Private Endpoint.
29. **Captura de paquetes gestionada.** Lanza `az network watcher packet-capture create --vm vm-web-1 -n cap-web --storage-account stnortesur<sufijo>` (o `--file-path` local en la VM) mientras haces peticiones desde `vm-app`, para la captura, descárgala y ábrela con `tcpdump -r` o Wireshark. Identifica el origen real de las conexiones (¿ves 10.2.1.4 o la IP del NVA? Explica por qué, según tu regla `MASQUERADE`: ajusta la regla para que solo enmascare el tráfico hacia Internet, `! -d 10.0.0.0/8`, y repite).
30. Escribe un **runbook de diagnóstico de red en Azure** de una página: orden de comprobación (DNS → NSG/ASG → rutas efectivas → peering → NVA → servicio destino), comando o herramienta para cada paso, qué es gratuito y qué se cobra.

**Parte G — Limpieza (30 min)**

31. `terraform destroy`, `az group delete -n rg-nortesur-red --yes`, y borra el grupo `NetworkWatcherRG` si no lo usas en otros cursos. Para `wg-quick@wg0` en `lab-so`. Al día siguiente, captura Cost Management filtrado por la etiqueta `curso=networking-avanzado` y anota el coste real frente a tu estimación.

### Resultado esperado

- `nortesur-red/` con el código Terraform completo, formateado y con `README.md` que explique cómo desplegar y destruir.
- `laboratorio-networking.md` con las partes A-G, salidas de comandos, diagrama, tabla de precios, ADRs, tabla de equivalencias, comparativas y el runbook.
- Evidencias de las cuatro averías: síntoma, diagnóstico, evidencia y reparación.
- Ningún recurso vivo al terminar y captura de coste del día siguiente.

### Criterios de validación

- [ ] Parte A: la tabla de precios tiene todas las filas con cifras de la calculadora y las ADRs justifican cada sustitución barata frente a la opción de producción.
- [ ] Parte B: el tráfico spoke-a-spoke y el de salida a Internet pasan por el NVA (evidencia: `traceroute`, `ifconfig.me`, `tcpdump` y logs `NVA-FWD`); las rutas efectivas muestran las rutas de sistema invalidadas; la regla `iptables` de bloqueo funciona y se explica el equivalente en Azure Firewall.
- [ ] Parte C: el nombre público de la cuenta resuelve a IP privada dentro de Azure y a pública fuera; el acceso público está deshabilitado; el forwarder responde desde el NVA; la explicación DNS (168.63.129.16, zonas, enlaces, Private Resolver) es correcta.
- [ ] Parte D: el balanceador alterna entre las dos web y detecta la caída de una; la comparativa LB/AppGw/Front Door/Traffic Manager y la explicación de WAF son precisas.
- [ ] Parte E: desde `lab-so` se alcanza la web balanceada y el almacenamiento por IP privada a través del túnel; se explica el camino completo y el papel de la ruta `10.99.0.0/24`; no hay claves privadas en la entrega.
- [ ] Parte F: las cuatro averías tienen síntoma, herramienta, evidencia y reparación por `terraform apply`; el runbook es utilizable por otra persona.
- [ ] Parte G: todo destruido y coste real documentado.
- [ ] El estudiante puede, en una llamada con el mentor, diagnosticar en vivo una avería nueva que el mentor provoque en un despliegue similar.

## Entrega

En tu repositorio de entregas, carpeta `03-modulo-avanzado/04-networking-cloud-avanzado/`:

1. `nortesur-red/` (código Terraform; sin `terraform.tfstate`, sin claves ni `.tfvars` con datos sensibles).
2. `laboratorio-networking.md` con diagrama (`diagrama.png` o Mermaid), tabla de precios, ADRs, equivalencias, evidencias y runbook.
3. `wireguard/` con los archivos de configuración **sin claves privadas** (sustitúyelas por `<REDACTED>`).
4. `capturas/`.
5. `ENTREGA.md` con evaluación, checklist y uso de IA.

Nota sobre IA: pedirle que te explique una salida de `show-effective-route-table` o un error de `terraform apply` es un buen uso. Pedirle "el Terraform de un hub-spoke" y pegarlo no lo es: el mentor te preguntará por cada ruta y cada peering.

## Evaluación

1. **Conceptual.** El peering de VNets no es transitivo. Explica qué significa con tu topología y qué dos mecanismos permiten que spoke-web hable con spoke-app. ¿Qué papel juega `allow_forwarded_traffic`?
2. **Técnica.** Una subred tiene una ruta de sistema `10.1.0.0/16 → VNetPeering` y tú añades una UDR `10.1.0.0/16 → VirtualAppliance 10.0.1.4`. ¿Cuál gana y por qué? ¿Y si tu UDR fuera `10.1.1.0/24`? ¿Y si llegara una ruta BGP `10.1.0.0/16` desde un gateway?
3. **Troubleshooting.** Un compañero asocia la tabla de rutas del spoke (con `0.0.0.0/0 → NVA`) también a `snet-nva`. ¿Qué ocurre y por qué? ¿Cómo lo detectarías con las rutas efectivas?
4. **Situacional.** Nortesur crece a 30 spokes y el NVA B1s se queda sin CPU. Da tres opciones (escalar el NVA, par de NVAs detrás de un Load Balancer interno, Azure Firewall) con ventajas, inconvenientes y coste aproximado según tu tabla.
5. **Conceptual.** Explica el flujo completo de resolución de `stnortesur.blob.core.windows.net` desde una VM de Azure con Private Endpoint: qué devuelve el DNS público, qué hace la zona `privatelink`, qué es `168.63.129.16` y qué cambia si la VNet usa servidores DNS personalizados.
6. **Troubleshooting.** Una aplicación en un spoke nuevo recibe `403 PublicAccessNotPermitted` al conectar con la cuenta de almacenamiento, pero la misma aplicación funciona en otro spoke. Da la causa más probable y los dos comandos con los que la confirmarías.
7. **Conceptual.** Service endpoint frente a Private Endpoint: qué IP de origen ve el servicio, quién resuelve el nombre, si funciona desde on-premises, qué cuesta. ¿Cuándo elegirías cada uno?
8. **Situacional.** La oficina de Nortesur necesita resolver nombres privados de Azure desde sus equipos. Compara tres soluciones: forwarder en una VM (tu `dnsmasq`), Azure DNS Private Resolver y reenvío condicional en el DNS de la oficina hacia cualquiera de los dos. ¿Qué elegirías con 10 empleados? ¿Y con 2.000?
9. **Técnica.** Explica qué hace tu regla `iptables -t nat -A POSTROUTING -s 10.0.0.0/8 -j MASQUERADE`, qué problema causó en la captura de paquetes de la Parte F y cómo la corregiste. ¿Qué hace exactamente lo mismo en Azure Firewall y en NAT Gateway?
10. **Conceptual.** Load Balancer, Application Gateway, Front Door y Traffic Manager: capa OSI, ámbito (regional/global), qué protege un WAF y coste aproximado. Asigna uno a cada caso: web interna de RR. HH., API pública para clientes en tres continentes, aplicación de un solo país con requisitos de WAF, failover DNS entre dos regiones.
11. **Situacional.** Nortesur pide "conectar la fábrica a Azure con 200 Mbps garantizados y latencia estable para un sistema industrial". Justifica ExpressRoute frente a VPN Gateway y frente a tu WireGuard: SLA, cifrado, coste, plazo. ¿Qué añadirías para alta disponibilidad?
12. **Técnica.** En tu configuración WireGuard, ¿por qué `AllowedIPs` en `lab-so` incluye los tres prefijos de las VNets y en el NVA solo `10.99.0.2/32`? ¿Qué pasaría si en el NVA pusieras `0.0.0.0/0`? ¿Por qué necesitaste una UDR `10.99.0.0/24 → NVA` en los spokes?
13. **Troubleshooting.** `test-ip-flow` dice `Allow` en ambos sentidos, `show-next-hop` devuelve `VirtualAppliance 10.0.1.4` y aun así `vm-app` no llega a `vm-web-1`. Nombra tres causas posibles que están **dentro** del NVA y cómo comprobarías cada una.
14. **Conceptual.** De las herramientas de Network Watcher que usaste, ¿cuáles son gratuitas, cuáles necesitan agente en la VM y cuál no sirve para un problema de DNS? ¿Qué añadirías (flow logs, Connection Monitor) en producción y qué cuesta?
15. **Reflexión.** ¿Cuál de las cuatro averías te costó más diagnosticar y qué orden de comprobación adoptarás a partir de ahora? ¿Qué habrías pagado de más si hubieras seguido el tutorial oficial al pie de la letra?

## Checklist final

Antes de continuar, deberías poder:

- [ ] Dibujar y desplegar con Terraform un hub-spoke con peering y explicar la no transitividad.
- [ ] Escribir UDRs hacia una NVA, leer las rutas efectivas de una NIC y explicar la prioridad UDR > BGP > sistema.
- [ ] Configurar una VM Linux como NVA (IP forwarding, `iptables`, NAT) y justificar cuándo pasar a Azure Firewall.
- [ ] Publicar un servicio PaaS solo por Private Endpoint con su zona DNS privada enlazada a todas las VNets que lo necesitan.
- [ ] Explicar la resolución DNS en Azure y montar un forwarder para redes híbridas.
- [ ] Poner un Load Balancer Standard interno delante de dos VMs y elegir entre LB, Application Gateway, Front Door y Traffic Manager.
- [ ] Comparar VPN Gateway, ExpressRoute y Virtual WAN por requisitos y coste.
- [ ] Montar un túnel WireGuard site-to-site y enrutar tráfico híbrido a los spokes.
- [ ] Diagnosticar peering, UDR, NSG y DNS con Network Watcher y `tcpdump`, siguiendo un orden.
- [ ] Traducir cada servicio a AWS y GCP.
- [ ] Tener la suscripción limpia y el coste real del laboratorio documentado.

---

*Recursos verificados el 2026-09-27 mediante búsqueda web (existencia y vigencia de las URLs). Si un enlace falla, abre un issue en este repositorio.*
