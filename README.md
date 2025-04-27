# Indice
- [Sobre](#sobre)
- [Requisitos](#requisitos)
- [Ferramentas de monitoramento](#ferramentas-de-monitoramento)
- [Resultados](#resultados)


# Sobre
Este repositório visa resumir e servir como guia para implementar ferramentas de monitoramento de forma rápida a fim de testá-las e escolher a que melhor atende ao seu cenário. As ferramentas de monitoramento aqui testadas são free/open source. 

### Objetivo
* centralizar informações sobre algumas ferramentas em um único repositório
* facilitar a rápida implementação para teste
* agilizar a escolha de uma ferramenta de monitoramento de disponibilidade

Após testar os projetos e escolher a que melhor atende seu cenário, consulte a documentação oficial para implementar em ambiente de produção.


# Requisitos
Todos os projetos testados foram implementados via container Docker usando Debian. 

Para instalar o Docker em seu Debian execute esse script [willyamcts/containers-solutions](https://raw.githubusercontent.com/willyamcts/containers-solutions/refs/heads/main/install-docker.sh) ou consulte o guia de instalação oficial [aqui](https://docs.docker.com/engine/install/).


# Ferramentas de monitoramento
O foco das ferramentas escolhidas é no <ins>monitoramento ativo</ins> e <ins>monitoramento de disponibilidade</ins>. 

A intenção é configurar monitoramento em ICMP, DNS query, HTTP(S) ou conexão TCP. SNMP também é considerado mas é apenas para fins de documentação, visto que pode requerer configuração adicional no host a ser monitorado. 


A seguir as ferramentas testadas:

| Ferramenta | Release | Release Data | Demo |
|--------|---------|---------|----------|
|[Netdata](https://github.com/netdata/netdata) | x | | :e-mail: https://app.netdata.cloud/spaces/netdata-demo |
|[Zabbix](https://github.com/zabbix/zabbix) | x | | :heavy_check_mark: https://demo-zabbix.racom.eu/zabbix (user:customer pass:RacomDemo1234) |
|[Uptime Kuma](https://github.com/louislam/uptime-kuma) | 1.23.16 | 12/2024 | :heavy_check_mark: https://demo.kuma.pet/start-demo |
|[OpenNMS](https://github.com/OpenNMS/opennms) | x | | - |
|[Pandora FMS](https://github.com/pandorafms/pandorafms) | x | | - |
|[Observium](https://observium.org/) | CE 24.12.13800 | 12/2024 | :heavy_check_mark: https://demo.observium.org | 
|[Checkmk](https://github.com/Checkmk/checkmk) | x | | :e-mail: https://checkmk.com/play-with-checkmk |
|[Icinga2](https://github.com/Icinga/icinga2) | x | | :heavy_check_mark: https://icinga.com/demo |
|[Cacti](https://github.com/Cacti/cacti) | x | | - |


# Resultados
A tabela abaixo visa auxiliar na escolha da ferramenta ideal, apontando pontos positivos e negativos em forma de tabela.


