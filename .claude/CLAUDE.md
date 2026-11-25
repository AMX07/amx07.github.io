# amx07.github.io

Ansh Mittal's personal website, served by GitHub Pages straight from `main` (no build step for the HTML).

## Resume

- Source: `_resume/AnshMittal-resume.tex` (Jake Gutierrez-style template; compiles with Tectonic/XeTeX).
- Published PDF: `AnshMittal-master.pdf` at the repo root. Every "Resume" link on the site points to it.
- Never edit or commit `AnshMittal-master.pdf` by hand. The `Resume PDF` GitHub Action
  (`.github/workflows/resume.yml`) rebuilds it from the `.tex` on every push to `main`,
  commits it, and asks Pages to republish.
- On a pull request the same Action only checks that the resume compiles and attaches the PDF
  to the run as the `resume-pdf` artifact.

### Making a resume change

1. Branch from `main` and edit `_resume/AnshMittal-resume.tex`.
2. If `tectonic` is installed, build and look at it:
   `tectonic _resume/AnshMittal-resume.tex --outdir _resume/build` (the build folder is git-ignored).
3. Open a pull request. Wait for the `Resume PDF` check to pass; if `tectonic` isn't available locally,
   download the `resume-pdf` artifact (`gh run download <run-id> -n resume-pdf`) and check it.
4. Merge only when Ansh says to. After merging, the Action publishes the PDF; confirm with
   `curl -s https://amx07.github.io/AnshMittal-master.pdf` once the Pages build finishes.

### Resume rules

- Keep it to one page, with no line running past the right margin (the Action warns on "Overfull").
- Project bullets must use real, measured results from the linked repos. No placeholders like `[X]`.
- Don't use these words: study, investigate, system, pipeline, features, combine, modify, expand.
- Escape LaTeX special characters (`\%`, `\&`, `\$`, `\_`, `\#`).

## Website changes

- Plain HTML/CSS. The nav block is repeated on every page (`index.html`, `media.html`, `quotes.html`,
  `resume.html`, `thoughts.html`); keep them in sync.
- Work on a branch, open a pull request, and merge only when Ansh approves.
- Use `uv` for any Python (`uv run --no-project ...`, `uvx ...`), never pip or venv.
