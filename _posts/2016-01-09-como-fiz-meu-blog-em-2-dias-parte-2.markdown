---
layout: post
title:  "Como fiz meu blog em 2 dias - Parte 2: Bootstrap e Sass"
image_list: /blog/src/img/2016-01-09-como-fiz-meu-blog-em-2-dias-parte-2.jpg
comments: true
description: >
  Já conhecia essas duas ferramentas, mas aprendi algumas coisas legais durante o desenvolvimento do blog e gostaria de mostrar para vocês! Olha aqui e me conte o que achou.
---
<style type="text/css">
  /* -- applyed only to this post -- */
  .-padding-change .-padding-element, .-padding-change pre {
    margin: 10px 0 !important;
  }
</style>

Gostaria de começar dizendo que, apesar de ter uma certa prática com CSS e o post ser sobre isso, não sou designer e gastei muito tempo para fazer essa ~linda imagem:

<span class="center-horizontal">
  ![sass boostrap][image sass_boostrap]
</span>

Então, por favor, se for criticar algo, que seja sobre o post, e não sobre a imagem. <small>brincadeira hehe</small>

E se não viu a primeira parte da série, que explico sobre Jekyll e GitHub Pages, <a href="/blog/como-fiz-meu-blog-em-2-dias/">veja aqui</a>.


Bootstrap é um framework para CSS <small>principalmente</small> para desenvolvimento responsivo. Ele possui várias classes utilitárias prontas, tanto para facilitar que seu site fique responsivo <small>você pode abrir esse blog no celular que ele fica bonitinho &hearts;</small>, quanto para componentes, como por exemplo botões, com a classe `btn`:

<div class="two-columns join -padding-change">
  {% highlight html %}
    <button>Hey!</button>
  {% endhighlight %}
  <div class="-padding-element">
    <button>Hey!</button>
  </div>
</div>
<div class="two-columns join -padding-change">
  {% highlight html %}
    <button class="btn">Hey!</button>
  {% endhighlight %}
  <div class="-padding-element">
    <button class="btn">Hey!</button>
  </div>
</div>
<div class="two-columns join -padding-change">
  {% highlight html %}
    <button class="btn btn-danger">Hey?</button>
  {% endhighlight %}
  <div class="-padding-element">
    <button class="btn btn-danger">Hey?</button>
  </div>
</div>

<p style="margin-top: 20px">
  É um exemplo simples, existem vários outros, mas deu pra ter uma ideia né?
</p>

Agora falando sobre algo muito mais empolgante! Que é responsividade, isto é, um layout que caiba bem em todos os tipos de tela, como nesse gif:

<span class="center-horizontal">
  <img src="/blog/src/img/2016-01-09-my-website-responsive.gif" style="height: 250px">
</span>

Percebe como os posts vão se ajeitando para cada tamanho de tela? Quando a tela fica pequena os cards vão diminuindo, e quando fica realmente muito pequeno, a imagem some para dar mais espaço ao texto.

O fato da imagem sumir nos dá mais uma vantagem além de mais espaço, é o <strong>tempo de renderização da página</strong>.

Bom, naturalmente os dispositivos com telas menores são celulares <small>e relógios inteligentes</small>, que em grande parte das vezes, são usados com redes móveis, como 3G e 4G, que são mais lentas que a internet a cabo que você tem na sua casa.

E um blog, ou qualquer outro site que preze por uma melhor <strong>experiência de usuário</strong>, deve se preocupar com esses casos e evitar ao máximo carregar coisas pesadas, como grandes <span class="highlight"><span class="nt">scripts</span> ou imagens de alta resolução. É por isso que em telas pequenas a imagem não é carregada, como mostra o gif.

~Mas como você fez isso?~ Você me pergunta. <br>
~Simples, com ajuda do Sass e das Media Query<small class="clear">s</small>~

<h2>
  Usando media query com Sass e Bootstrap
</h2>

Bom, ainda não apresentei o Sass para vocês, mas como a intenção do post não é falar sobre a ferramenta, e sim contar sobre como ela me ajudou a construir o blog, vou pontuar algumas coisas superficiais, mas depois explico com mais detalhes, ok?

Sass é o que chamamos de pré processador de CSS. Se você já tem algum conhecimento de CSS, já deve ter se perguntado porque até hoje não podemos fazer algo desse tipo:

{% highlight scss %}
footer {
  display: flex;
  
  p {
      color: grey;
      text-shadow: 0px 2px 0px white;
  }
}
{% endhighlight %}

Essa sintaxe claramente nos diz que estamos definindo um estilo para o elemento <span class="highlight"><span class="nt">footer</span>, e um estilo para todos os <span class="highlight"><span class="nt">p</span><small class="clear">s</small> dentro do <span class="highlight"><span class="nt">footer</span>.

Porém, se quisermos realmente fazer isso, em CSS seria necessário fazer assim:
{% highlight css %}
footer {
  display: flex;
}
footer p {
    color: grey;
    text-shadow: 0px 2px 0px white;
}
{% endhighlight %}

Acho que você já entendeu uma das vantagens de um pré processador. Só pra garantir, vou explicar. Um <strong>pré processador</strong>, em geral, define uma sintaxe um pouco diferente em relação à linguagem original, com algumas facilidades que esta não oferece.

No caso do Sass, você pode escrever seletores aninhados como no exemplo, pode utilizar variáveis e também funções. E são exatamente as funções que me ajudaram mais no processo da responsividade. Em Sass, uma função é chamada de `mixin`, e abaixo está um exemplo de um mixin que inclui `border-radius` e o seu uso:

