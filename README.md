# burleyson-etal_2025_ldrd

## Reproduce work done so far
Use the following notebooks to rerun the analysis and reproduce the main and supplementary figures. The analysis is currently 
configured to run for eight Balancing Authorities (AZPS, BPAT, CISO, ERCO, FPL, ISNE, PJM, and SWPP) in the CONUS. The 
specific BAs the analysis uses are controlled in the 'balancing_authority_modeled.yml' file in the `/data` directory. The
underlying machine learning models rely on functions within the Total ELectricity Loads (TELL) python package. Before 
running any of the scripts below you should install TELL using `pip install tell`.

| Figure Numbers |              Script Name               |                                                       Description                                                       | 
|:--------------:|:--------------------------------------:|:-----------------------------------------------------------------------------------------------------------------------:|
|      TBD       |    plot_ba_service_territory.ipynb     |                              Plots the service territory of the BAs used in this analysis.                              |
|      TBD       | plot_ba_load_weather_time_series.ipynb |                    Plots the raw time series of the load, weather, and population data for each BA.                     |
|      N/A       |    train_and_run_mlp_models.ipynb      | Iteratively trains the TELL MLP models using evolving time windows and uses the models to project loads forward in time |

## Proposed next steps
1. Retrain the MLP models to include total population in the BA as a predictive variable.