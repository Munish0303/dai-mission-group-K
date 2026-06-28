# [Project Title]

![Notebook CI](https://github.com/<YOUR_GITHUB_USERNAME>/<YOUR_REPO_NAME>/actions/workflows/run-notebook.yml/badge.svg)

> **Before submitting:** replace `<YOUR_GITHUB_USERNAME>/<YOUR_REPO_NAME>` in the badge URL above
> with your actual GitHub owner and repository name.

---

## Team

| Name | Role |
|------|------|
| Firstname Lastname | Lead / Causal Inference |
| Firstname Lastname | Supervised Learning |
| Firstname Lastname *(optional)* | Unsupervised / Generative |

> No student IDs in this file. Submit IDs separately via the course system (Moodle).

---

## Research Question

*One sentence: what causal or predictive question are you answering, and with what data?*

---

## Methods Overview

| Block | Method(s) |
|-------|-----------|
| Causal Inference | DoWhy — [backdoor / IV / propensity score] |
| Supervised Learning | [e.g., Ridge regression, Random Forest, …] |
| Unsupervised / Generative | [e.g., K-Means, VAE, Hierarchical clustering, …] |

---

## Data Sources

| Dataset | Source / URL | Access method |
|---------|-------------|---------------|
| | | local file / API / sklearn built-in / runtime download / Sciebo link |

> **Data size rule:** files < 100 MB may be committed directly. Files ≥ 100 MB must either
> be downloaded programmatically in the notebook (API/URL) or linked via a Sciebo share
> placed in this README — do NOT push large files to GitHub.

---

## How to Run

### Option A — GitHub Actions (zero local setup)

Push to `main`. The CI workflow executes `notebook.ipynb` automatically.

- Check the **Actions** tab to see whether the run passed or failed.
- Download the `executed-notebook-*` artifact to inspect all cell outputs.
- The badge at the top of this README turns green when the notebook runs clean.

### Option B — Local environment

```bash
# Clone your repo (not this template)
git clone https://github.com/<YOUR_GITHUB_USERNAME>/<YOUR_REPO_NAME>.git
cd <YOUR_REPO_NAME>

python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter lab notebook.ipynb
```

---

## Presentation Slide Requirements

| Item | Rule |
|------|------|
| Content slides | **Maximum 5** |
| Allowed extras | Title page · Literature/Reference slide · Backup slides |
| Backup slide content | Tables or figures/diagrams **only** |
| Required topics | Motivation & Economic Relevance · Data & Methodology · Results · Limitations & Synthesis |
| File format | **PDF only** — do not submit PPTX |
| Delivery | No live presentation — slides are reviewed during the oral exam |

---

## Oral Exam

- **Format:** 15-minute Q&A per group — questions on your Proposal and Presentation slides
- **Individual accountability:** each member answers questions on their own area (see Work Plan in notebook)
- **Rooms:** Morning sessions → M811 · Afternoon sessions → M827 · Arrive 10 minutes early
- **Grading:** oral performance directly modifies your Mission base score; significant individual
  discrepancies lead to differentiated individual grades

---

## Key Deadlines

| Date | Time | What |
|------|------|------|
| June 18 | 12:00 noon | Rank your session slots in Moodle (group lead) |
| June 30 | 12:00 noon | Submit repository link to Moodle (exactly one member per group) |
| June 30 | 23:59 | Final code deadline — commits after this are not graded |

> **Private repositories:** if your repo is private you MUST invite `pnposch` and
> `kiraschoenhuette` as collaborators before the deadline so the teaching team can clone it.

---

## Submission Checklist

| Item | Status |
|------|--------|
| Repo named `dai-mission-group-X` (replace X with your group letter) | [ ] |
| README updated (title, team, badge URL, research question, data sources) | [ ] |
| Work Plan filled in (`notebook.ipynb` — team member → section mapping) | [ ] |
| All rubric sections complete (§1–§5) | [ ] |
| Notebook submitted in **fully executed state** (all cell outputs visible) | [ ] |
| Notebook re-executes cleanly (CI badge green) | [ ] |
| `presentation.pdf` replaced with actual PDF (PDF only, no PPTX) | [ ] |
| Large data files (≥ 100 MB) not committed — downloaded or Sciebo-linked instead | [ ] |
| Custom `.py` modules included (if any) | [ ] |
| Private repo: `pnposch` + `kiraschoenhuette` added as collaborators | [ ] if private |
| Repository link submitted to Moodle by **June 30, 12:00 noon** | [ ] |

---

## Repository Structure

```
.
├── .github/workflows/run-notebook.yml   # CI: validates and executes notebook on every push
├── data/                                # local data files (see data/README.md)
├── notebook.ipynb                       # main deliverable — proposal + final submission (submit fully executed)
├── presentation.pdf                     # slide deck — PDF only, max 5 content slides
├── README.md                            # this file
└── requirements.txt                     # Python dependencies (required)
```
