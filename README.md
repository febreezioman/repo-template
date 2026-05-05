# Project Name

Brief description of the project.

See [`AI.md`](AI.md) for the AI assistant protocol used in this project.

## Directory structure

```
raw/            # Raw input data (gitignored)
out/            # Pipeline output (gitignored)
processing/     # Intermediate files (gitignored)
refs/           # Reference data, e.g. genome (gitignored)
results/
  figs/         # Selected figures (tracked)
envs/           # Conda environment files
scripts/        # Analysis scripts
papers/         # Literature index and reading notes
docs/
  overview.md   # Living project overview
  methods.md    # Analytical methods applied and planned
  methods/      # Method PDFs and supplementary notes
  sessions/     # Per-session AI logs
  slides/       # Slide source (Quarto .qmd) and rendered HTML
  draft/        # Draft methods/results source and rendered HTML
```

## Setup

```bash
conda env create -f envs/<env-name>.yml
conda activate <env-name>
```

## Slides

```bash
cd docs/slides && quarto render
# Output → docs/slides/presentation.html
```

## Draft methods/results

```bash
cd docs/draft && quarto render
# Output → docs/draft/draft_methods_results.html
```
