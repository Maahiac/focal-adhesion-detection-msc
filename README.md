# Focal Adhesion Detection (MSc Dissertation)

Reproducible single-class detector for focal adhesions (FAs) in fluorescence microscopy images. 
The work evaluates augmentation, morphology-preserving resizing, and modest data scaling to support future modelling of FA dynamics.
A GUI-based RT‑DETR baseline was also trained on the same annotations for comparison.

> **Code availability line (paste into your Methods):**  
> Code and configuration are available at: https://github.com/Maahiac/focal-adhesion-detection-msc (Release v1.0.0).  
> Dataset/model version IDs and exported metrics are listed in `VERSIONING.md`.

## Repository Structure
```
focal-adhesion-detection-msc/
├─ README.md
├─ VERSIONING.md
├─ environment/
│  └─ requirements.txt
├─ data/
│  └─ data.yaml             # class names & paths (no raw images committed)
├─ notebooks/
│  └─ FA_prediction_update.ipynb
└─ reports/
   ├─ metrics/
   │  └─ versions_metrics.csv
   ├─ pr_curves/            # PNGs used in the thesis
   ├─ confusion_matrices/   # PNGs used in the thesis
   └─ figures/              # pipeline, annotation example, prediction gallery
```

## Quick Start (pip)
```bash
python -m venv .venv
source .venv/bin/activate       # on Windows: .venv\Scripts\activate
pip install -r environment/requirements.txt
# If torch install fails, try:
# pip install --index-url https://download.pytorch.org/whl/cpu torch==2.2.1 torchvision==0.17.1
```

## Reproduce Metrics & Figures
1. Open `notebooks/FA_prediction_update.ipynb` and run the evaluation cells.  
2. Export figures to `reports/pr_curves/` and `reports/confusion_matrices/`.  
3. Ensure the consolidated table `reports/metrics/versions_metrics.csv` contains one row per version (v3–v8).

**Expected columns:** `version,precision,recall,map50,map50_95,notes`

## Notes
- Dataset is hosted on a platform (internal); we do not commit raw images. Use `data/data.yaml` to point to local copies.
- Model and dataset version IDs are recorded in `VERSIONING.md`.
- Generative AI assisted minor wording/bug-fixing; all analyses and decisions are the author’s.
