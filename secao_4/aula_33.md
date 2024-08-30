## Aula 33 - Manipulação de *containers*

**Objetivo:** compreender as ações para a manipulação de *containers* em *background*.

Para listar os *containers* em execução, é possível executar os seguintes comandos:

```shell
docker container ls
```

```shell
docker container list
```

```shell
docker container ps
```

```shell
docker ps
```

Para ver todos os *containers* já executados, basta adicionar a *flag* -a:

```shell
docker container ls -a
```

```shell
docker container list -a
```

```shell
docker container ps -a
```

```shell
docker ps -a
```

Para consultar os *logs* de um *container* é necessário executar o seguinte comando:

```shell
docker container logs ex-daemon-basic
```

Para uma análise mais detalha, é possível usar o comando de inspeção:

```shell
docker container inspect ex-daemon-basic
```
