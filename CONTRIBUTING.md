# Contribution Guide

This document describes how you can contribute documentation to Promitor.

The documentation for Promitor is stored in `/docs`.

## What technologies are we using?

Documentation is written in [Markdown](https://en.wikipedia.org/wiki/Markdown) and uses [MkDocs for Material](https://squidfunk.github.io/mkdocs-material) to generate a static website that is served with [GitHub Pages](https://pages.github.com/) from the [`live-docs` branch](https://github.com/promitor/docs/tree/live-docs).

In addition, [Mike](https://github.com/jimporter/mike) is being used to leverage versioned documentation.

For every new Promitor version, a new Git tag is created which [automatically builds and pushes a new doc version](https://github.com/promitor/docs/actions/workflows/publish-new-version.yml). Next to that, every push on `main` branch will update the `unreleased` version of the documentation that is [automatically published through GitHub Actions](https://github.com/promitor/docs/actions/workflows/publish-next.yml).

## Creating a PR with live preview

Every PR will automatically build and deploy a preview version of the documentation for you with [Netlify](https://netlify.com). This allows you to easily contribute changes without having to fully configure your local environment.

## Running the documentation locally

- Install Python:

```shell
⚡ tkerkhove@tomkerkhove C:\promitor
❯  choco install python
```

- Install dependencies

```shell
⚡ tkerkhove@tomkerkhove C:\promitor
pip install -r requirements.txt
```

- Serve the documentation:

```shell
⚡ tkerkhove@tomkerkhove C:\promitor
mkdocs serve
```
