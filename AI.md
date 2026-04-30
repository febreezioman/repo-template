# AI Guidelines

This file applies to any AI assistant working in this project (Claude, Codex, local models, etc.).

## Start of every session

1. **`git pull`** — sync the repo before doing anything else.
2. Read `docs/overview.md` — project goals, current status, and decisions made so far.
3. Read the **most recent file** in `docs/sessions/` — it summarises what happened last session and what to pick up next.
4. Ask the user to clarify the goal for this session if it is not already clear.

## During a session

- `docs/overview.md` is the source of truth for project state.
- Non-trivial methods and pipelines → document in `docs/methods/`.
- Prefer reproducible steps: conda environments go in `envs/`, scripts in `scripts/`, raw data stays unmodified in `raw/`.

## End of every session

1. **Create a session file** at `docs/sessions/YYYY-MM-DD_<brief-topic>.md` (see template below).
2. **Update `docs/overview.md`** — reflect any progress, decisions, or change of direction.
3. **`git add` + `git commit`** — commit all new/changed tracked files with a short message describing what changed.
4. Briefly tell the user what was written and what is flagged for next session.

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

## Figures and documents

See `docs/commands.md` for figures workflow (copy to `results/figs/`, commit) and Quarto render commands.

## Directory reference

| Path | Purpose |
|------|---------|
| `raw/` | Original input data — never modified |
| `processing/` | Intermediate files generated during analysis |
| `out/` | Final output files |
| `results/figs/` | Figures and plots — tracked |
| `envs/` | Conda environment `.yml` files |
| `scripts/` | Analysis scripts |
| `docs/overview.md` | Living project overview — update each session |
| `docs/sessions/` | Per-session logs |
| `docs/methods/` | Detailed notes on methods, tools, or pipelines |
