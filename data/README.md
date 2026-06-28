# data/ — Where to Put Your Dataset

## When to use this folder

Only commit a data file here if **all** of the following are true:

1. The file is **< 50 MB**
2. The data **cannot** be downloaded programmatically (no stable URL, no API)
3. The data has **no redistribution restrictions** (check the license)

All other cases: use one of the preferred alternatives below.

---

## Preferred data-access patterns

### 1. Built-in datasets — zero download, zero CI overhead

```python
from sklearn.datasets import fetch_california_housing, load_iris
import seaborn as sns

df = sns.load_dataset("titanic")           # seaborn built-ins
X, y = fetch_california_housing(return_X_y=True)
```

### 2. Download at notebook runtime — small files only

```python
import urllib.request, pathlib

url  = "https://example.com/your-dataset.csv"
dest = pathlib.Path("data/dataset.csv")
if not dest.exists():
    urllib.request.urlretrieve(url, dest)
df = pd.read_csv(dest)
```

Add the downloaded filename to `.gitignore` so it is not committed (`data/dataset.csv`).  
Prefer stable URLs (Zenodo DOI links, GitHub releases, official government portals).

### 3. Sciebo (TU Dortmund cloud storage) — large files

If your data exceeds 100 MB and cannot be downloaded via a public API, upload it to
[Sciebo](https://sciebo.de) and create a public share link. Then reference it in your
`README.md` Data Sources table so graders know where to find it.

Do **not** embed credentials in the notebook. Set a public Sciebo link with no password,
or describe the access steps clearly in your README.

### 4. API access

```python
import yfinance as yf
import pandas_datareader as pdr

df = yf.download("AAPL", start="2020-01-01")
df = pdr.get_data_fred("UNRATE")           # FRED macroeconomic data
```

**Never put API keys in the notebook.** Store secrets in GitHub Secrets
(repo Settings → Secrets and variables → Actions) and access them in the
workflow environment, or use public APIs that require no authentication.

---

## File size limits

| Size | What to do |
|------|-----------|
| < 50 MB | Commit to this folder (uncomment the relevant `.gitignore` line) |
| 50 MB – 2 GB | Use [Git LFS](https://git-lfs.com/) — free tier covers 1 GB storage |
| > 2 GB | Download at runtime or use a cloud storage URL |

GitHub enforces a **100 MB hard limit** per file and will reject pushes that exceed it.
Files pushed over ~50 MB will also trigger a warning.

---

## To commit a specific data file

By default, `.gitignore` blocks all common data file extensions in this folder.
To track a specific file, add an exception:

```
# in .gitignore — add this line:
!data/my_approved_file.csv
```

Then `git add data/my_approved_file.csv` will work normally.
