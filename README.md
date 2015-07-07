#Merge needsPermission and needsRoles artesaos/defender

[Readme em Português](https://github.com/resultsystems/needsroleorpermission/blob/master/README-pt_BR.md).

[artesaos/defender](https://github.com/artesaos/defender).

## Installation

### 1. Dependency

Using <a href="https://getcomposer.org/" target="_blank">composer</a>, execute the following command to automatically update your `composer.json`:

```shell
composer require resultsystems/needsroleorpermission
```

or manually update your `composer.json` file

```json
{
	"require": {
		"resultsystems/needsroleorpermission": "1.0.*"
	}
}
```

### 2. Middlewares
To use them, just put it in your `app/Http/Kernel.php` file.

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
    return 'Yes I can!';
}]);
```
