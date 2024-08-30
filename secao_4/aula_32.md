## Aula 31 - Gerenciamento de *container* em *background*

**Objetivo:** apresentar os comandos para o gerenciamento de *containers* em *background*.

Para iniciar um *container* em **Docker**, é necessário executar o comando:

```shell
docker container start ex-daemon-basic
```

Para parar o *container*, é necessário executar o seguinte comando:

```shell
docker container stop ex-daemon-basic
```

E para reiniciar o *container*:

```shell
docker container restart ex-daemon-basic
```

Os comandos apresentados funcionam pelo **nome** ou **id** do *container*.

Portanto, para o gerenciamento de *containers* temos os seguintes comandos: `start`, `restart` e `stop`.
