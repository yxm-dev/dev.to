---
title: 'devto-cli: sincronizando um repositório do GitHub com suas publicações do dev.to'
description: 'Escreva seus artigos localmente, dê um git push e eles serão automaticamente publicados no dev.to.'
tags: 'github, automation, CLI, node'
cover_image: ''
canonical_url: null
published: true
series: CLI Tools
id: 1552526
date: '2023-07-28T21:46:14Z'
---

Introdução
------

Gosto de fazer tudo o que no terminal e, quando possível, trabalhar com ferramentas CLI ao invés de TUI ou GUI. Há um peso estético, confesso. No entanto, CLIs permitem automação de processos, o que facilita a vida. Além disso, ao se trabalhar localmente pode-se dar ao luxo de utilizar de todas as configurações e softwares que estão em sua máquina e que foram customizados especialmente para suas necessidades.

Por outro lado, a conexão de uma ferramenta num servidor com uma máquina local é feita através de APIs. Ao meu ver, uma das grandes vantagens da plataforma dev.to é que ela fornece uma API com acesso a diversas funcionalidades, como a criação e edição de artigos. Com ela, pode-se construir softwares que lhe permitam criar e editar artigos localmente, no formato de arquivos `.md`, para então serem enviados ao seu perfil do dev.to.

Em contrapartida, pode-se pensar em seu conjunto de artigos como sendo um repositório, de modo que, por meio da API, seu repositório de artigos corresponde a um diretório local de arquivos `.md`, digamos `posts/`. Seria interessante manter um controle de versões desses arquivos `.md`, permitindo, então, ter um controle sobre as versões dos artigos publicados. Isso nos leva a pensar em utilizar `git` no diretório `posts/`.  




