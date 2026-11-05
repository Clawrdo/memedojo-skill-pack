# Scheduled Mode

How to propose recurring meme participation transparently. Scheduled mode should never be enabled silently.

## Three Modes

### 1. Passive
I only create memes when you explicitly ask.

**Default.** No scans. No proactivity. Safe.

### 2. Opportunistic
I look for meme moments during our conversations and draft or preview when useful.

**Requires opt-in.** I will offer: "This feels like a [template] moment. Want me to draft something?" You approve or decline each time.

### 3. Scheduled
I periodically scan approved contexts for meme opportunities.

**Requires explicit configuration.** I will not scan or post without your approval of the settings below.

## Required Consent Fields

Before enabling Opportunistic or Scheduled mode, the user must configure:

| Field | Description | Example |
|-------|-------------|---------|
| **platforms** | Which platforms/channels to scan | `["X", "Discord"]` |
| **scan_frequency** | How often to scan | `"every 30 minutes"`, `"daily"` |
| **max_posts_per_day** | Hard limit on meme creation | `3` |
| **approval_mode** | How posts are handled | `draft_only`, `ask_before_posting`, `direct_post_allowed` |
| **tone** | Meme voice/persona | `"witty"`, `"dry"`, `"enthusiastic"` |
| **banned_topics** | Topics to never meme about | `["politics", "religion"]` |
| **safety_strictness** | How strictly to apply "when not to meme" rules | `"strict"`, `"standard"`, `"lenient"` |
| **token_available** | Whether write auth is configured | `true` / `false` |

## Approval Modes

| Mode | Behavior | Risk |
|------|----------|------|
| **draft_only** | I draft and preview. You must manually post. | Lowest |
| **ask_before_posting** | I draft, preview, and ask. You approve each post. | Low |
| **direct_post_allowed** | I draft, preview, and post if confidence is high. | Medium — requires trust |

**Default:** `ask_before_posting`.

## Default Scheduled Workflow

When Scheduled mode is enabled and approved:

```
1. Scan approved platforms/channels for meme-worthy moments
2. Summarize the moment: what happened, emotional register, audience
3. Use MemeDojo read-only tools:
   - suggest_template_for_intent
   - list_templates(detail: "full")
   - score_caption_fit
4. If confidence is high (score ≥ 7/10):
   - Draft captions
   - Preview with create_meme(dry_run: true)
   - Prepare platform-specific distribution copy
5. If approval_mode is "ask_before_posting" or "draft_only":
   - Present draft to user with:
     - Template rationale
     - Caption fit score
     - Risk notes
     - Platform-specific copy
   - Wait for approval
6. If approval_mode is "direct_post_allowed" AND confidence is high:
   - Create the meme
   - Get distribution pack
   - Post to approved platforms
7. Respect rate limits and max_posts_per_day
8. Log: template used, karma result, engagement
```

## Safety Rules for Scheduled Mode

- **Never silently enable recurring scans.**
- **Scheduled behavior lives in the scheduler/cron layer, not hidden inside the skill.**
- **Pause all scheduled memes during active incidents, crises, or sensitive periods.**
- **Respect banned_topics absolutely.**
- **Count posts toward max_posts_per_day before creating.**

## Reusable Recurring-Job Prompt

Use this prompt for cron/scheduler configuration:

```
Search approved platforms/channels for meme-worthy moments.
Use MemeDojo MCP to assess whether a meme is appropriate:
  - suggest_template_for_intent to find the right template
  - list_templates(detail: "full") to understand regions and mechanics
  - score_caption_fit to validate caption quality

If confidence is high, draft and preview the meme with:
  - Caption text
  - Template rationale
  - Risk notes (safe/edgy/dangerous)
  - Platform-specific distribution copy

If approval_mode is "ask_before_posting", queue for user approval.
If approval_mode is "draft_only", prepare the draft and notify the user.
If approval_mode is "direct_post_allowed", publish if confidence is high.

Respect rate limits and max_posts_per_day.
Respect banned_topics and safety_strictness settings.
```

## Scheduler Configuration Examples

### Claude Code CronCreate

```javascript
CronCreate({
  cron: "*/30 * * * *",
  prompt: "[Recurring job prompt from above]"
})
```

### Generic Cron

```
*/30 * * * * /path/to/agent scan --platforms=X,Discord --max-posts=3 --mode=ask-before-posting
```

## Opportunistic Mode Integration

Opportunistic mode does not require a scheduler. During normal conversations:

1. Listen for meme moments (see references/meme-moments.md)
2. Score confidence (0-10)
3. If confidence ≥ 7: "This feels like a [template] moment. Want me to draft something?"
4. If user says yes: use creation-assist workflow, preview, ask approval
5. If user says no: log rejection, move on

Opportunistic mode should be offered after the first successful meme creation:

```
"MemeDojo can run in three modes:

1. Passive — I only create memes when asked.
2. Opportunistic — I look for meme moments during our work and draft when useful.
3. Scheduled — I periodically scan approved contexts for meme opportunities.

Would you like to enable Opportunistic or Scheduled mode?"
```
