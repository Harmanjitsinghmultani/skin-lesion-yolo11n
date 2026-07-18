# Skin Disease Detection with Explainability using YOLO11 and Grad-CAM

Multi-class dermoscopic skin lesion classification on the ISIC 2019 dataset (25,331 images, 8 classes), using YOLO11n with Grad-CAM explainability and a confidence-threshold clinical triage framework.

**Status:** Accepted for oral presentation, IEEE ICEC2NT 2026 (Paper ID 2725) — to be published in IEEE Xplore, indexed in Ei Compendex and Scopus.

## Results

| Metric | Value |
|---|---|
| Top-1 accuracy | 82.26% |
| Top-5 accuracy | 99.64% |
| Balanced accuracy | 62.8% |
| Parameters | 1.54M |
| Inference speed | 1.0 ms/image (Tesla T4) |

Outperforms YOLOv8n, ResNet50, EfficientNet-B0, and GoogleNet at p < 0.001 (McNemar's test) on an identical held-out test set.

## What this repo contains

- `notebooks/skin_lesion_yolo11n.ipynb` — full training, evaluation, and Grad-CAM pipeline
- Dataset deduplication via perceptual hashing (removes 1,247 near-duplicates)
- Statistical validation: McNemar's test, Pearson correlation (class imbalance analysis), 5-seed variance check, Kolmogorov–Smirnov test
- Grad-CAM explainability validated qualitatively against the ABCD dermoscopic criteria
- Clinical triage analysis across confidence thresholds (0.70–0.95)

## Dataset

[ISIC 2019](https://challenge.isic-archive.com/data/#2019) — 25,331 dermoscopic images across 8 diagnostic categories (MEL, NV, BCC, AK, BKL, DF, VASC, SCC). Not redistributed here; see the ISIC Archive for access.

## Key finding

Class imbalance (54:1 NV:DF ratio), not model architecture, is the dominant constraint on per-class performance (Pearson r = 0.736, p < 0.05). At a 0.90 confidence threshold, the clinical triage framework automates 52% of cases at 94.1% accuracy, reducing missed melanoma cases from 67 to 8 and dermatologist workload by 48%.

## Author

Harmanjit Singh Multani — [harmanjit.netlify.app](https://harmanjit.netlify.app) — harmanjeet.multani@gmail.com

Co-authors: Sandeep Kaur Multani (Infosys), Atiya Khan (G H Raisoni College of Engineering)
