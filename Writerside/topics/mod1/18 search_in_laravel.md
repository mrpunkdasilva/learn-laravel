# Busca no Laravel
- Para criar uma busca no Laravel é muito simples, vamos utilizar o **Eloquent**;

- O método **where** os registros que precisamos, fazendo um filtro e nos enviando para uma View:
```php
<?php

namespace App\Http\Controllers;
use Illuminate\Http\Request;

// Model
use App\Models\Event;

class EventController extends Controller
{

  public function index() {
    $search = request('search');

    if ($search) {
      $events = Event::where([
        [
          'title', 
          'like', 
          '%'.$search.'%'
        ]
      ])->get();
    } 

    $events = Event::all();

    return view('welcome', [
      'events' => $events, 
      'search' => $search
    ]);
  }
}
``` 

- Podemos fazer a exibição da busca na view Home, mudando o layout com **diretivas do Blade**;  
```html
@extends('layouts.main')

@section('title', 'EventForYou')

@section('content')
<div id="search-container" class="col-md-12">
    <h1>Busque um evento</h1>
    <form action="" method="GET">
        <input 
            type="text" 
            id="search" 
            name="search" 
            class="form-control" 
            placeholder="Procurar..." 
        />
    </form>
</div>

<div id="events-container" class="col-md-12">
  @if ($search)
    <h2>
        Buscando por: {{ $search }}
    </h2>
  @else
    <h2>
      Próximos Eventos
    </h2>
    <p class="subtitle">
      Veja os eventos dos proximos dias
    </p>
  @endif

  <p class="subtitle">Veja os eventos dos próximos dias</p>

  <div id="cards-container" class="row">
    @foreach($events as $event)
    <div class="card col-md-3">
      <img src="/images/events/{{ $event->image }}" alt="{{ $event->title }}">

      <div class="card-body">
        <p class="card-date">{{ date('d/m/Y', strtotime($event->date)) }}</p>
        <h5 class="card-title">{{ $event->title }}</h5>
        <p class="card-participants">X Participantes</p>
        <a href="/events/{{ $event->id }}" class="btn btn-primary">Saber mais</a>
      </div>
    </div>
    @endforeach

    @if (count($events) == 0 && $search)
      <p>
        Não foi possivel encontrar nenhum evento com {{ $search }}
        <a href="/">Ver todos os eventoss</a>
      </p>
    @elseif (count($events) == 0)
      <p>Não há eventos ainda</p>
    @endif
  </div>
</div>
@endsection	
``` 

