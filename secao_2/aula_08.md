## Aula 8 - O que é Docker

**Objetivo:** entender o objetivo e os de utilizar o Docker.

Docker é uma tecnologia de virtualização, diferente das tradicionais máquinas virtuais (MV), como o Virtual Box (máquina Linux e MV Windows por exemplo).

Docker é uma *engine* de administração de **containers**.

***Container*** é um processo isolado do sistema, em que é possível iniciar sua aplicação apartado do host, com sistemas de arquivos, com um ambiente completamente isolado com suas bibliotecas e dependências.

Diferente de uma MV, o *container* compartilha recursos com a máquina *host* (*kernel* e binários), utilizando menos memória que uma MV.

O *container* precisa de menos memória, pelo Docker utilizar *Linux Containers* (LXC), sendo portanto baseado apenas em comandos Linux. Porém, na prática, a maioria das aplicações funcionam em Linux, o que não é um impeditivo.

**Docker** é uma tecnologia de código aberto, escrita em Go, com base no sistema de virtualização baseado em software, com o *kernel* compartilhado do SO, fazendo otimização de memória e processamento, além de garantir o isolamento, como configuração de memória, rede, processamento, sistema de arquivos, etc.
