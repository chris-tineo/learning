# Fundamentos de Hardware

> Módulo: Básico · Curso 2 de 9 · Duración estimada: 8-12 horas · Estado: ✅ Completo

## Objetivo

Cuando en Azure elijas una máquina virtual "D4s v5 con 4 vCPU, 16 GiB de RAM y un disco Premium SSD", estarás tomando una decisión de hardware. Cuando un servidor vaya lento y tengas que decidir si el problema es CPU, memoria o disco, estarás razonando sobre hardware. Cuando un contenedor muera por falta de memoria, hardware otra vez.

Este curso te enseña **qué piezas forman una computadora, para qué sirve cada una y cómo se miden**. No para montar PCs, sino para que más adelante, cuando el hardware esté "escondido" detrás de la nube, sepas exactamente qué estás alquilando y qué cuello de botella puede tener tu sistema.

**Antes de empezar** conviene haber hecho el curso de Historia de la Computación (para saber qué es un transistor y un circuito integrado) y tener acceso a un equipo Windows, macOS o Linux en el que puedas mirar su configuración.

### Al terminar este curso deberías poder

- Nombrar los componentes principales de una computadora (CPU, RAM, almacenamiento, GPU, placa base, fuente, tarjeta de red) y explicar la función de cada uno.
- Explicar la diferencia entre núcleos, hilos y frecuencia de una CPU, y por qué "más GHz" no siempre significa "más rápido".
- Distinguir memoria volátil y no volátil, y explicar por qué la RAM y el disco cumplen funciones distintas.
- Comparar HDD, SSD SATA y SSD NVMe en velocidad, latencia y caso de uso.
- Explicar qué hacen BIOS/UEFI y qué pasa desde que enciendes el equipo hasta que arranca el sistema operativo.
- Convertir entre bits, bytes, KB, MB, GB, TB y PB, y distinguir base 10 (GB) de base 2 (GiB).
- Explicar la diferencia general entre arquitectura x86 y ARM y por qué ambas existen hoy en servidores y en la nube.
- Inventariar el hardware de tu propio equipo usando herramientas del sistema.
- Relacionar cada componente físico con su equivalente en una máquina virtual de Azure (vCPU, memoria, tipo de disco, red).

## Prerrequisitos

- Curso 1: Historia de la Computación.
- Un equipo Windows, macOS o Linux con permisos para ver su configuración (no hace falta abrirlo físicamente).
- Opcional: una cuenta en Cisco Networking Academy (gratuita) si quieres hacer el curso de Cisco.

## Temario

- CPU.
- Núcleos e hilos.
- Frecuencia.
- RAM.
- HDD.
- SSD.
- NVMe.
- GPU.
- Motherboard.
- Fuente de alimentación.
- BIOS y UEFI.
- Tarjetas de red.
- Periféricos.
- Almacenamiento.
- Memoria volátil y no volátil.
- Bits y bytes.
- KB, MB, GB, TB y unidades superiores.
- Diferencias generales entre arquitectura x86 y ARM.

## Recursos en español

### ¿Cómo funciona un PC y qué hace cada pieza? — Nate Gentile
- **URL:** https://www.youtube.com/watch?v=0zkX6nlpiSk
- **Autor / organización:** Nate Gentile (divulgador de hardware, canal en español con más de 3 M de suscriptores)
- **Idioma:** Español
- **Tipo:** Vídeo
- **Duración aproximada:** 20-25 min
- **Cubre:** CPU, RAM, almacenamiento (HDD/SSD), GPU, placa base, fuente de alimentación, periféricos.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la explicación en español más clara y visual de qué hace cada componente. Nate explica con analogías correctas y sin errores conceptuales. Es el vídeo con el que arrancar el curso.

