# stylelint_makedeb

Pacote Stylelint convertido e criado, através da versão do ArchLinux (16.10.0-1) para instalação no Ubuntu Linux 22.04

- [archlinux packages extra, stylelint](https://archlinux.org/packages/extra/any/stylelint/)   
- [gitlab.archlinux, stylelint](https://gitlab.archlinux.org/archlinux/packaging/packages/stylelint)  
___
## Pré-requisitos

- Ubuntu 22.04
- Permissões de superusuário

Certifique-se de que você tenha essas dependências instaladas antes de começar.

## Instalação

- Baixe o pacote .deb e instale com o apt, desta forma será instalado o pacote `nodejs` como dependência
```bash
sudo apt install ./stylelint_16.10.0-1_amd64.deb
```

No Archlinux o stylelint usa o nodejs do pacote `nodejs-lts-jod`, versão 22.14.0-1  
Mas o Ubuntu 22.04 mantém o nodejs do repositório apt antigo (12.22.9+), enquanto a versão snap está usando o pacote mais atual (22.14.0+).  
É necessário instalar o node do repositório snap e configurar o stylelint para usar o mesmo.  
Para isso, siga os seguintes passos:  

- Instale o node via Snap
```bash
sudo snap install node --classic
```
- Crie e configure o script `/usr/local/bin/stylelint` deixando o conteúdo desta forma:

```bash
#!/usr/bin/env bash

PATH=/snap/bin:$PATH
/usr/bin/stylelint "$@"
```
- Dê permissão de execução
```bash
sudo chmod +x /usr/local/bin/stylelint
```
