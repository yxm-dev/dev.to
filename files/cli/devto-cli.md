---
title: 'devto-cli: sincronizando um repositório do GitHub com suas publicações do dev.to'
description: 'Escreva seus artigos localmente, dê um git push e eles serão automaticamente publicados no dev.to.'
tags: 'github, automation, CLI, node'
cover_image: ''
canonical_url: null
published: true
series: CLI Tools
id: 1552537
date: '2023-07-29T00:42:16Z'
---

Introdução
------

Gosto de escrever e de compartilhar minhas ideias; gosto de tornar intuitivo aquilo que é tido como complexo. Ao longo da última década, escrevi livros, artigos científicos e notas de aula para cursos que ministrei em diversos tópicos da Física e da Matemática. No entanto, estando agora mais interessado em Desenvolvimento de Software, me vi na posição de buscar produzir e divulgar conteúdo em um novo formato.

Em contrapartida, gosto de fazer tudo o que puder no terminal e, quando possível, trabalhar com ferramentas CLI ao invés de TUI ou GUI. Há um peso estético, confesso. No entanto, CLIs permitem automação de processos, o que facilita a vida. Além disso, ao trabalhar localmente posso me dar ao luxo de utilizar de todas as configurações e customizações que fiz em meu computador para melhor se adaptarem as minhas necessidades. Isso, para mim, é qualidade de vida!

Ao meu ver, o ideal seria poder escrever os conteúdos localmente, em arquivos `.md`, para então publicá-los em plataformas de divulgação através de alguma ferramenta CLI. Além da comodidade de escrever em Markdown, isso permitiria facilmente reutilizar posts e automatizar sua publicação. Naturalmente, a construção de uma tal CLI depende da disponibilização por parte da plataforma de uma API versátil o suficiente.

Inicialmente cheguei a tentar me adaptar a publicar conteúdos no [Linkedin](https://linkedin/in/yxmartins), mas o fato de ter de preparar cada post especificamente para lá me fez repensar se realmente vale o esforço. Infelizmente, o Linkedin não fornece uma API oficial para criação e edição de postagens para usuários quaisquer (apenas para páginas vinculadas a alguma empresa - veja [aqui](https://www.linkedin.com/developers/apps/new?src=re-other&veh=learn.microsoft.com%7Cre-other)), o que inviabiliza a construção de CLI com as características desejadas (para uma CLI não oficial, baseada na API restrita fornecida pelo Linkedin, veja [tigillo/linkedin-cli](https://github.com/tigillo/linkedin-cli)).

Foi então que descobri que a plataforma [dev.to](https://dev.to) oferece uma API rica e, para minha surpresa, uma ferramenta CLI que já funciona muito bem: [sinedied/devto-cli](https://github.com/sinedied/devto-cli)! Por conta disso, decidi concentrar aqui a minha criação de conteúdo sobre Desenvolvimento de Software.

Como tudo funciona
----------
[sinedied/devto-cli](https://github.com/sinedied/devto-cli) é uma aplicação escrita em `Node.js` que permite a sincronização de um repositório local de arquivos `.md` com o conjunto de publicações de um perfil na plataforma [dev.to](https://dev.to). A sincronização se dá por intermédio da criação de um repositório no GitHub, conectado ao repositório local, o qual contém uma workflow que a cada novo commit criado pela CLI executa a GitHub Action [sinedied/publish-devto](https://github.com/sinedied/publish-devto). Esta, por sua vez, ativa a API que, por meio dos metadados contidos na frontmatter dos arquivos `.md`, os faz corresponder às publicações no [dev.to](https://dev.to).

Configuração
-----------

Descrevo o passo a passo da configuração do [sinedied/devto-cli](https://github.com/sinedied/devto-cli) no caso de um sistema operacional que utiliza `Bash` como shell:

1. instale [sinedied/devto-cli](https://github.com/sinedied/devto-cli) por meio do `npm`:
```bash
    npm install -g @sinedied/devto-cli
```
2. logado em sua conta do [dev.to](https://dev.to), acesse [dev.to/settings/extensions](https://dev.to/settings/extensions). No final da página, gere uma API.  
3. crie um repositório no seu GitHub, o qual servirá para intermediar o processo. Por exemplo, o meu é [yxm-dev/dev.to](https://github.com/yxm-dev/dev.to).
4. acesse seu repositório e vá em `Settings > Secrets and variables > Actions`.
5. adicione uma nova key com o nome `DEVTO_TOKEN` e com conteúdo dada por sua API obtida no passo 2.
6. crie um diretório local, digamos `dir/`, acesse-o e dê um `dev init`:
```bash
    cd dir
    dev init
```
7. complete com o nome do repositório do GitHub criado na etapa 3 e com o branch que você irá utilizar.
8. dentro de `dir/` crie um arquivo `.env` e adicione o repositório, o branch e a API:
```bash
    touch .env
    echo "DEVTO_TOKEN=sua_API" >> .env
    echo "DEVTO_REPO=seu_usuario/seu_repositorio" >> .env
    echo "DEVTO_BRANCH=seu_branch" >> .env
```
9. por segurança, crie um `.gitignore` e adicione o arquivo `.env`:
```bash
    touch .gitignore
    echo ".env" >> .gitignore
```
10. crie um remote para seu repositório do GitHub:
```bash
    git remote add seu_remote ssh://git@github.com/seu_usuario/seu_repositorio
```
11. push para o repositório no GitHub:
```bash
    git add .
    git commit -m "..."
    git push
```

Utilizando
---------

A utilização básica é bem simples:

1. dentro de `dir/` há um sub-diretório `dir/posts/`. É aqui que seus arquivos `.md` serão criados
2. para criar um arquivo `.md` pré-configurado, execute `dev new nome_post`
3. complete os metadados na frontmatter. Se quiser que o post seja publicado, coloque `published: true`
4. para publicar as postagens, em `dir/` execute `dev push -e`.
    * OBS: somente os arquivos `.md` que estiverem dentro de `dir/posts/` serão publicados  
5. se quiser ver o status de suas postagens, execute `dev stats` em `dir/`.

Mantendo as Postagens no GitHub
----------

Em minha humilde opinião, existe uma pequeno defeito na construção utilizada pelo [sinedied/devto-cli](https://github.com/sinedied/devto-cli). Ao se executar `dev push -e`, as postagens passam pelo GitHub, mas não ficam por lá! Você poderia pensar em dar um `git push`. Mas, neste caso, para cada novo commit, ao invés dos posts já publicados no [dev.to](https://dev.to) serem atualizados, eles são duplicados! 

Para remediar o problema e automatizar o processo de publicação, criei uma função `devp`, a qual copia os arquivos de `dir/posts/` para um outro diretório `dir/files/`. Para implementá-la, faça o seguinte:

1. adicione `posts/*` em `dir/.gitignore`:
```bash
    echo "posts/*" >> dir/.gitignore
```
2. em seu arquivo `~/.bashrc`, adicione o seguinte:
```bash
    function devp(){
        cd dir/
        cp -r posts/* files/
        git add .
        git commit -m "..."
        git push -q dev.to master
        dev p -e
    }

```

Pronto! Agora basta executar `devp` para publicar seus artigos no [dev.to](https://dev.to) e, ao mesmo tempo, mantê-los em seu repositório do GitHub.


