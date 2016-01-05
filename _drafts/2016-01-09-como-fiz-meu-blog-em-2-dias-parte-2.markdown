---
layout: post
title:  "Como fiz meu blog em 2 dias - Parte 2: Bootstrap e Sass"
image_list: /blog/src/img/2016-01-09-como-fiz-meu-blog-em-2-dias-parte-2.jpg
comments: true
description: >
  Já conhecia essas duas ferramentas, mas aprendi algumas coisas legais durante o desenvolvimento do blog e gostaria de contar para vocês! Olha aqui e me conte o que achou.
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

Bootstrap é um framework em CSS <small>principalmente</small> para desenvolvimento responsivo. Ele possui várias classes utilitárias prontas, tanto para facilitar que seu site fique responsivo <small>você pode abrir esse blog no celular que ele fica bonitinho &hearts;</small>, quanto para componentes, como por exemplo botões, com a classe `btn`:

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

Agora falando sobre layout responsivo, 

<h3>
  MOSTRA GIF DOS POSTS SE AJEITANDO E DA IMAGEM SUMINDO
</h3>

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

  <li>
    depois falar das imagens que não carregam em extra small pra nao consumir banda
  </li>
</ul>

<img src="/blog/src/img/Captura de Tela (17).png">

[image sass_boostrap]: /blog/src/img/2016-01-09-como-fiz-meu-blog-em-2-dias-parte-2.jpg