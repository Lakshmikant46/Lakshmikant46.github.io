# Laxmikanta Sarangi — personal academic website

A minimal, static academic site built with [Jekyll](https://jekyllrb.com/) and hosted on
GitHub Pages. Five pages: **Home, Research, CV, Teaching, Contact**.

Live site (once deployed): **https://lakshmikant46.github.io**

---

## How the content is organised

You almost never need to touch HTML. Content lives in plain-text data files:

| What you want to change | File to edit |
| --- | --- |
| Papers (add / edit / reorder) | `_data/publications.yml` |
| Teaching entries | `_data/teaching.yml` |
| Name, tagline, email, links, advisor | `_config.yml` |
| Home-page bio & research interests | `index.html` (text near the top) |
| The CV file shown on the CV page | `_config.yml` → `cv_file:` (see below) |
| Colours / fonts / layout | `assets/css/style.css` |

> After editing **`_config.yml`** you must restart the local server for changes to appear.
> Edits to `_data/*.yml` and the page files refresh automatically while the server runs.

---

## Add a new paper

Open `_data/publications.yml`, copy an existing block, and change the fields. Papers are
grouped into five sections, rendered in this order:

`featured` → `publications` → `working_papers` → `reviews` → `work_in_progress`

Example entry:

```yaml
working_papers:
  - title: "My New Paper Title"
    authors: "Laxmikanta Sarangi, Co-Author Name"   # your name is auto-bolded
    year: 2026
    venue: "Working paper."
    jel: "D22, L11"
    keywords: "markup, monopsony"
    pdf: "my-new-paper.pdf"      # put the file in assets/papers/  (leave blank if none)
    slides: ""                   # optional
    note: ""                     # optional small italic note
    abstract: >
      One paragraph. Keep the indentation; long lines are fine and will wrap.
```

To attach a PDF, drop it in `assets/papers/` and put its filename in the `pdf:` field.

---

## Update the CV

The CV page currently shows a "coming soon" notice. To publish your CV:

1. Put the PDF in `assets/cv/` — e.g. `assets/cv/laxmikanta-sarangi-cv.pdf`.
   *(Recommended: use a version with personal/referee phone numbers removed.)*
2. In `_config.yml` set:
   ```yaml
   cv_file: "laxmikanta-sarangi-cv.pdf"
   ```
3. Restart the server (or just push). An embedded PDF viewer and a **Download CV** button
   appear automatically.

---

## Run the site locally (preview before publishing)

Ruby 3.3 and Jekyll 4 are already installed on this machine. To preview, from this folder:

```powershell
.\serve.ps1
```

This starts the site at **http://127.0.0.1:4000/** and opens it in your browser. Leave the
window open while you work; edits reload on refresh. Press **Ctrl-C** to stop.

`serve.ps1` uses the installed Jekyll and ignores the `Gemfile` (that file is only for
GitHub's own build). On a new computer, install a "Ruby+Devkit" build from
<https://rubyinstaller.org/>, then `gem install jekyll` and use `serve.ps1` again.

**No Jekyll?** You don't strictly need a local preview — edit the files, push to GitHub
(below), and see the result live in about a minute; GitHub builds the site for you.

---

## Deploy to GitHub Pages

This is a **user site**, so the repository must be named exactly
`Lakshmikant46.github.io`.

First time:

```powershell
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/Lakshmikant46/Lakshmikant46.github.io.git
git push -u origin main
```

Then, on GitHub: **Settings → Pages →** set **Source = "Deploy from a branch"**,
**Branch = `main` / `(root)`**, and Save. Your site goes live at
**https://lakshmikant46.github.io** within a minute or two.

For later updates:

```powershell
git add .
git commit -m "Update research"
git push
```

### Want the address to read "laxmikantasarangi"?
GitHub Pages ties the free `*.github.io` address to your account name (`Lakshmikant46`).
To get a `laxmikantasarangi` address you would either **rename your GitHub account**, or
**add a custom domain** (e.g. `laxmikantasarangi.com`) under Settings → Pages → Custom
domain. No code changes are needed for a custom domain beyond adding a `CNAME` file.

---

## Placeholders still to fill in

- **Samiskhya citation details** — *done:* both published papers now read
  "Samiskhya, Vol. 15 (2026) … released on the 20th National Statistics Day, 29 June 2026".
  Add page numbers later if you get them.
- **Featured paper PDF & slides** — the markup/markdown paper has no compiled PDF yet.
  Export it from Overleaf and drop it in `assets/papers/`, then set `pdf:` (and `slides:`).
- **CV** — see "Update the CV" above.
- **Work-in-progress abstracts** — the two planned papers show a one-line note; add
  abstracts to `_data/publications.yml` when written.
- **Optional profile links** — Google Scholar, ORCID, LinkedIn, Twitter/X are blank in
  `_config.yml`; fill any you have and they appear automatically.
