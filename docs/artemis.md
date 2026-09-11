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
| Annotated images | 16,382 |
| Annotation instances | 289,405 |
| Crops in image corpus | 4 |
| Crops with published annotations | 3 |
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
    │   └── [<variety>/]                 # e.g. bush-bean when applicable
    │       ├── instance_segmentation/<set>/
    │       │   ├── <set>_all.json       # COCO
    │       │   └── annotated_images/
    │       └── object_detection/<set>/
    │           ├── <set>_all.json
    │           └── annotated_images/
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

Artemis annotations are organized by task (and optional variety) under each
crop's `annotations/` directory. The current public inventory (2026-09-11)
covers **instance segmentation** and **object detection** only.

| Task | Annotated images | Annotation instances | Crops |
|---|---:|---:|---|
| Object detection | 14,693 | 258,323 | common bean, cowpea, sorghum |
| Instance segmentation | 1,689 | 31,082 | common bean |
| **Total** | **16,382** | **289,405** | **3** |

### Annotated images by crop and type

| Crop | Instance segmentation | Object detection | Total |
|---|---:|---:|---:|
| Common bean | 1,689 | 3,703 | 5,392 |
| Cowpea | 0 | 4,264 | 4,264 |
| Sorghum | 0 | 6,726 | 6,726 |
| Soybean | 0 | 0 | 0 |

### Published annotation sets

| Crop | Variety | Type | Set | Images | Annotations |
|---|---|---|---|---:|---:|
| Common bean | bush-bean | instance_segmentation | bushbean_flower | 854 | 14,434 |
| Common bean | bush-bean | instance_segmentation | bushbean_pod | 835 | 16,648 |
| Common bean | bush-bean | object_detection | bushbean_plant_stand | 1,686 | 40,212 |
| Common bean | bush-bean | object_detection | bushbean_pod | 2,017 | 47,813 |
| Cowpea | — | object_detection | cowpea_plant_stand | 2,132 | 33,096 |
| Cowpea | — | object_detection | plant_stand_object_detection | 2,132 | 33,096 |
| Sorghum | — | object_detection | plant_stand_object_detection | 3,363 | 55,020 |
| Sorghum | — | object_detection | sorghum_plant_stand | 3,363 | 49,086 |

Example classes include `plant_bean`, `flower_open`, `flower_closed`, `pod`,
`fruit_pod`, `cowpea_plant`, weed classes, and `sorghum`. See
[`annotation_guidelines.md`](annotation_guidelines.md).

**Known inventory note:** one cowpea object-detection set reports missing linked
image objects in the 2026-09-11 bucket inventory; users should validate image
availability for that set before training.

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
