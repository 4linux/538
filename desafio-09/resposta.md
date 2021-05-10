# 09 - Resposta

Primeiro, vamos clonar a aplicação e entrar no diretório:

```bash
git clone https://github.com/4linux/4542-perl.git
cd 4542-perl
```

Depois, vamos definir o `Dockerfile` de nossa aplicação segundo as sugestões fornecidas:

```dockerfile
FROM debian:buster-slim

EXPOSE 5000

COPY . /opt/app

RUN apt-get update \
    && apt-get install -y perl cpanminus make gcc \
    && cpanm --installdeps /opt/app

CMD plackup /opt/app/bin/app.psgi
```

Uma vez que o `Dockerfile` esteja pronto, construímos a imagem com o nome **dancer**:

```bash
docker image build -t dancer .
```

> Isso vai levar algum tempo...

Com a imagem pronta, escrevemos nosso tão esperado `docker-compose.yml`:

```yaml
version: '3.0'

services:
  perl:
    image: dancer
    environment:
    - REDIS_SERVER=redis
    - REDIS_PORT=6379
    ports:
    - 5000:5000
  redis:
    image: redis:alpine
```

E colocamos tudo para funcionar:

```bash
docker-compose up -d
docker-compose logs
curl localhost:5000
```

Podemos inclusive modificar a página HTML:

```
curl -X POST -H 'Content-Type: application/json' -d '{"html" : "<div id=\"getting-started\"><h1>Atualizado via API REST!</h1><h2>Estes valores foram gravados no Redis</h2><ol><li><h2>HTML Cache</h2><p>É claro que esta pequena página não justifica a utilização do Redis, mas ao menos demonstra a integração entre duas aplicações.</p></li>"}' http://localhost:5000/update
```
