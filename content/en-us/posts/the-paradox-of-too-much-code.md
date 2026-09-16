+++
title = "The Paradox of Too Much Code: Why AI Is Great and Terrifying at the Same Time"
author = "João Pedro Sconetto"
date = "2026-09-16T10:00:00-03:00"
description = "AI gives us more code than ever, and that's the problem. A personal take on why the tool that builds our systems can't understand them."
cover = "/img/too-much-code.jpg"
translationKey = "en-us"
tags = ["ai", "software-engineering", "opinion", "tech-debt", "jevons-paradox"]
keywords = ["ai coding", "jevons paradox", "context window", "lost in the middle", "software architecture", "ai slop", "kantan coding", "tech debt"]
+++

Lately I've been feeling uneasy about the code I review. We ship faster than ever, and yet it takes me longer to understand what's in front of me. This is the third post I've written about AI on this blog, and I swear I didn't plan it as a trilogy.

Here's the honest thesis: AI is giving us too much code. Not _bad_ code, that complaint is getting less true every month. Even when the code is correct, compiles, passes every test, and does exactly what was asked, there is still too much of it. That makes AI the most powerful tool I've had in my career and the thing most likely to bury the systems I'm responsible for. Both are true at once.

> **This is an opinion post, and although I try to bring sources to some of the information I'm writing here, I am a human being, with bias and susceptible to making mistakes, misinterpretations, and downright stupid affirmations. I will always, 100%, recommend you to do your own research and build your own knowledge on the topic, so feel free to disagree with me!**

## The Video That Reframed It for Me

I stumbled onto a video by the YouTube channel Kantan Coding titled <cite>["The Paradox of Why AI Code Is Failing Us - 3 Pillars"][kantan-video][^1]</cite>, and it changed how I think about this problem.

{{< youtube k2qls2LiBRc >}}

It opens with economics and ends deep inside how transformers work, and the punchline is a self-reinforcing loop: the more code AI helps us generate, the bigger our systems get, and the harder it becomes for the tool that generated them to understand them. More AI doesn't solve it. It makes it worse.

## Pillar One: Cheap Code Doesn't Save Money, It Buys More Code

### The Naive Math

The first pillar is economics, and it starts with the argument we've all heard: if AI quadruples delivery speed, a forty-hour feature takes ten, so the company saves time and money.

The video models a feature backlog as a 3D bar chart where each bar's height is that feature's value. A critical bug losing customers is a tall bar. Paying down tech debt is a short one. Then it applies a demand function. At $6,000 per feature, only two features are worth building. At $1,000, seventeen are.

### Elasticity

That sensitivity has a name: _elasticity_. For a modern tech company, demand for features is highly elastic, meaning it grows _faster_ than the price falls. And even in the low-elasticity case, the number of features built still goes up.

### The Jevons Paradox

This is the **Jevons paradox**. In 1865, William Stanley Jevons noticed that more efficient steam engines needed less coal per unit of work, yet total coal consumption rose, because cheaper power made new uses viable.[^2] The video argues the same thing is happening to software, and I think it's right.

### Why Backlogs Don't Shrink

I've watched backlogs for years, and they don't shrink when you get faster. They get reprioritised. The tier of features that was "not worth it" at the old price becomes next quarter's roadmap at the new one. The uncomfortable conclusion: companies will spend substantially more on software, not less.

## Pillar Two: The Context Window Is the Real Ceiling

### How a Model Sees Code

To read code, a model splits it into tokens, maps each token to an ID, and each ID is a row in an embedding matrix holding a high-dimensional vector. Similar tokens end up near each other. Then _attention_ lets every token pull meaning from the tokens before it, across layers, until the model predicts the next one.

### The Window Is the Ceiling

All of that has to fit in the _context window_, the maximum number of tokens the model can hold at once. That's a hard limit on every model today. And the window isn't a grid of modules you can dip into, it's one long line of tokens from start to finish.

### Three Ways It Breaks

The video walks through three failure modes:

1. The model edits code inside the window and can check it against other modules inside the window, but it can't see the ones outside.
2. New code calls a function defined outside the window. The model can't see the definition, so it guesses the return shape from training. Assume a dictionary and get a list, and the code breaks in a way nobody notices until runtime.
3. The sinister one. A function that looks O(n) contains a loop calling a function outside the window that is itself O(n). You've just shipped an O(n²) function, and it only shows up at scale.

This isn't the model being dumb. It's the model not being able to see.

## Pillar Three: Why "Just Make the Window Bigger" Doesn't Work

