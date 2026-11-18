<!--

author:   Equipo LiaEditor
title:    Demo — lo que puedes hacer con LiaScript
language: es
version:  1.0.0
comment:  Muestra de las capacidades de LiaScript para el profesorado.
          Ábrelo en el editor para ver el código fuente de cada ejemplo.

-->

# Demo — lo que puedes hacer con LiaScript

Este material demuestra los componentes que puedes usar en tus unidades.
Ábrelo en modo edición para ver cómo está escrito cada ejemplo.

## Texto enriquecido

Puedes usar **negrita**, *cursiva*, ~~tachado~~, `código en línea`,
subíndices H~2~O y superíndices E=mc^2^, enlaces a
[documentación](https://liascript.github.io/) y notas al pie.[^1]

[^1]: Las notas al pie se definen al final del documento y LiaScript las
      convierte en referencias navegables.

> Las citas en bloque sirven para objetivos, avisos o definiciones
> destacadas.

## Tablas

| Componente | Sintaxis | Renderiza |
|---|---|---|
| Quiz opción única | `[[a|X|b]]` | Botones de selección |
| Código | ` ``` php ` | Resaltado de sintaxis |
| Fórmula | `$a^2+b^2=c^2$` | KaTeX |

## Fórmulas

Las fórmulas se escriben en LaTeX entre dólares. En línea: $e^{i\pi}+1=0$.

Y en bloque:

$$
\int_{a}^{b} f'(x)\,dx = f(b) - f(a)
$$

## Código con resaltado

```python
def fibonacci(n: int) -> int:
    """Sucesión de Fibonacci (ejemplo de resaltado Python)."""
    a, b = 0, 1
    for _ in range(n):
        a, b = b, a + b
    return a
```

```sql
SELECT curso, COUNT(*) AS materiales
FROM materiales
GROUP BY curso
ORDER BY materiales DESC;
```

## Autoevaluación: opción única

¿Qué símbolo marca una respuesta correcta en un quiz LiaScript?

    [[( )]]
    [[(X)]]
    [[?]] Piensa en cómo marcarías una casilla a mano.

## Autoevaluación: opción múltiple

Marca los formatos a los que Materiales Editables puede exportar:

    [[X]] H5P
    [[X]] ePub
    [[X]] PDF
    [[ ]] EXE

## Autoevaluación: respuesta corta

¿Qué sistema es la fuente de verdad de los materiales?

    [[Git]]

## Encuestas (sin nota)

¿Te resulta útil la autoevaluación en los materiales?

    [( )] Nada
    [(X)] Bastante
    [( )] Mucho

## Diagramas en texto plano

```text
┌──────────┐   edita    ┌─────────┐   commit   ┌─────┐
│ Profesor │ ─────────▶ │ LiaEdit │ ─────────▶ │ Git │
└──────────┘            └─────────┘            └─────┘
```

## Bloques plegables y multimedia

- Las imágenes se insertan con `![pie](ruta-de-la-imagen.jpg)`.
- Los vídeos de YouTube se embeben con `!?[título](url-del-vídeo)`.
- Cada sección puede ocultarse/mostrarse desde el índice del curso.

> **Consejo:** todo lo de esta página es Markdown normal con algunas
> extensiones. Si sabes Markdown, ya sabes el 90% de LiaScript.
