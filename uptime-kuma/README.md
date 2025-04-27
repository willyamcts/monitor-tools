# Uptime Kuma

Guia oficial: [louislam/uptime-kuma/wiki/How-to-Install](https://github.com/louislam/uptime-kuma/wiki/%F0%9F%94%A7-How-to-Install)


### Docker run

```
mkdir /usr/local/uptime-kuma

docker run -d --name uptime-kuma --restart=always --net host -v /usr/local/uptime-kuma:/app/data  louislam/uptime-kuma
```

### Acesso
Via web: `<IP>:3001`


### Alterar a senha

```
docker exec -it uptime-kuma sh -c 'npm run reset-password'
```
