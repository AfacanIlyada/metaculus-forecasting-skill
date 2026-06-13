# Forecasting skill on Metaculus is invisible in how authors write but partially visible in what they forecast

A study of forecasting accuracy on Metaculus across six categories, testing whether author-level linguistic signatures and track records identify skilled forecasters.

## Findings

1. **Skill is real and stable.** Person-level forecasting skill is identifiable and persists across domains — it is not an artifact of a single category or time window.
2. **Skill is not legible from how authors write.** Aggregated linguistic features do not recover skill out of sample; how forecasters write does not reveal how well they forecast.
3. **Skill is partially visible in explicit probabilities.** Where authors state explicit probabilities, calibration carries some of the skill signal that text alone does not.

## Repository layout

```
metaculus-forecasting-skill/
├── README.md            This file.
├── LICENSE              MIT license.
├── CITATION.cff         How to cite this work.
├── requirements.txt     Python dependencies (mixed model fit in R; see code/).
├── paper/               Manuscript sources and build.
├── code/                Analysis pipeline.
├── data/                Derived author-level features, comment IDs, codebook, manifest.
│   └── manifest/        SHA-256 hashes of the sealed analysis artifacts.
├── figures/             Generated figures.
└── supplement/          Supplementary materials.
```

## How to reproduce

1. Install Python dependencies: `pip install -r requirements.txt`.
2. Obtain raw comment text from the corresponding author (not redistributed here; see Data availability) and place it under `data/raw/`.
3. Run the pipeline stages described in [`code/README.md`](code/README.md): scrape → stance/forecast labelling → deduplication → feature extraction → reliability → cross-classified skill model → CV legibility test → Brier transfer.
4. The cross-classified mixed model is fit in R with `lme4::glmer`; see [`code/README.md`](code/README.md).

## Data availability

This repository releases the derived author-level feature tables, comment identifiers (not comment text), the analysis code, the codebook, and a manifest of SHA-256 hashes for the sealed analysis artifacts. Raw Metaculus comment text is not redistributed here, in line with Metaculus's terms of use and forecaster privacy, and is available from the corresponding author on reasonable request. Resolved-question metadata is retrievable from the public Metaculus API.

## AI-use disclosure

Two classification steps use a pinned Anthropic model, claude-haiku-4-5-20251001: a locked four-label stance classifier (YES/NO/NEUTRAL/UNCLEAR) and a locked binary forecast / not-forecast classifier. Both prompts are fixed and versioned; their text and SHA-256 hashes are in the paper's appendix. No generative-model output enters the statistical results other than these labels.

## Citation

See [`CITATION.cff`](CITATION.cff).

## License

MIT. See [`LICENSE`](LICENSE).

## Contact

Corresponding author: ikucukafacan25@ku.edu.tr
