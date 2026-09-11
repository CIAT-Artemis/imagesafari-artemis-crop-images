# Annotation guidelines

This document describes the annotation modalities and directory layout used in
the Artemis and Image Safari public release. Counts reflect the S3 inventory of
2026-09-11.

## Overview

| Collection | Annotated images | Annotation instances | Modality profile |
|---|---:|---:|---|
| Artemis | 16,382 | 289,405 | Instance segmentation, object detection |
| Image Safari | 30,570 | 10,049,665 | Point, scribble, semantic / instance segmentation, object detection |
| Combined | 46,952 | 10,339,070 | — |

## Artemis

### Layout

```text
Artemis/<crop>/annotations/[<variety>/]<annotation_type>/<set>/
├── <set>_all.json          # COCO annotations
└── annotated_images/       # JPEG images linked to the set
```

- Optional `<variety>` path segment (for example `bush-bean`) appears when
  variety-specific sets are published.
- Published Artemis types are **`instance_segmentation`** and
  **`object_detection`** only.
- Soybean has imagery and metadata in the release but no published annotation
  sets in this inventory.

### Modality definitions

| Type | Description | Typical labels |
|---|---|---|
| Instance segmentation | Per-instance polygon masks in COCO JSON | Flowers, pods, plant parts |
| Object detection | Axis-aligned bounding boxes in COCO JSON | Plant stands, pods, weeds |

### Published sets (summary)

| Crop | Sets | Images | Annotations |
|---|---:|---:|---:|
| Common bean | 4 | 5,392 | 119,107 |
| Cowpea | 2 | 4,264 | 66,192 |
| Sorghum | 2 | 6,726 | 104,106 |
| Soybean | 0 | 0 | 0 |

Named sets include `bushbean_flower`, `bushbean_pod`, `bushbean_plant_stand`,
`cowpea_plant_stand`, `plant_stand_object_detection`, and `sorghum_plant_stand`.

**Inventory caveat:** one cowpea object-detection set reports missing linked
image objects; validate image availability before training.

## Image Safari

### Layout

```text
ImageSafari/<crop>/annotations/standard/<annotation_type>/<set>/
```

- All published Image Safari annotations sit under the **`standard/`** track.
- Sets are named directories (for example `plant-part`, `plant-semantic`,
  `pseudo-instance`, `plant_points`).
- Finger millet and lentil have imagery but no published annotation sets in
  this inventory.
- African yam is *Dioscorea* spp.; S3 prefix `yam/` is an alternate path for
  the same crop as `african-yam/`, not a separate species.
- Object detection is currently concentrated on **common bean**.

### Modality definitions

| Type | Description |
|---|---|
| Point | Sparse point clicks on plant parts or organs |
| Scribble | Freehand stroke annotations |
| Semantic segmentation | Pixel-wise class maps without instance IDs |
| Instance segmentation | Per-instance masks |
| Object detection | Bounding boxes (primarily common bean) |

### Coverage by modality

| Modality | Annotated images | Annotation instances | Crops |
|---|---:|---:|---:|
| Point | 11,448 | 3,894,917 | 11 |
| Scribble | 7,831 | 3,243,389 | 11 |
| Semantic segmentation | 6,541 | 1,619,166 | 16 |
| Instance segmentation | 2,331 | 1,246,563 | 8 |
| Object detection | 2,419 | 45,630 | 1 |

Unique annotated images across modalities: **30,570** (images may appear in more
than one modality row above; the unique total is the inventory headline).

## Formats

| Format | Used for |
|---|---|
| COCO JSON | Artemis object detection and instance segmentation; Image Safari object / instance sets where applicable |
| Raster masks / label maps | Semantic and instance segmentation outputs |
| Point / scribble sidecars | Sparse supervision modalities under Image Safari `standard/` |

Exact file naming can vary by set. Prefer loading via the published set
directory rather than assuming a single global filename pattern.

## Quality notes

- Treat annotation inventory counts as the current public snapshot; re-inventory
  after future uploads.
- Prefer set-level manifests and COCO `images` / `file_name` fields to resolve
  image paths.
- Missing or unmatched image keys should be excluded from training splits and
  reported when citing subset sizes.
