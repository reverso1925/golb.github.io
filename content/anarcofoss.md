+++
title = "open source é essencialmente anarquia."
date = 2023-10-28
+++

software de código aberto (open source software) é todo software cujo código é distribuído livremente acompanhado de uma licença que segue a definição da [open source initiative](https://opensource.org/osd/), principalmente:

1. distribuição livre.
2. disponibilidade do código-fonte.
3. derivações na mesma licença.

essas regras permitem que o software seja desenvolvido, aprimorado, auditado e estudado por qualquer um.

> o [linux](https://www.linuxfoundation.org/), [chromium](https://chromium.org/) (a base dos navegadores chrome, brave, opera, vivaldi e edge), [firefox](https://mozilla.org/firefox), [libreoffice](https://pt-br.libreoffice.org/), [vim](https://www.vim.org/) e [esse site](https://git.envs.net/piuvas/piuvas.net) são exemplos de software aberto.

isso já seria o suficiente para categorizar esse método de desenvolvimento e distribuição de software como fundamentalmente da esquerda, mas analisando com paciência a evolução desses projetos e suas comunidades, fica clara uma conexão com o movimento libertário.

a iniciativa de código aberto como uma alternativa ao desenvolvimento de software proprietário já é um indicativo dos seus objetivos: democratizar o software. além disso, o desenvolvimento de "alternativas livres" para o software existente (como o libreoffice, que compete com o microsoft office) pressiona os monopólios a adotarem recursos que favorecem o consumidor: o software aberto se move rápido e não custa nada.

ser anti-capitalista não significa de forma alguma ser anarquista, mas é fácil identificar conceitos libertários na filosofia open source:
# autogestão
na maioria das vezes, esses aplicativos surgem por pura necessidade — tanto de praticidade quanto de um nicho ainda não explorado pelo silicon valley — e como projetos pessoais. assim, você mantém controle completo da direção do seu projeto e as prioridades nas decisões são sempre a experiência de usuário e simplicidade. além disso, outras pessoas terão essa mesma mentalidade para participar do desenvolvimento.

você pode começar um projeto para aprender uma linguagem de programação nova ou para solucionar um problema extremamente específico e mostrar a um fórum ou grupo — seja por conselhos, suporte, divulgação — e se deparar com alguns usuários e contribuintes cujas decisões também seguem a mesma filosofia. 

em pouco tempo, uma biblioteca livre pode ser utilizada por diversos programas de múltiplos desenvolvedores que contribuem de volta com mudanças que os beneficiam e logo forma-se uma rede de software intrinsecamente ligada pela boa-vontade de diversos engenheiros que trabalham juntos para a formação de um ecossistema.

ambientes de trabalho (_desktop environments_) no linux são exemplos de coletivos de software que compartilham escolhas de design e bibliotecas nativas e esses conjuntos demonstram como uma coisa pode ser construída sobre a outra de forma organizada enquanto são mantidas filosofias originais (conforto e limpeza no gnome, modernidade e customização no kde e desempenho no xfce, por exemplo).
# liberdade de associação
qualquer pessoa que resolver aderir ao projeto, o fará por pura vontade de contribuir e melhorar a própria experiência e, consequentemente, dos demais. como é essa contribuição, na prática? conheça o _forking_: a maioria dos sistemas de controle de versões (vcs) — como o [git](https://git-scm.com/) e... o [mercurial](https://www.mercurial-scm.org/)? — separam o código-fonte em uma espécie de histórico de mudanças. então o código, de qualquer ponto da história, pode divergir de maneira independente por alterações de qualquer um. 

o contribuidor então pode apresentar suas mudanças para o projeto original (conhecido como _pull requesting_) ou manter as mudanças independentes (como foi o [caso](https://codeberg.org/tenacityteam/tenacity#motivation) do editor de áudio [audacity](https://www.audacityteam.org/)).

não importa quem mantém o repositório principal (o tronco): ninguém é proprietário do código. a única garantia de um colaborador é que suas contribuições estarão para sempre preservadas em toda distribuição do código, suas manifestações de preocupação estarão preservadas nos fóruns e o nome de quem apaziguou conflitos nos chats do projeto será lembrado. 

a linguagem de programação rust possui uma governança extremamente descentralizada, dividida em sub-times e a entrada de ideias é feita por rfc's (_requests for comments_ ou solicitações de comentários) onde a apresentação de ideias pode moldar substancialmente o tronco do projeto. mesmo que uma hierarquia seja formada, como nos sub-times, ela se forma organicamente a fim de representar os interesses comuns, visto que eles podem ser dissolvidos em qualquer ramificação da comunidade.
# ajuda mútua
participar de um projeto open source, seja com código, documentação, organização de redes sociais e fóruns, cargos comunitários (como redes sociais e _troubleshooting_), ajuda a contribuidores ou apenas bate-papos dentro da comunidade, é uma experiência libertadora.

é muito comum alguém entrar em uma comunidade para tirar uma dúvida e acabar com um interesse em outras partes do projeto e, enfim, acabar contribuindo diretamente ao código. além disso, o mercado de programação é repleto de _crunching_, prazos apertados e a manutenção de código antigo, e os cursos refletem essa realidade. 

a realidade é que aprender como um _hobby_, por curiosidade e pura vontade de cooperação, com a companhia de fluentes no código-fonte e a apreciação coletiva do uso prático do saber (participar de um projeto _real_), forma programadores eficientemente realistas e com uma mentalidade libertária. essa é a pedagogia anarquista, facilmente paralela à "[la ruche](https://bibliotecaterralivre.noblogs.org/editora/a-colmeia/)".

além da educação, a colaboração é uma etapa intrínseca do desenvolvimento aberto, e em conjunto com a associação de pessoas genuinamente interessadas, torna projetos de paixão em experiências comunitárias incríveis que criam relacionamentos e unem pessoas com mentalidade coletiva para a formação de uma nova frente do desenvolvimento tecnológico. 

apenas ser um usuário é uma ajuda enorme para desenvolvedores independentes e é extremamente interessante conhecer projetos de código aberto para descobrir uma nova onda de problemas que estão sendo solucionados e paixões que estão nascendo.
# enfim...
programadores ainda vivem em um mundo capitalista: não importa quão útil seu aplicativo ou o quão adotada sua biblioteca seja, [você não vai receber comida na porta](https://docs.google.com/document/d/1kiW9qmNlJ9oQZM6r5o4_N54sX5F8_ccwCy0zpGh3MXk/edit). e defender o movimento de código aberto, agora, significa garantir que esses desenvolvedores possam continuar trabalhando em seus projetos. por isso, é importante compartilhá-los como alternativas ao software proprietário, oferecer _feedback_ e participar das discussões que surgem a respeito deles.

por fim, aqui vai uma lista com projetos que substituem algumas ferramentas do dia a dia.

* navegador:
    * [firefox](https://www.mozilla.org/pt-BR/firefox/new/) - possivelmente o mais popular dessa lista.
    * [min](https://minbrowser.org/).
* mensagens:
    * [signal](https://signal.org/) - já falei dele no primeiro post!
    * [element](https://element.io/) - ou qualquer outro do [ecossistema matrix](https://matrix.org/ecosystem/clients/).
    * [revolt](https://revolt.chat/).
* arte:
    * [krita](https://krita.org/).
    * [gimp](https://www.gimp.org/).
    * [inkscape](https://inkscape.org/) - para design vetorial.
* notas:
    * [logseq](https://logseq.com/).
    * [joplin](https://joplinapp.org/).
* office:
    * [libreoffice](https://www.libreoffice.org/).
    * [cryptpad](https://cryptpad.fr/) - online!
    * [onlyoffice](https://www.onlyoffice.com/).
* mapa e direções:
    * [organic maps](https://organicmaps.app/).
    * [osmand](https://osmand.net/).
