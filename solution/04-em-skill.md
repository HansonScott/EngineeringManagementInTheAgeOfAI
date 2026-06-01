# The EM Skill: A Strategic Partner, Not a Task Runner

*[← Custom Skills](./03-skills.md) | [Home](../README.md)*

---

The other skills solve discrete problems. This one is different.

Early in my Claude experimentation, I was using AI to do management tasks more efficiently. Schedule prep, note capture, status updates. The efficiency was real. But I kept running into the same uncomfortable question: *efficient at what, exactly?*

The problem wasn't that I was doing things wrong. It was that I had no systematic way to see the full scope of what the EM role actually requires, and therefore no way to know what I was missing. Any individual session looked fine. The aggregate picture was invisible.

The EM Skill was built to make that picture visible. It's not a workflow. It's a system for running the EM job itself.

At its core: 21 workflows mapped across People, Process, and Product, each with defined healthy states, observable gap signals, and a companion file that persists context between sessions. A health registry that surfaces where each workflow stands at any moment. A signal taxonomy that governs what's worth logging after any meeting. A session tracker that accumulates those observations into a navigable history. A daily digest that orients the start of every workday. And a monthly strategic pulse that gathers live data before asking whether I'm leading at the right altitude, not just executing at the right pace.

The sections below walk through how each piece works.

---

## The 21 Workflows

The EM Skill starts from the basic question: what does the Engineering Manager role actually require? I started with the written job description, but then expanded it through iterative reflection into the full scope: everything an EM is accountable for, confirming that I'm doing the job well.

The answer is 21 workflows across three pillars.

Each workflow is a structured file, not a checklist. It contains a strategic framing (why this workflow exists and what the failure mode looks like), followed by observable criteria for what healthy looks like, specific signals that indicate drift, and clear criteria for moving between health states. Each one also has a companion state file that persists the current snapshot between sessions: where each person or area stands, what the last assessment found, and what changed since then.

**People** is the core of the role. Eight workflows cover the full arc of working with people: bringing on great people, growing careers, managing performance, coaching and caring through 1:1s, engaging and inspiring, building great teams, handling exits, and building resilience against burnout.

**Process** is the operational layer. Ten workflows cover how work gets done: driving agile delivery, continuously improving, reducing friction, making decisions, navigating ambiguity, broadcasting status, leading through change, managing team capacity, collaborating with other teams, and managing costs.

**Product** is the quality and direction layer. Three workflows cover what the team builds and how it holds up: building products in partnership with PM, owning the -ilities (reliability, scalability, observability, security), and ensuring compliance.

Walking into any deep dive, I'm not starting from scratch. The state file carries what was learned last time. The question isn't "where are things?" It's "what's changed since I last looked?"

## The Deep Dive

The most important thing the skill does, and the thing that separates it from a checklist, is how it actually evaluates a workflow.

Every deep dive opens with an intent reminder: two sentences on what the workflow is fundamentally about and what the failure mode looks like. Not as background, but as a frame. The right mindset before looking at any data matters.

Before a single question is asked, the skill reads everything relevant in parallel: the health registry for where this workflow last stood and how long it's been (which sets the lookback window for everything that follows), the companion state file from the last session, open and recently completed todo items tagged to this workflow, and 1:1 notes for every relevant direct report pulled directly from Google Docs. For delivery and process workflows, Jira sprint data and GitHub team activity come in alongside the people data. Calendar history surfaces where time has actually been going. Jellyfish allocation data fills in capacity and workload signals that conversations alone might miss. For reliability workflows, PagerDuty incident history and on-call load. Slack fills in the texture that structured data misses: friction named in passing, team mood, things that came up but never made it into a ticket. The signal tracker is cross-referenced against the taxonomy of what this specific workflow cares about. The data layer (contacts, patterns, preferences, memory) is already in context before any of it is read. The evaluation starts from evidence, not from where I think things stand.

The evaluation itself is structured around two questions: what do the healthy state criteria say, and what do the gap signals show? The rigor isn't just in the questions. It's in how they're answered. When a healthy state criterion says "can name X" or "can describe Y," the skill doesn't accept a self-assessment. It asks directly: *name one. Go.* If a concrete example doesn't come on the spot, that's treated as a gap, not a green. Absence of signals gets the same treatment: a workflow area that hasn't appeared in any meeting notes or tracker entries in weeks isn't automatically fine. It's a candidate for closer attention.

The output is a three-part summary: what looks healthy, what's unclear or missing, and what's clearly a gap. Each gap produces a path forward, handled in-session or added to the task list with a workflow tag so it doesn't disappear between sessions.

If health is non-green, the skill surfaces the explicit return-to-green criteria: what specifically needs to change, by when, and what concrete next steps would move the needle. A yellow status with no attached action items is considered incomplete. The conversation always produces at least one trackable thing.

