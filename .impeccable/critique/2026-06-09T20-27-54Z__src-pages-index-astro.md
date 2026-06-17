---
target: the landing page (src/pages/index.astro)
total_score: 31
p0_count: 0
p1_count: 2
timestamp: 2026-06-09T20-27-54Z
slug: src-pages-index-astro
---
## Design Health Score

| # | Heuristic | Score | Key Issue |
|---|-----------|-------|-----------|
| 1 | Visibility of System Status | 3 | Calculator gives live feedback; no scrollspy/active nav state |
| 2 | Match System / Real World | 4 | Plain declarative voice; jargon (power factor, THD) explained inline |
| 3 | User Control and Freedom | 3 | Free scroll + anchor nav; calculator easily reset |
| 4 | Consistency and Standards | 3 | Strong system, but floor table shows `[X]%` while calculator shows a concrete `11.0%` |
| 5 | Error Prevention | 3 | Sliders constrain input; primary CTA is a placeholder anchor |
| 6 | Recognition Rather Than Recall | 3 | Labeled nav, no memory load |
| 7 | Flexibility and Efficiency | 3 | Landing page; two hero CTAs + anchor nav, no accelerators needed |
| 8 | Aesthetic and Minimalist Design | 3 | Restrained and clean, but uppercase tracked eyebrow on ~9 of 12 sections adds scaffolding |
| 9 | Error Recovery | 3 | Minimal error surface; nothing broken |
| 10 | Help and Documentation | 3 | Inline explanations + calculator hint |
| **Total** | | **31/40** | **Good** |

## Anti-Patterns Verdict

**LLM assessment:** This does NOT read as obviously AI-generated. The dark drenched-navy palette, serif+mono pairing, rationed gold, and mint reserved for the reversal beat are committed, specific choices. No gradient text, no hero-metric template, no identical card-grid spine. The one real slop tell is the **tracked uppercase eyebrow repeated on nearly every section** ("Why we exist," "The threat, made physical," "Proof," "We quote the floor," "Model your own floor," "Where the number comes from," "The plan"). That cadence is exactly the AI grammar the rule warns against; one or two deliberate kickers is voice, nine is scaffolding.

