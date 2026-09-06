# Checks I ran, and the limits I refused to cross

## Recomputations (script over the raw Kaggle CSV)

| Claim in brief | My recomputation | Verdict |
|---|---|---|
| Nintendo 1,786.56M, total 8,920M | 1,786.56M / 8,920.4M incl. 271 undated rows | exact match |
| 2008 peak 678.90M; 2015 264.44M | 678.90M; 264.44M | exact match |
| 2008→2016 −89.6% | −89.6% (dated rows) | match, with caveat below |
| Regional mix NA 49.2/EU 27.3/JP 14.5/Oth 8.9 | 49.1/27.3/14.6/8.9 | match to rounding |
| Top-5 share 52.7% | 52.5% (all rows) / 53.1% (dated only) | near - denominator/label noise |

Caveat kept in the brief: the 2016 row is a reporting artifact (partial year capture), so the −89.6% headline includes it and overstates true decline; stated in the limitations section rather than fixed by cherry-picking 2015.

## External claims, graded by verifiability

- Microsoft–Activision Blizzard $68.7B (closed Oct 2023) and Take-Two–Zynga $12.7B (closed Mar 2022): public record, accepted.
- "EA $55B leveraged buyout led by Saudi PIF": reported in the Quick Research output but a *pending/estimated* transaction → brief marks it "reported" and it must not be used as settled fact.
- Mobile ≈ 55%/$108B, PC +10.4% YoY, market $182.7B→$227B @4.9%: standard tracker numbers but surfaced second-hand by the research agent without full citation per figure → direction High, magnitude Medium.
- GenAI halving $200–400M AAA budgets (Morgan Stanley): single bank estimate, no internal counter-evidence possible → Low-Medium; it never appears in the brief without its source label.

## Things I explicitly did NOT conclude

1. No "the industry shrank 90%" - the dataset measures a shrinking slice (retail-tracked ≥100k-unit titles), not the market.
2. No causal claim from the correlation "Gen 7 share collapse ↔ Gen 8 only 9.1% in data" - that is incomplete capture of a transitional year range.
3. No "subscriptions are failing" - one pricing episode (Game Pass price-hike churn) plus one product failure (Concord) ≠ model verdict.
4. No country-level APAC sizing from the dataset - "Other" lumps China/SE Asia/LATAM; the APAC claim stands only on external evidence.

## Known weaknesses a reviewer should weigh

- Both internal and external artifacts were produced in the same QuickSuite tenant by me; no third-party review of the agent's intermediate reasoning.
- The Quick Research report text saved here (`artifacts/05_quick_research_report.txt`) is the full report as rendered; figure-level citations inside it were not always resolvable to a primary source.
- One structural gap: the research report is not yet attached as Space knowledge (it is saved there as an artifact, but not "linked knowledge" for future chats).
