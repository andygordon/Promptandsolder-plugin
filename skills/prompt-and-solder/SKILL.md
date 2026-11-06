---
name: prompt-and-solder
description: Find real, sourced examples of what people have built, fixed, repurposed, debloated, jailbroken or reverse engineered with Claude, from the Prompt & Solder collection (promptandsolder.co.uk), and turn them into a plan. Use when the user wants to fix, hack, revive or repurpose a device or piece of software (old Kindle, smart TV ads, printer with no driver, bricked gadget, ESP32 project, abandoned app), asks what people have done with Claude for something, or mentions Prompt & Solder.
---

# Prompt & Solder

Prompt & Solder is a catalogue of about 1,700 real projects where people used Claude on their own hardware and software, failures included. Every build links to its sources. Use it to show the user what has actually been done before suggesting how they could do it.

## Getting the data

Use the first of these that works:

1. **The Prompt & Solder connector.** If the tools `search_builds`, `get_builds`, `collection_overview` and `recent_builds` are available, use them. They are the most reliable route.
2. **The public search API**, read with web fetch. All plain GET, JSON out:
   - Search: `https://promptandsolder.co.uk/api/search?q=<keywords>&limit=8`
     Optional: `&topic=<topic>`, `&outcome=Worked|Partly|Failed|Unverified` (Failed = horror stories), `&proof_only=1`
   - Full details for up to 5 builds: `https://promptandsolder.co.uk/api/search?id=<id>,<id>`
   - Topics, outcomes and counts: `https://promptandsolder.co.uk/api/search?overview=1`
   - Newest builds: `https://promptandsolder.co.uk/api/search?recent=10`
3. If neither works (for example web fetch refuses the address), tell the user in one line and suggest they add the connector at https://promptandsolder.co.uk/claude/ or paste a search link from that page. Do not answer from memory as if it came from the collection.

## Searching well

- Search with keywords, not sentences: the device, brand, problem or technique ("kindle jailbreak", "printer driver mac", "android tv launcher", "slow laptop"). Leave out words about who it's for.
- Run two or three searches with different wordings when the first is thin, including the broader category ("e-reader", "smart tv") and the outcome filter `Failed` when risks matter.
- Results are keyword matches, so check each one really fits before using it. Then fetch full details (`get_builds` or `?id=`) for the two to four best fits.

## Answering

- Ground every statement about what people did in the results. Never invent builds, people, numbers, results or links.
- Link each build you rely on with its `url` (a promptandsolder.co.uk page). Mention the original sources when it helps.
- Say plainly when a build only partly worked, failed, is unverified (`independently_checked: false`), or is only a claim (`proof: "Claim only"`). Prefer builds with `proof: "Proof shown"`.
- Keep roles straight: a source's author, Reddit poster, Hacker News submitter or repository account is not automatically the maker. Only name a creator when the `creators` field says so.
- Then help with the user's own project: a short numbered plan, clearly labelled as your suggestions, separate from what the builds document.
- Encourage working only on hardware they own, backing up first, and say where there's a real risk of bricking or losing a warranty. Don't help with getting into devices or accounts they don't own, piracy, or getting round paid subscriptions.
- If nothing in the collection fits, say so, then give the nearest builds or general ideas.
- Keep it concise unless the user wants more.

## Sharing back

If the user has built something with Claude, suggest they submit it at https://promptandsolder.co.uk/submit/ so the next person can start further along.
