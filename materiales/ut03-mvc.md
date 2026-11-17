<!--

author:   Equipo DWES
title:    UT03 — El patrón MVC en PHP
language: es
version:  1.0.0
comment:  Material de ejemplo LiaScript para el flujo LiaEditor–Moodle.

-->

# UT03 — El patrón MVC en PHP

Material de prueba del flujo LiaEditor–Moodle. Este fichero se edita desde
Moodle con el LiveEditor self-hosted y se guarda en Git.

## ¿Qué es MVC?

El patrón **Modelo–Vista–Controlador** separa la aplicación en tres capas:

1. **Modelo**: datos y lógica de negocio.
2. **Vista**: presentación (HTML).
3. **Controlador**: coordina peticiones entre Vista y Modelo.

```php
<?php
// Controlador mínimo
$usuarios = Usuario::todos($pdo);   // Modelo
require __DIR__ . '/vistas/listado.php';  // Vista
```

## Ejemplo: ciclo de una petición

    Usuario → Router → Controlador → Modelo → Vista → Respuesta HTML

El navegador pide `/usuarios`, el controlador consulta el modelo y la vista
renderiza el resultado.

## Comprueba lo aprendido

¿Qué capa debe contener la consulta SQL?

    [[Vista]]
    [[Controlador]]
    [[Modelo|X]]

¿Verdadero o falso? La Vista puede llamar directamente a la base de datos.

    [[Verdadero]]
    [[Falso|X]]

## Para saber más

- Documentación de LiaScript: https://liascript.github.io/
