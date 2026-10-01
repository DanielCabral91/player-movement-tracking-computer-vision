# Project structure

The repository is organised to separate source notebooks, configuration, local inputs, generated artefacts and documentation.

```text
player-movement-tracking-computer-vision/
├── README.md
├── AUTHORS.md
├── CITATION.cff
├── CONTRIBUTING.md
├── requirements.txt
├── .gitignore
├── configs/
│   └── botsort.yaml
├── notebooks/
│   ├── 01_hsv_calibration.ipynb
│   ├── 02_tracking_pipeline.ipynb
│   └── 03_tactical_metrics.ipynb
├── data/
│   ├── README.md
│   ├── input/
│   └── sample/
├── models/
│   └── README.md
├── outputs/
│   └── README.md
├── reports/
│   └── README.md
└── docs/
    ├── methodology.md
    ├── reproducibility.md
    ├── limitations.md
    ├── data_schema.md
    └── project_structure.md
```

## Design rationale

- `notebooks/` contains the executable research workflow in execution order.
- `configs/` stores tracker configuration kept separate from notebook logic.
- `data/input/` is for local source video and is ignored by Git.
- `data/sample/` contains small, reviewable examples only.
- `models/` documents model placement; weights are not kept in normal Git history.
- `outputs/` is for generated CSVs, images, GIFs and videos and is ignored except for documentation.
- `reports/` documents the academic report without assuming redistribution rights.
- `docs/` separates methodological, reproducibility and limitation notes from the main README.

This structure is intended to make the repository understandable to both technical reviewers and football-analytics practitioners while keeping large or rights-sensitive artefacts out of the Git history.
