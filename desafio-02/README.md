# 02 - E no Nginx?

No curso utilizamos o contêiner com um webserver apache e pudemos acessá-lo através do comando `curl`. Esse contêiner foi baseado em uma imagem chamada `httpd`, vamos fazer algo similar ao que fizemos mas com um contêiner que tenha o webserver nginx.

- Crie um contêiner baseado na imagem `nginx`;
- Entre no contêiner;
- Procure o HTML principal e escreva `Containers!` dentro deste arquivo - utilize aspas simples!
- Saia do contêiner;
- Descubra qual é o IP do contêiner com o comando `docker container inspect`;
- Utilize o comando `curl` com este IP para visualizar seu conteúdo.
