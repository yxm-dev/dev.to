---
title: 'berg: um CLI para Codeberg'
description: 'Neste post apresentamos berg, um CLI para Codeberg similar ao gh para Github e glab para Gitlab'
tags: 'git, cli, codeberg, rust'
cover_image: 'https://i.imgur.com/fPigp5O.png'
canonical_url: null
published: true
series: CLI tools
id: 1617389
date: '2023-10-01T16:42:13Z'
---

# Introdução

Em um [post anterior](https://dev.to/yxm/codeberg-uma-alternativa-open-source-e-gratuita-ao-github-e-gitlab-b80) apresentei a vocês o [Codeberg](https://codeberg.org): uma alternativa gratuita e Open-Source ao Github e ao Gitlab.

Sou adepto a usar o terminal sempre que possível. Dito isso, algo que me incomodava um pouco era o fato de que Github e Gitlab oferecem ferramentas CLI oficiais ([gh](https://github.com/cli/cli) e [glab](https://gitlab.com/gitlab-org/cli), respectivamente) para a configuração de repositórios, merges, etc. O Codeberg não fornece uma CLI, de modo que sempre que precisava criar, deletar ou editar a descrição de repositório, por exemplo, tinha que acessar via browser. Nada muito sério, só uma inconveniência.

Pois encontrei [berg](https://codeberg.org/RobWalt/codeberg-cli): uma CLI para o Codeberg que se propõe a ser uma solução similar ao `gh` e ao `glab`. A CLI não é oficial, mas cumpre bem com seu papel (veja observação no fim do post). 

Neste post descrevo brevemente como instalar e utilizar `berg`.

# Instalação

`berg` é escrito em `Rust`, de modo que o primeiro passo é instalar `Rust` e seu gerenciador de pacotes e builder `cargo`:

```bash
curl https://sh.rustup.rs -sSf | sh
```

Feito isso, o seguinte código será adicionado em seu `.bashrc`:

```bash
. "$HOME/.cargo/env"
```

Cabe notar que em `Bash` o ponto `.` é um alias para o builtin `source`. Se você utiliza `.` em outras aplicações (como é o meu caso), para que não haja problemas altere a linha acima para

```bash
source "$HOME/.cargo/env"
```

Agora clone o repositório do `berg` e o instale com `cargo`:

```bash
git clone https://codeberg.org/RobWalt/codeberg-cli
cd codeberg-cli
cargo install --path .
```

# Autorização

Depois de instalado, autorize o uso de `berg` em sua conta do Codeberg com

```bash
berg auth login
```
Prossiga com um `y` e você será redirecionado para sua conta do Codeberg. Gere um token adicionando um nome e as permissões que você deseja. Copie o token e cole no terminal onde executou o comando anterior. 

Pronto! Agora você já pode utilizar o `berg` com as permissões criadas.

# Utilização

Dê um `berg -h` para ver as opções disponíveis:

```
Usage: berg [COMMAND]

Commands:
  auth          Authentication subcommands
  user          User subcommands
  issue         Issue subcommands
  pull          Pull request subcommands
  label         Label subcommands
  repo          Repository subcommands
  milestone     Milestone subcommands
  notification  
  completion    Print completion script
  help          Print this message or the help of the given subcommand(s)

Options:
  -h, --help     Print help (see more with '--help')
  -V, --version  Print version

```

Por exemplo, se quiser criar um repositório, execute `berg repo create` e siga as instruções.

Para mais detalhes sobre um dada opção ou comando, execute `berg [option] --help`.

* **OBS:** uma pena é que com `berg` não se pode deletar repositórios, algo que pode ser feito diretamente com `gh`, por exemplo.

# Fim

É isso. Com `berg` o Codeberg se torna uma alternativa ainda mais viável ao manejo de pequenos projetos. Codeberg ainda não fornece (e ao que pude entender nem se propõe a tal) ferramentas CI/CD, de modo que o manejo de grandes projetos ainda é bastante limitado.

Um abraço e até mais.

Yuri Ximenes Martins

