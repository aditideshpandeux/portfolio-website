# Aditi Deshpande — Portfolio site

Project context for Claude Code. Read this fully before making changes. This is a personal portfolio for a senior product designer (10 years experience), built to replace an existing Adobe Portfolio site that had a high bounce rate (under 30 seconds on average).

## Goal

Get great job offers. The site is judged by: delight/craft (Aditi is a UX designer, will be judged by other designers), information architecture, and concise, accurate info about real projects. NOT judged by visual flash for its own sake.

## The core concept: "the unscramble"

Aditi's actual design philosophy: she makes complexity disappear before the user has to deal with it (Rubik's cube analogy, Naoto Fukasawa's "Super Normal"). Her actual logo is a Rubik's cube reoriented so one face (red) reads as a UI screen, and the other faces represent backend/business requirements/implementation — the parts that have to "line up" behind the UI.

The site's visual thread: things start visually scrambled/dense, then resolve into clarity as the user scrolls or interacts. This isn't decoration — it mirrors her actual work (15 min manual process → 10 sec automated; multi-screen config → one unified flow). Every "delight" moment should tie back to this idea, not be a separate gimmick.

The hook on the homepage should use the actual cube logo rotating from a scrambled/mismatched-faces state into the aligned state shown in the real logo — not generic placeholder tiles (a placeholder tile version exists in the mockup below; swap in the real cube when building).

## No-fabrication rule (critical)

Aditi has a strict personal principle: no embellished titles, metrics, or skills. Every claim must be traceable to her actual career documents. Do not invent numbers, baselines, or details not explicitly confirmed by her. If a case study has a content gap, leave a clearly marked placeholder rather than inventing plausible-sounding detail.

## NDA constraint — important

Aditi cannot show actual screens/UI from her Pega (enterprise employer) projects. For all Pega case studies (Fingerprinting, Cloud Secret Sync, OCPM, ABAC+RBAC):
- No real screenshots, no recreated UI that resembles the real product's visual design.
- Use abstract schematic diagrams instead — boxes/arrows/shapes showing the *structure* of the problem (e.g. "5 disconnected screens, each requiring manual re-entry") resolving into the *structure* of the solution (e.g. "1 contextual flow"). Plain shapes, no branding, no real UI chrome.
- Generic, rebuilt-from-scratch component demos are fine if illustrating an interaction pattern, as long as they don't resemble Pega's actual visual design.
- Process artifacts (journey maps, decision rationale, annotated diagrams) are fine and encouraged — these communicate the thinking, which is the more senior thing to show anyway.
- Personal/independent projects (Conversational AI Chatbot, Knowbility AIR 2024, Allowcents, Washeroma, Open Happiness) have NO NDA constraint — real visuals are fine for these.

## Aditi's voice — use this for ALL copy

Reference doc, "Aditi's Voice — Style Reference":

**Core character:** Intellectually confident but never performing it. Says the thing directly. Doesn't use big words to sound more sincere. Doesn't over-explain. Trusts the reader to get it.

**Rules:**
- Short, clean sentences that land. Not run-ons, not over-qualified.
- Casual connectors, not formal transitions. ("it frees up time for…" not "which consequently allows…")
- Names things plainly. ("my primary job" not "core responsibilities")
- No throat-clearing. No context-setting preamble. Gets to the point.
- No performative sincerity. Avoid: "my practice has evolved," "I am passionate about," "I bring a unique perspective."

**Reference sample (her own words, use as baseline):**
> "I've moved past designing screens in Figma or similar tools. I now vibe code UI, and am able to devote more time for my primary job — understanding the users and use cases, thinking through solutions with devs, PMs, testers, and designers. I'm looking to be somewhere that works this way, or wants to."

## Tech stack

- Plain HTML, CSS, and vanilla JS. No framework (React/Next.js not needed at this scale).
- No animation library (GSAP/AOS) — native CSS transitions/keyframes + `IntersectionObserver` for scroll-triggered reveals covers everything designed so far.
- Optional: one Google Font if system fonts aren't enough for editorial/thesis moments.

## Hosting & deployment

