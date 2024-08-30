## Aula 25 - Reutilização de *containers*

**Objetivo:** compreender a reutilazação de *containers*.

Para verificar os *containers* executados em **Docker** é necessário executar o seguinte comando:

```shell
docker container ls
```

Para verificar todos os *containers* executados em **Docker** é necessário executar o seguinte comando [a: *attach*]:

```shell
docker container ls -a
```

Para iniciar um *container* é possível executar o seguinte comando (a = *atach*, i = *interactive*) com o nome do *container*:

```shell
docker container start -ai mydeb
```

Portanto, a partir do **nome** de um *container* é possível inicializá-lo e reaproveitá-lo.
