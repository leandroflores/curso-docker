## Aula 44 - Execução do Container

**Objetivo:** criar o **Dockerfile** para o *container* com a **imagem Docker**.

O próximo passo é necessário criar um arquivo chamado `Dockerfile`.

Para cada comando, uma **layer** é gerada, sendo possível concatenar comandos para gerar uma única **layer**.

Uma boa prática é descrever as variáveis no final do `Dockerfile`, para que a parte superior do arquivo fique em `cache`.

```Dockerfile
FROM python:3.9
LABEL mantainer="Aluno <aluno.com.br>"

RUN useradd www && \
    mkdir /app && \
    mkdir /log && \
    chown www /log

USER www
VOLUME /log
WORKDIR /app
EXPOSE 8000

ENTRYPOINT [ "/usr/local/bin/python" ]
CMD [ "run.py" ]
```

E assim, é necessário gerar a **imagem**:

```shell
docker image build -t ex-build-dev .
```

E para executar o *container*:

```shell
docker container run -it -v $(pwd):/app -p 80:8000 --name python-server ex-build-dev
```

No comando, está criando o *container* na versão interativa (`-it`), com o volume no diretório atual do *container* `app`, para a porta `80` (externa) e `8000` (interna) com o nome `python-server` a partir da imagem `ex-build-dev`.

Portanto, temos o primeiro servidor Python rodando com **Docker**.

É possível criar um novo container para consultar o **log** do *container* com o servidor Python.

```shell
 docker container run -it --volumes-from=python-server debian cat /log/http-server.log
 ```

O comando acima acessa o *container* com o servidor Python, e acessa o arquivo `http-server.log`.
