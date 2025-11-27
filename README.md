# Egyptian Landscape Change Detection (Google Earth Engine)

This repository contains a set of Google Earth Engine (GEE) scripts for analysing environmental and archaeological landscape change across Egypt using Sentinel-2, Sentinel-1 and DEM-derived variables.

These scripts were developed for my undergraduate dissertation and are maintained by **Phoebe Slight (2025)**.

## Dissertation Research Question

**“How can AI algorithms and machine-learning techniques be applied to assess changing archaeological landscapes in Egypt, and in what ways can these methods enhance archaeological interpretation and predictive modelling?”**

## What the scripts do

The scripts in this repository:

- Use an Area of Interest (AOI) for Egyptian study regions (e.g., Nile Valley, desert margins, oasis basins).
- Load **Sentinel-2 Level-2A** imagery (surface reflectance).
- Apply a **cloud and cirrus mask** using the `QA60` band.
- Create **median composites** for selected years or seasons.
- Calculate spectral indices such as:
  - NDVI (vegetation)
  - NDWI (moisture)
  - NBR (disturbance)
- Integrate **Sentinel-1 GRD IW VV** radar data for detecting surface roughness and disturbance.
- Use **DEM (SRTM)** to derive:
  - Slope
  - Roughness
  - Hillshade
  - Terrain metrics
- Combine multisensor layers for multi-temporal comparison.
- (Optional) Use **Random Forest classification** for land-cover mapping.
- Produce change-detection outputs showing:
  - Vegetation gain/loss
  - Desertification patterns
  - Disturbance or surface modification
  - Changes affecting archaeological visibility

## Inputs you must provide

You need to replace the asset paths in each script with your own GEE FeatureCollections:

- **AOI geometry**
  - e.g., `users/yourusername/Egypt_AOI_1`

- **Training polygons** (only for RF classification workflows)
  - Vegetation: `users/yourusername/Vegetation`
  - Bare: `users/yourusername/Bare`
  - Built-up: `users/yourusername/BuiltUp`
  - Desertified: `users/yourusername/Desertified`

If analysing a different region, upload your own FeatureCollections and update the paths accordingly.

## How to use the scripts

1. Open the **Google Earth Engine Code Editor**.
2. Upload your AOI (and training data, if required) as **FeatureCollections**.
3. Replace asset paths at the top of each script.
4. Paste the script into a new GEE script.
5. Click **Run**.

You should see outputs such as:

- Sentinel-2 composites (true/false colour)
- NDVI, NDWI, NBR layers
- Sentinel-1 VV radar backscatter
- DEM-derived slope or roughness
- Random Forest classifications (if applicable)
- Multi-year change detection maps

The map will centre on your AOI.

## Requirements

- Google Earth Engine account
- Access to:
  - `COPERNICUS/S2_SR_HARMONIZED` or `COPERNICUS/S2`
  - `COPERNICUS/S1_GRD`
  - `USGS/SRTMGL1_003` (DEM)
- AOI uploaded as a FeatureCollection
- (Optional) training polygons for classification scripts

## Attribution

- Supervisory guidance: **Dr Louise Rayne**, Newcastle University
- Scripts created and maintained by: **Phoebe Slight (2025)**
- Contact: `phoebeslight1@icloud.com`
