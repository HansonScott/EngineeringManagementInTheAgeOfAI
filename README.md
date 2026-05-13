# Engineering Management in the Age of AI

*By Scott Hanson — Engineering Manager*

---

In Q4 2025, my organization told us that using AI was now a baseline expectation for management excellence. Not a suggestion. A baseline.

For engineers, the path forward was obvious: use AI to write faster, debug smarter, review more thoroughly. The tooling was everywhere and the feedback loop was immediate.

For managers, it was less clear.

Most of what I do as an Engineering Manager isn't code. It's information — absorbing it, synthesizing it, acting on it, and surfacing the right pieces at the right moments for the right people. It's context: knowing where each person is in their career, what's blocking the team, what's drifting, what's been said and what hasn't. It's presence: being prepared for every 1:1, following through on what I heard, remembering the person behind the work.

None of that has an obvious AI play. And yet, it's almost entirely information work. Turns out AI is really good at information work.

This repo documents what I explored, what I learned, what I built — and the bigger questions of *why* that I had to answer along the way.

---

## The Core Argument

I spent the first several months using AI to do my existing job faster — preparing for meetings, following up on 1:1s, writing Jira updates, getting back up to speed after an absence. It helped. I got hours back every week.

But I started to notice something uncomfortable. I was doing the same things faster, but I wasn't sure I was doing the right things. The urgency of the day still dominated. The important-but-not-urgent work still slipped. I still sometimes left a 1:1 wondering if I'd said the right thing, covered the right ground, seen what was actually in front of me.

I am more efficient — but am I making the right impact?

What I needed wasn't a better tool. I needed a thought partner — something that could help me step back from the daily grind and ask: *Am I leading well? Am I showing up the way my team deserves?* Something grounded in external standards, not just my own instincts.

So that's where it started. Those questions inspired me to keep exploring and building — until I had something that actually functioned as that thought partner.

What emerged isn't just a productivity system. It's a framework that has made me a more strategic and intentional leader: one who shows up to every 1:1 prepared, who tracks team health across a wide variety of distinct EM-specific workflow areas, who surfaces blind spots before they become problems, and who regularly steps back to ask whether the work I'm doing is the work that actually matters.

---

## What's Here

This repo is organized into four sections:

### [Philosophy](./philosophy/)
Five essays on the underlying challenges that make AI-augmented EM both necessary and non-obvious. Each one stands alone. Start here if you want the thinking before the building.

- [The EM Inflection Point](./philosophy/01-the-em-inflection-point.md) — Why the directive to "use AI" hits differently when your job is people, not code
- [The Context Problem](./philosophy/02-the-context-problem.md) — EM work is a context-maintenance problem, and context is expensive
- [The Efficiency Trap](./philosophy/03-the-efficiency-trap.md) — Getting faster is not the same as getting better
- [The Objectivity Problem](./philosophy/04-the-objectivity-problem.md) — AI is trained to be helpful, which makes it dangerously affirming
- [The Altitude Problem](./philosophy/05-the-altitude-problem.md) — The EM role is strategic; everything about the day-to-day pulls you tactical

### [Journey](./journey/)
The story of how this system came to be — the frustrations, the insights, and the pivots.

- [Discovery](./journey/01-discovery.md) — Teaching an AI your world, and what it costs to not do that
- [Evolution](./journey/02-evolution.md) — From ad-hoc tool to custom skills to the bigger question

### [Solution](./solution/)
The architecture of what I built: a layered system that starts with persistent context and builds up to strategic leadership support.

- [System Overview](./solution/README.md) — The full stack and why each layer exists
- [The Data Layer](./solution/01-data-layer.md) — Memory, preferences, contacts, and the init skill
- [Integrations](./solution/02-integrations.md) — Slack, Jira, Zoom, and Google as a unified interface
- [Custom Skills](./solution/03-skills.md) — catch-me-up, 1:1 prep, meeting follow-up, and status updates
- [The EM Skill](./solution/04-em-skill.md) — 22 workflows, signal tracking, and the strategic pulse

---

## A Note on What This Isn't

This isn't a template to copy. Every manager's world is different — different team, different company, different role expectations, different tools. The specific files I built reference my specific context.

What might be worth borrowing is the *approach*: start with the context problem, build integrations deliberately, let patterns emerge before automating them, and eventually ask the harder question about what all of it is actually for.

This is what that looked like for me.

---

*[Start with the philosophy →](./philosophy/01-the-em-inflection-point.md)*