At the end of every deep dive, the registry and state file are updated: health status, last checked date, next due date, and a dated entry summarizing what was found. The next deep dive starts from that summary, not from scratch.

## The Signal Taxonomy

Gathering all that data gets overwhelming quickly. Finding what actually matters among the volume requires a filter, and building that filter is what the Signal Taxonomy does.

A signal is a specific, named observation about a person, a pattern, or a situation: someone expressing interest in a promotion, a blocker that's appeared in three consecutive standups, a scope change that shifts team priority. A meeting summary is everything else: topics covered, discussions had, updates exchanged. Summaries tell me what happened. Signals tell me what to watch.

The taxonomy organizes signals into three categories that map directly to the workflow pillars. **People signals** cover career and growth, coaching moments, wellbeing, and team dynamics. **Process signals** cover delivery health, blockers, process friction, and decisions made or deferred. **Product signals** cover priority and scope changes, quality and reliability concerns, and stakeholder dynamics.

After any meeting, the question isn't "what should I write down?" It's "which signal categories fired?" The taxonomy guides the filter: a career conversation that surfaced promotion interest is a People/Career signal worth capturing; a blocker mentioned for the third standup in a row is a Process/Delivery signal. Both get logged with a specific person and a specific observation. A tracker entry that just notes "discussed sprint progress and retro items" adds nothing. The signal version names who said what and why it matters. If nothing in a meeting touched any of the signal categories, the entry is short. That's fine. The taxonomy also governs how signals get used downstream: when a deep dive runs, the skill cross-references every tracker entry against the taxonomy to determine which observations are relevant to the workflow being evaluated, filtering noise before any assessment begins, not during it.

Over time, the tracker becomes a navigable record: who's growing and who's coasting, what friction keeps surfacing, which decisions are being deferred. The signal taxonomy is what makes that accumulation useful rather than just large.

## The Session Tracker

Every session leaves a record. After any work using the skill (a deep dive, a pulse, a workflow review), the EM Skill hands off to a dedicated `/track` skill, which handles the structured log entry for both regular and pulse session formats. The entry captures what was worked on, which workflows and competencies were touched, any wins worth capturing, and any follow-up items generated. Pulse sessions add a second layer: anti-pattern assessments across People, Process, and Product, and a pillar balance count for the last 30 days. The EM Skill never writes to the tracker directly. Logging always goes through `/track`, which owns the format and enforces consistency across every session.

The tracker isn't just a log. It's a data source for the system itself. The routing check reads it at the start of every session to determine days since the last pulse and catch any outstanding follow-ups from prior sessions. Deep dives cross-reference it against the signal taxonomy to surface relevant observations since the last assessment. The pulse reads it to set context before asking the six strategic questions.

Over time, the tracker becomes a signal in its own right. A tracker showing ten consecutive Process sessions and no People sessions is a pattern worth naming. A follow-up item that's appeared in three consecutive entries without resolution is worth flagging. The accumulation tells a story that any single session can't.

## The Health Registry

Every workflow has a health state (green, yellow, or flagged), maintained in a central registry alongside two other pieces of information: when it was last evaluated, and when it's next due.

Cadences vary by workflow type. Some run weekly: delivery health and 1:1 coverage move fast enough that a week of drift is worth catching. Others run monthly or quarterly, areas where change is slower and a deeper look every 30 or 90 days is the right rhythm.

The registry is what makes the whole system auditable. At any point, I can open it and see the full picture: which workflows are green, which have slipped to yellow, which haven't been touched in longer than their cadence allows. The health notes on non-green workflows carry a one-liner on what's driving the status. Not just a color, but a reason.

The registry gets updated in two ways. Every deep dive closes by writing back to it: health, last checked date, next due date, and a health note if the status is non-green. The monthly strategic pulse does a lighter pass across all 21 workflows at once, updating the cadence dates and flagging any that picked up a signal during the pulse window. Everything else in the system reads from it: the daily digest surfaces what's overdue or non-green each morning, and every deep dive opens by checking it to set the lookback window for the data pull.

## The Strategic Pulse

The deep dive evaluates one workflow at a time. The strategic pulse zooms out and looks at all of them, not with workflow-level depth, but with the altitude needed to ask whether the role is being led well, not just executed.

The pulse runs monthly. The six structured questions it asks (altitude, people, anti-patterns, strategic intent, AI era, and wins) were drawn from the written job description and formal expectations for the EM role, then expanded through iterative reflection over time into the form they hold now. They're not generic management questions. They're grounded in what good looks like for this specific role, at this specific company.

Before any question is asked, the skill runs the same comprehensive data pull described in the deep dive section (Calendar, Jira, GitHub, Slack, Zoom, and the data layer), but across the full 30-day window rather than a single workflow's cadence. Everything is gathered and summarized before the conversation begins.

