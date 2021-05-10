# 07 - Variáveis de Ambiente

O MongoDB é um gerenciador de bancos de dados orientado a documentos, livre e de código aberto. Dentro do MongoDB guardamos os dados em um formato semelhante ao JSON.
A imagem do MongoDB aceita algumas variáveis de ambiente, o objetivo é o seguinte:

- Criar um contêiner chamado `mongo` baseado na imagem do MongoDB;
- O contêiner deverá rodar desatachado;
- Especificar as duas variáveis de ambiente configurando o nome do "root user" como `aluno` e sua senha como `4linux`;

Feito isso, você pode testar se o contêiner foi criado corretamente com o seguinte comando:

```bash
echo 'show dbs' | docker container exec -i mongo mongo -u aluno -p 4linux
# A saída será:
#
# MongoDB shell version v4.4.5
# connecting to: mongodb://127.0.0.1:27017/?compressors=disabled&gssapiServiceName=mongodb
# Implicit session: session { "id" : UUID("0d89cdae-6c8d-42d0-aacd-23aec0920dce") }
# MongoDB server version: 4.4.5
# admin   0.000GB
# config  0.000GB
# local   0.000GB
# bye
```
