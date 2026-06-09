+++
title = "A Epidemia de _AI Slop_: Por Que Precisamos Desacelerar e Ler Nosso Código"
author = "João Pedro Sconetto"
date = "2026-06-09T19:33:21-03:00"
description = "Agentes de IA estão inundando repositórios open source e bases de código empresariais com código não revisado. Está na hora de dar um passo atrás, sentir a fricção, e desacelerar."
cover = "/img/slow-down.jpg"
translationKey = "pt-br"
tags = ["ai", "engenharia-software", "opinião", "tech-debt", "oss"]
keywords = ["ai slop", "mario zechner", "clankers", "codificação com ia", "arquitetura de software", "dívida técnica", "open source"]
+++

Ultimamente, tenho sentido uma crescente sensação de desconforto ao revisar _Pull Requests_ (PRs) e _Merge Requests_ (MRs). Estamos vivendo uma era onde entregar código nunca foi tão rápido, mas, ao mesmo tempo, estou demorando cada vez mais para entender a lógica colocada na minha frente. O que começou como uma ferramenta útil para nos ajudar com código repetitivo (_boilerplate_) se transformou silenciosamente em algo muito mais difícil de gerenciar (e de prever).

## O Catalisador: Um Mundo de _Slop_

Recentemente, assisti a uma palestra brilhante do Mario Zechner intitulada <cite>["Building pi in a World of Slop"][zechner-video][^1]</cite>, e ela deu nome exatamente ao que venho sentindo.

> _"And then there's people that say, 'Our product's been 100% built by agents.' Yes, we know, it f\*\*\*ing sucks now. Congratulations."_
>
> — _E tem gente que diz: 'Nosso produto foi 100% construído por agentes.' Sim, nós sabemos, está uma merda agora. Parabéns._

{{< youtube RjfbvDXpFls >}}

Ele descreve como a internet, e nossos repositórios, estão sendo inundados com lixo gerado por IA (ele chama isso de _slop_ — aquela enxurrada de conteúdo gerado de baixa qualidade). E como sabemos, com IA estamos alimentando um ciclo de _garbage-in/garbage-out_ (lixo entra, lixo sai), impulsionado em grande parte pela promessa de produtividade infinita para entregar código _ad nauseam_. Ele também introduz o termo _"clankers"_, que particularmente amei, e vamos falar sobre eles também.

Esse conceito ressoou profundamente comigo. Precisamos conversar sobre o custo de longo prazo dessa epidemia, minha perspectiva sobre isso e esses _clankers_, e por que a habilidade mais importante para um engenheiro de software agora é a disciplina para desacelerar.

## A Ascensão do _"Clanker"_

Na palestra do Zechner, um _"clanker"_ é essencialmente um agente de IA solto por um desenvolvedor para escrever, corrigir e submeter código autonomamente, sem supervisão humana. Eles vagam por _issue trackers_ de projetos _open source_ e bases de código das empresas, deixando um rastro de código de baixa qualidade, nunca lido, não revisado e confiantemente quebrado, que pode até funcionar para um cenário específico, mas quem realmente sabe?

### Terceirizando o Pensamento

Quando ouvi esse termo, instantaneamente fez sentido. Para mim, o _clanker_ representa tudo de errado com nossa obsessão atual por velocidade em detrimento da qualidade. É a manifestação máxima da engenharia preguiçosa. O problema não é a IA em si; o problema é o ser humano do outro lado que trata a IA como um desenvolvedor sênior em vez de um _vibe-coder_ (alguém que apenas descansa, deixando a IA codificar) que digita rápido, não tem intenção de construir software de qualidade e só quer fechar _tickets_/_issues_.

Estamos vendo desenvolvedores terceirizarem não apenas a digitação, mas o _pensamento_. Eles implantam um _clanker_ para corrigir um _bug_, o agente gera um _patch_, e o desenvolvedor faz o _merge_ sem nem ler o código, otimizando puramente para _tickets_ fechados no Jira e alta quantidade de palavras por minuto (_words-per-minute_). Isso é uma traição fundamental da nossa responsabilidade como engenheiros.

## A Ausência de Dor (_Pain_)

Para entender completamente por que esse _slop_ gerado por _clankers_ é tão perigoso, precisamos olhar como os humanos realmente constroem software. Humanos são falíveis, altamente emocionais e facilmente irritáveis. E na engenharia de software, essa irritação é na verdade uma _feature_, não um _bug_.

### Fricção (_Friction_) como Funcionalidade

Quando um humano trabalha em uma base de código terrível e convoluta, ele sente _dor_ (_pain_). Depois da terceira vez revisando e corrigindo um _bug_ através de cinco camadas de abstração desnecessária, o humano se frustra. Ele pode reclamar em uma _retro_ (retrospectiva), pressionar por uma _sprint_ de refatoração, ou simplesmente reescrever o módulo por pura indignação. Essa fricção (_friction_) age como um gargalo natural contra o acúmulo de dívida técnica (_tech debt_).

