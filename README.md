# HE3027 Group Project: Air Quality and House Prices in London

## Data

The data files are not on GitHub (too large). Put them into the `data/` folder:

```
Code/
└── data/
    ├── land_registry_pollution.dta
    ├── land_registry_crime.dta
    └── land_registry_tube.dta
```

The file names must stay exactly like this, otherwise the code will not find them.

## Run

```
pip install pandas numpy matplotlib
python data_exploration.py
python basic_regressions.py
```

- `data_exploration.py` creates `data_exploration.md` and the graphs in `figures/`.
- `basic_regressions.py` creates `basic_regressions.md` with the regression table.