{% highlight scss %}
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
     -moz-border-radius: $radius;
      -ms-border-radius: $radius;
          border-radius: $radius;
}

.box { 
  @include border-radius(10px);
}
{% endhighlight %}

<h3>media query</h3>

Antes de continuar, vou falar rapidamente das media querys. Você já imaginou pode escrever um estilo diferente para diferentes tamanhos de tela?

Essa é o objetivo das media querys, e seu funcionamento é bem simples, como vocês podem ver no exemplo:

{% highlight scss %}
.gmap_canvas {
  border-radius: 50%;

  @media (max-width: 33.9em) {
    pointer-events: none;
  }
}
{% endhighlight %}

Esse código eu retirei do meu [site pessoal], e define que, para telas menores que `33.9em` <small>542px, no caso</small>, elementos com a classe <span class="highlight"><span class="nc">gmap_canvas</span> não vão responder à eventos do mouse. Isso é feito para impedir que os mapas que aparecem no site dificultem o scroll em telas pequenas.

Lembrando que essa sintaxe é a definida pelo Sass, e ela é compilada ~ao contrário, ficando assim:

{% highlight css %}
.gmap_canvas {
  border-radius: 50%;
}
@media (max-width: 33.9em) {
  .gmap_canvas {
    pointer-events: none;
  }
}
{% endhighlight %}

Se você notou que usei `em` no lugar de `px`, relaxe, é só outra forma de representar tamanhos, farei um post sobre isso.

Bom, explicado Sass e media query, é a hora do Bootstrap entrar. 

<h3>Bootstrap</h3>
O Bootstrap define o que ele chama de `breakpoints`, ou ~pontos de quebra. Cada breakpoint define um tamanho específico de tela:

|sigla|nome|device|tamanho|
|:---:|:--:|:----:|:-----:|
|xs|extra small|telefones em modo retrato|menor que 34em| 
|sm|small|telefones em modo paisagem|34em para cima|
|md|medium|tablets|48em para cima|
|lg|large|desktops|62em para cima|
|xl|extra large|desktops maiores|75em para cima|


Estes valores são importantes e definidos para otimizar e facilitar o layout responsivo. Eles são usados em várias classes, mas uma muito importante é a classe `container`. 

Como o próprio nome já diz, ela serve como um container e define um espaço centralizado e sempre menor que a tela, ou seja, ela sempre deixa uma margem em relação à borda. Veja seu código e funcionamento: 

{% highlight scss %}
.container {
  margin-right: auto;
  margin-left: auto;
  padding-left: 0.9375rem;
  padding-right: 0.9375rem;
}
@media (min-width: 34em) {
  .container { max-width: 34rem; }
}
@media (min-width: 48em) {
  .container { max-width: 45rem; }
}
@media (min-width: 62em) {
  .container { max-width: 60rem; }
}
@media (min-width: 75em) {
  .container { max-width: 72.25rem; }
}
{% endhighlight %}

<span class="center-horizontal">
  <img src="/blog/src/img/2016-01-09-my-website-responsive-highlight.gif" style="height: 250px">
</span>

Agora é que a mágica realmente acontece.

<h2><span style="color:#F10892;">@</span>include container(<span style="color:#8049E4;">0.8</span>);</h2>

Podemos ver que o container fica em torno o de 96% a 74% do tamanho da tela, como explicado acima. Porém, e se quisermos um tamanho proporcionalmente menor? Como metade disso, resultando algo em torno de 48% a 37%?

Bem, analisando o código do Bootstrap <small>que é feito em Sass</small> para ver como eles realmente compilam o código da classe `container`, pude ver que meu trabalho estava muito facilitado.

{% highlight scss %}
.container {
  @each $breakpoint, $container-max-width in $container-max-widths {
    @include media-breakpoint-up($breakpoint) {
      max-width: $container-max-width;
    }
  }
}
{% endhighlight %}

Esse código, basicamente, percorre os breakpoints que mencionamos acima, e cria uma media query para os respectivos tamanhos de tela e define o tamanho máximo do container, resultando no código compilado apresentado mais acima.

Nosso mixin para definir containers customizados já está quase pronto, basta apenas copiar um código, colocar dentro de uma função que recebe como parâmetro a <strong>porcentagem</strong>, e usá-la na definição do max-width, alterando apenas a linha 1 e 4:

{% highlight scss %}
@mixin container($percent) {
  @each $breakpoint, $container-max-width in $container-max-widths {
    @include media-breakpoint-up($breakpoint) {
      max-width: $container-max-width * $percent;
    }
  }
}
{% endhighlight %}

E usar assim: 

{% highlight scss %}
.post {
  article {
    @include container(0.8);
  }
}
{% endhighlight %}

Bom, tinha mais algumas coisinhas que eu gostaria de falar, mas como o post já ficou um pouco grande, deixo pra próxima. Aproveitem para deixar seu feedback sobre o tamanho e conteúdo, ficou bom? Gostaram? O que melhorar? Sexta, no <span class="line-crossed">Globo Reporter</span> próximo post.

[site pessoal]: https://github.com/Daymannovaes/daymannovaes.github.io/blob/master/src/sass/gmap.scss
[image sass_boostrap]: /blog/src/img/2016-01-09-como-fiz-meu-blog-em-2-dias-parte-2.jpg
[image my_website_responsive]: /blog/src/img/2016-01-09-my-website-responsive.gif
[image my_website_responsive_highlight]: /blog/src/img/2016-01-09-my-website-responsive-highlight.gif