# Changelog

All notable changes to public releases of *Artemis and Image Safari - Crop
Imagery Datasets Spanning Globally Critical Crop Species* are documented in
this file.

## [Unreleased]

### Documentation

- Adopt dataset name *Artemis and Image Safari - Crop Imagery Datasets Spanning Globally Critical Crop Species*.
- Remove FAIRGrounds references; AWS Open Data is the sole data hosting platform.
- Treat Artemis and Image Safari as one unified dataset release.
- Rename tutorial notebook to `get-to-know-a-dataset-imagesafari_artemis.ipynb`.
- Rename annotation track `automated` to `standard` for clarity.
- Align annotation documentation with the final 2026-09-11 inventory reports:
  Artemis **10,887** annotated images / **201,289** instances across **six**
  sets; Image Safari **29,671** / **9,753,271** across **67** sets; combined
  annotated images **40,558**. Retired incomplete Artemis cowpea
  `plant_stand_object_detection` and the duplicate Artemis sorghum
  `plant_stand_object_detection` set from published docs.
- Align African yam taxonomy with the data paper (*Dioscorea* spp., not
  *Sphenostylis*).
- Remove the benchmark annotation track from documentation; Artemis and Image
  Safari annotations are released under `standard/` only.
- Document Image Safari `standard/<modality>/<set>/` coverage for 16 of 18
  crops (finger millet and lentil have imagery but no annotations).
- Align Artemis annotation paths with Image Safari: `annotations/standard/...`
  (no variety / `bush-bean` path segment).
- Retain Madagascar among Image Safari / combined country coverage in the
  paper and repository documentation.
- Note that ~663,000 Image Safari images (~11%) lack JSON sidecars and must
  not be dropped when joining images to metadata.
- Keep the released-data variable dictionary and metadata validation report
  (sidecar coverage, model-output provenance) and align remaining docs to the
  final annotation inventory.

## [1.0.0] - TBD

### Added

- Initial public release (7,469,218 images), comprising Artemis (1,387,663
  images, four crops) and Image Safari (6,081,555 images, 18 crops).
- Annotated subset of 40,558 images (10,887 Artemis; 29,671 Image Safari) with
  instance segmentation, object detection, semantic segmentation, point, and
  scribble labels.
- Predefined evaluation splits stratified by location, acquisition method,
  date, and growth stage.
