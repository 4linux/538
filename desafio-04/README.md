# 04 - Encadeando Comandos

Quando rodamos um contêiner, podemos pedir para que este contêiner execute algo (assim como o `hello-world`) e simplesmente termine. Vamos criar um contêiner baseado na imagem `debian` que "roube" todo o HTML do site da 4Linux. Para contêineres de testes o parâmetro `--rm` é muito útil, pois faz com que o contêiner seja excluído automaticamente ao fim da execução.

Para que nosso objetivo funcione precisaremos atualizar a lista de pacotes, instalar o `curl` e rodar o `curl`, no Linux podemos encadear comandos com a sequência `&&`:

```bash
docker container run --rm debian:buster-slim apt-get update && apt-get install -y curl && curl -L 4linux.com.br
# saída
# bash: apt-get: command not found
```

Ué?! Porque `apt-get` não foi encontrado? Isso aconteceu porque os `&&` após o `apt-get update` não foram para o comando do `docker`, eles foram considerados outros comandos após a execução do comando `docker`.

Para enviar todos esses comandos para o contêiner é preciso passá-los como um único "texto" (ou string), e podemos fazer isso com `sh -c`, onde `-c` recebe uma string com os comandos:

```bash
docker container run --rm debian:buster-slim sh -c 'apt-get update && apt-get install -y curl && curl -L 4linux.com.br'
```

O contêiner já foi removido e temos o HTML em nossa tela.

## Desafio

Existe uma imagem bem pequena, menor que as imagens do alpine, chamada `busybox`. Esta imagem é muito útil para realizar testes na rede.

No Linux podemos utilizar o comando `nslookup` para verificar um registro no DNS ou mesmo realizar um simples teste de rede com o comando `ping`.

Nosso objetivo é rodar um contêiner que faça estas duas tarefas e finalize automaticamente. Há um certo nível de dificuldade nesta tarefa, vamos aos objetivos:

- Crie um contêiner baseado na imagem `busybox`
- Assim que o contêiner for criado dois passos precisam ser executados de uma única vez antes do contêiner finalizar:
  - O contêiner precisará fazer um teste de rede rodando um ping no endereço de DNS da Google
    - Para isso execute `ping -c1 8.8.8.8`
  - O contêiner precisará logo após o primeiro teste descobrir quais servidores DNS respondem pelo nome **4linux.com.br**
    - Para isso será preciso rodar o comando `nslookup -query=ns 4linux.com.br`