**Deterministic scan:** `detect.mjs` on `src/` = clean. On built `dist/index.html` = 1 finding: `numbered-section-markers` (01, 02, 03). These come from the Plan section, which is a genuine ordered 3-step process, the one case the skill explicitly permits. The trailing "11" in the match is a false positive (the calculator's "11.0%"). Accept the Plan numbering as deliberate; no change required.

**Visual overlays:** Not available. No browser automation/screenshot in this environment, so responsive behavior and exact contrast are reasoned from source, not visually confirmed.

## Overall Impression

The narrative spine is the strength: villain → guide → authority → threat → reversal lands with real restraint, and the page looks like it was made by someone with a point of view, not a template. The single biggest opportunity is removing the eyebrow-on-every-section reflex, which is the one thing dragging it toward generic. Second: the calculator's concrete `11.0%`/`$16,500` output quietly undercuts the "we leave the floor blank on purpose" discipline the rest of the page works so hard to establish.

## What's Working

1. **Trust architecture.** The Cliff Suljak credential cards (sole-source DoD/DoE, $600M SRP) and the mint "we pay to find out" reversal are visually distinct and placed at the right emotional beats. The reversal earns its single use of mint.
2. **Voice-to-design congruence.** Plain, declarative copy paired with serif headlines and mono measurements makes the "rigor, not hype" claim feel true rather than asserted.
3. **Color discipline.** Gold is genuinely rationed to CTAs + one emphasis; mint appears only on the guarantee and the `$0`. This is the hardest thing to hold and it holds.

## Priority Issues

- **[P1] Eyebrow on nearly every section.** The tracked uppercase mono kicker appears on ~9 of 12 sections. **Why it matters:** it's the highest-signal AI tell on the page and flattens the section-to-section cadence the narrative wants. **Fix:** keep eyebrows on at most 1-2 sections where they do real work (e.g. the calculator), and vary the others (lead with the headline, or a single mono label as a brand device). **Command:** `/impeccable typeset` or `/impeccable quieter`.

- **[P1] Primary CTA is a placeholder anchor.** "Book a verified pilot" / "Book the conversation" both point to `#book`, which just scrolls to the final section; there is no actual booking mechanism. **Why it matters:** the entire page funnels to one action and that action currently does nothing. A skeptical operator who clicks and gets a scroll loses trust. **Fix:** wire to the real scheduling link/form (Calendly, HubSpot, etc.); until then it's the top conversion blocker. **Command:** `/impeccable harden`.

- **[P2] Calculator output contradicts the "floor left blank" discipline.** The floor table shows `[X]%` and the math step shows `[result]`, but the live calculator prints a precise `11.0%` and `$16,500`. **Why it matters:** an attentive operator notices the page refuses to commit to a number in one place while quoting one to the dollar in another, exactly the audience most likely to catch it. **Fix:** until the rate is locked, present the calculator result in a visibly provisional state (e.g. label it "representative rate" inline near the number, or show a banded "~$15-18k" range rather than a false-precise figure). **Command:** `/impeccable clarify`.

- **[P2] Muted-gray small text contrast risk.** Figure notes, the calculator hint, case-study meta, and several captions use `--muted (#8DA0B5)` at small sizes on the dark navy. **Why it matters:** muted on dark hovers near the 4.5:1 AA floor for body-sized text; the spec itself says muted is for large/secondary text only. **Fix:** verify each muted run against its background; bump sustained small copy toward `--body`/`--ink`. **Command:** `/impeccable audit` (or `colorize`).

- **[P3] Proof section is an empty placeholder.** Act Five is load-bearing per the copy, and currently carries `[finding]`/`[result]` tokens. **Why it matters:** the page's proof beat is hollow until a verified install sits here. **Fix:** user-owned content; replace with one real case study. Not a design defect, but the single biggest credibility gap.

## Persona Red Flags

**Jordan (First-Timer / skeptical GM):** The hero and reversal are clear, but Act Four opens straight into "power factor," "harmonic distortion," "service entrance." The copy does explain each inline, so Jordan survives, but the section *leads* with the jargon before the payoff. Watch that the technical density reads as "they handle this," not "homework."

**Riley (Stress Tester):** Clicks "Book a verified pilot" and gets a scroll, not a booking, the clearest broken-promise on the page. Calculator scales cleanly at min/max with no broken state (good), but slider position is not preserved on refresh (minor). The `.ph` placeholder tooltips reading "placeholder" on hover currently ship to real visitors, Riley will hover and see them.

**Casey (Distracted Mobile):** Layout collapses responsibly (calculator → 1 column at 800px, nav links hide under 720px leaving the CTA). Slider thumb is 20px, usable but under the 44px comfortable-target ideal. Primary CTA sits at the top of the page and bottom of each viewport-ish; no sticky mobile CTA, so on a long scroll Casey may lose the action between the hero and the close. Responsive behavior is reasoned from source, not visually confirmed.

## Minor Observations

- `.ph` hover label "placeholder" and the dotted underline are dev-facing but currently render for end users. Strip the class (not just the values) before publish.
- No scrollspy / active-section state in the sticky header; on a 12-section page a subtle active indicator would aid orientation.
- Consider a sticky or repeated mid-page CTA on mobile given the page length.

## Questions to Consider

- If the floor genuinely can't be quoted yet, should the calculator exist in its current precise form at all, or present as a clearly-bracketed "directional range" until the rate is locked?
- The eyebrows are doing labeling work the serif headlines already do, what does each section lose if its eyebrow is simply deleted?
- What's the real first action, scheduling link, short form, or email? That decision unblocks the page's entire purpose.
