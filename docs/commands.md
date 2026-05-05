# Command Reference

Practical commands for day-to-day work on this project without AI assistance.

---

## Quarto slides

### Live preview while editing
```bash
conda activate <env-name>
cd ~/projects/<project>
cd docs/slides && quarto preview
# Opens a browser tab that hot-reloads as you save the .qmd file
# Ctrl+C to stop
```

### Render to final HTML
```bash
cd docs/slides && quarto render
# Output: docs/slides/presentation.html
```

### View the slides
Open `docs/slides/presentation.html` in your browser. The file is fully self-contained — email or share it as-is.

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

![](../../results/figs/your_figure.png){fig-alt="description"}
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

### Export to PDF / PPTX

```bash
# PPTX (native Quarto)
cd docs/slides && quarto render presentation.qmd --to pptx

# PDF via decktape (requires playwright Chromium)
decktape reveal presentation.html out.pdf --size 1280x720 \
  --chrome-path ~/.cache/ms-playwright/chromium-*/chrome-linux*/chrome \
  --chrome-arg=--no-sandbox --chrome-arg=--disable-setuid-sandbox
```

---

## Quarto draft document

The HTML draft (methods/results write-up for circulation) lives in `docs/draft/`.

```bash
cd docs/draft && quarto preview          # live preview
cd docs/draft && quarto render            # build HTML in place
```

Output: `docs/draft/draft_methods_results.html` (self-contained).

---

## Figures workflow

```bash
# 1. Copy a keeper figure into the tracked folder
cp processing/<run>/figures/my_plot.png results/figs/

# 2. Reference it from a slide:
#    docs/slides/presentation.qmd → ../../results/figs/my_plot.png
#    docs/draft/draft_methods_results.qmd → ../../results/figs/my_plot.png

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
git add docs/slides/presentation.qmd     # stage a specific file
git add results/figs/                    # stage a whole folder
git commit -m "Brief description of what changed"
git push
```

### Pull latest changes (e.g., after working on another machine)
```bash
git pull
```

### See recent history
```bash
git log --oneline -10
```

### Undo edits to a file before committing
```bash
git restore docs/slides/presentation.qmd
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
docs/slides/presentation.qmd       ← edit slides here
docs/slides/presentation.html      ← rendered slides (auto-generated)
docs/draft/draft_methods_results.qmd  ← edit draft write-up here
docs/draft/*.html                  ← rendered draft (auto-generated)
results/figs/                       ← copy keeper figures here (tracked)
docs/overview.md                    ← update after significant progress
docs/sessions/                      ← drop a session log after each AI session
docs/methods.md                     ← analytical methods applied and planned
docs/methods/                       ← method PDFs and supplementary notes
papers/index.md                     ← literature table
envs/                               ← conda env .yml files
scripts/                            ← analysis scripts
```
