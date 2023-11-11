---
title: Por que estudar teoria?
description: 'Nesse post, apresento alguns argumentos que corroboram para a tese de que, na verdade, ter uma boa bagagem teórica pode implicar diretamente em uma melhor performance como desenvolvedor'
tags: 'theory, study, programming, thinking'
cover_image: 'https://i.imgur.com/H6nuc66.png'
canonical_url: null
published: true
series: Theoretical Insights
id: 1558373
date: '2023-08-03T22:59:29Z'
---

Introdução
------

Oi. 

Essa é a primeira postagem da coluna *Theoretical Insights*. Nela pretendo apresentar, de maneira intuitiva e menos formal, alguns aspectos teóricos ligados à programação. Ao longo de vários artigos, responderemos perguntas como:

* o que, de fato, define uma linguagem de programação?
* como funciona o processo de compilação?
* o que são algoritmos?
* o que é uma máquina?
* como funcionam os computadores?

Mas, 

* por que um desenvolvedor de software deveria fazer algo para além de resolver problemas concretos e de estudar novas tecnologias?
* por que dedicar parte de seu tempo tentando compreender aspectos teóricos que, no dia a dia, aparentam ser irrelevantes?

Inicio esta coluna apresentando alguns argumentos que corroboram para a tese de que, na verdade, ter uma boa bagagem teórica pode implicar diretamente em uma melhor performance como desenvolvedor.

Independência da Linguagem
-----

Desenvolvedores se especializam em linguagens de programação, o que faz com que consigam refletir de maneira bastante intrincada em sua linguagem de especialização. No entanto, diferentes linguagens são construídas com diferentes propósitos e, dependendo da situação, seria mais interessantes construir algo em uma linguagem distinta daquela na qual se está habituado. Como proceder?

