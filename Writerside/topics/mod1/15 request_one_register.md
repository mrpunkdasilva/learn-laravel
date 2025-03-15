# Resgatando um registro
Para isso pode usar o método `findOrFail`, fazendo o resgate pelo Eloquent.

```php
public function show($id) {
  $event = Event::findOrFail($id);

  return view('events.show', ['events' => $event]);
}
```
