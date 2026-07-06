# Artemis and Image Safari Crop Image Collections

This repository hosts two complementary agricultural image datasets developed by
the Alliance of Bioversity International and CIAT.

**Artemis** is a structured phenotyping dataset that pairs imagery with
detailed agronomic, genotypic, and environmental metadata across four crop
species — common bean (*Phaseolus vulgaris*), cowpea (*Vigna unguiculata*),
soybean (*Glycine max*), and sorghum (*Sorghum bicolor*) — and three locations:
Tanzania, Uganda, and Colombia. Imaging was performed under defined protocols
that link each image to metadata collected in the field, supporting fine-grained
tasks such as trait estimation, growth stage recognition, and disease
quantification.

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

The collections are being prepared for publication through the Registry of Open
Data on AWS.

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
    │   ├── automated/
    │   └── benchmark/
    └── metadata/

ImageSafari/
└── <crop>/
    ├── images/<collection-site>/<acquisition-date>/
    ├── annotations/
    │   ├── automated/
    │   └── benchmark/
    └── metadata/
```

## Repository contents

| File | Purpose |
|---|---|
| [`Artemis/`](Artemis/) | Structured phenotyping dataset (4 crops) |
| [`ImageSafari/`](ImageSafari/) | Diversity-driven image corpus (18 crops) |
| [`docs/artemis.md`](docs/artemis.md) | Artemis documentation, metadata fields, and access instructions |
| [`docs/imagesafari.md`](docs/imagesafari.md) | Image Safari documentation, crop counts, curation summary, and access instructions |
| [`artemis-crop-images.yaml`](artemis-crop-images.yaml) | Artemis metadata entry for the Registry of Open Data on AWS |
| [`imagesafari-crop-images.yaml`](imagesafari-crop-images.yaml) | Image Safari metadata entry for the Registry of Open Data on AWS |
| [`get-to-know-a-dataset-imagesafari.ipynb`](get-to-know-a-dataset-imagesafari.ipynb) | Introductory AWS tutorial for Image Safari |
| [`CITATION.cff`](CITATION.cff) | Machine-readable citation metadata |
| [`LICENSE.md`](LICENSE.md) | Dataset license notice |

## Dataset summary

| | Artemis | Image Safari |
|---|---|---|
| Crops | 4 | 18 |
| Countries | 3 | 9 |
| Images | TBD | 6,081,555 |
| Focus | Structured phenotyping with linked field metadata | Diversity across crops, geographies, and imaging conditions |
| License | [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) | [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) |

## Access

The S3 bucket name and AWS Region will be added after AWS provisions the
publication infrastructure. Once available, both collections will support
anonymous access without an AWS account.

## Documentation

- See [`docs/artemis.md`](docs/artemis.md) for Artemis dataset description,
  metadata fields, and access examples.
- See [`docs/imagesafari.md`](docs/imagesafari.md) for Image Safari dataset
  description, crop counts, curation method, citation guidance, and
  limitations.

## Contact

Questions, corrections, and dataset issues can be submitted through the
[repository issue tracker](https://github.com/CIAT-Artemis/imagesafari_artemis-crop-images/issues).
