# Changelog

All notable changes to public releases of *Artemis and Image Safari - Crop
Imagery Datasets Spanning Globally Critical Food Species* are documented in
this file.

## [Unreleased]

### Documentation

- Adopt dataset name *Artemis and Image Safari - Crop Imagery Datasets Spanning Globally Critical Food Species*.
- Remove FAIRGrounds references; AWS Open Data is the sole data hosting platform.
- Treat Artemis and Image Safari as one unified dataset release.
- Rename tutorial notebook to `get-to-know-a-dataset-imagesafari_artemis.ipynb`.
- Rename annotation track `automated` to `standard` for clarity.
- Align annotation documentation with the 2026-09-11 S3 inventory, then retire
  the incomplete Artemis cowpea `plant_stand_object_detection` set (missing
  linked images): published Artemis annotated images **14,250** (combined
  **44,820** with Image Safari 30,570); seven Artemis sets retained.
- Align African yam taxonomy with the data paper (*Dioscorea* spp., not
  *Sphenostylis*).
- Remove the benchmark annotation track from documentation; Image Safari
  annotations are released under `standard/` only.
- Document Image Safari `standard/<modality>/<set>/` coverage for 16 of 18
  crops (finger millet and lentil imagery only; African yam = Dioscorea;
  `yam/` alternate prefix for `african-yam/`).

## [1.0.0] - TBD

### Added

- Initial public release (7,469,218 images), comprising Artemis (1,387,663
  images, four crops) and Image Safari (6,081,555 images, 18 crops).
- Annotated subset of 44,820 images (14,250 Artemis; 30,570 Image Safari) with
  instance segmentation, object detection, semantic segmentation, point, and
  scribble labels.
- Predefined evaluation splits stratified by location, acquisition method,
  date, and growth stage.
