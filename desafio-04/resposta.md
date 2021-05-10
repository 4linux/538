# 04 - Resposta

- Crie um contêiner baseado na imagem `busybox`
- Assim que o contêiner for criado dois passos precisam ser executados de uma única vez antes do contêiner finalizar:
  - O contêiner precisará fazer um teste de rede rodando um ping no endereço de DNS da Google
    - Para isso execute `ping -c1 8.8.8.8`
  - O contêiner precisará logo após o primeiro teste descobrir quais servidores DNS respondem pelo nome **4linux.com.br**
    - Para isso será preciso rodar o comando `nslookup -query=ns 4linux.com.br`

```bash
docker container run --rm busybox sh -c 'ping -c1 8.8.8.8 && nslookup -query=ns 4linux.com.br'
```

> Lembre-se, o parâmetro `--rm` remove o contêiner ao término de sua execução.

A saída será semelhante a seguinte:

```
Status: Downloaded newer image for busybox:latest
PING 8.8.8.8 (8.8.8.8): 56 data bytes
64 bytes from 8.8.8.8: seq=0 ttl=113 time=1.017 ms

--- 8.8.8.8 ping statistics ---
1 packets transmitted, 1 packets received, 0% packet loss
round-trip min/avg/max = 1.017/1.017/1.017 ms
Server:         8.8.8.8
Address:        8.8.8.8:53

Non-authoritative answer:
4linux.com.br   nameserver = ns1.4linux.com.br
4linux.com.br   nameserver = ns2.4linux.com.br
```

Contêineres baseados nas imagens do `busybox` são utilizados com certa frequência para fazer testes na rede e nas aplicações do Kubernetes ou do Docker Swarm.
