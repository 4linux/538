# 02 - Resposta

```bash
docker container run -dti --name nginx nginx
docker container exec -ti nginx sh
echo 'Containers!' > /usr/share/nginx/html/index.html
exit
docker container inspect nginx # o retorno varia, ex: 172.17.0.3
curl 172.27.0.3
# Containers!
```
