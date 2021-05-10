# 05 - Resposta

Preparando diretórios e arquivos:

```bash
mkdir php
cat > php/index.php <<'EOF'
<?php

for($i = 0; $i < 10; $i++)
  echo "$i<br />\n";
EOF
```

Subindo o contêiner:

```bash
docker container rm -f php-app
docker container run -dti --name php-app -v /root/php:/opt/app -p 8080:8080 php:alpine php -S 0.0.0.0:8080 -t /opt/app
```

Acessando:

```bash
curl localhost:8080
```

> Lembre-se da porta 8080!

Não foi preciso nos preocupar com o endereço IP pois estamos redirecionando todo o tráfego que chegar na porta `8080` da máquina para dentro do contêiner, sendo assim basta apontarmos para a própria máquina, ou seja, `localhost`.
