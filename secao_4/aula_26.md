## Aula 26 - Controle de *containers*

**Objetivo:** controlar o acesso de *containers*.

O *Docker Engine* fornece mecanismos para o *container* ficar isolado com a máquina local. No entanto, é necessário existir compartilhamento entre a máquina e o *container*.

É comum o compartilhamento de portas, diretórios e arquivos entre o *container* e a máquina local, e a comunicação entre diferentes *containers*.

Portanto, é fundamental o *container* se comunicar com outras fontes, para a aplicação funcionar.
