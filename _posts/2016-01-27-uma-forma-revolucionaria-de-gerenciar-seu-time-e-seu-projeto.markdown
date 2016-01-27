---
layout: post
title:  "Uma forma revolucionária de gerenciar seu time e seu projeto"
image_list: /blog/src/img/2016-01-26-real-tree-card.jpg
comments: true
description: >
    Você conhece o Git? Para alguns é comum. Para outros nem tanto. Porém tenho certeza que, em ambos os casos, você vai ficar impressionado com o que ele pode fazer por você.
twitter_text: Esse post conta (e conta muito bem) o melhor do Git!
---

<q> Revolucionário? O Git? Que exagero! </q> Você pode dizer.

Sim. Eu também diria a mesma coisa. Já trabalho com o Git a mais de 2 anos e para mim ele se tornou uma simples ferramenta de trabalho. <strong>Indispensável</strong>, mas <strong>simples</strong>. Acontece que na sua simplicidade se esconde a força de sua complexidade.

Você provavelmente deve imaginar que muito pesquisei sobre Git antes de escrever esse post, a fim de entender melhor a dinâmica de seu funcionamento. De fato, li muitos textos antes de começar mais um, procurei imagens didáticas e rodei o mundo a procura de especialistas <small>sem a parte de rodar o mundo hehe</small>.

Porém, depois de achar um mundo de bons artigos, pensei o que faria o meu post único, de forma a manter a identidade do blog e, mais importante, que acrescentasse algo para o leitor.

E finalmente, depois de muito pensar <small>mentira, nem pensei tanto assim</small>, decidi seguir um rumo um pouco diferente. Este <strong>não será um post técnico</strong>, mas mais <strong>subjetivo</strong> e escrito com minhas próprias palavras e as abstrações que consegui fazer do funcionamento do Git.

<h2 class="image-title">Versionador</h2>
![pendrive versus git][image pendrive_git]

Imagine antigamente, antes dos <i>cloud services</i> <small>dropbox, box, drive, etc</small> existirem, como um time de desenvolvedores fazia para compartilhar as alterações feita por cada um no projeto?

Bom, se não compartilhavam por disquete ou CD, era no mínimo por pendrive, espetando o dito cujo em cada computador, juntando as alterações manualmente nos arquivos já existentes e depois anotando, talvez no notepad ou em um papel, o que mudou nessa nova <strong>versão</strong>.

Bom, com os serviços de compartilhamento atuais tudo ficou claramente mais fácil e natural. Basta colocar um projeto na nuvem, dar acesso a todos da equipe, e <i>voilà</i>, teremos mais ou menos um controle sobre todas as alterações e de forma um pouco mais fácil do que ficar espetando o bom e velho pendrive.

Tudo <strong>quase</strong> lindo.

Queremos uma ferramenta que nos dê controle <strong>total</strong> sobre todas as alterações, com informações contextuais que digam o que foi alterado, onde, quando, por quem, e porquê <small>ufa!</small>. Também queremos fazer isso da forma mais simples o possível, de forma que, por exemplo, eu consiga migrar entre diferentes dispositivos e sempre ter a <strong>versão</strong> mais atual do projeto.

Queremos atualizar, alterar, e gerenciar nossos projetos e nossa equipe de <a href="/blog/como-programar-de-qualquer-lugar-do-mundo/">qualquer lugar do mundo</a>, como citei nesse meu último post.

<span class="center-horizontal">
	![coffee and rain][image coffee_rain]
</span>

Sim, é isso tudo mesmo. Tão fácil quanto digitar 3 linhas de comando, ou dar 3 cliques, ou tomar um chocolate quente em um dia chuvoso.

Desde o início do projeto, temos esse controle todo. No começo pode parecer complexo, mas rapidamente tudo se torna <i>tão natural quanto a luz do dia</i> <small>mas que preguiça boa, me deixa aqui atoa <i class="fa fa-music"></i></small>. E a cada alteração, ou conjunto de alterações feitas ao projeto, podemos lançar o que chamamos de nova <strong>versão</strong> do projeto.

