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

**ABAC+RBAC — before/after comparison:** two-column layout.
Left ("before — four separate paths"): four disconnected boxes, slightly offset/rotated to suggest disorder, no connecting arrows: Build case type / RBAC settings / ABAC settings / Persona (auth profile). Caption: "configured separately, held in memory by the user."
Right ("after — one authoring flow"): the same four items, but RBAC settings + ABAC settings merged into one box, all aligned vertically and connected by arrows, enclosed in a single dashed outline labeled "one authoring flow." Caption: "one flow, nothing to hold in memory."

**ABAC+RBAC — the workflow blend:** still needs to be built (referenced by Aditi as "a diagram showing how authorization was blended naturally into workflow authoring" — distinct from the before/after comparison above, more about the seamless single journey than the contrast). Not yet finalized — build this with Aditi before finalizing the ABAC+RBAC page.

## Homepage layout — drama direction (LOCKED)

The initial homepage build was structurally flat — everything centered, uniform spacing, no shift in rhythm or scale between sections. Aditi found this boring. The fix is NOT more animation layered on top — it's structural: asymmetry, scale contrast, and the unscramble concept expressed at the layout level, not just in one small graphic.

**Reference points discussed** (structural cues only, not visual copies):
- lolajiang.com — case studies are password-gated (an "exclusive access" framing), each project leads with one punchy line before a full-bleed image, minimal nav, no throat-clearing.
- kudos.framer.media — bold agency energy, numbered indices, big stat counters, heavy motion. Too much for this site's content volume (2 case studies) — borrow the confidence, not the density.

**Locked direction for the homepage specifically** (case study pages stay calm — see below, this drama is homepage-only):

1. **The opening viewport starts genuinely scrambled, structurally — not just a small tile graphic.** Name, thesis line, and proof-strip numbers all scattered at different sizes/rotations/positions across the full screen on load. After a beat (or on first scroll), everything snaps into the calm, aligned layout that holds for the rest of the page. This is the unscramble concept expressed as the actual layout, not a decoration sitting on top of a normal layout.

2. **Real asymmetry — break the center-everything habit.** Name pushed hard to one side, oversized, allowed to bleed off the screen edge. Thesis line small and quiet, positioned elsewhere, not directly centered under the name. Big contrast in scale and position between the two elements, not matching sizes both centered.

3. **The cube's geometry as a structural device, not just a logo.** Section backgrounds carry a very slight skew/rotation (a few degrees, subtle) suggesting adjacent cube facets as the user scrolls past — not uniform flat rectangular sections stacked straight down.

4. **Rhythm breaks between sections.** Avoid uniform spacing/size throughout. Tight, dense proof-strip typography should be followed by something sparse and large (e.g. one big word or short phrase taking most of the viewport) before the work selector — tension and release, not a steady uniform scroll.

5. **The NDA framing becomes a deliberate feature, not an apology.** Borrowing from Lola Jiang's password-gated case study framing: present the "real screens are NDA-protected, here's the thinking instead" moment as a confident, deliberate choice (rarer access, not absence) — matches the tone already locked for the Adobe Portfolio placeholder line ("This site has officially reached legacy status...").

**What does NOT change:** case study pages stay simple, calm, and content-dense — finesse of information architecture and a few well-chosen colors from the established palette (vermillion accent, warm cream/gray), not drama. The drama is homepage-only; case studies are where the actual proof lives and shouldn't compete for attention with the page itself.

## Process note for this build

Decisions, brainstorming, and visual prototypes happen in chat with Claude (claude.ai) first — fast iteration, see-before-you-commit. The actual project (real files, git, Netlify deploy) lives in VSCode with Claude Code. Prototypes built in chat are starting references to hand off and integrate, not a parallel version of the site — avoid letting two versions diverge.

## Open items / decisions still pending

- Custom domain decision — deferred, not blocking launch.
- Cloud Secret Sync, OCPM case study content — not yet drafted, not currently prioritized (ABAC+RBAC and Fingerprinting are the two case studies being built first).
- About page copy — not yet drafted.
- Explorations section copy — not yet drafted (source material exists in portfolio project pages, currently thin/unfinished — see uxbyaditi.myportfolio.com for what exists now, much of it needs real rewriting, not just porting over).
- Schematic diagrams for both locked case studies (Fingerprinting "tangle → single suggestion"; ABAC+RBAC "two disconnected systems → one unified view") — content is locked, visuals not yet built.
- Adobe Portfolio site (old site, still live) has a placeholder line added: "This site has officially reached legacy status. A new one's in progress." with a note that enterprise case studies are NDA-bound. A link to the new site should be added below that line once it's live.
