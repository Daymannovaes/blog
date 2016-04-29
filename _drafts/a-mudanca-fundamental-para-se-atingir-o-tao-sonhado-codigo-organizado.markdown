---
layout: post
title:  "A mudança fundamental para se atingir o tão sonhado &quot;código organizado&quot;"
image_list: /blog/src/img/a-mudanca-fundamental.jpg
comments: true
description: >
  As vezes procuramos a solução do nosso código incluindo mais ferramentas em nosso projeto. Porém o que deveria resolver as vezes parece apenas poluir. Qual seria a solução definitiva para isso?
twitter_text: Ótimo post que ensina técnicas sobre como investigar um código e encontrar erros!
---

Você é capaz de produzir um código organizado? Um projeto organizado? Um estilo de vida organizado?

<q>Qual a relação entre os três? O que minha vida tem a ver com meu código?</q> Você pode se perguntar.

Essas relações são muito maiores do que você pode imaginar! E é sobre isso que eu queria falar hoje com você. 

<h4>Motivo</h4>
Esse post cheio de perguntas foi motivado por alguns acontecimentos na minha vida que vou compartilhar com você.

Você já quis começar a aprender web e não sabia por onde? Principalmente se você está em uma faculdade, onde esse tipo de conteúdo deveria ser ofertado com frequência, você provavelmente já se frustrou ao procurar e... não achar.

<span class="center-horizontal">
	<img src="/blog/src/img/travolta-procurando.gif" style="height:250px;">
</span>

Então resolvi eu mesmo dar esse curso, de forma totalmente gratuita: o primeiro curso de web na UFMG.

<small>Até o presente momento você pode ver sobre o curso em <a href="http://cursos.dayman.io">http://cursos.dayman.io</a></small>.

Acontece que para fazer isso acontecer eu tive que me reinventar. Precisei ter mais disciplina para criar conteúdo a tempo, e precisei alocar o meu tempo para me dedicar às aulas. É uma <strong>responsabilidade</strong> muito grande, imagine de repente um grupo de pessoas confiando em você e esperando de sua parte aquelas aulas!

Mas nem por isso eu me desmotivei e me permiti ser medíocre ao não buscar a excelência no que estava fazendo. Mas por conta da inexperiência, inevitavelmente alguns desencontros ocorreram, como não conseguir reservar uma sala a tempo e ter que desmarcar uma aula cinco horas antes dela começar.

Isso é reflexo da minha vida desorganizada, porém como um sincero pedido de desculpa, resolvi criar esse post. 

<h2>Qual o significado da organização</h2>

Se você faz ou fez faculdade e teve um bom professor de Algoritmos, com certeza ele repetiu essa frase com você:

<q>faça um código organizado e legível! Indentação é o mínimo que você pode fazer. Declare variáveis e funções com nomes semânticos e intuitivos. Separe e modularize seu código de forma consistente.</q>

Certo? 

Trabalhando-se sozinho, as vezes é difícil entender a importância dessa atenção, porém quando se trabalha em time, cada um tende a programar à sua maneira, e se não for estabelecido um padrão de código e uma organização, vira tudo tão bagunçado quanto seu quarto poderia ser na sua adolescência.

Acontece, que mesmo trabalhando sozinho, não estamos sozinho! Você por acaso, é o mesmo do que a sete anos atrás? Você será o mesmo daqui a sete anos? Ou até mesmo, lembra do que comeu ontem no almoço?

<small>Comecei a escrever esse post no ônibus e fui obrigado a fazê-lo sem ouvir música! Isso tudo porque coloquei meu fone de ouvido em um bolso diferente do usual na mochila e não o encontrei, chegando a pensar que tinha perdido! Maldita desorganização!</small>

<h2>Qual exatamente a relação entre minha vida e meu codigo?</h2>

Tudo que produzimos é uma expressão de nós mesmos.

<strong>Tudo</strong>.

Tudo que criamos com nossas próprias mãos, tudo que surge dos nossos <strong>pensamentos</strong>, dos nossos <strong>desejos</strong> e das nossas <strong>ações</strong> é, em parte, nós mesmos.

Sem ficar filosofando muito <small>embora esse seja o slogan do Blog</small>, não basta simplesmente dar uma pesquisa no google de "ferramentas para organizar código" e tudo estará resolvido. Não são as <strong>ferramentas</strong>, ou o <strong>ambiente</strong> que vai fazer seu código melhor.

Claro que as ferramentas são imprescindíveis para melhorar a eficiência de nossa trabalho. Imagine um pintor sem pincel ou um jardineiro sem pá. Mas, apesar da importância de uma boa ferramenta, 90% <small>dados retirados do IBGE <small>mentira</small></small> da qualidade do que produzimos diz respeito apenas à nós. Inclusive comento disso <a href="http://me.dayman.io/blog/como-programar-de-qualquer-lugar-do-mundo/">nesse post aqui</a>.

Não é buscando algo exteriormente que vamos mudar fundalmentamente, a mudança precisa partir de dentro.

<span class="two-images join">
	<span>
		<img src="/blog/src/img/neuron.jpg">
	</span>
	<span>
		<img src="/blog/src/img/phedres-nebulab.jpg">
	</span>
</span>
<span class="center-block text-center">Assim como em cima, é embaixo.</span>

Minha mãe costumava dizer <small>ainda costuma as vezes</small> ao ver meu quarto bagunçado: <i>"arruma esse quarto filho. Quarto bagunçado igual a vida bagunçada</i>.

E tem um fundo de verdade. Não só o fundo, mas acredito que isso é uma total verdade!

<q>Então quer dizer que para organizar meu código vou precisar organizar minha vida toda? E para organizar minha vida preciso organizar também o meu quarto? E meus estudos? E minha mesa de trabalho? e etc?</q> Pode parecer desesperador a um primeiro momento. Mas calma lá, vem comigo que eu vou te explicar!.

Você tá achando esse post muito louco e viajado? Que bom! Já que você chegou até aqui, que tal fazer mais uma loucura e se inscrever na lista de emails, para receber os posts fresquinhos? Juro <small>mentira, nem juro</small> que você não vai se decepcionar!
<div class="mailchimp inner">
	<div>
		{% include /mailchimp/form.html pre="inner-1" label_text="<del>não</del> gostei! vou me inscrever" button_text="Receber por email!" %}
	</div>
</div>

<h2>A mudança na prática</h2>

Bom, como já comentei, a mudança fundamental não vem de fora. Para mudarmos aspectos de nossa vida <small>e de nossos projetos também</small>, devemos mudar a nós mesmos.

<strong>Porém</strong> <small>pausa dramática</small>, é uma <i>vida de mão dupla</i>. <strong>Personalidade e ação se influenciam mutuamente</strong>, isso é, a sua forma de ser influencia as suas ações, e suas ações também influenciam sua forma de ser.

Isso ajuda um pouco na hora de resolver o problema. Se eu consigo identificar várias ~falhas de organização~ na minha vida, posso começar resolvendo uma a uma e isso, naturalmente, vai ir se refletindo nos outros aspectos.

Esse é um blog de <strong>desenvolvimento</strong>, e tudo que estou falando é para te ajudar a melhorar o seu código! Tente ver toda essa ~filosofia como coisas que vão convergir em um crescimento profissional, como desenvolvedor.

A vida é composta de muitos aspectos mas, se organizar direitinho, todo mundo transa. <small>créditos à <a href="">André &hearts;</a> pela piada</small>.

<h3>Algumas ferramentas</h3>

IDE -