Esse é um dos trabalhos do Git, ser um <strong>controlador de versão</strong>. Isso facilita, por exemplo, retornar facilmente no tempo para recuperar um código perdido, ou testar se antigamente determinado erro já ocorria.

<h2>Árvore do projeto</h2>

<span>
	<span style="margin-right: 30px">
		![real seed][image real_seed]
	</span>
	<span>
		![git seed][image git_seed]
	</span>
</span>

Imagine como é plantar uma árvore.

Você escolhe um bom local, prepara o terreno, coloca adubo, e enfim coloca a semente.

Você tapa o buraco e dá uma simples regada. Você para e olha para a terra molhada no chão, vislumbrando no futuro como aquela árvore crescerá e se encherá de ramos, galhos e frutos.

Passa um tempo e, depois de muito trabalho, o <strong>tronco</strong> começa a crescer. Você fica maravilhado em como ela é jovem porém já tão robusta. <strong>Robusta e flexível</strong>.

<span>
	<span style="margin-right: 30px">
		![real trunk][image real_trunk]
	</span>
	<span>
		![git trunk][image git_trunk]
	</span>
</span>

E de repente, de forma muito rápida, os <strong>galhos</strong> começam a nascer e crescer. Se ramificam cada vez mais, e você precisa de mais pessoas para te ajudar a cuidar da árvore. Cada um cuida de uma parte, mas todos contribuem para o crescimento daquele corpo que está se formando.

As tempestades começam a aparecer e chacoalham os galhos, deixando-os confusos e desordenados. Parece que tudo vai ruir, mas ela aguenta firme, e o sol aparece de novo.

Então você para, e olha de novo para ela. Observa a tonalidade marcante que ela adquiriu. Orgulhoso de sua <small>e de tua</small> grandiosidade, respira fundo e pensa em todo o trabalho duro que ogirinou todos aqueles galhos.

<span>
	<span style="margin-right: 30px">
		![real tree][image real_tree]
	</span>
	<span>
		![git tree][image git_tree]
	</span>
</span>

Claro que os galhos dessa árvore que você plantou são meio doidos. Porque eles sempre acabam se juntando ao tronco de novo depois de um tempo, uns juntam com outros, ou até mesmo o tronco acaba se juntando com um determinado galho.

Claro, essa é a <strong>árvore do seu projeto</strong>. Me perdoem pela historinha, mas eu quis poetizar um pouco para mostrar como o Git trata cada elemento de um projeto, pensando nos detalhes e tornando tudo muito natural para você.

Se você sabe como é uma árvore, tudo será simples para você.

<h2>Árvore do projeto <small>de verdade</small></h2>

Bom, o Git mantém um <strong>repositório</strong> do projeto que guarda toda essa árvore de alterações. E <strong>primeiramente</strong>, tudo isso funciona de maneira <strong>local</strong>, na sua máquina.

<h4>commit</h4>
Cada alteração <small>ou um conjunto de</small> é salvo no repositório através do conhecido comando `git commit`. <i>Commit</i> é algo como enviar, entregar, executar.

E cada commit deve possuir uma mensagem <strong><u>auto</u>-explicativa</strong> dizendo o que foi alterado, como

 * "novo layout para os posts"
 * "melhorando organização do css"
 * "consertando bug de imagem em mobile"

Aos poucos, vai se formando o <strong>tronco</strong> do seu projeto.

<span class="two-images join">
	<span>
		![git trunk_2][image git_trunk_2]
	</span>
	<span>
		![git commit][image git_commit]
	</span>
</span>

Mas na prática, como é feito?

Suponha que você tenha alterado vários arquivos em duas pastas totalmente diferentes do seu projeto, e você quer criar um commit apenas com as alterações de uma pasta, e depois da outra, para manter as coisas organizadas.