### Conceptos básicos de hardware informático — Cisco Networking Academy
- **URL:** https://www.netacad.com/courses/computer-hardware-basics?courseLang=es-XL
- **Autor / organización:** Cisco Networking Academy
- **Idioma:** Español (también disponible en inglés con `courseLang=en-US`)
- **Tipo:** Curso online autoguiado con laboratorios virtuales
- **Duración aproximada:** 6 horas
- **Cubre:** Todos los componentes del temario, ensamblaje, portátiles y dispositivos móviles. Incluye 3 laboratorios virtuales.
- **Nivel:** Introductorio
- **Acceso:** Gratuito. **Requiere crear una cuenta gratuita** en netacad.com (no pide tarjeta). Da una insignia digital al terminar.
- **Por qué lo recomiendo:** Es el recurso principal del curso: estructurado, con evaluaciones y laboratorios virtuales donde "montas" un PC sin tocar hardware real. Es de una organización de referencia y completamente gratuito. Si solo vas a hacer un recurso largo, haz este.

### Introducción a ¿Cómo funcionan las computadoras? — Khan Academy en español (serie de Code.org)
- **URL:** https://es.khanacademy.org/computing/code-org/computers-and-the-internet/how-computers-work/v/khan-academy-and-codeorg-introducing-how-computers-work
- **Autor / organización:** Code.org, alojado en Khan Academy (con Bill Gates y otros ingenieros)
- **Idioma:** Español (vídeos en inglés con subtítulos en español)
- **Tipo:** Serie de 6 vídeos cortos
- **Duración aproximada:** 30 min en total
- **Cubre:** Qué es una computadora, bits y bytes, circuitos y lógica, CPU, memoria y entrada/salida, hardware y software.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Explica bits y bytes y la relación entre hardware y software desde cero, con animaciones. Ideal si nunca has pensado en cómo un "1" y un "0" se convierten en una foto o en un programa.

### Arquitectura x86 frente a ARM — Xataka
- **URL:** https://www.xataka.com/ordenadores/llevamos-cuatro-decadas-dominio-x86-nuestros-pcs-pc-copilot-basados-chips-arm-punto-inflexion
- **Autor / organización:** Xataka (medio tecnológico en español)
- **Idioma:** Español
- **Tipo:** Artículo
- **Duración aproximada:** 10-15 min
- **Cubre:** Diferencias generales entre x86 y ARM, por qué ARM domina en móviles y está entrando en portátiles y servidores.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Actualizado (habla de los PC con ARM de 2024 en adelante) y explica el contexto de mercado. Si quieres el detalle técnico RISC/CISC, complementa con el artículo de Profesional Review (2017, conceptos válidos): https://www.profesionalreview.com/2017/11/26/procesadores-x86-vs-arm-diferencias-ventajas-principales/

### Introducción a la computación / Arquitectura de los computadores — Wikiversidad
- **URL:** https://es.wikiversity.org/wiki/Introducci%C3%B3n_a_la_computaci%C3%B3n/Arquitectura_de_los_computadores
- **Autor / organización:** Wikiversidad en español (comunidad)
- **Idioma:** Español
- **Tipo:** Lección de texto
- **Duración aproximada:** 20 min
- **Cubre:** Componentes principales y cómo se relacionan entre sí (esquema de Von Neumann).
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Lectura corta y complementaria para tener por escrito, en español, el esquema de bloques de una computadora. Útil como repaso antes de la evaluación.

## Recursos en inglés

### How does Computer Hardware Work? [3D Animated Teardown] — Branch Education
- **URL:** https://www.youtube.com/watch?v=d86ws7mQYIg
- **Autor / organización:** Branch Education (canal educativo con animación 3D fotorrealista)
- **Idioma:** Inglés (subtítulos disponibles)
- **Tipo:** Vídeo
- **Duración aproximada:** 20 min
- **Cubre:** CPU, placa base, GPU, fuente de alimentación, RAM (DRAM), SSD, HDD.
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Desmonta un PC en 3D y muestra cómo funciona cada pieza por dentro. Es el mejor vídeo para "ver" lo que Nate Gentile explica. Complementa con "How does Computer Memory Work?" del mismo canal: https://www.youtube.com/watch?v=7J7X7aZvMXQ

