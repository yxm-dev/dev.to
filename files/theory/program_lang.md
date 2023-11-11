---
title: Linguagens e seus tipos
description: 'Nessa postagem apresentamos, de maneira simples e didática, o que de fato são linguagens e como se classificam entre linguagens naturais, linguagens formais, linguagens de máquina, linguagens de programação, etc.'
tags: 'language, study, LLM, syntax'
cover_image: 'https://i.imgur.com/FV7wDQE.png'
canonical_url: null
published: true
series: Theoretical Insights
id: 1556957
date: '2023-09-12T22:47:54Z'
---

## Apresentação

Linguagens são formas de *comunicação* bem estruturadas. Grosso modo, a comunicação se dá pelo envio de informação entre indivíduos: o *emissor* envia uma mensagem ao *receptor* que a recebe e *processa*. Dito isso, linguagens são formas de transmitir a informação seguindo *regras* pré-estabelecidas. Todos os animais, de uma ou outra forma, se comunicam entre si. No entanto, o uso de linguagens (isto é, de uma comunicação estruturada) é um dos critérios que diferencia nós, humanos, dos outros animais. 

Na comunicação entre animais, os "indivíduos" são sempre outros animais. O homem foi capaz de criar linguagens que permitem a comunicação não somente entre humanos, mas entre indivíduos denominados de *máquinas*. Estes, por sua vez, podem ser objetos inanimados formados de componentes físicos (como *hardwares*), ou mesmo construções abstratas, que não necessariamente existem aqui na Terra, mas apenas enquanto ideias ou conceitos. Veja até onde fomos: 

* *podemos falar da comunicação, de forma estruturada, entre indivíduos que não existe concretamente*!   

Tem-se diferentes tipos de linguagens, como as linguagens naturais, as linguagens de máquina, as linguagens formais e as linguagens de programação. Todas elas, no entanto, dividem diversas características, as quais discutimos em seguida.

## Sintaxe, Gramática e Semântica

Independentemente do seu tipo, linguagens são construções humanas. Isso significa que elas são *construídas* a partir de blocos fundamentais seguindo-se regras bem definidas. O que muda de um tipo de linguagem para outra **não** é a estrutura subjacente, mas sim a natureza dos blocos fundamentais e das regras utilizadas na construção da linguagem. De fato:  

1. parte-se de símbolos fundamentais, os quais definem o *alfabeto* da linguagem;
2. então se dita como símbolos devem ser unidos para formar palavras;
3. e como palavras se unem para formar frases;
4. e assim sucessivamente.

Ao conjunto das regras que ditam como construir palavras a partir de símbolos, frases a partir de palavras, etc., dá-se o nome de *sintaxe* da linguagem. Por sua vez, diz-se que os símbolos, as palavras e as frases propriamente ditas constituem sua *gramática*.

Observemos, no entanto, que linguagens **não** são meras construções. Afinal, elas possuem um objetivo claro: o da comunicação, e a comunicação só se concretiza quando a mensagem passada admite algum *significado* para aquele que a recebeu. Muitas vezes, no entanto, uma mesma mensagem pode admitir diferentes significados:

*  para um mesmo receptor, dependendo do *contexto* no qual a mensagem está inserida;
*  para diferentes receptores, dependendo do *contexto* no qual o receptor está inserido.

Sendo assim, dependendo do *contexto*, fala-se que uma mensagem recebe uma *interpretação*. Às diferentes maneiras de se interpretar as construções de uma linguagem (isto é, suas palavras, frases, etc.), dá-se o nome de *semântica*.

Desta forma, em poucas palavras, pode-se dizer que estudar uma linguagem consiste em:

* *construí-la*, o que é feito fornecendo símbolos e uma sintaxe, a partir da qual se obtém sua *gramática*;
* *interpretá-la*, que significa associar à sintaxe/gramática um significado concreto (ou abstrato - veja abaixo), o qual define sua *semântica*. 

De forma ainda mais resumida:

* *estuda-se uma linguagem através de sua sintaxe, gramática e semântica*.


## Tipos de Linguagem

Como comentamos, o que diferencia os tipos de linguagens não é a estrutura subjacente (admitir uma sintaxe, uma gramática e uma semântica), mas sim a *natureza* daquilo que compõe sua estrutura. Uma diferença, em particular, é especialmente interessante: a natureza das regras definidas pela sintaxe para se construir a gramática. Segundo tal critério, as linguagens podem ser divididas em dois tipos:

