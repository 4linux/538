# 01 - Um Container Qualquer

Ainda não vimos muita coisa sobre o Docker mas é possível se divertir um pouquinho, nem tudo precisa ser sério, certo?
Não podemos chamar isso de um exercício, mas serve para perceber que existe qualquer tipo de imagem por aí. Sendo assim vamos testar um contêiner relativamente curioso que pode servir como um descanso de tela para o terminal.

Ainda veremos os parâmetros `-t` e `-i`, por enquanto apenas observe seu "novo aquário":

```bash
docker container run -ti wernight/funbox asciiquarium
```

> Existem outros parâmetros que exibem outras animações curiosas como `nyancat`, `sl` e `cmatrix`, utilize `CTRL + C` para sair.
