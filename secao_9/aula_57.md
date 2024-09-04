## Aula 57 - Volumes

**Objetivo:** apresentar a criação dos volumes com **Docker**.

Neste passo, vamos criar um diretório chamado `scripts` para os comandos SQL. O primeiro arquivo é chamado `init.sql` com o script SQL para  a criação da tabela `emails`:

```sql
CREATE DATABASE email_sender;

\c email_sender

create table emails (
    id serial not null,
    data timestamp not null default current_timestamp,
    assunto varchar(100) not null,
    mensagem varchar(255) not null
);
```

E para a checagem dos dados um arquivo chamado `check.sql`:

```sql
\l
\c email_sender
\d emails
```

E para o arquivo `docker-compose.yml` é necessário atualizar os **volumes**:

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
```

E no terminal, é necessário subir a instância no modo *daemon*:

```shell
docker compose up -d 
```

E com o comando a seguir é possível ver os processos em execução:

```shell
docker-compose ps
```

E no fim, executar o comando `check.sql`:

```shell
docker-compose exec db psql -U postgres -U postgres -f /scripts/check.sql
```

Assim, temos criado o serviço de banco de dados.
