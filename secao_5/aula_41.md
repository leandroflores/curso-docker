## Aula 41 - Preparação da Imagem

**Objetivo:** construir um **Dockerfile** que receba parâmetros para uma **imagem Docker**.

Para a construção de uma **imagem** temos os seguintes passos:

1 - Criação de um arquivo chamado `Dockerfile`.

2 - Escrever o conteúdo da **imagem**

```Docker
FROM debian
LABEL maintainer="Aluno Cod3r <aluno at cod3r.com.br>"

ARG S3_BUCKET=files
ENV S3_BUCKET=${S3_BUCKET}
```

O comando acima é construído com uma máquina Debian, com o mantenedor aluno cod3r.

Como argumento temos o `S3_BUCKET` sendo o valor padrão files, sendo associada à variável de ambiente `S3_BUCKET`.

3 - Construir a **imagem**

Para a construção da **imagem** é necessário executar o seguinte comando:

```shell
docker image build -t ex-build-arg .
```

A *tag* -t indica o nome desejado, no caso `ex-build-arg` e o `.` indica que é no próprio diretório local.

Para conferir se a **imagem** foi criada:

```shell
docker image ls
```

4 - Instanciar o *container* a partir da **imagem**

Para executar um *container* a partir dessa **imagem**, é necessário:

```shell
docker container run ex-build-arg bash -c 'echo $S3_BUCKET'
```

Como resultado, é exibido `files`. Isto acontece pelo fato de não ter sido passado nenhum argumento, portanto é retornado o configurado como padrão.

5 - Construir a **imagem** com parâmetro

É necessário executar o seguinte comando:

```shell
docker image build --build-arg S3_BUCKET=myapp -t ex-build-arg .
```

Caso executar na sequência:

```shell
docker container run ex-build-arg bash -c 'echo $S3_BUCKET'
```

É exibido 'myapp'.

A passagem de argumentos é fundamental para o reuso de **imagens** em Docker, principalmente usando em conjunto variáveis de ambiente.
