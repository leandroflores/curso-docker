## Aula 56 - Banco de Dados

**Objetivo:** apresentar a criação do banco de dados (MongoDB) com **Docker**.

O primeiro passo é a criação do arquivo `docker-compose.yml` com a definição das **imagens**:

```yml
version: '3'
services:
  db:
    image: postgres:9.6 
```

A **imagem** é definida pelo serviço de banco de dados (**db**) com o *postgres* versão 9.6. Para a instanciação do *container* é necessário executar em modo *daemon*:

```shell
docker compose up -d 
```

E com o comando a seguir é possível ver os processos em execução:

```shell
docker-compose ps
```

