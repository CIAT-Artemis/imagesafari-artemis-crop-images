# ImageSafari_Artemis Crop Image Collection

This repository hosts the **ImageSafari_Artemis** dataset — also listed on the
[Registry of Open Data on AWS](https://registry.opendata.aws/) as **Artemis and
Image Safari Agricultural Imaging Dataset** — a unified agricultural image
collection comprising **7,469,220 field images** across two complementary
datasets, **Artemis** and **Image Safari**, developed by the
[Alliance of Bioversity International and CIAT](https://alliancebioversityciat.org/).

The collection spans **18 crop species** and **11 countries** across sub-Saharan
Africa, Latin America, and the United States, with emphasis on smallholder and
structured phenotyping farming systems that remain underrepresented in public
imaging corpora. Together, the datasets combine crop imagery, structured
metadata, and benchmark annotations to support agricultural foundation models,
plant disease detection, growth stage recognition, crop identification,
agricultural monitoring, and cross-environment generalisation research.

| Dataset | Images | Crops | Countries | Focus |
|---|---:|---:|---:|---|
| **Artemis** | 1,387,665 | 4 | 4 | Structured phenotyping with linked field metadata |
| **Image Safari** | 6,081,555 | 18 | 9 | Diversity across crops, geographies, and imaging conditions |
| **Combined** | **7,469,220** | **18** | **11** | Unified ImageSafari_Artemis collection |

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
The published collection contains **6,081,555 cleaned images** selected from a
working corpus of 7,352,184 images, contributed by **15 research centres**.
Multiple imaging devices and field conditions are represented, with particular
emphasis on smallholder farming systems common in the Global South that remain
substantially underrepresented in existing public datasets.

A subset of **42,981 annotated images** (12,216 Artemis; 30,765 Image Safari)
includes organ-level labels in **standard** and **benchmark** annotation tracks.
The **benchmark** track provides expert-reviewed annotations for banana, common
bean, potato, and sorghum; the **standard** track covers the broader annotated
subset produced through the scaled annotation pipeline.

## Public access

| Asset | Location | Notes |
|---|---|---|
| Images, annotations, and metadata | [Registry of Open Data on AWS](https://registry.opendata.aws/artemis-image-safari) | Public S3 bucket (`us-east-1`); bucket name to be added after provisioning |
| Documentation, schemas, splits, tutorials | This GitHub repository | [`docs/`](docs/) |
| Introductory tutorial | [`get-to-know-a-dataset-imagesafari_artemis.ipynb`](get-to-know-a-dataset-imagesafari_artemis.ipynb) | Browse S3 anonymously; examples use Amazon S3, SageMaker, Glue, and Athena |
| Issues and corrections | [GitHub Issues](https://github.com/CIAT-Artemis/imagesafari-artemis-crop-images/issues) | |

New imagery collected during annual field campaigns is reviewed, annotated, and
added to the dataset approximately once per year. Annotation updates and quality
corrections are versioned and documented in [`CHANGELOG.md`](CHANGELOG.md).

## Repository structure

The collection is organized into the Artemis and Image Safari datasets, grouped by crop. Each crop directory contains an
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
| [`Artemis/`](Artemis/) | Artemis dataset (4 crops) |
| [`ImageSafari/`](ImageSafari/) | Image Safari dataset (18 crops) |
| [`docs/artemis.md`](docs/artemis.md) | Artemis dataset documentation |
| [`docs/imagesafari.md`](docs/imagesafari.md) | Image Safari dataset documentation |
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

- See [`docs/artemis.md`](docs/artemis.md) for the Artemis dataset.
- See [`docs/imagesafari.md`](docs/imagesafari.md) for the Image Safari dataset.
- Consult [`docs/variable_dictionary.csv`](docs/variable_dictionary.csv) and
  [`docs/annotation_guidelines.md`](docs/annotation_guidelines.md) before use.

## Citation

Cite the data descriptor paper:

> Mutuvi S., Guerena D., Zych M., Henday S., Agesa B., Ghandi A., et al.
> *Artemis and Image Safari: Large imagery datasets targeting crop species and
> smallholder farming systems in the global south.* [PAPER_DOI_URL]

When accessing data through AWS, also cite the registry entry:

> Artemis and Image Safari Agricultural Imaging Dataset was accessed on [DATE]
> at [registry.opendata.aws/artemis-image-safari](https://registry.opendata.aws/artemis-image-safari).

Identify the ImageSafari_Artemis release version used, the S3 bucket prefix, and
the date accessed. Machine-readable citation metadata is in [`CITATION.cff`](CITATION.cff).

## Contact

Questions, corrections, and dataset issues can be submitted through the
[repository issue tracker](https://github.com/CIAT-Artemis/imagesafari-artemis-crop-images/issues)
or by email at [alliance-data-helpdesk@cgiar.org](mailto:alliance-data-helpdesk@cgiar.org).
