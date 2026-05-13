# The Context Problem

*[← AI for Engineers is Clear. AI for Managers is Not.](./01-the-em-inflection-point.md) | [Home](../README.md) | [Next →](./03-the-efficiency-trap.md)*

---

Management is, at its core, a context-holding job.

I carry a running model of every person on my team — where they are in their career, what's frustrating them, what they're proud of, what they need from me right now. I hold context for the team as a whole — its health, its direction, its gaps, the unspoken dynamics that don't show up in any ticket or status update. And I hold organizational context — what's shifting, what's expected, what matters this quarter versus last, which relationships need tending and which fires are real versus noise.

On top of that, I also serve as the product and project manager for my team. That means I'm holding a second layer of context simultaneously: what we're building and why, how the work maps to organizational priorities, what's in flight and what's at risk, where the dependencies are, and what the team has committed to delivering and by when. The people context and the work context are constantly intersecting — understanding a delivery risk often means understanding who's carrying it and what else they're dealing with.

None of that lives in a single document. It lives in my head, accumulated over dozens of conversations, built up over months of observation and follow-through.

---

## The Cost of Context Loss

Every time I lose that context — after a vacation, after a long gap between 1:1s, after any significant interruption — I pay a reconstruction tax. I spend the first part of every interaction rebuilding what I already knew before I can get to the actual work.

For engineers, context loss is annoying but manageable. They re-read the code, re-run the tests, catch up on the PR comments. The context is largely external — it lives in the codebase and the ticket history. It can be recovered.

For managers, context loss is structural. The context I hold is relational and historical, and much of it doesn't exist anywhere outside my own memory. I can't re-read a person the way I re-read a codebase. The reconstruction tax is real, and it compounds every time I lose the thread.

---

## Where AI Makes It Worse First

When I first started bringing AI into management work, I ran into an immediate problem: AI has no memory between sessions. Every conversation starts from zero.

So every time I wanted help with something real — preparing for a 1:1, thinking through a team dynamic, working through a difficult conversation — I had to re-explain my entire world first. Who's on my team. What their situations are. What the org context is. What's happened recently that matters. The history behind the question I was actually trying to ask.

It was more friction, not less. I was spending the first ten minutes of every session just getting Claude back up to speed, and even then the answers felt thin because there was no way to fully reconstruct six months of accumulated context in a few paragraphs.

A simple example: asking Claude to help draft a Slack message to the team about an upcoming org change. Without context, the output was technically correct but culturally hollow — generic encouragement, no acknowledgment of what the team had been through recently, no awareness of the specific concerns people had already voiced. Management communication isn't just information transfer. It's signal. It tells people whether their manager actually knows them and the situation. A message that could have been written by anyone, for any team, sends exactly that signal.

The tool that was supposed to help me think was constantly starting from scratch, while I already knew everything it needed to know and was just tired of explaining it again.

---

## The Insight

That frustration led to a reframe that changed everything.

But first, I had to understand what the frustration was actually pointing at. It wasn't a tool problem or a workflow problem. It was a structural mismatch: the directive to use AI assumed the tool could meet me where I was. But the nature of management work — built on accumulated, relational, hard-won context — ran directly into AI's fundamental design constraint. Every session started from zero. The thing that makes me effective as a manager was exactly the thing AI couldn't hold.

That gap wasn't going to close on its own. And until it did, every attempt to use AI for real management work would produce shallow results — not because the tool wasn't capable, but because it was operating blind.

That's when the clarity came.

Context isn't a prerequisite to doing the work. For managers, context *is* the work. The whole value I provide — the coaching, the judgment calls, the well-timed check-in, the accurate read on what's actually going on — flows from the context I hold. Strip that away and what's left is surface-level management.

Which means solving the context problem isn't a nice-to-have for AI-augmented management. It's the foundation. Nothing else works without it.

---

## Context as Infrastructure

Once I started treating context as infrastructure — something to build deliberately and maintain over time, not something to reconstruct on demand — the whole picture changed.

It was more upfront investment than I expected. But the return was immediate and compounding: every session started closer to where the last one left off. The reconstruction tax dropped. The quality of every conversation improved.

It started with the basics: a contacts file with everyone I work with, their roles, their handles, the relevant context about who they are. A links file with the tools and spaces I navigate repeatedly. A patterns file capturing the conventions and quirks of how my team and org actually operate — the things that take months to learn and seconds to forget to mention.

From there it built up: organizational context capturing the active themes shaping how I lead right now — a reorg in progress, a team member on leave, a cultural shift that's creating uncertainty. Not static facts, but living context with a shelf life, updated as things change.

And at the top: preferences. How I like to communicate, how I think about tradeoffs, what I expect from these interactions and what I don't. This is the layer that makes AI responses feel like they came from a partner who knows me, rather than a generic assistant who happens to be smart.

Each layer builds on the one below it. None of it is complicated to create — but all of it requires the deliberate decision to treat context as something worth investing in. The details of how each piece is structured and maintained are covered in the [Solution section](../solution/01-data-layer.md).

---

*[← AI for Engineers is Clear. AI for Managers is Not.](./01-the-em-inflection-point.md) | [Home](../README.md) | [The Efficiency Trap →](./03-the-efficiency-trap.md)*
