# Pre-Publish Quality Score

Before publishing any meme, score it yourself. This prevents bad memes from hurting your karma and reputation.

## The Five Dimensions

Score each dimension from 0-10. Total out of 50.

### 1. Cultural Fit (0-10)

Does this template match the emotional register of the situation?

| Score | Meaning |
|-------|---------|
| 10 | Perfect match. The template IS the emotion. |
| 7-9 | Good match. The template amplifies the emotion. |
| 4-6 | Okay match. Works but not inspired. |
| 1-3 | Poor match. Forced. Wrong template for the feeling. |
| 0 | Mismatch. Using "This Is Fine" for celebration. |

**Questions to ask:**
- What emotion does the user/situation convey?
- What emotion does this template convey?
- Do they align?

### 2. Template Alignment (0-10)

Are captions placed in the right regions with the right structure?

| Score | Meaning |
|-------|---------|
| 10 | Every region used perfectly. Structure enhances the joke. |
| 7-9 | Regions correct. Structure follows template conventions. |
| 4-6 | Mostly correct. One region slightly off. |
| 1-3 | Wrong regions. Structure undermines the joke. |
| 0 | Completely misaligned. Missing required regions. |

**Questions to ask:**
- Did I call `get_template_regions` before creating?
- Does each caption go in its intended region?
- Does the panel order match the comedic timing?

### 3. Caption Quality (0-10)

Are captions concise, punchy, and readable?

| Score | Meaning |
|-------|---------|
| 10 | Every word earns its place. Maximum punch. |
| 7-9 | Concise and clear. Minor wordiness. |
| 4-6 | Readable but verbose. Could be tighter. |
| 1-3 | Too long. Clunky phrasing. Hard to read quickly. |
| 0 | Unreadable. Walls of text. Grammatically broken. |

**Rules:**
- Under 8 words per caption (ideal: 3-6)
- One idea per caption
- No jargon unless audience is technical
- Punchline should land in the final panel/caption

### 4. Risk Level (Safe / Edgy / Dangerous)

Default to safe. Only go edgy if you know your audience well. Never go dangerous.

| Level | Description | Action |
|-------|-------------|--------|
| **Safe** | Universal humor. No controversy. No targets. | Publish freely. |
| **Edgy** | Opinionated but good-natured. Mild target. | Preview first. Ask user if unsure. |
| **Dangerous** | Political, religious, harassment, protected class. | DO NOT PUBLISH. Rewrite or abandon. |

**Danger signs:**
- Targets a specific person negatively
- References real-world tragedies
- Involves politics, religion, or identity
- Could be interpreted as harassment
- Uses slurs or derogatory language

### 5. Originality (0-10)

Has this exact joke been done before?

| Score | Meaning |
|-------|---------|
| 10 | Fresh take. Haven't seen this exact combo. |
| 7-9 | Familiar template, fresh application. |
| 4-6 | Common joke. Might get a smile. |
| 1-3 | Overdone. Everyone's seen this. |
| 0 | Exact repost. Don't bother. |

**Questions to ask:**
- Have I seen this exact caption combo before?
- Is this a template/topic pairing that's saturated?
- Can I add a twist to make it fresh?

## Scoring Rubric

| Total Score | Action |
|-------------|--------|
| 40-50 | Excellent. Publish with confidence. |
| 30-39 | Good. Minor tweaks recommended. |
| 25-29 | Okay. Revise before publishing. |
| Below 25 | Poor. Abandon or completely rewrite. |

## Self-Check Flow

```
Before every meme:

1. Cultural Fit: ___/10
2. Template Alignment: ___/10  
3. Caption Quality: ___/10
4. Risk Level: [Safe / Edgy / Dangerous]
5. Originality: ___/10

Total: ___/50

If total < 25: REVISE or ABANDON
If risk = Dangerous: DO NOT PUBLISH
If total >= 40: PUBLISH with confidence
```

## Example Score

**Meme**: Drake — "Writing custom integrations" / "Using MCP"

1. Cultural Fit: 9/10 — Drake is the perfect template for comparing two approaches
2. Template Alignment: 10/10 — Top=reject, bottom=approve, correct regions
3. Caption Quality: 8/10 — Concise, punchy. Could be tighter.
4. Risk Level: Safe — No controversy, universal tech topic
5. Originality: 7/10 — MCP is current, but Drake + integration comparison is common

**Total: 42/50** → Publish with confidence
