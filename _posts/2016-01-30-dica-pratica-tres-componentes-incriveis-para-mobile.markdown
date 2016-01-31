---
layout: post
title:  "<span class='tag'>#DicaPrática</span> Três técnicas e componentes incríveis para o seu site ficar (ainda mais!) responsivo"
image_list: /blog/src/img/2016-01-30-tres-componentes-rapidos.png
color_list: E0AC18
comments: true
description: >
  Essa #dicaPrática mostra algumas técnicas e componentes capazes de te dar insights para elevar a responsividade de seu site à outro nível.
twitter_text: Adorei essas dicas de CSS! Ótimo post, recomendo!
---

<style type="text/css">
  .nome {
    margin-bottom: 30px;
  }
  .nome:after {
    content: ' Novaes';
  }
  .nome:before {
    content: 'Dayman ';
  }
</style>

Como você deve ter percebido pelo título <small>se você não percebeu, por favor procure um oculista rápido! <small>e depois volte pra ler meu blog &hearts;</small></small>, tem uma parte amarela alí indicando que esse post:

 * Fará parte de uma série/hastag/sequência intitulada de <strong>Dica Prática</strong>
 * Será mais curto e direto, facilitando a leitura
 * Será prático! Facilitando a sua implementação

Se você <del>estava em coma</del> <ins>não sabe o que significa um design responsivo</ins>, eu falo um pouco sobre isso no meu <a href="/blog/como-fiz-meu-blog-em-2-dias-parte-2/">segundo post.</a> Mas é basicamente um design que se adequa à diferentes tipos de tela.

Os exemplos mostrados aqui serão feitos em <strong>Sass</strong> porque <del>eu quero e pronto</del> <ins>facilita muito nosso trabalho</ins>.

<strong>Se</strong> você é programador, <strong>e</strong> não conhece Sass ou outro pré-processador de CSS, como diria o <a href="http://guncast.com.br/" target="_blank">Murilo Gun</a>, você <strong>tá de brincadeira na tomateira</strong>. Levanta a bunda da cadeira <small>metaforicamente, a menos que queira usar o computador em pé</small> e vai logo aprender sobre isso, para o seu próprio bem! Meu <a href="/blog/como-fiz-meu-blog-em-2-dias/">primeiro post</a> conta um pouco das vantagens.

Sem mais delongas:

<h2>1. Mudando o texto com seletor :before e :after</h2>

Essa técnica é uma sacada <strong>muito</strong> boa, e confesso que a tirei do site do meu amigo <a href="http://willianjusten.com.br/ano-novo-blog-novo/" target="_blank">Will</a>.

Se você <del><small class="clear">tá de brincadeira na tomateira</small></del> não sabe o que significa esses `::after` e `::before`, é muito simples. Eles são <strong>pseudo elementos</strong>.

Como o w3schools explica muito bem <a href="http://www.w3schools.com/css/css_pseudo_elements.asp">nesse artigo</a>, esse tipo de seletor é usado para selecionar <strong>partes</strong> de <strong>dentro</strong> de um elemento, como a primeira linha ou a primeira letra.

Os seletores `after` e `before`, além disso, nos permitem inserir um conteúdo antes ou depois do conteúdo do elemento, como a propriedade `content`.

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


O <span class="highlight pre"><span class="k">&</span></span>, no Sass, referencia o seletor pai, no caso, o <span class="highlight pre"><span class="nc">.nome</span></span>. Portanto, esse código diz que a parte "Novaes" só será mostrada para telas maiores que tamanho médio (<strong>m</strong>e<strong>d</strong>ium), e "Dayman" apenas para telas maiores que tamanho pequeno (<strong>sm</strong>all).

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

Eu uso essa técnica no meu site pessoal, na seção de habilidade, onde mostra várias tecnologias com o nome e uma imagem. O nome é incluído desta forma, sendo que em dispositivos mobiles, o texto some e ficam apenas as imagens.

