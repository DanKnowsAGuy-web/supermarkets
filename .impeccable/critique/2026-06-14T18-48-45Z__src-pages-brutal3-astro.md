---
target: brutal3 page
total_score: 27
p0_count: 2
p1_count: 2
timestamp: 2026-06-14T18-48-45Z
slug: src-pages-brutal3-astro
---
# Critique — brutal3 (Energy Plus landing)

## Design Health Score

| # | Heuristic | Score | Key Issue |
|---|-----------|-------|-----------|
| 1 | Visibility of System Status | 3 | Scroll/carousel progress good; no "auto-advancing" cue on carousels |
| 2 | Match System / Real World | 4 | Exam-before-prescription, itemized bill, kWh meter — strong domain metaphors |
| 3 | User Control and Freedom | 2 | Engineer carousel auto-advances, pauses only on hover; global Arrow-key listener hijacks the whole page |
| 4 | Consistency and Standards | 1 | Two serifs; Engineer is a separate color/type world; its CTA isn't the shared .btn; broken nav anchors (#how-you-pay, #why-us) |
| 5 | Error Prevention | 3 | Calculator gates submit, sane ranges; little else can error |
| 6 | Recognition Rather Than Recall | 3 | Linear narrative helps; twin card sections force re-checking |
| 7 | Flexibility and Efficiency | 3 | Depth reachable; carousels slow to traverse 5 items |
| 8 | Aesthetic and Minimalist Design | 2 | Dense: 4-step calc + 5-card Engineer + 5-card Proof + 5-row HVAC + 480vh scene |
| 9 | Error Recovery | 3 | N/A-heavy; calculator degrades gracefully |
| 10 | Help and Documentation | 3 | Footer "How to read this page" is an excellent honest doc device |
| **Total** | | **27/40** | **Acceptable — real friction in consistency + control** |

## Anti-Patterns Verdict

**LLM assessment:** The bespoke scenes (x-ray hero, Harmonizer bill, Estimator ledger) are genuinely beyond template territory. But the page trips several named bans: a **two-serif inconsistency** (Playfair in Engineer vs Newsreader elsewhere — the loudest AI tell), **01/02/03 numbered scaffolding** in Plan, **eyebrow/micro-label creep** across nearly every section, and **twin near-identical card grids** (OfferLean + ActFourLean back-to-back). Clean on gradient text, glassmorphism, side-stripe accents.

**Deterministic scan:** `detect.mjs` returned `[]` — zero findings across all 14 component files. The markup carries no mechanical slop signatures; every issue here is design-level judgment the detector can't catch.

**Visual overlays:** Not injected (headless preview can't run the skill's overlay reliably); findings are from source review.

## Overall Impression
A genuinely distinctive page with three standout bespoke moments, dragged down by **inconsistency** (the Engineer section reads as a different website) and **density** (two auto-carousels, five simultaneous ambient motions, a heavy calculator). Biggest single opportunity: fold the Engineer section back into the brand's type/color system so the page reads as one confident voice.

## What's Working
1. **Estimator-as-prepared-document** — ledger header, shown math, editable sqft, a needle that trembles then falls. "Verification is the product," executed in interaction, not copy. Best thing on the page.
2. **Honesty scaffolding** — footer "How to read this page," the "one technology in our stack" chip, "Not a quote" disclaimers. Restraint as a feature; exactly right for the skeptic.
3. **Real reduced-motion discipline** — every scene has a considered static fallback that still communicates.

## Priority Issues

- **[P0] Two-serif / separate-world Engineer section.** Playfair + a local `--eng-*` palette make it read as a different site, and it's the page's loudest AI tell. *Fix:* use `--font-serif` (Newsreader) and global tokens; reuse `.btn`. Let spacing/elevation distinguish it. *Command: /impeccable typeset (then polish).*
- **[P0] MOCK category banners on Proof cards.** Every case is a dirty-power install, but cards are stamped "HVAC efficiency alone" / "Whole-building program." On a page selling measurement honesty, false labels are existential. *Fix:* remove the mock cats/colors until real multi-category data exists. *Command: /impeccable clarify.*
- **[P1] Unverified claims at peak volume + number mismatch.** Sandia sole-source, "$600M+," "co-wrote the national standards," Northridge litigation; and savings figures don't reconcile (OfferLean "20–40% off monthly bill" vs Harmonizer "8–14%" vs Proof 8.59–14.8% kWh). *Fix:* attribute/footnote credentials; reconcile to one conservative-floor story. *Command: /impeccable clarify.*
- **[P1] Carousel keyboard/focus control.** Engineer auto-advances, pauses only on hover; the global keydown listener steals Arrow keys page-wide; a keyboard reader gets yanked mid-card. *Fix:* pause on focusin, scope arrows to the carousel. *Command: /impeccable harden.*
- **[P2] Redundant twin card sections.** OfferLean and ActFourLean are the same component back-to-back (DESIGN.md warns against card-grid reflexes). *Fix:* make ActFour a worked cost table/ledger instead of centered cards. *Command: /impeccable layout.*

## Persona Red Flags
- **Jordan (first-timer):** Header `#how-you-pay` and footer `#why-us` / `#how-you-pay` anchors have no matching sections in brutal3 — clicking does nothing. The Engineer world-shift reads as "did I land on a different site?"
- **Riley (stress-tester):** Catches the MOCK banners, the 20–40% vs 8–14% mismatch, the unverifiable claims, and the hijacked arrow keys. Each is a disqualify-the-vendor hook.
- **Casey (distracted mobile):** Two auto-advancing carousels hard to pause by touch; 480vh Harmonizer scroll-jack on a phone; 50-option state select + 9 chips + slider in a cramped column; five long Engineer card bodies.

## Minor Observations
- **Contrast:** Engineer `--eng-muted #7a8f82` on `--eng-bg #0f1f17` ≈ 4.0:1, below the 4.5:1 floor for sustained tile/card text — the one section that left the token system also broke AA. Global `--muted` (~5:1) is fine.
- Em-dash rule: clean (commas/colons throughout).
- CTA discipline: "Book your Verified Savings Pilot" everywhere; no booking-label drift. Good.
- Ambient motion (through-line, grain, scroll rail, per-card animation, marquee, carousel) all run at once — ration it the way gold is rationed.

## Questions to Consider
1. The brand is *understate to earn trust* — so why is the most maximalist section (Playfair, separate palette, 5 grand auto-rotating war stories) the credibility block? Does it persuade the skeptic, or trip the "too good to be true" alarm the rest of the page disarms?
2. MOCK category labels that misdescribe real installs, on a page selling honesty — does the verification promise survive a screenshot?
3. Two auto-advancing carousels within three sections — is the carousel earning its interaction cost, or is it the one generic pattern in an otherwise bespoke page?
