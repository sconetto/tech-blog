+++
title = "My experience with _Vibe Coding_"
author = "João Pedro Sconetto"
date = "2026-02-08T21:25:25+01:00"
description = "My personal take on AI-assisted coding: the good, the bad, and the ugly of it."
cover = "/img/ai-coding.jpg"
translationKey = "en-us"
tags = ["ai", "vibe-coding", "cursor", "software-engineering", "opinion"]
keywords = ["vibe coding", "ai coding", "cursor", "software engineering", "artificial intelligence", "code generation"]
+++

I am adding one more page on the internet to the never ending list of people talking about AI, and code, and what feels like a buzzword that can't be shaken off, _vibe coding_ (letting AI code for you while you sit back and watch). But first and foremost, my intention with this post is not (_only_) to praise, or complain, or deify, or even shove it down every second person's throat as the next best thing since sliced bread, it is mostly to share a bit of my point of view on what's great about it, what's not so great, and what possibly is the "_bad_" about it, call it [the good, the bad, and the ugly](https://en.wikipedia.org/wiki/The_Good,_the_Bad_and_the_Ugly).

## Setting up the baseline

Personally, the best way to start describing my experience with the whole thing is to also describe what I understand of it. Giving way to my researcher side, let me maybe start with some definitions of it before I jump into my personal description of it.

### What is an AI?

> <cite>"Artificial intelligence (AI) is technology that enables computers and machines to simulate human learning, comprehension, problem solving, decision making, creativity and autonomy."[^1]</cite>¹

A simpler way to think about it is to also review the series of derivative concepts that have emerged over the last 70 years:

1. (1950's) Artificial Intelligence (AI): Human intelligence exhibited by machines.
2. (1980's) Machine Learning (ML): AI systems that learn from historical data.
3. (2010's) Deep Learning (DL): Machine learning models that mimic human brain function.
4. (2020's) Generative AI (Gen AI): Deep learning models (foundation models) that create original content.

Ultimately, underneath what we're currently talking or calling AI is machine learning, which involves creating models by training an algorithm to make predictions and/or decisions based on historical data or based on a training set of data. All of it is done aiming to have in the other end of the process a _machine_ that can then make inferences based on data without being explicitly programmed for specific tasks.

There are many types of machine learning techniques and algorithms, if you're into the idea of learning or understanding it more in-depth, how these techniques work, or how you can get started on building an _AI_ yourself, I would recommend to start at this [ML Concept Course Module][google-ml-concept-course] by Google. I'm not getting paid by Google to forward you to their content, nor saying that this is the definitive place to learn it, I, myself, learned it from different sources, just felt like a solid starting point from what I could gather around and what it offers.

### What is an AI? (But in my perspective)

Well, with the risk of sounding stupid and/or being too oversimplistic, I like to think that AIs are nothing more than state machines that calculate, based on its training data, what's the most likely next output for the input you're giving to it (in the case of Gen AI). I don't think I am completely wrong, but definitely not completely right either, so let me explain myself:

- AIs are algorithms that read from an input, process that input through a series of mathematical transformations, and then generate an output.
- With that output, the code tries to categorize it based on what it has seen before.
- On that, the algorithm checks if it was right or wrong (or if it was far or close to the "correct" answer), feeding itself that information and passing it onto the "next-generation".
- This process continues until the person responsible for that AI is satisfied with the accuracy of the model (the final state machine, with its given weights to process inputs into outputs).

That being said, I am compelled to give the next disclaimer:

> **This is an opinion post, and although I try to bring sources to some of the information I'm writing here, I am a human being, with bias and susceptible to making mistakes, misinterpretations, and downright stupid affirmations. I will always, 100%, recommend you to do your own research and build your own knowledge on the topic, so feel free to disagree with me!**

Now, with a lighter heart after disclaiming this section, let's move forward.

## My experience with AI in my work & personal life

My first attempt in trying to understand AIs and learn more about the topic (passing the surface level) was about 7 years ago, mid-2019, when I took a class in the last years of my bachelor's in Software Engineering at UnB (Universidade de Brasília). It was when I coded [Kara][kara-github] and [bAIch][baich-github] (the second was a bit later, caused I really liked the subject and it was fairly easy to get a good grade, so I did it again, don't tell anyone).

If you're wondering yourself, yes, I gave the name for both projects, *Kara* was after the character in [Detroit: Become Human][detroid-become-human], which I really saw fitting for the theme, and *bAIch* was a low effort wordplay with AI and Bach, from Johann Sebastian Bach, the composer.

At this time I learned about, mainly, machine learning, neural networks, algorithms, and a good amount of math formulas. Then, based on it we were off to the races to build half-baked AIs with our classmates, not having hardware to get even close to something smart enough to impress a 5th-grader. Nevertheless, I understand today that it was not the final goal to build amazing AIs, we were there to learn and so we tried (and hopefully did).

Fast forward a not insignificant amount of years later and I see myself before ChatGPT 3.5, if I recall it correctly, and I couldn't shake the feeling of seeing it more as a party trick or something that could generate some sort of gibberish with some sense to it, it was for me a Lorem Ipsum generator with phrases that could be read. By this point I imagine that there are plenty of people that were already using it to generate emails, or documents, or supporting with studies and questions, but I was still very skeptical of its usefulness and very uncertain on how I could implement it in my day-to-day life. I guess I was too concerned with covid or something else to give it my full attention.

At that time I felt like it would never become a great thing, how wrong I was, and because of that I never felt "liable" for using it more or trying to integrate it in my work/routine.

Going forward another year or so, then I couldn't help but hear about it everywhere, see people pinning it as the next phase of the industrial revolution and etc, how everything was AI, that it would replace people, and that we would be out of jobs because of it. I believe that at this point you probably also heard it, this sudden heavy weight to it made me be a bit reluctant to use it more, somehow it all felt shoved in our faces and an ultimatum of "either you use it or will be out of a job soon". That whole sentiment made me a later adopter of AI into my workflow and after some internal struggle I started using it, but mainly to revise content or create content, like emails, documentation for processes, and other minor question and research-related workflows.

## Tipping point

My overall relationship with AIs started really changing when last year I changed my workplace, when joining the new team I discovered that the company offered to all engineers [Cursor][cursor], which is an IDE based on Visual Studio Code but with AI features integrated to it. It has, in the paid version, the models to generate the code, documentation, to run, debug, and everything that you tech heart desires to create (maybe you could use that in the free version but with heavy limitations or you need to bring your own API key).

So, imagine the following scenario:

1. You're new to a workplace and haven't seen their code/architecture;
2. You need to get some fixes and some developments going from the get go;
3. You're trying to make a good impression at developing your first task.

At the same time that you're going the extra mile, everything has an extra layer of difficulty because you're still trying to figure out the codebase, the architecture, the people, the systems, and how everything kinda connects together. This is how I saw myself at that new environment having access to a tool that frankly I hadn't used that much before (not really for coding) and navigating all of it. Long story short, I delivered that task, although at the time I was unsure if I was using it to its fullest and if the task was well-coded. We deployed it to production, got some feedback for improvements, and finally, I felt a little bit more comfortable in understanding my new tools and the systems I am working on, since then I have been using AI way more in my daily activities.

## Why I wanted to write this and my review in AI/_Vibe Coding_

Now, almost six months in my new job and using AI on a daily basis I was fairly comfortable using cursor and tapping into some models to help me solve problems on some tasks, more and more I was using it to generate code, to explain codebases, and to just help me plan how to tackle some coding issues. What I noticed with using it was that my workflow completely changed from coding, testing, and pushing it into a PR so someone could review it, to write my intention, revise "_someone else's_" code, test, and so on. Of course, every now and then it was required of me to rewrite some code or re-input something because it hadn't done it well, but ultimately I realized that I was writing less code and reviewing more the model's implementation. As you can imagine, what it generates some times is really bad, but this change on the workflow made me much more efficient, cause it could output more than me in my keyboard could ever try to do in WPM (_words per minute_).

Some of the fairly simple tasks, or quick bugfixes, became complete _vibe coding_, just type the prompt, tell it what needs to be changed, commit, and then open the PR (use your _vibe coding_ with caution).

### _"Here Comes a New Challenger"_

Noticing this change on my workflow, it didn't take me long to have the following idea: "What if I pick up on an old idea that I never moved forward with?"

In my mind it was clear, there was plenty of coding ideas that never got out of my head because it required me to learn new frameworks, or coding languages, although being something I really like to do, the older we grow, the more difficult it is to find time to do everything we want. So I took the risk of taking one of these ideas for a spin with my newly discovered skill of writing to a prompt what I want it to do and transform into a software.

I began then coding an application on Flutter/Dart to be a companion for people who are practitioners of Buddhism. The main feature is to allow and help people to recite the <cite>_Daimoku (題目)_[^2]</cite>, which is the core practice in the Nichiren Buddhism, involving the repeated chanting of "Namu Myōhō Renge Kyō" to manifest one's innate Buddha nature.

Up to this point I have a total of 0 hours of experience with Flutter/Dart, I remember only reading about it back in college when I coded some multi-platform applications in Ionic/React-Native. I had a plan and a vision where to go alongside my prompt and a few free hours on my weekend. After a lot of testing, researching, and prompting, I had this (screenshots are in Portuguese):

#### Homepage

{{< figure src="/img/vibe-coding/screenshot-1.png" alt="App Homepage Preview" position="center" caption="App Homepage Preview" captionPosition="center" >}}

#### Profile

{{< figure src="/img/vibe-coding/screenshot-2.png" alt="App Profile Preview" position="center" caption="App Profile Preview" captionPosition="center" >}}

#### Recital Feature

{{< figure src="/img/vibe-coding/screenshot-3.png" alt="App Recital Companion Preview (Gongyo)" position="center" caption="App Recital Companion Preview (Gongyo)" captionPosition="center" >}}

---

I must say, for my first time doing something on Flutter/Dart, I was very proud of what I could achieve with a couple of hours of _vibe coding_, pleasantly surprised with what I could get out of the model and for a quick prototype of an idea, already running on my own smartphone, it was amazing!

Furthermore, my wife, who also works in the IT field, was also impressed with the quality of the first debug build, the UI elements, the colors, the features, I got her even excited to help me with it. In my books, this is one of the greatest things that AI/_Vibe coding_ can give us.

> In case you want to see the source code of it (which by no means is going to be great since I am still learning Flutter/Dart), you can refer to the GitHub repository of the application: [sconetto/iBuddhism][ibuddhism]

## The good, the bad, and the ugly (plus the conclusion)

Now, don't take me wrong, even though I was very happy with the outcome of the experiment, it wasn't short of issues, debugging, prompt to correct issues, and telling AI where to look to fix their own mistakes, I think there's value to be extracted from all of it, which I summarize as my personal opinion:

### The good

AI code or _vibe coding_ is a tool, and if used correctly it can be a great addition to one's toolbox. It allows you to output more and focus on review/testing, shifting from long hours of coding before having a first version of something. It can quickly review code bases and make sense of what's seeing there for you to evaluate. For super precise, super laser-focused changes, it even allows you to just type the correct prompt and go get yourself a coffee while it makes the necessary update in the code, which, let's be honest, is great!

Ultimately, in my opinion, AI tools for coding tend to boost the type of engineer/developer that you already are and if well used, you can become a productivity machine, completing issues like you never did before. On top of all of that, it also lowers the entry barrier for new programming languages/frameworks. Being honest again, we're engineers, we know the logic and we know what we're trying to achieve, but knowing if for that syntax I need to add a semicolon or not, or if I can iterate over object instead of _for-looping_ it, it all can be fairly time consuming, AI lets you become the reviewer as you learn the syntax (there's a pitfall to this that I will mention later).

### The bad

Top one reason why we should be careful with AI for coding: It might turn us into lazy engineers/developers.

Trust me, I know it's way simpler to tell yourself that you write good prompts and that you tested the workflow with the generated code, you take efficiency to its maximum and become a _pure vibe coder_, you just prompt and test, and even though it might be that this will work some of the times, it will also fail, a good amount of times. AI coding is improving as you read this post, and I have no doubt that it will get better and better with time, but between us two, sometimes it can generate such poor code that even you in college were able to write better logic/syntax, so you must resist the will to vibe code all the time! Not reviewing what it generated, not testing the whole workflow trying to catch edge cases, trusting that it isn't generating _spaghetti code_ will make you fall, and hard. It will take you away from your weekend to fix a production bug that got released without anyone noticing it, even more if your organization (or you) is also using AI to review PRs, then the cycle is complete.

### The ugly

As I mentioned in the beginning, I really do believe AIs are statistical machines, the data on which it's trained could predict that the next best line of code for what you're writing is something abysmal that will make the software prone to issues or even insecure because it saw it one too many times, the key here is to "trust, but verify".

Add to that some borderline insane prices to the tools (like Cursor, Claude Code) or to the models (ChatGPT, Gemini, etc.), you will run out of tokens or be caught up in a subscription that will cost you the more you use AI. I guess I'm a lucky person, since my company offers us Cursor to work in our activities, but I'm also aware not everybody has the same luck.

Lastly, I want to mention the pitfall I said earlier, while doing my Flutter/Dart project I was always mentioning in my prompts to make it adhere to framework standards and coding best practices, there was a lot of bad code in the generation. To some extent, if I, myself, don't dive deeper to understand what clean code in Flutter/Dart looks like, my code will feed itself bad practices up until the time I take matter into my own hands, and this for me is one of the worst things that AI coding adds as a challenge for us (the never-ending cycle of bad code training AIs to generate more bad code), being one of the main reasons to say that we should always verify.

### Conclusion

It is rather unreasonable to not be using these tools, it does bring positive things and qualities to our day-to-day, and it could for you as it was for me, be a way to lower the barrier for you to try new things and get that coding project going. To deny AI is to deny the change that will shape how we are and will be perceived as software engineers. Nevertheless, don't be fooled to think that AI will solve everything and you'll never have to write another line of code in your life (or that anyone can make excellent software with it), we're somewhat far from that being our reality, and in my opinion, moving forward, towards the future, the distinction between a good and a great engineer/developer will be the one who doesn't trust productive software to be defined by a tool, but uses the tool to amplify themselves and improve their software.

## Resources

Cover Photo by <a href="https://unsplash.com/@dkomow?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Daniil Komov</a>

[^1]: What is artificial intelligence (AI)?. Stryker, Cole. Kavlakoglu, Eda. IBM Website. [Source][ibm-what-is-ai]
[^2]: _Namu Myōhō Renge Kyō_. [Source][daimoku-wiki]

[ibm-what-is-ai]: https://www.ibm.com/think/topics/artificial-intelligence
[google-ml-concept-course]: https://developers.google.com/machine-learning/crash-course/neural-networks
[kara-github]: https://github.com/deeplearningunb/kara
[baich-github]: https://github.com/deeplearningunb/baich
[detroid-become-human]: https://en.wikipedia.org/wiki/Detroit:_Become_Human
[cursor]: https://cursor.com/
[daimoku-wiki]: https://en.wikipedia.org/wiki/Namu_My%C5%8Dh%C5%8D_Renge_Ky%C5%8D
[ibuddhism]: https://github.com/sconetto/iBuddhism
