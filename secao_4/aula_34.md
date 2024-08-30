## Aula 34 - Sintaxe do *Docker Client*

**Objetivo:** apresentar a sintaxe dos comandos para o *Docker Client*.

O *Docker Client* apresenta uma sintaxe mais clara para manipulação no **Docker**.

Para listar os *containers* em execução:

```shell
docker container ls
```

Para listar as **imagens** em execução:

```shell
docker image ls
```

Para listar os **volumes** em execução:

```shell
docker volume ls
```

E para a remoção, é necessário usar o comando `rm`:

```shell
docker container rm <container>
```

```shell
docker image rm <image>
```

```shell
docker volume rm <volume>
```
