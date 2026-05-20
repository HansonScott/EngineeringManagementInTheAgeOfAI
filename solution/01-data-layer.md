# The Data Layer

*[← Solution Overview](./00-overview.md) | [Home](../README.md) | [Next →](./02-integrations.md)*

---

The context problem isn't a question of keeping memory between sessions. Claude's memory has gotten genuinely good, and it does provide real project context. But what I needed was something different: structured, intentional awareness of my world — the specifics that never come up in prompts because I'm too busy using them to think to explain them.

Who's on my team and what they're carrying. How my org operates. What's in motion right now. What the norms are for the tools we use every day. That context doesn't emerge from conversations. It has to be built deliberately.

The data layer is how I built it: organized, topic-specific files that give Claude complete knowledge of my world, loaded automatically at the start of every session.

The files:

- **Profile** — who I am, what I value, and how I think
- **Preferences** — how Claude and I work together
- **Patterns** — tool conventions, quirks, and known gotchas
- **Contacts** — people, handles, roles, and relationship docs
- **Adjacent Teams** — peer teams, dependencies, and disbanded history
- **Links** — permanent assets, eliminating repeated searches
- **Team Process** — team agreements, cadence, and delivery norms
- **Current Influences** — what's active and in motion right now
- **File Infrastructure** — where this all lives

---

### Profile

This is the calibration document for every other conversation. Before Claude can give useful advice about my career, my team, or my role, it needs to know who I actually am: what I value, what I'm trying to build, and what kinds of framing would miss the mark entirely.

**Values and priorities** — what matters most in how I approach work and life. This isn't abstract; it's operational. It determines how career conversations get framed. "Maximize your visibility for the next promotion" lands very differently depending on what someone actually cares about.

**Career direction** — where I'm headed and, critically, where I'm not. Knowing both saves Claude from suggesting strategies that don't fit. Not every career question is about advancement.

**Technical background** — I came up as an engineer. I can follow technical depth and appreciate precision. This shapes how Claude calibrates explanations: no oversimplification, full detail when it's relevant.

**What energizes me** — the work that lights me up. Knowing this lets Claude connect tasks back to what's meaningful rather than treating all work as equivalent.

**What drains me** — patterns that create friction or anxiety, and the coping mechanisms I've built around them. If I'm over-engineering something, there's often a reason, and knowing it leads to a better response than "just simplify."

---

### Preferences

Preferences governs how Claude and I work together: communication norms, workflow defaults, judgment calls about when to pause and when to proceed. The distinction from Patterns matters — Patterns tells Claude how to work with my tools; Preferences tells Claude how to work with me.

The sections below grew organically from situations where Claude and I assumed differently. Each one exists because an autonomous decision needed alignment with my expectations. These are examples of how to direct Claude, not an exhaustive list — this document grows with my experience.

**Communication norms** — Claude can send messages. Without clear norms, it might fire off a Slack post because the content looks ready. But sending is irreversible and carries my name. Communication norms define the line: Claude always creates a draft; the act of sending is always mine. This applies even when the content seems obvious or was just reviewed.

**Writing style** — Claude has recognizable patterns: em dashes, certain sentence structures, hedging language. When content carries my name, those patterns undermine the authenticity of the communication. The writing style section tells Claude which habits to suppress and how I actually write.

**Proactive suggestions** — Claude knows things I don't always think to ask about: a simpler approach, a relevant skill, a reason to start a fresh session. Without guidance it either surfaces everything or nothing. This section defines what's worth surfacing and what isn't. The standard: suggest without starting work.

**Workflow defaults** — How I want Claude to move through work. Incremental steps over doing everything at once. Explain the why before acting on unfamiliar setups. Check existing state before assuming a clean slate. These aren't constraints — they're how I stay in control of work that touches real systems.

**Honesty and anti-sycophancy** — The most substantive section. AI has a natural pull toward agreement: softening a concern, framing a gap as "worth watching" when it warrants stronger language, changing a position when pushed back on without new information. This section names that risk explicitly. EM health assessments reflect data, not the mood of the session.

