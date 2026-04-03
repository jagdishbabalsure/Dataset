# Unified Glaucoma Segmentation & Classification Dataset

## Overview
This dataset is a consolidated and standardized repository of several public glaucoma datasets, including **G1020**, **ORIGA**, **REFUGE**, and **REFUGE2**. It has been specifically curated for both segmentation (Optic Cup/Disc) and classification (Glaucoma/Normal) tasks.

- **Total Image/Mask Pairs**: 2,470
- **Splits**: 80% Train, 20% Test (randomly shuffled)
- **Classes**: Glaucoma, Normal
- **Mask Encoding**: Lossless PNG with visible intensity levels (0, 128, 255)

---

## Directory Structure

The dataset is organized into `train` and `test` splits, with separate subfolders for images and masks categorized by diagnosis:

```text
final_dataset/
├── train/
│   ├── images/
│   │   ├── glaucoma/ (Prefixes: g1020_, origa_, refuge_, refuge2_)
│   │   └── normal/   (Prefixes: g1020_, origa_, refuge_, refuge2_)
│   └── masks/
│       ├── glaucoma/ (Same naming as images)
│       └── normal/   (Same naming as images)
└── test/
    ├── images/
    │   ├── glaucoma/
    │   └── normal/
    └── masks/
        ├── glaucoma/
        └── normal/
```

---

## Data Source Integration

| Source Dataset | Contribution (Pairs) | Labeling Method |
| :--- | :--- | :--- |
| **G1020** | 1,020 | Mapped via `G1020.csv` metadata |
| **ORIGA** | 650 | Mapped via `OrigaList.csv` metadata |
| **REFUGE (Train Set)** | 400 | Prefix `g` (Glaucoma) and `n` (Normal) |
| **REFUGE2 (Train Set)** | 400 | Prefix `g` (Glaucoma) and `n` (Normal) |

*Note: REFUGE val/test sets were excluded to maintain 100% label accuracy, as they follow a different naming convention.*

