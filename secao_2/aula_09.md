## Aula 9 - Docker x Máquina Virtual

**Objetivo:** entender a diferença entre Docker e Máquina Virtual.

A máquina virtual foi um padrão do mercado, com os seguintes benefícios:
* Isolamento de sistema
* Elasticidade de recursos
* Dimensionamento de memória

O *container* além dessas vantagens, precisa de menos recursos para inicializar. Na prática, seria possível ter N *containers*, enquanto seria impossível ter N VMs.

Nas máquinas virtuais, é necessário ter um supervisor, e o *guest OS* com o SO completo (*kernel*, memória, sistemas). Portanto, a VM consome mais memória e demanda tempo maior para inicializar.

No *container* Docker, existe o *container engine* com um processo isolado no SO (máquina local), com sistema de arquivos isolados, compartilhando recursos com o SO da máquina, exigindo menor memória e tempo para inicialização, atuando isoladamente.

Docker criou a camada **Docker Engine** para conseguir fazer uma interface entre o cliente e o SO da máquina local, a partir de uma **imagem Docker**, fazendo uso do conceito de containers Linux.

Portanto, o *container* mantém os benefícios da MV, com uma menor demanda de tempo e memória, fato que acarretou no sucesso do **Docker** no mercado, em especial pela agilidade e isolamento.