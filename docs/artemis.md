# Artemis Phenotyping Dataset

Artemis is a structured phenotyping dataset that pairs imagery with detailed
agronomic, genotypic, and environmental metadata. Imaging was performed under
defined smartphone and push-cart protocols that link each image to metadata
collected in the field, supporting fine-grained tasks such as trait estimation,
growth stage recognition, and disease quantification.

The dataset is maintained by the
[Alliance of Bioversity International and CIAT](https://alliancebioversityciat.org/).

## Dataset summary

| Attribute | Value |
|---|---:|
| Images | 1,387,663 |
| Annotated images | 12,216 |
| Crops | 4 |
| Countries | 4 |
| Image format | JPEG |
| License | CC BY-SA 4.0 |

## Crops

| Crop | Scientific name |
|---|---|
| Common bean | *Phaseolus vulgaris* |
| Cowpea | *Vigna unguiculata* |
| Soybean | *Glycine max* |
| Sorghum | *Sorghum bicolor* |

## Locations

Structured breeding trials and phenotyping experiments were conducted at
research stations in:

- Tanzania
- Uganda
- Colombia
- United States

## Images by crop and country

| Crop | Country | Images |
|---|---|---:|
| Common bean | Tanzania | 739,649 |
| Common bean | Uganda | 285,394 |
| Common bean | Colombia | 230,691 |
| Common bean | United States | 12,054 |
| Cowpea | United States | 59,614 |
| Cowpea | Tanzania | 520 |
| Sorghum | United States | 58,765 |
| Sorghum | Tanzania | 648 |
| Soybean | Colombia | 330 |
| **Total** | | **1,387,663** |

Counts are reported after automated quality control.

## Data acquisition

Artemis imagery was acquired using Android smartphones in handheld and
push-cart configurations. Capture protocols distinguish platform, viewpoint
(top-down, above-canopy, under-canopy), and spatial framing across growth
stages. Device models included Samsung Galaxy, OnePlus, Infinix, Tecno, Redmi,
and Nokia handsets, reflecting realistic field phenotyping equipment.

## Data organization

```text
Artemis/
└── <crop>/
    ├── images/
    ├── annotations/
    │   ├── instance_segmentation/
    │   ├── object_detection/
    │   └── image_classification/
    └── metadata/
```

Images are stored as JPEG files. Segmentation outputs are PNG masks. Object-level
annotations are COCO JSON. Metadata files are provided as Parquet and CSV
under each crop's `metadata/` subtree.

## Metadata

Standard fields are documented in [`variable_dictionary.csv`](variable_dictionary.csv).
Artemis records link each image to plot identifiers, variety identifiers,
treatments, growth stage, and quantitative field observations collected in
Open Data Kit.

## Annotations

Artemis annotations are organized by task under each crop's `annotations/`
directory:

| Task | Directory | Typical formats |
|---|---|---|
| Instance segmentation | `instance_segmentation/` | Polygon masks / COCO |
| Object detection | `object_detection/` | Bounding boxes / COCO |
| Image classification | `image_classification/` | Class labels |

Annotated Artemis subsets:

| Crop | Countries | Annotated images | Types |
|---|---|---:|---|
| Common bean | TZ, UG, CO | 4,292 | Polygon, bounding boxes |
| Cowpea | TZ, US | 4,642 | Polygon, bounding boxes |
| Sorghum | TZ, US | 3,282 | Polygon, bounding boxes |

## Public access

| Channel | Location |
|---|---|
| Dataset hosting | [Registry of Open Data on AWS](https://registry.opendata.aws/artemis-image-safari) (`s3://alliance-artemis-imagesafari/Artemis/`) |
| Documentation and schemas | [GitHub repository](https://github.com/CIAT-Artemis/imagesafari-artemis-crop-images) |

```bash
aws s3 ls --no-sign-request --region us-west-2 s3://alliance-artemis-imagesafari/Artemis/
```

## License

Released under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).

## Citation

> Mutuvi S., Guerena D., Zych M., Henday S., Girma E., Mungubariki T., Agesa B.,
> Zochowski M., Ciolek D., Lazowik M., Chen J., Goeke L., Omwandho J., del Palma
> G., Malabi J., Phomebeya S., Sanena M., Marcos J. T. C., Ghandi H., Nas M.,
> Rathore A., Mendes T., Yadav S., Adjah K. L., Woltering L., Lekasio E., Mushi
> B., Abraham L., Katunzi G., Remy S. L., Siyavora T., Selvaraj M., Casas J.,
> Boukar O., Ongom P., Nakato G. V., Mwanje G., Agre P., Laporte M.-A., Asefa
> T., Odama R., Mukankusi C., and Wu W. (2026). *Artemis and Image Safari - Crop
> Imagery Datasets Spanning Globally Critical Food Species*. Registry of Open
> Data on AWS.

## Contact

[Repository issue tracker](https://github.com/CIAT-Artemis/imagesafari-artemis-crop-images/issues)
