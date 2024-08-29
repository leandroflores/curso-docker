## Aula 20 - Hello World no Docker

**Objetivo:** configurar a mensagem 'Hello World' com o **Docker**.

1 - No terminal, confira se o Docker está instalado:
```shell
docker --help
```

2 - Executar o comando para verificar se a instalação está correta
```shell
docker container run hello-world
```

Como a **imagem** não está baixada, o **Docker** baixou a **imagem** no repositório, e executou o *container* com a mensagem configurada na imagem.
