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

## Fingerprinting case study — DRAFT, has open gaps

This is the first case study being built (template-setter). Current draft, with gaps marked — these need Aditi's input before finalizing, do not fill them in with invented detail:

> **TL;DR:** Pega's workflow discovery process took weeks of manual digging. I designed a feature that surfaces the workflow instantly, end to end, solo. Spot Award.
>
> **Context:** Pega's Process & Task Mining suite helps enterprise clients understand how work actually happens across their teams — not how it's documented, how it's really done. [GAP: who specifically used this — process analysts? ops managers?]
>
> **Problem:** Before Fingerprinting, finding a workflow pattern meant manual discovery — someone had to dig through activity data by hand, over [GAP: confirm rough duration and what the manual process actually involved — interviews? spreadsheet digging?]
>
> **Process:** Owned end to end — understood the problem space, designed the solution, with guidance only on user testing methodology from a mentor. [GAP: was there a technical constraint or stakeholder input that shaped the design approach?]
>
> **Solution (schematic):** Before: scattered, multi-step manual process — pull data, dig through it by hand, infer the pattern. After: one instant suggestion, surfaced automatically. [Diagram to be built once the "before" steps above are confirmed.]
>
> **Outcome:** Validated through scripted, task-based usability studies with enterprise clients — measured by task success rate and qualitative feedback. Recognized with a Spot Award.

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
2. Case study template: build using Fingerprinting once content gaps are filled.
3. Remaining case studies: Cloud Secret Sync, OCPM, (optional) ABAC+RBAC — reuse template.
4. Work index + Explorations section.
5. About page: bio, full philosophy paragraph, skills snapshot, resume link.
6. Writing index + article template (structure only, can be empty).
7. Google Analytics script across all pages, mobile check, ship.
8. Ongoing: add articles, revisit based on Analytics data.

## Open items / decisions still pending

- Fingerprinting case study gaps (see above) — need Aditi's input, not to be invented.
- Custom domain decision — deferred, not blocking launch.
- Cloud Secret Sync, OCPM, ABAC+RBAC case study content — not yet drafted.
- About page copy — not yet drafted.
- Explorations section copy — not yet drafted (source material exists in portfolio project pages, currently thin/unfinished — see uxbyaditi.myportfolio.com for what exists now, much of it needs real rewriting, not just porting over).
