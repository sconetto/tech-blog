+++
title = "The AI Slop Epidemic: Why We Need to Slow Down and Read Our Code"
author = "João Pedro Sconetto"
date = "2026-06-09T19:33:21-03:00"
description = "AI agents are flooding open source and enterprise codebases with unreviewed code. It’s time we step back, feel the friction, and slow the f*** down."
cover = "/img/slow-down.jpg"
translationKey = "en-us"
tags = ["ai", "software-engineering", "opinion", "tech-debt", "oss"]
keywords = ["ai slop", "mario zechner", "clankers", "ai coding", "software architecture", "tech debt", "open source"]
+++

Lately, I’ve been feeling a creeping sense of unease while reviewing Pull/Merge Requests. We are living through an era where shipping code has never been faster, yet I find myself taking longer to untangle the logic placed in front of me. What started as a neat tool to help us write boilerplate has quietly mutated into something much harder to manage (and forecast).

## The Catalyst: A World of Slop

Recently, I watched a brilliant talk by Mario Zechner titled <cite>["Building pi in a World of Slop"][zechner-video][^1]</cite>, and it put a name to exactly what I’ve been feeling.

> *"And then there's people that say, 'Our product's been 100% built by agents.' Yes, we know, it f\*\*\*ing sucks now. Congratulations."*
>
> — _E tem gente que diz: 'Nosso produto foi 100% construído por agentes.' Sim, nós sabemos, está uma merda agora. Parabéns._

{{< youtube RjfbvDXpFls >}}

He describes how the internet, and our repositories, are being flooded with generated garbage, and as we know, with AI we have been feeding a cycle of garbage-in/garbage-out, largely driven by the promise of never-ending productivity to ship code *ad nauseam*. There's also the introduction to "clankers", which personally, I loved the term, we will get to those too.

That concept resonated deeply with me. We need to talk about the long-term cost of this epidemic, my own perspective on that and these clankers, and why the most important skill for a software engineer right now is the discipline to slow the f*** down.

## The Rise of the "Clanker"

In Zechner's talk, a "clanker" is essentially an AI agent let loose by a developer to autonomously write, patch, and submit code without human oversight. They roam open-source issue trackers and internal enterprise codebases, dropping low-quality, never read, not reviewed, and confidently broken code, that might work for one scenario, but who really knows?

### Offloading the Thinking

When I heard that term, it instantly clicked. To me, the clanker represents everything wrong with our current obsession with velocity over quality. It’s the ultimate manifestation of lazy engineering. The problem isn't the AI itself; the problem is the human on the other side who treats the AI as a senior developer rather than a fast-typing vibe-coder, that has not intention to build quality software, mainly wants to close tickets/issues.

We are seeing developers offload not just the typing, but the *thinking*. They deploy a clanker to fix a bug, the agent generates a patch, and the developer merges it without even reading it, optimizing purely for closed Jira tickets and high words-per-minute. It is a fundamental betrayal of our responsibility as engineers.

## The Absence of Pain

To fully grasp why this clanker-driven slop is so dangerous, we have to look at how humans actually build software. Humans are failable, highly emotional, and easily annoyed creatures. And in software engineering, that annoyance is actually a feature, not a bug.

### Friction as a Feature

When a human works in a terrible, convoluted codebase, they feel *pain*. After the third time tracing a bug through five layers of unnecessary abstraction, the human gets frustrated. They might complain in a retro, push for a refactoring sprint, or just rewrite the module out of spite. That friction acts as a natural bottleneck against compounding tech debt.

**_Agents do not feel pain!_**

### Compounding Complexity

If you unleash a clanker on a complex codebase, it will happily dive into the spaghetti, add another layer of abstract sauce, and submit the PR. It doesn't care that the code is unreadable. It doesn't care about the poor soul who has to debug it at 3 AM six months from now. As Zechner points out, these models learned how to code by scraping the internet—and let's be honest, 90% of the code on the internet is our old, unmaintained, messy garbage.

When developers let AI "handle" the architecture, what they get is enterprise-grade complexity generated in seconds. The errors don't just add up; they compound (and fast).

## The Illusion of the "Detailed Spec"

A common defense I hear from peers is, *"It's fine as long as you write a sufficiently detailed spec for the AI."*

But here is the reality we often forget: a sufficiently detailed spec *is* a program. If you leave blanks in your prompt, the AI has to fill them. And it fills them with the median average of the internet's garbage code (rest in peace stackoveflow).

### The Black Box Codebase

I’ve seen this firsthand. A clanker will confidently write a patch that fixes a local bug, but because the agent doesn't possess the global context of the system architecture, it quietly breaks something else downstream. When the developer doesn't read the generated code, that poison pill gets merged.

Suddenly, nobody in the team actually understands how the system works anymore. The codebase becomes a black box of AI-generated abstractions. If your users start screaming about a production outage and you can't fix it because you "don't read the code anymore," you aren't an engineer. You're just a liability.

## Slowing the F*** Down

In my personal life, I'm a big believer in intentionality. I like the friction of doing things manually because it forces me to be present. I feel the exact same way about software engineering: **friction is where understanding happens.**

The act of typing out a critical algorithm, making mistakes, and debugging it by hand is how you build a mental model of the system. If you outsource that friction entirely to an AI, you outsource your understanding.

### Setting Boundaries for AI

This isn't a call to uninstall your AI tools. It's a call for discipline. We need to define boundaries for where AI belongs in our workflow:

1. **Wipe the slop:** Use agents for the boring stuff. Writing reproduction cases for obscure user bugs, generating unit test boilerplate, or rubber-ducking a logic problem? Perfect. Let the AI handle it.
2. **Read every line of the critical path:** If it handles payments, authentication, core business logic, or complex state, you write it. Or, at the very least, you read every single line the AI generates with extreme prejudice.
3. **Stop optimizing for speed:** Shipping a feature in two days instead of a week doesn't matter if it takes three months to untangle the resulting architecture later.

## Conclusion

We are living through a strange era where the industry is actively celebrating the ability to build entire products without understanding how they work. It’s almost like we are renting our architecture from an LLM rather than owning the knowledge ourselves.

The engineers who will thrive in the next decade won't be the fastest "prompt engineers" or the ones who can deploy an army of clankers to close tickets. The great engineers will be the ones who know when to shut the AI off, roll up their sleeves, and read the damn code.

Take a breath. Protect your codebase. Slow the f*** down.

---

## Resources

Cover Photo by <a href="https://unsplash.com/@navarrovisuals?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Ángel Navarro</a>.

[^1]: Building pi in a World of Slop. Mario Zechner, AI Engineer World's Fair 2026. [Source][zechner-video]

[zechner-video]: https://youtu.be/RjfbvDXpFls