# Reproducibility

This repository documents a research prototype developed for the 2025 final project **Player Movement Tracking using Computer Vision**.

## Reproduction prerequisites

To reproduce the project workflow, a local user needs:

1. Python 3.10+ and the packages listed in `requirements.txt`;
2. the trained YOLO weights at `models/best.pt`;
3. a permitted football video at `data/input/sample.mp4`;
4. match-specific HSV ranges for both teams;
5. the tracker configuration under `configs/botsort.yaml`.

## Execution order

Run the notebooks in this order:

1. `notebooks/01_hsv_calibration.ipynb`
2. `notebooks/02_tracking_pipeline.ipynb`
3. `notebooks/03_tactical_metrics.ipynb`

The tracking stage should write:

- `outputs/tracking_output.csv`
- `outputs/tracking_video.mp4`

The metrics stage should write figures and animations under `outputs/metrics/`.

## What is not bundled in Git history

The repository intentionally excludes:

- model weights (`*.pt`);
- raw broadcast video;
- generated videos and GIFs;
- large derived datasets;
- local credentials.

These exclusions keep Git history lightweight and avoid redistributing third-party media or artefacts whose licence may differ from the repository documentation.

## Exact reproducibility limits

Exact numerical reproduction cannot be guaranteed from the public repository alone unless the same trained weights, source clip, HSV calibration and software versions are used. Broadcast camera motion, detector confidence, tracker behaviour and geometric estimation can all change downstream outputs.

The repository therefore targets **workflow reproducibility and methodological transparency**, not a claim of deterministic reproduction across arbitrary videos.
