# Predefined evaluation splits

Predefined train, validation, and test splits are provided to support
reproducible evaluation. Splits are stratified by location, acquisition
method, capture date, and growth stage to reduce leakage across geographic,
device, temporal, and phenological domains.

## Files

Split manifests will be added at release as CSV files in this directory:

- `artemis_train.csv`, `artemis_val.csv`, `artemis_test.csv`
- `imagesafari_train.csv`, `imagesafari_val.csv`, `imagesafari_test.csv`

Each manifest lists `object_key`, `crop`, `site`, `country`, `date_captured`,
`growth_stage`, and `split`. Image Safari rows may also include
`annotation_track` (`standard`).

## Usage

When reporting results, specify the dataset (Artemis or Image Safari), crop
subset, and split files used. For Image Safari annotations, cite the
`standard/<modality>/<set>/` paths used.
