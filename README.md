# Cascadia Ground Failure Data Repository

[![License: BSD-3-Clause](https://img.shields.io/badge/License-BSD_3--Clause-blue.svg)](LICENSE)

Collection, harmonization and preparation of landslide and ground-failure inventories for the Cascadia region (California, Oregon, Washington and British Columbia). This repository underpins the CRESCENT Ground Failure Repository and viewer with reproducible data-processing workflows, and its Jupyter Book is the main reference for contributors.

**Read the book:** https://cascadiaquakes.github.io/cascadia-landslide-book/

**Viewer:** https://ground-failure.cascadiaquakes.org

---

## Contents

- **Processing**: notebooks for data acquisition, preprocessing, harmonization and enrichment (`processing_notebooks/`)
- **Submission Instructions**: how to contribute an inventory (`submission_instructions.md`)
- Standardized GeoJSON / CSV outputs for visualization and analysis

---

## Data

Download the source datasets and place them in a local `DATA/` directory (not tracked by git) before running the notebooks.

**Landslide inventories**

- **Oregon**: Statewide Landslide Information Database for Oregon (SLIDO), https://www.oregon.gov/dogami/slido/Pages/data.aspx
- **Washington**: Washington Geological Survey, Landslide Hazard Program, https://dnr.wa.gov/washington-geological-survey/geologic-hazards-and-environment/landslides
- **California**: California Geological Survey, Landslide Inventory and Deep-Seated Landslide Susceptibility Map, https://maps.conservation.ca.gov/cgs/lsi/
- **British Columbia (regional example)**: Landslide inventory map of the Valemount area, https://ostrnrcan-dostrncan.canada.ca/entities/publication/405661b8-7bd8-49d0-8f03-f9bac9aa7c52
- **Canada (national)**: Preliminary Canadian Landslide Database, https://doi.org/10.5281/zenodo.7089351

**Ancillary hazard data**

- **Seismic shaking**: the ShakeMap XML grid file (`grid.xml`) for the USGS M9.0 Cascadia scenario, https://earthquake.usgs.gov/scenarios/eventpage/cszm9ensemble_se/shakemap/intensity
- **Rainfall**: 30-year (1990-2019) annual average DAYMET precipitation for North America, https://doi.org/10.5066/P9E0JZ82

All original datasets remain the intellectual property of their respective agencies and authors.

---

## Processing Workflow

1. **Exploratory data analysis**: inspect raw inventories (formats, attributes, spatial coverage).
2. **Preprocessing**: ingest raw datasets, normalize geometries and coordinate reference systems, and map source attributes to a common schema.
3. **Postprocessing**: assign unique landslide identifiers, add seismic shaking metrics (ShakeMap) and rainfall, and produce standardized GeoJSON / CSV outputs.
4. **Vector tiles (optional)**: convert processed GeoJSON into vector tiles for web visualization (`static_tiling/`).

---

## Running Locally

Install the core Python packages to run the notebooks:

```bash
pip install geopandas numpy pandas seaborn fiona contextily
```

For vector tile generation, install [Tippecanoe](https://github.com/mapbox/tippecanoe) (`brew install tippecanoe` on macOS, or build it from source on Linux).

The book is built with [Jupyter Book](https://jupyterbook.org) (v1). To build it, from the repository root:

```bash
pip install -r requirements.txt
jupyter-book build .
```

Then open `_build/html/index.html`.

---

## Project Structure

```
.
├── processing_notebooks/
│   ├── ExploratoryDataAnalysis/     # Initial exploration (not part of the book)
│   ├── PreProcessing/               # Source-specific ingestion and cleaning
│   ├── PostProcessing/              # Harmonization, IDs, hazard attribution
│   └── postGIS/                     # Optional database workflows
├── datasets_description/            # Supporting metadata and notes
├── static_tiling/                   # Vector tile generation pipelines
├── intro.md                         # Book landing page
├── processing.md                    # Processing overview
├── submission_instructions.md       # Contribution guide
├── _toc.yml / _config.yml           # Jupyter Book configuration
└── README.md
```

---

## Deployment

GitHub Actions builds the book on every push to `main` and publishes it to GitHub Pages.

---

## Contributing

1. Follow the preprocessing examples in the book.
2. Produce a clean, standardized GeoJSON output.
3. Review the [Submission Instructions](https://cascadiaquakes.github.io/cascadia-landslide-book/submission_instructions.html).
4. Contact the team below to coordinate inclusion.

---

## License

This project is licensed under the BSD 3-Clause License. See [LICENSE](LICENSE).

---

## Contacts

- **Loïc Bachelot**, University of Oregon: [lbachelo@uoregon.edu](mailto:lbachelo@uoregon.edu)
- **William Marfo**, University of California, Davis: [wmarfo@ucdavis.edu](mailto:wmarfo@ucdavis.edu)
- **Amanda M. Thomas**, University of California, Davis: [amthom@ucdavis.edu](mailto:amthom@ucdavis.edu)

For corrections or suggestions, please [open an issue](https://github.com/cascadiaquakes/cascadia-landslide-book/issues).

---

## Acknowledgments

<table>
  <tr>
    <td align="center" valign="middle">
      <img src="https://raw.githubusercontent.com/cascadiaquakes/.github/main/assets/crescent-circle.png" alt="CRESCENT Logo" width="150" />
    </td>
    <td align="center" valign="middle">
      <img src="https://raw.githubusercontent.com/cascadiaquakes/.github/main/assets/nsf-logo.png" alt="NSF Logo" width="450" />
    </td>
  </tr>
</table>

This project is supported by the National Science Foundation through the Cascadia Region Earthquake Science Center (CRESCENT), Cooperative Agreement EAR-2225286.
