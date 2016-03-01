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

E considere os <strong>mistérios insolúveis</strong> como licença poética.

Não que eu ache que eu chegue aos pés desse maravilhoso personagem, mas eu estava <strong>falando de mim</strong>, nesse exato instante, enquanto escrevo esse texto.

Nesse texto, vou contar da minha primeira experiência profissional e como ela me ajudou a desenvolver a <del><small>estranha</small></del> habilidade de encontrar erros em códigos, com o auxílio de incríveis ferramentas de debug. Meu trabalho era <strong>encontrar e consertar erros de usabilidade</strong> no software usado pela empresa, e isso era bem parecido com um trabalho investigativo, pois encontrar esses erros nem sempre era tão fácil.

E em vários momentos eu me sentia um verdadeiro Sherlock Holmes ao solucionar mais um misterioso bug.

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

<div style="text-align:center">
  <div>
  	<input type="text" id="input-exemple-1" placeholder="Digite aqui..." />
  </div>
  <div>
  	<span id="span-exemple-1" style="border: 1px solid black; padding: 0px 6px; display: inline-block; min-height: 34px; margin-top: 10px;"></span> </div>
</div>
<script type="text/javascript">
	var input = document.getElementById('input-exemple-1');
	var span = document.getElementById('span-exemple-1');

	input.oninput = function() {
		span.innerHTML = this.value;
	}
</script>

Você cria o input, cria o código e quando vai testar... Não funciona. Meu deus, porque será?! Como vamos resolver esse problema? Calma amigo. Lembra? Calma. 

Há <strong>infinitas</strong> causas para não ter funcionado, umas delas:

 * Seu browser está com algum problema de renderização
 * Os pixels da tela do seu computador pararam de funcionar exatamente na área que deveria aparecer o texto
 * Você está sonhando e a lógica não funciona direito
 * O código que te ensinaram na faculdade/curso na verdade era falso, e não funciona no mundo real
 * Formigas comeram uma parte do circuito do seu computador que impediu a comunicação com o campo de texto

São explicações completamente improváveis, certo? Mas elas poderiam muito bem acontecer. Mas ainda são bem improváveis, por isso, vamos descartá-las e pensar em algo mais provável, ok?

Esse tipo de reflexão é importante, porque há momentos que simplesmente não entendemos porque algo não funciona na nossa aplicação. E isso provavelmente acontece porque estamos com algum preconceito, ou algum pré suposição nos impedindo de enxergar algo.

Então esse é o primeiro ponto a ser considerado.

<span class="center-horizontal">
  ![keep calm][image keep calm]
</span>


<h4>
  Suposições prováveis e a busca reversa <i class="fa fa-search"></i>
</h4>

Para fazer suposições, primeiro precisamos conhecer um pouco do funcionamento. Se um prédio está prestes a ruir, por exemplo, você, programador, provavelmente não faz nenhuma ideia de por onde começar a procurar a causa.

Sabemos que para fazer a nossa "caixa copiadora", precisamos de:

 * Selecionar o elemento <small>html</small> campo de texto
 * Selecionar a caixa que conterá o texto
 * A cada vez que o conteúdo do campo mudar, pegar o seu valor e colocar na caixa

Isso já nos ajuda a fazer algumas suposições mais prováveis de porque não funcionou, que envolvem esses passos, entre elas:

 * O elemento html selecionado está errado
 * Não estamos conseguindo "capturar" o momento que o valor muda, isto é, o evento correto do campo de texto
 * Nossa função que troca o conteúdo está com algum erro de execução

Com algumas sugestões em mente temos pelo menos um guia na hora de procurar o erro e não navegamos mais à deriva como se fossemos programadores tentando encontrar um erro na construção de um prédio.

Esse caso da caixa copiadora é um exemplo simples, mas para projetos mais complexos, essa forma de pensar não nos leva diretamente para a solução do problema, mas devemos lembrar que sempre precisamos ter calma.

Essa abordagem, que chamarei aqui de <strong>busca reversa</strong>, nos leva a investigar o caso pelo fim, pelas consequencias, pelo o que se manifesta, mas em direção à origem e à causa.

<h2>
  Ferramentas
</h2>
![tools][image tools]

Uma ferramenta que todo desenvolvedor frontend deve conhecer e dominar é o <strong>Chrome Developer Tools</strong> <small>se você usa o Chrome, claro. Caso você não use, passe a usar</small>.

O Dev Tools também existe nos outros browsers e, pelo o que pude perceber, tendem a seguir o mesmo padrão de funcionamento. Aqui mostrarei apenas exemplos do Chrome, mas como vivemos num país livre, pode escolher o de sua preferência.

Para abrir essa maravilhosa ferramenta, você pode apertar <strong>f12</strong> ou <strong>control</strong>+<strong>shift</strong>+<strong>j</strong>. Um comando que também utilizo bastante <small>e que consequentemente abre o dev tools também</small> é o <strong>control</strong>+<strong>shift</strong>+<strong>c</strong>. Se você usou esse último comando, talvez tenha percebido que os elementos da página são destacados à medida que você vai passando o mouse. Essa é uma funcionalidade legal e chamamos de <strong>inspecionar elemento</strong>.

<span class="center-horizontal">
  ![dev tools 1][image dev tools 1]
</span>

Note no canto superior esquerdo, logo abaixo do símbolo do Chrome, e do lado do símbolo do celular, está vendo um símbolo azul? Então, esse é o símbolo do inspecionar elemento, e ele está azul indicando que está ativado.

Isso é interessante para ver o tamanho e as margens dos elementos, e também para encontrá-lo na <strong>árvore de elementos</strong> dentro do dev tools, para observá-lo com mais detalhe.

Falando em árvore de elementos, está vendo que há várias abas no topo? E que a que está selecionada na imagem é a de <strong>elementos</strong>? Então, essa aba mostra os elementos <i>HTML</i> da página em detalhes, com o <i>CSS</i> aplicado a cada um e com possibilidade de edição em tempo real. Se você está editando o CSS de algum elemento, é o local mais indicado, pois você consegue ver em tempo real. Depois de terminado, <strong>não se esqueça</strong> de copiar o código e salvar no seu arquivo de estilo!

Ufa! Só o Dev Tools é assunto para um post inteiro! Por isso gravei um vídeo rápido <small>sério, tentei ser o mais conciso <small>palavra estranha</small> o possível</small> explicando alguns conceitos legais.


[image sherlock_221b]: /blog/src/img/2016-02-15-sherlock-221b.jpg
[image enxaqueca]: /blog/src/img/2016-02-15-enxaqueca.jpg
[image keep calm]: /blog/src/img/2016-02-15-keep-calm.jpg
[image tools]: /blog/src/img/2016-02-15-tools.jpg
[image dev tools 1]: /blog/src/img/2016-02-15-dev-tool-1.jpg