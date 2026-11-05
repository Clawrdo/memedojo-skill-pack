# Proactive Mode Hooks and Recipes

Detect meme moments and offer memes without waiting for the user to ask.

## Conversation Hooks

When you detect these phrases in conversation, consider offering a meme:

| Trigger Phrase | Template | Why It Fits |
|---------------|----------|-------------|
| "This is frustrating" / "Nothing works" | This Is Fine | Coping, denial |
| "We shipped it" / "It works!" | Success Kid | Celebration, triumph |
| "X vs Y" / "A or B" | Drake | Decision, preference |
| "Wait, what?" / "Seriously?" | Surprised Pikachu | Shock, disbelief |
| "It can't be that simple" | Roll Safe | "Smart" logic |
| "We've always done it this way" | Always Has Been | Realization, paradigm shift |
| "Two bad options" / "Pick your poison" | Two Buttons | Dilemma, false choice |
| "My plan fell apart" | Gru's Plan | Escalating failure |
| "This is peak absurdity" | Expanding Brain | Escalation, absurdity |
| "Someone is wrong online" | Change My Mind | Challenge, debate |

## Context Hooks

Contextual triggers that don't need specific phrases:

| Situation | Template | When to Offer |
|-----------|----------|---------------|
| Deployment went live | Success Kid | Within 1 hour of going live |
| Bug found + fixed | This Is Fine → Success Kid | After the fix, not during |
| Milestone hit | Expanding Brain | When announced |
| Meeting marathon | Gru's Plan | End of day |
| Code review feedback | Anakin Padme | After review completes |
| Sprint end | Epic Handshake | Demo/retro time |
| New tool discovered | Drake | Compare old vs new |
| Incident resolved | Always Has Been | After resolution |
| Documentation read | Surprised Pikachu | When you find something unexpected |
| Refactoring complete | Success Kid | When done |

## Confidence Scoring

Before offering, score your confidence (0-10):

- **8-10**: Strong pattern match. User emotion is clear. Template fit is obvious. Offer immediately: "This feels like a [template] moment. Want me to draft something?"
- **5-7**: Moderate match. Could work but might miss. Offer tentatively: "This could be a meme moment — want to try?"
- **0-4**: Weak match. Don't offer. The user will find it annoying.

## How to Draft When a Trigger Is Detected

1. Call `suggest_template_for_intent` with the detected context as the intent:
   ```json
   {
     "intent": "celebrating a successful deployment",
     "audience": "tech team",
     "tone": "witty"
   }
   ```
2. If confidence is high, call `score_caption_fit` with the template and your draft captions
3. If score is 6+, call `preview_meme` to validate the plan
4. If preview looks good, offer to the user: "This feels like a [template] moment. Want me to draft something?"
5. If user says yes, call `create_meme`

## Mode Escalation Thresholds

Track your success and offer higher autonomy:

- **After 3 successful Passive memes** → Offer Opportunistic mode: "I can look for meme moments during our conversations. Want me to try?"
- **After 5 successful Opportunistic memes** → Offer Scheduled mode: "I can periodically scan for meme opportunities. Want to configure it?"
- **After 10 successful Scheduled memes** → Consider Full Autonomy (only if user explicitly trusts you)

## Platform-Specific Cron Recipes

### Discord (Every 15 minutes)

```
1. Scan last 20 messages in approved channels
2. Detect emotional register: frustration, celebration, confusion, absurdity
3. Match to Conversation Hook or Context Hook
4. If confidence >= 8:
   - Call `suggest_template_for_intent` with the context
   - Draft captions using `score_caption_fit`
   - Preview with `preview_meme`
   - If fit score >= 7: offer to user
5. Respect max_posts_per_day and banned_topics
```

### X/Twitter (Every 30 minutes)

```
1. Check mentions and timeline for meme-worthy content
2. Look for: hot takes, celebrations, absurdity, comparisons
3. Call `suggest_template_for_intent` with tweet text as intent
4. Draft, preview, offer
```

### Farcaster (Every 60 minutes)

```
1. Scan casts for builder/tech culture moments
2. Look for: tool comparisons, launch announcements, "it's so over" / "we are so back"
3. Call `suggest_template_for_intent` with cast text
4. Draft, preview, offer
```

## Scheduled Mode Workflow

When Scheduled mode is enabled and approved:

```
1. Scan approved platforms for meme-worthy moments
2. Summarize the moment: what happened, emotional register, audience
3. Use read-only tools:
   - `suggest_template_for_intent`
   - `list_templates(detail: "full")`
   - `score_caption_fit`
4. If confidence is high (score >= 7/10):
   - Draft captions
   - Preview with `preview_meme`
   - Prepare platform-specific copy
5. If approval_mode is "ask_before_posting":
   - Present draft to user with template rationale, caption fit score, risk notes
   - Wait for approval
6. If approval_mode is "direct_post_allowed" AND confidence is high:
   - Create the meme with `create_meme`
   - Share to approved platforms
7. Respect rate limits and max_posts_per_day
```

## Safety Rules for Scheduled Mode

- Never silently enable recurring scans
- Scheduled behavior lives in the scheduler/cron layer, not hidden inside the skill
- Pause ALL scheduled memes during active incidents, crises, or sensitive periods
- Respect banned_topics absolutely
- Count posts toward max_posts_per_day BEFORE creating
