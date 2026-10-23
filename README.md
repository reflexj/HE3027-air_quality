# HE3027 Group Project: Air Quality and House Prices in London

## Data

The data files are not on GitHub (too large). Put them into the `data/` folder:

```
Code/
└── data/
    ├── land_registry_pollution.dta
    ├── land_registry_crime.dta
    ├── land_registry_tube.dta
    ├── gla_lsoa_atlas/lsoa-data.csv                              (only for model_v1_income_small_area.py, model_v2.py)
    ├── ons_msoa_income/ons-model-based-income-estimates-msoa.xls  (only for model_v1_income_small_area.py)
    ├── os_open_roads/oproad_essh_gb.zip                          (only for model_v2_roads.py, keep zipped)
    ├── defra_road_noise/Road_Lden_London.shp (+ .dbf .shx .prj)  (only for model_v2_roads.py, unzipped)
    └── road_features.csv                                         (created by model_v2_roads.py on its first run)
```

The two income files are free downloads from the London Datastore:
[LSOA Atlas](https://data.london.gov.uk/dataset/lsoa-atlas) ("Current LSOA boundaries post-2011", CSV) and
[ONS Model-Based Income Estimates, MSOA](https://data.london.gov.uk/dataset/ons-model-based-income-estimates-msoa).

The road data are also free (Open Government Licence):
[OS Open Roads](https://osdatahub.os.uk/downloads/open/OpenRoads) (ESRI Shapefile, GB, about 600 MB; only the
London grid squares TQ and TL are read) and the Defra road noise map 2012 from the London Datastore,
[Noise pollution in London](https://data.london.gov.uk/dataset/noise-pollution-in-london-2zwnk) (`Road_Lden_London.zip`).

The file names must stay exactly like this, otherwise the code will not find them.

## Run

The file names show which model a script belongs to: `model_v0` (first regressions), `model_v1` (M8 with
the controls step by step) and `model_v1_*` (analyses built on it), `model_v2` (the newest model).

```
pip install pandas numpy matplotlib xlrd scipy shapely pyproj pyshp
python data_exploration.py
python model_v0.py
python model_v1.py
python model_v1_non-linear.py
python model_v1_income_groups.py
python model_v1_income_small_area.py
python model_v1_pm10_smoothing.py
python model_v2.py
python model_v2_roads.py
```

- `data_exploration.py` creates `data_exploration.md` and the graphs in `figures/`.
- `model_v0.py` creates `model_v0.md` with the regression table.
- `model_v1.py` creates `model_v1.md` (controls step by step, v1 model M8, robustness checks).
- `model_v1_non-linear.py` creates `model_v1_non-linear.md` (non-linear distance controls; needs scipy).
- `model_v1_income_groups.py` creates `model_v1_income_groups.md` and `figures/wtp_by_income_group.png` (functional form of income, WTP by low/middle/high income boroughs).
- `model_v1_income_small_area.py` creates `model_v1_income_small_area.md` and one graph per income measure, `figures/wtp_by_income_{lsoa,msoa,borough}.png` (WTP by income group with LSOA and MSOA household income, data sources, all specifications).
- `model_v1_pm10_smoothing.py` creates `model_v1_pm10_smoothing.md` and `figures/pm10_smoothing.png` (the 2011-2012 PM10 jump, smoothed PM10 measures and an IV with last year's PM10, with sources).
- `model_v2.py` creates `model_v2.md` and `figures/v2_interactions.png` (v2 model: log-quadratic distances, cubic borough pay, 3-year average PM10; interactions PM10 × house, PM10², PM10 × share aged 0-15/65+, PM10 × education). Needs `gla_lsoa_atlas/lsoa-data.csv`.
- `model_v2_roads.py` creates `model_v2_roads.md` and `figures/v2_roads.png` (v2 model with distance to the nearest motorway / A road and road noise: price effects, PM10 × near a main road, PM10 × noise, and whether main roads explain the larger PM10 discount for flats). Needs shapely, pyproj and pyshp.
- `null_results.txt` is a running list of everything we tested that had no (robust) effect, with numbers and the source file.
