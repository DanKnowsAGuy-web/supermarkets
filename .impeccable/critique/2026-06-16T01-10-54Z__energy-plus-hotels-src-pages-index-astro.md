---
target: the live homepage (src/pages/index.astro)
total_score: 29
p0_count: 1
p1_count: 2
timestamp: 2026-06-16T01-10-54Z
slug: energy-plus-hotels-src-pages-index-astro
---
## Design Health Score

| # | Heuristic | Score | Key Issue |
|---|-----------|-------|-----------|
| 1 | Visibility of System Status | 4 | Scroll-progress rail, Harmonizer step card, calculator `aria-live` all communicate state. |
| 2 | Match System / Real World | 4 | Excellent domain language ("exam vs prescription", "your meter", named verifiers). |
| 3 | User Control and Freedom | 2 | Magnetic CTA, 3D tilt, and auto-rotating carousels move without user intent. |
| 4 | Consistency and Standards | 2 | Two CTA systems (anchor-jump vs expand-in-place); `--font-serif` resolves to a sans; dead styles. |
| 5 | Error Prevention | 3 | Calculator gates submit and clamps input; no failure state for booking iframe / SMS handoff. |
| 6 | Recognition Rather Than Recall | 3 | Header is non-sticky and CTA hides <720px, so the single action is often off-screen. |
| 7 | Flexibility and Efficiency | 3 | Two doors + calculator serve different speeds; no true progressive-disclosure depth layer. |
| 8 | Aesthetic and Minimalist Design | 1 | 14 always-on sections with motion on nearly every element; volume dilutes the single CTA. |
| 9 | Error Recovery | 3 | Calculator robust; no visible failure path for the Google booking iframe. |
| 10 | Help and Documentation | 4 | Footer "How to read this page" note is an exemplary, on-brand methodology disclosure. |
| **Total** | | **29/40** | **Good — solid content engine dragged down by motion overload and length** |

## Anti-Patterns Verdict

**Does this look AI-generated? In substance, no. In surface costume, partly yes.**

**LLM assessment:** The static content is well above slop — specific declarative copy, unit-honest figures (kWh vs kW), named third-party verifiers, custom illustration. But several individual tells are exactly the patterns PRODUCT.md lists as anti-references: numbered section markers `01/02/03` (Plan.astro), recurring uppercase eyebrows/mono kickers despite DESIGN.md's "no eyebrow over every section", a 4-up icon/figure/label benefit grid (OfferLean) and 3-up team grid, a 138px hero-metric number with count-up (FloorStat), a top-stripe accent rule on hover (Engineer `eng__tile::before`), and aphoristic "statement + punchy negation" cadence repeated ~8x ("He didn't follow best practice. He wrote it.", "Proof, not promises.", "The smart operators don't guess. They measure."). No em dashes, no gradient text, no glassmorphism on content (brand rules honored there).

**The central finding — motion undercuts the trust thesis.** For a buyer defined by sales fatigue, the magnetic CTA that drifts toward the cursor (index.astro 111-130), 3D tilt cards that wobble in perspective (index.astro 70-87), ambient neon-teal/red parallax light blobs (index.astro 89-103), and count-up tickers everywhere all read as "vendor trying to dazzle me" — the exact pattern the audience scans to disqualify. DESIGN.md forbids animated number tickers by name (twice) and says "restraint signals competence here." The content is built for the skeptic; the surface signals the opposite.

**Deterministic scan (detect.mjs):** 3 findings, all corroborating the review.
- `single-font` — Base.astro: only Hanken Grotesk is used. Agrees with the review's typography regression: `--font-serif` and `--font-sans` both resolve to Hanken (index.astro 64-65), so DESIGN.md's defining "serif headlines + humanist sans body" contrast axis is silently gone. Newsreader is imported but unused.
- `layout-transition` — CtaPair.astro:129 (`transition: max-height, margin-top`) and Plan.astro:93 (`transition: height`). Animating layout properties; janky on the expand-in-place disclosures. The review flagged the expand behavior but not its perf cost, so the detector adds value here.
- No false positives.

**Visual overlays:** Not available. Two screenshot attempts against the running preview timed out with no console errors — the renderer never reaches an idle state, which is itself consistent with the always-on motion (count-ups, parallax, auto-loops, and the 480vh scroll scene running continuously). No reliable user-visible overlay was produced; this is the fallback signal, not an injected overlay.

## Overall Impression

The thinking behind this page is genuinely good. The StoryBrand spine, the floor-first honesty, the calculator with shown math, and the volunteered limits in the footer are exactly right for a burned, skeptical operator. The problem is that the **surface performs against its own message.** A brand whose entire promise is "rigorous, understated, we have nothing to inflate" shipped a page that inflates — count-ups, a cursor-chasing button, tilting cards, glowing ambient light, 14 sections of always-on motion. The single biggest opportunity is subtraction: strip the page down until the surface is as honest and quiet as the content already is.

## What's Working

1. **Footer "How to read this page" methodology note (Footer.astro 31-41).** Volunteers the limits and explains why measurement happens before commitment. The most on-brand element on the page.
2. **The Estimator (Estimator.astro).** A real, spec-conformant calculator with shown math, a per-step ledger, floor-vs-ceiling range, and an honest "Not a quote" disclaimer. Treats complexity as the firm's competence, not the operator's homework.
3. **Floor-first, unit-honest proof (Proof.astro 13-64).** Real verifiers named, kWh vs kW demand distinguished, a 9-19% range left deliberately un-count-upped. Textbook "understate to earn trust."

