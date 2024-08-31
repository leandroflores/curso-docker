## Aula 38 - Gerenciamento de Imagens

**Objetivo:** compreender com mais detalhes os comandos para o gerenciamento de **imagem** em **Docker**.

Os comandos relativos à **imagem** sempre iniciam com `docker image`.

Para fazer o *download* de uma **imagem** do *Docker Hub* é o seguinte comando:

```shell
docker image pull <name>
```

Para exibir as **imagens** atuais é o seguinte comando:

```shell
docker image ls
```

Para remover uma **imagem** é o seguinte comando:

```shell
docker image rm <tags>
```

Para ver as informações detalhadas de um **imagem** é o seguinte comando:

```shell
docker image inspect <tags>
```

Para criar uma tag de uma **imagem** é o seguinte comando:

```shell
docker image tag <source> <new-tag>
```

Para construir uma **imagem** é o seguinte comando:

```shell
docker image build
```

Para enviar uma **imagem** (local ou *Docker Hub*) é o seguinte comando:

```shell
docker image push
```

Portanto, esses sete comandos são fundamentais para o gerenciamento de **imagens** em **Docker**.
