# Prompt & Solder for Claude

[Prompt & Solder](https://promptandsolder.co.uk/) is a sourced catalogue of about 1,700 real projects where people used Claude on their own hardware and software: jailbroken Kindles, debloated smart TVs, printers given new drivers, bricked gadgets revived, abandoned apps rebuilt, and the times it went badly wrong. Every build links to where it was shared.

This plugin lets Claude search that collection while it helps you. Ask about your device or idea and Claude finds what people have already done, checks the sources, says what worked and what didn't, and helps you plan your own project.

## What's included

- **Connector** (`.mcp.json`): the Prompt & Solder MCP server at `https://promptandsolder.co.uk/mcp`, with four read-only tools: `search_builds`, `get_builds`, `collection_overview` and `recent_builds`. No sign-in.
- **Skill** (`skills/prompt-and-solder`): teaches Claude to search with good keywords, check each build really fits, cite the build pages and sources, flag failures and unverified claims, and keep its own suggestions separate from what the builds document. If the connector isn't available, the skill reads the same data from the public search API at `https://promptandsolder.co.uk/api/search`.

## Try asking

- "Using Prompt & Solder, what have people done with an old Kindle?"
- "My printer has no driver for macOS. What have people tried?"
- "Which smart TV debloats went wrong, and why?"

## What it sends and fetches

The plugin runs no local code. When Claude uses it, the only data sent is the search words and build ids Claude chooses, to `promptandsolder.co.uk` (the connector at `/mcp`, or the search API at `/api/search`). Nothing is written or changed anywhere; every tool is read-only and returns public information that is already on the website.

## Privacy

The server doesn't store search words or tie requests to people. To stop overload, each request's address is turned into a salted one-way hash that changes daily and is used only to count requests per minute and deleted shortly afterwards. The web host may keep standard access logs. Full policy: https://promptandsolder.co.uk/privacy/

## About

Prompt & Solder is an independent community project, not affiliated with Anthropic. Builds are what people reported online; check the sources, back up first, and only modify hardware you own.

Setup without the plugin, and the public API: https://promptandsolder.co.uk/claude/
