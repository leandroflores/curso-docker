## Aula 18 - Instalação Linux

**Objetivo:** fazer a instalação do **Docker** no Linux.

1 - Atualizar o sistema:
```shell
sudo apt-get update
```

2 - Instalar pacotes:
```shell
sudo apt-get install  curl apt-transport-https ca-certificates software-properties-common
```

3 - Atualizar o repositório:
```shell
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

```

4 - Arquitetura 64
```shell
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```

5 - Atualizar o sistema:
```shell
sudo apt update
```

6 - Instalar o Docker:
```shell
apt-cache policy docker-ce
```

7 - Conferir a instalação:
```shell
docker --help
```
