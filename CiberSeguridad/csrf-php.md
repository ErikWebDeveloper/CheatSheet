# Ejemplo práctico par implementar CSRF en PHP:

- Generar el token CSRF y guardarlo en la sesión del usuario:

`formulario.php`

 ```php
<?php
session_start();

// Generar un token CSRF único
$token = bin2hex(random_bytes(32));

// Guardar el token en la sesión del usuario
$_SESSION['csrf_token'] = $token;
?>

<!-- Incluir el token en el formulario -->
<form action="procesar_formulario.php" method="post">
    <!-- Otros campos del formulario -->
    <input type="hidden" name="csrf_token" value="<?php echo $token; ?>">
    <button type="submit">Enviar</button>
</form>
 ```

- Validar el token CSRF en el script que procesa el formulario:

`procesar_formulario.php`

```php
<?php
session_start();

// Comprobar si el token CSRF enviado coincide con el token almacenado en la sesión
if ($_SERVER['REQUEST_METHOD'] === 'POST' && isset($_POST['csrf_token']) && isset($_SESSION['csrf_token']) && $_POST['csrf_token'] === $_SESSION['csrf_token']) {
    // El token CSRF es válido, procesar el formulario
    // Aquí puedes realizar las acciones necesarias
    // ...
    // Después de procesar el formulario, elimina el token CSRF para que no pueda ser utilizado nuevamente
    unset($_SESSION['csrf_token']);
} else {
    // El token CSRF no coincide o no está presente, considerar la solicitud como potencialmente maliciosa
    // Puedes redirigir a una página de error o simplemente ignorar la solicitud
    // ...
}
?>
``
