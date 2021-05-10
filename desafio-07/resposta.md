# Resposta

A imagem do MongoDB chama-se `mongo` e as variáveis para controlar o usuário e sua senha são:

- `MONGO_INITDB_ROOT_USERNAME` - configura o usuário;
- `MONGO_INITDB_ROOT_PASSWORD` - configura a senha do usuário.

Sendo assim, para criar o contêiner conforme descrito pelo exercício, basta digitar:

```bash
docker container run -dti --name mongo \
-e MONGO_INITDB_ROOT_USERNAME=aluno \
-e MONGO_INITDB_ROOT_PASSWORD=4linux \
mongo
```

> A barra invertida "\" nos permite quebrar a linha sem que o shell interprete como um envio de comando.
