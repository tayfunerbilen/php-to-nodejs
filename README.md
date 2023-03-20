# PHP'den NodeJS'e Geçiş

Bildiğiniz gibi yıllardır PROTOTURK youtube kanalında PHP programlama dili ile ilgili içerikler ürettim. Birazda NodeJS içerikleri üretmek istediğim için ve kanalın neredeyse tamamı PHP geliştirdiği için PHP'den NodeJS'e soft bir geçiş için bir rehber hazırlamak istiyorum.

Aynı zamanda zaten bu işlemi videolu olarak yapıyoruz, burada da yazılı kalsın.

## Gereksinimler

Bu rehber sizin PHP'yi zaten bildiğinizi ve temel JavaScript'e hakim olduğunuzu kabul eder. O yüzden değişkenler, fonksiyonlar, döngüler, diziler, nesneler gibi kavramları ele almadan NodeJS ve Express ile web uygulamaları geliştirmeye odaklanır.

Ancak elbette bazı durumlarda PHP'de nasıldı, NodeJS'de nasıl gibi sorulara cevap vereceğimiz bölümler olacak.

## Hello World!

### PHP

PHP'de bir işleme başlamak istediğinizde `.php` uzantılı bir dosya açıp `echo` ile bir çıktı verebiliyorsunuz. ,

```php
<?php

echo "Hello, world!";
```

### NodeJS

NodeJS'de ise önce bir proje initialize etmeniz gerekiyor. Bunun için ilk olarak şu komutu çalıştırıyorsunuz:

```shell
npm init -y
```

> bu bize bir `package.json` dosyası oluşturuyor. NPM node'un paket yöneticisi, PHP'deki composer gibi düşünebilirsiniz. `package.json` ise php'deki `composer.json` gibi düşünebilirsiniz.

Daha sonra bir `app.js` dosyası oluşturup şu kodları yazın:

```js
console.log('Hello, world!')
```

Ve çalıştırıp test edin:

```shell
node app.js
```

Elbete, PHP'de yazılanı tarayıcıda, NodeJS'de yazılanı konsol'da görüyoruz şu an. O yüzden biraz daha anlamlı örnek verelim.

## Routing Islemleri

### PHP

PHP'de routing işlemleri için bir sürü paket var kullanabileceğimiz. Ama temelde aslında URL'i parse ederek hangi alanda hangi kodun çalıştıracağını söylüyoruz. Örneğin:

```php
Route::get('/', function() {
  return 'anasayfa'
});

Route::get('/iletisim', '\Controllers\Contact');
```

gibi. Tabi bu kod doğrudan çalışmaz ancak PHP developer olarak ne demek istediğimi anladınız bence :D

### NodeJS

NodeJS'de web uygulamarı geliştirilirken en yaygın kullanılan `express` çatısı. Elbette bir sürü alternatifi var ama soft geçişte sanırım en manıtklısı bu. Dolayısı ile routing'ler ile çalışmak için ilk olarak `express` paketini kuralım.

```shell
npm i express
```

Ve daha sonra `app.js` dosyamızı şöyle güncelleyelim.

```js
import express from "express"

const app = express()

app.get('/', (req, res) => {
  res.send('anasayfa')
})

app.get('/iletisim', (req, res) => {
  res.send('iletisim')
})

app.listen(3000, () => console.log('Uygulama 3000 portundan dinleniyor'))
```

Ve bunu çalıştıralım.

```shell
node app.js
```

Artık `http://localhost:3000` ve `http://localhost:3000/iletisim` adreslerinden yazdığınız kodları görebilirsiniz.
