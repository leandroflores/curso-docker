## Aula 10 - Containers

**Objetivo:** entender o conceito de ***Container***.

*Containers* são processos segredados no mesmo *kernel* (isolamento), sendo possível existir subprocessos filhos. 

No entanto, um *container* deve por princípio executar uma única aplicação, sendo possível inicializar vários *containers*.

Os *containers* possuem um sistema de arquivos próprio.

Os *containers* são ambientes leve e portáteis, com o encapsulamento das bibliotecas e dependências, para serem executadas de maneira isolada.

A vantagem de usar vários *containers* é justamente o isolamento e rapidez de inicialização, com os *containers* atuando como agentes autonômos e se comunicando para o sistema com um todo.