The analysis is where the real value is. Each question isn't a prompt for self-reflection. It's an assessment the skill delivers first, grounded in the data it just gathered, and the conversation is a reaction to that read. The altitude question doesn't ask "where do you think you've been spending time?" It shows the actual breakdown from calendar and GitHub and asks whether that matches where the time should be going. The people question surfaces who was met with, how often, and what patterns showed up in the Zoom summaries and 1:1 notes before asking whether anyone is quietly struggling. The anti-pattern scan runs the formal failure modes from the Manager Expectations doc against real signals from Jira, GitHub, and Slack, not self-report. The skill reaches conclusions and names them. The job is to react, confirm, or push back.

After the six questions, the pulse does a lightweight pass across all 21 workflows in the registry, not a deep dive on any of them, but enough to confirm greens, check yellows for progress, and flag anything that picked up a signal during the pulse window. Health states and cadence dates are updated for all 21 before the session closes.

The pulse doesn't replace the deep dives. It holds the larger frame that makes them add up to something.

## The Daily Digest

The deep dives and the pulse operate on cadences: weekly, monthly, quarterly. The daily digest operates on a different rhythm entirely, every morning, before the first meeting.

Where the other components evaluate and assess, the digest orients. It's not asking whether something is healthy or what needs to change. It's surfacing what the day looks like and what needs attention before it starts. The design target is two to three minutes, not a full session.

What makes it more than a calendar view is what's layered underneath. The digest opens with today's meetings, flagged by type and labeled by timing, with an embedded offer to run 1:1 prep for any direct report appearing on the schedule. It surfaces high-priority and overdue todos alongside recurring responsibilities from a separate cadence file, so nothing slips through the gap between the task list and the calendar. Workflow health from the registry is present too, not as a full assessment but as a lightweight signal: any non-green workflows, anything overdue, and any area that's gone quiet long enough relative to its cadence to be worth noticing.

Beyond the operational layer, the digest surfaces growth tracks: open items from the learning curriculum, a flag if a presentation is coming up this week, and on Thursdays a specific prompt for the weekly recognition shoutout. It also pulls sports headlines tailored to which teams each team member follows, a small thing that adds up over time in terms of being genuinely present in workplace relationships.

It closes with one question: *anything specific you want to work on today?* If yes, it routes directly to whatever workflow is relevant. If not, the orientation is done.

The daily digest is where all the other components become visible in the flow of an ordinary workday, not as a system to maintain, but as context that's already there when it's needed.

## How It Routes

Every `/em` invocation starts the same way: two parallel reads before anything else happens. The tracker is checked for days since the last strategic pulse and whether this is a first-ever session. The health registry is checked for non-green workflows and overdue cadence dates. Those two reads determine what happens next.

Explicit commands skip the routing entirely. `/em daily` goes straight to the digest. `/em pulse` and `/em workflow [N]` route directly to their respective components, but with one additional check first: whether the reasoning effort is set high enough. Deep dives and pulse sessions benefit from deeper reasoning, and the skill surfaces that explicitly before loading either one, giving the option to adjust before the session begins.

Morning sessions, before 10 AM, route automatically to the daily digest without prompting. A first-ever session routes to a welcome flow that explains the system and offers to run an initial pulse to set a baseline.

If the pulse is overdue, 30 or more days since the last one, the skill flags it before presenting anything else: how many days it's been, and a choice of whether to run it now or proceed to the menu. The cadence doesn't enforce itself, but it doesn't go unnoticed either.

Otherwise, the session opens with a brief status read, days since the last pulse, any non-green or overdue workflows, any outstanding follow-ups from prior sessions, and routes to the EM menu.

Most sessions close with a `/track` entry, but the tracker isn't limited to formal EM sessions. When the daily digest surfaces something worth capturing, or a conversation produces a signal worth logging outside of a scheduled workflow review, `/track` can be invoked directly. The system is built to accumulate, not just to review on a schedule.

---

## The Bigger Idea

The question that opened this essay (*am I doing the things that actually matter?*) has always been worth asking. What's new is that it's now answerable.

The EM Skill doesn't ask how things are going. It already knows: how many days since the last structured people review, which workflows have gone quiet, who hasn't had a meaningful career conversation in 60 days, whether time allocation for the last 30 days matches the priorities that actually matter. The pulse doesn't ask for reflection. It shows a breakdown from real data and asks whether I agree.

That's only possible because of the full stack beneath it. But that's also the point: the stack was built so that this layer could exist. Every integration, every context file, every skill below this one was building toward a system that could hold the EM role accountable to itself, not just execute within it.

That question always had an answer. Now it has evidence.

---

*[← Custom Skills](./03-skills.md) | [Home](../README.md)*
