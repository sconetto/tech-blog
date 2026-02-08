+++
title = "Minha Experiência com _Vibe Coding_"
author = "João Pedro Sconetto"
date = "2026-02-08T21:25:25+01:00"
description = "Minha opinião pessoal sobre a codificação com IA: o que há de bom, ruim e péssimo nela."
cover = "/img/ai-coding.jpg"
translationKey = "pt-br"
tags = ["ai", "vibe-coding", "cursor", "engenharia-software", "opinião"]
keywords = ["vibe coding", "ai coding", "cursor", "engenharia de software", "inteligência artificial", "geração de código"]
+++

Eis que estou adicionando mais uma página na internet à lista interminável de pessoas falando sobre IA, código e o que parece ser uma palavra da moda que não dá para ignorar: _vibe coding_ (deixar a IA codificar para você enquanto você relaxa e observa). Mas, antes de tudo, minha intenção com este post não é (_apenas_) elogiar, reclamar, idolatrar ou mesmo empurrar goela abaixo de todo mundo como se fosse a melhor coisa desde a invenção do chuveiro elétrico. É principalmente compartilhar um pouco do meu ponto de vista sobre o que há de bom nisso, o que não é tão bom e o que possivelmente é “_ruim_”, chame-o [the good, the bad, and the ugly](https://pt.wikipedia.org/wiki/The_Good,_the_Bad_and_the_Ugly).

## Definindo o ponto de partida

Pessoalmente, a melhor maneira de começar a descrever minha experiência com tudo isso é também descrever o que eu entendo sobre o assunto. Dando espaço ao meu lado pesquisador, talvez eu deva começar com algumas definições antes de passar para minha descrição pessoal.

### O que é uma IA?

> <cite>"Inteligência artificial (IA) é uma tecnologia que permite que computadores e máquinas simulem o aprendizado, a compreensão, a resolução de problemas, a tomada de decisões, a criatividade e a autonomia dos seres humanos."[^1]</cite>¹

Uma maneira mais simples de pensar sobre isso é também revisar a série de conceitos derivados que surgiram nos últimos 70 anos:

1. (1950) Inteligência Artificial (IA): Inteligência humana exibida por máquinas.
2. (1980) _Machine Learning_ (ML): Sistemas de IA que aprendem com dados históricos.
3. (2010) _Deep Learning_ (DL): Modelos de aprendizado de máquina que imitam o funcionamento do cérebro humano.
4. (2020) IA Generativa (Gen AI): Modelos de aprendizado profundo (modelos base) que criam conteúdo original.

Em última análise, por trás do que atualmente chamamos de IA está o aprendizado de máquina, que envolve a criação de modelos por meio do treinamento de um algoritmo para fazer previsões e/ou tomar decisões com base em dados históricos ou em base a um conjunto de dados de treinamento. Tudo isso é feito com o objetivo de obter, no final do processo, uma _máquina_ capaz de fazer inferências com base em dados sem ser explicitamente programada para tarefas específicas.

Existem muitos tipos de técnicas e algoritmos de aprendizado de máquina (ML). Se você estiver interessado em aprender ou compreender mais a fundo como essas técnicas funcionam ou como você mesmo pode começar a construir uma _IA_, recomendo começar por este [Módulo do Curso de Conceitos de ML][google-ml-concept-course] (em inglês) do Google. Não estou sendo pago pelo Google para encaminhar vocês ao conteúdo deles, nem estou dizendo que este é o lugar definitivo para aprender sobre o assunto. Eu mesmo aprendi com diferentes fontes, mas achei que este era um bom ponto de partida com base no que consegui reunir e no que ele oferece.


### O que é uma IA? (Mas na minha perspectiva)

Bem, correndo o risco de parecer estúpido e/ou simplista demais, gosto de pensar que as IAs nada mais são do que máquinas de estado que calculam, com base em seus dados de treinamento, qual é o resultado mais provável para a entrada que você está fornecendo (no caso da IA generativa). Não acho que esteja completamente errado, mas definitivamente também não estou completamente certo, então deixe-me explicar:

- As IAs são algoritmos que leem uma entrada, processam essa entrada por meio de uma série de transformações matemáticas e, em seguida, geram uma saída/resultado.
- Com essa saída/resultado, o código tenta categorizá-la com base no que viu anteriormente.
- Com base nisso, o algoritmo verifica se estava certo ou errado (ou se estava longe ou perto da resposta “correta”), alimentando-se dessa informação e passando-a para a “próxima geração”.
- Esse processo continua até que o responsável por essa IA esteja satisfeito com a precisão do modelo (a máquina de estados final, com seus pesos determinados para processar entradas em saídas/resultados).

Dito isto, sinto-me obrigado a fazer a seguinte advertência:

> **Este é um post de opinião e, embora eu tente citar fontes para algumas das informações que estou escrevendo aqui, sou um ser humano, com vieses e suscetível a cometer erros, interpretações equivocadas e afirmações totalmente estúpidas. Eu sempre, 100% das vezes, recomendo que você faça sua própria pesquisa e construa seu próprio conhecimento sobre o assunto, então fique à vontade para discordar de mim!**

Agora, com o coração mais leve após a advertência desta seção, vamos seguir em frente.

## Minha experiência com IA no trabalho e na vida pessoal

Minha primeira tentativa de entender as IAs e aprender mais sobre o assunto (indo além do nível superficial) foi há cerca de 7 anos, em meados de 2019, quando fiz uma disciplina nos últimos anos do meu bacharelado em Engenharia de Software na UnB (Universidade de Brasília). Foi quando programei [Kara][kara-github] e [bAIch][baich-github] (o segundo foi um pouco mais tarde, porque gostei muito da matéria e era bastante fácil tirar uma boa nota, então fiz novamente, não conte a ninguém).

Se você está se perguntando, sim, eu dei o nome para ambos os projetos. *Kara* foi inspirado na personagem de [Detroit: Become Human][detroid-become-human], que eu achei muito adequado para o tema, e *bAIch* foi um trocadilho besta com AI e Bach, de Johann Sebastian Bach, o compositor.

Naquela época, aprendi principalmente sobre aprendizado de máquina (ML: _machine learning_), redes neurais, algoritmos e uma boa quantidade de fórmulas matemáticas. Então, com base nisso, começamos a trabalhar para construir IAs incompletas com nossos colegas de universidade, sem ter hardware que chegasse nem perto de algo inteligente o suficiente para impressionar um aluno da 5ª série. No entanto, hoje entendo que o objetivo final não era construir IAs incríveis, estávamos lá para aprender e, por isso, tentamos (e espero que tenhamos conseguido).

Avançando alguns anos, vejo-me diante do ChatGPT 3.5, se bem me lembro, e não conseguia deixar de pensar nele como um truque de festa ou algo que poderia gerar algum tipo de texto com algum sentido. Para mim, era um gerador de Lorem Ipsum com frases que podiam ser lidas. A essa altura, imagino que já havia muitas pessoas usando-o para gerar e-mails, documentos ou para estudos e perguntas, mas eu ainda estava muito cético quanto à sua utilidade e muito incerto sobre como poderia usá-lo em minha vida cotidiana. Acho que estava muito preocupado com a covid ou outra coisa qualquer para dar toda a minha atenção a ele.

Naquela época, achei que nunca se tornaria algo importante, mas estava muito enganado e, por causa disso, nunca me senti “_responsável_” por usá-lo mais ou tentar integrá-lo ao meu trabalho/rotina.

Passado mais um ano, não pude deixar de ouvir falar disso em todo o lado, ver as pessoas a considerá-lo como a próxima fase da revolução industrial, etc., como tudo era IA, que iria substituir as pessoas e que ficaríamos sem emprego por causa disso. Acredito que, a essa altura, você provavelmente também já tinha ouvido falar isso. Esse peso repentino me deixou um pouco relutante em usá-la mais, de alguma forma tudo parecia ser empurrado na nossa cara e um ultimato do tipo “ou você usa ou logo estará desempregado”. Todo esse sentimento me fez adotar a IA mais tarde em meu fluxo de trabalho e, após alguma luta interna, comecei a usá-la, mas principalmente para revisar ou criar conteúdo, como e-mails, documentação para processos e outros fluxos de trabalho menores relacionados a perguntas e pesquisas.

## Momento crítico

Minha relação geral com as IAs começou a mudar de verdade quando, no ano passado, mudei de emprego. Ao entrar para a nova equipe, descobri que a empresa oferecia a todos os engenheiros o [Cursor][cursor], um IDE baseado no Visual Studio Code, mas com recursos de IA integrados. Na versão paga, ele tem modelos para gerar código, documentação, executar, depurar e tudo o que seu coração tecnológico deseja criar (talvez você possa usar isso na versão gratuita, mas com limitações significativas ou precisando trazer sua própria chave API).

Então, imagine o seguinte cenário:

1. Você é novo no local de trabalho e ainda não viu o código/arquitetura deles;
2. Você precisa fazer algumas correções e alguns desenvolvimentos já no primeiro dia;
3. Você está tentando causar uma boa impressão ao desenvolver sua primeira tarefa.

Ao mesmo tempo em que você está se esforçando, tudo fica um pouco mais difícil porque você ainda está tentando entender o código-fonte, a arquitetura, as pessoas, os sistemas e como tudo se conecta. Era assim que eu me via naquele novo ambiente, tendo acesso a uma ferramenta que, francamente, eu não tinha usado muito antes (não realmente para codificação) e navegando por tudo isso. Resumindo, entreguei a tarefa, embora na época não tivesse certeza se estava usando a ferramenta em todo o seu potencial e se a tarefa estava bem codificada. Implementamos a nova _feature_ em produção, recebemos alguns comentários para melhorias e, finalmente, me senti um pouco mais confortável em entender minhas novas ferramentas e os sistemas com os quais trabalho. Desde então, tenho usado muito mais a IA em minhas atividades diárias.

## Por que eu quis escrever esse artigo e minha avaliação em IA/_Vibe Coding_

Agora, após quase seis meses no meu novo emprego e usando IA diariamente, eu me sinto bastante confortável usando o cursor e acessando alguns modelos para me ajudar a resolver problemas em algumas tarefas. Cada vez mais, eu a o utilizo para gerar código, explicar bases de código e simplesmente me ajudar a planejar em como lidar com algumas questões de codificação. O que percebi ao usá-lo foi que meu fluxo de trabalho mudou completamente, passando de codificar, testar e enviar para um PR para que alguém pudesse revisar, para escrever minha intenção, revisar o código de “_outra pessoa_”, testar e assim por diante. É claro que, de vez em quando, era necessário reescrever algum código ou reinserir algo no _prompt_ porque não tinha sido bem feito, mas, no final das contas, percebi que estava escrevendo menos código e revisando mais a implementação dos modelos de IA. Como você pode imaginar, o que ele gera às vezes é muito ruim, mas essa mudança no fluxo de trabalho me tornou muito mais eficiente, pois ele conseguia produzir mais do que eu jamais conseguiria com meu teclado em WPM (_palavras por minuto_).

Algumas das tarefas relativamente simples, ou correções rápidas de bugs, tornaram-se _vibe coding_ completo, basta digitar o _prompt_, informar o que precisa ser alterado, "_commitar_" e, em seguida, abrir o PR (use _vibe coding_ com moderação).

### _"Here Comes a New Challenger"_

Percebendo essa mudança no meu fluxo de trabalho, não demorei muito para ter a seguinte ideia: “E se eu retomasse uma ideia antiga que nunca levei adiante?”

Na minha cabeça estava claro: havia muitas ideias de programação que nunca saíram do papel porque exigiam que eu aprendesse novos _frameworks_ ou linguagens de programação. Embora seja algo que eu realmente goste de fazer, quanto mais velhos ficamos, mais difícil é encontrar tempo para fazer tudo o que queremos. Então, arrisquei colocar uma dessas ideias em prática com minha recém-descoberta habilidade de escrever o que eu queria que fosse feito e transformá-lo em um software.

Comecei então a programar um aplicativo no Flutter/Dart para ser um companheiro para pessoas que praticam o budismo. A principal característica é permitir e ajudar as pessoas a recitar o <cite>_Daimoku (題目)_[^2]</cite>, que é a prática central do budismo Nichiren, envolvendo o canto repetido de “Namu Myōhō Renge Kyō” para manifestar a natureza búdica inata de cada um.

Até este momento, eu tinha um total de 0 horas de experiência com Flutter/Dart. Lembro-me apenas de ter lido sobre na universidade, quando programei alguns aplicativos multiplataforma em Ionic/React-Native. Eu tinha um plano e uma visão de onde ir, além do meu _prompt_ e algumas horas livres no fim de semana. Depois de muitos testes, pesquisas e _prompts_, cheguei a este resultado:

#### Homepage

{{< figure src="/img/vibe-coding/screenshot-1.png" alt="Pré-visualização da <i>Homepage</i>" position="center" caption="Pré-visualização da <i>Homepage</i>" captionPosition="center" >}}

#### Perfil

{{< figure src="/img/vibe-coding/screenshot-2.png" alt="Pré-visualização do Perfil" position="center" caption="Pré-visualização do Perfil" captionPosition="center" >}}

#### Página de recitação

{{< figure src="/img/vibe-coding/screenshot-3.png" alt="Pré-visualização da página de recitação (Gongyo)" position="center" caption="Pré-visualização da página de recitação (Gongyo)" captionPosition="center" >}}

---

Devo dizer que, para ser a minha primeira vez a trabalhar com Flutter/Dart, fiquei muito orgulhoso do que consegui alcançar com algumas horas de _vibe coding_, estava agradavelmente surpreendido com o que consegui obter da ferramenta e, para um protótipo rápido de uma ideia, já a funcionar direto do meu próprio smartphone, foi incrível!

Além disso, minha esposa, que também trabalha na área de TI, ficou impressionada com a qualidade da primeira versão de depuração, os elementos da interface do usuário, as cores, os recursos, e até ficou animada para me ajudar com isso. Na minha opinião, essa é uma das melhores coisas que a IA/_vibe coding_ pode nos oferecer.

> Caso você queira ver o código-fonte (que não é nada bom, pois ainda estou aprendendo Flutter/Dart), consulte o repositório GitHub do aplicativo: [sconetto/iBuddhism][ibuddhism]

## _The good, the bad, and the ugly_ (mais a conclusão)

Agora, não me interpretem mal, embora eu tenha ficado muito feliz com o resultado da experiência, ela não foi isenta de problemas, depuração, solicitações para corrigir erros e instruções à IA sobre onde procurar para corrigir seus próprios erros. Acho que há valor a ser extraído de tudo isso, o que resumo como minha opinião pessoal:

### "_The good_"

O código feito por IA ou _vibe coding_ é uma ferramenta e, se usado corretamente, pode ser uma excelente adição ao seu conjunto de ferramentas. Ele permite que você produza mais e se concentre na revisão/teste, deixando de lado as longas horas de codificação antes de ter uma primeira versão de algo. Ele pode revisar rapidamente bases de código e dar sentido ao que está vendo para você avaliar. Para alterações superprecisas e superfocadas, ele permite até mesmo que você digite o _prompt_ correto e vá tomar um café enquanto ele faz as atualizações necessárias no código, o que, sejamos honestos, é ótimo!

Em análise, baseado em minha opinião, as ferramentas de IA para codificação tendem a impulsionar o tipo de engenheiro/desenvolvedor que você já é e, se bem utilizadas, você pode se tornar uma máquina de produtividade, resolvendo problemas como nunca antes. Além de tudo isso, elas também reduzem a barreira de entrada para novas linguagens/_frameworks_ de programação. Sendo honesto novamente, somos engenheiros, conhecemos a lógica e sabemos o que estamos tentando alcançar, mas saber se, para essa sintaxe específica, preciso adicionar um ponto-e-vírgula ou não, ou se posso iterar sobre um objeto em vez de usar um _for-loop_, tudo isso pode ser bastante demorado (e chato). A IA permite que você se torne o revisor enquanto aprende a sintaxe (há uma armadilha nisso que mencionarei mais tarde).

### "_The bad_"

A principal razão pela qual devemos ter cuidado com a IA para codificação: ela pode nos transformar em engenheiros/desenvolvedores preguiçosos.

Acredite, eu sei que é muito mais simples dizer a si mesmo que você escreve bons _prompts_ e que testou o fluxo de _feature_ com o código gerado, que você maximiza a eficiência e se torna um _pure vibe coder_ (a IA faz tudo), que você apenas faz _prompts_ e testes, e mesmo que isso funcione algumas vezes, também falhará muitas outras vezes. A código gerado por IAs está melhorando enquanto você lê este post, e não tenho dúvidas de que ficará cada vez melhor com o tempo, mas, entre nós dois, às vezes ela pode gerar um código tão ruim que até você, na época da universidade, era capaz de escrever uma lógica/sintaxe melhor, então você deve resistir à vontade de apenas fazer _vibe coding_ o tempo todo! Não revisar o que foi gerado, não testar todo o fluxo da _feature_ tentando detectar casos extremos (_edge cases_), confiar que não está gerando código ruim, fará com que você caia, e com força. Você perderá seu fim de semana para corrigir um bug de produção que foi lançado sem que ninguém percebesse, ainda mais se sua empresa (ou você) também estiver usando IA para revisar PRs, então o ciclo estará completo.

### "_The ugly_"

Como mencionei no início, acredito realmente que as IAs são máquinas estatísticas, e os dados com os quais são treinadas podem prever que a próxima melhor linha de código para o que você está escrevendo é algo péssimo que tornará o software propenso a problemas ou até mesmo inseguro, porque já viu isso muitas vezes. O segredo aqui é “confiar, mas verificar”.

Acrescente a isso alguns preços quase absurdos para as ferramentas (como Cursor, Claude Code) ou para os modelos (ChatGPT, Gemini, etc.), e você ficará sem tokens ou preso a uma assinatura que custará mais quanto mais você usar a IA. Acho que sou uma pessoa de sorte, já que minha empresa nos oferece o Cursor para trabalhar em nossas atividades, mas também estou ciente de que nem todos têm a mesma sorte.

Por último, gostaria de mencionar a armadilha que mencionei anteriormente: enquanto trabalhava no meu projeto Flutter/Dart, eu sempre mencionava nas minhas instruções que ele deveria seguir os padrões do _framework_ e as melhores práticas de codificação, mas havia muito código ruim na geração. Até certo ponto, se eu mesmo não me aprofundar para entender como é um código limpo no Flutter/Dart, meu código continuará alimentando práticas ruins até que eu resolva tomar as rédeas da situação. Para mim, essa é uma das piores coisas que a codificação por IA acrescenta como desafio para nós (o ciclo interminável de códigos ruins treinando IAs para gerar mais códigos ruins), sendo uma das principais razões para dizer que devemos sempre verificar.

### Conclusão

É bastante irracional não usar essas ferramentas, pois elas trazem pontos e qualidades positivas para o nosso dia a dia e podem ser, para você como foram para mim, uma forma de diminuir a barreira para experimentar coisas novas e dar andamento àquele projeto de programação que está parado. Negar a IA é negar a mudança que moldará como somos e seremos percebidos como engenheiros de software. No entanto, não se iluda pensando que a IA resolverá tudo e que você nunca mais terá que escrever outra linha de código na vida (ou que qualquer pessoa pode criar um software excelente com ela). Estamos um pouco distantes dessa realidade e, na minha opinião, no futuro, a diferença entre um bom e um ótimo engenheiro/desenvolvedor será aquele que não confia que um software produtivo seja definido por uma ferramenta, mas usa a ferramenta para se ampliar e melhorar seu software.

## Fontes

Foto da capa por <a href="https://unsplash.com/@dkomow?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Daniil Komov</a>

[^1]: O que é inteligência artificial (IA)?. Stryker, Cole. Kavlakoglu, Eda. IBM Website. [Source][ibm-what-is-ai]
[^2]: _Namu Myōhō Renge Kyō_. [Source][daimoku-wiki]

[ibm-what-is-ai]: https://www.ibm.com/br-pt/think/topics/artificial-intelligence
[google-ml-concept-course]: https://developers.google.com/machine-learning/crash-course/neural-networks
[kara-github]: https://github.com/deeplearningunb/kara
[baich-github]: https://github.com/deeplearningunb/baich
[detroid-become-human]: https://pt.wikipedia.org/wiki/Detroit:_Become_Human
[cursor]: https://cursor.com/
[daimoku-wiki]: https://en.wikipedia.org/wiki/Namu_My%C5%8Dh%C5%8D_Renge_Ky%C5%8D
[ibuddhism]: https://github.com/sconetto/iBuddhism
