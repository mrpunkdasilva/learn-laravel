# Upload de Imagens
Salvar imagens no Laravel requer mudar o enctype do formulário e também criar um input de envio de imagens:
```html
<form action="/upload" method="POST" enctype="multipart/form-data">
    @csrf

    <label for="image">Escolha uma imagem:</label>
    <input type="file" name="image" id="image">

    <button type="submit">Enviar</button>
</form>
```

No Controller vamos fazer um tratamento de verificação da imagem que foi enviada. E depois vamos salvar ela com um nome único em um diretório do projeto. No banco salvamos apenas o path para a imagem:
```php 
if ($request->hasFile('image') && $requst->file('image')->isValid()) {
  // pega a imagem vinda da requisição
  $requestImage      = $request->image();

  // pega a extensão 
  $extension         = ".".$requstImage->extension();
  $originalNameImage = $requestImage->getClientOriginalName();
  $dateNow           = strtotime("now");
  $newImageName      = md5($originalNameImage.$dateNow.$extension);

  // lugar onde a imagem será savla, caso não exista a pasta será criada
  $request->image->move(public_path('images/events'), $newImageName);

  // passando a imagem para a requisição
  $event->image = $newImageName;
}
```