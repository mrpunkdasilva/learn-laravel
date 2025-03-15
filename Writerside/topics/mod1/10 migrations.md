# Migrations

- As **Migrations** funcionam como um versionamento de banco de dados;
- Podemos **avançar e retroceder** a qualquer momento;
- **Adicionar colunas e remover** de forma mais facilitada;
- Fazer o setup da base de dados de uma nova instalação em apenas um comando;
- Podemos verificar as migrations com **migrate:status**;


### Criar uma migration

- Para criar deve-se usar o Artisan, executando o comando:
	`php artisan make:migration create_product_table`

- Ao fazer isso, criara uma estrutura básica para a Migration:
```php
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::create('product', function (Blueprint $table) {
            $table->id();
            $table->timestamps();
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::dropIfExists('product');
    }
};

```

- O método `up` irá avançar a migration

- O método `down` vai voltar a migration


## Comando fresh
- Com o uso do comando fresh da migrate é possivel deletar todas as migrations e 
- em seguida cria-las de novo, uma especie de refresh
- Comando:
    `php artisan migrate:fresh`


## Indo Além 

- ! Quando precisamos adicionar um novo campo na tabela **devemos criar uma nova** migration !
- Pórem devemos tomar cuidado para não rodar o comando `fresh` e apagar os dados já existentes
- Para voltar alguma migration devemos utilizar o comando `rollback`
    - sintaxe:
        `php artisan migrate:rollback`
-Para voltar todas as migrations podemos utilizar o comando `reset`
    - sintaxe:
        `php artisan migrate:reset`
- Pode-se usar `refresh` para voltar todas e rodar novamente
    - sintaxe:
        `php artisan migrate:refresh`

### Adicionar coluna em uma tabela:

- Para fazer isso use o comando abaixo:
    `php artisan make:migration add_category_to_products_table`
- Obs: 
    + Ao se criar uma migration para fazer isso deve se ter: `add_nomeColuna_to_nomeTabela_table`
    + Ao se adionar um novo campo a tabela é criada uma estrutura diferente da `create` pois agora se estara usando a Schema

- Dentro do arquivo criado, escreva dentro da Schema de `up` adicione o que irá acontecer quando a migration rodar
  - ou seja, criar um novo campo `$table->string('category', 100);`:
- Assim como também adicionara dentro da Schmea de `down` adicione o que irá acontecer quando a migration voltar
  - ou seja, adicione `$table->dropColumn('category');`  
<br>

`[codigo de exemplo]`
```php
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::table('products', function (Blueprint $table) {
          $table->string('category', 100);
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::table('products', function (Blueprint $table) {
          $table->dropColumn('category');
        });
    }
};
```

