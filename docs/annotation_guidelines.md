# Annotation guidelines

Annotations follow a hierarchical plant-organ taxonomy with primary categories
for whole plants, leaves, stems, flowers, fruits, and weeds, subdivided into
crop-specific classes such as `plant_sorghum`, `flower_panicle`, `fruit_grain`,
and `weed_broadleafed`.

## Annotation types

Five representations are provided:

| Type | Format | Typical use |
|---|---|---|
| Bounding box | COCO JSON | Detection and localization |
| Masks / polygon | PNG mask or COCO JSON | Semantic and instance segmentation |
| Point | COCO JSON | Keypoint and weak supervision |
| Scribble | COCO JSON | Scribble-supervised segmentation |

## Annotation tracks

- **automated/** — higher-volume labels suitable for pre-training and
  representation learning.
- **benchmark/** — expert-reviewed labels for method comparison and
  reproducibility studies.

### Benchmark crops

The benchmark track is populated for four Image Safari crops selected to
represent distinct agronomic groups:

| Crop | Group |
|---|---|
| Banana | Perennial |
| Common bean | Legume |
| Potato | Tuber |
| Sorghum | Grass |

For Artemis, annotated subsets use polygon and bounding-box formats for common
bean, cowpea, and sorghum under defined trial protocols.

## Quality control

Annotations were produced in Roboflow, CVAT, and Supervisely following a
standardized protocol covering class definitions, boundary rules,
ambiguity-resolution procedures, and return-for-correction workflows. Benchmark
subsets were independently reviewed by three expert annotators using semantic
segmentation; inter-annotator agreement is reported in the data descriptor.

## File layout

```text
<crop>/annotations/
├── automated/
│   ├── coco/
│   └── masks/
└── benchmark/
    ├── coco/
    └── masks/
```

Mask filenames match the corresponding image filenames with a `.png` extension.
