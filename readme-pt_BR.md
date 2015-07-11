#Junção dos middleware needsPermission e needsRoles do pacote artesaos/defender

[Readme on English](https://github.com/resultsystems/needsroleorpermission/blob/master/readme.md).

[artesaos/defender](https://github.com/artesaos/defender).

## Instalação

### 1. Dependência

Usando o <a href="https://getcomposer.org/" target="_blank">composer</a>, execute o comando a seguir para instalar automaticamente `composer.json`:

```shell
composer require resultsystems/needsroleorpermission
```

ou manualmente no seu arquivo `composer.json`

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
