---
layout: post
title:  "Como se tornar o Sherlock Holmes da programação"
image_list: /blog/src/img/2016-02-15-como-se-tornar-o-sherlock-holmes-da-programacao.jpg
comments: true
description: >
  
twitter_text: Ótimo post que ensina técnicas sobre como investigar um código e encontrar erros!
---

Como de costume, lá estava ele. No mesmo aposento da mesma casa em Baker Street. Enterrado entre seus livros novos, e alternando, semana a semana, a música clássica com a contemporânea, estudos complicados com exercícios físicos.

Continuava, como sempre, profundamente atraído pelos estudos do crime e dedicava seus portentosos poderes de observação a seguir pistas e desvendar mistérios abandonados como insolúveis pela polícia oficial.

Desta vez ele estava sentado em seu computador enquanto ouvia sonatas de Bach em ré menor, ou as vezes em pé na sua cama enquanto escrevia em seu quadro e tomando um café islandês.

<span class="center-horizontal">
  ![sherlock holmes 221b][image sherlock_221b]
</span>

Esse não é o <strong>Sherlock Holmes</strong>.

Troque <strong>Baker Street</strong> por <strong>Belo Horizonte</strong>.

Troque <strong>estudos do crime</strong> por <strong>estudos de tecnologia</strong>.

E considere os <strong>mistérios insolúveis</strong> como liçensa poética.

Não que eu ache que eu chegue aos pés desse maravilhoso personagem, mas eu estava <strong>falando de mim</strong>, nesse exato instante, enquanto escrevo esse texto.

Nesse texto, vou contar da minha primeira experiência profissional e como ela me ajudou a desenvolver a <del><small>estranha</small></del> habilidade de encontrar erros em códigos, com o auxílio de incríveis ferramentas de debug. Meu trabalho era <strong>encontrar e consertar erros de usabilidade</strong> no software usado pela empresa, e isso era bem parecido com um trabalho investigativo, pois encontrar esses erros nem sempre era tão fácil.

E em vários momentos eu me sentia um verdadeiro Sherlock Holmes ao solucionar mais um misterioso bug.

<h2>
  Por que isso se assemelha a um trabalho investigativo
</h2>

Seção que explica RAPIDAMENTE a semelhança de debug com investigação

Usar um pré-call falando da importância de se achar o problema para achar a solução.

<h2>
  Para resolver o consequência, resolva a causa
</h2>

A vida de Sherlock Holmes era fácil. A unica coisa que ele precisava fazer era achar a causa do problema, ou de um crime, e tudo estaria resolvido. 

Nós, programadores, <strong>além</strong> de ter que encontrar a causa do problema, precisamos pensar em uma solução para, <strong>de fato</strong>, resolver o problema. Seja implementando uma nova funcionalidade no sistema, ou apenas corrigindo um bug.

É uma brincadeira, claro que não é fácil fazer o que o Sherlock faz, não é um trabalho simples, mas é essencial.

Encontrar a causa do problema <strong>não é simples</strong>, mas é <strong>essencial</strong>.

Claro que há aqueles que preferem simplesmente tapar o buraco da forma mais fácil, a famosa <i>~gambiarra</i>, sem se preocupar com a origem do problema.

Porém, no futuro, essa má prática pode significar o fim do seu projeto, ou do seu emprego, ou da sua vida.

Assim como o corpo humano, um projeto ou um código também dá varios sinais sobre sua saúde. E devemos <strong>ficar atentos</strong> a estes sinais.

<span class="center-horizontal">
  ![enxaqueca][image enxaqueca]
</span>

É exatamente igual quando, por exemplo, estamos com dor de cabeça. Vamos tomar um remédio que simplesmente nos faz parar de sentir a dor, ou vamos procurar a causa? 

<strong>Resolva a causa, e a consequência estará</strong> <small>quase</small> <strong>resolvida</strong>.

<h2>Um pouco da metodologia</h2>

Para achar a causa de um problema primeiramente precisamos ter calma. 

Calma. 

Muita calma. 

Não porque é demorado, mas porque é minucioso, e precisamos de atenção para, principalmente, <strong>não tirarmos conclusões precipitadas</strong>. Por isso, calma. 

Vamos supor, por exemplo, que você queira criar um campo de texto que tenha seu conteúdo copiado, em ~tempo real~ para outro lugar. Assim como o exemplo abaixo.

@@@@ EXEMPLO AQUI @@@@

Você cria o input, cria o código e quando vai testar... Não funciona. Qual o primeiro passo para tentar resolver? Isso mesmo, ter calma. 



[image sherlock_221b]: /blog/src/img/2016-02-15-sherlock-221b.jpg
[image enxaqueca]: /blog/src/img/2016-02-15-enxaqueca.jpg