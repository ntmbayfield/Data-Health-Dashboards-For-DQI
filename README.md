# Data health dashboards — review mockups

Static mockups of a data quality and integration health dashboard suite for a decentralised
university advancement operation. Built as a **design review artifact**, not a working application.

## What this is

A proof of concept prototyped against five decentralised units that create and enter data —
Alumni Relations, Development, Events, Marketing & Communications, and the Registrar Office —
with an architecture of external sources → Omatic Cloud (middleware) → Salesforce.
The same functionality scales without redesign to an institution with thirty units.

Six boards, one data model:

| | Board | Purpose |
|---|---|---|
| 01 | Integration register & mapping attestation | Inventory, and whether mappings running in production were ever reviewed |
| 02 | Integration health — central view | Alarms, including the create:update canary and derived staleness |
| 03 | Graduate import audit | Semiannual SIS load — who graduated and did not arrive |
| 04 | Seven-day processing log | Every run, every trigger, every error |
| 05 | Data health defect backlog | State of the database, with defects attributed to the run that caused them |
| 06 | Unit dashboard | One per unit — score, integrations, alerts, 30-day log |
| KEY | Appendix | Margin reference key: build requirements, implementation decisions, findings |
| XLS | Integration register | The weeks 1-2 inventory workbook, rendered read-only and downloadable |

## Every figure here is synthetic

No real institution's data appears anywhere in this repository. Run counts, error volumes,
defect totals, scores and dates are plausible fabrications constructed to make design decisions
visible. Staff names are role labels, not people. **Do not quote a figure from this site.**

## Structure

```
index.html        landing page — scope, summary, board cards, build requirements
board-01..06.html one page per board
appendix.html     margin reference key
register.html     workbook viewer — all ten tabs, plus download link
styles.css        shared stylesheet
.nojekyll         disables Jekyll processing
404.html          custom not-found page
```

No build step, no dependencies. Every internal link is relative, so the site works from a
repository subpath (`username.github.io/repo-name/`) as well as from a domain root.
Typefaces load from Google Fonts over HTTPS and fall back to system faces offline.


## Companion workbook

`integration-register.xlsx` ships with the site and is viewable at `register.html`. Ten tabs:

| Tab | Purpose |
|---|---|
| README | Overview, why the inventory comes first, how the tabs fit together |
| Integration Register | The spine — one row per integration |
| Unit × Integration Map | Which units see which integration, including shared ones |
| Build Requirements | All twelve, with acceptance criteria |
| Implementation Decisions | Fifteen, each open or governed by a build requirement |
| Detection Methods | The logic behind every alert |
| Unit Score Model | Score components, weights and known distortions |
| Cadence & Stale Config | Expected cadence and next-run dates |
| Field Write Matrix | Which integration writes which field |
| Risk Findings | Eight findings from the inventory alone |
