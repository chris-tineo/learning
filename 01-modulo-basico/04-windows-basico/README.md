# Windows Básico

> Módulo: Básico · Curso 4 de 9 · Duración estimada: 10-15 horas · Estado: ✅ Completo

## Objetivo

Windows sigue siendo el sistema operativo de la inmensa mayoría de los puestos de trabajo y de una parte importante de los servidores de las empresas. En Azure desplegarás máquinas virtuales Windows Server, gestionarás identidades que vienen del mundo Windows (Active Directory, Entra ID) y usarás PowerShell tanto para administrar Windows como para administrar Azure.

Este curso te enseña a **administrar un equipo Windows como técnico, no como usuario**: saber qué hay dentro (usuarios, grupos, permisos, servicios, eventos, dispositivos), moverte por la línea de comandos (CMD y PowerShell), entender las variables de entorno, configurar y diagnosticar la red con las herramientas básicas y resolver problemas elementales con método.

Aunque después trabajes sobre todo con Linux, casi todo lo que aprendas aquí tiene su equivalente directo allí, y ya viste en el curso anterior cuáles son. Además, PowerShell es la herramienta oficial para administrar Azure desde la terminal, así que lo que empieces aquí lo seguirás usando en toda la ruta.

**Antes de empezar** debes haber completado Fundamentos de Sistemas Operativos: sabes qué es un proceso, un servicio, un usuario y un permiso. Necesitas un equipo con Windows 10 u 11 (cualquier edición) con permisos de administrador. Si tu equipo es macOS o Linux, avisa al mentor: la alternativa es una VM con Windows 11 de evaluación o una VM Windows en Azure cuando llegues al curso 8.

### Al terminar este curso deberías poder

- Explicar la estructura básica de Windows: unidades, carpetas del sistema, perfil de usuario, Registro (a nivel conceptual).
- Crear, modificar y eliminar usuarios locales y grupos, y explicar la diferencia entre un usuario estándar y un administrador.
- Leer y modificar permisos NTFS de una carpeta y explicar la herencia.
- Inspeccionar, iniciar, detener y cambiar el tipo de inicio de un servicio, y saber con qué cuenta se ejecuta.
- Usar el Visor de eventos para encontrar errores del sistema y de aplicaciones, y filtrar por origen, nivel y fecha.
- Usar el Administrador de dispositivos para identificar hardware sin driver o con problemas.
- Ejecutar comandos básicos en CMD y en PowerShell, y explicar la diferencia entre ambos.
- Usar cmdlets de PowerShell con `Get-Help`, `Get-Command` y la tubería (`|`) para consultar procesos, servicios y eventos.
- Consultar y definir variables de entorno de usuario y de sistema, y explicar para qué sirve `PATH`.
- Instalar y desinstalar software con la interfaz gráfica y con `winget`.
- Consultar la configuración de red y diagnosticar conectividad con `ipconfig`, `ping`, `tracert` y `nslookup`.
- Aplicar un método de troubleshooting elemental: reproducir, aislar, consultar eventos, probar una hipótesis, documentar.

## Prerrequisitos

- Curso 3: Fundamentos de Sistemas Operativos.
- Equipo con Windows 10 u 11 y cuenta de administrador local. Windows Home sirve para todo el laboratorio (se indican alternativas cuando una herramienta solo existe en Pro).
- Conexión a Internet.

## Temario

- Estructura básica de Windows.
- File Explorer.
- Task Manager.
- Usuarios y grupos.
- Permisos.
- Services.
- Event Viewer.
- Device Manager.
- CMD.
- PowerShell introductorio.
- Variables de entorno.
- Instalación y desinstalación de software.
- Configuración de red.
- ipconfig.
- ping.
- tracert.
- nslookup.
- Troubleshooting elemental.

## Recursos en español