**Confirmation gates** — Claude has broad file access. Without clear rules, it might make structural changes to skill files that affect every future session, or modify things that were actually in use. Confirmation gates define the line: some files can be edited directly as routine maintenance; others always require a pause and explicit approval.

---

### Patterns

Patterns governs how Claude works with my tools. Where Preferences is about how Claude and I work together, Patterns is about the systems I work in: how they're structured, where they behave unexpectedly, and what org-specific conventions apply. Without it, Claude operates on generic assumptions — and those assumptions are frequently wrong.

Like Preferences, this file grew from friction. Each entry exists because a default behavior produced a wrong or incomplete result. Some sections stay here as reference; others grow complex enough to graduate into a custom skill, where the patterns are baked in and Claude follows them automatically rather than re-interpreting them each session. Google Docs is an example of this — it started as a patterns section and is now its own skill.

**Jira** — project structure, issue hierarchy, and how work maps to financial reporting. Jira at any company has its own conventions: which projects exist, how initiatives relate to epics and stories, what fields carry special meaning for capitalization reporting. Getting this wrong produces work breakdown suggestions that don't fit the actual structure, or financial categorizations that cause downstream reporting problems.

**Confluence** — how pages are organized and where the API falls short. Two recurring quirks: filenames in table cells auto-convert to hyperlinks, breaking formatted content; and pages that embed dynamic Jira content return those sections silently empty via API. Without this knowledge, Claude presents incomplete content as complete, or produces formatting that breaks on publish.

**Google Calendar** — event creation follows a two-step workflow: look up the current state first, then act. Every creation requires a conflict check, full details surfaced for review, and explicit approval before sending. Invites are treated the same as messages — irreversible. Recurring event instances carry timestamp-suffixed IDs; modifying one doesn't touch the series. Datetime formatting requires both a UTC offset and a separate timezone field — missing either causes silent scheduling errors.

**Google Drive** — shared drives require a specific API flag that standard Drive operations omit. Without it, operations on shared content fail silently or return access errors that look like permission problems. Word documents can't be read through the standard Docs or export APIs — they require raw binary download and XML parsing. Native Google Docs and Word files look similar in search results but require completely different handling.

**Google Docs** — three persistent gotchas, all producing silent failures. First: heading styles don't apply automatically when content is inserted — they require a separate batch update pass, and skipping it leaves the document as a wall of plain text. Second: URLs must be embedded as clickable hyperlinks, not inserted as plain text — the API operation succeeds either way, but plain text insertion renders as raw URLs in the document. Third: date chips (Google's smart chip format for inline dates) aren't returned as readable text by the Docs API — extracting the underlying date value requires a separate workaround. Docs operations have grown complex enough that they now live in a dedicated custom skill rather than this file.

**Google Sheets** — the lightest section currently. Sheets interactions have been straightforward enough that no major gotchas have required documentation yet. That will change as usage grows.

**Slack** — inline link syntax uses its own markdown format with literal angle brackets. Getting this wrong causes raw HTML entities to appear in messages instead of rendered hyperlinks. Small detail, visible and embarrassing result.

**Zoom** — transcript interpretation. Zoom's AI misreads names regularly, and conference room hardware shows up as a single speaker rather than multiple attendees. Without knowing this, meeting summaries assign action items to people who weren't there — or to conference rooms that aren't people at all. The Zoom conference room problem from [The Context Problem](../philosophy/04-the-context-problem.md) is the example that made this file necessary.

---

### Contacts

Contacts delivers two distinct benefits. The first is natural language context: when I say "my team," Claude knows exactly who that refers to. When I mention someone by name, Claude already knows their role, their relationship to me, and how they fit into the org. No disambiguation, no clarification needed — the words map directly to the right people.

The second is efficiency: when I ask Claude to find out what someone has been up to this week, it already has their Slack ID, their GitHub handle, and their Jira ID. It can query all three systems immediately, without a lookup step. The contacts file is what makes cross-system operations feel seamless rather than manual — the identifiers are already there, organized and ready.

Together, these two benefits mean that conversations about people can move at the speed of conversation rather than the speed of directory searches.

Every person in the file carries a consistent set of fields:

**Name and pronouns** — the basics, but important for correct addressing in any drafted communication.

