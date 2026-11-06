# contenidos-test

Repositorio de contenidos de prueba para **Moodle Course as Code** (entorno
alpha): módulo *Desarrollo Web en Entorno Servidor* (2º DAW).

## Estructura

```text
course.yml          # manifest del curso (lista de books)
books/ut03-mvc/     # book de prueba: MVC y patrones de diseño
```

## Flujo de publicación

1. Edita el contenido y valida: `courseascode validate .`
2. Preview local: `courseascode preview books/ut03-mvc`
3. Publica una versión con tag: `git tag book/ut03-mvc/v1.1.0 && git push --tags`
4. Los cursos Moodle vinculados verán `UPDATE_AVAILABLE` en el panel del
   plugin `local_courseascode`.

Las versiones oficiales son los tags `book/<id>/vX.Y.Z` (nunca HEAD).
