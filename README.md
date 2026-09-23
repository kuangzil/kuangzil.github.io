# kuangzil.github.io

This repository contains my Quarto personal website for DSCI 521. It includes blog posts, rendered GitHub Pages output, and reproducible R and Python environments for the computational posts.

## Required Software

Install these tools before building the site:

- Quarto 1.10.18
- uv 0.12.13
- R 4.6.1
- Git

The Python packages are restored by `uv sync` from `uv.lock`. The R packages are restored by `renv::restore()` from `renv.lock`; `renv` bootstraps itself from the project files.

## Build From a Fresh Clone

Run these commands in a terminal:

```sh
git clone git@github.com:kuangzil/kuangzil.github.io.git
cd kuangzil.github.io
uv sync
```

Then restore the R environment from the repository root:

```sh
Rscript -e 'renv::restore(prompt = FALSE)'
```

Render the site from the repository root using the project Python environment:

```sh
uv run quarto render
```

The rendered website is written to `docs/`. To preview it locally, run:

```sh
uv run quarto preview
```

Quarto will print a local URL such as `http://localhost:4200`.

## Data Sources

The computational posts use package-bundled datasets, so no data files need to be downloaded separately and the build does not fetch data from the network at render time.

- Python post: [Iris plants dataset](https://scikit-learn.org/stable/datasets/toy_dataset.html#iris-plants-dataset), bundled with `scikit-learn` under the BSD 3-Clause license.
- R post: [`mtcars`](https://stat.ethz.ch/R-manual/R-devel/library/datasets/html/mtcars.html), bundled with R's `datasets` package.
