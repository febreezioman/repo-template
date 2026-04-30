# Project Name

Brief description of the project.

See [`AI.md`](AI.md) for the AI assistant protocol used in this project.

## Directory structure

```
raw/            # Raw input data (gitignored)
out/            # Pipeline output (gitignored)
processing/     # Intermediate files (gitignored)
results/
  figs/         # Selected figures (tracked)
envs/           # Conda environment files
scripts/        # Analysis scripts
docs/
  overview.md          # Living project overview
  methods.md           # Analytical methods applied and planned
  sessions/            # Per-session AI logs
  methods/             # Method and pipeline notes
```

## Setup

```bash
conda env create -f envs/environment.yml
conda activate <env-name>
```

## Slides

```bash
cd slides && quarto render
# Output → results/slides/presentation.html
```
