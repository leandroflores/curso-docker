## Aula 47 - Rede None

**Objetivo:** apresentar uma visão geral do tipo de rede *None* em **Docker**.

Em redes do tipo *None*, o *container* fica isolado, sem acesso para outros *containers* e à máquina local.

Assim, o acesso é feito somente via terminal, e o *container* possui acesso apenas ao volume local.

Ideal para *containers* que não façam processamento com a rede.

Para execução de um *container*, é possível executar, sendo utilizada a rede *bridge*:

```shell
docker container run --rm alpine ash -c "ifconfig"
```

Para rodar com rede do tipo *None*, é possível executar:

```shell
docker container run --rm --net none alpine ash -c "ifconfig"
```

Assim, como resultado, o *container* é isolado, sem acesso ao exterior.