## Priority Issues

**[P0] Remove the magnetic/drift CTA and 3D tilt — they break the trust thesis.**
- Why it matters: A button that chases the cursor and cards that wobble read as eager salesmanship to a buyer whose entire mindset is disqualifying salesmanship. Directly contradicts PRODUCT.md ("burned by vendors") and DESIGN.md ("restraint signals competence"). Highest leverage: a few CSS/JS blocks defeating the brand's core promise.
- Fix: Delete the magnetic-CTA transform/sheen (index.astro 111-130) and the tilt selectors + JS (index.astro 70-87, Base.astro tilt driver). Keep one restrained hover: `translateY(-2px)` plus the soft gold glow at rest.
- Suggested command: /impeccable quieter

**[P1] Kill the count-up tickers (explicit, named anti-reference).**
- Why it matters: DESIGN.md names "animated number tickers" as forbidden twice. They make every figure feel sold rather than measured — the inverse of the rigor positioning. The 20% floor and the proof figures are more credible sitting still.
- Fix: Remove the `[data-countup]` driver (Base.astro) or gate it off; render the static figures that already exist as default text.
- Suggested command: /impeccable quieter

**[P1] Repeat the risk-reversal guarantee at the booking moment.**
- Why it matters: Conversion happens at FinalCta, but the mint "verify first, commit after / diagnosis is on us / nothing owed until proven" promise lives hundreds of pixels away in OfferLean/Plan. Burned buyers commit only when the risk-reversal is adjacent to the action.
- Fix: Add the mint guarantee block directly above CtaPair in FinalCta.astro, framed as the one calm promise. Also re-sacralize mint (it currently appears on ~6 unrelated positive accents, diluting its meaning).
- Suggested command: /impeccable clarify

**[P2] Cut/collapse sections; implement the real two-door IA.**
- Why it matters: 14 always-on sections fail 5/8 cognitive-load checks and dilute the CTA. The spec wants a simple linear default with optional depth ("show me the method"), not forced inline depth.
- Fix: Collapse method-grade depth (HvacLean's solution menu, parts of Engineer's carousel, the Harmonizer mechanism) behind expandable panels. Target a default scroll of ~7-8 sections. Drop the 01/02/03 markers in Plan.astro.
- Suggested command: /impeccable distill

**[P2] Fix the typography contrast-axis regression and dead styles.**
- Why it matters: DESIGN.md's defining type decision is "elegant serif headlines + humanist sans body." As shipped both tokens resolve to Hanken Grotesk, so every headline is sans — the brand's "one considered solution, not SaaS monoculture" signal is gone. Confirmed by the detector's `single-font` finding. Dead styles (`.eng__eyebrow`, `.eng__btn`, unused clock branches) signal unfinished work.
- Fix: Restore a real serif for h1-h3 (Newsreader is already imported but unused). Remove unreferenced style blocks.
- Suggested command: /impeccable typeset

## Persona Red Flags

**Jordan (first-timer):** Lands in a hero with a crosshair cursor and an auto-running scan demo; may not realize the lens follows the mouse. The single most important fact ("the diagnosis is on us, costs nothing") is buried in section 2's mint panel, not in the hero chips. May bounce before learning it's free to find out.

**Riley (stress tester):** Two CTA systems behave differently (header anchor-jump vs in-place expand). Auto-rotating carousels (Engineer 15s, Proof 5s) shift content mid-read. The Google booking iframe has no failure state. Tilt/magnetic/count-up read as marketing theater to a substance-seeker. The calculator, by contrast, wins Riley over — the most stress-test-resilient element.

**Casey (distracted mobile):** Fine-pointer motion is correctly disabled on coarse pointers (good). But the page is very long on mobile — 14 sections plus a 480vh scroll-jacked sticky scene (Harmonizer) — and the header CTA is hidden <720px, so Casey scrolls a long way between booking opportunities. Needs a sticky mobile CTA most of all.

**The burned skeptic operator (project persona):** This is who the motion fails hardest. Every drifting button, wobbling card, glowing blob, and counting number reads as "vendor trying to dazzle me" — the exact pattern they scan to reject. The content is built precisely for them; the surface signals the opposite. They may disqualify on vibe before reading the substance that would convince them.

## Minor Observations

- `theme-color` meta is `#081710` (forest green from the old theme), mismatched to the shipped graphite `#141a1e`.
- Skip-link uses navy `#0a1422` on teal `--gold` (#1f8390) — a holdover; verify contrast.
- Proof.astro carries a live `MOCK categories for layout testing only` comment (lines 5-7); placeholder data may be shipped.
- `--mint` is no longer "sacred" — it appears on Offer promise, Problem check, Success column, Harmonizer, calculator dial, and the text-founder button.
- FloorStat's only `<h2>` is `visually-hidden`, so the 20% figure floats without a visible titled context.
- The shipped theme (graphite/teal "Mix") has diverged from DESIGN.md (navy/gold/mint). DESIGN.md is now stale relative to production.

## Questions to Consider

1. If "verification is the offer," why does the page perform so much? What would it look like if you trusted the content to carry it — no count-ups, no tilt, no magnetic button — and is that version more or less convincing to someone who's been lied to before?
2. Is the cursor-chasing "Book" button the most off-brand single element you could have shipped for a buyer defined by sales fatigue? What does it say that it survived to production?
3. You wrote the perfect closing argument (the Footer "How to read this page" note) and hid it in muted gray below the fold. If that paragraph is the truest expression of the brand, why isn't it the hero?
