---
layout: post
title:  "<span class='tag'>#DicaPrática</span> Três técnicas e componentes incríveis para o seu site ficar (ainda mais!) responsivo"
image_list: /blog/src/img/2016-01-30-tres-componentes-rapidos.png
comments: true
description: >
  Essa #dicaPrática mostra algumas técnicas e componentes capazes de te dar insights para elevar a responsividade de seu site à outro nível.
twitter_text: Esse post conta (e conta muito bem) o melhor do Git!
---

<style type="text/css">
  .nome {
  margin-bottom: 30px; }
  @media (min-width: 48em) {
    .nome:after {
      content: ' Novaes'; } }
  @media (min-width: 34em) {
    .nome:before {
      content: 'Dayman '; } }
</style>

Como você deve ter percebido pelo título <small>se você não percebeu, por favor procure um oculista rápido! <small>e depois volte pra ler meu blog &hearts;</small></small>, tem uma parte amarela alí indicando que esse post:

 * Fará parte de uma série/hastag/sequência intitulada de <strong>dica prática</strong>
 * Será mais curto e direto, facilitando a leitura
 * Será prático! Facilitando a sua implementação

Se <del>você estava em coma</del> <ins>não sabe o que significa um design responsivo</ins>, eu falo um pouco sobre isso no meu <a href="/blog/como-fiz-meu-blog-em-2-dias-parte-2/">segundo post.</a> Mas é basicamente um design que se adequa à diferentes tipos de tela.

Os exemplos mostrados aqui serão feitos em <strong>Sass</strong> porque <del>eu quero e pronto</del> <ins>facilita muito nosso trabalho</ins>.

<strong>Se</strong> você é programador, <strong>e</strong> não conhece Sass ou outro pré-processador de CSS, como diria o <a href="http://guncast.com.br/" target="_blank">Murilo Gun</a>, você <strong>tá de brincadeira na tomateira</strong>. Levanta a bunda da cadeira <small>metaforicamente, a menos que queira usar o computador em pé</small> e vai logo aprender sobre isso, para o seu próprio bem! Meu <a href="/blog/como-fiz-meu-blog-em-2-dias/">primeiro post</a> conta um pouco das vantagens.

Sem mais delongas:

<h2>1. Mudando o texto com seletor :before e :after</h2>

Essa técnica é uma sacada <strong>muito</strong> boa, e confesso que a tirei do site do meu amigo <a href="http://willianjusten.com.br/ano-novo-blog-novo/" target="_blank">Will</a>.

Se você <del><small class="clear">tá de brincadeira na tomateira</small></del> não sabe o que significa esses `::after` e `::before`, é muito simples. Eles são <strong>pseudo elementos</strong>.

Como o w3schools explica muito bem <a href="http://www.w3schools.com/css/css_pseudo_elements.asp">nesse artigo</a>, esse tipo de seletor é usado para selecionar <strong>partes</strong> de <strong>dentro</strong> de um elemento a primeira linha ou a primeira letra.

Os seletores after e before nos permitem inserir um conteúdo antes ou depois do conteúdo do elemento.

Olha esse exemplo simples e legal:

{% highlight html %}
<style>
  div.nome:before {
    content: 'Dayman ';
  }
  div.nome:after {
    content: ' Novaes';
  }
</style>

<div class="nome">Moreira</div>
{% endhighlight %}

Produz o resultado:

<div class="nome">Moreira</div>

E como esse texto é inserido com CSS, pode ser facilmente alterado com o uso de <a href="http://www.w3schools.com/cssref/css3_pr_mediaquery.asp">Media Query</a>. Como por exemplo, mostrar apenas partes do nome em telas menores:

{% highlight scss %}
.nome {
  @include media-query(md) {
    &:after {
        content: ' Novaes';
    }
  }
  @include media-query(sm) {
    &:before {
        content: 'Dayman ';
    }
  }
}
{% endhighlight %}


Esse código diz que a parte "Novaes" só será mostrada para telas maiores que tamanho média (<strong>m</strong>e<strong>d</strong>ium), e "Dayman" apenas para telas maiores que tamanho pequeno (<strong>sm</strong>all).

O compilado fica assim:

{% highlight css %}
@media (min-width: 48em) {
  .nome:after { content: ' Novaes'; }
}
@media (min-width: 34em) {
  .nome:before { content: 'Dayman '; }
}
{% endhighlight %}

E o resultado:

<span class="center-horizontal">
  <img src="/blog/src/img/2016-01-30-gif-nome.gif" alt="nome responsivo" style="height: 25px;">
</span>

Eu uso essa técnica no meu site pessoal, na seção de habilidade, onde mostra várias tecnologias com o nome a uma imagem. O nome é incluído desta forma, sendo que em dispositivos mobiles, o texto some e ficam apenas as imagens.

<span class="center-horizontal">
  <img src="/blog/src/img/2016-01-30-gif-skills.gif" alt="habilidades responsivas">
</span>

<h2>2. Utilitários Sass que podem salvar seu tempo</h2>

Os `mixins` do Sass são ótimos, pois são funções que podemos criar para executar e compilar algum código CSS.

Misturando um pouco com a ideia de <strong>breakpoints</strong> do Bootstrap <small>olha no segundo post</small>, podemos criar um mixin que utiliza disso para facilitar e padronizar o desenvolvimento.

Você deve ter percebido que usei no exemplo anterior o <span class="highlight pre"><span class="k">@include</span> <span class="nd">media-query</span><span class="p">(..)</span></span>, é exatamente ele que vou explicar agora.

Primeiro, precisamos definir as variáveis que definem os tamanhos de tela que queremos, isto é, os <strong>breakpoints</strong>.


{% highlight scss %}
$breakpoints: (
  // Extra small screen / phone
  xs: 22em,
  // Small screen / phone
  sm: 34em,
  // Medium screen / tablet
  md: 48em,
  // Large screen / desktop
  lg: 62em,
  // Extra large screen / wide desktop
  xl: 75em
);
{% endhighlight %}

Essa variável é do tipo map, e podemos acessá-la usando `map-get($breakpoints, xs)` por exemplo.

A definição do mixin então fica assim:

{% highlight scss %}
@mixin media-query($breakpoint) {
  @media (min-width: #{map-get($breakpoints, $breakpoint)}) {
    @content;
  }
}
{% endhighlight %}

{% highlight scss %}
@mixin media-query-down($breakpoint) {
  @media (max-width: #{map-get($breakpoints, $breakpoint) - 0.01}) {
    @content;
  }
}
{% endhighlight %}

<h2>3. Modularização inteligente com o Sass</h2>

Modularização não está diretamente ligada à responsividade, 

[image gif_nome]: /blog/src/img/2016-01-30-gif-nome.gif
[image gif_nome]: /blog/src/img/2016-01-30-gif-skills.gif