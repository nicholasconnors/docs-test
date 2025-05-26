# Testing open source docs for open source projects

Testing making a documentation website using different packages and hosted on GitHub pages

### MkDocs
Installation:

`pip install mkdocs`

`pip install mkdocstrings-python` Lets you automatically include docstrings, method signatures, etc of code

`pip install markdown-include` Lets you include markdown files in other markdown files to reduce copy-pasting

`pip install mkdocs-jupyter` Lets you include Jupyter notebooks as pages

`pip install mkdocs-material` Provides a nicer theme and a lot of additional options

### How to set up bare minimum docs on your own repo

1. Install MkDocs
2. Create a folder in your repo named docs
3. Create index.md in that folder. Write anything inside it (this will be your home page)
4. In the root directory of your repo create a file named mkdocs.yml with the contents:
```
site_name: [Whatever you want to name your website]
nav:
  - Home: 'index.md'
```
5. Run `mkdocs server` from the terminal in the root directory of your repo to have a version of your site hosted locally

### How to publish a bare minimum GitHub pages site

1. Make the folder `.github/workflows` in your repo and copy `docs.yml` from this repo into there.
2. By pushing this file to your repo it will automatically run and generate the gh-pages branch. Check the `Actions` tab to ensure it worked.
3. Enable GitHub pages in `Settings>Pages`. Make sure the source is set to `Deploy from a branch` and that the selected branch is `gh-pages` with the root directory.
4. Your site will go live at \[your github username\].github.io/\[your repo name\]

Notes about the GitHub action:
- You might have to enable actions and/or workflow permissions I'm not sure what the default settings are
- The workflow expects that you will be doing dev work on a branch called `dev`, that the latest released version of your code is costed on a branch called `main` or `master`, and that all previous releases have their legacy code kept in a branch labeled with their version number `X.Y.Z` (semantic versioning)
- What I would do is, when your development branch is ready to be released (merged into main) create a new branch based on main with its version number as the name and then publish that branch and never touch it again. Then merge `dev` into `main`.
