## Template Website
https://digital-metabolic-twin-centre.github.io/docTemplate/index.html

## Documentation Template (Sphinx + gh-pages CI)

This repository is a template for new projects with documentation generated from `.rst` files using Sphinx.

## CI behavior

- CI runs only on pushes to the `gh-pages` branch.
- CI builds docs from `Documentation/`.
- CI copies generated HTML to branch root and commits it.

Workflow file:
- `.github/workflows/sphinx-docs.yml`

## How to use this template in a project

### Option A: New repository from this template

1. Create a repository from this template.
2. Ensure branch `gh-pages` exists.
3. In GitHub repo settings, open **Pages** and set source to:
   - Branch: `gh-pages`
   - Folder: `/ (root)`
4. Edit files in `Documentation/`.
5. Commit and push to `gh-pages`.
6. Wait for Actions to finish, then open your Pages URL.

### Option B: Add this setup to an existing repository

Run these commands in your own repository:

```bash
# create gh-pages branch if it does not exist yet
git checkout --orphan gh-pages

# remove tracked files from the orphan branch index
# (safe for branch setup; your other branches are untouched)
git rm -rf .

# copy this template content into the repo root
# then commit and push
git add .
git commit -m "Initialize Sphinx docs template on gh-pages"
git push -u origin gh-pages
```

Then in GitHub Pages settings choose:
- Branch: `gh-pages`
- Folder: `/ (root)`

After that, each push to `gh-pages` rebuilds and republishes docs.

## Documentation structure

- `Documentation/index.rst` main landing page
- `Documentation/project/` project placeholders
- `Documentation/logbook/` weekly update placeholders

## Local build

```bash
cd Documentation
python -m pip install -r requirements.txt
make html
```

Open `Documentation/_build/html/index.html`.
