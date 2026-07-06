# Changelog

All notable changes to the ImageSafari_Artemis public releases are documented
in this file.

## [Unreleased]

### Documentation

- Consolidate AWS registry metadata into a single `imagesafari_artemis-crop-images.yaml`.
- Treat ImageSafari_Artemis as one unified dataset with Artemis and Image Safari components.
- Rename tutorial notebook to `get-to-know-a-dataset-imagesafari_artemis.ipynb`.
- Rename annotation track `automated` to `standard` for clarity.

## [1.0.0] - TBD

### Added

- Initial public release of ImageSafari_Artemis (7,469,220 images), comprising
  Artemis (1,387,665 images, four crops) and Image Safari (6,081,555 images,
  18 crops).
- Annotated subset of 42,981 images with bounding box, mask, point, scribble,
  and polygon labels.
- Benchmark annotation track for banana, common bean, potato, and sorghum.
- Predefined evaluation splits stratified by location, acquisition method,
  date, and growth stage.
