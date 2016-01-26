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

Imagine antigamente, antes dos <i>cloud services</i> <small>dropbox, box, drive, etc</small> existirem, como um time de desenvolvedor fazia para compartilhar as alterações feita por cada um no projeto?

Bom, se não compartilhavam por disquete ou CD, era no mínimo por pendrive, espetando o dito cujo em cada computador, juntando as alterações manualmente nos arquivos já existentes e depois anotando, talvez no notepad ou em um papel, o que mudou nessa nova <strong>versão</strong>.

Bom, com os serviços de compartilhamento atual tudo ficou claramente mais fácil e natural. Basta colocar um projeto na nuvem, dar acesso a todos da equipe, e <i>voilà</i>, teremos mais ou menos um controle sobre todas as alterações, de forma um pouco mais fácil do que ficar espetando o bom e velho pendrive.

Tudo <strong>quase</strong> lindo.

Queremos uma ferramenta que nos dê controle <strong>total</strong> sobre todas as alterações, com informações contextuais que digam o que foi alterado, onde, quando, por quem, e porquê <small>ufa!</small>. Também queremos fazer isso da forma mais simples o possível, de forma que, por exemplo, eu consiga migrar entre diferentes dispositivos e sempre ter a <strong>versão</strong> mais atual do projeto.

Queremos atualizar, alterar, e gerenciar nossos projetos e nossa equipe de <a href="/blog/como-programar-de-qualquer-lugar-do-mundo/">qualquer lugar do mundo</a>, como citei nesse meu último post.

<span class="center-horizontal">
	![coffee and rain][image coffee_rain]
</span>

Sim, é isso tudo mesmo. Tão fácil quanto digitar 3 linhas de comando, ou dar 3 cliques, ou tomar um chocolate quente em um dia chuvoso.


<h2>Árvore do projeto</h2>

<span>
	<span style="margin-right: 30px">
		![real tree][image real_tree]
	</span>
	<span>
		![git tree][image git_tree]
	</span>
</span>



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
[image real_tree]: /blog/src/img/2016-01-26-real-tree.jpg
[image git_tree]: /blog/src/img/2016-01-26-git-tree.png