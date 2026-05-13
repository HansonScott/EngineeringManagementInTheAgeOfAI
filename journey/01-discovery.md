# Discovery: Teaching an AI Your World

*[← Home](../README.md) | [Next →](./02-evolution.md)*

---

The first thing I did with AI was ask it to help me draft a message.

It was fine. It helped. But then I needed to explain who the message was for, what team they were on, what our working relationship was, what the context of the situation was. By the time I finished explaining, I could have written the message myself.

That's the first wall every manager hits with AI: the context gap.

Engineers can describe their codebase, paste in a file, share an error. The context is concrete and transferable. For a manager, the context is relational — it lives in the history of conversations, the texture of team dynamics, the shorthand that only makes sense inside a particular org. You can't paste that.

Every new session started fresh. I'd spend the first ten minutes re-explaining what my team was called, who was on it, what we were working on. I'd describe the same tools over and over. I'd restate preferences that I'd already stated a dozen times.

It was frustrating enough that I almost stopped.

---

## The Insight: Context Is Infrastructure

What changed things was recognizing that context isn't just helpful — it's foundational. Without it, you're not really getting AI assistance. You're getting a general-purpose language model that happens to be responding to you.

The session-to-session amnesia wasn't a bug I had to work around. It was a design constraint I needed to solve for explicitly. The solution wasn't to explain more patiently — it was to build a persistent layer that the AI could load before I said a word.

So I started building.

The first file was simple: who I am, what I do, how I like to work. A preferences file. Two pages. I pointed the AI at it before each session and the difference was immediate — fewer clarifying questions, faster responses, recommendations that fit my actual situation.

Then I built a contacts file. This one got long. It started as a list of my team members — names, roles, and a sentence about each. But it kept growing. I added their communication handles so the AI could look people up without asking. I added their GitHub profiles so it could check their activity. I added context about our working relationship and what I was tracking with each person.

---

## The Huddle Incident

There's a moment that crystallized why the contacts file mattered.

My team used a recurring meeting room for standups. In our organization, that room had a name — and our AI tools kept treating the room name as a person. The AI would reference "updates from Huddle" or "Huddle mentioned concerns about the timeline" as if Huddle were a colleague with opinions.

Every time this happened, I had to stop and correct it. Multiple sessions. Multiple corrections. And then the next session would start and it would happen again.

When I added a note to the contacts file — *this is a conference room, not a person; when you see this name in meeting summaries, it refers to whoever was physically in the room* — it stopped immediately.

That's a small example, but it pointed at something larger: the AI had no way to know what I knew. Not because it wasn't capable — because it didn't have access to the context I carried in my head. Building that context into files wasn't just about convenience. It was about making the AI usable for my specific situation, rather than useful in some general way.

---

## What I Built, and Why

Over several months, the data layer grew from a preferences file into a small ecosystem:

**Preferences** — how I work, what I care about, how I want AI to communicate with me. Calibrates every response.

**Patterns** — how my specific tools behave, what the AI needs to know to use them reliably, workarounds for things that break. Without this, the AI would keep rediscovering edge cases I'd already encountered.

**Contacts** — my team, my peers, my manager, adjacent teams. Role, handle, context. The AI knows who people are without being told.

**Links** — the tools and spaces I navigate repeatedly. Project boards, communication channels, document folders. Saves lookup time and reduces errors.

**Memory** — things worth remembering across sessions that don't fit elsewhere. Decisions made, projects ongoing, context from past conversations.

Each file started small and grew through use. When something required re-explanation, I'd add it to the file so it would be there next time. Over months, the explanation overhead dropped close to zero.

---

## The Init Skill

The final piece was an init skill — a startup routine that loaded all of these files automatically at the beginning of every session.

Before the init skill, I had to remember to provide context. Sometimes I'd forget and the session would go sideways before I caught it. After, the AI always started calibrated. It knew my world before I said anything. I'd start with "what do I have going on today?" and it would know where to look.

That's the data layer. It's not glamorous. It's maintenance. But it's what makes everything else possible.

The session stops starting from zero. The AI stops being a general-purpose tool responding to prompts. It becomes something closer to a knowledgeable colleague — one who knows your team, understands your role, and has enough context to be genuinely useful from the first exchange.

---

*[← Home](../README.md) | [Evolution →](./02-evolution.md)*
