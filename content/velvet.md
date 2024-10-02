+++
title = "dedicação e satisfação."
date = 2022-12-16
update = 2023-03-27
+++

em dezembro do ano passado, em um hotel, eu tive uma ideia. era um momento de relaxamento e calma: eram as férias. mesmo assim, essa ideia consumiu meus pensamentos e eu não consegui esperar. eu instalei o [obsidian](https://obsidian.md/) no celular para documentar o projeto do início ao fim.

a ideia veio da dificuldade de administrar os diversos mods de minecraft que são comumente instalados para lidar com o desempenho do jogo. quem jogou minecraft moderno sabe que além de instalar o fabric, é necessário manter-se informado sobre o ecossistema de mods de otimização do jogo, principalmente após a queda do optifine. para pessoas que querem apenas jogar o jogo, essa dinâmica não é ideal. 

o objetivo principal era instalar o fabric e organizar os mods em pastas separadas pela versão do jogo para que o usuário possa, simultaneamente, manter diversas instalações com suas respectivas pastas de mod.

no início, eu não tinha acesso ao computador e não podia testar código algum ou colocar meus pensamentos em prática. uma consequência interessante disso foi que pude conceitualizar o projeto inteiro antes de escrever o código.

eu sabia que queria os meus mods na estrutura `.minecraft/.woven/mods/<versão>`. o nome do subdiretório `.woven` é derivado de fabric: um nome apropriado para o projeto.

o fabric sempre lê os mods na pasta `.minecraft/mods`, então teria que ser modificado para lidar com a pasta de mods dinamicamente. daí veio a primeira dificuldade: programar em java. eu tenho pouca experiência com java, mas como seria um pequeno _patch_ no código, eu pensei que seria simples o suficiente.

meus três objetivos iniciais foram definidos: modificar o fabric, instalá-lo e baixar os mods.

uma vantagem de dividir as etapas antes de começar a programar é que você fica preso às ideias originais e não começa a adicionar funções novas com o tempo.
# em prática
eu comecei a programar o programa em rust, essa escolha foi definida desde o início do projeto. modificar o fabric seria simples. em sua inicialização, ele já sabe a versão na qual o jogo está rodando. o maior problema foi na instalação.

o launcher do minecraft trabalha com json. a biblioteca [serde](https://serde.rs/) possui todas as ferramentas necessárias para lidar com as principais estruturas de dados. porém, eu senti medo porque todos os exemplos da biblioteca tinham muitas coisas que eu ainda não havia aprendido. por causa disso, eu deixei o projeto de lado.

em novembro, pouco mais de nove meses depois, eu lembrei do projeto e continuei de onde tinha parado. porém, pelo intervalo de tempo, algumas coisas mudaram.

primeiro, um _fork_ do fabric, [quilt](https://quiltmc.org), implementou a função de passar uma pasta de mods dinâmica usando apenas opções da jvm. por causa disso, eu optei pelo quilt porque, então, não precisaria manter minha própria modificação do fabric e um maven para distribuição.

segundo, eu descobri um projeto com o nome "[wovenmc](https://github.com/wovenmc)" e decidi mudar para "velvet".

por fim, eu escrevi toda a instalação do quilt e usei a biblioteca [ferinth](https://crates.io/crates/ferinth) para comunicar com o api do modrinth, uma plataforma de mods que amadureceu durante o ano, e instalar os mods.
# conclusão
é interessante pensar que eu demorei quase um ano para trazer uma pequena ideia à vida. às vezes, abandonamos projetos porque nos vemos longe demais de concluí-los.

meu principal relato é que o sentimento de retomar um projeto com conhecimento e energia suficiente para terminá-lo é muito gratificante.

por causa disso, documentar o processo é uma etapa importante. a principal vantagem dessa experiência foi manter comigo minhas anotações do início até o final.

o código do projeto está disponível [aqui](https://github.com/derspyy/velvet).