## Aula 31 - Servidor Web em *background*

**Objetivo:** apresentar um exemplo de servidor web em *background*.

Quando o *container* é executado em *background*, o que é muito comum, sendo um processo rodando aguardando requisições. A *flag* -d representa o modo *daemon*.

```shell
docker container run -d --name ex-daemon-basic -p 8080:80 -v $(pwd)/curso:/usr/share/nginx/html nginx
```

Assim, o *container* fica executando em *background*, aguardando possíveis requisições.

Para parar o *container*, é necessário executar o seguinte comando:

```shell
docker container stop start-basic
```
