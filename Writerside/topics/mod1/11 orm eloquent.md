# Usando o ORM do Laravel
- Eloquent é a **ORM** do Laravel
- Cada tabela tem um **Model** que sendo responsavel pelas requisições ao banco
- A convenção para o Model é utilizar o nome da **Entidade** no singular enquanto que a tabela é a entidade no plural:
  - **exemplo:** Model -> Event | Tabela -> Events
- No Model normalmente não se faz muitas alterações dos arquivos, **geralmente para configurações específicas** 

## Usando Eloquent
- Deve-se importar:
  - Sintaxe:
    `use App\Models\Event;`

- Dentro do Controller, chama-se um determinado método do ORM para obter os dados ou setar eles:
  ```php
  # Chamada do método `all()` que vai resgatar todos os registros da tabela (events) do model (event)
  $events = Event::all();
  ```

- Armazenando e passando para uma View os dados retornados pelo Model:
  ```php
  return view('welcome', ['events' => $events]);
  ```

- Renderizando o array de dados passados na View:
  ```php
  @foreach($events as $event)
    <p>
      {{ $event->title }} -- {{ $event->description }}
    </p>
  @endforeach
  ```