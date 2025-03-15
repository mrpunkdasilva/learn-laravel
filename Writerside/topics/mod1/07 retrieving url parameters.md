# Recuperando paramêtros da URL (Rescuing Parameters)

- Podemos mudar como as views tem uma response adicionando parametros a uma rota;
- Ao definir parametros devemos colocar o pârametro dentro de chaves e seu respectivo nome: `{id}`;
- Pode-se ter também pârametros opcionais usando o ponto de interrogação (?);
- O Laravel também aceita `Query Parameters` (Algo como: Pârametros de Consulta), utilizando a sintaxe: `?nome=Gustav&idade=17`;


## Recuperando pârametros definidos nas routes

### Definir que uma rota deve esperar um pârametro:
```php
[routes/web.php]

// -> onde `parameter` é o parametro que está sendo esperado para aquela route
// -> para passar esse parametro vindo da URL deve ser passado um array com o nome do parametro e o seu valor
Route::get('/products/{parameter}', function ($id) {
  return view('product', ['id' => $id]);
});
```

### Parâmetro opcional
+ Para criar parametros opcionais deve-se fazer:
  - definir na rota que o pârametro é opcional, adicionando na frente do mesmo o sinal de interogação (?)
    `/products_test/{id?}`
  - passar um pârametro (recomendavel que seja de mesmo nome que o pârametro da URL) no callback
    `function ($id = 1) {`
      + no callback é feito uma definição de um valor default (padrão) para um pârametro
      + sendo assim, caso não seja passado nenhum parametro, o Laravel não vai reclamar 
      + se for passado nenhum valor ou mesmo nenhum pârametro

```php
Route::get('/products_test/{id?}', function ($id = null) {
  return view('products', ['id' => $id]);
});
```


## Recuperando parâmetros com request (sem a necessidade de definir um parametro a ser esperado em uma route)

### Definir qual será a request (requisição) a ser usada

```php
Route::get('/products', function () {
  // -> nome da requisição a ter seu valor armazenado na variavel busca
  $busca = request('search');

  // -> passando o valor da requisição para a view
  return view('products', ['busca' => $busca]);
});
```

