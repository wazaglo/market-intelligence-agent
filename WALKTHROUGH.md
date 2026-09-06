# Walkthrough — exactly what we did, with every input and where it came from

Reproduce this in roughly one long session (the Quick Research job alone takes ~9 minutes). Section order is the real work order.

## 0. Prerequisites & provenance of every input

| Input | What it is | Where it came from |
|---|---|---|
| `data/vgsales.csv` | Kaggle dataset **`gregorut/videogamesales`** ("Video Game Sales", 16,598 titles, 1995–2016, ~8,920M units total; cols: Rank, Name, Platform, Year, Genre, Publisher, NA/EU/JP/Other_Sales, Global_Sales) | kaggle.com — public dataset. Downloaded as `videogamesales.zip` (kept file as Kaggle provides it; single CSV inside). Either via the site (needs sign-in) or `kaggle datasets download gregorut/videogamesales` with an API token (`~/.kaggle/access_token`). Included in this repo at `data/`. |
| `research-brief-template.docx` | The graded deliverable template (9 sections) | project lesson's **Downloads** tab on learn.udacity.com |
| Lab environment | Amazon Quick Suite (QuickSight) enterprise trial: Spaces, Chat agents, Quick Research, us-west-2, namespace `UdacityQuicksightLab` | project lesson → **Cloud Resources** tab → *Start Cloud Resource* → *Open Cloud Console* → AWS access portal (`d-…awsapps.com/start`) → tile **UdacityQuicksightLab**. Sessions expire fast — have the SAML link ready. |

No code was needed to build the project; python was used afterwards only for verification and to render the chart/brief (`matplotlib`, `python-docx`, both pip-installable).

## 1. Space + dataset upload (screenshots `620–624`)

