# Ground truth

Each row in `ground_truth_template.csv` is one observation.

| Column | Meaning |
|---|---|
| `id` | Unique ID, e.g. GT002 |
| `date_observed` | Date the photo or observation was made (YYYY-MM-DD) |
| `latitude`, `longitude` | Field location in decimal degrees (from photo GPS or a map) |
| `village` | Village name |
| `crop` | Crop in the field (e.g. paddy, sugarcane) |
| `damage_class` | `none`, `partial`, `total`, or `not_a_field` |
| `damage_type` | `hail`, `waterlogging`, `lodging` (flattened), `both`, or `none` |
| `source` | `own_photo`, `family`, `farmer`, `news`, `patwari`, `district_record` |
| `photo_file` | Path(s) in `evidence/`, separated by `;` |
| `consent` | `yes` if the field owner agreed to their information being used |
| `notes` | Anything else |

Undamaged fields matter as much as damaged ones: the map can only be tested if both are recorded.
Ask permission before photographing someone's field or using their information.
