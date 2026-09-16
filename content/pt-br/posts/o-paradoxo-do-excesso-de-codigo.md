+++
title = "O Paradoxo do Excesso de Código: Por Que a IA é Ótima e Terrível ao Mesmo Tempo"
author = "João Pedro Sconetto"
date = "2026-09-16T10:00:00-03:00"
description = "A IA está nos dando código demais, e o paradoxo de Jevons garante que vamos gastar mais, não menos. Sobre elasticidade e acoplamento invisível."
cover = "/img/too-much-code.jpg"
translationKey = "pt-br"
tags = ["ai", "engenharia-software", "opinião", "tech-debt", "paradoxo-de-jevons"]
keywords = ["codificação com ia", "paradoxo de jevons", "janela de contexto", "lost in the middle", "arquitetura de software", "ai slop", "kantan coding", "dívida técnica"]
+++

Ultimamente eu tenho sentido um incômodo com o código que eu reviso. Entregamos mais rápido do que nunca, e ainda assim eu demoro mais para entender o que está na minha frente. Este é o terceiro post sobre IA neste blog, e eu não planejei uma trilogia.

A tese honesta é essa: a IA está nos dando código demais. Não código _ruim_, essa reclamação está cada vez menos verdadeira. Mesmo quando o código está correto, compila, passa nos testes e faz exatamente o que foi pedido, ainda é em excesso. Isso faz da IA a ferramenta mais poderosa que já tive e a coisa mais provável de enterrar os sistemas pelos quais sou responsável. As duas coisas são verdade ao mesmo tempo.

> **Este é um post de opinião, e apesar de eu tentar trazer fontes para algumas das informações que escrevo aqui, sou um ser humano, com viés e suscetível a cometer erros, interpretações equivocadas e afirmações completamente estúpidas. Vou sempre recomendar, 100%, que você faça sua própria pesquisa e construa seu próprio conhecimento sobre o tema, então sinta-se livre para discordar de mim!**

## O Vídeo Que Reenquadrou Tudo Para Mim

Eu esbarrei em um vídeo do canal Kantan Coding chamado <cite>["The Paradox of Why AI Code Is Failing Us - 3 Pillars"][kantan-video][^1]</cite>, e ele mudou como eu penso sobre esse problema.

{{< youtube k2qls2LiBRc >}}

Ele começa em economia e termina lá dentro de como os _transformers_ funcionam, e a conclusão é um loop que se alimenta de si mesmo: quanto mais código a IA nos ajuda a gerar, maiores ficam nossos sistemas, e mais difícil fica para a própria ferramenta que os gerou entendê-los. Mais IA não resolve. Piora.

## Primeiro Pilar: Código Barato Não Economiza Dinheiro, Compra Mais Código

### A Matemática Ingênua

O primeiro pilar é economia, e começa com o argumento que todo mundo já ouviu: se a IA quadruplica a velocidade de entrega, uma _feature_ de quarenta horas passa a levar dez, então a empresa economiza tempo e dinheiro.

O vídeo modela o _backlog_ como um gráfico de barras 3D onde a altura de cada barra é o valor daquela _feature_. Um _bug_ crítico perdendo clientes é uma barra alta. Pagar débito técnico é uma barra baixa. Aí entra a função de demanda: a $6.000 por _feature_, só duas valem a pena. A $1.000, dezessete valem.

### Elasticidade

Essa sensibilidade tem nome: **elasticidade** (_elasticity_). Para uma empresa de tecnologia moderna, a demanda por _features_ é altamente elástica, ou seja, cresce _mais rápido_ do que o preço cai. E mesmo no caso de baixa elasticidade, o número de _features_ construídas ainda aumenta.

### O Paradoxo de Jevons

Isso é o **paradoxo de Jevons**. Em 1865, William Stanley Jevons notou que máquinas a vapor mais eficientes precisavam de menos carvão por unidade de trabalho, e ainda assim o consumo total de carvão subiu, porque energia mais barata viabilizou usos novos[^2]. O vídeo argumenta que o mesmo está acontecendo com software, e eu acho que ele está certo.

