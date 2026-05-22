# Custom Skills: Encoding the Patterns That Kept Repeating

*[← Integrations](./02-integrations.md) | [Home](../README.md) | [Next →](./04-em-skill.md)*

---

Before I had custom skills, I had habits. The same sequence of steps before every 1:1. The same ritual of checking four different systems after a vacation. The same weekly scramble to draft status updates before the deadline. None of it was particularly hard. It was just repetitive, context-dependent, and easy to do slightly wrong, or forget altogether.

Skills are the encoded version of those habits. They're not automation in the fire-and-forget sense, most of them are explicitly interactive. They surface what they find, present drafts for review, and pause before writing anything. I guide the intent; Claude does the research and assembly; I make the call. The workflow is structured, but the conversation is real. The goal isn't to replace judgment: it's to make sure judgment is the only thing I'm doing.

---

## The Pattern That Became a Skill

Every repeating workflow followed the same arc:

1. I did the thing manually a few times and noticed the steps
2. I realized the steps were the same every time, just with different inputs
3. I noticed I was re-explaining the steps to Claude in each new session
4. I wrote them down once as a skill file
5. I ran it, hit the edge cases, and updated the file when reality didn't match the assumption
6. I kept refining it as my process matured: the skill grows when the workflow grows

That's it. Skills aren't architecture. They're documented patterns, the operational equivalent of a runbook, except Claude executes them instead of a person. They're also living documents. The ones I use most have been through several versions: tightened after edge cases, extended when the workflow expanded, simplified when I realized I'd over-engineered something early.

What follows are the skills that have become load-bearing in my daily work as an engineering manager. Some run every day. Some run every week. A few run quarterly. All of them replace something I was doing manually, inconsistently, or not at all.

---

## The Skills

### catch-me-up

**The friction it solved:** Every Monday morning, and every return from time off, I was doing the same thing: checking Slack for what I missed, scanning Jira for updates, reviewing my calendar for what's coming, and skimming email. Four systems, 20-30 minutes, before I could actually get to work.

**What it does:** Determines the lookback window automatically from my calendar (detecting OOO events and weekends), then scans Slack channels, Jira issues, GitHub PRs, Gmail, and the upcoming calendar in parallel. Surfaces only the things that matter: decisions made, blockers named, team PRs opened or merged, things assigned to me, and anything that needs a response. Confirms the window before running, then delivers two things: what happened since I was last in, and what needs attention today.

**What I get:** A single synthesis in under two minutes. The morning no longer starts with context reconstruction.

---

### 1on1-prep

**The friction it solved:** Before a 1:1, I'd open the notes doc, check Slack for recent messages from that person, think about what we talked about last time, try to remember if I had any open commitments. This worked, but it was scattered. I frequently started conversations without the full picture.

**What it does:** Given a name, reads their personal notes doc (durable context: family, values, career goals, life events), their 1:1 notes doc (recent meeting history), recent Slack activity, GitHub PRs authored and reviewed, and Zoom AI summaries from recent team meetings. It also surfaces personal context as conversation anchors: sports teams, hobbies, significant things happening in their life. Synthesizes a pre-meeting brief: what's top of mind for them, what I committed to last time, what's been happening in their work, and what I should probably ask about.

**What I get:** Walking into every 1:1 with the full picture already assembled: the work context and the human context. If someone has a sick parent, a new baby, or a big move coming up, that context shapes the conversation before it starts. The "I remember you mentioned your team made the playoffs" moment isn't luck or a good memory. It's a system that makes that kind of care consistent.

---

### 1on1-followup

**The friction it solved:** After a 1:1, three things need to happen: capture what I learn about the person as a human, log anything worth tracking as a manager signal, and surface what needs follow-through. Without a system, I could do all of these, just not as completely or consistently as I wanted to.

**What it does:** Pulls the Zoom AI summary, identifies all attendees against my contacts roster, reads their existing personal notes docs, and presents a consolidated proposal: meeting summary, follow-up suggestions, and personal details worth capturing (classified by type: family, hobbies, work perspectives, watch items). Nothing is written until I confirm.

**What I get:** A relationship that deepens over time. Every conversation adds a layer: something they mentioned about a family situation, a career aspiration they floated, a frustration they named indirectly. Captured consistently, those layers accumulate into a genuine understanding of each person: not just what they're working on, but who they are, what they care about, and what they need from me as a manager.

