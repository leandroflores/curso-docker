## Aula 21 - Comando run

**Objetivo:** compreender o comando *run* do **Docker**.

Na aula anterior, foi executado o seguinte comando:

```shell
docker container run hello-world
```

O comando *run* agrupa uma série de quatro comandos:
 * 1 - Download da **imagem** do *Docker Hub* (*docker image pull*).
 * 2 - Criação de um *container* (*docker container create*).
 * 3 - Inicialização de um *container* (*docker container start*).
 * 4 - Execução do *container* (docker container exec).

Na próxima tentativa, a **imagem** já está baixada, portanto a execução é mais rápida.
