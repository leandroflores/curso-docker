## Aula 59 - Filas

**Objetivo:** apresentar a criação das **filas** com **Docker**.

Neste passo, vamos criar um diretório chamado `app`, com o arquivo `app.sh`:

```shell
#!/bin/sh

pip install bottle
python -u sender.py
```

No mesmo diretório, criar o arquivo `sender.py`:

```python
from bottle import request, route, run

@route("/", method="POST")
def send():
    assunto = request.forms.get("assunto")
    mensagem = request.forms.get("mensagem")
    print("fwedasckxzl")
    return f"Mensagem enfileirada! Assunto {assunto} Mensagem {mensagem}"

if __name__ == "__main__":
    run(host="0.0.0.0", port=8080, debug=True)
``` 



```html
<html>
    <head>
        <meta charset='uft-8'>

        <title>E-mail Sender</title>

        <style>
            label { display: block; }
            textarea, input { width: 400px; }
        </style>
    </head>
    <body class="container">
        <h1>E-mail Sender</h1>
        <form action="http://localhost/8080" method="POST">
            <div>
                <label for="assunto">Assunto</label>
                <input type="text" name="assunto">
            </div>

            <div>
                <label for="mensagem">Mensagem</label>
                <textarea name="mensagem" cols="50" rows="6"></textarea>
            </div>

            <div>
                <button>Enviar</button>
            </div>
        </form>
    </body>
</html>
```

E para o arquivo `docker-compose.yml` é necessário atualizar criar um novo serviço chamado `app`:

```yml
version: '3'
volumes:
  dados: 
services:
  db:
    image: postgres:9.6
    environment:
      POSTGRES_DB: "db"
      POSTGRES_HOST_AUTH_METHOD: "trust"
    volumes:
      # Database <source:target>
      - dados:/var/lib/postgres/data
      # Scripts <source:target>
      - ./scripts:/scripts
      # Init script <source:target>
      - ./scripts/init.sql:/docker-entrypoint-initdb.d/init.sql
  frontend:
    image: nginx:1.13
    volumes:
      - ./web:/usr/share/nginx/html/
    ports:
      - 80:80
  app:
    image: python:3.6
    volumes:
      - ./app:/app
    working_dir: /app
    command: bash ./app.sh
    ports:
      - 8080:8080
```

Assim, temos um novo *container* chamado *app* que usa a porta `8080` e recebe os dados do *frontend*.

E no terminal, é necessário subir a instância no modo *daemon*:

```shell
docker compose up -d 
```

E com o comando a seguir é possível ver os processos em execução:

```shell
docker-compose ps
```

Assim, temos criado o serviço de *app*.