<h4>add</h4>
Então, o Git tem um estágio antes do `commit`, que é o `add`. O, também famoso, comando `git add`, adiciona os arquivos desejados em uma espécie de <i>repositório temporário</i>, que o Git chama de <i>index</i>, ou índice.

O fluxo seria mais ou menos assim:

 * `git add caminho/para/arquivo.txt`
 * `git commit -m "comentario explicativo"`

O commit então manda <strong>todos</strong> os arquivos <small><img src="/blog/src/img/X-All-The-Y-icon.jpg"></small> adicionados no index para o repositório.

<span class="center-horizontal">
	![git push][image git_push]
</span>

<h4>status</h4>
Um comando muito também útil e usado é o <small>deixa eu adivinhar, famoso?</small> famoso comando `git status`. Na imagem você pode ver que <span class="highlight pre"><span class="na">verde</span></span> é o que está adicionado e pronto para o commit. O que está em <span class="highlight pre"><span class="nt">vermelho</span></span> é um arquivo que foi alterado, alteração que pode facilmente ser desfeita com o <small>um pouco menos famoso</small> comando `git checkout caminho/para/arquivo.txt`.

<h4>branch</h4>
Imagine agora que você está em um time de desenvolvedores e decide implementar uma nova funcionalidade no projeto. Naturalmente você alterará vários arquivos e fará vários commits. Durante esse tempo, outras pessoas da equipe também estão commitando e fazendo alterações. Virará tudo uma bagunça, certo?

E se seu chefe fazer algo que chefes nunca fazem, que é voltar a trás e pedir pra desfazer o que você já fez? Terá que ir olhando commit por commit, para identificar qual é relacionado, e depois fazer alguma mágica para sumir com eles do tronco.

Para isso existe o <strong>branch</strong>, ou, em mineirês, o <strong><i>gái</i></strong>.

Basta criar um branch novo `git branch branch_novo`, mudar para esse branch `git checkout branch_novo` e meter o pau. Você também pode unir os dois comandos fazendo `git checkout -b branch_novo`.

<h4>push</h4>
Por fim entra a <strong>nuvem</strong>, ou <strong>remote</strong>, um repositório online no qual nosso repositório local está associado.

De que adianta ter todo esse controle sozinho e não poder compartilhar com outras pessoas? Afinal, essa é uma das grandes felicidades da vida, não? Compartilhar momentos.

<p class="share-inner">
	E posts também, aproveita pra compartilhar com os amigos se está gostando do texto: {% include share-icons.html %}
</p>

Há várias formas de ter uma repositório Git online e uma delas é no GitHub. Aliás esse é um ponto que confunde muitas pessoas, a diferença entre Git e GitHub <small>não, não são a mesma coisa</small>, fique tranquilo que vou explicar mais no final.

Ao clonar um repositório, com o comando `git clone http://url-qualquer.com/caminho/qualquer.git/`, é criado uma pasta no seu computador com o projeto Git automaticamente já linkado com esse repositório online.

<span class="center-horizontal">
	![git clone][image git_clone]
</span>

Porém, você pode iniciar um projeto no seu computador e depois adicionar o repo online, com o comando `git remote add branch http://outra-url.com/outro/caminho.git/`.

Em posse de um repositório online <small>que emoção</small>, surgem dois super conhecidos <small>cansei de falar famoso</small> comandos: `git pull` e `git push`.

Enquanto o primeiro é para atualizar seu repositório local com o remoto, o segundo faz o contrário. Pega todos os seus commits e manda para o remoto. Obviamente que esses novos commits irão para a ~ponta do tronco, por isso seu repositório deve estar sempre atualizado em relação ao remoto, antes de performar um push.

<h3>Para relembrar</h3>

