## Aula 14 - Instalação Docker

**Objetivo:** compreender o processo de instalação do **Docker**.

Caso a instalação do **Docker** (com base no Linux Container) seja feita em uma máquina Linux, é um processo mais simples, assim o *Docker Host* é instalado na próprio SO Linux. Assim, dentro do *Docker Host* é iniciado o *Docker Client*, o *Docker Engine* e os *containers*.

Em uma máquina que não possui Linux (como MacOS e Windows 7, 8), o *Docker Engine* é instalado em uma máquina virtual Linux, que atua como *Docker Host*, e o *Docker Client* atua no SO da máquina local e acessa de forma remota por meio da máquina virtual o *Docker Engine*, exigindo uma maior complexidade na comunicação.

Em versões mais modernas do Windows, possui mais compatilidade com o Linux, sendo assim possível manter uma interface compatível e retira a complexidade da comunicação. Por exemplo, o Windows 10 não exige uma máquina virtual, se comunicando diretamente com o Linux.

