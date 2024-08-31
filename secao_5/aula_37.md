## Aula 37 - Imagem

**Objetivo:** compreender com mais detalhes o conceito de **imagem** em **Docker**.

As **imagens** possuem um identificador único, geradas a partir de uma extensa string, sendo então comum usar *tags* com nomes mais simples.

As **imagens** são armazenadas em repositórios (*Docker Hub* por exemplo), sendo comum existir nas *tags* uma indicação de *latest*.

O comando para buscar uma imagem é possível usar o seguinte comando:

```shell
docker image pull redis:latest
```

Para listas as imagens disponíveis em seu **Docker**:

```shell
docker image ps
```

Para inspecionar a imagem:

```shell
docker inspect redis:latest
```

Para vincular um nome à imagem, é necessário executar o seguinte comando:

```shell
docker image tag redis:latest cod3r-redis
```

E para excluir imagem(ns):

```shell
docker image rm redis:latest cod3r-redis
```

Portanto, podem existir várias *tags* apontando para diferentes imagens.
