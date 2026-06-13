# Data

## Data-availability policy

This repository releases the derived author-level feature tables, comment identifiers (not comment text), the analysis code, the codebook, and a manifest of SHA-256 hashes for the sealed analysis artifacts. Raw Metaculus comment text is not redistributed here, in line with Metaculus's terms of use and forecaster privacy, and is available from the corresponding author on reasonable request. Resolved-question metadata is retrievable from the public Metaculus API.

## What IS included

- **Derived author-level feature tables** — aggregated per-author linguistic, structural, and activity features.
- **Comment identifiers** — comment IDs (and question/author IDs), *not* comment bodies.
- **Codebook** — column-by-column documentation in [`codebook.md`](codebook.md).
- **Manifest of hashes** — SHA-256 hashes of the sealed analysis artifacts in [`manifest/`](manifest/).

## What is NOT included

- **Raw Metaculus comment text** (comment bodies). Not redistributable; available from the corresponding author on reasonable request.
- Any file containing comment text. See the root `.gitignore`.

## manifest/

`manifest/` holds SHA-256 hashes of the sealed analysis artifacts so that anyone who obtains the underlying data can verify byte-for-byte that they are working with the exact frozen inputs used in the paper. The hashes are for integrity-checking only; the raw artifacts themselves are not stored here.
