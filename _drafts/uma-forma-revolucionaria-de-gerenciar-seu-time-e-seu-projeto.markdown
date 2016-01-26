---
layout: post
title:  "Uma forma revolucionária de gerenciar seu time e seu projeto"
image_list: /blog/src/img/2016-01-24-forma-revolucionaria-de-gerenciar-seu-time-e-seu-projeto.png
comments: true
description: >
    Você conhece o Git? Para alguns é comum. Para outros nem tanto. Porém tenho certeza que, em ambos os casos, você vai ficar impressionado com o que ele pode fazer por você.
---

<q> Revolucionário? O Git? Que exagero! </q> Você pode dizer.

Sim. Eu também diria a mesma coisa. Já trabalho com o Git a mais de 2 anos e para mim ele se tornou uma simples ferramenta de trabalho. <strong>Indispensável</strong>, mas <strong>simples</strong>. Acontece que na sua simplicidade se esconde a força de sua complexidade.

Você provavelmente deve imaginar que muito pesquisei sobre Git antes de escrever esse post, a fim de entender melhor a dinâmica de seu funcionamento. De fato, li muitos textos antes de começar mais um, procurei imagens didáticas e rodei o mundo a procura de especialistas <small>sem a parte de rodar o mundo hehe</small>.

Porém, depois de achar um mundo de bons artigos, pensei o que faria o meu post único, de forma a manter a identidade do blog e, mais importante, que acrescentasse algo para o leitor.

E finalmente, depois de muito pensar <small>mentira, nem pensei tanto assim</small>, decidi seguir um rumo um pouco diferente. Este <strong>não será um post técnico</strong>, mas mais <strong>subjetivo</strong> e escrito com minhas próprias palavras e as abstrações que consegui fazer do funcionamento do Git.

<h2>Versionador</h2>

IMG DO PENDRIVE VS. GIT

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

Passa um tempo e, depois de muito trabalho, o tronco começa a crescer. Você fica maravilhado em como ela é jovem porém já tão robusta. <strong>Robusta e flexível</strong>.

<span>
	<span style="margin-right: 30px">
		![real trunk][image real_trunk]
	</span>
	<span>
		![git trunk][image git_trunk]
	</span>
</span>

E de repente, de forma muito rápida, os galhos começam a nascer e crescer. Se ramificam cada vez mais, e você precisa de mais pessoas para te ajudar a cuidar da árvore. Cada um cuida de uma parte, mas todos contribuem para o crescimento daquele corpo que está se formando.

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

A árvore


## fluxo normal:
 * git add --all
 * git commit -m "message"
 * git pull
 * git push

## comandos ~mágicos
 * cherry pick (http://think-like-a-git.net/sections/rebase-from-the-ground-up/cherry-picking-explained.html)
 * rebase e merge (https://www.atlassian.com/git/tutorials/merging-vs-rebasing/the-golden-rule-of-rebasing)
 * stash
 * squash (https://ariejan.net/2011/07/05/git-squash-your-latests-commits-into-one/)

## github
* overlap
* nuvem
* pages
* gist
* student pack

## student pack
 * yey


[image coffee_rain]: /blog/src/img/2016-01-26-coffee-and-rain.jpg
[image real_seed]: /blog/src/img/2016-01-26-real-seed.jpg
[image git_seed]: /blog/src/img/2016-01-26-git-seed.png
[image real_trunk]: /blog/src/img/2016-01-26-real-trunk.jpg
[image git_trunk]: /blog/src/img/2016-01-26-git-trunk.png
[image real_tree]: /blog/src/img/2016-01-26-real-tree.jpg
[image git_tree]: /blog/src/img/2016-01-26-git-tree.png