## Aula 30 - Mapeamneto de *containers*

**Objetivo:** apresentar o mapeamento entre a máquina local e um *container* **Docker**.

Crie um diretório chamado `curso` com um arquivo HMTL chamado `index.html`.

Uma forma de mapear uma porta para um arquivo da máquina local, é possível usar o seguinte comando:

```shell
docker container run -p 8080:80 -v $(pwd)/curso:/usr/share/nginx/html nginx
```

Assim, o *container* nginx vai ser direcionado para o diretório `curso`, sendo exibido a página HTML definida no arquivo `index.html`.

Portanto, esse mapeamento permite que o *container* acesse um recurso externo da máquina local, usando a *flag* v (volume).
