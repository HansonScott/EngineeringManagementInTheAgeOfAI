# Integrations: One Interface for All the Tools

*[← Data Layer](./01-data-layer.md) | [Home](../README.md) | [Next →](./03-skills.md)*

---

The tools are already there. Slack, Jira, Zoom, GitHub, Google Calendar, Gmail — every system
my job runs through exists and works. The problem isn't access. It's the weight of actually
using them the way good management requires.

Doing a 1:1 well means reading the notes from last time, scanning what that person has shipped
recently, checking whether anything notable came through in Slack, and thinking about what's
been happening in their life outside the task list. All of that information exists. Getting to
it means opening four systems, running searches in each one, holding the pieces in memory while
the next tab loads. The ideal amount of research is too much to do consistently. So most of the
time, some of it gets skipped.

That's the problem the integrations layer solves. Not convenience — completeness. Each system
is connected to a single conversational interface, so the full research load runs in the
background rather than manually in the foreground. Ask a question and get a synthesized answer
drawn from whatever sources are relevant. The research happens; it just doesn't require me to
conduct it.

What follows is what that looks like in practice — which systems connect, what each one
actually involved, and what becomes possible when they work together.

---

## Communication: Slack and Gmail

Slack is high volume. Across team channels, subgroup channels, peer manager channels, and the
broader engineering community, the message count on any given day makes manual review
impractical. Important threads get buried. Decisions surface in passing comments. Someone
shares something relevant in a channel I'm not actively watching. Email compounds it — a
separate stream of signal that accumulates independently and doesn't cross-reference anything
happening in Slack.

The difference shows up clearly with questions like "what's the latest on this project?" or
"who has my team been working with this week?" Answering either one well means scanning
relevant channels, following thread branches, checking email for parallel context, and
connecting it back to specific people and their roles. That's a ten-minute manual exercise on
a good day — and the second question is barely feasible manually at all. With the integration,
both are single questions. The answer comes back as a synthesis, not a pile of search results
to sift through.

What makes that possible is the data layer underneath. The links file carries the channel IDs
for every channel that matters — team, subgroup, peer managers, and others — so "my team
channel" or "the enablement subgroup" resolve to specific targets without disambiguation. The
contacts file carries Slack IDs for every person I work with, so a question about a specific
person runs against the right identifier rather than a fuzzy display name. The integration
doesn't just connect to Slack and Gmail — it connects to them with full awareness of my world,
which is what turns volume into signal.

---

## Google Docs

The documents that matter most to my EM work all live in Google Docs. Every direct report
has a 1:1 notes doc and a personal notes doc. The team meeting record is a shared doc updated
every week. Key reference documents — role expectations, career frameworks, project briefs —
live there too. Connecting to this layer meant the right context could load automatically
before any conversation that needed it, rather than being opened and scrolled manually each
time.

Getting the connection working was the starting point. Making it work the way I actually
needed took longer. Both reading and writing to Docs turned out to require a detailed
understanding of how the Docs API actually behaves, which differs from how it appears to
behave in a few important ways.

Heading styles don't apply when content is inserted. The API accepts the text and returns
success, but the document renders as a wall of unstyled paragraphs with no visual hierarchy.
Applying heading styles requires a separate batch update pass after content insertion,
targeting specific index ranges. Miss this step and the output is technically correct but
visually broken.

URL handling has the same shape: the API accepts both plain text and embedded hyperlinks and
confirms success either way. Plain text insertion renders as a raw URL string in the document.
Embedding a hyperlink requires a three-step sequence — delete the plain text, insert display
text, apply a link style to that range. Both paths look identical from the API's perspective.
Only the rendered document reveals the difference.

Date chips — Google's smart chip format for inline dates — don't come back as readable text
from the API. The chip renders correctly in the document but returns as an opaque object in
the API response. Extracting the underlying date value requires a workaround that isn't in
the standard documentation.

Each of these was discovered by producing wrong output and working backwards. They're all
captured in a dedicated Docs skill now, which means they don't have to be rediscovered. Any
session that touches a Google Doc goes through the skill; the patterns are baked in.

---

## Google Calendar

Calendar serves two roles in the stack. The first is scheduling — creating, reading, and
modifying events. The second is routing: when another skill needs to locate a Zoom meeting,
it starts with Calendar to identify the event and find the organizer. That routing function
makes Calendar foundational in a way that isn't obvious from its surface purpose.

