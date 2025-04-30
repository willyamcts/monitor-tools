# Netdata

Guia oficial: [netdata.cloud/docker](https://learn.netdata.cloud/docs/netdata-agent/installation/docker)


### Docker compose

```
mkdir -p /usr/local/netdata/etc
```

```
version: '3'

services:
  netdata:
    image: netdata/netdata:stable
    container_name: netdata
    pid: host
    network_mode: host
    restart: unless-stopped
    cap_add:
      - SYS_PTRACE
      - SYS_ADMIN
    security_opt:
      - apparmor:unconfined
    volumes:
      - /usr/local/netdata/etc:/etc/netdata
      - netdatalib:/var/lib/netdata
      - netdatacache:/var/cache/netdata
      - /:/host/root:ro,rslave
      - /etc/passwd:/host/etc/passwd:ro
      - /etc/group:/host/etc/group:ro
      - /etc/localtime:/etc/localtime:ro
      - /proc:/host/proc:ro
      - /sys:/host/sys:ro
      - /etc/os-release:/host/etc/os-release:ro
      - /var/log:/host/var/log:ro
      - /var/run/docker.sock:/var/run/docker.sock:ro
      - /run/dbus:/run/dbus:ro

volumes:
  netdatalib:
  netdatacache:
```

### Acesso
Via web: `<IP>:19999`



## Configuração de plugins

Após a adição de monitoramentos é necessário reiniciar o serviço do Netdata executando o comando abaixo:

```
docker exec -it netdata sh -c 'netdatacli shutdown-agent'
```

### Notificação via Discord

 - Channel webhook: https://support.discord.com/hc/en-us/articles/228383668-Intro-to-Webhooks
 - https://learn.netdata.cloud/docs/alerts-&-notifications/notifications/agent-dispatched-notifications/discord

```
cd /usr/local/netdata/etc
nano ./edit-config health_alarm_notify.conf
```

```
END_DISCORD="YES"  
DISCORD_WEBHOOK_URL="https://discord.com/api/webhooks/XXXXXXXXXXXXX/XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"  
DEFAULT_RECIPIENT_DISCORD="alerts"
```

