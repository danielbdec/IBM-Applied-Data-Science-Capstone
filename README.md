# SpaceX Falcon 9 First Stage Landing Prediction — IBM Data Science Capstone

**Author:** Daniel B. de Carvalho  
**Repository:** https://github.com/danielbdec/IBM-Applied-Data-Science-Capstone  

## Project Overview

SpaceX advertises Falcon 9 rocket launches at **$62 million**, compared to competing launch providers at over **$165 million**, largely enabled by first-stage booster reusability. Predicting whether the Falcon 9 first stage will land successfully allows stakeholders to accurately estimate launch costs and evaluate competitive launch bids.

All notebooks and dashboard applications in this repository were executed end-to-end in IBM Skills Network Labs (JupyterLab / JupyterLite Pyodide / Cloud IDE) with zero execution errors.

## Repository Contents

| Stage | Deliverable | Key Outputs & Verified Findings |
|---|---|---|
| 1. Data Collection (API) | [`jupyter-labs-spacex-data-collection-api.ipynb`](jupyter-labs-spacex-data-collection-api.ipynb) | Filtered 94 raw SpaceX launches to 90 Falcon 9 launches; imputed 5 missing `PayloadMass` entries with exact mean `6104.9594 kg` (26 ocean/unattempted `LandingPad` nulls preserved cleanly). |
| 2. Data Collection (Web Scraping) | [`jupyter-labs-webscraping.ipynb`](jupyter-labs-webscraping.ipynb) | Parsed SpaceX Falcon 9 & Falcon Heavy Wikipedia launch tables via `BeautifulSoup`, generating a `121 x 11` structured dataset. |
| 3. Data Wrangling | [`labs-jupyter-spacex-Data-wrangling.ipynb`](labs-jupyter-spacex-Data-wrangling.ipynb) | Labeled binary `Class` targets across 90 Falcon 9 launches (`60` successes = `66.67%`, `30` failures = `33.33%`) across `CCAFS SLC 40` (55), `KSC LC 39A` (22), and `VAFB SLC 4E` (13). |
| 4. EDA with SQL | [`jupyter-labs-eda-sql-coursera_sqllite.ipynb`](jupyter-labs-eda-sql-coursera_sqllite.ipynb) | Executed all 10 SQL tasks in SQLite `SPACEXTABLE` (`101` records): identified **4 unique launch sites** (`CCAFS LC-40`, `VAFB SLC-4E`, `KSC LC-39A`, `CCAFS SLC-40`), NASA CRS payload `45,596 kg`, `F9 v1.1` mean `2,928.4 kg`, and first ground pad success on `2015-12-22`. |
| 5. EDA with Visualization | [`edadataviz.ipynb`](edadataviz.ipynb) | Generated 7 Seaborn/Matplotlib plots revealing steady reliability growth (`0.0%` in 2010–2013 to `90.0%` in 2019, `84.21%` in 2020) and `80` engineered one-hot features (`(90, 80)`). |
| 6. Interactive Geospatial Analytics | [`lab_jupyter_launch_site_location.ipynb`](lab_jupyter_launch_site_location.ipynb) | Built interactive Folium MarkerCluster & proximity maps across all 4 launch sites (`56` records); computed exact Haversine distances from `CCAFS SLC-40` to Coastline (`0.86 km`), Highway (`0.58 km`), Railway (`1.28 km`), and Titusville (`23.19 km`). |
| 7. Interactive Visual Dashboard | [`spacex-dash-app.py`](spacex-dash-app.py) | Built and ran a Plotly Dash dashboard (port `8050`): `KSC LC-39A` achieved both the highest success count (`10` / `41.7%` of 24 total successes) and highest success rate (`76.92%`); `3,000–4,000 kg` payload reached `72.73%`. |
| 8. Predictive Classification | [`SpaceX_Machine_Learning_Prediction_Part_5.ipynb`](SpaceX_Machine_Learning_Prediction_Part_5.ipynb) | StandardScaler + 80/20 split (`72` train / `18` test, `random_state=2`) + 10-fold `GridSearchCV` across Logistic Regression, SVM, Decision Tree, and KNN. **Decision Tree** achieved the highest 10-fold CV accuracy (**`87.50%`**) and highest held-out test accuracy (**`94.44%`**, Confusion Matrix `[[5, 1], [0, 12]]`), vs `83.33%` test accuracy (`[[3, 3], [0, 12]]`) for Logistic Regression (`84.64%` CV), SVM (`84.82%` CV), and KNN (`84.82%` CV). |
