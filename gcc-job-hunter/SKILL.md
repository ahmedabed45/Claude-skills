---
name: gcc-job-hunter
description: Automates Mido's (Ahmed Abed Khattab's) job search for senior Business Process Re-engineering (BPR) / Transformation / Operational Excellence roles across Egypt and the GCC (UAE, KSA, Qatar). Use this skill whenever Mido asks to "find jobs", "search for openings", "look for roles", "check Indeed/LinkedIn for jobs", wants his CV tailored to a specific job post, wants a keyword/ATS match check, wants to prep or send an application, or wants an updated tracker/log of jobs found or applied to. Trigger eagerly for any job-search, CV-tailoring, or application-tracking request, even if phrased casually (e.g. "any new roles out there?", "update my job list", "tailor my CV for this one"). Covers targets in banking, fintech, IT services & consulting, consumer finance, and mortgage companies. Does NOT auto-submit applications without explicit per-job approval.
---

# GCC / Egypt Job Hunter

End-to-end workflow for sourcing, tailoring, and tracking applications for Mido's target roles: **Head of BPR, Head of Operational Excellence, Business Transformation Lead**, and close variants (Process Reengineering Manager, IT Change Management Lead, Business Analysis Director, Digital Transformation Manager) — in Egypt and the GCC.

## Guardrail — never auto-submit

This skill **searches, tailors, and drafts**. It never clicks "Apply" or sends an application on Mido's behalf without him explicitly confirming that specific job in that turn. Always end a sourcing/tailoring pass by presenting the shortlist and asking which ones to prepare full applications for, and end an application-prep pass by asking for go-ahead before using any tool that actually submits/sends (e.g. Indeed apply, email send, form submit).

## Step 1 — Source jobs

Search across two lanes every time this skill runs a sourcing pass:

1. **Indeed connector** (already available: `Indeed:search_jobs`, `Indeed:get_job_details`, `Indeed:get_company_data`). This is the primary structured source — use it first.
2. **Web search** for postings on LinkedIn Jobs, Bayt, GulfTalent, NaukriGulf, and Wuzzuf (Egypt), since Indeed doesn't cover everything. Use `web_search` with combinations of title + location, e.g. `"Head of Business Process Reengineering" Dubai`, `"Business Transformation Lead" Riyadh`, `Wuzzuf "process reengineering" Cairo`.

Run searches per **title × location** combination rather than one broad query (see Progressive Disclosure note below) — search each of the 3-4 target titles against each of the 4 locations (Egypt, UAE, KSA, Qatar) separately for real coverage; don't collapse into one query.

### Target keyword set (apply as search terms and later as ATS match terms)

Core role/function keywords:
`Business Process Re-engineering (BPR)`, `Process Reengineering`, `Business Process Management (BPM)`, `Operational Excellence`, `Business Transformation`, `Digital Transformation`, `IT Change Management`, `Change Management`, `Business Analysis`, `Lean Six Sigma`, `Kaizen`, `DMAIC`, `Process Optimization`, `Workflow Automation`, `BPMN`, `Requirements Elicitation`, `BRD/FRD Writing`.

Sector/industry keywords (combine with the above):
`Banking`, `Retail Banking`, `Corporate Banking`, `Fintech`, `IT Services`, `IT Consulting`, `Management Consulting`, `Consumer Finance`, `Mortgage`, `Islamic Finance` (common in GCC postings).

When building a query, pair one role keyword + one sector keyword + location, e.g. `"Business Transformation" fintech Abu Dhabi`, `"Process Reengineering" mortgage Cairo`.

### What to capture per job

For every plausible match, record: title, company, location, seniority level, posting URL, platform, date posted, and a 1-line note on fit (which of Mido's certifications/experience it matches — CBAP, Lean Six Sigma Black Belt, CRISC, ITIL, 24+ yrs banking, ADIB/NBK/SAIB background).

Filter out anything clearly below senior/manager level or unrelated to BPR/transformation/BA — Mido doesn't want junior analyst roles.

## Step 2 — Tailor the CV per job

Once Mido picks a job (or says "tailor for this one"), pull his latest CV. If it's not attached in this conversation, ask him to upload it or check for prior tailored versions via `conversation_search` (query: "CV" or "resume" plus a keyword from the target company/role).

Tailoring approach:
1. Read the job description closely (via `Indeed:get_job_details` or `web_fetch` on the posting URL).
2. Extract the job's specific required keywords/skills.
3. Rewrite the CV's summary and key bullet points to mirror those keywords naturally (never fabricate experience — only rephrase/reprioritize real experience to surface the relevant parts).
4. Cross-check against the target keyword set above — make sure BPR/transformation/BA terminology plus the relevant sector term (banking/fintech/IT services/consumer finance/mortgage) appear in the summary and skills section.
5. Flag, don't fill, any placeholder metrics — Mido's CV has a recurring gap of unquantified achievements; ask him for real numbers rather than inventing any.
6. Use the **docx skill** (`/mnt/skills/public/docx/SKILL.md`) to produce the tailored CV as a polished Word doc. Save with a clear filename: `CV_[Company]_[RoleShort]_[YYYYMMDD].docx`.

## Step 3 — Prep the application (draft only)

Draft a short tailored cover note / application message referencing the specific role and company. Present it to Mido for approval. Only after explicit "yes, send/apply this one" should any submission tool be used (e.g. Indeed's apply flow, if available in the connector — check via `tool_search` for an apply-capable Indeed tool before assuming one exists; if none exists, prepare the material and tell Mido to apply manually, or ask if he wants to open the connector page).

## Step 4 — Log everything to Excel

Maintain a single running tracker workbook, `GCC_Job_Applications_Tracker.xlsx`, with one row per job found (not just applied). Use the **xlsx skill** (`/mnt/skills/public/xlsx/SKILL.md`) for formatting/formulas.

Columns:
`Date Found | Job Title | Company | Location | Platform | Posting URL | Sector | Seniority Fit | Key Matched Keywords | CV Version Used | Status | Date Applied | Notes`

`Status` values: `Sourced`, `CV Tailored`, `Applied`, `Interview`, `Rejected`, `Offer`.

If a tracker already exists from a prior session (check `/mnt/user-data/uploads` or ask Mido / search past chats), read it and append new rows rather than overwriting — never destroy existing tracked history. Re-save and present the updated file each time.

## Notes on Mido's context

- He's completing a Master's at ESLSCA (expected Sept 2026) — don't let that affect target seniority, he's targeting senior roles now based on his 24+ years experience, not entry-level based on being a student.
- Recruiter firms he's previously engaged: Robert Walters, Michael Page, Cooper Fitch, Harrington Starr — worth including in web searches for GCC-specific postings too (e.g. `site:michaelpage.ae "business transformation"`).
- He communicates in Egyptian Arabic mixed with English — match his language if he writes to you in Arabic/mixed, but keep CVs and formal application material in English (standard for GCC banking/corporate roles) unless he asks otherwise.
- He prefers direct, polished, immediately-usable deliverables over back-and-forth — so default to producing the tailored CV + tracker in one pass rather than asking many clarifying questions, and only pause for approval at the actual "submit application" step.
