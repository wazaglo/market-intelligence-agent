# Reliability, Confidence & Limitations Evaluation

Step 6 validation of the Market Intelligence Brief. Written by the student (not the agent) after checking the agent's claims against the raw dataset and the Quick Research report.

Method: every major insight was recomputed from `vgsales.csv` (16,327 dated rows, 8,820M units) where possible, and cross-read against the Quick Research report "Global Video Game Publishing Market Intelligence 2024–2026" (generated in QuickSuite on 2026-09-06).

## Insight-by-insight evaluation

### I1 — The market transformed, it did not shrink (unit sales −89.6% from 2008 peak vs. $182.7B → $227B revenue growth)
- **What the insight is:** Post-2008 decline in tracked unit sales reflects migration to digital/mobile/recurring models, not demand collapse.
- **Evidence:** Dataset: recomputed independently — 678.9M units in 2008, 600.5M (2010), 264.4M (2015); matches agent figures exactly. External: market-size series $182.7B (2024) → ~$227B (2028), 4.9% CAGR (research report, aggregator estimates).
- **Gaps / assumptions:** The dataset tracks only best-selling physical/retail titles ≥100k units; digital and free-to-play are invisible. The external CAGR comes from market-research aggregates of differing definitions (consumer spend vs. publisher revenue).
- **Confidence:** **High** (both sources independently agree on direction; magnitudes are definition-dependent).
- **Limitations:** Cannot conclude the true revenue trajectory from unit data; cannot quantify digital share precisely.
- **Signal freshness:** Dataset frozen at 2016 (reporting lag makes 2016 especially incomplete); external figures captured 2026-09-06, describing 2024–2026 — still the current consensus window.

### I2 — Consolidation is squeezing mid-tier publishers
- **What the insight is:** Concentration is structural and accelerating; mid-tier publishers face existential pressure.
- **Evidence:** Dataset: top-5 share 52.7% recomputed ≈ 52.4% (4,680/8,920M incl. rows with Year; 52.7% is the agent's consistent denominator) — agreement within rounding. THQ arc (33.3M in 2007 → 0.4M in 2013) verified in dataset; THQ's 2012–13 bankruptcy is public record. External: Microsoft–Activision $68.7B (closed Oct 2023), Take-Two–Zynga $12.7B (2022) are verifiable public transactions; the EA "$55B leveraged buyout led by Saudi PIF" is a **reported/estimated** deal figure — weakest single claim.
- **Gaps / assumptions:** Assumes deal values map directly to market-power increase; synergy and portfolio effects not measured.
- **Confidence:** **High** for the trend, **Medium** for the specific EA transaction figure.
- **Limitations:** Cannot conclude regulators will allow further consolidation (UK/EU review precedents cut both ways).
- **What would change our mind:** A regulatory block that reverses a major deal, or data showing mid-tier share rising in 2024–2026.

### I3 — Growth vectors are mobile + PC; console is mature
- **What the insight is:** Historical console-dominant strategies (72.6% console, 2.9% PC in dataset) mismatch today's revenue mix (mobile ~55%/$108B; PC +10.4% YoY).
- **Evidence:** Dataset share recomputed (console/handheld/PC split reproduced within 1pt). External: Newzoo-style figures for mobile and PC growth.
- **Gaps / assumptions:** Dataset PC share understates PC because PC bestsellers were historically fragmented (free-to-play never appears in a ≥100k-unit retail list). External mobile share covers consumer spend, not publisher take-rate.
- **Confidence:** **High** on direction, **Medium** on magnitudes.
- **Limitations:** Cannot conclude console is declining in absolute revenue (it is flat-to-growing, just not the growth engine); console premium sales still fund blockbuster IPs.
- **What would change our mind:** Two consecutive years of mobile revenue decline or a console-first hit cycle (e.g., GTA VI launch effects) that materially re-inflates console share.

### I4 — Geographic gravity has shifted to Asia-Pacific
- **What the insight is:** NA share declined 51.4% → 47.6% late in the dataset while "Other" (incl. APAC ex-Japan) grew ~2x; today APAC leads globally.
- **Evidence:** Dataset recomputation confirms the NA-decline/Other-rise drift (dataset "Other" aggregates all ex-NA/EU/JP sales — coarse). External: APAC-largest claim is standard in every current tracker.
- **Gaps / assumptions:** "Other" is a blunt proxy for APAC — China, SE Asia, LATAM are lumped together and under-reported pre-2016.
- **Confidence:** **Medium** (direction is corroborated by both sources; the dataset cannot resolve country-level truth).
- **Limitations:** Cannot size China or any single market from this dataset; mobile-first APAC monetization (loot boxes, gacha) is qualitatively different from the dataset's unit model.

### I5 — GenAI is a cost lever but culturally contested
- **What the insight is:** AAA budgets of $200–400M/title could roughly halve with GenAI (Morgan Stanley estimate), but player backlash and workforce concerns constrain adoption.
- **Evidence:** External only ([Quick Research]); the 1995–2016 dataset contains no cost data at all.
- **Gaps / assumptions:** One bank's estimate; no internal validation possible. "Backlash" is qualitative (Concord failure cited as live-service signal, partly conflated).
- **Confidence:** **Low-Medium**.
- **Limitations:** Cannot conclude when or whether cost reductions materialize; productivity claims for GenAI in creative pipelines are still immature.

## Cross-cutting limitations and risks
1. **Temporal gap:** internal evidence ends mid-2016; ~10 years of structural change (digital storefronts, F2P, mobile, live-service) happened outside the knowledge base. Any dataset-only strategy is systematically biased toward boxed console economics.
2. **Coverage bias:** the dataset lists only titles ≥100k units; the long tail and all of free-to-play are absent. Publisher names in the dataset predate mergers (Activision under Microsoft, Bethesda under Microsoft, etc.) so "competitive landscape" labels are historical.
3. **Single-source externals:** mobile share, CAGR, and GenAI savings trace to market-research aggregators and one bank note surfaced by Quick Research; QuickSuite does not expose the full source list per figure, so independent spot-checking was partial.
4. **Model risk:** all three artifacts were drafted by the same agent whose knowledge includes my framing prompts; agreement between [Dataset] and [Quick Research] tags was verified by me against raw numbers, but selection bias in what the agent surfaced remains possible.

## Overall confidence
**Medium-High.** The five insights' *directions* are corroborated by two independent evidence bases and recomputation; magnitudes that depend on external aggregate estimates (I1 revenue path, I5 cost savings) carry Medium/Low confidence.

## What would change our mind (top 2)
1. Authoritative 2024–2026 data showing global consumer spend contracting (not growing at ~5% CAGR) → invalidates the "transformation, not shrinkage" frame (I1).
2. A blocked or unwound mega-merger plus rising mid-tier share → weakens the oligopoly-squeeze thesis (I2).

## Impact vs effort matrix for recommended actions (confidence-adjusted)
| Recommended action | Impact | Effort | Confidence backing |
|---|---|---|---|
| Build recurring-monetization capability (live ops, battle pass) on existing IPs | High | High | High (I1) |
| PC + mobile port/remaster program for catalog IP | High | Medium | High (I3) |
| APAC-aware publishing partnerships / localization | High | Medium | Medium (I4) |
| GenAI-assisted production pilots on non-narrative asset pipelines | Medium | Low | Low-Medium (I5) |
| M&A optionality review (stay independent vs. sell to consolidator) | High | Low | High (I2) |
