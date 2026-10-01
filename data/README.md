# Data

This directory documents the data expected by the project.

## Input video

The tracking notebook expects a local video at:

```text
data/input/sample.mp4
```

The original project evaluated the detector on broadcast clips from the **DFL Bundesliga Data Shootout** dataset. Raw broadcast footage is not redistributed here because dataset and media rights may restrict redistribution.

## Tracking output schema

The project-generated CSV contains the following fields:

| Column | Meaning |
|---|---|
| `frame` | Video frame index |
| `time_s` | Time in seconds |
| `jogador` | Player / tracking identifier |
| `equipa` | Assigned team |
| `img_x` | Horizontal image coordinate |
| `img_y` | Vertical image coordinate |
| `coord_x` | Estimated pitch x-coordinate |
| `coord_y` | Estimated pitch y-coordinate |
| `conf` | Detection confidence |
| `cov_teamA` | Team A coverage-related value |
| `cov_teamB` | Team B coverage-related value |

Generated CSVs should be written under `outputs/` rather than committed as raw experiment history.

## Reproducibility

To reproduce the original workflow you need:

1. a compatible football video;
2. the trained YOLO model weights;
3. HSV ranges appropriate for the two teams;
4. the tracking configuration under `configs/botsort.yaml`.
