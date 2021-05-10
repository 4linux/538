# 03 - Resposta

Primeiro baixe as imagens:

```bash
docker pull postgres
docker pull postgres:alpine
```

Vamos comparar as imagens:

```bash
docker images postgres
# REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
# postgres     alpine    e43172f9204f   3 weeks ago   160MB
# postgres     latest    26c8bcd8b719   4 weeks ago   314MB
```

A imagem baseada em **alpine** tem 154MB a menos (pode variar) justamente porque sua imagem base, a Alpine, é mais leve que a imagem base da imagem padrão, baseada em Debian.

Se olharmos a [documentação](https://hub.docker.com/_/postgres) da imagem no Docker Hub podemos clicar nas tags que nos levará aos seus respectivos `Dockerfiles`. Ainda não vimos o que é um `Dockerfile` mas na primeira linha podemos observar `FROM debian:buster-slim` em algumas delas e `FROM alpine` em outras.

O `Dockerfile` é utilizado para criar imagens, mas não se preocupe, ainda aprenderemos!
