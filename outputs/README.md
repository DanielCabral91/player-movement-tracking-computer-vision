# Outputs

Generated artefacts belong in this directory and are intentionally excluded from normal Git history.

The canonical workflow writes:

```text
outputs/
├── tracking_output.csv
├── tracking_video.mp4
└── metrics/
    ├── average_positions.png
    ├── distance_covered.png
    ├── player_1_heatmap.png
    ├── zone_control.png
    ├── zone_control.gif
    ├── team_surface.png
    ├── defensive_coverage_index.png
    ├── heatmap_avg_teamA.png
    ├── heatmap_avg_teamB.png
    ├── heatmap_avg_both.png
    └── heatmap_combined.gif
```

The tracking notebook produces the structured CSV and annotated video. The metrics notebook consumes `tracking_output.csv` and writes analysis figures and animations under `outputs/metrics/`.

For reproducibility, commit only small, intentionally curated samples or final publication figures. Do not use the repository as storage for repeated experimental videos, model outputs or large generated datasets.
