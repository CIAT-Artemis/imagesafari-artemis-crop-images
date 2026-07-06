# Predefined evaluation splits

Predefined train, validation, and test splits are provided to support
reproducible benchmarking. Splits are stratified by location, acquisition
method, capture date, and growth stage to reduce leakage across geographic,
device, temporal, and phenological domains.

## Files

Split manifests will be added at release as CSV files in this directory:

- `artemis_train.csv`, `artemis_val.csv`, `artemis_test.csv`
- `imagesafari_train.csv`, `imagesafari_val.csv`, `imagesafari_test.csv`
- `benchmark_train.csv`, `benchmark_val.csv`, `benchmark_test.csv`

Each manifest lists `object_key`, `crop`, `site`, `country`, `date_captured`,
`growth_stage`, `annotation_track`, and `split`.

## Usage

When reporting results, specify the dataset (Artemis or Image Safari), crop
subset, annotation track (`standard` or `benchmark`), and split files used.
