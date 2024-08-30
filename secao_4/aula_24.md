## Aula 24 - Nome dos *containers*

**Objetivo:** compreender a importação dos nomes para os *containers*.

Para a criação de um *container* com um nome específico, é necessário executar os seguinte comando:
```shell
docker-container run --name mydeb -it debian bash
```

Caso o comando seja executado novamente, ocorre um erro por já exister um *container* com o mesmo nome.

Portanto, os *containers* devem possuir nome único em **Docker**.
