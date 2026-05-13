# Integrations: One Interface for All the Tools

*[← Data Layer](./01-data-layer.md) | [Home](../README.md) | [Next →](./03-skills.md)*

---

> *This document is in progress. It will cover: connecting Slack, Jira, Zoom, and Google Workspace to a single conversational interface, what the wrappers actually solved (and what they didn't), and lessons from building reliable integrations.*

**What this covers:** The principle of using AI as a hub rather than adding another tool. Each integration required custom work — authentication models vary, APIs have quirks, failure modes are different. Zoom in particular required significant wrapper work because of how meeting ownership affects recording access. The result: ask a single question in plain language and get synthesized answers drawn from all the relevant sources.

**What success looks like:** You stop context-switching between tools to answer a single question. "What's been going on with the project this week?" returns a synthesis from your project tracker, your communication platform, and your meeting summaries — without manually checking each one.

---

*[← Data Layer](./01-data-layer.md) | [Home](../README.md) | [Custom Skills →](./03-skills.md)*
