# 09 - Infraestrutura como Código

O objetivo é subir uma infraestrutura definida em um **compose file** com uma aplicação em Perl e um contêiner do Redis. A aplicação pode ser acessada pelo navegador, sendo assim, exponha uma porta que achar conveniente.

## O que essa aplicação faz?

Quando a aplicação inicia ela se conecta ao Redis gravando em seu cache uma página HTML, exibindo-a logo em seguida. Os acessos subsequentes leêm deste cache e exibem a página.

Dentro da aplicação há uma simples API capaz de modificar a página no cache, e pode ser ativada da seguinte forma:

```bash
curl -X POST -H 'Content-Type: application/json' -d '{"html" : "<div id=\"getting-started\"><h1>Atualizado via API REST!</h1><h2>Estes valores foram gravados no Redis</h2><ol><li><h2>HTML Cache</h2><p>É claro que esta pequena página não justifica a utilização do Redis, mas ao menos demonstra a integração entre duas aplicações.</p></li>"}' 172.17.0.2/update
```

Antes de criar o nosso `compose file` será preciso construir a imagem da aplicação.

## A Aplicação

Dancer é um framework em Perl para criar aplicações web bastante utilizado para APIs Rest.

A construção desta imagem é relativamente demorada pois centenas de testes são executados durante a instalação, sendo assim, utilize as camadas que achar necessário e preste atenção para evitar builds indesejadas.

Esta aplicação se conecta a um servidor redis para gravar uma página HTML que pode ser modificada através de um POST em sua API.

Utilizar o código da aplicação em https://github.com/4linux/4542-perl para construir uma imagem chamada **dancer**.

- Basear a imagem em **debian:buster-slim**
- Esta aplicação depende de um servidor **redis**, a comunicação é ditada pelas variáveis da aplicação, não é necessário usar senha.
- Instalar os pacotes `perl cpanminus make gcc`
- O comando para instalar as dependências do **perl** é `cpanm --installdeps /diretorio/aplicacao`
- O comando do contêiner deverá ser `plackup /diretorio/aplicacao/bin/app.psgi`
- Por padrão, a aplicação escuta na porta 5000

> **Observação:** Substituir `/diretorio/aplicacao` pelo caminho que achar mais conveniente. Prestar atenção na documentação da própria aplicação em seu GitHub.
