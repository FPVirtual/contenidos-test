<!--

author:   Equipo DWES
title:    UT03 — El patrón MVC en PHP
language: es
version:  2.0.0
comment:  Unidad de ejemplo del sistema Materiales Editables. Cubre el
          patrón Modelo-Vista-Controlador con ejemplos en PHP y
          autoevaluación LiaScript.

-->

# UT03 — El patrón MVC en PHP

> Al terminar esta unidad serás capaz de explicar las tres capas del patrón
> MVC, trazar el ciclo de vida de una petición y separar correctamente las
> responsabilidades en una aplicación PHP.

## ¿Por qué MVC?

Sin estructura, una aplicación PHP mezcla SQL, HTML y lógica en el mismo
fichero. El patrón **Modelo–Vista–Controlador** propone una separación en
tres capas con responsabilidades claras:

| Capa | Responsabilidad | No debe |
|---|---|---|
| **Modelo** | Datos y reglas de negocio | Generar HTML |
| **Vista** | Presentación al usuario | Consultar la base de datos |
| **Controlador** | Coordinar petición → acción → respuesta | Contener SQL ni HTML |

```text
 Navegador ──petición──▶ Router ──▶ Controlador ──▶ Modelo
                                        │              │
                                        ▼              ▼
                              Respuesta ◀── Vista ◀── datos
```

## Un controlador mínimo

```php
<?php
// Controlador: coordina, no calcula ni dibuja.
declare(strict_types=1);

require_once __DIR__ . '/../src/UsuarioRepository.php';

function listadoUsuarios(PDO $pdo): void {
    $usuarios = UsuarioRepository::todos($pdo);   // ① Modelo
    require __DIR__ . '/../vistas/usuarios/listado.php'; // ② Vista
}
```

1. El controlador pide los datos al modelo.
2. Pasa esos datos a la vista, que solo los presenta.

## La vista: solo presentación

```php
<?php /** @var array $usuarios */ ?>
<h1>Listado de usuarios</h1>
<ul>
  <?php foreach ($usuarios as $u): ?>
    <li><?= htmlspecialchars($u['nombre'], ENT_QUOTES, 'UTF-8') ?></li>
  <?php endforeach; ?>
</ul>
```

Fíjate en dos cosas:

- La vista **no** importa el repositorio ni abre conexiones: recibe
  `$usuarios` ya preparado.
- Todo dato que se imprime pasa por `htmlspecialchars` (prevención XSS).

## El modelo: datos y reglas

```php
<?php
declare(strict_types=1);

final class UsuarioRepository {
    public static function todos(PDO $pdo): array {
        $stmt = $pdo->query(
            'SELECT id, nombre, email FROM usuarios ORDER BY nombre'
        );
        return $stmt->fetchAll(PDO::FETCH_ASSOC);
    }
}
```

## Señales de que la separación se está rompiendo

- Un `echo` dentro del modelo.
- Una consulta SQL en un fichero de vista.
- Un controlador de 300 líneas que "hace de todo".

Si aparece alguna, la responsabilidad está en la capa equivocada.

## Autoevaluación

**1.** ¿En qué capa debe vivir una consulta SQL?

    [[Vista]]
    [[Controlador]]
    [[Modelo|X]]
    [[?]] ¿Quién conoce la estructura de la base de datos?

**2.** Selecciona las afirmaciones correctas:

    [[ ]] La vista puede llamar al modelo directamente si es más rápido.
    [[X]] El controlador coordina modelo y vista sin conocer detalles de SQL.
    [[X]] `htmlspecialchars` pertenece a la capa de presentación.
    [[ ]] El modelo debe devolver HTML ya maquetado.

**3.** Escribe el nombre de la capa que falta: «El ________ decide qué
vista se muestra tras procesar la petición».

    [[controlador]]

## Para practicar

Toma un script tuyo que mezcle SQL y HTML y reescríbelo en tres ficheros
(modelo, vista, controlador). Compara el antes y el después: ¿qué fichero
cambiarías si mañana cambia el diseño? ¿Y si cambia la base de datos?
