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

E um blog, ou qualquer outro site que preze por uma melhor <strong>experiência de usuário</strong>, deve se preocupar com esses casos e evitar ao máximo carregar coisas pesadas, como grandes <span class="highlight"><span class="nt">scripts</span> ou imagens de alta resolução. É por isso que a imagem some no gif em telas pequenas.

~Mas como você fez isso?~ Você me pergunta. <br>
~Simples, com ajuda do Sass e das Media Query<small class="clear">s</small>~

<h2>
  Usando media query com Sass e Bootstrap
</h2>

Bom, ainda não apresentei o Sass para vocês, mas como a intenção do post não é falar sobre a ferramenta, e sim contar sobre como ela me ajudou a construir o blog, vou pontuar algumas coisas superficiais, mas depois explico com mais detalhes, ok?

Sass é o que chamamos de pré processador de CSS. Se você já tem algum conhecimento de CSS, nunca se perguntou porque até hoje não pode fazer algo desse tipo:

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

No caso do Sass, você pode escrever seletores aninhados como no exemplo, pode utilizar variáveis e também funções. E são exatamente as funções que me ajudaram mais no processo da responsividade.

Antes de continuar, vou falar rapidamente das media querys. Você já imaginou pode escrever um estilo diferente para diferentes tamanhos de tela?

Essa é a função das media querys, e seu funcionamento é bem simples, como vocês podem ver no exemplo:

<h2>media query</h2>

Bom, explicado Sass e media query, é a hora do Bootstrap entrar. 

O Bootstrap define o que ele chama de `breakpoints`, ou ~pontos de quebra. Cada breakpoint define um tamanho específico de tela:

|sigla|nome|device|tamanho|
|:---:|:--:|:----:|:-----:|
|xs|extra small|phones|? 
|sm|small|
|md|medium|
|lg|large|
|xl|extra large|




<br>
<br>

<ul>
  <li>
      carregamento de imagem em mobile
        @include media-query-down(xs) {
          background: none !important;
          background-image: none !important;
        }
  </li>

  <li>
    falar do @include container()
  </li>

  <li>
    falar sobre como deixar o html mais limpo com sass
  </li>
  <li>
    falar das diferenças entre "Helvetica" e "Source Sans Pro"
  </li>
</ul>

<img src="/blog/src/img/Captura de Tela (17).png">

[image sass_boostrap]: /blog/src/img/2016-01-09-como-fiz-meu-blog-em-2-dias-parte-2.jpg
[image my_website_responsive]: /blog/src/img/2016-01-09-my-website-responsive.gif