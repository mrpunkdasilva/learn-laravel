# Layouts com Blade

- Com layouts pode-se ter mais reaproveitamento de código o que gera mais performance em produção e manutenção 

- Por exemplo podemos utilizar o mesmo **header** e **footer** em todas as páginas da nossa aplicação

- Para isso deve se criar primeiro a pasta `layouts` dentro da folder views
  
- Em seguida criar o arquivo que conterá o layout

### Colocar conteudos dentro de layouts

- Primeiro devemos colocar a diretiva `yield` no lugar em que queremos colocar algum conteudo, ou seja, essa diretiva vai servir como um replace para algum contéudo

- Definir na view de qual layout você está extendendo (entenda como herdando), usando a diretiva:
  
    `@extends('layouts.main')`

- Definir qual secção será mudada, ou seja, qual campo definido no `yield` será trocado 
  - Para casos em que só precise inserir um unico valor:
        `@section('content', 'Value from content)`
  - Casos em que precise exibir mais de um valor, colocar um trecho de HTML por exemplo, deve-se usar:
    ```php
    @section('content')
    <h2>Conteudo da section a ser alterado</h2>
    @endsection
    ```
