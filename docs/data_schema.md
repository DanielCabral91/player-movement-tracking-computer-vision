# Tracking data schema

The tracking pipeline exports a frame-level CSV used by the downstream tactical-analysis notebook.

## Canonical output path

`outputs/tracking_output.csv`

## Columns

| Column | Type | Description |
|---|---|---|
| `frame` | integer | Video frame index. |
| `time_s` | float | Video time in seconds. |
| `jogador` | integer | Public player / tracking identifier assigned by the project ID-management layer. |
| `equipa` | string | Team assignment (`A` or `B`). |
| `img_x` | float | Horizontal image coordinate of the player's estimated foot point. |
| `img_y` | float | Vertical image coordinate of the player's estimated foot point. |
| `coord_x` | float / empty | Normalised pitch x-coordinate estimated through the geometric mapping. |
| `coord_y` | float / empty | Normalised pitch y-coordinate estimated through the geometric mapping. |
| `conf` | float | Object-detection confidence. |
| `cov_teamA` | float | Fraction of the jersey ROI matching Team A's configured HSV range. |
| `cov_teamB` | float | Fraction of the jersey ROI matching Team B's configured HSV range. |

## Coordinate convention

The tracking notebook writes pitch coordinates normalised to approximately `[0, 1]` when a usable homography is available. Rows can contain empty pitch-coordinate fields when a frame does not have a valid geometric mapping.

The tactical-metrics notebook converts those normalised values to the 105 m × 68 m pitch convention used in the project visualisations.

## Data-quality caveat

The public identifier is an engineering stabilisation layer built on top of tracker IDs. It reduces ID proliferation and some identity switches, but it should not be treated as guaranteed person-level identity across an entire match.
