<!--

author:   Equipo LiaEditor
title:    Demo — Python ejecutable con la plantilla Pyodide
language: es
version:  1.0.0
comment:  Material de prueba que importa una plantilla LiaScript externa
          (LiaTemplates/Pyodide, versión fijada 0.3.5) para ejecutar
          Python en el navegador. Sirve para probar los imports: al
          exportarlo, liaex necesita descargar la plantilla.

import:   https://raw.githubusercontent.com/LiaTemplates/Pyodide/0.3.5/README.md

-->

# Demo — Python ejecutable con la plantilla Pyodide

Las plantillas añaden macros a LiaScript. Esta importa **Pyodide**, que
ejecuta Python directamente en el navegador del alumnado, sin servidor.

> La plantilla se fija a una versión concreta (`0.3.5`) en el `import:` de
> la cabecera, nunca a `main`/`master`: así el material no cambia si la
> plantilla evoluciona.

## Un programa ejecutable

Basta con añadir la macro `@Pyodide.eval` justo debajo del bloque de
código:

```python
nombres = ["Ana", "Luis", "Marta"]
for n in sorted(nombres):
    print(f"Hola, {n}")
```
@Pyodide.eval

## Cálculo con la biblioteca estándar

```python
import statistics

notas = [6.5, 8, 4.75, 9, 7]
print("Media:", statistics.mean(notas))
print("Mediana:", statistics.median(notas))
```
@Pyodide.eval

## Autoevaluación

¿Qué escribe `print(sorted([3, 1, 2]))`?

[( )] `[3, 1, 2]`
[(X)] `[1, 2, 3]`
[( )] `[3, 2, 1]`
[[?]] `sorted` ordena de menor a mayor por defecto.
