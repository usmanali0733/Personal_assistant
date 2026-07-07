---
name: ai-receptionist-prospect-research
description: Deep B2B sales research skill for evaluating whether any company (dental practice, med spa, law firm, salon, home services, or any other business that takes inbound calls/bookings) is a strong prospect for purchasing an AI Receptionist / AI automation offering. Use this when the user asks to "research a prospect," "research this business/company," "run prospect research," "build a sales intelligence profile," "score this lead," or provides a business name/website and wants a detailed, evidence-based outreach-readiness report on whether they'd buy an AI receptionist. Also use for batch prospecting across a list of companies (e.g. "research these 40 businesses"). Produces a structured, citation-backed report covering company size, tech stack, growth signals, AI opportunity, ability to pay, outreach difficulty, and a 1-10 fit score — never invented data, only verified facts or "Unknown / Could not verify."
---
 
# AI Receptionist Prospect Research Analyst
 
Deep, evidence-based B2B research on individual companies to determine how good a fit they are
for purchasing an AI Receptionist / AI automation offering, and to arm a salesperson with everything
needed to write a highly personalized cold outreach message immediately.
 
This skill works across any industry that relies on inbound calls, bookings, or appointments —
dental practices, med spas, law firms, salons, home services, clinics, and similar service
businesses — not just one vertical.
 
This skill is manually invoked — only run it when the user explicitly asks for prospect research,
a lead score, or a sales intelligence profile on one or more named companies.
 
## Core Principle: Research-Driven, Never Assumption-Driven
 
Every fact in the report must trace back to something actually found on the web. Do not infer
facts from a business's name, city, or "vibe."
 
If something cannot be verified after a reasonable search effort, write exactly:
 
> Unknown / Could not verify
 
Never guess provider counts, ratings, review counts, tech stack, or locations. Never estimate
values unless the user explicitly asks for an estimate — and even then, always use `web_search`
and `web_fetch` first and label any inference as an estimate, not a fact.
 
## Workflow
 
For each business being researched:
 
1. **Find the official website.** `web_search` for the business name + city/state if not
   already given, then `web_fetch` the homepage, "About," "Services," "Contact," and booking
   pages. Look for staff bios, technology badges/widgets (booking software, chat widgets),
   promotions, hiring/careers links, and any "new patients welcome" or expansion language.
2. **Find the Google Business Profile.** Search `"<business name>" <city> reviews` to surface
   the Google rating, review count, and — if visible in results — hours and multiple listed
   locations. If there are multiple locations, research each one separately.
3. **Cross-check with other public sources** as needed (Healthgrades, Yelp, Facebook, LinkedIn,
   Indeed job postings, local news) — but treat the official site and Google Business Profile as
   primary sources of truth. Note if sources conflict.
4. **Fill in the Information to Collect** (below) using only what you verified.
5. **Produce the Output Report** in the exact structure specified below.
Scale effort to the ask: a single business warrants a thorough multi-query pass (roughly 5-10
searches/fetches). A batch of many businesses (see Batch Mode below) still requires this same
process per business — don't shortcut individual research just because there are many.
 
## Information to Collect
 
### Business Information
- Business Name, Website, Phone Number, State, City, Years in Business (if available)
### Google Business Information
- Google Rating, Google Review Count
- If multiple locations: total locations, and whether review counts/ratings differ significantly
  between them
### Company/Business Size
- Number of Locations
- Number of Providers/Practitioners (e.g. dentists, attorneys, stylists, technicians) — verified only
- Number of Specialists
- Number of support staff (e.g. Hygienists) — optional, if available
- Approximate total staff size (if available)
### Online Presence
- Online Booking, Appointment Request Form, Live Chat, Patient/Client Portal, Emergency Contact,
  Contact Form, SMS/Text capability (if publicly visible)
### Growth Signals
- Accepting new patients/clients, running promotions, actively hiring, expanding, opening new
  locations, offering premium/new services
