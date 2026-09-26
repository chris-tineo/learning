# Guía de uso de la ruta

Esta guía explica cómo estudiar la ruta de forma autónoma, cómo entregar el trabajo y qué papel tiene el mentor.

## 1. Cómo está organizado cada curso

Cada curso es un único archivo `README.md` con estas secciones, siempre en el mismo orden:

1. **Nombre del curso y objetivo**
2. **Prerrequisitos**
3. **Temario** (fijo, no se modifica)
4. **Recursos en español**
5. **Recursos en inglés**
6. **Documentación oficial** (cuando el curso trata una tecnología concreta)
7. **Ruta recomendada de estudio** (el orden en el que consumir los recursos)
8. **Laboratorio**
9. **Entrega**
10. **Evaluación**
11. **Checklist final**

La regla general es **30 % teoría, 60 % práctica, 10 % evaluación**. Si notas que llevas horas leyendo y no has tocado una terminal, estás fuera de proporción.

## 2. Cómo estudiar un curso

1. Lee la introducción y los objetivos. Si no cumples los prerrequisitos, vuelve al curso anterior.
2. Sigue la **ruta recomendada de estudio** en orden. No es una colección de enlaces: está secuenciada.
3. Haz el **laboratorio** completo. No lo leas, hazlo. Documenta lo que te sale mal: eso es parte del aprendizaje.
4. Prepara la **entrega** con la plantilla de entregas.
5. Responde la **evaluación** por escrito, con tus palabras, sin copiar de Internet.
6. Repasa el **checklist final**. Si hay casillas que no puedes marcar con honestidad, no avances todavía.

Cuando te quedes bloqueado más de 30-45 minutos en algo, pide ayuda al mentor. Antes de preguntar, escribe: qué intentabas hacer, qué esperabas que pasara, qué pasó realmente y qué has probado ya. Esa disciplina es exactamente la que usarás después para abrir incidentes y tickets.

## 3. Entregas

Cada estudiante crea un **repositorio propio en GitHub** llamado `learning-entregas-<tu-usuario>` (o el nombre que el mentor indique) con esta estructura:

```
learning-entregas-<usuario>/
├── README.md                     # quién eres, en qué curso estás
├── 01-modulo-basico/
│   ├── 01-historia-de-la-computacion/
│   │   ├── ENTREGA.md            # copia de plantillas/plantilla-entrega.md rellenada
│   │   └── ...                   # capturas, código, diagramas
│   ├── 02-fundamentos-de-hardware/
│   └── ...
├── 02-modulo-intermedio/
├── 03-modulo-avanzado/
└── 04-proyecto-final/
```

Reglas:

- Una carpeta por curso, con un `ENTREGA.md` basado en [`plantillas/plantilla-entrega.md`](../plantillas/plantilla-entrega.md).
- Las capturas de pantalla deben mostrar **tu** nombre de usuario, nombre de máquina o fecha visible cuando sea posible.
- El código, los scripts, el Terraform y los pipelines van como archivos, no como capturas.
- La evaluación se responde dentro de `ENTREGA.md`, con tus palabras.
- Cuando termines un curso, avisa al mentor con el enlace a la carpeta. Si el mentor lo prefiere, abre un Pull Request en tu propio repo para que revise con comentarios en línea.

Hasta el curso "Fundamentos de Git" (Módulo Básico, curso 7) no sabrás usar Git. Para los cursos 1 a 6, puedes subir los archivos por la interfaz web de GitHub o entregarlos por el canal que indique el mentor; a partir del curso 7 se espera que uses Git.

## 4. Entorno de laboratorio

A lo largo de la ruta necesitarás:

| Necesidad | Desde qué curso | Opción recomendada | Coste |
|---|---|---|---|
| Un equipo Windows o macOS/Linux con permisos de administrador | Curso 2 | Tu propio equipo | 0 |
| Software de virtualización | Curso 3 | VirtualBox (Windows/Linux/mac Intel), Hyper-V (Windows Pro), UTM (mac Apple Silicon) | 0 |
| Una VM Linux | Curso 3 | Ubuntu LTS o Debian estable en la VM | 0 |
| Cuenta de GitHub | Curso 7 | github.com | 0 |
| Cuenta de Azure | Curso 8 | Cuenta gratuita de Azure o Azure for Students | Ver nota |

**Nota sobre Azure.** La cuenta gratuita estándar de Azure exige una **tarjeta de crédito o débito no prepagada** para verificar identidad, aunque no se cobra nada mientras no cambies a pago por uso y no superes los límites gratuitos. La opción **Azure for Students** no exige tarjeta pero requiere un correo académico válido. Se explica en detalle en el curso "Introducción a Cloud Computing". Hasta ese curso no necesitas Azure.

Si tu equipo es poco potente (menos de 8 GB de RAM), avisa al mentor: hay alternativas para las VMs (por ejemplo, usar una VM pequeña en Azure cuando llegues al curso 8, o WSL en Windows para gran parte de la práctica Linux).

## 5. Uso de Inteligencia Artificial durante la ruta

La IA (ChatGPT, Copilot, Claude, Gemini u otras) es una herramienta legítima y **se espera que la uses**, pero con criterio:

- **Sí**: pedir que te explique un error, un comando, un concepto; pedir ejemplos; pedir que te haga preguntas de repaso; pedir que revise un script que ya escribiste.
- **No**: pegar el enunciado del laboratorio y copiar la respuesta; responder la evaluación con texto generado; entregar código que no entiendes línea por línea.
- **Siempre**: verifica lo que te dice contra la documentación oficial. Los modelos inventan flags, versiones y nombres de servicios.
- **Nunca** pegues credenciales, tokens, claves, IPs internas ni datos de clientes en una herramienta de IA.

En la entrega hay una sección "Uso de IA" donde declaras para qué la usaste. Declararlo no penaliza; ocultarlo sí.

El principio de toda la ruta: **la IA acelera el aprendizaje y el trabajo, no sustituye la comprensión técnica.** Si no puedes explicar con tus palabras lo que entregas, no lo has aprendido todavía.

## 6. Papel del mentor

El mentor:

- Responde dudas y desbloquea cuando el estudiante lleva un rato atascado.
- Revisa las entregas con los criterios de validación de cada laboratorio.
- Decide si el estudiante avanza al siguiente curso o repite parte del actual.
- Ajusta el ritmo. No hay fechas fijas: hay hitos.

El mentor **no** da clases ni resuelve el laboratorio por el estudiante.

## 7. Sobre los recursos enlazados

- Todos los recursos son gratuitos. Cuando exigen registro (por ejemplo, Cisco Networking Academy o Microsoft Learn para guardar progreso) se indica. Cuando algo exige tarjeta de crédito, se dice de forma explícita.
- La documentación oficial siempre tiene prioridad sobre blogs y vídeos.
- Los vídeos antiguos se incluyen solo cuando los conceptos siguen siendo válidos, y se indica.
- Las URLs se verifican en la fecha indicada al pie de cada curso. Si encuentras un enlace roto, abre un issue en este repositorio o avisa al mentor.

## 8. Idiomas

La ruta está escrita en español. Desde el primer curso hay recursos en inglés porque la documentación técnica real está en inglés y hay que acostumbrarse cuanto antes. No hace falta el mismo recurso en ambos idiomas: se eligen los mejores disponibles en cada uno.
