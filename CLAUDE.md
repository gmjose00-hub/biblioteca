# CLAUDE.md — Plantilla para cada carpeta de proyecto

> Copia este archivo en la raíz de CADA proyecto nuevo y rellena la sección 1.
> Mantenlo corto: se carga en cada sesión y cada línea cuesta tokens.

## 1. Contexto del proyecto (rellenar al crear el proyecto)
- **Nombre:**
- **Qué hace (1-2 frases):**
- **Usuario final:**
- **Stack:** (lenguaje, framework, base de datos)
- **Cómo se ejecuta:** (comando)
- **Cómo se prueba:** (comando)
- **Estado actual:** ver `docs/ESTADO.md`

## 2. Sobre quién te lo pide
- El propietario NO programa: sabe qué quiere y cómo lo quiere. Explica en lenguaje llano, sin jerga innecesaria.
- No tomes decisiones de alcance por tu cuenta: si algo es ambiguo, pregunta UNA vez, con opciones concretas.
- Español de España. Fechas dd/mm/aaaa. Unidades métricas.

## 3. Ahorro de tokens
- No leas el proyecto entero. Empieza por este archivo y `docs/ESTADO.md`; abre solo los archivos que necesites.
- Busca antes de leer (Grep/Glob). Lee por tramos (offset/limit), no archivos completos de más de 300 líneas.
- No releas lo que acabas de editar ni pegues código largo en el chat: indica archivo y cambio.
- Ignora siempre: `node_modules/`, `dist/`, `build/`, `.venv/`, `__pycache__/`, `*.lock`, binarios, datos, logs.
- Respuestas cortas: qué has hecho, dónde y qué falta. Sin resúmenes repetidos ni explicaciones no pedidas.
- Tareas grandes: divídelas en pasos pequeños y verificables; no abras varias líneas de trabajo a la vez.
- Al terminar cada sesión, actualiza `docs/ESTADO.md` (máx. 20 líneas) para que la siguiente no tenga que reconstruir el contexto.

## 4. Flujo de trabajo (explorar → plan → ejecutar → comprobar)
- **Primero entiende, luego edita:** en un proyecto o zona nueva, empieza respondiendo preguntas (cómo funciona X, dónde se usa Y, por qué está así según el historial de git) antes de tocar nada.
- **Plan antes de código en lo grande:** ante una función o cambio no trivial, propón un plan breve (qué harás, archivos afectados, riesgos) y espera confirmación antes de escribir código. En cambios pequeños no hace falta.
- **Comprueba tu trabajo e itera:** ejecuta las pruebas o la interfaz, compara con lo pedido y corrige hasta que cuadre antes de presentar el resultado. Si no hay forma de comprobarlo, dilo y propón una.
- **Aprende de los errores:** si el propietario te corrige algo que puede repetirse (formato, unidad, convención, decisión), añade una línea en la sección 11 para no repetirlo.

## 5. Contexto y memoria (CLAUDE.md)
- Este archivo debe ser corto: solo comandos, decisiones de arquitectura y archivos clave.
- Lo que sea de una zona concreta va en un `CLAUDE.md` dentro de esa subcarpeta (se carga solo cuando trabajas ahí). Lo personal, en `CLAUDE.local.md` (no se sube a git).
- Lo que se repite (comandos de prueba, herramientas, servidores MCP) se configura una vez: `.mcp.json` y `.claude/commands/` en la raíz del proyecto, en vez de explicarlo en cada sesión.
- Al cerrar sesión, poda lo obsoleto: una regla que ya no aplica solo gasta tokens.

## 6. Arquitectura (reglas no negociables)
- **Separación de capas:** interfaz (UI/CLI/API) → lógica de negocio → acceso a datos. La UI nunca habla con la base de datos directamente.
- **Una responsabilidad por módulo/función.** Funciones cortas (idealmente < 40 líneas), archivos < 300 líneas.
- **Sin duplicar:** si algo se escribe dos veces, se extrae a una función o módulo común.
- **Configuración fuera del código:** rutas, claves, URLs y parámetros en `config/` o variables de entorno. Nada «hardcodeado».
- **Secretos:** jamás en el repositorio. `.env` en `.gitignore`; deja un `.env.example` sin valores reales.
- **Dependencias mínimas:** no añadas una librería nueva si la estándar lo resuelve; si la añades, anótalo en `docs/DECISIONES.md`.
- **Errores:** nunca silencies una excepción. Captura donde puedas actuar, registra con contexto y muestra al usuario un mensaje comprensible.
- **Nombres claros** y consistentes (un idioma, un estilo). Nada de abreviaturas crípticas.
- **Datos del usuario:** valida toda entrada; no confíes en formatos de fichero externos sin comprobar.
- **Rutas portables:** el proyecto se usa en dos equipos Windows con rutas de OneDrive distintas. Usa rutas relativas a la raíz del proyecto o configurables; nunca rutas absolutas fijas.

## 7. Estructura de carpetas recomendada
```
proyecto/
├── CLAUDE.md
├── README.md            # qué es y cómo arrancarlo (para humanos)
├── docs/
│   ├── ESTADO.md        # estado actual y próximos pasos (breve)
│   └── DECISIONES.md    # decisiones de diseño y el porqué (una línea cada una)
├── src/
│   ├── ui/              # interfaz
│   ├── core/            # lógica de negocio (sin dependencias de UI)
│   ├── data/            # acceso a datos / ficheros / APIs
│   └── utils/           # utilidades pequeñas y genéricas
├── config/
├── tests/
└── .env.example
```

## 8. Calidad y pruebas
- Toda lógica de negocio nueva lleva al menos una prueba automática. Antes de dar algo por hecho, ejecútalo y comprueba que funciona.
- No des por terminada una tarea si hay errores o avisos sin explicar.
- Refactoriza solo lo que toca la tarea; no reescribas código que funciona «por limpieza».

## 9. Git
- Commits pequeños, con mensaje en imperativo y en español (`Añade validación de parcelas`).
- Un cambio lógico por commit. Nunca subas datos reales de clientes, claves ni binarios pesados.
- Antes de cambios grandes o destructivos, avisa y propón una rama.

## 10. Qué NO hacer
- No inventes requisitos, datos ni cifras. Si falta información, pregunta.
- No borres ni muevas archivos del usuario sin pedir confirmación.
- No cambies la estructura del proyecto ni el stack sin anotarlo y avisar.
- No dejes código muerto, comentado o `TODO` sin dueño.

## 11. Lecciones del proyecto (se rellena con el uso)
- (una línea por lección: qué falló y qué hacer en su lugar)

## 12. Atajos del propietario (referencia; Claude no necesita actuar)
- `#` + texto: Claude lo guarda en su memoria (CLAUDE.md). `!` + comando: lo ejecuta en local y lo ve Claude. (Pueden variar según la versión.)
- Mayús+Tab: aceptar ediciones automáticamente (cuando va bien encaminado). Esc: parar a Claude sin riesgo; Esc dos veces: volver atrás.
- `/memory`: ver y editar los CLAUDE.md cargados. `claude --continue` o `--resume`: retomar una sesión. Ctrl+R: ver la salida completa.
- Para prompts largos y concretos, dictar con Win+H en lugar de teclear.