O fluxo normal e mais comum fica assim:

 * `git add --all` o sufixo --all adiciona todos os arquivos que sofreram alteração
 * `git commit -m "no comments"` você também pode usar `git commit -am "add and commit together!"` que não precisará da etapa anterior
 * `git pull` só para garantir que estamos atualizados antes de ~pushar.
 * `git push` <i>voilà</i>.

Simples, bonito, rápido e fácil, não achou? Se concorda e gostou, garanto que os próximos post vão ter conteúdos melhores ainda. Pra garantir que você não vai ficar sem receber, sinta-se à vontade de se inscrever na lista de email. Juro que não mando spam <small>nenhunzinho mesmo</small>.

<div class="mailchimp inner">
	<div>
		{% include /mailchimp/form.html pre="inner-1" label_text="Gostei! vou me inscrever" button_text="Receber por email!" %}
	</div>
</div>

Agora que estamos todos alinhados, que tal ver um pouco de <del>magia</del> <ins>comandos legais</ins>?

<h2 class="image-title"> comandos ~mágicos</h2>
![cherrys][image cherrys]

Imagine como é plantar uma árvore de cereja.

Bricadeira hehe, não vou começar outra história romântica sobre como plantas crescem. Mas é interessante observar o nome do comando.

Imagine que cada commit seja uma saborosa bolinhas vermelha, como uma cereja. <img src="/blog/src/img/2016-01-26-cherry.jpg">

Como <i>cherry pick</i> significa, literalmente, <i>escolher cerejas</i>, na nossa metáfora isso se torna <strong>escolher commits</strong>. A expressão, portanto, mostra que o que o comando faz: escolher um commit e colocar em outro lugar.

Olhe essa bonitinha árvore de cerejas para entender:

<span class="center-horizontal">
	![git cherry tree][image git_cherry_tree]
</span>

Imagine que cada commit seja identificado por uma letra <small>na verdade é por um <a href="https://en.wikipedia.org/wiki/Secure_Hash_Algorithm">SHA</a></small>, e que seu último commit foi o `H`. Isto é, você está no branch de cima.

Se você deseja pegar as alterações feitas no commit `E` a aplicar no seu branch atual, basta executer `git cherry-pick E`, que a árvore ficará assim:

<span class="center-horizontal">
	![git cherry pick][image git_cherry_pick]
</span>

It´s a kind of magic ... <i class="fa fa-music"></i>

<h4>merge <small class="clear">e</small> rebase</h4>

Merge é tão simples que nem imagem vai ter, vai na lata mesmo: enquanto `git branch` abre um novo ramo a partir de onde você está, o `git merge` pega todas essas alterações e aplica de novo em outro branch, criando uma espécie de um novo commit, porém mantendo o histórico do outro branch intacto.

Deu pra entender?

Ta bom, vai uma imagem aí:

<span class="center-horizontal">
	![git merge][image git_merge]
</span>

Essa imagem eu peguei desse <a href="https://www.atlassian.com/git/tutorials/merging-vs-rebasing/the-golden-rule-of-rebasing" target="_blank">link aqui</a>. Ele explica tão bem, mas tão bem como é o `rebase` e sua relação com o merge, que vou deixar a explicação a cargo dele. Mas você promete que volta pra terminar de ler meu post? Tá no finalzinho e ainda tem coisa legal!

<h4>squash</h4>

Esse também é fácil. <strong>squash</strong> é esmagar, achatar, e serve para juntar vários commits em apenas um.

<q>Mas porque eu iria querer fazer isso?</q> Você me pergunta.

Sei lá cara, o projeto é seu, você que decide o que quer fazer com ele. Eu te respondo &hearts;

<h4>stash</h4>

Esse também é legal, ele pega as alterações que você fez nos arquivos <small>aqueles que estão vermelho no git status</small>, e coloca em um mundo paralelo totalmente desconectado da árvore do seu projeto.

<q>Mas porque eu iria querer fazer isso?</q> Você me pergunta.

Agora eu sei te responder!