1. Quick Suite home → **Spaces → Create space** → name `WA - Market Intelligence – Video Game Publishing`, description stating its purpose and contents. (Space id `25cc817f`.)
2. Space → **Add → Upload files** → `vgsales.csv`. Waited until status = **Ready** (this is the agent's internal knowledge base).

## 2. The chat agent (screenshots `642–662`)

1. **Chat agents → Create chat agent → Blank** (skip the AI-generated wizard — manual config gives reproducible results; a first attempt using Generate produced an unsaved draft).
2. Name: `WA - Market Intelligence Agent – VG Publishing` (≤50 chars enforced).
3. Description: *"An evidence-driven market analyst agent for the video game publishing market. Synthesizes the Kaggle Video Game Sales dataset with Quick Research external signals to produce market analyses and leadership-ready briefs with explicit citations, confidence levels, and limitations."*
4. Instructions (verbatim, the core of the design):

> You are a Market Intelligence Agent. Your job is to analyze a dataset and external market signals to produce a market analysis and a leadership-ready brief.
>
> Domain: video game publishing market. Internal knowledge base: Kaggle dataset 'Video Game Sales' (gregorut/videogamesales), 16,598 best-selling titles 1995-2016 with regional sales in millions (NA/EU/JP/Other) by publisher, platform, genre and year.
>
> Operating rules:
> 1. Always cite each insight: label it [Dataset] for the internal Kaggle dataset or [Quick Research] for external research.
> 2. Give a confidence level (High/Medium/Low) per insight and state limitations instead of overstating certainty.
> 3. Cover: competitive landscape by publisher/platform, key trends and signals over time and by region, opportunities, risks.
> 4. Market Analysis sections: Competitive landscape; Key trends and signals; Opportunities and risks; Supporting evidence.
> 5. Market Intelligence Brief sections: Objective and scope; 3-5 key insights with why they matter; confidence and limitations summary; strategic implications and next steps.
> 6. Distinguish dataset facts (through 2016) from current market conditions; flag timeliness gaps.
>
> Tone: concise, structured, evidence-driven, executive-ready.

5. **Knowledge sources → Link spaces** → tick the WA space checkbox → **Link**. Gotcha: the space grid sometimes loads empty — close and reopen the dialog until the row appears, tick the **row checkbox** (clicking the row text does nothing).
6. Save/Launch. Verify: the agent appears in the home chat-agent picker (`662_picker`).

## 3. Quick Research (screenshots `664–673`)

1. **Research → New research**, objective used verbatim:

> Market intelligence research on the global video game publishing market, current state 2024-2026: (1) overall market size and growth rate; (2) competitive landscape among major publishers - Tencent, Sony, Microsoft/Activision Blizzard, Nintendo, EA, Ubisoft, Take-Two, Krafton - with recent revenues and market shares; (3) structural trends: mobile vs console vs PC share, subscription and live-service business models, and the impact of generative AI on development costs; (4) pricing trends (full-price games at $70, monetization); (5) recent M&A and consolidation activity and what it signals; (6) key risks for publishers. Context: we hold a dataset of 16,598 best-selling titles 1995-2016 by publisher/platform/region, and need today's external signals to update that historical picture.

2. QuickSuite replies with a rephrased plan (est. 7–10 min) → choose **Start the research**. ~9 min wall-clock.
3. Output: report *Global Video Game Publishing Market Intelligence 2024–2026: Competitive Landscape, Platform Trends, and Strategic Risks* (id `e7c70710`). Full saved text: `artifacts/05_quick_research_report.txt`. Headline signals: $182.7B(2024)→$227B(2028) @4.9% CAGR; mobile ~55%/$108B; PC +10.4% YoY; MSFT–Activision $68.7B, T2–Zynga $12.7B, reported EA $55B buyout; Game Pass churn after +50% price; GenAI could halve $200–400M AAA budgets.

## 4. Three-turn agent conversation (screenshots `674–678`)

Same conversation, three prompts (full verbatim text of each is visible in the screenshots):

- **Task 1 — internal analysis**: state dataset context (source, shape, columns), goal, then ask for a `[Dataset]`-labelled Market Analysis with (a) publisher landscape incl. shares of ~8.8B total, (b) trends incl. 2008 peak/decline/platforms/regional mix, (c) opportunities/risks, (d) specific figures. Agent retrieved the CSV from the Space ("Searching your documents") and produced tabular evidence.
- **Task 2 — integration**: paste the eight external findings as an explicit `[Quick Research]` bullet block and demand the 4-section Market Analysis *with agreement/divergence called out explicitly* between dataset and research.
- **Task 3 — brief**: ~500-word leadership brief with objective/scope, 3–5 insights + why, confidence & limitations, strategic implications/next steps.

Outputs saved as `artifacts/01–03`.

## 5. Human validation (this is a step, not a footnote)

1. Recomputed every dataset claim from `data/vgsales.csv` (`docs/limitations_and_checks.md` has the table; one-liner in `CONTRIBUTING.md`). Nintendo 1,786.56M and total 8,920.4M matched exactly; top-5 share within 0.2pt.
2. Graded each external claim by verifiability (closed M&A deals vs. one reported buyout vs. one bank estimate).
3. Wrote `artifacts/04_reliability_evaluation.md` myself: per-insight evidence/gaps/confidence/limitations + signal freshness + "what would change our mind" + impact/effort matrix.
4. Chart for the brief's Visual Evidence section: bar (top-10 publishers) + line (annual 1995–2015 units) → `artifacts/decision_chart.png` (matplotlib; exact snippet reconstructable from the PNG axes).

## 6. Assemble & deliver

1. Filled the course template section-by-section → `Research_Brief_WA_Market_Intelligence.docx` (python-docx; embeds the chart).
2. Uploaded `02–05` artifacts into the Space so a stakeholder finds everything in one place (`679_space_organized`, all statuses Ready).
3. Zip = README + docs + artifacts + screenshots + `data/vgsales.csv` + docx → submitted on the lesson's **Submit Project** tab. Result: *Awaiting Review* (`695/696` screenshots).
4. This repo mirrors the zip.

## Failure log (so you don't repeat them)

- Agent drafts made via the AI wizard + page navigation can be **silently unsaved** — the agent vanished from the list. Blank editor + manual fields + Launch persisted it.
- Agent name hard-limits at 50 characters (en dash included).
- Link-spaces dialog: the space grid intermittently renders empty; tick the checkbox column, not the row text.
- Kaggle sign-in: Google SSO was blocked (changed password + reCAPTCHA on sign-up); the API token route worked in one command.
- Quick Research only starts after you click **Start the research** on its plan message — nothing happens if you just hit Send.
