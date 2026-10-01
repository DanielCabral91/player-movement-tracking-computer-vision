# Outputs

Generated artefacts belong in this directory and are intentionally excluded from normal Git history.

Typical outputs include:

```text
outputs/
├── tracking_data.csv
├── tracking_demo.mp4
└── figures/
```

The main tracking notebook writes a structured CSV and an annotated video. The metrics notebook consumes the CSV to calculate and visualise football performance indicators.

For reproducibility, commit only small, intentionally curated samples or final publication figures. Do not use the repository as storage for repeated experimental videos or model outputs.
