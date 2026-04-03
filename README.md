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

---

## Preprocessing & Data Standards

### 1. Unique File Naming
To prevent filename collisions across different sources, every file has been renamed following the pattern:
`{source}_{shuffled_index}_{original_filename}`

### 2. Standardized Formats
- **Images**: All images saved as high-quality `JPEG`.
- **Masks**: All masks saved as lossless `PNG`.

### 3. Mask Normalization (Visibility)
Original masks with ultra-low intensity values (0, 1, 2) have been **normalized** to be human-visible:
- `0` (Background) -> `0` (Black)
- `1` (Optic Disc) -> `128` (Gray)
- `2` (Optic Cup) -> `255` (White)

### 4. Verified Integrity
A 1:1 mapping between every image and its corresponding mask has been verified by dimension and basename comparison. The dataset has **0 missing masks** and **0 size mismatches**.

---

## Technical Specifications
- **Image Mode**: RGB
- **Mask Mode**: Grayscale (1-channel)
- **Primary Use Case**: Semantic Segmentation (U-Net) and Binary Classification (ResNet/EfficientNet).

---

#
