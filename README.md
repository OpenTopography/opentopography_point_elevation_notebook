# OpenTopography Point Elevation API — Demo Notebook

[![NSF-2410799](https://img.shields.io/badge/NSF-2410799-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=2410799)
[![NSF-2410800](https://img.shields.io/badge/NSF-2410800-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=2410800)
[![NSF-2410801](https://img.shields.io/badge/NSF-2410801-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=2410801)

A Jupyter notebook demonstrating how to use the
[OpenTopography Point Elevation API](https://portal.opentopography.org/apidocs/#/Public/getPointElevation)
to retrieve and compare elevation values across multiple global datasets at a single geographic coordinate.

## What this notebook does

Rather than downloading and processing a full DEM for an area of interest, the Point Elevation API
returns the interpolated elevation at a single point from any of the datasets hosted by OpenTopography.
This makes it well suited for workflows like:

- Annotating a list of addresses or GPS waypoints with elevation
- Rapid cross-dataset comparison at specific field sites
- Validating or correcting elevation values in tabular datasets

The notebook queries three representative locations (urban, arid desert, forested) across 16 global
elevation datasets, then produces a multi-panel figure showing the elevation from each dataset alongside
regional and satellite map context.

## Datasets included

| Vertical datum | Datasets |
|---|---|
| EGM2008 Geoid | COP30, COP90, EU_DTM |
| EGM96 Geoid | SRTM_GL1, SRTM_GL3, NASADEM, AW3D30, SRTM15Plus, GEBCOIceTopo, GEBCOSubIceTopo |
| WGS84 Ellipsoid | GEDI_L3, AW3D30_E, SRTM_GL1_Ellip, GEDTM30 |
| NAVD88 | USGS10m, USGS30m |

## Requirements

```
pip install requests matplotlib numpy contextily geopandas shapely
```

> `contextily` and `geopandas` are only used for the map panels. If you only want the elevation
> bar charts, those two packages are not required.

## Getting an API key

A free OpenTopography account and API key are required to run the notebook.

1. Register at https://portal.opentopography.org/newUser
2. Request an API key at https://portal.opentopography.org/requestService?service=api
3. Paste your key into the `API_KEY` variable in the **Configuration** cell

## API usage limits

During the initial release of the Point Elevation API the following daily query limits apply:

| User type | Limit |
|---|---|
| Registered OpenTopography user | 50 queries/day |
| [OT+](https://opentopography.org/plus) member or academic user (`.edu` email) | 250 queries/day |

## Running the notebook

```bash
jupyter notebook PointElevationAPI_demo.ipynb
```

Run all cells in order. The data-fetching cell makes one API call per dataset per scenario
(48 calls total for the default three scenarios) and typically completes in about 60 seconds.

## License

This notebook is provided under the [BSD 3-Clause License](https://opensource.org/licenses/BSD-3-Clause).
