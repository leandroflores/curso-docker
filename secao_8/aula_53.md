## Aula 53 - Estrutura Docker Compose

**Objetivo:** apresentar uma aplicação com **Docker** com três serviços: banco de dados (MongoDB), *backend* (*Node*) e *frontend* (*nginx*).

O próximo passo consiste em implementar no diretório *backend*, o arquivo `app.js`:

```javascript
const express = require("express")
const restful = require("node-restful")

const server = express()
const mongoose = restful.mongoose

// DB:
mongoose.Promise = global.Promise
mongoose.connect("mongodb://db/mydb")

// Middleware
server.use(express.urlencoded());

// Routes
server.get("/", (req, res, next) => res.send("Backend"))

// Start Server:
server.listen(3000)
```

No diretório *frontend*, é necessário criar o arquivo `index.html`:

```html
<h1>Frontend</h1>
```

E um arquivo `Dockerfile.yml`, com os comandos a serem executados:

```yml
version: '3'
services:
  db:
    image: mongo:3.4
  backend:
    image: node:8.1
    volumes:
      - ./backend:/backend
    ports:
      - 3000:3000
    command: bash -c "cd /backend && npm i && npm install express node-restful mongoose@4.11.1 body-parser cors && node app"
  frontend:
    image: nginx:1.13
    volumes:
      - ./frontend:/usr/share/nginx/html/
    ports:
      - 80:80
```

O arquivo possui três serviços: `db`, `backend` e `frontend`.

O `db` é construído com a **imagem** do `mongo:3.4`.

O `backend` é construído com a **imagem** do `node:8.1`, com o **volume**, mapeando o diretório *backend* da máquina local para o *container*, as **portas** como `3000:3000` (externa:interna) e o **comando** `cd /backend && npm i && npm install express node-restful mongoose@4.11.1 body-parser cors && node app`.

O `frontend` é construído com a **imagem** do `nginx:1.13`, com o **volume** mapeando o diretório *frontend* para o diretório do `nginx`, com as **portas** `80:80` (externa:interna).

Portanto, a **imagem** está construída, e para instanciar os **containers** é necessário executar:

```shell
docker compose up
```