<span class="center-horizontal p">
  <img src="/blog/src/img/2016-01-30-gif-skills.gif" alt="habilidades responsivas">
</span>

<h2>2. Utilitários Sass que podem salvar seu tempo</h2>

Os `mixins` do Sass são ótimos, pois são funções que podemos criar para executar e compilar algum código CSS.

Misturando um pouco com a ideia de <strong>breakpoints</strong> do Bootstrap, podemos criar um mixin que utiliza disso para facilitar e padronizar o desenvolvimento.

Você deve ter percebido que usei no exemplo anterior o <span class="highlight pre"><span class="k">@include</span> <span class="nd">media-query</span><span class="p">(..)</span></span>, e é exatamente ele que vou explicar agora.

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

Calma que vou explicar. Ta vendo a parte amarela desse código aqui?

<div class="highlight pre p"><span class="si">#{</span><span class="nf">map-get</span><span class="p">(</span><span class="nv">$breakpoints</span><span class="o">,</span> <span class="nv">$breakpoint</span><span class="p">)</span><span class="si">}</span></div>

Então, esse é a sintaxe de <i>interpolation</i> do Sass. Interpolation significa algo como trocar, substituir. Significa que, no caso, o Sass pega o valor da chave escolhida (xs, sm, md...) e colocar na propriedade de `min-width`.

<div class="highlight pre p"><span class="n">min-width</span><span class="o">:</span> <span class="si">#{</span><span class="nf">map-get</span><span class="p">(</span><span class="nv">$breakpoints</span><span class="o">,</span> <span class="nv">$breakpoint</span><span class="p">)</span><span class="si">}</span></div>

E dentro das chaves tem um <span class="highlight pre"><span class="k">@content</span></span>, que basicamente pega o conteúdo que você definiu na <strong>chamada</strong> do mixin, e coloca alí.

Exemplificando:

{% highlight scss %}
@include media-query(xs) {
  article {
      max-width: 350px;
  }
}
{% endhighlight %}

Compila para:

{% highlight scss %}
@media (min-width: 22em) {
  article {
      max-width: 350px;
  }
}
{% endhighlight %}

É <strong>simples</strong>, mas <strong>muito útil</strong> para agilizar nosso desenvolvimento.

E se você quiser fazer um mixin que, ao invés do `min-width` da tela utilize o `max-width`, é simples, basta trocar essa propriedade no mixin, usar o mesmo valor do breakpoint mas <strong>subtrair um centésimo</strong>, para que as duas não se confudam quando o tamanho de tela for exatamente aquele.

{% highlight scss %}
@mixin media-query-down($breakpoint) {
  @media (max-width: #{map-get($breakpoints, $breakpoint) - 0.01}) {
    @content;
  }
}
{% endhighlight %}

<h2>3. Modularização inteligente com o Sass</h2>

Modularização não é algo que está diretamente ligada à responsividade, porém é algo tão importante, mas tão importante, que ou você se atenta à isso, ou você se atenta à isso.

Se você não busca organizar e modularizar seu código, tome vergonha na cara e só volte aqui quando refatorar todo o seu projeto.

Vamos lá!

Digamos que você esteja trabalhando com Bootstrap e deseja um componente que em telas grandes ocupe duas colunas, e em telas pequenas ocupe quatro colunas, como é o caso do componente de <i>skill</i> que fiz e exemplifiquei no primeiro tópico. O código ficaria assim:

{% highlight html %}
<div class="col-lg-2 col-xs-4 component-skill">
  ...
</div>
{% endhighlight %}

A classe `.component-skill` seria usada para adicionar estilos diferentes. Mas ao invés de "poluir" o html, podemos torná-lo mais semântico dessa forma:

{% highlight scss %}
.component-skill {
  @extend .col-lg-2;
  @extend .col-xs-4;
}
{% endhighlight %}

Agora, quais são os componentes que têm dentro deste componente? O texto, e a imagem. O html fica, então, intuitivo:

