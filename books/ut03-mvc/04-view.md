# La vista

La vista genera el HTML que ve el usuario. Recibe datos del controlador y
solo los **muestra**:

```php
<?php
/** @var array $usuario */
?>
<h1>Perfil de <?= htmlspecialchars($usuario['nombre']) ?></h1>
<p>Email: <?= htmlspecialchars($usuario['email']) ?></p>
```

:::warning
Escapa siempre la salida con `htmlspecialchars()` para prevenir XSS.
:::

La vista no consulta la base de datos: los datos llegan desde
[el controlador](05-controller.md).
