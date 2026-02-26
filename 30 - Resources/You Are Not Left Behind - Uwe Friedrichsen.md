---
created: 2026-02-26
updated: 2026-02-26
tags:
  - area/work
---

# You Are Not Left Behind — Uwe Friedrichsen

**Author:** Uwe Friedrichsen
**Published:** February 20, 2026
**Source:** [ufried.com](https://www.ufried.com/blog/not_left_behind/)
**Reading time:** ~17 minutes

---

## Summary

The article pushes back against the pervasive fear-mongering around AI adoption — the idea that if you don't immediately master every AI/LLM/agentic tool, you'll lose your job and be permanently left behind. Friedrichsen argues this framing is false, but also that completely ignoring AI is risky. The key insight is the concept of **inflection points**.

### Main points

- **AI tooling is still immature.** Current agentic AI behaves like an apprentice with attention deficit: it needs tasks sliced small, lots of context, repeated instructions, and still drifts or makes subtle mistakes. A human in the loop is always required.
- **Immature technology knowledge becomes obsolete.** Just like knowing UNIX nice levels, DOS memory layout, SQL query hints, or container driver quirks, today's "secret AI recipes" will be irrelevant in a year or two as the tooling matures. "Prompt engineering" from two years ago is already nearly worthless.
- **You are not left behind for not knowing the tricks.** Waiting for the tools to mature before going deep is a reasonable strategy — people who adopted Windows after the early-days mess were fine.
- **But you can't ignore the evolution.** The DOS-vs-Windows analogy: devs who ignored Windows' trajectory entirely and doubled down on DOS were caught flat-footed when the market shifted. They missed the inflection points and had to start over from scratch.
- **Two inflection points to watch:**
  1. *When to add AI to your portfolio* — in software development, this point is **now**, driven by market pressure from AI vendors gaming the mainstream earlier than technology maturity would normally warrant.
  2. *When AI becomes the dominant paradigm* — unclear; could be months, years, or may never fully arrive in the way predicted.
- **Ironic footnote:** The context, requirements, and architecture that AI agents need to work well are exactly what companies historically refused to provide to human developers. Developers who compensate by adding that context themselves are inadvertently masking the dysfunction.

### Conclusion

> Do not fall for the fear-mongering messages regarding AI.
> Still, watch the AI evolution closely enough to be prepared when the inflection points arrive.

---

## Full Text

### You are not left behind

How often have you heard a phrase like "If you do not become highly proficient in AI/LLMs/Agentic AI now, you will be left behind!" in recent months? Probably more often than you were able (or willing) to count. And it does not stop there. If we do not immediately learn the stuff as advised by the person uttering such phrases, we will lose our jobs and never get a job again. Our existences will be *destroyed*. And this will be solely our fault because we did not listen and obey.

Fear-mongering at its best. Not only AI investors and vendors flood us with such messages. Also, all the wannabe profiteers of AI jumped on the fear-mongering bandwagon and flooded us with such messages – oftentimes having a remedy in place for the exchange of some money.

And so we stand here, with such messages hollered into our faces day by day, and ask ourselves: Are we "left behind" if we do not immediately learn all that AI magic?

### Are we left behind?

I thought about this question for a bit. Do we really need to pick up all that daily changing and evolving AI and agentic stuff to not be "left behind?"

The short answer I came up with is:

> No, you are not left behind if you do not immediately pick up everything AI and agentic.
>
> However, ignoring it is not an option either.

I.e., there are things you should not ignore, but these are not the things you are usually told you must not ignore. Sounds cryptic? Probably yes – at least without further explanation. Thus, let me unpack my answer.

### Still a subpar performance

Let us begin with a look at the current state of AI solutions. I took software development as an example domain because it is probably the domain where AI penetration is highest and, with it, the fear-mongering is also highest. So, what is the current state of the art in AI-driven software development?

AI solutions meanwhile can create impressive solutions if we slice the problem small enough, give them enough context, and it is a well-known problem. If we feed them too large a chunk of work or if we do not provide enough context, it often becomes a game of chance if we get a good solution.

Regarding the context that needs to be provided: Such context descriptions can easily become several thousand words if working with agentic solutions. Additionally, it needs to be provided a bit differently for each agent framework and each model to create the desired results.

If the problem we need to solve is not a well-known one, i.e., if the underlying LLMs lack sufficient training examples in their corpus, more often than not the AI solutions are not able to come up with a reasonable solution. Luckily, most of the time we tend to solve well-known problems. Therefore, this issue strikes less often than we might expect. Still, depending on the problem you attempt to solve, it may strike.

Then, there is another issue: If you talk to serious power users, all of them tell you the same story: The AI solutions drift off. For a while, they produce good results and then they start to drift off. They stop doing what you told them to do and start doing different things. There are recommended "best practices" to deal with this drifting, like, e.g., feeding the AI solution the whole context before every single task, or reminding it in some other way. Then the solutions drift off less often – but they still drift off sometimes. Therefore, we always need a human in the loop who checks if the result meets the demands.

And even if everything is set up perfectly, the AI solutions still tend to make mistakes sometimes. They have become a lot better, especially over the last few months. However, they still tend to make mistakes. The problem with such mistakes is that they are very different from mistakes a human would make. Oftentimes, they are subtle, odd, and hard to spot. Still, they would create a mess if released to production. This is another reason why we always need a human in the loop.

If we put all this together, take a step back from the hype and look at it dispassionately, the current state of AI-based software basically looks like:

- Slice everything down into small chunks, or you may be out of luck.
- Make sure it is a well-known problem, or you may be out of luck.
- Provide a lot of context, or you may be out of luck.
- Provide the context and the instructions over and over again, or you may be out of luck.
- But no matter what you do, sometimes you are out of luck.

This sounds a lot like dealing with an apprentice suffering from attention deficit. We slice the task down into small bites, complement it with lots of additional information, and repeat everything over and over again.

The most ironic part: a big key to success is providing good requirements, good architectural framing, good context, etcetera. The lack of all this is exactly what developers suffered from in the past decades. Most companies actively prevented good requirements, architecture and context engineering due to their efficiency and feature obsession. It was the biggest impediment for developers when they tried to deliver reliable code timely. Requirements sucked. Architecture sucked. Context sucked. Developers pointed out the problems time and again and were turned down. But for AI agents, everyone accepts it as a must-have.

But that is just an ironic side effect worth mentioning. The main point is that AI agents still behave like an apprentice suffering from an attention deficit if we look dispassionately at the current state of affairs.

When confronted with this observation, the regular AI aficionado will tell you that things are so much better than they were a year or two ago. And they are right. Things are a lot better than they were a year ago. On the other hand, this is the least we should expect from the hundreds of billions that were spent on AI in the last year or two.

Still, agentic AI does not feel like a mature technology but like a technology that is still in its early infancy. And this brings me to the point why I do not think we are left behind if we do not immediately go all-in on AI and agentic AI.

### Technology infancy

If I look at the current state of AI solutions, I see something I have seen many times before: technology in its early infancy. If you are as old as I am, you may remember the times when it was crucial to know

- how to set process priorities and nice levels appropriately when starting processes on UNIX machines because otherwise the scheduler often accidentally starved crucial processes.
- the memory layout of a PC and how to squeeze the last bit out of the lower 640 KB to start bigger DOS applications because otherwise they did not start.
- which hints to add to SQL queries because otherwise the optimizer would mess up the access plans.
- how container resource virtualization worked and which disk drivers (not) to use because otherwise disk access became unbearably slow.

And so on. The current state of AI tools feels a lot like this. We need to know a lot of "magic" to get the thing working properly – sort of. Yes, things became a lot more powerful over the last 2 years, but if we are honest, they still feel quite immature and brittle.

### Growing up

This is not a drama. This is a normal evolution we experience with every young and immature technology, and we can draw from other technologies how things will evolve:

- UNIX schedulers became better and better, and eventually nobody needed to set process priorities and nice levels anymore. Today, people start processes on UNIX machines without knowing these concepts.
- DOS was replaced by Windows, including practical memory virtualization concepts, and eventually nobody needed to know about the 640 KB memory barrier anymore. Today, people start applications on PCs without knowing these concepts.
- Database optimizers became better and better, and eventually nobody needed to add hints anymore. Today, people create and run SQL queries without knowing these concepts.
- Container resource drivers became better and better, and eventually people created and ran containers without caring about which drivers to use. Today, people use containers without knowing these concepts.

All that "arcane" knowledge that is crucial in the early days of a new technology eventually becomes irrelevant. More importantly, people were able to enter the realm later without knowing all that stuff. They were able to focus simply on the upsides of the technology and were more productive without needing to burden themselves with all those quirky details.

And this is exactly what we are going to see with AI, too. The tools will become better and better, and eventually, all that secret arcane knowledge currently needed to get useful results will become obsolete.

This is why I say you are not left behind if you do not immediately jump on the bandwagon. And this is why I advise you not to buy the secret recipe from some AI aficionado who promises to share their secret AI sauce for money after a round of fear-mongering. Whatever they tell you about which tricks you need to apply to become an AI winner, this knowledge will be obsolete in a year.

I mean, do you still remember the fuss people made about "prompt engineering" two years ago? A whole training industry emerged in no time, with everyone selling their secret sauce to success. Companies looking for prompt engineers, partially offering ridiculous salaries. And today? Basically obsolete knowledge. The models and the agent frameworks have become so much better that all this knowledge from a year ago is hardly worth anything anymore.

Hence, from a tooling perspective, it could be even better to wait a bit until the usage of the tools becomes straightforward and we do not need to know secret handshakes and other quirky rituals anymore to get the expected results from them.

### The inflection point trap

However, before you think you can safely ignore AI for the next 2 or 3 years because the technology is not yet mature, there is a catch – which brings me to the second part of my answer at the beginning of this post.

The catch is not about the tooling and what you need to know to get useful results. It is about not missing the inflection point. Let me share a quick story from the past to explain what I mean:

I knew some guys back in the early 1990s who were convinced that Windows will never make it on a PC, that DOS will persist as the dominant OS. Windows was still in its infancy and working with it was a mess back then (if you worked with Windows 3.0 as I did, you know what I mean). Developing Windows applications was even messier. The API was cumbersome, relevant parts undocumented, and the whole OS was everything but stable. Therefore, those guys came to the conclusion that ignoring Windows and continuing developing DOS applications was a safe bet.

For a while, this was fine. But gradually, things became unpleasant.

The problem was that those guys ignored the ongoing development of Windows after they made their choice. This way, they were still solely focused on DOS when it became obvious that DOS was a goner. But at this point in time, it was too late for them to migrate their business to the meanwhile dominant Windows. They were actually left behind. Their accumulated knowledge and experience had become worthless, and they basically needed to start from scratch – against competitors with years of experience.

They did not run into the problem because they did not immediately go all-in when Windows became popular. They ran into the problem because they missed the ongoing evolution of Windows and how the market shifted over time. With that, they missed the relevant inflection points: the first inflection point being when it became necessary to add Windows development to their portfolio (while still being able to make a living from DOS development), and the second inflection point being when it became time to let go of DOS and completely focus on Windows development.

When applying this story to AI, it becomes clear that completely ignoring the evolution of AI is probably not a good idea, even if the technology is still in its infancy. It is important to understand how the technology evolves and where the market is heading to not miss the inflection points.

### Applying it to software development

Looking at AI in the realm of software development, we realize a bit paradoxical situation. Even though the technology is obviously still in its infancy, we face a significant market demand towards using it. Usually, the market majority picks up a technology only after it has reached a certain degree of maturity. Before, only the innovators and early adopters tended to use it.

With AI, it is somewhat different. The AI investors and vendors relentlessly pushed their intrusive and fear-mongering marketing messages, backed by billions of dollars, trying to game the market and make the majority pick up AI earlier than they usually would. And to a certain degree, their strategy was successful. AI was picked up by the mainstream a lot earlier than the tooling reached the usually required maturity – especially in software development.

As a consequence, the first inflection point is about now in software development. Even if the tooling is still in its infancy, the market is crying for AI-based software development. Nevertheless, it becomes increasingly risky to ignore AI in software development completely.

This does not mean that you need to go all-in immediately. It especially does not mean you need to learn all those secret recipes needed to convince the still immature tooling to do exactly what you expect. But you should familiarize yourself well enough with the possibilities and limitations of AI-based coding to be able to use it if needed and understand the ongoing evolution. Doing this, you will acquire some knowledge that will be worthless in a year. And maybe you will not immediately become an "AI rockstar". But that is okay. It is about understanding the development of the technology, the evolution of its possibilities and limitations.

In other domains, the first inflection point may not yet have come. Still, keeping an eye on the ongoing evolution is probably a good idea.

It is not yet clear when the second inflection point will be. It may be in a few months. It may be in a few years. It may be later. It may never arrive. We do not know yet.

Overall, this means, even if we already need to pick up AI-based software development while the tooling is still in its infancy, we are not left behind if we do not know all the tricks and secret recipes needed to get the desired results from the still immature tooling. Regarding the tooling, time will work for us, not against us. But we still need to understand AI-based software development well enough to understand when the second inflection point is about to come.

### Summing up

Many people, especially the (wannabe) profiteers of AI, want to make us believe that if we do not go all-in with AI *now* and learn all those tools and tricks on how to get them properly working, we would be left behind.

This is not true. We are not left behind if we do not learn all the tools and the secret recipes needed to get them (halfway) properly working.

If we look at the state of the current tooling, we realize it is still in its infancy, far from being mature. We know from many examples of the past that knowing all the quirks needed to get immature tools working properly quickly becomes irrelevant knowledge. Therefore, you are not left behind if you do not know perfectly how to use the currently available tools. Actually, most of the knowledge you accumulate today will be worthless in a year or so.

However, especially in software development, it is quite likely that AI-based software development will eventually become the predominant paradigm and the tools will mature. Therefore, it is highly advisable not to ignore AI-based software development even if the tooling is still highly immature. Instead, it is important to follow the evolution and understand the technology well enough to know when the inflection points arrive.

In short:

- The secret recipes of the (wannabe) AI experts are not the important part when it comes to being "left behind" or not. Most of today's expert knowledge will be worthless in a year because the technology evolves quickly and is still far from mature.
- Completely ignoring the technology and its evolution on the other side is risky because you may miss the point when you need to pick it up. Then you actually may be left behind and have to start over from scratch, which may be very hard.

Thus, my conclusive recommendation is:

> Do not fall for the fear-mongering messages regarding AI.
>
> Still, watch the AI evolution closely enough to be prepared when the inflection points arrive.

Or, as a meditation teacher might phrase it: "Find a relaxed, yet alert position" … ;)
