# contenidos-test

Repositorio de **materiales docentes LiaScript** para el sistema
*Materiales Editables* (LiaEditor–Moodle). Git es la única fuente de
verdad del contenido; Moodle solo lo vincula y publica.

Además de material de ejemplo, es el **conjunto de pruebas** del editor
y del pipeline de publicación: entre todos los materiales cubren los
constructos LiaScript que el editor debe conservar.

## Estructura

```text
materiales/                  # un material = un fichero .md LiaScript
├── ut03-mvc.md              # UT03 — El patrón MVC en PHP
├── ut04-pdo.md              # UT04 — La capa de acceso a datos con PDO
├── ut05-sesiones.md         # UT05 — Sesiones y cookies en PHP
├── demo-liascript.md        # escaparate de capacidades LiaScript
└── demo-python-pyodide.md   # Python ejecutable con plantilla importada
```

| Material | Qué cubre |
| --- | --- |
| `ut03-mvc`, `ut04-pdo` | Unidades de prosa con tablas, código PHP y autoevaluación (opción única, múltiple, respuesta corta) |
| `ut05-sesiones` | Unidad completa con cajas (`@nota`, `@aviso`, `@error`), narración, animaciones `{{n}}` con bloques `****`, quiz con solución, matriz, selección en línea y encuesta |
| `demo-liascript` | Todos los tipos de quiz y encuesta, cajas, fórmulas, notas al pie, `~sub~`/`^sup^`, JavaScript ejecutable, animaciones y narración |
| `demo-python-pyodide` | `import:` de una plantilla externa fijada (LiaTemplates/Pyodide 0.3.5) y bloques `@Pyodide.eval`. Al exportarlo, liaex necesita red para descargar la plantilla |

## Convenciones

Cada material lleva una cabecera de comentario HTML con metadatos
LiaScript (`author`, `title`, `language`, `version`, `comment`). El
`title` alimenta el catálogo de Moodle.

- **Quizzes sin indentar.** `[( )]`/`[(X)]` es opción única, `[[ ]]`/`[[X]]`
  opción múltiple, `[[respuesta]]` respuesta corta, `[[a | (b) | c]]`
  selección en línea y `[[?]]` una pista. La solución va entre líneas de
  `****` justo debajo.
- **Encuestas (sin nota)**: `[(1)]`, `[(2)]`… (una opción), `[[1]]`,
  `[[2]]`… (varias) y `[[___]]` (texto libre). Ojo: `[(X)]` no es una
  encuesta, es un quiz puntuable.
- **Cajas** `@nota`, `@aviso` y `@error`: macros definidas en la cabecera
  del propio material. El texto va entre comillas invertidas,
  `@aviso(`…`)`, para que pueda llevar comas. Dentro, los guiones bajos se
  escapan (`password\_verify`) y no se usan comillas invertidas ni
  paréntesis.
- **Plantillas** importadas siempre con versión fija en la URL (etiqueta,
  nunca `main`/`master`).
- Solo encabezados `#` (ATX): LiaScript no trata `Título\n=====` como
  sección.

Comprobación antes de subir un cambio (requiere Docker):

```bash
docker run --rm -v "$PWD/materiales":/work liascript/exporter \
  liaex -i /work/<material>.md -f fullJson -o /work/<material>
```

El JSON resultante (`quiz`, `survey` por sección) dice qué quizzes y
encuestas reconoce realmente LiaScript. No lo subas al repo.

## Flujo de edición

- El profesorado **no edita aquí directamente**: lo hace desde Moodle con
  el editor, que crea ramas `edicion/<usuario>/<material>` y commitea con
  token de servidor.
- Los conflictos de edición concurrente se resuelven en ramas
  `resolucion/<usuario>/<timestamp>-<material>`.
- `main` es la línea oficial (máster). Solo mantenedores.
