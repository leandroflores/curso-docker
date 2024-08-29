## Aula 11 - Imagens

**Objetivo:** entender o conceito de **Imagem Docker**.

**Imagem** é um modelo de sistema de arquivos para inicializar o *container*, sendo um arquivo de somente leitura. O *container* é criado com base em uma **imagem**.

**Imagens** são criadas por meio de um processo chamado **build**. O **build** apresenta um arquivo descritor com os passos de criação da **imagem**, sendo possível gerar de maneira mais simples e objetiva.

As **imagens Docker** podem ser armazenadas em um serviço de registro (*Registry*) chamado ***Docker Hub***, que é um repositório oficial de imagens Docker, com padrões de imagens de acordo com recursos necessários para o *container*.

As **imagens** são compostas por uma ou mais **camadas** (*layers*), sendo que uma **camada** representa mudanças no sistema de arquivo, sendo uma **camadas** também chamada de **imagem intermediária**. 

A junção de **camadas** formam uma **imagem**. O *Advanced multi-layered unification filesystem* (AUFS) é um sistema de arquivos baseado em *layers, é responsável  por carregar o *container*, partindo da *layer* mais básica até a mais complexa, para iniciar o *container*.

A principal vantagem de organizar a **imagem** em **camadas** é o reuso, pelo fato de ser possível compor **imagens** a partir de **camadas** de outras **imagens**.