* *Linguagens Naturais*. Nelas, as regras da sintaxe são definidas por convenções sociais e agrupadas naquilo se chama de *dicionários* e *livros gramaticais* (também chamados simplesmente de *gramáticas*). Ao se aprender uma nova língua, olha-se em gramáticas para saber quais palavras existem, como formar frases, etc. Por sua vez, olha-se no dicionário para saber o significado social associado a cada uma dessas palavras definidas na gramática.
    * Português, Inglês e outras línguas definem linguagens naturais. 
* *Linguagens Formais*. Em contrapartida, em *linguagens formais* as regras da sintaxe (isto é, as regras que definem como se formam palavras válidas, frases, etc.) são dadas não por convenções sociais, mas por fórmulas de alguma *lógica*. Existem diferentes tipos de lógica e, para cada uma delas, um tipo diferentes de linguagem formal.
    *  Linguagens utilizadas dentro da Matemática e da Computação são exemplos de linguagens formais.

Lembre-se que em uma comunicação por meio de linguagens, os humanos não são os únicos indivíduos: tem-se, também, as *máquinas*. Desta forma, pode-se classificar as linguagens também com respeito ao tipo de indivíduo envolvido na comunicação:

* *Linguagens Humanas*. Tratam-se, pois, daquelas utilizadas na comunicação humano-humano;
* *Linguagens de Máquina*. São aquelas em que ao menos um indivíduo não é um humano, mas sim uma máquina.

Linguagens de máquina são tipicamente formais, enquanto que linguagens humanas podem ser formais ou naturais. Antes do avanço da Inteligência Artificial, linguagens naturais só eram processadas por humanos, o que as caracterizava, necessariamente, como linguagens humanas. No entanto, com a evolução do Processamento de Linguagens Naturais ([Natural Language Processing](https://en.wikipedia.org/wiki/Natural_language_processing)) e com o desenvolvimento dos Modelos de Grandes Linguagens ([Large Language Models](https://en.wikipedia.org/wiki/Large_language_model)), torna-se possível, ainda que de maneira limitada, a comunicação entre humanos e máquinas por meio de linguagens naturais.


## Linguagens de Programação

No início da texto, comentamos que "máquinas" podem ser objetos concretos, formados de componentes físicos (como hardwares) ou mesmo abstrações que, a princípio, existem apenas enquanto conceitos criados pelo homem. Um exemplo de tal diferenciação entre "máquinas concretas" e "máquinas abstratas" se dá no uso de recursos naturais: a energia em nosso universo é *finita*. Portanto, algo criado pelo homem só pode consumir uma quantidade *finita* de energia. 

Em uma *máquina concreta*, leva-se esse ponto em consideração: seus componentes devem ser tais que consumam somente *finitos* recursos. No imaginário humano, no entanto, podemos pensar em máquinas que não satisfazem tal premissa básica do universo. Estas, em tese, poderiam consumir recursos *indefinidamente*. A elas dá-se o nome de *máquinas abstratas*.

Tipicamente se dá o nome de *computador* a uma máquina concreta. Linguagens de máquina que envolvem computadores (isto é, quando algum dos indivíduos é uma máquina concreta, cujos componentes consomem uma quantidade finita de energia) são então chamadas de *linguagens de computadores*.

Ao se querer enfatizar que uma linguagem de máquina envolve a comunicação de máquinas que não são necessariamente concretas (isto é, quando não se leva em consideração o consumo de energia), fala-se, então, de *linguagens de programação*. Desta forma, linguagens de computadores são exemplos de linguagens de programação. 

Existem muitas outras classificações e subtipos de linguagens de programação. Por outro lado, assim como os diferentes tipos de linguagens (naturais, formais, humanas, de máquina, etc.) admitem a mesma estrutura (gramática, sintaxe e semântica), as diferentes classes de linguagens de programação possuem muitos aspectos em comum. A área de estudo que estuda tais aspectos em comum é chamada de Teoria das Linguagens de Programação ([Programming Language Theory](https://en.wikipedia.org/wiki/Programming_language_theory)). Conhecer um pouco dela significa *aprender sobre* ***todas*** *as linguagens de programação ao mesmo tempo*!