### Introducción a Windows PowerShell (ruta de aprendizaje) — Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/training/paths/get-started-windows-powershell/
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Ruta de aprendizaje interactiva (varios módulos con preguntas de comprobación)
- **Duración aproximada:** 2-3 h
- **Cubre:** PowerShell introductorio: qué es, cómo abrirlo, estructura de los cmdlets, parámetros, sistema de ayuda, tubería, consulta de procesos y servicios.
- **Nivel:** Introductorio
- **Acceso:** Libre. Cuenta Microsoft gratuita opcional para guardar el progreso.
- **Por qué lo recomiendo:** Es el material oficial de Microsoft para empezar con PowerShell y está completo en español. Es el recurso principal de la parte de línea de comandos. Complementa con el módulo "¿Qué es PowerShell?" (https://learn.microsoft.com/es-es/training/modules/introduction-to-powershell/) si quieres una introducción más corta antes de la ruta.

### PowerShell 101 — Microsoft Learn (documentación)
- **URL:** https://learn.microsoft.com/es-es/powershell/scripting/learn/ps101/00-introduction
- **Autor / organización:** Microsoft (escrito por Mike F. Robbins)
- **Idioma:** Español (traducción de la documentación oficial)
- **Tipo:** Guía en capítulos
- **Duración aproximada:** 2 h para los capítulos 1 a 4 (Introducción, Sistema de ayuda, Detección de objetos, Una sola línea y la canalización)
- **Cubre:** PowerShell introductorio en profundidad.
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la guía "PowerShell 101" oficial, más detallada que la ruta de aprendizaje. Léela después de la ruta, solo los capítulos 1-4; el resto (scripting) se retoma en el Módulo Intermedio.

### Cuentas locales — Microsoft Learn (documentación de Windows)
- **URL:** https://learn.microsoft.com/es-es/windows/security/identity-protection/access-control/local-accounts
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Documentación oficial
- **Duración aproximada:** 20 min
- **Cubre:** Usuarios y grupos: cuentas predeterminadas (Administrador, Invitado, SYSTEM...), grupos locales, buenas prácticas (usar cuenta estándar y elevar cuando haga falta).
- **Nivel:** Introductorio-intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Explica de forma oficial qué cuentas trae Windows de serie y por qué no debes trabajar a diario como administrador. Es la base de la parte de usuarios del laboratorio.

### Configuración de la conectividad de red IP — Microsoft Learn
- **URL:** https://learn.microsoft.com/es-es/training/modules/configure-ip-network-connectivity/
- **Autor / organización:** Microsoft
- **Idioma:** Español
- **Tipo:** Módulo de aprendizaje
- **Duración aproximada:** 45-60 min
- **Cubre:** Configuración de red en Windows, IPv4, direcciones públicas y privadas, DHCP, herramientas de diagnóstico (`ipconfig`, `ping`, `tracert`, `nslookup`, Test-NetConnection).
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es el módulo oficial que explica exactamente las herramientas de red del temario. La parte de IPv6 puedes leerla por encima; se retoma en Networking Básico.

### Curso gratuito de PowerShell (vídeos 1 a 6) — YouTube, serie "Aprende Sistemas Operativos"
- **URL:** Vídeo 1, "Introducción y primeros pasos": https://www.youtube.com/watch?v=YwGIXXqLDkM · Vídeo 2, "Mi primer script": https://www.youtube.com/watch?v=FFrOAjVchn0 · Vídeo 3, "Variables": https://www.youtube.com/watch?v=b4FA8Q5r3fs
- **Autor / organización:** Serie "Aprende Sistemas Operativos" (canal educativo en español); repositorio de apoyo en GitHub: https://github.com/addcostatropical/curso-gratuito-powershell
- **Idioma:** Español
- **Tipo:** Serie de vídeos
- **Duración aproximada:** 10-20 min por vídeo; para este curso bastan los 3-6 primeros (~1 h)
- **Cubre:** PowerShell introductorio (consola, cmdlets, primer script, variables).
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Vídeos en español, cortos y prácticos, para "ver" lo que la documentación de Microsoft explica por escrito. Es de 2020, pero PowerShell 5.1/7 no ha cambiado en lo que cubre. Es complementario: la referencia sigue siendo Microsoft Learn.

## Recursos en inglés

### Professor Messer's CompTIA A+ 220-1202 Core 2 Training Course (sección 1: Operating Systems) — Professor Messer
- **URL:** https://www.professormesser.com/free-a-plus-training/220-1202/220-1202-video/220-1202-training-course/ · Vídeos concretos: "Task Manager" https://www.professormesser.com/free-a-plus-training/220-1202/220-1202-video/task-manager-220-1202/ · "The Microsoft Management Console" (Event Viewer, Device Manager, Services...) https://www.professormesser.com/free-a-plus-training/220-1202/220-1202-video/the-microsoft-management-console-220-1202/ · "The Windows Network Command Line" https://www.professormesser.com/free-a-plus-training/220-1202/220-1202-video/the-windows-network-command-line-220-1202/
- **Autor / organización:** Professor Messer (James Messer)
- **Idioma:** Inglés (subtítulos en YouTube)
- **Tipo:** Curso en vídeo; para este curso interesa la sección 1.x "Operating Systems" (~3 h)
- **Duración aproximada:** 3 h (solo sección 1)
- **Cubre:** Todo el temario: estructura de Windows, Task Manager, MMC (Event Viewer, Device Manager, Services, Local Users and Groups), CMD, redes en Windows, herramientas de línea de comandos, troubleshooting.
- **Nivel:** Introductorio-intermedio (nivel CompTIA A+)
- **Acceso:** Libre (vídeos gratuitos; notas y exámenes de práctica de pago, no necesarios)
- **Por qué lo recomiendo:** Es el recurso en inglés que cubre exactamente el temario del curso, herramienta por herramienta, con demostraciones en pantalla. Actualizado a la versión 2025 del examen A+.

### Windows commands (referencia de comandos) — Microsoft Learn
- **URL:** https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/windows-commands (también en español: https://learn.microsoft.com/es-es/windows-server/administration/windows-commands/windows-commands)
- **Autor / organización:** Microsoft
- **Idioma:** Inglés (existe traducción al español)
- **Tipo:** Documentación de referencia
- **Duración aproximada:** Consulta puntual
- **Cubre:** CMD: `ipconfig`, `ping`, `tracert`, `nslookup`, `net user`, `net localgroup`, `sc`, `tasklist`, `taskkill`, `set`, etc.
- **Nivel:** Todos
- **Acceso:** Libre
- **Por qué lo recomiendo:** Es la página de manual oficial de cada comando de Windows, el equivalente a `man` en Linux. Úsala para leer la sintaxis real de cada comando del laboratorio en vez de fiarte de blogs.

### Introduction to PowerShell y Introduction to scripting in PowerShell — Microsoft Learn
- **URL:** https://learn.microsoft.com/en-us/training/modules/introduction-to-powershell/ · https://learn.microsoft.com/en-us/training/modules/script-with-powershell/
- **Autor / organización:** Microsoft
- **Idioma:** Inglés
- **Tipo:** Módulos de aprendizaje
- **Duración aproximada:** 1 h el primero; el segundo (scripting) es opcional en este curso, ~1 h
- **Cubre:** PowerShell introductorio; scripting básico (opcional).
- **Nivel:** Introductorio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Versión en inglés de los módulos oficiales, útil para acostumbrarte a los nombres reales de los cmdlets y a la terminología con la que están escritos todos los ejemplos de PowerShell en Internet.

### Sysinternals (Process Explorer, Autoruns) — Microsoft Learn
- **URL:** https://learn.microsoft.com/en-us/sysinternals/ · Autoruns: https://learn.microsoft.com/en-us/sysinternals/downloads/autoruns
- **Autor / organización:** Microsoft (Sysinternals)
- **Idioma:** Inglés
- **Tipo:** Herramientas gratuitas con documentación oficial
- **Duración aproximada:** 20 min de lectura + uso
- **Cubre:** Troubleshooting elemental (qué arranca con el sistema, qué procesos hay).
- **Nivel:** Intermedio
- **Acceso:** Libre
- **Por qué lo recomiendo:** Complementario. Autoruns muestra todo lo que arranca con Windows (servicios, tareas, entradas de registro) y es la herramienta que usan los técnicos para encontrar software que ralentiza el arranque o que no debería estar ahí.

## Documentación oficial

- **Microsoft Learn — Documentación del cliente Windows:** https://learn.microsoft.com/es-es/windows/resources/
- **Microsoft Learn — Cuentas locales:** https://learn.microsoft.com/es-es/windows/security/identity-protection/access-control/local-accounts
- **Microsoft Learn — Referencia de comandos de Windows (CMD):** https://learn.microsoft.com/es-es/windows-server/administration/windows-commands/windows-commands
- **Microsoft Learn — Documentación de PowerShell:** https://learn.microsoft.com/es-es/powershell/ (referencia de cada cmdlet, por ejemplo `Get-Service`, `Get-WinEvent`, `Get-LocalUser`)
- **Microsoft Learn — Variables de entorno (Win32):** https://learn.microsoft.com/es-es/windows/win32/procthread/environment-variables
- **Microsoft Learn — Sysinternals:** https://learn.microsoft.com/en-us/sysinternals/
- **Microsoft Support — Tareas y configuración de red esenciales en Windows:** https://support.microsoft.com/es-es/windows/experience/connectivity-networking/essential-network-settings-and-tasks-in-windows

Regla del curso: cuando uses un comando o cmdlet nuevo, abre su página en Microsoft Learn (o ejecuta `Get-Help <cmdlet> -Online`) antes de buscar en un blog.

## Ruta recomendada de estudio

1. **Ver** los vídeos de Professor Messer "Task Manager", "The Microsoft Management Console" y "Additional Windows Tools" (~45 min). Ve abriendo en tu equipo cada herramienta que aparece: Administrador de tareas, `eventvwr.msc`, `devmgmt.msc`, `services.msc`, `compmgmt.msc`.
2. **Leer** "Cuentas locales" en Microsoft Learn (20 min). Anota qué cuentas y grupos existen por defecto en tu equipo (lo comprobarás en el laboratorio con `net user` y `net localgroup`).
3. **Hacer** la ruta de aprendizaje "Introducción a Windows PowerShell" de Microsoft Learn (2-3 h). Hazla con una consola de PowerShell abierta y ejecuta todo lo que se explica. Si algo no queda claro, ve el vídeo correspondiente de la serie en español.
4. **Leer** PowerShell 101, capítulos 1 a 4 (2 h). Objetivo: entender que en PowerShell todo son objetos y que la tubería pasa objetos, no texto. Practica `Get-Process | Sort-Object CPU -Descending | Select-Object -First 5`.
5. **Leer** la referencia de comandos de Windows para `ipconfig`, `ping`, `tracert`, `nslookup`, `net user`, `net localgroup`, `tasklist`, `taskkill` y `set` (45 min). Ejecuta cada uno.
6. **Hacer** el módulo "Configuración de la conectividad de red IP" (1 h). Ejecuta las herramientas mientras lo lees.
7. **Ver** el vídeo de Professor Messer "The Windows Network Command Line" (15 min) como repaso.
8. **Leer** la página de variables de entorno de Microsoft Learn (15 min) y compárala con lo que ves en `Get-ChildItem Env:` y en Propiedades del sistema → Variables de entorno.
9. **Hacer el laboratorio** (4-6 h, en dos o tres sesiones).
10. **Responder la evaluación** y **revisar el checklist**.

## Laboratorio

### Objetivo

Administrar tu equipo Windows como si fuera un puesto de trabajo de una empresa: crear usuarios y grupos con permisos controlados, inspeccionar y ajustar servicios, revisar eventos, gestionar software, diagnosticar la red y resolver dos averías provocadas, documentando todo con capturas y comandos.

### Requisitos

- Windows 10 u 11 con cuenta de administrador local.
- PowerShell 5.1 (viene con Windows) o PowerShell 7 (opcional, instalable con `winget install Microsoft.PowerShell`).
- Un compañero, el mentor o tu propia VM `lab-so` del curso anterior para la parte de red (opcional; si no, se usan hosts públicos).
- **Advertencia:** trabajarás con usuarios, servicios y variables de entorno reales de tu equipo. Sigue los pasos tal cual y deshaz al final lo indicado. No toques servicios que no aparezcan en las instrucciones.

### Instrucciones

Crea `laboratorio-windows.md` y ve documentando cada parte con los comandos usados, su salida (pegada como texto, no solo capturas) y al menos una captura por parte.

**Parte A — Reconocimiento del sistema (45 min)**

1. Abre PowerShell **como administrador** y ejecuta:
   ```powershell
   Get-ComputerInfo | Select-Object WindowsProductName, WindowsVersion, OsArchitecture, CsName, OsInstallDate
   Get-PSDrive -PSProvider FileSystem
   Get-ChildItem C:\ -Force | Select-Object Name, Mode, LastWriteTime
   $env:USERPROFILE; $env:SystemRoot; $env:ProgramFiles
   ```
   Explica con tus palabras para qué sirven `C:\Windows`, `C:\Program Files`, `C:\Program Files (x86)`, `C:\Users\<tu usuario>` y `C:\ProgramData`. ¿Por qué `ProgramData` y `AppData` están ocultas?
2. En el Explorador de archivos activa "Elementos ocultos" y "Extensiones de nombre de archivo". Explica por qué un técnico las activa siempre (pista: `factura.pdf.exe`).
3. Abre el Administrador de tareas → pestaña Inicio (o "Aplicaciones de inicio"). Anota qué programas arrancan con Windows y su impacto. Desactiva uno que no necesites y justifícalo.

**Parte B — Usuarios, grupos y permisos (60-90 min)**

4. Lista las cuentas y grupos existentes:
   ```powershell
   Get-LocalUser | Select-Object Name, Enabled, LastLogon
   Get-LocalGroup | Select-Object Name, Description
   Get-LocalGroupMember Administrators
   whoami /groups
   ```
   Compara con lo que leíste en "Cuentas locales": ¿qué cuentas predeterminadas ves, cuáles están deshabilitadas y por qué?
5. Crea un grupo `Operaciones` y dos usuarios **estándar** (no administradores), `ana.ops` y `luis.ops`, con contraseña, y añádelos al grupo. Hazlo con PowerShell y anota los comandos (`New-LocalUser`, `New-LocalGroup`, `Add-LocalGroupMember`). Comprueba el resultado con `net user` y `net localgroup Operaciones` desde CMD.
6. Crea la carpeta `C:\Compartido\Operaciones`. Con el Explorador (Propiedades → Seguridad → Opciones avanzadas):
   - Deshabilita la herencia (convierte los permisos heredados en explícitos).
   - Quita el acceso al grupo `Usuarios` (Users).
   - Da al grupo `Operaciones` permiso de **Modificar**.
   - Deja `Administradores` y `SYSTEM` con control total.
   Muestra el resultado con `icacls C:\Compartido\Operaciones` y explica cada línea.
7. Cambia de sesión a `ana.ops` (o usa `runas /user:ana.ops cmd`). Comprueba que puede crear un archivo en `C:\Compartido\Operaciones` y que **no** puede crear uno en `C:\Windows` ni en `C:\Users\<tu usuario>`. Captura los mensajes de error. Vuelve a tu sesión.
8. Intenta instalar cualquier programa como `ana.ops`. ¿Qué ocurre? Explica qué es UAC y por qué es correcto que pida credenciales de administrador.

**Parte C — Servicios y eventos (60 min)**

9. Servicios:
   ```powershell
   Get-Service | Group-Object Status | Select-Object Name, Count
   Get-Service | Where-Object Status -eq Running | Sort-Object DisplayName | Select-Object -First 20 Name, DisplayName, StartType
   Get-CimInstance Win32_Service | Where-Object Name -in 'Spooler','wuauserv','Dhcp','W32Time' | Select-Object Name, State, StartMode, StartName
   ```
   Explica para cada uno de los cuatro servicios: qué hace, con qué cuenta se ejecuta (`StartName`) y qué tipo de inicio tiene.
10. Detén el servicio **Cola de impresión (Spooler)** con `Stop-Service Spooler`. Intenta imprimir a PDF desde cualquier aplicación ("Microsoft Print to PDF"). ¿Qué pasa? Vuelve a iniciarlo con `Start-Service Spooler` y comprueba que funciona. Documenta el síntoma que vería un usuario y cómo lo relacionarías con el servicio.
11. Visor de eventos. Abre `eventvwr.msc` → Registros de Windows → Sistema. Crea un filtro (Filtrar registro actual) con nivel **Error** y **Crítico** de los últimos 7 días. Anota los tres orígenes más frecuentes y qué significa uno de los eventos (busca su ID en Microsoft Learn o en la propia descripción). Después localiza en el registro **Sistema** los eventos que generaste al parar y arrancar el Spooler (origen Service Control Manager, ID 7036). Repite la búsqueda desde PowerShell:
    ```powershell
    Get-WinEvent -FilterHashtable @{LogName='System'; Id=7036; StartTime=(Get-Date).AddHours(-2)} | Select-Object TimeCreated, Message | Format-List
    ```
12. Administrador de dispositivos. Abre `devmgmt.msc` → Ver → Mostrar dispositivos ocultos. Anota si hay algún dispositivo con icono de advertencia. Localiza tu adaptador de red, abre Propiedades → Controlador y anota proveedor, fecha y versión. Explica qué harías si el adaptador apareciera con un signo de exclamación.

**Parte D — CMD, PowerShell y variables de entorno (45 min)**

13. Ejecuta en **CMD**: `dir`, `cd`, `type`, `tasklist | findstr explorer`, `set`, `echo %PATH%`, `where notepad`. Ejecuta lo equivalente en **PowerShell**: `Get-ChildItem`, `Set-Location`, `Get-Content`, `Get-Process explorer`, `Get-ChildItem Env:`, `$env:PATH -split ';'`, `Get-Command notepad`. Escribe una tabla de equivalencias y explica en 5 líneas la diferencia de fondo entre CMD y PowerShell (texto frente a objetos).
14. Variables de entorno. Crea una carpeta `C:\Herramientas`, guarda dentro un archivo `hola.cmd` con el contenido `@echo Hola desde %COMPUTERNAME%, usuario %USERNAME%`. Comprueba que `hola` **no** funciona desde otra carpeta. Añade `C:\Herramientas` al `PATH` **de usuario** (Propiedades del sistema → Variables de entorno, o `[Environment]::SetEnvironmentVariable('Path', $env:Path + ';C:\Herramientas', 'User')`). Abre una consola **nueva** y comprueba que ahora `hola` funciona desde cualquier carpeta. Explica por qué hacía falta abrir una consola nueva y qué diferencia hay entre variables de usuario y de sistema.
15. Usa `Get-Help Get-Service -Full` y `Get-Help Get-WinEvent -Examples`. Encuentra por ti mismo, solo con la ayuda, cómo listar los servicios cuyo tipo de inicio es Automático pero están detenidos, y ejecútalo. Anota el comando y qué encontraste.

**Parte E — Software (20 min)**

16. Lista el software instalado con `winget list` (y opcionalmente `Get-Package`). Instala una herramienta útil con `winget install` (por ejemplo `7zip.7zip`, `Microsoft.PowerShell` o `Git.Git`, que necesitarás en el curso 7) y desinstala alguna aplicación que no uses, primero desde Configuración → Aplicaciones y después otra con `winget uninstall`. Documenta ambos métodos y cuándo usarías cada uno.

**Parte F — Red y diagnóstico (60 min)**

17. Ejecuta y explica cada línea de la salida:
    ```cmd
    ipconfig /all
    ```
    Identifica: tu IPv4, máscara, puerta de enlace, servidores DNS, si la IP la asignó DHCP (y cuándo caduca la concesión) y la dirección MAC.
18. Conectividad por capas. Ejecuta en orden y explica qué prueba cada paso y qué concluirías si fallara **solo** ese paso:
    ```cmd
    ping 127.0.0.1
    ping <tu IPv4>
    ping <tu puerta de enlace>
    ping 1.1.1.1
    ping learn.microsoft.com
    nslookup learn.microsoft.com
    nslookup learn.microsoft.com 8.8.8.8
    tracert -d 1.1.1.1
    ```
    En PowerShell prueba también `Test-NetConnection learn.microsoft.com -Port 443` y explica qué añade respecto a `ping`.
19. **Avería provocada 1 (DNS).** Cambia el servidor DNS de tu adaptador a una IP inválida, por ejemplo `10.255.255.1` (Configuración → Red → Propiedades del adaptador → Asignación de servidor DNS → Manual). Abre el navegador e intenta entrar en una web. Ejecuta los comandos del paso 18 y explica cuáles fallan y cuáles no, y por qué eso te dice que el problema es DNS y no "Internet". Restaura DNS a automático.
20. **Avería provocada 2 (servicio).** Deshabilita el servicio **Cliente DHCP** (`Set-Service Dhcp -StartupType Disabled; Stop-Service Dhcp -Force`) y reinicia el adaptador de red (deshabilitar y habilitar). Ejecuta `ipconfig`. ¿Qué IP tienes ahora y por qué (busca "APIPA" y el rango 169.254.x.x)? Registra en el Visor de eventos qué eventos aparecieron. Restaura: `Set-Service Dhcp -StartupType Automatic; Start-Service Dhcp` y reinicia el adaptador.

**Parte G — Limpieza y método (15 min)**

21. Elimina los usuarios `ana.ops` y `luis.ops`, el grupo `Operaciones`, la carpeta `C:\Compartido` y la entrada `C:\Herramientas` del `PATH` si no quieres conservarla. Comprueba que Spooler y Cliente DHCP están en Automático y en ejecución.
22. Escribe, en 10-15 líneas, el **método de troubleshooting** que has seguido en las averías 19 y 20, en pasos genéricos reutilizables (síntoma → reproducir → aislar por capas → hipótesis → prueba → corrección → verificación → documentación).

### Resultado esperado

Un documento con las siete partes, comandos con su salida, capturas, la tabla CMD/PowerShell, el análisis de las dos averías y el método de troubleshooting. El equipo debe quedar como estaba (usuarios de prueba eliminados, servicios restaurados).

### Criterios de validación

- [ ] Parte B: los usuarios se crearon como estándar (no administradores), los permisos NTFS muestran herencia deshabilitada y `icacls` refleja exactamente lo pedido; las pruebas de acceso de `ana.ops` incluyen el error de acceso denegado.
- [ ] Parte C: los cuatro servicios están descritos con función, cuenta y tipo de inicio correctos; el evento 7036 del Spooler aparece tanto en el Visor como en `Get-WinEvent`.
- [ ] Parte D: la tabla CMD/PowerShell es correcta; la explicación de por qué hace falta una consola nueva tras cambiar `PATH` es correcta; el comando del paso 15 se encontró usando la ayuda (se acepta cualquier forma válida).
- [ ] Parte F: la interpretación de `ipconfig /all` identifica correctamente cada dato; el diagnóstico por capas explica correctamente qué significa que falle cada paso; la avería 1 se identifica como DNS con los comandos que lo demuestran (`ping 1.1.1.1` funciona, `ping learn.microsoft.com` falla, `nslookup ... 8.8.8.8` funciona); la avería 2 explica APIPA.
- [ ] Parte G: el sistema se restauró y el método de troubleshooting es genérico y aplicable a otros casos.
- [ ] Las explicaciones están escritas con palabras propias.

## Entrega

En tu repositorio de entregas, carpeta `01-modulo-basico/04-windows-basico/`:

1. `laboratorio-windows.md` con las siete partes.
2. Carpeta `capturas/`.
3. `comandos.ps1`: un archivo con **todos** los comandos de PowerShell que usaste, en orden, comentados con `#` explicando qué hace cada bloque (no es un script para ejecutar de golpe, es tu bitácora).
4. `ENTREGA.md` con evaluación, checklist y uso de IA.

## Evaluación

1. **Conceptual.** ¿Por qué Microsoft recomienda trabajar a diario con una cuenta estándar y elevar privilegios solo cuando hace falta? ¿Qué mecanismo de Windows hace posible esa elevación?
2. **Situacional.** Un usuario del grupo `Contabilidad` puede leer pero no modificar los archivos de `D:\Datos\Contabilidad`, aunque su grupo tiene permiso de Modificar en esa carpeta. Da dos causas posibles relacionadas con permisos NTFS y cómo comprobarías cada una.
3. **Conceptual.** ¿Qué diferencia hay entre un servicio con inicio Automático, Automático (inicio retrasado), Manual y Deshabilitado? ¿Cuándo usarías cada uno?
4. **Situacional.** Nadie en la oficina puede imprimir desde esta mañana. ¿Qué servicio revisarías primero, qué comando usarías para verlo y qué buscarías en el Visor de eventos?
5. **Troubleshooting.** Un equipo va muy lento al arrancar. Describe tres herramientas de Windows que usarías, en orden, para encontrar la causa.
6. **Técnica.** Explica la diferencia entre CMD y PowerShell con un ejemplo: cómo obtendrías en cada uno los cinco procesos que más memoria consumen. ¿Por qué en PowerShell puedes hacer `| Sort-Object` y en CMD no hay un equivalente directo?
7. **Técnica.** ¿Qué hace la tubería (`|`) en PowerShell? ¿Qué devuelve `Get-Service | Where-Object Status -eq Stopped | Select-Object -First 3`?
8. **Situacional.** Instalas una herramienta de línea de comandos y al escribir su nombre la consola dice que no se reconoce como comando. ¿Qué variable de entorno está implicada, cómo la revisarías y qué dos formas hay de solucionarlo?
9. **Conceptual.** ¿Qué diferencia hay entre una variable de entorno de usuario y una de sistema? Da un ejemplo de cada una que ya exista en Windows.
10. **Troubleshooting.** `ping 8.8.8.8` responde pero `ping www.microsoft.com` da "No se puede encontrar el host". ¿Qué falla? ¿Qué comando lo confirma y cómo lo arreglarías temporalmente?
11. **Troubleshooting.** `ipconfig` muestra la dirección 169.254.23.7 y no hay conexión. ¿Qué significa esa dirección, qué la asigna y cuáles son las dos causas más probables?
12. **Técnica.** ¿Qué te dice `tracert` que no te dice `ping`? ¿Por qué algunos saltos aparecen como `*` y eso no siempre significa un problema?
13. **Conceptual.** ¿Para qué sirve el Visor de eventos en un incidente real? Describe los tres registros principales (Aplicación, Seguridad, Sistema) y qué tipo de evento buscarías en cada uno.
14. **Situacional.** Un compañero instala software descargado de una web cualquiera haciendo doble clic en un `.exe`. Explícale por qué `winget` (o un repositorio controlado) es preferible en una empresa, con al menos dos razones.
15. **Reflexión.** Nombra tres cosas del laboratorio que tengan un equivalente directo en Linux (según lo que viste en el curso anterior) y una que no lo tenga o funcione de forma distinta.

## Checklist final

Antes de continuar, deberías poder:

- [ ] Explicar la estructura de carpetas básica de Windows y para qué sirve cada carpeta del sistema.
- [ ] Crear y eliminar usuarios y grupos locales desde PowerShell y desde la interfaz.
- [ ] Leer y modificar permisos NTFS, incluida la herencia, y verificarlos con `icacls`.
- [ ] Listar, iniciar, detener y cambiar el tipo de inicio de un servicio, y saber con qué cuenta corre.
- [ ] Encontrar un error en el Visor de eventos filtrando por nivel, origen y fecha, con la interfaz y con `Get-WinEvent`.
- [ ] Identificar un dispositivo con problemas de driver en el Administrador de dispositivos.
- [ ] Usar `Get-Help`, `Get-Command` y la tubería para construir un comando de PowerShell que no conocías.
- [ ] Explicar y modificar variables de entorno, incluido `PATH`.
- [ ] Instalar y desinstalar software con la interfaz y con `winget`.
- [ ] Leer `ipconfig /all` completo y diagnosticar conectividad por capas con `ping`, `tracert`, `nslookup` y `Test-NetConnection`.
- [ ] Distinguir un fallo de DNS de un fallo de conectividad IP y de un fallo de DHCP.
- [ ] Describir un método de troubleshooting genérico en pasos.

---

*Recursos verificados el 2026-09-26 mediante búsqueda web (existencia y vigencia de las URLs). Si un enlace falla, abre un issue en este repositorio.*