### Services Offered
List the major services/offerings found on the site (e.g. for a dental practice: Family Dentistry,
Cosmetic Dentistry, Implants, Orthodontics, Emergency Dentistry, Invisalign, Sedation Dentistry,
Pediatric Dentistry; for a law firm: practice areas like Family Law, Personal Injury, Estate
Planning; for a salon: Hair, Color, Skin, Nails, etc. — adapt to whatever industry the company is
in). Broader service range → higher likely call complexity.
 
### Operational Complexity
Rate **Low / Medium / High / Very High** and explain why, considering: number of providers,
number of specialties, apparent appointment volume, emergency services, consultation-heavy
services (cosmetic, implants, etc.), multiple locations.
 
### Estimated Call Volume
Rate **Very Low / Low / Medium / High / Very High**, reasoned from: review count/velocity,
number of providers, office hours, breadth of services, number of locations. Always show the
reasoning, not just the label.
 
### Technology Adoption
Report only what's verifiable: online booking, digital intake forms, AI chatbot, CRM, client
portal, modern scheduling software, and named platforms if identifiable (e.g. Weave, NexHealth,
Solutionreach, Dentrix, Open Dental for dental; Clio or MyCase for law firms; Vagaro or Mindbody
for salons/spas; or equivalents for the relevant industry).
 
### AI Receptionist Opportunity Analysis
Identify concrete, business-specific opportunities — missed calls, after-hours calls, appointment
scheduling/rescheduling, new patient/client intake, FAQ handling (e.g. insurance), emergency call
routing, reminders, lead qualification. Explain specifically how AI helps *this* business — avoid
generic boilerplate that could apply to any business in the vertical.
 
### Ability to Pay
Rate **Low / Medium / High / Very High**, supported by evidence: practice/business size, number
of providers/locations, premium branding, visible marketing investment, high-value service mix,
reputation. Never base this on city/location alone.
 
### Outreach Difficulty
Rate **Easy / Medium / Hard** and explain why (e.g. gatekeeper likely, decision-maker
identifiable, contact channels available, responsiveness signals).
 
### Personalization Opportunities
Concrete, specific details for a cold outreach opener: awards, community involvement, recent
expansion, notable tech adoption, unique services, mission statement language, patient/client
testimonials, special achievements.
 
### AI Receptionist Fit Score (1-10)
- 10 = Nearly perfect client
- 9 = Excellent prospect
- 8 = Strong prospect
- 7 = Good prospect
- 6 = Average
- Below 6 = Low priority
Always explain exactly why the score was given, referencing the evidence gathered above.
 
## Output Format
 
Produce, for every business, a structured report with these sections in order:
 
1. Executive Summary
2. Business Overview
3. Company/Business Size
4. Google Business Analysis
5. Website Analysis
6. Operational Analysis
7. AI Receptionist Opportunity
8. Ability to Pay
9. Outreach Difficulty
10. Personalization Ideas
11. Final Recommendation
12. AI Receptionist Fit Score (with justification)
The result should be detailed enough that a salesperson can start a highly personalized outreach
campaign immediately without doing any further research themselves.
 
## Delivery Format
 
- **Single business, quick lookup**: respond inline in chat with the structured report.
- **Single business, thorough/formal report, or user asks to "save"/"send" a report**: create a
  Word document. Read `/mnt/skills/public/docx/SKILL.md` first, then produce the .docx following
  its guidance, and place it in `/mnt/user-data/outputs`.
- **Batch mode (multiple businesses)**: research each business fully per the workflow above, then
  compile into one document — a table summarizing key fields (name, rating, size, fit score,
  ability to pay, outreach difficulty) followed by the full per-business reports. For anything
  beyond a handful of businesses, this should be a .docx or .xlsx (ask the user which they'd
  prefer if it's not obvious, e.g. a table-heavy comparison suits .xlsx, a narrative report suits
  .docx). Read the relevant skill (`/mnt/skills/public/docx/SKILL.md` or
  `/mnt/skills/public/xlsx/SKILL.md`) before building it.
## Accuracy Rules (non-negotiable)
 
- Never invent data. Never guess. Never estimate when verification is possible.
- If information is unavailable after a genuine search effort: write "Unknown / Could not verify."
- Do not fabricate provider counts, ratings, review counts, locations, or technology usage.
- If sources conflict, report the conflict rather than picking one silently.
 