{% highlight html %}
<div class="component-skill">
  <span class="component-skill-title"></span>
  <div class="component-skill-img"></div>
</div>
{% endhighlight %}

Esse é o nosso componente. Simples e modular.

<strong>Vamos agora implementá-lo</strong>.

Se quisermos mostrar nossa habilidade em <a href="https://angularjs.org/">Angular</a>, basta fazer assim:

{% highlight scss %}
.component-skill {
  @extend .col-lg-2;
  @extend .col-xs-4;

  &:angular {
    .component-skill-title:before {
      content: 'Angular';
    }
    .component-skill-img {
      background-image: url(/img/angular-logo.png);
    }
  }
}
{% endhighlight %}

Desta forma, basta adicionar a classe `.angular` no nosso componente, que o seu title conterá o texto "Angular" e o sua imagem terá a logo do Angular.

{% highlight html %}
<div class="component-skill javascript">
  <span class="component-skill-title"></span>
  <div class="component-skill-img"></div>
</div>
{% endhighlight %}

<strong>Mas peraí</strong>...

Adicionaremos manualmente tooodas <small><img src="/blog/src/img/X-All-The-Y-icon.jpg"></small> as habilidades no CSS, mudando nas partes convenientes?

Bom, seria uma forma, mas ainda assim, é claro que podemos modularizar ainda mais. E se criarmos uma lista com as habilidades, e criarmos uma `@foreach` para percorrer cada uma e compilar o código?

Bom, vamos lá então. A lista ficaria algo assim:

{% highlight scss %}
$skills: (
  javascript: "Javascript",
  java: "Java",
  c: "C/C++"
);
{% endhighlight %}


É importante ser do tipo map, e não apenas um array de strings, porque se não não conseguiremos, por exemplo, criar a classe `.C/C++`, pois seria um nome inválido.

A sintaxe do Sass para percorrer um map é simples, seria algo como `@each $skill, $s in $skills`, onde `$skill` corresponde à chave, e `$l` ao valor. Exemplificando, o primeiro seria `c` e o segundo `C/C++`.

A implementação fica assim:

{% highlight scss %}
@each $skill, $s in $skills {
  .component-skill--#{$skill} {
    @extend .col-lg-2;
    @extend .col-xs-4;

    .component-skill-title:before {
      content: '#{$s}';
    }

    .component-skill-img {
      background-image: url(/img/#{$skill}-logo.png);
    }
  }
}
{% endhighlight %}

Note os <strong>três</strong> interpolations que criei. O primeiro é para criar o nome da classe. No caso, é compilado para `.component-skill--javascript`,  `.component-skill--java` e `.component-skill--c`.

E o segundo e terceiro é apenas para preencher e ficar igual àquele exemplo que dei do Angular, mas com os parâmetros de cada linguagem.

Legal né? Faltam apenas alguns detalhes, como a media query no title para sumir com o nome, e algum estilo na imagem para deixá-la arredondada e aumentá-la em mobile.

O <strong>resultado final</strong> fica assim:

{% highlight scss %}
@each $skill, $s in $skills {
  .component-skill--#{$skill} {
    @extend .col-lg-2;
    @extend .col-xs-4;

    @include media-query(sm) {
      .component-skill-title:before {
        content: '#{$s}';
      }
    }

    .component-skill-img {
      border-radius: 50%;

      width: 30px;
      height: 30px;
      
      @include media-query-down(sm) {
        width: 60px;
        height: 60px;
      }

      background-image: url(/img/#{$skill}-logo.png);
    }
  }
}
{% endhighlight %}

É isso, se você gostou, compartilha e se inscreva na lista de email pra receber mais dicas práticas como essa.

E para garantir que você não vai ficar de brincando na tomateira, aqui vai uma foto de um tomate:

<div class="center-horizontal">
  <img src="/blog/src/img/2016-01-30-tomate.jpg" alt="tomate">
</div>