The obvious answer is a bigger window. The video explains why that fails too.

### Lost in the Middle

_Lost in the middle_ is a documented phenomenon: models pay close attention to the start and end of a long context but ignore what's buried in the middle, even when it's inside the window.[^3]

### The Cost of Attention

Attention compares every token with every previous token, which is n(n+1)/2 comparisons, or **O(n²)**. Double the window and the work roughly quadruples, and it repeats on every query.

### Sparse Attention and Retrieval

_Sparse attention_ has each token attend only to a chosen subset, which is cheaper, but pairs that never get compared are links that never get seen. _Retrieval_ puts the codebase in a search index outside the model and pulls dependencies in on demand. It sounds like the fix, until you see where it breaks.

### The Nightly Report Nobody Updated

Some AI-generated code writes orders to a database, with the total and any discount in the columns. Outside the window, a nightly report calculates revenue by aggregating totals minus discounts, reading the orders table directly. Now ask the model to apply the discount to the total _before_ inserting the order. The two are coupled through the database, but nothing in the visible code references the report, so there is nothing to search for. The report never gets updated and the discount is subtracted twice. As the video puts it, good luck winning back the trust of your accounting team.

The dangerous failures aren't syntax errors. They're _invisible coupling_, dependencies that exist in the system but not in the code you can see.

## The Part Where AI Is Genuinely Great

Let me be fair, because I use these tools daily and I genuinely like them.

My workflow shifted from typing code to reviewing it. I write the intention, the model writes the implementation, and I spend my energy on review and testing. That's a real improvement.

Then there's my iBuddhism app, which I built with little prior Flutter experience, running on my phone. A weekend, and a working prototype. Ideas that used to die in my notes app now get built.

And honestly, that's the part that still amazes me. I keep a long list of random ideas, and the only things that ever stood between me and building them were the cost of learning whatever the idea needed and actually having the time to do it. Now I just build them. Most of them end up on my homelab, which is where I run a lot of my side projects and services (I have a post about that setup coming, I promise).

The catch is that my AI token spend has definitely gone up. I'm not saving money, I'm buying more side projects. Which is the Jevons paradox again, except this time it's personal and it's on my own credit card.

## The Part Where It Gets Terrifying

But the video names the fear well. It's a self-reinforcing loop. The tool that builds the systems can't fully comprehend them, so as the systems grow, the problem grows.

I don't have a good name for this kind of debt yet, so let me call it _understanding debt_. If nobody reads the code, nobody owns the knowledge. And pillar one means the organisation will rationally keep building, because the features clear the bar now. Nobody is being irrational. That's the scary part.

It's the same warning from my slop post, about the clankers and the fact that **_agents do not feel pain_**. That post was about quality. This one is about quantity, and quantity has a quality of its own.

## Where I Land: Three Pillars of My Own

The video has three pillars. Here are mine.

1. **Read the seams, not just the diff.** The danger is in the coupling you can't see. Don't just ask "is this correct?", ask "what does this touch that I can't see?"
2. **Keep the critical path human.** Payments, auth, core business logic. The model can write the boilerplate; the code money flows through gets read line by line.
3. **Budget for comprehension, not just generation.** If we can generate ten times the code, we have to fund ten times the review, or we're just moving the debt somewhere quieter.

One last thought on _elasticity_: before building the next feature, ask whether it's worth the maintenance. The price of building collapsed. The price of owning didn't.

## Conclusion

Both things are true at once. This is the best time in history to build software and the easiest time to lose the plot. The paradox isn't a reason to stop, it's a reason to be deliberate.

Don't take me wrong, I'm not telling anyone to throw the tools away. I'm telling you to slow the f\*\*\* down, read the damn code, and build a little less of it.

---

## Resources

Cover Photo by <a href="https://unsplash.com/@adigold1?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Adi Goldstein</a>.

[^1]: The Paradox of Why AI Code Is Failing Us - 3 Pillars. Kantan Coding, YouTube. [Source][kantan-video]
[^2]: Jevons paradox. Wikipedia. [Source][jevons-paradox-wiki]
[^3]: Lost in the Middle: How Language Models Use Long Contexts. Liu et al., 2023. [Source][lost-in-the-middle]

[kantan-video]: https://www.youtube.com/watch?v=k2qls2LiBRc
[jevons-paradox-wiki]: https://en.wikipedia.org/wiki/Jevons_paradox
[lost-in-the-middle]: https://arxiv.org/abs/2307.03172
