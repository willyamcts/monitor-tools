# Pandora FMS

* Install via script -> https://github.com/pandorafms/pandorafms/blob/develop/extras/deploy-scripts/INSTALL.md
* Install via docker -> https://hub.docker.com/r/pandorafms/pandorafms-open-stack-el8


### Docker compose

```
PANDORA_DIR=/usr/local/pandora
mkdir -p ${PANDORA_DIR}/{server,database}
mkdir ${PANDORA_DIR}/database/mysql

chown 1000:0 ${PANDORA_DIR}/server
chown 1001:1001 ${PANDORA_DIR}/database/mysql
```

```
services:

  pandora:
    image: pandorafms/pandorafms-open-stack-el8:latest
    restart: always
    container_name: pandora
    volumes:
      - /usr/local/pandora/server:/usr/share/pandora_server
    depends_on:
      - db
    environment:
      TZ: America/Sao_Paulo
      MYSQL_ROOT_PASSWORD: pandora
      DBHOST: db
      DBNAME: pandora
      DBUSER: pandora
      DBPASS: pandora
      DBPORT: 3306
      INSTANCE_NAME: pandora01
      PUBLICURL: ""
      SLEEP: 5
      RETRIES: 10
    network_mode: host
#    network:
#     - pandora
#     - bridge1
    ports:
      - "8080:80"
      - "41121:41121"
      - "162:162/udp"
      - "9995:9995/udp"

  db:
    image: pandorafms/pandorafms-percona-base
    restart: always
    #command: ["mysqld", "--innodb-buffer-pool-size=900M"]
    container_name: pandora-db
    volumes:
      - /usr/local/pandora/database/mysql:/var/lib/mysql
    environment:
      MYSQL_ROOT_PASSWORD: pandora
      MYSQL_DATABASE: pandora
      MYSQL_USER: pandora
      MYSQL_PASSWORD: pandora
    networks:
     - pandora

networks:
  pandora:
    name: pandora_network
  bridge1:
    name: pandora_bridge
    driver: bridge
```


## Acesso
Via web em: `<IP>:8080`
* **User**: admin
* **Senha**: pandora


## Configuração das sondas (módulos)
* https://pandorafms.com/guides/public/books/first-steps-with-pandora-fms/page/7-network-device-remote-monitoring

### DNS query
Não foi possível realizar o monitoramento desejado da consulta DNS, o retorno do plugin só verifica se o DNS está resolvendo para um IP esperado. A intenção do teste seria coletar o tempo de resolução da consulta de DNS.