- GitHub repo → Netlify, connected for auto-deploy on push.
- Free tier covers this comfortably. HTTPS automatic.
- Custom domain is optional and can be added later without any rebuild — just a DNS change pointed at the same Netlify site. Decision deferred for now; building on the free `*.netlify.app` subdomain to start.
- Google Analytics (GA4) to be added via script tag in `<head>` of every page — needed to actually measure the bounce-rate problem this whole rebuild is meant to fix.

## Site structure (sitemap)

```
Home
├── Work (index)
│   ├── Case study: Fingerprinting (Pega) — schematic only, no screenshots
│   ├── Case study: Cloud Secret Sync (Pega) — schematic only
│   ├── Case study: OCPM / Process & Task Mining (Pega) — schematic only
│   ├── Case study: ABAC+RBAC Security (Pega) — optional 4th, schematic only
│   └── Explorations (personal/independent projects — real visuals OK)
│       ├── Conversational AI Chatbot
│       ├── Knowbility AIR 2024
│       ├── Allowcents
│       └── Washeroma / Open Happiness
├── About
└── Writing (index + article template — build structure now even with zero articles; should be a 5-minute job to add a new one later)
```

Footer (every page): email, LinkedIn, resume download link.

## Home page — section breakdown

1. **Hook + thesis (merged into one moment).** The cube logo unscrambles/resolves, then the hero line appears: settle on "Aditi Deshpande." first, then second clause fades in right after.
2. **Proof strip.** Single scannable row, directly under the hero line.
3. **Work selector.** Project cards framed with the puzzle/unscramble motif — hover triggers a small "shard" elements shifting into alignment (see mockup code below); click transitions into the case study.

## LOCKED CONTENT — do not alter without Aditi's explicit input

**Hero line (final):**
> Aditi Deshpande. I unscramble software so it makes sense to the people using it.

**Proof strip (final):**
> 10 years · 15 min → 10 sec · 2× Spot Award · M.Des, IISc

(Note: 15 min → 10 sec refers to the cloud secret sync project, reducing setup time per item. The "~75% reduction in design-to-dev cycle" metric exists in source docs but is flagged as unverified/unconfirmed baseline — do NOT use it anywhere until Aditi explicitly confirms it.)

## Case study template (apply to every project)

1. Header — project name, company, role, timeframe, tools
2. TL;DR — 2-3 lines, problem + outcome, before anything else
3. Context — what the product/team was, who used it
4. Problem — the specific pain point
5. Process — approach, key decisions, constraints navigated
6. Solution — for Pega projects: schematic "tangle → resolved" diagram with captions, NOT screenshots. For personal projects: real visuals OK.
7. Outcome — the metric, stated plainly
8. Link to next case study

## Fingerprinting case study — LOCKED, ready to build

> **TL;DR:** Process analysts used to spend close to two months manually piecing together how a department actually worked — tweak by tweak, person by person — before they could call it "the process." I turned a raw pattern-detection algorithm into a feature that does that in moments. Spot Award.
>
> **Context:** The starting point was an algorithm out of Pega's Process & Task Mining suite — it read screen-level activity data and flagged clusters of screens that looked like a task. That's all it did: groups of screens, no framing, no way for anyone to act on it. Used by process analysts, ops managers, and sometimes department heads — anyone trying to understand how a department's workflow actually runs, versus how it's documented to run.
>
> **Problem:** Before this, understanding a department's real process meant manual reconstruction: talking to people, watching how work actually got done, noticing each person's individual tweak on the "official" process, then working out the broad pattern underneath all those variations. For a sizeable department, that could take close to two months. One process analyst told Aditi directly it saved his team weeks. (Note: any specific department example used to illustrate scale, e.g. "loan applications," is illustrative only — not a real client detail. Keep illustrative examples clearly generic if used at all.)
>
> **Process:** Aditi was handed the algorithm's raw output — clusters of screens it flagged as a likely task, nothing else. The real design problem was turning that into something a process analyst would actually trust and act on: what to surface, how to frame a detected pattern, how much of the algorithm's reasoning to show versus hide. She worked closely with the product manager and the architect who held the patent on the algorithm — brought designs to them, took feedback, iterated. The design team's reviews shaped a lot of the refinement too.
>
> **Solution (schematic, not a screenshot):** Before: a tangle of individual habits and workarounds across a whole department, manually cross-referenced by hand. After: the algorithm's output surfaced as a single, clear suggestion.
>
> **Outcome:** Tested directly with 6 client-side process and senior analysts — each given the prototype and asked to complete tasks on their own. From first concept to VP buy-in to client testing permission to running the sessions: about 2.5 months. Spot Award.

