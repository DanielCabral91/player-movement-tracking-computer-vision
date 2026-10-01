# Contributing

This repository documents a co-authored academic research project and is primarily maintained as a technical portfolio and reproducibility record.

## Before proposing a change

Please keep changes aligned with the original project scope and evidence. Contributions should not silently introduce new metrics, claim stronger validation than the project achieved, or present prototype outputs as production-grade measurements.

## Suggested workflow

1. Create a branch from `main`.
2. Make one logically scoped change.
3. Keep generated videos, model weights and large datasets out of Git history.
4. Verify notebook paths and imports.
5. Document methodological changes in `docs/` when they alter interpretation.
6. Open a pull request describing what changed and why.

## Notebook conventions

- clear stored execution outputs before committing unless an output is essential for explanation;
- use repository-relative paths;
- do not commit API keys, tokens or local credentials;
- keep the execution order documented;
- preserve the distinction between original project logic and later experimental extensions.

## Data and media

Do not add raw broadcast footage or third-party datasets unless redistribution rights are clear. Small synthetic or permitted samples are preferred for examples.

## Model artefacts

Large trained weights should be versioned outside normal Git history, for example as a release asset, only after their redistribution terms and training provenance are documented.

## Authorship

The original academic work is jointly authored by Eduardo Cruz, Daniel Cabral, David Gonçalves and Guilherme Vieira. Repository maintenance does not transfer or replace that authorship.
