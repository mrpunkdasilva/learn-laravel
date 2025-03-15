# Controllers 

+ Os **Controllers** são parte fundamentais de uma aplicação em Laravel;
+ Sendo eles geralmente condensam a maior parte da lógicada;
+ Tem o papel de enviar e esperar respostas (reponses) para as **Views**;
+ Os **Controllers** podem ser criados via terminal, ou seja, usando o Artisan;
+ É comum retornar uma View ou redirecionar para uma **URL** pelo Controller;
+ Todo Controller é uma classe, que por sua vez possuí atributo, sendo eles nomeados de actions
	+ essas actions são todas as ações que o controller pode fazer, 
	+ entenda que o Controller é a personificação de uma entendida (model)
	+ ou seja, nele que contará a forma como cada Rota, View, Model será gerenciado 
	**! é uma conveção chamar a primeira action de um Controller de: index**

### Criar Controller com Artisan

- Para tal, deve-se executar no terminal estando na pasta raiz do projeto o comando:

	`php artisan make:controller EventController`

	**! o nome do controller deve ser no singular e deve colocar no final a palavra 'Controller'**
		- exemplo: `EventController`

- O Artisan criara um arquivo com o nome que você deu ao controller com uma estrura básica:
```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;

class EventController extends Controller
{

  // actions

}
```

### Usando o Controller

- Para usar esse controller já criado, devemos importa-lo no arquivo nas Routes 

- Sendo assim deve se importar o mesmo usando, assim será carregado o namesspace do controller: 
```php 
	[routes/web.api]

	use App\Http\Controllers\EventController
```

- Após isso devemos usar ele de fato, para isso a algumas formas como passar um **array**
- com o **controller** (Controller:class) desejado e sua **action** ('index') a ser usada;

**Exemplo:*
```php
[routes/web.api]

use App\Http\Controllers\EventController;
								 # controller            # action
Route::get('/', [EventController::class, 'index']);
```

