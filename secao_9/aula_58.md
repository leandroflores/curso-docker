## Aula 58 - *Frontend*

**Objetivo:** apresentar a criação do *frontend* com **Docker**.

Neste passo, vamos criar um diretório chamado `web`, com o arquivo `index.html`:

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
        <form action="" method="POST">
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

E para o arquivo `docker-compose.yml` é necessário atualizar criar um novo serviço:

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
```

Assim, temos um novo *container* chamado *frontend* que usa a porta `80` e encaminha para o arquivo `index.hml`.

E no terminal, é necessário subir a instância no modo *daemon*:

```shell
docker compose up -d 
```

E com o comando a seguir é possível ver os processos em execução:

```shell
docker-compose ps
```

Assim, temos criado o serviço de *frontend*.
