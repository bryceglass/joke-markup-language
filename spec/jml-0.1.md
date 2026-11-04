# JML v0.1 — Experimental Draft

Joke Markup Language (JML) is an XML-based, performer-independent language for comedic structure, intent, delivery and staging. This is a **draft**, not a stable standard.

## Principles
Semantic direction by default; precise overrides when needed. The words of dialogue are authoritative: renderers must not rewrite dialogue based on annotations. Unsupported directions should degrade gracefully with diagnostics.

## Structural model
`routine` contains `scene` elements; scenes can contain `bit`, `joke`, `beat`, `line`, and stage cues. A **bit** explores a premise, a **joke** builds toward one or more payoffs, and a **beat** is a meaningful unit of performance, not necessarily a pause. These containers need not all be present.

Vocabulary: `routine`, `scene`, `bit`, `joke`, `beat`, `line`, `setup`, `misdirect`, `punch`, `tag`, `callback`, `button`, `attitude`, `delivery`, `pause`, `emote`, `react`, `sfx`, `look`, `hold`.

## Draft attributes
- `routine`: required `id` and `version="0.1"`.
- `bit`: `id`, `premise`, `arc`.
- `joke`: `id`, `form`, `intent`, `target`.
- `beat`: `id`, `intent`.
- `line`: required `character`; optional `id`.
- `punch`: `id`, `intent`.
- `attitude`: `tone`, `ire`, `irony`, `energy`, `confidence`.
- `delivery`: `pitch`, `volume`, `pace`, `rhythm`, `inflection`, `emphasis`.
- `pause`: `ms` (nonnegative integer).
- `react`: `character`, `emote`, `after`, `delay`.
- `sfx`: `id`, `after`, `delay`.

Delivery suggestions: pitch `low|mid|high|+2st`; volume `whisper|soft|normal|loud|shout`; pace `very-slow|slow|normal|fast|very-fast|140wpm`; rhythm `natural|staccato|legato|clipped`; inflection `natural|rising|falling|flat`; emphasis `none|light|medium|strong`.

Attitude suggestions: tone `neutral|dry|deadpan|playful|earnest|sarcastic|incredulous|indignant|exasperated|conspiratorial`; ire, energy and confidence `0.0–1.0`; irony `none|subtle|moderate|strong`.

## Timing and inheritance
Speech proceeds in document order unless explicitly overlapped. References use `after="element-id.end"` or `after="element-id.start"` and delays such as `400ms`. IDs must be unique, references resolvable, and timing dependencies acyclic. Reactions anchored to speech should use measured synthesized-audio durations when available.

Settings inherit by property: character profile → routine → scene → beat/line → inline attitude/delivery. One-shot cues and structural annotations do not inherit. Character defaults apply to that character only.

## Outstanding specification work
Formal mixed-content grammar, nesting constraints, namespaces, profile definitions, timing concurrency, conformance classes, extension rules, and exact validation requirements remain open. No normative XSD is claimed yet.
