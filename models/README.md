# Models

The original project uses a custom-trained **YOLOv8n** detector for football objects.

## Expected local file

Place the trained weights at:

```text
models/best.pt
```

The model file is intentionally excluded from regular Git history through `.gitignore`.

## Why weights are not committed

Model artefacts are handled separately because they are binary, can grow quickly across experiments and may be subject to dataset, framework or publication constraints.

For a future public release, the preferred approach is to publish a versioned model asset through **GitHub Releases** together with:

- training dataset reference;
- model architecture;
- class definitions;
- training configuration;
- evaluation metrics;
- framework version;
- licence / redistribution terms.

## Original project context

The academic report states that the detector was trained with a labelled football dataset obtained through Roboflow and used to detect players, referees and the ball.
