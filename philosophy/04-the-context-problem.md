# The Context Problem

*[← Finally, the Data](./03-finally-the-data.md) | [Home](../README.md) | [Next →](./05-the-efficiency-trap.md)*

---

Management is, at its core, a context-holding job.

I carry a running model of every person on my team — where they are in their career, what's frustrating them, what they're proud of, what they need from me right now. I hold context for the team as a whole — its health, its direction, its gaps, the unspoken dynamics that don't show up in any ticket or status update. And I hold organizational context — what's shifting, what's expected, what matters this quarter versus last, which relationships need tending and which fires are real versus noise.

On top of that, I also serve as the product and project manager for my team. That means I'm holding multiple layers of context simultaneously: what we're building and why, how the work maps to organizational priorities, what's in flight and what's at risk, where the dependencies are, and what the team has committed to delivering and by when. The people context and the work context are constantly intersecting — understanding a delivery risk often means understanding who's carrying it and what else they're dealing with.

None of that lives in a single document. It lives in my head, accumulated over dozens of conversations, built up over months of observation and follow-through.

---

## The Cost of Context Loss

Every time I lose that context — after a vacation, after a long gap between 1:1s, after any significant interruption — I pay a reconstruction tax. I spend the first part of every interaction rebuilding what I already knew before I can get to the actual work.

For engineers, context loss is annoying but manageable. They re-read the code, re-run the tests, catch up on the PR comments. The context is largely external — it lives in the codebase and the ticket history. It can be recovered.

For managers, context loss doesn't recover the same way. The context I hold is relational and historical, and much of it doesn't exist anywhere outside my own memory. I can't re-read a person the way I re-read a codebase. The reconstruction tax is real, and it compounds every time I lose the thread.

---

## Where AI Makes It Worse First

When I first started bringing AI into management work, I ran into an immediate problem: AI has no memory between sessions. Every conversation starts from zero.

A simple example: asking Claude to summarize a meeting and draft follow-up items. The Zoom transcript included action items attributed to someone named Huddle. Huddle is not a person — it's a conference room. In Zoom, everyone speaking from a shared hardware room shows up under a single label, and without that context, Claude dutifully assigned follow-up tasks to a team member who doesn't exist while leaving the actual attendees unaddressed.

It was funny, in the way that immediately-obvious mistakes are funny. But it landed precisely. The output wasn't wrong because AI was incapable. It was wrong because the tool had no way to know what I knew without thinking about it: that Huddle is a room, not a person, and that conference room dynamics matter when you're assigning next steps to a team.

It was more friction, not less. I was spending the first ten minutes of every session just getting Claude back up to speed, and even then the answers felt thin because there was no way to fully reconstruct six months of accumulated context in a few paragraphs.

A second example: asking Claude to help draft a Slack message to the team about an upcoming org change. Without context, the output was technically correct but culturally hollow — generic encouragement, no acknowledgment of what the team had been through recently, no awareness of the specific concerns people had already voiced. Management communication isn't just information transfer. It's signal. It tells people whether their manager actually knows them and the situation. A message that could have been written by anyone, for any team, sends exactly that signal.

I knew everything it needed. Explaining it from scratch every session wasn't a workflow — it was a tax that made the tool impractical for real use.

---

## The Insight

I started asking a different question. Not "why isn't this working?" but "what does this tool actually need that it isn't getting?"

The answer, when I finally sat with it, was simple: it didn't know anything about my world.

That sounds obvious in hindsight. But it took a while to name clearly, because the problem wasn't the output — it was the input. Claude could write. Claude could reason. Claude could structure. What it couldn't do was apply any of that to my team, my org, my context — because I hadn't given it any.

That's when I learned about memory files. I'd heard of them in a developer context — a way to give Claude persistent awareness of a codebase, project conventions, technical decisions. Useful, but not obviously relevant to management work. What I hadn't considered was applying the same idea beyond the project: as a persistent awareness of my world. Who I work with. How my org operates. What's in motion right now. Not technical context, but human context — and it turns out that's exactly what was missing. Written down, structured, and loaded into every session. Not pasted in once, but maintained over time. Infrastructure, not a workaround.

That's when it clicked. Context isn't a prerequisite to doing the work. For managers, context *is* the work. The whole value I provide — the coaching, the judgment calls, the well-timed check-in, the accurate read on what's actually going on — flows from the context I hold. Strip that away and what's left is surface-level management.

Which means solving the context problem isn't a nice-to-have. It's the foundation. Nothing else works without it.

---

## Context as Infrastructure

That framing gave me a clear direction. If context is infrastructure, then it needs to be built like infrastructure — deliberately, over time, not reconstructed from scratch on demand.

It required more upfront investment than I expected. But the return was immediate and compounding: every session started closer to where the last one left off. The reconstruction tax dropped. The quality of every interaction improved — not because AI got smarter, but because it finally had what it needed to be useful.

The specifics of how that infrastructure is built and maintained are in the [Solution section](../solution/01-data-layer.md). But the decision that unlocked it wasn't technical. It was accepting that if context is the work, then building it deliberately isn't overhead. It's the job.

---

*[← Finally, the Data](./03-finally-the-data.md) | [Home](../README.md) | [The Efficiency Trap →](./05-the-efficiency-trap.md)*
