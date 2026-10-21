# HE3027 Group Project: Air Quality and House Prices in London

## Data

The data files are not on GitHub (too large). Put them into the `data/` folder:

```
Code/
└── data/
    ├── land_registry_pollution.dta
    ├── land_registry_crime.dta
    ├── land_registry_tube.dta
    ├── gla_lsoa_atlas/lsoa-data.csv                              (only for income_small_area.py)
    └── ons_msoa_income/ons-model-based-income-estimates-msoa.xls  (only for income_small_area.py)
```

The two income files are free downloads from the London Datastore:
[LSOA Atlas](https://data.london.gov.uk/dataset/lsoa-atlas) ("Current LSOA boundaries post-2011", CSV) and
[ONS Model-Based Income Estimates, MSOA](https://data.london.gov.uk/dataset/ons-model-based-income-estimates-msoa).

The file names must stay exactly like this, otherwise the code will not find them.

## Run

```
pip install pandas numpy matplotlib xlrd
python data_exploration.py
python basic_regressions.py
python final_model.py
python income_groups.py
python income_small_area.py
```

- `data_exploration.py` creates `data_exploration.md` and the graphs in `figures/`.
- `basic_regressions.py` creates `basic_regressions.md` with the regression table.
- `final_model.py` creates `final_model.md` (controls step by step, final model M8, robustness checks).
- `income_groups.py` creates `income_groups.md` and `figures/wtp_by_income_group.png` (functional form of income, WTP by low/middle/high income boroughs).
- `income_small_area.py` creates `income_small_area.md` and one graph per income measure, `figures/wtp_by_income_{lsoa,msoa,borough}.png` (WTP by income group with LSOA and MSOA household income, data sources, all specifications).
