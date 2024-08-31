## Aula 42 - Instruções de Povoamento

**Objetivo:** povoar uma **imagem Docker**.

Um passo importante é copiar arquivos da máquina local para o *container*.

Nesse exemplo seguimos os seguintes passos:

1 - Criar o arquivo `Dockerfile`:

```Dockerfile
FROM ngix:latest
LABEL maintainer 'Aluno <aluno.com.br>'

RUN echo '<h1>Sem conteudo</h1>' > /usr/share/nginx/conteudo.html
COPY *.html /usr/share/nginx
```

O `Dockerfile` escreve o h1 em um arquivo chamado `conteudo.html` e copia todos os arquivos `.html` da máquina local.

2 - Criar um arquivo `index.html`:

```html
<a href="conteudo.html">Conteúdo do site</a>
```

3 - Criar a **imagem**:

```shell
docker image build -t ex-build-copy .
```

4 - Executar o *container* com a **imagem**:

```shell
docker container run -p 80:80 ex-build-copy
```