### Crash Course Computer Science, episodios 3 a 9 — CrashCourse / PBS
- **URL:** Empieza en el episodio 7, "The Central Processing Unit (CPU)": https://www.youtube.com/watch?v=FZGugFqdr60 · La serie completa está en el canal CrashCourse de YouTube; página de la serie: https://thecrashcourse.com/courses/the-central-processing-unit-cpu-crash-course-computer-science-7/
- **Autor / organización:** CrashCourse (PBS Digital Studios)
- **Idioma:** Inglés (subtítulos)
- **Tipo:** Serie de vídeos
- **Duración aproximada:** 10-12 min por episodio; los episodios 3-9 suman ~75 min
- **Cubre:** Bits y bytes (ep. 4), puertas lógicas y ALU (ep. 3, 5), registros y RAM (ep. 6), CPU (ep. 7), instrucciones (ep. 8), diseños avanzados de CPU: caché, pipelining, núcleos (ep. 9).
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la explicación más didáctica de cómo una CPU ejecuta instrucciones y por qué existen los núcleos, la caché y la frecuencia. El episodio 9 explica exactamente por qué "más GHz" dejó de ser la única forma de ir más rápido. Serie de 2017, conceptos totalmente vigentes.

### Computers and the Internet: Computers, Bits and bytes — Khan Academy
- **URL:** Unidad "Computers": https://www.khanacademy.org/computing/computers-and-internet/xcae6f4a7ff015e7d:computers · Artículo "Bits (binary digits)": https://www.khanacademy.org/computing/computers-and-internet/xcae6f4a7ff015e7d:digital-information/xcae6f4a7ff015e7d:bits-and-bytes/a/bits-binary-digits
- **Autor / organización:** Khan Academy
- **Idioma:** Inglés
- **Tipo:** Artículos + ejercicios interactivos
- **Duración aproximada:** 60-90 min
- **Cubre:** Bits, bytes, unidades, cómo funciona una computadora (transistores, puertas lógicas, CPU, memoria, sistema de archivos).
- **Nivel:** Introductorio
- **Acceso:** Libre (cuenta opcional para guardar progreso)
- **Por qué lo recomiendo:** Tiene ejercicios de práctica con corrección automática sobre bits, bytes y conversión de unidades. Es la mejor forma de asegurarte de que dominas las unidades antes del laboratorio.

### Computer Hardware Basics — Cisco Networking Academy (versión en inglés)
- **URL:** https://www.netacad.com/courses/computer-hardware-basics?courseLang=en-US
- **Autor / organización:** Cisco Networking Academy
- **Idioma:** Inglés
- **Tipo:** Curso autoguiado
- **Duración aproximada:** 6 horas
- **Cubre:** Igual que la versión en español.
- **Nivel:** Introductorio
- **Acceso:** Gratuito, requiere cuenta gratuita
- **Por qué lo recomiendo:** Si tu inglés lo permite, hacerlo en inglés te acostumbra al vocabulario técnico que encontrarás en toda la documentación de Azure, Linux y Kubernetes. Elige un idioma, no hagas los dos.

### Professor Messer's CompTIA A+ 220-1201 Core 1 Training Course (secciones de hardware) — Professor Messer
- **URL:** https://www.professormesser.com/free-a-plus-training/220-1201/220-1201-video/220-1201-training-course/
- **Autor / organización:** Professor Messer (James Messer), formador de certificaciones CompTIA
- **Idioma:** Inglés
- **Tipo:** Curso en vídeo (63 vídeos, ~10 h en total). Para este curso solo interesan las secciones 3.x "Hardware" (~3 h)
- **Duración aproximada:** 3 h (solo secciones de hardware)
- **Cubre:** Todo el temario en profundidad: CPU, RAM, tipos de almacenamiento, placas base, fuentes, BIOS/UEFI, tarjetas de red, periféricos.
- **Nivel:** Introductorio-intermedio (nivel certificación CompTIA A+)
- **Acceso:** Libre (los vídeos son gratuitos; las notas en PDF y los exámenes de práctica son de pago, no son necesarios)
- **Por qué lo recomiendo:** Complementario, para quien quiera profundizar o plantearse la certificación A+ más adelante. Es el material gratuito de referencia para A+ y está actualizado a la versión 2025 del examen.

## Documentación oficial

