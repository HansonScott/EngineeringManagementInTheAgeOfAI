# The Objectivity Problem

*[← The Efficiency Trap](./03-the-efficiency-trap.md) | [Home](../README.md) | [Next →](./05-the-altitude-problem.md)*

---

Here's something nobody tells you when you start using AI as a thought partner: it will agree with almost everything you say.

Not because it's wrong — it's often right. But because it's trained to be helpful. And helpful, in the context of a conversational AI, tends to mean supportive, constructive, and affirming. When you share an idea, it finds merit in it. When you describe your approach, it validates the logic. When you ask if something sounds right, it usually tells you that it does.

This is fine for a lot of use cases. If you're asking for help writing something, enthusiastic support is useful. But if you're trying to evaluate your own leadership — to actually see your blind spots — a yes-man is actively counterproductive.

---

## What I Noticed

I was building the EM skill and I started to realize something uncomfortable. Every time I described my thinking about a situation, Claude responded warmly. Every time I proposed a course of action, it found ways to affirm it. The conversations felt good. The feedback felt validating.

And I started to wonder: was I actually getting an honest read on my own performance, or was I just getting a sophisticated mirror that reflected my own views back at me in cleaner language?

I tested it. I floated ideas I wasn't sure about. I described approaches I had genuine doubts about. The responses were supportive, occasionally with light caveats, but fundamentally affirming.

That's not evaluation. That's encouragement.

For casual use, encouragement is fine. But I was trying to build a system that would tell me when I was getting something wrong — when I was spending time on the wrong things, when a team member needed more from me than I was giving, when I was operating below my altitude. A system that only confirms my existing views is worse than no system at all, because it creates false confidence.

I needed something different.

---

## The Problem with Self-Referential Evaluation

The deeper issue is that any evaluation system anchored to your own perspective will eventually just reflect your own blind spots back to you.

Managers have a particular vulnerability here. We operate in domains with low observability and long feedback loops. Engineers get immediate feedback from compilers, tests, and users. Managers get feedback from team behavior, attrition, performance, and culture — months or years after the decisions that shaped it. In the meantime, we mostly evaluate ourselves.

Self-evaluation has a well-documented flaw: we tend to evaluate ourselves against what we intended, not what we actually did. We remember the difficult conversation we had in our head. We credit the good coaching we meant to give. We don't notice what we avoided, what we minimized, what we didn't bring enough curiosity to.

An AI that learns your perspective and responds to your inputs will replicate this flaw. It will evaluate you against your stated intentions, not your observable behavior. It will see what you see.

The only way out is to anchor the evaluation to something external.

---

## External Standards as the Solution

What actually changed things for me was building the evaluation against my company's published expectations for the role — not my own conception of what I should be doing.

My organization had documented what good engineering management looked like: the competencies, the behaviors, the signals of health and the signals of risk. I had read it. But reading it and being regularly evaluated against it are very different things.

When the system could compare my actual behavior — drawn from meeting notes, calendar data, task completions, team activity — against those external standards, something shifted. The question stopped being "does this seem like reasonable leadership?" and became "does this match what's expected of the role?"

The difference is significant. When the standard is external:

- The evaluation doesn't move when my self-perception moves
- Gaps become visible even when I think things are going well
- The system can say "you haven't had a meaningful career conversation with this person in two months" without caring whether I feel like that's true

The AI is still affirming in its tone. But the evaluation is grounded in something it can't just validate away.

---

## The Lesson

If you're building AI support for your own work, pay attention to what you're anchoring it to.

If you ask an AI to evaluate you against your own sense of what good looks like, it will mostly tell you you're doing well. If you give it external standards — a role definition, a competency framework, a set of explicit expectations — it can actually surface the gaps between where you are and where you should be.

The affirming AI isn't broken. It's just not the right tool for self-evaluation unless you give it something outside yourself to evaluate against.

That's the design insight that made the difference.

---

*[← The Efficiency Trap](./03-the-efficiency-trap.md) | [Home](../README.md) | [The Altitude Problem →](./05-the-altitude-problem.md)*
