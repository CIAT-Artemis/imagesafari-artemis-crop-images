# ImageSafari_Artemis Crop Image Collection

This repository hosts the **ImageSafari_Artemis** dataset — a unified agricultural image collection comprising **7,469,220 field images** across two complementary components, **Artemis** and **Image Safari**, developed by the Alliance of Bioversity International and CIAT.

| Component | Images | Crops | Countries | Focus |
|---|---:|---:|---:|---|
| **Artemis** | 1,387,665 | 4 | 4 | Structured phenotyping with linked field metadata |
| **Image Safari** | 6,081,555 | 18 | 9 | Diversity across crops, geographies, and imaging conditions |

## Artemis

Artemis is a structured phenotyping dataset that pairs imagery with detailed
agronomic, genotypic, and environmental metadata across four crop species —
common bean (*Phaseolus vulgaris*), cowpea (*Vigna unguiculata*), soybean
(*Glycine max*), and sorghum (*Sorghum bicolor*) — and four locations:
Tanzania, Uganda, Colombia, and the United States. Imaging was performed under
defined smartphone and push-cart protocols that link each image to metadata
collected in the field, supporting fine-grained tasks such as trait estimation,
growth stage recognition, and disease quantification.

## Image Safari

Image Safari is a diversity-driven agricultural image corpus assembled to
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

A subset of **42,981 annotated images** (12,216 Artemis; 30,765 Image Safari)
includes organ-level labels in **standard** and **benchmark** annotation tracks.

## Public access

| Asset | Location | Notes |
|---|---|---|
| Images, annotations, and metadata | [Registry of Open Data on AWS](https://registry.opendata.aws/) | Public S3 bucket; bucket name and Region to be added after provisioning |
| Documentation, schemas, splits, tutorials | This GitHub repository | [`docs/`](docs/) |
| Issues and corrections | [GitHub Issues](https://github.com/CIAT-Artemis/imagesafari-artemis-crop-images/issues) | |

Versioned releases are documented in [`CHANGELOG.md`](CHANGELOG.md).

## Repository structure

The dataset is organized by component and crop. Each crop directory contains an
`images/` subtree organized by collection site and acquisition date, an
`annotations/` subtree with **standard** and **benchmark** tracks, and a
`metadata/` subtree.

```text
Artemis/
└── <crop>/
    ├── images/<collection-site>/<acquisition-date>/
    ├── annotations/
    │   ├── standard/
    │   └── benchmark/
    └── metadata/

ImageSafari/
└── <crop>/
    ├── images/<collection-site>/<acquisition-date>/
    ├── annotations/
    │   ├── standard/
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
| [`Artemis/`](Artemis/) | Artemis component (4 crops) |
| [`ImageSafari/`](ImageSafari/) | Image Safari component (18 crops) |
| [`docs/artemis.md`](docs/artemis.md) | Artemis component documentation |
| [`docs/imagesafari.md`](docs/imagesafari.md) | Image Safari component documentation |
| [`docs/variable_dictionary.csv`](docs/variable_dictionary.csv) | Metadata field definitions |
| [`docs/annotation_guidelines.md`](docs/annotation_guidelines.md) | Annotation ontology and quality-control procedures |
| [`docs/splits/`](docs/splits/) | Predefined train/validation/test splits |
| [`docs/metadata_validation_report.csv`](docs/metadata_validation_report.csv) | Metadata validation summary |
| [`imagesafari_artemis-crop-images.yaml`](imagesafari_artemis-crop-images.yaml) | Registry of Open Data on AWS metadata entry |
| [`get-to-know-a-dataset-imagesafari_artemis.ipynb`](get-to-know-a-dataset-imagesafari_artemis.ipynb) | Introductory AWS tutorial |
| [`CITATION.cff`](CITATION.cff) | Machine-readable citation metadata |
| [`CHANGELOG.md`](CHANGELOG.md) | Version history |
| [`LICENSE.md`](LICENSE.md) | Dataset license notice |

## License

[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) for the full
ImageSafari_Artemis collection.

## Documentation

- See [`docs/artemis.md`](docs/artemis.md) for the Artemis component.
- See [`docs/imagesafari.md`](docs/imagesafari.md) for the Image Safari component.
- Consult [`docs/variable_dictionary.csv`](docs/variable_dictionary.csv) and
  [`docs/annotation_guidelines.md`](docs/annotation_guidelines.md) before use.

## Citation

Cite the data descriptor paper and identify the ImageSafari_Artemis release
version used. Also cite the AWS Open Data registry entry, S3 bucket prefix, and the
date accessed.

## Contact

Questions, corrections, and dataset issues can be submitted through the
[repository issue tracker](https://github.com/CIAT-Artemis/imagesafari-artemis-crop-images/issues).