---

### initiative-update

**The friction it solved:** Every week, my manager needs a progress update on each active engineering initiative. If I'm being honest, my manual process wasn't careful research, it was gut feel with minimal facts. I'd write from memory, approximate the status, and move on. The updates went out, but they weren't grounded in what was actually happening in Jira, GitHub, or Slack that week.

**What it does:** Gathers signals from Jira, GitHub, and Slack in a single pass, determines the right lookback window per initiative based on when the last update was posted, cross-references PR work against active epics, drafts a comment per initiative, and presents them for review before posting.

**What I get:** Weekly updates that take five minutes instead of forty-five. More importantly: because the research is thorough and consistent, the updates are actually more accurate than what I write by hand when I'm in a hurry.

---

### recognize

**The friction it solved:** Recognition is easy to mean and hard to do consistently. When I'm heads-down in a sprint, the people who deserve a shout-out last week don't always get one, not because I don't care, but because "send recognition" doesn't survive a busy afternoon. And when I did remember, I often couldn't reconstruct the specifics well enough to write something genuine.

**What it does:** Scans recent signals across Slack, GitHub, Jira, 1:1 notes, and meeting notes to surface recognition candidates, both my direct reports and cross-team collaborators. Drafts messages using the SBI model (Situation, Behavior, Impact), grounded in the actual facts the research surfaces: the specific PR, the Slack thread where someone unblocked a teammate, the meeting where they spoke up. Two tiers: lightweight shoutouts for good work, point-backed awards for significant effort. Tracks past recognitions to flag when someone is due for something more.

**What I get:** Recognition that actually happens, on a regular cadence, and is specific enough to land. Generic recognition feels like a checkbox. Recognition that names the moment: what happened, what they did, why it mattered. That feels like someone was actually paying attention. The skill does the research so I can do the latter, consistently, without relying on memory or a clear afternoon.

---

### todo

**The friction it solved:** Everyone has a task list. The problem isn't capturing tasks: it's that most task apps are invisible to the tool where the work actually happens. Claude can't see what's in Reminders or Asana without being told. That means priorities still have to be brought to each session manually, and they don't always make it.

**What it does:** Manages a structured plain-text file that Claude reads at session start: open tasks surface automatically, before the first message. Any session can add, update, or complete items mid-conversation without context switching. Items carry structured metadata: priority, level of effort, due date, and notes. Completing an item archives it with full context preserved, so there's a searchable history of what got done and why.

**What I get:** A task list that's part of the conversation, not separate from it. When a commitment surfaces in a 1:1, I say "add that to my todo" and it's captured. When I start a session, my open priorities are already on the table. When I'm deep in a performance cycle, I can pull every task I've completed in that area over the past quarter. The list doesn't live in a separate app I have to remember to check, it lives where the work happens.

---

## Beyond the Core: Narrow Skills with Real Value

The weekly skills came first, they were the obvious candidates, the workflows I touched every day. But over time I started noticing a different category: complex, infrequent tasks that required me to reconstruct the process from scratch each time they came around.

The work wasn't hard. The overhead was. Re-learning the steps, double-checking the sequence, holding the edge cases in mind for something I only do a few times a year. That's cognitive load with no return. Once the task is done, all of that context evaporates until next quarter.

The answer was the same as it was for the weekly habits: write it down once. A quarterly compliance audit is the clearest example: two systems, cross-referenced against an access list, evidence captured and documented before a deadline. It became a skill. Now it runs consistently every quarter without requiring me to carry the process in memory between runs. I show up, guide the intent, and review the output.

The principle generalizes: complex, infrequent workflows with a defined correct output are skill candidates too. The process lives in the file. My head stays clear.

---

## What Skills Are Not

Skills don't replace thinking. They take on everything that falls below the judgment line.

The 1:1 prep skill doesn't decide what to talk about, I do. The initiative-update skill doesn't judge whether the team is making progress, I do. What these skills do is make sure I'm operating from complete information, consistently, without spending my time on the retrieval and assembly that Claude can do faster and more reliably than I can.

The goal was never to automate management. It was to make sure management work happens at the right level: human judgment applied to well-organized context, instead of human judgment buried under information archaeology.

---

*[← Integrations](./02-integrations.md) | [Home](../README.md) | [EM Skill →](./04-em-skill.md)*
