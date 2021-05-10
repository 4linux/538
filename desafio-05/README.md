# 05 - Volumes

Nosso objetivo é desenvolver um simples script em PHP e rodá-lo utilizando contêineres:

- Crie um diretório chamado `php`;
- Dentro do diretório crie um arquivo chamado `index.php` com o conteúdo mostrado ao final desta lista;
- Monte o volume dentro de um contêiner baseado em `php:alpine` chamado `php-app`, o volume pode estar em qualquer diretório;
- Rode o contêiner desatachado fornecendo o comando `php -S 0.0.0.0:8080 -t </caminho/do/diretorio>` durante o `docker container run`;
- Procure pelo IP do contêiner com `docker container inspect`;
- Acesse a página com `curl <enderecoip>:8080` 

```php
<?php

for($i = 0; $i < 10; $i++)
  echo "$i<br />\n";
```

A saída deverá ser a seguinte:

```
0<br />
1<br />
2<br />
3<br />
4<br />
5<br />
6<br />
7<br />
8<br />
9<br />
```
