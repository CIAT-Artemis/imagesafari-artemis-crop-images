# Artemis and Image Safari - Crop Imagery Datasets Spanning Globally Critical Food Species

This repository hosts **Artemis and Image Safari - Crop Imagery Datasets Spanning
Globally Critical Food Species**, listed on the
[Registry of Open Data on AWS](https://registry.opendata.aws/artemis-image-safari)
— a unified agricultural image collection comprising **7,469,218 field images**
across two complementary datasets, **Artemis** and **Image Safari**, developed by
the
[Alliance of Bioversity International and CIAT](https://alliancebioversityciat.org/).

The collection spans **18 crop species** and **11 countries** across sub-Saharan
Africa, Latin America, and the United States, with emphasis on smallholder and
structured phenotyping farming systems that remain underrepresented in public
imaging corpora. Together, the datasets combine crop imagery, structured
metadata, and annotations to support agricultural foundation models,
plant disease detection, growth stage recognition, crop identification,
agricultural monitoring, and cross-environment generalisation research.

| Dataset | Images | Crops | Countries | Focus |
|---|---:|---:|---:|---|
| **Artemis** | 1,387,663 | 4 | 4 | Structured phenotyping with linked field metadata |
| **Image Safari** | 6,081,555 | 18 | 9 | Diversity across crops, geographies, and imaging conditions |
| **Combined** | **7,469,218** | **18** | **11** | Unified Artemis and Image Safari collection |

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

A subset of **46,952 annotated images** (16,382 Artemis; 30,570 Image Safari)
includes organ-level labels organized by annotation task. Artemis provides
**instance segmentation** and **object detection** across three crops (common
bean, cowpea, and sorghum). Image Safari annotations are released under a
**standard** track for **16 of 18** crops and include **point**, **semantic
segmentation**, **scribble**, **object detection**, and **instance
segmentation** (object detection currently for common bean only). Finger millet
and lentil have imagery but no published annotation sets.

## Public access

| Asset | Location | Notes |
|---|---|---|
| Images, annotations, and metadata | [Registry of Open Data on AWS](https://registry.opendata.aws/artemis-image-safari) | Public S3 bucket `s3://alliance-artemis-imagesafari/` (`us-west-2`) |
| Documentation, schemas, splits, tutorials | This GitHub repository | [`docs/`](docs/) |
| Introductory tutorial | [`get-to-know-a-dataset-imagesafari_artemis.ipynb`](get-to-know-a-dataset-imagesafari_artemis.ipynb) | Browse S3 anonymously; examples use Amazon S3, SageMaker, Glue, and Athena |
| Issues and corrections | [GitHub Issues](https://github.com/CIAT-Artemis/imagesafari-artemis-crop-images/issues) | |

New imagery collected during annual field campaigns is reviewed, annotated, and
added to the dataset approximately once per year. Annotation updates and quality
corrections are versioned and documented in [`CHANGELOG.md`](CHANGELOG.md).

## Repository structure

The collection is hosted in the `alliance-artemis-imagesafari` S3 bucket and is
organized into the Artemis and Image Safari datasets, grouped by crop. Each crop
directory contains an `images/` subtree, an `annotations/` subtree, and a
`metadata/` subtree. Artemis annotations are nested by optional variety, task
type, and named set. Image Safari annotations are organized under a **standard**
track by modality and named set.

```text
alliance-artemis-imagesafari/
├── Artemis/
│   └── <crop>/                    # e.g. common-bean, cowpea, sorghum, soybean
│       ├── images/
│       ├── annotations/
│       │   └── [<variety>/]       # e.g. bush-bean (when applicable)
│       │       ├── instance_segmentation/<set>/
│       │       └── object_detection/<set>/
│       └── metadata/
└── ImageSafari/
    └── <crop>/
        ├── images/
        ├── annotations/
        │   └── standard/
        │       ├── point/<set>/
        │       ├── semantic_segmentation/<set>/
        │       ├── scribble/<set>/
        │       ├── object_detection/<set>/      # common-bean in current release
        │       └── instance_segmentation/<set>/
        └── metadata/
```

**Artemis** annotations cover instance segmentation and object detection
(16,382 annotated images; 289,405 annotation instances across eight published
sets). Soybean imagery is included in the corpus but has no published
annotation sets in the current inventory. **Image Safari** annotations cover
point, semantic segmentation, scribble, object detection, and instance
segmentation (30,570 annotated images; about 10.05 million annotation
instances across 68 published sets). Finger millet and lentil are present in
the image corpus but have no published annotation sets in the current
inventory. African yam documentation treats S3 prefixes `african-yam/` and
`yam/` as the same crop.

Images are stored as JPEG files at original acquisition resolution. Segmentation
outputs are provided as PNG masks with matching filenames. Object-level
annotations are stored in COCO JSON format. **Artemis** metadata is provided as
Parquet and CSV files under each crop's `metadata/` subtree. **Image Safari**
metadata is provided as JSON sidecar files.

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
Artemis and Image Safari collection.

## Documentation

- See [`docs/artemis.md`](docs/artemis.md) for the Artemis dataset.
- See [`docs/imagesafari.md`](docs/imagesafari.md) for the Image Safari dataset.
- Consult [`docs/variable_dictionary.csv`](docs/variable_dictionary.csv) and
  [`docs/annotation_guidelines.md`](docs/annotation_guidelines.md) before use.

## Citation

Cite the data descriptor paper:

> Mutuvi S., Guerena D., Zych M., Henday S., Girma E., Mungubariki T., Agesa B.,
> Zochowski M., Ciolek D., Lazowik M., Chen J., Goeke L., Omwandho J., del Palma
> G., Malabi J., Phomebeya S., Sanena M., Marcos J. T. C., Ghandi H., Nas M.,
> Rathore A., Mendes T., Yadav S., Adjah K. L., Woltering L., Lekasio E., Mushi
> B., Abraham L., Katunzi G., Remy S. L., Siyavora T., Selvaraj M., Casas J.,
> Boukar O., Ongom P., Nakato G. V., Mwanje G., Agre P., Laporte M.-A., Asefa
> T., Odama R., Mukankusi C., and Wu W. *Artemis and Image Safari - Crop Imagery
> Datasets Spanning Globally Critical Food Species.*

When accessing data through AWS, also cite the registry entry:

> Artemis and Image Safari - Crop Imagery Datasets Spanning Globally Critical
> Food Species was accessed on [DATE] at
> [registry.opendata.aws/artemis-image-safari](https://registry.opendata.aws/artemis-image-safari).

Identify the release version used, the S3 bucket prefix, and the date accessed.
Machine-readable citation metadata is in [`CITATION.cff`](CITATION.cff).

## Contact

Questions, corrections, and dataset issues can be submitted through the
[repository issue tracker](https://github.com/CIAT-Artemis/imagesafari-artemis-crop-images/issues)
or by email at [alliance-data-helpdesk@cgiar.org](mailto:alliance-data-helpdesk@cgiar.org).