**_Agentes não sentem dor! (Agents do not feel pain!)_**

### Complexidade Composta

Se você soltar um _clanker_ em uma base de código complexa, ele vai felizmente mergulhar no _spaghetti code_ (código confuso e mal escrito), adicionar mais uma camada de molho de abstração, e submeter o PR. Ele não se importa que o código seja ilegível. Ele não se importa com a pobre alma que terá que depurar aquilo às 3 da manhã daqui a seis meses. Como Zechner aponta, esses modelos aprenderam a programar varrendo a internet, e vamos ser honestos, 90% do código na internet é nosso lixo velho, não mantido e bagunçado.

Quando desenvolvedores deixam a IA "cuidar" da arquitetura, o que eles obtêm é complexidade de nível empresarial gerada em segundos. Os erros não apenas se somam; eles se _multiplicam_ (e rápido).

## A Ilusão do _"Detailed Spec"_ (Especificação Detalhada)

Uma defesa comum que ouço de colegas é: _"It's fine as long as you write a sufficiently detailed spec for the AI."_ (Tudo bem, desde que você escreva uma especificação suficientemente detalhada para a IA).

Mas aqui está a realidade que frequentemente esquecemos: uma especificação suficientemente detalhada _é_ um programa. Se você deixa espaços em branco no seu _prompt_, a IA precisa preenchê-los. E ela os preenche com a mediana do código lixo da internet (descanse em paz, _StackOverflow_).

### A Base de Código como Caixa Preta

Já vi isso pessoalmente. Um _clanker_ vai escrever confiantemente um _patch_ que corrige um _bug_ local, mas como o agente não possui o contexto global da arquitetura do sistema, ele silenciosamente quebra algo no caminho (_downstream_). Quando o desenvolvedor não lê o código gerado, essa pílula envenenada é incorporada ao projeto.

De repente, ninguém no time entende mais como o sistema funciona. A base de código se torna uma caixa preta de abstrações geradas por IA. Se seus usuários começarem a gritar por causa de uma parada de produção e você não conseguir consertar porque "não lê mais o código", você não é um engenheiro. Você é apenas um passivo (_liability_).

## Desacelerando (_Slowing the F*** Down_)

Na minha vida pessoal, sou um grande defensor da intencionalidade. Gosto do "trabalho" (fricção) de fazer as coisas manualmente porque isso me força a estar presente. Sinto exatamente o mesmo sobre engenharia de software: **a fricção é onde o entendimento acontece.**

O ato de digitar um algoritmo crítico, cometer erros e debugá-lo manualmente é como você constrói um modelo mental do sistema. Se você terceiriza essa fricção inteiramente para uma IA, você terceiriza seu entendimento.

### Estabelecendo Limites para a IA

Isso não é um chamado para desinstalar suas ferramentas de IA. É um chamado para disciplina. Precisamos definir limites para onde a IA pertence em nosso fluxo de trabalho:

1. **_Wipe the slop:_** Use agentes para o trabalho chato. Escrever casos de reprodução para _bugs_ obscuros de usuários, gerar _boilerplate_ de testes unitários, ou usar como _rubber duck_ (um pato de borracha para pensar em voz alta sobre um problema de lógica)? Perfeito. Deixe a IA cuidar disso.
2. **Leia cada linha do caminho crítico:** Se lida com pagamentos, autenticação, lógica de negócios ou estados complexos, _você_ escreve. Ou, no mínimo, você lê cada linha que a IA gera com extremo cuidado.
3. **Pare de otimizar para velocidade:** Entregar uma funcionalidade em dois dias em vez de uma semana não importa se levará três meses para entender a arquitetura resultante depois.

## Conclusão

Estamos vivendo uma era estranha onde a indústria está ativamente celebrando a capacidade de construir produtos inteiros sem entender como eles funcionam. É quase como se estivéssemos alugando nossa arquitetura de um _LLM_ em vez de possuir o conhecimento nós mesmos.

Os engenheiros que prosperarão na próxima década não serão os "_prompt engineers_" mais rápidos ou aqueles que conseguem implantar um exército de _clankers_ para fechar _tickets_. Os grandes engenheiros serão aqueles que sabem quando desligar a IA, arregaçar as mangas, e ler a p*rra do código.

Respire fundo. Proteja sua base de código. _Slow the f*** down._

---

## Recursos

Cover Photo by <a href="https://unsplash.com/@navarrovisuals?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Ángel Navarro</a>.

[^1]: Building pi in a World of Slop. Mario Zechner, AI Engineer World's Fair 2026. [Source][zechner-video]

[zechner-video]: https://youtu.be/RjfbvDXpFls
