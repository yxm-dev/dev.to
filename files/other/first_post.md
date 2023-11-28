---
title: 'Prazer, Yuri.'
description: Um pouco sobre quem sou e sobre minha história
tags: 'linux, bash, logic, devops'
cover_image: 'https://i.imgur.com/jpU19nM.png'
canonical_url: null
published: true
id: 1552536
date: '2023-07-28T22:07:42Z'
---

Oi.

Sou novo por aqui no [dev.to](https://dev.to/yxm) e essa é a minha primeira postagem. Gostaria de iniciar esse contato me apresentando, contando um pouco de minha história e dizendo o que você pode esperar mim.

Yuri
=======

Meu nome é Yuri Ximenes Martins e tenho 30 anos. Sou um pesquisador brasileiro que atua na interseção entre Matemática, Ciência da Computação, Física e Filosofia, em temas ligados à abstração. Atuo, também, como desenvolvedor de software, onde tenho afinidade com o paradigma funcional. 

Sou um usuário assíduo de Linux e gosto de trabalhar dentro de um terminal. Amante de Vim, prefiro arquiteturas minimalistas. Gosto de pensar sobre o meu impacto no meio ambiente, de tornar o que é complexo intuitivo e de me expressar através de versos.

Física e Matemática
========  

Comecei minha graduação em Física em meados de 2010. De 2016 a 2022 estive no programa de Pós Graduação em Matemática da Universidade Federal de Minas Gerais (UFMG), onde fiz meu mestrado e doutorado.

Durante a graduação fui me interessando cada vez mais por extrair a essência de conceitos, por generalizar ideias, e pela criação de novas estruturas; exemplos do que se pode chamar de *processos de abstração*. Ao se seguir nessa direção, naturalmente se chega a questões ligadas aos fundamentos da área de estudo em questão. O entendimento dos pilares fundamentais da Física foi tema de minha pesquisa durante a pós-graduação. Mais precisamente, meu interesse se concentrou em questões que conectam a Física, a Matemática e a Filosofia.

* *O que é, de fato, um sistema da Física?* Essa foi minha questão central.

Existem várias maneiras de se perguntar sobre o que uma coisa "é". Uma delas é buscar dizer se ela pode ser "formalizada". Isso significa se perguntar se ela pode ser descrita puramente em termos de estruturas da Matemática e de certas áreas da Filosofia. No que diz respeito à Física, para descrevê-la precisa-se da Lógica (que vem da Matemática) e da Ontologia (que vem da Filosofia). A questão, então, é saber se Lógica e Ontologia são *suficientes* para descrever a Física.

A existência de uma base formal para a Física foi proposta, pela primeira vez, em 1900 pelo matemático David Hilbert. Mesmo depois de mais de 120 anos de pesquisa intensa, uma construção completa ainda não foi obtida. Como uma pequena amostra da importância e da grandiosidade do problema, noto que parte do que seria uma possível solução é considerada, ao lado de [P=NP](https://en.wikipedia.org/wiki/P_versus_NP_problem) e outras questões, como um dos [Problemas do Milênio](https://en.wikipedia.org/wiki/Millennium_Prize_Problems), os quais possuem como recompensa um prêmio de um milhão de dólares!

Desenvolvimento de Software
=========

Talvez você esteja se perguntando: mas como o estudo dos fundamentos da Física se relaciona com o Desenvolvimento de Software? E como você saiu de lá para chegar aqui na [dev.to](https://dev.to/yxm)?
 
Explico.

Toda linguagem (seja ela de programação, formal ou natural) pode ser estudada de diferentes aspectos. Dentre eles, tem-se a *sintaxe* (que lida com sua estrutura) e a *semântica* (que diz respeito às formas de se interpretá-la). 

Uma maneira de se organizar a sintaxe é por meio de "tipos". Isso significa que a sintaxe de uma linguagem está muito ligada com o que se chamada de [Teoria de Tipos](https://en.wikipedia.org/wiki/Type_theory). Por sua vez, uma maneira de se interpretar uma linguagem é associando a ela estruturas da Matemática. Assim, a semântica de uma linguagem está relacionada com a "teoria das estruturas matemáticas", a qual recebe o nome de [Teoria das Categorias](https://en.wikipedia.org/wiki/Category_theory).

![sintaxe_semantica](https://i.imgur.com/vLjiSfV.png)

Um fato interessante é que, no caso de linguagens de programação, tem-se uma seta contrária a partir do qual, para determinados sistemas de tipos, sabe-se associar uma linguagem de programação. Esse é a chamada [correspondência de Curry-Howard](https://en.wikipedia.org/wiki/Curry%E2%80%93Howard_correspondence).

![curry-howard](https://i.imgur.com/4fyd796.png)

Teoria das categorias e Teoria de Tipos são temas extremamente importantes em minha pesquisa. Por sua vez, a correspondência acima coloca Ciência da Computação em jogo. Através dela pode-se pensar em formalizar a Física e/ou a Matemática não em uma linguagem qualquer, mas em uma linguagem de programação! Esse é o cerne da pesquisa no desenvolvimento de linguagens de programação altamente estruturadas que atuem como verificadores de prova, como é o caso de [Coq](https://coq.inria.fr/) e [Agda](https://wiki.portal.chalmers.se/agda/pmwiki.php).

Portanto, sim: linguagens de programação aparecem nos fundamentos da Física. No entanto, como os problemas a serem descritos e solucionados por elas são extremamente abstratos e distantes daqueles da "vida real", tais linguagens destoam daquelas com cunho mais comercial, as quais foram desenvolvidas para atacar e serem eficientes na solução de problemas concretos.

Cansado de emergir em abstração, resolvi ter contato com questões concretas (e, portanto, com as ferramentas inerentes a elas), as quais possuem potencial de influenciar, de forma mais direta e imediata, o mundo em que vivemos. Foi assim que decidi entrar pro meio do Desenvolvimento de Software...  

Linux e Bash
===========

Desde que entrei na universidade, em 2010, utilizo Linux. No começo fui um usuário mais passivo. Aos poucos, à medida em que me aproximava da abstração e da busca pelo essencial, tornei-me mais ativo, no sentido de não só utilizar ferramentas, mas também modificá-las e criar novas de acordo com meus interesses e necessidades.

Pra ser sincero, aprendi a programar de forma procedural em Bash. Gosto muito de automatizar pequenas tarefas, criar funções que incorporem diferentes funcionalidades, desenvolver versões interativas para CLI já existentes, criar TUI para aplicações, etc. No fundo, gosto mesmo é de trabalhar no terminal! 

No entanto, me dá um pouco de agonia ver como lidar só com linha de comando pode ser contra intuitivo. Sinto-me forçado a recorrer a documentações da GNU recorrentemente, bem como a (salvadora) [ArchWiki](https://wiki.archlinux.org/). Nesse sentido, tenho medido alguns esforços para construir um ambiente mais intuitivo que, quem sabe, possa servir não só a mim, mas a outros que desejam viver no terminal sem serem grandes especialistas em Linux. Chamo tal projeto de *InTUI* (uma mistura de "intuição" com "TUI"). Trata-se de um conjunto de funções e scripts em Bash, as quais disponibilizo em meu [GitHub](https://github.com/yxm-dev).

Lab
======

Tenho tentado pegar o hábito de documentar minhas dúvidas e as respostas que melhor se adequam a elas. Como as dúvidas são recorrentes, fica mais simples de encontrar a resposta caso precise outra vez. Junto delas tenho criado listas com documentações e referências complementares para softwares que utilizo, além de um "dicionário" contendo uma tentativa de dar definições mais precisas a termos do meio.

Pensando que talvez possa ser útil a alguém, disponibilizo o conteúdo na página [lab.yxm.me](https://lab.yxm.me), cujos arquivos `.md` subjacentes podem ser encontrados [neste](https://codeberg.org/yxm/lab) repositório no [Codeberg](https://codeberg.org).

O que esperar de mim
===========

Aqui no [dev.to](https://dev.to/yxm) pretendo escrever no formato de colunas sobre temas nos quais tenho interesse e que acredito que possa contribuir de alguma forma. Por exemplo, pretendo manter as seguintes colunas:

1. Linux Tips, com dicas rápidas sobre Linux
2. Bash Tips, com dicas rápidas sobre Bash
3. Vim Tips, com dicas rápidas sobre Vim
4. CLI Tools, com pequenos tutoriais e sugestões de ferramentas que operam por linha de comando,

bem como algo sobre Lógica, abstração, teoria das categorias, teoria de tipos, novas tecnologias que eu estiver estudando, e o que mais me parecer útil a alguém.

Fim
=====

Um abraço e até mais!

* [yxm.me](https://yxm.me)
* [github.com/yxm-dev](https://github.com/yxm.dev)
* [codeberg.com/yxm](https://codeberg.com/yxm)

