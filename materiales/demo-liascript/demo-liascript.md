<!--

author:   Equipo LiaEditor
title:    Demo — lo que puedes hacer con LiaScript
language: es
narrator: Spanish Female
version:  1.1.0
comment:  Muestra de las capacidades de LiaScript para el profesorado.
          Ábrelo en el editor para ver el código fuente de cada ejemplo.

@nota
<div style="border-left: 4px solid #2e7d32; background: #edf7ee; padding: .6em 1em; margin: 1em 0">

**Nota:** @0

</div>
@end

@aviso
<div style="border-left: 4px solid #b26a00; background: #fff4e5; padding: .6em 1em; margin: 1em 0">

**Aviso:** @0

</div>
@end

@error
<div style="border-left: 4px solid #c62828; background: #fdecea; padding: .6em 1em; margin: 1em 0">

**Error frecuente:** @0

</div>
@end

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

## Imágenes

Las imágenes viven en la carpeta `img/` del material y se enlazan con
rutas relativas. El texto entre corchetes es el **texto alternativo**:
descríbela para quien no pueda verla.

![Paisaje de montañas verdes bajo un cielo azul con el sol](img/paisaje.jpg "Una foto en JPEG")

También pueden ir dentro de un párrafo, como este indicador animado
![Indicador de carga animado](img/cargando.gif) en GIF.

## Cajas de nota, aviso y error

Las cajas son *macros* definidas en la cabecera del material. El texto va
entre comillas invertidas para que pueda contener comas:

@nota(`Las macros se definen una vez en la cabecera y se usan en todo el material.`)

@aviso(`Comprueba la versión de PHP del servidor antes de usar **match**.`)

@error(`Olvidar llamar a **session\_start** antes de leer **$\_SESSION**.`)

## Tablas

| Componente | Sintaxis | Renderiza |
|---|---|---|
| Quiz de opción única | `[(X)] opción` | Botones de radio |
| Quiz de opción múltiple | `[[X]] opción` | Casillas |
| Respuesta corta | `[[respuesta]]` | Campo de texto |
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

## Código ejecutable

El alumnado puede modificar y ejecutar este JavaScript en el navegador:

```js
const notas = [6.5, 8, 4.75, 9]
const media = notas.reduce((a, b) => a + b, 0) / notas.length
console.log(`Media: ${media.toFixed(2)}`)
```
<script>@input</script>

## Animaciones y narración

                                   --{{0}}--
El narrador lee este texto al entrar en la sección (modo presentación).

Los contenidos pueden aparecer paso a paso:

    {{1}}
Primero aparece este párrafo.

{{2}}
********************************************************************
Y después este bloque completo, con su lista:

* paso a paso
* sin saturar la diapositiva
********************************************************************

                                   --{{2}}--
Esta narración acompaña al segundo paso.

## Autoevaluación: opción única

¿Qué símbolo marca la respuesta correcta en un quiz LiaScript?

[( )] El asterisco `*`
[(X)] La equis `X`
[( )] La almohadilla `#`
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

## Autoevaluación: selección en línea

El patrón MVC separa los datos (modelo), la presentación
([[ controlador | (vista) | servicio ]]) y la coordinación (controlador).

## Autoevaluación: matriz

[[Verdadero] (Falso)]
[    (X)       ( )  ]  PHP se ejecuta en el servidor.
[    ( )       (X)  ]  CSS es un lenguaje de programación.
[    (X)       ( )  ]  Git guarda el historial de cambios.

## Autoevaluación con solución

¿Cuántos bits tiene un byte?

[[8]]
[[?]] Es una potencia de dos.
****************************************************************
Un byte tiene **8 bits**, que permiten representar 2^8^ = 256 valores.
****************************************************************

## Encuestas (sin nota)

Las encuestas recogen opiniones; no tienen respuesta correcta.

¿Te resulta útil la autoevaluación en los materiales?

[(1)] Nada
[(2)] Bastante
[(3)] Mucho

¿Qué lenguajes has usado antes?

[[1]] PHP
[[2]] Python
[[3]] JavaScript

¿Qué mejorarías de esta unidad?

[[___]]

## Diagramas en texto plano

```text
┌──────────┐   edita    ┌─────────┐   commit   ┌─────┐
│ Profesor │ ─────────▶ │ Editor  │ ─────────▶ │ Git │
└──────────┘            └─────────┘            └─────┘
```

## Multimedia

Las imágenes se insertan con `![pie](ruta.jpg)`, los vídeos de YouTube
con `!?[título](url-del-vídeo)` y el audio con `?[título](url-del-audio)`.

> **Consejo:** todo lo de esta página es Markdown normal con algunas
> extensiones. Si sabes Markdown, ya sabes el 90 % de LiaScript.
