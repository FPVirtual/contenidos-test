# El controlador

El controlador conecta la petición con el modelo y la vista:

```php
<?php
class PerfilController
{
    public function __construct(private Usuario $usuarios) {}

    public function show(int $id): void
    {
        $usuario = $this->usuarios->find($id);
        if ($usuario === null) {
            http_response_code(404);
            return;
        }
        require __DIR__ . '/../views/perfil.php';
    }
}
```

## Resumen de la unidad

- El **modelo** gestiona los datos ([capítulo 3](03-model.md)).
- La **vista** presenta ([capítulo 4](04-view.md)).
- El **controlador** coordina.

:::note
Vuelve a la [introducción](01-introduccion.md#qué-aprenderás) y repasa los
objetivos antes de hacer la tarea de la unidad.
:::
