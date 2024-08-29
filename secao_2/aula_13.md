## Aula 13 - Arquitetura

**Objetivo:** entender a **Arquitetura do Docker**.

O Docker é dividido em duas partes:
* *Docker Daemon*: também chamado de *Docker Engine* ou *Docker Server*.
* *Docker Client*: interface com linha de comando para acessar os serviços do *Docker Daemon*

O *Docker Daemon* vai no *Registry*, trás as **imagens** por meio de *cache* local e instancia os ***containers*** na máquina local.

O *Docker Daemon* também pode ser acessado por API REST e uma interface gráfica *Kitematic*.

Portanto, a arquitetura do Docker é composta por:
* *Registry*: na nuvem, um repositório contendo as **imagens**.
* *Daemon*: a partir de uma requisição, baixa a **imagem** via *cache* no *Registy* e inicia o ***container*** na máquina local.
* *Client*: interface para interação com o *Docker Daemon*, normalmente na máquina local também.
