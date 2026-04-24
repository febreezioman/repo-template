# Project Name

Brief description of the project.

## AI guidelines

See [`AI.md`](AI.md) for the protocol any AI assistant should follow in this project (works with Claude, Codex, local models, etc.).

## Directory structure

```
raw/          # Raw, unmodified input data
processing/   # Intermediate files generated during analysis
out/          # Final output files
results/
  figs/       # Figures and plots
  slides/     # Presentation materials
envs/         # Conda environment files (.yml)
scripts/      # Analysis scripts
docs/
  overview.md     # Living project overview — updated each session
  sessions/       # Per-session AI logs
  methods/        # Detailed method / pipeline notes
```

## Setup

```bash
conda env create -f envs/environment.yml
conda activate <env-name>
```

## Usage

Describe how to run the analysis.
