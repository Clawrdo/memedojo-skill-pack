# Platform Adapters

How to package and distribute memes for each platform. Meme grammar differs across platforms.

## X / Twitter

**Format:** Short, high-contrast, reply-aware  
**Best templates:** Drake, Surprised Pikachu, Always Has Been, Success Kid

### Guidelines
- Keep captions under 6 words per panel
- High visual contrast — must read in a small timeline thumbnail
- Quote-tweet friendly: the meme should make sense even without the quoted text
- Thread-aware: if replying in a thread, reference the thread topic
- Alt text: include for accessibility
- Hashtags: minimal (0-2), only if genuinely relevant

### Distribution Copy Structure
```
[Optional: brief context sentence]
[Image]
[Optional: 1-2 hashtags]
```

### Example
```
Every integration project ever.

[Drake meme: "Writing custom integrations" / "Using MCP"]

#MCP #AgentProtocol
```

## Discord

**Format:** Fast, community-native, emote/sticker energy  
**Best templates:** This Is Fine, Mocking Spongebob, Surprised Pikachu, Roll Safe

### Guidelines
- Speed matters — post quickly after the moment
- Match the channel's energy and inside jokes
- Emote/sticker culture: memes can be simpler, more reaction-like
- Nitro-friendly: high-quality images work well
- Thread-aware: reply in the right thread
- Less formal than X — community slang is okay

### Distribution Copy Structure
```
[Optional: @mention if replying to someone]
[Image]
[Optional: single emoji or reaction phrase]
```

### Example
```
@dev-team [This Is Fine meme: "It's just a small config change"]
🔥
```

## Farcaster

**Format:** AI/crypto/builder-native, concise  
**Best templates:** Drake, Buff Doge vs Cheems, Expanding Brain, Tuxedo Pooh

### Guidelines
- Audience is builders, AI enthusiasts, crypto-native
- Tech-forward topics perform best
- Concise — frames and casts are short
- Warpcast-specific: consider frame interactions
- Crypto culture references land well
- Less about memes as reactions, more about memes as signals

### Distribution Copy Structure
```
[Short, punchy observation]
[Image]
[Optional: frame or link]
```

### Example
```
The duality of builder tools

[Buff Doge vs Cheems: "Complex custom stack" / "One MCP call"]
```

## Reddit

**Format:** Subreddit-aware, less polished, avoid marketing tone  
**Best templates:** Expanding Brain, Always Has Been, Gru's Plan, Woman Yelling At Cat

### Guidelines
- Match the subreddit's culture and rules
- Less polished, more authentic — "fellow Redditor" energy
- Avoid any hint of marketing or self-promotion
- Comment replies are often better than top-level posts
- Cross-post carefully — check subreddit rules first
- Title is crucial — make it click-worthy but not clickbait

### Distribution Copy Structure
```
[Title that matches subreddit style]
[Image]
[Optional: brief context in body]
```

### Example (r/programminghumor)
```
Title: "The evolution of API integration"

[Expanding Brain meme: 4 stages from REST chaos to MCP zen]
```

## Telegram

**Format:** Sticker-like, simple, punchy  
**Best templates:** Surprised Pikachu, Success Kid, This Is Fine, Drake

### Guidelines
- Sticker energy — fast, punchy, immediately readable
- Groups vs channels: group memes can be more conversational
- Inline bots: some groups have meme bots, consider compatibility
- Less text is more — image should carry the joke
- Reaction-friendly: Telegram reactions make meme feedback instant

### Distribution Copy Structure
```
[Optional: one-line setup]
[Image]
```

### Example
```
POV: You discover the bug was a missing semicolon

[Surprised Pikachu meme]
```

## Slack

**Format:** Workplace-safe, lightweight  
**Best templates:** Success Kid, Epic Handshake, This Is Fine, Tuxedo Pooh

### Guidelines
- Workplace-appropriate: no controversial topics, no harassment-adjacent humor
- Channel-aware: #general has different standards than #random
- Thread-friendly: reply in threads to keep channels clean
- Emoji reactions: expect emoji reactions rather than text replies
- Timing: work hours are fine, but avoid late-night or early-morning spam
- @channel / @here: never use with memes unless explicitly appropriate

### Distribution Copy Structure
```
[Optional: brief, work-appropriate context]
[Image]
```

### Example (#random or #memes channel)
```
Friday deploy energy

[This Is Fine meme: "It's just a small hotfix"]
```

## Livestream

**Format:** Fast reaction cards, minimal text, hype-aware  
**Best templates:** Surprised Pikachu, Success Kid, Drake, Always Has Been

### Guidelines
- Speed is everything — react within seconds of the moment
- Minimal text: must be readable at a glance while chat scrolls
- Hype-aware: match the stream's energy level
- Chat integration: consider how chat will react
- Overlay-friendly: if used as an overlay, ensure text is large enough
- No sound dependency: meme must work without audio

### Distribution Copy Structure
```
[Image only — no text needed]
```

### Example
```
[Drake meme overlay reacting to streamer's choice]
```

## Platform Comparison

| Platform | Text Amount | Speed | Tone | Audience |
|----------|------------|-------|------|----------|
| X/Twitter | Minimal | Medium | Witty | General tech |
| Discord | Minimal | Fast | Casual | Community |
| Farcaster | Minimal | Medium | Builder | AI/crypto |
| Reddit | Moderate | Slow | Authentic | Niche |
| Telegram | Minimal | Fast | Punchy | Group/chat |
| Slack | Minimal | Medium | Work-safe | Workplace |
| Livestream | None | Instant | Reactive | Viewers |

## Cross-Platform Strategy

1. **Create once** using `create_meme`
2. **Distribution metadata** is included in the `create_meme` response
3. **Adapt copy** per platform using this guide
4. **Post separately** — do not cross-post identical text
5. **Track per-platform performance** if possible

## Platform-Specific Templates

| Platform | Top Performers | Avoid |
|----------|---------------|-------|
| X/Twitter | Drake, Surprised Pikachu, Success Kid | Long-caption templates (Gru's Plan, Expanding Brain) |
| Discord | This Is Fine, Mocking Spongebob, Roll Safe | Overly formal templates (Tuxedo Pooh) |
| Farcaster | Drake, Buff Doge vs Cheems, Expanding Brain | Generic non-tech templates |
| Reddit | Expanding Brain, Always Has Been, Gru's Plan | Overly polished / corporate memes |
| Telegram | Surprised Pikachu, Success Kid, Drake | Text-heavy templates |
| Slack | Success Kid, Epic Handshake, This Is Fine | Controversial/opinionated templates |
| Livestream | Drake, Surprised Pikachu, Success Kid | Any template requiring reading time |
