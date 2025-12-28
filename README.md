# LB3TH - RF & Electronics Lab Website

A Quarto-based website for documenting RF and electronics experiments.

## Prerequisites

- [Quarto](https://quarto.org/docs/get-started/) (v1.4+)
- [uv](https://docs.astral.sh/uv/) for Python environment management
- R (optional, for R code blocks)

## Quick Start

```bash
# Install Python dependencies
uv sync

# Preview the site locally
quarto preview
```

## Directory Structure

```
├── _quarto.yml          # Site configuration
├── index.qmd            # Homepage
├── about.qmd            # About page
├── contact.qmd          # Contact page
├── styles.scss          # Custom styling
├── lab/                 # Lab notes (blog-style)
│   ├── index.qmd        # Lab notes listing
│   └── YYYY-MM-DD-*/    # Individual posts
├── projects/            # Project pages
│   ├── index.qmd        # Projects listing
│   └── *.qmd            # Individual projects
├── mylab/               # Lab overview section
│   ├── index.qmd        # Lab overview
│   └── equipment/       # Equipment details
├── pyproject.toml       # Python dependencies
└── _freeze/             # Cached computation results
```

## Adding Content

### Adding a Lab Note

1. Create a new folder in `lab/` with format `YYYY-MM-DD-title/`:
   ```bash
   mkdir lab/2024-12-30-my-experiment
   ```

2. Create `index.qmd` inside with this front matter:
   ```yaml
   ---
   title: "My Experiment Title"
   description: "Brief description for listings"
   date: 2024-12-30
   categories: [project-name]  # Optional: link to projects
   ---

   Your content here...
   ```

3. Add images in the same folder and reference them:
   ```markdown
   ![Caption](image.jpg)
   ```

### Adding a Project Page

1. Create a new `.qmd` file in `projects/`:
   ```bash
   touch projects/my-project.qmd
   ```

2. Add front matter:
   ```yaml
   ---
   title: "My Project"
   description: "Brief project description"
   ---
   ```

3. To include related lab notes, add a listing:
   ```yaml
   ---
   title: "My Project"
   description: "Brief project description"
   listing:
     id: related-notes
     contents: ../lab
     type: default
     sort: "date desc"
     include:
       categories: "my-project"
   ---

   Your project content...

   ## Related Lab Notes

   ::: {#related-notes}
   :::
   ```

### Adding Equipment Pages

1. Create a new `.qmd` in `mylab/equipment/`
2. Add it to the sidebar in `_quarto.yml`:
   ```yaml
   sidebar:
     - id: mylab
       contents:
         - section: "Equipment"
           contents:
             - mylab/equipment/your-new-page.qmd
   ```

## Using R and Python

### Python Code Blocks

```{python}
#| label: fig-example
#| fig-cap: "Example plot"

import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(0, 10, 100)
plt.plot(x, np.sin(x))
plt.show()
```

### R Code Blocks

```{r}
#| label: tbl-example

# Create a simple table
data.frame(
  Frequency = c(7.0, 7.1, 7.2),
  Power = c(-3, 0, -3)
)
```

### Code Block Options

Common options for code blocks:

- `#| label: fig-name` - Reference label for figures
- `#| fig-cap: "Caption"` - Figure caption
- `#| echo: false` - Hide code, show only output
- `#| eval: false` - Show code, don't run it
- `#| warning: false` - Suppress warnings

## Computation Workflow (Freeze)

This site uses `freeze: auto` for computations. This means:

1. **Local rendering**: Code runs on your machine when you `quarto render`
2. **Results cached**: Output saved in `_freeze/` directory
3. **Commit cache**: Include `_freeze/` in git commits
4. **Fast deployment**: Netlify builds without running computations

### Workflow

```bash
# Edit your .qmd file with R/Python code
# Render locally (runs computations)
quarto render

# Commit both source and frozen results
git add .
git commit -m "Add new lab note"
git push
```

### Force Re-computation

To re-run a specific document:
```bash
quarto render lab/2024-12-28-experiment/index.qmd --execute
```

To re-run everything:
```bash
quarto render --execute
```

## Local Preview

```bash
# Start live preview server
quarto preview

# Preview opens at http://localhost:4000
```

## Deployment

The site is configured for Netlify deployment:

1. Push to GitHub
2. Netlify builds and publishes automatically

Build command: `quarto render`
Publish directory: `_site`

## Tags/Categories

Lab notes can belong to multiple projects using `categories`:

```yaml
categories: [vhf-antenna, field-day]
```

Project pages can filter by category:

```yaml
listing:
  include:
    categories: "vhf-antenna"
```

## Customization

### Fonts

Edit `styles.scss` to change fonts. Currently using:
- **Body**: Roboto
- **Code**: JetBrains Mono

### Theme

The site uses the Cosmo theme with custom styling. Edit `styles.scss` for colors and styling.
