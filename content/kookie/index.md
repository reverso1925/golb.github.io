+++
title = "a alternativa legalmente duvidosa ao twitter."
date = 2024-07-18
updated = 2024-07-21
+++

> "Nunca atribua à malícia o que pode ser adequadamente explicado pela burrice."
> 
> _(Robert J. Hanlon)_

por mais que o título e a epígrafe sejam bem provocativos, eu queria falar a respeito de um servidor/instância de misskey que surgiu repentinamente e anda causando uma pequena comoção por aí: [kookie.app](https://kookie.app/).

inicialmente, eu fiquei contente em ver um servidor brasileiro usando misskey, um programa que permite qualquer um hospedar sua própria rede social.

eu pessoalmente não conheço nenhum (se você hospeda um, me manda um e-mail e eu adiciono aqui) e é parte do motivo de eu recomendar geralmente o [shonk.social](https://shonk.social/)[^1] para as pessoas que eu incomodo rotineiramente para conhecer as maravilhas do activitypub.

o que me incomodou, de cara, foi uma prepotência cômica dos administradores da instância:

{{ picture( name="sobre", alt="uma screenshot da página 'sobre' do kookie no momento dessa publicação, indicando que o website é fornecido por uma empresa chamada Kookie Tecnologia Ltda." ) }}

eu não faço ideia do que esses caras realmente fazem, mas é muito engraçado você ter um CNPJ para administrar uma instância com...

```json
"usage": {
    "localComments": 0,
    "localPosts": 44995,
    "users": {
        "activeHalfyear": null,
        "activeMonth": null,
        "total": 414
    }
},
```

... 414 usuários.

além disso, chamou atenção a versão que eles usam: 2024.6.6.

a última atualização do misskey foi 2024.5.0, o que indica que eles estão usando uma modificação do software original. realmente, por mais que o serviço se comporte exatamente como o misskey, eles orgulhosamente anunciam que o software utilizado é o 'kookie'.

```json
"software": {
    "homepage": "https://kookie.app",
    "name": "kookie",
    "version": "2024.6.6"
},
```

agora a história começa a ficar divertida.
# problemas de licença

> para não-desenvolvedores: 
> 
> a licença de um software é basicamente a garantia de direitos autorais de quem o programou. é um contrato jurídico escolhido pelos desenvolvedores que permite a cooperação voluntária e apresenta as liberdades e restrições para seu uso.
>
> a AGPL — licença do misskey — exige que o kookie disponibilize seu código-fonte e que ele perpetue a licença AGPL. 
> 
> ou seja, você não precisa pagar para utilizar o misskey, hospedá-lo ou modificá-lo. a única exigência é que o website apresente um link de download para as modificações feitas pelo kookie ao misskey. 
> 
> isso acontece para que os desenvolvedores originais (do misskey) possam atestar que não há vírus ou vulnerabilidades, e também para que eles sejam devidamente creditados.
>
> minha única vontade é denunciar o uso indevido de código da mesma forma que um grupo de artistas denuncia _tracing_ ou uma repostagem de arte sem créditos. não pôr as modificações é como negar creditar um artista quando ele o pede.
>
> essa mesma situação já ocorreu com a rede social truth social — que será mencionada — por modificar o mastodon sem hospedar seu código. a diferença aqui é que eles responderam [hospedando seu código](https://help.truthsocial.com/legal/open-source/), enquanto o kookie [nega sua responsabilidade](https://archive.ph/dS6TY).
>
> _atualização — 21 de julho de 2024_

o programa original, misskey, atua com uma licença de código aberto chamada [AGPL](https://www.gnu.org/licenses/agpl-3.0.pt-br.html), a qual — justiça seja feita — permite a modificação e distribuição tanto comercial quanto sem fins lucrativos. no entanto, a licença exige explicitamente que você informe os usuários das alterações feitas e os permita modificar a sua versão do programa.

aqui está o problema: as menções ao código-fonte na página 'sobre' e a [homenagem aos verdadeiros desenvolvedores do projeto](https://misskey.io/about-misskey)[^2] foram removidas na versão do kookie; uma mudança que, superficialmente, parece intencional e maliciosa, pois lembra do [caso Truth Social](https://blog.joinmastodon.org/2021/10/trumps-new-social-media-platform-found-using-mastodon-code/), a rede social do donald trump.

além disso, os [termos de uso](https://kookie.app/@kookie/pages/termos) do website são proprietários e não refletem de forma alguma a AGPL, exigência da licença. não me assustaria se aquele CNPJ recebesse algum tipo de notificação dos desenvolvedores originais.

outra coisa que me incomodou bastante, além do óbvio disfarce, são as comuns menções a um 'aplicativo nativo' que está sendo desenvolvido.

{{ picture( name="kimis", alt="publicação de @lucas@kookie.app: 'Estamos passando novamente por um processo de avaliação pela playstore. Aproveitando o momento para informar que temos dois tipos de aplicativos em desenvolvimento, temos o app baseado na versão do kookie web que será lançado temporariamente e temos os aplicativos nativos. Os nativos são mais difíceis de serem desenvolvidos e requer mais tempo e recursos financeiro, mas são mais otimizados e possui uma experiência de usuário melhor.  
Abaixo as imagens de comparativos entre a versão nativa e web' as imagens mostram o app kimis e a interface web do kookie." ) }}

duas coisas se destacam:

- a mais óbvia é que essa screenshot é do aplicativo [kimis](https://apps.apple.com/br/app/kimis-a-client-for-misskey/id1667275125)[^3]. caso eles estivessem apenas usando o kimis como exemplo de um aplicativo nativo que pode ser utilizado, eu imagino que a autoria do app seria mencionada e eles possivelmente teriam um guia de como acessá-lo com o kookie.
- a outra é o 'processo de avaliação da playstore'. pela falta de transparência por parte da equipe, é preocupante a ideia de que eles estejam, novamente, fazendo rebranding de um programa desenvolvido por voluntários.

eu realmente espero que o aplicativo seja um programa original ou, no mínimo, seja transparente a respeito da licença.
# o experimento fediverso
é engraçado que eu não tenha falado tanto, nesse blog, sobre o fediverso; então eu preciso fazer uma pausa. 

eu aprendi, depois de tentar explicá-lo centenas de vezes, que a melhor maneira de fazer isso é a mais simples, sem entrar em detalhes técnicos e tudo mais.

basicamente, "fediverse" é um conceito informal e não oficial que se refere a uma ampla rede social que inclui quaisquer aplicativos que utilizem um protocolo chamado _activitypub_ (um nome que você não precisa saber), os quais conversam entre si. 

ele inclui várias redes sociais que você nunca ouviu falar como [mastodon](https://joinmastodon.org/pt-BR/servers), [misskey](https://misskey-hub.net/en/servers/), [akkoma](https://akkoma.social) e [peertube](https://joinpeertube.org) — que, ainda, se distribuem em diversas "instâncias"; sendo o kookie uma instância do misskey — e já recebeu atenção do [threads](https://engineering.fb.com/2024/03/21/networking-traffic/threads-has-entered-the-fediverse/) e do [tumblr](https://techcrunch.com/2023/12/11/tumblrs-fediverse-integration-is-still-being-worked-on-says-owner-and-automattic-ceo-matt-mullenweg/). você pode acompanhar o crescimento da rede pelo projeto voluntário [fedidb](https://fedidb.org).

parece com email: você tem outlook, seu amigo tem yahoo. não importa: funciona.

de qualquer forma, como o kookie é inteiramente baseado no misskey, eles podem apenas apertar um botão e habilitar essa conexão. foi o que eles fizeram, e durou pouco:

a primeira coisa que a ampla rede percebeu foi os problemas de licença, os quais são _extremamente_ mal vistos por qualquer desenvolvedor que se preze.

por isso, alguns gringos começaram a questionar os desenvolvedores. a resposta foi, em português: "Nós tornaremos nossa fonte disponível quando terminada. Nós estamos implementando IA e algoritmos personalizados, logo não fizemos a fonte disponível."[^4]. 

em primeiro lugar, isso não justifica nada; é questão de minutos você pegar a pasta do código, colocar em um _zip_ e servir no website. 

em segundo lugar... IA e algoritmos... sério?

quando perceberam que o kookie não tinha intenção de dar os créditos a ninguém, o servidor foi floodado com copypastas aleatórias. depois disso, a integração foi desligada. ok.
# a primeira iteração
depois de pesquisar a respeito, eu também descobri que o site já havia passado por uma primeira versão, no ano passado, que chegou a 18 mil usuários.

pelas [screenshots disponíveis](https://www.breaktudo.com/conheca-o-kookie-nova-rede-social-microblogging/) do período, é possível ver a interface do [soapbox](https://soapbox.pub), então acredito que o intuito do projeto sempre tenha sido manter um servidor de outro serviço, apenas modificando o rótulo do website.

também havia um aplicativo na play store, que já foi retirado. na verdade, parece que era só um web-app. ou seja, a versão de navegador rodando por um aplicativo.

o que realmente me interessou foi que a rede teve um certo alcance (maior do que qualquer servidor brasileiro do mastodon, por exemplo), e eu imagino que haja uma parte dos brasileiros que — mesmo estando descontente com a direção do twitter — ainda não conseguiu romper a bolha das redes sociais tradicionais e permanece nesse meio-termo entra elas e as redes federadas.

realmente me incomoda que esse vácuo tenha dado tanto poder a uma rede que não tem responsabilidade.
# e as pessoas?
o fator central de qualquer rede social é os usuários. por isso, analisar o vaivém do kookie sem observar a demográfica e público alvo é impossível. 

eu interagi com a rede pelo fediverso enquanto a federação deles ainda estava ativada e também tive a oportunidade de assistir a uma livestream da [yvis](https://www.twitch.tv/yvissaintlaurent), onde pude interagir com mais pessoas.

a mais pura verdade é que as pessoas que participam dessa rede são genuinamente queridas, acolhedoras e formam uma comunidade que lembra muito, culturalmente, o fediverso brasileiro. a _vibe_ no geral vinha do mesmo sentimento contra bots, propagandas, assinaturas e quaisquer outros mecanismos de monetização de plataforma que os tornaram refugiados do twitter.

no entanto, a regência da rede — a qual tenta esconder ao máximo todas as indicações de que o software não é original — me impede de acreditar que eles estejam a hospedando sem nenhum interesse econômico, como fazem [diversas instâncias do mastodon](https://manualdousuario.net/mastodon-instancias-brasileiras/). 

essa vontade explícita de cercear a experiência do fediverso e não aderir aos acordos de bom senso dos desenvolvedores indicam uma ausência do companheirismo característico da iniciativa de software aberto.

se eu fosse prever o futuro da plataforma, eu o enxergo assim: ou os desenvolvedores reconhecem a licença do código que eles usaram, passam a ser transparentes com os usuários, habilitam novamente a conexão com a ampla rede e permitem a migração de contas para outras plataformas; ou ela continuará recebendo críticas daqueles envolvidos com seu desenvolvimento, não conseguirá se abrir novamente e será lentamente consumida pela mesma fome de capital que contaminou o twitter. 

eu sei qual seria melhor para os usuários. ; )

[^1]: o shonk.social roda sharkey, que é uma modificação do misskey. vai ficar menos confuso, eu prometo, mas por enquanto só compare a página "explorar" dos dois servidores: [aqui](https://shonk.social/explore) e [aqui](https://kookie.app/explore). aliás, agora eu consigo adicionar notas de rodapé. legal, vou usar toda hora.
[^2]: existem diversos servidores do misskey. eu peguei o do misskey.io porque é o mais comum de ser compartilhado quando se trata da versão original do software. esse indicador aparece na grande maioria dos servidores. 
[^3]: qualquer usuário do kookie pode usar apps feitos para o misskey, como o [takesama](https://takesama.com) e o [kaiteki](https://kaiteki.app).
[^4]: [citação completa](https://social.nano.lgbt/notes/9vgax1v9b0uuiojl): "We will make our customized source available when it is finalized, we are implementing AI and personalized algorithms, so no source has been made available yet, do you understand?"
