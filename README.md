# YOLOv10 Weapon Detection

Real-time weapon detection with YOLOv10, trained on CCTV footage.

## Results

| Metric | Value |
|---|---|
| mAP50 | 0.995 |
| mAP50-95 | 0.68 |
| Epochs | 130 |
| Training time | ~5 min (Tesla T4, Kaggle) |
| Images | 141 (train 112 / val 21 / test 8) |
| Classes | person, weapon |
| Box loss | 0.93 → 0.69 |

## Dataset

Simuletic CCTV Weapon Detection Dataset (free sample) — 141 synthetic CCTV images with YOLO labels. Full dataset is paid at simuletic.com. License: CC BY-SA 4.0.

## Honest note

mAP50 0.995 is measured on a small 141-image synthetic sample — it is NOT comparable to the 0.911 mAP50 of my IEEE Access paper, which used the full dataset. The trained model is a specialist: ~0.99 confident on CCTV-style images, but weak on real street photos and webcam (domain shift). At conf 0.25 it detected nothing on a street photo; at conf 0.1 it found 3 persons but also 5 false weapons.

## Usage

pip install ultralytics
yolo predict model=best.pt source=bus.jpg
yolo predict model=best.pt source=0 show=True

## Files

- yolov10_weapon_training.ipynb — training notebook (Kaggle, Tesla T4)
- best.pt — trained weights (YOLOv10n, 2 classes)
- results/ — prediction images

## Paper

Real-Time Multi-Camera Weapon Detection System with Automated Alert for Street Crime Prevention — submitted to IEEE Access (Manuscript ID: Access-2026-59086, under review).

## License

MIT