## ABAC+RBAC Security case study — LOCKED, ready to build

> **TL;DR:** Pega's authorization setup forced two completely different security models — role-based and attribute-based — into separate, disconnected flows. Aditi combined them into one. Validated as workable by security leadership and the architects who'd actually have to build it. Never got prioritized for implementation — that's the honest ending, not a launch story.
>
> **Context:** Meant for citizen developers — but realistically, configuring authorization needs someone who already understands the basics of access control.
>
> **Problem:** A heuristic review of the existing flow found flexibility built in at the cost of friction. The system used Pega-specific terms instead of language people already knew, so there was nothing to recognize, only things to learn. Settings had to be held in memory while switching tabs, because nothing surfaced what had already been configured. The interface wasn't built for anyone without deep familiarity — dense rows, horizontal scroll, no clear path through it. Even the documentation didn't help.
>
> **Process:** Aditi didn't have direct access to the people who'd actually configure this at client companies, so she went to the next best source: solution architects, who build these systems for clients and see where people get stuck firsthand. They gave her real use cases and flagged where users would likely struggle. Once she understood both paradigms well enough to combine them, she ran a workshop with the Security stream director and the project owner, specifically to show ABAC and RBAC could be merged into one model instead of staying two separate systems. From there, iteration went the same way Fingerprinting did — design reviews with the PO and architect, feedback folded back in. Total time: about 3 months overall (roughly 1 month for heuristic analysis, research, architect calls, and design iteration specifically).
>
> **Solution (schematic, not a screenshot):** Two moves, not one. (1) Authorization configuration was pulled out of its own disconnected area and folded directly into the main flow of building a case type in Launchpad — no separate detour required. (2) One view was built where role-based and attribute-based rules could be created together instead of separately — so a rule like "tier 2 service specialists get elevated rights, and cases from a given location route to specialists in that location" becomes one configuration, not two systems to reconcile by hand.
>
> **Outcome:** Validated as workable and implementable through the workshop and ongoing architect feedback — but it didn't get prioritized for build. The concept proved two incompatible models could become one; that part held up. It just didn't ship. State this plainly in the case study — do not spin it as a launch or imply it shipped.

## Verified facts available for use (from career docs — safe to cite)

