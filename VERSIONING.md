# VERSIONING — Dataset, Models, and Figure Provenance

This file records the exact dataset versions, model runs, and which exported artefacts map to the figures/tables in the dissertation.

## Dataset Versions
| Version | Resize Strategy | Base Images | Added Images | Total Images | Notes |
|--------:|-----------------|------------:|-------------:|-------------:|-------|
| v3      | Stretch to 640  | 19          | —            | 19           | Baseline (no aug) |
| v4      | Stretch to 640  | 19          | —            | 19           | + rotation |
| v5      | Stretch to 640  | 19          | —            | 19           | + rotation + flip |
| v6      | Fit‑within 640  | 19          | —            | 19           | Padding to preserve morphology |
| v7      | Fit‑within 640  | 19          | +24          | 43           | Data growth (same batch) |
| v8      | Fit‑within 640  | 19          | +30          | 49           | Final curated total |

*Splits:* train/val/test are fixed per version; see `reports/metrics/versions_metrics.csv` for counts and metrics.

## Model & Training
- **Code-based local baseline:** YOLOv8s (pretrained on COCO), single class, imgsz=640, epochs=30, batch=8, patience=15, seed fixed, CPU device.  
- **GUI baseline:** RT‑DETR (platform), trained on same annotations; identical evaluation metrics reported.

**Environment pins (local):** ultralytics==8.2.61, numpy==1.26.4, scipy==1.11.4, opencv-python-headless==4.8.0.74, tensorboard==2.15.1, roboflow==1.1.27, torch==2.2.1, torchvision==0.17.1.

## Operating Thresholds
- Unless specified otherwise, qualitative figures use the default threshold (0.5) and a stricter threshold (0.65) to illustrate FP/FN balance.
- The recommended operating point for downstream tracking favours recall (state the exact threshold you chose in the text).

## Metrics Table (source of truth)
- File: `reports/metrics/versions_metrics.csv`  
- Columns: `version,precision,recall,map50,map50_95,notes`  
- **Ensure v5 row is complete** (from your final runs).

## Figure Provenance (example mapping — update to match your filenames)
- **Fig. Methods (Annotation example):** `reports/figures/annotation_example.png`  
- **Fig. Results (Threshold sweep):** `reports/figures/threshold_50.png`, `reports/figures/threshold_65.png`  
- **Fig. Results (PR curve):** `reports/pr_curves/v8_pr.png`  
- **Fig. Results (Confusion matrix):** `reports/confusion_matrices/v8_cm.png`  
- **Fig. Results (Version comparison):** `reports/figures/version_comparison_bars.png`  
- **Fig. Results (Progression line):** `reports/figures/performance_progression.png`  
- **Fig. Gallery:** `reports/figures/predictions_gallery/*.png`

## Reproducibility Notes
- Keep `data/data.yaml` up to date with your local paths and class label. Do **not** commit raw images if restricted.
- If re-running, use the same seed and exact hyper-parameters. Record any deviations here.
- Snapshot the submission with a **GitHub Release** (e.g., v1.0.0) and keep figures/metrics in `reports/` in sync with the dissertation.
