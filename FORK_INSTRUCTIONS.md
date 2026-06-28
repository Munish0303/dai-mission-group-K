# How to Start Your DAI Mission from This Template

## Why "Use this template" and not "Fork"?

| | "Use this template" | Fork |
|-|---------------------|------|
| Commit history | Fresh single commit | Full history of the template |
| Connection to template | None — fully independent | Linked; PRs back to template are possible |
| Naming | Your choice | Shows "forked from firrm/dai-mission-template" |

For academic submissions, **"Use this template"** is cleaner: no accidental pull
requests back to the instructor's repository, and each team has an independent history.

---

## Key Deadlines (do not miss these)

| Date | Time | Action |
|------|------|--------|
| **June 18** | 12:00 noon | Group lead ranks session slots in Moodle |
| **June 30** | 12:00 noon | Exactly one member submits repo link to Moodle |
| **June 30** | 23:59 | Final code deadline — commits after this are not graded |

---

## Step 1 — Create your team's repository

1. Go to **https://github.com/firrm/dai-mission-template**
2. Click the green **"Use this template"** button (top right of the repo page)
3. Select **"Create a new repository"**
4. Set the **owner** to one team member's GitHub account
5. Set the **repository name** following this exact format: `dai-mission-group-A`
   (replace `A` with your group's actual letter, e.g. `dai-mission-group-G`)
6. Set visibility to **Public** or **Private** (your choice)
   - **If private:** you MUST add `pnposch` and `kiraschoenhuette` as collaborators
     (Settings → Collaborators → Add people) before the deadline
   - **If public:** the CI badge is visible to anyone without authentication
7. Click **"Create repository from template"**

---

## Step 2 — Invite your teammates

Go to **Settings → Collaborators → Add people** and search by GitHub username.
All team members need **Write** access.

If your repo is private, also add the teaching team at this step:
- `pnposch`
- `kiraschoenhuette`

---

## Step 3 — Update the README

Open `README.md` and:

- Replace `[Project Title]` with your actual project title
- Fill in the **Team** table (names and roles — no student IDs in this file)
- **Update the CI badge URL**: replace `<YOUR_GITHUB_USERNAME>/<YOUR_REPO_NAME>`
  with your actual owner/repo, e.g.:
  ```
  ![Notebook CI](https://github.com/jsmith/dai-mission-group-G/actions/workflows/run-notebook.yml/badge.svg)
  ```
- Fill in **Research Question**, **Methods Overview**, and **Data Sources**
- If your data is ≥ 100 MB, add a Sciebo share link in the Data Sources table
  (do not commit files this large to git)

---

## Step 4 — Fill in the Work Plan

Open `notebook.ipynb` and fill in the **Work Plan** table near the top.
This maps each team member to their section responsibility and is the basis for
individual accountability during the oral exam — every member must be able to
answer questions about their own area.

---

## Step 5 — Work in the notebook

1. Open `notebook.ipynb` in JupyterLab
2. Read the **`[TEMPLATE]`** markdown cells — they explain what's expected in each section
3. Replace the **`[EXAMPLE — replace with your analysis]`** code cells with your own analysis
4. Keep the section structure (§1–§5) — graders navigate by section

**Proposal stage:** complete the Work Plan + Sections 1–5 up to the level that
your research question is clear and your methods are planned.
The proposal is approved once the instructor accepts your research question.

---

## Step 6 — Commit and push during development

```bash
git add notebook.ipynb README.md
git commit -m "feat: add team info and initial research question"
git push origin main
```

CI starts automatically. Check the **Actions** tab — a green badge means the
notebook runs end-to-end without errors. Fix any red runs before the deadline.

---

## Step 7 — Prepare the final submission

Before the **June 30, 23:59** code deadline:

1. **Run the notebook fully** in JupyterLab so all cell outputs and plots are visible
2. **Commit the executed notebook** — the file in your repo must contain all outputs:
   ```bash
   git add notebook.ipynb
   git commit -m "final: submit fully executed notebook"
   ```
3. **Replace `presentation.pdf`** with your actual slide deck (PDF format only — no PPTX):
   ```bash
   # delete the placeholder, copy your real PDF, then:
   git add presentation.pdf
   git commit -m "final: add presentation slides"
   ```
4. **Include any custom `.py` modules** if you outsourced helper functions:
   ```bash
   git add my_helpers.py
   ```
5. **Verify CI is green** — check the Actions tab one last time
6. Check the CI log for any submission warnings (unexecuted cells, placeholder PDF)

---

## Step 8 — Submit to Moodle

By **June 30, 12:00 noon**: exactly **one member** from the group submits the
repository URL to Moodle. You may keep pushing code after submitting the link —
the teaching team will clone at the **June 30, 23:59** deadline.

---

## Presentation slide rules (summary)

- Maximum **5 content slides** (plus title page, references, and optional backup slides)
- Backup slides may only contain tables or figures — no text bullets
- Required topics across your 5 slides:
  1. Motivation & Economic Relevance
  2. Data & Methodology
  3. Results
  4. Limitations & Synthesis
- **PDF format only** — do not submit PPTX
- No live presentation: slides are reviewed during the oral exam Q&A

---

## Oral Exam (Q&A)

- **Duration:** 15 minutes per group
- **Format:** Q&A on your Proposal notebook and Presentation slides — no live presentation
- **Rooms:** Morning slots → M811 · Afternoon slots → M827 · **Arrive 10 minutes early**
- **Individual:** each member answers questions on their own Work Plan area
- **Grading:** oral performance directly modifies your Mission base score

---

## Troubleshooting

**CI is failing (red badge)**

1. Click the failing workflow run in the **Actions** tab
2. Expand the failing step and read the traceback

Common causes:

| Symptom | Fix |
|---------|-----|
| `ModuleNotFoundError: No module named 'X'` | Add `X` to `requirements.txt` and push |
| `FileNotFoundError: data/myfile.csv` | Commit the file or download it in the notebook |
| `TimeoutError` (cell ran > 600 s) | Reduce data size or iterations for CI runs |
| Validation: "PPTX file found" | Remove PPTX — submit PDF only |
| Validation: "unexecuted cells" | Run all cells in JupyterLab, then commit the output |

**Badge shows "unknown"**

- No workflow has run yet — push a commit to trigger the first run
- Private repo — badge shows "unknown" to unauthenticated viewers (this is expected
  for private repos; graders will clone directly)

**Badge not updating**

GitHub CDN caches badges for up to 5 minutes. Hard-refresh (`Ctrl+Shift+R`).

**Large data file rejected (> 100 MB)**

See `data/README.md` for alternatives: runtime download, API access, or Sciebo link.

---

## Adding heavier dependencies (TensorFlow, PyTorch, etc.)

Add to `requirements.txt`:

```
tensorflow>=2.17.0
# or
torch>=2.3.0
torchvision>=0.18.0
```

The pip cache means subsequent pushes with unchanged `requirements.txt` take ~30 s
instead of several minutes.
