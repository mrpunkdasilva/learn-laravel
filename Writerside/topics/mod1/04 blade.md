# Blade

Para começar o Blade é uma **template engine** do Laravel, sendo ela a padrão para o Laravel. Usando ele, as páginas das nossas aplicações se **tornam mais dinâmicas**.

Inserindo dados que provém do Banco e também tags HTML. Ou seja, as Views serão responsabilidade do Blade de se fazer tota a interpretação do template


### Diretivas


**Exibir dados**

- Para tal deve-se, usar ``{{ code.. }}``:

**Sintaxe**

```php
# Com isso o dado que estiver dentro de $nome será retornado e impresso na View
<p>{{ $nome }}</p>
```

<br>

**if-else statement**

**Sintaxe**

- Quando se quer usar a diretiva if do blade deve se usar:

```php
@if (condition)
    <p>Code HTML</p>
@endif
```

- Quando nas operações lógicas é necessario usar mais de uma condição, ou seja, o else:
- 
**Sintaxe**

```php
@if ($nome === 'Pedro')
    <p>O nome é Pedro</p>
@else
    <p>O nome não é Pedro</p>
@endif
```

- Para casos de varias condicionais, em uma mesma verificação lógica usando o elseif:

**Sintaxe**

```php
@if ($nome === 'Pedro')
    <p>O nome é pedro</p>
@elseif ($nome === 'Gustavo')
    <p>O nome é Gustavo</p>
@else
    <p>Não sei que nome é</p>
@endif
```

<br>

**Loop**

Podemos criar **estruturas de controle** (loops ou mesmo laços de repetição) no Blade;

Assim como também é possivel executar codigo **PHP Puro**, possui uma alta versatilidade e permite chegar em um resultado excelente;

- for-statement

**Sintaxe**

```php
@for ($i = 0; $i < count($arr); $i++)
    @if ($i > 2)
    <p>
        {{ $arr[$i] }} - {{ $i }}
    </p>
    @endif
@endfor
```

- foreach-statement

**Sintaxe**

```php
@foreach ($nomes as $nome)
    <p>
        {{ $nome }}
    </p>
@endforeach
```

Para saber o `index` do item do array (collection) use, `$loop->index`:
```php
@foreach ($nomes as $nome)
    <p>
    {{ $loop->index }} - {{ $nome }}
    </p>
@endforeach
```

<br>

**Exibir código PHP puro**

Os códigos que venham a ser de PHP puramente devem ser colocados entre a diretiva `@php`

```php
@php
    $name = 'Punk Junior Silveira';
    echo $name;
@endphp
```