**Email, Slack ID, GitHub handle, Jira ID** — the handles that connect a person to each system. Slack IDs rather than display names, because display names can be ambiguous or change. GitHub handles for connecting PR activity back to the right person. Jira IDs for accurate assignment and filtering. Each field is what makes cross-system references resolve correctly.

**Role** — a defined taxonomy that tells Claude the relationship, not just the title. The distinction between a direct report, a peer EM, a director-level peer, and a manager shapes how communication gets framed in every context. The role field also carries a `departed` value — preventing Claude from suggesting people who've left as contacts, owners, or approvers.

**Location** — affects availability assumptions, timezone considerations, and in-office context. Relevant any time scheduling or in-person coordination comes up.

**Personal links** — each contact can carry links to any documents relevant to that relationship. In my setup, this means a 1:1 notes doc (the living record of our meetings: what was discussed, what was committed to, what's in progress) and a personal notes doc (human context: career goals, family details, things shared in conversation worth remembering). These links are what custom skills use to pull the right documents directly — no Drive search required. Any doc that belongs to a specific person lives here, so skills can reference it by name rather than hunting for it each time.

The contacts file is a roster in format, but a relationship map in function. The handles make people findable across systems. The role taxonomy shapes how communication lands. The personal links are what make every 1:1 a continuation rather than a fresh start.

---

### Adjacent Teams

Contacts covers the people I work with. Adjacent Teams covers the org around me — the teams I partner with, depend on, and exist alongside. Without it, cross-team questions land without context: Claude knows the people but not the organizational relationships, the active initiatives, or the history that shapes how those relationships work.

The file has two distinct layers. The first is active teams: my own team in its broader context, the peer teams within my org group, and the adjacent teams outside it. Each entry includes the team's mission, its current members, and — critically — its relationship to my team. Not just "here's who they are," but "here's how our work intersects and what the active connection points are."

The second layer is disbanded teams, retained specifically for historical reference translation. The org I work in went through a significant restructuring, and old Jira tickets, Confluence pages, and architecture docs still reference team names that no longer exist. Without this layer, Claude would encounter those references and have no way to map them to current owners. The disbanded entries are a translation table: when a doc says this team owned something, here's who owns it now.

---

### Links

Claude can search for assets, but after finding myself looking up the team meeting agenda doc multiple times across sessions in the same day — same doc, same search, same friction — a lookup table became painfully necessary. The problem wasn't that Claude couldn't find things. It was that making it search for the same assets at the start of every session was wasted motion, and occasionally it found the wrong version of something entirely.

Links is the fix: a reference file for every asset that comes up repeatedly. Project boards, Confluence spaces and key pages, Drive folder IDs (shared drives require them), frequently used Docs and Sheets, recurring calendar event IDs, GitHub team links, and Slack channels with their IDs. Each category covers assets that would otherwise require a search that always returns the same answer.

The file grows on a simple principle: any permanent asset that comes up repeatedly belongs here. It doesn't need to be exhaustive upfront — it fills in naturally through use.

---

### Team Process

Every team operates differently, and Claude has no idea how mine works without being told. Left to defaults, it fills the gap with assumptions — usually textbook scrum, usually by-the-book agile. Those assumptions quietly shape every process-related response: what healthy delivery looks like, what the EM's role as product and project leader involves, what belongs in a sprint update, what counts as scope creep versus legitimate change.

Team Process is where those assumptions get replaced with reality. Unlike Preferences, which is about how I work, this file is about how the team works — agreements made collectively, not my decisions alone. It doesn't need to be a comprehensive methodology doc; it just needs to capture the decisions that would surprise someone operating from defaults.

The kinds of things that might live here: whether the team runs scrum, kanban, or something in between; sprint length and what happens at the boundaries; how meetings are structured and what they're for; how tickets get created and who owns that process; delivery language and what "done" actually means; and how AI-assisted delivery factors into capacity and quality expectations. Many of the assets that support these processes — meeting notes docs, sprint tracking sheets, planning boards — are also catalogued in Links, so Claude can reference both the process and the artifacts that support it in the same session.

One example of why this matters: early on, Claude assumed standard scrum operations and framed process questions accordingly. Once I documented that the team runs a hybrid model with specific ownership expectations for me as both EM and product lead, the framing shifted entirely. The same questions started landing in the right context rather than the wrong one.

---

### Current Influences

Every other file in the data layer describes things that are relatively stable: who I am, how I work, who's on my team, how we operate. Current Influences is different. It's the live layer — the active forces shaping how I show up as a manager right now.

Without it, Claude can give advice that's technically correct but contextually wrong. Coaching someone on career growth without acknowledging company-wide uncertainty about AI's impact on roles misses a huge piece of their reality. Framing a team communication as "things will settle down" during a reorg that's explicitly still fluid sends the wrong signal. The context that makes management advice land well isn't just who people are — it's what they're living through right now.

Each entry in the file covers a specific force in motion: what it is, when it started and when to revisit it, who it affects, and how it should shape coaching and communication decisions. The recheck date is what keeps the file honest — Current Influences isn't a permanent record, it's a rolling window. Entries expire when the situation resolves or changes enough to need rewriting. Without that discipline, the file drifts from live context into stale history.

The kinds of things that live here: org changes and reorgs still in motion, company-wide policy shifts with real consequences for how people are feeling, active uncertainty that would change how I'd frame a conversation if Claude knew about it, and team member situations viewed holistically — not just the event itself, but how it ripples outward into sprint capacity, coaching priorities, and the dynamics of the team around it.

---

### File Infrastructure

There's an important technical detail underneath all of these files: where they live, and why that decision matters.

The data layer files are stored in a dedicated directory at the user's home level — not inside any project folder, and not alongside Claude's own internal files. That separation was intentional and required some deliberate working-through. Claude Desktop has its own behaviors around project memory, session context, and sensitive file detection. Placing custom data files in the wrong location means they either get treated as project-specific (and stop loading when you're working outside that project) or they interact unexpectedly with Claude's own memory infrastructure.

The home-level directory solves both problems. Files stored there load consistently across every session and every project, because they're not scoped to any particular working context. They're always accessible, always loaded, always in scope — regardless of what Claude Desktop thinks the current project is.

This also makes the relationship between these files and Claude's own memory explicit rather than accidental. Claude maintains its own session memory and project context alongside these structured files — and that's fine. They serve different purposes: Claude's memory captures what emerges from conversations; the data layer files hold what was deliberately built. Both layers are in the room at the same time, complementing each other rather than competing.

---

## Session Initialization

The data layer doesn't load automatically — it loads because I configured it to. CLAUDE.md, Claude's global config file, contains a rule I've set: run `/start` before responding to any first message, no exceptions. That's a deliberate choice, not a default. My work as an EM can go in any direction from the first message, and I need the full context available every time. Others might configure this differently — triggering it manually, or only for certain session types. For me, every session needs it.

The start skill loads all of the data layer files simultaneously in a single parallel batch. It also pulls the current date and time for temporal awareness, and discovers what memory files are available. Memory files are listed but not bulk-loaded — surfaced as accessible and pulled on demand rather than flooding the context window upfront.

When I start a new session, Claude is ready to meet me with knowledge of my world.

---

## A Practice, Not a Project

None of this existed at the start. I didn't design the data layer upfront and then build it. I built it backwards, one file at a time, in response to friction.

The pattern was always the same: something required re-explanation. I stopped and wrote it down. It never needed re-explaining again.

Contacts started as a list of a few people and now covers my full team, my peer group, and the adjacent partners I work with regularly. Patterns started with two Zoom quirks and now holds conventions for five tools. Current Influences was created most recently — I realized there was a cloud hanging over everything: active forces shaping every conversation and coaching moment, and Claude had no awareness of any of it.

The overhead doesn't drop all at once. It drops incrementally, every time something gets written down that used to live only in my head. After a few months, the reconstruction tax from [The Context Problem](../philosophy/04-the-context-problem.md) had effectively reached zero. Not because I found a smarter way to explain my context, but because I stopped needing to.

That's the insight the data layer delivers: building it isn't a project with a finish line. It's a practice with a compounding return.

---

*[← Solution Overview](./00-overview.md) | [Home](../README.md) | [Integrations →](./02-integrations.md)*
