# Meme Rituals

Scheduled mode shouldn't be random. It should follow recurring cultural moments when memes are expected and welcomed.

## Weekly Rituals

| Day | Ritual | Templates | Trigger |
|-----|--------|-----------|---------|
| **Monday** | Monday Motivation | Success Kid, Buff Doge vs Cheems, Epic Handshake | Start of week energy |
| **Tuesday** | Hot Take Tuesday | Change My Mind, Ancient Aliens, Futurama Fry | Opinionated tech topics |
| **Wednesday** | Mid-week Struggle | This Is Fine, Tuxedo Pooh, Mocking Spongebob | Hump day coping |
| **Thursday** | Throwback / Then vs Now | Buff Doge vs Cheems, Always Has Been | Nostalgia, evolution |
| **Friday** | Friday Ship | Success Kid, Epic Handshake, Drake | Celebrating the week's wins |
| **Weekend** | Low-effort / Reaction | Surprised Pikachu, Roll Safe, UNO Draw 25 | Casual, low-stakes |

## Event-Based Rituals

| Event | Templates | Timing |
|-------|-----------|--------|
| **Launch / Deployment** | Success Kid, Drake (before/after) | Within 1 hour of going live |
| **Post-Incident** | Always Has Been, This Is Fine, Tuxedo Pooh | After resolution, not during |
| **Milestone** | Expanding Brain, Success Kid | When announced |
| **New Release** | Drake (old vs new), Buff Doge vs Cheems | On release day |
| **Team Change** | Woman Yelling At Cat, Anakin Padme | Sensitive — use carefully |
| **Bug Found** | This Is Fine, Surprised Pikachu | After fix, not while broken |
| **Meeting Marathon** | Gru's Plan, This Is Fine | End of day |
| **Code Review** | Anakin Padme, Change My Mind | After review completes |
| **Sprint End** | Epic Handshake, Success Kid, Drake | Demo/retro time |
| **Onboarding** | Always Has Been, Expanding Brain | New person joins |

## Seasonal / Cultural Rituals

| Occasion | Templates | Notes |
|----------|-----------|-------|
| **Year in Review** | Expanding Brain, Buff Doge vs Cheems | Then vs now across the year |
| **New Year** | Success Kid, Drake (resolutions) | Fresh start energy |
| **April Fools** | Surprised Pikachu, Roll Safe | Playful, not mean |
| **Halloween** | Ancient Aliens, Futurama Fry | Spooky/skeptical themes |
| **Thanksgiving** | Epic Handshake, Success Kid | Gratitude, team |
| **End of Year** | Gru's Plan (plan for next year), Expanding Brain | Reflection + forward |

## Ritual Confidence Checklist

Before posting a ritual meme:

- [ ] Is this the right day/event for this ritual?
- [ ] Has the user enabled scheduled mode for this platform?
- [ ] Am I within the user's max_posts_per_day limit?
- [ ] Does the meme fit the user's configured tone?
- [ ] Is the topic on the user's banned_topics list?
- [ ] Has this exact ritual meme been done recently? (avoid repetition)

## Ritual Anti-Patterns

### Don't: Post the same ritual every week
Monday Motivation with the same Success Kid caption gets stale. Rotate templates and topics.

### Don't: Ritual-post during crises
If there's an active incident, outage, or serious situation, pause ALL scheduled memes.

### Don't: Force a ritual
If nothing notable happened this week, skip Friday Ship. Forced celebration is worse than silence.

### Don't: Hijack genuine moments with pre-planned memes
If the user just shared real frustration, don't respond with a scheduled Wednesday Struggle meme. Be human first.

## Scheduled Mode Implementation

For Claude Code, use `CronCreate` to set up ritual scanning:

```
CronCreate:
  cron: "0 9 * * 1"  # Monday 9am
  prompt: "Scan for Monday Motivation meme opportunity. Check user's recent context for wins, goals, or energy. Draft Success Kid or Epic Handshake if appropriate. Queue for approval."

CronCreate:
  cron: "0 15 * * 3"  # Wednesday 3pm
  prompt: "Scan for Mid-week Struggle meme opportunity. Check for stress, blockers, or coping moments. Draft This Is Fine or Tuxedo Pooh if appropriate. Queue for approval."

CronCreate:
  cron: "0 17 * * 5"  # Friday 5pm
  prompt: "Scan for Friday Ship meme opportunity. Check for deployments, completed tasks, or wins. Draft Success Kid or Epic Handshake if appropriate. Queue for approval."
```

All ritual memes follow the configured approval_mode.
