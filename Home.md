# Welcome to the jems3-frontend wiki!

For accessing the application documentation, the provided sidebar in the right links to the different document sections (in english).

The user shown documentation does not include this page and it's default page is the [[Index]].

## Como editar a documentação

A melhor forma para editar essa Wiki é clonando o repositório Git:

```
git clone https://github.com/ComputerNetworks-UFRGS/jems3-wiki.wiki.git
```

Dessa forma, os arquivos podem ser editados diretamente no seu editor de texto, fazendo referências para outras páginas e arquivos (como imagens) com caminhos relativos.

O GitHub trabalha com arquivos [Markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet).
Um editor sugerido, que contém ferramenta de preview de Markdown, é o [VS Code](https://code.visualstudio.com/).

Novas páginas precisam ser adicionadas manualmente em `_Sidebar.md` para serem mostradas na guia lateral.

## Como a Wiki afeta a documentação interna do JEMS3

A aplicação, no seu pipeline de deployment (quando uma nova versão do sistema é lançada) irá clonar o repositório da Wiki e inseri-lo na sua pasta de assets, em `src/assets/wiki`.

Para que novas modificações na Wiki sejam alteradas na versão em produção, é necessário [reexecutar o pipeline](https://gitlab.com/ComputerNetworks-UFRGS/jems3-frontend/-/pipelines) para o branch desejado (master é o nome atual do branch de produção), de forma que a Wiki seja atualizada para o sistema rodando em produção.

Nota: não é necessário o lançamento de uma nova versão. A operação irá pegar sempre a versão mais recente da documentação. Não possuímos versionamento da documentação (ex: versão x da wiki para versão y do sistema). Sempre que houver um deploy do sistema, irá pegar a Wiki mais recente para utilizar no sistema.