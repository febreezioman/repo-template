# Command Reference

Practical commands for day-to-day work on this project without AI assistance.

---

## Quarto slides

### Live preview while editing
```bash
conda activate <env-name>
cd ~/projects/<project>
cd slides && quarto preview
# Opens a browser tab that hot-reloads as you save the .qmd file
# Ctrl+C to stop
```

### Render to final HTML
```bash
cd slides && quarto render
# Output: results/slides/presentation.html
```

### View the slides
Open `results/slides/presentation.html` in your browser. The file is fully self-contained — email or share it as-is.

### Keyboard shortcuts inside rendered slides
| Key | Action |
|-----|--------|
| `→` / `Space` | Next slide |
| `←` | Previous slide |
| `f` | Fullscreen |
| `s` | Speaker notes view |
| `o` | Slide overview |
| `Esc` | Exit fullscreen / overview |

### Add a new slide
```markdown
## Slide title

- Bullet point

![](../results/figs/your_figure.png){fig-alt="description"}
```

### Two-column layout
```markdown
::: columns
::: {.column width="50%"}
Left content or figure
:::
::: {.column width="50%"}
Right content or figure
:::
:::
```

---

## Figures workflow

```bash
# 1. Copy a keeper figure into the tracked folder
cp processing/<run>/figures/my_plot.png results/figs/

# 2. Reference it in slides/presentation.qmd as:
#    ../results/figs/my_plot.png

# 3. Commit it
git add results/figs/my_plot.png
git commit -m "Add keeper figure: my_plot"
git push
```

---

## Git — daily workflow

### Check what has changed
```bash
git status          # which files are modified / untracked
git diff            # line-by-line changes in tracked files
```

### Save your work
```bash
git add slides/presentation.qmd      # stage a specific file
git add results/figs/                # stage a whole folder
git commit -m "Brief description of what changed"
git push
```

### Pull latest changes (e.g. after working on another machine)
```bash
git pull
```

### See recent history
```bash
git log --oneline -10
```

### Undo edits to a file before committing
```bash
git restore slides/presentation.qmd
```

### Check what is gitignored
```bash
git status --ignored
```

---

## Conda environment

### Activate
```bash
conda activate <env-name>
```

### Update the spec after installing new packages
```bash
conda activate <env-name>
conda env export --no-builds > envs/<env-name>.yml
git add envs/<env-name>.yml
git commit -m "Update conda env"
git push
```

### Recreate on a new machine
```bash
conda env create -f envs/<env-name>.yml
conda activate <env-name>
```

---

## GitHub

### Clone on a new machine
```bash
gh auth login        # first time only
git clone https://github.com/<user>/<repo>.git
```

### Open the repo in the browser
```bash
gh repo view --web
```

---

## Quick layout reference

```
slides/presentation.qmd   ← edit slides here
results/figs/              ← copy keeper figures here (tracked)
results/slides/            ← rendered HTML (auto-generated)
docs/overview.md           ← update after significant progress
docs/sessions/             ← drop a session log after each AI session
docs/methods/              ← method and pipeline notes
papers/index.md            ← literature table
envs/                      ← conda env .yml files
scripts/                   ← analysis scripts
```
