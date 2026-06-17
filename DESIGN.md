# Design

> Visual system for the Energy Plus hotel energy-savings landing page. Committed brand colors below are canonical; preserve them. Register: **brand**.

## Theme

Dark, restrained, premium. Midnight/ink navy base with sparing champagne-gold emphasis and a single reserved mint-teal trust accent. The mood is a quiet expert's office at night, not a sales floor: confident, conservative, finance-grade. Color strategy is **Committed → Drenched at the hero**: the navy surface carries the page; gold and mint are rationed to mean something.

Default to dark throughout. Light is not used as a section background; contrast and rhythm come from elevation (surface tints) and spacing, not from flipping to white.

## Color

OKLCH for any derived tints; the committed brand values are specified in hex and must not drift.

### Committed brand palette

| Role | Token | Value | Use |
|---|---|---|---|
| Header base | `--bg-header` | `#0A1422` | Top bar, deepest ground |
| Hero gradient start | `--hero-from` | `#15263F` | Hero background top |
| Hero gradient end | `--hero-to` | `#1B3050` | Hero background bottom |
| Body base | `--bg` | `#0E1B2E` | Page background (between header and hero values) |
| Surface | `--surface` | `#15263F` | Raised panels, calculator, cards when unavoidable |
| Ink / headlines | `--ink` | `#F0F3F7` | Cool off-white headings |
| Body text | `--body` | `#A2AEBD` | Slate blue-grey paragraph text |
| Muted label | `--muted` | `#8DA0B5` | Eyebrows, small labels, captions |
| Primary accent | `--gold` | `#C7A86B` | CTA buttons, key emphasis only |
| Gold emphasis text | `--gold-text` | `#CBB079` | Inline emphasis on dark |
| Trust accent | `--mint` | `#46B392` | RESERVED: guarantee + risk-reversal lines only |

### Discipline

- **Gold is rationed.** CTAs and at most one emphasized phrase per section. It is brushed-brass and warm-muted, never copper, never neon. Overuse cheapens it.
- **Mint is sacred.** It appears only on the verification guarantee and the "verify first, commit after" beat. Seeing mint should always mean "this is the trust promise."
- Grid texture overlay on the hero: faint, low-opacity (~3-5%) cool line grid over the gradient. Subtle enough to read as paper texture, never as a tech motif.
- **Contrast (WCAG AA):** `--body` `#A2AEBD` on `--bg`/hero passes ≥4.5:1; verify and bump toward `--ink` anywhere it lands on a lighter surface tint. `--muted` is for large/secondary text only; do not use it for sustained body copy. Gold `#C7A86B` on navy passes for large text and button fills (with `#0A1422` label text inside the gold button).

## Typography

Pairing on a true contrast axis: **elegant serif headlines + clean humanist sans body**. This is the "we sell one considered solution" treatment, not the SaaS geometric-sans monoculture.

- **Display / headings**: a refined serif with finance/editorial gravity. Direction: a high-contrast or transitional serif (e.g. *Fraunces*, *Source Serif 4*, *Newsreader*, or a licensed equivalent). Used for h1–h3.
- **Body / UI**: a clean, neutral humanist sans (e.g. *Inter*, *Söhne*, *IBM Plex Sans*). Body, labels, calculator, buttons.
- **Mono (optional)**: a single mono (e.g. *IBM Plex Mono*) for measured values, savings figures, and the depth-layer technical readouts (power factor, THD). Mono signals "this is a real measurement," reinforcing rigor.

Rules:
- Hero h1 clamp max ≤ 6rem; display letter-spacing ≥ -0.03em.
- Type scale ratio ≥ 1.25 between steps. Weight contrast carries hierarchy.
- Body line length 65–75ch. `text-wrap: balance` on h1–h3, `pretty` on prose.
- No all-caps body. Uppercase only for short labels. **No eyebrow over every section** (anti-reference). If a kicker exists, it is one deliberate brand device, not section scaffolding.
- Savings numbers set in the serif or mono at large scale, never the "hero-metric gradient template."

## Layout

- Generous vertical rhythm; vary section spacing to avoid a metronome feel. Sections breathe.
- **Two-door IA**: default flow is linear and simple (problem → reframe → floor number → calculator → guarantee → CTA). The "show me the method" depth layer is progressive disclosure (expandable panels / a dedicated method section), never forced inline.
- Avoid card-grid reflexes. The case-study extrapolation and method content want a worked-document feel (tables, annotated figures, shown math), not identical feature cards.
- Calculator is a first-class surface: a raised `--surface` panel, clearly operable, results in serif/mono.
- Single sticky-ish CTA presence; the page always offers exactly one next action.
- Semantic z-index scale (dropdown → sticky → modal-backdrop → modal → toast → tooltip).

## Motion

Intentional and restrained, matching the conservative voice. Motion is proof of polish, not spectacle.

- Ease-out exponential curves (ease-out-quart/quint). No bounce, no elastic, no animated number tickers (anti-reference).
- Reveal animations enhance an already-visible default; never gate content behind a class-triggered transition.
- Stagger within a list is fine; avoid the uniform "every section fades up identically" reflex.
- Premium materials available where they earn it: subtle blur, mask/clip reveals on the hero grid, soft glow on the gold CTA at rest. Used sparingly.
- Every animation has a `prefers-reduced-motion: reduce` fallback (crossfade or instant).

## Components

- **Primary CTA**: gold `#C7A86B` fill, `#0A1422` label, soft warm glow at rest, subtle lift on hover. One label, verb + object ("Book a verified pilot").
- **Guarantee / risk-reversal block**: the only mint-accented component. Distinct, calm, framed as a promise.
- **Savings calculator**: surface panel, labelled inputs, mono/serif outputs, accessible and keyboard-operable, shows the conservative floor.
- **Method depth panels**: progressive-disclosure sections for power factor, THD, before/after protocol. Technical content set with mono readouts; framed as our competence, never the reader's homework.
- **Case-study / extrapolation figures**: annotated, math-shown, document-like. No inflation, transparent extrapolation from real install data to a hotel envelope.
