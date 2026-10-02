# How to Edit Your Website — A Simple Guide

Your website files live in the folder **`E:\Lakshmikant46.github.io`**, and the live site
is at **https://lakshmikant46.github.io**.

Every change you ever make follows the **same three steps**:

1. **Edit** a file (usually just a text/data file — not code).
2. **Preview** it on your own computer (optional but nice).
3. **Publish** it with three commands. GitHub rebuilds the live site in about a minute.

---

## Step 0 — How to open PowerShell in the folder

You'll need this for previewing and publishing.

- Open **File Explorer** and go to `E:\Lakshmikant46.github.io`
- Click in the **address bar** at the top, type `powershell`, and press **Enter**.

A blue window opens, already pointing at the right folder.

---

## Step 1 — Which file do I edit?

| I want to change… | Open this file | With… |
| --- | --- | --- |
| Add / edit / remove a **paper** | `_data/publications.yml` | Notepad or VS Code |
| My **name, tagline, emails, links** (Scholar, LinkedIn, X) | `_config.yml` | Notepad or VS Code |
| My **Home-page bio** and research interests | `index.html` | Notepad or VS Code |
| **Teaching** entries | `_data/teaching.yml` | Notepad or VS Code |
| Replace my **CV** | put PDF in `assets/cv/`, edit `_config.yml` | — |
| **Colours / fonts** | `assets/css/style.css` (colours are the `--plum`, `--teal`, `--gold` lines at the top) | VS Code |
| My **photo** | replace `assets/img/laxmikanta-sarangi-2026.jpg` (portrait, 4:5) and `laxmikanta-sarangi-2026-square.jpg` (link previews); the original is `LK_mandira_Photo.jpeg` | — |
| The **News** box and the four **Research at a glance** cards | `index.html` | Notepad or VS Code |

> **Tip:** these `.yml` and `.html` files are just text. You can open them by
> right-clicking → *Open with* → *Notepad*. (A free editor like **VS Code** is nicer
> because it colours the text and warns you about mistakes, but Notepad works.)

---

## Step 2 — Preview before publishing (optional)

In the folder, double-click **`serve.ps1`** (or type `.\serve.ps1` in PowerShell).
It opens the site at **http://127.0.0.1:4000/** in your browser and updates as you edit.
Press **Ctrl-C** in that window to stop it.

*This preview is only on your computer — nobody else can see it.*

---

## Step 3 — Publish your changes

In PowerShell (in the folder), run these **three commands**:

```powershell
git add .
git commit -m "short note about what I changed"
git push
```

Wait about a minute, then refresh **https://lakshmikant46.github.io** (press **Ctrl-F5**
for a fresh copy). Done.

---

# Worked examples

## Example 1 — Add a new working paper

1. Open `_data/publications.yml`.
2. Find the line `working_papers:`.
3. Copy one existing paper block and paste it just below, then change the details.
   Keep the spacing exactly (each field indented under `- title:`):

```yaml
working_papers:
  - title: "My New Paper Title Goes Here"
    authors: "Laxmikanta Sarangi, Co-Author Name"
    year: 2026
    venue: "Working paper."
    jel: "D22, L11"
    keywords: "markup, monopsony"
    pdf: "my-new-paper.pdf"
    slides: ""
    note: ""
    abstract: >
      Paste your abstract here as one paragraph. Long lines are fine —
      just keep every line indented to the same depth as this one.
```

4. If the paper has a PDF, copy it into the `assets/papers/` folder and write **that exact
   file name** in the `pdf:` line (e.g. `pdf: "my-new-paper.pdf"`). No PDF yet? Leave it
   as `pdf:`.
5. Save the file, then do **Step 3** (publish).

> The sections, in the order they appear on the page, are:
> `featured` → `publications` → `working_papers` → `reviews` → `work_in_progress`.
> Add your paper under whichever fits.

---

## Example 2 — Add the *Samiskhya* page numbers (or edit a published paper)

1. Open `_data/publications.yml` and find the `publications:` section.
2. Edit the `venue:` line, e.g.:

```yaml
    venue: "Published in Samiskhya, Vol. 15 (2026), pp. 45–60 — Journal of the Directorate of Economics & Statistics, Government of Odisha."
```

3. Save → publish (Step 3).

---

## Example 3 — Replace your CV with a new version

1. Put the new PDF in the `assets/cv/` folder (any name, e.g. `cv-2027.pdf`).
2. Open `_config.yml` and change the line:

```yaml
cv_file: "cv-2027.pdf"
```

3. Save → publish (Step 3). The embedded viewer and download button update automatically.

---

## Example 4 — Add or change a profile link (Google Scholar, ORCID, etc.)

1. Open `_config.yml`.
2. Fill in the blank next to the link you want, e.g.:

```yaml
google_scholar: "https://scholar.google.com/citations?user=XXXXXXXX"
orcid:          "https://orcid.org/0000-0000-0000-0000"
```

3. Save → publish. Blank links stay hidden; filled ones appear automatically on the Home
   and Contact pages.

---

## Example 5 — Change your Home-page bio

1. Open `index.html`.
2. Near the top you'll see your bio inside a `<p> … </p>` block. Edit the words between the
   tags. Don't remove the `<p>` and `</p>` themselves.
3. Save → publish.

---

## If something goes wrong

- **The live site didn't change after a few minutes.** Go to your repository on GitHub →
  the **Actions** tab. A green tick = it built fine (just refresh with Ctrl-F5).
  A red ✗ = there's a small mistake in a file you edited.
- **Most common mistake:** in `_data/publications.yml`, a title that contains a colon `:`
  must be wrapped in "double quotes", and every field must line up with the same spacing.
- **Undo local edits you haven't published yet:** in PowerShell run `git checkout -- .`
  (this reverts your files back to the last published version).

---

## Quick reference — the whole loop

```powershell
# 1. (optional) preview
.\serve.ps1                     # Ctrl-C to stop

# 2. publish
git add .
git commit -m "what I changed"
git push
```

That's everything. When in doubt, edit → preview → `add` / `commit` / `push`.
