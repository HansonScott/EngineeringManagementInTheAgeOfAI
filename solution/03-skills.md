# Custom Skills: Encoding the Patterns That Kept Repeating

*[← Integrations](./02-integrations.md) | [Home](../README.md) | [Next →](./04-em-skill.md)*

---

Before I had custom skills, I had habits. The same sequence of steps before every 1:1. The same ritual of checking four different systems after a vacation. The same weekly scramble to draft status updates before the deadline. None of it was particularly hard — it was just repetitive, context-dependent, and easy to do slightly wrong.

Skills are the encoded version of those habits. They're not automation in the fire-and-forget sense. They're structured workflows that Claude follows consistently, informed by my data layer, integrated with my tools. The goal isn't to replace judgment — it's to remove the parts that don't require it.

---

## The Pattern That Became a Skill

Every repeating workflow followed the same arc:

1. I did the thing manually a few times and noticed the steps
2. I realized the steps were the same every time, just with different inputs
3. I noticed I was re-explaining the steps to Claude in each new session
4. I wrote them down once as a skill file

That's it. Skills aren't architecture. They're documented patterns — the operational equivalent of a runbook, except Claude executes them instead of a person.

---

## The Skills

### catch-me-up

**The friction it solved:** Every Monday morning, and every return from time off, I was doing the same thing: checking Slack for what I missed, scanning Jira for updates, reviewing my calendar for what's coming, and skimming email. Four systems, 20–30 minutes, before I could actually think.

**What it does:** Determines the lookback window automatically from my calendar (detecting OOO events and weekends), then scans Slack channels, Jira issues, Gmail, and the upcoming calendar in parallel. Surfaces only the things that matter: decisions made, blockers named, things assigned to me, and anything that needs a response. Confirms the window before running.

**What I get:** A single synthesis — "here's what happened while you were away, here's what needs your attention today" — in under two minutes. The morning no longer starts with context reconstruction.

---

### 1on1-prep

**The friction it solved:** Before a 1:1, I'd open the notes doc, check Slack for recent messages from that person, think about what we talked about last time, try to remember if I had any open commitments. This worked, but it was scattered. I frequently started conversations without the full picture.

**What it does:** Given a name, reads their personal notes doc (durable context: family, values, career goals), their 1:1 notes doc (recent meeting history), recent Slack activity, and recent GitHub PR work. Synthesizes a pre-meeting brief: what's top of mind for them, what I committed to last time, what's been happening in their work, and what I should probably ask about.

**What I get:** Walking into every 1:1 with the full picture already assembled. The conversation can start at the level it should, not at the level of "let me pull up my notes."

---

### 1on1-followup

**The friction it solved:** After a 1:1, three things needed to happen: capture what I learned about the person as a human, log anything worth tracking as a manager signal, and surface what needs follow-through. Without a system, personal details got lost, signals went uncaptured, and follow-ups lived in my head until they didn't.

**What it does:** Pulls the Zoom AI summary, identifies all attendees against my contacts roster, reads their existing personal notes docs, and presents a consolidated proposal: meeting summary, follow-up suggestions, personal details worth capturing (classified by type — family, hobbies, work perspectives, watch items), and EM workflow signals observed. Nothing is written until I confirm.

**What I get:** A personal notes layer that actually grows over time. The "I remember you mentioned your kid was starting school" moment — that's not memory, that's a system. The system makes it consistent.

---

### initiative-update

**The friction it solved:** Every week, my manager's team needed a progress update on each active engineering initiative. Writing these from scratch meant pulling Jira status, checking GitHub for recent PRs, scanning Slack for context, and synthesizing it into a coherent paragraph per initiative — for multiple initiatives at once. It was the kind of work that felt important but didn't require me specifically.

**What it does:** Gathers signals from Jira, GitHub, and Slack in a single pass, determines the right lookback window per initiative based on when the last update was posted, cross-references PR work against active epics, drafts a comment per initiative, and presents them for review before posting.

**What I get:** Weekly updates that take five minutes instead of forty-five. More importantly: because the research is thorough and consistent, the updates are actually more accurate than what I was writing by hand when I was in a hurry.

---

## What Skills Are Not

Skills don't replace thinking. They remove the work that doesn't require it.

The 1:1 prep skill doesn't decide what to talk about — I do. The initiative-update skill doesn't judge whether the team is making progress — I do. What these skills do is make sure I'm operating from complete information, consistently, without spending my time on the retrieval and assembly that Claude can do faster and more reliably than I can.

The goal was never to automate management. It was to make sure management work happened at the right level: human judgment applied to well-organized context, instead of human judgment buried under information archaeology.

---

*[← Integrations](./02-integrations.md) | [Home](../README.md) | [EM Skill →](./04-em-skill.md)*
