# Artemis Phenotyping Dataset

Artemis is a structured phenotyping dataset that pairs imagery with detailed
agronomic, genotypic, and environmental metadata. Imaging was performed under
defined protocols that link each image to metadata collected in the field,
supporting fine-grained tasks such as trait estimation, growth stage
recognition, and disease quantification.

The dataset is maintained by the
[Alliance of Bioversity International and CIAT](https://alliancebioversityciat.org/)
and is being prepared for publication through the Registry of Open Data on AWS.

## Dataset summary

| Attribute | Value |
|---|---|
| Crops | 4 |
| Countries | 3 |
| License | CC BY-SA 4.0 |

## Crops

| Crop | Scientific name |
|---|---|
| Common bean | *Phaseolus vulgaris* |
| Cowpea | *Vigna unguiculata* |
| Soybean | *Glycine max* |
| Sorghum | *Sorghum bicolor* |

## Locations

Imaging was conducted at research sites in:

- Tanzania
- Uganda
- Colombia

## Data organization

The repository is organized by crop. Each crop directory contains:

- an `images/` subtree organized by collection site and acquisition date
- an `annotations/` subtree containing both automated and benchmark annotation
  tracks
- a `metadata/` subtree with agronomic, genotypic, and environmental records
  linked to each image

Representative structure:

```text
Artemis/
└── <crop>/
    ├── images/
    │   └── <collection-site>/
    │       └── <acquisition-date>/
    │           └── <file>.<extension>
    ├── annotations/
    │   ├── automated/
    │   └── benchmark/
    └── metadata/
```

## Metadata

Artemis links each image to field-collected metadata, including agronomic
observations, genotypic information, and environmental conditions recorded
under defined imaging protocols. Metadata files are stored in the `metadata/`
subtree for each crop.

| Field category | Description |
|---|---|
| Agronomic | Growth stage, trait measurements, and field observations |
| Genotypic | Variety or genotype identifiers linked to the imaged plot |
| Environmental | Site conditions, season, and capture context |
| Acquisition | Collection site, date, and imaging device |

## Annotations

The `annotations/` subtree provides two tracks:

- **automated/** — model-generated labels and trait estimates produced at
  scale across the collection
- **benchmark/** — expert-reviewed annotations intended for evaluation and
  method comparison

## Suggested research tasks

- Trait estimation from field imagery
- Growth stage recognition under controlled protocols
- Disease quantification with linked field metadata
- Genotype–phenotype association using paired imagery and metadata
- Cross-location generalization across Tanzania, Uganda, and Colombia

## Accessing the data

The S3 bucket name and AWS Region will be added after AWS provisions the
publication infrastructure. Once available, the collection will support
anonymous access without an AWS account.

List crop directories:

```bash
aws s3 ls --no-sign-request --region <AWS-REGION> s3://<S3-BUCKET-NAME>/Artemis/
```

List images for one crop:

```bash
aws s3 ls --no-sign-request --region <AWS-REGION> --recursive \
  s3://<S3-BUCKET-NAME>/Artemis/common-bean/images/
```

## License

The dataset is released under the
[Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/).

## Citation

> Alliance of Bioversity International and CIAT (2026). *Artemis Phenotyping
> Dataset*. Registry of Open Data on AWS.

Also include the date on which the data were accessed and identify the release
or S3 prefix used in the analysis.

## Contact

Questions, corrections, and dataset issues can be submitted through the
[repository issue tracker](https://github.com/CIAT-Artemis/imagesafari_artemis-crop-images/issues).
