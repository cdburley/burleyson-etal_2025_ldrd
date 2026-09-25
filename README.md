# burleyson-etal_2026b_applied_energy

## Workflow
Use the following notebooks to rerun the analysis and reproduce the main and supplementary figures. The analysis is currently 
configured to run for eight Balancing Authorities (AZPS, BPAT, CISO, ERCO, FPL, ISNE, PJM, and SWPP) in the CONUS. The 
specific BAs the analysis uses are controlled in the `balancing_authority_modeled.yml` file in the `/data` directory. The
underlying machine learning models rely on functions within the Total ELectricity Loads (TELL) python package. Before 
running any of the scripts below you should install TELL using `pip install tell`.

| Notebook Order |              Script Name               |                                                       Description                                                        | 
|:--------------:|:--------------------------------------:|:------------------------------------------------------------------------------------------------------------------------:|
|       1        |    plot_ba_service_territory.ipynb     |                              Plots the service territory of the BAs used in this analysis.                               |
|       2        | plot_ba_load_weather_time_series.ipynb |                     Plots the raw time series of the load, weather, and population data for each BA.                     |
|       3        |     train_and_run_mlp_models.ipynb     | Iteratively trains the TELL MLP models using evolving time windows and uses the models to project loads forward in time. |
|       4        |    calculate_error_statistics.ipynb    |                             Calculates the error statistics for each of the trained models.                              |
|       5        |     plot_ba_error_evolution.ipynb      |                        Plots the evolution of annual errors by BA for each of the trained models.                        |
|       6        |      plot_ba_diurnal_errors.ipynb      |                         Plots the diurnal cycle of errors by BA for each of the trained models.                          |
|       7        | calculate_annual_energy_and_peak.ipynb |                    Calculates the annual energy and peak demand for each year from the EIA-930 data.                     |
