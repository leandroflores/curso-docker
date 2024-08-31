## Aula 45 - Imagens e *Docker Hub*

**Objetivo:** enviar uma **imagem** para o ***Docker Hub*** com **Docker**.

É necessário criar uma conta no *Docker Hub*.

Para listar as **imagens** disponíveis:

```shell
docker image ls
```

É possível associar uma *tag* à uma **imagem**:

```shell
docker image tag ex-simple-build dockercod3r/simple-build:1.0
```

Assim, é criada uma *tag* apontando para a mesma **imagem**.

O próximo passo é fazer o *login* no *Docker Hub*:

```shell
docker login --username=<user>
```

E então subir a **imagem**

```shell
docker image push dockercod3r/simple-build:1.0
```

Assim, você terá subido a sua **imagem** para o *Docker Hub*.
