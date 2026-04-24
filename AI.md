# AI Guidelines

This file applies to any AI assistant working in this project (Claude, Codex, local models, etc.).

## Start of every session

1. Read `docs/overview.md` — project goals, current status, and decisions made so far.
2. Read the **most recent file** in `docs/sessions/` — it summarises what happened last session and what to pick up next.
3. Ask the user to clarify the goal for this session if it is not already clear.

## During a session

- Keep `docs/overview.md` in mind as the source of truth for project state.
- If you introduce or use a non-trivial method, tool, or workflow, create or update its documentation in `docs/methods/`.
- Prefer reproducible steps: conda environments go in `envs/`, scripts in `scripts/`, raw data stays unmodified in `raw/`.

## End of every session

1. **Create a session file** at `docs/sessions/YYYY-MM-DD_<brief-topic>.md` (see template below).
2. **Update `docs/overview.md`** — reflect any progress, decisions, or change of direction.
3. Briefly tell the user what was written and what is flagged for next session.

### Session file template

```markdown
# Session — YYYY-MM-DD: <brief topic>

## Goal
What was this session trying to accomplish?

## What was done
- Bullet summary of steps taken and tools/scripts used.

## Results / findings
Key outcomes, numbers, or observations.

## Decisions made
Any choices that affect future work (parameters, tools selected, data excluded, etc.).

## Next session
What should be tackled next, and any open questions.
```

## Directory reference

| Path | Purpose |
|------|---------|
| `raw/` | Original input data — never modified |
| `processing/` | Intermediate files generated during analysis |
| `out/` | Final output files |
| `results/figs/` | Figures and plots |
| `results/slides/` | Presentation materials |
| `envs/` | Conda environment `.yml` files |
| `scripts/` | Analysis scripts |
| `docs/overview.md` | Living project overview — update each session |
| `docs/sessions/` | Per-session logs |
| `docs/methods/` | Detailed notes on methods, tools, or pipelines |

## Figures workflow

Pipeline output directories are typically **gitignored** (large intermediate files, local only).

When a figure is worth keeping:
1. Copy it to `results/figs/`: `cp processing/<run>/figures/foo.png results/figs/`
2. Reference it in `slides/presentation.qmd` as `../results/figs/foo.png`
3. `results/figs/` and `results/slides/` are tracked by git — figures and rendered slides are versioned together.

## Slides

Presentations are authored in `slides/presentation.qmd` using Quarto revealjs format.

```bash
cd slides && quarto render
# Output → results/slides/presentation.html
```

`embed-resources: true` (already set) produces a single self-contained HTML — shareable by email or link with no dependencies.

## What to document in `docs/methods/`

Create a file here whenever a method deserves more detail than fits in a session log:

- Non-default parameters and why they were chosen
- A pipeline or multi-step workflow
- Tool versions or known quirks
- QC thresholds and their rationale