Linguagens de programação implementam algoritmos. Uma linguagem é dita ser *completa* ([Turing complete](https://en.wikipedia.org/wiki/Turing_completeness)) se é capaz de implementar todos os algoritmos realizáveis em um computador moderno (isto é, em uma [Turing machine](https://en.wikipedia.org/wiki/Turing_machine)). Fato é que as linguagens de programação de alto nível e mais utilizadas no meio corporativo, como `C`, `C++`, `Java`, `C#`, `JavaScript`, `Python`, `Go`, `Ruby`, `Rust`, etc., são completas. Isso significa que, em termos da capacidade de implementar algoritmos, todas elas cumprem o mesmo papel. Isso também significa que existe uma maneira de se pensar e construir soluções que é independente da linguagem de programação a ser utilizada. A saber, através de *algoritmos*.

* **Conclusão.** *Entender melhor o que é uma linguagem de programação e o que são algoritmos nos permite desenvolver a capacidade de resolver problemas que independam de uma dada linguagem de programação.*

Otimização
-----

Ao se trabalhar com desenvolvimento de software, lida-se, diariamente, com a construção de soluções para problemas. Às vezes não paramos para pensar, mas um mesmo problema pode admitir diferentes soluções. Julgo que uma das características que demonstram a senioriedade de um desenvolvedor é conseguir olhar para o leque de possíveis soluções de um dado problema e saber decidir, baseado em critérios previamente estabelecidos, qual a solução é a mais adequada. Mas, como fazer isso de maneira sistemática?

Escolher *a melhor* dentre um conjunto de possibilidades é um problema de *otimização*. Como comentado, linguagens de programação implementam algoritmos. Fato é que existem áreas de estudo devotadas ao problema de análise e otimização de algoritmos, como a *Teoria da Complexidade Computacional* ([Computational Complexity Theory](https://en.wikipedia.org/wiki/Computational_complexity_theory)) e a *Análise de Algoritmos* ([Analysis of Algorithms](https://en.wikipedia.org/wiki/Analysis_of_algorithms)).

* **Conclusão.** *Estudar sobre a teoria dos algoritmos nos dá critérios objetivos para decidir, dentre uma gama de possíveis soluções, qual é que melhor se adapta a uma dada demanda*.

Inovação
-----

Para pensar em buscar pela solução otimizada, precisa-se, antes, conhecer o leque de possíveis soluções. Algumas soluções tendem a ser mais óbvias que outras e, não raro, a solução mais adequada é altamente não-trivial. Ser não-trivial é ser inesperado, e ser inesperado é ser inovador. Ao se trabalhar mergulhado em uma linguagem de programação específica, tende-se a construir soluções que mais se adequam aos objetivos e características da própria linguagem, o que naturalmente diminui o leque de possíveis soluções a serem observadas.

* **Conclusão.** *Se desprender de uma dada linguagem e pensar de forma mais abstrata abre horizontes e possibilita a construção de soluções inovadoras.*

Visão Panorâmica
-----

Tornando-se especialista, dá-se um zoom em toda a gama de conhecimentos e passa-se a concentrar em assuntos restritos e a assuntos fortemente relacionados a eles. Ao se estudar aspectos teóricos e fundamentalistas, diminui-se um pouco esse zoom, permitindo uma observação mais panorâmica dos problemas extremamente especializados que se estava lidando. Uma visão mais abrangente é menos enviesada e permite, por exemplo, observar conexões entre assuntos e problemas que antes não se via. Talvez a solução que se busca já exista, mas seja adaptada a um problema em um tópico ligeiramente distante, o qual não poderia ser observado em um zoom muito grande.

*  **Conclusão.** *Estudar teoria fornece uma visão abrangente, a qual possibilita a adaptação de soluções já existentes para problemas de outras áreas.*


Não-Linearidade do Aprendizado
-----

Por fim, gostaria de dizer que, diferentemente do que é exposto em livros técnicos e na estrutura de cursos de graduação, o aprendizado não se dá de forma linear. Existe um campo devoto ao estudo da construção do conhecimento, chamado de [Epistemologia](https://pt.wikipedia.org/wiki/Epistemologia), o qual se origina na Filosofia e se intersecta com outras áreas como a Psicologia. 

Uma das questões epistemológicas é como se dá o aprendizado. Existem diversas teorias e vários modelos educacionais associadas a elas. Uma delas, pela a qual tenho grande apreço, é a *Teoria do Aprendizado por Descobertas*, de Jerome Bruner ([Discovery Learning](https://en.wikipedia.org/wiki/Discovery_learning), em inglês), cujo modelo educacional é não-linear baseado em um formato espiral. Nele, não se torna especialista em algo, para então se tornar especialista em outro algo, e assim sucessivamente (perspectiva linear). Ao contrário, aprende-se de maneira efetiva tendo uma visão inicialmente rudimentar do todo (primeira volta da espiral), e então revendo o todo com maior profundidade e abstração (segunda volta da espiral), e assim por diante.

![linear vs espiral](https://i.imgur.com/SXp1KcA.png)

Em outras palavras, segundo esta perspectiva, uma aprendizagem efetiva é obtida partindo-se de uma visão generalista, e então retomando os diferentes assuntos por diversas vezes, cada vez com maior compreensão e profundidade.

Estudar aspectos teóricos e fundamentalistas é ir exatamente na direção de construir essa espiral do aprendizado, e as experiências e vivências adquiridas em cada volta certamente darão uma maior amplitude no momento de atacar um problema específico.

Fim
----

Fica a minha mensagem. 

Espero ter transmitido a ideia de que ao se descer do mundo dos códigos especializados e estudar um pouco de teoria, tem-se a possibilidade de obter ferramentas poderosas que o tornarão um profissional capaz de pensar fora da caixa, propor soluções otimizadas e ideias inovadoras. Pode parecer perda de tempo, mas é um investimento.

Obviamente não estou dizendo que aprender habilidades técnicas especializadas não é útil ou necessário. Pelo contrário: digo que aliar o conhecimento técnico ao teórico tem o potencial de ampliar suas capacidades e seu desempenho enquanto desenvolvedor. 

No entanto, sinta-se à vontade para discordar do meu ponto de vista e contribuir nos comentários com suas vivências.

Um abraço e até mais,

Yuri.
