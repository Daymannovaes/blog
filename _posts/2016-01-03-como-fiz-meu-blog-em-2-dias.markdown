---
layout: post
title:  "Como fiz meu blog em 2 dias - Parte 1: Jekyll e GitHub Pages"
image_list: /blog/src/img/2016-01-03-como-fiz-meu-blog-em-2-dias.png
comments: true
description: >
  Por algum<small>s</small> motivo<small>s</small> resolvi fazer um blog.
  Talvez por não ter nada para fazer, mas alguns amigos me influenciaram e agradeço o apoio.
  Já que estou aqui, porque não compartilhar como eu fiz o dito cujo <small>só a parte legal</small>?
---

Olá, se você chegou até aqui, você está <span class="line-crossed">louco</span> com sorte. Este é um post que explica por alto como fiz este blog. <small>é um "clássico" começar assim né?</small>

Mas por que <strong>2 dias</strong>? Porque no processo descobri e utilizei algumas tecnologias que me ajudaram muito no processo, e que podem ser muito úteis para você, mesmo que não pretenda fazer um blog.

Primeiro de tudo, estas são algumas das tecnologias usadas: <br> <small>fique tranquilo caso não conheça alguma, com certeza farei um post explicando cada uma</small>.

 * [Jekyll]
 * [GitHub Pages]
 * [Sass]
 * [Bootstrap 4]

<span class="center-horizontal">
	![html code][image html_code]
</span>

Desculpem pela imagem clichê utilizada, mas ela me lembra o quanto Jekyll me ajudou e facilitou para a modularização do código do blog, algo essencial para se acelerar o desenvolvimento. 

Só para se ter uma ideia, vejam um exemplo do template default do meu blog:

{% highlight html %}
<!DOCTYPE html>
<html>
  {% raw %}{% include head.html %}{% endraw %}
  <body>
    {% raw %}{% include header.html %}{% endraw %}
    <main>
      {% raw %}{{ content }}{% endraw %}
    </main>
    {% raw %}{% include footer.html %}{% endraw %}
  </body>
</html>

{% endhighlight %}

Para quem já é familiarizado com desenvolvimento web, sabe que em páginas html não é simples nem comum essa separação de elementos de forma que se possa incluí-los depois. Geralmente, o código de uma página fica em um único arquivo, ou modularizado mas ficando a cargo do browser de juntar as partes <small>como acontece com o Angular.js por exemplo</small>, o que atrasa um pouco o carregamento da página. 

Com <strong>Jekyll</strong>, ele próprio se responsabiliza por compilar tudo em uma única página estática. <strong>Facilita o desenvolvimento e de forma transparente para o leitor.</strong>

<span class="two-images join">
	<span>
		![jekyll logo][image jekyll_logo]
	</span>
	<span>
		![github logo][image github_logo]
	</span>
</span>

Quem também facilita o desenvolvimento com o Jekyll é o GitHub Pages. Para quem não conhece, [GitHub] é uma ferramenta de revisão e gerenciamento de código open source e projetos privados.

O GitHub Pages permite hospedar páginas estáticas e de graça de repositórios no GitHub. Para quem quer colocar no ar um site que não depende de servidor ou banco de dados, é ideal, pois é simples e de graça.

Inclusive o meu [site pessoal] está hospedado no GitHub, mas o que nunca imaginei <small>até começar esse blog</small>, é que o GitHub <strong>sempre</strong> disponibiliza as páginas rodando um build do Jekyll. 

<span class="center-horizontal">
	![my website][image my_website]
</span>

O que isso significa? Em outras palavras: Lembra que eu disse que com Jekyll é possível separar uma página html em diferentes arquivos e ele se encarrega de compilar e gerar a página completa? 
Ao invés de se hospedar a página gerada, podemos hospedar nosso código em Jekyll que o GitHub se responsabiliza de compilar e disponibilizar o compilado.

Isso acelera e facilita o desenvolvimento por exemplo, ao permitir que você escreva um post do celular, e o envie diretamente para o repositório.

O Pages também permite a utilização de URL<small class="clear">s</small> customizadas ao invés da padrão, caso contrário, você só conseguiria accessar esse blog através de [daymannovaes.github.io/blog] e, caso tenha acessado esse link, percebeu que foi direcionado para [me.dayman.io/blog].

Se você tem ou já teve um domínio pessoal, já é familiarizado com os [DNS Records], para fazer essa ~mágica, precisei criar um record to tipo `CNAME` no repositório do blog no GitHub com o texto:


{% highlight html %}
  blog.dayman.io
{% endhighlight %}

Sim, apenas uma linha. E você pode notar que é um link diferente do usado nesse blog, e que se acessá-lo, será redirecionado para cá. Eu não coloquei <strong>me.dayman.io/blog</strong> no `CNAME` simplesmente porque não posso, ele não permite caminhos após o link.

Então porque simplesmente não deixei <strong>blog.dayman.io</strong>? Na verdade eu não lembro, mas a resposta que posso te dar agora é porque não quero. Então configurei outro record para redirecionar `blog.` para `me.`.

A ~mágica termina configurando um último record no seu gerenciador de DNS <small>que no meu caso é o AWS a Amazon</small>, também do tipo `CNAME`, e que aponta a sua URL customizada para a URL padrão do github, que no meu caso ficou como

| name | type | value |
|:------:|:------:|:-------:|
| me.dayman.io. | CNAME | daymannovaes.github.io |

<hr>

A explicação das tecnologias ficou um pouco superficial, mas a ideia é depois fazer um post exclusivo sobre cada um, com mais exemplos e tudo mais. A continuação da série, na qual explico sobre Sass e Bootstrap <a href="/blog/post/como-fiz-meu-blog-em-2-dias-parte-2/">está aqui</a>.

Qualquer dúvida, sugestão e crítica, sintam-se à vontade.


[Jekyll]: http://jekyllrb.com/
[GitHub Pages]: https://pages.github.com/
[GitHub]: https://github.com/
[Sass]: http://sass-lang.com/
[Bootstrap 4]: http://v4-alpha.getbootstrap.com/
[site pessoal]: http://me.dayman.io
[daymannovaes.github.io/blog]: http://daymannovaes.github.io/blog
[me.dayman.io/blog]: http://me.dayman.io/blog
[DNS Records]: https://en.wikipedia.org/wiki/Domain_Name_System

[image html_code]: /blog/src/img/2016-01-03-como-fiz-meu-blog-em-2-dias-big.png
[image jekyll_logo]: /blog/src/img/jekyll-logo-light-solid.png
[image github_logo]: /blog/src/img/github-logo.png
[image my_website]: /blog/src/img/2016-01-03-my-website.gif