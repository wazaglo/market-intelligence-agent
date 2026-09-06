# Methodology - why the workflow looks like this

## Why this dataset

The project leaves the dataset choice open, so I chose for *tension*: *Video Game Sales* ends in 2016 at the exact moment the industry's accounting model broke (retail units → digital/recurring). That forces the agent - and me - to reconcile two evidence bases rather than just summarize one, which is the actual skill being graded. I verified the Kaggle file independently: 16,598 rows, 8,820M total units after dropping undated rows, Nintendo 1,784M, NA share 49.1%. These became my ground truth for checking the agent.

## Why the agent's instructions are written like rules

The free-text purpose is required ("You are a Market Intelligence Agent..."), but I deliberately added six operating rules because my tests of earlier agent drafts showed the failure mode is confident blending: the agent will happily state a 2016 number as if it were current. The rules force:

- `[Dataset]` / `[Quick Research]` tagging on every insight (source hygiene),
- a confidence level per insight (uncertainty is a requirement, not a caveat),
- fixed section skeletons for the Analysis and the Brief (so outputs are comparable and gradeable),
- an explicit timeliness duty (dataset facts end 2016).

The rule that mattered most: *"flag timeliness gaps"*. Without it the brief reads like a 2016 market memo.

## Why Quick Research ran as a separate deep-research job

Dataset questions and web questions have different failure modes; mixing them in one chat gives you plausible mush. I scoped the research objective around the four decision-critical unknowns only (size/growth, platform mix, consolidation, business-model shifts). QuickSuite first returned a rephrased plan (estimated 7–10 min) - I approved it rather than letting it free-run. While it ran I did the internal analysis through the agent in parallel, so integration later would be fast.

## Integration step (the part that is easy to fake)

I pasted the eight key external findings into the agent as an explicit `[Quick Research]` block and asked for agreement/divergence, not synthesis-by-vibes. That produced the useful friction: the dataset's "market collapse" story is *contradicted in interpretation* (not data) by the external revenue growth, and the agent's GenAI insight correctly came back with no internal support.

## Validation design

Before touching the brief I recomputed every dataset claim from the raw CSV with a script (shares, trajectories, regional mix, top publishers). Nintendo's 1,786.56M and the 8,920M total matched the agent exactly once I realized it included the 271 undated rows I had first dropped (the agent's trajectory figures match my dated-rows recomputation exactly). My top-5 share lands at 52.5% vs the agent's 52.7% - a residual from Sony's regional label handling; documented, not quietly harmonized. External claims I split by verifiability: named closed M&A deals = fine; the EA $55B reported buyout and Morgan Stanley GenAI savings = flagged, not deleted.

## What I'd do differently

Attach the Quick Research report to the Space *before* the integrated run (currently it lives in Research and its numbers entered the conversation via my prompt). Also add a second dataset (a recent one, e.g. Steam reviews) to shrink the 10-year evidence gap - the largest structural weakness in this build is temporal, not analytical.
