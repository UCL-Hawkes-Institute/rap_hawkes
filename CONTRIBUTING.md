# Contributing to RAP @ Hawkes

Thanks for helping out with the site! This guide covers how to preview the site locally and how to add or update content.

The site is built with [Jupyter Book 2](https://jupyterbook.org) (powered by [MyST](https://mystmd.org)) and deployed to GitHub Pages automatically whenever changes are merged into `main`.

## Local setup

You will need:

- Your favourite way of installing and running a Python environment. We recommend and assume use of [uv](https://docs.astral.sh/uv/getting-started/installation/).

Then clone the repository and install the dependencies:

```bash
git clone https://github.com/UCL-Hawkes-Institute/rap_hawkes.git
cd rap_hawkes
uv sync
```

## Previewing the site

Start a local server with live reload:

```bash
uv run jupyter-book start
```

or activate the environment and run the command directly:

```bash
jupyter-book start
```

Then open <http://localhost:3000>. Stop the server with `Ctrl+C`.

### Previewing while you edit

Leave `jupyter-book start` running while you work. It watches the project for changes, so each time you save a file the site rebuilds and the open page refreshes in your browser.

A typical setup:

1. Run `uv run jupyter-book start` in a terminal and leave it running.
2. Open the page you're working on at <http://localhost:3000>, with your editor and browser side by side.
3. Edit and save. The browser updates within a second or two, and any warnings (such as a broken link or a missing file) are printed in the terminal.

If you use VS Code, you can keep the preview inside the editor: open the Command Palette (`Cmd+Shift+P` on macOS, `Ctrl+Shift+P` on Windows/Linux), run **Simple Browser: Show** and enter `http://localhost:3000`. Then drag the tab to one side of your editor. The [MyST-Markdown extension](https://marketplace.visualstudio.com/items?itemName=ExecutableBookProject.myst-highlight) also adds syntax highlighting for MyST directives.

> [!NOTE]
> VS Code's built-in Markdown preview doesn't understand MyST directives such as `{note}` or `{iframe}`, so use the local server to see how pages will actually look.

If a change to `myst.yml` (such as the table of contents) doesn't show up, stop the server and start it again.

To run the same build as the deploy workflow (useful for checking for errors before opening a PR):

```bash
uv run jupyter-book build --html
```

The output goes to `_build/html`. Warnings and errors (e.g. broken links or missing files) are printed in the terminal.

If the site looks stale or out of date, delete the `_build` folder and run the command again.

## Project structure

```text
├── myst.yml               # Site config and table of contents
├── README.md              # Home page and GitHub README
├── workshops/
│   ├── index.md           # Workshops landing page
│   ├── 2025-2026/
│   │   ├── index.md       # Series overview and schedule table
│   │   ├── 1_python/
│   │   │   └── index.md   # One page per workshop
│   │   └── ...
│   └── 2026-2027/
│       └── index.md
├── resources/             # Useful links, VS Code extensions, etc.
└── assets/                # Logo and custom CSS
```

Pages are written in [MyST Markdown](https://mystmd.org/guide/typography), which supports directives such as `{note}`, `{iframe}` and `{literalinclude}`. The existing workshop pages are good examples to copy from.

## Adding content

### A new workshop

1. Create a folder in the relevant academic year, named `<number>_<topic>`, containing an `index.md`, for example `workshops/2026-2027/1_intro/index.md`.
2. Start the page with a heading in the form `# 1. Workshop title`, followed by the date and a short summary. Add the recording, slides and any code examples as sections below.
3. Put any supporting files (code examples, images, slides) alongside the `index.md` in the same folder.
4. Update the schedule table in that year's `index.md` to link to the new page.

You don't need to edit `myst.yml`. Workshop folders are picked up automatically by the `workshops/<year>/*/index.md` pattern and sorted by folder name.

### A new academic year

1. Create `workshops/<year>/index.md` (for example `workshops/2027-2028/index.md`) with an overview and a schedule table. The previous year's page is a good starting point.
2. Add an entry for it to the `toc` in `myst.yml`, above the previous years:

   ```yaml
   - title: "2027/28"
     file: workshops/2027-2028/index.md
     children:
       - pattern: "workshops/2027-2028/*/index.md"
         sort: "ascending"
   ```

3. Update the schedule and "Previous series" sections in `README.md`.

### Resources

Add a link or VS Code extension to the relevant file in `resources/`. Any new `.md` file in that folder appears automatically under **Resources** in the sidebar.

## Submitting changes

1. Create a branch from `main`:

   ```bash
   git switch main
   git pull
   git switch -c <your-name>/<short-description>
   ```

2. Make your changes and check them locally with `uv run jupyter-book build --html`.
3. Commit, push your branch and open a pull request against `main`.
4. Once the PR is reviewed and merged, the [deploy workflow](.github/workflows/deploy.yml) builds and publishes the site. You can follow its progress in the **Actions** tab on GitHub.

If you have questions, or ideas for the site that you'd like to discuss first, please open an issue.
