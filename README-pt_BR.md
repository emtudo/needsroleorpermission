#Junção dos middleware needsPermission e needsRoles do pacote artesaos/defender

[Readme on English](https://github.com/resultsystems/needsroleorpermission/blob/master/README.md).

[artesaos/defender](https://github.com/artesaos/defender).

## Instalação

### 1. Dependência

Using <a href="https://getcomposer.org/" target="_blank">composer</a>, execute the following command to automatically update your `composer.json`:

```shell
composer require resultsystems/needsroleorpermission
```

ou manualmente pelo no seu arquivo `composer.json`

```json
{
	"require": {
		"resultsystems/needsroleorpermission": "1.0.*"
	}
}
```

### 2. Middlewares
Para utilizá-los é necessário registrá-los no seu arquivo app/Http/Kernel.php.

```php
protected $routeMiddleware = [
    'auth'            => 'App\Http\Middleware\Authenticate',
    'auth.basic'      => 'Illuminate\Auth\Middleware\AuthenticateWithBasicAuth',
    'guest'           => 'App\Http\Middleware\RedirectIfAuthenticated',

    // Controle de acesso usando permissões e grupos
    'needsRoleOrPermission' => 'ResultSystems\NeedsRoleOrPermission\Http\Middleware\NeedsRoleOrPermission',
];
Route::get('foo', ['middleware' => ['auth', 'needsRoleOrPermission'], 'can' => ['user.index', 'user.create'], 'is' => 'admin', function()
{
    return 'Sim eu posso!';
}]);
```