### Por Que os _Backlogs_ Não Encolhem

Eu observo _backlogs_ há anos, e eles não encolhem quando você fica mais rápido. Eles são repriorizados. O tier de _features_ que "não valia a pena" no preço antigo vira o _roadmap_ do próximo trimestre no preço novo. A conclusão desconfortável: as empresas vão gastar substancialmente mais com software, não menos.

## Segundo Pilar: A Janela de Contexto É o Teto

### Como um Modelo Vê Código

Para ler código, um modelo divide o texto em _tokens_, mapeia cada _token_ para um ID, e cada ID é uma linha numa matriz de _embeddings_ com um vetor de alta dimensionalidade. Tokens parecidos ficam perto uns dos outros. Depois, a **attention** (atenção) deixa cada _token_ puxar significado dos anteriores, camada após camada, até o modelo prever o próximo _token_.

### A Janela É o Teto

Tudo isso precisa caber na **janela de contexto** (_context window_), o número máximo de _tokens_ que o modelo aguenta de uma vez. É um limite duro em todos os modelos atuais. E a janela não é uma grade de módulos; é uma linha longa de _tokens_, do começo ao fim.

### Três Modos de Falha

O vídeo mostra três:

1. O modelo altera código dentro da janela e consegue checar contra outros módulos dentro dela, mas não enxerga os de fora.
2. Código novo chama uma função definida fora da janela. O modelo não vê a definição, então chuta o formato do retorno a partir do treinamento. Assuma um dicionário e receba uma lista, e o código quebra de um jeito que ninguém percebe até rodar.
3. O mais sinistro. Uma função que parece O(n) tem um loop que chama uma função fora da janela que também é O(n). Você acabou de subir uma função O(n²), e ela só aparece em escala.

Isso não é o modelo sendo burro. É o modelo não conseguindo _ver_.

## Terceiro Pilar: Por Que "Só Aumentar a Janela" Não Funciona

A resposta óbvia é aumentar a janela. O vídeo explica por que isso também falha.

### _Lost in the Middle_ (Perdido no Meio)

_Lost in the middle_ é um fenômeno documentado: modelos prestam atenção no começo e no fim de um contexto longo e ignoram o que está enterrado no meio, mesmo dentro da janela[^3].

### O Custo da _Attention_

A _attention_ compara cada _token_ com todos os anteriores, o que dá n(n+1)/2 comparações, ou **O(n²)**. Dobre a janela e o trabalho quase quadruplica, e isso se repete em cada consulta.

### _Sparse Attention_ e _Retrieval_

A **sparse attention** faz cada _token_ atender só um subconjunto escolhido, o que é mais barato, mas pares que nunca são comparados são vínculos que nunca são vistos. O **retrieval** coloca a base de código num índice de busca fora do modelo e puxa dependências sob demanda. Parece a solução, até você ver onde quebra.

### O Relatório Noturno Que Ninguém Atualizou

Um código gerado por IA escreve pedidos num banco de dados, com o total e o desconto nas colunas. Fora da janela, um relatório noturno calcula a receita somando totais menos descontos, lendo a tabela direto. Agora peça ao modelo para aplicar o desconto ao total _antes_ de inserir o pedido. Os dois estão acoplados pelo banco, mas nada no código visível referencia o relatório, então não há nada para buscar. O relatório nunca é atualizado e o desconto é subtraído duas vezes. Como o vídeo resume:

> _"Good luck winning back the trust of your accounting team."_
>
> — _Boa sorte reconquistando a confiança do seu time de contabilidade._

As falhas perigosas não são erros de sintaxe. São **acoplamento invisível**, dependências que existem no sistema mas não no código que você enxerga.

## A Parte Em Que a IA É Genuinamente Ótima

Deixa eu ser justo, porque eu uso essas ferramentas todo dia e gosto delas de verdade.

