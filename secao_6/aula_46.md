## Aula 46 - Redes em Docker

**Objetivo:** apresentar uma visão geral e tipos de redes em **Docker**.

O **Docker** usa como padrão o modelo *bridge*, com cada *container* possuindo sua própria interface com seu próprio endereço IP.

A partir da ponte (*bridge*), um *container* acessa a máquina local e posteriormente a *internet*.

Um *container* pertencem a mesma rede, mas é possível criar redes diferentes para cada *container*.

É criada uma camada de isolamento entre os *containers*, sendo um mecanismo de proteção entre os *containers*.

Existem quatro tipos de redes:

* ***None Network***: *container* não possui nenhum acesso à rede.
* ***Bridge Network***: uma ponte (*bridge*) entre os *containers* com a máquina local com acesso à rede.
* ***Host Network***: *container* possui acesso direto à maquina local.
* ***Overlay Network (swarm)***: *container* com *cluster*.

Para consultar as redes disponíveis no **Docker** é possível executar:

```shell
docker network ls
```

Sendo apresentado os três primeiros tipos apresentados: `none`, `host` e `bridge`.
