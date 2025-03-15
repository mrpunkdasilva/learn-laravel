# Routes e Views

### Rotas

+ Irá definir onde vamos acessar as páginas do projeto;
+ As Rotas vão chamar Views, que por sua vez são  as representações gráficas das páginas;
+ Obs:
    + Não é obrigatorio a rota ter o mesmo nome da view;
    + Rotas podem exibir a mesma view;

**Para criar uma rota:**

```php
/*
* O metodo get deve conter a rota (o diretorio de navegação da url e retornar uma view, ou seja, um template)
* Route::get('/route', view);
*/
Route::get('/route', function () {
    return view('nameView');
});
```

**Passar valores de uma rota para uma View**

```php
Route::get('/', function () {
  $nome = 'Gustavo';

  # -> O segundo argumento, da função view, é um array com os valores, que serão passados para a View
  # ¬ e assim eles poderão ser utilizados.
  # -> Basta apenas, instanciar essas variaveis dentro da view, por exemplo dentro de uma view use:
  #   <p>{{ $nome }}</p>
  # obs: podem ser passados diversos dados de diversos em seus varios tipos, no Blade não há essa limitação de tipagem
  return view('welcome', ['nome' => $nome]);
});
```
### Views

+ Nas views teremos os templates, onde há a estruturação por meio do HTML, usando a template engine: Blade;
+ Os templates também renderizam dados dinâmicos por meio do PHP;

**Para criar views, deve ir em:**

<pre>
myapp
  |
  |__ resources
         |
         |__ views
</pre>

Depois deve se criar um arquivo com: `nomeDaView.blade.php`.
  - Sempre deve ter o `.blade.php` seguido depois do nome da sua view;

