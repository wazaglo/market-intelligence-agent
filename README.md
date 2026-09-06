# Market Intelligence Agent — Amazon QuickSuite (Udacity nd2726 Project 2)

A no-code Market Intelligence workflow built entirely in **Amazon QuickSuite**: a Kaggle dataset as internal knowledge, an agent with an enforced evidence-citation persona, a Quick Research external briefing, and a validated, leadership-ready Market Intelligence Brief — organized in one Space.

## The one-paragraph version

I picked the Kaggle *Video Game Sales* dataset (16,598 best-selling titles, 1995–2016) because it captures an era whose end is still misunderstood: retail unit sales collapsed ~90% after 2008 while the actual market grew to $182.7B. My agent was instructed to never blend evidence types: every claim is tagged `[Dataset]` (internal, through-2016) or `[Quick Research]` (external, 2024–2026). I then ran a Quick Research deep-research job on the current market, fed its findings back to the agent for an integrated Market Analysis, and asked for a final brief. Before accepting anything I recomputed the key numbers from the raw CSV and wrote a reliability evaluation that downgrades two insights to Medium confidence and flags the EA-buyout figure as the weakest claim.

## What was built (all named `WA - ...`)

| Asset | Name / ID |
|---|---|
| Space | `WA - Market Intelligence – Video Game Publishing` (`25cc817f`) |
| Knowledge | `vgsales.csv` (Kaggle `gregorut/videogamesales`) + 4 analysis artifacts |
| Chat agent | `WA - Market Intelligence Agent – VG Publishing` (`c46b71b2`) |
| Quick Research report | `Global Video Game Publishing Market Intelligence 2024–2026` (`e7c70710`) |
| Conversations | dataset analysis → integrated analysis → final brief |

## Repo map

- `Research_Brief_WA_Market_Intelligence.docx` — the graded deliverable (template sections 1–9, chart embedded)
- `docs/methodology.md` — why each step was designed the way it was
- `docs/limitations_and_checks.md` — what I re-verified myself and what I refused to conclude
- `artifacts/` — agent outputs (dataset analysis, integrated analysis, brief), the reliability evaluation, the raw Quick Research report text, and `decision_chart.png`
- `screenshots/` — 20 evidence shots following the build order (portal → space → agent → research → analysis → brief → final space)

## Headline findings (with source labels, as the agent enforced)

1. The market transformed, it did not shrink — 678.9M units (2008) → $182.7B (2024), ~4.9% CAGR to $227B. **[Dataset + Quick Research]** High confidence.
2. Consolidation (MSFT–Activision $68.7B, T2–Zynga $12.7B, reported EA deal) + top-5 historical share 52.7% → mid-tier squeeze. High / Medium on the EA figure.
3. Mobile ≈ 55% of revenue ($108B), PC +10.4% YoY vs a dataset that was 72.6% console. High/Medium.
4. APAC gravity shift (NA 51.4%→47.6% in-data, APAC-largest today). Medium.
5. GenAI could halve $200–400M AAA budgets — single-source. Low-Medium.

## Built with

Amazon QuickSuite (Spaces, Chat agents, Quick Research), Kaggle public dataset, matplotlib (one summary chart for the brief), python-docx (brief rendering).

Student: Wisdom Azaglo — September 2026.
