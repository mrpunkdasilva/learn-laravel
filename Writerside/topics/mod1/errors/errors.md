# Erros que vão acontecer um dia e suas possiveis soluções

## Deu erro HTTP 500
Caso acontecer, faça isso:

+ `copy .env.example .env`

+ `php artisan key:generate` 

+ `php artisan serve`


## `SerializableClosure` error in Laravel - Your serialized closure might have been modified and it's unsafe to be unserialized

+ `php artisan route:clear`

+ `php artisan cache:clear`

+ `php artisan config:clear`

+ `php artisan view:clear`

+ `php artisan key:g  enerate`

+  `composer update`