# Player Movement Tracking using Computer Vision

> Computer vision pipeline for football player detection, multi-object tracking, team classification and tactical analysis from broadcast video.

**Final Project — Master in Big Data Applied to Football, Sports Data Campus (2025)**

**Authors:** Eduardo Cruz · Daniel Cabral · David Gonçalves · Guilherme Vieira

---

## Overview

This repository documents a football analytics prototype designed to transform conventional broadcast footage into structured positional data and interpretable tactical metrics.

The project combines **YOLOv8** object detection, **BoT-SORT** multi-object tracking, a custom **ID management layer**, **HSV-based team classification**, pitch-coordinate estimation and downstream tactical analysis.

The objective was not to reproduce an elite commercial tracking system, but to evaluate whether accessible, open-source computer-vision methods can provide a useful first layer of objective analysis for football environments with limited technical resources.

## Pipeline

```text
Broadcast video
      │
      ▼
YOLOv8 detection
(players / referees / ball)
      │
      ▼
BoT-SORT tracking
      │
      ▼
Custom ID management
      │
      ▼
HSV team classification
      │
      ▼
Pitch-coordinate estimation
      │
      ▼
Structured tracking CSV
      │
      ▼
Tactical & physical metrics
```

## Main outputs

The analysis layer derives metrics and visualisations including:

- Distance covered
- Average player positions
- Individual heatmaps
- Zone Control
- Defensive Coverage Index (ICD)
- Team Surface

The tracking dataset contains frame-level information such as time, player ID, team, image coordinates, estimated pitch coordinates and detection confidence.

## Repository structure

```text
.
├── README.md
├── AUTHORS.md
├── CITATION.cff
├── requirements.txt
├── .gitignore
├── configs/
│   └── botsort.yaml
├── notebooks/
│   ├── 01_hsv_calibration.ipynb
│   ├── 02_tracking_pipeline.ipynb
│   └── 03_tactical_metrics.ipynb
├── data/
│   └── README.md
├── models/
│   └── README.md
├── outputs/
│   └── README.md
├── reports/
│   └── README.md
└── docs/
    └── methodology.md
```

## Notebooks

The workflow is organised in execution order:

1. **`01_hsv_calibration.ipynb`** — interactive calibration of HSV colour ranges for the two teams.
2. **`02_tracking_pipeline.ipynb`** — detection, tracking, ID management, team classification and CSV/video export.
3. **`03_tactical_metrics.ipynb`** — tactical and physical metrics calculated from the generated tracking CSV.

The notebooks committed to this repository are cleaned versions of the project notebooks, with execution outputs removed and repository-relative paths used where appropriate.

## Installation

Python 3.10+ is recommended.

```bash
python -m venv .venv
```

### Windows

```bash
.venv\Scripts\activate
pip install -r requirements.txt
```

### macOS / Linux

```bash
source .venv/bin/activate
pip install -r requirements.txt
```

## Running the project

### 1. Add the trained model

Place the YOLO weights at:

```text
models/best.pt
```

The weights are intentionally not committed to Git history. See [`models/README.md`](models/README.md).

### 2. Add an input video

Place a permitted local test clip at:

```text
data/input/sample.mp4
```

Raw broadcast footage is not distributed in this repository. See [`data/README.md`](data/README.md).

### 3. Calibrate team colours

Run:

```text
notebooks/01_hsv_calibration.ipynb
```

### 4. Run tracking

Run:

```text
notebooks/02_tracking_pipeline.ipynb
```

Expected outputs are written under `outputs/`.

### 5. Calculate metrics

Run:

```text
notebooks/03_tactical_metrics.ipynb
```

## Technical notes

The original project used a labelled football dataset obtained through Roboflow to train a YOLOv8n detector. The model was then applied to broadcast clips from the DFL Bundesliga Data Shootout dataset.

A major engineering challenge was **identity instability**: players frequently leave and re-enter a broadcast frame, overlap during duels, or become partially occluded. The project therefore introduced an additional ID-management layer to reduce unrealistic ID proliferation and improve temporal consistency.

Team classification was tested with colour clustering and manually defined HSV ranges. Manual HSV calibration produced the more consistent results in the project and was retained in the final pipeline.

## Known limitations

This is a research prototype. Important limitations include:

- identity switches and re-identification errors under severe occlusion;
- broadcast camera pan, zoom and partial-pitch visibility;
- reduced reliability of ball detection compared with player detection;
- pitch-coordinate error when geometric references are insufficient;
- HSV team classification sensitivity to lighting, shadows and similar kit colours;
- computational constraints that limited model training and full-match processing.

These limitations are documented because they materially affect the interpretation of derived physical and tactical metrics.

## Reproducibility and data policy

Large model weights, raw broadcast footage and generated videos are excluded from normal Git history. This keeps the repository lightweight and avoids redistributing assets whose licensing may differ from the source code.

The project depends on third-party software and datasets, each of which remains subject to its own licence or terms of use. In particular, the included BoT-SORT configuration retains the upstream Ultralytics licence notice.

## Academic report

The final academic report is referenced under [`reports/README.md`](reports/README.md). Binary report files can be added separately once publication and authorship permissions are confirmed.

## Citation

If you reference this project, please use the metadata in [`CITATION.cff`](CITATION.cff).

## Licence

No repository-wide open-source licence has been granted yet. This is intentional because the project is co-authored and includes dependencies, datasets and model artefacts governed by separate terms. Until a licence is explicitly added, copyright remains with the respective authors and rights holders.
