# Artemis and Image Safari Crop Image Collections

This repository hosts documentation, metadata schemas, predefined evaluation splits,
and tutorials for two complementary agricultural image datasets developed by the
Alliance of Bioversity International and CIAT.

**Artemis** is a structured phenotyping dataset that pairs imagery with detailed
agronomic, genotypic, and environmental metadata across four crop species —
common bean (*Phaseolus vulgaris*), cowpea (*Vigna unguiculata*), soybean
(*Glycine max*), and sorghum (*Sorghum bicolor*) — and four locations:
Tanzania, Uganda, Colombia, and the United States. Imaging was performed under
defined smartphone and push-cart protocols that link each image to metadata
collected in the field, supporting fine-grained tasks such as trait estimation,
growth stage recognition, and disease quantification.

**Image Safari** is a diversity-driven agricultural image corpus assembled to
capture variability across 18 crops — banana (*Musa* spp.), cassava (*Manihot
esculenta*), chickpea (*Cicer arietinum*), common bean (*P. vulgaris*), cowpea
(*V. unguiculata*), finger millet (*Eleusine coracana*), groundnut (*Arachis
hypogaea*), lentil (*Lens culinaris*), maize (*Zea mays*), pearl millet
(*Cenchrus americanus*), pigeon pea (*Cajanus cajan*), potato (*Solanum
tuberosum*), rice (*Oryza sativa*), sorghum (*S. bicolor*), soybean (*Glycine
max*), sweet potato (*Ipomoea batatas*), wheat (*Triticum aestivum*), and
African yam (*Sphenostylis stenocarpa*) — across nine countries: Tanzania,
Côte d'Ivoire, Madagascar, Nigeria, Senegal, Kenya, Ghana, Uganda, and Malawi.
Multiple imaging devices and field conditions are represented, with particular
emphasis on smallholder farming systems common in the Global South that remain
substantially underrepresented in existing public datasets.

## Public access

| Asset | Location | Notes |
|---|---|---|
| Dataset files (images, annotations, metadata) | [FAIRGrounds](https://fairgrounds.org) | Primary release; accession to be assigned at publication |
| Bulk anonymous download | Registry of Open Data on AWS | S3 bucket and Region to be added after provisioning |
| Documentation, schemas, splits, tutorials | This GitHub repository | [`docs/`](docs/) |
| Issues and corrections | [GitHub Issues](https://github.com/CIAT-Artemis/imagesafari-artemis-crop-images/issues) | |

Versioned releases are documented in [`CHANGELOG.md`](CHANGELOG.md).

## Repository structure

The repository is organized by crop, with each crop directory containing an
`images/` subtree organized by collection site and acquisition date, an
`annotations/` subtree containing both automated and benchmark annotation
tracks, and a `metadata/` subtree.

```text
Artemis/
└── <crop>/
    ├── images/<collection-site>/<acquisition-date>/
    ├── annotations/
    │   ├── automated/    # COCO JSON and PNG masks
    │   └── benchmark/    # expert-reviewed subset (where applicable)
    └── metadata/         # CSV and Parquet tables

ImageSafari/
└── <crop>/
    ├── images/<collection-site>/<acquisition-date>/
    ├── annotations/
    │   ├── automated/
    │   └── benchmark/    # banana, common-bean, potato, sorghum
    └── metadata/
```

Images are stored as JPEG files at original acquisition resolution. Segmentation
outputs are provided as PNG masks with matching filenames. Object-level
annotations are stored in COCO JSON format. Metadata tables are provided in CSV
format, with Parquet copies for analytical workflows.

## Repository contents

| File | Purpose |
|---|---|
| [`Artemis/`](Artemis/) | Structured phenotyping dataset (4 crops) |
| [`ImageSafari/`](ImageSafari/) | Diversity-driven image corpus (18 crops) |
| [`docs/artemis.md`](docs/artemis.md) | Artemis documentation and access instructions |
| [`docs/imagesafari.md`](docs/imagesafari.md) | Image Safari documentation, crop counts, and curation summary |
| [`docs/variable_dictionary.csv`](docs/variable_dictionary.csv) | Metadata field definitions |
| [`docs/annotation_guidelines.md`](docs/annotation_guidelines.md) | Annotation ontology and quality-control procedures |
| [`docs/splits/`](docs/splits/) | Predefined train/validation/test splits |
| [`docs/metadata_validation_report.csv`](docs/metadata_validation_report.csv) | Metadata validation summary |
| [`artemis-crop-images.yaml`](artemis-crop-images.yaml) | Artemis entry for the Registry of Open Data on AWS |
| [`imagesafari-crop-images.yaml`](imagesafari-crop-images.yaml) | Image Safari entry for the Registry of Open Data on AWS |
| [`get-to-know-a-dataset-imagesafari.ipynb`](get-to-know-a-dataset-imagesafari.ipynb) | Introductory AWS tutorial for Image Safari |
| [`CITATION.cff`](CITATION.cff) | Machine-readable citation metadata |
| [`CHANGELOG.md`](CHANGELOG.md) | Version history |
| [`LICENSE.md`](LICENSE.md) | Dataset license notice |

## Dataset summary

| | Artemis | Image Safari | Combined |
|---|---|---|---|
| Crops | 4 | 18 | — |
| Countries | 4 | 9 | 10 |
| Images | 1,387,665 | 6,081,555 | 7,469,220 |
| Annotated images | 12,216 | 30,765 | 42,981 |
| Focus | Structured phenotyping with linked field metadata | Diversity across crops, geographies, and imaging conditions | Complementary pair |
| License | [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) | [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) | [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) |

## Documentation

- See [`docs/artemis.md`](docs/artemis.md) for Artemis dataset description,
  crop counts, metadata fields, and access examples.
- See [`docs/imagesafari.md`](docs/imagesafari.md) for Image Safari dataset
  description, crop counts, curation method, citation guidance, and limitations.
- Consult [`docs/variable_dictionary.csv`](docs/variable_dictionary.csv) and
  [`docs/annotation_guidelines.md`](docs/annotation_guidelines.md) before use.

## Citation

Cite the data descriptor paper and identify the dataset version used. Also cite
the FAIRGrounds accession or AWS release prefix and the date accessed.

## Contact

Questions, corrections, and dataset issues can be submitted through the
[repository issue tracker](https://github.com/CIAT-Artemis/imagesafari-artemis-crop-images/issues).
