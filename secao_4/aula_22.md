## Aula 22 - Ferramentas alternativas

**Objetivo:** conhecer ferramentas alternativas para trabalhar com **Docker**.

No Linux, o primeiro passo da aula é executar o seguinte comando:
```shell
bash --version
```

E hoje, como resultado, a máquina retornou o seguinte:
```
GNU bash, versão 5.2.21(1)-release (x86_64-pc-linux-gnu)
```

Agora, é necessário executar o seguinte comando:
```shell
docker container run debian bash --version
```

O comando *run*, como mostrado aula passada, segue os seguintes passos:
 * Download da **imagem** (*docker push image*)
 * Criar o **container** (*docker container create*)
 * Iniciar o **container** (*docker container start*)
 * Executar o **container** (*docker container exec*)

 E como resultado o terminal apresenta:
 ```
 GNU bash, version 5.2.15(1)-release
 ```

E como explicado aula passada, uma nova execução do comando anterior é mais rápida por já possuir a **imagem** em *cache*.

Para verificar quais *containers* estão sendo executados no **Docker** é necessário executar o seguinte comando:

```
docker container ps
```

Para verificar todos os *containers* já executados no **Docker** é necessário executar o seguinte comando:

```
docker container ps -a
```

Para remover o *container* dessa lista de histórico, é possível executar o comando:

```
docker container run --rm debian bash --version
```