El hardware no tiene "documentación oficial" única, pero sí la tiene su equivalente en la nube, que es donde vas a aplicar este curso. Estas páginas de Microsoft Learn se usan en el laboratorio:

- **Descripción general de los tamaños de máquinas virtuales en Azure:** https://learn.microsoft.com/es-es/azure/virtual-machines/sizes/overview — explica cómo se nombran los tamaños (familia, vCPU, memoria, características) y qué familias existen (uso general, optimizadas para cómputo, memoria, almacenamiento, GPU).
- **Selección de un tipo de disco para máquinas virtuales de Azure (discos administrados):** https://learn.microsoft.com/es-es/azure/virtual-machines/disks-types — compara Standard HDD, Standard SSD, Premium SSD, Premium SSD v2 y Ultra Disk. Es la traducción directa de HDD/SSD/NVMe al mundo Cloud.
- **Documentación del kernel de Linux (referencia):** https://docs.kernel.org/ — no hace falta leerla ahora; solo saber que existe y que ahí está la documentación de cómo el sistema operativo habla con el hardware.

## Ruta recomendada de estudio

1. **Ver** "¿Cómo funciona un PC y qué hace cada pieza?" de Nate Gentile (25 min). Anota los componentes que menciona.
2. **Ver** la serie de Code.org en Khan Academy en español (30 min), en especial "Binario y datos" y "CPU, memoria, entrada y salida".
3. **Hacer** los ejercicios de bits y bytes de Khan Academy en inglés (45 min). Asegúrate de poder convertir entre unidades sin calculadora en los casos sencillos, y de entender la diferencia entre GB (10⁹) y GiB (2³⁰).
4. **Ver** Crash Course Computer Science, episodios 6, 7 y 9 (35 min): RAM, CPU y por qué existen caché, pipelining y núcleos.
5. **Ver** Branch Education "How does Computer Hardware Work?" (20 min). Fíjate en la diferencia física entre DRAM, SSD y HDD.
6. **Hacer** el curso "Conceptos básicos de hardware informático" de Cisco (6 h, puedes repartirlo en varios días). Haz los 3 laboratorios virtuales.
7. **Leer** el artículo de Xataka sobre x86 y ARM (15 min).
8. **Leer** las dos páginas de Microsoft Learn de la sección de documentación oficial (30 min): tamaños de VM y tipos de disco. No hace falta entenderlo todo; el objetivo es ver que los conceptos del curso (vCPU, GiB, SSD, IOPS) aparecen tal cual.
9. **Hacer el laboratorio** (2-3 h).
10. **Responder la evaluación** y **revisar el checklist**.

## Laboratorio

### Objetivo

Inventariar el hardware real de tu equipo con herramientas del sistema, explicar la función de cada componente y traducir ese inventario a una máquina virtual de Azure equivalente.

### Requisitos

- Tu propio equipo (Windows, macOS o Linux). Si solo tienes acceso a un equipo compartido o del trabajo, avisa al mentor: cualquier equipo sirve mientras puedas ejecutar las herramientas de solo lectura indicadas.
- Navegador para consultar Microsoft Learn.
- No hace falta cuenta de Azure: se usan solo las páginas públicas de documentación.

### Instrucciones

**Parte A — Inventario (60-90 min)**

1. Crea un archivo `inventario-hardware.md`.
2. Obtén los datos de tu equipo con las herramientas del sistema operativo:
   - **Windows:** ejecuta `msinfo32` (Información del sistema), abre el Administrador de tareas → pestaña Rendimiento (CPU, Memoria, Disco, GPU) y ejecuta en PowerShell:
     ```powershell
     Get-ComputerInfo | Select-Object CsProcessors, CsNumberOfLogicalProcessors, CsTotalPhysicalMemory, BiosFirmwareType
     Get-PhysicalDisk | Select-Object FriendlyName, MediaType, BusType, Size
     Get-NetAdapter | Select-Object Name, InterfaceDescription, LinkSpeed
     ```
   - **Linux:** ejecuta `lscpu`, `free -h`, `lsblk -d -o NAME,SIZE,ROTA,TRAN,MODEL`, `lspci | grep -i -E "vga|network|ethernet"`, `sudo dmidecode -t baseboard` (si está disponible) y `[ -d /sys/firmware/efi ] && echo UEFI || echo BIOS`.
   - **macOS:** menú Apple → Acerca de este Mac → Informe del sistema, y en la terminal `system_profiler SPHardwareDataType SPStorageDataType`.
