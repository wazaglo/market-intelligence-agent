# Contributing

This is a **course capstone portfolio repo** documenting a no-code market-intelligence build on Amazon QuickSuite against a fixed brief (the Udacity rubric). The Space, agent, and research report live in a Vocareum lab account that is torn down after the course - the repo and its screenshots are the deliverable.

## Contribution types

| Kind of feedback | How |
|---|---|
| Factual error in an insight, figure, or confidence call | Open an issue citing the file/section; I re-verify against `data/vgsales.csv` and the Quick Research report, and credit you in the doc |
| Better way to structure the dataset↔research integration or the validation design | Issue against `docs/methodology.md` / `docs/limitations_and_checks.md` - design critique especially welcome |
| Reproduction problems with the verify snippet | Issue with your OS/Python version (needs stdlib only) |

Please **don't** open PRs that rewrite the analysis voice of the docs - they are deliberately first-person learning artifacts.

## Reproducing the checks

```bash
# Recompute the publisher ranking and dataset totals from the Kaggle CSV
python - <<'EOF'
import csv
from collections import defaultdict
rows=list(csv.DictReader(open('data/vgsales.csv')))
pub=defaultdict(float); total=0.0
for r in rows:
    g=float(r['Global_Sales']); total+=g; pub[r['Publisher']]+=g
print("total M:", round(total,1))
print(sorted(pub.items(), key=lambda x:-x[1])[:5])
# expect: total ≈ 8920.4 ; Nintendo 1786.56 ; EA 1110.3 ; Activision 727.5 ...
EOF
```

External figures (market size, platform mix, M&A values) come from the Quick
Research report kept at `artifacts/05_quick_research_report.txt` - treat them as
secondary sources, exactly as the reliability doc does.

## Style notes

- Every quantitative claim states its source: `[Dataset]`, `[Quick Research]`, or "recomputed".
- Confidence levels are part of the claims - a contribution that raises or lowers one should carry evidence.
- Screenshots in `screenshots/` are append-only evidence; never edit or relabel them.

## License

By opening an issue or PR you agree your contributions are offered under the same
CC BY-NC-ND 4.0 terms that cover this repository (see `LICENSE`).