The scheduling side has one rule that shapes every operation: calendar actions are
irreversible. An invite sent to the wrong people, at the wrong time, carries my name and lands
in someone's inbox. There's no recall. The right pattern — always look up the current state
first, surface the full details for review, wait for explicit approval before sending —
emerged from taking that seriously rather than discovering it the hard way.

The API has two behaviors worth knowing. Recurring event instances carry timestamp-suffixed
IDs that look different from the series ID. Modifying an instance by its specific ID affects
only that occurrence; the series stays intact. Getting this wrong modifies every future
occurrence rather than the one intended — a mistake that's immediately visible to everyone on
the invite.

Datetime formatting requires both a UTC offset in the ISO string and a separate timezone
field. Providing one without the other produces silent scheduling errors — the event creates
successfully but lands at the wrong time. Both fields are required; the API doesn't enforce
this, it just quietly gets it wrong.

---

## Google Drive, Sheets, and Slides

The remaining Google Workspace surfaces are connected but still maturing. Each has a working
integration; none has yet accumulated the depth of edge cases that Docs and Calendar have.

Drive is the file system everything else sits on. The one behavior that breaks standard
operations if missed: shared drives require a specific API flag that regular Drive calls don't
include by default. Without it, operations on shared content fail silently or return access
errors that look like permission problems rather than missing parameters. Word documents
require a different read path from native Google Docs — raw binary download and XML parsing
rather than the Docs API. Both are handled; the distinction just has to be detected before
choosing the path.

Sheets and Slides are functional integrations that haven't yet pushed into complexity. Sheets
supports tabular reads and writes — useful for reporting workflows and audit processes. Slides
handles presentation creation and editing; existing decks serve as format templates, providing
the style and layout context needed to produce output that matches established patterns. One
practical discovery: navigating slide output through the API to evaluate formatting is slow.
Taking a screenshot of the rendered slide and bringing it directly into the conversation turns
out to be significantly faster for formatting feedback — a feedback loop that the API path
alone doesn't provide efficiently. The patterns for both are straightforward so far and will
deepen from here.

---

## Jira

Jira is where work is structured and tracked — but the integration is only as useful as the
understanding of how the org uses it. Generic JQL queries return issues. Queries that
understand the project hierarchy, issue types, and classification conventions return work that
can be correctly interpreted and acted on.

The hierarchy matters in particular. Initiatives roll up to epics, epics to stories, and the
Dev Type field set at the initiative level flows down to determine whether child work is
capitalizable for financial reporting. Getting this wrong produces summaries and reports that
look accurate but aren't. That structural knowledge lives in the patterns file from the data
layer — the integration and the context work together. One without the other produces
plausible-looking output that misses what actually matters.

In practice, the Jira integration serves three distinct functions. Search: finding active
work, identifying what's in progress or blocked, scanning epics against their parent
initiatives. Posting: publishing weekly initiative update comments on behalf of the team,
drafted from real signals rather than from memory. And hygiene: surfacing issues that are
miscategorized, missing parents, or carrying the wrong Dev Type — all of which have
downstream consequences for financial reporting and CapEx classification. Monthly CapEx
reporting depends on the board being clean; issues without parents, work categorized as
"Other" instead of a defined type, or stories that have drifted from their initiative all
introduce errors into reporting that compound over time. The integration makes it possible
to run those hygiene checks systematically rather than catching problems manually during
the monthly review. Each function requires the same underlying connection but uses it
differently — the integration is a foundation, and the skills that sit on top of it determine
what it actually does.

---

## GitHub

GitHub is where delivery becomes visible. Pull requests, code reviews, merge history — the
actual output of engineering work, timestamped and attributable. For an EM, that signal is
useful in a way that Jira alone isn't: Jira captures what the team committed to; GitHub
captures what's actually shipping.

The integration runs through the command line interface rather than a web API, querying by
individual handle rather than at the team or organization level. That approach is deliberate.
Handle-level queries return activity that can be attributed to a specific person and
cross-referenced against everything else known about them — their open Jira stories, their
recent Slack messages, their 1:1 notes. The contacts file carries a GitHub handle for every
team member, which is what makes those parallel queries possible without a lookup step each
time.