3. Rellena esta tabla (una fila por componente):

   | Componente | Modelo / valor en mi equipo | Función (con mis palabras) | Herramienta con la que lo obtuve |
   |---|---|---|---|
   | CPU (modelo, núcleos, hilos, frecuencia base) | | | |
   | Arquitectura (x86-64 o ARM64) | | | |
   | RAM (capacidad, tipo si se ve) | | | |
   | Almacenamiento (tipo HDD/SSD/NVMe, capacidad, interfaz) | | | |
   | GPU (integrada o dedicada, modelo) | | | |
   | Placa base / modelo del equipo | | | |
   | Firmware (BIOS o UEFI) | | | |
   | Tarjeta(s) de red (Ethernet, Wi-Fi, velocidad) | | | |
   | Periféricos conectados | | | |

4. Añade capturas de pantalla de las herramientas que usaste (al menos tres). En la captura debe verse el nombre de tu equipo o tu usuario.

**Parte B — Unidades (20 min)**

5. Añade una sección "Unidades" y responde mostrando el cálculo:
   - Tu RAM en bytes, en GB (base 10) y en GiB (base 2). Explica por qué el sistema operativo suele mostrar un número menor que el anunciado por el fabricante.
   - Tu disco: capacidad anunciada frente a capacidad que muestra el sistema. Explica la diferencia.
   - ¿Cuántas fotos de 4 MB caben en tu disco libre? ¿Cuántos discos como el tuyo harían falta para almacenar 1 PB?

**Parte C — Traducción a Azure (45-60 min)**

6. Añade una sección "Equivalente en Azure". Usando la documentación oficial de tamaños de VM y tipos de disco:
   - Elige la **familia** de VM y el **tamaño** más parecidos a tu equipo (vCPU y GiB). Explica cómo se lee el nombre del tamaño (por ejemplo, qué significa cada parte de `Standard_D4s_v5`).
   - Elige el **tipo de disco administrado** equivalente a tu almacenamiento y justifica (HDD → Standard HDD; SSD SATA → Standard SSD; NVMe → Premium SSD o Premium SSD v2).
   - Indica qué componentes de tu equipo **no tienen equivalente directo** en una VM (placa base, fuente, periféricos, GPU si no es una VM con GPU) y explica quién se ocupa de ellos en la nube.
   - Responde: si tu equipo tuviera que atender a 500 usuarios simultáneos y se quedara corto, ¿qué cambiarías primero y por qué: más vCPU, más memoria o disco más rápido? Justifica con lo aprendido (no hay una única respuesta correcta; se valora el razonamiento).

### Resultado esperado

Un documento Markdown con tres secciones (Inventario, Unidades, Equivalente en Azure), la tabla completa, al menos tres capturas y las justificaciones escritas.

### Criterios de validación

- [ ] La tabla de inventario tiene las 9 filas y los valores son coherentes con las capturas.
- [ ] La columna "Función" está escrita con palabras propias y es correcta (por ejemplo, no confunde RAM con almacenamiento).
- [ ] Los cálculos de unidades son correctos y distinguen GB de GiB.
- [ ] La elección de tamaño de VM y tipo de disco está justificada y el nombre del tamaño está bien interpretado.
- [ ] La sección de componentes sin equivalente en la nube menciona correctamente el modelo de responsabilidad (quién gestiona el hardware físico).
- [ ] La respuesta sobre el cuello de botella muestra razonamiento, no una respuesta memorizada.

## Entrega

En tu repositorio de entregas, carpeta `01-modulo-basico/02-fundamentos-de-hardware/`:

