## Aula 36 - *Container* e **Imagem**

**Objetivo:** compreender a diferença entre o conceito de *container* e **imagem** no contexto de **Docker**.

A **imagem** seria uma classe, sendo um modelo de sistema de arquivos.

O ***container*** é a instância da **imagem**, atuando como um processo isolado, com seu próprio sistema de arquivos.

Assim, a partir de uma **imagem** é possível instanciar vários ***containers***.

Para consultar os comandos disponíveis em **Docker**:

```shell
docker --help
```

Para consultar os comandos disponíveis para **imagens** em Docker:

```shell
docker image --help
```

Para consultar os comandos disponíveis para **volumes** em Docker:

```shell
docker volume --help
```