Imagine que você acabou de terminar uma nova <i>feature</i> do projeto em um branch, e acabou de criar outro para começar outra <i>feature</i>. Ai você começa a fazer as <strong>alterações</strong>, mas percebe que precisa de consertar algo errado na <i>feature</i> anterior. Se você simplesmente fizer `git checkout primeiro_branch`, as <strong>alterações</strong> permanecem nos arquivos <small>o vermelhinho do git status continua igual</small>, algo que você não quer, você quer deixar as alterações no segundo branch.

Você pode commitar as alterações antes de dar o checkout, mas você não quer poluir seu projeto com um commit antes da hora. 

Ou você pode fazer isso e fazer um squash depois e reescrever o commit anterior.

Que confusão!

Tá bom, é mais fácil colocar essas alterações no <strong>mundo paralelo</strong> com `git stash`, mudar de branch, fazer o que quiser fazer, voltar pro outro branch, e pegar tudo de novo com `git stash apply`.

Tão simples quanto colher cerejas!

<h2 class="image-title">GitHub</h2>
![github finally][image github_finally]

Talvez nesse ponto você já tenha ideia <small>é só eu que acho estranho escrever ideia sem acento?</small> de algumas diferenças. O GitHub seria mais ou menos um cloud service para o Git.

Porém, o Git não engloba um GitHub, e nem vice-versa, ambos são mais ou menos independentes.

<span class="center-horizontal">
	![git github][image git_github]
</span>

Além do Git, o GitHub tem:

 * o Pages, para hospedar páginas estáticas e gratuitas, com a possibilidade de usar domínios próprios, tudo de graça. Tem um <a href="/blog/como-fiz-meu-blog-em-2-dias/">post legal</a> de um blog legal que ensina a fazer isso com Jekyll.

 * Tem também o <a href="https://gist.github.com/">Gist</a>, para compartilhar e discutir trechos simples de código de forma rápida.

 * E tem o incrível <a href="https://education.github.com/pack">pacote para estudantes</a>, que, ao comprovar que é estudante, você ganha várias coisas de graça, como planos em ferramentas pagas, editores de texto pago, e até 5 repositórios privados no GitHub.

Eu sei, o post ficou grande. Mas isso não é uma boa coisa?

Se achou ruim, para te compensar eu vou parar de enrolar e acabar o post aqui mesmo, abruptamente.

<small class="clear">tchau</small>.

[image pendrive_git]: /blog/src/img/2016-01-26-pendrive-vs-git.jpg
[image coffee_rain]: /blog/src/img/2016-01-26-coffee-and-rain.jpg
[image real_seed]: /blog/src/img/2016-01-26-real-seed.jpg
[image git_seed]: /blog/src/img/2016-01-26-git-seed.png
[image real_trunk]: /blog/src/img/2016-01-26-real-trunk.jpg
[image git_trunk]: /blog/src/img/2016-01-26-git-trunk.png
[image real_tree]: /blog/src/img/2016-01-26-real-tree.jpg
[image git_tree]: /blog/src/img/2016-01-26-git-tree.png
[image git_trunk_2]: /blog/src/img/2016-01-26-git-trunk-2.png
[image git_commit]: /blog/src/img/2016-01-26-git-commit.png
[image git_push]: /blog/src/img/2016-01-26-git-push.png
[image git_clone]: /blog/src/img/2016-01-26-git-clone.png
[image git_merge]: /blog/src/img/2016-01-26-git-merge.png
[image git_cherry_tree]: /blog/src/img/2016-01-26-git-cherry-tree.png
[image git_cherry_pick]: /blog/src/img/2016-01-26-git-cherry-pick.png
[image cherrys]: /blog/src/img/2016-01-26-cherrys.jpg
[image github_finally]: /blog/src/img/2016-01-26-github-finally.jpg
[image git_github]: /blog/src/img/2016-01-26-git-github.png