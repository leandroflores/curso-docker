## Aula 50 - Introdução

**Objetivo:** apresentar uma introdução sobre a coordenação de múltiplos *containers* em **Docker**.

Um ambiente real é composto de vários elementos: servidos de banco de dados, fila, *batch*, *backend*, *frontend*, etc.

Uma boa prática é organizar estas partes em *containers* próprios. Não é recomendado criar uma **imagem** única com todos os recursos, pelas limitações relacionadas a desempenho, organização e escalabilidade.

Para organizar vários *containers*, é necessário usar um arquivo *docker compose*, que referencia vários serviços, responsável pela composição de várias *containers*.

Assim, é possível definir uma **imagem** para cada serviço e o **docker compose** instancia os *containers* para o sistema.

O consumo de memória é leve na instanciação de *container*, garantindo o isolamento e a independência, sendo o **docker compose** responsável por iniciar e orquestrar os *containers*.