Meu fluxo mudou de digitar código para revisar código. Eu escrevo a intenção, o modelo escreve a implementação, e eu gasto minha energia em revisão e teste. É uma melhoria real.

E tem o meu aplicativo iBuddhism, que eu construí com pouca experiência prévia em Flutter, rodando no meu celular. Um fim de semana, e um protótipo funcionando. Ideias que morriam no meu aplicativo de notas agora saem do papel.

E, sinceramente, é essa a parte que ainda me deixa maravilhado. Eu mantenho uma lista longa de ideias aleatórias, e as únicas coisas que sempre ficaram entre mim e construí-las eram o custo de aprender o que a ideia pedia e o tempo de realmente sentar e fazer. Agora eu simplesmente construo. A maioria acaba no meu _homelab_ (servidor caseiro), que é onde eu rodo boa parte dos meus projetos paralelos e serviços (tem um post sobre essa configuração vindo, eu prometo).

O detalhe é que meu gasto com _tokens_ de IA com certeza subiu. Não estou economizando dinheiro, estou comprando mais projetos paralelos. Que é o paradoxo de Jevons de novo, só que agora é pessoal e está no meu próprio cartão de crédito.

## A Parte Em Que Fica Terrível

Mas o vídeo nomeia bem o medo. É um loop que se alimenta de si mesmo. A ferramenta que constrói os sistemas não consegue compreendê-los por completo, então conforme os sistemas crescem, o problema cresce.

Eu ainda não tenho um nome bom para esse tipo de dívida, então vou chamar de **dívida de compreensão**. Se ninguém lê o código, ninguém possui o conhecimento. E o primeiro pilar garante que a organização vai racionalmente continuar construindo, porque agora as _features_ passam no corte. Ninguém está sendo irracional. Essa é a parte assustadora.

É o mesmo alerta do meu post sobre _AI slop_, sobre os _clankers_ e o fato de que **_agentes não sentem dor_**. Aquele post era sobre qualidade. Este é sobre quantidade, e quantidade tem uma qualidade própria.

## Onde Eu Aterrisso: Três Pilares Meus

O vídeo tem três pilares. Aqui estão os meus.

1. **Leia as costuras, não só o _diff_.** O perigo está no acoplamento que você não vê. Não pergunte só "isso está certo?", pergunte "o que isso toca que eu não consigo ver?".
2. **Mantenha o caminho crítico humano.** Pagamentos, autenticação, lógica de negócio. O modelo pode escrever o _boilerplate_; o código por onde o dinheiro passa é lido linha por linha.
3. **Orce para a compreensão, não só para a geração.** Se dá para gerar dez vezes mais código, tem que financiar dez vezes mais revisão, ou a gente só está movendo a dívida para um lugar mais silencioso.

Uma última reflexão sobre elasticidade: antes de construir a próxima _feature_, pergunte se ela vale a manutenção. O preço de construir desabou. O de manter, não.

## Conclusão

As duas coisas são verdade ao mesmo tempo. Este é o melhor momento da história para construir software e o mais fácil para perder o controle. O paradoxo não é motivo para parar, é motivo para ser deliberado.

Não me entenda mal, não estou dizendo para jogar as ferramentas fora. Estou dizendo para desacelerar, ler a p*rra do código, e construir um pouco menos.

---

## Recursos

Cover Photo by <a href="https://unsplash.com/@adigold1?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Adi Goldstein</a>.

[^1]: The Paradox of Why AI Code Is Failing Us - 3 Pillars. Kantan Coding. [Source][kantan-video]
[^2]: Paradoxo de Jevons. [Fonte][jevons-wiki]
[^3]: Lost in the Middle: How Language Models Use Long Contexts. Liu et al., 2023. [Source][lost-in-the-middle]

[kantan-video]: https://www.youtube.com/watch?v=k2qls2LiBRc
[jevons-wiki]: https://en.wikipedia.org/wiki/Jevons_paradox
[lost-in-the-middle]: https://arxiv.org/abs/2307.03172
