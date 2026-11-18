# contenidos-test

Repositorio de **materiales docentes LiaScript** para el sistema
*Materiales Editables* (LiaEditor–Moodle). Git es la única fuente de
verdad del contenido; Moodle solo lo vincula y publica.

## Estructura

```text
materiales/          # un material = un fichero .md LiaScript
├── ut03-mvc.md      # UT03 — El patrón MVC en PHP
├── ut04-pdo.md      # UT04 — La capa de acceso a datos con PDO
└── demo-liascript.md # escaparate de capacidades LiaScript
```

Cada material lleva una cabecera de comentario HTML con metadatos
LiaScript (`author`, `title`, `language`, `version`, `comment`). El
`title` alimenta el catálogo de Moodle.

## Flujo de edición

- El profesorado **no edita aquí directamente**: lo hace desde Moodle con
  el editor LiaEdit, que crea ramas `edicion/<usuario>/<material>` y
  commitea con token de servidor.
- Los conflictos de edición concurrente se resuelven en ramas
  `resolucion/<usuario>/<timestamp>-<material>`.
- `main` es la línea oficial (máster). Solo mantenedores.
