# Limitations

This project is a research prototype built from conventional broadcast footage rather than a calibrated full-pitch tracking system. The limitations below materially affect interpretation of the outputs.

## Player identity

Broadcast players regularly leave and re-enter the frame. Occlusion and physical overlap can produce identity switches, ID fragmentation or incorrect re-assignment. The custom ID-management layer reduces these problems but does not eliminate them.

## Ball detection

The ball is substantially harder to detect consistently than players because of its small apparent size, motion blur and frequent occlusion. The final project therefore did not claim reliable ball tracking.

## Camera motion and pitch visibility

Broadcast footage includes pan, zoom and changing viewing angles. Only part of the pitch is visible at a given time, so geometric references may be insufficient for stable coordinate mapping.

## Homography / coordinate estimation

Pitch coordinates are estimates derived from visual field references. When lines or reference structures are missing, noisy or partially visible, coordinate error increases. Downstream physical and tactical metrics inherit this uncertainty.

## Team classification

The final workflow uses manually calibrated HSV colour ranges because that approach was more consistent than the clustering approach tested in the project. HSV classification remains sensitive to shadows, lighting changes and similar kit colours.

## Distance covered

Distance is calculated from estimated frame-to-frame positional changes. It should be interpreted as a prototype approximation rather than a validated GPS-equivalent workload measure.

## Tactical metrics

Average positions, heatmaps, Zone Control, Defensive Coverage Index (ICD) and Team Surface depend on the quality and completeness of the positional tracking. They are analytical aids, not ground-truth tactical measurements.

## Compute constraints

The academic project was developed under limited compute resources. This constrained model training, ball-detection improvement and full-match processing.

## Scope

The repository demonstrates an accessible computer-vision workflow for football analysis. It is not intended to compete with calibrated multi-camera commercial tracking systems or to provide production-grade real-time event detection.