In practice GitHub surfaces in several distinct ways. Recent PR activity gives a concrete
picture of what someone has been working on in the days before a conversation — a signal
that's harder to fabricate than a status update and more specific than a ticket title.
Contribution history surfaces effort that might not be visible in standups: review depth,
cross-team work, consistent output during a difficult period. And PR activity cross-referenced
against active project work validates whether reported progress reflects commits that are
actually happening. The plan and the evidence, in the same frame.

---

## Zoom: The Hard Case

Every meeting is a signal. What someone raised, what was decided, what tension surfaced, what
commitment was made out loud. Getting reliable access to that signal turned out to be the most
technically involved integration in the stack — not because Zoom is poorly designed, but
because the combination of how recording access works, where summaries live, and how AI
transcription behaves created a chain of problems that each required its own solution.

Recording access depends on who hosted the meeting. If the host is someone else, the direct
API path doesn't work. The solution is to use Google Calendar as a routing layer: find the
calendar event, identify the organizer's email, and use that to locate the right recording.
This works reliably, but it means every Zoom lookup involves at least two systems before it
reaches the meeting content.

Even with routing resolved, the most useful artifact — the AI-generated meeting summary —
doesn't come from the API. It lives in the Zoom Hub, a web portal without a clean API
surface. Accessing it requires browser automation: navigate to the Hub, load the specific
meeting page, extract the summary from the rendered page. Three steps, each with its own
failure mode, to get to what should be a single call.

Then there's transcript interpretation. Zoom's AI misreads names consistently enough that
the misreadings needed to be catalogued explicitly. The same name gets rendered differently
across summaries. Conference room hardware — where multiple in-person attendees speak from
a single device — shows up as one speaker in the transcript, which means attendee attribution
in any meeting with a room requires human clarification. Without knowing these patterns,
summaries assign observations and action items to the wrong people, or to rooms that aren't
people at all.

The Zoom skill now handles all of this: calendar routing, Hub navigation, name correction,
and conference room flagging. Any other skill that needs meeting context passes a meeting
name and date and gets back a resolved result. The complexity lives in one place.

---

## Claude Chrome Extension: When There Is No API

Not every tool exposes what's needed through an API. Some lock their most useful surfaces
behind web portals. Some have APIs that require access levels the setup doesn't have. Some
simply weren't designed for programmatic use. For these, the browser is the integration layer.

The Claude Chrome extension provides a set of tools for navigating to a URL, reading the
rendered page, executing JavaScript, and interacting with UI elements. Where a direct API
path doesn't exist, it fills the gap — and it turns out that gap covers more ground than
expected.

Zoom Hub is the clearest example. The AI-generated meeting summaries that make Zoom useful
as a signal source live in a web portal, not an API endpoint. The extension is what makes
them accessible to the rest of the stack. The quarterly SOX audit is another: the review
process requires navigating access management portals, pulling user lists from rendered pages,
and capturing evidence screenshots — all browser-bound regardless of how the work gets done.
Automating that navigation turns a multi-hour manual process into something that runs with a
single review checkpoint in the middle.

Browser automation carries a different quality bar than API access. It's more brittle — a
page layout change can break a navigation path in ways that an API version change wouldn't.
The approach accounts for this: navigation targets stable, predictable pages rather than
dynamically generated content, and failures surface explicitly rather than silently returning
wrong data. It's a less elegant integration than a clean API, and it's used specifically where
no cleaner path exists.

---

## The Unified Interface

None of what's described above is visible when the stack is working.

Preparing for a conversation with a team member means reading their notes, scanning their
recent activity across communication and project tools, and arriving with the full picture
assembled — not gathered manually in the minutes before. Recovering from a week away means
checking what moved across every relevant channel and system in parallel and getting a single
synthesis back: here's what happened, here's what needs attention. Reporting on team progress
means pulling signals from project trackers, communication threads, and contribution history
at once rather than assembling them by hand.

The switching is gone. The synthesis happens in the response.

That's the shift the integrations layer produces: not better access to individual tools, but
the ability to ask questions that cross tool boundaries. "What's been going on with this
project?" is not a Jira question or a Slack question or a GitHub question. It's a question.
The integrations layer is what makes it answerable. That access is what makes the deeper
leadership questions and role reflection possible.

---

*[← Data Layer](./01-data-layer.md) | [Home](../README.md) | [Custom Skills →](./03-skills.md)*
