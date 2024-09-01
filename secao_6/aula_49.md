## Aula 49 - Rede Host

**Objetivo:** apresentar uma visão geral do tipo de rede *Host* em **Docker**.

No tipo *host* os *containers* fazem comunicação diretamente com a máquina local, sendo menos segura, no entanto, é mais rápida.

O modo *bridge* oferece uma camada de proteção, enquanto o modo *host* retira essa proteção.

Para executar um *container* no modo *host*:

```shell
docker container run -d --name container4 --net host alpine sleep 1000
```

E para verificar o resultado:

```shell
docker container exec -it container4 ifconfig
```

Apresenta as mesmas interfaces que a máquina local, sendo o *container* mais exposto, no entanto, é mais rápido.

O modo padrão do **Docker** é o *bridge* resultando em maior proteção.
