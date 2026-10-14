# Mapping Rain and Hail Crop Damage in Udham Singh Nagar, Uttarakhand

> **In progress. No results yet.** Built in the open; every decision is logged in [`notes.md`](notes.md).

In autumn 2026, heavy rain and a hailstorm hit the farming plains of Udham Singh Nagar, where my family farms.
Storms like this can flatten or destroy a season's crop in a single day, and farmers often wait weeks for
damage surveys that decide compensation.

Optical satellites can't see through storm clouds, but **Sentinel-1 radar can**, and its data is free.
This project asks a simple question: **can free radar imagery show which fields were damaged, within days
of a storm, and how well does that hold up against what happened on the ground?**

## Approach (planned)

1. **Confirm the event:** pin down the storm's date and time and check it in satellite rainfall (NASA GPM IMERG).
2. **Check the data:** list Sentinel-1 radar passes before and after the storm, and clear Sentinel-2 images.
3. **Cropland mask:** use ESA WorldCover to keep only farmland.
4. **Simple baseline first:** compare radar backscatter (VV, VH) before and after the storm to flag
   fields that changed.
5. **Ground truth:** field photos, crop type and damage level from farmers, news reports and district records.
6. **Honest evaluation:** spatially separated validation, error maps, and clear limitations.
7. **ML only if it helps:** try a model only if it clearly beats the simple baseline.

Hail damage and waterlogging may look different to radar: standing water usually lowers the signal sharply,
while hail changes plant structure and may be subtler. Ground truth will record which fields had which.

## Ground truth so far

| Evidence | What it shows | Limitation |
|---|---|---|
| Two photos of hail at my home | Hail fell, roughly pea- to marble-sized, strong enough to strip leaves | Not a crop field; original metadata (time, GPS) not in these copies |
| A short video from a car during the storm | Storm clouds, rain, a fallen power line | Not a crop field; no date or location metadata |

Field photos with location, crop type and damage level are still being collected
(template: [`data/ground_truth/ground_truth_template.csv`](data/ground_truth/ground_truth_template.csv)).

## Roadmap

- [ ] Phase 1: Confirm event date, study area and satellite coverage (`notebooks/01_event_and_data_check.ipynb`)
- [ ] Phase 2: Prepare Sentinel-1 before/after images and cropland mask
- [ ] Phase 3: Change-detection baseline and first damage map
- [ ] Phase 4: Ground truth and honest validation
- [ ] Phase 5: ML model, only if it beats the baseline
- [ ] Phase 6: Village-level summary, write-up and interactive map

## Data sources

| Data | Source | Use |
|---|---|---|
| Radar (VV, VH) | Copernicus Sentinel-1 GRD | Before/after change |
| Optical | Copernicus Sentinel-2 surface reflectance | Crop condition on clear days |
| Land cover | ESA WorldCover 10 m v200 | Cropland mask |
| Rainfall | NASA GPM IMERG V07 | Confirm event timing |
| Boundary | FAO GAUL | Study area |
| Ground truth | Own photos, farmers, news, district records | Validation |

## Repository structure

| Path | What it is |
|---|---|
| `notebooks/01_event_and_data_check.ipynb` | Confirms the event and checks satellite coverage |
| `data/ground_truth/` | Ground truth template and evidence |
| `figures/` | Figures, added as the project progresses |
| `notes.md` | Running log of every decision, problem and fix |

## Run it

1. Get a free [Google Earth Engine](https://earthengine.google.com/) account (noncommercial use).
2. Open `notebooks/01_event_and_data_check.ipynb` in Colab or Jupyter.
3. Set your Earth Engine project ID and the event date in the configuration cell.

## Related work

This builds on my landslide susceptibility study of Rudraprayag:
[repository](https://github.com/makkergauri/uttarakhand-landslide-risk).

## Licence

MIT. Contains modified Copernicus Sentinel data.
