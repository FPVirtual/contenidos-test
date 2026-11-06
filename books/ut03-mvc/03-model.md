# El modelo

El modelo encapsula el acceso a datos. En PHP usaremos **PDO**:

```php
<?php
class Usuario
{
    public function __construct(private PDO $db) {}

    public function find(int $id): ?array
    {
        $stmt = $this->db->prepare('SELECT * FROM usuarios WHERE id = :id');
        $stmt->execute(['id' => $id]);
        return $stmt->fetch(PDO::FETCH_ASSOC) ?: null;
    }
}
```

:::tip
Usa siempre **sentencias preparadas**: evitan inyección SQL.
:::

El modelo no sabe nada de HTML: eso es trabajo de [la vista](04-view.md).
