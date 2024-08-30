## Aula 28 - Mapeamento de Portas

**Objetivo:** compreender o mapeamento de portas de *containers* **Docker**.

O primeiro comando visa executar um *container* fazendo uso de portas.

```shell
docker container run -p 8080:80 nginx
```

No comando acima, o `-p` corresponde ao uso da porta, sendo 8080 a **porta externa**, 80 a **porta interna** e nginx é a **imagem** do *container* a ser executado.

Em um novo terminal, execute o seguinte comando:

```shell
curl http://localhost:8080
```

Como resultado, tem o resultado do *container* executado Para conferir se o *container* está sendo executado:

```shell
docker container ps
```
