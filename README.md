# Laravel Users Online


## Laravel compatibility

 Laravel      | Package
:-------------|:----------
  5.3.x        | 2.0.x
  5.2.x        | 1.0.x

## Instalation

Add the new required package in your composer.json

```
"highideas/laravel-users-online": "^2.0"
```
Run `composer update` or `php composer.phar update`.

Or install directly via composer

```
composer require highideas/laravel-users-online
```

After composer command, add new service provider in `config/app.php` :

```php
HighIdeas\UsersOnline\UsersOnlineServiceProvider::class,
HighIdeas\UsersOnline\Providers\UsersOnlineEventServiceProvider::class,
```

And add new middleware in `app/Http/Kernel.php` :

```php
\HighIdeas\UsersOnline\Middleware\UsersOnline::class,
```

After this, add the trait in your model User in `app/User.php`:

```php

class User extends Authenticatable
{
    use \HighIdeas\UsersOnline\Traits\UsersOnlineTrait;
...

```

For show the users online just use the method `isOnline()`:

```php

$user->isOnline();

// Or

$users = User::all();

foreach ($users as $user) {

    if ($user->isOnline()) {
        // show the user
    }
}

```


Finally run `php artisan vendor:publish` for add the namespaces

