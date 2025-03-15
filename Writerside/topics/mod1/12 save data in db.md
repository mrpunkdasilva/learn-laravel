# Salvando dados no Database
- No Laravel é comum ter uma action específica para o POST chamada de **store**;
- Lá vamos criar o objeto e compor ele com base nos dados enviados pelo **POST**;
- Com o objeo formado utilizamos o método **save** para **persistir** os dados;

1. Deve-se criar a rota que vai receber os dados, o controller e o método para lidar os dados (sendo a `store`):

```php
Route::post('/events', [EventController::class, 'store']);
```

2. Criar o `form` ara enviar os dados:

```html
<form action="/events" method="POST">
  @csrf
  <div class="form-group">
    <label for="title">Evento:</label>
    <input 
      type="text" 
      class="form-control" 
      id="title" 
      name="title"
      placeholder="Nome do evento" 
    />
  </div>

  <div class="form-group">
    <label for="title">Local do evento:</label>
    <input 
      type="text" 
      class="form-control" 
      id="city" 
      name="city" 
      placeholder="Local do evento" 
    />
  </div>

  <div class="form-group">
    <label for="title">O evento é privado?</label>
    <select name="private" id="private" class="form-control">
      <option value="0">Não</option>
      <option value="1">Sim</option>
    </select>
  </div>

  <div class="form-group">
    <label for="title">Descrição:</label>
    <textarea 
      name="description" 
      id="description" 
      cols="30" 
      rows="10"
      class="form-control" 
      placeholder="O que vai acontecer no evento?" 
    ></textarea>
  </div>

  <button class="btn btn-primary">
    Criar Evento
  </button>
</form>
```

>  Deve ter a diretiva `@csrf` para que o Laravel possa enviar os dados. Já que ela é uma diretiva do Laravel para tratar ataques ao formulario.

