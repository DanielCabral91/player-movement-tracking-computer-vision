# Notebooks

The original project is organised around three Jupyter workflows:

1. `01_hsv_calibration.ipynb` — interactive HSV calibration for team colours.
2. `02_tracking_pipeline.ipynb` — YOLOv8 detection, BoT-SORT tracking, ID management, team classification, coordinate estimation and CSV/video export.
3. `03_tactical_metrics.ipynb` — tactical and physical metrics calculated from the generated tracking CSV.

## Repository import policy

Notebook outputs are removed before version control so the repository stores source logic rather than large embedded plots, videos or execution artefacts.

The HSV calibration notebook has already been normalised and committed in this setup branch. The two larger analysis notebooks should be imported as cleaned, output-free versions before the setup branch is merged. Their original project files are preserved separately during this repository migration.

## Path convention

The repository-ready notebooks use relative paths:

```text
../models/best.pt
../configs/botsort.yaml
../data/input/sample.mp4
../outputs/tracking_data.csv
../outputs/tracking_demo.mp4
```

This avoids machine-specific paths and makes the workflow easier to reproduce after cloning.
