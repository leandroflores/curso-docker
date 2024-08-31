## Aula 40 - Docker Build

**Objetivo:** apresentar e compreender o processo de ***build*** do **Docker**.

A diferença entre um usuário comum e um usuário avançado em **Docker** é a capacide de construir **imagens**.

Para a construção de uma **imagem** temos os seguintes passos:

1 - Criação de um arquivo chamado `Dockerfile`. 

2 - Escrever o conteúdo da **imagem**

```Docker
FROM nginx:latest
RUN echo '<h1>Hello World!</h1>' > /usr/share/nginx/index.html
```

O comando ordena escrever 'Hello World!' no `index.html`.

3 - Construir a **imagem**

Para a construção da **imagem** é necessário executar o seguinte comando:

```shell
docker image build -t ex-simple-build .
```

A *tag* -t indica o nome desejado, no caso `ex-simple-build` e o `.` indica que é no próprio diretório local.

Para conferir se a **imagem** foi criada:

```shell
docker image ls
```

4 - Instanciar o *container* a partir da **imagem**

Para executar um *container* a partir dessa **imagem**, é necessário:

```shell
docker container run -p 80:80 ex-simple-build
```

O arquivo deve ser exatamente chamado de `Dockerfile`.
