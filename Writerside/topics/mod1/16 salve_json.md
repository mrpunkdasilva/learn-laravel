# Salvando JSON

Precisamos salvar um conjunto de dados em um banco para itens de múltipla escolha. 
Vamos criar um campo determinado de JSON via migrações. No front-end, devemos utilizar inputs com checkboxes. 
Após enviá-los para o controller, receberemos apenas os itens do request e o restante do processo é igual aos outros dados do nosso modelo.

- Criar HTML que vai cnter a lista cm os items:
```html
<div class="form-group">
  <label for="title">Adicine itens de infraestrutura:</label>
  <div class="form-group">
    <input 
      type="checkbox" 
      name="items[]" <!-- indica que vai ser um array chamado items --> 
      value="cadeiras" 
    />
    Cadeiras
  </div>
  <div class="form-group">
    <input 
      type="checkbox" 
      name="items[]" 
      value="palco" 
    />
    Palco
  </div>
  <div class="form-group">
    <input 
      type="checkbox" 
      name="items[]" 
      value="Open foods" 
    />
    Cerveja Gratis
  </div>
  <div class="form-group">
    <input 
      type="checkbox" 
      name="items[]" 
      value="Brindse" 
    />
    Brindes
  </div>
</div>
``` 

- Definir que no Controller que recebe a requisição o atributo será usado pelo Model:
```php
use App\Models\Event;
$event = new Event;

$event->items = $request->items;
```

- Fazer o casting de dados usando o Eloquent:
```php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class Event extends Model
{
    use HasFactory;
    //+> Com isso o Eloquent fara o casting de dados 
    protected $casts = [
        //item  => "tipo" 
        "items" => "array"
    ];
}
```
