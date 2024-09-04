## Aula 54 - Cadastro Completo com Docker Compose

**Objetivo:** apresentar o exercício completo de uma aplicação com **Docker** com três serviços: banco de dados (MongoDB), *backend* (*Node*) e *frontend* (*nginx*).

O próximo passo consiste em complementar no diretório *backend*, o arquivo `app.js`:

```javascript
const express = require("express")
const restful = require("node-restful")
const bodyParser = require("body-parser")
const cors = require("cors")

const server = express()
const mongoose = restful.mongoose

// DB:
mongoose.Promise = global.Promise
mongoose.connect("mongodb://db/mydb")

// Middleware
server.use(express.urlencoded());
server.use(bodyParser.json())
server.use(cors())

// ODM:
const Client = restful.model("Client", {
    name: { type: String, required: true }
})

// Rest API
Client.methods(["get", "post", "put", "delete"])
Client.updateOptions({new: true, runValidators: true})

// Routes
Client.register(server, "/clients")

// Start Server:
server.listen(3000)


```

No diretório *frontend*, é necessário criar o arquivo `index.html`:

```html
<html>
    <head>
        <meta charset="utf-8">
        <title>Cadastro Simples</title>
        <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
    </head>
    <body>
        <div class="container">
            <h1>Cadastro Simples</h1>
            <hr>
            <div>
                <input name="id" type="hidden" />
                <div class="form-group">
                    <label for="Name"></label>
                    <input class="form-control" name="name" placeholder="Digite o nome" />
                </div>
                <button class="btn btn-success" save>Salvar</button>
            </div>

            <table class="table" id="clients">
                <thead>
                    <tr>
                        <th>Nome</th>
                        <th>Ações</th>
                    </tr>
                </thead>
                <tbody id="clientsRows"></tbody>
            </table>
        </div>

        <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>

        <script>
            const API = "http://localhost:3001";

            const createButton = (label, type) => {
                return $("<button>").addClass(`btn btn-${type}`).html(label);
            }

            const renderRows = clients => {
                const rows = clients.map(client => {
                    const updateButton = createButton("Atualizar", "warning");
                    updateButton.click(() => loadClient(client));

                    const removeButton = createButton("Excluir", "danger");
                    removeButton.click(() => removeClient(client));

                    return $("<tr>")
                        .append($("<td>").append(client.name))
                        .append($("<td>").append(updateButton).append(removeButton));
                })

                $("#clientsRows").html(rows);
            }

            const loadClient = client => {
                $("[name=id]").val(client._id);
                $("[name=name]").val(client.name);
            }

            const removeClient = client => {
                $.ajax({
                    method: "DELETE",
                    url: `${API}/clients/${client._id}`,
                    success: getClients
                });
            }

            const getClients = () => {
                $.ajax({
                    url: `${API}/clients`,
                    success: clients => {
                        renderRows(clients);
                        $("[name]").val("");
                    }
                });
            }

            const saveClient = () => {
                const _id = $("[name=id]").val();
                const name = $("[name=name]").val();
                $.ajax({
                    method: _id ? "PUT" : "POST",
                    url: `${API}/clients/${_id}`,
                    data: _id ? { _id, name } : { name },
                    success: getClients
                });
            }

            $(() => {
                getClients();
                $("[save]").click(saveClient);
            })
        </script>
    </body>
</html>
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
