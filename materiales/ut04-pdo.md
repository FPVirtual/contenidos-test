<!--

author:   Equipo DWES
title:    UT04 — Introducción a la capa de acceso a datos
language: es
version:  0.1.0
comment:  Borrador de material LiaScript para pruebas de edición y conflicto.

-->

# UT04 — Introducción a la capa de acceso a datos

Segundo material de prueba (pensado para ensayar conflictos de edición
entre dos profesores).

## PDO en una frase

**PDO** es la interfaz estándar de PHP para acceder a bases de datos de
forma uniforme, con sentencias preparadas contra la inyección SQL.

```php
<?php
$pdo = new PDO('mysql:host=db;dbname=app', 'user', 'pass');
$stmt = $pdo->prepare('SELECT * FROM usuarios WHERE id = :id');
$stmt->execute(['id' => $id]);
$usuario = $stmt->fetch(PDO::FETCH_ASSOC);
```

## Ideas clave

- Siempre **sentencias preparadas**, nunca concatenar datos en el SQL.
- Configura `PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION`.
- Un único punto de conexión compartido (patrón *singleton* sencillo o
  contenedor de dependencias).

## Mini-reto

Escribe una función `buscar_usuario(PDO $pdo, int $id): ?array` usando el
código anterior como guía.
