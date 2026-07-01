---
name: linkedin-personal-brand
description: Build Mido's LinkedIn personal brand around Business Process Re-engineering (BPR), AI, automation, and digital transformation. Use this skill whenever Mido asks to research LinkedIn/industry trends in BPR-AI-automation-transformation, draft a weekly LinkedIn article, draft daily LinkedIn posts, review/approve pending LinkedIn drafts, or publish an approved post/article to LinkedIn. Trigger eagerly for phrases like "LinkedIn post", "LinkedIn article", "weekly article", "daily post", "post this on LinkedIn", "what's trending in BPR/transformation", or "publish to LinkedIn", even if phrased casually. Always draft content first and get explicit approval before calling any publish tool.
---

# LinkedIn Personal Brand Builder

Builds and runs Mido's personal-branding content engine on LinkedIn, centered on Business Process Re-engineering (BPR), AI, automation, and digital transformation — the themes that map to his GCC job search positioning (IBM BAW delivery + Lean Six Sigma Black Belt + CRISC).

## Workflow overview

1. **Surface trends** — live web search for what's currently moving in BPR / AI / automation / transformation (LinkedIn discourse, industry news, thought-leader posts).
2. **Draft weekly article** — one interactive/long-form LinkedIn article per week, grounded in trend research.
3. **Draft daily posts** — one short LinkedIn post per day. Mix of two angles:
   - **POV/hot-take** days: Mido's own opinion or contrarian take on a BPR-AI-transformation topic.
   - **News-recap** days: a recent development + his commentary.
   Alternate or ask Mido which angle he wants for a given day if unclear.
4. **Present for review** — ALWAYS show drafts in the chat conversation for Mido's approval. Never publish without explicit sign-off. No file is needed — chat approval is the review step.
5. **Publish via Composio** — once Mido approves a specific draft (word like "approved", "publish it", "go ahead"), use the Composio LinkedIn tool to post it. Only publish the exact approved text, or the text as amended by Mido's final edits.

## Step 1: Surfacing trends

Use `web_search` (and `web_fetch` for promising articles) each time — do not rely on memorized/stale knowledge of "trends." Search terms to rotate through:
- "business process re-engineering AI trends"
- "agentic automation banking transformation"
- "AI transformation leadership LinkedIn"
- "process mining automation 2026"
- "digital transformation GCC banking"

Scale search depth to the ask: 2-3 searches for a daily post, 5-8 for a weekly article research pass. Prioritize sources from the last 1-4 weeks. Do not quote sources beyond a fragment — always paraphrase per standard citation rules (this is content Mido will publish under his own name, so it must be original wording throughout, not just short-quote-compliant).

Weave in Mido's established positioning where natural (not every time): SAIB Head of BPR, 24+ years in Egyptian/Gulf banking transformation, CBAP/Lean Six Sigma Black Belt/CRISC, IBM BAW delivery experience — but only when it fits the specific post, don't force it.

## Step 2: Weekly interactive article

- Cadence: one per week (ask which day if not specified, default Monday research → Wednesday draft is a reasonable rhythm, but follow Mido's stated cadence if given).
- Length: ~600-1000 words, structured with subheadings, suited to LinkedIn's article format.
- "Interactive" = include a clear discussion hook — a poll-style question, a "which side are you on" framing, or an explicit call for comments — near the top or the close.
- Angle: connects a live industry trend to practical BPR/transformation implications, ideally with a real-world banking/enterprise framing (without disclosing anything confidential from SAIB — see Confidentiality note below).
- Present the full draft in chat with a suggested title, then wait for approval or edit requests.

## Step 3: Daily posts

- Length: 100-250 words, native LinkedIn post style — short paragraphs/line breaks, no heavy markdown (LinkedIn doesn't render markdown).
- One clear idea per post. End with a light engagement prompt (a question, an invite to share experience) rather than a generic CTA.
- Rotate POV and news-recap angles across the week; ask Mido once at the start of a batch if he wants a specific split (e.g. 2 POV / 3 news this week).
- Present drafts in chat, one at a time or as a batch (ask Mido's preference if doing multiple days at once), each clearly labeled with the day and angle.

## Step 4: Review gate (mandatory)

- Never call the Composio LinkedIn publish tool until Mido has given explicit approval on that specific piece of content in the conversation.
- If Mido asks for edits, revise and re-present — do not auto-publish the revised version either.
- Treat silence or a vague "looks good" as approval only if it clearly follows a specific draft just shown; if ambiguous, ask which draft/version he's approving.

## Step 5: Publishing via Composio

Use `tool_search` with a query like "linkedin post composio" or "composio linkedin" to load the actual Composio LinkedIn publish tool — its exact name and parameters aren't known in advance and must be discovered via `tool_search` (per the deferred-tools system). Steps:

1. `tool_search(query="linkedin composio post")` to find and load the relevant tool.
2. If no LinkedIn-capable Composio tool is connected, use `search_mcp_registry` / `suggest_connectors` to help Mido connect it — do not fall back to a different platform.
3. Call the tool with exactly the approved text (article or post). For articles, check whether the tool supports LinkedIn's long-form article format vs. a standard post, and flag to Mido if only standard posts are supported so he knows the article may need manual formatting on LinkedIn's side.
4. Confirm success back to Mido with a short summary (don't dump raw API output).

## Confidentiality note

Mido's SAIB work (Contracts Initiation Process, BRDs, Market Pulse Reports, internal metrics) is confidential and must never appear in LinkedIn content — draw on his general expertise/credentials only, never internal SAIB specifics, data, or documents.

## Style notes

- Voice: senior practitioner, direct, not overly corporate/buzzword-heavy — avoid the "humble-brag hustle" LinkedIn cliché tone (Mido has explicitly critiqued that style before, via his linkedin-roast skill usage).
- Egyptian/Gulf banking context is a differentiator, not a limitation — fine to reference regional experience specifically.
- No emojis by default unless Mido asks for them.
