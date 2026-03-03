# AlignED Report 2 — Site Guidelines

## Project Overview

AlignED Report 2 examines whether two Gemini models can assess complex student competencies using a standardised rubric. The central finding is a data contamination effect: models recall ETS scores without seeing the rubric (67% exact match on ETS essays vs ~33-42% on PERSUADE essays), suggesting inflated accuracy on well-known corpora.

This is a static HTML/CSS/JS site hosted on GitHub Pages. No build tools, no templating. Text is written directly in each page's HTML file. The site is structured as a frozen academic paper and is not updated after publication.

## File Structure

- Abstract/Cover: `index.html`
- Introduction: `introduction.html`
- Methods: `methods.html`
- Results: `results.html` (charts render here via `js/charts.js`)
- Discussion: `discussion.html`
- Appendices: `appendices.html`
- Shared styles: `css/style.css` (unified stylesheet, no inline styles)
- Charts: `js/charts.js` (uses `document.body.dataset.page` for page detection)
- Navigation: `js/main.js` (mobile toggle, active link)
- Data: `data/ets_scoring.json`, `data/persuade_scoring.json`, `data/contamination.json`, `data/feedback_samples.json`

## Navigation Structure

```
AlignED | Abstract | 1. Introduction | 2. Methods | 3. Results | 4. Discussion | Appendices
```

## Page Detection

Charts only render on the Results page. Detection uses `document.body.dataset.page`:
- `data-page="abstract"` — index.html
- `data-page="introduction"` — introduction.html
- `data-page="methods"` — methods.html
- `data-page="results"` — results.html (charts render here)
- `data-page="discussion"` — discussion.html
- `data-page="appendices"` — appendices.html

## Writing Rules (MUST follow for all copy changes)

### Epistemic Precision (most important rule)

This report examines a proof-of-concept with 2 models and 18 essays. Every claim must be appropriately hedged. Frame as signal, not proof.

| Never write | Write instead |
|-------------|---------------|
| "LLMs cannot assess essays" | "Score recall rates differed between corpora, suggesting a contamination effect" |
| "proves data contamination" | "consistent with data contamination" |
| "the models memorised the scores" | "models recalled scores at a higher rate for the likely-contaminated corpus" |
| "AI grading is unreliable" | "accuracy on well-known corpora may be inflated by memorisation" |

### Contamination Framing (critical)

Always distinguish between:
- **Verbatim recall** (can the model reproduce the essay text?) — LOW for both models
- **Score recall** (can the model guess the score without the rubric?) — HIGH for ETS, LOWER for PERSUADE
- **Assessment accuracy** (does the model score correctly when given the rubric?) — separate question

The contamination signal is the *gap* between ETS and PERSUADE score recall, not the absolute recall rate.

### Numbers

- Always show raw counts alongside percentages: "4 of 6 (67%)"
- For small samples, lead with the count: "4 of 6 essays" not "67% of essays"
- Report exact values from data files; do not round or approximate

### Tone

- Short, confident sentences. Vary sentence length.
- Active voice. Be direct about limitations.
- Trust the reader's intelligence.
- Use British/Australian spelling (prioritise, recognise, organisation, behaviour).

### AI Slop Blacklist

DO NOT USE any of the following:

Punctuation: Em dashes as all-purpose connectors (max one per page). Excessive colons.

Phrasing: "It's not X, it's Y". "In today's rapidly evolving...". "It's worth noting that...". "This is particularly important because...". "The short answer is...". "Here's the thing:". "Let's dive in" / "Let's explore" / "Let's unpack". "At the end of the day". "Importantly," / "Crucially," / "Notably,".

Words: Groundbreaking, Revolutionary, Ensure, Empower, Leverage, Harness, Holistic, Cutting-edge, State-of-the-art, Stakeholders, Ecosystem, Deep dive, Robust (as general praise), Genuine/Genuinely.

### Footer Tagline (all pages)

Use: "Benchmarking AI models for educational practice."

## Visual Design

Warm parchment palette (identical to Report 1):
- Background: `#F4F1EB`, Surface: `#FEFDFB`, Text: `#2D3748`
- Primary: `#3B6B9A`, Accent: `#B67D5C`
- Typography: Inter (headings) + Georgia (body) + Consolas (code/prompts)

## CSS Rules

All styles in `css/style.css`. No inline styles on any page.

## Chart Colours

- Google blue `#4285F4` for Gemini 3.1 Pro
- Lighter blue `#7BAAF7` for Gemini 3 Flash
- Grey `#9CA3AF` for human/ETS baseline scores
