# grahamgreene88.github.io

This is a Quarto website that serves as a personal portfolio. It outlines some information about myself,
my background and journey through the MDS program so far. It also includes some very simple analysis in R and Python
as well as a portfolio project.

## Requirements

Tested on macOS 26.6.2 with:

- Quarto 1.10.18 — https://quarto.org/docs/get-started/
- uv 0.12.7 (installs Python 3.14.7 for the project automatically) — https://docs.astral.sh/uv/getting-started/installation/
- R 4.6.1 (renv installs itself on first run) — https://cran.r-project.org/
- git (on macOS: `xcode-select --install`)

## Build

Run all commands from a terminal (shell) in order. After the `cd`, all commands 
run from the repository root. The `Rscript -e` line runs R code from the shell;
the first time R starts in this folder, renv installs itself before restoring packages.

    git clone git@github.com:grahamgreene88/grahamgreene88.github.io.git
    # or, without an SSH key: git clone https://github.com/grahamgreene88/grahamgreene88.github.io.git
    cd grahamgreene88.github.io
    uv sync
    Rscript -e 'renv::restore(prompt = FALSE)'
    uv run quarto render

## View the site

The built site is written to `docs/`. This folder is committed to the
repository because GitHub Pages serves the live site from it; running
`uv run quarto render` regenerates it from the source files.

To view the site locally, start a preview server from the repository root:

    uv run quarto preview

This opens the preview at a local address in your browser automatically. 
The preview updates when you edit and save a source file. Press `Ctrl+C` in 
the terminal to stop the server.

## Publishing (maintainer only)

The live site is served by GitHub Pages from the `docs/` folder on the
`main` branch. To update it, render and push the regenerated `docs/`:

    uv run quarto render
    git add docs
    git commit -m "Rebuild site"
    git push

## Data

The Palmer Penguins dataset comes bundled with the `palmerpenguins` package
(installed by `renv::restore()` for R and `uv sync` for Python), so rendering
does not download any data.

The setup steps do need a network connection: `uv sync`, renv's first-run
bootstrap, and `renv::restore()` download packages from PyPI and CRAN.
After setup, `uv run quarto render` works offline.