1. `inventario-hardware.md` con las tres partes del laboratorio.
2. Carpeta `capturas/` con las imágenes.
3. `ENTREGA.md` con la evaluación, el checklist y la declaración de uso de IA.
4. Opcional: la insignia digital del curso de Cisco (enlace o captura).

## Evaluación

1. **Conceptual.** Explica la diferencia entre núcleos e hilos de una CPU. Si una CPU tiene 4 núcleos y 8 hilos, ¿tiene "8 procesadores"? ¿Qué significa eso para un programa que solo usa un hilo?
2. **Conceptual.** ¿Por qué una CPU de 3,0 GHz de 2024 es mucho más rápida que una de 3,0 GHz de 2008 si la frecuencia es la misma?
3. **Conceptual.** Explica por qué necesitamos RAM y disco a la vez. ¿Qué pasaría si solo tuviéramos disco? ¿Y si solo tuviéramos RAM?
4. **Técnica.** Ordena de más lento a más rápido: SSD NVMe, HDD, RAM, SSD SATA, caché de CPU. Da una razón física para cada salto.
5. **Situacional.** Un servidor de base de datos va lento. El monitor muestra CPU al 20 %, RAM al 40 % y el disco al 100 % de tiempo activo con colas altas. ¿Dónde está el cuello de botella? ¿Qué cambiarías si estuviera en Azure (tipo de disco, tamaño de VM...)?
6. **Situacional.** Un compañero compra un portátil con "16 GB de RAM" y se queja de que Windows muestra 15,8 GiB "utilizables". Explícale qué pasa (dos motivos distintos son aceptables).
7. **Técnica.** Convierte: 2 TB a GB, 512 MiB a bytes, 1,5 GB a MB. ¿Cuántos bytes tiene un byte de 8 bits, y por qué la unidad mínima de almacenamiento no es el bit?
8. **Conceptual.** ¿Qué hace la BIOS/UEFI entre que pulsas el botón de encendido y aparece el sistema operativo? ¿Por qué UEFI sustituyó a la BIOS clásica?
9. **Conceptual.** ¿Cuál es la diferencia general entre x86 y ARM? ¿Por qué Azure (y AWS) ofrecen máquinas virtuales ARM y cuándo tendría sentido elegir una?
10. **Situacional.** Estás eligiendo una VM en Azure para un servidor web pequeño. Ves `Standard_B2s`, `Standard_D2s_v5` y `Standard_E2s_v5`, todas con 2 vCPU. Sin mirar precios, ¿en qué se diferencian las familias B, D y E según la documentación y cuál elegirías para empezar?
11. **Troubleshooting.** Un PC arranca, muestra la pantalla del fabricante y luego dice "No bootable device". Nombra dos causas posibles relacionadas con el hardware o el firmware y cómo comprobarías cada una.
12. **Conceptual.** ¿Para qué sirve una GPU además de para juegos, y por qué es tan importante para la Inteligencia Artificial moderna? Conecta la respuesta con lo que viste en el curso de Historia.

## Checklist final

Antes de continuar, deberías poder:

- [ ] Nombrar los componentes de una computadora y explicar la función de cada uno sin mirar apuntes.
- [ ] Explicar núcleos, hilos y frecuencia, y por qué la frecuencia sola no mide el rendimiento.
- [ ] Distinguir memoria volátil de no volátil y explicar el papel de RAM y almacenamiento.
- [ ] Comparar HDD, SSD SATA y NVMe y elegir uno según el caso de uso.
- [ ] Explicar qué hace la BIOS/UEFI durante el arranque.
- [ ] Convertir entre bits, bytes, KB/MB/GB/TB/PB y distinguir GB de GiB.
- [ ] Explicar la diferencia general entre x86 y ARM.
- [ ] Inventariar el hardware de un equipo con herramientas del sistema (Windows y Linux).
- [ ] Leer el nombre de un tamaño de VM de Azure y saber qué familia y recursos indica.
- [ ] Relacionar HDD/SSD/NVMe con los tipos de disco administrado de Azure.

---

*Recursos verificados el 2026-09-26 mediante búsqueda web (existencia y vigencia de las URLs). Si un enlace falla, abre un issue en este repositorio.*
