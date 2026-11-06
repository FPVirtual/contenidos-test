# El patrón MVC

MVC divide la aplicación en tres componentes:

| Componente | Responsabilidad | Ejemplo en PHP |
|------------|-----------------|----------------|
| Modelo | Datos y lógica de negocio | `Usuario::find(1)` |
| Vista | Presentación (HTML) | `perfil.php` |
| Controlador | Coordina petición y respuesta | `PerfilController` |

:::important
El controlador **nunca** contiene SQL; el modelo **nunca** imprime HTML.
:::

## Flujo de una petición

1. El navegador pide `/perfil/1`.
2. El **controlador** recibe la petición y pide datos al **modelo**.
3. El **modelo** devuelve el `Usuario`.
4. El controlador se lo pasa a la **vista**, que genera el HTML.

En el siguiente capítulo empezamos por [el modelo](03-model.md).
