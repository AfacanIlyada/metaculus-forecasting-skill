# code/

Analysis pipeline. Scripts will be added in a later release; this file documents the intended stages and their order.

## Pipeline stages

1. **Scrape** — collect resolved binary questions, resolutions, and comments from the Metaculus API per category.
2. **Stance / forecast labelling** — apply the pinned classifiers (`claude-haiku-4-5-20251001`): a locked four-label stance classifier (YES/NO/NEUTRAL/UNCLEAR) and a locked binary forecast / not-forecast classifier. Prompts are fixed and versioned (see the paper's appendix).
3. **Deduplication** — remove duplicate/near-duplicate comments before feature extraction.
4. **Feature extraction** — compute comment-level features, then aggregate to author-level (the seventeen text features plus activity controls; see [`../data/codebook.md`](../data/codebook.md)).
5. **Reliability** — estimate reliability of the author-level feature and skill estimates.
6. **Cross-classified skill model** — fit the cross-classified mixed model (authors × questions) to estimate author skill BLUPs. **Fit in R with `lme4::glmer`**, not in Python.
7. **CV legibility test** — out-of-sample cross-validation testing whether aggregated text features recover skill.
8. **Brier transfer** — calibration / Brier-score analysis on the explicit-probability subset and its cross-domain transfer.

> Note: scripts are not included in this scaffold and will be added later. No analysis scripts have been copied from the working tree.
