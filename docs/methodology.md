# Methodology

## 1. Project objective

The prototype investigates whether standard football broadcast footage can be transformed into structured positional data and interpretable tactical information using accessible computer-vision methods.

The original workflow was implemented in **Python** using **Jupyter Lab**.

## 2. Detection

A labelled football dataset obtained through Roboflow was used to train a **YOLOv8n** model to detect the principal visual objects required by the pipeline: players, referees and the ball.

The project report records stronger performance for player and referee detection than for the ball. Ball detection was identified as a persistent difficulty because of its small visual footprint, occlusion and motion blur.

## 3. Multi-object tracking

The detector was combined with **BoT-SORT** to assign identities across frames.

Broadcast video created several practical problems:

- players frequently left and re-entered the camera frame;
- physical duels and overlap caused temporary identity merging;
- IDs could switch between players after occlusion;
- the tracker could create more active IDs than the realistic number of outfield players.

The project therefore added an **IDManager** layer intended to improve identity consistency. Its logic focused on limiting unrealistic ID proliferation, reusing previous identities when players reappeared and reducing identity exchanges after overlap.

## 4. Team classification

Two approaches were explored:

1. automatic colour clustering based on shirt HSV information;
2. manually defined HSV ranges for each team.

The final project retained manual HSV calibration because it produced more consistent team assignment in the evaluated clips.

## 5. Coordinate estimation

Detected player positions were mapped from image space toward a two-dimensional pitch representation. The project used pitch-line information and homography-related processing to estimate positional coordinates.

This stage is especially sensitive to broadcast pan, zoom, camera direction changes and incomplete pitch visibility. Derived coordinates should therefore be interpreted as prototype estimates rather than ground-truth tracking data.

## 6. Structured tracking output

The tracking pipeline exports a CSV containing frame-level information such as:

- frame number;
- timestamp;
- player ID;
- team;
- image coordinates;
- estimated pitch coordinates;
- detection confidence;
- team coverage-related values.

This structured output separates the computer-vision stage from the downstream analysis stage.

## 7. Tactical and physical analysis

The metrics notebook derives visual and numerical outputs including:

### Distance covered

An initial physical-load approximation derived from positional trajectories. Because coordinate error can accumulate, it should not be treated as equivalent to validated GPS or optical tracking data.

### Average positions

Mean positional locations used to support interpretation of team structure and player occupation.

### Heatmaps

Player-specific spatial-density visualisations used to represent zones of greater presence.

### Zone Control

A spatial-control representation estimating which areas of the pitch are relatively controlled by each team at a given moment. The project implementation does not incorporate all variables used by commercial pitch-control models.

### Defensive Coverage Index (ICD)

A collective-space indicator used to interpret whether a team is more compact or more dispersed over time.

### Team Surface

A representation of the area occupied collectively by a team, supporting interpretation of width, depth, compactness and expansion.

## 8. Main limitations

The project report identifies the following important constraints:

- moving broadcast cameras rather than fixed tactical cameras;
- incomplete pitch visibility;
- loss of geometric references during pan and zoom;
- unreliable ball detection;
- limited computation available for model training and long-video processing;
- sensitivity of shirt-colour classification to shadows and illumination;
- difficulty separating teams with visually similar kits;
- remaining tracking and re-identification errors.

These limitations directly affect the confidence with which tactical or physical outputs should be interpreted.

## 9. Intended scope

This repository should be understood as an **academic research prototype and portfolio project**, not as a production-grade validated tracking product. Its value lies in demonstrating an end-to-end workflow from video detection through structured data generation to football-specific analysis, while explicitly documenting the failure modes that remain to be solved.
