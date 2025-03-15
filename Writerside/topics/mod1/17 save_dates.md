# Salvando Datas
- Para salvar datas no Laravel é muito fácil, precisamos criar um input do tipo `date` na view
```html
<div class="form-group">
  <label for="title">Data do Evento:</label>
  <input 
    type="date" 
    class="form-control" 
    id="date" 
    name="date"
  />
</div>
``` 

- Um campo de dateTime deve ser criado, criando via Migration:
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
        Schema::table('events', function (Blueprint $table) {
            $table->dateTime('date_event');
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::table('events', function (Blueprint $table) {
            $table->dropColumn('date_event');
        });
    }
};
```

- E processar o envio dos dados via Controller pelo request de POST:
```php
use App\Models\Event;

class EventController extends Controller {
	public function store(Request $request) {
	  $event = new Event;

	  $event->date = $request->date;
	}
}
```

- Definir para o Eloquent quais campos são datas
```php
protected $dates = [ 'date' ];
```

- Exibir no formato correto a data na View:
```html 
<p class="card-date">{{ date('d/m/Y', strtotime($event->date)) }}</p>
```


