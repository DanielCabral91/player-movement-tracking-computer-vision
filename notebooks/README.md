# Notebooks

The project is organised around three Jupyter workflows:

1. `01_hsv_calibration.ipynb` — interactive HSV calibration for team colours.
2. `02_tracking_pipeline.ipynb` — YOLOv8 detection, BoT-SORT tracking, ID management, team classification, coordinate estimation and CSV/video export.
3. `03_tactical_metrics.ipynb` — tactical and physical metrics calculated from the generated tracking CSV.

## Repository policy

Notebook outputs are removed before version control so the repository stores source logic rather than large embedded plots, videos or execution artefacts.

All three repository-ready notebooks are committed in this branch. The two larger notebooks were cleaned from the original project versions, had execution outputs removed, and were adapted to repository-relative paths without intentionally changing the underlying project logic.

## Execution order

Run the notebooks from the repository root or from inside `notebooks/` in this order:

```text
01_hsv_calibration.ipynb
02_tracking_pipeline.ipynb
03_tactical_metrics.ipynb
```

## Canonical paths

The repository-ready workflow uses:

```text
models/best.pt
data/input/sample.mp4
configs/botsort.yaml
outputs/tracking_output.csv
outputs/tracking_video.mp4
outputs/metrics/
```

The path-resolution cells account for execution either from the repository root or from inside the `notebooks/` directory.