- 10 years in product design; Pegasystems (2022–present), Illumine Foundation (2021–2022), Expert Global Solutions (2016–2020), Cerebrum LLP (2020–2021), Exalt Design (2014–2016)
- M.Des, IISc Bengaluru (2012–2014); B.Arch, MIT Aurangabad (2005–2012)
- 2× Spot Award (Fingerprinting; AI-augmented design workflows/playbook — published as Pega's internal AI onboarding resource), Team Splash Award (Launchpad Boosters), GenAI Hackathon Finalist (Pega-wide)
- Cloud secret sync: 15 min → 10 sec per item; 50% effort reduction; eliminated recurring outages
- OCPM design recognized in Pega's internal Gartner review
- Karmayogi (Illumine Foundation): national skilling platform, 100,000+ government employees, web + mobile, low-bandwidth optimized
- EGS: Machine Talk manufacturing platform launched at Coca-Cola; IoT monitoring for Alliance Laundry
- EGS job title was "UX Specialist," not "Lead UX Designer" — do not use the latter anywhere

## Homepage mockup — working starting code

This HTML/CSS/JS approximates the hook → thesis → proof strip → work selector sequence. It was tested as a widget mockup; treat it as a structural starting point, not final code — swap the placeholder tile grid for the actual cube logo animation, and reconnect the copy to the locked content above.

```html
<style>
@keyframes settle{from{opacity:.5}to{opacity:1;transform:translate(0,0) rotate(0deg)}}
@keyframes fadein{from{opacity:0;transform:translateY(6px)}to{opacity:1;transform:translateY(0)}}
@media (prefers-reduced-motion: reduce){.tile,.thesis-word{animation:none!important;opacity:1!important;transform:none!important}}
.tile{position:absolute;width:34px;height:34px;border-radius:8px;background:#f1efe8;border:0.5px solid #d3d1c7;animation:settle .9s cubic-bezier(.2,.8,.2,1) both}
.thesis-word{display:inline-block;animation:fadein .5s ease both}
.card{position:relative;background:#fff;border:0.5px solid #d3d1c7;border-radius:12px;padding:1rem 1.1rem;overflow:hidden}
.shard{position:absolute;width:9px;height:9px;border-radius:2px;background:#888780;transition:transform .35s ease,opacity .35s ease}
.card:hover .shard{transform:translate(0,0) rotate(0deg)!important}
.card:hover .open{opacity:1;transform:translateX(0)}
.open{opacity:0;transform:translateX(-4px);transition:opacity .25s ease,transform .25s ease;font-size:13px}
</style>
<!-- Replace this tile grid with the real cube logo unscramble animation -->
<!-- Hero text should read: "Aditi Deshpande." then fade in "I unscramble software so it makes sense to the people using it." -->
<!-- Proof strip: 10 years · 15 min -> 10 sec · 2x Spot Award · M.Des, IISc -->
<!-- Work selector cards: hover triggers .shard elements aligning (see .card:hover rule above) -->
```

(Full original mockup with all tile/card markup can be regenerated on request — this is the reusable CSS logic, the actual markup should be rebuilt cleanly as real project files, not copy-pasted from a chat mockup.)

## Build order (phases)

0. Foundation: file structure, shared CSS, shared header/footer, placeholder page pushed to GitHub + Netlify to confirm deploy pipeline works.
1. Home page: hook/thesis/proof strip/work selector, using locked content above.
2. Case study template: build using Fingerprinting (now locked, see above).
3. ABAC+RBAC case study (now locked, see above) — reuse template.
4. Remaining case studies if pursued later: Cloud Secret Sync, OCPM — not yet drafted, lower priority for now.
5. Work index + Explorations section.
6. About page: bio, full philosophy paragraph, skills snapshot, resume link.
7. Writing index + article template (structure only, can be empty).
8. Google Analytics script across all pages, mobile check, ship.
9. Ongoing: add articles, revisit based on Analytics data.

## Illustration assets — hero images per case study

Aditi is generating mood/hero illustrations via ChatGPT (flat editorial style, cream background #FAFAF8, vermillion accent #C1391D, no text in image, no real UI). These are a *mood layer* sitting above the precise structural diagrams below — not a replacement for them. Use one hero illustration per case study section, with the precise diagram still doing the actual explaining underneath it.

Files will be added to `assets/illustrations/` with these working titles (as named by Aditi):
1. "Fingerprinting — before" → Fingerprinting case study, before-state (manual loop)
2. "Fingerprinting — the design move" → Fingerprinting case study, design-move illustration
3. "ABAC+RBAC — before" → disconnected panels
4. "ABAC+RBAC — after" → unified panels
5. "ABAC+RBAC — the workflow blend" → ribbon weaving through nodes

Note for Claude Code: these filenames likely contain spaces and an em dash, which break cleanly in file paths/URLs on case-sensitive hosts like Netlify. Rename to kebab-case slugs when wiring into HTML (e.g. `fingerprinting-before.png`, `fingerprinting-design-move.png`, `abac-rbac-before.png`, `abac-rbac-after.png`, `abac-rbac-workflow-blend.png`) and confirm the mapping above still holds. Add descriptive alt text for each — these are decorative-but-meaningful, not pure decoration, so alt text should describe what the image conveys (e.g. "Illustration of a figure looping repeatedly through scattered fragments, representing the manual two-month discovery process").

## Locked structural diagrams — rebuild these as real SVG in the project

These were finalized as content/structure (built and approved as mockups) and should be recreated as clean, accessible SVG files in the project, using the homepage's existing color tokens (`--accent: #C1391D`, `--cube-face`, `--cube-edge`, `--ink`, etc.) rather than a separate palette:

**Fingerprinting — before (the manual loop):** four-step vertical flow, single direction, with a "repeats" note below, not drawn as an actual ring:
1. Talk to people — how do you do this work?
2. Watch the work happen — see the real routine
3. Spot individual tweaks — everyone does it differently
4. Guess the shared pattern — piece it into one process
Caption below: "repeats per department, ~2 months each"

**Fingerprinting — the design move (raw output → usable suggestion):** four-step vertical flow, first node visually distinct (neutral/structural) from the remaining three (the designed layers):
1. Raw algorithm output — clusters of screens, unlabeled (neutral/structural styling)
2. Suggested workflows list — ranked, plain language
3. Expand one workflow — see why it was flagged
4. Confirm or dismiss — narrows to the one that fits
Caption below: "progressive disclosure: detail unfolds only when asked for"

**Fingerprinting — usability outcome:** six small markers in a row, four styled as one category (completed unprompted), one as a second category (needed a nudge), one as a third (didn't finish), with a short legend:
- 4 of 6 completed without prompting
- 1 needed a small nudge
- 1 didn't finish — different role focus (a call-center participant evaluating a tool built for process analysts — note this plainly in the case study text, don't gloss over it)

**Unified Authorization — before/after (v2, replaces earlier simplified version, supersedes the separate "workflow blend" diagram entirely — this pair now covers that ground too, no third diagram needed):**

*Before — LOCKED, the disjointed journey version (replaces the earlier static scattered version, which is no longer used):* five separate pieces (Case type, Permissions, Access role, Access groups, Conditional access/ABAC), scattered and slightly rotated to suggest disorder, connected by 5 dashed arrows in a deliberately non-sequential, crossing pattern — each arrow goes to a non-adjacent box, so the lines cross each other multiple times, showing a tangled path rather than one clean route. This is richer than a static "things sit separately" diagram — it shows the lived experience of hopping between them, not just where they live. Caption: "one task, five places to visit — none of them line up."

Pieces, for reference:
1. Case type
2. Permissions
3. Access role (permissions get attached here)
4. Access groups (access role gets attached here)
5. Conditional access (ABAC) — built entirely separately

*After:* one outer dashed container labeled "building a case type — one flow," containing three connected steps inside the same container:
1. Define the case — subtitle: "the basic unit of work" (case type is the unit of thinking for large applications)
2. Author permissions — subtitle: "and conditional access, inline" (ABAC/conditional access happens as part of the same authoring step, no separate process)
3. Access role & groups — subtitle: "assembled automatically"
Below the container, two checkmark callout lines:
- "✓ advanced users can still configure any piece on its own" (flexibility is preserved, not removed — this is about removing forced separation, not removing options)
- "✓ one view shows everything configured for access" (no jumping between rules to understand what's been set up)

**Build note — line/arrow visibility:** for any free-floating connecting line or arrow (not a box border), use an explicit, sufficiently dark stroke color (e.g. equivalent to --ink-soft or darker, not --line-soft or --cube-edge) — the lighter border-tone grays used for box outlines are too subtle and can disappear against the cream background when used for a standalone line. This came up directly while testing Version B above.

This is the most NDA-safe version of the story Aditi can tell — it describes the structural shift (5 disjointed pieces → 1 authored flow with automatic assembly) without revealing any actual screen design.

## Homepage layout — drama direction (LOCKED v2 — supersedes earlier scramble/skew version below)

The initial homepage build was structurally flat — everything centered, uniform spacing, no shift in rhythm or scale between sections. An earlier round of this section called for a scattered scramble animation and skewed 3D panels (see superseded notes at the bottom of this section, kept for context only) — that direction is now replaced by the sharper version below, after reviewing actual screenshots of two reference sites. **Build this version, not the scramble/skew one.**

**Reference sites — specific visual moves being borrowed (structural inspiration only, not visual copies):**
- lolajiang.com: a soft atmospheric color wash behind the hero (gradient, not flat color); hero text positioned off-center (not centered horizontally or vertically) with a thin vertical accent line beside the text block instead of a border or box; generous negative space; case study visuals sit in a soft rounded card offset beside text, not full-bleed under it.
- kudos.framer.media: faint dotted grid lines running down the page as a structural decorative device; a massive ghosted/watermark-scale wordmark used once as a transition layer between two sections (not as content, not repeated); small monospace "eyebrow" labels before section headers; only part of a headline colored with the accent, not the whole line; hard alternation between two background tones as the pacing device between sections.

**Locked direction for the homepage (homepage only — case study pages stay calm, see below):**

1. **Atmospheric wash behind the hero only.** A soft gradient using the existing cream background fading very subtly into a low-opacity vermillion blush (not a flat color, not full accent strength) — replaces the earlier "scrambled tiles" hook entirely. Quieter and more sophisticated, and less likely to read as a generic AI-generated effect.
2. **Off-center hero text.** Name + thesis line positioned off-center (not centered horizontally or vertically in the viewport), with a thin vertical line (1px, --line-soft or accent color) beside the text block. Generous whitespace around it.
3. **One oversized ghosted wordmark or cube glyph as a single section transition.** Used once, between the hero and the work selector (or wherever it reads best) — not repeated, not used as a background texture everywhere.
4. **Faint dotted grid lines running down the page**, full height, low opacity — a structural decorative device, not functional grid content.
5. **Alternating background tone between sections** (cream / a slightly warmer or darker panel tone from the existing palette) as the primary rhythm-break device — replaces the earlier "skewed 3D panels" idea, much more reliable to build cleanly and closer to what was actually liked in the references.
6. **Color only one word within the thesis line** in vermillion, not the full sentence — small, cheap, effective contrast move.
7. **Small monospace "eyebrow" label above section headers** (e.g. "+ selected work" above the work selector) for editorial rhythm — optional, low-cost addition if time allows.

**What does NOT change:** case study pages stay simple, calm, and content-dense — finesse of information architecture and a few well-chosen colors from the established palette, not drama. The drama is homepage-only.

**Superseded — do not build:** the original version of this section called for (a) the opening viewport starting genuinely scrambled with name/thesis/proof-strip scattered at random sizes/rotations before snapping into place, and (b) section backgrounds carrying a slight 3D skew suggesting cube facets. Both are replaced by points 1–7 above. Kept here only so Claude Code doesn't reintroduce them from earlier context.

## Process note for this build

Clear division of labor, as of this point in the project:
- **Content, copy, and diagrams** — decided and built in chat with Claude (claude.ai). This includes case study text, hero/proof-strip copy, structural diagrams, illustration prompts/critique, naming decisions.
- **Layout, color, and other visual styling** — implemented directly in VSCode with Claude Code. This includes CSS, page structure, responsive behavior, color palette changes, animation/motion implementation.

Either way, any decision that should persist gets written into this file. If a layout/color decision made in VSCode should be known going forward (e.g. a palette change, a new component pattern), bring it back here so this file stays the single source of truth — don't let decisions live only in one place or the other.

## Homepage work selector — FINAL lineup (LOCKED)

Down to two case studies only, per the 2-day deadline decision — Cloud Secret Sync and OCPM are fully removed from the homepage selector (not just deprioritized in the backlog, actually removed from the `.card-grid`). Grid should be 2 columns, not 3, when there are only 2 cards — adjust `.card-grid` accordingly (3-column grid with 2 items looks unbalanced/incomplete).

1. **Fingerprinting** — outcome line: "Manual discovery → instant suggestions" — `href="case-studies/fingerprinting.html"`
2. **Unified authorization** (final title for the ABAC+RBAC case study — "ABAC+RBAC" is internal jargon, not used anywhere in visible copy) — outcome line: "Two access models, combined into one" — `href="case-studies/unified-authorization.html"`

## Build-quality note: extract shared design tokens

The current `index.html` has all design tokens (`--accent`, `--paper`, `--ink`, etc.) and base styles embedded in its own `<style>` block. Before building case study pages, extract the shared `:root` tokens, base resets, and any reusable classes (`.card`, `a:focus-visible`, etc.) into a shared stylesheet (e.g. `assets/styles.css`), linked from every page. Page-specific styles (hero layout, case-study-specific layout) can stay in a per-page `<style>` block or a second linked file. Avoids drift between pages as the site grows past two.

## Fingerprinting illustration — in use

One ChatGPT-generated illustration was approved: a figure walking a winding, footprint-marked path through towering, scattered browser-window panels and red-tabbed sticky notes, looking down, small relative to the clutter. This maps directly to the "Fingerprinting — before" slot (the two-month manual loop) — use this image there. The "Fingerprinting — the design move" image (funnel of shapes resolving into one glowing accent-colored rectangle) was also approved as usable, can go in that slot if Aditi confirms, or be sharpened further on request.

ABAC+RBAC illustrations (before/after/workflow-blend) were not approved — the generated versions were too generic/symmetric (flat unrelated shapes, no accent color, no sense of motion or convergence). Revised prompts were written emphasizing asymmetry, traceable before/after fragments, and accent color presence — but no final images exist yet. Build the Unified Authorization case study using the locked structural diagrams only for now; illustrations can be added later without restructuring the page.

## Illustration generation — style anchor and lessons learned

Illustrations are generated externally via ChatGPT, not by Claude/Claude Code. If asked to help refine prompts for future illustrations (e.g. for Unified Authorization, or future case studies), use this anchor and these lessons.

**Style anchor — paste before every illustration prompt:**
> Flat, minimalist editorial illustration. Warm cream background (#FAFAF8). One accent color: a deep vermillion red (#C1391D). Supporting tones in muted warm gray. Clean geometric shapes, no gradients, no photorealism, no text or labels anywhere in the image, no real software UI of any kind.

**Lessons learned from reviewing generated images:**
- **Specificity beats a vague style description.** A prompt describing the *exact scene* (e.g. "a figure walking a winding, footprint-marked path through towering, scattered browser-window panels and red-tabbed sticky notes, looking down, small relative to the clutter") produces something genuinely specific to the story. A vague prompt ("a person navigating complexity") produces generic stock-illustration output even with the same style anchor attached.
- **Asymmetry reads as process; symmetry reads as decoration.** A perfectly symmetric arrangement (e.g. a 6-way mandala/hexagon) looks like a static logo or pattern, not "two things resolving into one." Asymmetric, slightly imperfect compositions read as something actively happening.
- **The accent color must be present and meaningful, not absent.** A generated image with zero vermillion anywhere doesn't feel like it belongs to this brand, no matter how well it matches the style anchor's described palette.
- **Before/after pairs need traceable continuity.** If two images are meant to be a before/after pair (e.g. ABAC+RBAC before/after), the same elements (same four fragments, same shapes) should be visibly present in both, just rearranged/resolved — not two unrelated compositions that happen to share a color palette.

**Status of illustrations as of this point:**
- Fingerprinting — before (the manual loop): APPROVED, in use (see "Fingerprinting illustration — in use" above)
- Fingerprinting — the design move (funnel resolving to one glowing rectangle): approved as usable, not yet confirmed for final placement
- ABAC+RBAC (Unified Authorization) — before/after/workflow blend: NOT approved, regenerate using the lessons above. First attempts were too generic/symmetric/missing accent color.

## Open items / decisions still pending

- Custom domain decision — deferred, not blocking launch.
- Cloud Secret Sync, OCPM case study content — not yet drafted, not currently prioritized (ABAC+RBAC and Fingerprinting are the two case studies being built first).
- About page copy — not yet drafted.
- Explorations section copy — not yet drafted (source material exists in portfolio project pages, currently thin/unfinished — see uxbyaditi.myportfolio.com for what exists now, much of it needs real rewriting, not just porting over).
- Schematic diagrams for both locked case studies (Fingerprinting "tangle → single suggestion"; ABAC+RBAC "two disconnected systems → one unified view") — content is locked, visuals not yet built.
- Adobe Portfolio site (old site, still live) has a placeholder line added: "This site has officially reached legacy status. A new one's in progress." with a note that enterprise case studies are NDA-bound. A link to the new site should be added below that line once it's live.
