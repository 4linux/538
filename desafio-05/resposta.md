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
docker container run -dti --name php-app -v /root/php:/opt/app php:alpine php -S 0.0.0.0:8080 -t /opt/app
```

Procurando IP e acessando:

```bash
docker container inspect php-app # 172.17.0.4
curl 172.17.0.4:8080
```

> Lembre-se da porta 8080!
