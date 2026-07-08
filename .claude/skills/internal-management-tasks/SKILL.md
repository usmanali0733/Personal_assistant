---
name: internal-management-tasks
description: Structures internal work items for company management tools (ClickUp-like) with Problem, Value, Scope, User Story, Acceptance Criteria, and task-completion reports. Use when creating internal tasks, engineering briefs, sprint tickets, handoffs, or writing a "what we did" task report after shipping work.
disable-model-invocation: true
---

# Internal management tasks (ClickUp-style)

## When to use

Apply when the user asks to draft or refine an internal task, ticket, or brief—or a **task report** summarizing completed work—for tools such as ClickUp, Jira, Linear, or similar.

## Task structure

Produce tasks with:

1. **Title** — Short, action-oriented, unique enough to find later.

2. **Long description** — Use these sections in order (omit only if truly N/A). Match headings exactly:

   - **Problem** — Current pain, inconsistency, risk, or gap.
   - **Value** — Outcomes for users, team velocity, quality, or compliance.
   - **Scope** — In scope vs out of scope (explicit boundaries reduce churn).
   - **User Story** — `As a [role], I want [capability] so that [benefit].`
   - **Acceptance Criteria** — Numbered or checklist items; each testable and unambiguous.

Use markdown headings (`##` or `###`) consistent with the destination tool. Preserve product/repo paths, filenames, and constraints exactly as given.

## Acceptance criteria

- Write criteria so someone else can verify completion without asking.
- Include technical checks (paths, builds, i18n keys, a11y) when relevant.
- Call out exclusions (“out of scope”) again if they affect verification.

## Time Tracking & Billing

- Note that tracking time does not automatically mark it as billable. The **Billable** flag is a separate input and must be explicitly checked/set when logging the task.

## Task report (completion summary)

After work is done, a **Task report** documents what shipped. Format:

- Start with the label `Task report :` (or `Task report:`) on its own line if the tool expects it.
- Bullet list of concrete changes: files added/changed, routes, config, translations, removals.
- Stay factual; no restating the whole original brief unless asked.

---

## Example — full task (template reference)

**Title** (example): Onboarding assets and i18n under repo

**Long description**

**Problem**

Design-approved onboarding art lived outside the repo or was split across old generic screenshots; text duplicated between code and design. We needed dedicated assets under a stable public path and short accessibility copy without duplicating visible titles in code for greet slides.

**Value**

Pixel-faithful onboarding, faster design iteration (swap PNGs without code changes), consistent branding (mark SVG), and localized experience for English and Arabic users.

**Scope**

laiwyer-fe/public/assets/... additions and en.json / ar.json onboarding-related keys (staged). Includes LaiwyerMarkBlack.svg and public/assets/onboarding_images/* plus any new keys for carousel alt text, chat labels, etc. Out of scope: translating non-onboarding modules, CMS-driven asset hosting.

**User Story**

As a product owner, I want onboarding visuals and copy versioned in the repo under predictable URLs so engineering can ship the exact frames from design with minimal code churn and full EN/AR coverage for new strings.

**Acceptance Criteria**

1. Four onboarding slide images exist under public/assets/onboarding_images/ and are referenced by the carousel (paths valid in production build).

2. LaiwyerMarkBlack.svg is available for welcome/chat avatar usage as staged.

3. All new user-visible strings introduced for onboarding appear in en.json and ar.json (no hard-coded locale-only text for those keys).

4. Slide images use meaningful alt text via i18n for screen readers (visible copy lives in artwork).

5. Filenames with spaces/special characters are handled safely in src (e.g. encoded URL where used).

6. Assets are committed (not gitignored) and size is reasonable for web (no multi‑MB surprises without team sign-off.)

---

## Example — task report

Task report :

- Added LaiwyerMarkBlack.svg under public/assets/images/ for compact brand mark usage.

- Added onboarding_images set: Research.png, El-Sanhuri.png, Analyse.png, and encoded reference for Analyse (1).png as the fourth slide source.

- Pointed greet carousel slides at /assets/onboarding_images/... and removed redundant in-code titles/descriptions for those slides.

- Extended en.json / ar.json with onboarding keys (including slide alt labels and carousel helper copy).

- Kept i18n as the single source for remaining onboarding strings (welcome, chat, greeting, buttons, a11y).
