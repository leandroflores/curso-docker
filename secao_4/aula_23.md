## Aula 23 - Comando *run* e *containers*

**Objetivo:** compreender a relação entre o comando *run* e os *containers*.

Na última aula, a partir do comando abaixo, foi exibido a lista de *containers* executados pelo **Docker**:
```shell
docker container run -a
```

Para entrar no terminal do *container* é possível acessar por meio do seguinte comando:
```shell
docker container -it debian bash
```

Dentro do bash, crie um arquivo:
```shell
touch test.txt
```

E confira a criação do arquivo:
```shell
ls
```

O arquivo `test.txt` estará criado. Para sair do *container*, execute o seguinte comando:
```shell
exit
```

Execute novamente:
```shell
docker container -it debian bash
```

Execute agora:
```shell
ls test.txt
```

Portanto, o comando *run* cria novos *containers* toda vez que é executado.

Para verificar os *containers*, é possível usar o seguinte comando:
```shell
docker container ps -a
```

O **Docker** cria automaticamente identificadores e nomes para os novos *containers*, porém é possível atribuir nomes específicos aos novos *containers*.
