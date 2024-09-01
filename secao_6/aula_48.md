## Aula 48 - Rede Bridge

**Objetivo:** apresentar uma visão geral do tipo de rede *Bridge* em **Docker**.

Para verificar as redes disponíveis no **Docker** é necessário executar:

```shell
docker network ls
```

Então é listado as redes disponíveis. E para inspecionar uma rede é ncessário executar:

```shell
docker network inspect bridge
```

Assim é apresentado a rede *bridge*, sendo possível alocar endereços com intervalo de rede entre 172.17.0.1 à 172.17.255.255.

Para executar o primeiro *container* é necessário executar:

```shell
docker container run -d --name container1 alpine sleep 1000
```

E para verificar o endereço do `container1` é necessário executar:

```shell
docker container exec -it container1 ifconfig
```

Para o `container1` o endereço é 172.17.0.2.

Fazendo o mesmo para um segundo container:

```shell
docker container run -d --name container2 alpine sleep 1000
```

E para o `container2` é necessário executar:

```shell
docker container exec -it container2 ifconfig
```

O `container2` possui o endereço é 172.17.0.3.

E para fazer uma comunição entre o `container1` e o `container2`, é possível executar:

```shell
docker container exec -it container1 ping 172.17.0.3
```

É possível também fazer um `ping` externo.

```shell
docker container exec -it container1 ping www.google.com
```

Para a criação de uma nova rede é necessário:

```shell
docker network create --driver bridge rede_nova
```

Para verificar:

```shell
docker network ls
```

E inspecionar:

```shell
docker inspect rede_nova
```

E a `rede_nova` possui endereço 172.20.0.1.

E para um novo *container* na nova rede criada:

```shell
docker container run -d --name container3 --net rede_nova alpine sleep 1000
```

E para consultar o endereço do `container3`:

```shell
docker container inspect container3
```

O `container3` possui endereço 172.20.0.2.

Um exemplo seria tentar conectar o `container3` ao endereço do `container1`:

```shell
docker container exec -it container3 ping 172.17.0.2
```

Porém não existe acesso. Para conectar o `container3` à rede *bridge* é necessário:

```shell
docker network connect bridge container3
```

Agora rodando novamente o comando:

```shell
docker container exec -it container3 ping 172.17.0.2
```

É possível verificar que é feito o `ping`, pois possui interface para as redes.

Para desconectar o `container3` da rede:

```shell
docker network disconnect bridge container3
```

Assim, o `container3` fica fora de alcance da rede *bridge*.
